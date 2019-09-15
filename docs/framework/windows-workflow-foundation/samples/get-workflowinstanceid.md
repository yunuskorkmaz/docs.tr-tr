---
title: WorkflowInstanceId Alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: f8bd3205f5b7a4b3bae5203dc90a3c393cedcbdd
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989377"
---
# <a name="get-workflowinstanceid"></a>WorkflowInstanceId Alma
Bu örnek, `GetWorkflowInstanceId` iş akışı örnek kimliğini döndürmek için özel etkinliğin nasıl kullanılacağını gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Özel etkinlik geliştirme, iş akışı örneğine erişme.  
  
## <a name="discussion"></a>Tartışma  
 Çalışan bir iş akışının örnek KIMLIĞINI almak için kod yazılması gerekir. Tam bildirim temelli bir iş akışı yazmak isterseniz, etkinlik iş akışında, tam bildirim temelli bir iş akışı yazma deneyimi sağlamak üzere başvurulabilmesi için iş akışı örnek KIMLIĞINI döndürebilen bir etkinliğe ihtiyacınız vardır. Birçok senaryoda örnek KIMLIĞI için erişim gerekir: birkaç örnek günlüğe kaydetme veya denetim amacıyla veya örnek KIMLIĞINI bir istemciye daha sonra ilişkilendirme için geri (örneğin, bir SendReply etkinliği).  
  
 `GetWorkflowInstanceId`, <xref:System.Guid>' a bir <xref:System.Activities.CodeActivity%601> değer döndürmesi gerektiğinden, iş akışının örnek kimliğini almak <xref:System.Activities.CodeActivityContext> için öğesine erişiminin olması gerekir. Uygulama oldukça temel.  
  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
