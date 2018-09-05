---
title: ReceiveContext etkinleştirilmiş WCF kanalları
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: d7f80d0874606129876fbf7dfa30c0327680b922
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515936"
---
# <a name="receivecontext-enabled-wcf-channels"></a>ReceiveContext etkinleştirilmiş WCF kanalları
Bu örnek kullanışlılığını gösterir <xref:System.ServiceModel.Channels.ReceiveContext>-etkinleştirilmiş WCF kanalları. Örnek Ürün NetMSMQ kanalı kullanılarak iki sayının bulmak için bir hizmet uygular.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> Sınıfı, iletinin erişmek veya iletinin içeriğini bile inceledikten sonra daha fazla işleme için sıradaki bırakın karar vermek bir uygulama sağlar. Bu örnekte, bir istemci rastgele tamsayı işlem bir kuyruğa gönderir. `ProductCalculator` Hizmet iletileri alır ve ürün hesaplanan olup olmadığını belirlemek için tamsayılardır iletisi içeriği olup olmadığını denetler. Hizmet işlemi ürün işlem değil, ileti yeniden kuyruğa alınan ve kuyrukta dinleme hizmeti tarafından tekrar alınabilir.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Microsoft Message Queuing (MSMQ) yüklendiğinden emin olun.  
  
    1.  MSMQ yüklemek için [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:  
  
        1.  İçinde **Sunucu Yöneticisi'ni**, tıklayın **özellikleri**.  
  
        2.  Sağ bölmede **özellikler özeti**, tıklayın **Özellik Ekle**.  
  
        3.  Sonuçta elde edilen penceresinde **Message Queuing**.  
  
        4.  Genişletin **Message Queuing Hizmetleri**.  
  
        5.  Tıklayın **Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için) ve ardından **HTTP desteği**.  
  
        6.  Tıklayın **sonraki**ve ardından **yükleme**.  
  
    2.  MSMQ yüklemek için [!INCLUDE[wv](../../../../includes/wv-md.md)]:  
  
        1.  Açık **Denetim Masası**.  
  
        2.  Tıklayın **programlar** ve sonra **programlar ve Özellikler**, tıklayın **Windows özelliklerini açma ve kapatma**.  
  
        3.  Genişletin **Microsoft Message Queue (MSMQ) sunucusu**, genişletme **Microsoft Message Queue (MSMQ) Server Core**ve sonra yüklemek aşağıdaki olan Message Queuing özellikler için onay kutularını seçin:  
  
            -   Message Queuing sunucusu  
  
            -   MSMQ Active Directory etki alanı Hizmetleri Tümleştirme (bir etki alanına katılmış bilgisayarlar için)  
  
            -   MSMQ HTTP desteği  
  
        4.  **Tamam**'ı tıklatın.  
  
        5.  Bilgisayarı yeniden başlatmanız istenirse, tıklayın **Tamam** yüklemeyi tamamlamak için.  
  
2.  Emin [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] bilgisayara yüklendi.  
  
3.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ReceiveContextProductGenerator.sln çözüm dosyasını açın.  
  
4.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
5.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.
