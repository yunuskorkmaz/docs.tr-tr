---
title: WorkflowHostingEndpoint Sürdürme Yer İşareti
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: b7f701c012c05dcc7e05c56123436af3dbacf4c4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267448"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>WorkflowHostingEndpoint Sürdürme Yer İşareti

Bu örnek, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı örnekleri oluşturmak için ile nasıl kullanılabileceğinizi gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  

 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  

 Bu örnek <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanılarak barındırılan bir iş akışı örneği oluşturmak için öğesini kullanır <xref:System.ServiceModel.Activities.WorkflowServiceHost> . <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> , için <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilecek bir genişletilebilirlik noktasıdır:  
  
- Yeni iş akışı örnekleri oluşturuluyor.  
  
- İçinde barındırılan bir iş akışı örneğinde yer işaretleri sürdürülüyor <xref:System.ServiceModel.Activities.WorkflowServiceHost> .  
  
 Dahil edilen örnek uç nokta, iş akışı oluşturma ve örnek KIMLIĞI döndürme veya belirli bir KIMLIĞE sahip bir örnek oluşturma işlemlerini sağlayan bir sözleşme sunar. Örnek konsol uygulaması <xref:System.ServiceModel.Activities.WorkflowServiceHost> , temel bir iş akışı tanımına sahip bir örnek oluşturur ve konağa bir ekler `CreationEndpoint` . Ardından `Create` , yeni bir iş akışı örneği oluşturmak için uç noktada işlemi çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü derleyin.  
  
2. Uygulamayı çalıştırın. `CreationEndpoint`Konsol, iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir. "Merhaba Dünya!" iletisi , yer işaretinin başarılı sürdürme iş akışı tarafından yazdırılır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
