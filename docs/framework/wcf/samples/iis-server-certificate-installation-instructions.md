---
title: Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 46d1acf758dd50b881527a16570a1e4a45933958
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri
Internet Information Services (IIS) güvenli iletişim örnekleri çalıştırmak için oluşturma ve sunucu sertifikasını yüklemeniz gerekir.  
  
## <a name="step-1-creating-certificates"></a>Adım 1. Sertifikaları oluşturma  
 Bilgisayarınız için bir sertifika oluşturmak için yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve her IIS ile güvenli iletişim kullanmak örnekleri dahil Setup.bat çalıştırın. Bu toplu iş dosyasını çalıştırmadan önce Makecert.exe içeren klasörün yolunu içerdiğinden emin olun. Aşağıdaki komutu Setup.bat sertifikayı oluşturmak için kullanılır.  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>Adım 2. Sertifikaları yükleme  
 Yeni oluşturduğunuz sertifikaları yüklemek için gerekli olan adımları IIS sürümünü kullanmakta olduğunuz üzerinde bağlıdır.  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>IIS 5.1 (Windows XP) ve IIS 6. 0'ı (Windows Server 2003) IIS yüklemek için  
  
1.  Internet Bilgi Hizmetleri Yöneticisi'ni MMC ek bileşenini açın.  
  
2.  Varsayılan Web sitesini sağ tıklatıp **özellikleri**.  
  
3.  Seçin **dizin güvenliği** sekmesi.  
  
4.  Tıklatın **sunucu sertifikası** düğmesi. Web Sunucusu Sertifika Sihirbazı'nı başlatır.  
  
5.  Sihirbazı tamamlayın. Bir sertifika atama seçeneğini seçin. ServiceModelSamples HTTPS sunucusu sertifikasını görüntülenen sertifika listesinden seçin.  
  
     ![IIS Sertifika Sihirbazı](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6.  Test hizmetine erişim bir tarayıcıda HTTPS adresi kullanarak https://localhost/servicemodelsamples/service.svc.  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>SSL, daha önce Httpcfg.exe kullanılarak yapılandırıldıysa  
  
1.  MakeCert.exe (veya çalışma Setup.bat) sunucu sertifikası oluşturmak için kullanın.  
  
2.  IIS Yöneticisi'ni çalıştırın ve önceki adımları göre sertifika yükleyin.  
  
3.  Aşağıdaki kod satırını istemci programına ekleyin.  
  
> [!IMPORTANT]
>  Bu kod yalnızca gerekli olan test Makecert.exe tarafından oluşturulanlar gibi sertifikaları. Üretim kodu için önerilmez.  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>IIS 7.0 (Windows Vista ve Windows Server 2008) IIS yüklemek için  
  
1.  Gelen **Başlat** menüsünde tıklatın **çalıştırmak**, yazın **inetmgr** Internet Information Services (IIS) MMC ek bileşenini açmak için.  
  
2.  Sağ **varsayılan Web sitesi** seçip **bağlamaları Düzenle...**  
  
3.  Tıklatın **Ekle** düğmesine **Site bağlamaları** iletişim kutusu.  
  
4.  Seçin **HTTPS** gelen **türü** aşağı açılan liste.  
  
5.  Seçin **ServiceModelSamples HTTPS sunucusu** gelen **SSL sertifikası** aşağı açılan liste ve tıklatın **Tamam**.  
  
6.  Test hizmetine erişim bir tarayıcıda HTTPS adresi kullanarak https://localhost/servicemodelsamples/service.svc.  
  
> [!NOTE]
>  Yeni yüklediğiniz test sertifikası güvenilen bir sertifika olduğundan, bu sertifikası ile güvenli yerel Web adresler gözatarken ek Internet Explorer güvenlik uyarılarını karşılaşabilirsiniz.  
  
## <a name="removing-certificates"></a>Sertifikaları kaldırma  
  
-   Internet Information Services Yöneticisi, daha önce yönlendirilmiş ancak sertifika veya onu eklemek yerine bağlama Kaldır olarak kullanın.  
  
-   Aşağıdaki komutu kullanarak bilgisayar sertifikası kaldırın.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
