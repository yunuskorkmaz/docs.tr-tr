---
title: Windows Workflow Foundation 4 performansı
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: 85556a6e7a55e0afb206d1e04bfdd9fc66fa99b1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201484"
---
# <a name="windows-workflow-foundation-4-performance"></a>Windows Workflow Foundation 4 performansı
Dustin Metzgar  
  
 Wenlong Dongu  
  
 Microsoft Corporation ' ın Eylül 2010  
  
 Microsoft [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] büyük bir düzeltme ağır yatırımlarla Windows Workflow Foundation (WF), performans içerir.  Bu yeni bir düzeltme önemli tasarım değişiklikleri önceki sürümlerinden tanıtır [!INCLUDE[wf1](../../../includes/wf1-md.md)] .NET Framework 3.0 bir parçası olarak gönderilen ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Programlama modeli, çalışma zamanı ve performansı ve kullanılabilirliği büyük ölçüde artırmak için araç setinin bir mimariye kavuşturulan olmuştur. Bu konu, bu değişiklikleri önemli performans özellikleri gösterir ve bu önceki sürüme karşı karşılaştırır.  
  
 Tek bir iş akışı bileşen performansı, WF3 WF4 arasındaki onlarca kat artırdı.  Windows Communication Foundation (WCF) hizmetlerini elle kodlanmış ve oldukça küçük olacak şekilde WCF iş akışı hizmetleri arasında boşluk bırakır.  İş akışı gecikme süresi içinde WF4 önemli ölçüde azalttı.  Kalıcılık performans 2.5 3.0 faktörüyle arttı.  İş akışı izleme yoluyla sistem durumu izleme önemli ölçüde daha az yüke sahiptir.  Bu, geçiş veya uygulamalarınızda WF4 benimsemek için neden cazip.  
  
## <a name="terminology"></a>Terminoloji  
 Sürümü [!INCLUDE[wf1](../../../includes/wf1-md.md)] sunulan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] için bu konunun geri kalanı için WF4 anılacaktır.  [!INCLUDE[wf1](../../../includes/wf1-md.md)] .NET 3.0 kullanılmıştır ve birkaç küçük düzeltmeden sahipti [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] SP1. [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Workflow Foundation sürümü başvurulabilir WF3 bu konunun geri kalanı için. WF3 gönderildiği [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] yan yana WF4 ile. WF3 yapılara WF4 geçirme hakkında daha fazla bilgi için bkz: [Windows Workflow Foundation 4 Geçiş Kılavuzu](https://go.microsoft.com/fwlink/?LinkID=153313)  
  
 Windows Communication Foundation (WCF) hizmet yönelimli uygulamalar oluşturmak için Microsoft'un programlama modelidir. İlk .net 3.0 WF3 birlikte bir parçası olarak kullanıma sunulmuştur ve artık'in temel bileşenlerinden biri olan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Windows Server AppFabric oluşturun, ölçek ve Web uygulamaları ve IIS'de çalışan bileşik uygulamaları yönetmek kolaylaştıran tümleşik teknoloji kümesidir. Hizmetleri ve iş akışlarını yönetme ve izleme araçları sağlar. Daha fazla bilgi için [Windows Server AppFabric](https://msdn.microsoft.com/windowsserver/ee695849.aspx)  
  
## <a name="goals"></a>Hedefleri  
 Bu konu başlığının hedefi farklı senaryolar için ölçülen verilerle WF4 performans özellikleri göstermektir. Ayrıca WF4 WF3 arasındaki ayrıntılı karşılaştırmalarıdır sağlar ve bu nedenle yeni bu düzeltmede yapılan önemli geliştirmeler gösterir. Senaryolar ve bu makalede gösterilen verileri temel maliyetleri WF4 ve WF3 farklı yönlerini de ölçme. Bu veriler WF4 performans özellikleri anlamak yararlı ve WF3 geçişleri WF4 için planlama veya uygulama geliştirmesinde WF4 kullanarak yararlı olabilir. Ancak, bu makaledeki sunulan veriler ile sonuçları içinde dikkatli olunması. Bir bileşik iş akışı uygulamasının performansını, yüksek oranda bağımlı iş akışını nasıl uygulandığını ve farklı bileşenleri ile tümleştirilmiştir. Bir uygulama performans özelliklerini belirlemek için her bir uygulama ölçmeniz gerekir.  
  
## <a name="overview-of-wf4-performance-enhancements"></a>WF4 performans geliştirmelerini genel bakış  
 WF4 dikkatli bir şekilde tasarlanmış ve yüksek performans ve ölçeklenebilirlik aşağıdaki bölümlerde açıklanan ile uygulanmıştır.  
  
### <a name="wf-runtime"></a>WF çalışma zamanı  
 Setinin merkezinde [!INCLUDE[wf1](../../../includes/wf1-md.md)] yürütme etkinliklerinin bir iş akışında yönlendiren bir zaman uyumsuz bir zamanlayıcı çalışma zamanıdır. Bu yüksek performanslı, etkinlikler için öngörülebilir yürütme ortamı sağlar. Ortamda yürütme, devamlılık, tamamlama, iptal, özel durumlar ve öngörülebilir bir iş parçacığı modeli için iyi tanımlanmış bir sözleşme var.  
  
 WF3 kolaylığına WF4 çalışma zamanı daha verimli bir zamanlayıcı var. Bu, toplu iş öğelerini yürütülürken en çok verimli olan WCF için kullanılan g/ç iş parçacığı havuzu yararlanır. İç iş öğesi Zamanlayıcı sıranın en sık karşılaşılan kullanım desenleri için optimize edilmiştir. WF4 çalışma zamanı yürütme durumları en az bir eşitleme ve olay ağır olay kaydı ve karmaşık eşitleme için durum geçişlerini gerçekleştirmek için çağırma WF3 bağlıdır ancak mantıksal, işleme çok hafif bir yolla da yönetir.  
  
### <a name="data-storage-and-flow"></a>Veri depolama ve akış  
 WF3 içinde tür tarafından uygulanan bağımlılık özellikleri aracılığıyla bir etkinlikle ilişkili verileri modellenmiştir <xref:System.Windows.DependencyProperty>. Bağımlılık özelliği desenini Windows Presentation Foundation (WPF) kullanıma sunulmuştur. Genel olarak, bu düzen kolay veri bağlama ve diğer kullanıcı Arabirimi özellikleri desteklemek için çok esnektir. Ancak, deseni, iş akışı tanımında statik alanlar olarak tanımlanması için özellikleri gerektirir. Her [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanı özellik değerlerini alır veya ayarlar, yoğun ağırlıklı arama mantığı içerir.  
  
 WF4 mantığı kapsam verileri Temizle bir iş akışında verilerin nasıl işlendiğini büyük ölçüde artırmak için kullanır. İki farklı kavram kullanarak etkinlik sınırları boyunca akan verileri etkinliği depolanan veriler ayırır: değişkenler ve bağımsız değişkenler. Değişkenleri ve ", / Out/Inout" bağımsız değişkenler için clear hiyerarşik bir kapsamı kullanarak, etkinlikler için veri kullanımı karmaşıklığı önemli ölçüde azaltılır ve veri ömrünü da otomatik olarak kapsamlıdır. Etkinlikler, kendi bağımsız değişken tarafından açıklanan iyi tanımlanmış bir imzaya sahip. Bir etkinlik inceleyerek hangi verileri almak için bekliyor ve hangi verilerin tarafından yürütülmesinin bir sonucu olarak üretilecek belirleyebilirsiniz.  
  
 Bir iş akışı oluşturulurken WF3 içinde etkinlikleri hazırlaması başlatılmış. Yalnızca ilgili etkinlikleri yürütürken WF 4'te etkinlikleri başlatılır. Bu yeni bir iş akışı örneği oluşturulduğunda ve bu nedenle daha fazla verimlilik elde ettiği başlatma/Uninitialize işlemleri gerçekleştirmeden daha basit bir etkinlik yaşam döngüsü sağlar  
  
### <a name="control-flow"></a>Denetim Akışı  
 Herhangi bir programlama dilinde olduğu gibi [!INCLUDE[wf1](../../../includes/wf1-md.md)] sıralama, döngü, dallanma ve desenler için denetim akışı etkinlikleri kümesi sunarak iş akışı tanımları için Denetim akışları için destek sağlar. İçinde aynı etkinlik, yeni bir yeniden yürütülür gerektiğinde WF3 <xref:System.Workflow.ComponentModel.ActivityExecutionContext> oluşturulur ve etkinlik dayalı bir ağır serileştirme ve seri durumundan çıkarma mantık aracılığıyla kopyalanan <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Genellikle performans yinelemeli denetim akışı için bir etkinlik dizisini çalıştırma daha yavaştır.  
  
 WF4 bu oldukça farklı işler. Etkinlik şablonunu alıp, yeni bir ActivityInstance nesnesi oluşturur ve Zamanlayıcı kuyruğa ekler. Tüm bu işlem yalnızca açık nesne oluşturma içerir ve çok hafif.  
  
### <a name="asynchronous-programming"></a>Zaman uyumsuz programlama  
 Uygulamalar genellikle daha iyi performans ve ölçeklenebilirlik g/ç gibi uzun süre çalışan engelleme işlemleri veya dağıtılmış bilgi işlem işlemleri için zaman uyumsuz programlama ile sahiptir. Temel etkinlik türleri aracılığıyla zaman uyumsuz destek WF4 sağlar <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.AsyncCodeActivity%601>. Çalışma zamanı zaman uyumsuz etkinlikler yerel olarak anlıyor ve zaman uyumsuz iş bekleyen olmakla birlikte bu nedenle otomatik olarak örnek no-persist bölgesinde koyabilirsiniz. Özel etkinlikler iş akışı Zamanlayıcı iş parçacığı bulunduran ve paralel olarak çalıştırmak için herhangi bir etkinlik engelleme olmadan zaman uyumsuz çalışmayı gerçekleştirmek için bu türlerinden türeyebilir.  
  
### <a name="messaging"></a>İleti  
 Başlangıçta WF3 çok olan dış olayları ya da web aracılığıyla sınırlı Mesajlaşma destek hizmetleri çağrıları. .NET 3.5, iş akışları WCF istemcileri olarak uygulanan veya WCF hizmetleri kullanıma sunulan <xref:System.Workflow.Activities.SendActivity> ve <xref:System.Workflow.Activities.ReceiveActivity>. WF4 içinde iş akışı tabanlı bir Mesajlaşma programlama kavramı daha sıkı bir tümleştirme WCF, WF mantığının Mesajlaşma aracılığıyla güçlendirilmiş.  
  
 WCF .net 4'te sunulan birleşik ileti işleme işlem hattı, önemli ölçüde daha iyi performans ve ölçeklenebilirlik WF3 daha WF4 Hizmetleri yardımcı olur. WF4, karmaşık ileti Exchange desenleri (MEPs) modelleyebilir daha zengin Mesajlaşma programlama desteği de sağlar. Geliştiriciler, ya da yazılı Hizmet sözleşmeleri, kolay bir programlama veya türsüz hizmet sözleşme serileştirme maliyetler için ödeme gerek kalmadan daha iyi performans elde etmek için elde etmek için kullanabilirsiniz. İstemci tarafı önbelleğe alma desteği aracılığıyla kanal <xref:System.ServiceModel.Activities.SendMessageChannelCache> WF4 sınıfında geliştiricilerin çok az bir çabayla hızlı uygulamalar oluşturmasına yardımcı olur. Daha fazla bilgi için [etkinlikleri göndermek için önbellek paylaşımı düzeylerini değiştirme](../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).  
  
### <a name="declarative-programming"></a>Bildirim temelli programlama  
 WF4 bir temiz ve basit tanımlayıcı programlama çerçevesi model iş süreçleri ve hizmetleri sağlar. Tam bildirim temelli etkinliklerle, hiçbir kod-iş akışı yazma büyük ölçüde basitleştirme yanında, oluşumunu programlama modelini destekler. İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], tek bir derlemeye hem WPF ve WF desteklemek için System.Xaml.dll XAML tabanlı bildirime dayalı programlama çerçevesi birleşik.  
  
 XAML WF4, gerçek anlamda bildirim temelli bir deneyim sağlar ve etkinlikleri ve .NET kullanarak yerleşik türlerine başvuran tüm iş akışı tanımı için XML biçimlendirme içinde tanımlanmasına izin verir. Özel arka plan kod mantığının işe karıştırılmaksızın WF3 içinde XOML biçimi ile yapmak zordu. Yeni XAML yığın .net 4'te, serileştirme/iş akışı yapıtları seri durumdan çıkarılırken çok daha iyi performans sahiptir ve bildirim temelli programlama daha cazip ve sağlam hale getirir.  
  
### <a name="workflow-designer"></a>İş Akışı Tasarımcısı  
 Tam bildirim temelli programlama desteği WF4 açıkça daha büyük iş akışları için tasarım zamanı performans gereksinimleri getirir. İş Akışı Tasarımcısı'nda WF4 WF3 için daha büyük iş akışları için çok daha yüksek ölçeklenebilirlikten sahiptir. Bir iş akışı birkaç yüz etkinliklerin WF3 tasarımcı ile yüklemek neredeyse imkansız olduğu sürece kullanıcı Arabirimi sanallaştırma desteği sayesinde, Tasarımcı kolayca 1000 etkinlik büyük bir iş akışı birkaç saniye içinde yükleyebilirsiniz.  
  
## <a name="component-level-performance-comparisons"></a>Bileşen düzeyinde performans karşılaştırmaları  
 Bu bölümde WF3 ve WF4 iş akışlarında etkinlikler arasında doğrudan bir karşılaştırma verilerini içerir.  Kalıcılık gibi önemli alanlardan performans etkinliği ayrı Bileşenler'den daha çok büyük bir etkiye sahip.  Bileşenleri artık düzenleme el kodlanmış mantıksal karşı Karşılaştırılacak hızlı olduğundan WF4 bileşenleri tek tek'taki performans iyileştirmelerinden yine de önemlidir.  Bir örneği, sonraki bölümde ele alınmıştır: "Hizmetleri oluşturma senaryosu."  
  
### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performans sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
 Yukarıdaki şekilde, bileşen düzeyinde performans ölçümü için kullanılan makine yapılandırmasını gösterir. Tek bir sunucu ve beş istemciler üzerinde bir 1 GB/sn Ethernet ağ arabirim bağlı. Kolay ölçümleri için sunucu Windows Server 2008 x86 çalıştıran bir çift proc/dört çekirdek sunucusunun tek bir çekirdek kullanmak için yapılandırılmış. CPU kullanımı sistem neredeyse % 100 oranında korunur.  
  
### <a name="test-details"></a>Test ayrıntıları  
 WF3 <xref:System.Workflow.Activities.CodeActivity> büyük olasılıkla bir WF3 iş akışında kullanılabilecek basit bir etkinliktir.  Etkinlik iş akışı programcının özel kod içine koyabilirsiniz kodu arka plan içindeki bir yöntemi çağırır.  WF4 içinde hiçbir karşılıklarına WF3 yoktur <xref:System.Workflow.Activities.CodeActivity> aynı işlevselliği sağlar.  Unutmayın bir <xref:System.Activities.CodeActivity> temel sınıfta WF3 için ilgili olmayan WF4 <xref:System.Workflow.Activities.CodeActivity>.  Özel etkinlikler ve yalnızca XAML iş akışları oluşturmak için iş akışı yazarları önerilir.  Bir etkinlik testlerinde adlı `Comment` yerine boş bir kullanılan <xref:System.Workflow.Activities.CodeActivity> WF4 iş akışlarında.  Kodda `Comment` etkinlik aşağıdaki gibidir:  
  
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
  
### <a name="single-activity"></a>Tek Etkinlik  
 Bir alt etkinlik içeren bir sıralı iş akışı iş akışıdır.  Etkinlik bir <xref:System.Workflow.Activities.CodeActivity> WF3 durumda kod olmadan ve `Comment` etkinlik WF4 durumda.  
  
### <a name="while-with-1000-iterations"></a>While 1000 yineleme ile  
 Bir sıralı iş akışı içeren <xref:System.Activities.Statements.While> etkinliği ile bir alt etkinlik Döngüdeki herhangi bir iş yapmaz.  
  
### <a name="replicator-compared-to-parallelforeach"></a>Çoğaltıcı ParallelForEach için karşılaştırma  
 <xref:System.Workflow.Activities.ReplicatorActivity> sıralı ve Paralel yürütme modları WF3 vardır.  Sıralı modunda etkinliğe ilişkin performans benzer <xref:System.Workflow.Activities.WhileActivity>.  <xref:System.Workflow.Activities.ReplicatorActivity> Paralel yürütme için kullanışlıdır.  Bu WF4 analog olan <xref:System.Activities.Statements.ParallelForEach%601> etkinlik.  
  
 Aşağıdaki diyagramda, bu test için kullanılan iş akışlarını gösterir. WF3 iş akışı sol tarafta ve WF4 iş akışı sağ tarafta.  
  
 ![WF3 ReplicatorActivity ve WF4 ParallelForEach](../../../docs/framework/windows-workflow-foundation/media/replicatorandparallelforeach.gif "ReplicatorAndParallelForEach")  
  
### <a name="sequential-workflow-with-five-activities"></a>Beş etkinlikleri olan sıralı iş akışı  
 Bu test, sıralı biçimde yürütmek birkaç etkinliği olan etkisini göstermek için tasarlanmıştır.  Sırayla beş etkinlikler vardır.  
  
### <a name="transaction-scope"></a>İşlem kapsamı  
 Her yineleme için yeni bir iş akışı örneği oluşturulmamış işlem kapsamı test diğer testlerden biraz farklıdır.  Bunun yerine, iş akışı biraz ile yapılandırılmış döngü içeren bir <xref:System.Activities.Statements.TransactionScope> hiçbir çalışır, tek bir etkinlik içeren etkinlik.  Her bir toplu 50 yinelemelerin while aracılığıyla döngü, tek bir işlem olarak sayılır.  
  
### <a name="compensation"></a>Dengeleme  
 Adlı tek bir üst öğesi dengelenebilir etkinlik WF3 iş akışı sahip `WorkScope`.  Yalnızca bir etkinlik uygulayan <xref:System.Workflow.ComponentModel.ICompensatableActivity> arabirimi:  
  
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
  
 Hata işleyicisi hedefleri `WorkScope` etkinlik. WF4 iş akışı eşit basit kalıyor.  A <xref:System.Activities.Statements.CompensableActivity> gövde ve bir dengeleme işleyicisini vardır.  Bir açık compensate dizideki sonraki.  Gövde etkinliği ve maaş işleyicisi etkinliği boş hem uygulamalardır:  
  
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
  
 ![WF3 ve WF iş akışlarını temel maaş](../../../docs/framework/windows-workflow-foundation/media/basiccompensationworkflows.gif "BasicCompensationWorkflows")  
  
 Şekil 2 – WF3 (solda) ve WF4 (sağda) temel Maaş iş akışları  
  
### <a name="performance-test-results"></a>Performans testi sonuçları  
 ![Performans testi sonuçları](../../../docs/framework/windows-workflow-foundation/media/performancedata.gif "PerformanceData")  
  
 ![Performans testi veri grafiği](../../../docs/framework/windows-workflow-foundation/media/performancetestchart.gif "PerformanceTestChart")  
  
 Tüm testler, iş akışlarında işlem kapsamı test dışında saniye başına ölçülür.  Yukarıdaki görüldüğü gibi [!INCLUDE[wf1](../../../includes/wf1-md.md)] panosunda, özellikle while gibi aynı etkinliğin birden çok yürütme gerektiren alanları genelinde çalışma zamanı performansı geliştirildi döngü.  
  
## <a name="service-composition-scenario"></a>Hizmetleri oluşturma senaryosu  
 "Bileşen düzeyinde performans karşılaştırma," önceki bölümde gösterildiği gibi ek yüküne WF3 WF4 arasındaki önemli bir azalma olmuştur.  WCF iş akışı Hizmetleri artık el kodlanmış WCF hizmetleri performansını neredeyse eşleşen ancak tüm avantajlarını çözümlenmedi [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanı.  Bu test senaryosu WF4 WCF iş akışı hizmetinde bir WCF Hizmeti karşılaştırır.  
  
### <a name="online-store-service"></a>Çevrimiçi Store hizmeti  
 Windows Workflow Foundation'ın gücünü birkaç hizmet kullanan işlemleri oluşturma olanağı biridir.  Bu örnekte, bir sipariş satın almak için iki hizmet çağrıları düzenleyen bir çevrimiçi mağaza hizmeti yok.  İlk adım bir sipariş doğrulama hizmetini kullanarak sırasını doğrulamaktır.  İkinci adım, ambarı hizmetini kullanmaya sırasını doldurmaktır.  
  
 İki arka uç Hizmetleri, sipariş doğrulama hizmeti ve ambar hizmeti, her iki testler için aynı kalır.  Değişiklikleri bölümü çevrimiçi Store düzenleme gerçekleştiren hizmettir.  Bir durumda, bir WCF hizmeti olarak ele kodlanmış hizmetidir.  Diğer bir olay için hizmet WF4 WCF iş akışı hizmetinde olarak yazılır. [!INCLUDE[wf1](../../../includes/wf1-md.md)]-İzleme ve Kalıcılık bu test için kapalı gibi belirli özellikleri.  
  
### <a name="environment"></a>Ortam  
 ![İş akışı performans sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
 İstemci istekleri, birden çok bilgisayarda çevrimiçi Store hizmetine HTTP üzerinden yapılır.  Tek bir bilgisayar, tüm üç hizmeti barındırır.  Çevrimiçi Store hizmeti ve arka uç hizmetleri arasında Aktarım katmanı, TCP veya HTTP ' dir.  Ölçü işlem/saniye sayısına dayanır tamamlanmış `PurchaseOrder` çevrimiçi Store hizmetine yapılan çağrılar.  Kanal havuzu yeni WF4 içinde kullanılabilen bir özelliktir.  Basit bir havuzu oluşturma tekniği el kodlanmış bir uyarlamasını çevrimiçi Store hizmette kullanılan şekilde WCF'de kullanıma hazır bu test kanal havuz bölümü sağlanmadı.  
  
### <a name="performance"></a>Performans  
 ![Çevrimiçi Store hizmeti performans grafiği](../../../docs/framework/windows-workflow-foundation/media/onlinestoreperfgraph.gif "OnlineStorePerfGraph")  
  
 Kanal havuzu olmadan arka uç TCP hizmetlere bağlanma [!INCLUDE[wf1](../../../includes/wf1-md.md)] hizmeti, aktarım hızını %17,2 etkiye sahiptir.  Kanal havuzu ile yaklaşık %23,8 cezasına sebep olur.  HTTP için çok daha az olmasının etkisidir: havuzu olmadan %4,3 ve 8.1 havuzu ile %.  Kanal havuzu çok az avantajı HTTP kullanırken sağladığını unutmayın.  
  
 Varken yükü bu testteki el kodlanmış WCF Hizmeti ile karşılaştırıldığında WF4 çalışma zamanının, iki katına senaryo değerlendirilebilir.  Bu testteki iki arka uç Hizmetleri, çok az iş yapın.  Gerçek için uçtan uca bir senaryoda, bu hizmetler, veritabanı çağrıları, Aktarım katmanı performans etkisini daha az önemli yapma gibi daha pahalı işlemler gerçekleştirmelisiniz.  Bu artı WF4 içinde kullanılabilir özelliklerden avantajlarını Workflow Foundation düzenleme hizmetleri oluşturmak için uygulanabilir bir seçenek yapar.  
  
## <a name="key-performance-considerations"></a>Ana performans konuları  
 Birlikte çalışma, hariç olmak üzere bu bölümdeki özellik alanları, WF4 WF3 arasında önemli ölçüde değişti.  Bu tasarım performansının yanı sıra iş akışı uygulamaları etkiler.  
  
#### <a name="workflow-activation-latency"></a>İş akışı etkinleştirme gecikmesi  
 WCF iş akışı hizmeti uygulaması içinde yeni bir iş akışı başlatma veya varolan bir iş akışı yüklenirken için gecikme süresi, engelleme gibi önemlidir.  Bu test çalışması, tipik bir senaryoda bir WF4 XAMLX konağa karşı WF3 XOML konak ölçer.  
  
##### <a name="environment-setup"></a>Ortam Kurulumu  
 ![Gecikme süresi ve aktarım hızı testler için ortam Kurulumu](../../../docs/framework/windows-workflow-foundation/media/latencyandthroughputenvironment.gif "LatencyAndThroughputEnvironment")  
  
##### <a name="test-setup"></a>Test Kurulumu  
 Senaryoda bir istemci bilgisayara içerik temelli bağıntı kullanarak bir WCF iş akışı hizmeti ile iletişim kurar.  Bağlam bağıntı özel bağlam bağlama gerektirir ve iletileri için doğru iş akışı örneği ilişkilendirmek için bir bağlam üst bilgi veya tanımlama bilgisi kullanır.  Bir performans, bağıntı kimliği, ileti gövdesi ayrıştırılacak gerek kalmayacak şekilde ileti üstbilgisinde bulunur fayda var. Bağlam bağıntı hakkında daha fazla bilgi için bkz: [bağlam değişimi bağıntısı](../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
  
 Hizmet isteği ile yeni bir iş akışı oluşturma ve anlık bir yanıt gönderin, böylece gecikme süresi ölçümü iş akışını çalıştıran geçen süre dahil değildir.  WF3 iş akışı XOML arka plan kod ile ve WF4 iş akışı tamamen XAML.  WF4 iş akışı şöyledir:  
  
 ![WF 4 bağıntı kapsam](../../../docs/framework/windows-workflow-foundation/media/correlationscopeworkflow.gif "CorrelationScopeWorkflow")  
  
 <xref:System.ServiceModel.Activities.Receive> Etkinlik iş akışı örneği oluşturur.  Alınan iletide geçirilen bir değer yanıt iletisinde okunmaz.  Yanıt aşağıdaki bir dizi iş akışının geri kalanı içerir.  Yukarıdaki durumda, yalnızca bir yorum etkinliği gösterilmektedir.  Açıklama etkinlik sayısı, iş akışı karmaşıklığı benzetimini yapmak için değiştirilir.  Bir yorum etkinliği için bir WF3 eşdeğerdir <xref:System.Workflow.Activities.CodeActivity> , hiçbir çalışma gerçekleştirir. Açıklama etkinliği hakkında daha fazla bilgi için bu makalenin önceki kısımlarında "bileşen düzeyinde performans karşılaştırması" bölümüne bakın.  
  
##### <a name="test-results"></a>Test Sonuçları  
 ![Gecikme süresi sonuçları](../../../docs/framework/windows-workflow-foundation/media/latencyresultsgraph.gif "LatencyResultsGraph")  
  
 3 – Durgun şekil ve normal WCF iş akışı hizmetleri için gecikme süresi  
  
 Yukarıdaki grafikte, soğuk servis talebini başvuruyor değil mevcut olduğunda <xref:System.ServiceModel.WorkflowServiceHost> belirtilen iş akışı için.  Diğer bir deyişle, iş akışı, ilk kez kullanılıyor ve derlenmesi gereken XOML veya XAML soğuk bir gecikme olur.  Sıcak gecikme süresi, iş akışı türü zaten derlendikleri zaman yeni bir iş akışı örneği oluşturmak için saattir.  İş akışı karmaşıklığını WF4 durumda tutulmaları şeylerdir ancak WF3 durumda doğrusal ilerlemeyi sahip değil.  
  
#### <a name="correlation-throughput"></a>Bağıntı aktarım hızı  
 WF4 yeni bir içerik temelli bağıntı özelliği sunmaktadır.  Yalnızca içerik temelli bağıntı WF3 sağlanır.  İçerik temelli bağıntı yalnızca belirli WCF kanal bağlamaları yapılabilir.  İş akışı kimliği, ileti üst bilgisi içinde bu bağlamaları kullanırken eklenir.  WF3 çalışma zamanı yalnızca kendi kimliğine göre bir iş akışı tanımlayabilir  İçerik temelli bağıntı ile iş akışı Yazar hesap numarası veya müşteri kimliği gibi verilerle ilgili bir parçasını dışında bir bağıntı anahtar oluşturabilirsiniz. İçerik temelli bağıntı hakkında daha fazla bilgi için bkz. [içeriğe dayalı bağıntı](../../../docs/framework/wcf/feature-details/content-based-correlation.md).  
  
 Bağıntı anahtar ileti üstbilgisinde bulunan, içerik temelli bağıntı performans avantajı vardır.  Anahtar sona erdirme olanağı-serialization/ileti kopyalama olmadan iletisi okuyabilirsiniz.  İçerik temelli bağıntı bağıntı anahtar ileti gövdesi içinde depolanır.  Bir XPath ifadesi anahtarı bulmak için kullanılır.  Bu ek işlem maliyetini ileti gövdesi ve anahtar sayısı anahtarı derinliğini boyutuna bağlıdır.  Bu test, içerik ve içerik temelli bağıntı karşılaştırır ve ayrıca birden çok anahtar kullanırken performans düşüşü gösterir.  
  
#### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performans sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
#### <a name="test-setup"></a>Test Kurulumu  
 ![Bağıntı işleme iş akışı Test](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputworkflow.gif "CorrelationThroughputWorkflow")  
  
 Yukarıda gösterilen "Kalıcılık" bölümünde kullanılan hizmet örneğiyle aynı iş akışıdır.  Kalıcılık olmadan bağıntı testler için çalışma zamanı'nda yüklü bir Kalıcılık sağlayıcı yok.  Bağıntı iki yerde oluşur: CreateOrder ve CompleteOrder.  
  
#### <a name="test-results"></a>Test Sonuçları  
 ![Bağıntı aktarım hızı](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputgraph.gif "CorrelationThroughputGraph")  
  
 Bu grafik, içerik temelli bağıntı artışlar kullanılan anahtar sayısı olarak performans gösterir.  Bu iletişim kuralları ile ilgili ek yükü TCP ve HTTP arasında eğrileri içinde benzerlik gösterir.  
  
#### <a name="correlation-with-persistence"></a>Yurt içi hasıla ile kalıcılığı  
 Kalıcı bir iş akışı ile CPU baskısı içerik temelli bağıntı alanından SQL veritabanına iş akışı çalışma zamanını şuradan kaydırır.  SQL kalıcı bir sağlayıcı saklı yordamları, uygun iş akışı bulmak için anahtarları eşleşen iş yapın.  
  
 ![Bağıntı ve Kalıcılık sonuçları](../../../docs/framework/windows-workflow-foundation/media/correlationandpersistencegraph.gif "CorrelationAndPersistenceGraph")  
  
 İçerik temelli bağıntı hala içerik temelli bağıntı hızlıdır.  Ancak, fark Kalıcılık daha fazla bağıntı performans üzerindeki etkisi olarak daha az belirgin olur.  
  
### <a name="complex-workflow-throughput"></a>Karmaşık iş akışı işleme  
 Bir iş akışı karmaşıklığını yalnızca etkinlikleri sayısına göre ölçülmez.  Bileşik etkinlikleri birçok alt içerebilir ve alt bileşik etkinlikleri de olabilir.  İç içe geçmiş bir artış düzeylerini sayısı arttıkça, bu nedenle şu anda yürütülen durumunda olabilir etkinliklerin sayısını ve durumda olabilecek bir değişken sayısı yapar.  Bu test, karmaşık iş akışı yürütülürken işleme WF3 WF4 arasındaki karşılaştırır.  
  
### <a name="test-setup"></a>Test Kurulumu  
 Bu testler, üzerinde bir Intel Xeon X5355 2.66 GHz 4 yönlü bilgisayar @ 4 GB RAM çalıştıran Windows Server 2008 x64 yürütüldü.  Test kodu, % 100 CPU kullanımına ulaşmak için çekirdek başına tek bir iş parçacığı ile tek bir işlemde çalıştırır.  
  
 Bu test için oluşturulan iş akışları iki ana değişkene sahiptir: derinliği ve her bir dizideki etkinlik sayısı.  Her derinlik düzeyini döngü, kararlar, atamalarını ve dizileri sırasında paralel bir etkinlik içerir.  Aşağıda gösterilen WF4 tasarımcısında, üst düzey akış çizelgesi Resimli.  Her akış çizelgesi etkinlik ana akış benzer.  Bu iş akışı derinliği test parametreleri için sınırlı olduğu picturing olduğunda bir düzgünleştiren parçalı dikkate almak yararlı olabilir.  
  
 Belirli bir testi etkinliklerin sayısını derinliği ve dizisi başına etkinlik sayısı tarafından belirlenir.  Aşağıdaki denklemi WF4 test etkinliklerin sayısını hesaplar:  
  
 ![Etkinliklerin sayısını hesaplamak için eşitlik](../../../docs/framework/windows-workflow-foundation/media/numberofactivitiesequation.gif "NumberOfActivitiesEquation")  
  
 WF3 testin etkinlik sayısı, ek bir sıra nedeniyle biraz farklı bir eşitlik ile hesaplanabilir:  
  
 ![Etkinliklerin sayısını hesaplamak için eşitlik](../../../docs/framework/windows-workflow-foundation/media/w3numberofactivitiesequation.gif "W3NumberOfActivitiesEquation")  
  
 D derinliği olduğu ve etkinliği dizisi her sayısıdır.  Bu denklemler ardındaki mantığı ilk sabit zaman çarpılarak emin olup dizileri sayısı ve statik düzeyine etkinliklerin sayısını ikinci sabittir.  Her akış üç akış alt etkinlik vardır.  Alt derinliği düzeyde, bu akış çizelgeleri boş ancak diğer düzeylerde bunlar ana akış kopyalarını.  Aşağıdaki tabloda her test değişim ait iş akışı tanımında etkinliklerinin sayısı gösterilir:  
  
 ![Her testte kullanılan etkinliklerin sayısını karşılaştıran](../../../docs/framework/windows-workflow-foundation/media/comparechart.gif "CompareChart")  
  
 İş akışı tanımında etkinliklerin sayısını keskin ile her derinlik düzeyini artırır.  Karar noktası başına yalnızca bir yol yürütülür, ancak belirli bir iş akışı örneğinde, gerçek etkinliklerin yalnızca küçük bir kısmı yürütülür.  
  
 ![Karmaşık iş akışı](../../../docs/framework/windows-workflow-foundation/media/complexworkflowthroughputworkflow.gif "ComplexWorkflowThroughputWorkflow")  
  
 Eşdeğer bir iş akışı için WF3 oluşturuldu. WF3 Tasarımcı iş akışının tamamını tasarımı alanında yerine iç içe geçme, bu nedenle, bu konu başlığında görüntülenecek çok büyük gösteriyor. İş akışının bir parçacığı aşağıda gösterilmiştir.  
  
 ![WF3 İş akışı](../../../docs/framework/windows-workflow-foundation/media/wf3workflow.gif "WF3Workflow")  
  
 İç içe bir olağanüstü durumda kullanmak için bu testin bir parçası olan başka bir iş akışı 100 iç içe geçmiş sıralar kullanır.  En içteki içinde tek bir dizidir `Comment` veya <xref:System.Workflow.Activities.CodeActivity>.  
  
 ![İç içe dizileri](../../../docs/framework/windows-workflow-foundation/media/nestedsequencewf.gif "NestedSequenceWF")  
  
 Bu testin bir parçası olarak, izleme ve Kalıcılık kullanılmaz.  
  
### <a name="test-results"></a>Test Sonuçları  
 ![Üretilen iş grafiklerini](../../../docs/framework/windows-workflow-foundation/media/testresults1.gif "TestResults1")  
  
 Daha karmaşık iş akışlarıyla derinliği çok sayıda ve çok sayıda etkinlikleri performans sonuçlarını bu makalenin önceki bölümlerinde gösterilen diğer aktarım hızı numaralarının tutarlıdır.  WF4'ın aktarım hızı kat daha hızlı ve Logaritmik ölçekte Karşılaştırılacak vardır.  
  
### <a name="memory"></a>Bellek  
 Windows Workflow Foundation bellek yükü iki önemli alanda ölçülür: iş akışı karmaşıklığı ve iş akışı tanımları sayısı.  Bellek ölçümleri, Windows 7 64-bit istasyonunda alınmıştır.  Çalışma kümesi boyutu performans sayaçlarını izleme, Environment.WorkingSet yoklama veya VMMap kullanılabilir gibi bir araç kullanarak gibi ölçüsü elde etmek için birçok yolu vardır [VMMap](https://technet.microsoft.com/sysinternals/dd535533.aspx). Yöntemlerin bir bileşimi elde edilir ve her test sonuçlarını doğrulamak için kullanıldı.  
  
### <a name="workflow-complexity-test"></a>İş akışı karmaşıklığı Test  
 Bir iş akışı karmaşıklığı fark çalışma kümesi iş akışı karmaşıklığı test ölçer.  Önceki bölümde kullanılan karmaşık iş akışlarının yanı sıra yeni çeşitlemeleri iki temel servis taleplerini karşılamak için eklenir: tek bir etkinlik iş akışı ve 1000 etkinliklerle bir dizisi.  Bu testler için iş akışlarını başlatılır ve tek bir seri döngü tamamlanmasında bir dakikalık bir süre için çalıştırılır.  Her test değişim üç kez çalışır ve kaydedilen bilgiler bu üç çalıştırması ortalamasıdır.  
  
 İki yeni temel testleri gibi aşağıda gösterilen şekilde iş akışları sahiptir:  
  
 ![Karmaşık iş akışları](../../../docs/framework/windows-workflow-foundation/media/complexworkflowboth.gif "ComplexWorkflowBoth")  
  
 Yukarıda gösterilen WF3 iş akışında boş <xref:System.Workflow.Activities.CodeActivity> etkinlikleri kullanılır.  Kullanımlar yukarıda WF4 iş akışı `Comment` etkinlikler.  `Comment` Etkinlik bileşen düzeyinde performans karşılaştırmalar bölümü bu makalenin önceki kısımlarında açıklanan.  
  
 ![Bellek kullanımı grafiğinde](../../../docs/framework/windows-workflow-foundation/media/complexmemoryusage.gif "ComplexMemoryUsage")  
  
 Bu grafikte fark Temizle eğilimlerini iç içe geçme bellek kullanımını WF3 hem de WF4 göreceli olarak en az bir etkiye sahip biridir.  Belirli bir iş akışındaki etkinliklerin sayısını en önemli bellek etkisi gelir.  Veri dizisi 1000, karmaşık derinliği 5 dizisi 5 ve karmaşık derinlik 1 7 serisi çeşitlemeleri verildiğinde, etkinliklerin sayısını binlik girdiğinde, bellek kullanım artışı daha belirgin hale işaretlenmemiştir.  (1 derinliği 7 serisi) olağanüstü durumda ~ 29K etkinlikleri olduğu WF4 neredeyse %79 daha az bellek WF3 daha kullanıyor.  
  
### <a name="multiple-workflow-definitions-test"></a>Birden çok iş akışı tanımları Test  
 İş akışı tanımı başına bellek ölçme iki farklı testlere WF3 ve WF4 iş akışlarını barındırmak için kullanılabilir seçenekleri nedeniyle ayrılmıştır.  Belirli bir iş akışı örnekli ve tanımı yalnızca bir kere yürütülen iş akışı karmaşıklığı test değerinden farklı bir şekilde testleri çalıştırın.  İş akışı tanımı ile bunun konağı AppDomain ömrü boyunca bellekte kalır olmasıdır.  Belirtilen iş akışı örneği'ni çalıştırarak kullanılan bellek, çöp toplama sırasında temizlenmelidir.  Geçiş kılavuzunu WF4 için barındırma seçenekleri hakkında daha ayrıntılı bilgi içerir. Daha fazla bilgi için [WF geçiş Kitapçığı: iş akışı barındırma](https://go.microsoft.com/fwlink/?LinkID=153313).  
  
 Bir iş akışı tanımı test için çok iş akışı tanımları oluşturma, çeşitli şekillerde yapılabilir.  Örneği için bir ad dışında aynı olan 1000 iş akışları oluşturmak için kod oluşturmayı kullan ve bu iş akışlarının her ayrı dosyaların kaydedileceği.  Bu yaklaşım, konsolu barındırılan testi yapılmadı.  WF3 içinde <xref:System.Workflow.Runtime.WorkflowRuntime> sınıf, iş akışı tanımları çalıştırmak için kullanıldı.  WF4 olabilir ya da kullanım <xref:System.Activities.WorkflowApplication> doğrudan kullanabilir veya tek bir iş akışı örneği için <xref:System.Activities.WorkflowInvoker> bir yöntem çağrısının değilmiş gibi etkinliği çalıştırmak için.  <xref:System.Activities.WorkflowApplication> bir iş akışı tek örneği çok sayıda ve daha yakın özellik eşliği için <xref:System.Workflow.Runtime.WorkflowRuntime> böylece bu sınamada kullanıldı.  
  
 IIS akışlarında barındırırken kullanmak mümkün mü bir <xref:System.Web.Hosting.VirtualPathProvider> yeni bir <xref:System.ServiceModel.WorkflowServiceHost> tüm XAMLX veya XOML dosyaları oluşturmak yerine.  <xref:System.Web.Hosting.VirtualPathProvider> Gelen isteği işler ve "bir veritabanından yüklendi ya da, bu durumda, çalışma sırasında oluşturulan bir sanal dosya" ile yanıt verir.  Bu nedenle, 1000 fiziksel dosyaları oluşturmak gerekli değildir.  
  
 Konsol testte kullanılan iş akışı tanımları basit sıralı iş akışları ile tek bir etkinlik oldu.  Boş bir tek bir etkinlik oldu <xref:System.Workflow.Activities.CodeActivity> WF3 çalışması için ve bir `Comment` WF4 çalışması için etkinlik.  IIS barındırılan durum iletisi ve bir yanıt gönderme son alınmasına başlangıç iş akışları kullanılır:  
  
 ![İş akışı hizmetleri WF3 ve WF4](../../../docs/framework/windows-workflow-foundation/media/receiveworkflowboth.gif "ReceiveWorkflowBoth")  
  
 Şekil 4-istek/yanıt düzendeki ReceiveActivity ve WF4 iş akışı ile WF3 iş akışı  
  
 Aşağıdaki tabloda çalışma kümesi tek bir iş akışı tanımı ve 1001 tanımları arasında değişiklik gösterir:  
  
|Barındırma seçenekleri|WF3 Çalışma kümesi Delta|WF4 Çalışma kümesi Delta|  
|---------------------|---------------------------|---------------------------|  
|İş akışı konsol uygulaması barındırılan|18 MB|9 MB|  
|IIS barındırılan iş akışı Hizmetleri|446 MB|364 MB|  
  
 İş akışı tanımları IIS'de barındırma nedeniyle çok daha fazla bellek tüketir <xref:System.ServiceModel.WorkflowServiceHost>, ayrıntılı WCF hizmeti yapıları ve işleme mantığı konakla ilişkili ileti.  
  
 Konsolu WF3 içinde iş akışları barındırma için XOML yerine kod da uygulanan.  İçinde WF4 varsayılan XAML kullanmaktır.  XAML derlemesinde gömülü bir kaynak olarak depolanan ve çalışma zamanı sırasında bir iş akışı bir uygulama sağlamak için derlenmiş.  Bu işlemle ilişkili bazı ek yükler vardır.  Kodlanmış iş akışları WF3 ve WF4 arasında adil bir karşılaştırma yapmak için XAML yerine kullanıldı.  WF4 iş akışlarının bir örneği aşağıda gösterilmiştir:  
  
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
  
 Bellek tüketimi etkileyebilecek diğer birçok faktörü vardır. Aynı öneriler tüm yönetilen programlar için geçerli olacaktır.  IIS barındırılan ortamlarda <xref:System.ServiceModel.WorkflowServiceHost> bir iş akışı tanımı için oluşturulan nesne, uygulama havuzu geri dönüştürülmeden kadar bellekte kalır.  Bunu göz önünde uzantıları yazarken tutulmalıdır.  Ayrıca, "Genel" değişkenler (tüm iş akışına kapsamlı değişkenler) kullanmaktan kaçının ve mümkünse değişkenleri kapsamını sınırlamak idealdir.  
  
## <a name="workflow-runtime-services"></a>İş akışı çalışma zamanı Hizmetleri  
  
### <a name="persistence"></a>Kalıcılığı  
 WF3 ve WF4 hem de SQL kalıcı bir sağlayıcı ile gönderin.  WF3 SQL kalıcı bir sağlayıcı iş akışı örneği serileştirir ve bir blobun depolayan basit bir uygulamadır.  Bu nedenle, bu sağlayıcı performansı yoğun iş akışı örneği boyutuna bağlıdır.  WF3 içinde bu belgede daha önce anlatıldığı gibi çeşitli nedenlerle örnek boyutunu artırabilir.  Birçok müşteri, serileştirilmiş bir örnek, bir veritabanında saklamanın hiçbir iş akışı durumunu görünürlük sağladığından varsayılan SQL kalıcı bir sağlayıcı kullanmamayı seçin.  Belirli bir iş akışı, iş akışı kimliği bilmeden bulmak amacıyla bir kalıcı her örneği seri durumdan ve içeriğini inceleyin gerekir.  Bu sorunu çözmek için kendi Kalıcılık sağlayıcıları yazmak birçok geliştiricinin tercih eder.  
  
 WF4 SQL kalıcı bir sağlayıcı, bu sorunlar bazılarını ele almak çalıştı.  Kalıcılık tablolar active yer işaretleri ve promotable özellikleri gibi belirli bilgileri ortaya çıkarır.  WF4 yeni içerik temelli bağıntı özelliği de kalıcı iş akışı örneği bir kuruluştaki bazı değişiklik yürütmüştür WF3 SQL Kalıcılık yaklaşımı kullanarak işlemi.  Bu kalıcı bir sağlayıcı işini daha karmaşık hale getirir ve veritabanı üzerinde ek yük getirir.  
  
### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performans sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-setup"></a>Test Kurulumu  
 Hatta bir gelişmiş özellik kümesi ve daha iyi eşzamanlılık işleme ile WF4 SQL Kalıcılık sağlayıcı WF3 sağlayıcısında hızlıdır.  Bu göstermek için aşağıda WF3 ve WF4 temelde aynı işlemleri gerçekleştirme iki iş akışları karşılaştırılır.  
  
 ![Kalıcılık iş akışları](../../../docs/framework/windows-workflow-foundation/media/persistworkflow.gif "PersistWorkflow")  
  
 Şekil 5 – WF3 üzerinde iş akışı kalıcılığı sol ve sağ taraftaki WF4  
  
 İki iş akışları her ikisi tarafından alınan bir ileti oluşturulur.  Bir ilk yanıt gönderdikten sonra iş akışı kalıcı hale getirilir.  WF3 durumda, boş bir <xref:System.Workflow.ComponentModel.TransactionScopeActivity> Kalıcılık başlatmak için kullanılır.  Aynı WF3 içinde bir etkinlik "kalıcı olarak kapalı durumda." olarak işaretleyerek elde edilebilir  İş akışı ikinci, ilişkili bir iletiyi tamamlar.  İş akışı kalıcı ancak değil kaldırıldı.  
  
### <a name="test-results"></a>Test Sonuçları  
 ![Aktarım hızı Kalıcılık](../../../docs/framework/windows-workflow-foundation/media/throughputpersistence.gif "ThroughputPersistence")  
  
 İstemci ve orta katman arasında taşıma HTTP olduğunda WF4 kalıcı bir geliştirme 2.6 kaç kez gösterir.  TCP aktarımı yalıtılması için 3.0 sürelerini artırır.  Her durumda, CPU kullanımı orta katman %98 olduğu veya üzeri.  WF4 aktarım hızını büyük olduğunu nedeni daha hızlı iş akışı çalışma zamanı nedeniyle olmasıdır.  Seri hale getirilmiş örnek boyutu için her iki durumda düşüktür ve önemli bir katkıda bulunan öğesi böyle bir durumda değil.  
  
 Bu test WF3 hem WF4 akışlarında bir etkinliğin ne zaman Kalıcılık gerçekleşmesi gerektiğini açıkça belirtmek için kullanın.  Bu eklentiyi olmadan iş akışını sürdürmek avantajına sahiptir.  WF3 içinde da kullanarak kalıcı hale getirmek mümkündür <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> özellik, ancak bu bellek iş akışı örneğinden kaldırır.  Bir geliştirici WF3 kullanarak bir iş akışı devam ederse bazı noktalarda emin olmak isterse, ya da iş akışı tanımını veya iş akışı örneği yeniden yükleme ve kaldırma için maliyet ödeme sahiptirler.  Yeni bir özellik WF4 kaldırmadan kalıcı hale getirmek mümkün kılar: <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>.  Bu özellik, iş akışı örneği kadar bellekte kalır ancak üzerinde kalıcı olmasını sağlar. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> eşiği karşılanıyorsa veya yürütme sürdürüldü.  
  
 WF4 SQL kalıcı bir sağlayıcı veritabanı katmanında daha fazla iş gerçekleştireceğini unutmayın.  SQL veritabanı, burada CPU ve disk kullanımını izlemek önemlidir bir performans sorunu haline gelebilir.  Aşağıdaki eklediğinizden emin olun performans sayaçlarını SQL veritabanı performans testi iş akışı uygulamaları:  
  
-   PhysicalDisk\\% Disk Zamanı okuma  
  
-   PhysicalDisk\\% Disk Zamanı  
  
-   PhysicalDisk\\% Disk yazma saati  
  
-   PhysicalDisk\\% ortalama Disk kuyruğu uzunluğu  
  
-   PhysicalDisk\Avg. Disk okuma kuyruğu uzunluğu  
  
-   PhysicalDisk\Avg. Disk yazma kuyruğu uzunluğu  
  
-   PhysicalDisk\Current Disk kuyruğu uzunluğu  
  
-   İşlemci bilgileri\\% işlemci zamanı  
  
-   SQLServer:Latches\Average Mandal bekleme süresi (ms)  
  
-   SQLServer:Latches\Latch bekler/sn  
  
### <a name="tracking"></a>İzleme  
 İş akışı izleme, bir iş akışı ilerlemesini izlemek için kullanılabilir.  İzleme olayları dahil edilmiş bilgileri bir izleme profili tarafından belirlenir.  Daha karmaşık izleme profili, izleme daha pahalı olur.  
  
 WF3 SQL tabanlı izleme hizmeti ile birlikte gelir.  Bu hizmet, toplu ve toplu olmayan modda çalışabilir.  Toplu olmayan modda, izleme olayları doğrudan veritabanına yazılır.  Toplu iş modunda izleme olaylarını, iş akışı örneği durumu olarak aynı toplu iş içine toplanır.  Toplu iş modu iş akışı tasarım yelpazedeki en iyi performansı vardır.  Ancak, toplu işleme olumsuz bir etkisi olmadan kalıcı birçok etkinlik iş akışı çalıştırır ve bu etkinlikler izlenir olabilir.  Bu genellikle Döngülerde olacağını ve bu senaryonun olmaması için en iyi bir Kalıcılık noktası içerecek şekilde büyük döngüler tasarlamak için yoludur.  Her maliyetleri ve bir bakiye ile gündeme önemlidir bir döngüye Kalıcılık noktası ile tanışın de performansı olumsuz yönde etkileyebilir.  
  
 WF4 hizmet İzleme SQL ile birlikte gönderilmeyen.  İzleme bilgilerini bir SQL veritabanı'na kayıt daha iyi bir uygulama sunucusundan işlenen yerine yerleşik [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Bu nedenle SQL izleme artık AppFabric tarafından işlenir.  Kullanıma hazır izleme sağlayıcısı WF4 olay izleme için Windows (ETW üzerinde) temel alır.  
  
 ETW, Windows içinde oluşturulmuş bir çekirdek düzeyinde ve düşük gecikmeli olay sistemidir.  Bu, aslında bir tüketici olduğunda yalnızca için olay izleme cezası uygulanmaya mümkün kılan bir sağlayıcı/tüketici modeli kullanır.  İşlemci, disk, bellek ve ağ kullanımı gibi çekirdek olayları yanı sıra birçok uygulama ETW de yararlanın.  Olayları, uygulama için özelleştirilebilir, ETW olayları, performans sayaçları daha güçlü.  Bir olay iş akışı kimliği ya da bir bilgi iletisidir gibi metin içerebilir.  Ayrıca, belirli bir alt olayların kullanan tüm olayları yakalamak daha az performans etkisine sahip olur, böylece olayları bit maskesi ile ayrılır.  
  
 ETW İzleme SQL yerine kullanmanın yaklaşımın avantajları şunlardır:  
  
-   Olayları izleme koleksiyonu başka bir işlem için ayrılabilir.  Bu, olayların nasıl kaydedileceğini daha fazla esneklik sağlar.  
  
-   ETW İzleme olayları kolayca WCF ETW olayları veya bir SQL Server veya çekirdek sağlayıcısı gibi diğer ETW sağlayıcıları ile birleştirilir.  
  
-   İş akışı yazarları WF3 SQL izleme hizmetin toplu iş modu gibi belirli izleme yer alan bir uygulama daha iyi çalışması için bir iş akışı alter gerek yoktur.  
  
-   Yönetici izleme üzerinde veya ana bilgisayar işlemi geri dönüştürme olmadan kapatabilirsiniz.  
  
 ETW İzleme için performans avantajlarının bir dezavantajı ile gelir.  Sistemin yoğun kaynak baskısı altında ise ETW olayları kaybolabilir.  Olayların işlenmesini normal program yürütme engelleyecek şekilde tasarlanmamıştır ve bu nedenle, tüm ETW olayları abonelerini için yayın garanti edilmez.  Bu sistem durumu izleme harika ancak denetim için uygun ETW İzleme sağlar.  
  
 WF4 SQL izleme sağlayıcısı yokken, AppFabric yapar.  AppFabric'ın SQL izleme olayları binlik toplu işlem ve bunları hızlı eklemeleri için tasarlanmış bir SQL tablosunu yazan bir Windows hizmeti ile ETW olayları abone olmak için bir yaklaşımdır.  Ayrı bir iş, bu tablodaki verileri boşaltır ve AppFabric Panoda görüntülenebilir tabloları raporlamasına reforms.  Başka bir deyişle, bir batch olayları izleme geldiği ve bu nedenle bir Kalıcılık noktası için kaydedilen önce beklenecek sahip iş akışı bağımsız olarak işlenir.  
  
 ETW olayları logman veya xperf gibi araçlarla kaydedilebilir.  Compact ETL dosyası xperfview gibi bir araçla görüntülenebilir veya daha okunabilir bir biçimde, XML gibi tracerpt ile dönüştürülür.  WF3 içinde bir SQL veritabanı olmadan olayları izleme almak için tek seçenek özel izleme hizmeti oluşturmaktır. ETW hakkında daha fazla bilgi için bkz: [WCF hizmetleri ve olay izleme için Windows](../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) ve [olay izleme için Windows](https://msdn.microsoft.com/library/ff190903.aspx\)).  
  
 Etkinleştirme iş akışı izleme değişen derece cinsinden performansını etkiler.  Aşağıdaki Kıyaslama ETW olayları izleme kullanmak ve bunları bir ETL dosyası olarak kaydetmek için logman Aracı'nı kullanır.  AppFabric içinde İzleme SQL maliyeti, bu makale kapsamında değil.  Ayrıca AppFabric içinde kullanılan temel izleme profili, bu karşılaştırmalı gösterilir.  De dahil, yalnızca sistem durumu izleme olaylarını izleme maliyetidir.  Bu olaylar ile ilgili sorunları giderme ve ortalama sistemin aktarım hızının belirlemek için yararlıdır.  
  
### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performans sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-results"></a>Test Sonuçları  
 ![İş akışı izleme maliyeti](../../../docs/framework/windows-workflow-foundation/media/workflowtracingcost.gif "WorkflowTracingCost")  
  
 Sistem durumu izleme kabaca bir %3 aktarım hızını etkiler.  Temel profilin maliyet yaklaşık % 8'dir.  
  
## <a name="interop"></a>Birlikte çalışma  
 WF4 olan neredeyse tamamını yeniden yazmak [!INCLUDE[wf1](../../../includes/wf1-md.md)] ve bu nedenle WF3 iş akışları ve etkinlikler doğrudan WF4 ile uyumlu değildir.  Windows Workflow Foundation erken benimsenen birçok müşteri, şirket içi veya üçüncü taraf iş akışı tanımları ve özel etkinlikler için WF3 olacaktır.  WF4 geçişi kolaylaştırmak için bir yol, bir iş akışındaki WF4 WF3 etkinlikten yürütebilir birlikte çalışma etkinliği kullanmaktır.  Önerilir <xref:System.Activities.Statements.Interop> etkinliği yalnızca kullanılabilir gerektiğinde. İçin WF4 geçirme hakkında daha fazla bilgi için kullanıma [WF4 geçiş kılavuzuna](https://go.microsoft.com/fwlink/?LinkID=153313).  
  
### <a name="environment-setup"></a>Ortam Kurulumu  
 ![İş akışı performans sınama ortamı](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-results"></a>Test Sonuçları  
 Aşağıdaki tabloda, çeşitli yapılandırmalarda dizisindeki beş etkinlik içeren bir iş akışı çalıştırma sonuçları gösterir.  
  
|Test|Aktarım hızı (iş akışları/sn)|  
|----------|-----------------------------------|  
|WF3 sırayla WF3 çalışma zamanı|1,576|  
|WF3 sırayla WF4 çalışma zamanı birlikte çalışabilirliği kullanma|2,745|  
|WF4 dizisi|153,582|  
  
 Düz WF3 birlikte çalışması kullanarak için önemli performans artışı yoktur.  Ancak, WF4 etkinlikleri karşılaştırıldığında göz ardı edilebilir artıştır.  
  
## <a name="summary"></a>Özet  
 Performans WF4 için ağır Yatırımlar birçok önemli alanda ödemesi devre dışı.  Tek bir iş akışı bileşen performansı, bazı durumlarda yüzlerce kez WF4 WF3 için karşılaştırılması nedeniyle bir daha yalın, daha hızlı [!INCLUDE[wf1](../../../includes/wf1-md.md)] çalışma zamanı.  Gecikme rakamları de önemli ölçüde daha uygundur.  Performans cezası kullanmak için başka bir deyişle [!INCLUDE[wf1](../../../includes/wf1-md.md)] el kodlama WCF düzenleme aksine Hizmetleri eklenen kullanmanın avantajları dikkate çok küçük [!INCLUDE[wf1](../../../includes/wf1-md.md)].  Kalıcılık performans 2.5 3.0 faktörüyle arttı.  İş akışı izleme yoluyla artık sistem durumu izleme, çok az yüke sahiptir.  Geçiş kılavuzlarını kapsamlı bir dizi WF3 WF4 için taşıma dikkate olanlar için kullanılabilir.  Tüm bu karmaşık uygulamalar yazmak için çekici bir seçenek WF4 olmanız gerekir.  
  
## <a name="acknowledgements"></a>Onayları  
 Çoğu aşağıdaki Katkıda Bulunanlar ve çalışmalarını için gözden geçirenler sayesinde:  
  
-   Leon Welicki, Microsoft Corporation  
  
-   Ryszard Kwiecinski, Microsoft Corporation  
  
-   Emil Velinov, Microsoft Corporation  
  
-   Nate Talbert, Microsoft Corporation  
  
-   Bob Etikan, Microsoft Corporation  
  
-   Stefan Batres, Microsoft Corporation
