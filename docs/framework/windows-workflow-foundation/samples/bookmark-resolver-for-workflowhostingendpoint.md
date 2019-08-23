---
title: WorkflowHostingEndpoint için Yer İşareti Çözümleyici
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 017c5f959ed109ffe9b5e5c4bf2b9de9d04fdcdb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964937"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>WorkflowHostingEndpoint için Yer İşareti Çözümleyici
Bu örnek, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> iş akışı örnekleri oluşturmak için ile <xref:System.ServiceModel.Activities.WorkflowServiceHost> nasıl kullanılabileceğinizi gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek kullanılarak <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> iş akışı örnekleri oluşturmak için kullanır. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, için <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilecek bir genişletilebilirlik noktasıdır:  
  
- Yeni iş akışı örnekleri oluşturuluyor.  
  
- İçinde barındırılan iş akışı örneğinde yer işaretleri sürdürülüyor <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Dahil edilen örnek uç nokta, iş akışı oluşturmak için işlem sağlayan ve örnek KIMLIĞINI döndüren veya belirli bir KIMLIĞE sahip bir örnek oluşturan bir sözleşme gösterir. Örnek konsol uygulaması, iş akışı <xref:System.ServiceModel.Activities.WorkflowServiceHost> tanımıyla bir örnek oluşturur ve konağa bir `CreationEndpoint` ekler. Ardından, yeni bir `Create` iş akışı örneği oluşturmak için uç noktada işlemi çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü oluşturun.  
  
2. Uygulamayı çalıştırın. `CreationEndpoint` Konsol, iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir. "Merhaba Dünya!" iletisi , iş akışı örneği tarafından yazdırılır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
