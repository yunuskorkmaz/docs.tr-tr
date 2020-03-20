---
title: WorkflowHostingEndpoint için Yer İşareti Çözümleyici
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 113e6e52214d482dcd733bbd07ef2aab9f1b8c3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142816"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>WorkflowHostingEndpoint için Yer İşareti Çözümleyici
Bu örnek, iş <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> akışı örnekleri <xref:System.ServiceModel.Activities.WorkflowServiceHost> oluşturmak için nasıl kullanılabileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanılarak barındırılan iş <xref:System.ServiceModel.Activities.WorkflowServiceHost>akışı örneklerini oluşturmak için kullanır. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>aşağıdaki senaryolarda kullanılabilecek bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> genişletilebilirlik noktasıdır:  
  
- Yeni iş akışı örnekleri oluşturma.  
  
- İş akışı örneğinde yer imleri <xref:System.ServiceModel.Activities.WorkflowServiceHost>devam ediyor.  
  
 Dahil edilen örnek uç noktası, iş akışı oluşturmak için işlemler sağlayan ve örnek kimliği döndüren veya belirli bir kimliği olan bir örnek oluşturan bir sözleşmeyi ortaya çıkarır. Örnek konsol uygulaması, <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı tanımına sahip `CreationEndpoint` bir örnek oluşturur ve ana bilgisayara bir örnek ekler. Daha sonra `Create` yeni bir iş akışı örneği oluşturmak için bitiş noktasında ki işlemi çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Çözümü derleyin.  
  
2. Uygulamayı çalıştırın. Konsol, `CreationEndpoint` iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir. Mesaj "Merhaba Dünya!" iş akışı örneği tarafından yazdırılır.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
