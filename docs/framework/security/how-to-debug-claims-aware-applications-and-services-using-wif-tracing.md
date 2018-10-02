---
title: 'Nasıl yapılır: Talep kullanan uygulamalar ve hizmetler WIF izleme kullanarak hata ayıklama'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: e10d8d2ea869b03586b4680ad8320aeb2de90620
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862981"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Nasıl yapılır: Talep kullanan uygulamalar ve hizmetler WIF izleme kullanarak hata ayıklama
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)  
  
-   WIF uygulamalarında hata ayıklama ve sorun giderme  
  
## <a name="summary"></a>Özet  
 İzlemeyi analiz etmek nasıl izleme Görüntüleyicisi aracı kullanarak kaydeder ve bu'nasıl yapılır WIF izlemeyi yapılandırma, izleme günlükleri toplamak gerekli adımlar açıklar. Bu izleme girişleri WIF ilgili sorunları gidermek için gerekli eylemleri için genel eşleme sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Adımların Özeti  
  
-   1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırma  
  
-   2. adım: WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanarak analiz edin  
  
-   3. adım – WIF düzeltmek için çözümleri tanımla ilgili sorunlar  
  
-   İlgili öğeler  
  
## <a name="objectives"></a>Amaçlar  
  
-   WIF izlemeyi yapılandırın.  
  
-   Görünüm izleme izleme Görüntüleyicisi Aracı'nda günlüğe kaydeder.  
  
-   WIF tanımlamak ilgili sorunları izleme günlüğüne kaydeder.  
  
-   Uygulama WIF düzeltici eylemler ilgili sorunları izleme günlükleri bulunamadı.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırma  
  
-   2. adım: WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanarak analiz edin  
  
-   3. adım – WIF düzeltmek için çözümleri tanımla ilgili sorunlar  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>1. adım – WIF Web.config yapılandırma dosyası kullanarak izlemeyi yapılandırma  
 Bu adımda, yapılandırma bölümlerine değişiklikleri ekleyeceksiniz *Web.config* olaylarını izleme ve izleme günlüğüne saklamak WIF etkinleştirme dosya.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Web.config yapılandırma dosyası kullanarak WIF izlemeyi yapılandırmak için  
  
1.  Açın **Web.config** veya **App.config** yapılandırma dosyası içinde bulunan çift tıklayarak Visual Studio düzenleyicisinde **Çözüm Gezgini**. Çözümünüzü yoksa **Web.config** veya **App.config** yapılandırma dosyasında, çözüm üzerinde sağ tıklayarak ekleyin **Çözüm Gezgini** tıklayıp **Ekleme**, ardından **yeni öğe...** . Üzerinde **yeni öğe** iletişim kutusunda, **uygulama yapılandırma dosyası** için **App.config** veya **Web yapılandırma dosyası** için**Web.config** listesi ve **Tamam**.  
  
2.  Yapılandırma dosyası içinde aşağıdaki gibi yapılandırma girdileri eklemek  **\<yapılandırma >** düğüm yapılandırma dosyasının sonunda:  
  
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
  
3.  Yukarıdaki yapılandırma ayrıntılı izleme olayları oluşturmak ve bunları oturum WIF bildirir *WIFTrace.e2e* dosya. Değerleri için tam bir listesi için **switchValue** değiştirmek, aşağıdaki konuda bulunan izleme düzeyini tabloya bakın: [yapılandırma izleme](../wcf/diagnostics/tracing/configuring-tracing.md).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>2. adım: WIF izleme dosyaları izleme Görüntüleyicisi aracı kullanarak analiz edin  
 Bu adımda, WIF izleme günlükleri analiz etmek için izleme Görüntüleyicisi aracı (SvcTraceViewer.exe) kullanır.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) kullanarak WIF izleme günlükleri analiz etmek için  
  
1.  İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe), Windows SDK'ın bir parçası olarak sunulur. Windows SDK'yı henüz yüklemediyseniz, buradan indirebilirsiniz: [Windows SDK'sı](https://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2.  İzleme Görüntüleyicisi aracı (SvcTraceViewer.exe) çalıştırın. Genellikle kullanılabilir **Bin** yükleme yolunun klasör.  
  
3.  WIF izleme günlük dosyası, örneğin, seçerek WIFTrace.e2e açın **dosya**, **Aç...** seçenek menüde veya bu adı kullanıyor **Ctrl + O** kısayol. İzleme günlük dosyası izleme Görüntüleyicisi aracı açılır.  
  
4.  Girdileri gözden **etkinlik** sekmesi. Her girdi, bir etkinlik sayısı, günlüğe kaydedilen izlemeleri sayısı, süresi etkinliği ve kendi başlangıç ve bitiş zaman damgası içermelidir.  
  
5.  Tıklayarak **etkinlik** sekmesi. Ayrıntılı izleme girişleri aracının ana alanında görmeniz gerekir. Kullanım **düzeyi** menüsünde belirli düzeyde izleme, örneğin filtre uygulamak için açılır liste: **tüm**, **uyarı**, **hataları**, **Bilgi**vb.  
  
6.  Belirli izleme girişleri alt alanında aracı ayrıntıları görüntülemek için tıklayın. Ayrıntıları kullanarak görüntülenebilir **biçimlendirilmiş** ve **XML** karşılık gelen sekmelerini seçerek görünümü.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>3. adım – WIF düzeltmek için çözümleri tanımla ilgili sorunlar  
 Bu adımda WIF izleme günlüğü ve izleme Görüntüleyicisi Aracı'nı kullanarak belirlenmiş WIF ilgili sorunlara yönelik çözümler tanımlayabilirsiniz. Genel özetler WIF eşleme ilgili olası bir çözüm ya da sorunu gidermek için gerekli eylemleri için özel durumlar.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>WIF düzeltmek için çözümleri tanımlamak için ilgili sorunlar  
  
1.  Aşağıdaki tabloda WIF özel durumlar ve sorunları düzeltmek için gerekli eylemleri gözden geçirin.  
  
|**Hata Kimliği**|**Hata iletisi**|**Hatayı düzeltmek eylem gerekli**|  
|-|-|-|  
|ID4175|Güvenlik belirteci veren IssuerNameRegistry tarafından tanınmadı.  Bu veren güvenlik belirteçleri kabul etmek için geçerli bir verenin adı döndürülecek IssuerNameRegistry yapılandırın.|Bu hata, bir parmak izi MMC ek bileşeninden kopyalayıp yapıştırarak kaynaklanabilir *Web.config* dosya. Özellikle, sertifika Özellikler penceresinden kopyalarken metin dizesinde yazdırılamayan ekstra bir karakter alabilirsiniz. Bu ek karakter parmak izi eşleşme başarısız olmasına neden olur. Parmak izi doğru bir şekilde kopyalamak için yordam burada bulunabilir: [http://msdn.microsoft.com/library/ff359102.aspx](https://msdn.microsoft.com/library/ff359102.aspx)|  
  
## <a name="related-items"></a>İlgili öğeler  
  
-   [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
