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
# <a name="durable-duplex-correlation"></a>Dayanıklı Çift Yönlü Bağıntı
Geri arama korelasyon olarak da bilinen dayanıklı çift yönlü korelasyon, bir iş akışı hizmetinin ilk arayanın geri aramasını gönderme gereksinimi olduğunda yararlıdır. WCF dubleks aksine, geri arama gelecekte herhangi bir zamanda olabilir ve aynı kanal veya kanal ömrübağlı değildir; tek gereksinim, arayanın geri arama iletisini etkin bir bitiş noktası dinlemesidir. Bu, iki iş akışı hizmetinin uzun süren bir konuşmada iletişim kurmasına olanak tanır. Bu konu, dayanıklı çift yönlü korelasyona genel bir bakış sağlar.  
  
## <a name="using-durable-duplex-correlation"></a>Dayanıklı Çift Yönlü Korelasyon Kullanma  
 Dayanıklı çift yönlü korelasyon kullanmak için, iki hizmetin iki yönlü işlemleri destekleyen <xref:System.ServiceModel.NetTcpContextBinding> <xref:System.ServiceModel.WSHttpContextBinding>bağlam etkin bir bağlama kullanması gerekir. Arama hizmeti, istemcileri <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> <xref:System.ServiceModel.Endpoint>için istenilen bağlama ile a kaydeder. Alıcı hizmet bu verileri ilk çağrıda alır ve aramayı <xref:System.ServiceModel.Endpoint> arama <xref:System.ServiceModel.Activities.Send> hizmetine geri döndüren etkinlikte kendi başına kullanır. Bu örnekte, iki hizmet birbiriyle iletişim kurar. İlk hizmet ikinci hizmette bir yöntem çağırır ve ardından bir yanıt bekler. İkinci hizmet geri arama yönteminin adını bilir, ancak bu yöntemi uygulayan hizmetin bitiş noktası tasarım zamanında bilinmemektedir.  
  
> [!NOTE]
> Dayanıklı çift yönlü lük yalnızca <xref:System.ServiceModel.Channels.AddressingVersion> bitiş noktası ile yapılandırıldığında <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>kullanılabilir. Değilse, aşağıdaki iletiyle <xref:System.InvalidOperationException> bir özel durum atılır: "İleti, [AdreslemeSürümü](http://schemas.xmlsoap.org/ws/2004/08/addressing)için bir bitiş noktası referansı içeren bir geri arama bağlamı üstbilgisi içerir. Geri arama bağlamı yalnızca AdreslemeSürümü 'WSAddressing10' ile yapılandırıldığında iletilebilir.
  
 Aşağıdaki örnekte, bir iş akışı hizmeti <xref:System.ServiceModel.Endpoint> kullanarak <xref:System.ServiceModel.WSHttpContextBinding>bir geri arama oluşturan barındırılır.  
  
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
  
 Bu iş akışı hizmetini uygulayan iş akışı, geri arama <xref:System.ServiceModel.Activities.Send> ilişkisini etkinliğiyle başbaşalaştırır ve <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send>bu geri arama bitiş noktasına ' ile ilişkili olan etkinlikten başvurur. Aşağıdaki örnek, yöntemden döndürülen iş `GetWF1` akışını temsil eder.  
  
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
  
 İkinci iş akışı hizmeti, sistem tarafından sağlanan, bağlam tabanlı bir bağlama kullanılarak barındırılır.  
  
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
  
 Bu iş akışı hizmetini uygulayan iş akışı <xref:System.ServiceModel.Activities.Receive> bir etkinlikle başlar. Bu alma etkinliği, bu hizmet için geri arama ilişkilendirmesini başlatır, uzun süren çalışmayı simüle etmek için bir süre geciktirir ve ardından ilk çağrıda hizmete geçirilen geri arama bağlamını kullanarak ilk hizmete geri çağrır. Aşağıdaki örnek, bir aramadan 'a `GetWF2`döndürülen iş akışını temsil eder. <xref:System.ServiceModel.Activities.Send> Etkinliğin yer tutucu adresi olduğunu `http://www.contoso.com`unutmayın; çalışma zamanında kullanılan gerçek adres, sağlanan geri arama adresidir.  
  
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
  
 `StartOrder` Yöntem ilk iş akışında çağrıldığızaman, iki iş akışı üzerinden yürütme akışını gösteren aşağıdaki çıktı görüntülenir.  
  
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
  
 Bu örnekte, her iki iş akışı <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>da korelasyonun bir . Bu örnek iş akışlarında yalnızca tek bir <xref:System.ServiceModel.Activities.CorrelationHandle> korelasyon olduğundan, varsayılan yönetim yeterli olurdu.
