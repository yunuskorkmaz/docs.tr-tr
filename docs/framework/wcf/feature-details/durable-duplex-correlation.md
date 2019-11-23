---
title: Dayanıklı Çift Yönlü Bağıntı
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: efc647b8a39f419f2165fe355529ba145663b753
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291584"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="a42c0-102">Dayanıklı Çift Yönlü Bağıntı</span><span class="sxs-lookup"><span data-stu-id="a42c0-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="a42c0-103">Geri arama bağıntısı olarak da bilinen dayanıklı çift yönlü bağıntı, bir iş akışı hizmeti ilk arayana geri çağrı göndermek için bir gereksinime sahip olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="a42c0-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="a42c0-104">WCF çift yönlü olarak, geri çağırma gelecekte herhangi bir zamanda gerçekleşebilir ve aynı kanala veya kanal ömrüne bağlı değildir; Tek gereksinim, çağıranın geri çağırma iletisini dinleyen etkin bir uç noktaya sahip olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="a42c0-105">Bu, iki iş akışı hizmetinin uzun süre çalışan bir konuşmada iletişim kurmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="a42c0-106">Bu konu, dayanıklı çift yönlü bağıntı için bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a42c0-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="a42c0-107">Dayanıklı çift yönlü bağıntı kullanma</span><span class="sxs-lookup"><span data-stu-id="a42c0-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="a42c0-108">Dayanıklı çift yönlü bağıntı kullanmak için, iki hizmetin <xref:System.ServiceModel.NetTcpContextBinding> veya <xref:System.ServiceModel.WSHttpContextBinding>gibi iki yönlü işlemleri destekleyen bir bağlam özellikli bağlama kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="a42c0-109">Çağıran hizmet, istemci <xref:System.ServiceModel.Endpoint>istenen bağlamaya sahip bir <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a42c0-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="a42c0-110">Alıcı hizmeti bu verileri ilk çağrıda alır ve ardından çağıran hizmete geri çağrı yapan <xref:System.ServiceModel.Activities.Send> etkinliğinde kendi <xref:System.ServiceModel.Endpoint> kullanır.</span><span class="sxs-lookup"><span data-stu-id="a42c0-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="a42c0-111">Bu örnekte, iki hizmet birbirleriyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="a42c0-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="a42c0-112">İlk hizmet ikinci hizmette bir yöntemi çağırır ve sonra bir yanıt bekler.</span><span class="sxs-lookup"><span data-stu-id="a42c0-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="a42c0-113">İkinci hizmet geri arama yönteminin adını bilir, ancak bu yöntemi uygulayan hizmetin uç noktası tasarım zamanında bilinmez.</span><span class="sxs-lookup"><span data-stu-id="a42c0-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a42c0-114">Dayanıklı çift yönlü yalnızca uç noktanın <xref:System.ServiceModel.Channels.AddressingVersion> <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>ile yapılandırıldığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="a42c0-115">Aksi takdirde, aşağıdaki iletiyle bir <xref:System.InvalidOperationException> özel durumu oluşturulur: "ileti [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing)için uç nokta başvurusuna sahip bir geri çağırma bağlam üst bilgisi içerir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="a42c0-116">Geri çağırma bağlamı yalnızca AddressingVersion ' WSAddressing10 ' ile yapılandırıldığında aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="a42c0-117">Aşağıdaki örnekte, <xref:System.ServiceModel.WSHttpContextBinding>kullanarak bir geri çağırma <xref:System.ServiceModel.Endpoint> oluşturan bir iş akışı hizmeti barındırılır.</span><span class="sxs-lookup"><span data-stu-id="a42c0-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
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
  
 <span data-ttu-id="a42c0-118">Bu iş akışı hizmetini uygulayan iş akışı, geri çağırma bağıntısını <xref:System.ServiceModel.Activities.Send> etkinliğiyle başlatır ve bu geri çağırma uç noktasına <xref:System.ServiceModel.Activities.Send>ilişkili <xref:System.ServiceModel.Activities.Receive> etkinliğinden başvurur.</span><span class="sxs-lookup"><span data-stu-id="a42c0-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="a42c0-119">Aşağıdaki örnek, `GetWF1` yönteminden döndürülen iş akışını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a42c0-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
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
  
 <span data-ttu-id="a42c0-120">İkinci iş akışı hizmeti, sistem tarafından sağlanmış, bağlam tabanlı bağlama kullanılarak barındırılır.</span><span class="sxs-lookup"><span data-stu-id="a42c0-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
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
  
 <span data-ttu-id="a42c0-121">Bu iş akışı hizmetini uygulayan iş akışı <xref:System.ServiceModel.Activities.Receive> etkinlikle başlar.</span><span class="sxs-lookup"><span data-stu-id="a42c0-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="a42c0-122">Bu alma etkinliği, bu hizmet için geri çağırma bağıntısını başlatır, uzun süredir çalışan çalışmanın benzetimini yapmak için bir süre gecikmesini sağlar ve ardından hizmete ilk çağrıda geçirilen geri çağırma bağlamını kullanarak ilk hizmete geri çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="a42c0-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="a42c0-123">Aşağıdaki örnek, `GetWF2`çağrısından döndürülen iş akışını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a42c0-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="a42c0-124"><xref:System.ServiceModel.Activities.Send> etkinliğinin `http://www.contoso.com`yer tutucu adresi olduğunu unutmayın; çalışma zamanında kullanılan gerçek adres, sağlanan geri arama adresidir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
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
  
 <span data-ttu-id="a42c0-125">`StartOrder` yöntemi ilk iş akışında çağrıldığında, iki iş akışı aracılığıyla yürütme akışını gösteren aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
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
  
 <span data-ttu-id="a42c0-126">Bu örnekte her iki iş akışı <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>kullanarak bağıntıyı açıkça yönetir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="a42c0-127">Bu örnek iş akışlarında yalnızca tek bir bağıntı bulunduğundan, varsayılan <xref:System.ServiceModel.Activities.CorrelationHandle> yönetimi yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="a42c0-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
