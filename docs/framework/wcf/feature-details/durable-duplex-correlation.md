---
title: Dayanıklı Çift Yönlü Bağıntı
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: bb73cef5190a0b146e713ef1adae24219dc2eed8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185167"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="1b407-102">Dayanıklı Çift Yönlü Bağıntı</span><span class="sxs-lookup"><span data-stu-id="1b407-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="1b407-103">Geri arama korelasyon olarak da bilinen dayanıklı çift yönlü korelasyon, bir iş akışı hizmetinin ilk arayanın geri aramasını gönderme gereksinimi olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1b407-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="1b407-104">WCF dubleks aksine, geri arama gelecekte herhangi bir zamanda olabilir ve aynı kanal veya kanal ömrübağlı değildir; tek gereksinim, arayanın geri arama iletisini etkin bir bitiş noktası dinlemesidir.</span><span class="sxs-lookup"><span data-stu-id="1b407-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="1b407-105">Bu, iki iş akışı hizmetinin uzun süren bir konuşmada iletişim kurmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1b407-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="1b407-106">Bu konu, dayanıklı çift yönlü korelasyona genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b407-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="1b407-107">Dayanıklı Çift Yönlü Korelasyon Kullanma</span><span class="sxs-lookup"><span data-stu-id="1b407-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="1b407-108">Dayanıklı çift yönlü korelasyon kullanmak için, iki hizmetin iki yönlü işlemleri destekleyen <xref:System.ServiceModel.NetTcpContextBinding> <xref:System.ServiceModel.WSHttpContextBinding>bağlam etkin bir bağlama kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b407-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="1b407-109">Arama hizmeti, istemcileri <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> <xref:System.ServiceModel.Endpoint>için istenilen bağlama ile a kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1b407-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="1b407-110">Alıcı hizmet bu verileri ilk çağrıda alır ve aramayı <xref:System.ServiceModel.Endpoint> arama <xref:System.ServiceModel.Activities.Send> hizmetine geri döndüren etkinlikte kendi başına kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b407-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="1b407-111">Bu örnekte, iki hizmet birbiriyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="1b407-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="1b407-112">İlk hizmet ikinci hizmette bir yöntem çağırır ve ardından bir yanıt bekler.</span><span class="sxs-lookup"><span data-stu-id="1b407-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="1b407-113">İkinci hizmet geri arama yönteminin adını bilir, ancak bu yöntemi uygulayan hizmetin bitiş noktası tasarım zamanında bilinmemektedir.</span><span class="sxs-lookup"><span data-stu-id="1b407-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b407-114">Dayanıklı çift yönlü lük yalnızca <xref:System.ServiceModel.Channels.AddressingVersion> bitiş noktası ile yapılandırıldığında <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b407-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="1b407-115">Değilse, aşağıdaki iletiyle <xref:System.InvalidOperationException> bir özel durum atılır: "İleti, [AdreslemeSürümü](http://schemas.xmlsoap.org/ws/2004/08/addressing)için bir bitiş noktası referansı içeren bir geri arama bağlamı üstbilgisi içerir.</span><span class="sxs-lookup"><span data-stu-id="1b407-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="1b407-116">Geri arama bağlamı yalnızca AdreslemeSürümü 'WSAddressing10' ile yapılandırıldığında iletilebilir.</span><span class="sxs-lookup"><span data-stu-id="1b407-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="1b407-117">Aşağıdaki örnekte, bir iş akışı hizmeti <xref:System.ServiceModel.Endpoint> kullanarak <xref:System.ServiceModel.WSHttpContextBinding>bir geri arama oluşturan barındırılır.</span><span class="sxs-lookup"><span data-stu-id="1b407-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
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
  
 <span data-ttu-id="1b407-118">Bu iş akışı hizmetini uygulayan iş akışı, geri arama <xref:System.ServiceModel.Activities.Send> ilişkisini etkinliğiyle başbaşalaştırır ve <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send>bu geri arama bitiş noktasına ' ile ilişkili olan etkinlikten başvurur.</span><span class="sxs-lookup"><span data-stu-id="1b407-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="1b407-119">Aşağıdaki örnek, yöntemden döndürülen iş `GetWF1` akışını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1b407-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
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
  
 <span data-ttu-id="1b407-120">İkinci iş akışı hizmeti, sistem tarafından sağlanan, bağlam tabanlı bir bağlama kullanılarak barındırılır.</span><span class="sxs-lookup"><span data-stu-id="1b407-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
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
  
 <span data-ttu-id="1b407-121">Bu iş akışı hizmetini uygulayan iş akışı <xref:System.ServiceModel.Activities.Receive> bir etkinlikle başlar.</span><span class="sxs-lookup"><span data-stu-id="1b407-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="1b407-122">Bu alma etkinliği, bu hizmet için geri arama ilişkilendirmesini başlatır, uzun süren çalışmayı simüle etmek için bir süre geciktirir ve ardından ilk çağrıda hizmete geçirilen geri arama bağlamını kullanarak ilk hizmete geri çağrır.</span><span class="sxs-lookup"><span data-stu-id="1b407-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="1b407-123">Aşağıdaki örnek, bir aramadan 'a `GetWF2`döndürülen iş akışını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1b407-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="1b407-124"><xref:System.ServiceModel.Activities.Send> Etkinliğin yer tutucu adresi olduğunu `http://www.contoso.com`unutmayın; çalışma zamanında kullanılan gerçek adres, sağlanan geri arama adresidir.</span><span class="sxs-lookup"><span data-stu-id="1b407-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
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
  
 <span data-ttu-id="1b407-125">`StartOrder` Yöntem ilk iş akışında çağrıldığızaman, iki iş akışı üzerinden yürütme akışını gösteren aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1b407-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
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
  
 <span data-ttu-id="1b407-126">Bu örnekte, her iki iş akışı <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>da korelasyonun bir .</span><span class="sxs-lookup"><span data-stu-id="1b407-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="1b407-127">Bu örnek iş akışlarında yalnızca tek bir <xref:System.ServiceModel.Activities.CorrelationHandle> korelasyon olduğundan, varsayılan yönetim yeterli olurdu.</span><span class="sxs-lookup"><span data-stu-id="1b407-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
