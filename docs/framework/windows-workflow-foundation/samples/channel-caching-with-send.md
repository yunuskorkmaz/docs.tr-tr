---
title: "Kanal göndererek önbelleğe alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b12ebe4cc15629125627253200a95b1f8353bbc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="channel-caching-with-send"></a>Kanal göndererek önbelleğe alma
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Kullanıcıların kanal önbelleğe almayı, farklı düzeylerde olanak sağlayan <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.SendParametersContent> etkinlikler. Örnek düzeyinde önbelleğe almayı varsayılan olarak etkindir ve aşağıdaki özellikleri bu örnek gösterilmektedir:  
  
1.  Paylaşımı bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> uygulama etki alanı üzerinde.  
  
2.  Kanal önbelleğe almayı devre dışı bırakın.  
  
3.  Paylaşımı bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> iş akışı örnekleri arasında bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>uzantı, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi oluşturun.  
  
2.  \EchoWorkflowService\bin\debug içinde oluşturulan EchoWorkflowService uygulamayı çalıştırın.  
  
3.  .\EchoWorkflowClient\bin\debug içinde oluşturulan EchoWorkflowClient uygulamayı çalıştırın.  
  
4.  İstemci Yankı işlemi hizmet üzerinde çağıran ve sonuçları yazdırır. Yazdırma sonuçları, istemci ve hizmet çıkmak için ENTER tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
