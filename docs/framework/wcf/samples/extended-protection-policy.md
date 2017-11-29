---
title: "Genişletilmiş Koruma İlkesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e2d9389487bb95fe13b5c12b6f861ae30e29677
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="extended-protection-policy"></a>Genişletilmiş Koruma İlkesi
Genişletilmiş koruma, ADAM-in--middle (MITM) saldırılarına karşı korumak için bir güvenlik girişimidir. MITM saldırı bir güvenlik tehdididir bir MITM bir istemcinin kimlik bilgilerini alır ve bir sunucuya iletir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Genişletilmiş koruma  
  
## <a name="discussion"></a>Tartışma  
 Kerberos, Özet veya HTTPS kullanarak NTLM kullanarak uygulamaları kimliğini doğrularken bir aktarım düzeyi güvenlik (TLS) kanalı ilk kurulduktan sonra ve ardından kimlik doğrulaması güvenli kanalı kullanılarak gerçekleşir. Ancak, SSL ile oluşturulan oturum anahtarı ile kimlik doğrulaması sırasında oluşturulan oturum anahtarı arasındaki hiçbir bağlama yok. Tüm MITM kendisini istemci ve sunucu arasında kurmak ve sunucu güvenli kanal istemciden kurulan olup olmadığını bilmek hiçbir şekilde olduğundan taşıma kanalını güvenli olsa bile, istemciden istekleri iletme Başlat veya bir MITM. Bu senaryoda sağlayacak şekilde sunucunun bir MITM olup olmadığını Algıla iç kimlik doğrulama kanalı ile dış TLS kanalına bağlamak için çözümüdür.  
  
> [!NOTE]
>  Bu örnek yalnızca IIS üzerinde barındırıldığında çalışır ve Cassini HTTPS desteklemediğinden Cassini – Visual Studio geliştirme sunucusu çalışamaz.  
  
> [!NOTE]
>  Bu özellik şu anda yalnızca Windows 7'de kullanılabilir. Aşağıdaki adımlar, Windows 7'ye özeldir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Internet Information Services gelen yükleme **Denetim Masası**, **Program Ekle/Kaldır**, **Windows özelliklerini**.  
  
2.  Yükleme **Windows kimlik doğrulaması** içinde **Windows özelliklerini**, **Internet Information Services**, **World Wide Web Hizmetleri**,  **Güvenlik**, ve **Windows kimlik doğrulaması**.  
  
3.  Yükleme **Windows Communication Foundation HTTP etkinleştirmesi** içinde **Windows özelliklerini**, **Microsoft .NET Framework 3.5.1**, ve **Windows iletişimi Foundation HTTP etkinleştirme**.  
  
4.  Bu örnek, Internet Information Services (IIS) Yöneticisi'nden yüklenebilecek bir sunucu sertifikası varlığını gerekir böylece sunucu ile güvenli bir kanal oluşturmak için istemcinin gerektirir.  
  
    1.  IIS Yöneticisi'ni açın. Açık **sunucu sertifikaları**, göründüğü içinde **özellik görünümü** sekmesinde (makine adı) kök düğümü seçildiğinde.  
  
    2.  Bu örnek test amacıyla, otomatik olarak imzalanan bir sertifika oluşturun. Internet Explorer'ı güvenli olmadığı sertifika hakkında soracak şekilde istemiyorsanız, sertifikayı güvenilen kök sertifika yetkilisi depolarında yükleyin.  
  
5.  Açık **Eylemler** varsayılan Web sitesi için bölmesi. Tıklatın **Düzenle Site**, **bağlamaları**. Bir tür olarak HTTPS eklemek henüz yoksa, bağlantı noktası numarası 443'tür. Önceki adımda oluşturulan SSL sertifika atayın.  
  
6.  Hizmet oluşturun. Bu IIS içinde bir sanal dizin oluşturur ve .dll, .svc ve .config dosyaları barındırılan Web hizmeti için gerekli olarak kopyalar.  
  
7.  IIS Yöneticisi'ni açın. Sanal dizin sağ tıklayın (**ExtendedProtection**), önceki adımda oluşturulmuş. Seçin **uygulamasına dönüştürün**.  
  
8.  Açık **kimlik doğrulaması** bu sanal dizin ve etkinleştirmek için IIS Yöneticisi'nde Modülü **Windows kimlik doğrulaması**.  
  
9. Açık **Gelişmiş ayarları** altında **Windows kimlik doğrulaması** bu sanal dizin için ve ayarlamak **gerekli**.  
  
10. HTTPS URL'sini bir tarayıcı penceresi (bir tam etki alanı adı sağlayın) erişerek hizmetini test edebilirsiniz. Bu URL uzak bir makineden erişmek isterseniz, güvenlik duvarının tüm gelen HTTP ve HTTPS bağlantıları için açıldığında emin olun.  
  
11. İstemci yapılandırma dosyasını açın ve değiştirir istemci veya uç nokta adresi özniteliği için bir tam etki alanı ad `<<full_machine_name>>`.  
  
12. İstemciyi çalıştırın. İstemci, güvenli bir kanal oluşturur ve genişletilmiş koruma kullanan hizmeti ile iletişim kurar.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
