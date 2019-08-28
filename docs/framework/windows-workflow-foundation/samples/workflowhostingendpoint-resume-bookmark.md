---
title: WorkflowHostingEndpoint Sürdürme Yer İşareti
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 83065a0034303dcbc83f846ba455f71e954fdb54
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037773"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>WorkflowHostingEndpoint Sürdürme Yer İşareti
Bu örnek, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> iş akışı örnekleri oluşturmak için ile <xref:System.ServiceModel.Activities.WorkflowServiceHost> nasıl kullanılabileceğinizi gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek kullanılarak <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> bir iş akışı örneği oluşturmak için öğesini kullanır. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, için <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilecek bir genişletilebilirlik noktasıdır:  
  
- Yeni iş akışı örnekleri oluşturuluyor.  
  
- İçinde barındırılan bir iş akışı örneğinde yer işaretleri sürdürülüyor <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Dahil edilen örnek uç nokta, iş akışı oluşturma ve örnek KIMLIĞI döndürme veya belirli bir KIMLIĞE sahip bir örnek oluşturma işlemlerini sağlayan bir sözleşme sunar. Örnek konsol uygulaması, temel bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı tanımına sahip bir örnek oluşturur ve konağa bir `CreationEndpoint` ekler. Ardından, yeni bir `Create` iş akışı örneği oluşturmak için uç noktada işlemi çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü oluşturun.  
  
2. Uygulamayı çalıştırın. `CreationEndpoint` Konsol, iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir. "Merhaba Dünya!" iletisi , yer işaretinin başarılı sürdürme iş akışı tarafından yazdırılır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
