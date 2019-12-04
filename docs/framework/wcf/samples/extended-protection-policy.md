---
title: Genişletilmiş Koruma İlkesi
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 1cb6d44e8f6ee8f54f776453e5a1783ab0cfa4f0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716416"
---
# <a name="extended-protection-policy"></a>Genişletilmiş Koruma İlkesi
Genişletilmiş koruma, ortadaki adam (MITD) saldırılarına karşı koruma için bir güvenlik girişimidir. Bir mitd saldırısı, bir MITD 'nin istemcinin kimlik bilgilerini aldığı ve sunucuya ileten bir güvenlik tehdidi olur.  
  
## <a name="demonstrates"></a>Gösterir  
 Genişletilmiş koruma  
  
## <a name="discussion"></a>Tartışma  
 Uygulamalar HTTPS kullanarak Kerberos, Özet veya NTLM kullanarak kimlik doğrulaması yaparken, önce bir aktarım düzeyi güvenlik (TLS) kanalı oluşturulur ve ardından güvenli kanal kullanılarak kimlik doğrulaması gerçekleştirilir. Ancak, SSL tarafından oluşturulan oturum anahtarı ve kimlik doğrulaması sırasında oluşturulan oturum anahtarı arasında bir bağlama yoktur. Herhangi bir MITD, istemci ve sunucu arasında kendisini oluşturabilir ve aktarım kanalının kendisi güvenli olsa bile istemciden gelen istekleri istemciye iletmeyi başlatabilir, çünkü sunucu güvenli kanalın istemciden yapılıp yapılmadığını bilmiyor. ya da bir MITD. Bu senaryodaki çözüm, dış TLS kanalını, sunucunun bir MITD olup olmadığını algılayabilmesi için iç kimlik doğrulama kanalına bağlamalıdır.  
  
> [!NOTE]
> Bu örnek yalnızca IIS üzerinde barındırıldığında çalışır ve Cassini, HTTPS 'yi desteklemediğinden Cassini – Visual Studio geliştirme sunucusu üzerinde çalışmaz.  
  
> [!NOTE]
> Bu özellik şu anda yalnızca Windows 7 ' de kullanılabilir. Aşağıdaki adımlar Windows 7 ' ye özgüdür.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. **Denetim Masası**, **Program Ekle/Kaldır**, **Windows özellikleri**' nden Internet Information Services yükler.  
  
2. Windows **özellikleri**, **Internet Information Services**, **World Wide Web Hizmetleri**, **güvenlik**ve **Windows kimlik doğrulaması**'nda **Windows kimlik doğrulamasını** yükler.  
  
3. **Windows özellikleri**, **Microsoft .NET Framework 3.5.1**ve **Windows Communication Foundation HTTP etkinleştirmesi** **Windows Communication Foundation HTTP Etkinleştirme** 'yi yükler.  
  
4. Bu örnek, istemcisinin sunucu ile güvenli bir kanal kurmasını gerektirir, bu nedenle Internet Information Services (IIS) Yöneticisi 'nden yüklenebilen bir sunucu sertifikası bulunması gerekir.  
  
    1. IIS Yöneticisi'ni açın. Kök düğüm (makine adı) seçildiğinde **Özellik görünümü** sekmesinde görünen **sunucu sertifikaları**' nı açın.  
  
    2. Bu örneği test etmek amacıyla kendinden imzalı bir sertifika oluşturun. Internet Explorer 'ın sertifikayı güvenli hale getirmeye yönelik olarak sormasını istemiyorsanız, sertifikayı güvenilir sertifika kök yetkilisi deposuna yükleyebilirsiniz.  
  
5. Varsayılan Web sitesi için **Eylemler** bölmesini açın. Site, **bağlamaları** **Düzenle**' ye tıklayın. Zaten mevcut değilse HTTPS 'yi bir tür olarak ekleyin, bağlantı noktası numarası 443. Önceki adımda oluşturulan SSL sertifikasını atayın.  
  
6. Hizmeti oluşturun. Bu, IIS 'de bir sanal dizin oluşturur ve hizmetin Web 'de barındırılması için. dll,. svc ve. config dosyalarını gerektiği şekilde kopyalar.  
  
7. IIS Yöneticisi'ni açın. Önceki adımda oluşturulan sanal dizine (**ExtendedProtection**) sağ tıklayın. **Uygulamaya Dönüştür**' ü seçin.  
  
8. Bu sanal dizin için IIS Yöneticisi 'nde **kimlik doğrulama** modülünü açın ve **Windows kimlik doğrulamasını**etkinleştirin.  
  
9. Bu sanal dizin için **Windows kimlik doğrulaması** altında **Gelişmiş ayarları** açın ve **gerekli**olarak ayarlayın.  
  
10. Bir tarayıcı penceresinden (tam etki alanı adı sağlayın) HTTPS URL 'sine erişerek hizmeti test edebilirsiniz. Bu URL 'YI uzak bir makineden erişmek istiyorsanız, tüm gelen HTTP ve HTTPS bağlantıları için güvenlik duvarının açık olduğundan emin olun.  
  
11. İstemci yapılandırma dosyasını açın ve `<<full_machine_name>>`yerine geçen istemci veya uç nokta adresi özniteliği için tam etki alanı adı sağlayın.  
  
12. İstemcisini çalıştırın. İstemci, güvenli bir kanal kuran ve genişletilmiş koruma kullanan hizmetle iletişim kurar.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
