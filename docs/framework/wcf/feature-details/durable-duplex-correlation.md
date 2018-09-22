---
title: Dayanıklı Çift Yönlü Bağıntı
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: 82c052ff87eb8b125dfc64e1567dbd00d255894d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46699189"
---
# <a name="durable-duplex-correlation"></a>Dayanıklı Çift Yönlü Bağıntı
Dayanıklı çift yönlü bağıntı, geri çağırma bağıntı olarak da bilinen bir iş akışı hizmeti ilk çağırana bir geri çağırma göndermek için bir gereksinimi olduğunda yararlıdır. WCF çift yönlü, farklı bir geri çağırma dilediğiniz zaman gelecekte oluşabilir ve aynı kanalı veya kanal ömrü bağlı değildir; çağıran bir etkin uç noktası için geri çağırma iletiyi dinleme sahip tek gereksinim olmasıdır. Bu, uzun süre çalışan konuşmada iletişim kurmak iki iş akışı hizmetleri sağlar. Bu konu, dayanıklı çift yönlü bağıntı genel bir bakış sağlar.  
  
## <a name="using-durable-duplex-correlation"></a>Dayanıklı çift yönlü bağıntı kullanma  
 Dayanıklı çift yönlü bağıntı kullanmak için iki hizmet gibi çift yönlü işlemleri destekleyen bir bağlamı etkin bağlama kullanmalısınız <xref:System.ServiceModel.NetTcpContextBinding> veya <xref:System.ServiceModel.WSHttpContextBinding>. Arama hizmeti kayıtları bir <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> kendi istemci üzerinde istenen bağlama <xref:System.ServiceModel.Endpoint>. Alan hizmeti ilk çağrıda bu verileri alır ve ardından, kendi kullanır <xref:System.ServiceModel.Endpoint> içinde <xref:System.ServiceModel.Activities.Send> çağrıda arama hizmeti etkinlik. Bu örnekte, iki hizmet birbiriyle iletişim kurar. İlk hizmet ikinci hizmet üzerinde bir yöntemi çağırır ve ardından bir yanıt bekler. İkinci hizmet adını geri çağırma yöntemi bilir, ancak bu yöntem hizmetinin uç noktası, tasarım zamanında bilinmiyor.  
  
> [!NOTE]
> Dayanıklı çift yönlü yalnızca olabilir kullanılabilir <xref:System.ServiceModel.Channels.AddressingVersion> uç noktası ile yapılandırılmış <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Bu değilse bir <xref:System.InvalidOperationException> şu ileti ile özel durum oluştu: "iletiyi içeren bir uç nokta başvurusu için bir geri çağırma bağlam üstbilgiyle [AddressingVersion değerini](http://schemas.xmlsoap.org/ws/2004/08/addressing). Geri çağırma bağlam AddressingVersion değerini 'WSAddressing10' ile yapılandırıldığında, yalnızca iletilebilir.
  
 Aşağıdaki örnekte, bir geri çağırma oluşturan bir iş akışı hizmeti barındırılan <xref:System.ServiceModel.Endpoint> kullanarak <xref:System.ServiceModel.WSHttpContextBinding>.  
  
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
  
 Bu iş akışı hizmeti uygulayan bir iş akışı geri çağırma yurt içi hasıla ile başlatır, <xref:System.ServiceModel.Activities.Send> etkinliği ve bu geri çağırma uç noktasından başvurur <xref:System.ServiceModel.Activities.Receive> ile karşılık gelen etkinlik <xref:System.ServiceModel.Activities.Send>. Aşağıdaki örnek öğesinden döndürülen iş akışını temsil eden `GetWF1` yöntemi.  
  
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
  
 İkinci iş akışı hizmeti kullanarak sistem tarafından sağlanan, içerik tabanlı bir bağlama barındırılır.  
  
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
  
 Bu iş akışı hizmeti uygulayan bir iş akışı ile başlayan bir <xref:System.ServiceModel.Activities.Receive> etkinlik. Bu geri çağırma bağıntı gecikmeleri uzun süre çalışan işler ve hizmete ilk çağrıda geçirilen geri çağırma bağlamı kullanarak ilk hizmet geri çağırıyor benzetimini yapmak için bir süre için bu hizmet için etkinlik başlatır alırsınız. Aşağıdaki örnek çağrısından döndürülen iş akışını temsil eden `GetWF2`. Unutmayın <xref:System.ServiceModel.Activities.Send> etkinliğinde bir yer tutucu adresini `http://www.contoso.com`; çalışma zamanında kullanılan gerçek adresi sağlanan geri çağırma adresidir.  
  
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
  
 Zaman `StartOrder` ilk iş akışını yöntemi çağrıldığında, iki iş akışları aracılığıyla akışını gösterir aşağıdaki çıktıyı görüntülenir.  
  
```Output  
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
  
 Bağıntı kullanarak açıkça Bu örnekte, her iki iş akışlarını yönetme bir <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Bu örnek iş akışları, varsayılan olarak yalnızca tek bir bağıntı olduğundan <xref:System.ServiceModel.Activities.CorrelationHandle> yönetim olabilirdi yeterli.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dayanıklı çift yönlü &#91;WF örnekleri&#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
