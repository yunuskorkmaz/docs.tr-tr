---
title: Bir İş Akışı Hizmetinden OperationContext Erişimi
ms.date: 03/30/2017
ms.assetid: b1dafe55-a20e-4db0-9ac8-90c315883cdd
ms.openlocfilehash: 15dd817dddbe3272b188f6b74697f8c5839d498b
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540758"
---
# <a name="accessing-operationcontext-from-a-workflow-service"></a><span data-ttu-id="6b282-102">Bir İş Akışı Hizmetinden OperationContext Erişimi</span><span class="sxs-lookup"><span data-stu-id="6b282-102">Accessing OperationContext from a Workflow Service</span></span>
<span data-ttu-id="6b282-103">Erişim için <xref:System.ServiceModel.OperationContext> bir iş akışı hizmeti içinde uygulamanız gereken <xref:System.ServiceModel.Activities.IReceiveMessageCallback> özel yürütme özelliğinde arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6b282-103">To access the <xref:System.ServiceModel.OperationContext> inside a workflow service, you must implement the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> interface in a custom execution property.</span></span> <span data-ttu-id="6b282-104">Geçersiz kılma <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> başvuru geçirilen yöntemi <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="6b282-104">Override the <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> method which is passed a reference to the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="6b282-105">Bu konuda, bu özelliğe belirir özel bir etkinlik yanı sıra, bir özel üst bilgi almak için bu yürütme özelliğini uygulama konusunda size yol gösterecek <xref:System.ServiceModel.Activities.Receive> zamanında.</span><span class="sxs-lookup"><span data-stu-id="6b282-105">This topic will walk you through implementing this execution property to retrieve a custom header, as well as a custom activity that will surface this property to the <xref:System.ServiceModel.Activities.Receive> at runtime.</span></span>  <span data-ttu-id="6b282-106">Özel Etkinlik aynı davranışı uygulayan bir <xref:System.Activities.Statements.Sequence> olduğunda dışında bir etkinlik bir <xref:System.ServiceModel.Activities.Receive> bunun içinde yerleştirilir <xref:System.ServiceModel.Activities.IReceiveMessageCallback> olarak adlandırılır ve <xref:System.ServiceModel.OperationContext> bilgiler alınabilir.</span><span class="sxs-lookup"><span data-stu-id="6b282-106">The custom activity will implement the same behavior as a <xref:System.Activities.Statements.Sequence> activity, except that when a <xref:System.ServiceModel.Activities.Receive> is placed inside of it, the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> will be called and the <xref:System.ServiceModel.OperationContext> information will be retrieved.</span></span>  <span data-ttu-id="6b282-107">Bu konuda ayrıca istemci-tarafı erişmek nasıl gösterir <xref:System.ServiceModel.OperationContext> aracılığıyla giden üst bilgilerini eklemek için <xref:System.ServiceModel.Activities.ISendMessageCallback> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6b282-107">This topic also shows how to access the client-side <xref:System.ServiceModel.OperationContext> to add outgoing headers via the <xref:System.ServiceModel.Activities.ISendMessageCallback> interface.</span></span>  
  
### <a name="implement-the-service-side-ireceivemessagecallback"></a><span data-ttu-id="6b282-108">Hizmet tarafı IReceiveMessageCallback uygulayın</span><span class="sxs-lookup"><span data-stu-id="6b282-108">Implement the Service-side IReceiveMessageCallback</span></span>  
  
1.  <span data-ttu-id="6b282-109">Boş bir oluşturma [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] çözüm.</span><span class="sxs-lookup"><span data-stu-id="6b282-109">Create an empty [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solution.</span></span>  
  
2.  <span data-ttu-id="6b282-110">Adlı yeni bir konsol uygulaması Ekle `Service` çözüm.</span><span class="sxs-lookup"><span data-stu-id="6b282-110">Add a new console application called `Service` to the solution.</span></span>  
  
3.  <span data-ttu-id="6b282-111">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6b282-111">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="6b282-112">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="6b282-112">System.Runtime.Serialization</span></span>  
  
    2.  <span data-ttu-id="6b282-113">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6b282-113">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="6b282-114">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="6b282-114">System.ServiceModel.Activities</span></span>  
  
4.  <span data-ttu-id="6b282-115">Adlı yeni bir sınıf ekleyin `ReceiveInstanceIdCallback` ve uygulama <xref:System.ServiceModel.Activities.IReceiveMessageCallback> aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="6b282-115">Add a new class called `ReceiveInstanceIdCallback` and implement <xref:System.ServiceModel.Activities.IReceiveMessageCallback> as shown in the following example.</span></span>  
  
    ```csharp  
    class ReceiveInstanceIdCallback : IReceiveMessageCallback  
    {  
          public const string HeaderName = "InstanceIdHeader";  
          public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
         public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
          {              
                try  
                {  
                    Guid instanceId = operationContext.IncomingMessageHeaders.GetHeader<Guid>(HeaderName, HeaderNS);  
                    Console.WriteLine("Received a message from a workflow with instanceId = {0}", instanceId);  
                }  
                catch (MessageHeaderException)  
                {  
                    Console.WriteLine("This message must not be from a workflow.");  
                }  
            }  
    }  
    ```  
  
     <span data-ttu-id="6b282-116">Bu kod <xref:System.ServiceModel.OperationContext> gelen ileti üstbilgileri erişmek için metodun Metoda geçilen.</span><span class="sxs-lookup"><span data-stu-id="6b282-116">This code uses the <xref:System.ServiceModel.OperationContext> passed into the method to access the incoming message’s headers.</span></span>  
  
### <a name="implement-a-service-side-native-activity-to-add-the-ireceivemessagecallback-implementation-to-the-nativeactivitycontext"></a><span data-ttu-id="6b282-117">İçin NativeActivityContext IReceiveMessageCallback uygulama eklemek için bir hizmet tarafı yerel etkinlik uygulayan</span><span class="sxs-lookup"><span data-stu-id="6b282-117">Implement a Service-side Native activity to add the IReceiveMessageCallback implementation to the NativeActivityContext</span></span>  
  
1.  <span data-ttu-id="6b282-118">Türetilen bir yeni sınıf ekleyin <xref:System.Activities.NativeActivity> adlı `ReceiveInstanceIdScope`.</span><span class="sxs-lookup"><span data-stu-id="6b282-118">Add a new class derived from <xref:System.Activities.NativeActivity> called `ReceiveInstanceIdScope`.</span></span>  
  
2.  <span data-ttu-id="6b282-119">Alt etkinlikleri, değişkenleri, geçerli etkinlik dizini izlemek için yerel değişkeni ekleyin ve bir <xref:System.Activities.CompletionCallback> geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="6b282-119">Add local variables to keep track of child activities, variables, current activity index, and a <xref:System.Activities.CompletionCallback> callback.</span></span>  
  
    ```  
    public sealed class ReceiveInstanceIdScope : NativeActivity  
        {  
            Collection<Activity> children;  
            Collection<Variable> variables;  
            Variable<int> currentIndex;  
            CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  <span data-ttu-id="6b282-120">Uygulama Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="6b282-120">Implement the constructor</span></span>  
  
    ```  
    public ReceiveInstanceIdScope()  
                : base()  
            {  
                this.children = new Collection<Activity>();  
                this.variables = new Collection<Variable>();  
                this.currentIndex = new Variable<int>();  
            }  
    }  
    ```  
  
4.  <span data-ttu-id="6b282-121">Uygulama `Activities` ve `Variables` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6b282-121">Implement the `Activities` and `Variables` properties.</span></span>  
  
    ```  
    public Collection<Activity> Activities  
    {  
         get { return this.children; }  
    }  
  
    public Collection<Variable> Variables  
    {  
        get { return this.variables; }  
    }  
    ```  
  
5.  <span data-ttu-id="6b282-122">geçersiz kılma <xref:System.Activities.NativeActivity.CacheMetadata%2A></span><span class="sxs-lookup"><span data-stu-id="6b282-122">Override <xref:System.Activities.NativeActivity.CacheMetadata%2A></span></span>  
  
    ```  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  <span data-ttu-id="6b282-123">geçersiz kılma <xref:System.Activities.NativeActivity.Execute%2A></span><span class="sxs-lookup"><span data-stu-id="6b282-123">Override <xref:System.Activities.NativeActivity.Execute%2A></span></span>  
  
    ```  
    protected override void Execute(  
                NativeActivityContext context)  
            {  
                context.Properties.Add("ReceiveInstanceIdCallback", new ReceiveInstanceIdCallback());  
                InternalExecute(context, null);  
            }  
  
            void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
            {  
                //grab the index of the current Activity  
                int currentActivityIndex = this.currentIndex.Get(context);  
                if (currentActivityIndex == Activities.Count)  
                {  
                    //if the currentActivityIndex is equal to the count of MySequence's Activities  
                    //MySequence is complete  
                    return;  
                }  
  
                if (this.onChildComplete == null)  
                {  
                    //on completion of the current child, have the runtime call back on this method  
                    this.onChildComplete = new CompletionCallback(InternalExecute);  
                }  
  
                //grab the next Activity in MySequence.Activities and schedule it  
                Activity nextChild = Activities[currentActivityIndex];  
                context.ScheduleActivity(nextChild, this.onChildComplete);  
  
                //increment the currentIndex  
                this.currentIndex.Set(context, ++currentActivityIndex);  
            }  
    ```  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="6b282-124">Bir iş akışı hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="6b282-124">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="6b282-125">Varolan öğeyi `Program` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6b282-125">Open the existing `Program` class.</span></span>  
  
2.  <span data-ttu-id="6b282-126">Aşağıdaki sabitler tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="6b282-126">Define the following constants:</span></span>  
  
    ```  
    class Program  
    {  
       const string addr = "http://localhost:8080/Service";  
       static XName contract = XName.Get("IService", "http://tempuri.org");  
    }  
    ```  
  
3.  <span data-ttu-id="6b282-127">Adlı statik bir yöntem ekleyin `GetWorkflowService` iş akışı hizmeti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b282-127">Add a static method called `GetWorkflowService` that creates the workflow service.</span></span>  
  
    ```  
    static Activity GetServiceWorkflow()  
            {  
                Variable<string> echoString = new Variable<string>();  
  
                Receive echoRequest = new Receive  
                {  
                    CanCreateInstance = true,  
                    ServiceContractName = contract,  
                    OperationName = "Echo",  
                    Content = new ReceiveParametersContent()  
                    {  
                        Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
                    }  
                };  
  
                return new ReceiveInstanceIdScope  
                {  
                    Variables = { echoString },  
                    Activities =  
                    {  
                        echoRequest,  
                        new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
                        new SendReply  
                        {  
                            Request = echoRequest,  
                            Content = new SendParametersContent()  
                            {  
                                Parameters = { { "result", new InArgument<string>(echoString) } }   
                            }  
                        }  
                    }  
                };  
            }  
    ```  
  
4.  <span data-ttu-id="6b282-128">Mevcut `Main` yöntemi, iş akışı hizmeti konağı.</span><span class="sxs-lookup"><span data-stu-id="6b282-128">In the existing `Main` method, host the workflow service.</span></span>  
  
    ```  
    static void Main(string[] args)  
            {  
                string addr = "http://localhost:8080/Service";  
  
                using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
                {  
                    host.AddServiceEndpoint(contract, new BasicHttpBinding(), addr);  
  
                    host.Open();  
                    Console.WriteLine("Service waiting at: " + addr);  
                    Console.WriteLine("Press [ENTER] to exit");  
                    Console.ReadLine();  
                    host.Close();  
                }  
            }  
    ```  
  
### <a name="implement-the-client-side-isendmessagecallback"></a><span data-ttu-id="6b282-129">İstemci tarafı ISendMessageCallback uygulayın</span><span class="sxs-lookup"><span data-stu-id="6b282-129">Implement the Client-side ISendMessageCallback</span></span>  
  
1.  <span data-ttu-id="6b282-130">Adlı yeni bir konsol uygulaması Ekle `Service` çözüm.</span><span class="sxs-lookup"><span data-stu-id="6b282-130">Add a new console application called `Service` to the solution.</span></span>  
  
2.  <span data-ttu-id="6b282-131">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6b282-131">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="6b282-132">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="6b282-132">System.Runtime.Serialization</span></span>  
  
    2.  <span data-ttu-id="6b282-133">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6b282-133">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="6b282-134">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="6b282-134">System.ServiceModel.Activities</span></span>  
  
3.  <span data-ttu-id="6b282-135">Adlı yeni bir sınıf ekleyin `SendInstanceIdCallback` ve uygulama <xref:System.ServiceModel.Activities.ISendMessageCallback> aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="6b282-135">Add a new class called `SendInstanceIdCallback` and implement <xref:System.ServiceModel.Activities.ISendMessageCallback> as shown in the following example.</span></span>  
  
    ```csharp  
    class SendInstanceIdCallback : ISendMessageCallback  
        {  
            public const string HeaderName = "InstanceIdHeader";  
            public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
            public Guid InstanceId { get; set; }  
  
            public void OnSendMessage(System.ServiceModel.OperationContext operationContext)  
            {  
                operationContext.OutgoingMessageHeaders.Add(MessageHeader.CreateHeader(HeaderName, HeaderNS, this.InstanceId));  
            }  
        }  
    ```  
  
     <span data-ttu-id="6b282-136">Bu kod <xref:System.ServiceModel.OperationContext> gelen iletiyi özel bir başlık eklemek için yöntemini yöntemlere geçirilen.</span><span class="sxs-lookup"><span data-stu-id="6b282-136">This code uses the <xref:System.ServiceModel.OperationContext> passed into the method to add a custom header to the incoming message.</span></span>  
  
### <a name="implement-a-client-side-native-activity-to-add-the-client-side-isendmessagecallback-implementation-to-the-nativeactivitycontext"></a><span data-ttu-id="6b282-137">İstemci-tarafı ISendMessageCallback uygulaması için NativeActivityContext eklemek için bir istemci-tarafı yerel etkinlik uygulayan</span><span class="sxs-lookup"><span data-stu-id="6b282-137">Implement a Client-side Native activity to add the client-side ISendMessageCallback implementation to the NativeActivityContext</span></span>  
  
1.  <span data-ttu-id="6b282-138">Türetilen bir yeni sınıf ekleyin <xref:System.Activities.NativeActivity> adlı `SendInstanceIdScope`.</span><span class="sxs-lookup"><span data-stu-id="6b282-138">Add a new class derived from <xref:System.Activities.NativeActivity> called `SendInstanceIdScope`.</span></span>  
  
2.  <span data-ttu-id="6b282-139">Alt etkinlikleri, değişkenleri, geçerli etkinlik dizini izlemek için yerel değişkeni ekleyin ve bir <xref:System.Activities.CompletionCallback> geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="6b282-139">Add local variables to keep track of child activities, variables, current activity index, and a <xref:System.Activities.CompletionCallback> callback.</span></span>  
  
    ```  
    public sealed class SendInstanceIdScope : NativeActivity  
        {  
            Collection<Activity> children;  
            Collection<Variable> variables;  
            Variable<int> currentIndex;  
            CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  <span data-ttu-id="6b282-140">Uygulama Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="6b282-140">Implement the constructor</span></span>  
  
    ```  
    public SendInstanceIdScope()  
                : base()  
            {  
                this.children = new Collection<Activity>();  
                this.variables = new Collection<Variable>();  
                this.currentIndex = new Variable<int>();  
            }  
    ```  
  
4.  <span data-ttu-id="6b282-141">Uygulama `Activities` ve `Variables` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6b282-141">Implement the `Activities` and `Variables` properties.</span></span>  
  
    ```  
    public Collection<Activity> Activities  
    {  
         get { return this.children; }  
    }  
  
    public Collection<Variable> Variables  
    {  
        get { return this.variables; }  
    }  
    ```  
  
5.  <span data-ttu-id="6b282-142">geçersiz kılma <xref:System.Activities.NativeActivity.CacheMetadata%2A></span><span class="sxs-lookup"><span data-stu-id="6b282-142">Override <xref:System.Activities.NativeActivity.CacheMetadata%2A></span></span>  
  
    ```  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  <span data-ttu-id="6b282-143">geçersiz kılma <xref:System.Activities.NativeActivity.Execute%2A></span><span class="sxs-lookup"><span data-stu-id="6b282-143">Override <xref:System.Activities.NativeActivity.Execute%2A></span></span>  
  
    ```  
    protected override void Execute(  
                NativeActivityContext context)  
            {  
                context.Properties.Add("SendInstanceIdCallback", new SendInstanceIdCallback() { InstanceId = context.WorkflowInstanceId });  
                InternalExecute(context, null);  
            }  
  
            void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
            {  
                //grab the index of the current Activity  
                int currentActivityIndex = this.currentIndex.Get(context);  
                if (currentActivityIndex == Activities.Count)  
                {  
                    //if the currentActivityIndex is equal to the count of MySequence's Activities  
                    //MySequence is complete  
                    return;  
                }  
  
                if (this.onChildComplete == null)  
                {  
                    //on completion of the current child, have the runtime call back on this method  
                    this.onChildComplete = new CompletionCallback(InternalExecute);  
                }  
  
                //grab the next Activity in MySequence.Activities and schedule it  
                Activity nextChild = Activities[currentActivityIndex];  
                context.ScheduleActivity(nextChild, this.onChildComplete);  
  
                //increment the currentIndex  
                this.currentIndex.Set(context, ++currentActivityIndex);  
            }  
    protected override void Execute(  
                NativeActivityContext context)  
            {  
                context.Properties.Add("ReceiveInstanceIdCallback", new ReceiveInstanceIdCallback());  
                InternalExecute(context, null);  
            }  
  
            void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
            {  
                //grab the index of the current Activity  
                int currentActivityIndex = this.currentIndex.Get(context);  
                if (currentActivityIndex == Activities.Count)  
                {  
                    //if the currentActivityIndex is equal to the count of MySequence's Activities  
                    //MySequence is complete  
                    return;  
                }  
  
                if (this.onChildComplete == null)  
                {  
                    //on completion of the current child, have the runtime call back on this method  
                    this.onChildComplete = new CompletionCallback(InternalExecute);  
                }  
  
                //grab the next Activity in MySequence.Activities and schedule it  
                Activity nextChild = Activities[currentActivityIndex];  
                context.ScheduleActivity(nextChild, this.onChildComplete);  
  
                //increment the currentIndex  
                this.currentIndex.Set(context, ++currentActivityIndex);  
            }  
    ```  
  
### <a name="implement-a-workflow-client"></a><span data-ttu-id="6b282-144">İş akışı istemcisini uygulama</span><span class="sxs-lookup"><span data-stu-id="6b282-144">Implement a workflow client</span></span>  
  
1.  <span data-ttu-id="6b282-145">Adlı yeni bir konsol uygulama projesi oluşturma `Client`.</span><span class="sxs-lookup"><span data-stu-id="6b282-145">Create a new console application project called `Client`.</span></span>  
  
2.  <span data-ttu-id="6b282-146">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6b282-146">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="6b282-147">System.Activities</span><span class="sxs-lookup"><span data-stu-id="6b282-147">System.Activities</span></span>  
  
    2.  <span data-ttu-id="6b282-148">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6b282-148">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="6b282-149">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="6b282-149">System.ServiceModel.Activities</span></span>  
  
3.  <span data-ttu-id="6b282-150">Oluşturulan Program.cs dosyasını açın ve adlı statik bir yöntem ekleyin `GetClientWorkflow` istemci iş akışı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6b282-150">Open the generated Program.cs file and add a static method called `GetClientWorkflow` to create the client workflow.</span></span>  
  
    ```  
    static Activity GetClientWorkflow()  
            {  
                Variable<string> echoString = new Variable<string>();  
  
                // Define the endpoint  
                Endpoint clientEndpoint = new Endpoint  
                {  
                    Binding = new BasicHttpBinding(),  
                    AddressUri = new Uri("http://localhost:8080/Service")  
                };  
  
                // Configure the Send activity used to send a message  
                Send echoRequest = new Send  
                {  
                    Endpoint = clientEndpoint,  
                    ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
                    OperationName = "Echo",  
                    Content = new SendParametersContent()  
                    {  
                        Parameters = { { "echoString", new InArgument<string>("Hello, World") } }   
                    }  
                };  
  
                // Place the Send activity in a SendInstanceIdScope. This hooks up the ISendMessageCallback   
                // implementation to the client workflow.  
                return new SendInstanceIdScope  
                {  
                    Variables = { echoString },  
                    Activities =  
                    {                      
                        new CorrelationScope  
                        {  
                            Body = new Sequence  
                            {  
                                Activities =   
                                {  
                                    // Send the request message  
                                    echoRequest,  
  
                                   // Receive the reply from the service  
                                    new ReceiveReply  
                                    {  
                                        Request = echoRequest,  
                                        Content = new ReceiveParametersContent  
                                        {  
                                            Parameters = { { "result", new OutArgument<string>(echoString) } }  
                                        }  
                                    }  
                                }  
                            }  
                        },                      
                        new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },                      
                    }  
                };  
            }  
    ```  
  
4.  <span data-ttu-id="6b282-151">Barındırma için aşağıdaki kodu ekleyin `Main()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6b282-151">Add the following hosting code to the `Main()` method.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
       Activity workflow = GetClientWorkflow();  
       WorkflowInvoker.Invoke(workflow);  
       WorkflowInvoker.Invoke(workflow);  
       Console.WriteLine("Press [ENTER] to exit");  
       Console.ReadLine();  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="6b282-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b282-152">Example</span></span>  
 <span data-ttu-id="6b282-153">Kaynak tam bir listesi aşağıdadır. Bu konuda kullanılan kod.</span><span class="sxs-lookup"><span data-stu-id="6b282-153">Here is a complete listing of the source code used in this topic.</span></span>  
  
```  
// ReceiveInstanceIdScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System.Activities;  
using System.Collections.ObjectModel;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    public sealed class ReceiveInstanceIdScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
  
        public ReceiveInstanceIdScope()  
            : base()  
        {  
            this.children = new Collection<Activity>();  
            this.variables = new Collection<Variable>();  
            this.currentIndex = new Variable<int>();  
        }  
  
        public Collection<Activity> Activities  
        {  
            get  
            {  
                return this.children;  
            }  
        }  
  
        public Collection<Variable> Variables  
        {  
            get  
            {  
                return this.variables;  
            }  
        }  
  
        protected override void CacheMetadata(NativeActivityMetadata metadata)  
        {  
            //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
            base.CacheMetadata(metadata);  
            //add the private implementation variable: currentIndex   
            metadata.AddImplementationVariable(this.currentIndex);  
        }                     
  
        protected override void Execute(  
            NativeActivityContext context)  
        {  
            context.Properties.Add("ReceiveInstanceIdCallback", new ReceiveInstanceIdCallback());  
            InternalExecute(context, null);  
        }  
  
        void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
        {  
            //grab the index of the current Activity  
            int currentActivityIndex = this.currentIndex.Get(context);  
            if (currentActivityIndex == Activities.Count)  
            {  
                //if the currentActivityIndex is equal to the count of MySequence's Activities  
                //MySequence is complete  
                return;  
            }  
  
            if (this.onChildComplete == null)  
            {  
                //on completion of the current child, have the runtime call back on this method  
                this.onChildComplete = new CompletionCallback(InternalExecute);  
            }  
  
            //grab the next Activity in MySequence.Activities and schedule it  
            Activity nextChild = Activities[currentActivityIndex];  
            context.ScheduleActivity(nextChild, this.onChildComplete);  
  
            //increment the currentIndex  
            this.currentIndex.Set(context, ++currentActivityIndex);  
        }  
    }  
}  
```  
  
```  
// ReceiveInstanceIdScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    class ReceiveInstanceIdCallback : IReceiveMessageCallback  
    {  
        public const string HeaderName = "InstanceIdHeader";  
        public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
        public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
        {              
            try  
            {  
                Guid instanceId = operationContext.IncomingMessageHeaders.GetHeader<Guid>(HeaderName, HeaderNS);  
                Console.WriteLine("Received a message from a workflow with instanceId = {0}", instanceId);  
            }  
            catch (MessageHeaderException)  
            {  
                Console.WriteLine("This message must not be from a workflow.");  
            }  
        }  
    }  
}  
```  
  
```  
// Service.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{      
    class Program  
    {  
        const string addr = "http://localhost:8080/Service";  
        static XName contract = XName.Get("IService", "http://tempuri.org");  
  
        static void Main(string[] args)  
        {  
            string addr = "http://localhost:8080/Service";  
  
            using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
            {  
                host.AddServiceEndpoint(contract, new BasicHttpBinding(), addr);  
  
                host.Open();  
                Console.WriteLine("Service waiting at: " + addr);  
                Console.WriteLine("Press [ENTER] to exit");  
                Console.ReadLine();  
                host.Close();  
            }  
  
        }  
  
        static Activity GetServiceWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Receive echoRequest = new Receive  
            {  
                CanCreateInstance = true,  
                ServiceContractName = contract,  
                OperationName = "Echo",  
                Content = new ReceiveParametersContent()  
                {  
                    Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
                }  
            };  
  
            return new ReceiveInstanceIdScope  
            {  
                Variables = { echoString },  
                Activities =  
                {  
                    echoRequest,  
                    new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
                    new SendReply  
                    {  
                        Request = echoRequest,  
                        Content = new SendParametersContent()  
                        {  
                            Parameters = { { "result", new InArgument<string>(echoString) } }   
                        }  
                    }  
                }  
            };  
        }  
    }  
  
}  
```  
  
```  
// SendInstanceIdCallback.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    class SendInstanceIdCallback : ISendMessageCallback  
    {  
        public const string HeaderName = "InstanceIdHeader";  
        public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
        public Guid InstanceId { get; set; }  
  
        public void OnSendMessage(System.ServiceModel.OperationContext operationContext)  
        {  
            operationContext.OutgoingMessageHeaders.Add(MessageHeader.CreateHeader(HeaderName, HeaderNS, this.InstanceId));  
        }  
    }  
}  
```  
  
```  
// SendInstanceIdScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System.Activities;  
using System.Collections.ObjectModel;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    public sealed class SendInstanceIdScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
  
        public SendInstanceIdScope()  
            : base()  
        {  
            this.children = new Collection<Activity>();  
            this.variables = new Collection<Variable>();  
            this.currentIndex = new Variable<int>();  
        }  
  
        public Collection<Activity> Activities  
        {  
            get  
            {  
                return this.children;  
            }  
        }  
  
        public Collection<Variable> Variables  
        {  
            get  
            {  
                return this.variables;  
            }  
        }  
  
        protected override void CacheMetadata(NativeActivityMetadata metadata)  
        {  
            //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
            base.CacheMetadata(metadata);  
            //add the private implementation variable: currentIndex   
            metadata.AddImplementationVariable(this.currentIndex);  
        }  
  
        protected override void Execute(  
            NativeActivityContext context)  
        {  
            context.Properties.Add("SendInstanceIdCallback", new SendInstanceIdCallback() { InstanceId = context.WorkflowInstanceId });  
            InternalExecute(context, null);  
        }  
  
        void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
        {  
            //grab the index of the current Activity  
            int currentActivityIndex = this.currentIndex.Get(context);  
            if (currentActivityIndex == Activities.Count)  
            {  
                //if the currentActivityIndex is equal to the count of MySequence's Activities  
                //MySequence is complete  
                return;  
            }  
  
            if (this.onChildComplete == null)  
            {  
                //on completion of the current child, have the runtime call back on this method  
                this.onChildComplete = new CompletionCallback(InternalExecute);  
            }  
  
            //grab the next Activity in MySequence.Activities and schedule it  
            Activity nextChild = Activities[currentActivityIndex];  
            context.ScheduleActivity(nextChild, this.onChildComplete);  
  
            //increment the currentIndex  
            this.currentIndex.Set(context, ++currentActivityIndex);  
        }  
    }  
}  
```  
  
```  
// Client.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Activity workflow = GetClientWorkflow();  
            WorkflowInvoker.Invoke(workflow);  
            WorkflowInvoker.Invoke(workflow);  
            Console.WriteLine("Press [ENTER] to exit");  
            Console.ReadLine();  
        }  
  
        static Activity GetClientWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Endpoint clientEndpoint = new Endpoint  
            {  
                Binding = new BasicHttpBinding(),  
                AddressUri = new Uri("http://localhost:8080/Service")  
            };  
  
            Send echoRequest = new Send  
            {  
                Endpoint = clientEndpoint,  
                ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
                OperationName = "Echo",  
                Content = new SendParametersContent()  
                {  
                    Parameters = { { "echoString", new InArgument<string>("Hello, World") } }   
                }  
            };  
  
            return new SendInstanceIdScope  
            {  
                Variables = { echoString },  
                Activities =  
                {                      
                    new CorrelationScope  
                    {  
                        Body = new Sequence  
                        {  
                            Activities =   
                            {  
                                echoRequest,  
                                new ReceiveReply  
                                {  
                                    Request = echoRequest,  
                                    Content = new ReceiveParametersContent  
                                    {  
                                        Parameters = { { "result", new OutArgument<string>(echoString) } }  
                                    }  
                                }  
                            }  
                        }  
                    },                      
                    new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },                      
                }  
            };  
        }  
    }  
}  
```  
  
 <span data-ttu-id="6b282-154">İsteğe bağlı yorumlar.</span><span class="sxs-lookup"><span data-stu-id="6b282-154">Optional comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b282-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b282-155">See Also</span></span>  
 [<span data-ttu-id="6b282-156">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6b282-156">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="6b282-157">OperationContext Erişimi</span><span class="sxs-lookup"><span data-stu-id="6b282-157">Accessing OperationContext</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/accessing-operationcontext.md)  
 [<span data-ttu-id="6b282-158">Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma</span><span class="sxs-lookup"><span data-stu-id="6b282-158">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)
