---
title: Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 8d0b80930424f0d8529f2b035a8e1167f361f99a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303953"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri
Internet Information Services (IIS) güvenli şekilde iletişim kurması örnekleri çalıştırmak için oluşturma ve bir sunucu sertifikası yükleyin.  
  
## <a name="step-1-creating-certificates"></a>Adım 1. Sertifikaları oluşturma  
 Bilgisayarınız için bir sertifika oluşturmak için yönetici ayrıcalıklarıyla Visual Studio için geliştirici komut istemi açın ve her IIS ile güvenli iletişim kullanan örnekler dahil Setup.bat çalıştırın. Bu toplu iş dosyasını çalıştırmadan önce Makecert.exe içeren klasörün yolunu içerdiğinden emin olun. Aşağıdaki komut, Setup.bat sertifikayı oluşturmak için kullanılır.  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>Adım 2. Sertifikaları yükleme  
 Yeni oluşturduğunuz sertifikaları yüklemek için gerekli adımlar, IIS sürümünü kullandığınız bağlıdır.  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>IIS 5.1 (Windows XP) ve IIS 6. 0'ı (Windows Server 2003) IIS yükleme  
  
1. Internet Bilgi Hizmetleri Yöneticisi MMC ek bileşenini açın.  
  
2. Varsayılan Web sitesini sağ tıklatıp **özellikleri**.  
  
3. Seçin **dizin güvenliği** sekmesi.  
  
4. Tıklayın **sunucu sertifikası** düğmesi. Web sunucusu sertifikası Sihirbazı başlar.  
  
5. Sihirbazı tamamlayın. Bir sertifika atama seçeneğini seçin. ServiceModelSamples HTTPS sunucu sertifikasına, görüntülenen sertifika listesinden seçin.  
  
     ![IIS Sertifika Sihirbazı](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6. Test hizmetine erişiminizi bir tarayıcıda HTTPS adresi kullanarak `https://localhost/servicemodelsamples/service.svc`.  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>SSL, daha önce Httpcfg.exe kullanılarak yapılandırıldıysa  
  
1. MakeCert.exe (veya çalıştırma Setup.bat) sunucu sertifikası oluşturmak için kullanın.  
  
2. IIS Yöneticisi'ni çalıştırın ve önceki adımlara göre sertifika yükleyin.  
  
3. Aşağıdaki kod satırını, istemci programa ekleyin.  
  
> [!IMPORTANT]
>  Bu kod yalnızca gereklidir test sertifikaları Makecert.exe tarafından oluşturulanlar gibi. Üretim kodu için önerilmez.  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>IIS 7.0 (Windows Vista ve Windows Server 2008) IIS yüklemek için  
  
1. Gelen **Başlat** menüsünde, tıklayın **çalıştırın**, yazın **inetmgr** Internet Information Services (IIS) MMC ek bileşenini açın.  
  
2. Sağ **varsayılan Web sitesi** seçip **bağlamaları Düzenle...**  
  
3. Tıklayın **Ekle** düğmesini **Site bağlamaları** iletişim kutusu.  
  
4. Seçin **HTTPS** gelen **türü** aşağı açılan listesi.  
  
5. Seçin **ServiceModelSamples HTTPS sunucusu** gelen **SSL sertifikası** aşağı açılan liste ve tıklatın **Tamam**.  
  
6. Test hizmetine erişiminizi bir tarayıcıda HTTPS adresi kullanarak `https://localhost/servicemodelsamples/service.svc`.  
  
> [!NOTE]
>  Yüklediğiniz test sertifikası güvenilen bir sertifika olduğundan, bu sertifika ile güvenli hale getirilmiş yerel Web adresleri göz atarken ek Internet Explorer güvenlik uyarıları karşılaşabilirsiniz.  
  
## <a name="removing-certificates"></a>Sertifikalarını kaldırma  
  
-   Internet Information Services Manager daha önce yönlendirilir, ancak sertifika veya onu eklemek yerine bağlamayı Kaldır'ı kullanın.  
  
-   Aşağıdaki komutu kullanarak bilgisayar sertifikası kaldırın.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
