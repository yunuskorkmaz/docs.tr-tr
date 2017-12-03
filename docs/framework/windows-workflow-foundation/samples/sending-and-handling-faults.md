---
title: "Gönderme ve hata işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97a957932c04f52a4a77d7d636cda08a63121f2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`