---
title: Hata gönderme ve işleme
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 896f209e7daeeab2bb33c1fde15298aae96c8776
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037717"
---
# <a name="sending-and-handling-faults"></a>Hata gönderme ve işleme
Bu örnek nasıl kullanılacağını gösterir <xref:System.ServiceModel.Activities.SendReply> ve <xref:System.ServiceModel.Activities.ReceiveReply> beklenen ve beklenmedik hataları gönderip etkinlikler ileti. Bu senaryoda, ilk istemci isteği içinde bulunan bir beklenen hata sonuçlarında kendi <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> koleksiyonu. Sonraki birkaç istemci istekleri son istek başarılı olmadan önce beklenmeyen hataları alma neden olur.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinlerle [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini seçip **yönetici olarak çalıştır**.  
  
2.  Faults.sln çözüm dosyasını açın.  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
4.  Hizmet projeyi çalıştırın.  
  
    1.  İçinde **Çözüm Gezgini**, sağ `FaultService` seçin ve proje **başlangıç projesi olarak ayarla**.  
  
    2.  CTRL + F5 tuşlarına basın.  
  
5.  Başka bir kopyasını açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinlerle [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini seçip **yönetici olarak çalıştır**.  
  
6.  Faults.sln çözüm dosyasını açın.  
  
7.  İstemci projesini çalıştırın.  
  
    1.  İçinde **Çözüm Gezgini**, sağ `FaultClient` seçin ve proje **başlangıç projesi olarak ayarla**.  
  
    2.  CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`