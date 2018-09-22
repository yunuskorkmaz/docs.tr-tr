---
title: Compensable etkinliği örneği
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583333"
---
# <a name="compensable-activity-sample"></a>Compensable etkinliği örneği
Bu örnek nasıl kullanılacağını gösterir `CompensableActivity` normal yürütme sırasında belirli bir eylemi için yapılacak işleri ve bu eylemi dengelemek için daha sonra gerekirse yapılması gereken çalışmayı tanımlamak için etkinlik.  Windows Workflow Foundation (WF) compensable iş birimleri nasıl tanımlanabilir örnek ilk bölümü gösterir kullanarak bir `CompensableActivity` etkinliği ve nasıl başarılı bir çalıştırmada yürütülür.  İkinci örnek bölümü nasıl aynı compensable iş birimleri otomatik olarak maaş beklenmeyen bir olay ulaşılır ve iş akışı örneği iptal ilgileniriz gösterir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Visual Studio 2010'u kullanarak, CompensableActivity.sln açın.  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  F5 tuşuna basarak uygulamayı çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`