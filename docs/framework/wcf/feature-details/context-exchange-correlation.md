---
title: "Bağlam Değişimi Bağıntısı "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee22feab20e2c96f3e708a277f9048f739213520
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="context-exchange-correlation"></a>Bağlam Değişimi Bağıntısı 
Bağlam bağıntı açıklanan bağlam değişimi mekanizması temel [.NET bağlam değişimi protokolü belirtimi](http://go.microsoft.com/fwlink/?LinkId=166059). Bağlam bağıntı, doğru örneğini iletileri ilişkilendirmek için iyi bilinen içerik üstbilgisi veya tanımlama bilgisi kullanır. Bir bağlam tabanlı gibi bağlama bağlamı bağıntı kullanılacak <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, veya <xref:System.ServiceModel.NetTcpContextBinding> için sağlanan uç kullanılmalıdır <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bu konu bir iş akışı hizmeti Mesajlaşma etkinliklerle bağlam bağıntı kullanmayı açıklar.  
  
## <a name="using-context-correlation"></a>Bağlam bağıntı kullanma  
 Bağlam bağıntı bir istemci bir iş akışı hizmeti yinelenen çağrılarını yapmanız gerekir ve bağlam bağlamaları birini kullanarak barındırılan hizmetin olmadığında kullanılır. Bu tür bir bağıntı tarafından başlatılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> iş akışı hizmetinde çifti. Bağlam istemciyi yanıtla birlikte gönderilir ve sonra istemci hizmete sonraki çağrılar bu bağlamda ekler.  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a>Bir iş akışı hizmetinde bağlam bağıntı yapılandırma  
 Bağlam bağıntı başlatıldığı kullanarak bir <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> ile ilişkili <xref:System.ServiceModel.Activities.SendReply> ilk gelen iletisini yanıtladığı etkinlik. Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.SendReply> bağlamı bağıntı başlatmak için yapılandırılır.  
  
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
>  Bu örnekte kullanılan bağıntı gerçekte iki tür vardır: bağlam bağıntı ve istek-yanıt bağıntısı. Böylece istemcilerden çağrılarını doğru örneğine yönlendirilecek bağlam bağıntı kullanılır. İstek-yanıt bağıntısı tarafından kullanılan <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri birlikte iki yönlü işlemi uygulamak için bu etkinlikler tarafından modellenir. Bu örnekte, yalnızca bağlam bağıntı açıkça yapılandırılmış ve <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti örtük tarafından sağlanan varsayılan istek-yanıt bağıntısı kullanarak <xref:System.ServiceModel.Activities.CorrelationHandle> yönetimini <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Kullanırken **ReceiveAndSendReply** iş akışı Tasarımcısı, istek-yanıt bağıntısı etkinlik şablonu açıkça yapılandırılmış. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]İstek-yanıt bağıntısı ve örtük bağıntı tanıtıcısı yönetimi Bkz [istek-yanıt](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) ve [bağıntı genel bakış](../../../../docs/framework/wcf/feature-details/correlation-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]**ReceiveAndSendReply** etkinlik şablonu bkz [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).  
  
 Sonraki <xref:System.ServiceModel.Activities.Receive> iş akışı hizmetinde etkinlikleri başvuru <xref:System.ServiceModel.Activities.CorrelationHandle> , başlatılmış tarafından <xref:System.ServiceModel.Activities.SendReply> önceki örnekte.  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 Uç nokta sonra yapılandırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir bağlam tabanlı, gibi bağlama kullanmak için <xref:System.ServiceModel.BasicHttpContextBinding>.  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a>Bir iş akışı istemcisinde bağlam bağıntı yapılandırma  
 İstemci başka bir iş akışı olduğunda, bağlam bağıntı istemcide yapılandırılmış olması gerekir. İstemci akışında <xref:System.ServiceModel.Activities.ReceiveReply> , <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> iş akışı hizmeti ilk çağrıda çifti ile yapılandırılması gerekir bir <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.  
  
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
  
 Bağıntı sonra başlatılmış, sonraki <xref:System.ServiceModel.Activities.Send> etkinlikleri kullanma <xref:System.ServiceModel.Activities.CorrelationHandle> aynı hizmet örneği üzerinde yöntemleri çağırmak için.  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 Bu örneklerde, bağlam bağıntı açıkça yapılandırıldığını unutmayın. İstemci iş akışı ayrıca içinde barındırılmıyorsa bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>, etkinlikleri içerdiği sürece bağıntı açıkça, yapılandırılmalıdır sonra bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinlik. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bağlam bağıntı bkz [NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) örnek.  
  
 İş akışı hizmeti çağrıları yapma istemci bir iş akışı değilse, bunu açıkça geri iş akışı hizmeti için ilk çağrısından döndürülen bağlam geçirir sürece sonra bunu hala yinelenen aramaları yapabilir. Hizmet başvuru ekleyerek oluşturulan proxy'leri [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] depolamak ve varsayılan olarak bu bağlamda geçer.
