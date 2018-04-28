---
title: Windows Workflow Foundation 4 performansı
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b34a0118c9223e8d09bf56de39e3fea1b115688f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="windows-workflow-foundation-4-performance"></a>Windows Workflow Foundation 4 performansı
Dustin Metzgar  
  
 Wenlong Dong  
  
 Microsoft Corporation ' ın Eylül 2010  
  
 Microsoft [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] büyük düzeltme ağır Yatırımlar ile Windows Workflow Foundation (WF), performans içerir.  Bu yeni bir düzeltme önemli tasarım değişiklikleri önceki sürümlerinden tanıtır [!INCLUDE[wf1](../../../includes/wf1-md.md)] .NET Framework 3.0 bir parçası olarak gönderilen ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Programlama modeli, çalışma zamanı ve performansını ve kullanılabilirliğini önemli ölçüde artırmak için araç çekirdek yeniden tasarlanmış olmuştur. Bu konu, bu düzeltmeleri önemli performans özelliklerini gösterir ve bu önceki sürüm karşı karşılaştırır.  
  
 Büyüklük WF3 WF4 arasındaki tarafından ayrı ayrı iş akışı bileşen performansı artar.  Bu, elle kodlanmış arasında boşluk bırakır [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmetleri ve [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] oldukça küçük olacak şekilde iş akışı hizmetleri.  İş akışı gecikme süresi içinde WF4 önemli ölçüde düşürdü.  2.5-3.0 faktörüyle Kalıcılık performans artar.  İş akışı izleme yoluyla sistem durumu izleme önemli ölçüde daha az yüke sahiptir.  Bu, geçiş veya WF4 uygulamalarınızda benimsemek için nedenleri çekici.  
  
## <a name="terminology"></a>Terminoloji  
 Sürümü [!INCLUDE[wf1](../../../includes/wf1-md.md)] sunulan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] için bu konunun geri kalanı için WF4 anılacaktır.  [!INCLUDE[wf1](../../../includes/wf1-md.md)] .NET 3.0 sunulmuştur ve birkaç küçük düzeltmeden vardı [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] SP1. [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Workflow Foundation sürümü bulunulabilir için WF3 bu konunun geri kalanı için. WF3 gönderildiği [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] yana birimi WF4 ile. [!INCLUDE[crabout](../../../includes/crabout-md.md)] WF4 geçirme WF3 yapılara bkz: [Windows Workflow Foundation 4 Geçiş Kılavuzu](http://go.microsoft.com/fwlink/?LinkID=153313)  
  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmet odaklı uygulamalar oluşturmak için Microsoft'un programlama modelidir. İlk .net 3.0 WF3 birlikte bir parçası olarak sunulmuştur ve şimdi anahtar bileşenlerinden biri olan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Windows Server AppFabric oluşturulmasını, ölçeklenmesini ve Web ve IIS'de çalışan bileşik uygulamaları yönetmek kolaylaştıran bir tümleşik teknoloji kümesidir. İzleme ve Hizmetleri ve iş akışlarını yönetmek için araçlar sağlar. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Windows Server AppFabric](http://msdn.microsoft.com/windowsserver/ee695849.aspx)  
  
## <a name="goals"></a>Hedefleri  
 Bu konuda farklı senaryolar için ölçülen verilerle WF4 performans özelliklerini göstermek için hedefidir. Ayrıca WF4 WF3 arasındaki ayrıntılı karşılaştırmaları sağlar ve böylece bu yeni düzeltmede yapılan harika geliştirmeleri gösterir. Senaryolar ve bu makalede sunulan veri WF4 ve WF3 farklı yönlerini temel maliyetini ölçme. Bu veriler WF4 performans özelliklerini anlamak yararlı olur ve WF4 WF3 kümesinden planlama veya uygulama geliştirme WF4 kullanılarak yararlı olabilir. Ancak, bu makaledeki sunulan verilerden çizilmiş sonuçları dikkatli olunmalıdır. Yüksek oranda bağımlı iş akışının nasıl uygulandığını ve farklı bir bileşik iş akışı uygulamanın performansını bileşenleri ile tümleştirilmiştir. Bir uygulama performans özelliklerini belirlemek için her bir uygulama ölçmek gerekir.  
  
## <a name="overview-of-wf4-performance-enhancements"></a>WF4 performans geliştirmeleri genel bakış  
 WF4 dikkatli bir şekilde tasarlanmış ve yüksek performans ve aşağıdaki bölümlerde açıklanan ölçeklenebilirlik ile uygulanmıştır.  
  
### <a name="wf-runtime"></a>WF çalışma zamanı  
 En [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanı olan bir iş akışında etkinliklerin yürütülmesini sürücüleri zaman uyumsuz bir zamanlayıcı. Bu kullanıcı, etkinlikler için öngörülebilir yürütme ortamı sağlar. Ortam iyi tanımlanmış bir sözleşme yürütme, devamlılık, tamamlama, iptal, özel durumlar ve tahmin edilebilir bir iş parçacığı modeli vardır.  
  
 WF3 kıyasla daha verimli bir zamanlayıcı WF4 çalışma zamanı yok. İçin kullanılan g/ç iş parçacığı havuzu yararlanır [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], iş öğelerini toplu yürütme en çok verimli olduğu. İç iş öğesi Zamanlayıcı sıranın en yaygın kullanım desenlerini için optimize edilmiştir. WF4 çalışma zamanı en az eşitleme ve olay ağır olay kaydı ve karmaşık eşitleme için durumu geçişleri gerçekleştirmek için çağrısının WF3 bağlıdır sırada mantığı, işleme sahip çok hafif şekilde yürütme durumları da yönetir.  
  
### <a name="data-storage-and-flow"></a>Veri depolama ve akış  
 WF3 içinde bir etkinlikle ilişkili veri türü tarafından uygulanan bağımlılık özellikleri aracılığıyla modellenir <xref:System.Windows.DependencyProperty>. Bağımlılık özelliği düzeni, Windows Presentation Foundation (WPF) sunulmuştur. Genel olarak, bu deseni kolay veri bağlama ve diğer kullanıcı Arabirimi özelliklerini desteklemek için çok esnektir. Ancak, düzeni iş akışı tanımı statik alanlar olarak tanımlanması için özellikleri gerektirir. Her [!INCLUDE[wf1](../../../includes/wf1-md.md)] özellik değerlerini alır veya ayarlar çalışma zamanı, son derece ağırlıklı arama mantığı içerir.  
  
 WF4 mantığı kapsamı Temizle verileri veri akışında nasıl işlendiğini büyük ölçüde artırmak için kullanır. İki farklı kavram kullanarak etkinlik sınırları boyunca akan verilerden bir etkinlikte depolanan verileri ayırır: değişkenleri ve bağımsız değişkenler. Değişkenleri ve "İçinde/çıkış/InOut" bağımsız değişkenler için temizleyin hiyerarşik bir kapsam kullanarak etkinlikler için verileri kullanım karmaşıklığını önemli ölçüde azalır ve veri ömrü da otomatik olarak kapsamlıdır. Etkinlikler değişkenlerinin tarafından açıklanan iyi tanımlanmış bir imzaya sahip. Bir etkinlik inceleyerek almak için bekliyor hangi verilerin ve hangi verilerin tarafından yürütülmesinin sonucu olarak üretilecek belirleyebilirsiniz.  
  
 Bir iş akışı oluşturduğunuzda WF3 etkinlikleri başlatılan. Yalnızca ilgili etkinlikleri yürütülürken WF 4'te etkinlikleri başlatılır. Bu yeni bir iş akışı örneği oluşturulduğunda ve bu nedenle daha fazla verimlilik elde ettiği başlatma/UnInitialize işlemlerini gerçekleştirme olmadan daha basit bir etkinlik yaşam döngüsü sağlar  
  
### <a name="control-flow"></a>Denetim Akışı  
 Herhangi bir programlama dili olduğu gibi yalnızca [!INCLUDE[wf1](../../../includes/wf1-md.md)] döngü, sıralama, dallanma ve diğer desenler için denetim akışı etkinlikleri kümesi tanımlayarak Denetim Akışları iş akışı tanımları için destek sağlar. Aynı etkinlik, yeni bir yeniden yürütülmesi gerektiğinde WF3 içinde <xref:System.Workflow.ComponentModel.ActivityExecutionContext> oluşturulur ve etkinlik dayalı bir ağır seri hale getirme ve seri durumdan çıkarma mantığı üzerinden kopyalanması <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Genellikle performans yinelemeli denetim akışları için etkinlikler dizisini yürütme daha yavaştır.  
  
 WF4 bu oldukça farklı bir şekilde işler. Etkinlik şablonu alır, yeni bir ActivityInstance nesnesi oluşturur ve Zamanlayıcı kuyruğa ekler. Tüm bu işlem yalnızca açık nesne oluşturma içerir ve çok hafif.  
  
### <a name="asynchronous-programming"></a>Zaman uyumsuz programlama  
 Uygulamalar genellikle daha iyi performans ve ölçeklenebilirlik g/ç gibi uzun süren durdurma işlemlerini veya dağıtılmış bilgi işlem işlemleri için zaman uyumsuz programlama ile sahiptir. Temel etkinlik türleri üzerinden zaman uyumsuz desteği sağlar. WF4 <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.AsyncCodeActivity%601>. Çalışma zamanı yerel olarak zaman uyumsuz etkinlikleri anlar ve zaman uyumsuz iş bekleyen olsa da bu nedenle otomatik olarak örnek no-persist bölgesinde koyabilirsiniz. Özel etkinlikler iş akışı Zamanlayıcı iş parçacığı tutan ve paralel olarak çalıştırılabilmesi için hiç etkinlik engelleme olmadan zaman uyumsuz işlemleri gerçekleştirmesi için bu türlerinden türetmesine.  
  
### <a name="messaging"></a>İleti  
 Başlangıçta WF3 çok olan dış olayları veya web üzerinden sınırlı Mesajlaşma Destek Hizmetleri çağrılarını. .NET 3.5, iş akışları olarak uygulanabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcileri veya olarak sunulan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aracılığıyla Hizmetleri <xref:System.Workflow.Activities.SendActivity> ve <xref:System.Workflow.Activities.ReceiveActivity>. WF4 içinde iş akışı tabanlı Mesajlaşma programlama kavramı daha fazla ile sıkı tümleştirme güçlendirilmiş [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] mantığı WF Mesajlaşma.  
  
 Sağlanan birleştirilmiş ileti işleme ardışık düzen [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] .Net 4 önemli ölçüde daha iyi performans ve ölçeklenebilirlik WF3 daha WF4 Hizmetleri yardımcı olur. WF4 karmaşık ileti Exchange desenleri (MEPs) model daha zengin Mesajlaşma programlama desteği de sağlar. Geliştiriciler ya da yazılı Hizmet sözleşmeleri kolay programlama veya seri hale getirme maliyetleri ödeme olmadan daha iyi performans elde etmek için türsüz Hizmet sözleşmeleri elde etmek için kullanabilirsiniz. İstemci tarafı önbelleğe alma desteğini kanal <xref:System.ServiceModel.Activities.SendMessageChannelCache> WF4 sınıfında geliştiricileri en az çaba ile hızlı uygulamalar oluşturmanıza yardımcı olur. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Düzeyler gönderme işlemleri için önbellek paylaşımı değiştirme](../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).  
  
### <a name="declarative-programming"></a>Bildirim temelli programlama  
 WF4 bir temiz ve basit bildirim temelli programlama çerçevesi model iş süreçlerini ve hizmetleri sağlar. Tam bildirim temelli birleşim ile hiçbir kod-iş akışı yazma büyük ölçüde basitleştirir yanında, etkinliklerin programlama modelini destekler. İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], XAML tabanlı bildirim temelli programlama çerçevesini tek derlemeye WPF ve WF desteklemek için System.Xaml.dll birleşik.  
  
 WF4, XAML gerçekten bildirim temelli bir deneyim sağlar ve etkinlikleri ve .NET kullanarak yerleşik türleri başvuran tüm iş akışı tanımı için XML biçimlendirmede tanımlanmasına izin verir. Bu, özel arka plan kodu mantığı karıştırılmaksızın içinde WF3 XOML biçimi ile yapmak zordu. Yeni XAML yığını .net 4'te seri hale getirme/iş akışı yapıları seri durumdan Çıkarmada çok daha iyi performans var ve bildirim temelli programlama daha çekici ve sağlam hale getirin.  
  
### <a name="workflow-designer"></a>İş Akışı Tasarımcısı  
 Tam bildirim temelli programlama desteği WF4 açıkça tasarım sırasında performansı büyük iş akışları için daha yüksek gereksinimleri getirir. İş Akışı Tasarımcısı'nda WF4 WF3 için çok büyük iş akışları için daha iyi ölçeklenebilirlik daha vardır. Bir iş akışı birkaç yüz etkinliklerin WF3 Tasarımcısı ile yüklemek neredeyse imkansız olsa UI sanallaştırma desteği ile Tasarımcı kolayca 1000 etkinliklerin büyük bir iş akışı birkaç saniye içinde yükleyebilirsiniz.  
  
## <a name="component-level-performance-comparisons"></a>Bileşen düzeyinde performans karşılaştırmaları  
 Bu bölümde WF3 ve WF4 iş akışlarında etkinlikler arasında doğrudan karşılaştırmaları verilerini içerir.  Kalıcılık gibi önemli alanlar performans tek tek etkinlikleri Bileşenler'den daha çok büyük bir etkisi vardır.  WF4 bileşenleri tek tek deki performans iyileştirmeleri, ancak bileşenler şimdi orchestration el kodlanmış mantığı karşı Karşılaştırılacak hızlı olduğu için önemlidir.  Bir örneği bir sonraki bölümde ele alınmıştır: "Hizmet birleşim senaryosu."  
  
### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performansı sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
 Yukarıdaki şekilde, bileşen düzeyinde performans ölçümü için kullanılan makine yapılandırmasını gösterir. Tek bir sunucu ve beş istemciler üzerinde bir 1 GB/sn Ethernet ağ arabirim bağlı. Kolay ölçümler için sunucunun Windows Server 2008 x86 çalıştıran bir çift proc/dört çekirdek sunucusunun tek bir çekirdek kullanacak şekilde yapılandırılır. CPU kullanımı sistem yaklaşık % 100 oranında korunur.  
  
### <a name="test-details"></a>Test Ayrıntıları  
 WF3 <xref:System.Workflow.Activities.CodeActivity> büyük olasılıkla WF3 iş akışı içinde kullanılabilecek en basit bir etkinliktir.  Etkinlik, iş akışı programcı özel kod içine koyabilirsiniz arka plan kod içinde bir yöntemi çağırır.  WF4 içinde WF3 için hiçbir doğrudan analog olduğundan <xref:System.Workflow.Activities.CodeActivity> aynı işlevselliği sağlar.  Unutmayın bir <xref:System.Activities.CodeActivity> temel WF3 ilgili olmayan WF4 sınıfında <xref:System.Workflow.Activities.CodeActivity>.  İş akışı yazarları özel etkinlikler ve yalnızca XAML iş akışları oluşturmak için önerilir.  Bir etkinlik testlerinde adlı `Comment` yerine boş bir kullanılan <xref:System.Workflow.Activities.CodeActivity> WF4 iş akışlarında.  Kodda `Comment` etkinlik aşağıdaki gibidir:  
  
```  
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
  
### <a name="empty-workflow"></a>Boş iş akışı  
 Bu test, hiçbir alt etkinliklerle bir sıralı iş akışı kullanır.  
  
### <a name="single-activity"></a>Tek etkinliği  
 Bir alt etkinliğini içeren bir sıralı iş akışı iş akışıdır.  Etkinliği bir <xref:System.Workflow.Activities.CodeActivity> WF3 durumda kod olmadan ve `Comment` etkinlik WF4 durumda.  
  
### <a name="while-with-1000-iterations"></a>While 1000 yineleme ile  
 Sıralı iş akışı içeriyor <xref:System.Activities.Statements.While> herhangi bir iş gerçekleştirmez döngüsünde bir alt aktivitesiyle etkinlik.  
  
### <a name="replicator-compared-to-parallelforeach"></a>Çoğaltıcı ParallelForEach için karşılaştırma  
 <xref:System.Workflow.Activities.ReplicatorActivity> içinde WF3 sıralı ve Paralel yürütme modu vardır.  Sıralı modunda etkinliğe ilişkin performans benzer <xref:System.Workflow.Activities.WhileActivity>.  <xref:System.Workflow.Activities.ReplicatorActivity> Paralel yürütme için kullanışlıdır.  Bu WF4 analog olduğu <xref:System.Activities.Statements.ParallelForEach%601> etkinlik.  
  
 Aşağıdaki diyagramda bu test için kullanılan iş akışı gösterilmektedir. WF3 iş akışı solda ve WF4 iş akışı sağ tarafta.  
  
 ![WF3 ReplicatorActivity ve WF4 ParallelForEach](../../../docs/framework/windows-workflow-foundation/media/replicatorandparallelforeach.gif "ReplicatorAndParallelForEach")  
  
### <a name="sequential-workflow-with-five-activities"></a>Beş etkinliklerle sıralı iş akışı  
 Bu test bir sırayla yürütmek çeşitli etkinlikler kullanılmasının etkisini göstermek için tasarlanmıştır.  Sıralı etkinlikler beş vardır.  
  
### <a name="transaction-scope"></a>İşlem kapsamı  
 Her yineleme için yeni bir iş akışı örneği oluşturulmamış işlem kapsam test diğer testlerden biraz farklıdır.  Bunun yerine, iş akışı biraz ile yapılandırılmış döngü içeren bir <xref:System.Activities.Statements.TransactionScope> hiçbir iş olmadığından tek bir etkinlik içeren etkinlik.  Her çalışma bir toplu işlemin while aracılığıyla 50 tekrar döngü tek bir işlem olarak kabul edilir.  
  
### <a name="compensation"></a>Maaş  
 Adlı tek bir üst öğesi dengelenebilir etkinlik WF3 iş akışı sahip `WorkScope`.  Yalnızca etkinlik uygulayan <xref:System.Workflow.ComponentModel.ICompensatableActivity> arabirimi:  
  
```  
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
  
 Hataya işleyici hedefleri `WorkScope` etkinlik. Eşit oranda simplistic WF4 akışıdır.  A <xref:System.Activities.Statements.CompensableActivity> gövde ve bir dengeleme işleyicisini sahiptir.  Bir açık compensate sırayla sonraki ' dir.  Gövde ve maaş işleyici etkinliğiyle hem boş uygulamaları şunlardır:  
  
```  
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
  
 ![WF3 ve WF iş akışları temel maaş](../../../docs/framework/windows-workflow-foundation/media/basiccompensationworkflows.gif "BasicCompensationWorkflows")  
  
 Şekil 2 – WF3 (sol) ve WF4 (sağdaki) temel Maaş iş akışları  
  
### <a name="performance-test-results"></a>Performans testi sonuçları  
 ![Performans testi sonuçları](../../../docs/framework/windows-workflow-foundation/media/performancedata.gif "performans")  
  
 ![Performans testi veri grafiği](../../../docs/framework/windows-workflow-foundation/media/performancetestchart.gif "PerformanceTestChart")  
  
 Tüm testler, iş akışlarında işlem kapsam test dışında saniyede ölçülür.  Yukarıdaki görüldüğü gibi [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanı performans geliştirilmiş panosunda, özellikle while gibi aynı etkinliğin birden çok yürütmeleri gerektiren alanlar arasında döngü.  
  
## <a name="service-composition-scenario"></a>Hizmet oluşturma senaryosu  
 "Bileşen düzeyinde performans karşılaştırmaları" önceki bölümde gösterildiği gibi önemli ölçüde azalma WF3 WF4 arasındaki yükündeki açıldı.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] İş akışı Hizmetleri artık neredeyse aynı el kodlanmış performansını [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetleri hala ancak sahip tüm avantajlarını [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanı.  Bu test senaryosu karşılaştıran bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] karşı hizmet bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] WF4 iş akışı hizmetinde.  
  
### <a name="online-store-service"></a>Çevrimiçi depolama hizmeti  
 Windows Workflow Foundation'ın gücünü de birkaç hizmetleri kullanan işlemleri oluşturan yeteneğidir.  Bu örnekte, bir sıra satın almak için iki hizmet çağrıları düzenler bir çevrimiçi mağaza hizmeti yok.  İlk adım bir sipariş doğrulama hizmetini kullanarak sipariş doğrulamaktır.  İkinci adım ambar hizmetini kullanarak sipariş doldurmaktır.  
  
 İki arka uç, sipariş doğrulama ve hizmetlerini ambarı hizmeti, her iki testler için aynı kalır.  Değişen orchestration gerçekleştirir çevrimiçi mağaza hizmetinin parçasıdır.  Bir durumda, hizmet el olarak kodlanmıştır bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet.  Diğer durumlarda, hizmet olarak yazılmış bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] WF4 iş akışı hizmetinde. [!INCLUDE[wf1](../../../includes/wf1-md.md)]-Bu test için izleme ve kalıcılığı kapalıdır gibi belirli özellikleri.  
  
### <a name="environment"></a>Ortam  
 ![İş akışı performansı sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
 İstemci istekleri varsayılan olarak, birden çok bilgisayarlardan çevrimiçi depolama hizmetine HTTP üzerinden yapılır.  Tek bir bilgisayar, tüm üç hizmeti barındırır.  Çevrimiçi mağaza hizmetini ve arka uç hizmetleri arasında Aktarım katmanı, TCP veya HTTP değil.  Ölçümü işlem/saniye sayısına dayanır tamamlanmış `PurchaseOrder` çevrimiçi depolama hizmetine yapılan çağrıları.  Kanal havuzu yeni WF4 içinde kullanılabilen bir özelliktir.  İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bu test kanal havuz bölümü sağlanamadığından kutu dışı çevrimiçi depolama Hizmeti'nde basit bir havuzu oluşturma teknik el kodlanmış uyarlamasını kullanıldı.  
  
### <a name="performance"></a>Performans  
 ![Çevrimiçi mağaza hizmeti performans grafiği](../../../docs/framework/windows-workflow-foundation/media/onlinestoreperfgraph.gif "OnlineStorePerfGraph")  
  
 Kanal havuzu olmadan arka uç TCP hizmetlerine bağlanan [!INCLUDE[wf1](../../../includes/wf1-md.md)] hizmet üzerinde üretilen işi %17,2 etkisi vardır.  Kanal havuzu ile cezası hakkında %23,8 olur.  HTTP için daha az etkisidir: 4.3 havuzu olmadan % ve % havuzu ile 8.1.  Kanal havuzu çok az avantajı HTTP kullanırken sağladığı dikkate almak önemlidir.  
  
 Varken yükü bir yandan kodlanmış ile karşılaştırıldığında WF4 çalışma zamanının [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti bu test, bunu en kötü Durum senaryosu olarak değerlendirilebilir.  Bu test iki arka uç Hizmetleri'nde çok az şey yapın.  Gerçek uçtan uca senaryoda, bu Hizmetleri veritabanı çağrısı, Aktarım katmanı performans etkisini daha az önemli yapma gibi daha pahalı işlemleri gerçekleştirebilirsiniz.  Bu artı WF4 içinde kullanılabilen özelliklerin yararları Workflow Foundation orchestration hizmetleri oluşturmak için uygun bir seçenek sağlar.  
  
## <a name="key-performance-considerations"></a>Anahtar performans etkenleri  
 Özellik alanları ile birlikte çalışma hariç olmak üzere, bu bölümde, WF3 ve WF4 arasında önemli ölçüde değişti.  Bu tasarım, performans yanı sıra iş akışı uygulamaları etkiler.  
  
#### <a name="workflow-activation-latency"></a>İş akışı etkinleştirme gecikmesi  
 İçinde bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] iş akışı hizmeti uygulaması, yeni bir iş akışı başlatma veya varolan bir iş akışı yükleme için gecikme süresi önemlidir olarak engelliyor olabilir.  Bu test çalışması WF3 XOML konak tipik bir senaryo WF4 XAMLX ana bilgisayar karşı ölçer.  
  
##### <a name="environment-setup"></a>Ortam Kurulumu  
 ![Ortam Kurulumu testleri gecikme süresi ve verimlilik için](../../../docs/framework/windows-workflow-foundation/media/latencyandthroughputenvironment.gif "LatencyAndThroughputEnvironment")  
  
##### <a name="test-setup"></a>Test Kurulumu  
 Senaryoda, bir istemci bilgisayarın bağlantı kurduğu bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Bağlam tabanlı bağıntı kullanarak iş akışı hizmeti.  Bağlam bağıntı özel bağlam bağlama gerektirir ve iletileri doğru iş akışı örneğine ilişkilendirmek için içerik üstbilgisi veya tanımlama bilgisi kullanır.  İleti gövdesi ayrıştırılacak gerek kalmayacak şekilde kimliği ileti üstbilgisinde bulunan bağıntı yararlı bir performans sahiptir. [!INCLUDE[crabout](../../../includes/crabout-md.md)] bağlam bağıntı bkz [bağlam değişimi bağıntısı](../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
  
 Hizmet isteği ile yeni bir iş akışı oluşturmak ve böylece gecikme süresi ölçümü iş akışını çalıştıran harcanan süre içermez hemen bir yanıt gönderin.  WF3 XOML bir arka plan kodu ile iş akışıdır ve WF4 tamamen XAML iş akışıdır.  WF4 iş akışı şu şekildedir:  
  
 ![WF 4 bağıntı kapsam](../../../docs/framework/windows-workflow-foundation/media/correlationscopeworkflow.gif "CorrelationScopeWorkflow")  
  
 <xref:System.ServiceModel.Activities.Receive> Etkinliği iş akışı örneği oluşturur.  Alınan iletide geçirilen bir değer yanıt iletisinde yansıtılır.  İş akışının geri kalanı yanıt izleyen bir dizisini içerir.  Yukarıdaki durumda yalnızca bir yorum etkinlik gösterilir.  İş akışı karmaşıklık benzetimini yapmak için açıklama etkinliklerin sayısını değiştirildi.  Bir WF3 eşdeğer yorum etkinliktir <xref:System.Workflow.Activities.CodeActivity> çalışma gerçekleştirir. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Açıklama etkinlik bu makalenin "bileşen düzeyinde performans karşılaştırma" bölümüne bakın.  
  
##### <a name="test-results"></a>Test Sonuçları  
 ![Gecikme süresi sonuçları](../../../docs/framework/windows-workflow-foundation/media/latencyresultsgraph.gif "LatencyResultsGraph")  
  
 3 – Durgun şekil ve WCF iş akışı hizmetleri için gecikme süresini sıcak  
  
 Yukarıdaki grafikte soğuk talebine başvuruyor. söz konusu olduğunda olmayan mevcut bir <xref:System.ServiceModel.WorkflowServiceHost> verilen iş akışı için.  Diğer bir deyişle, iş akışı ilk kez kullanılıyor ve XOML ya da XAML derlenmesi gerekiyor soğuk gecikme olur.  Yarı gecikme iş akışı türü zaten derlenmiş zaman yeni bir iş akışı örneği oluşturmak için saattir.  İş akışı karmaşıklığını WF4 durumda çok az fark etmez ancak WF3 durumda doğrusal progression sahiptir.  
  
#### <a name="correlation-throughput"></a>Bağıntı işleme  
 WF4 yeni bir içerik tabanlı bağıntı özelliği sunmaktadır.  WF3 yalnızca Bağlam tabanlı bağıntı sağlanır.  Bağlam tabanlı bağıntı özel yalnızca yapılabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kanal bağlamaları.  İş akışı kimliği, bu bağlamaların kullanırken ileti üstbilgisine eklenir.  WF3 çalışma zamanı yalnızca bir iş akışı kimliğini tarafından tanımlayamadı  İçeriğe dayalı bağıntı ile iş akışı Yazar bir bağıntı anahtar ilgili bir hesap numarası veya müşteri kimliği gibi veri parçası dışında oluşturabilir [!INCLUDE[crabout](../../../includes/crabout-md.md)] içerik tabanlı bağıntı bakın [içeriğe dayalı bağıntı](../../../docs/framework/wcf/feature-details/content-based-correlation.md).  
  
 Bağıntı anahtarı ileti üstbilgisinde bulunur, bağlam tabanlı bağıntı performans avantajı vardır.  Anahtar iletisi Kaldır-serialization/ileti kopyalama olmadan okuyabilir.  İçeriğe dayalı bağıntı içinde bağıntı anahtar ileti gövdesi içinde depolanır.  Bir XPath ifadesi anahtarı bulmak için kullanılır.  Bu ek işleme maliyetini ileti gövdesi ve anahtar sayısı anahtarında derinliği boyutuna bağlıdır.  Bu test içeriği ve içerik tabanlı bağıntı karşılaştırır ve aynı zamanda birden çok anahtar kullanırken performans düşüşü gösterir.  
  
#### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performansı sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
#### <a name="test-setup"></a>Test Kurulumu  
 ![Bağıntı işleme iş akışı Test](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputworkflow.gif "CorrelationThroughputWorkflow")  
  
 Yukarıda gösterilen iş akışı "Kalıcılık" bölümünde kullanılan aynıdır.  Kalıcılık olmadan bağıntı testler için çalışma zamanı'nda yüklü hiçbir Kalıcılık sağlayıcısı yok.  Bağıntı iki yerde oluşur: CreateOrder ve CompleteOrder.  
  
#### <a name="test-results"></a>Test Sonuçları  
 ![Bağıntı işleme](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputgraph.gif "CorrelationThroughputGraph")  
  
 Bu grafik içerik tabanlı bağıntı artışlar kullanılan anahtar sayısı olarak performans düşüklüğü gösterir.  TCP ve HTTP arasında Eğriler uygulamada benzerliği bu iletişim kuralları ile ilgili ek yükü gösterir.  
  
#### <a name="correlation-with-persistence"></a>Bağıntı Kalıcılık ile  
 Kalıcı bir iş akışı ile CPU baskısı içerik tabanlı bağıntı öğesinden iş akışı çalışma zamanı SQL veritabanına kaydırır.  Saklı yordamlar SQL Kalıcılık sağlayıcısında eşleşen uygun iş akışı bulmaya anahtarlarla çalışma yapın.  
  
 ![Bağıntı ve kalıcılığı sonuçları](../../../docs/framework/windows-workflow-foundation/media/correlationandpersistencegraph.gif "CorrelationAndPersistenceGraph")  
  
 Bağlam tabanlı bağıntı hala içerik tabanlı bağıntı hızlıdır.  Ancak, fark Kalıcılık daha fazla bağıntı daha performans üzerindeki etkisi gibi daha az belirgin olur.  
  
### <a name="complex-workflow-throughput"></a>Karmaşık iş akışı işleme  
 Bir iş akışı karmaşıklığını yalnızca etkinlikleri sayısına göre ölçülen değil.  Bileşik etkinlikleri birçok alt içerebilir ve bu alt bileşik etkinlikleri de olabilir.  İç içe geçmiş artar düzeylerini sayısı olarak, bu nedenle şu anda yürütülen durumda olabilir etkinliklerin sayısını ve durumda olabilir değişken sayısı yapar.  Bu test, karmaşık iş akışı yürütülürken WF3 WF4 arasındaki verimliliği karşılaştırır.  
  
### <a name="test-setup"></a>Test Kurulumu  
 Bu testler, bir Intel Xeon X5355 2,66 GHz 4 yönlü bilgisayar @ 4 GB RAM Windows Server 2008 x64 çalıştıran üzerinde yürütüldü.  % 100 CPU kullanımına ulaşmak için çekirdek başına tek bir iş parçacığı ile tek bir işlemde test kodu çalıştırır.  
  
 Bu test için oluşturulan iş akışları iki ana değişkenleriniz: derinliği ve her sıralı etkinlik sayısı.  Her derinlik düzeyini döngü, kararlar, atamalarını ve dizileri çalışırken bir paralel etkinlik içerir.  Aşağıda gösterilen WF4 Tasarımcısı'nda, üst düzey akış çizelgesi gösterilen.  Her akış etkinliği ana akış benzer.  Bu iş akışı derinliği test parametreleri için sınırlı olduğu picturing düzgünleştiren parçalı düşünün yararlı olabilir.  
  
 Belirli bir test etkinlik sayısını derinliği ve dizisi başına etkinlik sayısı tarafından belirlenir.  Aşağıdaki eşitliği WF4 test etkinlik sayısını hesaplar:  
  
 ![Etkinlik sayısını hesaplamak için eşitlik](../../../docs/framework/windows-workflow-foundation/media/numberofactivitiesequation.gif "NumberOfActivitiesEquation")  
  
 WF3 testin etkinlik sayısı, ek bir sıra nedeniyle biraz farklı bir eşitlik ile hesaplanabilir:  
  
 ![Etkinlik sayısını hesaplamak için eşitlik](../../../docs/framework/windows-workflow-foundation/media/w3numberofactivitiesequation.gif "W3NumberOfActivitiesEquation")  
  
 D derinliği olduğu ve etkinlikler dizisi başına sayısıdır.  Bu denklemini arkasındaki mantığı ilk sabiti zaman çarpılarak emin olup sıraların sayısı ve ikinci sabit geçerli düzeyi etkinliklerin statik numarasıdır.  Her akış üç akış çizelgesi alt etkinlik vardır.  Alt derinliği düzeyde, bu akış çizelgeleri boş ancak diğer düzeylerde ana akış kopyalarını etmektedir.  Her sınama değişim ait iş akışı tanımı etkinlik sayısını aşağıdaki tabloda belirtilmiştir:  
  
 ![Her testte kullanılan etkinliklerin sayısını karşılaştırır](../../../docs/framework/windows-workflow-foundation/media/comparechart.gif "CompareChart")  
  
 İş akışı tanımı etkinlik sayısını keskin ile her derinlik düzeyini artırır.  Ancak karar noktası başına yalnızca bir yol yürütüldüğünde belirli iş akışı örneğinde yalnızca küçük bir alt gerçek etkinliklerin çalıştırılır.  
  
 ![Karmaşık iş akışı](../../../docs/framework/windows-workflow-foundation/media/complexworkflowthroughputworkflow.gif "ComplexWorkflowThroughputWorkflow")  
  
 Eşdeğer bir iş akışı için WF3 oluşturuldu. WF3 Tasarımcısı tüm iş akışı tasarım alanı iç içe geçme yerine bu nedenle bu konudaki görüntülenemeyecek kadar büyük gösterir. İş akışının bir parçası, aşağıda gösterilmiştir.  
  
 ![WF3 İş akışı](../../../docs/framework/windows-workflow-foundation/media/wf3workflow.gif "WF3Workflow")  
  
 İç içe bir olağanüstü durumda kullanmak için bu test parçası olan başka bir iş akışı 100 iç içe geçmiş sıralar kullanır.  En içteki içinde tek bir dizidir `Comment` veya <xref:System.Workflow.Activities.CodeActivity>.  
  
 ![İç içe sıraları](../../../docs/framework/windows-workflow-foundation/media/nestedsequencewf.gif "NestedSequenceWF")  
  
 İzleme ve kalıcılığı bu testin bir parçası olarak kullanılmaz.  
  
### <a name="test-results"></a>Test Sonuçları  
 ![Üretilen iş grafiği](../../../docs/framework/windows-workflow-foundation/media/testresults1.gif "TestResults1")  
  
 Daha karmaşık iş akışları ile çok sayıda derinliği ve çok sayıda etkinlikleri ile performans sonuçları bu makalenin önceki bölümlerinde gösterilen diğer verimlilik numaralarının tutarlıdır.  WF4'ın işleme büyüklük daha hızlıdır ve Logaritmik ölçekte Karşılaştırılacak sahiptir.  
  
### <a name="memory"></a>Bellek  
 Windows Workflow Foundation bellek yükü iki önemli alanda ölçülür: iş akışı karmaşıklığı ve iş akışı tanımları sayısı.  Bellek ölçümlerinin bir Windows 7 64-bit iş istasyonunda gerçekleştirilen.  Çalışma kümesi boyutu performans sayaçlarını izleme, Environment.WorkingSet yoklama veya VMMap kullanılabilir gibi bir araç kullanarak gibi ölçüsü elde etmek için birçok yolu vardır [VMMap](http://technet.microsoft.com/sysinternals/dd535533.aspx). Yöntemlerinin bir birleşimini elde edilir ve her test sonuçlarını doğrulamak için kullanıldı.  
  
### <a name="workflow-complexity-test"></a>İş akışı karmaşıklık Test  
 İş akışı kapsamına bağlı fark çalışma kümesi iş akışı karmaşıklık test ölçer.  Önceki bölümde kullanılan karmaşık iş akışları ek olarak, iki temel durumları karşılamak üzere yeni Çeşitlemeler eklenir: tek etkinliği iş akışı ve 1000 etkinliklerle dizisi.  Bu testler için iş akışlarını başlatılamadı ve tek bir seri döngü tamamlanmasında bir dakikalık bir süre için çalıştırılır.  Her bir test çeşidine üç kez çalıştırın ve kaydedilen veriler bu üç çalıştırır ortalaması.  
  
 İki yeni temel testleri olanlar gibi aşağıda gösterilen ara iş akışları vardır:  
  
 ![Karmaşık iş akışları](../../../docs/framework/windows-workflow-foundation/media/complexworkflowboth.gif "ComplexWorkflowBoth")  
  
 Yukarıda gösterilen WF3 akışında boş <xref:System.Workflow.Activities.CodeActivity> etkinlikleri kullanılır.  WF4 iş akışı kullanımlar yukarıda `Comment` etkinlikler.  `Comment` Etkinlik bileşen düzeyinde performans karşılaştırmaları bölümünde daha önce bu makalede açıklanan.  
  
 ![Bellek kullanım grafiği](../../../docs/framework/windows-workflow-foundation/media/complexmemoryusage.gif "ComplexMemoryUsage")  
  
 Bu grafikte fark Temizle eğilimleri iç içe geçme bellek kullanımını WF3 ve WF4 göreceli olarak en az bir etkiye sahip biridir.  Belirli bir iş akışındaki etkinliklerin sayısını en önemli bellek etkiye gelir.  Veri dizisi 1000, karmaşık derinliği 5 dizisi 5 ve karmaşık derinliği 7 sırası 1 Çeşitlemeler verildiğinde, etkinliklerin sayısını binlerce girerken, bellek kullanım artışı daha belirgin hale işaretlenmemiştir.  (1 derinliğini 7 sırası) olağanüstü durumda ~ 29K etkinlikleri olduğu WF4 neredeyse %79 daha az bellek WF3 daha kullanıyor.  
  
### <a name="multiple-workflow-definitions-test"></a>Birden çok iş akışı tanımları testi  
 İş akışı tanımı başına bellek ölçme iki farklı testlere WF3 ve WF4 iş akışlarını barındırmak için kullanılabilir seçenekleri nedeniyle ayrılmıştır.  Belirli bir iş akışı instanced ve tanımı yalnızca bir kez yürütülen iş akışı karmaşıklık test değerinden farklı bir şekilde testleri çalıştırın.  İş akışı tanımı ve ana bilgisayar AppDomain ömrü boyunca bellekte kalması olmasıdır.  Belirtilen iş akışı örneği çalıştıran tarafından kullanılan bellek çöp toplama sırasında temizlenmelidir.  Geçiş Kılavuzu WF4 için barındırma seçenekleri hakkında daha ayrıntılı bilgi içerir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [WF Geçiş Kılavuzu: İş akışı barındırma](http://go.microsoft.com/fwlink/?LinkID=153313).  
  
 İş akışı tanımı testi için birçok iş akışı tanımları oluşturma çeşitli şekillerde yapılabilir.  Örneği için bir ad aynı dışında 1000 iş akışları oluşturmak için kod oluşturma kullanın ve bu iş akışlarının her ayrı dosyalara kaydedin.  Bu yaklaşım için konsol barındırılan sınama yapılmadı.  WF3 içinde <xref:System.Workflow.Runtime.WorkflowRuntime> sınıfı, iş akışı tanımları çalıştırmak için kullanıldı.  WF4 olabilir ya da kullanım <xref:System.Activities.WorkflowApplication> tek iş akışı örneği oluşturmak veya doğrudan kullanmak için <xref:System.Activities.WorkflowInvoker> bir yöntem çağrısı değilmiş gibi etkinliği çalıştırmak için.  <xref:System.Activities.WorkflowApplication> tek iş akışı örneğinin bir ana bilgisayardır ve daha yakın özellik eşliği sahip <xref:System.Workflow.Runtime.WorkflowRuntime> böylece bu test kullanıldı.  
  
 IIS iş akışlarında barındırdığında kullanmak mümkün bir <xref:System.Web.Hosting.VirtualPathProvider> yeni <xref:System.ServiceModel.WorkflowServiceHost> tüm XAMLX veya XOML dosyaları oluşturmak yerine.  <xref:System.Web.Hosting.VirtualPathProvider> Gelen isteği işler ve "bir veritabanından yüklenen ya da, bu durumda, anında oluşturulan bir sanal dosya" ile yanıt verir.  Bu nedenle, 1000 fiziksel dosyaları oluşturmak gerekli değildir.  
  
 Konsol testinde kullanılan iş akışı tanımları basit sıralı iş akışlarıyla tek bir etkinliğin yoktu.  Boş bir tek Etkinlik olduğu <xref:System.Workflow.Activities.CodeActivity> WF3 çalışması için ve bir `Comment` WF4 çalışması için etkinlik.  IIS barındırılan durum iletisi ve yanıt gönderme bitiş alma üzerinde Başlat iş akışları kullanılır:  
  
 ![İş akışı hizmetleri WF3 ve WF4](../../../docs/framework/windows-workflow-foundation/media/receiveworkflowboth.gif "ReceiveWorkflowBoth")  
  
 Şekil 4 – istek/yanıt düzendeki ReceiveActivity ve WF4 akışıyla WF3 iş akışı  
  
 Aşağıdaki tabloda, tek bir iş akışı tanımı 1001 tanımları arasındaki çalışma kümesindeki delta gösterilmektedir:  
  
|Barındırma seçenekleri|WF3 Çalışma kümesi Delta|WF4 Çalışma kümesi Delta|  
|---------------------|---------------------------|---------------------------|  
|Konsol uygulaması iş akışları barındırılan|18 MB|9 MB|  
|IIS barındırılan iş akışı Hizmetleri|446 MB|364 MB|  
  
 İş akışı tanımları IIS'de barındırma nedeniyle daha fazla bellek tüketir <xref:System.ServiceModel.WorkflowServiceHost>, ayrıntılı [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti yapıları ve ileti işleme mantığı konak ile ilişkili.  
  
 İş akışı içinde WF3 barındırma konsol için XOML yerine kodu da uygulanan.  İçinde WF4 varsayılan XAML kullanmaktır.  XAML derlemesinde katıştırılmış bir kaynağı olarak depolanır ve çalışma zamanı sırasında bir uygulama bir iş akışı sağlamak için derlenmiş.  Bu işlemle ilişkili bazı ek yoktur.  WF3 ve WF4 arasında eşit bir karşılaştırma yapmak için kodlanmış iş akışı XAML yerine kullanılmıştır.  WF4 iş akışları bir örneği aşağıda verilmiştir:  
  
```  
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
  
 Bellek tüketimi etkileyebilecek diğer birçok faktöre vardır. Aynı öneriler tüm yönetilen programlar için hala geçerlidir.  IIS barındırılan ortamlarda <xref:System.ServiceModel.WorkflowServiceHost> bir iş akışı tanımı için oluşturulan nesne, uygulama havuzu geri dönüştürülmeden kadar bellekte kalır.  Bunu göz önünde uzantıları yazılırken tutulmalıdır.  Ayrıca, "Genel" değişkenleri (tüm iş akışına kapsamlı) önlemek ve mümkün olduğunda değişkenleri kapsamını sınırlandırmak en iyisidir.  
  
## <a name="workflow-runtime-services"></a>İş akışı çalışma zamanı Hizmetleri  
  
### <a name="persistence"></a>Kalıcılığı  
 Her ikisi de bir SQL Kalıcılık sağlayıcıyla sevk WF3 ve WF4.  WF3 SQL Kalıcılık sağlayıcısı iş akışı örneği serileştirir ve bir blob'a depolayan basit bir uygulamasıdır.  Bu nedenle, bu sağlayıcı performansını büyük oranda iş akışı örneği boyutuna bağlıdır.  WF3 içinde örnek boyutu Bu yazıda, daha önce bahsedildiği gibi çeşitli nedenlerle artırabilir.  Birçok müşteri seri hale getirilmiş bir örneği veritabanında saklamak hiçbir iş akışı durumunu görünürlük verdiğinden varsayılan SQL Kalıcılık sağlayıcısı kullanmamayı.  Belirli bir iş akışının iş akışı kimliği bilmeden bulmak için bir kalıcı her örneği seri durumdan ve içeriğini inceleyin etmesi gerekir.  Bu sorunu çözmek için kendi Kalıcılık sağlayıcıları yazmak birçok geliştiriciler tercih.  
  
 WF4 SQL Kalıcılık sağlayıcısı bazı bu sorunları gidermek çalıştı.  Kalıcılık tablolar active yer işaretleri ve yükseltilebilir özellikler gibi belirli bilgileri kullanıma sunar.  WF4 yeni içerik tabanlı bağıntı özelliği de bazı değişiklikler kalıcı iş akışı örneği kuruluşta güdümlü WF3 SQL Kalıcılık yaklaşımı kullanarak gerçekleştirebilirsiniz değil.  Bu iş Kalıcılık sağlayıcısının daha karmaşık hale getirir ve veritabanı üzerinde fazladan stres koyar.  
  
### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performansı sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-setup"></a>Test Kurulumu  
 Bile bir gelişmiş özellik kümesini ve daha iyi eşzamanlılık işleme ile WF4 SQL Kalıcılık sağlayıcısında WF3 sağlayıcısında hızlıdır.  Bunu göstermek için aşağıda WF3 ve WF4 temelde aynı işlemleri gerçekleştirmek iki iş akışları karşılaştırılır.  
  
 ![Kalıcılık iş akışları](../../../docs/framework/windows-workflow-foundation/media/persistworkflow.gif "PersistWorkflow")  
  
 Şekil 5 – WF3 üzerinde Kalıcılık akışında sol ve sağ taraftaki WF4  
  
 İki iş akışları her ikisi tarafından alınan ileti oluşturulur.  İlk yanıt gönderdikten sonra iş akışı kalıcıdır.  WF3 durumda, boş bir <xref:System.Workflow.ComponentModel.TransactionScopeActivity> Kalıcılık başlatmak için kullanılır.  Aynı WF3 içinde bir etkinlik "kapatırken kalıcı olmasını sağlar." olarak işaretlemek için elde edilebilir  İkinci, ilişkili ileti akışı tamamlar.  İş akışları kalıcı ancak değil kaldırıldı.  
  
### <a name="test-results"></a>Test Sonuçları  
 ![Üretilen iş kalıcılığı](../../../docs/framework/windows-workflow-foundation/media/throughputpersistence.gif "ThroughputPersistence")  
  
 Orta katman ile istemci arasında aktarım HTTP olduğunda, WF4 kalıcılığı bir geliştirme 2.6 zamanlarının gösterir.  TCP taşıma 3.0 saatler faktörün artırır.  Tüm durumlarda, CPU kullanımı orta katman %98 olduğu ya da daha yüksek.  WF4 verimlilik büyük olduğunu daha hızlı iş akışı çalışma zamanı nedeniyle nedenidir.  Seri hale getirilmiş örnek boyutu için her iki durumda yetersiz ve bu durumda ana katkıda bulunan bir öğe değil.  
  
 Bu test WF3 ve WF4 akışlarında bir etkinlik Kalıcılık oluştuğunda açıkça belirtmek için kullanın.  Bu eklentiyi olmadan iş akışını sürdürmek avantajına sahiptir.  WF3 içinde da kullanarak kalıcı hale getirmek mümkündür <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> özellik, ancak bu iş akışı örneği belleğinden kaldırır.  Bir iş akışı bazı noktalarda devam ederse emin olmak WF3 kullanarak bir geliştirici istiyorsa, bunlar ya da iş akışı tanımını veya kaldırılmasını ve iş akışı örneği yeniden yükleme için maliyet ödeme gerekir.  WF4 yeni bir özellik yüklemeyi kaldırma olmadan kalıcı hale getirmek mümkün kılar: <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>.  Bu özellik iş akışı örneği üzerinde boşta kalıcı ancak kadar bellekte kalır sağlar <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> eşiği karşılanıyorsa veya yürütme devam etti.  
  
 WF4 SQL Kalıcılık sağlayıcı veritabanı katmanında daha fazla iş gerçekleştirmediğini unutmayın.  SQL veritabanı var. CPU ve disk kullanımını izlemek önemlidir bir ayak bağı olabilir.  Aşağıdaki eklediğinizden emin olun performans sayaçlarını SQL veritabanı performans iş akışı uygulamaları testi:  
  
-   PhysicalDisk\\% Disk Zamanı okuma  
  
-   PhysicalDisk\\% Disk Zamanı  
  
-   PhysicalDisk\\% Disk Zamanı yazma  
  
-   PhysicalDisk\\% Ort. Disk Sırası Uzunluğu  
  
-   PhysicalDisk\Avg. Disk okuma sırası uzunluğu  
  
-   PhysicalDisk\Avg. Disk yazma sırası uzunluğu  
  
-   PhysicalDisk\Current Disk Sırası Uzunluğu  
  
-   İşlemci bilgileri\\% işlemci zamanı  
  
-   SQLServer:Latches\Average Mandal bekleme süresi (ms)  
  
-   SQLServer:Latches\Latch bekler/sn  
  
### <a name="tracking"></a>İzleme  
 İş akışı izleme, bir iş akışı ilerlemesini izlemek için kullanılabilir.  İzleme olayları dahil bilgiler izleme profili tarafından belirlenir.  Daha karmaşık izleme profili, daha pahalı izleme haline gelir.  
  
 WF3 SQL tabanlı izleme hizmeti ile birlikte gelir.  Bu hizmet toplu ve toplu olmayan modda işe yarayabilir.  Toplu olmayan modda, izleme olayları doğrudan veritabanına yazılır.  Toplu iş modunda izleme olaylarını aynı toplu iş akışı örneği durum olarak içine toplanır.  Toplu iş modu en iyi performans için iş akışı tasarımları yelpazedeki vardır.  Ancak, toplu işlem performansı olumsuz kalıcı olmadan birçok etkinlik iş akışı çalıştırıyorsa ve bu etkinlikler izlenir olabilir.  Bu genellikle Döngülerde olacağını ve bu senaryonun olmaması için en iyi Kalıcılık noktası içerecek şekilde büyük döngüler tasarlamak için yoludur.  Her maliyetlerini ölçmek ve bakiyesi olan gündeme önemlidir Kalıcılık noktası bir döngüye Tanıtımı olumsuz yanı performansını etkileyebilir.  
  
 Hizmet İzleme SQL ile WF4 gönderilmeyen.  İzleme bilgilerini bir SQL veritabanına kayıt daha iyi bir uygulama sunucusundan işlenmiş yerine yerleşik [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Bu nedenle SQL izleme şimdi AppFabric tarafından işlenir.  WF4 Giden kutusu izleme sağlayıcıda olay Windows için izleme (ETW üzerinde) temel alır.  
  
 ETW, Windows'da yerleşik bir çekirdek düzeyi, düşük gecikme süreli olay sistemidir.  Gerçekte bir tüketici olduğunda cezasına olay izleme için yalnızca sebep olanaklı kılan bir sağlayıcı/tüketici modeli kullanır.  İşlemci, disk, bellek ve ağ kullanımı gibi çekirdek olaylar yanı sıra birçok uygulama de ETW yararlanın.  Olaylar uygulamaya özelleştirilebilir ETW olayları performans sayaçları'den daha güçlü bir seçenektir.  Bir olay iş akışı kimliği ya da bir bilgi iletisidir gibi metin içerebilir.  Ayrıca, belirli bir alt olayların kullanan tüm olayları yakalamak daha az performans etkisi sahip olmasını olayları bit maskesi ile ayrılır.  
  
 ETW İzleme SQL yerine kullanmanın yaklaşımın avantajları şunlardır:  
  
-   Olayları izleme koleksiyonu için başka bir işlem ayrılabilir.  Bu olayların nasıl kaydedileceğini daha fazla esneklik sağlar.  
  
-   ETW İzleme olayları ile kolayca birleştirilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ETW olayları veya bir SQL Server veya çekirdek sağlayıcısı gibi diğer ETW sağlayıcıları.  
  
-   İş akışı yazarları WF3 SQL izleme hizmetin toplu iş modunda gibi belirli izleme yer alan bir uygulama daha iyi çalışması için bir iş akışı alter gerekmez.  
  
-   Bir yönetici izleme üzerinde veya konak işlem geri dönüştürme olmadan kapatabilirsiniz.  
  
 ETW İzleme için performans avantajları bir dezavantajı ile gelir.  Sistem yoğun kaynak baskısı altında ise ETW olayları kaybolmuş olabilir.  Olayları işleme normal program yürütme engelleyecek şekilde tasarlanmamıştır ve bu nedenle, tüm ETW olayları kendi abonelere yayınlanacaktır garanti edilmez.  Bu sistem durumu izleme için harika ancak denetlemek için uygun değil ETW İzleme hale getirir.  
  
 WF4 SQL izleme sağlayıcısı olmasa AppFabric yapar.  AppFabric'ın SQL izleme olayları toplu işlemleri ve bunları hızlı eklemeleri için tasarlanmış bir SQL tablosuna yazan bir Windows hizmeti ile ETW olayları abone olmak için bir yaklaşımdır.  Ayrı bir iş, bu tablodan veri boşaltır ve AppFabric Panosunda görüntülenebilir tabloları raporlamasına reforms.  Başka bir deyişle, olayları izleme toplu geldiği ve bu nedenle Kalıcılık noktası için kaydedilen önce beklenecek yok iş akışının bağımsız olarak işlenir.  
  
 ETW olayları logman veya XPerf'in gibi araçlarla kaydedilebilir.  Compact ETL dosya xperfview gibi bir araçla görüntülenemez veya daha okunabilir bir biçimde, XML gibi tracerpt ile dönüştürülür.  WF3 içinde bir SQL veritabanı olmadan olayları izleme almak için tek seçenek özel izleme hizmeti oluşturmaktır. [!INCLUDE[crabout](../../../includes/crabout-md.md)] ETW, bkz: [WCF hizmetleri ve Windows için olay izleme](../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) ve [Windows için olay izleme](http://msdn.microsoft.com/library/ff190903.aspx\)).  
  
 Etkinleştirme iş akışı izleme değişen derece cinsinden performansını etkiler.  Kıyaslama logman aracı olayları izleme ETW tüketebilir ve bir ETL dosyasına kaydetmek için kullanır.  İçinde AppFabric İzleme SQL maliyetini bu makalenin kapsamı içinde değil.  Ayrıca AppFabric içinde kullanılan temel izleme profili, bu Kıyaslama gösterilir.  ' De yer izleme olaylarını izleme durumu maliyetidir.  Bu olaylar, sorun giderme ve sistem ortalama verimi belirlemek için kullanışlıdır.  
  
### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performansı sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-results"></a>Test Sonuçları  
 ![Maliyet izleme iş akışı](../../../docs/framework/windows-workflow-foundation/media/workflowtracingcost.gif "WorkflowTracingCost")  
  
 Sistem durumu izleme kabaca üzerinde üretilen işi %3 bir etkisi yoktur.  Temel profilinin maliyet yaklaşık % 8'dir.  
  
## <a name="interop"></a>Birlikte çalışma  
 WF4 olduğu neredeyse Tamamlandı'nin yeniden [!INCLUDE[wf1](../../../includes/wf1-md.md)] ve bu nedenle WF3 iş akışları ve etkinlikler WF4 ile doğrudan uyumlu değil.  Windows Workflow Foundation erken benimsenen birçok müşteri şirket içi veya üçüncü taraf iş akışı tanımları ve özel etkinlikler için WF3 sahip olacaktır.  WF4 geçişi kolaylaştırmak için bir yol WF4 iş akışı içinde WF3 etkinliklerden yürütebilir birlikte çalışma etkinlik kullanmaktır.  Önerilir <xref:System.Activities.Statements.Interop> etkinliği yalnızca kullanılabilir gerektiğinde. [!INCLUDE[crabout](../../../includes/crabout-md.md)] WF4 kullanıma geçiş [WF4 Geçiş Kılavuzu](http://go.microsoft.com/fwlink/?LinkID=153313).  
  
### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performansı sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-results"></a>Test Sonuçları  
 Aşağıdaki tabloda, çeşitli yapılandırmaları bir sırasında beş etkinlikler içeren bir iş akışını çalıştırma sonuçları gösterir.  
  
|Test|Üretilen işi (iş akışları/sn)|  
|----------|-----------------------------------|  
|WF3 çalışma zamanında WF3 sırası|1,576|  
|Birlikte çalışması kullanarak WF4 çalışma zamanında WF3 sırası|2,745|  
|WF4 sırası|153,582|  
  
 Düz WF3 birlikte çalışması kullanarak için önemli performans artışı yoktur.  Ancak, WF4 etkinlikleri karşılaştırıldığında artırma önemsizdir.  
  
## <a name="summary"></a>Özet  
 Performans WF4 için yoğun yatırım birçok önemli alanda Ücretli.  Ayrı ayrı iş akışı bileşen performansı olduğu bazı durumlarda yüzlerce kez WF3 için leaner nedeniyle karşılaştırıldığında WF4 içinde daha hızlı [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanı.  Gecikme rakamları de önemli ölçüde daha uygundur.  Bu yaşanan performans sorunları kullanmak için anlamına gelir [!INCLUDE[wf1](../../../includes/wf1-md.md)] elle kodlama aksine [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] orchestration Hizmetleri eklenen kullanmanın yararları dikkate çok küçük [!INCLUDE[wf1](../../../includes/wf1-md.md)].  2.5-3.0 faktörüyle Kalıcılık performans artar.  İş akışı şimdi izleme yoluyla sistem durumu izleme, çok az yüke sahiptir.  Geçiş kılavuzlarını kapsamlı bir kümesini WF3 WF4 için taşıma dikkate olanlar için kullanılabilir.  Tüm bunlar, karmaşık uygulamalar yazma çekici bir seçenek WF4 olmanız gerekir.  
  
## <a name="acknowledgements"></a>Katkıda Bulunanlar  
 Çoğu aşağıdaki Katkıda Bulunanlar ve gözden geçirenler sarf için teşekkür ederiz:  
  
-   Leon Welicki, Microsoft Corporation  
  
-   Ryszard Kwiecinski, Microsoft Corporation  
  
-   Emil Velinov, Microsoft Corporation  
  
-   Can Etikan Talbert, Microsoft Corporation  
  
-   Bob Etikan, Microsoft Corporation  
  
-   Stefan Batres, Microsoft Corporation
