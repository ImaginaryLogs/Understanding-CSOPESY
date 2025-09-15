One or more threads generate data (producers) while other threads process that data (consumers). They communicate through a shared buffer/queue. 

Simplest threads.

> [!note] General Structure
> ```mermaid
> graph LR
> Producers --> Queue --> Consumers
>```

How it works:
 - Producers add items to a queue if not full
 - Consumers remove items from the queue if not empty
 - Synchronizing who gets to use the queue ensure safety.

**Benefits**:
- Decouples data generation and processing, so there is freedom of prioritization as to who gets more CPU resources.

>[!example] Web Server
>
>```mermaid
>graph LR
>
>	PC_Client[Client Requests] --> PC_Queue[Request Queue]
>	PC_Producer[Accept Thread<br/>Producer] --> PC_Queue
>	PC_Queue --> PC_Worker1[Worker Thread 1<br/>Consumer]
>	PC_Queue --> PC_Worker2[Worker Thread 2<br/>Consumer]
>	PC_Queue --> PC_Worker3[Worker Thread N<br/>Consumer]
>	PC_Worker1 --> PC_Response1[HTTP Response]
>	PC_Worker2 --> PC_Response2[HTTP Response]
>	PC_Worker3 --> PC_Response3[HTTP Response]
>	
>```
>
> A web server where one thread accepts requests and adds them to the request queue buffer. Then, a pool of workers processes them. 

# Design Considerations

Ask yourself this when choosing the design pattern:
- Do you have data generators that work at different speeds than data processors?
- Is there a natural separation between data creation and data consumption?
- Are your producers and consumers naturally independent operations?