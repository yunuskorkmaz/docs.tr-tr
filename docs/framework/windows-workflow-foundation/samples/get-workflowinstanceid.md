---
title: WorkflowInstanceId Alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 8cb83fcf15b814b0ca6f7f95f1a9b8eec70185cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142738"
---
# <a name="get-workflowinstanceid"></a>WorkflowInstanceId Alma
Bu örnek, `GetWorkflowInstanceId` iş akışı örneği kimliğini döndürmek için özel etkinliğin nasıl kullanılacağını gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Özel etkinlik geliştirme, iş akışı örneğine nasıl erişileceği.  
  
## <a name="discussion"></a>Tartışma  
 Çalışan bir iş akışının örnek kimliğini almak için kod yazmak gerekiyor. Tam bildirimsel bir iş akışı yazmak istiyorsanız, tam bildirimsel iş akışı yetkilendirme deneyimi sağlamak için etkinliğin iş akışında başvurulabilmesi için iş akışı örneği kimliğini döndürebilecek bir etkinlik gerekir. Birçok senaryo örnek kimliğine erişim gerektirir: birkaç örnek, günlüğe kaydetme veya denetleme amacıyla veya örnek kimliğini gelecekteki ilişkilendirme için bir istemciye geri sağlayarak uygulama düzeyi korelasyonu yapmak içindir (örneğin, bu etkinliği bir SendReply etkinliği).  
  
 `GetWorkflowInstanceId`bir tür <xref:System.Activities.CodeActivity%601> <xref:System.Guid>değeri döndürmesi gerektiği ve iş akışının örnek <xref:System.Activities.CodeActivityContext> kimliğini almak için erişmesi gerektiği için bir olarak uygulanır. Uygulanması oldukça basittir.  
  
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
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
