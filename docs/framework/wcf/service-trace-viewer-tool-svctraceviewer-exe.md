---
title: Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: 215e34a3e7b075463ceeaa15386d3a347ffff064
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)
Windows Communication Foundation (WCF) hizmet izleme Görüntüleyicisi aracı WCF tarafından oluşturulan tanılama izlemeleri analiz etmenize yardımcı olur. Hizmet izleme görüntüleyicisini kolayca birleştirmek, görüntülemek ve Tanılama, onarma ve WCF hizmeti sorunları doğrulayın izleme günlüğü iletileri filtrelemek için bir yol sağlar.  
  
## <a name="configuring-tracing"></a>İzlemeyi Yapılandırma  
 Tanılama izlemeleri uygulamanızın işlemi neler olduğunu gösteren bilgiler sağlar. Adından da anlaşılacağı gibi işlemleri kendi kaynaktan hedef ve Ara noktaları da üzerinden izleyebilirsiniz.  
  
 Uygulama yapılandırma dosyası kullanarak izlemeyi yapılandırabilirsiniz — her iki Web.config Web barındırılan uygulamalar için veya *Appname*.config kendini barındıran uygulamalar için. Bir örnek verilmiştir:  
  
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
  
 Bu örnekte, adını ve türünü İzleme dinleyicisi belirtilen. Dinleyici adlı `sdt` ve standart .NET Framework İzleme dinleyicisi (System.Diagnostics.XmlWriterTraceListener) türü olarak eklenir. `initializeData` Olması bu dinleyici için günlük dosyasının adını ayarlamak için kullanılan öznitelik `SdrConfigExample.e2e`. Günlük dosyası için bir basit dosya adı için bir tam yol yerine kullanabilirsiniz.  
  
 Örnek SdrConfigExample.e2e adlı kök dizindeki bir dosya oluşturur. "Ve görüntüleme WCF izleme dosyaları açma" bölümünde açıklandığı gibi dosyayı açmaya izleme görüntüleyicisini kullandığınızda, gönderilen tüm iletileri görebilirsiniz.  
  
 İzleme düzeyini tarafından denetlenen `switchValue` ayarı. Kullanılabilir izleme düzeyleri aşağıdaki tabloda açıklanmıştır.  
  
|İzleme düzeyi|Açıklama|  
|-----------------|-----------------|  
|Kritik|-Başarısız hızlı ve olay günlüğü girişleri ve izleme bağıntı bilgileri kaydeder. Kritik düzeyi kullanmak isteyeceğiniz durumların bazı örnekleri şunlardır:<br />-AppDomain nedeniyle işlenmeyen bir özel durum oluştu.<br />-Uygulama başlatılamıyor.<br />-MyApp.exe işleminden kaynaklanan hatasına neden oldu ileti.|  
|Hata|-Tüm özel durumları günlüğe kaydeder. Aşağıdaki durumlarda hata düzeyi kullanabilirsiniz:<br />-Kodunuzu geçersiz bir Cast özel durum nedeniyle kilitlendi.<br />-a "uç noktası oluşturulamadı" özel durum, uygulamanızın başlangıçta başarısız olmasına neden oluyor.|  
|Uyarı|-Bir koşul bulunmaktadır daha sonra bir hata veya kritik bir hata neden olabilir. Aşağıdaki durumlarda bu düzey kullanabilirsiniz:<br />-Uygulama azaltma ayarlarının izin verdiğinden daha fazla isteklerini alıyor.<br />-Yapılandırılmış kapasitesi yüzde 98 alıcı sırasıdır.|  
|Bilgiler|-İletileri izleme ve sistem durumu Tanılama, performansını ölçmek veya profil oluşturma için yararlı oluşturulur. Kapasite planlama ve performans yönetimi gibi bilgileri kullanabilir. Aşağıdaki durumlarda bu düzey kullanabilirsiniz:<br />-İleti AppDomain ulaştı ve Serisi kaldırılan sonra bir hata oluştu.<br />-HTTP bağlaması oluşturulurken bir hata oluştu.|  
|Ayrıntılı|Hata ayıklama için her iki kullanıcı kodu izleme ve bakım düzeyli. Bu düzey ayarlandığında:<br />-Hata oluştuğunda, kodunuzda hangi yöntemi çağrıldı emin değilseniz.<br />-Yapılandırılan yanlış bir uç noktası varsa ve hizmeti ayırma deposundaki giriş kilitlendiğinden başlatılamadı.|  
|ActivityTracing|İşlem etkinlikleri ve bileşenler arasındaki akış olaylar.<br /><br /> Bu düzey, Yöneticiler ve geliştiriciler uygulamalar aynı uygulama etki alanındaki ilişkilendirmenize olanak sağlar.<br /><br /> -İzlemeleri etkinlik sınırlar için: Başlat/Durdur.<br />-Aktarımları için izlemeleri.|  
  
 Kullanabileceğiniz `add` adını ve kullanmak istediğiniz İzleme dinleyicisi türünü belirtmek için. Örnek yapılandırma dinleyicisi adlı `sdt` ve standart .NET Framework İzleme dinleyicisi (`System.Diagnostics.XmlWriterTraceListener`) türü olarak eklenir. Kullanım `initializeData` bu dinleyici için günlük dosyasının adını ayarlamak için. Ayrıca, bir basit dosya adı için bir tam yol yerine kullanabilirsiniz.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Hizmet izleme Görüntüleyicisi Aracı'nı kullanma  
  
### <a name="opening-and-viewing-wcf-trace-files"></a>Açma ve WCF izleme dosyalarını görüntüleme  
 Hizmet izleme görüntüleyicisini üç dosya türlerini destekler:  
  
-   WCF dosya (.svcLog) izleme  
  
-   Dosya (.etl) izleme olayı  
  
-   Koyu izleme dosyası  
  
 Hizmet izleme görüntüleyicisini, tüm desteklenen izleme dosyasını açın, ekleme ve ek izleme dosyaları tümleştirmek veya açın ve izleme dosyaları bir grup aynı anda birleştirme sağlar.  
  
##### <a name="to-open-a-trace-file"></a>Bir izleme dosyasını açmak için  
  
1.  WCF yükleme konumuna (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin) gidin ve ardından türü için bir komut penceresi kullanarak hizmet izleme görüntüleyicisini Başlat `SvcTraceViewer.exe`.  
  
> [!NOTE]
>  Hizmet izleme Görüntüleyicisi aracı iki dosya türleriyle ilişkilendirebilirsiniz: .svclog ve .stvproj. Komut satırında iki parametre kaydetmek ve dosya uzantılarını kaydını kaldırmak için kullanabilirsiniz.  
>   
>  Register: dosya uzantıları ".svclog" ve ".stvproj" ilişkisini SvcTraceViewer.exe ile kaydetme  
>   
>  / kaydı: SvcTraceViewer.exe dosya uzantıları ".svclog" ve ".stvproj" ilişkilendirmesini kaydı  
  
1.  Hizmet izleme görüntüleyicisini başladığında tıklayın **dosya** üzerine gelin ve ardından **açık**. İzleme dosyalarının depolandığı konuma gidin.  
  
2.  Açmak istediğiniz izleme dosyasını çift tıklatın.  
  
    > [!NOTE]
    >  Birden çok izleme dosyaları tıklarken seçmek ve aynı anda açmak için SHIFT tuşuna basın. Hizmet izleme görüntüleyicisini tüm dosyaların içeriğini birleştirir ve bir görünüm sunar. Örneğin, hem istemci hem de hizmet izleme dosyaları açabilirsiniz. İleti günlüğe kaydetme ve Etkinlik yayma Yapılandırması etkinleştirildiğinde, bu yararlıdır. Bu şekilde, istemci ve hizmet arasında ileti alışverişi inceleyebilirsiniz. Ayrıca, birden çok dosya Görüntüleyicisi'ne sürükleyin veya kullanabilirsiniz **proje** sekmesi. Daha fazla ayrıntı için proje yönetme bölümüne bakın.  
  
3.  Ek izleme dosyaları açık koleksiyona eklemek için tıklatın **dosya** üzerine gelin ve ardından **Ekle**. Açılır penceresinde, izleme dosyalarının konumuna gidin ve eklemek istediğiniz dosyayı çift tıklatın.  
  
> [!CAUTION]
>  İzleme günlük dosyasını 200 MB'den daha büyük yük önerilmez. Bu boyuttan daha büyük bir dosyayı yüklemeye çalışırsanız, yükleme işlemi, bilgisayar kaynağına bağlı olarak uzun bir süre devam edebilir. Hizmet izleme Görüntüleyicisi aracı uzun süredir yanıt verebilir durumda olmayabilir veya makinenizin bellek tüketebilir. Bu durumu önlemek için kısmi yükleme yapılandırmanız önerilir. Bunun nasıl yapılacağı hakkında daha fazla bilgi için "Yükleme büyük izleme dosyaları" bölümüne bakın.  
  
#### <a name="event-tracing-and-crimson-tracing"></a>Olay izleme ve koyu izleme  
 İzleyicinin yerel biçimi WCF gösterdiği Etkinlik izleme biçimidir. Görüntüleyici bunları görüntülemeden önce farklı bir biçimde yayılan izlemeleri dönüştürülmesi gerekir. Şu anda, etkinlik izleme biçimi ek olarak olay izleme ve koyu izleme Görüntüleyicisi'ni destekler.  
  
 Etkinlik izlemeleri içermeyen bir dosyayı açtığınızda, Görüntüleyici dosya dönüştürmeye çalışır. Dönüştürülen izleme verilerini içeren dosyanın konumunu ve adını belirtmeniz gerekir. Veri dönüştürülen Görüntüleyici yeni dosyanın içeriğini görüntüler.  
  
> [!NOTE]
>  Dönüştürme dönüştürülmüş izleme verilerini depolamak için disk alanı gerektirir. Bir dönüştürme işlemine başlamadan önce verileri depolamak yeterli disk alanı olduğundan emin olun. Aksi takdirde, dönüştürme başarısız olur.  
  
### <a name="managing-projects"></a>Projeleri Yönetme  
 Görüntüleyici, birden çok izleme dosyalarını görüntüleme kolaylaştırmak için projeleri destekler. Örneğin, bir istemci izleme dosyası ve bir hizmet izleme dosyası varsa, bunları projeye ekleyebilirsiniz. Ardından, her projeyi açtığınızda, projedeki tüm izleme dosyaları aynı anda yüklenir.  
  
 Projeleri yönetme için iki yol vardır:  
  
-   İçinde **dosya** menüsünde açın, kaydedebilir ve projeleri kapatın.  
  
-   İçinde **proje** sekmesi, projeye dosyaları ekleyebilirsiniz.  
  
### <a name="viewing-wcf-traces"></a>WCF izlemeleri görüntüleme  
 WCF Etkinlik izleme biçimi kullanarak izlemeleri yayar. Etkinlik izleme modelinde, tek tek izlemeleri etkinliklerde amaçlarına göre gruplandırılır. Mantıksal denetim akışı etkinlikleri aktarılır. Örneğin, bir uygulamanın yaşam süresi sırasında birçok "iletisi gönder etkinliği" görünür ve kaybolur. İzlemeleri ve etkinlikleri ve hizmet izleme görüntüleyicisini kullanıcı arabiriminin çok görüntüleme hakkında daha fazla bilgi için bkz: [bağıntılı izlemeleri görüntüleme ve sorun giderme için hizmet izleme görüntüleyicisini kullanma](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
#### <a name="switching-to-different-views"></a>Farklı görünümleri değiştirme  
 Hizmet izleme görüntüleyicisini aşağıdaki farklı görünümleri sağlar. Görüntüleyicisi'nin sol bölmesinde sekmelerinde olarak görüntülenir ve ayrıca erişilebilen **Görünüm** menüsü.  
  
-   Etkinlik görünümü  
  
-   Proje görünümü  
  
-   İleti görünümü  
  
-   Grafik görünümü  
  
##### <a name="activity-view"></a>Etkinlik görünümü  
 İzleme dosyaları açıldığından sonra etkinliklerine gruplandırılmış ve görüntülenen izlemeleri görebilirsiniz **etkinlik** sol bölmesindeki görünümü.  
  
 **Etkinlik** görünüm görüntüler Etkinlik adları, etkinlik içindeki sayısı süresini, başlangıç ve bitiş zamanı.  
  
 Listelenen etkinlikleri hiçbirini tıklayarak, bu etkinlikte izlemeleri sağdaki izleme bölmesinde görüntülenir. Ayrıntılarını görüntülemek için bir izleme sonra seçebilirsiniz.  
  
 Basarak birden çok etkinliği seçebilirsiniz **Ctrl** veya **Shift** anahtarı ve istenen etkinlikleri'nı tıklatın. İzleme bölmesinde seçili etkinlikler tüm izlerini görüntüler.  
  
 İçinde görüntülemek için bir etkinliğe çift **grafik** görünümü. Bir etkinlik seçin ve geçmek için alternatif yoludur **grafik** görünümü.  
  
> [!NOTE]
>  "000000000000" Grafik görünümünde görüntülenen özel bir aktivite etkinliktir. Tüm diğer etkinlikler kendisine bağlı olduğundan, bu etkinlik görüntüleme bir önemli performans etkisi olur.  
  
 Etkinlik sıralamak için sütun başlığını tıklatabilirsiniz. Uyarı izlemeleri içeren etkinlikleri sarı bir arka plan ve hata izlemeleri içeren kırmızı bir sahiptir.  
  
 Farklı tür etkinlik vardır ve her etkinlik sol tarafındaki bir simge karşılık gelen her türü. Anlamları anlama izleme simgeler bölümünde başvurabilirsiniz.  
  
##### <a name="project-view"></a>Proje görünümü  
 Bu görünüm, geçerli projedeki izleme dosyaları yönetmenizi sağlar. Daha fazla ayrıntı için proje yönetme bölümüne bakın.  
  
##### <a name="graph-view"></a>Grafik görünümü  
 Hizmet izleme Görüntüleyicisi'nin en güçlü özelliklerden biridir **grafik** belirli bir etkinlik izleme verilerini grafik biçiminde görüntüler görünümü. Grafik formu, bunlar arasında verileri taşır gibi olayları ve birden çok etkinliği birbiriyle adım yürütülmesini görmenizi sağlar.  
  
 Geçiş yapmak için **grafik** görüntülemek için bir etkinlik seçin **etkinlik** görüntülemek ve **etkinlik** sekme ya da bir ileti günlüğü izlemede **ileti**Görünümü. Birden çok izleme dosyaları yüklenir ve birden fazla dosya izlemeleri etkinlik içerir, tüm ilgili izlemeleri Grafik görünümünde görüntülenir. Etkinlikleri ve ileti günlük izlemelerini çift de müşteri adayları, **grafik** görünümü.  
  
 İçinde **grafik** görünümü, her dikey sütunda bir etkinliği temsil eder ve bir izleme sütunundaki her bloğunu temsil eder. Etkinlikler, işlem (veya iş parçacığı) tarafından gruplandırılır. Etkinlikler arasında küçük oklar aktarımları temsil eder. Büyük oklar işlemleri arasındaki ileti değişimi temsil eder. Seçimdeki her zaman sarı olarak etkinliktir.  
  
###### <a name="selecting-traces-in-the-graph"></a>Grafikte izlemeleri seçme  
  
1.  Grafikte bir blok'ı tıklatın.  
  
2.  Yukarı ve aşağı komşu izlemeleri seçmek için tuşlarına basın.  
  
3.  İzleme ve ayrıntılı bölmelerinde izleme bilgilerini inceleyin.  
  
###### <a name="expanding-or-collapsing-activity-transfers"></a>Genişleterek veya daraltarak etkinlik aktarımları  
 Başka bir etkinliğin seçimi etkinliğinde dışarı aktarırken etkinlik aktarımları genişletebilirsiniz. Aktarımları izlemenizi sağlar.  
  
 Genişlet veya daralt etkinlik aktarımları için  
  
1.  "+" İşareti aktarım izleme aktarımı simgesine sol tarafta bulun.  
  
2.  "+"'yi tıklatın veya basın **Ctrl** ve "+" için klavyeyi kullanma.  
  
3.  Sonraki etkinliği grafikte görüntülenir.  
  
4.  Bir "-" aktarımı simgesinin solunda belirir. Tıklayın "-" oturum veya CTRL tuşunu basılı tutun ve "-", etkinlik aktarım daraltır.  
  
> [!NOTE]
>  Bir etkinlik içine birden çok aktarımı aktarımları birini genişletin yapıldığında, yeni etkinlik kök etkinliğinden sağlama etkinlikler görüntülenir. Bu yeni etkinlikler daraltılmış biçiminde görünür. Bu etkinlikler ayrıntılarını görmek istiyorsanız, bunları dikey grafik üstbilgisinde genişletme simgesine tıklayarak genişletin.  
  
###### <a name="expanding-or-collapsing-activities-vertically"></a>Genişletme veya etkinlikleri dikey daraltma  
 Görüntüleyici, etkinliği grafikte gereksiz ayrıntı etkinlikleri daraltarak gizler. Daraltılmış bir etkinliğin bireysel izlemeleri görüntülenmez. Yalnızca aktarımları izleme görünür. Bir etkinlik tüm izlemeleri görüntülemek istiyorsanız, etkinlik dikey grafik üstbilgisinde etkinliğin genişletme simgesini tıklatarak genişletin.  
  
 Genişletmek veya etkinlikleri dikey daraltmak için  
  
1.  Etkinlik dikey genişletmek için etkinlik üstbilgisindeki "+" simgesine tıklayın.  
  
2.  Tüm izlemeleri grafikte görüntülenen dikkat edin.  
  
3.  Tıklayın "-" etkinliği dikey daraltmak için etkinlik üst bilgisindeki simge.  
  
4.  Bildirim yalnızca önemli aktarımları ileti günlükleri, uyarı ve özel durum izlemeleri etkinliğin gösterilir.  
  
###### <a name="options"></a>Seçenekler  
 İki seçenekler arasından seçim yapabilirsiniz **seçeneği** Grafik görünümünde menüsü.  
  
-   İşaretlenmediğinde grafikte etkinlik sınır izlemeleri yoksay etkinlik sınır izlemeleri göster.  
  
-   Olmayan ileti ayrıntılı ileti izlemeleri dışında ayrıntılı düzeyi izlemeleri işaretlenmediğinde yoksay izlerini gösterir. Çoğu durumda, ayrıntılı düzeyi izlemeleri analiz için küçük büyük/küçük harf önemlidir. Bu seçenek, ayrıntılı düzeyi izlemeleri çözümlemek ve yalnızca üzerinde daha önemli izlemeler odaklanmak istiyorsanız istemediğiniz zaman yararlıdır.  
  
###### <a name="layout-mode"></a>Düzen modu  
 Görüntüleyici iki Düzen modu vardır: **işlem** ve **iş parçacığı**. Bu ayar, en büyük kuruluş birimi tanımlar. Düzen mod varsayılan **işlem**, yani etkinlikleri grafikte işlemler tarafından gruplandırılır.  
  
###### <a name="execution-list"></a>Yürütme listesi  
 Hangi işlemin veya iş parçacığı bu aşağı açılan listeden grafikte görüntülenecek seçebilirsiniz. Örneğin, iki istemcileri (A ve B) izleme dosyaları ve açılan bir hizmet ve yalnızca hizmet ve istemci bir grafikte görüntülemek istediğiniz varsa, listeden B istemcisi seçimini kaldırabilirsiniz.  
  
#### <a name="viewing-trace-details"></a>Görüntüleme İzleme Ayrıntıları  
 İzleme ayrıntı görüntülemek için izleme bölmesinde bir izleme seçin. Ayrıntıları ayrıntı bölmesinde görüntülenir.  
  
##### <a name="trace-pane"></a>İzleme bölmesi  
 Hizmet izleme görüntüleyicisini üst sağ bölmede izleme bölmesinde bulunur. Tüm izlemeleri ek bilgilerle seçili etkinliğinde izleme düzeyi, iş parçacığı kimliği ve işlem adını listeler.  
  
 Ham XML izlemeye izleme sağ tıklayıp seçerek panoya kopyalayabilirsiniz **Panoya Kopyala izleme**.  
  
##### <a name="detail-pane"></a>Ayrıntılar bölmesi  
 Hizmet izleme görüntüleyicisini alt sol bölmesinde ayrıntı bölmesinde bulunur. İzleme ayrıntılarını görüntülemek için üç sekme sağlar.  
  
 **Biçimlendirilmiş** görünümü daha düzenli bir şekilde bilgilerini görüntüler. Tabloları ve daha kolay okumak ve bilgileri anlamak ağaçları, tüm bilinen XML öğeleri listeler.  
  
 **XML** Görünüm Seçili izleme karşılık gelen XML görüntüler. Söz dizimi vurgulama ve renk destekler. Kullandığınızda **Bul** dizeleri aramak için arama sonuçlarını vurgular.  
  
 **İleti** görünüm ileti günlük izlemelerini XML ileti parçası görüntüler. İleti olmayan izleme seçtiğinizde görünmez durumdadır.  
  
### <a name="filtering-wcf-traces"></a>Filtreleme WCF izlemeleri  
 İzleme analizini kolaylaştırmak için bunları aşağıdaki şekillerde filtreleyebilirsiniz:  
  
-   Filtre araç önceden tanımlanmış ve özel filtreler erişim sağlar. Aracılığıyla etkinleştirilebilir **Görünüm** menüsü.  
  
-   Önceden tanımlanmış filtre Görüntüleyici'nin, seçmeli olarak WCF izlemeleri bölümlerini filtrelemek için kullanılabilir. Varsayılan olarak, tüm altyapı izlemeleri geçmesine izin verecek şekilde ayarlanır. Bu filtre ayarlarını tanımlanan **filtre seçenekleri** altında alt menüsünde **Görünüm** menüsü.  
  
-   Özel XPath filtreler kullanıcılara filtreleme üzerinde Tam Denetim verin. İçinde tanımlanabilir **özel filtre** altında **Görünüm** menüsü.  
  
 Tüm filtreleri yoluyla aktardığı izlemeleri görüntülenir.  
  
#### <a name="using-the-filter-toolbar"></a>Filtre araç çubuğunu kullanarak  
 Filtre araç çubuğu araç üst kısmında görüntülenir. Mevcut değilse, bunu etkinleştirebilirsiniz **Görünüm** menüsü. Çubuğu üç bileşenden oluşur:  
  
-   Aranan: **Ara** filtre işlemi aranacak konu tanımlar. Örneğin, işlem X bağlamında yayılan tüm izlemeler bulmak istiyorsanız, bu alan X ayarlayın ve **arama yeri** 'İşlem adı' alanı. Bir tarih saat seçici denetimi zamanı temelli bir filtre olduğunda bu alan değişiklikleri seçilidir.  
  
-   Aramada: Bu alan uygulamak için filtre türünü tanımlar.  
  
-   Düzeyi: Düzeyi ayarı filtre tarafından izin verilen minimum izleme düzeyini tanımlar. Örneğin, yalnızca izlemeleri hata ve kritik düzeyinde düzeyi hata ve yedekleme ayarlarsanız görüntülenir. Bu filtre ara ve arama tarafından belirtilen ölçütleri birleştirir.  
  
 **Şimdi filtre** düğmesi filtre işlemi başlatır. Özellikle büyük bir veri kümesine uygulandığında, bazı filtreler tamamlanması uzun sürebilir. Tuşlarına basarak filtre işlemi iptal edebilirsiniz **durdurmak** altında durum çubuğunda görünen düğmesine **Operations** menüsü.  
  
 **Temizle** düğme tüm izlemeleri geçmesine izin vermek için önceden tanımlanmış ve özel filtreler sıfırlar.  
  
#### <a name="filter-options"></a>Filtre Seçenekleri  
 Görüntüleyici otomatik olarak WCF izlemeleri görünümden kaldırın. WCF özel alanlara göre yayılan izlemeleri seçici olarak silebilirsiniz, örneğin, işlem kaldırma izlemeleri görünümden ilgili.  
  
 Bu filtre ayarlarını tanımlanan **filtre seçenekleri** altında alt menüsünde **Görünüm** menüsü.  
  
#### <a name="custom-filters"></a>Özel Filtreler  
 XML Path dili (XPath) biliyorsanız, ilgilendiğiniz herhangi bir XML öğesi izleme verilerini aramak için özel filtreler oluşturmak için kullanabilirsiniz. Filtreler, filtre araç çubuğu aracılığıyla erişilebilir.  
  
 Özel Filtreler parametreleri dahil edebilirsiniz. Önceden var olan özel filtreler de içeri aktarabilirsiniz.  
  
##### <a name="creating-a-custom-filter"></a>Özel filtre oluşturma  
 Filtreler iki şekilde oluşturulabilir:  
  
###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Şablon Sihirbazı'nı kullanarak bir özel filtre oluşturma  
 Var olan bir izleme'yi tıklatın ve bir izleme yapısında bir filtre oluşturun. Bu örnek, iş parçacığı kimliğine göre özel bir filtre oluşturur.  
  
1.  Görüntüleyici sağ üst bölümünde izleme bölmesinde için filtre uygulamak istediğiniz öğeyi içeren bir izleme seçin.  
  
2.  Tıklatın **oluşturma özel filtre** düğmesi İzleme bölmenin en üstünde yer alan.  
  
3.  Görüntülenen iletişim kutusunda filtreniz için bir ad girin. Bu örnekte, girin `Thread ID`. Filtre açıklamasını sağlar.  
  
4.  1. adımda seçtiğiniz izleme kaydı yapısını soldaki ağaç görünümünü görüntüler. İçin bir koşul oluşturmak istediğiniz öğesine göz atın. Bu örnekte, XPath bulunmasını ThreadID göz atın: /E2ETraceEvent/System/Execution/@ThreadID düğümü. Ağaç görünümünde ThreadID özniteliğini çift tıklatın. Bu öznitelik için bir ifade iletişim kutusunun sağında oluşturur.  
  
5.  ThreadID koşul için parametre alan Yok'a çıkarılıp '{0}'. Bu adım, filtre uygulandığında yapılandırılacak ThreadID değeri etkinleştirir. (Nasıl Uygula filtresi bölümüne bakın) En fazla dört parametreleri tanımlayabilirsiniz. Koşullar veya işlecini kullanarak birleştirilir.  
  
6.  Tıklatın **Tamam** filtre oluşturmak için.  
  
> [!NOTE]
>  Şablon Sihirbazı'nı kullanarak bir filtre oluşturulduktan sonra yalnızca el ile düzenlenebilir. Daha önce oluşturduğunuz bir filtre için Sihirbazı'nı etkinleştirmek mümkün değildir. Ayrıca, şablonu Sihirbazı'nda oluşturulan bir XPath filtresi koşulları veya işlecini kullanarak birleştirilir. AND işlemi gerekiyorsa, oluşturulduktan sonra filtre ifadesi düzenleyebilirsiniz.  
  
###### <a name="creating-a-custom-filter-manually"></a>Özel filtre el ile oluşturma  
 Özel Filtreler menüsünden XPath filtreleri el ile girmenize olanak sağlar.  
  
1.  Görünüm menüsünde tıklatın **özel filtreler** menü öğesi.  
  
2.  Görüntülenen iletişim kutusunda, tıklatın **yeni.**  
  
3.  En azından bir filtre adı ve XPath ifadesi belirtin.  
  
4.  **Tamam**'ı tıklatın.  
  
###### <a name="applying-a-custom-filter"></a>Özel filtre uygulama  
 Özel filtre oluşturulduktan sonra yine de erişilebilir filtre araç. İçinde uygulamak istediğiniz filtreyi seçin **arama yeri** filtre araç çubuğu alanı. Önceki örnekte, iş parçacığı'ID ' seçin.  
  
1.  Değer olarak aradığınız belirtin **Aranan** alan. Bizim örneğimizde, aramak istediğiniz iş parçacığı Kimliğini girin.  
  
2.  Tıklatın **şimdi filtre**, işleminin sonucu olduğunu gözleyin.  
  
 Filtre birden çok parametre kullanıyorsa, bunları girmeniz kullanarak ';' ayırıcı olarak **Aranan** alan. Örneğin, aşağıdaki dizeyi 3 parametrelerini tanımlar: '1; findValue; metin'. Görüntüleyici '1' uygulandığı {0} filtre parametresi. 'findValue' ve 'text' uygulanır {1} ve {2} sırasıyla.  
  
###### <a name="sharing-custom-filters"></a>Özel Filtreler paylaşımı  
 Özel Filtreler, farklı oturumlar ve farklı kullanıcılar arasında paylaşılabilir. Filtre tanımı dosyasına aktarın ve bu dosya başka bir konumda içe aktarabilirsiniz.  
  
 Özel filtre içeri aktarmak için:  
  
1.  İçinde **Görünüm** menüsünde tıklatın **özel filtreler**.  
  
2.  Açılan iletişim kutusunda tıklatın **alma** düğmesi.  
  
3.  Özel filtre (.stvcf) dosyasına gidin, dosyayı tıklatın ve'ı tıklatın **açık** düğmesi.  
  
 Özel filtre dışarı aktarmak için:  
  
1.  Görünüm menüsünde tıklatın **özel filtreler**.  
  
2.  Açılan iletişim kutusunda, dışa aktarmak istediğiniz filtreyi seçin.  
  
3.  Tıklatın **verme** düğmesi.  
  
4.  Özel filtre tanım dosyası (.stvcf) konumunu ve adını belirtin ve tıklatın **kaydetmek** düğmesi.  
  
> [!NOTE]
>  Bu özel filtreler yalnızca içe ve dışa aktarılan hizmet izleme Görüntüleyicisi'nden. Diğer araçları tarafından okunamıyor.  
  
### <a name="finding-data"></a>Verileri bulma  
 Görüntüleyici verileri bulmak için aşağıdaki yöntemleri sağlar:  
  
-   Bul araç yaygın bulma seçenekleri için hızlı erişim sağlar.  
  
-   Bul iletişim kutusu, daha fazla bulma seçenekleri sağlar. Aracılığıyla erişilebilen **Düzenle** menüsünde veya kısa anahtar Ctrl + f  
  
 Bul araç Görüntüleyici üstünde görünür. Mevcut değilse, bunu etkinleştirebilirsiniz **Görünüm** menüsü. Çubuğu iki bileşenden oluşur:  
  
-   Aranan: arama anahtar sözcüğü girmenize olanak sağlar.  
  
-   Bakılacak yer: arama kapsamını girmenize olanak sağlar. Tüm etkinlikleri veya yalnızca geçerli etkinliği aramak seçebilirsiniz.  
  
 Bul iletişim kutusu iki ek seçenekleri sağlar:  
  
-   Hedef bulun:  
  
    -   "Ham günlük veri" seçeneği, tüm ham veriler, anahtar sözcüğü arar.  
  
    -   "XML metni" ve "XML özniteliği" seçenekleri yalnızca XML öğeleri arayın.  
  
    -   "İletisi günlüğe" seçeneğini anahtar sözcüğü yalnızca iletilerinde arar.  
  
-   Kök etkinlik yoksay: arama "000000000000" etkinliğinde izlemeleri yok sayar. Kök etkinlik izleme, hangi aktarımları çoğu binlerce sahip olduğunda bu büyük izleme dosyaları performansı artırır.  
  
### <a name="navigating-traces"></a>İzlemeler gezinme  
 İzlemeler adım adım uygulama çalışma zamanı sırasında kayıtlı olduğundan, izlemeleri gezinme uygulamanızda hata ayıklama yardımcı olabilir. Hizmet izleme görüntüleyicisini içindeki gitmek için çeşitli yöntemler sağlar.  
  
#### <a name="step-forward-or-backward"></a>İleriye veya geriye doğru adım  
 Program kodunda bir satır olarak her izleme düşünüyorsanız, ileri atlama çok "Adımlama", Visual Studio tümleşik geliştirme ortamı (IDE) benzer. Aynı zamanda geri izlemeleri geçebilirsiniz, farktır. İleri atlama etkinliğinde sonraki izleme geçme anlamına gelir.  
  
-   İleri Adım: Kullanma **etkinlik** menüsü veya "F10" tuşlarına basın. Ok tuşu "kapalı" izleme bölmesinde kullanabilirsiniz.  
  
-   Adım geri: Kullanmak **etkinlik** menüsü veya "F9" tuşuna basın. Ok tuşu "yedekleme" izleme bölmesinde kullanabilirsiniz.  
  
> [!NOTE]
>  WCF iletileri etkinlik makineler span kimlikleri taşıyabilir çünkü bu, farklı bir işlemde veya hatta farklı bir bilgisayar üzerinde gerçekleşen bir etkinliğin alabilir.  
  
#### <a name="follow-transfer"></a>Aktarım izleyin  
 Aktarım izlemeleri izleme dosyasında özel izlemeleri ' dir. Bir etkinlik için başka bir etkinlik aktarım izleme tarafından aktarabilir. Örneğin, "Etkinliği A", "Etkinliği B" aktarabilir. Böyle bir durumda, "Etkinliği A" ile ": etkinlik" adı ve aktarım simgesinde aktarım izleme yoktur. Bu aktarım izleme iki izlemeleri arasında bir bağlantıdır. "Etkinliği B" da olabilir geri "etkinliği için bir" aktarmak üzere etkinlik sonunda aktarım izleme. Bu işlev çağrıları programlarda benzer: A, B döndürür sonra B çağırır.  
  
 "Aktarımı takip" Hata Ayıklayıcısı'ndaki "Adımla" benzer. Bu aktarım A'dan B'ye izler Diğer izlemeleri herhangi bir etkisi yok.  
  
 Bir aktarım izlemek için iki yolu vardır: klavye veya fare tarafından:  
  
-   Fareyle: izleme bölmesinde aktarım izleme çift tıklayın.  
  
-   Klavye tarafından: aktarımı izleme seçin ve "Transfer izleyin" kullanmak **etkinlik** menüsü veya "F11" tuşlarına basın  
  
> [!NOTE]
>  Etkinlik bir etkinlik B'ye aktarırken etkinlik B geri etkinlik A. aktarır çoğu durumda, etkinlik A bekler Bu, etkinlik bir etkinlik B etkin olarak izleme zaman süresi boyunca açık hiç bir izleme olduğu anlamına gelir. Ancak, aynı zamanda etkinlik A beklememek ve izlemeleri oturum devam mümkündür. Ayrıca etkinlik B geri etkinlik A. aktarmaz mümkündür Bu nedenle, etkinlik aktarımları hala bu bağlamdaki işlev çağrılarını farklıdır. Etkinlik aktarımları Grafik görünümünde daha iyi anlayabilirsiniz.  
  
#### <a name="jump-to-next-or-previous-transfer"></a>Sonraki veya önceki aktarımı atlama  
 Birden çok etkinliği seçildiğinde, geçerli etkinliği veya seçili etkinlikler çözümlemesi yaparken, için aktarır etkinlikleri kolayca bulmak isteyebilirsiniz. "Sonraki aktarım atlama" sonraki aktarım izleme etkinliğini bulmak için sağlar. Aktarım izleme bulduktan sonra sonraki etkinliği adımla için "aktarımı takip"'ı kullanabilirsiniz.  
  
-   Atlama sonraki aktarmak için: kullanım **etkinlik** menüsü veya "Ctrl + F10" tuşlarına basın.  
  
-   Atlama önceki aktarmak için: kullanım **etkinlik** menüsü veya "Ctrl + F9" tuşuna basın.  
  
#### <a name="navigate-in-graph-view"></a>Grafik görünümünde gezinme  
 Etkinlik ve izleme bölmesinde gezinme hata ayıklama için benzer olmakla birlikte, kullanarak **grafik** görünümü çok daha iyi bir deneyim Gezinti de sağlar. Daha fazla bilgi için "Grafik görünümü" bölümüne bakın.  
  
### <a name="loading-large-trace-files"></a>Büyük izleme dosyaları yükleniyor  
 İzleme dosyası çok büyük olabilir. Örneğin, birkaç dakika çalıştıran kolayca için "Ayrıntılı" düzeyi, elde edilen izleme dosyası izleme kapatırsanız yüz megabayt veya daha da büyük, ağ hızını ve iletişim düzeni bağlı olabilir.  
  
 Hizmet izleme Görüntüleyicisi'nde çok fazla izleme dosyası açtığınızda, sistem performansını olumsuz yönde etkilenebilir. Yükleme hızı ve yükleme sonrasında yanıt süresi yavaş olabilir. Gerçek hızı, zaman zaman, donanım yapılandırmanıza bağlı olarak farklılık gösterir. Çoğu PC içinde 200 M büyük bir izleme dosyası yüklenirken bir önemli performans etkisi olur. İzlemeler için 1 G'den büyük dosyaları, araç tüm kullanılabilir bellek kullanın veya çok uzun bir süredir yanıt vermiyor.  
  
 Büyük izleme dosyaları çözümlenerek içinde yanıt süresi ve yavaş yüklenmesini önlemek için hizmet izleme görüntüleyicisini "Kısmi izleme küçük bir bölümünü aynı anda yalnızca yükleyen yüklemeden" adlı bir özelliği sağlar. Örneğin, bir izleme dosyasını 1 birkaç gün boyunca sunucu üzerinde çalışan GB'den, olabilir. Bazı hatalar oluşmuş ve izleme analiz etmek istiyorsanız, tüm izleme dosyasını açmak gerekli değildir. Bunun yerine, zaman zaman hatası oluşmuş olabilir bir belirli bir süre içinde izlemeleri yükleyebilirsiniz. Kapsam daha küçük olduğu için hizmet izleme Görüntüleyicisi aracı dosyanın daha hızlı yükleyebilir ve daha küçük bir veri kümesi kullanarak hataları tanımlayabilir.  
  
#### <a name="enabling-partial-loading"></a>Kısmi yükleme etkinleştirme  
 Kısmi yükleme el ile etkinleştirmeniz gerekmez. Yükleme denemesi izleme dosyaların toplam boyutu, 40 MB aşarsa, hizmet izleme görüntüleyicisini kısmi yükleme bir iletişim kutusu, yüklemek istediğiniz bölümü seçmek için otomatik olarak görüntüler.  
  
> [!NOTE]
>  İzlemeler zamanında eşit olarak dağıtılmış değil çünkü yayılma, kısmi araç gösterilen yükleme orantılı olmayabilir yüklemede belirttiğiniz süre uzunluğu. Gerçek yükleme boyutu kısmi yükleniyor iletişim tahmini boyutundan küçük olabilir.  
  
#### <a name="adjusting-partial-loading"></a>Kısmi yüklenmesini ayarlama  
 İzleme dosyası kısmen yüklemiş sonra yüklenmekte olan veri kümesini değiştirmek isteyebilirsiniz. Kısmi yüklenirken üstündeki araç çubuğunda görüntüleyicisinin ayarlayarak bunu yapabilirsiniz.  
  
1.  Araç tarafından fareyi hareket ettirin veya başlangıç ve bitiş saati girin.  
  
2.  Tıklatın **Ayarla** düğmesi.  
  
## <a name="understanding-trace-icons"></a>Anlama İzleme simgeleri  
 Hizmet izleme Görüntüleyicisi aracı kullanır simge listesi aşağıdadır **etkinlik** görünümü **grafik** Görünüm ve **izleme** farklı öğeleri göstermek için bölmesi.  
  
> [!NOTE]
>  Kategorilere Ayrılmadı bazı izlemeler (örneğin, "bir ileti kapalı") bir simgesi vardır.  
  
### <a name="activity-tracing-traces"></a>İzlemeler izleme etkinliği  
  
|Simge|Açıklama|  
|----------|-----------------|  
|![Uyarı izleme](../../../docs/framework/wcf/media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Uyarı izleme: uyarı düzeyinde yayılan bir izleme|  
|![Hata izleme](../../../docs/framework/wcf/media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Hata izleme: hata düzeyinde yayılan bir izleme.|  
|![Etkinlik Başlangıç izleme:](../../../docs/framework/wcf/media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Etkinlik Başlangıç izleme: bir etkinlik başlangıcını işaretleyen izleme. Bu etkinliğin adını içerir. Uygulama Tasarımcısı ya da geliştiricisi olarak, bir etkinliğin etkinlik kimliği işlem veya iş parçacığı başına başına başlangıç izleme tanımlamanız gerekir.<br /><br /> Etkinlik Kimliği izleme bağıntı izleme kaynakları arasında yayılır, daha sonra aynı etkinlik kimliği (izleme kaynak her bir) için birden çok başlatır görebilirsiniz. İzleme kaynağı ActivityTracing etkinleştirilirse başlangıç izleme yayınlanır.|  
|![Etkinlik İzlemeyi Durdur](../../../docs/framework/wcf/media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Etkinlik İzlemeyi Durdur: Etkinliğin sonunu işaretleyen izleme. biçimindeki telefon numarasıdır. Bu etkinliğin adını içerir. Uygulama Tasarımcısı ya da geliştiricisi olarak, bir etkinliğin etkinlik kimliği izleme kaynağı başına başına İzlemeyi Durdur tanımlamanız gerekir. Hiçbir izlemeleri belirtilen izleme kaynağına izleme zaman ayrıntı yeterince küçük değilse dışında bu izleme kaynağı tarafından gösterilen Dur etkinlikten sonra görünür. Bu durum oluştuğunda bir Dur birlikte aynı anda ile iki izlemeleri görüntülendiğinde araya. Etkinlik Kimliği izleme bağıntı izleme kaynakları arasında yayılır aynı etkinlik kimliği (izleme kaynak her bir) için birden çok durdurulur görebilirsiniz. ActivityTracing izleme kaynağı etkinse, İzlemeyi Durdur yayınlanır.|  
|![Etkinlik askıya alma izleme](../../../docs/framework/wcf/media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Etkinlik askıya alma izleme: bir etkinlik duraklatıldı zaman işaretleyen izleme. Etkinlik yeniden devam edene dek hiçbir izlemeleri askıya alınmış bir etkinlik gösterilen. Askıya alınmış bir etkinlik hiçbir işlem izleme kaynağı kapsamı içinde bu etkinlikte gerçekleşmekte olduğunu gösterir. Askıya alma Sürdür izlemeleri, profil için faydalıdır. ActivityTracing izleme kaynağı etkinse, askıya alma izleme yayınlanır.|  
|![Etkinlik izleme sürdürmek](../../../docs/framework/wcf/media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4e0a-9988-cdc2f7030f17")|Etkinlik izleme Sürdür: askıya alınmış sonra bir etkinlik sürdürüldü zaman işaretleyen izleme. Bu etkinlikte izlemeleri yeniden yayılan. Askıya alma Sürdür izlemeleri, profil için faydalıdır. İzleme kaynağı ActivityTracing etkinleştirilirse Sürdür izleme yayınlanır.|  
|![Aktarım](../../../docs/framework/wcf/media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Aktarım: mantıksal denetim akışı bir etkinlikten diğerine aktarılırken yayılan bir izleme. Aktarımı kaynaklandığı etkinlik aktarımı gider etkinliğine paralel iş gerçekleştirmeye devam edebilir. İzleme kaynağı ActivityTracing etkinleştirilirse aktarım izleme yayınlanır.|  
|![Aktarımı](../../../docs/framework/wcf/media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Aktarımı: başka bir etkinliğin geçerli etkinliği bir aktarımı tanımlayan bir izleme.|  
|![Transfer](../../../docs/framework/wcf/media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Aktarım için: bir aktarımını mantıksal denetim akışı geçerli etkinliğinden başka bir etkinliğin tanımlayan bir izleme.|  
  
### <a name="wcf-traces"></a>WCF izlemeleri  
  
|Simge|Açıklama|  
|----------|-----------------|  
|![Günlük izleme iletisi](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Günlük izleme iletisi: bir WCF ileti ileti günlüğe kaydetme özelliği tarafından günlüğe kaydedildiğinde yayılan izleme zaman `System.ServiceModel.MessageLogging` izleme kaynağını etkindir. Bu izleme tıklatarak iletisi görüntülenir. Bir ileti için dört yapılandırılabilir günlüğe kaydetme noktası vardır: ServiceLevelSendRequest, TransportSend, TransportReceive ve tarafından da belirtilebilir ServiceLevelReceiveRequest `messageSource` ileti günlüğü izleme özniteliği.|  
|![Alınan izleme iletisi](../../../docs/framework/wcf/media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Alınan izleme iletisi: bir WCF ileti alındığında, gösterilen izleme `System.ServiceModel` izleme kaynağını bilgi veya ayrıntı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliğini görüntülemek için gerekli olan **grafik** görünümü.|  
|![Gönderilen izleme iletisi](../../../docs/framework/wcf/media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Gönderilen izleme iletisi: varsa bir WCF ileti gönderildiğinde yayılan izleme `System.ServiceModel` izleme kaynağını bilgi veya ayrıntı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliğini görüntülemek için gerekli olan **grafik** görünümü.|  
  
### <a name="activities"></a>Etkinlikler  
  
|Simge|Açıklama|  
|----------|-----------------|  
|![Activity](../../../docs/framework/wcf/media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Etkinliği: Geçerli etkinlik genel bir etkinlik olduğunu gösterir.|  
|![Kök etkinlik](../../../docs/framework/wcf/media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Kök etkinlik: bir işlem kök etkinliğini gösterir.|  
  
### <a name="wcf-activities"></a>WCF etkinlikleri  
  
|Simge|Açıklama|  
|----------|-----------------|  
|![Ortam etkinlik](../../../docs/framework/wcf/media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Ortam etkinliği: oluşturur, açar veya bir WCF konak veya istemci kapatır bir etkinlik. Bu aşamaları sırasında oluşmuş hatalar bu etkinlikte görünecektir.|  
|![Etkinlik dinleme](../../../docs/framework/wcf/media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Etkinlik dinleme: izlemeleri günlüklerini bir etkinlik için bir dinleyici ilgili. Bu etkinliği içinde biz dinleyicisi bilgileri ve bağlantı isteklerini görüntüleyebilirsiniz.|  
|![Alma bayt etkinliğinin](../../../docs/framework/wcf/media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Bayt etkinlik alırsınız: tüm izlemeleri grupları bir etkinlik ilgili iki uç noktalar arasında bir bağlantı gelen bayt alma ile. Bu etkinlik, http.sys gibi etkinlik kimliği yayma aktarım etkinliklerle bağıntı gereklidir. Bu etkinlik, bağlantı hatalarını iptalleri gibi görünür.|  
|![İleti etkinliği işlemek](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|İleti etkinliği işlemek: izlemeleri grupları bir etkinlik ilgili bir WCF ileti oluşturmak için. Bu etkinlikte hataları nedeniyle hatalı zarf veya hatalı bir ileti görünür. Bu etkinliği içinde biz bir etkinlik kimliği bir çağrıyı yapandan yayıldığı görmek için ileti üstbilgilerini inceleyebilirsiniz. Biz işlem eylem aktivitesi (sonraki simgesi) aktardığınızda bu true ise, biz bu etkinliğe çağıran ve çağrılan'ın izlemeleri arasında bağıntı yayılan etkinlik kimliği atayabilirsiniz.|  
|![Günlük izleme iletisi](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Eylem etkinlik işlem: tüm izlemeleri grupları bir etkinlik iki uç noktalar arasında bir WCF isteğine ilgili. Varsa `propagateActivity` ayarlanır `true` yapılandırmasındaki her iki uç noktalarda doğrudan bağıntı için bir etkinlik her iki uç noktalar tüm izlemeleri birleştirilir. Bu tür etkinlik aktarım ya da işlem, kullanıcı kodu sınırına genişletme güvenlik nedeniyle hatalar içeren ve (bir yanıt varsa) geri.|  
|![İleti etkinliği işlemek](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Kullanıcı kodu etkinliği yürütmek: kullanıcı kodu grupları bir etkinlik bir isteği işlemek için izler.|  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Kayıt defterine yazma izni yoksa, "Microsoft Service izleme görüntüleyicisini kaydedilmemiş sisteme" aşağıdaki hata iletisini alırsınız kullandığınızda, "`svctraceviewer /register`" aracı kaydetmek için komutu. Bu gerçekleşirse, kayıt defterine yazma erişimi olan bir hesap kullanarak oturum açması gerekir.  
  
 Ayrıca, hizmet izleme Görüntüleyicisi aracı bazı ayarları (örneğin, özel filtreler ve filtreleme seçeneklerini) derleme klasörü SvcTraceViewer.exe.settings dosyasına yazar. Dosya için okuma izni yoksa, aracı hala başlatabilirsiniz, ancak ayarları yüklenemiyor.  
  
 "Bilinmeyen bir hata oluştu bir veya daha fazla izlemeler işlenirken" hata iletisi alırsanız .etl dosyası açılırken .etl dosyasının biçimi geçersiz olduğunu gösterir.  
  
 Arapça bir işletim sistemi kullanılarak oluşturulan bir izleme günlüğü açarsanız, filtre çalışmıyor saat fark edebilirsiniz. Örneğin, yıl 2005 Arapça takvimindeki yılın 1427 karşılık gelir. Ancak, hizmet izleme Görüntüleyicisi aracı Filtresi tarafından desteklenen zaman aralığı 1752'den önceki bir tarih desteklemez. Bu, filtrenin doğru bir tarih seçin mümkün olmadığını kapsıyor. Bu sorunu gidermek için bir özel filtre oluşturabilirsiniz (**görünüm/özel filtreler**) belirli bir zaman aralığına dahil etmek için bir XPath ifadesi kullanarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [İzlemeyi Yapılandırma](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Etkinlik izleme ve uçtan uca izleme bağıntı yayma](http://msdn.microsoft.com/library/2c11a905-64f8-47b5-bae5-a74fc666137e)
