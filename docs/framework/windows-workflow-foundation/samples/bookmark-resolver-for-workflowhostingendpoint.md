---
title: WorkflowHostingEndpoint için Yer İşareti Çözümleyici
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 99371cc64ca2790bec383b4ab5dca280d4bb9659
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716760"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>WorkflowHostingEndpoint için Yer İşareti Çözümleyici
Bu örnek, iş akışı örnekleri oluşturmak için <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> <xref:System.ServiceModel.Activities.WorkflowServiceHost> ile nasıl kullanılabileceğini gösterir.  
  
## <a name="demonstrates"></a>Gösterir  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, <xref:System.ServiceModel.Activities.WorkflowServiceHost>kullanılarak barındırılan iş akışı örnekleri oluşturmak için <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanır. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, aşağıdaki senaryolarda kullanılabilen <xref:System.ServiceModel.Activities.WorkflowServiceHost> için bir genişletilebilirlik noktasıdır:  
  
- Yeni iş akışı örnekleri oluşturuluyor.  
  
- <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan iş akışı örneğinde yer işaretleri sürdürülüyor.  
  
 Dahil edilen örnek uç nokta, iş akışı oluşturmak için işlem sağlayan ve örnek KIMLIĞINI döndüren veya belirli bir KIMLIĞE sahip bir örnek oluşturan bir sözleşme gösterir. Örnek konsol uygulaması, bir iş akışı tanımıyla <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir örnek oluşturur ve konağa bir `CreationEndpoint` ekler. Ardından, yeni bir iş akışı örneği oluşturmak için uç noktada `Create` işlemini çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü oluşturun.  
  
2. Uygulamayı çalıştırın. `CreationEndpoint` konsolu, iş akışı örneği oluşturulduğunda örnek KIMLIĞINI içeren bir ileti gösterir. "Merhaba Dünya!" iletisi , iş akışı örneği tarafından yazdırılır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
