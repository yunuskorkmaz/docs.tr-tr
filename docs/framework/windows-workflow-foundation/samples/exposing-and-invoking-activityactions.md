---
title: Gösterme ve ActivityActions çağırma
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 99207c33d82ec9028da2355cc792c366dc5e0cc6
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583068"
---
# <a name="exposing-and-invoking-activityactions"></a>Gösterme ve ActivityActions çağırma
Bu örnek sahip özel bir etkinlik nasıl geliştirilebileceğini gösterir bir <xref:System.Activities.ActivityAction>. Ayrıca uygulaması sağlayarak bu etkinliğin nasıl yapılacağı açıklanır <xref:System.Activities.ActivityAction>.  
  
 Bir <xref:System.Activities.ActivityAction> belirli imzalarla "açıkları burada etkinliği kullanıcı bağlama noktasına sahip özel bir davranışı" kullanıma sunmak bir etkinlik yazarın sağlar. Örneğin, <xref:System.Activities.Statements.ForEach%601> etkinliği içeriyor (öğe koleksiyonu üzerinde çalıştığı), bir <xref:System.Activities.ActivityAction> Etkinlik geçerli yineleme öğede çalışır davranışı takın kullanıcıya izin verir.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Açık **ActivityAction.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`