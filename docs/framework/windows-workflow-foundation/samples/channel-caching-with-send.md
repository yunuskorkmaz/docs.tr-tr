---
title: Kanalı önbelleğe alma ile Gönder
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: 619088def1f5e443a31244516655d75d1e25c9cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503821"
---
# <a name="channel-caching-with-send"></a>Kanalı önbelleğe alma ile Gönder
<xref:System.ServiceModel.Activities.SendMessageChannelCache> İle kanalı önbelleğe alma farklı düzeylerine sahip kullanıcıların sağlayan <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.SendParametersContent> etkinlikler. Örnek düzeyi önbelleğe alma varsayılan olarak etkindir ve bu örnek, aşağıdaki özellikleri gösterir:  
  
1.  Paylaşımı bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> uygulama etki alanı arasında.  
  
2.  Kanal önbelleğe alma devre dışı bırakın.  
  
3.  Paylaşımı bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> iş akışı örnekleri arasında bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache> uzantı, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi derleyin.  
  
2.  \EchoWorkflowService\bin\debug içinde oluşturulan EchoWorkflowService uygulamayı çalıştırın.  
  
3.  .\EchoWorkflowClient\bin\debug içinde oluşturulan EchoWorkflowClient uygulamayı çalıştırın.  
  
4.  İstemci, Echo hizmet işlemini çağırır ve sonuçları yazdırır. Yazdırma sonuçları, hizmet ve istemci çıkmak için ENTER tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
