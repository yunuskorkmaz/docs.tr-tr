---
description: 'Daha fazla bilgi: Workflowwhostingendpoint için yer Işareti Çözümleyicisi'
title: WorkflowHostingEndpoint için Yer İşareti Çözümleyici
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: fc2a21a33560452b141069e88b4d7ff816712d96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653816"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>WorkflowHostingEndpoint için Yer İşareti Çözümleyici

Bu örnek, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı örnekleri oluşturmak için ile nasıl kullanılabileceğinizi gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  

 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  

 Bu örnek <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanılarak barındırılan iş akışı örnekleri oluşturmak için kullanır <xref:System.ServiceModel.Activities.WorkflowServiceHost> . <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> , için <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilecek bir genişletilebilirlik noktasıdır:  
  
- Yeni iş akışı örnekleri oluşturuluyor.  
  
- İçinde barındırılan iş akışı örneğinde yer işaretleri sürdürülüyor <xref:System.ServiceModel.Activities.WorkflowServiceHost> .  
  
 Dahil edilen örnek uç nokta, iş akışı oluşturmak için işlem sağlayan ve örnek KIMLIĞINI döndüren veya belirli bir KIMLIĞE sahip bir örnek oluşturan bir sözleşme gösterir. Örnek konsol uygulaması, <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı tanımıyla bir örnek oluşturur ve konağa bir ekler `CreationEndpoint` . Ardından `Create` , yeni bir iş akışı örneği oluşturmak için uç noktada işlemi çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümü derleyin.  
  
2. Uygulamayı çalıştırın. `CreationEndpoint`Konsol, iş akışı örneği oluşturulduğunda örnek kimliğini içeren bir ileti gösterir. "Merhaba Dünya!" iletisi , iş akışı örneği tarafından yazdırılır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
