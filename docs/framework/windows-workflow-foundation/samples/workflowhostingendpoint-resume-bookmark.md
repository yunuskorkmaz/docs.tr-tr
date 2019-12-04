---
title: WorkflowHostingEndpoint Sürdürme Yer İşareti
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3b3c7d40a70e797960837c82e2f5a08b2814e17f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710956"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>WorkflowHostingEndpoint Sürdürme Yer İşareti
Bu örnek, iş akışı örnekleri oluşturmak için <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> <xref:System.ServiceModel.Activities.WorkflowServiceHost> ile nasıl kullanılabileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösterir  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, <xref:System.ServiceModel.Activities.WorkflowServiceHost>kullanılarak barındırılan bir iş akışı örneği oluşturmak için <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanır. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, aşağıdaki senaryolarda kullanılabilen <xref:System.ServiceModel.Activities.WorkflowServiceHost> için bir genişletilebilirlik noktasıdır:  
  
- Yeni iş akışı örnekleri oluşturuluyor.  
  
- <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan bir iş akışı örneğinde yer işaretleri sürdürülüyor.  
  
 Dahil edilen örnek uç nokta, iş akışı oluşturma ve örnek KIMLIĞI döndürme veya belirli bir KIMLIĞE sahip bir örnek oluşturma işlemlerini sağlayan bir sözleşme sunar. Örnek konsol uygulaması, temel bir iş akışı tanımıyla <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir örnek oluşturur ve konağa bir `CreationEndpoint` ekler. Ardından, yeni bir iş akışı örneği oluşturmak için uç noktada `Create` işlemini çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü oluşturun.  
  
2. Uygulamayı çalıştırın. `CreationEndpoint` konsolu, iş akışı örneği oluşturulduğunda örnek KIMLIĞINI içeren bir ileti gösterir. "Merhaba Dünya!" iletisi , yer işaretinin başarılı sürdürme iş akışı tarafından yazdırılır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
