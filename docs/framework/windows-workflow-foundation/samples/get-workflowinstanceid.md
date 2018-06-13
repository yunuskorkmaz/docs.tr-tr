---
title: WorkflowInstanceID Al
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: fbfaf52931345571e5125200fe467dcc098b9dc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513912"
---
# <a name="get-workflowinstanceid"></a>WorkflowInstanceID Al
Bu örnek özel etkinlik kullanımı gösterilmiştir `GetWorkflowInstanceId` iş akışı örneği kimliğine döndürmek için  
  
## <a name="demonstrates"></a>Gösteriler  
 Özel Etkinlik geliştirme iş akışı örneği erişim.  
  
## <a name="discussion"></a>Tartışma  
 Çalışan bir iş akışı örneği kimliği alma kod yazma gerektirir. Tam bildirim temelli bir iş akışını yazmak istiyorsanız, iş akışı örneği kimliği yazma deneyimini tam bildirim temelli bir iş akışı sağlamak için iş akışı içinde döndürebilir ve böylece etkinliğin başvurulamıyor aktivite gerekir. Birçok senaryo örneği kimliği erişmesi: günlüğü veya denetim amacıyla ya da bir istemcisine geri gelecekteki ilişkilendirme için örnek kimliği sağlayarak uygulama düzeyi bağıntı yapmak için birkaç örnek verilmiştir (Bu etkinliği içinde kullanarak örneğin, bir SendReply etkinliği).  
  
 `GetWorkflowInstanceId` olarak uygulanan bir <xref:System.Activities.CodeActivity%601> türünde bir değer döndürmesi gerekir çünkü <xref:System.Guid>, ve erişimi olmalıdır <xref:System.Activities.CodeActivityContext> iş akışının almak için örnek kimliği Uygulaması oldukça basittir.  
  
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
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
