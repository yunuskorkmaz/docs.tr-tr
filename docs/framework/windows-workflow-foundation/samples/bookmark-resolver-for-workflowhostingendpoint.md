---
title: "WorkflowHostingEndpoint için bir çözümleyici yer işareti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 97e58699573aeae1594c1eea74fe1ce860cf6ed4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>WorkflowHostingEndpoint için bir çözümleyici yer işareti
Bu örnek gösterilmektedir nasıl <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> ile kullanılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı örnekleri oluşturmak için.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnekte <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanarak barındırılan iş akışı örnekleri oluşturmak için <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>için genişletilebilirlik noktasıdır <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilir:  
  
-   Yeni iş akışı örnekleri oluşturma.  
  
-   İş akışı örneği yer işaretlerini sürdürme barındırılan bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Bir iş akışı oluşturmak için işlemler sağlar ve örnek kimliği döndürür veya belirli bir kimliğe sahip bir örnek oluşturur sözleşme bulunan örnek uç nokta gösterir Örnek konsol uygulaması oluşturur bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> örnek bir iş akışı tanımıyla ve ekleyen bir `CreationEndpoint` ana bilgisayara. Daha sonra çağırır `Create` yeni bir iş akışı örneği oluşturmak için uç nokta işlemi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Çözümü oluşturun.  
  
2.  Uygulamayı çalıştırın. `CreationEndpoint` Konsol iş akışı örneği oluşturulduğunda, örnek kimliği içeren bir ileti gösterir. "Hello World!" iletisi İş akışı örneği tarafından yazdırılır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
