---
title: 'Bağlam Değişimi Bağıntısı '
ms.date: 03/30/2017
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
ms.openlocfilehash: d9de111fa08b4a398bba52bc903ea1fec8c7f298
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519738"
---
# <a name="context-exchange-correlation"></a>Bağlam Değişimi Bağıntısı 
Bağlam bağıntı açıklanan bağlam değişimi mekanizması temel [.NET bağlam değişimi protokolü belirtimi](https://go.microsoft.com/fwlink/?LinkId=166059). Bağlam bağıntı iletileri doğru örneğini ilişkilendirmek için iyi bilinen bağlam üst bilgi veya tanımlama bilgisi kullanır. Bir bağlam tabanlı gibi bağlama, bağlam bağıntı kullanılacak <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, veya <xref:System.ServiceModel.NetTcpContextBinding> sağlanan uç nokta üzerinde kullanılmalıdır <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bu konuda, Mesajlaşma etkinlikleriyle iş akışı hizmeti içinde bağlam bağıntı kullanmayı açıklar.  
  
## <a name="using-context-correlation"></a>Bağlam bağıntı kullanma  
 Bir istemci, yinelenen bir iş akışı hizmeti çağrılarını yapmanız gerekir ve bağlam bağlamaları birini kullanarak barındırılan Hizmet bağlamı bağıntı kullanılır. Bu tür bir bağıntı tarafından başlatılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti içindeki iş akışı hizmeti. Bağlam istemcisine yanıtla birlikte gönderilir ve ardından istemci hizmeti arka arkaya çağrı bu bağlam ekler.  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a>Bir iş akışı hizmetinde bağlam bağıntı yapılandırma  
 Bağlam bağıntı kullanarak tarafından başlatılan bir <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> ilişkili <xref:System.ServiceModel.Activities.SendReply> ilk gelen iletiye yanıt etkinlik. Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.SendReply> bağlam bağıntı başlatmak üzere yapılandırılır.  
  
```csharp  
Variable<string> Item = new Variable<string>();  
Variable<CorrelationHandle> OrderHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IOrderService",  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    CorrelationInitializers =  
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = OrderHandle  
        }  
    }  
};  
```  
  
> [!NOTE]
>  Bu örnekte kullanılan bağıntı aslında iki tür vardır: bağlam bağıntı ve istek-yanıt bağıntısı. İstemcilerden gelen çağrıları doğru örneğini yönlendirilebilmesi bağlam bağıntı kullanılır. İstek-yanıt bağıntısı tarafından kullanılan <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler birlikte iki yönlü işlemi uygulamak için bu etkinlikleri tarafından modellenir. Bu örnekte, yalnızca bağlam bağıntı açıkça yapılandırılmış ve <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çiftini örtük tarafından sağlanan varsayılan istek-yanıt bağıntısı kullanarak <xref:System.ServiceModel.Activities.CorrelationHandle> yönetimini <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Kullanırken **ReceiveAndSendReply** etkinlik iş akışı Tasarımcısı, istek-yanıt bağıntısı şablonda açıkça yapılandırılmış. İstek-yanıt bağıntısı ve örtük bağıntı tanıtıcısı yönetimi hakkında daha fazla bilgi için bkz. [istek-yanıt](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) ve [bağıntı genel bakış](../../../../docs/framework/wcf/feature-details/correlation-overview.md). Hakkında daha fazla bilgi için **ReceiveAndSendReply** etkinlik şablonu görmek [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).  
  
 Sonraki <xref:System.ServiceModel.Activities.Receive> etkinlikleri iş akışı hizmeti içinde başvurabilir <xref:System.ServiceModel.Activities.CorrelationHandle> , başlatılan tarafından <xref:System.ServiceModel.Activities.SendReply> önceki örnekte.  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 Uç nokta üzerinde yapılandırılır <xref:System.ServiceModel.Activities.WorkflowServiceHost> Bağlam tabanlı, gibi bağlama kullanılacak <xref:System.ServiceModel.BasicHttpContextBinding>.  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a>Bir iş akışı istemcisinde bağlam bağıntı yapılandırma  
 İstemci başka bir iş akışı olduğunda, bağlam bağıntı istemcide yapılandırılması gerekir. İstemci iş akışındaki <xref:System.ServiceModel.Activities.ReceiveReply> , <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> iş akışı hizmeti ilk çağrıda çifti ile yapılandırılması gerekir bir <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.  
  
```csharp  
Variable<CorrelationHandle> cchandle = new Variable<CorrelationHandle>();  
Send request = new Send  
{  
    // Activity configuration omitted.  
};  
  
ReceiveReply reply = new ReceiveReply  
{  
    Request = request,  
    CorrelationInitializers =   
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = cchandle  
        }  
    }  
};  
```  
  
 Bağıntı sonra başlatılmış, sonraki <xref:System.ServiceModel.Activities.Send> etkinlikleri kullanma <xref:System.ServiceModel.Activities.CorrelationHandle> aynı hizmet örneği üzerinde yöntem çağırmak için.  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 Bu örneklerde, bağlam bağıntı açıkça yapılandırılmış olduğunu unutmayın. İstemci iş akışı da içinde barındırılmaması durumunda bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>, etkinlikleri içerdiği sürece bağıntı açıkça, yapılandırılmalıdır bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik. Bağlam bağıntı hakkında daha fazla bilgi için bkz: [NetContextExchangeCorrelation](https://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) örnek.  
  
 İş akışı hizmetine çağrı yapan istemcinin bir iş akışı değilse, onu açıkça geri iş akışı hizmeti ilk çağrısından döndürülen bağlamı geçirir sürece ardından, hala yinelenen çağrıları zorlaştırabilir. Bir hizmet başvurusu ekleyerek oluşturulan Proxy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] depolayabilir ve varsayılan olarak bu bağlamı.
