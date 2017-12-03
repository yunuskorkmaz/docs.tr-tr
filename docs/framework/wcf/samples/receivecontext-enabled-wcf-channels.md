---
title: "ReceiveContext etkinleştirilmiş WCF kanalları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 729bf8bd1371bf64b9b05a235331120608824083
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="receivecontext-enabled-wcf-channels"></a>ReceiveContext etkinleştirilmiş WCF kanalları
Bu örnek yararlılığı gösteren <xref:System.ServiceModel.Channels.ReceiveContext>-WCF kanalları etkin. Örnek NetMSMQ kanalı kullanılarak iki sayının çarpımını bulmak için bir hizmet uygular.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> Sınıfı erişim iletisi veya iletinin içeriğini bile inceledikten sonra daha fazla işleme için sıraya bırakın karar vermek bir uygulama sağlar. Bu örnekte, bir istemci için bir işlem sırası rastgele tamsayılar gönderir. `ProductCalculator` Hizmeti iletileri alır ve ürünün hesaplanan olup olmadığını belirlemek için tamsayı olduğunu iletisi içeriği olup olmadığını denetler. Hizmet işlemini ürün işlem değil, ileti geri sıraya konur ve sıra üzerinde dinleme hizmeti tarafından tekrar alınabilir.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Microsoft Message Queuing (MSMQ) yüklü olduğundan emin olun.  
  
    1.  MSMQ yüklemek için [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:  
  
        1.  İçinde **Sunucu Yöneticisi'ni**, tıklatın **özellikleri**.  
  
        2.  Sağ bölmede altında **Özellik Özeti**, tıklatın **Özellik Ekle**.  
  
        3.  Sonuçta elde edilen penceresinde **Message Queuing**.  
  
        4.  Genişletme **Message Queuing Hizmetleri**.  
  
        5.  Tıklatın **Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için) ve ardından **HTTP desteği**.  
  
        6.  Tıklatın **sonraki**ve ardından **yükleme**.  
  
    2.  MSMQ yüklemek için [!INCLUDE[wv](../../../../includes/wv-md.md)]:  
  
        1.  Açık **Denetim Masası**.  
  
        2.  Tıklatın **programları** ve ardından, **programlar ve Özellikler**, tıklatın **Windows özelliklerini açma ve kapatma**.  
  
        3.  Genişletme **Microsoft Message Queue (MSMQ) sunucusu**, genişletin **Microsoft Message Queue (MSMQ) Sunucu Çekirdeği**ve ardından yüklemek aşağıdaki olan Message Queuing özelliklerin onay kutularını seçin:  
  
            -   Message Queuing sunucusu  
  
            -   MSMQ Active Directory etki alanı Hizmetleri Tümleştirme (bir etki alanına katılmış bilgisayarlar için)  
  
            -   MSMQ HTTP desteği  
  
        4.  **Tamam**'ı tıklatın.  
  
        5.  Bilgisayarı yeniden başlatmanız istenirse, tıklatın **Tamam** yüklemeyi tamamlayın.  
  
2.  Emin [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] bilgisayara yüklendi.  
  
3.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ReceiveContextProductGenerator.sln çözüm dosyasını açın.  
  
4.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
5.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.
