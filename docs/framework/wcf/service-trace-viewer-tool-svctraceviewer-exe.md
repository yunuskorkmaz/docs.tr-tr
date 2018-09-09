---
title: Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: a03c459355f18ad30849113f353e35e97b6141ae
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251790"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)
Windows Communication Foundation (WCF) hizmet izleme Görüntüleyicisi aracı WCF tarafından oluşturulan tanılama izlemeleri analiz etmenize yardımcı olur. Hizmet izleme görüntüleyicisini kolayca birleştirmek, görüntülemek ve böylece tanılama onarın ve WCF hizmet sorunları doğrula izleme günlüğü iletileri filtrelemek için bir yol sağlar.  
  
## <a name="configuring-tracing"></a>İzlemeyi Yapılandırma  
 Tanılama izlemeleri, uygulamanızın işlem neler olduğunu gösteren bilgiler sağlar. Adından da anlaşılacağı gibi operations, kaynaktan hedefe ve de ara noktaları aracılığıyla izleyebilirsiniz.  
  
 Uygulamanın yapılandırma dosyası kullanarak izlemeyi yapılandırabilirsiniz; barındırılan Web uygulamaları için Web.config veya *Appname*.config şirket içinde barındırılan uygulamalar için. Bir örnek verilmiştir:  
  
```xml  
<system.diagnostics>  
    <trace autoflush="true" />  
    <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="sdt"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "SdrConfigExample.e2e" />  
            </listeners>  
         </source>  
    </sources>  
</system.diagnostics>  
```  
  
 Bu örnekte, İzleme dinleyicisi türünü ve adını belirtildi. Dinleyici adlı `sdt` ve standart .NET Framework İzleme dinleyicisi (System.Diagnostics.XmlWriterTraceListener) türü olarak eklenir. `initializeData` Olması bu dinleyici için günlük dosyasının adı ayarlamak için kullanılan öznitelik `SdrConfigExample.e2e`. Günlük dosyası için bir basit dosya adı için bir tam yol yerine kullanabilirsiniz.  
  
 Örnek SdrConfigExample.e2e adlı kök dizininde bir dosya oluşturur. "Açma ve WCF izleme dosyaları görüntüleme" bölümünde açıklandığı gibi dosyayı açmak için izleme görüntüleyicisini kullandığınızda, gönderilen tüm iletileri görebilirsiniz.  
  
 İzleme düzeyini tarafından denetlenir `switchValue` ayarı. Kullanılabilir izleme düzeylerini, aşağıdaki tabloda açıklanmıştır.  
  
|İzleme düzeyi|Açıklama|  
|-----------------|-----------------|  
|Kritik|-Hata ve olay günlüğü girişleri ve izleme bağıntı bilgileri günlüğe kaydeder. Kritik düzey kullanmak isteyeceğiniz durumların bazı örnekleri şunlardır:<br />-AppDomain nedeniyle işlenmeyen bir özel durum oluştu.<br />-Uygulama başlatılamıyor.<br />-MyApp.exe işleminden kaynaklanan bir hata nedeniyle ileti.|  
|Hata|-Tüm özel durumları günlüğe kaydeder. Aşağıdaki durumlarda hata düzeyini kullanabilirsiniz:<br />-Kodunuzu geçersiz bir tür dönüştürme özel durum nedeniyle kilitlendi.<br />-a "uç noktası oluşturma başarısız oldu" özel durum, uygulamanızın başlatma sırasında başarısız olmasına neden oluyor.|  
|Uyarı|-Bir koşul bulunduğunu daha sonra bir hata veya Kritik hata neden olabilir. Aşağıdaki durumlarda bu düzey kullanabilirsiniz:<br />-Uygulama, azaltma ayarlarını izin verdiğinden daha fazla isteklerini alıyor.<br />-Alıcı sırası, yapılandırılmış kapasitesinin yüzde 98 ' dir.|  
|Bilgiler|-İleti izleme ve tanılama sistem durumu, performans ölçüm veya profil oluşturma için faydalı oluşturulur. Kapasite planlama ve performans yönetimi gibi bilgileri kullanabilir. Aşağıdaki durumlarda bu düzey kullanabilirsiniz:<br />-İleti AppDomain ulaştı ve seri durumdan çıkarılmakta sonra bir hata oluştu.<br />-HTTP bağlaması oluşturulurken bir hata oluştu.|  
|Ayrıntılı|Debug-her iki kullanıcı kodu için izleme ve hizmet düzeyi. Bunu yaptığınızda düzeyi ayarlayın:<br />-Hatanın oluştuğu andaki kodunuzda hangi yöntemi çağrıldı emin değilseniz.<br />-Yanlış bir uç nokta yapılandırılmış olması ve hizmeti ayırma depolama girişte kilitlendiğinden başlatılamadı.|  
|ActivityTracing|Akış olaylarını işleme etkinlikleri ve bileşenleri arasında.<br /><br /> Bu düzey, Yöneticiler ve geliştiriciler uygulamalarını aynı uygulama etki alanında bağıntısını kurmanızı sağlar.<br /><br /> -Etkinlik sınırları izlemelerini: Başlat/Durdur.<br />-İzlemeleri aktarımları.|  
  
 Kullanabileceğiniz `add` adını ve kullanmak istediğiniz İzleme dinleyicisi türünü belirtmek için. Örnek Yapılandırması, dinleyici adlı `sdt` ve standart .NET Framework İzleme dinleyicisi (`System.Diagnostics.XmlWriterTraceListener`) türü olarak eklenir. Kullanım `initializeData` günlük dosyasının adı için bu dinleyici ayarlamak için. Ayrıca, bir basit dosya adı için bir tam yol yerine kullanabilirsiniz.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Hizmet izleme görüntüleyicisini kullanma  
  
### <a name="opening-and-viewing-wcf-trace-files"></a>Açma ve WCF izleme dosyalarını görüntüleme  
 Hizmet izleme görüntüleyicisini üç dosya türlerini destekler:  
  
-   WCF izleme dosyası (.svcLog)  
  
-   Olay dosyası (.etl) izleme  
  
-   Koyu izleme dosyası  
  
 Hizmet izleme görüntüleyicisini, tüm desteklenen izleme dosyasını açın, ekleyin ve ek izleme dosyaları, tümleştirme veya açın ve izleme dosyaları bir grup aynı anda birleştirme sağlar.  
  
##### <a name="to-open-a-trace-file"></a>Bir izleme dosyasını açmak için  
  
1.  WCF yükleme konumuna (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin) gidin ve ardından yazın, bir komut penceresi kullanarak hizmet izleme görüntüleyicisini Başlat `SvcTraceViewer.exe`.  
  
> [!NOTE]
>  Hizmet izleme Görüntüleyicisi aracı iki dosya türleri ile ilişkilendirebilirsiniz: .svclog ve .stvproj. Kaydolun ve dosya uzantılarını kaydını silmek için komut satırında iki parametre kullanabilirsiniz.  
>   
>  / register: dosya uzantıları ".svclog" ve ".stvproj" ilişkisini SvcTraceViewer.exe ile kaydetme  
>   
>  / unregister: dosya uzantıları ".svclog" ve ".stvproj" SvcTraceViewer.exe ile ilişkisini kaydını sil  
  
1.  Hizmet izleme görüntüleyicisini başladığında tıklayın **dosya** gelin ve ardından **açık**. İzleme dosyalarınızın depolandığı konuma gidin.  
  
2.  Açmak istediğiniz izleme dosyasına çift tıklayın.  
  
    > [!NOTE]
    >  Birden çok izleme dosyaları tıklatırken seçmek ve aynı anda açmak için SHIFT tuşuna basın. Hizmet izleme görüntüleyicisini tüm dosyaların içeriğini birleştirir ve bir görünüm sunar. Örneğin, hem istemci hem de hizmet izleme dosyaları açabilirsiniz. İleti günlüğe kaydetme ve Etkinlik yayma Yapılandırması etkinleştirildiğinde, bu yararlıdır. Bu şekilde, hizmet ve istemci arasında ileti değişimi inceleyebilirsiniz. Ayrıca, birden çok dosya Görüntüleyicisi'ne sürükleyin veya kullanın **proje** sekmesi. Daha fazla ayrıntı için proje yönetimi bölümüne bakın.  
  
3.  Ek izleme dosyaları, açık olan koleksiyona eklemek için tıklatın **dosya** gelin ve ardından **Ekle**. Açılan pencerede izleme dosyalarının konumuna gidin ve eklemek istediğiniz dosyaya çift tıklayın.  
  
> [!CAUTION]
>  200 MB değerinden daha büyük bir izleme günlük dosyası yüklemek önerilmez. Bu sınırdan büyük bir dosya yüklemeye çalışırsanız, yükleme işlemi, bilgisayar kaynağınıza bağlı olarak uzun zaman alabilir. Hizmet izleme Görüntüleyicisi aracı uzun süredir duyarlı olmayabilir veya makinenizin bellek tüketebilir. Bunu önlemek için kısmi yüklemeyi yapılandırmanız önerilir. Bunun nasıl yapılacağı hakkında daha fazla bilgi için "Yükleme büyük izleme dosyaları" bölümüne bakın.  
  
#### <a name="event-tracing-and-crimson-tracing"></a>Olay izleme ve koyu izleme  
 İzleyicinin yerel biçimi WCF yayan Etkinlik izleme biçimidir. Görüntüleyici bunları görüntülemeden önce farklı bir biçimde yayılan izlemeleri dönüştürülmesi gerekir. Şu anda Etkinlik izleme biçimi ek olarak, olay izleme ve koyu izleme Görüntüleyicisi'ni destekler.  
  
 Etkinlik izlemeleri içermeyen bir dosyayı açtığınızda, Görüntüleyici dosyanın dönüştürmeye çalışır. Dönüştürülen izleme verilerini içerecek dosyanın konumunu ve adını belirtmeniz gerekir. Veri dönüştürüldükten sonra Görüntüleyicisi yeni dosyanın içeriğini görüntüler.  
  
> [!NOTE]
>  Dönüştürme, dönüştürülen izleme verilerini depolamak için disk alanı gerektirir. Bir dönüştürme işlemine başlamadan önce verileri depolamak yeterli disk alanı olduğundan emin olun. Aksi takdirde, dönüştürme başarısız olur.  
  
### <a name="managing-projects"></a>Projeleri Yönetme  
 Görüntüleyici, birden çok izleme dosyalarını görüntüleme kolaylaştırmak için projeleri destekler. Örneğin, bir istemci izleme dosyası ve bir hizmeti izleme dosyası varsa, bunları projeye ekleyebilirsiniz. Ardından, projeyi her açışlarında, projedeki tüm izleme dosyaları aynı anda yüklenir.  
  
 Projeleri yönetmeye yönelik iki yolu vardır:  
  
-   İçinde **dosya** menüsünü açabilir, kaydedin ve kapatın projeleri.  
  
-   İçinde **proje** sekmesi, dosyaları bir projeye ekleyebilirsiniz.  
  
### <a name="viewing-wcf-traces"></a>WCF izlemeleri görüntüleme  
 WCF Etkinlik izleme biçimini kullanarak izlemeleri yayar. Etkinlik izleme modelinde, tek tek izlemeleri etkinliklerde amaçlarına göre gruplandırılır. Mantıksal denetim akışı etkinlikleri arasında aktarılır. Örneğin, bir uygulamanın kullanım ömrü, süresince birçok "iletisi gönder etkinliği" görünür ve kaybolur. İzlemeleri ve etkinlikleri ve hizmet izleme görüntüleyicisini kullanıcı arabiriminin çok görüntüleme ile ilgili daha fazla bilgi için bkz: [ilişkilendirilmiş izlemeleri görüntülemek ve sorun giderme için hizmet izleme görüntüleyicisini kullanarak](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
#### <a name="switching-to-different-views"></a>Geçiş için farklı görünümleri  
 Hizmet izleme görüntüleyicisini aşağıdaki farklı görünümler sağlar. Görüntüleyici'nin sol bölmede sekme olarak gösterilen ve yanından erişilebilen **görünümü** menüsü.  
  
-   Etkinliği Görüntüle  
  
-   Proje görünümü  
  
-   İleti görünümü  
  
-   Graf Görünümü  
  
##### <a name="activity-view"></a>Etkinliği Görüntüle  
 İzleme dosyaları açılmadı sonra etkinliklerine gruplandırılmış ve görüntülenen izlemeleri görebilirsiniz **etkinlik** sol bölmesindeki görünümü.  
  
 **Etkinlik** görünüm görüntüler Etkinlik adları, etkinlik izlemelerinde sayısı süresini, başlangıç zamanı ve bitiş zamanı.  
  
 Herhangi bir listedeki etkinliklerin tıklayarak, bu etkinlik izlemelerinde sağdaki izleme bölmesinde görüntülenir. Ardından, ayrıntılarını görüntülemek için bir izleme de seçebilirsiniz.  
  
 Birden çok etkinlik tuşlarına basarak seçebileceğiniz **Ctrl** veya **Shift** anahtar ve istenen etkinlikleri tıklayarak. İzleme bölmesinde seçili etkinliklerinin tüm izlemeleri görüntüler.  
  
 İçinde görüntülemek için bir etkinliğe çift tıklayabilirsiniz **grafik** görünümü. Bir etkinlik seçin ve geçiş için alternatif bir yolu olan **grafik** görünümü.  
  
> [!NOTE]
>  "000000000000" Etkinlik Grafiği görünümü'nde görüntülenen özel bir etkinliktir. Tüm diğer etkinlikler kendisine bağlı olduğundan, bu etkinlik görüntüleyen bir ciddi performans etkisi yoktur.  
  
 Etkinlik listesi sıralamak için sütunun başlığına tıklayabilir. Uyarı izlemeleri içeren etkinlikler sarı bir arka plan ve kırmızı bir hata izlemeleri içeren sahiptir.  
  
 Farklı etkinlik türleri vardır ve her etkinlik sol tarafındaki simge karşılık gelen her türü. Anlamları için anlama izleme simgeler bölümüne bakabilirsiniz.  
  
##### <a name="project-view"></a>Proje görünümü  
 Bu görünüm, geçerli projede izleme dosyaları yönetmenizi sağlar. Daha fazla ayrıntı için proje yönetimi bölümüne bakın.  
  
##### <a name="graph-view"></a>Graf Görünümü  
 Hizmet izleme görüntüleyicisini en güçlü özelliklerinden biri **grafik** görünümü, belirli bir etkinlik izleme verilerini grafik biçiminde görüntüler. Grafik formun veri bunlar arasında hareket ettikçe tarafınızdaki yürütülmesi olayları ve birden çok etkinlik birbiriyle görmenizi sağlar.  
  
 Geçiş yapmak **grafik** görüntülemek için bir etkinlik seçin **etkinlik** görüntülemek ve **etkinlik** sekmesini veya bir ileti günlüğü izlemede **ileti**Görünümü. Birden çok izleme dosyaları yüklenir ve birden fazla dosya izlemelerinden etkinlik içerir, tüm ilgili izlemeleri Grafik Görünümü'nde görünür. Etkinlikleri ve ileti günlük izlemelerini çift ayrıca müşteri adayları, **grafik** görünümü.  
  
 İçinde **grafik** görünümü dikey her sütun bir etkinlik ve sütundaki her bir blok bir izleme temsil eder. Etkinlikler, işlem (veya iş parçacığı) tarafından gruplandırılır. Etkinlikler arasında küçük oklar aktarımları temsil eder. İşlemler arasında büyük oklar ileti değişimi temsil eder. Seçimdeki her zaman sarı renkli bir etkinliktir.  
  
###### <a name="selecting-traces-in-the-graph"></a>Grafikte izlemeleri seçme  
  
1.  Graftaki bir blok tıklayın.  
  
2.  Yukarı ve aşağı tuşlarını, komşu izlemeleri seçin.  
  
3.  İzleme ve ayrıntılı bölmesinde izleme bilgileri inceleyin.  
  
###### <a name="expanding-or-collapsing-activity-transfers"></a>Genişletme veya daraltma etkinlik aktarımları  
 Başka bir etkinlik için etkinlik seçimi dışarı aktarırken, etkinlik aktarımları genişletebilirsiniz. Aktarımları izlemenizi sağlar.  
  
 Genişlet veya daralt etkinlik aktarımları için  
  
1.  "+" İşareti ile Aktarım izleme aktarımı simgesine sol tarafında bulun.  
  
2.  "+"'a tıklayın veya basın **Ctrl** ve "+" için klavyeyi kullanma.  
  
3.  Sonraki etkinliği grafikte görünür.  
  
4.  A "-" aktarımı simgesine sol tarafında görünür. Tıklayın "-" oturum veya Ctrl tuşuna basın ve "-", etkinlik aktarım daraltır.  
  
> [!NOTE]
>  Birden çok aktarımları içine bir aktivitesi olduğundan ve aktarımları birini genişletin, yeni bir etkinlik için Kök etkinlikten neden etkinlikleri görüntülenir. Bu yeni etkinlikler daraltılmış formda görüntülenir. Bu etkinlikler ile ilgili ayrıntıları görmek istiyorsanız, bunları dikey grafiğin üst bilgisindeki Genişlet simgesine tıklayarak genişletin.  
  
###### <a name="expanding-or-collapsing-activities-vertically"></a>Etkinlikleri dikey daraltma veya genişletme  
 Viewer etkinliklerini daraltarak gereksiz ayrıntılı Etkinlik Grafiği olarak gizler. Daraltılmış bir etkinliğe tek tek izlemeleri görüntülenmez. Yalnızca aktarımları izleme görünür. Bir etkinlikte tüm izlemeleri görüntülemek istiyorsanız, etkinlik grafiğin üst bilgisindeki etkinliğin genişletme simgesini tıklatarak dikey olarak genişletin.  
  
 Genişletmek veya daraltmak için dikey etkinlikleri için  
  
1.  Etkinlik dikey olarak genişletmek için etkinlik üst bilgisindeki "+" simgesine tıklayın.  
  
2.  Tüm izlemeleri grafikte görüntülenen dikkat edin.  
  
3.  Tıklayın "-" etkinlik dikey daraltmak için etkinlik üst bilgisindeki simge.  
  
4.  Bildirim yalnızca önemli aktarımları ileti günlükleri, uyarı ve etkinlik özel durumu izlemeleri gösterilir.  
  
###### <a name="options"></a>Seçenekler  
 İki seçenekler arasından seçim yapabilirsiniz **seçeneği** graf görünümünü menüsünde.  
  
-   İşaretlenmediğinde, grafik etkinliği sınır izlemelerinde yoksay etkinlik sınır izlemeleri göster.  
  
-   Hangi işaretlenmediğinde ileti izlemeleri dışında ayrıntılı düzeyi izlemeleri yoksay olmayan ileti ayrıntılı izleme, gösterir. Çoğu durumda, ayrıntılı düzeyi izlemeleri analiz için küçük büyük/küçük harf önemlidir. Ayrıntılı düzeyi izlemeleri analiz edin ve yalnızca üzerinde daha önemli izlemeler odaklanmayı tercih istemediğinizde bu seçenek yararlı olur.  
  
###### <a name="layout-mode"></a>Düzen modu  
 Görüntüleyici iki Düzen modu vardır: **işlem** ve **iş parçacığı**. Bu ayar, en büyük kuruluş birimi tanımlar. Düzen modu varsayılan **işlem**, etkinlik grafiğinde işlemler tarafından gruplandırılır anlamına gelir.  
  
###### <a name="execution-list"></a>Yürütme listesi  
 Hangi işlemin veya iş parçacığı bu aşağı açılan listeden grafikte görüntülenecek seçebilirsiniz. Örneğin, (A ve B) iki istemci izleme dosyaları ve açık bir hizmet ve yalnızca hizmet ve istemci bir grafikte görüntülemek istediğiniz varsa, istemci B listeden kaldırın.  
  
#### <a name="viewing-trace-details"></a>İzleme Ayrıntıları görüntüleme  
 Bir izleme ayrıntılarını görüntülemek için izleme bölmesinde bir izleme seçin. Ayrıntı bölmesinde ayrıntıları görüntülenir.  
  
##### <a name="trace-pane"></a>İzleme bölmesi  
 Hizmet izleme görüntüleyicisini üst sağ bölmede, izleme bölmesinde bulunur. Tüm izlemeleri, ek bilgilerle, seçili Etkinlik izleme düzeyi, iş parçacığı kimliği ve işlem adını listeler.  
  
 Ham XML izleme bir izleme sağ tıklatıp seçerek panoya kopyalayabilirsiniz **Panoya kopyalama izleme**.  
  
##### <a name="detail-pane"></a>Ayrıntı bölmesi  
 Hizmet izleme görüntüleyicisini alt sol bölmesinde ayrıntı bölmesinde bulunur. Bu işlem izleme ayrıntılarını görüntülemek için üç sekme sağlar.  
  
 **Biçimlendirilmiş** görünüm daha düzenli bir şekilde bilgi görüntüler. Tablo ve ağaçları okumanız ve anlamanız bilgileri kolaylaştıran, bilinen tüm XML öğeleri listeler.  
  
 **XML** Görünüm Seçili izlemeye karşılık gelen XML görüntüler. Bu, söz dizimi vurgulama ve renk destekler. Kullanırken **Bul** dizeleri aramak için arama sonuçlarında vurgulanır.  
  
 **İleti** görünüm ileti günlüğü izlemelerinde XML ileti bölümü görüntüler. Bir ileti olmayan izleme seçtiğinizde görünmez durumdadır.  
  
### <a name="filtering-wcf-traces"></a>Filtreleme WCF izlemeleri  
 İzleme analizi kolaylaştırmak için bunları aşağıdaki şekillerde filtreleyebilirsiniz:  
  
-   Filtre araç önceden tanımlanmış ve özel filtreler erişim sağlar. Aracılığıyla etkinleştirilebilir **görünümü** menüsü.  
  
-   Önceden tanımlanmış filtre Görüntüleyicisi, seçmeli olarak WCF izlemeleri bölümlerini filtrelemek için kullanılabilir. Varsayılan olarak, tüm altyapı izlemeleri geçmesine izin verecek şekilde ayarlanır. Bu filtre ayarlarını tanımlanan **filtreleme seçeneklerini** alt menüsü altında **görünümü** menüsü.  
  
-   Özel için XPath filtrelerinde kullanıcılar filtreleme üzerinde tam denetim verir. İçinde tanımlanabilir **özel filtre** altında **görünümü** menüsü.  
  
 Tüm filtreleri geçen izlemeleri görüntülenir.  
  
#### <a name="using-the-filter-toolbar"></a>Filtre araç çubuğunu kullanma  
 Filtre araç çubuğu araç üst kısmında görünür. Mevcut değilse, bunu etkinleştirebilir **görünümü** menüsü. Çubuğundaki üç bileşenden oluşur:  
  
-   Aranan: **Ara** filtre işlemi aramak için konu tanımlar. Örneğin, yayılan tüm izlemeler X işlem bağlamında bulmak istiyorsanız, bu alanı X ayarlayın ve **arama içinde** 'İşlem adı' alanı. Bir tarih saat seçici denetimi zamana bağlı filtre olduğunda bu alanı değişiklikleri seçilidir.  
  
-   Aramada: Bu alan uygulanacak filtrenin türünü tanımlar.  
  
-   Düzeyi: Düzeyi ayarı filtre tarafından izin verilen minimum izleme düzeyini tanımlar. Örneğin, hata ve düzeyi ayarlama, yalnızca kritik düzey ve hata izlemeleri görüntülenir. Bu filtre, Ara ve arama tarafından belirtilen ölçütleri ile birleştirir.  
  
 **Artık filtre** düğmesi filtre işlemi başlatır. Bazı filtreler, özellikle de büyük bir veri kümesine uygulandığında, tamamlanması uzun sürebilir. Tuşlarına basarak filtre işlemi iptal edebilirsiniz **Durdur** durum çubuğunda görünen bir düğme **işlemleri** menüsü.  
  
 **Temizle** düğme önceden tanımlanmış ve özel filtreler tüm izlemeleri geçmesine izin verecek şekilde sıfırlar.  
  
#### <a name="filter-options"></a>Filtre Seçenekleri  
 Görüntüleyici, WCF izlemeleri görünümünden otomatik olarak kaldırabilirsiniz. WCF özel alanlara göre yayılan izlemeleri seçmeli olarak kaldırabilirsiniz, örneğin, işlem kaldırma izlemeleri görünümden ilgili.  
  
 Bu filtre ayarlarını tanımlanan **filtreleme seçeneklerini** alt menüsü altında **görünümü** menüsü.  
  
#### <a name="custom-filters"></a>Özel Filtreler  
 XML Path Language (XPath) hakkında bilginiz varsa, ilgilendiğiniz herhangi bir XML öğesi için izleme verilerini aramak için özel filtreler oluşturmak için kullanabilirsiniz. Filtreler, filtre araç çubuğu aracılığıyla erişilebilir.  
  
 Özel Filtreler parametreler ekleyebilir. Ayrıca, önceden mevcut olan özel filtreler de içeri aktarabilirsiniz.  
  
##### <a name="creating-a-custom-filter"></a>Özel filtre oluşturma  
 Filtreler, iki şekilde oluşturulabilir:  
  
###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Özel Şablon Sihirbazı'nı kullanarak bir filtre oluşturma  
 Varolan bir izleme'yi tıklatın ve izleme yapısına göre bir filtre oluşturun. Bu örnek, iş parçacığı kimliğini temel alan özel bir filtre oluşturur.  
  
1.  Görüntüleyici'nin sağ üst kısımdaki alana izleme bölmesinde, filtrelemek için kullanmak istediğiniz öğeyi içeren bir izleme seçin.  
  
2.  Tıklayın **özel filtre oluşturma** düğmesi İzleme bölmesinin en üstünde yer alan.  
  
3.  Görüntülenen iletişim kutusunda, filtreniz için bir ad girin. Bu örnekte, girin `Thread ID`. Filtre kümenizi bir açıklamasını sağlar.  
  
4.  Soldaki ağaç görünümünde 1. adımda seçtiğiniz izleme kaydının yapısını görüntüler. Bir koşul için oluşturmak istediğiniz öğeyi bulun. Bu örnekte XPath bulunmasını ThreadID göz atın: /E2ETraceEvent/System/Execution/@ThreadID düğümü. Ağaç görünümünde ThreadID öznitelik çift tıklayın. Bu iletişim kutusunun sağ tarafındaki özniteliği için bir ifade oluşturur.  
  
5.  Parametre alanı ThreadID koşulu için None olarak değiştirin '{0}'. Bu adım, filtre uygulandığında yapılandırılması ThreadID değeri sağlar. (Bkz. nasıl filtre bölümünde uygulanır) En fazla dört parametre tanımlayabilirsiniz. Koşullar, OR operatörü kullanılarak birleştirilir.  
  
6.  Tıklayın **Tamam** filtre oluşturmak için.  
  
> [!NOTE]
>  Bir filtre Şablonu Sihirbazı'nı kullanarak oluşturulduktan sonra yalnızca el ile düzenlenebilir. Daha önce oluşturduğunuz bir filtre için Sihirbazı'nı etkinleştirmek mümkün değildir. Ayrıca, şablonu Sihirbazı'nda oluşturulan bir XPath filtresi Koşulları OR operatörü kullanılarak birleştirilir. Bir AND işlemi gerekiyorsa, oluşturulduktan sonra filtre ifadesi düzenleyebilirsiniz.  
  
###### <a name="creating-a-custom-filter-manually"></a>Özel filtre el ile oluşturma  
 Özel Filtreler menüsü için XPath filtrelerinde el ile girmenizi sağlar.  
  
1.  Görünüm menüden **özel filtreler** menü öğesi.  
  
2.  Görüntülenen iletişim kutusunda tıklatın **yeni.**  
  
3.  En az bir filtre adı ve XPath ifadesi belirtin.  
  
4.  **Tamam**'ı tıklatın.  
  
###### <a name="applying-a-custom-filter"></a>Özel filtre uygulama  
 Özel filtre oluşturulduktan sonra ancak erişilebilir durumda filtre araç. İçinde uygulamak istediğiniz filtreyi seçin **arama içinde** filtre araç alanı. Önceki örnekte, iş parçacığı'ID ' seçin.  
  
1.  İçinde aradığınız değeri belirtin **Aranan** alan. Bizim örneğimizde, aramak istediğiniz iş parçacığı Kimliğini girin.  
  
2.  Tıklayın **artık filtre**ve işlemin sonucu inceleyin.  
  
 Filtreniz birden çok parametre kullanıyorsa, bunları girmeniz kullanarak ';' ayırıcı olarak **Aranan** alan. Örneğin, 3 parametre aşağıdaki dizeyi tanımlar: '1; findValue; metin'. Görüntüleyici '1' uygulandığı {0} filtre parametresi. 'findValue' ve 'text' uygulandığı {1} ve {2} sırasıyla.  
  
###### <a name="sharing-custom-filters"></a>Özel Filtreler paylaşma  
 Özel Filtreler farklı oturumları ve farklı kullanıcılar arasında paylaşılabilir. Filtreler için bir tanım dosyasını dışarı aktarmak ve bu dosyayı başka bir yerde içeri aktarabilirsiniz.  
  
 Özel filtre içeri aktarmak için:  
  
1.  İçinde **görünümü** menüsünde tıklatın **özel filtreler**.  
  
2.  Açılan iletişim kutusunda, tıklayın **alma** düğmesi.  
  
3.  Özel filtre (.stvcf) dosyasına gidin, dosyayı ve tıklayın **açık** düğmesi.  
  
 Özel filtre dışarı aktarmak için:  
  
1.  Görünüm menüden **özel filtreler**.  
  
2.  Açılan iletişim kutusunda, dışarı aktarmak istediğiniz filtreyi seçin.  
  
3.  Tıklayın **dışarı** düğmesi.  
  
4.  Özel filtre tanım dosyası (.stvcf) konumunu ve adını belirtin ve tıklayın **Kaydet** düğmesi.  
  
> [!NOTE]
>  Bu özel filtreler yalnızca içe ve dışa aktarılan hizmet izleme Görüntüleyicisi'nden. Diğer araçları tarafından okunamaz.  
  
### <a name="finding-data"></a>Bulma verileri  
 Görüntüleyici verileri bulmak için aşağıdaki yöntemleri sağlar:  
  
-   Bul araç, en yaygın Bul seçenekleri bir hızlı erişim sağlar.  
  
-   Daha fazla bulma seçenekleri Bul iletişim kutusu sağlar. Aracılığıyla erişilebilir **Düzenle** menüsünden veya kısa anahtar Ctrl + f  
  
 Bul araç Görüntüleyicisi üst kısmında görünür. Mevcut değilse, bunu etkinleştirebilir **görünümü** menüsü. Çubuk iki bileşenden oluşur:  
  
-   Aranan: arama anahtar sözcüğü girmenizi sağlar.  
  
-   Konum: arama kapsamını girmenizi sağlar. Tüm etkinliklerde veya yalnızca geçerli etkinliği aramak seçebilirsiniz.  
  
 Bul iletişim kutusu iki ek seçenekler sağlar:  
  
-   Hedef bulun:  
  
    -   "Ham günlük veri" seçeneği, anahtar sözcüğü tüm ham verileri kullanarak arar.  
  
    -   "XML metni" ve "XML özniteliği" seçenekleri yalnızca XML öğeleri arayın.  
  
    -   "İleti günlüğe" seçeneği, anahtar sözcüğü yalnızca iletileri arar.  
  
-   Kök etkinlik yoksay: arama "000000000000" etkinlik izlemelerinde yok sayar. Kök etkinlik aktarımları çoğu, izleme, binlerce sahip olduğunda bu büyük izleme dosyaları performansını artırır.  
  
### <a name="navigating-traces"></a>İzlemeleri gezinme  
 Uygulama çalışma zamanı sırasında izlemeleri adım adım kayıtlı olduğundan izlemeleri gezinme, uygulamanızda hata ayıklamak için yardımcı olabilir. Hizmet izleme görüntüleyicisini izlemelerinde gitmek için çeşitli yollar sağlar.  
  
#### <a name="step-forward-or-backward"></a>İleriye veya geriye doğru adım  
 Her izleme bir programda kod satırı olarak düşünün, İleri Adımlama "Adımlama" içinde Visual Studio tümleşik geliştirme ortamı (IDE) için benzer. Aynı zamanda geri izlemelerinde geçebilirsiniz, farktır. İleri Adımlama, sonraki etkinliği izlemede geçme anlamına gelir.  
  
-   İleri Adım: Kullanma **etkinlik** menüsünden veya "F10" tuşuna basın. Ok tuşu "kapalı" izleme bölmesinde kullanabilirsiniz.  
  
-   Adımda geri: Kullanmak **etkinlik** menüsünden veya "F9" tuşuna basın. Ok tuşu "yukarı" izleme bölmesinde kullanabilirsiniz.  
  
> [!NOTE]
>  WCF iletileri etkinlik makineler span kimlikleri gerçekleştirebilirsiniz çünkü bu, farklı bir işlemde veya hatta farklı bir bilgisayara gerçekleşen bir etkinliğin alabilir.  
  
#### <a name="follow-transfer"></a>Aktarım izleyin  
 Aktarım izlemeleri özel izlemelerinde izleme dosyası var. Bir etkinlik için başka bir etkinlik tarafından bir aktarım izleme aktarabilir. Örneğin, "Etkinlik A", "Etkinlik B" aktarabilir. Böyle bir durumda, "Etkinlik" ": etkinlik" adını aktarımı içeren simge bir aktarım izleme yoktur. Bu aktarım izleme, iki arasında bir bağlantıdır. "Etkinlik B", ayrıca olabilir bir aktarım izleme geri "etkinlik için" aktarmak için etkinlik sonunda. Bu işlev çağrıları programlarda benzer: A, B, B verir çağırır.  
  
 "Aktarımı İzle" bir hata ayıklayıcıda "İçine Adımlama" benzer. Aktarım A'dan B'ye takip eden Diğer izlemeleri üzerinde hiçbir etkisi yok.  
  
 Aktarım izlemek için iki yolu vardır: klavye veya fare tarafından:  
  
-   Fareyle: izleme bölmesinde aktarım izleme çift tıklayın.  
  
-   Klavye: Bir aktarım izleme seçin ve "Transfer izleyin" kullanın **etkinlik** menüsünden veya "F11" tuşuna basın.  
  
> [!NOTE]
>  Etkinlik B, etkinlik A aktarırken geri etkinlik a etkinlik B aktarır kadar birçok durumda, etkinlik bekler Bu, etkinlik, etkinlik B etkin bir şekilde izleme dönemi boyunca günlüğe bir izleme yok olduğu anlamına gelir. Ancak, aynı zamanda etkinlik beklememeyi ve günlük izlemeleri devam mümkündür. Etkinlik B geri etkinlik a aktarmaz olanağı da sağlar Bu nedenle, etkinlik aktarımları hala işlev çağrıları bu bağlamdaki farklıdır. Aktarımları Etkinlik Grafiği görünümü'nde daha iyi anlayabilirsiniz.  
  
#### <a name="jump-to-next-or-previous-transfer"></a>Sonraki veya önceki aktarımı atla  
 Birden çok etkinlik seçildiğinde, geçerli etkinliği ya da seçili etkinlikler çözümlerken, hızlı bir şekilde aktarır, etkinlikleri bulmak isteyebilirsiniz. "Aktarmak sonraki atlama", sonraki aktarım izleme etkinliğini bulundurmanıza olanak tanır. Aktarım izleme bulduktan sonra sonraki etkinliği içine Adımlama için "aktarımı İzle"'ı kullanabilirsiniz.  
  
-   Atlama sonraki aktarmak için: kullanım **etkinlik** menüsünden veya "Ctrl + F10" tuşuna basın.  
  
-   Atlama önceki aktarmak için: kullanım **etkinlik** menüsünden veya "Ctrl + F9" tuşuna basın.  
  
#### <a name="navigate-in-graph-view"></a>Graf görünümü içinde gezinme  
 Etkinlik ve izleme bölmesinde gezinme hatalarının ayıklanmasına benzer olsa da, kullanarak **grafik** görünümü çok daha iyi bir deneyim gezinti sağlar. Daha fazla bilgi için "Grafik görünümü" bölümüne bakın.  
  
### <a name="loading-large-trace-files"></a>Büyük izleme dosyaları yükleniyor  
 İzleme dosyası çok büyük olabilir. Örneğin, birkaç dakika çalışan kolayca için "Ayrıntılı" düzeyi, elde edilen izleme dosyası izleme kapatırsanız yüz megabayt veya daha da büyük, ağ hızını ve iletişim deseni bağlı olabilir.  
  
 Hizmet izleme Görüntüleyicisi'nde bir çok büyük izleme dosyasını açtığınızda, sistem performansı olumsuz yönde etkilenebilir. Yükleme hızı ve yanıt süresi yüklemeden sonra yavaş olabilir. Gerçek aktarım hızı, zaman zaman, donanım yapılandırmanıza bağlı olarak farklılık gösterir. Çoğu PC içinde 200 milyon daha büyük bir izleme dosyası yüklenirken, bir önemli performans etkisi yoktur. 1 G büyük izlemeler dosyalar için araç tüm kullanılabilir belleği kullanın veya çok uzun bir süredir yanıt vermiyor.  
  
 Büyük izleme dosyaları çözümlenerek içinde yanıt süresi ve yavaş yükleniyor önlemek için hizmet izleme görüntüleyicisini "Kısmi yalnızca teker teker izleme küçük bir bölümünü yükleyen yüklenmesi" adlı bir özellik sağlar. Örneğin, bir izleme dosyası 1 birkaç gün için sunucu üzerinde çalışan GB'den, olabilir. Bazı hatalar oluştu ve izlemeyi analiz etmek istediğiniz tüm izleme dosyasını açmak gerekli değildir. Bunun yerine, belirli bir hata oluşmuş olabilir ne zaman zaman diliminde izlemeleri yükleyebilirsiniz. Kapsamı daha küçük olduğundan, hizmet izleme Görüntüleyicisi aracı daha hızlı dosya yükleyebilir ve daha küçük bir veri kümesini kullanarak hataları tespit edebilirsiniz.  
  
#### <a name="enabling-partial-loading"></a>Kısmi yüklemeyi etkinleştirme  
 Kısmi yüklemeyi el ile etkinleştirmeniz gerekmez. Yükleme girişimi izleme dosyalarının toplam boyutu, 40 MB aşarsa, hizmet izleme görüntüleyicisini kısmi yükleme bir iletişim kutusu, yüklemek istediğiniz bölümü seçmek otomatik olarak görüntüler.  
  
> [!NOTE]
>  İzlemeleri saat eşit olarak dağıtılmış değil çünkü yayılma, araç yükleme boyutunu gösterilen orantılı değil kısmi yüklenirken belirttiğiniz süre uzunluğu. Gerçek yükleme boyutu kısmi yüklemeyi iletişim tahmini boyutundan daha küçük olabilir.  
  
#### <a name="adjusting-partial-loading"></a>Kısmi yüklemeyi ayarlama  
 İzleme dosyasını kısmen yüklediğiniz sonra yüklenen veri kümesini değiştirmek isteyebilirsiniz. Kısmi yüklenirken araç Görüntüleyicisi üst kısmındaki ayarlayarak bunu yapabilirsiniz.  
  
1.  Araç çubuğunun fareyle taşıyın veya başlangıç ve bitiş saati girin.  
  
2.  Tıklayın **Ayarla** düğmesi.  
  
## <a name="understanding-trace-icons"></a>İzleme simgeler anlama  
 Hizmet izleme Görüntüleyicisi aracı kullanır simge listesi aşağıdadır **etkinlik** görünümü **grafik** görünümü ve **izleme** bölmesinde farklı öğeleri göstermek için.  
  
> [!NOTE]
>  Kategorilere Ayrılmadı bazı izlemeler (örneğin, "bir ileti kapatıldı") oluştur.  
  
### <a name="activity-tracing-traces"></a>İzlemeleri izleme etkinliği  
  
|Simge|Açıklama|  
|----------|-----------------|  
|![Uyarı izleme](../../../docs/framework/wcf/media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Uyarı izleme: uyarı düzeyinde yayılan izleme|  
|![İzleme hatası](../../../docs/framework/wcf/media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|İzleme hatası: hata düzeyinde yayılan izleme.|  
|![Etkinlik Başlangıç izleme:](../../../docs/framework/wcf/media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Etkinlik Başlangıç izleme: etkinlik başlangıcını işaretleyen izleme. Bu etkinliğin adını içerir. Uygulama Tasarımcısı veya geliştirici olarak, bir etkinlik başlangıç izleme etkinlik kimliği işlem veya iş parçacığı başına başına tanımlamanız gerekir.<br /><br /> Etkinlik Kimliği izleme kaynakları için izleme bağıntı arasında yayılır, daha sonra aynı etkinlik kimliği (izleme kaynak başına bir adet) için birden çok başlatır görebilirsiniz. İzleme kaynağı ActivityTracing etkinse başlangıç izleme yayılır.|  
|![Etkinlik İzlemeyi Durdur](../../../docs/framework/wcf/media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Etkinlik İzlemeyi Durdur: Etkinliğin sonunu işaretleyen izleme. biçimindeki telefon numarasıdır. Bu etkinliğin adını içerir. Uygulama Tasarımcısı veya geliştirici olarak, bir etkinliğin etkinlik kimliği başına iz başına İzlemeyi Durdur tanımlamanız gerekir. Hiçbir izlemelerinden belirtilen izleme kaynağına izleme zaman ayrıntı düzeyi yeterince küçük ise bu izleme kaynağı tarafından yayılan dışında durdurma etkinlikten sonra görünür. Bu durum oluştuğunda, bir Dur dahil olmak üzere aynı anda iki izlemeleri görüntülendiğinde aralıklı. Etkinlik Kimliği izleme kaynakları için izleme bağıntı arasında yayılır aynı etkinlik kimliği (izleme kaynak başına bir adet) için birden çok duraklarını görebilirsiniz. İzlemeyi Durdur ActivityTracing izleme kaynağı etkinse yayılır.|  
|![Etkinlik askıya izleme](../../../docs/framework/wcf/media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Etkinlik askıya izleme: etkinlik duraklatıldı zaman işaretleyen izleme. Etkinliği yeniden devam edene dek izleme yok askıya alınmış bir etkinlik içinde gönderilir. Askıya alınmış bir etkinlik, hiçbir işlem, etkinlik izleme kaynağı kapsamında gerçekleşmekte olduğunu gösterir. Askıya alma/sürdürme izlemeleri, profil oluşturma için kullanışlıdır. İzleme kaynağı ActivityTracing etkinse askıya izleme yayılır.|  
|![İzleme etkinliği sürdürme](../../../docs/framework/wcf/media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4e0a-9988-cdc2f7030f17")|İzleme etkinliği sürdürme: etkinlik askıya alınmıştı sonra sürdürüldü zaman işaretleyen izleme. Bu etkinlik izlemeleri yeniden yayılan. Askıya alma/sürdürme izlemeleri, profil oluşturma için kullanışlıdır. İzleme kaynağı ActivityTracing etkinse sürdürme izleme yayılır.|  
|![Aktarım](../../../docs/framework/wcf/media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Aktarım: mantıksal denetim akışı bir etkinlikten diğerine aktarılırken yayılan bir izleme. Aktarım kaynaklandığı etkinlik aktarım gider etkinliğine paralel çalışmayı gerçekleştirmek devam edebilir. İzleme kaynağı ActivityTracing etkinse aktarım izleme yayılır.|  
|![Aktarımı](../../../docs/framework/wcf/media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Sunucudan aktar: Geçerli etkinlik için başka bir etkinlikten bir aktarım tanımlayan bir izleme.|  
|![Transfer](../../../docs/framework/wcf/media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Aktarım için: bir aktarım mantıksal denetim akışı geçerli etkinlikten diğerine geçirmek için tanımlayan izleme.|  
  
### <a name="wcf-traces"></a>WCF izlemeleri  
  
|Simge|Açıklama|  
|----------|-----------------|  
|![Günlük izleme iletisi](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Günlük izleme iletisi: bir WCF ileti ileti günlüğe kaydetme özelliğiyle günlüğe kaydedildiğinde yayılan izleme zaman `System.ServiceModel.MessageLogging` izleme kaynağı etkinleştirilir. Bu izleme tıklayarak iletisi görüntülenir. Bir ileti için dört yapılandırılabilir günlüğe kaydetme noktası vardır: ServiceLevelSendRequest, TransportSend TransportReceive ve tarafından belirtilebilir ServiceLevelReceiveRequest, `messageSource` ileti günlüğü izleme özniteliği.|  
|![Alınan izleme iletisi](../../../docs/framework/wcf/media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Alınan izleme iletisi: bir WCF ileti alındığında, yayılan izleme `System.ServiceModel` izleme kaynağı bilgi veya ayrıntı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliğini görüntülemek için gerekli **grafik** görünümü.|  
|![Gönderilen izleme iletisi](../../../docs/framework/wcf/media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Gönderilen izleme iletisi: varsa bir WCF ileti gönderildiğinde yayılan izleme `System.ServiceModel` izleme kaynağı bilgi veya ayrıntı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliğini görüntülemek için gerekli **grafik** görünümü.|  
  
### <a name="activities"></a>Etkinlikler  
  
|Simge|Açıklama|  
|----------|-----------------|  
|![Activity](../../../docs/framework/wcf/media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Etkinlik: geçerli etkinliği bir genel etkinlik olduğunu gösterir.|  
|![Kök etkinlik](../../../docs/framework/wcf/media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Kök etkinlik: Kök etkinlik, bir işlemin gösterir.|  
  
### <a name="wcf-activities"></a>WCF etkinlikleri  
  
|Simge|Açıklama|  
|----------|-----------------|  
|![Ortamı etkinliğini](../../../docs/framework/wcf/media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Ortamı etkinliğini: bir etkinlik oluşturur, açar veya bir WCF konak veya istemci kapatır. Bu etkinlik, bu aşamaları sırasında gerçekleşen hataları görünür.|  
|![Etkinlik dinleme](../../../docs/framework/wcf/media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Etkinlik dinleme: izlemeleri günlüğe kaydeden bir etkinlik için bir dinleyici ilgili. Bu etkinlik içinde biz dinleyicisi bilgileri ve bağlantı istekleri görüntüleyebilirsiniz.|  
|![Bayt etkinlik alma](../../../docs/framework/wcf/media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Bayt etkinlik alır: tüm izlemeleri gruplandıran bir etkinlik gelen bayt sayısı iki uç noktalar arasında bir bağlantı alma ile ilgili. Bu etkinlik, http.sys gibi etkinlik kimliği yayma aktarım etkinliklerle ilişkilendirme gereklidir. Bu etkinlik, bağlantı hataları iptalleri gibi görünür.|  
|![İleti etkinliği işlem](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|İleti etkinliği işlem: izlemeleri gruplandıran bir etkinlik ilgili bir WCF ileti oluşturmak için. Bu etkinlik hataları nedeniyle bir hatalı zarf veya hatalı bir ileti görüntülenir. Bu etkinlik içinde size bir etkinlik kimliği bir çağrıyı yapandan yayıldığı görmek için ileti üst bilgileri inceleyebilirsiniz. Biz işlem eylem etkinliği (sonraki simgesi) aktarırken bu doğruysa, ki bu etkinlik çağıran ve çağrılan'ın izlemeler arasında bağıntı yayılan etkinlik kimliği atayabilirsiniz.|  
|![Günlük izleme iletisi](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Eylem etkinliği işlem: iki uç noktalar genelinde tüm izlemeleri gruplandıran bir etkinlik ilgili WCF istek. Varsa `propagateActivity` ayarlanır `true` yapılandırmasındaki her iki bitiş noktasında bir etkinlik doğrudan bağıntı için tüm izlemeler her iki bitiş noktasında birleştirilir. Bu tür bir etkinlik aktarım veya işlemi, kullanıcı kodu sınırına genişletme güvenlik nedeniyle hataları içeriyor ve (bir yanıt varsa) geri.|  
|![İleti etkinliği işlem](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Yürütme kullanıcı kodu etkinliği: kullanıcı kodu gruplandıran bir etkinlik bir isteği işlemek için izler.|  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Kayıt defterine yazma izni yoksa, "Microsoft Service izleme görüntüleyicisini sisteme kaydedilmedi" aşağıdaki hata iletisini almak kullandığınızda, "`svctraceviewer /register`" aracı kaydetmek için komutu. Bu meydana gelirse, kayıt defterine yazma erişimi olan bir hesap kullanarak oturum açmanız gerekir.  
  
 Ayrıca, hizmet izleme Görüntüleyicisi aracı bazı ayarları (örneğin, özel filtreler ve filtre seçeneklerini) derleme klasörünün SvcTraceViewer.exe.settings dosyasına yazar. Dosya için okuma iznine sahip değilsiniz, aracı hala başlatabilirsiniz, ancak ayarlar yüklenemiyor.  
  
 "Bilinmeyen bir hata oluştu işlenirken bir veya daha fazla izlemeleri" hata iletisi alırsanız .etl dosyasını açarken .etl dosyasının biçimi geçersiz olduğunu gösterir.  
  
 Arapça işletim sistemine kullanılarak oluşturulan bir izleme günlüğü açarsanız, zaman filtresi çalışmıyor fark edebilirsiniz. Örneğin, 2005 yılı Arapça takvim yılında 1427 karşılık gelir. Ancak, hizmet izleme Görüntüleyicisi aracı filtre tarafından desteklenen zaman aralığıyla 1752'den önceki bir tarihi desteklemez. Bu filtrede doğru bir tarih seçmek mümkün olmadığını kapsıyor. Bu sorunu çözmek için özel bir filtresi oluşturabilirsiniz (**görünüm/özel filtreler**) belirli bir zaman aralığı içerecek şekilde bir XPath ifadesi kullanarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [İzlemeyi Yapılandırma](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Etkinlik izleme ve yayılma için uçtan uca izleme bağıntı](https://msdn.microsoft.com/library/2c11a905-64f8-47b5-bae5-a74fc666137e)
