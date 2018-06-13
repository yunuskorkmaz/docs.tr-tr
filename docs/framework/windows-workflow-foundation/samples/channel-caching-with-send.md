---
title: Kanal göndererek önbelleğe alma
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: c26d81b9cd85ba75189fafddd82c3fb4673c7fae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514045"
---
# <a name="channel-caching-with-send"></a>Kanal göndererek önbelleğe alma
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Kullanıcıların kanal önbelleğe almayı, farklı düzeylerde olanak sağlayan <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.SendParametersContent> etkinlikler. Örnek düzeyinde önbelleğe almayı varsayılan olarak etkindir ve aşağıdaki özellikleri bu örnek gösterilmektedir:  
  
1.  Paylaşımı bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> uygulama etki alanı üzerinde.  
  
2.  Kanal önbelleğe almayı devre dışı bırakın.  
  
3.  Paylaşımı bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> iş akışı örnekleri arasında bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache> uzantı, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.  
  
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
