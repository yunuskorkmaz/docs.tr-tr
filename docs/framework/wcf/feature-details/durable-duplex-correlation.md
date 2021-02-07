---
description: 'Daha fazla bilgi edinin: dayanıklı çift yönlü bağıntı'
title: Dayanıklı Çift Yönlü Bağıntı
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: e30356e03ccb6f8fae7ca735d2ad674bbe2a191d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704959"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="31455-103">Dayanıklı Çift Yönlü Bağıntı</span><span class="sxs-lookup"><span data-stu-id="31455-103">Durable Duplex Correlation</span></span>

<span data-ttu-id="31455-104">Geri arama bağıntısı olarak da bilinen dayanıklı çift yönlü bağıntı, bir iş akışı hizmeti ilk arayana geri çağrı göndermek için bir gereksinime sahip olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="31455-104">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="31455-105">WCF çift yönlü olarak, geri çağırma gelecekte herhangi bir zamanda gerçekleşebilir ve aynı kanala veya kanal ömrüne bağlı değildir; Tek gereksinim, çağıranın geri çağırma iletisini dinleyen etkin bir uç noktaya sahip olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="31455-105">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="31455-106">Bu, iki iş akışı hizmetinin uzun süre çalışan bir konuşmada iletişim kurmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="31455-106">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="31455-107">Bu konu, dayanıklı çift yönlü bağıntı için bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="31455-107">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="31455-108">Dayanıklı çift yönlü bağıntı kullanma</span><span class="sxs-lookup"><span data-stu-id="31455-108">Using Durable Duplex Correlation</span></span>  

 <span data-ttu-id="31455-109">Dayanıklı çift yönlü bağıntı kullanmak için, iki hizmetin, veya gibi iki yönlü işlemleri destekleyen bir bağlam özellikli bağlama kullanması gerekir <xref:System.ServiceModel.NetTcpContextBinding> <xref:System.ServiceModel.WSHttpContextBinding> .</span><span class="sxs-lookup"><span data-stu-id="31455-109">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="31455-110">Çağıran hizmet, <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> istemci üzerindeki istenen bağlamayı kaydeder <xref:System.ServiceModel.Endpoint> .</span><span class="sxs-lookup"><span data-stu-id="31455-110">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="31455-111">Alıcı hizmeti, bu verileri ilk çağrıda alır ve ardından <xref:System.ServiceModel.Endpoint> , <xref:System.ServiceModel.Activities.Send> çağıran hizmete geri çağrı yapan etkinliğin kendi öğesinde kullanır.</span><span class="sxs-lookup"><span data-stu-id="31455-111">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="31455-112">Bu örnekte, iki hizmet birbirleriyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="31455-112">In this example, two services communicate with each other.</span></span> <span data-ttu-id="31455-113">İlk hizmet ikinci hizmette bir yöntemi çağırır ve sonra bir yanıt bekler.</span><span class="sxs-lookup"><span data-stu-id="31455-113">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="31455-114">İkinci hizmet geri arama yönteminin adını bilir, ancak bu yöntemi uygulayan hizmetin uç noktası tasarım zamanında bilinmez.</span><span class="sxs-lookup"><span data-stu-id="31455-114">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31455-115">Dayanıklı çift yönlü yalnızca <xref:System.ServiceModel.Channels.AddressingVersion> uç noktanın ile yapılandırıldığı durumlarda kullanılabilir <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A> .</span><span class="sxs-lookup"><span data-stu-id="31455-115">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="31455-116">Aksi takdirde, <xref:System.InvalidOperationException> aşağıdaki iletiyle bir özel durum oluşturulur: "Ileti [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing)için uç nokta başvurusuna sahip bir geri çağırma bağlamı üst bilgisi içerir.</span><span class="sxs-lookup"><span data-stu-id="31455-116">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="31455-117">Geri çağırma bağlamı yalnızca AddressingVersion ' WSAddressing10 ' ile yapılandırıldığında aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="31455-117">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="31455-118">Aşağıdaki örnekte, kullanarak bir geri çağırma oluşturan bir iş akışı hizmeti barındırılır <xref:System.ServiceModel.Endpoint> <xref:System.ServiceModel.WSHttpContextBinding> .</span><span class="sxs-lookup"><span data-stu-id="31455-118">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 <span data-ttu-id="31455-119">Bu iş akışı hizmetini uygulayan iş akışı, geri çağırma bağıntısını <xref:System.ServiceModel.Activities.Send> etkinliğiyle başlatır ve <xref:System.ServiceModel.Activities.Receive> ile ilişkili etkinlikten bu geri çağırma uç noktasına başvurur <xref:System.ServiceModel.Activities.Send> .</span><span class="sxs-lookup"><span data-stu-id="31455-119">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="31455-120">Aşağıdaki örnek, yönteminden döndürülen iş akışını temsil eder `GetWF1` .</span><span class="sxs-lookup"><span data-stu-id="31455-120">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="31455-121">İkinci iş akışı hizmeti, sistem tarafından sağlanmış, bağlam tabanlı bağlama kullanılarak barındırılır.</span><span class="sxs-lookup"><span data-stu-id="31455-121">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 <span data-ttu-id="31455-122">Bu iş akışı hizmetini uygulayan iş akışı bir etkinlikle başlar <xref:System.ServiceModel.Activities.Receive> .</span><span class="sxs-lookup"><span data-stu-id="31455-122">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="31455-123">Bu alma etkinliği, bu hizmet için geri çağırma bağıntısını başlatır, uzun süredir çalışan çalışmanın benzetimini yapmak için bir süre gecikmesini sağlar ve ardından hizmete ilk çağrıda geçirilen geri çağırma bağlamını kullanarak ilk hizmete geri çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="31455-123">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="31455-124">Aşağıdaki örnek, bir çağrısından döndürülen iş akışını temsil eder `GetWF2` .</span><span class="sxs-lookup"><span data-stu-id="31455-124">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="31455-125"><xref:System.ServiceModel.Activities.Send>Etkinliğin bir yer tutucu adresine sahip olduğunu `http://www.contoso.com` ; çalışma zamanında kullanılan gerçek adres, sağlanan geri arama adresidir.</span><span class="sxs-lookup"><span data-stu-id="31455-125">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="31455-126">`StartOrder`Yöntem ilk iş akışında çağrıldığında, iki iş akışı üzerinden yürütme akışını gösteren aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="31455-126">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
```output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 <span data-ttu-id="31455-127">Bu örnekte her iki iş akışı, kullanarak bağıntıyı açıkça yönetir <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .</span><span class="sxs-lookup"><span data-stu-id="31455-127">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="31455-128">Bu örnek iş akışlarında yalnızca tek bir bağıntı bulunduğundan, varsayılan <xref:System.ServiceModel.Activities.CorrelationHandle> Yönetim yeterli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="31455-128">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
