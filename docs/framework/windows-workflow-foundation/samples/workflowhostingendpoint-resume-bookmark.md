---
title: WorkflowHostingEndpoint Sürdürme Yer İşareti
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: d393a26dd29624765e01b139e818de8a41f73e06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182738"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>WorkflowHostingEndpoint Sürdürme Yer İşareti
Bu örnek, iş <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> akışı örnekleri <xref:System.ServiceModel.Activities.WorkflowServiceHost> oluşturmak için nasıl kullanılabileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanarak <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan bir iş akışı örneği oluşturmak için kullanır. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>aşağıdaki senaryolarda kullanılabilecek bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> genişletilebilirlik noktasıdır:  
  
- Yeni iş akışı örnekleri oluşturma.  
  
- Bir iş akışı örneğinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>yer imleri devam .  
  
 Dahil edilen örnek bitiş noktası, iş akışı oluşturmak ve örnek kimliği döndürmek veya belirli bir tağa sahip bir örnek oluşturmak için işlemler sağlayan bir sözleşmeyi ortaya çıkarır. Örnek konsol uygulaması temel <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı tanımına sahip bir `CreationEndpoint` örnek oluşturur ve ana bilgisayara bir örnek ekler. Daha sonra `Create` yeni bir iş akışı örneği oluşturmak için bitiş noktasında ki işlemi çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Çözümü derleyin.  
  
2. Uygulamayı çalıştırın. Konsol, `CreationEndpoint` iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir. Mesaj "Merhaba Dünya!" yer imi nin başarılı bir şekilde yeniden başlatılmasına ilişkin iş akışı tarafından yazdırılır.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
