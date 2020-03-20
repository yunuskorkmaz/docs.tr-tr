---
title: Genişletilmiş Koruma İlkesi
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 3a5b1c7f296c68d407f0217963dec56f53e9a08a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144728"
---
# <a name="extended-protection-policy"></a>Genişletilmiş Koruma İlkesi
Genişletilmiş Koruma, ortadaki adam (MITM) saldırılarına karşı koruma sağlayan bir güvenlik girişimidir. MITM saldırısı, Bir MITM'nin istemcinin kimlik bilgilerini alıp bir sunucuya ilettiği bir güvenlik tehdididir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Genişletilmiş koruma  
  
## <a name="discussion"></a>Tartışma  
 Uygulamalar HTTPS kullanarak Kerberos, Digest veya NTLM kullanılarak kimlik doğrulaması yaptığında, önce bir Aktarım Düzeyi Güvenliği (TLS) kanalı kurulur ve ardından güvenli kanal kullanılarak kimlik doğrulaması gerçekleşir. Ancak, SSL tarafından oluşturulan oturum anahtarı ile kimlik doğrulama sırasında oluşturulan oturum anahtarı arasında bir bağlama yoktur. Herhangi bir MITM istemci ve sunucu arasında kendini kurabilir ve aktarım kanalının kendisi güvenli olsa bile istemciden gelen istekleri iletmeye başlayabilir, çünkü sunucunun istemciden güvenli kanal oluşturulup oluşturulmadığını bilmenin bir yolu yoktur veya Bir MITM. Bu senaryodaki çözüm, dış TLS kanalını, sunucunun MITM olup olmadığını algılayabileceği iç kimlik doğrulama kanalıyla bağlamaktır.  
  
> [!NOTE]
> Bu örnek yalnızca IIS'de barındırıldığında çalışır ve Cassini - Visual Studio Development Server'da çalışamaz çünkü Cassini HTTPS'yi desteklemez.  
  
> [!NOTE]
> Bu özellik şu anda yalnızca Windows 7'de kullanılabilir. Aşağıdaki adımlar Windows 7'ye özgüdir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. **Denetim Panelinden**İnternet Bilgi Hizmetleri Yükleyin, **Programlar Ekle/Kaldır**, **Windows Özellikleri**.  
  
2. **Windows Özellikleri,** **Internet Bilgi Hizmetleri,** **World Wide Web Services,** **Güvenlik**ve Windows Kimlik **Doğrulama'da Windows Kimlik Doğrulama'yı** **yükleyin.**  
  
3. **Windows Özellikler** **Windows İletişim Vakfı HTTP Etkinleştirme** yükleyin , Microsoft **.NET Framework 3.5.1**, ve **Windows Communication Foundation HTTP Etkinleştirme**.  
  
4. Bu örnek, istemcinin sunucuyla güvenli bir kanal oluşturmasını gerektirir, bu nedenle Internet Information Services (IIS) Manager'dan yüklenebilecek bir sunucu sertifikasının bulunmasını gerektirir.  
  
    1. IIS Yöneticisi'ni açın. Kök düğüm (makine adı) seçildiğinde **Özellik Görünümü** sekmesinde görünen **Sunucu sertifikaları**aç.  
  
    2. Bu örneği test etmek amacıyla, kendi imzalı bir sertifika oluşturun. Internet Explorer'ın sertifikanın güvenli olmaması konusunda size soru saçması istemiyorsanız, sertifikayı Güvenilen Sertifika Kökü yetkilisi deposuna yükleyin.  
  
5. Varsayılan Web sitesi için **Eylemler** bölmesini açın. **Siteyi Edit**, **Ciltler'e**tıklayın. 443 numaralı bağlantı noktası yla, zaten mevcut değilse, https türünü bir tür olarak ekleyin. Önceki adımda oluşturulan SSL sertifikasını atayın.  
  
6. Hizmeti oluşturun. Bu, IIS'de sanal bir dizin oluşturur ve hizmetin Barındırılan Web'de barındırılması için gereken .dll, .svc ve .config dosyalarını kopyalar.  
  
7. IIS Yöneticisi'ni açın. Bir önceki adımda oluşturulan sanal dizinin **(ExtendedProtection)** sağ tıkla.'ya tıklayın. **Uygulamaya Dönüştür'ü**seçin.  
  
8. Bu sanal dizin için IIS Manager'da **Kimlik Doğrulama** modüllerini açın ve Windows **Kimlik Doğrulama'yı etkinleştirin.**  
  
9. Bu sanal dizin için **Windows Kimlik Doğrulaması** altında **Gelişmiş Ayarlar'ı** açın ve **Gerekli**olarak ayarlayın.  
  
10. Bir tarayıcı penceresinden HTTPS URL'ye erişerek hizmeti test edebilirsiniz (Tam nitelikli bir etki alanı adı sağlayın). Bu URL'ye uzak bir makineden erişmek istiyorsanız, güvenlik duvarının gelen tüm HTTP ve HTTPS bağlantıları için açıldığından emin olun.  
  
11. İstemci yapılandırma dosyasını açın ve istemci veya yerine gelen bitiş noktası `<<full_machine_name>>`adresi özniteliği için tam nitelikli bir etki alanı adı sağlayın.  
  
12. İstemciyi çalıştırın. İstemci, güvenli bir kanal oluşturan ve genişletilmiş koruma kullanan hizmetle iletişim kurar.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
