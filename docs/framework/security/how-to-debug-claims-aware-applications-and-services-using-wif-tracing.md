---
title: 'Nasıl yapılır: WIF İzleme Kullanarak Talep Kullanan Uygulama ve Hizmetlerde Hata Ayıklama'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: 604ebf5ad71197f6614ffa45b6d7c181d474e1aa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990474"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Nasıl yapılır: WIF İzleme Kullanarak Talep Kullanan Uygulama ve Hizmetlerde Hata Ayıklama
## <a name="applies-to"></a>Uygulanan Öğe  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)  
  
- WıF uygulamalarında sorun giderme ve hata ayıklama  
  
## <a name="summary"></a>Özet  
 Bu nasıl yapılır, WıF izlemenin nasıl yapılandırılacağı, İzleme günlüklerinin toplanması ve izleme günlüklerini Izleme Görüntüleyicisi aracını kullanarak nasıl analiz edileceği için gereken adımları açıklar. WıF ile ilgili sorunları gidermek için gereken eylemlere izleme girişleri için genel eşleme sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
- Amaçlar  
  
- Adımların Özeti  
  
- Adım 1 – Web. config yapılandırma dosyasını kullanarak WıF Izlemeyi yapılandırın  
  
- 2\. adım – Izleme Görüntüleyicisi aracını kullanarak WıF Izleme dosyalarını çözümleme  
  
- 3\. adım – Ilgili sorunları gidermek için çözümleri tanımla  
  
- İlgili öğeler  
  
## <a name="objectives"></a>Amaçlar  
  
- WıF izlemeyi yapılandırın.  
  
- İzleme günlüklerini Izleme Görüntüleyicisi aracında görüntüleyin.  
  
- İzleme günlüklerinde WıF ile ilgili sorunları belirler.  
  
- İzleme günlüklerinde ilgili sorun yaşıyorsanız WIF düzeltme eylemleri uygulayın.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
- Adım 1 – Web. config yapılandırma dosyasını kullanarak WıF Izlemeyi yapılandırın  
  
- 2\. adım – Izleme Görüntüleyicisi aracını kullanarak WıF Izleme dosyalarını çözümleme  
  
- 3\. adım – Ilgili sorunları gidermek için çözümleri tanımla  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>Adım 1 – Web. config yapılandırma dosyasını kullanarak WıF Izlemeyi yapılandırın  
 Bu adımda, *Web. config* dosyasındaki yapılandırma bölümlerine değişiklikler ekleyerek, olaylarının izlenmesini ve bir izleme günlüğünde depolanmasını sağlayabilirsiniz.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Web. config yapılandırma dosyasını kullanarak WıF izlemeyi yapılandırmak için  
  
1. **Çözüm Gezgini**içinde çift tıklayarak kök **Web. config** veya **app. config** yapılandırma dosyasını Visual Studio düzenleyicisinde açın. Çözümünüz **Web. config** veya **app. config** yapılandırma dosyasına sahip değilse, **Çözüm Gezgini** çözüme sağ tıklayıp **Ekle**' ye tıklayın ve ardından **Yeni öğe... öğesine**tıklayın. **Yeni öğe** iletişim kutusunda, listeden **app. config** veya Web **. config** Için **Web yapılandırma dosyası** Için **uygulama yapılandırma dosyası** ' nı seçin ve **Tamam**' ı tıklatın.  
  
2. Yapılandırma dosyasının sonundaki yapılandırma  **\<>** düğümü içindeki yapılandırma dosyasına benzer yapılandırma girdilerini ekleyin:  
  
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
  
3. Yukarıdaki yapılandırma, WıF 'nin ayrıntılı izleme olayları oluşturmasını ve bunları *Wiftrace. e2e* dosyasında oturum açmasını sağlar. **SwitchValue** anahtarı için değerlerin tamamen listesi için, aşağıdaki konuda bulunan izleme düzeyi tablosuna bakın: [Izleme yapılandırılıyor](../wcf/diagnostics/tracing/configuring-tracing.md).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>2\. adım – Izleme Görüntüleyicisi aracını kullanarak WıF Izleme dosyalarını çözümleme  
 Bu adımda, WıF izleme günlüklerini çözümlemek için Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe) kullanacaksınız.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe) kullanarak WıF izleme günlüklerini çözümlemek için  
  
1. İzleme Görüntüleyicisi Aracı (SvcTraceViewer. exe) Windows SDK bir parçası olarak gelir. Windows SDK henüz yüklemediyseniz, buradan indirebilirsiniz: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2. Izleme Görüntüleyici aracını (SvcTraceViewer. exe) çalıştırın. Genellikle yükleme yolunun **bin** klasöründe bulunur.  
  
3. WıF izleme günlük dosyasını açın, örneğin, **Dosya**, **Aç..** . öğesini seçerek wiftrace. e2e. menüsünde veya **CTRL + O** kısayolunu kullanarak seçeneğini kullanın. İzleme günlüğü dosyası Izleme Görüntüleyici aracında açılır.  
  
4. **Etkinlik** sekmesindeki girişleri gözden geçirin. Her giriş bir etkinlik numarası, günlüğe kaydedilen izleme sayısı, etkinliğin süresi ve başlangıç ve bitiş zaman damgaları içermelidir.  
  
5. **Etkinlik** sekmesine tıklayın. Aracının ana alanında ayrıntılı izleme girişleri görmeniz gerekir. Belirli izleme düzeyini filtrelemek için menüdeki **düzey** açılan listesini kullanın, örneğin: **Tümü**, **Uyarı**, **hatalar**, **bilgiler**vb.  
  
6. Aracın alt alanındaki ayrıntıları gözden geçirmek için belirli izleme girişlerine tıklayın. Ayrıntılar, ilgili sekmeler seçilerek **biçimlendirilen** ve **XML** görünümü kullanılarak görüntülenebilir.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>3\. adım – Ilgili sorunları gidermek için çözümleri tanımla  
 Bu adımda, WıF izleme günlüğü ve Izleme Görüntüleyicisi Aracı kullanılarak tanımlanan WıF ile ilgili sorunların çözümlerini tanımlayabilirsiniz. Sorunu gidermek için, olası çözümlerin veya gerekli eylemlerin genel eşleştirmesiyle ilgili genel eşlemeyi özetler.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>WıF ile ilgili sorunları gidermeye yönelik çözümleri belirlemek için  
  
1. Sorunları düzeltmek için aşağıdaki WıF özel durumları ve gerekli eylemleri tablosunu inceleyin.  
  
|**Hata KIMLIĞI**|**Hata Iletisi**|**Hatayı onarmak için gereken eylem**|  
|-|-|-|  
|ID4175|Güvenlik belirtecini veren ıssuernameregyıpu tarafından tanınmadı.  Bu verenin güvenlik belirteçlerini kabul etmek için, ıssuernameregyıpı ' yi bu veren için geçerli bir ad döndürecek şekilde yapılandırın.|Bu hata, MMC ek bileşeninden bir parmak izi kopyalanarak ve *Web. config* dosyasına yapıştırılarak meydana gelir. Özellikle, sertifika özellikleri penceresinden kopyalama yaparken metin dizesinde yazdırılabilir bir ek karakter alabilirsiniz. Bu ek karakter, parmak izinin başarısız olmasına neden olur. Parmak izini doğru şekilde kopyalama yordamı, [Web Için talep tabanlı çoklu oturum açma ve Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29)bulunabilir.|  
  
## <a name="related-items"></a>İlgili öğeler  
  
- [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
