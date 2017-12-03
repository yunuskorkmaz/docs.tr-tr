---
title: "Keşif Yönlendirme Hizmeti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 66ff9d760ee59ef7a08f38826437b29077bc68d5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-router-service"></a>Keşif Yönlendirme Hizmeti
Bu örnek, başka bir uç nokta bulma iletilerini gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Keşif yönlendirme  
  
## <a name="discussion"></a>Tartışma  
 Keşif yönlendirme, bir istemci bir proxy kullanarak bir hizmet için arıyor ve proxy bu tür bir hizmet farkında değildir, ancak başka bir proxy bilir bir senaryoda yararlı olur. Bu proxy bulma paketi Bu istemciden ikinci proxy sunucusuna iletebilir. İkinci proxy hizmeti için konum ve özgün istemci yanıtlarını döndürür.  
  
 Bu örnekte, bir istemci bir bulma yönlendirme bileşenine bir ileti gönderir. Bu ileti bulma yönlendirici belirli bir noktadaki gönderilir. Yönlendirici, iletiyi daha sonra bir UDP iletir. çok noktaya yayın bitiş noktası. Yoklama iletisi çok noktaya yayın bitiş noktası ve UDP çok noktaya yayın üzerinde dinleyen bir hizmeti adresi o bulma yönlendiriciye yanıt gider. Bulma yönlendirici yanıtları toplar ve bunları istemciye geri gönderir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Örnek oluşturun.  
  
2.  DiscoveryRouter yürütülebilir dosyayı çalıştırın.  
  
3.  Hizmeti yürütülebilir dosyası derleme dizininden çalıştırın.  
  
4.  İstemci yürütülebilir çalıştırın. İstemci hizmeti bulur unutmayın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
