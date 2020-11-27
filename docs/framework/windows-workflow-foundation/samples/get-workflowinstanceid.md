---
title: WorkflowInstanceId Alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: db06b30f24a2d620406b3e6a35bba3a1fca70a9c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251561"
---
# <a name="get-workflowinstanceid"></a>WorkflowInstanceId Alma

Bu örnek, `GetWorkflowInstanceId` iş akışı örnek kimliğini döndürmek için özel etkinliğin nasıl kullanılacağını gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  

 Özel etkinlik geliştirme, iş akışı örneğine erişme.  
  
## <a name="discussion"></a>Tartışma  

 Çalışan bir iş akışının örnek KIMLIĞINI almak için kod yazılması gerekir. Tam bildirim temelli bir iş akışı yazmak isterseniz, etkinlik iş akışında, tam bildirim temelli bir iş akışı yazma deneyimi sağlamak üzere başvurulabilmesi için iş akışı örnek KIMLIĞINI döndürebilen bir etkinliğe ihtiyacınız vardır. Birçok senaryoda örnek KIMLIĞI için erişim gerekir: birkaç örnek günlüğe kaydetme veya denetim amacıyla veya örnek KIMLIĞINI bir istemciye daha sonra ilişkilendirme için geri (örneğin, bir SendReply etkinliği içinde kullanarak) sağlayarak uygulama düzeyinde bağıntı oluşturma amaçlıdır.  
  
 `GetWorkflowInstanceId` , ' a bir <xref:System.Activities.CodeActivity%601> değer döndürmesi gerektiğinden <xref:System.Guid> , <xref:System.Activities.CodeActivityContext> Iş akışının örnek kimliğini almak için öğesine erişiminin olması gerekir. Uygulama oldukça temel.  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
