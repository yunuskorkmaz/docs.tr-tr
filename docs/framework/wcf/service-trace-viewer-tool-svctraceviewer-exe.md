---
title: Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)
description: WCF hizmeti sorunlarını tanılamanıza, onarmanıza ve doğrulayabilmeniz için günlükteki izleme iletilerini birleştirmek, görüntülemek ve filtrelemek için hizmet Izleme Görüntüleyicisi 'ni kullanın.
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: 0ad6094965291a965346522688a8334abbd4e6b3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244575"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)

Windows Communication Foundation (WCF) hizmet Izleme Görüntüleyicisi Aracı, WCF tarafından oluşturulan tanılama izlemelerini çözümlemenize yardımcı olur. Hizmet Izleme Görüntüleyicisi, WCF hizmeti sorunlarını tanılamanıza, onarmanıza ve doğrulayabilmeniz için günlükteki izleme iletilerini kolayca birleştirmek, görüntülemek ve filtrelemek için bir yol sağlar.

## <a name="configuring-tracing"></a>İzlemeyi Yapılandırma

Tanılama izlemeleri, uygulamanızın işlemi boyunca neler olduğunu gösteren bilgiler sağlar. Adından da anlaşılacağı gibi, işlemler kaynağından hedefe ve ara noktalara göre işlemleri izleyebilirsiniz.

Uygulamanın yapılandırma dosyasını kullanarak izlemeyi, Web 'de barındırılan uygulamalar için Web.config ya da şirket içinde barındırılan uygulamalar için *appname*. config ' i kullanarak yapılandırabilirsiniz. Aşağıda bir örnek verilmiştir:

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

Bu örnekte, İzleme dinleyicisinin adı ve türü belirtilir. Dinleyici adlandırılır `sdt` ve standart .NET Framework İzleme dinleyicisi (System.Diagnostics.XmlWriterTraceListener) tür olarak eklenir. `initializeData`Özniteliği, bu dinleyicinin bir günlük dosyasının adını ayarlamak için kullanılır `SdrConfigExample.e2e` . Günlük dosyası için, basit bir dosya adı için tam olarak nitelenmiş bir yol kullanabilirsiniz.

Örnek, SdrConfigExample. e2e adlı kök dizinde bir dosya oluşturur. Izleme görüntüleyicisini kullanarak dosyayı "WCF Izleme dosyalarını açma ve görüntüleme" bölümünde açıklandığı gibi açtığınızda, gönderilen tüm iletileri görebilirsiniz.

İzleme düzeyi ayar tarafından denetlenir `switchValue` . Kullanılabilir izleme düzeyleri aşağıdaki tabloda açıklanmıştır.

|İzleme düzeyi|Description|
|-----------------|-----------------|
|Kritik|-Başarısız-hızlı ve olay günlüğü girişleri ve İzleme bağıntı bilgilerini günlüğe kaydeder. Kritik düzeyini ne zaman kullanacağınızı aşağıda bulabilirsiniz:<br />-İşlenmemiş bir özel durum nedeniyle AppDomain 'e aşağı gitti.<br />-Uygulamanız başlatılamıyor.<br />-İşlemden kaynaklanan hata MyApp.exe ileti.|
|Hata|-Tüm özel durumları günlüğe kaydeder. Aşağıdaki durumlarda hata düzeyini kullanabilirsiniz:<br />-Geçersiz bir tür dönüştürme özel durumu nedeniyle kodunuz kilitlendi.<br />-"Uç nokta oluşturulamadı" özel durumu, uygulamanızın başlangıçta başarısız olmasına neden oluyor.|
|Uyarı|-Daha sonra bir hata veya kritik hata oluşmasına neden olabilecek bir koşul var. Aşağıdaki durumlarda bu düzeyi kullanabilirsiniz:<br />-Uygulama, azaltma ayarlarından izin verdiğinden daha fazla istek alıyor.<br />-Alma sırası yapılandırılmış kapasitesinin yüzde 98 ' sinden fazla.|
|Bilgi|-Sistem durumunu izleme ve tanılama, performansı ölçme veya profil oluşturma konularında yararlı iletiler oluşturulur. Kapasite planlama ve performans yönetimi için bu bilgilerden yararlanabilirsiniz. Aşağıdaki durumlarda bu düzeyi kullanabilirsiniz:<br />-İleti AppDomain 'e ulaştıktan ve seri durumdan çıkarıldıktan sonra bir hata oluştu.<br />-HTTP bağlaması oluşturulurken bir hata oluştu.|
|Ayrıntılı|-Hem Kullanıcı kodu hem de bakım için hata ayıklama düzeyi izleme. Şu durumlarda bu düzeyi ayarla:<br />-Hata oluştuğunda kodunuzda hangi yöntemin çağrıldığı konusunda emin değilsiniz.<br />-Ayrılmış bir uç noktanız var ve ayırma deposundaki giriş kilitlendiğinden hizmet başlatılamadı.|
|ActivityTracing|İşlem etkinlikleri ve bileşenleri arasındaki akış olayları.<br /><br /> Bu düzey, yöneticilerin ve geliştiricilerin aynı uygulama etki alanındaki uygulamaları ilişkilendirmelerine olanak sağlar.<br /><br /> -Etkinlik sınırları için izlemeler: Başlat/Durdur.<br />-Aktarımlar için izlemeler.|

 `add`Kullanmak istediğiniz izleme dinleyicisinin adını ve türünü belirtmek için ' i kullanabilirsiniz. Örnek yapılandırmada, dinleyici adlandırılır `sdt` ve standart .NET Framework İzleme dinleyicisi ( `System.Diagnostics.XmlWriterTraceListener` ) tür olarak eklenir. `initializeData`Bu dinleyicinin günlük dosyasının adını ayarlamak için kullanın. Buna ek olarak, basit bir dosya adı için tam nitelikli bir yol kullanabilirsiniz.

.NET Framework 4,8 ' den başlayarak, bazı yüksek karşıtlık temalarında ComboBox denetimleri doğru renkte görüntülenir. *svcTraceViewer.exe.config* dosyasından aşağıdaki ayarı kaldırarak bu değişikliği devre dışı bırakabilirsiniz:

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

## <a name="using-the-service-trace-viewer-tool"></a>Hizmet Izleme Görüntüleyicisi aracını kullanma

### <a name="opening-and-viewing-wcf-trace-files"></a>WCF Izleme dosyalarını açma ve görüntüleme

Hizmet Izleme Görüntüleyicisi üç dosya türünü destekler:

- WCF Izleme dosyası (. svcLog)

- Olay Izleme dosyası (. etl)

- Crimson Izleme dosyası

 Service Trace Viewer, desteklenen herhangi bir izleme dosyasını açmanıza, ek izleme dosyaları eklemenize ve tümleştirmenize ya da bir izleme dosyaları grubunu aynı anda açıp birleştirmeye olanak sağlar.

##### <a name="to-open-a-trace-file"></a>Bir izleme dosyasını açmak için

1. WCF yükleme konumunuza (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin) gitmek için bir komut penceresi kullanarak hizmet Izleme görüntüleyicisini başlatın ve ardından yazın `SvcTraceViewer.exe` .

> [!NOTE]
> Hizmet Izleme Görüntüleyicisi aracı iki dosya türüyle ilişkilendirebilir:. svclog ve. stvproj. Dosya uzantılarını kaydetmek ve kaydını silmek için komut satırında iki parametre kullanabilirsiniz.
>
> /Register: dosya uzantılarının ". svclog" ve ". stvproj" ilişkilendirmesini SvcTraceViewer.exe ile kaydedin
>
> /Unregister: ". svclog" ve ". stvproj" dosya uzantılarının ilişkilendirmesini SvcTraceViewer.exe ile

1. Hizmet Izleme Görüntüleyicisi başladığında **Dosya** ' ya tıklayın ve sonra **Aç**' a gelin. İzleme Dosyalarınızın depolandığı konuma gidin.

2. Açmak istediğiniz izleme dosyasına çift tıklayın.

    > [!NOTE]
    > Aynı anda seçmek ve açmak için birden çok izleme dosyasına tıklarken SHIFT tuşuna basın. Hizmet Izleme Görüntüleyicisi tüm dosyaların içeriğini birleştirir ve bir görünüm sunar. Örneğin, hem istemci hem de hizmetin izleme dosyalarını açabilirsiniz. Bu, yapılandırmada ileti günlüğe kaydetmeyi ve etkinlik yaymayı etkinleştirdiğinizde yararlıdır. Bu şekilde, istemci ve hizmet arasındaki ileti değişimini inceleyebilirsiniz. Ayrıca, birden çok dosyayı görüntüleyiciye sürükleyebilir veya **Proje** sekmesini kullanabilirsiniz. Daha fazla bilgi için projeyi yönetme bölümüne bakın.

3. Açık koleksiyona ek izleme dosyaları eklemek için **Dosya** ' ya tıklayın ve ardından **Ekle**' ye gelin. Açılan pencerede, izleme dosyalarının konumuna gidin ve eklemek istediğiniz dosyaya çift tıklayın.

> [!CAUTION]
> 200 MB 'den büyük bir izleme günlüğü dosyası yüklemeniz önerilmez. Bu sınırdan daha büyük bir dosya yüklemeye çalışırsanız, bilgisayarınızın kaynağına bağlı olarak yükleme işlemi uzun sürebilir. Hizmet Izleme Görüntüleyicisi aracı uzun süredir yanıt vermeyebilir veya makinenizin belleğini tüketebilir. Bunu önlemek için kısmi yüklemeyi yapılandırmanız önerilir. Bunun nasıl yapılacağı hakkında daha fazla bilgi için "büyük Izleme dosyalarını yükleme" bölümüne bakın.

#### <a name="event-tracing-and-crimson-tracing"></a>Olay Izleme ve Crimson Izleme

Görüntüleyicinin yerel biçimi, WCF 'nin yaydığı etkinlik izleme biçimidir. Farklı biçimde yayılan izlemeler, Görüntüleyici tarafından görüntülenmeden önce dönüştürülmelidir. Şu anda, etkinlik izleme biçimine ek olarak, Görüntüleyici olay izlemeyi ve Crimson izlemeyi destekler.

Etkinlik izlemeleri içermeyen bir dosyayı açtığınızda, görüntüleyici dosyayı dönüştürmeye çalışır. Dönüştürülen izleme verilerini içerecek dosyanın adını ve konumunu belirtmeniz gerekir. Veriler dönüştürüldükten sonra, görüntüleyici yeni dosyanın içeriğini görüntüler.

> [!NOTE]
> Dönüştürme, dönüştürülmüş izleme verilerini depolamak için disk alanı gerektirir. Dönüştürme işlemine başlamadan önce, verileri depolamak için yeterli disk alanına sahip olduğunuzdan emin olun. Aksi takdirde, dönüştürme başarısız olur.

### <a name="managing-projects"></a>Projeleri yönetme

Görüntüleyici, birden çok izleme dosyasını görüntülemeyi kolaylaştırmak için projeleri destekler. Örneğin, bir istemci izleme dosyanız ve bir hizmet izleme dosyanız varsa, bunları bir projeye ekleyebilirsiniz. Ardından, projeyi her açışınızda projedeki tüm izleme dosyaları aynı anda yüklenir.

Projeleri yönetmenin iki yolu vardır:

- **Dosya** menüsünde projeleri açabilir, kaydedebilir ve kapatabilirsiniz.

- **Proje** sekmesinde, bir projeye dosyalar ekleyebilirsiniz.

### <a name="viewing-wcf-traces"></a>WCF Izlemelerini görüntüleme

WCF, etkinlik izleme biçimini kullanarak izlemeleri yayar. Etkinlik izleme modelinde, bireysel izlemeler, kendi amaçlarına göre etkinliklerde gruplandırılır. Mantıksal denetim akışı etkinlikler arasında aktarılır. Örneğin, bir uygulamanın kullanım ömrü boyunca pek çok "ileti gönderme etkinliği" görüntülenir ve kaybolur. İzleme ve etkinlikleri görüntüleme hakkında daha fazla bilgi ve hizmet Izleme görüntüleyicisinin Kullanıcı arabirimi de, bkz. [bağıntılı izlemeleri ve sorun gidermeyi görüntülemek Için hizmet Izleme görüntüleyicisini kullanma](./diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).

#### <a name="switching-to-different-views"></a>Farklı görünümlere geçme

Hizmet Izleme Görüntüleyicisi aşağıdaki farklı görünümleri sağlar. Bunlar, görüntüleyicisinin sol bölmesinde sekmeler olarak görüntülenir ve **Görünüm** menüsünden de erişilebilir.

- Etkinlik görünümü

- Proje görünümü

- İleti görünümü

- Graf Görünümü

##### <a name="activity-view"></a>Etkinlik görünümü

İzleme dosyaları açıldıktan sonra etkinlikler halinde gruplanmış ve sol bölmedeki **etkinlik** görünümünde görüntülenen izlemeleri görebilirsiniz.

Etkinlik **görünümü etkinlik** adlarını, etkinlik içindeki izlemelerin sayısını, süre süresini, başlangıç saatini ve bitiş saatini görüntüler.

Listelenen etkinliklerin herhangi birine tıkladığınızda, bu etkinlikteki izlemeler sağdaki izleme bölmesinde görüntülenir. Daha sonra ayrıntılarını görüntülemek için bir izleme seçebilirsiniz.

**CTRL** veya **SHIFT** tuşuna basarak ve istenen etkinliklere tıklayarak birden fazla etkinlik seçebilirsiniz. İzleme bölmesi, seçilen etkinliklerin tüm izlemelerini görüntüler.

**Grafik** görünümünde görüntülemek için bir etkinliğe çift tıklayabilirsiniz. Alternatif yol, bir etkinlik seçmek ve **grafik** görünümüne geçmek.

> [!NOTE]
> "000000000000" etkinliği grafik görünümünde görüntülenemeyecek özel bir etkinliktir. Diğer tüm etkinlikler onunla bağlantılı olduğundan, bu etkinliğin gösterilmesi önemli bir performans etkisine sahiptir.

Etkinlik listesini sıralamak için sütun başlığına tıklayabilirsiniz. Uyarı izlemeleri içeren etkinliklerin sarı bir arka planı vardır ve hata izlemelerinin kırmızı bir tane vardır.

Farklı türlerde etkinlikler vardır ve her bir tür, her etkinliğin sol tarafındaki bir simgeye karşılık gelir. Anlamları için Izleme simgelerini anlama bölümüne başvurabilirsiniz.

##### <a name="project-view"></a>Proje görünümü

Bu görünüm, geçerli projedeki izleme dosyalarını yönetmenizi sağlar. Daha fazla bilgi için projeyi yönetme bölümüne bakın.

##### <a name="message-view"></a>İleti görünümü

Bu görünüm eylem, tarih/saat, Işlem, Aciçekimi ve From/To dahil tüm ileti günlüğü izlemelerini görüntülemenize ve ilişkili ileti günlüğü izlemenin ayrıntılarına gitmenize olanak sağlar. İleti akışının daha kolay gezinmesi için etkinlik sınırına, Işleme/Iş parçacığına göre ileti günlüğü izlemelerini gruplandırabilir veya & alma gönderebilirsiniz.

##### <a name="graph-view"></a>Graf Görünümü

Bu görünüm, grafik formundaki belirli bir etkinliğin izleme verilerini görüntüler. Grafik formu, verilerin aralarında taşınması halinde olayların ve birden çok etkinlik arasındaki ilişkilerin birlikte yürütülmesini görmenizi sağlar.

**Grafik** görünümüne geçiş yapmak için **etkinlik** görünümündeki bir etkinliği seçin ve **etkinlik** sekmesine tıklayın veya **ileti** görünümünde bir ileti günlüğü izleyin. Birden çok izleme dosyası yüklenirse ve etkinlik birden fazla dosyadan izleme içeriyorsa, tüm ilgili izlemeler grafik görünümünde görüntülenir. Etkinliklere ve mesaj günlüğü izlemeleri ' na çift tıkladığınızda **grafik** görünümüne de yol görüntülenir.

**Graph** görünümünde, her dikey sütun bir etkinliği temsil eder ve sütundaki her bir blok bir izlemeyi temsil eder. Etkinlikler işleme göre gruplandırılır (veya iş parçacığı). Etkinlikler arasındaki küçük oklar aktarımları temsil eder. Süreçler arasındaki büyük oklar ileti değişimini temsil eder. Seçimdeki etkinlik her zaman sarı olarak belirlenir.

###### <a name="selecting-traces-in-the-graph"></a>Grafikteki Izlemeleri seçme

1. Grafikteki bir bloğa tıklayın.

2. Yukarı ve aşağı tuşlarını kullanarak komşu izlemelerinin seçimini yapın.

3. İzleme bölmesinde ve ayrıntı bölmesinde izleme bilgilerini gözlemleyin.

###### <a name="expanding-or-collapsing-activity-transfers"></a>Etkinlik aktarımlarını genişletme veya daraltma

Seçimdeki etkinlik başka bir etkinliğe aktardığınızda, etkinlik aktarımlarını genişletebilirsiniz. Aktarımları izlemenizi sağlar.

Etkinlik aktarımlarını genişletmek veya daraltmak için

1. Aktarım simgesinin solunda bir "+" işareti ile aktarım izlemesini bulun.

2. "+" Düğmesine tıklayın veya klavyeyi kullanarak **CTRL** ve "+" tuşlarına basın.

3. Sonraki etkinlik grafikte görüntülenir.

4. Aktarım simgesinin solunda bir "-" görünür. "-" İşaretine tıklayın veya CTRL ve "-" tuşlarına basarak etkinlik aktarımı daraltılır.

> [!NOTE]
> Bir etkinliğin içine birden fazla aktarımı olduğunda ve aktarımlardan birini genişlettiğinizde, kök etkinlikten yeni etkinliğe yol açabilecek etkinlikler görüntülenir. Bu yeni etkinlikler daraltılmış biçimde görünür. Bu etkinliklerin ayrıntılarını görmek isterseniz, grafiğin üstbilgisindeki Genişlet simgesine tıklayarak bunları dikey olarak genişletin.

###### <a name="expanding-or-collapsing-activities-vertically"></a>Etkinlikleri dikey olarak genişletme veya daraltma

Görüntüleyici etkinlikleri daraltarak etkinlik grafiğinde gereksiz ayrıntıyı gizler. Daraltılmış bir etkinlikte, bireysel izlemeler gösterilmez. Yalnızca aktarım izleme görüntülenir. Bir etkinlikteki tüm izlemeleri görüntülemek istiyorsanız, grafiğin üstbilgisinde etkinliğin genişletme simgesine tıklayarak etkinliği dikey olarak genişletin.

Etkinlikleri dikey olarak genişletmek veya daraltmak için

1. Etkinliği dikey olarak genişletmek için etkinlik üstbilgisindeki "+" simgesine tıklayın.

2. Tüm izlemelerin grafikte görüntülendiğinden emin olun.

3. Etkinliği dikey olarak daraltmak için etkinlik üstbilgisindeki "-" simgesine tıklayın.

4. Etkinlikte yalnızca önemli aktarımların, ileti günlüklerinin, uyarının ve özel durum izlemelerinin gösterildiğine dikkat edin.

###### <a name="options"></a>Seçenekler

Grafik görünümündeki **seçenek** menüsünden iki seçenek belirleyebilirsiniz.

- Grafikteki etkinlik sınırı izlemelerini işaretlenmediğinde, etkinlik sınırı Izlemelerini göster.

- İleti izlemeleri hariç, denetimsiz ayrıntı düzeyi izlemelerinin işaretini kaldırdığınızda ileti olmayan ayrıntılı Izlemeleri göster. Çoğu durumda, ayrıntı düzeyi izlemeleri analiz için daha az önemlidir. Bu seçenek, ayrıntılı düzeyi izlemeleri çözümlemek istemediğiniz ve yalnızca daha önemli izlemelere odaklanmak istemediğinizde yararlıdır.

###### <a name="layout-mode"></a>Düzen modu

Görüntüleyicinin iki düzen modu vardır: **işlem** ve **iş parçacığı**. Bu ayar, en büyük kuruluş birimini tanımlar. Varsayılan düzen modu **işlem**olur, bu da etkinliklerin grafikteki işlemlere göre gruplanmasıdır.

###### <a name="execution-list"></a>Yürütme listesi

Grafikte görüntülenecek işlem veya iş parçacığını, bu açılan listeden seçebilirsiniz. Örneğin, iki istemci (A ve B) izleme dosyalarınız ve bir hizmet açılırsa ve yalnızca bir hizmet ve istemci A 'yı grafikte göstermek istiyorsanız, istemci B 'yi listeden kaldırabilirsiniz.

#### <a name="viewing-trace-details"></a>Izleme ayrıntılarını görüntüleme

İzleme ayrıntılarını görüntülemek için, Izleme bölmesinde bir izleme seçin. Ayrıntılar, ayrıntı bölmesinde görüntülenir.

##### <a name="trace-pane"></a>İzleme bölmesi

Hizmet Izleme görüntüleyicisindeki sağ üst bölmede Izleme bölmesi bulunur. Seçili etkinlikteki tüm izlemeleri, örneğin, izleme düzeyi, iş parçacığı KIMLIĞI ve işlem adı gibi ek bilgilerle listeler.

Bir izlemeye sağ tıklayıp **Izlemeyi panoya kopyala**' yı seçerek IZLEMENIN ham xml 'sini panoya kopyalayabilirsiniz.

##### <a name="detail-pane"></a>Ayrıntı bölmesi

Hizmet Izleme görüntüleyicisinde sol alt bölmede ayrıntı bölmesi bulunur. İzleme ayrıntılarını görüntülemek için üç sekme sağlar.

**Biçimlendirilen** görünüm, bilgileri daha düzenli bir şekilde görüntüler. Tablolardaki ve ağaçlarda bilinen tüm XML öğelerini listeler, bu da bilgileri okumayı ve anlamayı kolaylaştırır.

**XML** görünümü seçili izlemeye KARŞıLıK gelen XML 'yi görüntüler. Vurgulamayı ve sözdizimi rengini destekler. Dizeleri aramak için **bul** 'u kullandığınızda, arama sonuçlarını vurgular.

**İleti** görünümü ileti günlüğü IZLEMELERINDE XML 'nin ileti parçasını görüntüler. İleti olmayan bir izleme seçtiğinizde görünmez.

### <a name="filtering-wcf-traces"></a>WCF Izlemelerini filtreleme

İzlemenin analizini daha kolay hale getirmek için bunları aşağıdaki yollarla filtreleyebilirsiniz:

- Filtre araç çubuğu, önceden tanımlanmış ve özel filtrelere erişim sağlar. **Görünüm** menüsü aracılığıyla etkinleştirilebilir.

- Görüntüleyicinin önceden tanımlanmış filtresi, WCF izlemelerinin parçalarını seçmeli filtrelemek için kullanılabilir. Varsayılan olarak, tüm altyapı izlemelerinin geçiş yapmasına izin vermek üzere ayarlanır. Bu filtrenin ayarları, **Görünüm** menüsündeki **filtre seçenekleri** alt menüsünde tanımlanmıştır.

- Özel XPath filtreleri kullanıcılara filtreleme üzerinde tam denetim sağlar. Bunlar, **Görünüm** menüsü altında **özel filtre** içinde tanımlanabilir.

Yalnızca tüm filtrelerle geçen izlemeler görüntülenir.

#### <a name="using-the-filter-toolbar"></a>Filtre araç çubuğunu kullanma

Filtre araç çubuğu, aracın üst kısmında görünür. Mevcut değilse, **Görünüm** menüsünden etkinleştirebilirsiniz. Çubuğun üç bileşeni vardır:

- **Aranan: arama** , filtre işleminde aranacak konuyu tanımlar. Örneğin, işlem X bağlamında oluşturulmuş tüm izlemeleri bulmak istiyorsanız, bu alanı X olarak ve alanında **Ara** ' işlem adı ' olarak ayarlayın. Bu alan, zaman tabanlı bir filtre seçildiğinde bir tarih saat Seçici denetimine değişir.

- İçinde ara: Bu alan uygulanacak filtrenin türünü tanımlar.

- Düzey: düzey ayarı, filtrenin izin verdiği en düşük izleme düzeyini tanımlar. Örneğin, düzey hata ve yukarı olarak ayarlandıysa yalnızca hata ve kritik düzeydeki izlemeler görüntülenir. Bu filtre, aranan ve arama ölçütü ile belirtilen ölçütlere göre birleşir.

**Şimdi filtrele** düğmesi filtre işlemini başlatır. Özellikle büyük bir veri kümesine uygulanan bazı filtreler, tamamlanması uzun zaman alır. **İşlemler** menüsünün altındaki durum çubuğunda görüntülenen **Durdur** düğmesine basarak filtre işlemini iptal edebilirsiniz.

**Şifresiz** düğme, tüm izlemelerin geçmesine izin vermek için önceden tanımlanmış ve özel filtreleri sıfırlar.

#### <a name="filter-options"></a>Filtre seçenekleri

Görüntüleyici, otomatik olarak WCF izlemelerini görünümden kaldırabilir. Belirli bir WCF alanı tarafından yayılan izlemeleri seçerek kaldırabilir, örneğin, görünümden işlemle ilgili izlemeler kaldırılıyor.

Bu filtrenin ayarları, **Görünüm** menüsündeki **filtre seçenekleri** alt menüsünde tanımlanmıştır.

#### <a name="custom-filters"></a>Özel Filtreler

XML yol dili (XPath) hakkında bilginiz varsa, herhangi bir XML öğesi için izleme verilerini aramak üzere özel filtreler oluşturmak için bunu kullanabilirsiniz. Filtreler Filtre araç çubuğu aracılığıyla erişilebilir.

Özel filtreler parametreler içerebilir. Ayrıca, önceden var olan özel filtreleri içeri aktarabilirsiniz.

##### <a name="creating-a-custom-filter"></a>Özel filtre oluşturma

Filtreler iki şekilde oluşturulabilir:

###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Şablon Sihirbazı 'Nı kullanarak özel filtre oluşturma

Mevcut bir izlemeye tıklayıp, izlemenin yapısına göre bir filtre oluşturabilirsiniz. Bu örnek iş parçacığı KIMLIĞI temel alınarak özel bir filtre oluşturur.

1. Görüntüleyicinin sağ üst bölümündeki izleme bölmesinde, filtrelemek istediğiniz öğeyi içeren bir izleme seçin.

2. İzleme bölmesinin en üstünde yer alan **özel filtre oluştur** düğmesine tıklayın.

3. Görüntülenen iletişim kutusunda filtreniz için bir ad girin. Bu örnekte, girin `Thread ID` . Filtreniz için bir açıklama da sağlayabilirsiniz.

4. Soldaki ağaç görünümü, 1. adımda seçtiğiniz izleme kaydının yapısını görüntüler. Koşul oluşturmak istediğiniz öğeye gidin. Bu örnekte, XPath: düğümünde bulunan ThreadID öğesine gidin /E2ETraceEvent/System/Execution/@ThreadID . Ağaç görünümündeki ThreadID özniteliğine çift tıklayın. Bu, iletişim kutusunun sağ tarafındaki özniteliği için bir ifade oluşturur.

5. ThreadID koşulunun parametre alanını None iken ' ' olarak değiştirin {0} . Bu adım, filtre uygulandığında ThreadID değerinin yapılandırılmasını sağlar. (Filtre uygulama bölümüne bakın) En fazla dört parametre tanımlayabilirsiniz. Koşullar OR işleci kullanılarak birleştirilir.

6. Filtreyi oluşturmak için **Tamam** ' ı tıklatın.

> [!NOTE]
> Şablon Sihirbazı kullanılarak bir filtre oluşturulduktan sonra yalnızca el ile düzenlenebilir. Daha önce oluşturulmuş bir filtre için Sihirbazı etkinleştirmek mümkün değildir. Ayrıca, şablon sihirbazında oluşturulan bir XPath filtresinin koşulları OR işleci kullanılarak birleştirilir. VE işlemine ihtiyacınız varsa, filtre ifadesini oluşturulduktan sonra düzenleyebilirsiniz.

###### <a name="creating-a-custom-filter-manually"></a>Özel bir filtreyi El Ile oluşturma

Özel filtreler menüsü, XPath filtrelerini el ile girmenize olanak sağlar.

1. Görünüm menüsünde **özel filtreler** menü öğesine tıklayın.

2. Görüntülenen iletişim kutusunda yeni ' ye tıklayın **.**

3. En azından bir filtre adı ve XPath ifadesi belirtin.

4. **Tamam**'a tıklayın.

###### <a name="applying-a-custom-filter"></a>Özel filtre uygulama

Özel bir filtre oluşturulduktan sonra filtre araç çubuğu buna karşın erişilebilir olur. Filtre araç çubuğunun **Içindeki arama** alanına uygulamak istediğiniz filtreyi seçin. Önceki örnekte ' Iş parçacığı KIMLIĞI ' seçeneğini belirleyin.

1. **Bulma** alanı alanında aradığınız değeri belirtin. Örneğimizde, aramak istediğiniz iş parçacığının KIMLIĞINI girin.

2. **Şimdi filtrele**' ye tıklayın ve işlemin sonucunu gözlemleyin.

Filtreniz birden çok parametre kullanıyorsa, '; ' öğesini '; ' öğesini **bul** alanına ayırıcı olarak girin. Örneğin, aşağıdaki dize 3 parametre tanımlar: ' 1; findValue; Text '. Görüntüleyici, filtrenin parametresine ' 1 ' uygular {0} . ' findValue ' ve ' text ', sırasıyla öğesine {1} uygulanır {2} .

###### <a name="sharing-custom-filters"></a>Özel filtreleri paylaşma

Özel filtreler, farklı oturumlar ve farklı kullanıcılar arasında paylaşılabilir. Filtreleri bir tanım dosyasına aktarabilir ve bu dosyayı başka bir konumda içeri aktarabilirsiniz.

 Özel bir filtreyi içeri aktarmak için:

1. **Görünüm** menüsünde **özel filtreler ' e**tıklayın.

2. Açılan iletişim kutusunda **Içeri aktar** düğmesine tıklayın.

3. Özel filtre dosyasına (. stvcf) gidin, dosyaya tıklayın ve **Aç** düğmesine tıklayın.

Özel bir filtreyi dışarı aktarmak için:

1. Görünüm menüsünde **özel filtreler ' e**tıklayın.

2. Açılan iletişim kutusunda, dışarı aktarmak istediğiniz filtreyi seçin.

3. **Dışarı aktar** düğmesine tıklayın.

4. Özel filtre tanım dosyasının (. stvcf) adını ve konumunu belirtin ve **Kaydet** düğmesine tıklayın.

> [!NOTE]
> Bu özel filtreler yalnızca hizmet Izleme görüntüleyicisinden içeri ve içeri aktarılabilir. Diğer araçlar tarafından okunamaz.

### <a name="finding-data"></a>Veri bulma

Görüntüleyici, verileri bulmak için aşağıdaki yolları sağlar:

- Bul araç çubuğu en sık kullanılan bulma seçeneklerine hızlı erişim sağlar.

- Bul iletişim kutusu daha fazla bulma seçeneği sağlar. Bu, **düzenleme** menüsünde veya kısayol tuşu Ctrl + F ile erişilebilir.

Bul araç çubuğu görüntüleyicinin en üstünde görünür. Mevcut değilse, **Görünüm** menüsünden etkinleştirebilirsiniz. Çubuğun iki bileşeni vardır:

- Aranan: arama anahtar sözcüğü girmenize Izin verir.

- Konum: arama kapsamını girmenize Izin verir. Tüm etkinliklerde mi yoksa yalnızca geçerli etkinlikte mi arama yapmak istediğinizi seçebilirsiniz.

Bul iletişim kutusu iki ek seçenek sunar:

- Hedefi bul:

  - "Ham günlük verileri" seçeneği, tüm ham verilerde anahtar sözcüğünü arar.

  - "XML metni" ve "XML özniteliği" seçenekleri yalnızca XML öğelerinde arama yapın.

  - "Günlüğe kaydedilen Ileti" seçeneği, anahtar sözcüğünü yalnızca iletilerde arar.

- Kök etkinliğini yoksay: arama, "000000000000" etkinliğindeki izlemeleri yoksayar. Bu, büyük izleme dosyalarında, kök etkinliğin çoğu aktarım olan binlerce izlem olduğunda performansı geliştirir.

### <a name="navigating-traces"></a>Izlemelere gitme

İzleme, uygulama çalışma zamanı sırasında adım adım kaydedildiğinden, izlemelerde gezinmek uygulamanızda hata ayıklamanıza yardımcı olabilir. Hizmet Izleme Görüntüleyicisi, izlemelerde gezinmek için çeşitli yollar sağlar.

#### <a name="step-forward-or-backward"></a>Ileri veya geri adımla

Her bir izlemeyi programdaki bir kod satırı olarak kabul ediyorsanız, ileri ' yi, Visual Studio tümleşik geliştirme ortamında (IDE) "Adımlama" a benzer. Fark, izlemelerde geriye doğru de adım adım olabilir. İleri atlama, etkinliğin sonraki izlemeye geçme anlamına gelir.

- Ileri adımla: **etkinlik** menüsünü kullanın veya "F10" tuşuna basın. İzleme bölmesinde "aşağı" ok tuşunu da kullanabilirsiniz.

- Geri adımla: **etkinlik** menüsünü kullanın veya "F9" tuşuna basın. İzleme bölmesinde "yukarı" ok tuşunu da kullanabilirsiniz.

> [!NOTE]
> Bu, sizi farklı bir işlemde veya hatta farklı bir bilgisayarda gerçekleşen bir etkinliğe götürebileceği için, WCF iletileri, makinelere yayılan etkinlik kimlikleri taşıyabilir.

#### <a name="follow-transfer"></a>Aktarımı izle

Aktarım izlemeleri, izleme dosyasındaki özel izlemelerdir. Bir etkinlik, bir aktarım izleme tarafından başka bir etkinliğe aktarabilir. Örneğin, "Activity A", "Activity B" öğesine aktarım gösterebilir. Böyle bir durumda, "Activity A" adında "to: Activity" ve aktarma simgesiyle bir aktarım izlemesi vardır. Bu aktarım izlemesi iki izleme arasındaki bir bağlantıdır. "Activity B" içinde, etkinliğin sonunda "Activity A" öğesine geri aktarılacak bir aktarım izlemesi de olabilir. Bu, programlarda işlev çağrılarına benzer: A çağrısı B, sonra B döndürür.

"Aktarımı izle" bir hata ayıklayıcıda "adımla" ya benzer. A 'dan B 'ye aktarımı izler. Başka izlemeler üzerinde herhangi bir etkiye sahip değildir.

Bir aktarımı izlemek için iki yol vardır: fareyle veya klavyeye göre:

- Fare: izleme bölmesinde aktarım izlemeye çift tıklayın.

- Klavyeye göre: bir aktarım izlemesi seçin ve **etkinlik** menüsünde "aktarımı izle" yi kullanın veya "F11" tuşuna basın.

> [!NOTE]
> Çoğu durumda, etkinlik b, etkinlik a 'ya aktarıldıktan sonra, etkinlik B, etkinlik A 'ya geri aktarana kadar bekler. Bu, etkinliğin B etkin bir şekilde izlendiğinde, etkinlik A 'nın dönemde günlüğe kaydedilen izleme olmadığı anlamına gelir. Ancak, A etkinliğinin beklememe olasılığı da vardır ve günlük izlemelerinin devam etmesini sağlar. B etkinliğinin A etkinliğine geri aktarılmadığından da olasıdır. Bu nedenle, etkinlik aktarımları hala bu anlamda işlev çağrılarından farklıdır. Grafik görünümünde etkinlik aktarımlarını daha iyi anlayabilirsiniz.

#### <a name="jump-to-next-or-previous-transfer"></a>Sonraki veya önceki aktarıma geç

Geçerli etkinliği veya birden çok etkinlik seçildiğinde seçili etkinlikleri analiz ettiğinizde, aktardığı etkinlikleri hızlı bir şekilde bulmak isteyebilirsiniz. "Sonraki aktarıma geç", etkinliğin sonraki aktarım izlemesini bulmanıza olanak tanır. Aktarım izlemeyi bulduktan sonra, sonraki etkinliğe geçmek için "aktarımı Izle" seçeneğini kullanabilirsiniz.

- Sonraki aktarıma geç: **etkinlik** menüsünü kullanın veya "CTRL + F10" tuşuna basın.

- Önceki aktarıma geç: **etkinlik** menüsünü kullanın veya "CTRL + F9" tuşuna basın.

#### <a name="navigate-in-graph-view"></a>Grafik görünümünde gezinme

Etkinlik bölmesinde ve izleme bölmesinde gezinme, hata ayıklamaya benzer olsa da, **grafik** görünümü kullanılarak gezintide çok daha iyi bir deneyim sağlanır. Daha fazla bilgi için bkz. "grafik görünümü" bölümü.

### <a name="loading-large-trace-files"></a>Büyük Izleme dosyalarını yükleme

İzleme dosyaları çok büyük olabilir. Örneğin, "verbose" düzeyinde izlemeyi açarsanız, ağ hızına ve iletişim düzenine bağlı olarak birkaç dakika çalıştırmak için ortaya çıkan izleme dosyası kolayca yüzlerce megabayt veya daha büyük olabilir.

Hizmet Izleme görüntüleyicisinde çok büyük bir izleme dosyasını açtığınızda sistem performansı olumsuz etkilenebilir. Yükleme hızı ve yükleme sonrası yanıt süresi yavaş olabilir. Gerçek hız, donanım yapılandırmanıza bağlı olarak zaman zaman zamana göre farklılık gösterir. Çoğu bilgisayarda, 200D 'den büyük bir izleme dosyası yüklemek ciddi bir performans etkisine sahiptir. 1G 'den büyük izleme dosyaları için, araç kullanılabilir tüm belleği kullanabilir veya çok uzun bir süre yanıt vermeyi durdurabilir.

Büyük izleme dosyalarını çözümlemede yavaş yükleme ve yanıt süresini önlemek için, hizmet Izleme Görüntüleyicisi "kısmi yükleme" adlı bir özellik sağlar ve bu da yalnızca izlemenin küçük bir bölümünü aynı anda yükler. Örneğin, sunucusunda birkaç gün boyunca çalışan 1 GB üzerinde bir izleme dosyanız olabilir. Bazı hatalar oluştuğunda ve izlemeyi çözümlemek istediğinizde, tüm izleme dosyalarını açmak gerekli değildir. Bunun yerine, hata oluştuğunda belirli bir süre içinde izlemeleri yükleyebilirsiniz. Kapsam daha küçük olduğundan, hizmet Izleme Görüntüleyicisi aracı dosyayı daha hızlı yükleyebilir ve hataları daha küçük bir veri kümesi kullanarak belirleyebilirsiniz.

#### <a name="enabling-partial-loading"></a>Kısmi yüklemeyi etkinleştirme

Kısmi yüklemeyi el ile etkinleştirmeniz gerekmez. Yüklemeye çalıştığınız izleme dosyalarının toplam boyutu 40MB 'yi aşarsa, Service Trace Viewer, yüklemek istediğiniz bölümü seçmeniz için otomatik olarak bir kısmi yükleme iletişim kutusu görüntüler.

> [!NOTE]
> İzlemeler zaman aralığında eşit olarak dağıtılmayabilir, ancak kısmi yükleme araç çubuğunda belirttiğiniz zaman döneminin uzunluğu, gösterilen yükleme boyutuyla orantısız olmayabilir. Gerçek yükleme boyutu, kısmi yükleme iletişim kutusunda tahmini boyuttan daha küçük olabilir.

#### <a name="adjusting-partial-loading"></a>Kısmi yüklemeyi ayarlama

İzleme dosyasını kısmen yükledikten sonra, yüklenen veri kümesini değiştirmek isteyebilirsiniz. Bunu, görüntüleyicisinin en üstündeki kısmi yükleme araç çubuğunu ayarlayarak yapabilirsiniz.

1. Araç çubuğunu fareyle taşıyın veya başlangıç ve bitiş saatini girin.

2. **Ayarla** düğmesine tıklayın.

## <a name="understanding-trace-icons"></a>Izleme simgelerini anlama

Aşağıda, hizmet Izleme Görüntüleyicisi aracının, farklı öğeleri göstermek için **etkinlik** görünümü, **grafik** görünümü ve **izleme** bölmesinde kullandığı simgelerin bir listesi verilmiştir.

> [!NOTE]
> Kategorilere ayrılmamış bazı izlemeler (örneğin, "bir ileti kapatılmış") simge içermez.

### <a name="activity-tracing-traces"></a>Etkinlik Izleme Izlemeleri

|Simge|Description|
|----------|-----------------|
|![Uyarı izleme](./media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-badav-bcb27409dad58")|Uyarı izleme: uyarı düzeyine yayılan bir izleme|
|![Hata izleme](./media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Hata izleme: hata düzeyine yayılan bir izleme.|
|![Etkinlik başlangıç izlemesi:](./media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4A95-AFE8-0b6acd6e0317")|Etkinlik başlangıcı izlemesi: bir etkinliğin başlangıcını işaretleyen bir izleme. Etkinliğin adını içerir. Uygulama Tasarımcısı veya geliştirici olarak, işlem veya iş parçacığı başına etkinlik kimliği başına bir etkinlik başlangıç izlemesi tanımlamanız gerekir.<br /><br /> Etkinlik kimliği izleme bağıntısı için izleme kaynakları arasında yayıldığında, daha sonra aynı etkinlik kimliği (izleme kaynağı başına bir tane) için birden çok Başlat görebilirsiniz. İzleme kaynağı için ActivityTracing etkinleştirilirse başlangıç izlemesi yayınlanır.|
|![Etkinlik durdurma izlemesi](./media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Etkinlik durdurma izlemesi: etkinliğin sonuna işaret eden bir izleme. . Etkinliğin adını içerir. Uygulama Tasarımcısı veya geliştirici olarak, izleme kaynağı başına etkinlik kimliği başına bir etkinlik İzlemeyi Durdur ' u tanımlamanız gerekir. İzleme süresi ayrıntı düzeyi yeterince küçük olmadığı sürece, belirli bir izleme kaynağından bir izleme kaynağı, etkinlik o izleme kaynağı tarafından, bu izleme kaynağı tarafından yayıldıktan sonra görünmez. Bu durumda, bir Dur dahil olmak üzere aynı zamana sahip iki izleme, gösterildiğinde araya eklenebilir. Etkinlik kimliği izleme bağıntısı için izleme kaynakları arasında yayıldığında aynı etkinlik kimliği (izleme kaynağı başına bir tane) için birden çok durak görebilirsiniz. İzleme kaynağı için ActivityTracing etkinleştirilirse durdurma izlemesi yayınlanır.|
|![Etkinlik askıya alma izlemesi](./media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Etkinlik askıya alma izlemesi: etkinliğin duraklatıldığı saati işaretleyen bir izleme. Etkinlik sürdürülene kadar askıya alınmış bir etkinlikte izleme yapılmaz. Askıya alınmış bir etkinlik, izleme kaynağı kapsamındaki bu etkinlikte hiçbir işlemin gerçekleşmediğini belirtir. Bekletme/sürdürülme izlemeleri profil oluşturma için faydalıdır. İzleme kaynağı için ActivityTracing etkinleştirilirse, askıya alma izlemesi yayınlanır.|
|![Etkinlik özgeçmişi izlemesi](./media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4E0A-9988-cdc2f7030f17")|Etkinlik devam izleme: etkinlik askıya alındıktan sonra devam eden süreyi işaretleyen bir izleme. İzlemeler, bu etkinlikte yeniden dağıtılabilir. Bekletme/sürdürülme izlemeleri profil oluşturma için faydalıdır. İzleme kaynağı için ActivityTracing etkinleştirilirse, sürdürülme izlemesi yayınlanır.|
|![Aktarma](./media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Aktarım: mantıksal denetim akışı bir etkinlikten diğerine aktarıldığında yayınlanan bir izleme. Aktarımın kaynaklandığı etkinlik, aktarımın gittiği etkinliğe paralel olarak iş gerçekleştirmeye devam edebilir. İzleme kaynağı için ActivityTracing etkinleştirilirse, aktarım izlemesi yayınlanır.|
|![Aktarma yeri](./media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bdad741")|Aktarma yeri: başka bir etkinlikten geçerli etkinliğe bir aktarımı tanımlayan bir izleme.|
|![Aktarım yeri](./media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Aktar: geçerli etkinlikten başka bir etkinliğe mantıksal denetim akışının aktarımını tanımlayan bir izleme.|

### <a name="wcf-traces"></a>WCF Izlemeleri

|Simge|Description|
|----------|-----------------|
|![İleti günlüğü izleme](./media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|İleti günlüğü izleme: izleme kaynağı etkinleştirildiğinde, ileti günlüğü özelliği tarafından bir WCF iletisi günlüğe kaydedildiğinde yayınlanan bir izleme `System.ServiceModel.MessageLogging` . Bu izlemeye tıkladığınızda ileti görüntülenir. İleti için dört yapılandırılabilir günlüğe kaydetme noktası vardır: ServiceLevelSendRequest, TransportSend, TransportReceive ve ServiceLevelReceiveRequest. Bu, `messageSource` ileti günlüğü izlemesinde özniteliği tarafından da belirlenebilir.|
|![İleti alındı izlemesi](./media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|İleti alındı izlemesi: `System.ServiceModel` izleme kaynağı bilgi veya ayrıntılı düzeyde etkinleştirilmişse, BIR WCF iletisi alındığında yayınlanan bir izleme. Bu izleme, etkinlik **grafiği** görünümünde ileti bağıntı okuna bakmak için gereklidir.|
|![İleti gönderme izlemesi](./media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4C12-9405-677e995ac387")|İleti gönderildi izlemesi: `System.ServiceModel` izleme kaynağı bilgi veya ayrıntılı düzeyde etkinleştirilmişse, BIR WCF iletisi gönderildiğinde yayınlanan bir izleme. Bu izleme, etkinlik **grafiği** görünümünde ileti bağıntı okuna bakmak için gereklidir.|

### <a name="activities"></a>Etkinlikler

|Simge|Description|
|----------|-----------------|
|![Etkinlik](./media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Etkinlik: geçerli etkinliğin genel etkinlik olduğunu gösterir.|
|![Kök etkinlik](./media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Kök etkinlik: bir işlemin kök etkinliğini gösterir.|

### <a name="wcf-activities"></a>WCF etkinlikleri

|Simge|Description|
|----------|-----------------|
|![Ortam etkinliği](./media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-CF78-46e5-822d-56222fff61d1")|Ortam etkinliği: WCF konağını veya istemcisini oluşturan, açan veya kapatan bir etkinlik. Bu evreler sırasında gerçekleşen hatalar bu etkinlikte görünür.|
|![Dinleme etkinliği](./media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Dinleme etkinliği: bir dinleyiciyle ilgili izlemeleri günlüğe kaydeden bir etkinlik. Bu etkinliğin içinde, dinleyici bilgilerini ve bağlantı isteklerini görüntüleyebiliriz.|
|![Bayt alma etkinliği](./media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45A7-925b-616c96426c0e")|Bayt alma etkinliği: iki uç nokta arasındaki bir bağlantıda gelen baytları alma ile ilgili tüm izlemeleri gruplandıran bir etkinlik. Bu etkinlik, http.sys gibi etkinlik kimliklerini yayan taşıma etkinlikleriyle ilgili bir temel öneme sahiptir. Bu etkinlikte, iptal gibi bağlantı hataları görüntülenir.|
|![Iletiyi işle etkinliği](./media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|İşlem Iletisi etkinliği: bir WCF iletisi oluşturmayla ilgili izlemeleri gruplandıran bir etkinlik. Hatalı bir zarf veya hatalı biçimlendirilmiş bir ileti nedeniyle oluşan hatalar söz konusu etkinlikte görüntülenir. Bu etkinliğin içinde, çağrı kaynağından bir etkinlik kimliğinin yayıldığını görmek için ileti üstbilgilerini inceleyebilirsiniz. Bu değer true ise, Işlem eylemi etkinliğine (bir sonraki simge) aktarım yaptığımız zaman, bu etkinliğe, çağıran ve çağrılan izlemeler arasındaki bağıntı için yayılan etkinlik kimliği de atayabiliriz.|
|![İleti günlüğü izleme](./media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|İşlem eylemi etkinliği: iki uç nokta genelinde bir WCF isteğiyle ilgili tüm izlemeleri gruplandıran bir etkinlik. `propagateActivity` `true` Yapılandırma içindeki her iki uç nokta için olarak ayarlandıysa, her iki uç noktanın tüm izlemeleri doğrudan bağıntı için tek bir etkinlikte birleştirilir. Bu etkinlik, taşıma veya güvenlik işleme nedeniyle, Kullanıcı kodu sınırına ve geri (bir yanıt varsa) Genişlemeden hatalar içerecektir.|
|![Iletiyi işle etkinliği](./media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Kullanıcı kodunu Yürüt etkinliği: bir isteği işlemek için Kullanıcı kod izlemelerini gruplandıran bir etkinlik.|

## <a name="troubleshooting"></a>Sorun giderme

Kayıt defterine yazma izniniz yoksa, `svctraceviewer /register` Aracı kaydettirmek için "" komutunu kullandığınızda "Microsoft hizmet Izleme Görüntüleyicisi sisteme kaydedilmedi" hata iletisini alırsınız. Bu durumda, kayıt defterine yazma erişimi olan bir hesap kullanarak oturum açmanız gerekir.

Ayrıca, hizmet Izleme Görüntüleyicisi aracı derleme klasöründeki SvcTraceViewer.exe. Settings dosyasına bazı ayarları (örneğin, özel filtreler ve filtre seçenekleri) yazar. Dosya için okuma izniniz yoksa, aracı yine de başlatabilirsiniz, ancak ayarları yükleyemezsiniz.

. Etl dosyasını açarken "bir veya daha fazla izleme işlenirken bilinmeyen bir hata oluştu" hata iletisini alırsanız,. etl dosyasının biçiminin geçersiz olduğu anlamına gelir.

Arapça bir işletim sistemi kullanılarak oluşturulmuş bir izleme günlüğü açarsanız, zaman filtresinin çalışmadığına fark edebilirsiniz. Örneğin, 2005 yılı, Arapça takvim 'teki yıl 1427 ' e karşılık gelir. Ancak, hizmet Izleme Görüntüleyicisi aracı filtresi tarafından desteklenen zaman aralığı 1752 öncesi bir tarihi desteklemez. Bu, filtrede doğru bir tarih seçemeyebilirsiniz anlamına gelmez. Bu sorunu çözmek için belirli bir zaman aralığı dahil etmek üzere bir XPath ifadesi kullanarak özel bir filtre (**görünüm/özel filtreler**) oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma ](./diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [İzlemeyi Yapılandırma](./diagnostics/tracing/configuring-tracing.md)
- [Uçtan Uca İzleme](./diagnostics/tracing/end-to-end-tracing.md)
