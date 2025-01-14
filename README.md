# CXDatePickerView
![自定义日期选择器](https://github.com/CXTretar/CXDatePickerView/blob/master/screenshots/1.png)
# Install【安装】
在Podfile文件中添加`pod 'CXDatePickerView'`，并运行 `pod install`
# Usage【使用】
* import【导入框架】
`#import "CXDatePickerView.h"`

* init【创建选择器】

```  
  /**
 默认滚动到当前时间
 */
- (instancetype)initWithDateStyle:(CXDateStyle)datePickerStyle CompleteBlock:(void(^)(NSDate *date))completeBlock;

/**
 滚动到指定的的日期
 */
- (instancetype)initWithDateStyle:(CXDateStyle)datePickerStyle scrollToDate:(NSDate *)scrollToDate CompleteBlock:(void(^)(NSDate *date))completeBlock;
```
* style【选择器样式】

```  
/**
 *  弹出日期类型
 */
typedef NS_ENUM(NSUInteger, CXDateStyle) {
    CXDateStyleShowYearMonthDayHourMinute  = 0,//年月日时分
    CXDateStyleShowMonthDayHourMinute,//月日时分
    CXDateStyleShowYearMonthDay,//年月日
    CXDateStyleShowYearMonth,//年月
    CXDateStyleShowMonthDay,//月日
    CXDateStyleShowHourMinute//时分
};
```
* custom【自定义属性】
```
@property (nonatomic, assign) CGFloat showAnimationTime; // 弹出动画时间
@property (nonatomic, assign) CGFloat shadeViewAlphaWhenShow; // 展示时背景透明度
@property (nonatomic, strong) UIColor *headerViewColor; // 头部视图背景颜色
@property (nonatomic, strong) UIColor *doneButtonColor; // 确定按钮颜色
@property (nonatomic, copy) NSString *doneButtonTitle; // 确定按钮文字
@property (nonatomic, strong) UIFont *doneButtonFont; // 确定按钮字体
@property (nonatomic, strong) UIColor *cancelButtonColor; // 取消按钮颜色
@property (nonatomic, copy) NSString *cancelButtonTitle; // 取消按钮文字
@property (nonatomic, strong) UIFont *cancelButtonFont // 取消按钮字体
@property (nonatomic, strong) UIColor *dateLabelColor; // 年-月-日-时-分 文字颜色
@property (nonatomic, strong) UIColor *datePickerColor; // 滚轮日期颜色
@property (nonatomic, strong) UIFont *datePickerFont; // 滚轮日期字体
@property (nonatomic, strong) NSDate *maxLimitDate; // 限制最大时间（默认2099）datePicker大于最大日期则滚动回最大限制日期
@property (nonatomic, strong) NSDate *maxLimitDate; // 限制最小时间（默认0） datePicker小于最小日期则滚动回最小限制日期
@property (nonatomic, strong) UIColor *yearLabelColor; // 大号年份字体颜色
@property (nonatomic, assign) BOOL hideDateNameLabel; // 隐藏每行年月日文字
@property (nonatomic, assign) BOOL hideSegmentedLine; // 隐藏每行分割线
@property (nonatomic, assign) BOOL hideBackgroundYearLabel; // 隐藏背景年份文字
@property (nonatomic, assign) CGFloat topViewHeight; // 头部按钮视图高度
@property (nonatomic, assign) CGFloat pickerViewHeight; // 选择器部分视图高度
@property (nonatomic, assign) CGFloat pickerRowHeight // 选择器每行高度
```
* example【示例】 
```
CXDatePickerView *datepicker = [[CXDatePickerView alloc] initWithDateStyle:CXDateStyleShowYearMonthDayHourMinute CompleteBlock:^(NSDate *selectDate) {
                
                NSString *dateString = [selectDate stringWithFormat:@"yyyy-MM-dd HH:mm"];
                NSLog(@"选择的日期：%@",dateString);
                [btn setTitle:dateString forState:UIControlStateNormal];
            }];
            datepicker.dateLabelColor = [UIColor orangeColor];//年-月-日-时-分 颜色
            datepicker.datePickerColor = [UIColor blackColor];//滚轮日期颜色
            datepicker.headerViewColor = [UIColor orangeColor]; // 顶部视图背景颜色
            datepicker.shadeViewAlphaWhenShow = 0.3;
            datepicker.showAnimationTime = 0.4;
            [datepicker show];
```
