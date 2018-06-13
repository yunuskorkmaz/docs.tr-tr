---
title: Gönderme ve hata işleme
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 6796b4daccd88adc3bd006f454ce96ca155fbcb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516132"
---
# <a name="sending-and-handling-faults"></a>Gönderme ve hata işleme
Bu örnek nasıl kullanılacağı ortaya <xref:System.ServiceModel.Activities.SendReply> ve <xref:System.ServiceModel.Activities.ReceiveReply> Mesajlaşma etkinlikleri beklenen ve beklenmeyen hataları alıp göndermek için. Bu senaryoda, ilk istemci isteği içinde bulunan bir beklenen hatasına sonuçlarında kendi <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> koleksiyonu. Son istekten başarılı olmadan önce beklenmeyen hataları alma sonraki birkaç istemci istekleri neden olur.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinleri olan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.  
  
2.  Faults.sln çözüm dosyasını açın.  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
4.  Hizmet projesini çalıştırın.  
  
    1.  İçinde **Çözüm Gezgini**, sağ `FaultService` proje ve seçin **başlangıç projesi olarak ayarla**.  
  
    2.  CTRL + F5 tuşuna basın.  
  
5.  Başka bir kopyasını açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinleri olan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.  
  
6.  Faults.sln çözüm dosyasını açın.  
  
7.  İstemci projesini çalıştırın.  
  
    1.  İçinde **Çözüm Gezgini**, sağ `FaultClient` proje ve seçin **başlangıç projesi olarak ayarla**.  
  
    2.  CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`