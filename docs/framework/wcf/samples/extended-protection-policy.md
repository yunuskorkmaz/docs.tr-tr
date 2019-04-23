---
title: Genişletilmiş Koruma İlkesi
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 645b48b3c7ce3daaaedac372ba5ba6fd5edfc8f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768429"
---
# <a name="extended-protection-policy"></a>Genişletilmiş Koruma İlkesi
Genişletilmiş koruma, ADAM-de-adam (MITM) saldırılarına karşı korumaya yönelik bir güvenlik girişimidir. MITM saldırı bir güvenlik tehdididir bir MITM istemci kimlik bilgilerini alır ve bir sunucuya iletir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Genişletilmiş koruma  
  
## <a name="discussion"></a>Tartışma  
 Uygulamalar, Kerberos, Özet veya HTTPS kullanarak NTLM kullanarak kimlik doğrulaması sırasında aktarım düzeyi güvenlik (TLS) kanalı ilk kurulur ve ardından kimlik doğrulama kullanarak güvenli kanal gerçekleşir. Ancak, SSL ile oluşturulan oturum anahtarı ile kimlik doğrulaması sırasında oluşturulan oturum anahtarı arasında hiçbir bağlama yok. Tüm MITM kendi istemci ve sunucu arasında kurmak ve sunucu güvenli kanal istemciden kurulan olmadığını olduğunu bilmesinin imkanı olduğundan taşıma kanalının güvenli olsa bile, istemciden istekleri iletme Başlat veya bir MITM. Bu senaryoda sunucunun bir MITM olup olmadığını Algıla şekilde iç kimlik doğrulaması kanal ile dış TLS kanalına bağlamak için çözümüdür.  
  
> [!NOTE]
>  Bu örnek, yalnızca IIS üzerinde barındırıldığında çalışır ve HTTPS Cassini'ye desteklemediğinden Cassini'ye – Visual Studio geliştirme sunucusu çalışamaz.  
  
> [!NOTE]
>  Bu özellik şu anda yalnızca Windows 7'de kullanılabilir. Aşağıdaki adımlar, Windows 7'ye özeldir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Internet Information Services yükleme **Denetim Masası**, **Program Ekle/Kaldır**, **Windows özellikleri**.  
  
2. Yükleme **Windows kimlik doğrulaması** içinde **Windows özellikleri**, **Internet Information Services**, **World Wide Web Hizmetleri**,  **Güvenlik**, ve **Windows kimlik doğrulaması**.  
  
3. Yükleme **Windows Communication Foundation HTTP etkinleştirme** içinde **Windows özellikleri**, **Microsoft .NET Framework 3.5.1**, ve **Windows iletişimi Foundation HTTP etkinleştirme**.  
  
4. Bu örnek, Internet Information Services (IIS) Yöneticisi'nden yüklenebilecek bir sunucu sertifikası varlığını gerektirir böylece sunucu ile güvenli bir kanal oluşturmak istemci gerektirir.  
  
    1.  IIS Yöneticisi'ni açın. Açık **sunucu sertifikaları**, içinde göründüğü **özellik görünümü** (makine adı) kök düğümü seçildiğinde sekme.  
  
    2.  Bu örnek test amacıyla otomatik olarak imzalanan bir sertifika oluşturun. Internet Explorer'ı güvenli olmadığı hakkında sertifika istemek için istemiyorsanız, sertifikayı güvenilen kök sertifika yetkilisi depolarında yükleyin.  
  
5. Açık **eylemleri** bölmesinde varsayılan Web sitesi için. Tıklayın **Site Düzenle**, **bağlamaları**. Bir tür olarak HTTPS eklemek henüz yoksa, bağlantı noktası numarası 443'tür. Önceki adımda oluşturulan SSL sertifika atayın.  
  
6. Derleme hizmeti. Bu IIS sanal dizini oluşturur ve .dll, .svc ve .config barındırılan Web hizmeti için gereken dosyaları kopyalar.  
  
7. IIS Yöneticisi'ni açın. Sanal dizin sağ tıklayın (**ExtendedProtection**), önceki adımda oluşturulan. Seçin **uygulamasına dönüştürün**.  
  
8. Açık **kimlik doğrulaması** bu sanal dizin ve etkinleştirmek için IIS Yöneticisi'nde Modülü **Windows kimlik doğrulaması**.  
  
9. Açık **Gelişmiş ayarlar** altında **Windows kimlik doğrulaması** bu sanal dizin için ve **gerekli**.  
  
10. HTTPS URL'sini bir tarayıcı penceresi (tam etki alanı adı belirtin) erişerek hizmetini test edebilirsiniz. Bu URL, uzak bir makineden erişmek istiyorsanız, güvenlik duvarı tüm gelen HTTP ve HTTPS bağlantıları için açık olduğundan emin olun.  
  
11. İstemci yapılandırma dosyasını açın ve yerini alan istemci veya uç nokta adresi özniteliği için bir tam etki alanı adı sağlayın `<<full_machine_name>>`.  
  
12. İstemciyi çalıştırın. İstemci, güvenli bir kanal oluşturur ve genişletilmiş koruma kullanıldığı hizmetiyle iletişim kurar.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
