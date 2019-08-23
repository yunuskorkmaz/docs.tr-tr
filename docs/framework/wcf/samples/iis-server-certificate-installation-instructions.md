---
title: Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 50fa7f1094d4b05bcadb229072293da233a18a2b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931864"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri
Internet Information Services (IIS) ile güvenli bir şekilde iletişim kuran örnekleri çalıştırmak için bir sunucu sertifikası oluşturmanız ve kurmanız gerekir.  
  
## <a name="step-1-creating-certificates"></a>Adım 1. Sertifika oluşturma  
 Bilgisayarınız için bir sertifika oluşturmak üzere, yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve IIS ile güvenli iletişim kullanan her bir örnek için bulunan Setup. bat dosyasını çalıştırın. Bu toplu iş dosyasını çalıştırmadan önce yolun MakeCert. exe içeren klasörü içerdiğinden emin olun. Setup. bat ' de sertifikayı oluşturmak için aşağıdaki komut kullanılır.  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>Adım 2. Sertifikaları yükleme  
 Az önce oluşturduğunuz sertifikaları yüklemek için gereken adımlar kullandığınız IIS sürümüne bağlıdır.  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>IIS 5,1 (Windows XP) ve IIS 6,0 (Windows Server 2003) üzerinde IIS yüklemek için  
  
1. Internet Information Services Manager MMC ek bileşenini açın.  
  
2. Varsayılan Web sitesine sağ tıklayın ve **Özellikler**' i seçin.  
  
3. **Dizin Güvenliği** sekmesini seçin.  
  
4. **Sunucu sertifikası** düğmesine tıklayın. Web sunucusu sertifikası Sihirbazı başlatılır.  
  
5. Sihirbazı tamamlayın. Sertifika atama seçeneğini belirleyin. Görüntülenen sertifikalar listesinden ServiceModelSamples-HTTPS-Server sertifikasını seçin.  
  
     ![IIS sertifikası Sihirbazı](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6. HTTPS adresini `https://localhost/servicemodelsamples/service.svc`kullanarak bir tarayıcıda hizmete erişimi test edin.  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>SSL daha önce Httpcfg. exe kullanılarak yapılandırıldıysa  
  
1. Sunucu sertifikasını oluşturmak için MakeCert. exe (veya Setup. bat dosyasını çalıştırın) kullanın.  
  
2. IIS Yöneticisi 'ni çalıştırın ve önceki adımlara göre sertifikayı yükler.  
  
3. Aşağıdaki kod satırını istemci programına ekleyin.  
  
> [!IMPORTANT]
>  Bu kod yalnızca, MakeCert. exe tarafından oluşturulanlar gibi test sertifikaları için gereklidir. Üretim kodu için önerilmez.  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>IIS 7,0 (Windows Vista ve Windows Server 2008) üzerinde IIS yüklemek için  
  
1. **Başlat** menüsünde **Çalıştır**' a tıklayın ve ardından Internet INFORMATION SERVICES (IIS) MMC ek bileşenini açmak için **inetmgr** yazın.  
  
2. **Varsayılan Web sitesine** sağ tıklayın ve **bağlamaları Düzenle...** seçeneğini belirleyin.  
  
3. **Site bağlamaları** Iletişim kutusunun **Ekle** düğmesine tıklayın.  
  
4. **Tür** açılır listesinden **https** ' yi seçin.  
  
5. **SSL sertifikası** açılır listesinden **servicemodelsamples-HTTPS-Server** ' ı seçin ve **Tamam**' a tıklayın.  
  
6. HTTPS adresini `https://localhost/servicemodelsamples/service.svc`kullanarak bir tarayıcıda hizmete erişimi test edin.  
  
> [!NOTE]
> Yeni yüklediğiniz test sertifikası güvenilen bir sertifika olmadığından, bu sertifikayla güvenliği sağlanmış yerel web adreslerine gözatarken ek Internet Explorer güvenlik uyarılarıyla karşılaşabilirsiniz.  
  
## <a name="removing-certificates"></a>Sertifikaları kaldırma  
  
- Internet Information Services yöneticisini daha önce yönlendirildiğinden kullanın, ancak bunu eklemek yerine sertifikayı veya bağlamayı kaldırın.  
  
- Aşağıdaki komutu kullanarak bilgisayar sertifikasını kaldırın.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
