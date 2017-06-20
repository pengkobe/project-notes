## login 请求流程
OnDataListener
    ^
    |(实现)
BaseActivity -->  mAsyncTaskManager  --> EventBus( 融云内部库 )
    ^
    |(继承)
LoginActivity