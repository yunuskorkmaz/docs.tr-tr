---
title: Windows Workflow Foundation 4 Performansı
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: 5fec41baacca0f35618dd5bc409b88ac792ad125
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182972"
---
# <a name="windows-workflow-foundation-4-performance"></a>Windows Workflow Foundation 4 Performansı

 .NET Framework 4, Windows İş Akışı Vakfı'nın (WF) performansa ağır yatırımlarla büyük bir revizyonunu içerir. Bu yeni revizyon, .NET Framework 3.0 ve .NET Framework 3.5'in bir parçası olarak gönderilen [!INCLUDE[wf1](../../../includes/wf1-md.md)] önceki sürümlerden önemli tasarım değişiklikleri sunar. Performans ve kullanılabilirliği büyük ölçüde artırmak için programlama modelinin, çalışma zamanının ve araçlamanın özünden yeniden şekillendirilmiştir. Bu konu, bu düzeltmelerin önemli performans özelliklerini gösterir ve bunları önceki sürümle karşılaştırır.

 Bireysel iş akışı bileşeni performansı WF3 ve WF4 arasındaki büyüklük siparişleri ile artmıştır.  Bu, el kodlu Windows Communication Foundation (WCF) hizmetleri ile WCF iş akışı hizmetleri arasındaki boşluğu oldukça küçük bırakır.  WF4'te iş akışı gecikmesi önemli ölçüde azaltıldı.  Kalıcılık performansı 2,5 - 3,0 faktörüyle artmıştır.  İş akışı izleme yoluyla sistem durumu izleme nin önemli ölçüde daha az yükü vardır.  Bunlar, uygulamalarınızda WF4'e geçiş yapmak veya benimsemek için zorlayıcı nedenlerdir.

## <a name="terminology"></a>Terminoloji

 .NET [!INCLUDE[wf1](../../../includes/wf1-md.md)] Framework 4'te tanıtılan sürümü, bu konunun geri kalanı için WF4 olarak anılacaktır. [!INCLUDE[wf1](../../../includes/wf1-md.md)].NET Framework 3.0'da tanıtıldı ve .NET Framework 3.5 SP1 üzerinden birkaç küçük revizyon yapıldı. İş Akışı Vakfı'nın .NET Framework 3.5 sürümü bu konunun geri kalanı için WF3 olarak anılacaktır. WF3,.NET Framework 4'te WF4 ile yan yana gönderilir. WF3 yapılarını WF4'e geçirme hakkında daha fazla bilgi için bkz: [Windows İş Akışı Vakfı 4 Geçiş Kılavuzu.](migration-guidance.md)

 Windows Communication Foundation (WCF), Microsoft'un hizmet odaklı uygulamalar oluşturmak için birleştirilmiş programlama modelidir. İlk olarak .NET 3.0'ın bir parçası olarak WF3 ile birlikte tanıtıldı ve şimdi .NET Framework'ün temel bileşenlerinden biri.

 Windows Server AppFabric, IIS'de çalışan Web ve bileşik uygulamaları oluşturmayı, ölçeklendirmeyi ve yönetmeyi kolaylaştıran bir dizi entegre teknolojidir. Hizmetleri ve iş akışlarını izlemek ve yönetmek için araçlar sağlar. Daha fazla bilgi için [Windows Server AppFabric 1.0'a](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10))bakın.

## <a name="goals"></a>Hedefler
 Bu konunun amacı, farklı senaryolar için ölçülen verilerle WF4'ün performans özelliklerini göstermektir. Ayrıca WF4 ve WF3 arasında ayrıntılı karşılaştırmalar sağlar ve böylece bu yeni revizyon yapılmış büyük iyileştirmeler gösterir. Bu makalede sunulan senaryolar ve veriler, WF4 ve WF3'ün farklı yönlerinin temel maliyetini ölçer. Bu veriler WF4'ün performans özelliklerini anlamada yararlıdır ve WF3'ten WF4'e geçişlerin planlanmasında veya uygulama geliştirmede WF4'ün kullanılmasında yararlı olabilir. Ancak, bu makalede sunulan verilerden elde edilen sonuçlara dikkat edilmelidir. Bileşik iş akışı uygulamasının performansı, iş akışının nasıl uygulandığına ve farklı bileşenlerin nasıl entegre edildiğine bağlıdır. Bu uygulamanın performans özelliklerini belirlemek için her uygulamayı ölçmek gerekir.

## <a name="overview-of-wf4-performance-enhancements"></a>WF4 Performans Geliştirmelerine Genel Bakış
 WF4, aşağıdaki bölümlerde açıklanan yüksek performans ve ölçeklenebilirlik ile özenle tasarlanmış ve uygulanmıştır.

### <a name="wf-runtime"></a>WF Çalışma Süresi
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] Çalışma zamanının özünde, bir iş akışındaki etkinliklerin yürütülmesini sağlayan eşzamanlı bir zamanlayıcı yer alan bir zamanlama yer alan bir programcıdır. Etkinlikler için performant, öngörülebilir bir yürütme ortamı sağlar. Ortamın yürütme, devamı, tamamlanması, iptali, özel durumlar ve öngörülebilir bir iş parçacığı modeli için iyi tanımlanmış bir sözleşmesi vardır.

 WF3 ile karşılaştırıldığında, WF4 çalışma süresi daha verimli bir zamanlayıcıya sahiptir. Bu, toplu iş öğelerinin yürütülmesinde çok verimli olan WCF için kullanılan aynı G/Ç iş parçacığı havuzundan yararlanır. İç iş öğesi zamanlayıcı sırası en yaygın kullanım desenleri için en iyi duruma getirilmiş. WF4 çalışma süresi de en az eşitleme ve olay işleme mantığı ile çok hafif bir şekilde yürütme durumları yönetir, WF3 ağır olay kaydı ve devlet geçişleri için karmaşık senkronizasyon gerçekleştirmek için çağırma bağlıdır.

### <a name="data-storage-and-flow"></a>Veri Depolama ve Akış
 WF3'te, bir etkinlikle ilişkili veriler, türe <xref:System.Windows.DependencyProperty>göre uygulanan bağımlılık özellikleri yle modellenir. Bağımlılık özelliği deseni Windows Sunu Temeli'nde (WPF) tanıtıldı. Genel olarak, bu desen kolay veri bağlama ve diğer UI özelliklerini desteklemek için çok esnektir. Ancak, desen özellikleri iş akışı tanımında statik alanlar olarak tanımlanmasını gerektirir. [!INCLUDE[wf1](../../../includes/wf1-md.md)] Çalışma zamanı, özellik değerlerini her aldığında veya aldığında, ağırlıklı arama mantığı içerir.

 WF4, verilerin iş akışında nasıl işleneceğini büyük ölçüde iyileştirmek için net veri kapsam mantığı kullanır. Bir etkinlikte depolanan verileri, değişkenler ve bağımsız değişkenler olmak üzere iki farklı kavram kullanarak etkinlik sınırları boyunca akan verilerden ayırır. Değişkenler ve "In/Out/InOut" bağımsız değişkenleri için açık bir hiyerarşik kapsam kullanılarak, etkinlikler için veri kullanım karmaşıklığı önemli ölçüde azalır ve verilerin ömrü de otomatik olarak kapsamlıdır. Etkinlikler, bağımsız değişkenleri tarafından açıklanan iyi tanımlanmış bir imzaya sahiptir. Bir etkinliği inceleyerek hangi verilerin almayı beklediğini ve yürütülmesi sonucunda hangi verilerin üretileceğini belirleyebilirsiniz.

 WF3'te bir iş akışı oluşturulduğunda faaliyetler başharfe çevrildi. WF 4'teki etkinlikler yalnızca ilgili etkinlikler yürütüldüğünde başolarak başolarak verilir. Bu, yeni bir iş akışı örneği oluşturulduğunda Initialize/Uninitialize işlemleri gerçekleştirmeden daha basit bir etkinlik yaşam döngüsü sağlar ve böylece daha fazla verimlilik elde etmiştir

### <a name="control-flow"></a>Denetim Akışı
 Her programlama dilinde olduğu [!INCLUDE[wf1](../../../includes/wf1-md.md)] gibi, sıralama, döngü, dallanma ve diğer desenler için bir dizi denetim akışı aktivitesi sunarak iş akışı tanımları için denetim akışları için destek sağlar. WF3'te, aynı etkinliğin yeniden yürütülmesi gerektiğinde, <xref:System.Workflow.ComponentModel.ActivityExecutionContext> yeni bir etkinlik oluşturulur ve etkinlik, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>'ye dayalı ağır bir serileştirme ve deserialization mantığı ile klonlanır. Genellikle yinelemeli denetim akışları için performans çok daha yavaş bir dizi etkinlik yürütme daha.

 WF4 bu oldukça farklı işler. Etkinlik şablonunu alır, yeni bir ActivityInstance nesnesi oluşturur ve zamanlayıcı sırasına ekler. Tüm bu işlem yalnızca açık nesne oluşturma içerir ve çok hafiftir.

### <a name="asynchronous-programming"></a>Zaman Uyumsuz Programlama
 Uygulamalar genellikle G/Ç veya dağıtılmış bilgi işlem işlemleri gibi uzun süreli engelleme işlemleri için eşzamanlı programlama ile daha iyi performans ve ölçeklenebilirlik sağlar. WF4, temel etkinlik türleri <xref:System.Activities.AsyncCodeActivity>aracılığıyla eşzamanlı <xref:System.Activities.AsyncCodeActivity%601>destek sağlar. Çalışma zamanı, eşzamanlı etkinlikleri yerel olarak anlar ve bu nedenle, eşzamanlı çalışma olağanüstüyken örneği otomatik olarak kalıcı olmayan bir bölgeye koyabilir. Özel etkinlikler, iş akışı zamanlayıcısı iş parçacığı tutmadan ve paralel olarak çalıştırmak mümkün olabilecek herhangi bir etkinlikleri engellemeden eşzamanlı çalışma gerçekleştirmek için bu tür tür türlerden türetebilirsiniz.

### <a name="messaging"></a>Mesajlaşma
 Başlangıçta WF3 dış olaylar veya web hizmetleri çağrıları ile çok sınırlı mesajlaşma desteği vardı. .NET 3.5'te, iş akışları WCF istemcileri olarak uygulanabilir <xref:System.Workflow.Activities.SendActivity> veya <xref:System.Workflow.Activities.ReceiveActivity>WCF hizmetleri yoluyla ve . WF4'te, iş akışı tabanlı mesajlaşma programlama kavramı, WCF mesajlaşma mantığının WF'ye sıkı entegrasyonu yla daha da güçlendirilmiştir.

 .NET 4'te WCF'de sağlanan birleşik ileti işleme ardışık hattı, WF4 hizmetlerinin WF3'ten önemli ölçüde daha iyi performans ve ölçeklenebilirliğe sahip olmasını sağlar. WF4 ayrıca karmaşık İleti Değişim Desenleri (MEPs) modelleyebilir zengin mesajlaşma programlama desteği sağlar. Geliştiriciler, serileştirme maliyetleri ödemeden daha iyi performans elde etmek için kolay programlama veya yazılmamış hizmet sözleşmeleri elde etmek için yazılı hizmet sözleşmelerini kullanabilir. WF4'te <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıf boyunca istemci tarafındaki kanal önbelleğe alma desteği, geliştiricilerin en az çabayla hızlı uygulamalar oluşturmasına yardımcı olur. Daha fazla bilgi için, [Etkinlikler Gönder için Önbellek Paylaşım Düzeylerini Değiştirme'ye](../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)bakın.

### <a name="declarative-programming"></a>Bildirimsel Programlama
 WF4, iş süreçlerini ve hizmetlerini modellemek için temiz ve basit bir bildirimsel programlama çerçevesi sağlar. Programlama modeli, iş akışı yetkilendirmeyi büyük ölçüde basitleştirerek, hiçbir kod yanında olmayan, tam olarak bildirimsel etkinlik bileşimini destekler. .NET Framework 4'te, XAML tabanlı bildirimsel programlama çerçevesi, hem WPF hem de WF'yi desteklemek için tek montaj System.Xaml.dll'de birleştirilmiştir.

 WF4'te XAML gerçekten açıklayıcı bir deneyim sağlar ve iş akışının tüm tanımının XML biçimlendirmesinde tanımlanmasına izin verir, etkinliklere ve .NET kullanılarak oluşturulmuş türlere başvurur. Bu özel kod arkası mantığı dahil olmadan XOML biçimi ile WF3 yapmak zordu. .NET 4'teki yeni XAML yığını, iş akışı yapılarını serileştirme/deserializing'de çok daha iyi performansa sahiptir ve bildirimsel programlamayı daha çekici ve sağlam hale getirir.

### <a name="workflow-designer"></a>İş Akışı Tasarımcısı
 WF4 için tam bildirimsel programlama desteği, büyük iş akışları için tasarım süresi performansı için daha yüksek gereksinimler açıkça uygular. WF4'teki İş Akışı tasarımcısı, büyük iş akışları için WF3'ten çok daha iyi ölçeklenebilirliğe sahiptir. UI sanallaştırma desteği ile tasarımcı, WF3 tasarımcısıyla birkaç yüz aktiviteden oluşan bir iş akışını yüklemek neredeyse imkansızken, birkaç saniye içinde 1000 aktiviteden oluşan büyük bir iş akışını kolayca yükleyebilir.

## <a name="component-level-performance-comparisons"></a>Bileşen düzeyinde Performans Karşılaştırmaları
 Bu bölümde, WF3 ve WF4 iş akışlarındaki tek tek etkinlikler arasındaki doğrudan karşılaştırmalar hakkında veriler yer almaktadır.  Kalıcılık gibi temel alanlar, performans üzerinde tek tek etkinlik bileşenlerine göre daha derin bir etkiye sahiptir.  WF4'teki tek tek bileşenlerdeki performans iyileştirmeleri önemlidir, çünkü bileşenler artık elle kodlanmış orkestrasyon mantığıyla karşılaştırılacak kadar hızlıdır.  Bir sonraki bölümde ele alınan bir örnek: "Hizmet Kompozisyonu Senaryosu."

### <a name="environment-setup"></a>Ortamı Ayarlama
 ![İş akışı performans ölçümü için ortam kurulumu](./media/performance/performance-test-environment.gif)

 Yukarıdaki şekil, bileşen düzeyinde performans ölçümü için kullanılan makine yapılandırmasını gösterir. Tek bir sunucu ve beş istemci bir 1 Gbps Ethernet ağ arabirimi üzerinden bağlanır. Kolay ölçümler için sunucu, Windows Server 2008 x86 çalıştıran çift proc/dört çekirdekli sunucunun tek bir çekirdeğini kullanacak şekilde yapılandırılmıştır. Sistem CPU kullanımı yaklaşık% 100 korunur.

### <a name="test-details"></a>Test Detayları
 WF3 <xref:System.Workflow.Activities.CodeActivity> büyük olasılıkla bir WF3 iş akışında kullanılabilecek en basit etkinliktir.  Etkinlik, iş akışı programcısının özel kodu koyabileceği kod arkasında bir yöntem çağırır.  WF4'te, aynı işlevselliği sağlayan WF3'e <xref:System.Workflow.Activities.CodeActivity> doğrudan analog yoktur.  WF4'te <xref:System.Activities.CodeActivity> WF3 <xref:System.Workflow.Activities.CodeActivity>ile ilgili olmayan bir taban sınıf olduğunu unutmayın.  İş akışı yazarlarının özel etkinlikler oluşturması ve yalnızca XAML iş akışları oluşturması teşvik edilir.  Aşağıdaki testlerde, WF4 iş akışlarında `Comment` <xref:System.Workflow.Activities.CodeActivity> boş bir boş yerine bir etkinlik kullanılır.  Etkinlikteki `Comment` kod aşağıdaki gibidir:

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

### <a name="empty-workflow"></a>Boş İş Akışı
 Bu test, alt etkinlik olmayan bir dizi iş akışı kullanır.

### <a name="single-activity"></a>Tek Etkinlik
 İş akışı, bir alt etkinlik içeren bir dizi iş akışıdır.  Etkinlik, <xref:System.Workflow.Activities.CodeActivity> WF3 örneğinde kod olmayan ve `Comment` WF4 durumunda ki bir etkinliktir.

### <a name="while-with-1000-iterations"></a>1000 Yinelemeli iken
 Sıra iş akışı, <xref:System.Activities.Statements.While> döngüde herhangi bir çalışma gerçekleştirmeyen bir alt etkinlik içeren bir etkinlik içerir.

### <a name="replicator-compared-to-parallelforeach"></a>ParallelForEach ile karşılaştırıldığında çoğaltıcı
 <xref:System.Workflow.Activities.ReplicatorActivity>WF3 sıralı ve paralel yürütme modları vardır.  Sıralı modda, etkinliğin performansı <xref:System.Workflow.Activities.WhileActivity>.  Paralel <xref:System.Workflow.Activities.ReplicatorActivity> yürütme için en yararlıdır.  Bunun için WF4 analog <xref:System.Activities.Statements.ParallelForEach%601> faaliyettir.

 Aşağıdaki diyagram, bu test için kullanılan iş akışlarını gösterir. WF3 iş akışı solda, WF4 iş akışı sağdadır.

 ![WF3 ÇoğalıcıAktivite ve WF4 ParallelForEach](./media/performance/replicator-parallel-wf3-wf4.gif)

### <a name="sequential-workflow-with-five-activities"></a>Beş Etkinlikli Sıralı İş Akışı
 Bu test, sırayla yürütülmesi birkaç etkinlik olan etkisini göstermek içindir.  Dizide beş etkinlik vardır.

### <a name="transaction-scope"></a>İşlem Kapsamı
 Her yineleme için yeni bir iş akışı örneği oluşturulmamasına göre, işlem kapsamı sınaması diğer testlerden biraz farklıdır.  Bunun yerine, iş akışı, hiçbir iş <xref:System.Activities.Statements.TransactionScope> yok tek bir etkinlik içeren bir aktivite içeren bir while döngüsü ile yapılandırılır.  While döngüsü boyunca 50 yinelemeden oluşan bir toplu işlemin her çalışması tek bir işlem olarak sayılır.

### <a name="compensation"></a>Dengeleme
 WF3 iş akışı adlı `WorkScope`tek bir telafi edici etkinlik vardır.  Etkinlik yalnızca <xref:System.Workflow.ComponentModel.ICompensatableActivity> arabirimi uygular:

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

 Hata işleyicisi `WorkScope` etkinliği hedefler. WF4 iş akışı eşit derecede basittir.  A'nın <xref:System.Activities.Statements.CompensableActivity> bir gövdesi ve bir tazminat işleyicisi vardır.  Sırada açık bir telafi sonraki sıradadır.  Gövde aktivitesi ve tazminat işleyicisi etkinliği her ikisi de boş uygulamalardır:

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

Aşağıdaki diyagram, temel kompanzasyon iş akışını gösterir. WF3 iş akışı solda, WF4 iş akışı sağdadır.

![WF3 ve WF4 temel kompanzasyon iş akışları](./media/performance/basic-compensation-workflows-wf3-wf4.gif)

### <a name="performance-test-results"></a>Performans Testi Sonuçları

 ![Performans testi sonuçları verilerini gösteren tablo](./media/performance/performance-test-data.gif)

 ![WF3 ve WF4 performans testi verilerini karşılaştıran sütun grafiği](./media/performance/performance-test-chart.gif)

 Tüm testler, işlem kapsamı testi dışında saniyede iş akışları cinsinden ölçülür.  Yukarıda da görüleceği [!INCLUDE[wf1](../../../includes/wf1-md.md)] gibi, çalışma zamanı performansı, özellikle while döngüsü gibi aynı etkinliğin birden fazla yürütülmesini gerektiren alanlarda, yönetim kurulu genelinde iyileşmiştir.

## <a name="service-composition-scenario"></a>Hizmet Kompozisyonu Senaryosu
 Önceki bölümde gösterildiği gibi, "Bileşen düzeyinde Performans Karşılaştırmaları," WF3 ve WF4 arasında genel olarak önemli bir azalma olmuştur.  WCF iş akışı hizmetleri artık neredeyse elle kodlanmış WCF hizmetlerinin performansıyla eşleşebilir, ancak çalışma süresinin [!INCLUDE[wf1](../../../includes/wf1-md.md)] tüm avantajlarına sahip olabilir.  Bu test senaryosu, WCF hizmetini WF4'teki bir WCF iş akışı hizmetiyle karşılaştırır.

### <a name="online-store-service"></a>Online Mağaza Hizmeti
 Windows İş Akışı Temeli'nin güçlü yanlarından biri, çeşitli hizmetleri kullanarak işlem oluşturabilmektir.  Bu örnekte, sipariş satın almak için iki servis çağrısı düzenleyen bir çevrimiçi mağaza hizmeti vardır.  İlk adım, sipariş doğrulama hizmetini kullanarak siparişi doğrulamaktır.  İkinci adım, ambar hizmetini kullanarak siparişi doldurmaktır.

 İki arka uç hizmeti, Sipariş Doğrulama Hizmeti ve Ambar Hizmeti, her iki test için de aynı kalır.  Değişen bölüm, orkestrasyonu gerçekleştiren Çevrimiçi Mağaza Hizmeti'dir.  Bir durumda, hizmet wcf hizmeti olarak elle kodlanır.  Diğer durumda, hizmet WF4'te WCF iş akışı hizmeti olarak yazılır. [!INCLUDE[wf1](../../../includes/wf1-md.md)]-izleme ve kalıcılık gibi belirli özellikler bu test için kapatılır.

### <a name="environment"></a>Ortam
![Performans ölçümü için ortam kurulumu](./media/performance/performance-test-environment.gif)

 İstemci istekleri, birden çok bilgisayardan HTTP aracılığıyla Çevrimiçi Mağaza Hizmeti'ne yapılır.  Tek bir bilgisayar üç hizmeti de barındırabilir.  Çevrimiçi Mağaza Hizmeti ile arka uç hizmetleri arasındaki aktarım katmanı TCP veya HTTP'dir.  İşlemlerin/saniyelerin ölçümü, Çevrimiçi Mağaza `PurchaseOrder` Hizmeti'ne yapılan tamamlanmış arama ların sayısına bağlıdır.  Kanal havuzu WF4'te kullanılabilen yeni bir özelliktir.  Bu test kanalı havuzunun WCF bölümünde kutudan dışarı sağlanamamaktadır, bu nedenle Çevrimiçi Mağaza Hizmeti'nde basit bir havuzlama tekniğinin elle kodlanmış bir uygulaması kullanılmıştır.

### <a name="performance"></a>Performans
![Çevrimiçi Mağaza Hizmeti performansını gösteren sütun grafiği](./media/performance/online-store-performance-graph.gif)

 Kanal havuzu olmadan arka uç TCP hizmetlerine [!INCLUDE[wf1](../../../includes/wf1-md.md)] bağlanan hizmet, iş yaratma üzerinde %17,2'lik bir etkiye sahiptir.  Kanal havuzu ile, ceza yaklaşık% 23,8 olduğunu.  HTTP için, etkisi çok daha azdır: 4.3% havuzlama olmadan ve% 8.1 havuzlama ile.  Ayrıca, http kullanırken kanal havuzu çok az fayda sağladığını unutmayın.

 WF4 çalışma zamanından genel olarak bu testte elle kodlanmış bir WCF hizmetiyle karşılaştırıldığında, en kötü durum senaryosu olarak kabul edilebilir.  Bu testte iki arka uç hizmetleri çok az iş yapmak.  Gerçek bir uçtan uca senaryoda, bu hizmetler veritabanı çağrıları gibi daha pahalı işlemler gerçekleştirerek aktarım katmanının performans etkisini daha az önemli hale getirir.  Bu ve WF4'te bulunan özelliklerin avantajları, İş Akışı Vakfı'nı orkestrasyon hizmetleri oluşturmak için uygun bir seçim haline getirir.

## <a name="key-performance-considerations"></a>Önemli Performans Hususları
 Bu bölümdeki özellik alanları, interop hariç, WF3 ve WF4 arasında önemli ölçüde değişti.  Bu, iş akışı uygulamalarının tasarımını ve performansı etkiler.

#### <a name="workflow-activation-latency"></a>İş Akışı Etkinleştirme Gecikmesi
 WCF iş akışı hizmeti uygulamasında, yeni bir iş akışı başlatma veya varolan bir iş akışını yükleme gecikmesi, engelleyici olabileceğinden önemlidir.  Bu test çalışması, tipik bir senaryoda wf4 XAMLX ana bilgisayara karşı bir WF3 XOML ana bilgisayarölçer.

##### <a name="environment-setup"></a>Ortamı Ayarlama
 ![Gecikme ve iş sonu testleri için ortam kurulumu](./media/performance/latency-throughput-environment-setup.gif)

##### <a name="test-setup"></a>Test Kurulumu
 Senaryoda, istemci bilgisayar bağlam tabanlı korelasyon kullanarak bir WCF iş akışı hizmetiyle bağlantı kurur.  Bağlam bağıntısı özel bir bağlam bağlama gerektirir ve iletileri doğru iş akışı örneğiyle ilişkilendirmek için bir bağlam üstbilgisi veya çerez kullanır.  İleti gövdesinin ayrıştırılması gerekmesin diye, korelasyon Kimliğinin ileti üstbilgisinde bulunması nda bir performans avantajı vardır.

 Hizmet, istekle birlikte yeni bir iş akışı oluşturur ve gecikme ölçüsünün iş akışını çalıştırmak için harcanan zamanı içermemesi için anında yanıt gönderir.  WF3 iş akışı, kod arkası xoml'dir ve WF4 iş akışı tamamen XAML'dir.  WF4 iş akışı aşağıdaki gibi görünür:

 ![WF4 Korelasyon Kapsamı iş akışı](./media/performance/wf4-correlationscope-workflow.gif)

 Etkinlik <xref:System.ServiceModel.Activities.Receive> iş akışı örneğini oluşturur.  Alınan iletide geçirilen bir değer yanıt iletisinde yankılanır.  Yanıtı izleyen bir sıra, iş akışının geri kalanını içerir.  Yukarıdaki durumda, yalnızca bir yorum etkinliği gösterilir.  İş akışı karmaşıklığını simüle etmek için yorum etkinliklerinin sayısı değiştirilir.  Yorum etkinliği, hiçbir iş gerçekleştirmeden wf3'e <xref:System.Workflow.Activities.CodeActivity> eşdeğerdir. Yorum etkinliği hakkında daha fazla bilgi için, bu makalenin daha önceki "Bileşen Düzeyinde Performans Karşılaştırması" bölümüne bakın.

##### <a name="test-results"></a>Test Sonuçları

 WCF iş akışı hizmetleri için soğuk ve sıcak gecikme:

 ![WF3 ve WF4 kullanarak WCF iş akışı hizmetleri için soğuk ve sıcak gecikmeyi gösteren sütun grafiği](./media/performance/latency-results-graph.gif)

 Önceki grafikte, soğuk, verilen iş akışı için <xref:System.ServiceModel.WorkflowServiceHost> varolan bir durum olmadığı durumu ifade eder.  Başka bir deyişle, soğuk gecikme iş akışının ilk kez kullanılması ve XOML veya XAML'nin derlenmesine ihtiyaç olduğu zamandır.  Sıcak gecikme süresi, iş akışı türü zaten derlenmişken yeni bir iş akışı örneği oluşturma zamanıdır.  İş akışının karmaşıklığı WF4 durumunda çok az fark yaratır, ancak WF3 durumunda doğrusal bir ilerleme vardır.

#### <a name="correlation-throughput"></a>Korelasyon İşi
 WF4 yeni bir içerik tabanlı korelasyon özelliği sunar.  WF3 yalnızca bağlam tabanlı korelasyon sağladı.  Bağlam tabanlı korelasyon yalnızca belirli WCF kanal bağlamaları üzerinden yapılabilir.  İş akışı Kimliği, bu bağlamaları kullanırken ileti üstbilgisine eklenir.  WF3 çalışma süresi yalnızca kimliğiyle bir iş akışını tanımlayabilir.  İçerik tabanlı korelasyonla, iş akışı yazarı hesap numarası veya müşteri Kimliği gibi ilgili bir veri parçasının korelasyon anahtarıoluşturabilir.

 Bağlam tabanlı korelasyon, bağıntı anahtarının ileti üstbilgisinde bulunması açısından bir performans avantajına sahiptir.  Anahtar, seri dışılaştırma/ileti kopyalama olmadan iletiden okunabilir.  İçerik tabanlı korelasyonda, korelasyon anahtarı ileti gövdesinde depolanır.  Anahtarı bulmak için xpath ifadesi kullanılır.  Bu ek işlemin maliyeti iletinin boyutuna, gövdedeki anahtarın derinliğine ve anahtar sayısına bağlıdır.  Bu test bağlam ve içerik tabanlı korelasyon karşılaştırır ve aynı zamanda birden çok anahtar kullanırken performans bozulması gösterir.

#### <a name="environment-setup"></a>Ortamı Ayarlama
![İş akışı performans testi için ortam kurulumu](./media/performance/performance-test-environment.gif)

#### <a name="test-setup"></a>Test Kurulumu
![Korelasyon İş Akışı Testi](./media/performance/correlation-throughput-workflow.gif "Korelasyon iş akışı testi kurulumu")

 Önceki iş akışı [Kalıcılık](#persistence) bölümünde kullanılanla aynıdır. Kalıcılık olmadan korelasyon testleri için, çalışma zamanında yüklü hiçbir kalıcılık sağlayıcısı yoktur. Korelasyon iki yerde gerçekleşir: CreateOrder ve CompleteOrder.

#### <a name="test-results"></a>Test Sonuçları
![Korelasyon İşi](./media/performance/correlation-throughput-graph.gif "Korelasyon iş girdisi grafiği")

 Bu grafik, içerik tabanlı korelasyonda kullanılan anahtar sayısı arttıkça performansta bir düşüş gösterir.  TCP ve HTTP arasındaki eğrilerde benzerlik, bu protokollerle ilişkili ek yükü gösterir.

#### <a name="correlation-with-persistence"></a>Kalıcılık ile Korelasyon
 Kalıcı bir iş akışıyla, içerik tabanlı korelasyondan CPU basıncı iş akışı çalışma zamanından SQL veritabanına geçer.  SQL kalıcılık sağlayıcısında depolanan yordamlar, uygun iş akışını bulmak için anahtarları eşleştirme işini yapar.

 ![Korelasyon ve kalıcılık sonuçlarını gösteren çizgi grafiği](./media/performance/correlation-persistence-graph.gif)

 Bağlam tabanlı korelasyon hala içerik tabanlı korelasyon daha hızlıdır.  Ancak, kalıcılık korelasyon daha performans üzerinde daha fazla etkisi olduğu gibi fark daha az belirgindir.

### <a name="complex-workflow-throughput"></a>Karmaşık İş Akışı İş Akışı
 İş akışının karmaşıklığı yalnızca etkinlik sayısıyla ölçülmez.  Kompozit aktiviteler birçok çocuk içerebilir ve bu çocuklar da kompozit aktiviteler olabilir.  İç içe geçme düzeylerinin sayısı arttıkça, şu anda yürütme durumunda olabilecek etkinlik sayısı ve durum içinde olabilecek değişken lerin sayısı da artar.  Bu test, karmaşık iş akışları çalıştırırken WF3 ve WF4 arasındaki iş akışını karşılaştırır.

### <a name="test-setup"></a>Test Kurulumu
 Bu testler Windows Server 2008 x64 çalıştıran 4GB RAM ile bir Intel Xeon X5355 @ 2.66GHz 4 yönlü bilgisayarda yürütülmüştür.  Test kodu, %100 CPU kullanımına ulaşmak için çekirdek başına tek bir iş parçacığı yla tek bir işlemde çalışır.

 Bu test için oluşturulan iş akışlarıiki ana değişkene sahiptir: her dizideki etkinlik derinliği ve sayısı.  Her derinlik düzeyi paralel bir etkinlik içerirken döngü, kararlar, atamalar ve diziler.  Aşağıda resimde bulunan WF4 tasarımcısında, üst düzey akış grafiği resmedilmiştir.  Her akış şeması aktivitesi ana akış şemasına benzer.  Derinliğitest parametreleri ile sınırlı olduğu bu iş akışını hayal ederken bir fraktal düşünmek yararlı olabilir.

 Belirli bir testteki etkinlik sayısı, dizi başına etkinlik derinliği ve sayısına göre belirlenir.  Aşağıdaki denklem WF4 testindeki etkinlik sayısını hesaplar:

 ![İşlem sayısını hesaplamak için denklem](./media/performance/number-activities-equation.gif)

 WF3 testinin etkinlik sayısı, ekstra bir dizi nedeniyle biraz daha farklı bir denklemle hesaplanabilir:

 ![WF3 etkinliklerinin hesaplama numarasını hesaplamak için denklem](./media/performance/wf3-number-activities-equation.gif)

 D'nin derinliği ve a olduğu yer, dizi başına etkinlik sayısıdır.  Bu denklemlerin arkasındaki mantık, a ile çarpılarak ilk sabitin dizi sayısı, ikinci sabitin ise geçerli düzeydeki statik etkinlik sayısı olmasıdır.  Her akış şemasında üç akış şeması çocuk aktivitesi vardır.  Alt derinlik düzeyinde, bu akış şemaları boşama diğer düzeylerde ana akış şemasının kopyalarıdır.  Her test varyasyonunun iş akışı tanımındaki etkinlik sayısı aşağıdaki tabloda gösterilir:

 ![Her testte kullanılan etkinlik sayısını gösteren bir tablo](./media/performance/workflow-variation-compare-table.gif)

 İş akışı tanımındaki etkinlik sayısı her derinlik düzeyiyle keskin bir şekilde artar.  Ancak, belirli bir iş akışı örneğinde karar noktası başına yalnızca bir yol yürütülür, bu nedenle gerçek etkinliklerin yalnızca küçük bir alt kümesi yürütülür.

 ![Karmaşık iş akışının akış şeması](./media/performance/complex-workflow-throughput-workflow.gif)

 WF3 için eşdeğer bir iş akışı oluşturuldu. WF3 tasarımcısı iç içe geçme yerine tasarım alanındaki tüm iş akışını gösterir, bu nedenle bu konuda görüntülenemeyecek kadar büyüktür. İş akışının bir bölümü aşağıda gösterilmiştir.

 ![WF3 iş akışının akış şeması](./media/performance/wf3-workflow-snippet.gif)

 Aşırı bir durumda iç içe geçme alıştırması yapmak için, bu testin bir parçası olan başka bir iş akışı 100 iç içe dizi kullanır.  En içteki sırada tek `Comment` <xref:System.Workflow.Activities.CodeActivity>veya .

 ![İç içe bir dizinin akış şeması](./media/performance/nested-sequence-workflow.gif)

 İzleme ve kalıcılık bu testin bir parçası olarak kullanılmaz.

### <a name="test-results"></a>Test Sonuçları
 ![İş sonu performansı sonuçlarını gösteren sütun grafiği](./media/performance/throughput-performance-results.gif)

 Çok sayıda derinliğe ve çok sayıda aktiviteye sahip karmaşık iş akışlarına rağmen, performans sonuçları bu makalede daha önce gösterilen diğer iş akışı numaralarıyla tutarlıdır.  WF4'ün iş letimatları daha hızlı büyüklüktedir ve logaritmik ölçekte karşılaştırılmalıdır.

### <a name="memory"></a>Bellek
 Windows İş Akışı Temeli'nin bellek yükü iki temel alanda ölçülür: iş akışı karmaşıklığı ve iş akışı tanımlarının sayısı.  Windows 7 64 bit iş istasyonunda bellek ölçümleri yapıldı.  Performans sayaçlarını izleme, Environment.WorkingSet yoklama veya VMMap gibi bir aracı [VMMap'ten](/sysinternals/downloads/vmmap)temin edilebilen bir araç kullanma gibi çalışma kümesi boyutunun ölçümünü elde etmenin birçok yolu vardır. Her testin sonuçlarını elde etmek ve doğrulamak için bir yöntem kombinasyonu kullanıldı.

### <a name="workflow-complexity-test"></a>İş Akışı Karmaşıklığı Testi
 İş akışı karmaşıklığı testi, iş akışının karmaşıklığına bağlı olarak çalışma kümesi farkını ölçer.  Önceki bölümde kullanılan karmaşık iş akışlarına ek olarak, iki temel servis örneğini kapsayacak şekilde yeni varyasyonlar eklenir: tek bir etkinlik iş akışı ve 1000 aktiviteiçeren bir dizi.  Bu testler için iş akışları baş harfe getirilir ve bir dakika süreyle tek bir seri döngüiçinde tamamlanmak üzere çalıştırılır.  Her test varyasyonu üç kez çalıştırılır ve kaydedilen veriler bu üç çalıştırmanın ortalamasıdır.

 İki yeni temel test, aşağıda gösterilengibi görünen iş akışlarına sahiptir:

 ![Hem WF3 hem de WF4 için karmaşık iş akışı](./media/performance/complex-workflow-wf3-wf4.gif)

 Yukarıda gösterilen WF3 iş akışında boş <xref:System.Workflow.Activities.CodeActivity> etkinlikler kullanılır.  Yukarıdaki WF4 iş `Comment` akışı etkinlikleri kullanır.  Etkinlik, `Comment` bu makalenin daha önceki Bileşen düzeyinde performans karşılaştırmaları bölümünde açıklanmıştır.

 ![WF3 ve WF4 iş akışları için karmaşık iş akışı bellek kullanımını gösteren sütun grafiği](./media/performance/complex-memory-usage-wf3-wf4.gif)

 Bu grafikte dikkat edilebilen açık eğilimlerden biri, iç içe geçmenin hem WF3 hem de WF4'te bellek kullanımı üzerinde nispeten en az etkiye sahip olmasıdır.  En önemli bellek etkisi, belirli bir iş akışındaki etkinlik sayısından gelir.  1000 dizisi, karmaşık derinlik 5 sıra 5 ve karmaşık derinlik 7 sıra 1 varyasyonları verileri göz önüne alındığında, etkinlik sayısı binlerce girdikçe, bellek kullanım artışı daha belirgin hale olduğu açıktır.  ~29K aktivitelerinin olduğu aşırı durumda (derinlik 7 sıra 1), WF4 WF3'e göre neredeyse %79 daha az bellek kullanır.

### <a name="multiple-workflow-definitions-test"></a>Çoklu İş Akışı Tanımları Testi
 WF3 ve WF4'te iş akışlarını barındırmak için kullanılabilir seçenekler nedeniyle iş akışı başına bellek ölçümü iki farklı sına ayrılır.  Testler, belirli bir iş akışının örnekli olması ve tanım başına yalnızca bir kez yürütülmesinde iş akışı karmaşıklığı testinden farklı bir şekilde çalıştırılır.  Bunun nedeni, iş akışı tanımının ve ana bilgisayar ının AppDomain'in ömrü boyunca bellekte kalmasıdır.  Belirli bir iş akışı örneğini çalıştırarak kullanılan bellek çöp toplama sırasında temizlenmelidir.  WF4 için geçiş kılavuzu barındırma seçenekleri hakkında daha ayrıntılı bilgi içerir. Daha fazla bilgi için [WF Migration Cookbook: Workflow Hosting'e](migration-guidance.md)bakın.

 İş akışı tanımı sınaması için birçok iş akışı tanımı oluşturma çeşitli şekillerde yapılabilir.  Örneğin, ad dışında aynı olan 1000 iş akışı kümesi oluşturmak ve bu iş akışlarının her birini ayrı dosyalara kaydetmek için kod oluşturma kullanabilirsiniz.  Bu yaklaşım konsol tarafından barındırılan test için alınmıştır.  WF3'te, <xref:System.Workflow.Runtime.WorkflowRuntime> sınıf iş akışı tanımlarını çalıştırmak için kullanıldı.  WF4, tek <xref:System.Activities.WorkflowApplication> bir iş akışı örneği oluşturmak <xref:System.Activities.WorkflowInvoker> için veya etkinliği bir yöntem çağrısıymış gibi çalıştırmak için doğrudan kullanabilir.  <xref:System.Activities.WorkflowApplication>tek bir iş akışı örneğinin ana bilgisayarıdır <xref:System.Workflow.Runtime.WorkflowRuntime> ve bu testte kullanılan bu nedenle daha yakın özellik paritesi vardır.

 IIS'de iş akışlarını barındırırken, <xref:System.Web.Hosting.VirtualPathProvider> xamlx veya XOML dosyalarının tümünün oluşturulması yerine yeni <xref:System.ServiceModel.WorkflowServiceHost> bir iş oluşturmak için bir kullanmak mümkündür.  Gelen <xref:System.Web.Hosting.VirtualPathProvider> isteği işler ve veritabanından yüklenebilen veya bu durumda anında oluşturulan bir "sanal dosya" ile yanıt verir.  Bu nedenle 1000 fiziksel dosya oluşturmak gereksizdir.

 Konsol testinde kullanılan iş akışı tanımları, tek bir etkinlikiçeren basit sıralı iş akışlarıydı.  Tek etkinlik WF3 durumda için boş <xref:System.Workflow.Activities.CodeActivity> `Comment` ve WF4 durumda için bir etkinlik oldu.  IIS tarafından barındırılan servis talebi, ileti almaya başlayan ve yanıt göndermeye son veren iş akışlarını kullandı:

Aşağıdaki resimde ReceiveActivity içeren bir WF3 iş akışı ve istek/yanıt deseni içeren bir WF4 iş akışı gösterilmektedir:

 ![WF3 ve WF4'te İş Akışı Hizmetleri](./media/performance/workflow-receive-activity.gif)

 Aşağıdaki tablo, tek bir iş akışı tanımı ve 1001 tanımları arasında çalışma kümesinde delta gösterir:

|Hosting Seçenekleri|WF3 Çalışma Seti Delta|WF4 Çalışma Seti Delta|
|---------------------|---------------------------|---------------------------|
|Konsol Uygulaması Barındırılan İş Akışları|18 MB|9 MB|
|IIS Hosted İş Akışı Hizmetleri|446 MB|364 MB|

 IIS'de iş akışı tanımlarını <xref:System.ServiceModel.WorkflowServiceHost>barındırmak, ayrıntılı WCF hizmet yapıları ve ana bilgisayarla ilişkili ileti işleme mantığı nedeniyle çok daha fazla bellek tüketir.

 WF3 konsol barındırma için iş akışları XOML yerine kod uygulanmıştır.  WF4'te varsayılan değer XAML kullanmaktır.  XAML, derlemede gömülü bir kaynak olarak depolanır ve iş akışının uygulanmasını sağlamak için çalışma zamanı derlenir.  Bu işlemle ilişkili bazı genel merkezler vardır.  WF3 ve WF4 arasında adil bir karşılaştırma yapmak için XAML yerine kodlanmış iş akışları kullanılmıştır.  WF4 iş akışlarından birine bir örnek aşağıda gösterilmiştir:

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

 Bellek tüketimini etkileyebilecek birçok faktör vardır. Yönetilen tüm programlar için aynı tavsiye hala geçerlidir.  IIS tarafından barındırılan <xref:System.ServiceModel.WorkflowServiceHost> ortamlarda, iş akışı tanımı için oluşturulan nesne, uygulama havuzu geri dönüştürülene kadar bellekte kalır.  Uzantıları yazarken bu akılda tutulmalıdır.  Ayrıca, "genel" değişkenlerden (tüm iş akışına göre kapsamlı değişkenler) kaçınmak ve değişkenlerin kapsamını mümkün olan her yerde sınırlamak en iyisidir.

## <a name="workflow-runtime-services"></a>İş Akışı Runtime Hizmetleri

### <a name="persistence"></a>Kalıcılık
 WF3 ve WF4 her iki gemi bir SQL kalıcılık sağlayıcısı ile.  WF3 SQL kalıcılık sağlayıcısı, iş akışı örneğini seri hale getiren ve bir blob'da depolayan basit bir uygulamadır.  Bu nedenle, bu sağlayıcının performansı büyük ölçüde iş akışı örneğinin boyutuna bağlıdır.  WF3'te, bu makalede daha önce de ele alındığı gibi, örnek boyutu birçok nedenden dolayı artabilir.  Bir veritabanında serileştirilmiş bir örneği depolamak iş akışının durumuna görünürlük vermediğinden, birçok müşteri varsayılan SQL kalıcılığı sağlayıcısını kullanmamayı tercih eder.  İş akışı kimliğini bilmeden belirli bir iş akışını bulmak için, kalıcı her örneği deserialize etmek ve içeriğini incelemek gerekir.  Birçok geliştirici bu engeli aşmak için kendi kalıcılık sağlayıcıları yazmayı tercih.

 WF4 SQL kalıcılık sağlayıcısı bu endişelerin bazılarını gidermeye çalışmıştır.  Kalıcılık tabloları, etkin yer imleri ve tanıtılabilir özellikler gibi belirli bilgileri ortaya çıkarır.  WF4'teki yeni içerik tabanlı korelasyon özelliği, kalıcı iş akışı örneğinin organizasyonunda bazı değişikliklere yol açan WF3 SQL kalıcılık yaklaşımını kullanarak iyi performans gösteremez.  Bu kalıcılık sağlayıcının iş daha karmaşık hale getirir ve veritabanı üzerinde ekstra stres koyar.

### <a name="environment-setup"></a>Ortamı Ayarlama
![İş akışı performans testi için ortam kurulumu](./media/performance/performance-test-environment.gif)

### <a name="test-setup"></a>Test Kurulumu
 Geliştirilmiş bir özellik kümesi ve daha iyi eşzamanlılık işleme ile bile, WF4'teki SQL kalıcılık sağlayıcısı WF3'teki sağlayıcıdan daha hızlıdır.  Bunu göstermek için, WF3 ve WF4'te temelde aynı işlemleri gerçekleştiren iki iş akışı aşağıda karşılaştırılabır.

 ![Solda WF3'te, sağda WF4'te kalıcılık iş akışı](./media/performance/persist-workflow-wf3-wf4.gif)

 İki iş akışı da alınan bir ileti tarafından oluşturulur.  İlk yanıt gönderdikten sonra, iş akışı devam eder.  WF3 durumunda, kalıcılığı <xref:System.Workflow.ComponentModel.TransactionScopeActivity> başlatmak için boş bir boş kullanılır.  Aynı şey WF3'te bir etkinliği "yakına devam" olarak işaretleyerek elde edilebilir.  İkinci, ilişkili ileti iş akışını tamamlar.  İş akışları kalıcıdır, ancak boşaltılmaz.

### <a name="test-results"></a>Test Sonuçları
 ![Elde girdi kalıcılığını gösteren sütun grafiği](./media/performance/throughput-persistence-graph.gif)

 İstemci ve orta katman arasındaki aktarım HTTP olduğunda, WF4'teki kalıcılık 2,6 kat lık bir iyileşme gösterir.  TCP taşıma bu faktörü 3,0 kata yükseltir.  Her durumda, orta katmandaki CPU kullanımı %98 veya daha yüksektir.  WF4 iş akışının daha büyük olmasının nedeni daha hızlı iş akışı çalışma süresidir.  Serileştirilmiş örneğin boyutu her iki durumda da düşüktür ve bu durumda önemli bir katkıda bulunan öğe değildir.

 Bu testteki Hem WF3 hem de WF4 iş akışları, kalıcılığın ne zaman gerçekleşmesi gerektiğini açıkça belirtmek için bir etkinlik kullanır.  Bu, iş akışını boşaltmadan kalıcı hale alma nın avantajına sahiptir.  WF3'te, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> özelliği kullanarak devam etmek de mümkündür, ancak bu iş akışı örneğini bellekten boşaltır.  WF3 kullanan bir geliştirici iş akışının belirli noktalarda devam etmesini sağlamak istiyorsa, iş akışı tanımını değiştirmesi veya iş akışı örneğini boşaltma ve yeniden yükleme maliyetini ödemesi gerekir.  WF4'teki yeni bir özellik, boşaltmadan <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>devam etmeyi mümkün kılar: .  Bu özellik, iş akışı örneğinin boşta kalmasını, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> ancak eşik karşılanana veya yürütmeye devam edilene kadar bellekte kalmasını sağlar.

 WF4 SQL kalıcılık sağlayıcısının veritabanı katmanında daha fazla iş gerçekleştirdiğini unutmayın.  ORADA CPU ve disk kullanımını izlemek önemlidir bu yüzden SQL veritabanı bir darboğaz haline gelebilir.  Performans testi iş akışı uygulamaları sırasında SQL veritabanından aşağıdaki performans sayaçlarını eklediğinizden emin olun:

- PhysicalDisk\\%Disk Okuma Süresi

- PhysicalDisk\\% Disk Süresi

- PhysicalDisk\\% Disk Yazma Süresi

- PhysicalDisk\\% Avg. Disk Sıra Uzunluğu

- PhysicalDisk\Avg. Disk Okuma Sırası Uzunluğu

- PhysicalDisk\Avg. Disk Yazma Sıra Uzunluğu

- PhysicalDisk\Geçerli Disk Sıra Uzunluğu

- İşlemci\\Bilgileri % İşlemci Süresi

- SQLServer:Mandal\Ortalama Mandal Bekleme Süresi (ms)

- SQLServer:Mandal\Mandal Bekler/sn

### <a name="tracking"></a>İzleme
 İş akışı izleme, bir iş akışının ilerlemesini izlemek için kullanılabilir.  İzleme olaylarında yer alan bilgiler bir izleme profili tarafından belirlenir.  İzleme profili ne kadar karmaşıksa, izleme de o kadar pahalı hale gelir.

 WF3, SQL tabanlı bir izleme hizmetiyle gönderilir.  Bu hizmet toplu ve toplu olmayan modlarda çalışabilir.  Toplu olmayan modda, izleme olayları doğrudan veritabanına yazılır.  Toplu modda, izleme olayları iş akışı örneği durumuyla aynı toplu iş partisinde toplanır.  Toplu mod, en geniş iş akışı tasarımları için en iyi performansa sahiptir.  Ancak, iş akışı devam etmeden birçok etkinlik çalıştırırsa ve bu etkinlikler izlenirse, toplu iş işlemi olumsuz bir performans etkisi ne olabilir.  Bu genellikle döngüler halinde olur ve bu senaryoyu önlemek için en iyi yolu bir kalıcılık noktası içerecek şekilde büyük döngüler tasarlamaktır.  Bir döngüye kalıcılık noktası nın getirilmesi performansı olumsuz yönde etkileyebilir, bu nedenle her birinin maliyetlerini ölçmek ve bir denge bulmak önemlidir.

 WF4 bir SQL izleme hizmeti ile sevk edilmez.  İzleme bilgilerini bir SQL veritabanına kaydetme,.NET Framework'de yerleşik yerine bir uygulama sunucusundan daha iyi işlenebilir. Bu nedenle SQL izleme artık AppFabric tarafından işlenir.  WF4'teki kutudan çıkma izleme sağlayıcısı, Windows için Olay İzleme'yi (ETW) temel alıyor.

 ETW, Windows'da yerleşik çekirdek düzeyinde, düşük gecikmeli bir olay sistemidir.  Bu mümkün sadece aslında bir tüketici olduğunda olay izleme için ceza tabi kılan bir sağlayıcı / tüketici modeli kullanır.  İşlemci, disk, bellek ve ağ kullanımı gibi çekirdek olaylarına ek olarak, birçok uygulama ETW'den de yararlanır.  ETW olayları, uygulamalara göre özelleştirilebilen performans sayaçlarından daha güçlüdür.  Olay, iş akışı kimliği veya bilgi iletisi gibi metin içerebilir.  Ayrıca, olaylar bit maskeleriyle sınıflandırılır, böylece belirli bir olay alt kümesini tüketmek tüm olayları yakalamaktan daha az performans etkisine sahip olur.

 SQL yerine izleme için ETW kullanma yaklaşımının yararları şunlardır:

- İzleme olaylarının toplanması başka bir işleme ayrılabilir.  Bu, olayların nasıl kaydedildiği konusunda daha fazla esneklik sağlar.

- ETW izleme olayları, WCF ETW olayları veya SQL Server veya çekirdek sağlayıcısı gibi diğer ETW sağlayıcılarıyla kolayca birleştirilir.

- İş akışı yazarlarının, WF3 SQL izleme hizmetinin toplu iş modu gibi belirli bir izleme uygulamasıyla daha iyi çalışması için iş akışını değiştirmeleri gerekmez.

- Yönetici, ana bilgisayar işlemini geri dönüştürmeden izlemeyi açabilir veya kapatabilir.

 ETW izleme için performans yararları bir dezavantajı ile birlikte gelir.  Sistem yoğun kaynak baskısı altındaysa ETW olayları kaybedilebilir.  Olayların işlenmesi normal program yürütmesini engellemek için değildir ve bu nedenle tüm ETW olaylarının abonelerine yayınlanacağı garanti edilmez.  Bu, ETW izleme sağlık izleme için büyük yapar ama denetim için uygun değil.

 WF4'ün bir SQL izleme sağlayıcısı olmasa da, AppFabric'in yoktur.  AppFabric'in SQL izleme yaklaşımı, olayları toplu hale getiren ve bunları hızlı ekler için tasarlanmış bir SQL tablosuna yazan bir Windows Hizmeti ile ETW olaylarına abone olmaktır.  Ayrı bir iş, bu tablodaki verileri boşaltıyor ve AppFabric panosunda görüntülenebilen raporlama tablolarına dönüştürüyor.  Bu, bir dizi izleme olayının geldiği iş akışından bağımsız olarak işlendiği ve bu nedenle kaydedilmeden önce kalıcıbir noktayı beklemesi gerekmediği anlamına gelir.

 ETW olayları logman veya xperf gibi araçlarla kaydedilebilir.  Kompakt ETL dosyası xperfview gibi bir araçla görüntülenebilir veya tracerpt ile XML gibi daha okunabilir bir biçime dönüştürülebilir.  WF3'te, SQL veritabanı olmadan olayları izlemenin tek seçeneği özel bir izleme hizmeti oluşturmaktır. ETW hakkında daha fazla bilgi için [WCF Hizmetleri ve Windows ve Olay](../wcf/samples/wcf-services-and-event-tracing-for-windows.md) İzleme - Windows uygulamaları için [Olay](/windows/desktop/etw/event-tracing-portal)İzleme'ye bakın.

 İş akışı izlemeyi etkinleştirmek performansı farklı derecelerde etkiler.  Aşağıdaki kıyaslama, ETW izleme olaylarını tüketmek ve bunları bir ETL dosyasına kaydetmek için logman aracını kullanır.  AppFabric'teki SQL izleme maliyeti bu makalenin kapsamında değildir.  AppFabric'te de kullanılan temel izleme profili bu kıyaslamada gösterilir.  Ayrıca sadece sağlık izleme olayları izleme maliyeti dahildir.  Bu olaylar, sorun giderme ve sistemin ortalama iş ortasını belirlemek için yararlıdır.

### <a name="environment-setup"></a>Ortamı Ayarlama
 ![İş akışı performans testi için ortam kurulumu](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Test Sonuçları

 ![İş akışı izleme maliyetlerini gösteren sütun grafiği](./media/performance/workflow-tracking-costs.gif)

 Sağlık izleme nin iş artışı üzerinde kabaca %3'lük bir etkisi vardır.  Temel profilin maliyeti %8 civarındadır.

## <a name="interop"></a>Interop
 WF4 neredeyse tam bir [!INCLUDE[wf1](../../../includes/wf1-md.md)] yeniden yazmak ve bu nedenle WF3 iş akışları ve faaliyetleri doğrudan WF4 ile uyumlu değildir.  Windows İş Akışı Temeli'ni erken benimseyen birçok müşteri, WF3 için şirket içi veya üçüncü taraf iş akışı tanımlarına ve özel etkinliklere sahip olur.  WF4'e geçişi kolaylaştıran yollardan biri, WF4 iş akışı içinden WF3 etkinliklerini yürütebilen Interop etkinliğini kullanmaktır.  <xref:System.Activities.Statements.Interop> Etkinliğin yalnızca gerektiğinde kullanılması önerilir. WF4'e geçiş hakkında daha fazla bilgi için [WF4 Geçiş Kılavuzu'na](migration-guidance.md)göz atın.

### <a name="environment-setup"></a>Ortamı Ayarlama
 ![İş akışı performans testi için ortam kurulumu](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Test Sonuçları

Aşağıdaki tablo, çeşitli yapılandırmalarda sırayla beş etkinlik içeren bir iş akışını çalıştırmanın sonuçlarını gösterir.

|Test|İş akışı (iş akışları/sn)|
|----------|-----------------------------------|
|WF3 çalışma zamanında WF3 Sırası|1,576|
|WF3 Sequence in WF4 çalışma zamanında Interop kullanarak|2,745|
|WF4 Dizisi|153,582|

 Düz WF3 üzerinde Interop kullanarak önemli bir performans artışı vardır.  Ancak, WF4 faaliyetleri ile karşılaştırıldığında, artış ihmal edilebilir.

## <a name="summary"></a>Özet
 WF4 için performans ağır yatırımlar birçok önemli alanlarda ödedi.  Bireysel iş akışı bileşen performansı, wf4'te bazı durumlarda daha yalın [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma süresi nedeniyle WF3'e göre yüzlerce kat daha hızlıdır.  Gecikme sayıları da önemli ölçüde daha iyidir.  Bu el kodlama WCF orkestrasyon hizmetleri aksine kullanmak [!INCLUDE[wf1](../../../includes/wf1-md.md)] için performans cezası kullanarak [!INCLUDE[wf1](../../../includes/wf1-md.md)]ek yararları dikkate alınarak çok küçük olduğu anlamına gelir.  Kalıcılık performansı 2,5 - 3,0 faktörüyle artmıştır.  İş akışı izleme yoluyla sistem durumu izleme nin artık çok az yükü vardır.  WF3'ten WF4'e taşınmayı düşünenler için kapsamlı bir geçiş kılavuzu kümesi mevcuttur.  Tüm bu WF4 karmaşık uygulamalar yazmak için cazip bir seçenek yapmalıdır.
