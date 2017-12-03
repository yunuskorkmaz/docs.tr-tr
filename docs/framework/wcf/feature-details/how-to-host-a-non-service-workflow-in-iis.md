---
title: "Nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f362562c-767d-401b-8257-916616568fd4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0abc1ac1cea6c9799c3d6bb349869b77f1d0b7c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a><span data-ttu-id="d5684-102">Nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma</span><span class="sxs-lookup"><span data-stu-id="d5684-102">How to: Host a non-service workflow in IIS</span></span>
<span data-ttu-id="d5684-103">İş akışı hizmetleri iş akışları IIS altında barındırılan / OLUŞTU.</span><span class="sxs-lookup"><span data-stu-id="d5684-103">Workflows that are not workflow services can be hosted under IIS/WAS.</span></span> <span data-ttu-id="d5684-104">Başkası tarafından yazılmış bir iş akışı barındırma gerektiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d5684-104">This is useful when you need to host a workflow written by somebody else.</span></span> <span data-ttu-id="d5684-105">Örneğin, iş akışı Tasarımcısı'nı yeniden barındırma ve kullanıcılar kendi iş akışları oluşturmak izin verirseniz.</span><span class="sxs-lookup"><span data-stu-id="d5684-105">For example, if you rehost the workflow designer and allow users to create their own workflows.</span></span>  <span data-ttu-id="d5684-106">IIS'de hizmet olmayan iş akışı barındırma işlem geri dönüştürme, boşta kapatma, sistem durumu izleme işlemi ve ileti tabanlı etkinleştirme gibi özellikleri için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5684-106">Hosting non-service workflows in IIS provides support for features like process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="d5684-107">IIS barındırılan iş akışı hizmetleri içeren <xref:System.ServiceModel.Activities.Receive> etkinlikleri ve bu IIS tarafından bir ileti alındığında etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="d5684-107">Workflow services hosted in IIS contain <xref:System.ServiceModel.Activities.Receive> activities and are activated when a message is received by IIS.</span></span> <span data-ttu-id="d5684-108">Hizmet olmayan iş akışları Mesajlaşma etkinlikleri içermez ve bir ileti göndererek varsayılan olarak devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="d5684-108">Non-service workflows do not contain messaging activities, and by default cannot be activated by sending a message.</span></span>  <span data-ttu-id="d5684-109">Öğesinden bir sınıf türetin <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> ve iş akışı örneği oluşturmak için işlemleri içeren bir hizmet sözleşmesini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="d5684-109">You must derive a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> and define a service contract that contains operations to create an instance of the workflow.</span></span> <span data-ttu-id="d5684-110">Bu konu basit bir iş akışı oluşturma, bir istemci, iş akışını etkinleştirmek için kullanabileceğiniz bir hizmet sözleşmesini tanımlama ve öğesinden bir sınıf türetme size yol gösterecektir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> istekleri oluşturma iş akışı için dinlemek için hizmet sözleşmesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5684-110">This topic will walk you through creating a simple workflow, defining a service contract a client can use to activate the workflow, and deriving a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> which uses the service contract to listen for workflow creating requests.</span></span>  
  
### <a name="create-a-simple-workflow"></a><span data-ttu-id="d5684-111">Basit bir iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5684-111">Create a simple workflow</span></span>  
  
1.  <span data-ttu-id="d5684-112">Yeni bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] boş adlı çözüm `CreationEndpointTest`.</span><span class="sxs-lookup"><span data-stu-id="d5684-112">Create a new [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] empty solution called `CreationEndpointTest`.</span></span>  
  
2.  <span data-ttu-id="d5684-113">Adlı yeni bir WCF iş akışı hizmeti uygulaması projesi eklemek `SimpleWorkflow` çözüme.</span><span class="sxs-lookup"><span data-stu-id="d5684-113">Add a new WCF Workflow Service Application project called `SimpleWorkflow` to the solution.</span></span> <span data-ttu-id="d5684-114">İş Akışı Tasarımcısı'nı açar.</span><span class="sxs-lookup"><span data-stu-id="d5684-114">The workflow designer will open.</span></span>  
  
3.  <span data-ttu-id="d5684-115">ReceiveRequest ve SendResponse etkinlikleri silin.</span><span class="sxs-lookup"><span data-stu-id="d5684-115">Delete the ReceiveRequest and SendResponse activities.</span></span> <span data-ttu-id="d5684-116">Bu etkinlikler, bir iş akışını bir iş akışı hizmeti kılan ' dir.</span><span class="sxs-lookup"><span data-stu-id="d5684-116">These activities are what makes a workflow a workflow service.</span></span> <span data-ttu-id="d5684-117">Bir iş akışı hizmeti ile çalışmayan olduğundan, artık bunları ihtiyacımız var.</span><span class="sxs-lookup"><span data-stu-id="d5684-117">Since we are not working with a workflow service, we no longer need them.</span></span>  
  
4.  <span data-ttu-id="d5684-118">DisplayName dizisi etkinliği için "Sıralı iş akışı" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d5684-118">Set the DisplayName for the sequence activity to "Sequential Workflow".</span></span>  
  
5.  <span data-ttu-id="d5684-119">Service1.xamlx Workflow1.xamlx için yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d5684-119">Rename Service1.xamlx to Workflow1.xamlx.</span></span>  
  
6.  <span data-ttu-id="d5684-120">Sıralı etkinlik dışında Tasarımcısı'nı tıklatın ve "Workflow1" için ad ve ConfigurationName özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="d5684-120">Click the designer outside of the sequence activity, and set the Name and ConfigurationName properties to "Workflow1"</span></span>  
  
7.  <span data-ttu-id="d5684-121">Sürükleme bir <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="d5684-121">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence>.</span></span> <span data-ttu-id="d5684-122"><xref:System.Activities.Statements.WriteLine> Etkinlik bulunabilir **Temelleri** araç bölümü.</span><span class="sxs-lookup"><span data-stu-id="d5684-122">The <xref:System.Activities.Statements.WriteLine> activity can be found in the **Primitives** section of the toolbox.</span></span> <span data-ttu-id="d5684-123">Ayarlama <xref:System.Activities.Statements.WriteLine.Text%2A> özelliği <xref:System.Activities.Statements.WriteLine> etkinliğe "Hello, world".</span><span class="sxs-lookup"><span data-stu-id="d5684-123">Set the <xref:System.Activities.Statements.WriteLine.Text%2A> property of the <xref:System.Activities.Statements.WriteLine> activity to "Hello, world".</span></span>  
  
     <span data-ttu-id="d5684-124">İş akışı, aşağıdaki diyagramda gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="d5684-124">The workflow should now look like the following diagram.</span></span>  
  
     <span data-ttu-id="d5684-125">![Basit bir iş akışı](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")</span><span class="sxs-lookup"><span data-stu-id="d5684-125">![A simple workflow](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")</span></span>  
  
### <a name="create-the-workflow-creation-service-contract"></a><span data-ttu-id="d5684-126">İş akışı oluşturma hizmet sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5684-126">Create the workflow creation service contract</span></span>  
  
1.  <span data-ttu-id="d5684-127">Adlı yeni bir sınıf kitaplığı proje ekleme `Shared` için `CreationEndpointTest` çözümü.</span><span class="sxs-lookup"><span data-stu-id="d5684-127">Add a new class library project called `Shared` to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="d5684-128">System.ServiceModel.dll, System.Configuration ve System.ServiceModel.Activities için bir başvuru ekleyin `Shared` projesi.</span><span class="sxs-lookup"><span data-stu-id="d5684-128">Add a reference to System.ServiceModel.dll, System.Configuration, and System.ServiceModel.Activities to the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="d5684-129">Class1.cs dosyası IWorkflowCreation.cs ve aşağıdaki kodu dosyayı yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d5684-129">Rename the Class1.cs file to IWorkflowCreation.cs and the following code to the file.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
  
    namespace Shared  
    {  
        //service contract exposed from the endpoint  
        [ServiceContract(Name = "IWorkflowCreation")]  
        public interface IWorkflowCreation  
        {  
            [OperationContract(Name = "Create")]  
            Guid Create(IDictionary<string, object> inputs);  
  
            [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
            void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
        }  
    }  
    ```  
  
     <span data-ttu-id="d5684-130">Bu sözleşme, iki işlem hem de yeni oluşturduğunuz hizmet olmayan iş akışı yeni bir örneğini oluşturmak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5684-130">This contract defines two operations both create a new instance of the non-service workflow you just created.</span></span> <span data-ttu-id="d5684-131">Bir oluşturulan örnek Kimliğine sahip yeni bir örneğini oluşturur ve diğer yeni iş akışı örneği için örnek kimliği belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d5684-131">One creates a new instance with a generated instance ID and the other allows you to specify the instance ID for the new workflow instance.</span></span>  <span data-ttu-id="d5684-132">Her iki yöntem, yeni iş akışı örneği parametreler olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d5684-132">Both methods allow you to pass in parameters to the new workflow instance.</span></span> <span data-ttu-id="d5684-133">Bu sözleşme tarafından sunulan <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> istemcilerin yeni bir hizmet olmayan iş akışı örneği oluşturmak izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="d5684-133">This contract will be exposed by the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to allow clients to create new instances of a non-service workflow.</span></span>  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a><span data-ttu-id="d5684-134">WorkflowHostingEndpoint bir sınıf türetin</span><span class="sxs-lookup"><span data-stu-id="d5684-134">Derive a class from WorkflowHostingEndpoint</span></span>  
  
1.  <span data-ttu-id="d5684-135">Adlı yeni bir sınıf ekleyin `CreationEndpoint` türetilen <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> için `Shared` projesi.</span><span class="sxs-lookup"><span data-stu-id="d5684-135">Add a new class called `CreationEndpoint` derived from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to the `Shared` project.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Globalization;  
    using System.ServiceModel;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Channels;  
  
    namespace Shared  
    {  
        public class CreationEndpoint : WorkflowHostingEndpoint  
        {  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="d5684-136">Yerel statik eklemek <xref:System.Uri> adlı değişken `defaultBaseUri` için `CreationEndpoint` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5684-136">Add a local static <xref:System.Uri> variable called `defaultBaseUri` to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  <span data-ttu-id="d5684-137">Aşağıdaki oluşturucuyu ekleyin `CreationEndpoint` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5684-137">Add the following constructor to the `CreationEndpoint` class.</span></span> <span data-ttu-id="d5684-138">Belirttiğimiz fark `IWorkflowCreation` temel oluşturucuyu çağrısında hizmet sözleşme.</span><span class="sxs-lookup"><span data-stu-id="d5684-138">Notice we specify the `IWorkflowCreation` service contract in the call to the base constructor.</span></span>  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  <span data-ttu-id="d5684-139">Aşağıdaki varsayılan oluşturucu ekleyin `CreationEndpoint` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5684-139">Add the following default constructor to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  <span data-ttu-id="d5684-140">Statik eklemek `DefaultBaseUri` özelliğine `CreationEndpoint` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5684-140">Add a static `DefaultBaseUri` property to the `CreationEndpoint` class.</span></span> <span data-ttu-id="d5684-141">Bu özellik, bir taban URI sağlanmamış varsayılan tutmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5684-141">This property will be used to hold a default base URI if one is not provided.</span></span>  
  
    ```  
    static Uri DefaultBaseUri  
    {  
       get  
       {  
          if (defaultBaseUri == null)  
          {  
             defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                Process.GetCurrentProcess().Id,  
                AppDomain.CurrentDomain.Id));  
          }  
          return defaultBaseUri;  
       }  
     }  
    ```  
  
6.  <span data-ttu-id="d5684-142">Oluşturma uç noktası için kullanılacak varsayılan bağlama almak için aşağıdaki yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5684-142">Create the following method to get the default binding to use for the creation endpoint.</span></span>  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  <span data-ttu-id="d5684-143">Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> iş akışı örneği kimliğine döndürülecek yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5684-143">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> method to return the workflow instance ID.</span></span> <span data-ttu-id="d5684-144">Varsa `Action` "Oluştur" başlığı biter, boş bir GUID dönmek `Action` üstbilgi bitip GUID yönteme geçirilen "CreateWithInstanceId" return ile.</span><span class="sxs-lookup"><span data-stu-id="d5684-144">If the `Action` header ends with "Create" return an empty GUID, if the `Action` header ends with "CreateWithInstanceId" return the GUID passed into the method.</span></span> <span data-ttu-id="d5684-145">Aksi takdirde, throw bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="d5684-145">Otherwise, throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="d5684-146">Bunlar `Action` üstbilgileri karşılık tanımlanan iki işlem `IWorkflowCreation` hizmet sözleşme.</span><span class="sxs-lookup"><span data-stu-id="d5684-146">These `Action` headers correspond to the two operations defined in the `IWorkflowCreation` service contract.</span></span>  
  
    ```  
    protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
    {  
       //Create was called by client  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
       {  
          return Guid.Empty;  
       }  
       //CreateWithInstanceId was called by client  
       else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
       {  
          return (Guid)inputs[1];  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
    }  
    ```  
  
8.  <span data-ttu-id="d5684-147">Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> yöntemi oluşturmak için bir <xref:System.ServiceModel.Activities.WorkflowCreationContext> ve iş akışı için herhangi bir bağımsız değişkeni ekleyin, örnek kimliği istemciye göndermek ve sonra geri dönüp <xref:System.ServiceModel.Activities.WorkflowCreationContext>.</span><span class="sxs-lookup"><span data-stu-id="d5684-147">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> method to create a <xref:System.ServiceModel.Activities.WorkflowCreationContext> and add any arguments for the workflow, send the instance ID to the client, and then return the <xref:System.ServiceModel.Activities.WorkflowCreationContext>.</span></span>  
  
    ```  
    protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
    {  
       WorkflowCreationContext creationContext = new WorkflowCreationContext();  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create") || (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId")))  
       {  
          Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
          if (arguments != null && arguments.Count > 0)  
          {  
             foreach (KeyValuePair<string, object> pair in arguments)  
             {  
                //arguments to pass to the workflow  
                creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
             }  
          }  
          //reply to client with instanceId  
          responseContext.SendResponse(instanceId, null);  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
       return creationContext;  
    }  
    ```  
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a><span data-ttu-id="d5684-148">WorkflowCreationEndpoint yapılandırmanıza izin vermek için bir standart endpoint öğesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5684-148">Create a standard endpoint element to allow you to configure the WorkflowCreationEndpoint</span></span>  
  
1.  <span data-ttu-id="d5684-149">İçinde paylaşılan bir başvuru ekleyin `CreationEndpoint` proje</span><span class="sxs-lookup"><span data-stu-id="d5684-149">Add a reference to Shared in the `CreationEndpoint` project</span></span>  
  
2.  <span data-ttu-id="d5684-150">Adlı yeni bir sınıf ekleyin `CreationEndpointElement`, türetilmiş <xref:System.ServiceModel.Configuration.StandardEndpointElement> için `CreationEndpoint` projesi.</span><span class="sxs-lookup"><span data-stu-id="d5684-150">Add a new class called `CreationEndpointElement`, derived from <xref:System.ServiceModel.Configuration.StandardEndpointElement> to the `CreationEndpoint` project.</span></span> <span data-ttu-id="d5684-151">Bu sınıfın temsil edecek bir `CreationEndpoint` web.config dosyasında.</span><span class="sxs-lookup"><span data-stu-id="d5684-151">This class will represent a `CreationEndpoint` in a web.config file.</span></span>  
  
    ```  
    using System;  
    using System.Configuration;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Configuration;  
    using System.ServiceModel.Description;  
    using Shared;  
  
    namespace CreationEndpointTest  
    {  
        //config element for CreationEndpoint  
        public class CreationEndpointElement : StandardEndpointElement  
        {  
       }  
    ```  
  
3.  <span data-ttu-id="d5684-152">Adlı bir özellik eklemek `EndpointType` uç nokta türünü dönün.</span><span class="sxs-lookup"><span data-stu-id="d5684-152">Add a property called `EndpointType` to return the type of the endpoint.</span></span>  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  <span data-ttu-id="d5684-153">Geçersiz kılma <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> yöntemi ve yeni bir iade `CreationEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="d5684-153">Override the <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> method and return a new `CreationEndpoint`.</span></span>  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  <span data-ttu-id="d5684-154">Aşırı yükleme <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, ve <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d5684-154">Overload the <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, and <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> methods.</span></span> <span data-ttu-id="d5684-155">Bu yöntemler tanımlanmış olması yeterlidir, bunları için herhangi bir kod eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d5684-155">These methods just need to be defined, you do not need to add any code to them.</span></span>  
  
    ```  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
    ```  
  
6.  <span data-ttu-id="d5684-156">Koleksiyon sınıfı ekleme `CreationEndpoint` CreationEndpointElement.cs dosyasında `CreationEndpoint` projesi.</span><span class="sxs-lookup"><span data-stu-id="d5684-156">Add the collection class for `CreationEndpoint` to the CreationEndpointElement.cs file in the `CreationEndpoint` project.</span></span> <span data-ttu-id="d5684-157">Bu sınıf tarafından yapılandırma bir dizi tutmak için kullanılan `CreationEndpoint` web.config dosyasında örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d5684-157">This class is used by configuration to hold a number of `CreationEndpoint` instances in a web.config file.</span></span>  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  <span data-ttu-id="d5684-158">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5684-158">Build the solution.</span></span>  
  
### <a name="host-the-workflow-in-iis"></a><span data-ttu-id="d5684-159">IIS'de iş akışı barındırma</span><span class="sxs-lookup"><span data-stu-id="d5684-159">Host the workflow in IIS</span></span>  
  
1.  <span data-ttu-id="d5684-160">Adlı yeni bir uygulama oluşturmak `MyCreationEndpoint` IIS'de.</span><span class="sxs-lookup"><span data-stu-id="d5684-160">Create a new application called `MyCreationEndpoint` in IIS.</span></span>  
  
2.  <span data-ttu-id="d5684-161">Uygulama dizini için iş akışı tasarımcısı tarafından oluşturulan workflow1.xaml dosyasını kopyalayın ve workflow1.xamlx için yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d5684-161">Copy the workflow1.xaml file generated by the workflow designer to the application directory and rename it to workflow1.xamlx.</span></span>  
  
3.  <span data-ttu-id="d5684-162">Shared.dll ve CreationEndpoint.dll dosyalarını uygulamanın bin dizinine kopyalayın (bölme dizini mevcut değilse oluşturun).</span><span class="sxs-lookup"><span data-stu-id="d5684-162">Copy the shared.dll and CreationEndpoint.dll files to the application’s bin directory (create the bin directory if it is not present).</span></span>  
  
4.  <span data-ttu-id="d5684-163">Web.config dosyasında Değiştir `CreationEndpoint` proje ile aşağıdaki kodu.</span><span class="sxs-lookup"><span data-stu-id="d5684-163">Replace the contents of the Web.config file in the `CreationEndpoint` project with the following code.</span></span>  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  <span data-ttu-id="d5684-164">Sonra `<system.web>` öğesi, kayıt `CreationEndpoint` aşağıdaki yapılandırma kodunu ekleyerek düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="d5684-164">After the `<system.web>` element, register `CreationEndpoint` by adding the following configuration code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <!--register CreationEndpoint-->  
        <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
        <extensions>  
          <endpointExtensions>  
            <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, CreationEndpoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </endpointExtensions>  
        </extensions>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="d5684-165">Bu kayıtları `CreationEndpointCollection` , yapılandırabilmek için sınıf bir `CreationEndpoint` web.config dosyasında.</span><span class="sxs-lookup"><span data-stu-id="d5684-165">This registers the `CreationEndpointCollection` class so you can configure a `CreationEndpoint` in a web.config file.</span></span>  
  
6.  <span data-ttu-id="d5684-166">Ekleme bir `<service>` öğesi (sonra \</extensions > etiketi) ile bir `CreationEndpoint` , gelen iletiler için dinleme.</span><span class="sxs-lookup"><span data-stu-id="d5684-166">Add a `<service>` element (after the \</extensions> tag) with a `CreationEndpoint` which will listen for incoming messages.</span></span>  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  <span data-ttu-id="d5684-167">Ekleme bir \<davranışları > öğesi (sonra  \< /Hizmetleri > etiketi) hizmeti meta verilerini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d5684-167">Add a \<behaviors> element (after the \</services> tag) to enable service metadata.</span></span>  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  <span data-ttu-id="d5684-168">Web.config, IIS uygulama dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d5684-168">Copy the web.config to your IIS application directory.</span></span>  
  
9. <span data-ttu-id="d5684-169">Oluşturma bitiş noktası tarafından Internet Explorer'ı başlatıp http://localhost/MyCreationEndpoint/Workflow1.xamlx için gözatma çalışıp çalışmadığını test edin.</span><span class="sxs-lookup"><span data-stu-id="d5684-169">Test to see if the creation endpoint is working by starting Internet Explorer and browsing to http://localhost/MyCreationEndpoint/Workflow1.xamlx.</span></span> <span data-ttu-id="d5684-170">Internet Explorer, aşağıdaki ekran görüntülenmelidir:</span><span class="sxs-lookup"><span data-stu-id="d5684-170">Internet Explorer should display the following screen:</span></span>  
  
     <span data-ttu-id="d5684-171">![Hizmet sınama](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span><span class="sxs-lookup"><span data-stu-id="d5684-171">![Testing the service](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span></span>  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a><span data-ttu-id="d5684-172">CreationEndpoint çağıracak bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5684-172">Create a client that will call the CreationEndpoint.</span></span>  
  
1.  <span data-ttu-id="d5684-173">Yeni bir konsol uygulaması ekleyin `CreationEndpointTest` çözümü.</span><span class="sxs-lookup"><span data-stu-id="d5684-173">Add a new Console application to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="d5684-174">System.ServiceModel.dll, System.ServiceModel.Activities, başvurular ekleyin ve `Shared` projesi.</span><span class="sxs-lookup"><span data-stu-id="d5684-174">Add references to System.ServiceModel.dll, System.ServiceModel.Activities, and the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="d5684-175">İçinde `Main` create yöntemi bir <xref:System.ServiceModel.ChannelFactory%601> türü `IWorkflowCreation` ve arama <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5684-175">In the `Main` method create a <xref:System.ServiceModel.ChannelFactory%601> of type `IWorkflowCreation` and call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.</span></span> <span data-ttu-id="d5684-176">Bu proxy döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5684-176">This will return a proxy.</span></span> <span data-ttu-id="d5684-177">Ardından çağırabilirsiniz `Create` iş akışı örneği oluşturmak için proxy üzerinde barındırılan IIS altında:</span><span class="sxs-lookup"><span data-stu-id="d5684-177">You can then call `Create` on that proxy to create the workflow instance hosted under IIS:</span></span>  
  
    ```  
    using System.Text;  
    using Shared;  
    using System.ServiceModel;  
  
    namespace CreationEndpointClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    //client using BasicHttpBinding  
                    IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/CreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                    Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                    Console.WriteLine("Press return to exit ...");  
                    Console.ReadLine();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex);  
                    Console.ReadLine();  
                }  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="d5684-178">CreationEndpointClient çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5684-178">Run the CreationEndpointClient.</span></span> <span data-ttu-id="d5684-179">Çıktı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="d5684-179">The output should look like the following:</span></span>  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d5684-180">Konsol çıktısı olan IIS altında çalıştığı için iş akışı çıktısı görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5684-180">You will not see the output of the workflow because it is running under IIS which has no console output.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5684-181">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5684-181">Example</span></span>  
 <span data-ttu-id="d5684-182">Bu örnek için tam kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d5684-182">The following is the complete code for this sample.</span></span>  
  
```xaml  
<!-— workflow1.xamlx -->  
<WorkflowService mc:Ignorable="sap"   
                 ConfigurationName="Workflow1"   
                 sap:VirtualizedContainerService.HintSize="263,230"   
                 Name="Workflow1"   
                 mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces"   
                 xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"   
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:mv="clr-namespace:Microsoft.VisualBasic;assembly=System"   
                 xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities"   
                 xmlns:p="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
                 xmlns:s="clr-namespace:System;assembly=mscorlib"   
                 xmlns:s1="clr-namespace:System;assembly=System"   
                 xmlns:s2="clr-namespace:System;assembly=System.Xml"   
                 xmlns:s3="clr-namespace:System;assembly=System.Core"   
                 xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities"   
                 xmlns:sap="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation"   
                 xmlns:scg="clr-namespace:System.Collections.Generic;assembly=System"   
                 xmlns:scg1="clr-namespace:System.Collections.Generic;assembly=System.ServiceModel"   
                 xmlns:scg2="clr-namespace:System.Collections.Generic;assembly=System.Core"   
                 xmlns:scg3="clr-namespace:System.Collections.Generic;assembly=mscorlib"   
                 xmlns:sd="clr-namespace:System.Data;assembly=System.Data"   
                 xmlns:sl="clr-namespace:System.Linq;assembly=System.Core"   
                 xmlns:st="clr-namespace:System.Text;assembly=mscorlib"   
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <p:Sequence DisplayName="Sequential Service"   
              sad:XamlDebuggerXmlReader.FileName="c:\projects\CreationEndpointTest\CreationEndpoint\Service1.xamlx"   
              sap:VirtualizedContainerService.HintSize="233,200"   
              mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces">  
    <p:Sequence.Variables>  
      <p:Variable x:TypeArguments="CorrelationHandle" Name="handle" />  
      <p:Variable x:TypeArguments="x:Int32" Name="data" />  
    </p:Sequence.Variables>  
    <sap:WorkflowViewStateService.ViewState>  
      <scg3:Dictionary x:TypeArguments="x:String, x:Object">  
        <x:Boolean x:Key="IsExpanded">True</x:Boolean>  
      </scg3:Dictionary>  
    </sap:WorkflowViewStateService.ViewState>  
    <p:WriteLine sap:VirtualizedContainerService.HintSize="211,61" Text="Hello, world" />  
  </p:Sequence>  
</WorkflowService>  
```  
  
```csharp  
// CreationEndpointElement.cs  
using System;  
using System.Configuration;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Description;  
using Shared;  
  
namespace CreationEndpointTest  
{  
    //config element for CreationEndpoint  
    public class CreationEndpointElement : StandardEndpointElement  
    {  
        protected override Type EndpointType  
        {  
            get { return typeof(CreationEndpoint); }  
        }  
  
        protected override ConfigurationPropertyCollection Properties  
        {  
            get  
            {  
                ConfigurationPropertyCollection properties = base.Properties;  
                properties.Add(new ConfigurationProperty("name", typeof(String), null, ConfigurationPropertyOptions.IsRequired));  
                return properties;  
            }  
        }  
  
        protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
        {  
            return new CreationEndpoint();  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
    }  
  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
}  
```  
  
```xml  
<!-- web.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <!--register CreationEndpoint-->  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
    <extensions>  
      <endpointExtensions>  
        <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, Shared, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <!-- add endpoint to service-->  
      <service name="Workflow1" behaviorConfiguration="basicConfig" >  
        <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="basicConfig">  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```csharp  
// IWorkflowCreation.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
  
namespace Shared  
{  
    //service contract exposed from the endpoint  
    [ServiceContract(Name = "IWorkflowCreation")]  
    public interface IWorkflowCreation  
    {  
        [OperationContract(Name = "Create")]  
        Guid Create(IDictionary<string, object> inputs);  
  
        [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
        void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
    }  
}  
```  
  
```csharp  
// CreationEndpoint.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
using System.ServiceModel;  
using System.Globalization;  
using System.Diagnostics;  
  
namespace Shared  
{  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
  
        public CreationEndpoint(Binding binding, EndpointAddress address)  
            : base(typeof(IWorkflowCreation), binding, address) { }  
  
        public CreationEndpoint()  
            : this(GetDefaultBinding(),  
                new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative)))) { }  
  
        static Uri DefaultBaseUri  
        {  
            get  
            {  
                if (defaultBaseUri == null)  
                {  
                    defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                        Process.GetCurrentProcess().Id,  
                        AppDomain.CurrentDomain.Id));  
                }  
                return defaultBaseUri;  
            }  
        }  
  
        //defaults to NetNamedPipeBinding  
        public static Binding GetDefaultBinding()  
        {  
            return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
        }  
  
        protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
        {  
            //Create was called by client  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                return Guid.Empty;  
            }  
  
            //CreateWithInstanceId was called by client  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                return (Guid)inputs[1];  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
        }  
  
        protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
        {  
            WorkflowCreationContext creationContext = new WorkflowCreationContext();  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to the workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
                //reply to client with instanceId  
                responseContext.SendResponse(instanceId, null);  
            }  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
            return creationContext;  
        }  
    }  
}  
```  
  
```csharp  
// CreationEndpointClient.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Shared;  
using System.ServiceModel;  
  
namespace CreationClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                //client using BasicHttpBinding  
                IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/MyCreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                Console.WriteLine("Press return to exit ...");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex);  
                Console.ReadLine();  
            }  
  
        }  
    }  
  
}  
```  
  
 <span data-ttu-id="d5684-183">Hiçbir zaman uygulayan bir hizmet uyguladığınız için bu örnek karmaşık görünebilir `IWorkflowCreation`.</span><span class="sxs-lookup"><span data-stu-id="d5684-183">This example may seem confusing because you never implement a service that implements `IWorkflowCreation`.</span></span> <span data-ttu-id="d5684-184">Bunun nedeni, `CreationEndpoint` bunu sizin için yapar.</span><span class="sxs-lookup"><span data-stu-id="d5684-184">This is because the `CreationEndpoint` does this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5684-185">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5684-185">See Also</span></span>  
 [<span data-ttu-id="d5684-186">İş akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d5684-186">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="d5684-187">Internet Information Services'te barındırma</span><span class="sxs-lookup"><span data-stu-id="d5684-187">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="d5684-188">Internet Information Services barındırma en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="d5684-188">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [<span data-ttu-id="d5684-189">Internet Information Service barındırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d5684-189">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [<span data-ttu-id="d5684-190">Windows iş akışı mimarisi</span><span class="sxs-lookup"><span data-stu-id="d5684-190">Windows Workflow Architecture</span></span>](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [<span data-ttu-id="d5684-191">WorkflowHostingEndpoint Sürdür yer işareti</span><span class="sxs-lookup"><span data-stu-id="d5684-191">WorkflowHostingEndpoint Resume Bookmark</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [<span data-ttu-id="d5684-192">İş Akışı Tasarımcısı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="d5684-192">Rehosting the Workflow Designer</span></span>](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="d5684-193">Windows iş akışı genel bakış</span><span class="sxs-lookup"><span data-stu-id="d5684-193">Windows Workflow Overview</span></span>](../../../../docs/framework/windows-workflow-foundation/overview.md)
