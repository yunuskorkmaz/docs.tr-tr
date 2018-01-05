---
title: "Compensable etkinlik örnek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2fd8d38e95dbddbe85f11bf88ef500697b6c02a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="compensable-activity-sample"></a>Compensable etkinlik örnek
Bu örnek nasıl kullanılacağı ortaya `CompensableActivity` normal yürütme sırasında belirli bir eylem için yapılacak işleri ve o eylemi dengelemek için daha sonra gerekirse yapılması gerekli olan iş tanımlamak için etkinlik.  Compensable iş birimleri içinde nasıl tanımlanabilir örnek ilk bölümü gösterir [!INCLUDE[wf](../../../../includes/wf-md.md)] kullanarak bir `CompensableActivity` etkinliği ve nasıl başarılı çalıştırılmasıyla yürütülür.  Örnek ikinci bölümü nasıl compensable iş aynı birimleri otomatik olarak maaş beklenmeyen bir olay isabet ve iş akışı örneği iptal ilgilenebilmek gösterir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Visual Studio 2010 kullanarak CompensableActivity.sln açın.  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  F5 tuşuna basarak uygulamayı çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`