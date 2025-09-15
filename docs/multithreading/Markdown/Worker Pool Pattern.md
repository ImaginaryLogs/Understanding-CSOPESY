Very similar to the [[Producer-Consumer Pattern]] as there is a fixed N number of workers, but inputs can come from anywhere. 

This concerns mostly as to how resources are managed in a pool. You ask questions more of:
 - How many workers are needed to work on this problem?

Can be coupled with different design patterns like the [[Pipeline Pattern]]

> [!example] Web Server Thread Pool
> ```mermaid
> graph LR
> WP_Requests[HTTP Requests] --> WP_Queue[Task Queue] 
> WP_Queue --> WP_Worker1[Worker Thread 1] 
> WP_Queue --> WP_Worker2[Worker Thread 2] 
> WP_Queue --> WP_Worker3[Worker Thread 3] 
> WP_Queue --> WP_WorkerN[Worker Thread N] 
> subgraph Worker Pool
> WP_Worker1 --> WP_Response1[Response 1] 
> WP_Worker2 --> WP_Response2[Response 2] 
> WP_Worker3 --> WP_Response3[Response 3] 
> WP_WorkerN --> WP_ResponseN[Response N]
> end
> ```


