# task-scheduler
library to assist in scheduling of tasks that run on specific intervals

this is just in the planning phases, work still needs to be done

```
Base Methods
-Start() : IBaseScheduler
-Stop() : IBaseScheduler
-StopByID(Const AID:String) : IBaseScheduler
-DeleteByID(Const AID:String) : IBaseScheduler
-StopGroup(Const AName:String) : IBaseScheduler
-DeleteGroup(Const AName:String) : IBaseScheduler
-Clear : IBaseScheduler

IN
-generic T data
-method to perform
-array of const additional data
-interval in milliseconds to perform

OUT
-id (guid)
-array of guids for group

//single task could look like this
scheduler<PGDAXOrder>
  .schedule(
    LOrder,
    @MethodName,
    @OnErrorMethod, 
    @OnFinishMethod,
    [],
    200, //run method every 200 msecs
    Synchronize=False //would just be a false, but for demonstration
  )
  .schedule(
    LOrder2,
    @Method,
    @OnErrorMethod,
    @OnFinishMethod,
    [],
    400 //run method every 400 msecs
  )
  .start();

//schedule a group of stuff
scheduler<PGDAXOrder>
  .group(
    'Orders'
    scheduler<PGDAXOrder>
      .TScheduleArray.Create(
        [
          @FTest,
          @FTest2
        ]
      ),
    @Method,
    @OnErrorMethod,
    @OnFinishMethod,
    [],
    200 //run method every 200 msecs
  )
  .Start()
```
