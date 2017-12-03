---
title: "WorkflowHostingEndpoint Sürdür yer işareti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1179d09d68d8730847776cf98e3996e3e6817753
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>WorkflowHostingEndpoint Sürdür yer işareti
Bu örnek gösterilmektedir nasıl <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> ile kullanılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı örnekleri oluşturmak için.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnekte <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> kullanarak barındırılan bir iş akışı örneği oluşturmak için <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>için genişletilebilirlik noktasıdır <xref:System.ServiceModel.Activities.WorkflowServiceHost> aşağıdaki senaryolarda kullanılabilir:  
  
-   Yeni iş akışı örnekleri oluşturma.  
  
-   Bir iş akışı örneği yer işaretlerini sürdürme barındırılan bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Bir iş akışı oluşturmak ve bir örnek kimliği dönmek için veya belirli bir kimliğe sahip bir örneğini oluşturmak için işlemler sağlar bir sözleşme bulunan örnek uç nokta gösterir Örnek konsol uygulaması oluşturur bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> örnek temel iş akışı tanımıyla ve ekler bir `CreationEndpoint` ana bilgisayara. Daha sonra çağırır `Create` yeni bir iş akışı örneği oluşturmak için uç nokta işlemi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Çözümü oluşturun.  
  
2.  Uygulamayı çalıştırın. `CreationEndpoint` Konsol iş akışı örneği oluşturulduğunda, örnek kimliği içeren bir ileti gösterir. "Hello World!" iletisi İş akışında yer işaretinin başarılı sürdürme tarafından yazdırılır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
