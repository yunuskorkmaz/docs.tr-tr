---
title: Bağıntılı hesaplayıcı
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 71cfdd0906ef20ec36b76ef5e508a4551b9fe3fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384677"
---
# <a name="correlated-calculator"></a>Bağıntılı hesaplayıcı
Bu örnek ileti etkinlikleri kullanma işlemini gösterir (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>) iletiyi bir parametre temel içerik temelli bağıntı ile Tasarımcısı'nda. Bu senaryoda paralel bir konvoy hesaplayıcı işlemlerdir. Hem bir örneği hem de bir bağıntı (temel `CalculatorId`) iş akışı ve daha sonraki iletileri aynı ilk ileti gönderildiğinde oluşturulan `CalculatorId` sıfırlama işlemi çağrılana kadar bu örneğe gönderilir. İstemci hizmetiyle iletişim kurmak için bir kod tabanlı istemci proxy kullanan bir WPF uygulaması olarak uygulanır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Başlangıç [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükseltilmiş izinler For.sln çözüm dosyasını açın.  
  
    1.  İçeren klasöre gidin [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Devenv.exe sağ tıklayıp **yönetici olarak çalıştır**.  
  
2.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CorrelatedCalculator.sln çözüm dosyasını açın.  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
4.  Hizmet projeyi çalıştırmak için CTRL + F5 tuşlarına basın.  
  
5.  Hazır ve dinleme iletileri, Çözüm Gezgini'nde Hizmet başladıktan sonra istemci projesini sağ tıklayın ve çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`