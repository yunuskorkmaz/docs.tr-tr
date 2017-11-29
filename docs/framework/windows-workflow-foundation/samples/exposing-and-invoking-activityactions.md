---
title: "Gösterme ve ActivityActions çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8a87e4463689e9301045a55b16af46cb037c1fa5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="exposing-and-invoking-activityactions"></a>Gösterme ve ActivityActions çağırma
Bu örnek sahip özel bir aktivite geliştirme yapmayı gösteren bir <xref:System.Activities.ActivityAction>. Ayrıca uygulaması sağlayarak bu etkinliği kullanın yapmayı gösteren <xref:System.Activities.ActivityAction>.  
  
 Bir <xref:System.Activities.ActivityAction> belirli imzaları ile "delik burada etkinliği kullanıcı takın özel bir davranış" kullanıma sunmak bir etkinlik Yazar verir. Örneğin, <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` etkinliği (öğeleri koleksiyonu faaliyet), sahip bir <xref:System.Activities.ActivityAction> Etkinlik geçerli yineleme öğede çalışır davranışı takın kullanıcıya izin verir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Açık **ActivityAction.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`  
  
## <a name="see-also"></a>Ayrıca Bkz.
