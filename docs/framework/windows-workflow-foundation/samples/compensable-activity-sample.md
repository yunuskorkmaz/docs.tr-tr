---
title: Compensable etkinlik örnek
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 8008eaaca062723cab1efabfb1b25018353c73b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="compensable-activity-sample"></a>Compensable etkinlik örnek
Bu örnek nasıl kullanılacağı ortaya `CompensableActivity` normal yürütme sırasında belirli bir eylem için yapılacak işleri ve o eylemi dengelemek için daha sonra gerekirse yapılması gerekli olan iş tanımlamak için etkinlik.  Windows Workflow Foundation (WF) compensable iş birimleri nasıl tanımlanabilir örnek ilk bölümü gösterir kullanarak bir `CompensableActivity` etkinliği ve nasıl başarılı çalıştırılmasıyla yürütülür.  Örnek ikinci bölümü nasıl compensable iş aynı birimleri otomatik olarak maaş beklenmeyen bir olay isabet ve iş akışı örneği iptal ilgilenebilmek gösterir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Visual Studio 2010 kullanarak CompensableActivity.sln açın.  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  F5 tuşuna basarak uygulamayı çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`