---
title: Dayanıklı Çift Yönlü Bağıntı
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ceb5cbedf30c8ec53bc815f9cd52f7bcb8a6e327
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="durable-duplex-correlation"></a>Dayanıklı Çift Yönlü Bağıntı
Dayanıklı çift yönlü bağıntı, geri çağırma bağıntı olarak da bilinen bir iş akışı hizmeti ilk çağıran için bir geri çağırma göndermek için bir gereksinim olduğunda yararlıdır. WCF çift yönlü aksine geri çağırma herhangi bir zamanda gelecekte oluşabilir ve aynı kanalı veya kanal ömrü bağlı değildir; tek gereksinim çağıran bir etkin uç nokta için geri çağırma iletisi dinleme olmasıdır. Bu, uzun süre çalışan konuşmada iletişim kurmak iki iş akışı hizmetleri sağlar. Bu konu, dayanıklı çift yönlü bağıntı genel bir bakış sağlar.  
  
## <a name="using-durable-duplex-correlation"></a>Dayanıklı çift yönlü bağıntı kullanma  
 Dayanıklı çift yönlü bağıntı kullanmak için iki hizmet, iki yönlü işlemleri gibi destekleyen bir bağlamı etkin bağlama kullanmalısınız <xref:System.ServiceModel.NetTcpContextBinding> veya <xref:System.ServiceModel.WSHttpContextBinding>. Arama hizmeti yazmaçlar bir <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> kendi istemci üzerinde istenen bağlama ile <xref:System.ServiceModel.Endpoint>. Alan hizmete ilk çağrıda bu verileri alır ve ardından, kendi kullanır <xref:System.ServiceModel.Endpoint> içinde <xref:System.ServiceModel.Activities.Send> çağrıda arama hizmeti etkinliği. Bu örnekte, iki hizmet birbirleri ile iletişim kurar. İlk hizmetin ikinci hizmetinde bir yöntemini çağırır ve yanıt için bekler. Geri çağırma yöntemi adını ikinci hizmet bilir, ancak bu yöntem uygulayan hizmet uç noktası tasarım zamanında bilinmiyor.  
  
> [!NOTE]
>  Dayanıklı çift yönlü yalnızca olabilir kullanılır <xref:System.ServiceModel.Channels.AddressingVersion> uç noktası ile yapılandırılmış <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Değilse sonra bir <xref:System.InvalidOperationException> aşağıdaki iletiyle özel durum: "ileti bir uç nokta başvurusu olan bir geri çağırma içerik üstbilgisi için AddressingVersion değerini içeriyor. ' Addressing200408 (HYPERLINK"http://schemas.xmlsoap.org/ws/2004/08/addressing" http://schemas.xmlsoap.org/ws/2004/08/addressing)'. AddressingVersion değerini 'WSAddressing10' ile yapılandırıldığında, geri çağırma bağlamı yalnızca iletilebilir."  
  
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
  
 Bu iş akışı hizmeti uygulayan bir iş akışı ile geri çağırma bağıntı başlatır, <xref:System.ServiceModel.Activities.Send> etkinliği ve bu geri çağırma uç noktasından başvurur <xref:System.ServiceModel.Activities.Receive> ile karşılık gelen etkinlik <xref:System.ServiceModel.Activities.Send>. Aşağıdaki örnekte sunucudan döndürülen iş akışı temsil eden `GetWF1` yöntemi.  
  
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
  
 İkinci iş akışı hizmeti, bir sistem tarafından sağlanan, bağlam tabanlı bağlamayı kullanarak barındırılır.  
  
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
  
 Bu iş akışı hizmeti uygulayan bir iş akışı ile başlayan bir <xref:System.ServiceModel.Activities.Receive> etkinlik. Bu uzun süre çalışan iş ve tekrar ilk çağrıda hizmete geçirildi geri çağırma bağlamı kullanarak ilk hizmet çağrıları benzetimini yapmak için bir süre için gecikmeler bu hizmet için geri çağırma bağıntı etkinlik başlatır alırsınız. Aşağıdaki örnek çağrısından döndürülen iş akışı temsil eden `GetWF2`. Unutmayın <xref:System.ServiceModel.Activities.Send> etkinliği olan bir yer tutucu adresini `http://www.contoso.com`; çalışma zamanında kullanılan gerçek adresi sağlanan geri çağırma adresidir.  
  
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
  
 Zaman `StartOrder` yöntemi ilk iş akışını çağrıldığında, iki iş akışları aracılığıyla akışını gösterir, aşağıdaki çıktısı görüntülenir.  
  
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
  
 Bu örnekte, her iki iş akışları açıkça bağıntı kullanarak yönetebileceğiniz bir <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Bu örnek iş akışları, varsayılan olarak yalnızca tek bir bağıntı olduğundan <xref:System.ServiceModel.Activities.CorrelationHandle> yönetim olabilirdi yeterli.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dayanıklı çift yönlü &#91;WF örnekleri&#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
