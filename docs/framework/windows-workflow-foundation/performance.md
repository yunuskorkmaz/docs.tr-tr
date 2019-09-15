---
title: Windows Workflow Foundation 4 Performansı
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: c656d1e23c7314cfd7b772faef842296d03e4af1
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989578"
---
# <a name="windows-workflow-foundation-4-performance"></a>Windows Workflow Foundation 4 Performansı

 Microsoft [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] , ağır yatırımlarla Windows Workflow Foundation (WF) büyük bir düzeltmesini içerir.  Bu yeni düzeltme, 3,0 ve [!INCLUDE[wf1](../../../includes/wf1-md.md)] [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].NET Framework bir parçası olarak sevk edilen önceki sürümlerinden önemli tasarım değişiklikleri sunmaktadır. Performansı ve kullanılabilirliği önemli ölçüde artırmak için programlama modeli, çalışma zamanı ve araç 'nın çekirdeğinizden yeniden tasarlanmıştır. Bu konu, bu düzeltmelerin önemli performans özelliklerini gösterir ve bunları önceki sürüme göre karşılaştırır.

 Bireysel iş akışı bileşeni performansı, WF3 ve WF4 arasındaki büyüklük üzerinden artmıştır.  Bu, el kodlu Windows Communication Foundation (WCF) Hizmetleri ve WCF iş akışı hizmetleri arasındaki boşluğu çok küçük olarak bırakır.  WF4 ' de iş akışı gecikmesi önemli ölçüde azaltılmıştır.  Kalıcılık performansı 2,5-3,0 faktörüyle artmıştır.  İş akışı izlemenin sistem durumu izlemenin önemli ölçüde daha az yükü vardır.  Bunlar, uygulamalarınızda WF4 'e geçiş yapmak veya benimsemek için etkileyici nedenlerdir.

## <a name="terminology"></a>Terminoloji
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] İçinde[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] tanıtılan sürümü, bu konunun geri kalanı için WF4 olarak adlandırılır.  [!INCLUDE[wf1](../../../includes/wf1-md.md)], .NET 3,0 ' de kullanıma sunulmuştur ve SP1 aracılığıyla [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] birkaç küçük düzeltmelere sahipti. Bu konunun geri kalanı için Workflow Foundation sürümüWF3olarakadlandırılacaktır.[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] WF3, WF4 ile [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] yan yana gönderilir. WF3 yapıtları WF4 'e geçirme hakkında daha fazla bilgi için bkz.: [Windows Workflow Foundation 4 geçiş kılavuzu](https://go.microsoft.com/fwlink/?LinkID=153313)

 Windows Communication Foundation (WCF), Microsoft 'un hizmet odaklı uygulamalar oluşturmaya yönelik Birleşik programlama modelidir. İlk olarak, WF3 ile birlikte .NET 3,0 'nin bir parçası olarak sunulmuştur ve artık .NET Framework temel bileşenlerinden biridir.

 Windows Server AppFabric, IIS üzerinde çalışan Web uygulamaları ve bileşik uygulamalar oluşturmayı, ölçeklendirmenizi ve yönetmeyi kolaylaştıran bir tümleşik teknolojiler kümesidir. Hizmetleri ve iş akışlarını izlemek ve yönetmek için araçlar sağlar. Daha fazla bilgi için bkz. [Windows Server AppFabric 1,0](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)).

## <a name="goals"></a>Hedefleri
 Bu konunun amacı, farklı senaryolar için ölçülen verilerle WF4 'in performans özelliklerini gösterir. Ayrıca, WF4 ve WF3 arasında ayrıntılı karşılaştırmalar sağlar ve bu yeni düzeltmede yapılan harika iyileştirmeleri gösterir. Bu makalede sunulan senaryolar ve veriler, WF4 ve WF3 ' nin farklı yönlerinin temel maliyetini hisize ediyor. Bu veriler, WF4 'in performans özelliklerini anlamak için yararlıdır ve WF3 'e geçiş planlaması veya uygulama geliştirmede WF4 kullanma konusunda yardımcı olabilir. Bununla birlikte, bu makalede sunulan verilerden ekibinizle bir şekilde ele alınması gerekir. Birleşik iş akışı uygulamasının performansı, iş akışının nasıl uygulandüğüne ve farklı bileşenlerin nasıl tümleştirilebilme konusunda oldukça bağımlıdır. Uygulamanın performans özelliklerini öğrenmek için her bir uygulamayı ölçmelidir.

## <a name="overview-of-wf4-performance-enhancements"></a>WF4 performans geliştirmeleriyle ilgili genel bakış
 WF4 dikkatle tasarlanmıştı ve aşağıdaki bölümlerde açıklanan yüksek performans ve ölçeklenebilirlik ile uygulandı.

### <a name="wf-runtime"></a>WF çalışma zamanı
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] Çalışma zamanının çekirdeği, bir iş akışındaki etkinliklerin yürütülmesini yönlendiren zaman uyumsuz bir Zamanlayıcı olur. Etkinlikler için performansı tahmin edilebilir bir yürütme ortamı sağlar. Ortamda yürütme, devamlılık, tamamlama, iptal etme, özel durumlar ve öngörülebilir bir iş parçacığı modeli için iyi tanımlanmış bir sözleşme vardır.

 WF3 ile karşılaştırıldığında, WF4 çalışma zamanının daha verimli bir Zamanlayıcı vardır. Toplu iş öğelerini yürütmek için çok verimli olan WCF için kullanılan aynı g/ç iş parçacığı havuzundan yararlanır. İç iş öğesi Zamanlayıcı kuyruğu, yaygın kullanım desenlerinin çoğunda en iyi duruma getirilmiştir. WF4 çalışma zamanı, yürütme durumlarını minimum eşitleme ve olay işleme mantığı ile çok hafif bir şekilde yönetir, WF3, durum geçişleri için karmaşık eşitleme gerçekleştirmek üzere ağır olay kaydına ve çağrıya bağlıdır.

### <a name="data-storage-and-flow"></a>Veri depolama ve akış
 WF3 ' de, bir etkinlikle ilişkili veriler, tür <xref:System.Windows.DependencyProperty>tarafından uygulanan bağımlılık özellikleri aracılığıyla modellenir. Bağımlılık özelliği deseninin Windows Presentation Foundation (WPF) tanıtılmıştı. Genel olarak, bu model kolay veri bağlamayı ve diğer kullanıcı arabirimi özelliklerini desteklemek için çok esnektir. Ancak, model, özelliklerin iş akışı tanımında statik alanlar olarak tanımlanmasını gerektirir. Çalışma zamanı [!INCLUDE[wf1](../../../includes/wf1-md.md)] , özellik değerlerini ayarlarken veya aldığında, yoğun olarak ağırlıklı arama mantığını içerir.

 WF4, verilerin bir iş akışında işlenme biçimini büyük ölçüde geliştirmek için net veri kapsamı mantığı kullanır. İki farklı kavram kullanılarak etkinlik sınırları genelinde akan verilerden bir etkinlikte depolanan verileri ayırır: değişkenler ve bağımsız değişkenler. Değişkenler ve "ın/out/Inout" bağımsız değişkenleri için açık bir hiyerarşik kapsam kullanarak, etkinliklere yönelik veri kullanımı karmaşıklığı önemli ölçüde azalır ve verilerin yaşam süresi de otomatik olarak kapsamlandırılır. Etkinliklerin bağımsız değişkenleri tarafından tanımlanan iyi tanımlanmış bir imzası vardır. Yalnızca bir etkinliği inceleyerek, hangi verilerin almak istediğinizi ve yürütme sonucu olarak hangi verilerin üretileceği belirlenir.

 Bir iş akışı oluşturulduğunda WF3 etkinliklerde başlatılmıştı. WF 4 etkinliklerinde yalnızca ilgili etkinlikler çalıştırıldığında başlatılır. Bu, yeni bir iş akışı örneği oluşturulduğunda Initialize/Uninitialize işlemleri yapılmadan daha basit bir etkinlik yaşam döngüsünü sağlar ve bu nedenle daha fazla verimlilik elde edilir

### <a name="control-flow"></a>Denetim Akışı
 Herhangi bir programlama dilinde olduğu gibi, [!INCLUDE[wf1](../../../includes/wf1-md.md)] sıralama, döngü, dallandırma ve diğer desenlere yönelik bir dizi denetim akışı etkinliği sunarak iş akışı tanımlarının denetim akışları için destek sağlar. WF3 ' de, aynı etkinliğin yeniden yürütülmesi gerektiğinde, yeni <xref:System.Workflow.ComponentModel.ActivityExecutionContext> bir oluşturulur ve etkinlik, temel alınarak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>ağır bir serileştirme ve seri durumdan çıkarma mantığı aracılığıyla klonlanır. Genellikle yinelemeli denetim akışlarının performansı, bir dizi etkinliği yürütmeden çok daha yavaştır.

 WF4 bu oldukça farklı bir şekilde işler. Etkinlik şablonunu alır, yeni bir ActivityInstance nesnesi oluşturur ve Zamanlayıcı kuyruğuna ekler. Bu bütün işlem yalnızca açık nesne oluşturma içerir ve çok hafif.

### <a name="asynchronous-programming"></a>Zaman Uyumsuz Programlama
 Uygulamalar genellikle g/ç veya dağıtılmış bilgi işlem işlemleri gibi uzun süre çalışan engelleme işlemleri için zaman uyumsuz programlama ile daha iyi performans ve ölçeklenebilirlik sahibi olur. WF4, <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity%601>temel etkinlik türleri aracılığıyla zaman uyumsuz destek sağlar. Çalışma zamanı zaman uyumsuz etkinlikleri yerel olarak anlamıştır ve bu nedenle, zaman uyumsuz çalışma devam ederken örneği kalıcı olmayan bir bölgeye otomatik olarak yerleştirebilir. Özel Etkinlikler, iş akışı Zamanlayıcı iş parçacığını tutmadan zaman uyumsuz çalışma gerçekleştirmek ve paralel çalışabilecek etkinlikleri engellemek için bu türlerden türetilebilir.

### <a name="messaging"></a>İleti
 Başlangıçta WF3, dış olaylar veya Web Hizmetleri etkinleştirmeleri aracılığıyla çok sınırlı mesajlaşma desteğine sahipti. .NET 3,5 ' de, iş akışları WCF istemcileri olarak uygulanabilir veya <xref:System.Workflow.Activities.SendActivity> ve <xref:System.Workflow.Activities.ReceiveActivity>ile WCF hizmeti olarak kullanıma sunulabilir. WF4 ' de, iş akışı tabanlı mesajlaşma programlama kavramı, WCF mesajlaşma mantığının WF ile sıkı bir şekilde tümleştirilmesine daha da güçleşti.

 .NET 4 ' te WCF 'de sunulan Birleşik ileti işleme işlem hattı, WF4 Services 'ın WF3 'den önemli ölçüde daha iyi performans ve ölçeklenebilirlik sağlanmasına yardımcı olur. WF4, karmaşık Ileti değişim düzenlerini (MEPs) modelleyebilir daha zengin mesajlaşma programlama desteği de sağlar. Geliştiriciler, serileştirme maliyetlerini ödemeksizin daha iyi performans elde etmek için kolayca programlama veya türsüz hizmet sözleşmeleri elde etmek üzere türü belirlenmiş hizmet sözleşmelerini kullanabilir. WF4 içindeki <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıfı aracılığıyla istemci tarafı kanal önbelleğe alma desteği, geliştiricilerin en düşük çabayla hızlı uygulamalar oluşturmasına yardımcı olur. Daha fazla bilgi için bkz. [gönderme etkinlikleri Için önbellek paylaşımı düzeylerini değiştirme](../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).

### <a name="declarative-programming"></a>Bildirim temelli programlama
 WF4, iş süreçlerini ve hizmetlerini modellemek için temiz ve basit bir bildirim temelli programlama çerçevesi sağlar. Programlama modeli, kod olmadan, iş akışı yazmayı büyük ölçüde basitleştirecek şekilde etkinliklerin tam bildirime dayalı olarak birleşimini destekler. ' [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]De, XAML tabanlı bildirim temelli programlama çerçevesi, hem WPF hem de WF 'yi desteklemek için tek derleme System. xaml. dll ' ye birleştirilmiştir.

 WF4 ' de, XAML gerçekten bildirime dayalı bir deneyim sağlar ve iş akışının tamamının tanımının, .NET kullanılarak oluşturulan etkinliklere ve türlere başvuran XML biçimlendirmesinde tanımlanmasını sağlar. Bu, WF3 ' de özel arka plan kod mantığı olmadan XOML biçimiyle yapılması zordur. .NET 4 ' teki yeni XAML yığını, iş akışı yapıtlarını serileştirmek/seri durumdan çıkarmak ve bildirim temelli programlamayı daha çekici ve düz hale getirir.

### <a name="workflow-designer"></a>İş Akışı Tasarımcısı
 WF4 için tam bildirime dayalı programlama desteği, büyük iş akışları için tasarım süresi performansına yönelik daha yüksek gereksinimleri açıkça uygular. WF4 ' deki Iş akışı Tasarımcısı, büyük iş akışları için WF3 için çok daha fazla ölçeklenebilirlik içerir. UI Sanallaştırması desteğiyle, tasarımcı büyük bir 1000 etkinlik iş akışını birkaç saniye içinde kolayca yükleyebilir, ancak WF3 Designer ile birkaç yüz etkinliğin iş akışını yüklemek neredeyse olanaksızdır.

## <a name="component-level-performance-comparisons"></a>Bileşen düzeyinde performans karşılaştırmaları
 Bu bölüm, WF3 ve WF4 iş akışlarında bağımsız etkinlikler arasındaki doğrudan karşılaştırmalar hakkında veri içerir.  Kalıcılık gibi önemli alanların performans üzerinde, bireysel etkinlik bileşenlerinden daha fazla etkisi vardır.  Bileşenler artık el ile kodlanmış düzenleme mantığına kıyasla yeterince hızlı olduğundan, WF4 içindeki tek tek bileşenlerin performans iyileştirmeleri önemlidir.  Bir sonraki bölümde ele alınan bir örnek: "Hizmet bileşim senaryosu."

### <a name="environment-setup"></a>Ortam kurulumu
 ![İş akışı performans ölçümü için ortam kurulumu](./media/performance/performance-test-environment.gif)

 Yukarıdaki şekil, bileşen düzeyinde performans ölçümü için kullanılan makine yapılandırmasını gösterir. Tek bir sunucu ve 1 GB/sn 'lik Ethernet ağ arabirimine bağlanmış beş istemci. Kolay ölçümler için sunucu, Windows Server 2008 x86 çalıştıran bir çift proc/dört çekirdekli sunucunun tek bir çekirdeğini kullanacak şekilde yapılandırılmıştır. Sistem CPU kullanımı yaklaşık% 100 ' de korunur.

### <a name="test-details"></a>Test ayrıntıları
 WF3 <xref:System.Workflow.Activities.CodeActivity> , büyük olasılıkla bir WF3 iş akışında kullanılabilen en basit etkinliktir.  Etkinlik, iş akışı Programlayıcısının özel kod koyabileceğiniz arka plan kod içinde bir yöntemi çağırır.  WF4 ' de, aynı işlevselliği sağlayan, WF3 <xref:System.Workflow.Activities.CodeActivity> 'ye doğrudan analog yoktur.  WF4 içinde WF3 <xref:System.Workflow.Activities.CodeActivity>ile ilişkili <xref:System.Activities.CodeActivity> olmayan bir temel sınıf olduğunu unutmayın.  İş akışı yazarlarının özel etkinlikler oluşturması ve yalnızca XAML iş akışları oluşturması önerilir.  Aşağıdaki sınamalarda, çağrılan `Comment` bir etkinlik WF4 iş akışlarında boş <xref:System.Workflow.Activities.CodeActivity> bir yerde kullanılır.  `Comment` Etkinlikteki kod şu şekildedir:

```csharp
[ContentProperty("Body")]
    public sealed class Comment : CodeActivity
    {
        public Comment()
            : base()
        {
        }

        [DefaultValue(null)]
        public Activity Body
        {
            get;
            set;
        }

        protected override void Execute(CodeActivityContext context)
        {
        }
    }
```

### <a name="empty-workflow"></a>Boş Iş akışı
 Bu test, alt etkinlikleri olmayan bir sıra iş akışı kullanır.

### <a name="single-activity"></a>Tek etkinlik
 İş akışı, bir alt etkinlik içeren bir sıra iş akışıdır.  Etkinlik, WF3 durumunda <xref:System.Workflow.Activities.CodeActivity> kod bulunmayan `Comment` ve WF4 durumunda bir etkinliğin bulunduğu bir etkinliktir.

### <a name="while-with-1000-iterations"></a>1000 yinelemeyle birlikte
 Sıralı iş akışı, döngüde <xref:System.Activities.Statements.While> hiçbir iş gerçekleştirmediğinden bir alt etkinliği olan bir etkinlik içeriyor.

### <a name="replicator-compared-to-parallelforeach"></a>Çoğaltıcı ParallelForEach ile karşılaştırılır
 <xref:System.Workflow.Activities.ReplicatorActivity>WF3 ' de sıralı ve paralel yürütme modları vardır.  Sıralı modda, etkinliğin performansı ile <xref:System.Workflow.Activities.WhileActivity>benzerdir.  , <xref:System.Workflow.Activities.ReplicatorActivity> Paralel yürütme için en yararlı seçenektir.  Bunun için WF4 analog bu <xref:System.Activities.Statements.ParallelForEach%601> etkinliktir.

 Aşağıdaki diyagramda, bu test için kullanılan iş akışları gösterilmektedir. WF3 iş akışı solda ve WF4 iş akışı sağda.

 ![WF3 ReplicatorActivity ve WF4 ParallelForEach](./media/performance/replicator-parallel-wf3-wf4.gif)

### <a name="sequential-workflow-with-five-activities"></a>Beş etkinlikli sıralı Iş akışı
 Bu test, birkaç etkinliğin sırayla yürütülme etkisini göstermek için tasarlanmıştır.  Dizide beş etkinlik vardır.

### <a name="transaction-scope"></a>İşlem kapsamı
 İşlem kapsamı testi, her yineleme için yeni bir iş akışı örneğinin oluşturulmatığından farklı testlerden farklılık gösterir.  Bunun yerine, iş akışı, hiçbir iş gerektirmeyen tek bir etkinlik <xref:System.Activities.Statements.TransactionScope> içeren bir while döngüsü ile yapılandırılır.  While döngüsü aracılığıyla 50 yinelemeden oluşan her çalıştırma tek bir işlem olarak sayılır.

### <a name="compensation"></a>Dengeleme
 WF3 iş akışında adlı `WorkScope`tek bir dengeleme etkinliği vardır.  Etkinlik yalnızca <xref:System.Workflow.ComponentModel.ICompensatableActivity> arabirimini uygular:

```csharp
class WorkScope :
        CompositeActivity, ICompensatableActivity
    {
        public WorkScope() : base() { }

        public WorkScope(string name)
        {
            this.Name = name;
        }

        public ActivityExecutionStatus Compensate(
            ActivityExecutionContext executionContext)
        {
            return ActivityExecutionStatus.Closed;
        }
    }
```

 Hata işleyicisi `WorkScope` etkinliği hedefliyor. WF4 iş akışı eşit uyarlaması.  <xref:System.Activities.Statements.CompensableActivity> , Bir gövdeye ve bir dengeleme işleyicisine sahiptir.  Sıranın yanında açık bir telafi vardır.  Gövde etkinliği ve dengeleme işleyicisi etkinliği hem boş uygulamalardır:

```csharp
public sealed class CompensableActivityEmptyCompensation : CodeActivity
    {
        public CompensableActivityEmptyCompensation()
            : base() { }

        public Activity Body { get; set; }

        protected override void Execute(CodeActivityContext context) { }
    }
    public sealed class CompensableActivityEmptyBody : CodeActivity
    {
        public CompensableActivityEmptyBody()
            : base() { }

        public Activity Body { get; set; }

        protected override void Execute(CodeActivityContext context) { }
    }
```

Aşağıdaki diyagramda temel Dengeleme iş akışı gösterilmektedir. WF3 iş akışı solda ve WF4 iş akışı sağda.

![WF3 ve WF4 temel Dengeleme iş akışları](./media/performance/basic-compensation-workflows-wf3-wf4.gif)

### <a name="performance-test-results"></a>Performans Test Sonuçları

 ![Performans testi sonuçları verilerini gösteren tablo](./media/performance/performance-test-data.gif)

 ![WF3 ve WF4 performans testi verilerini karşılaştıran sütun grafiği](./media/performance/performance-test-chart.gif)

 Tüm testler, işlem kapsamı testinin özel durumu ile saniye başına iş akışlarında ölçülür.  Yukarıda görünebildiğinden, [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanı performansı Pano genelinde geliştirilmiştir, özellikle de while döngüsü gibi aynı etkinliğin birden çok yürütmesi gerektiren alanlardır.

## <a name="service-composition-scenario"></a>Hizmet bileşim senaryosu
 Önceki bölümde gösterildiği gibi, "bileşen düzeyinde performans karşılaştırmaları", WF3 ve WF4 arasındaki ek yükün önemli bir azalmasıyla karşılaşıldı.  WCF iş akışı hizmetleri artık el ile kodlanmış WCF hizmetlerinin performansını neredeyse eşleştirebilir ancak [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanının tüm avantajlarına sahip olmaya devam edebilir.  Bu test senaryosu, bir WCF hizmetini WF4 içindeki bir WCF iş akışı hizmetiyle karşılaştırır.

### <a name="online-store-service"></a>Çevrimiçi mağaza hizmeti
 Windows Workflow Foundation güçlerinden biri, birkaç hizmeti kullanarak işlem oluşturma olanağıdır.  Bu örnek için, sipariş satın almak üzere iki hizmet çağrısı düzenleyen bir çevrimiçi mağaza hizmeti vardır.  İlk adım, siparişi doğrulama hizmeti kullanarak sıralamayı doğrulamaktır.  İkinci adım siparişi bir ambar hizmeti kullanarak dolduramadık.

 İki arka uç hizmeti, hizmet ve ambar hizmetini doğrulayan sipariş, her iki test için de aynı kalır.  Değişen bölüm, düzenleme işlemini gerçekleştiren çevrimiçi mağaza hizmetidir.  Tek bir durumda, hizmet bir WCF hizmeti olarak el ile kodlanır.  Diğer bir durumda, hizmet WF4 içinde bir WCF iş akışı hizmeti olarak yazılır. [!INCLUDE[wf1](../../../includes/wf1-md.md)]Bu test için izleme ve kalıcılık gibi belirli özellikler kapalıdır.

### <a name="environment"></a>Ortam
![Performans ölçümü için ortam kurulumu](./media/performance/performance-test-environment.gif)

 İstemci istekleri, birden fazla bilgisayardan HTTP aracılığıyla çevrimiçi mağaza hizmetine yapılır.  Tek bir bilgisayar, üç hizmeti de barındırır.  Çevrimiçi mağaza hizmeti ve arka uç hizmetleri arasındaki aktarım katmanı TCP veya HTTP 'dir.  İşlem/saniye ölçümü, çevrimiçi mağaza hizmetine yapılan tamamlanan `PurchaseOrder` çağrıların sayısını temel alır.  Kanal havuzu oluşturma, WF4 içinde sunulan yeni bir özelliktir.  Bu test kanalı havuzsının WCF bölümünde, çevrimiçi depolama hizmetinde basit bir havuzlama tekniğinden oluşan, el kodlu bir uygulama kullanıldığından, bu test kanalı havuzunun WCF bölümünde değil.

### <a name="performance"></a>Performans
![Çevrimiçi mağaza Hizmeti performansını gösteren sütun grafiği](./media/performance/online-store-performance-graph.gif)

 Kanal havuzu oluşturma olmadan arka uç TCP hizmetleri 'ne bağlanma [!INCLUDE[wf1](../../../includes/wf1-md.md)] , hizmet verimlilik üzerinde% 17,2 etkiye sahiptir.  Kanal havuzu oluşturma ile ceza% 23,8 ' dır.  HTTP için etki çok daha küçüktür: Havuz oluşturma ve% 8,1% 4,3.  Kanal havuzunun HTTP kullanırken çok az avantaj sağladığını aklınızda bulundurmamak da önemlidir.

 WF4 çalışma zamanından, bu testte el kodlu bir WCF hizmetiyle karşılaştırıldığında ek yük olsa da, en kötü durum senaryosu kabul edilebilir.  Bu testteki iki arka uç hizmeti çok az çalışır.  Gerçek uçtan uca bir senaryoda, bu hizmetler veritabanı çağrıları gibi daha pahalı işlemler gerçekleştirmeye ve aktarım katmanının performans etkisini daha az önemli hale getirir.  Bu, WF4 ' de kullanılabilen özelliklerin avantajları, Workflow Foundation 'ın Orchestration hizmetleri oluşturmak için uygun bir seçim olmasını sağlar.

## <a name="key-performance-considerations"></a>Ana performans konuları
 Bu bölümdeki özellik alanlarının birlikte çalışma hariç olması, WF3 ile WF4 arasında önemli ölçüde değişmiştir.  Bu, iş akışı uygulamalarının tasarımını ve performansını etkiler.

#### <a name="workflow-activation-latency"></a>İş akışı etkinleştirme gecikmesi
 Bir WCF iş akışı hizmeti uygulamasında, yeni bir iş akışı başlatma veya var olan bir iş akışını yükleme gecikmesi engelliyor olduğu için önemlidir.  Bu test çalışması, bir WF3 XOML konağını tipik bir senaryoda WF4 XAMLX ana bilgisayarına göre ölçer.

##### <a name="environment-setup"></a>Ortam kurulumu
 ![Gecikme süresi ve işleme testleri için ortam kurulumu](./media/performance/latency-throughput-environment-setup.gif)

##### <a name="test-setup"></a>Test kurulumu
 Senaryoda, bir istemci bilgisayar, bağlam tabanlı bağıntı kullanarak bir WCF iş akışı hizmetiyle iletişim kurar.  Bağlam bağıntısı özel bir bağlam bağlaması gerektirir ve iletileri doğru iş akışı örneğiyle ilişkilendirmek için bağlam üst bilgisini veya tanımlama bilgisini kullanır.  İleti gövdesinin ayrıştırılabilmesi için, bağıntı kimliğinin ileti üstbilgisinde bulunması açısından bir performans avantajı vardır.

 Hizmet, istekle birlikte yeni bir iş akışı oluşturur ve gecikme süresinin ölçümünün iş akışını çalıştırmak için harcanan süreyi içermemesi için anında yanıt gönderir.  WF3 iş akışı, bir arka plan kodu ile XOML ve WF4 iş akışı tamamen XAML.  WF4 iş akışı şöyle görünür:

 ![WF4 bağıntı kapsamı iş akışı](./media/performance/wf4-correlationscope-workflow.gif)

 <xref:System.ServiceModel.Activities.Receive> Etkinlik, iş akışı örneğini oluşturur.  Alınan iletiye geçirilen bir değer, yanıt iletisinde yankılanır.  Yanıtınızı izleyen bir sıra, iş akışının geri kalanını içerir.  Yukarıdaki örnekte yalnızca bir açıklama etkinliği gösterilir.  Açıklama etkinliklerinin sayısı, iş akışı karmaşıklığının benzetimini yapmak için değiştirilir.  Açıklama etkinliği, hiçbir iş gerçekleştirmeyen bir WF3 <xref:System.Workflow.Activities.CodeActivity> eşdeğerdir. Açıklama etkinliği hakkında daha fazla bilgi için, bu makalenin önceki kısımlarında bulunan "bileşen düzeyi performans karşılaştırması" bölümüne bakın.

##### <a name="test-results"></a>Test Sonuçları

 WCF iş akışı hizmetleri için soğuk ve sıcak gecikme süresi:

 ![WF3 ve WF4 kullanarak WCF iş akışı hizmetleri için soğuk ve ısınma gecikmesini gösteren sütun grafiği](./media/performance/latency-results-graph.gif)

 Önceki grafikte, soğuk, belirtilen iş akışı için mevcut <xref:System.ServiceModel.WorkflowServiceHost> olmayan bir durum anlamına gelir.  Diğer bir deyişle, soğuk gecikme süresi, iş akışının ilk kez kullanıldığı, XOML veya XAML 'in derlenmesi gerektiğinde olur.  Isınma gecikmesi, iş akışı türü zaten derlenmişse yeni bir iş akışı örneği oluşturmak için zaman.  İş akışının karmaşıklığı WF4 büyük/küçük bir süre içinde çok az farklılık yapar ancak WF3 durumunda doğrusal bir ilerleme içerir.

#### <a name="correlation-throughput"></a>Bağıntı Işleme
 WF4, içerik tabanlı yeni bir bağıntı özelliği sunar.  WF3 yalnızca bağlam tabanlı bağıntı sağladı.  Bağlam tabanlı bağıntı yalnızca belirli WCF kanal bağlamaları üzerinden yapılabilir.  Bu bağlamalar kullanılırken iş akışı kimliği ileti üstbilgisine eklenir.  WF3 çalışma zamanı bir iş akışını yalnızca kimliğine göre tanımlayabilir.  İçerik tabanlı bağıntı sayesinde, iş akışı yazarı, bir hesap numarası veya müşteri kimliği gibi ilgili veri parçalarından bir bağıntı anahtarı oluşturabilir.

 Bağlam tabanlı bağıntı, bağıntı anahtarının ileti üstbilgisinde bulunduğu bir performans avantajına sahiptir.  Anahtar, devre dışı serileştirme/ileti kopyalama olmadan iletiden okunabilir.  İçerik tabanlı bağıntı içinde, bağıntı anahtarı ileti gövdesinde depolanır.  Anahtarı bulmak için bir XPath ifadesi kullanılır.  Bu ek işlemenin maliyeti iletinin boyutuna, gövdedeki anahtarın derinliğine ve anahtar sayısına bağlıdır.  Bu test, bağlam ve içerik tabanlı bağıntıyı karşılaştırır ve ayrıca birden çok anahtar kullanırken performans düşüşünü gösterir.

#### <a name="environment-setup"></a>Ortam kurulumu
![İş akışı performans testi için ortam kurulumu](./media/performance/performance-test-environment.gif)

#### <a name="test-setup"></a>Test kurulumu
![Bağıntı üretilen Iş akışı testi](./media/performance/correlation-throughput-workflow.gif "Bağıntı üretilen iş akışı test kurulumu")

 Önceki iş akışı, [Kalıcılık](#persistence) bölümünde kullanılan bir bölümdür. Kalıcı olmayan bağıntı testleri için, çalışma zamanında yüklü bir kalıcılık sağlayıcısı yoktur. Bağıntı iki yerde gerçekleşir: CreateOrder ve CompleteOrder.

#### <a name="test-results"></a>Test Sonuçları
![Bağıntı işleme](./media/performance/correlation-throughput-graph.gif "Bağıntı üretilen iş grafiği")

 Bu grafik, içerik tabanlı korelasyonda kullanılan anahtarların sayısı arttıkça performansın azalışını gösterir.  TCP ve HTTP arasındaki eğrilerde benzerlik, bu protokollerle ilişkili ek yükü gösterir.

#### <a name="correlation-with-persistence"></a>Kalıcılık ile bağıntı
 Kalıcı bir iş akışıyla, içerik tabanlı bağıntıdan alınan CPU baskısı, iş akışı çalışma zamanından SQL veritabanına kayar.  SQL kalıcılık sağlayıcısındaki saklı yordamlar, uygun iş akışını bulmak için anahtarlarla eşleşen bir iş sağlar.

 ![Bağıntı ve kalıcılık sonuçlarını gösteren çizgi grafik](./media/performance/correlation-persistence-graph.gif)

 Bağlam tabanlı bağıntı, içerik tabanlı korelasyondan daha hızlıdır.  Bununla birlikte, kalıcılığı daha az önemlidir çünkü Kalıcılık, performans üzerinde bağıntı üzerinde daha fazla etkiye sahiptir.

### <a name="complex-workflow-throughput"></a>Karmaşık Iş akışı performansı
 Bir iş akışının karmaşıklığı yalnızca etkinlik sayısıyla ölçülemez.  Bileşik etkinlikler birçok alt içerebilir ve bu alt öğeler bileşik etkinlik de olabilir.  İç içe geçme seviyelerinin sayısı arttıkça, şu anda yürütme durumunda olabilecek etkinlik sayısı ve durum içinde olabilecek değişkenlerin sayısı vardır.  Bu test, karmaşık iş akışlarını yürütürken WF3 ile WF4 arasındaki aktarım hızını karşılaştırır.

### <a name="test-setup"></a>Test kurulumu
 Bu sınamalar, Windows Server 2008 x64 çalıştıran 4 GB RAM 'e sahip Intel Xeon X5355 @ 2,66 GHz 4 yönlü bir bilgisayar üzerinde yürütüldü.  Sınama kodu,% 100 CPU kullanımına ulaşmak için çekirdek başına bir iş parçacığı ile tek bir işlemde çalışır.

 Bu test için oluşturulan iş akışlarının iki ana değişkeni vardır: her bir dizideki derinlik ve etkinlik sayısı.  Her derinlik düzeyi paralel bir etkinlik, while döngüsü, kararlar, atamalar ve diziler içerir.  Aşağıda bulunan WF4 Tasarımcısı ' nda, üst düzey akış grafiği de görüntülenir.  Her akış çizelgesi etkinliği ana akış çizelgesine benzer.  Bu iş akışını yaparken bir Fractal 'in düşünmek faydalı olabilir. Bu, derinliğin testin parametreleriyle sınırlı olduğu yerdir.

 Belirli bir testte bulunan etkinliklerin sayısı, her sırada etkinliğin derinliğine ve sayısına göre belirlenir.  Aşağıdaki denklem WF4 testinde etkinlik sayısını hesaplar:

 ![Etkinlik sayısını hesaplamak için Denklem](./media/performance/number-activities-equation.gif)

 Ek bir sıra nedeniyle WF3 testinin etkinlik sayısı biraz farklı bir denklemle hesaplanabilir:

 ![WF3 etkinliği sayısını hesaplama denklemi](./media/performance/wf3-number-activities-equation.gif)

 Burada d derinlik ve a, dizi başına etkinlik sayısıdır.  Bu denklemlerin arkasındaki mantık, ilk sabitin, bir ile çarpılması, sıranın sayısı ve ikinci sabit ise geçerli düzeydeki etkinlik sayısının statik sayısıdır.  Her akış çizelgesinde üç akış çizelgesi alt etkinliği vardır.  Alt derinlik düzeyinde, bu akış çizelgeleri boş, ancak ana akış çizelgesinin kopyaları oldukları diğer düzeylerdir.  Her test çeşitlemesi iş akışı tanımındaki etkinlik sayısı aşağıdaki tabloda belirtilmiştir:

 ![Her testte kullanılan etkinlik sayısını gösteren bir tablo](./media/performance/workflow-variation-compare-table.gif)

 İş akışı tanımındaki etkinlik sayısı her derinlik düzeyiyle keskin şekilde artar.  Ancak, karar noktası başına yalnızca bir yol, belirli bir iş akışı örneğinde yürütülür, böylece gerçek etkinliklerin yalnızca küçük bir alt kümesi yürütülür.

 ![Karmaşık verimlilik iş akışının akış çizelgesi](./media/performance/complex-workflow-throughput-workflow.gif)

 WF3 için eşdeğer bir iş akışı oluşturuldu. WF3 Tasarımcısı tüm iş akışını iç içe yerleştirme yerine tasarım alanında gösterir, bu nedenle bu konuda görüntülenemeyecek kadar büyük olur. İş akışının kod parçacığı aşağıda gösterilmiştir.

 ![WF3 iş akışının akış çizelgesi parçacığı](./media/performance/wf3-workflow-snippet.gif)

 Büyük bir durumda iç içe geçme alıştırması yapmak için, bu testin parçası olan başka bir iş akışı 100 iç içe geçmiş dizileri kullanır.  En içteki dizide tek `Comment` bir veya <xref:System.Workflow.Activities.CodeActivity>olur.

 ![İç içe geçmiş sıranın akış çizelgesi](./media/performance/nested-sequence-workflow.gif)

 İzleme ve kalıcılık bu testin bir parçası olarak kullanılmaz.

### <a name="test-results"></a>Test Sonuçları
 ![Verimlilik performansı sonuçlarını gösteren sütun grafiği](./media/performance/throughput-performance-results.gif)

 Birçok derinliğe ve çok sayıda etkinliğe sahip karmaşık iş akışlarıyla bile, performans sonuçları bu makalede daha önce gösterilen diğer üretilen iş numaralarıyla tutarlıdır.  WF4's üretilen iş hacmi daha hızlı ve Logaritmik ölçekte karşılaştırılmalıdır.

### <a name="memory"></a>Bellek
 Windows Workflow Foundation bellek ek yükü iki temel alanda ölçülür: iş akışı karmaşıklığı ve iş akışı tanımlarının sayısı.  Windows 7 64 bit iş istasyonunda bellek ölçümleri alınmıştır.  Performans sayaçlarını izleme, ortam. WorkingSet [veya VMMap](/sysinternals/downloads/vmmap)' de VMMap gibi bir araç kullanma gibi çalışma kümesi boyutunun ölçüsünü almanın birçok yolu vardır. Her testin sonucunu elde etmek ve doğrulamak için yöntemlerin bir birleşimi kullanılmıştır.

### <a name="workflow-complexity-test"></a>İş akışı karmaşıklığı testi
 İş akışı karmaşıklığı testi, iş akışının karmaşıklığına göre çalışma kümesi farkını ölçer.  Önceki bölümde kullanılan karmaşık iş akışlarına ek olarak, iki temel durumu kapsayacak yeni Çeşitlemeler eklenmiştir: tek bir etkinlik iş akışı ve 1000 etkinlikteki bir sıra.  Bu sınamalar için iş akışları başlatılır ve bir dakikalık bir süre boyunca tek bir seri döngüsünde tamamlanması için yürütülür.  Her test çeşitlemesi üç kez çalıştırılır ve kaydedilen veriler bu üç çalıştırmanın ortalamasıdır.

 İki yeni temel test aşağıda gösterildiği gibi görünen iş akışlarına sahiptir:

 ![Hem WF3 hem de WF4 için karmaşık iş akışı](./media/performance/complex-workflow-wf3-wf4.gif)

 Yukarıda gösterilen WF3 iş akışında boş <xref:System.Workflow.Activities.CodeActivity> etkinlikler kullanılır.  Yukarıdaki WF4 iş akışı etkinlikleri `Comment` kullanır.  `Comment` Etkinlik, bu makalenin önceki kısımlarında yer alarak bileşen düzeyi performans karşılaştırmaları bölümünde açıklanmıştı.

 ![WF3 ve WF4 iş akışları için karmaşık iş akışı bellek kullanımını gösteren sütun grafiği](./media/performance/complex-memory-usage-wf3-wf4.gif)

 Bu grafikte dikkat edilecek açık eğilimler, iç içe geçme, hem WF3 hem de WF4 ' de bellek kullanımı üzerinde görece küçük bir etkiye sahiptir.  En önemli bellek etkisi, belirli bir iş akışındaki etkinlik sayısından gelir.  Sıra 1000, karmaşık Derinlik 5 sıra 5 ve karmaşık Derinlik 7 sıra 1 varyasyonlarından veriler verildiğinde, etkinlik sayısı binlerce ' a girdiğinde, bellek kullanımı artışının daha belirgin hale gelir.  Çok büyük bir durumda (Derinlik 7 sıra 1) ~ 29K etkinliği olan WF4, WF3 ' den yaklaşık% 79 daha az bellek kullanıyor.

### <a name="multiple-workflow-definitions-test"></a>Birden çok Iş akışı tanımı testi
 WF3 ve WF4 ' de iş akışlarını barındırmak için kullanılabilir seçenekler nedeniyle, iş akışı tanımı başına bellek ölçme, iki farklı teste bölünmüştür.  Testler, belirli bir iş akışının ınstanmiş ve her tanım için yalnızca bir kez yürütüldüğü iş akışı karmaşıklığı testinin farklı bir şekilde çalıştırılır.  Bunun nedeni, iş akışı tanımının ve ana bilgisayarının, AppDomain 'in ömrü boyunca bellekte kalması nedeniyle oluşur.  Belirli bir iş akışı örneği çalıştırılarak kullanılan bellek çöp toplama sırasında temizlenmelidir.  WF4 için geçiş kılavuzu, barındırma seçenekleri hakkında daha ayrıntılı bilgiler içerir. Daha fazla bilgi için bkz [. WF geçişi tanıtım rehberi: İş akışı](https://go.microsoft.com/fwlink/?LinkID=153313)barındırma.

 Bir iş akışı tanımı testi için birçok iş akışı tanımı oluşturmak çeşitli yollarla yapılabilir.  Örneğin, biri ad dışında özdeş olan 1000 iş akışı kümesi oluşturmak ve bu iş akışlarının her birini ayrı dosyalara kaydetmek için kod oluşturmayı kullanabilir.  Bu yaklaşım, konsolu tarafından barındırılan test için alınmıştır.  WF3 <xref:System.Workflow.Runtime.WorkflowRuntime> içinde sınıf, iş akışı tanımlarını çalıştırmak için kullanılmıştır.  WF4, tek bir <xref:System.Activities.WorkflowApplication> iş akışı örneği oluşturmak için ya da bir yöntem <xref:System.Activities.WorkflowInvoker> çağrısı gibi etkinliği çalıştırmak için doğrudan kullanabilirsiniz.  <xref:System.Activities.WorkflowApplication>, tek bir iş akışı örneğinin bir ana bilgisayarı ve bu testte kullanılan bu <xref:System.Workflow.Runtime.WorkflowRuntime> şekilde daha yakın özellik eşliği olur.

 IIS 'de iş akışlarını barındırırken, tüm xamlx veya xoml <xref:System.Web.Hosting.VirtualPathProvider> dosyalarını oluşturmak yerine yeni <xref:System.ServiceModel.WorkflowServiceHost> bir oluşturmak için kullanmak mümkündür.  , <xref:System.Web.Hosting.VirtualPathProvider> Gelen isteği işler ve bir veritabanından yüklenebilen veya bu durumda anında oluşturulan bir "sanal dosya" ile yanıt verir.  Bu nedenle 1000 fiziksel dosya oluşturmak gereksizdir.

 Konsol testinde kullanılan iş akışı tanımları, tek bir etkinlik içeren basit sıralı iş akışlarıdır.  Tek etkinlik WF3 Case ve WF4 <xref:System.Workflow.Activities.CodeActivity> Case için bir `Comment` etkinlik için boştu.  IIS ile barındırılan Case, bir ileti almaya başlayan ve yanıt gönderme sırasında biten iş akışlarını kullandı:

Aşağıdaki görüntüde ReceiveActivity ile bir WF3 iş akışı ve istek/yanıt düzenine sahip bir WF4 iş akışı gösterilmektedir:

 ![WF3 ve WF4 ' de iş akışı hizmetleri](./media/performance/workflow-receive-activity.gif)

 Aşağıdaki tabloda, tek bir iş akışı tanımı ve 1001 tanımları arasında çalışma kümesindeki Delta gösterilmektedir:

|Barındırma seçenekleri|WF3 çalışma kümesi Delta|WF4 çalışma kümesi Delta|
|---------------------|---------------------------|---------------------------|
|Konsol uygulaması barındırılan Iş akışları|18 MB|9 MB|
|IIS barındırılan Iş akışı hizmetleri|446 MB|364 MB|

 IIS 'de barındırılan iş akışı tanımları, ayrıntılı WCF hizmet yapıtları <xref:System.ServiceModel.WorkflowServiceHost>ve konakla ilişkili ileti işleme mantığı nedeniyle daha fazla bellek tüketir.

 WF3 içinde konsol barındırma için iş akışları XOML yerine kodda uygulandı.  WF4 içinde varsayılan değer XAML kullanmaktır.  XAML, derleme içinde gömülü bir kaynak olarak depolanır ve iş akışı uygulamasını sağlamak için çalışma zamanı sırasında derlenir.  Bu işlemle ilişkili bazı ek yük vardır.  WF3 ve WF4 arasında bir dengeli karşılaştırma yapmak için XAML yerine kodlanmış iş akışları kullanılmıştır.  WF4 iş akışlarından birine bir örnek aşağıda gösterilmiştir:

```csharp
public class Workflow1 : Activity
{
    protected override Func<Activity> Implementation
    {
        get
        {
            return new Func<Activity>(() =>
            {
                return new Sequence
                {
                    Activities = {
                        new Comment()
                    }
                };
            });
        }
        set
        {
            base.Implementation = value;
        }
    }
}
```

 Bellek tüketimini etkileyebilecek birçok başka etken de vardır. Tüm yönetilen programlar için aynı öneri hala geçerlidir.  IIS 'de barındırılan ortamlarda, <xref:System.ServiceModel.WorkflowServiceHost> bir iş akışı tanımı için oluşturulan nesne, uygulama havuzu geri dönüştürülmeden önce bellekte kalır.  Uzantı yazılırken bunun aklınızda tutulması gerekir.  Ayrıca, "genel" değişkenlerin (tüm iş akışı kapsamındaki değişkenler) ve mümkün olan yerlerde değişkenlerin kapsamını sınırlandırmamak en iyisidir.

## <a name="workflow-runtime-services"></a>İş akışı çalışma zamanı Hizmetleri

### <a name="persistence"></a>Kalıcılığı
 WF3 ve WF4 her ikisi de bir SQL kalıcılık sağlayıcısıyla birlikte sevk edin.  WF3 SQL kalıcılık sağlayıcısı, iş akışı örneğini seri hale getirilen ve BLOB 'da depolayan basit bir uygulama.  Bu nedenle, bu sağlayıcının performansı büyük ölçüde iş akışı örneğinin boyutuna bağlıdır.  WF3 ' de, bu belgede daha önce anlatıldığı gibi örnek boyutu birçok nedenden dolayı artabilir.  Bir veritabanında seri hale getirilmiş bir örneği depolamak iş akışının durumuyla bir görünürlük olmadığından, birçok müşteri varsayılan SQL kalıcılık sağlayıcısını kullanmamalıdır.  İş akışı kimliğini bilmeden belirli bir iş akışını bulmak için, birinin her kalıcı örnek serisini kaldırmak ve içeriği incelemesi gerekir.  Birçok geliştirici, bu engelleri aşmak için kendi Kalıcılık sağlayıcılarını yazmayı tercih eder.

 WF4 SQL kalıcılık sağlayıcısı bu konulardan bazılarını ele geçirmeye çalıştı.  Kalıcılık tabloları, etkin yer işaretleri ve promotable özellikleri gibi belirli bilgileri sunar.  WF4 ' deki yeni içerik tabanlı bağıntı özelliği, kalıcı iş akışı örneği kuruluşunda bazı değişiklikler sunan WF3 SQL kalıcılık yaklaşımını kullanarak iyi gerçekleştirmez.  Bu, kalıcılık sağlayıcısının işini daha karmaşık hale getirir ve veritabanına daha fazla stres koyar.

### <a name="environment-setup"></a>Ortam kurulumu
![İş akışı performans testi için ortam kurulumu](./media/performance/performance-test-environment.gif)

### <a name="test-setup"></a>Test kurulumu
 Geliştirilmiş bir özellik kümesi ve daha iyi eşzamanlılık işlemesi sayesinde, WF4 'deki SQL kalıcılık sağlayıcısı WF3 'deki sağlayıcıdan daha hızlıdır.  Bunu göstermek için, WF3 ve WF4 ' de temelde aynı işlemleri gerçekleştiren iki iş akışı aşağıda karşılaştırılır.

 ![WF3 'de kalıcı ve WF4 sağ tarafta Kalıcılık iş akışı](./media/performance/persist-workflow-wf3-wf4.gif)

 İki iş akışının ikisi de alınan bir ileti tarafından oluşturulur.  İlk yanıtı gönderdikten sonra iş akışı kalıcıdır.  WF3 durumunda, kalıcılığı başlatmak için boş <xref:System.Workflow.ComponentModel.TransactionScopeActivity> bir değer kullanılır.  Aynı etkinlik, "kapanmak üzere devam ediyor" olarak işaretleyerek WF3 içinde elde edilebilir.  İkinci, bağıntılı bir ileti iş akışını tamamlar.  İş akışları kalıcı, ancak yüklenmemiş.

### <a name="test-results"></a>Test Sonuçları
 ![Verimlilik kalıcılığını gösteren sütun grafiği](./media/performance/throughput-persistence-graph.gif)

 İstemci ve orta katman arasındaki aktarım HTTP olduğunda, WF4 ' de Kalıcılık 2,6 sürelerin bir geliştirmesini gösterir.  TCP taşıması bu faktörü 3,0 kez artırır.  Her durumda, orta katmandaki CPU kullanımı% 98 veya daha yüksektir.  WF4 aktarım hızı, daha hızlı iş akışı çalışma zamanının nedenidir.  Serileştirilmiş örnek boyutu her iki durum için de düşüktür ve bu durumda ana katkıda bulunan bir öğe değildir.

 Bu testteki WF3 ve WF4 iş akışlarının her ikisi de kalıcılığın ne zaman gerçekleşmesi gerektiğini açıkça belirtmek için bir etkinlik kullanır.  Bu, iş akışını kaldırmadan kalıcı hale getirme avantajına sahiptir.  WF3 ' de, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> özelliği kullanılarak kalıcı hale getirilmesi olasıdır, ancak bu, iş akışı örneğini bellekten kaldırır.  WF3 kullanan bir geliştirici, bir iş akışının belirli noktalarda devam ettiğinden emin olmak istiyorsa, iş akışı tanımını değiştirmeleri veya iş akışı örneğini kaldırma ve yeniden yükleme maliyetini ödemelidir.  WF4 ' deki yeni bir özellik, kaldırma olmadan kalıcı hale getirme olanağı <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>sağlar:.  Bu özellik, iş akışı örneğinin boşta durumunda kalıcı olmasını sağlar, ancak <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> eşik karşılanmadığında veya yürütme sürdürülene kadar bellekte kalır.

 WF4 SQL kalıcılık sağlayıcısı 'nın veritabanı katmanında daha fazla iş gerçekleştireceğini unutmayın.  SQL veritabanı performans sorunlarına yol açabilir, bu sayede CPU ve disk kullanımını izlemek önemlidir.  Performans testi iş akışı uygulamaları sırasında SQL veritabanından aşağıdaki performans sayaçlarını eklediğinizden emin olun:

- FizikselDisk\\okuma zamanı

- FizikselDisk\\zamanı

- FizikselDisk\\yazma zamanı

- Fiziksel\\disk% ort. Disk kuyruğu uzunluğu

- Fiziksel Disk\Ortalama Disk okuma sırası uzunluğu

- Fiziksel Disk\Ortalama Disk yazma sırası uzunluğu

- Physicaldisk\geçerli disk kuyruğu uzunluğu

- İşlemci bilgileri\\% işlemci zamanı

- SQLServer: Latches\ortalama mandal bekleme süresi (MS)

- SQLServer: Latches\mandal bekleme/sn

### <a name="tracking"></a>İzleme
 İş akışı izleme iş akışının ilerlemesini izlemek için kullanılabilir.  İzleme olaylarına dahil edilen bilgiler bir izleme profili tarafından belirlenir.  İzleme profili daha karmaşıktır, daha pahalı izleme olur.

 WF3, SQL tabanlı bir izleme hizmetiyle birlikte gönderilir.  Bu hizmet toplanmış ve toplu olmayan modlarda çalışabilir.  Toplu olmayan modda, izleme olayları doğrudan veritabanına yazılır.  Toplu modda, izleme olayları iş akışı örneği durumu ile aynı toplu işe toplanır.  Toplu iş modu, en geniş iş akışı tasarımı yelpazesi için en iyi performansa sahiptir.  Ancak, iş akışı kalıcı olmadan çok sayıda etkinlik çalıştırıyorsa ve bu etkinlikler izleniyorsa, toplu işleme olumsuz bir performans etkisine sahip olabilir.  Bu durum genellikle Döngülerde ve bu senaryonun oluşmaması için en iyi yol, kalıcılık noktası içeren büyük döngüler tasarlamanızı sağlar.  Bir döngüye bir kalıcılık noktası eklemek, performansı olumsuz etkileyebilir ve her birinin maliyetlerini ölçmek ve bir denge ile birlikte gelmesi önemlidir.

 WF4, bir SQL izleme hizmeti ile birlikte sunulmadı.  İzleme bilgilerinin bir SQL veritabanına kaydedilmesi .NET Framework yerleşik olarak değil, uygulama sunucusundan daha iyi işlenebilir. Bu nedenle, SQL izleme artık AppFabric tarafından işlenir.  WF4 ' deki kullanıma hazır izleme sağlayıcısı, Windows için olay Izleme 'yi (ETW) temel alır.

 ETW, Windows 'da yerleşik olarak bulunan çekirdek düzeyi, düşük gecikme süreli bir olay sistemidir.  Aslında bir tüketici olduğunda olay izlemenin ceza haline gelmesini olanaklı kılan bir sağlayıcı/tüketici modeli kullanır.  İşlemci, disk, bellek ve ağ kullanımı gibi çekirdek olaylarına ek olarak, birçok uygulama da ETW 'den yararlanır.  ETW olayları, olaylar uygulamaya özelleştirilebilecek performans sayaçlarından daha güçlüdür.  Bir olay, iş akışı KIMLIĞI veya bilgilendirici ileti gibi bir metin içerebilir.  Ayrıca, olaylar bitmaskelerle sınıflandırıldığından, belirli bir olay alt kümesini kullanabilmeniz tüm olayları yakalamaya kıyasla daha az performans etkisine sahip olur.

 SQL şunları yapmak yerine, izleme için ETW kullanma yaklaşımının avantajları şunlardır:

- İzleme olaylarının toplanması, başka bir işleme ayrılabilir.  Bu, olayların nasıl kaydedildiği konusunda daha fazla esneklik sağlar.

- ETW izleme olayları, WCF ETW olayları veya SQL Server veya çekirdek sağlayıcısı gibi diğer ETW sağlayıcılarıyla kolayca birleştirilir.

- İş akışı yazarlarının, WF3 SQL izleme hizmeti 'nin toplu işlem modu gibi belirli bir izleme uygulamasıyla daha iyi çalışması için iş akışını değiştirme gereksinimi yoktur.

- Yönetici, ana bilgisayar işlemini geri dönüşüme gerek kalmadan izlemeyi etkinleştirebilir veya devre dışı bırakır.

 ETW izlemeye yönelik performans avantajları bir dezavantajı sağlar.  Sistem yoğun kaynak baskısı altındaysa ETW olayları kaybolabilir.  Olayların işlenmesi normal program yürütmeyi engellenemez ve bu nedenle, tüm ETW olaylarının abonelere yayınlanacağı garanti edilmez.  Bu, ETW izlemeyi sistem durumu izleme için harika hale getirir ancak denetim için uygun değildir.

 WF4 bir SQL izleme sağlayıcısına sahip olmasa da, AppFabric bunu yapar.  AppFabric 'in SQL izleme yaklaşımı, olayları toplu olarak uygulayan bir Windows hizmeti ile ETW olaylarına abone olmak ve bunları hızlı ekleme için tasarlanan bir SQL tablosuna yazar.  Ayrı bir iş bu tablodaki verileri boşaltır ve bunu AppFabric panosunda görüntülenebilen raporlama tablolarına yeniden oluşturur.  Bu, izleme olaylarının bir toplu işlem tarafından geldiği iş akışından bağımsız olarak işlendiği ve bu nedenle kaydedilmeden önce bir kalıcılık noktası beklemek zorunda olmadığı anlamına gelir.

 ETW olayları, logman veya XPerf gibi araçlarla kaydedilebilir.  Compact ETL dosyası xperfview gibi bir araçla görüntülenebilir veya tracerpt ile XML gibi daha okunabilir bir biçime dönüştürülebilirler.  WF3 ' de, SQL veritabanı olmadan izleme olaylarını almak için tek seçenek, özel bir izleme hizmeti oluşturmaktır. ETW hakkında daha fazla bilgi için bkz. [Windows Için WCF Hizmetleri ve olay izleme](../wcf/samples/wcf-services-and-event-tracing-for-windows.md) ve [olay izleme-Windows uygulamaları](/windows/desktop/etw/event-tracing-portal).

 İş akışı izlemenin etkinleştirilmesi, performansı değişen derecelerde etkiler.  Aşağıdaki kıyaslama, ETW izleme olaylarını tüketmek ve bunları bir ETL dosyasına kaydetmek için logman aracını kullanır.  AppFabric 'teki SQL izlemenin maliyeti Bu makalenin kapsamında değildir.  Ayrıca, AppFabric 'te kullanılan temel izleme profili Bu kıyaslama bölümünde gösterilmiştir.  Ayrıca, yalnızca sistem durumu izleme olaylarının izlenmesi maliyetlidir.  Bu olaylar sorunları gidermek ve sistemin ortalama verimini belirlemek için faydalıdır.

### <a name="environment-setup"></a>Ortam kurulumu
 ![İş akışı performans testi için ortam kurulumu](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Test Sonuçları

 ![İş akışı izleme maliyetlerini gösteren sütun grafiği](./media/performance/workflow-tracking-costs.gif)

 Sistem durumu izleme performansı kabaca% 3 oranında etkiler.  Temel profilin maliyeti% 8 ' dir.

## <a name="interop"></a>Interop
 WF4 neredeyse tamamen yeniden yazın [!INCLUDE[wf1](../../../includes/wf1-md.md)] ve bu nedenle WF3 iş akışları ve etkinlikler doğrudan WF4 ile uyumlu değildir.  Erken Windows Workflow Foundation benimseyen birçok müşteri, şirket içi veya üçüncü taraf iş akışı tanımlarına ve WF3 için özel etkinliklere sahip olacaktır.  WF4 'e geçişi kolaylaştırmak için bir yol, bir WF4 iş akışı içinden WF3 etkinliklerini yürütebilen birlikte çalışma etkinliğini kullanmaktır.  <xref:System.Activities.Statements.Interop> Etkinliğin yalnızca gerektiğinde kullanılması önerilir. WF4 ' ye geçme hakkında daha fazla bilgi için [WF4 geçiş kılavuzunu](https://go.microsoft.com/fwlink/?LinkID=153313)inceleyin.

### <a name="environment-setup"></a>Ortam kurulumu
 ![İş akışı performans testi için ortam kurulumu](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Test Sonuçları
 
Aşağıdaki tabloda, çeşitli yapılandırmalarda bir dizide beş etkinlik içeren bir iş akışını çalıştırmanın sonuçları gösterilmektedir.

|Test|Aktarım hızı (iş akışı/sn)|
|----------|-----------------------------------|
|WF3 çalışma zamanında WF3 sırası|1,576|
|WF4 çalışma zamanında Interop kullanarak WF3 sırası|2,745|
|WF4 sırası|153,582|

 Düz WF3 ile birlikte çalışabilirliğine yönelik bir önemli performans artışı vardır.  Ancak, WF4 etkinlikleriyle karşılaştırıldığında artış göz ardı edilir.

## <a name="summary"></a>Özet
 WF4 için performans açısından ağır yatırımlar, birçok önemli alanda ödenmiştir.  Tek bir iş akışı bileşeni performansı, WF4 ' de bir daha yalın [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanı nedeniyle WF3 ile karşılaştırıldığında yüzlerce kat daha hızlı olur.  Gecikme süreleri de önemli ölçüde daha iyidir.  Bu, WCF düzenleme hizmetleri 'nin el [!INCLUDE[wf1](../../../includes/wf1-md.md)] ile kodlanması yerine kullanmanın performans cezası, kullanmanın [!INCLUDE[wf1](../../../includes/wf1-md.md)]sağladığı avantajların çok küçük olduğu anlamına gelir.  Kalıcılık performansı 2,5-3,0 faktörüyle artmıştır.  İş akışı izlemenin sistem durumu izleme işlemi artık çok az yüke sahip.  WF3 ' den WF4 ' ye geçmeyi düşünürken kapsamlı bir geçiş kılavuzu kümesi vardır.  Tüm bu WF4 karmaşık uygulamaları yazmak için etkileyici bir seçenek almalıdır.
