---
title: 'Nasıl yapılır: Talep kullanan uygulama ve WIF izlemeyi kullanma hizmetleri hata ayıklama'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0f2126a83e6a5638eb492bb2a529dbf4cdab1714
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Nasıl yapılır: Talep kullanan uygulama ve WIF izlemeyi kullanma hizmetleri hata ayıklama
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)  
  
-   Sorun giderme ve WIF uygulamalarında hata ayıklama  
  
## <a name="summary"></a>Özet  
 Bu yöntem WIF izlemeyi yapılandırmak, izleme günlükleri toplamak gerekli adımlar açıklanır ve izleme Görüntüleyicisi aracı kullanarak izleme analiz etme günlüğe kaydeder. İzleme girişleri WIF ilgili sorunları gidermek için gereken eylemleri için genel eşleme sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Adımların Özeti  
  
-   1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırın  
  
-   2. adım – WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanmak Çözümle  
  
-   Adım 3 – WIF düzeltmek için çözümleri tanımla ilgili sorunlar  
  
-   İlgili öğeler  
  
## <a name="objectives"></a>Amaçlar  
  
-   WIF izlemeyi yapılandırın.  
  
-   Görünüm izleme izleme Görüntüleyicisi aracı günlüğe kaydeder.  
  
-   WIF tanımlamak ile ilgili sorunlar izleme günlüğüne kaydeder.  
  
-   Uygulama WIF düzeltme eylemleriyle ilgili sorunları izleme günlüklerine bulundu.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırın  
  
-   2. adım – WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanmak Çözümle  
  
-   Adım 3 – WIF düzeltmek için çözümleri tanımla ilgili sorunlar  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırın  
 Bu adımda, değişiklikleri yapılandırma bölümlerinin ekler *Web.config* olaylarına izlemesini ve izleme günlüğüne depolamaya WIF etkinleştirmek dosya.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Web.config yapılandırma dosyası kullanarak WIF izlemeyi yapılandırmak için  
  
1.  Kök açmak **Web.config** veya **App.config** yapılandırma dosyası içinde üzerine çift tıklayarak Visual Studio düzenleyicisinde **Çözüm Gezgini**. Çözümünüzü yoksa **Web.config** veya **App.config** yapılandırma dosyası, çözüm üzerinde sağ tıklayarak eklemek **Çözüm Gezgini** tıklatıp **Ekleme**, ardından **yeni öğe...** . Üzerinde **yeni öğe** iletişim kutusunda **uygulama yapılandırma dosyası** için **App.config** veya **Web yapılandırma dosyası** için**Web.config** tıklatın ve liste **Tamam**.  
  
2.  İçindeki yapılandırma dosyasının aşağıdakine benzer yapılandırma girdileri eklemek  **\<configuration >** yapılandırma dosyasının sonuna düğümde:  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3.  Yukarıdaki yapılandırma ayrıntılı izleme olayları oluşturmak ve bunları oturum WIF bildirir *WIFTrace.e2e* dosya. Değerleri için tam bir listesi için **switchValue** anahtarı, aşağıdaki konuda bulunan izleme düzeyi tabloya başvurun: [yapılandırma izleme](http://msdn.microsoft.com/library/ms733025.aspx).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>2. adım – WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanmak Çözümle  
 Bu adımda, WIF izleme günlüklerini çözümlemek için izleme Görüntüleyicisi aracı (SvcTraceViewer.exe) kullanır.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) kullanarak WIF izleme günlüklerini çözümlemek için  
  
1.  İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) Windows SDK'ın bir parçası olarak gelir. Windows SDK'sı henüz yüklemediyseniz, buradan indirebilirsiniz: [Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2.  İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) çalıştırın. İçinde kullanılabilir genellikle **Bin** yükleme yolunun klasörü.  
  
3.  WIF izleme günlük dosyasını seçerek Örneğin, WIFTrace.e2e açmak **dosya**, **Aç...** seçenek menüde veya kullanarak **Ctrl + O** kısayol. İzleme günlük dosyasını izleme Görüntüleyicisi aracı açılır.  
  
4.  Gözden girişlerinde **etkinlik** sekmesi. Her giriş, bir etkinlik numarası, günlüğe kaydedilmiş izlemeleri sayısı, süresi etkinliği ve onun başlangıç ve bitiş tarih damgaları içermelidir.  
  
5.  Tıklayın **etkinlik** sekmesi. Aracının ana alanı ayrıntılı izleme girdiler görmeniz gerekir. Kullanım **düzeyi** açılır liste belirli düzeyi izlemeleri, örneğin filtrelemek için menüsünde: **tüm**, **uyarı**, **hataları**, **Bilgi**, vb.  
  
6.  Aracı'nın alt alanındaki ayrıntılarını gözden geçirmek için girişleri belirli izleme'yi tıklatın. Ayrıntıları kullanılarak görüntülenebilir **biçimlendirilmiş** ve **XML** ilgili sekmeleri seçerek görünümü.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>Adım 3 – WIF düzeltmek için çözümleri tanımla ilgili sorunlar  
 Bu adımda, WIF izleme günlüğü ve izleme Görüntüleyicisi Aracı'nı kullanarak tanımlanan WIF ilgili sorunların çözümleri tanımlayabilirsiniz. Genel özetlenmektedir WIF eşlenmesini ilgili olası çözümleri veya sorunu gidermek için gerekli eylemleri için özel durumlar.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>WIF düzeltmek için çözümleri tanımlamak için ilgili sorunlar  
  
1.  Aşağıdaki tabloda WIF özel durumlar ve sorunları düzeltmek için gerekli eylemleri gözden geçirin.  
  
|**Hata Kimliği**|**Hata iletisi**|**Hatayı düzeltmek işlem gerekiyor**|  
|-|-|-|  
|ID4175|Güvenlik belirteci veren IssuerNameRegistry tarafından tanınmadı.  Bu veren gelen güvenlik belirteçleri kabul etmek için bu veren için geçerli bir ad döndürülecek IssuerNameRegistry yapılandırın.|Bu hata, bir parmak izi MMC ek bileşeninden kopyalayıp içine yapıştırarak kaynaklanabilir *Web.config* dosya. Özellikle, sertifika Özellikler penceresinden kopyalarken metin dizesinde yazdırılamayan fazladan bir karakter alabilirsiniz. Bu ek karakter parmak izi eşleşme başarısız olmasına neden olur. Parmak izi doğru kopyalamak için yordam şurada bulunabilir: [http://msdn.microsoft.com/library/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)|  
  
## <a name="related-items"></a>İlgili öğeler  
  
-   [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](http://msdn.microsoft.com/library/aa751795.aspx)
