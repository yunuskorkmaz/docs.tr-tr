---
title: WorkflowInstanceID alma
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 6725ed92bf785e5b7f7d61332944fcce8427388a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520755"
---
# <a name="get-workflowinstanceid"></a>WorkflowInstanceID alma
Bu örnek özel etkinlik kullanma işlemini gösterir `GetWorkflowInstanceId` iş akışı örnek kimliğini döndürmek için  
  
## <a name="demonstrates"></a>Gösteriler  
 Özel Etkinlik geliştirme iş akışı örneği erişme.  
  
## <a name="discussion"></a>Tartışma  
 Çalışan bir iş akışı örnek kimliği başarmak için kod yazma gerekir. Tam bildirim temelli bir iş akışını yazmak istiyorsanız, tam bildirim temelli bir iş akışı yazma deneyimini sağlamak için iş akışı içinde iş akışı örnek Kimliğini döndürebilir ve böylece etkinlik başvurulabilen bir etkinlik gerekir. Örnek kimliği birçok senaryo erişmesi: günlüğe kaydetme veya denetim amacıyla veya örnek kimliği bir istemciye sağlayarak gelecekteki ilişkilendirme için uygulama düzeyi bağıntısı yapmak için birkaç örnek verilmiştir (Bu etkinliği içinde kullanarak örneğin, bir SendReply etkinliği).  
  
 `GetWorkflowInstanceId` olarak uygulanan bir <xref:System.Activities.CodeActivity%601> türünde bir değer döndürmesi gerekir çünkü <xref:System.Guid>, ve erişimi bulunmalıdır <xref:System.Activities.CodeActivityContext> iş akışının almak için örnek kimliği. Uygulanması oldukça basittir.  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
