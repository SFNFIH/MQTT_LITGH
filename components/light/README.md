# Component: Light

* 该组件将光定义为封装良好的对象。
* 灯光设备的定义为：
     * ledc定时器，用于控制光的pwm通道
     * LEDC定时器模式
     * LEDC定时器的频率
     * 灯的pwm通道数
     * LEDC定时器的位数
* 一个灯光装置可以提供：
     * iot_light_channel_regist函数将通道添加到对应的通道id
     * iot_light_duty_write函数设置相应通道的占空比，支持直接或逐步设置占空比
     * iot_light_breath_write函数设置对应通道为呼吸模式并且呼吸周期可设置
     * iot_light_blink_starte 和 iot_light_blink_stop 函数使某些通道在指定时间段内闪烁。 请注意，如果任何通道工作在闪烁模式，则所有其他通道都将关闭。

* 要使用灯光装置，您需要：
     * 创建由iot_light_create()返回的灯光对象
     * 通过iot_light_channel_regist()根据通道号注册光通道
     * 要释放对象，可以调用iot_light_delete删除按钮对象并释放内存。

### NOTE:
> 如果任何通道工作在闪烁模式，则所有其他通道将关闭。 在将任何通道设置为其他模式（写入任务或呼吸）之前，必须调用 iot_light_blink_stop()。
