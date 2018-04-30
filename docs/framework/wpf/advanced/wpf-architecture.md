---
title: WPF Mimarisi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [WPF], attached
- attached properties [WPF]
- architecture [WPF]
- unmanaged components [WPF]
- affinity thread [WPF]
- Storyboards [WPF]
- milcore [WPF]
- components [WPF], unmanaged
- painter's algorithm
- interfaces [WPF], INotifyPropertyChange
- CommandBindings [WPF]
- data templates [WPF]
- thread [WPF], affinity
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29c8e2d632c37a299389b1bdc7f3f19f7df2f7e7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="wpf-architecture"></a>WPF Mimarisi
Bu konu Windows Presentation Foundation (WPF) sınıf hiyerarşisinin Kılavuzlu Tur sağlar. Ana alt çoğunu kapsar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ve nasıl etkileşim kurduklarını açıklar. Bu ayrıca mimarlar tarafından yapılan seçimleri bazıları ayrıntıları [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
  
<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Birincil [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programlama modeli aracılığıyla yönetilen koda gösterilir. Tasarım aşamasında başlarında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sisteminin yönetilen bileşenleri ile yönetilmeyen olanları arasında satır nerede çizileceğini hakkında debates sayısı vardı. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Çok sayıda geliştirme daha üretken ve (dahil, bellek yönetimi, hata işleme, ortak tür sistemi, vb.) sağlam hale özelliği sağlar, ancak bir ücret gelir.  
  
 Ana bileşenlerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki çizimde gösterilmiştir. Kırmızı (PresentationFramework, PresentationCore ve milcore) diyagramı ana kod bölümlerini bölümleridir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Bu, tek bir yönetilmeyen – milcore bileşendir. Milcore ile sıkı tümleştirme etkinleştirmek için yönetilmeyen kodda yazılır [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Tümünü Göster [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yoluyla yapılır [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] altyapısı, verimli donanım ve yazılım işleme için izin verme. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Ayrıca farklı türlerde bellek ve yürütme gereklidir. Birleşim milcore içinde son derece hassas ve gerekli birçok avantajları vermiş performans altyapısıdır [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] performans elde etmek için.  
  
 ![.NET Framework içinde WPF konumu. ] (../../../../docs/framework/wpf/advanced/media/wpf-architect1.PNG "wpf_architect1")  
  
 Yönetilen ve yönetilmeyen kısımları arasındaki iletişimi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bu konunun ilerleyen bölümlerinde ele alınmıştır. Yönetilen programlama modeli geri kalanı aşağıda açıklanmıştır.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Çoğu nesneleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğesinden türetilen <xref:System.Windows.Threading.DispatcherObject>, eşzamanlılık ile ilgilenen ve iş parçacığı oluşturma için temel yapıları sağlar. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gönderici tarafından uygulanan bir ileti sistemi dayanır. Bu bilinen benzer çalışır [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ileti Pompalama; aslında, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dağıtıcısı çapraz iş parçacığı aramalar gerçekleştirmek için User32 iletileri kullanır.  
  
 Vardır gerçekten iki çekirdek içinde eşzamanlılık ele alırken anlamak için kavramları [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – dağıtıcısı ve iş parçacığı benzeşimini.  
  
 Tasarım aşaması sırasında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], hedef tek bir iş parçacığı yürütme için taşımak için olsa da, iş parçacığı olmayan "Benzetilen" modeli. İş parçacığı benzeşimini bir bileşen durumu tür depolamak için yürütme iş parçacığı kimliği kullandığında gerçekleşir. Bunun en yaygın form durumunu depolamak için iş parçacığı yerel depolama (TLS) kullanmaktır. İş parçacığı benzeşimini her mantıksal iş parçacığı yürütme yoğun olabilmesi için işletim sistemi, yalnızca bir fiziksel iş parçacığı tarafından ait gerekir. Sonunda, WPF'ın iş parçacığı modelini tek iş parçacıklı yürütme iş parçacığı benzeşimini ile varolan User32 iş parçacığı modeli ile senkronize tutulan. Bu temel nedeni birlikte çalışabilirlik – sistemleri ister [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], Pano ve Internet tek iş parçacığı benzeşimini (STA) yürütme gerektiren Explorer tüm.  
  
 STA iş parçacığı ile nesneleri görevinden olduğuna göre iş parçacıkları arasında iletişim kurmak ve doğrulamak için bir yol doğru iş parçacığında olan gerekir. Burada dağıtıcı rol arasındadır. Dağıtıcı, birden çok öncelikli kuyruklarla sistem göndermeyi temel bir iletidir. İletileri örnekleri arasında ham giriş bildirimleri (fare taşınmış), framework işlevleri (Düzen) ya da kullanıcı komutları (Bu yöntem yürütülmeye). Türetilen <xref:System.Windows.Threading.DispatcherObject>, oluşturduğunuz bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] STA davranışı olan nesne ve bir işaretçi bir dağıtıcı oluşturma sırasında verilir.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Binada kullanılan birincil mimari felsefeleri birini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yöntemleri veya olayları üzerinden özellikleri için bir tercih edildi. Özellikler bildirim temelli ve izin daha kolayca eylem yerine hedefi belirtin. Bu da bir model güdümlü ya da veri tabanlı, sistem kullanıcı arabirimi içeriğinin görüntülenmesi için desteklenir. Bu felsefesi hedeflenen etkisini daha iyi bir uygulama davranışını denetlemek için için bağlama yapılamadı daha fazla özellik oluşturma vardı.  
  
 Daha fazla özellikleri, miktardan daha zengin bir özellik sistemi tarafından yönlendirilen sistem olması için [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] sağlar gerekiyordu. Bir basit bu zenginliğini değişiklik bildirimleri örneğidir. İki yolla bağlama etkinleştirmek için her iki tarafında bir değişiklik bildirimi desteklemek için bağ gerekir. Özellik değerlerine bağlı davranışa sahip için özellik değeri değiştiğinde bildirilmesi gerekir. [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] Bir arabirime sahip **INotifyPropertyChange**, isteğe bağlıdır ancak değişiklik bildirimleri yayımlamak bir nesne sağlar.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] türetilen daha zengin bir özellik sistemi sağlar <xref:System.Windows.DependencyObject> türü. Özellik ifadeleri bağımlılıkları izler ve bağımlılıkları değiştirdiğinizde özellik değerlerini otomatik olarak yeniden doğrular özellik sistemi gerçek anlamda bir "bağımlılık" özelliği sistemidir. Örneğin, devralınan bir özellik varsa (gibi <xref:System.Windows.Controls.Control.FontSize%2A>), özellik değeri devralan bir öğenin üst öğede değişirse sistem otomatik olarak güncelleştirilir.  
  
 Temelini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özellik sistemi olan bir özellik ifadesi kavramı. Bu ilk sürümünde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]özelliği ifade sistem kapatılır ve ifadeler tüm framework'ün bir parçası olarak sağlanır. Özellik sistemi stil oluşturma, veri bağlama yoksa veya devralma sabit kodlanmış, ancak bunun yerine framework içindeki sonraki katmanları tarafından sağlanan neden ifadelerini olun.  
  
 Özellik sistemi özellik değerlerini seyrek depolama için de sağlar. Nesneleri düzinelerce (değilse yüzlerce) özelliklerinin olabilir ve değerleri çoğu kendi varsayılan durumda olduğundan (devralınan, stilleri tarafından ayarlama vb.), her bir nesnenin örneğine tanımlanmış her özellik tam ağırlığını olması gerekir.  
  
 Son yeni özellik sistemi ekli özellikler kavramı özelliğidir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğeleri oluşturma ve bileşeni yeniden ilkesini üzerinde oluşturulmuştur. Bu durum, bazı görülür öğeyi içeren (gibi bir <xref:System.Windows.Controls.Grid> Düzen öğesi), alt öğelerde (ör. satır/sütun bilgileri) davranışını denetlemek için ek veri gerekiyor. Bu özelliklerin tümünü her öğesiyle ilişkilendirme yerine, herhangi bir nesne başka bir nesne için özellik tanımları sağlamak izin verilmez. Bu, JavaScript "expando" özelliklerine benzer.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Sistemi tanımlı bir sonraki adımı ekrana çizilmiş piksel almaktır. <xref:System.Windows.Media.Visual> Visual nesnelerin bir ağaç her isteğe bağlı olarak çizim yönergeleri ve bu yönergeleri (kırpma, dönüştürme, vb.) oluşturmak nasıl hakkındaki meta verileri içeren oluşturmak için sınıf sağlar. <xref:System.Windows.Media.Visual> son derece basit ve esnek, hiçbir ortak özelliklerin çoğunu alacak şekilde olacak şekilde tasarlanmıştır [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] Etkilenme ve yoğun olarak korumalı geri çağırma işlevlerini kullanır.  
  
 <xref:System.Windows.Media.Visual> gerçekten için giriş noktası olduğundan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] birleşim sistem. <xref:System.Windows.Media.Visual> yönetilen iki bu sistemler arasında bağlantı noktasıdır [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] ve yönetilmeyen milcore.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] milcore tarafından yönetilen ve yönetilmeyen veri yapılarını geçme tarafından verilerini görüntüler. Birleşim düğüm olarak adlandırılan bu yapıları her düğümde işleme yönergeler içeren bir hiyerarşik görüntü ağacı temsil eder. Sağ tarafta, aşağıdaki şekilde gösterilen bu ağaç yalnızca bir Mesajlaşma protokolü aracılığıyla erişilebilir.  
  
 Programlama zaman [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], oluşturduğunuz <xref:System.Windows.Media.Visual> öğeleri ve dahili olarak birleşim ağacına bu Mesajlaşma protokolü üzerinden iletişim türetilmiş türler. Her <xref:System.Windows.Media.Visual> içinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] birini, yok veya birden fazla birleşim düğümleri oluşturabilir.  
  
 ![Windows Presentation Foundation görsel ağacı. ] (../../../../docs/framework/wpf/advanced/media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Burada – görselleri ağacının tümünü fark için çok önemli bir mimari ayrıntı yoktur ve yönergeleri çizim önbelleğe alınır. Grafik terimleriyle [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tutulan işleme sistemi kullanır. Bu kullanıcı kodu için geri çağırmaları engelleme birleşim sistem olmadan yüksek yenileme oranlarda çizilecek sistem sağlar. Bu, yanıt vermeyen bir uygulamada görünümünü önlemeye yardımcı olur.  
  
 Diyagramda gerçekten belirgin olmayan başka bir önemli ayrıntı nasıl sistem gerçekte oluşturma işlemini gerçekleştirir ' dir.  
  
 User32 içinde ve [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], sistem anlık kip kırpma sistemi üzerinde çalışır. Bir bileşenin oluşturulması gerektiğinde, sistem hangi dışında bileşen piksel touch için izin verilmeyen ve sonra o kutusuna piksel cinsinden boyamak için bileşen sorulan kırpma sınırları oluşturur. Bir şey değiştiğinde yalnızca etkilenen bileşeni touch gerekir çünkü bu sistemin kısıtlanmış belleğe sistemlerinde çok iyi çalışır. – hiçbir iki bileşen herhangi bir zamanda tek pikselli rengini katkıda.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] "model boyama ressamların algoritması" kullanır. Bu, her bileşen kırpma yerine, her bileşen arkadan öne görüntü işlemek için istedi olduğunu anlamına gelir. Bu, önceki bileşenin görüntü boyamak her bileşen sağlar. Bu modelin avantajı, karmaşık, kısmen saydam şekiller olabilir ' dir. Günümüzün modern grafik donanım ile bu modeli oldukça hızlıdır (durum sorgusuna zaman User32 / [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] oluşturulan).  
  
 Çekirdek felsefesi, daha önce belirtildiği gibi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programlama için bir daha bildirim temelli "özellik merkezli" modeli taşımaktır. Visual sisteminde bu ilginç yerler birkaç içinde görüntülenir.  
  
 Saklama modu grafik sistemi hakkında düşünüyorsanız, ilk olarak, bu gerçekten bir kesinlik temelli DrawLine/DrawLine türü modeli çıktığınızda yönelimli bir veri modeli için – taşınacağını yeni satır () / yeni Line(). Bu veri tabanlı işleme Git özellikleri kullanılarak ifade için çizim yönergelere karmaşık işlemlere izin verir. Türetme türleri <xref:System.Windows.Media.Drawing> etkili bir şekilde işleme için nesne modeli vardır.  
  
 İkinci olarak, animasyon sistemi değerlendirmek, neredeyse tamamen tanımlayıcı olduğunu görürsünüz. Bir geliştirici sonraki konumu veya sonraki renk işlem istemek yerine, bir animasyon nesne üzerinde bir özellikler kümesi animasyonları açıklayabilir. Animasyonlarına sonra geliştirici veya Tasarımcısı amacı express (taşıdığınızda bu düğme buradan orada için 5 saniye cinsinden) ve sistem bunu yapmaya yönelik en verimli şekilde belirleyebilirsiniz.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> Çekirdek alt sistemleri düzeni, giriş ve etkinlikler gibi tanımlar.  
  
 Düzen olan çekirdek kavram olarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Birçok sisteminde düzeni modellerin sabit ayarlanmış yok (HTML üç modeli düzenini destekler; akış, mutlak ve tablolar) veya hiçbir model düzeni için (User32 gerçekten yalnızca destekler mutlak konumlandırma). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geliştiricilerin ve tasarımcıların kesinlik temelli mantığı yerine özellik değerlerini tarafından yönlendirilen bir esnek ve Genişletilebilir düzeni modeli istedik varsayım ile başlatıldı. Konumundaki <xref:System.Windows.UIElement> düzeyi, sunulan düzeni için temel sözleşme – iki aşama modeliyle <xref:System.Windows.UIElement.Measure%2A> ve <xref:System.Windows.UIElement.Arrange%2A> geçirir.  
  
 <xref:System.Windows.UIElement.Measure%2A> Bunu yapmak istiyorsunuz ne kadar boyutunu belirlemek bir bileşen sağlar. Ayrı bir aşama budur <xref:System.Windows.UIElement.Arrange%2A> burada bir üst öğesi sorar kendi en iyi konumunu ve boyutunu belirlemek için birkaç kez ölçmek için bir alt pek çok durumda olduğundan. Üst öğeler alt öğelerin ölçmek isteyin olgu, başka bir anahtar felsefesi gösteren [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – içerik boyutu. İçindeki tüm denetimler [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriklerinin doğal boyutu özelliği destekler. Bu yerelleştirme çok daha kolay hale getirir ve öğeleri yeniden boyutlandırın gibi öğeleri dinamik düzen için sağlar. <xref:System.Windows.UIElement.Arrange%2A> Aşaması, konum ve her alt son boyutunu belirlemek bir üst sağlar.  
  
 Çok zaman çıktı tarafı hakkında konuşurken genellikle harcanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> ve ilgili nesneleri. Bununla birlikte inanılmaz bir yenilik miktarını da giriş tarafında yoktur. Büyük olasılıkla en temel bir değişiklik giriş modelinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] olarak giriş olaylarını sistem üzerinden yönlendirilir tutarlı modelidir.  
  
 Giriş bir çekirdek modu aygıt sürücüsü bir sinyal olarak kaynaklanan ve doğru işleme ve iş parçacığı Windows Çekirdeği ve User32 içeren karmaşık bir işlem aracılığıyla yönlendirilmiş. Giriş karşılık gelen User32 ileti yönlendirilir sonra [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], metne dönüştürülecek bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ham giriş iletisi ve dağıtıcı için gönderilir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] garantili teslim sistemiyle, düşük düzeyde uygulanacak "MouseEnter" gibi özellikleri etkinleştirme birden çok gerçek olayları dönüştürülecek ham giriş olaylarını sağlar.  
  
 Her giriş olayı, en az iki olaylarına – "Önizleme" olay ve gerçek olayın dönüştürülür. Tüm olaylar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğe ağacı üzerinden yönlendirme bir kavram vardır. Hedefin ağacı kök çapraz geçiş ve "kök dizininde başlatmak ve aşağıya doğru bir hedef geçiş tünel" söylenir olayları "Kabarcık" söylenir. Önizleme olayları tünel olayda eylemde veya filtre fırsatı ağacındaki herhangi bir öğeyi etkinleştirmeden, girin. Normal (Önizleme olmayan) olayları kök kadar hedeften sonra Kabarcık.  
  
 Bu bölünmüş tünel ve kabarcık aşaması arasında tutarlı bir şekilde bileşik dünyada klavye Hızlandırıcıları çalışma gibi özellikleri uyarlamasını yapar. İçinde User32 desteklemek istediğiniz tüm Hızlandırıcıları içeren tek bir genel tabloyu (Ctrl + N eşleme "Yeni") sağlayarak klavye Hızlandırıcıları uygulamak. Uygulamanız için dağıtıcı olarak, çağırırdı **TranslateAccelerator** User32 giriş iletileri bulmak ve herhangi bir kayıtlı Hızlandırıcı eşleşen belirlemek. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bu çalışmaz, çünkü "birleştirilebilir" tam olarak bir sistemdir – herhangi bir öğe işler ve tüm klavye kısayol tuşu kullanın. Bu iki aşama model giriş için sahip olmanız kendi "TranslateAccelerator" uygulamak bileşenleri sağlar.  
  
 Ayrıca, bunu bir adım öteye için <xref:System.Windows.UIElement> de CommandBindings kavramını sunmaktadır. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Komutu sistemin o uygular işlevselliği komutu uç noktası – açısından bir şey tanımlamak için geliştiricilere sağlar <xref:System.Windows.Input.ICommand>. Komut bağlamaları bir giriş hareketi (Ctrl + N) ve bir komut (yeni) arasında bir eşleme tanımlamak bir öğe etkinleştirin. Giriş hareketleri ve komut tanımları genişletilebilir ve birlikte kullanım zaman kablolu. Bu Önemsiz, örneğin, bir uygulama içinde kullanmak istedikleri anahtar bağlama özelleştirmek bir son kullanıcı olanak sağlar.  
  
 Bu noktada konusunda, "çekirdek" özelliklerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – PresentationCore derlemede Uygulanmayan Özellikler odağı olmuştur. Oluştururken [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], temiz temel parçalar arasında ayrım (ister düzeniyle sözleşme **ölçü** ve **Yerleştir**) ve (örneğin, belirli bir uygulama framework parçaları Düzen gibi <xref:System.Windows.Controls.Grid>) istenen sonuca oluştu. Genişletilebilirlik noktanız varsa, kendi çerçeveler oluşturmak dış geliştiriciler izin yığınında düşük gerekli sağlamak için hedef oluştu.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> iki farklı şekilde aranabilir. Bir dizi ilkeleri ve alt katmanında sunulan alt sistemleri üzerinde özelleştirmeleri tanıtır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Aynı zamanda, yeni alt kümesi sunar.  
  
 Tarafından sunulan birincil İlkesi <xref:System.Windows.FrameworkElement> uygulama düzeni. <xref:System.Windows.FrameworkElement> tarafından sunulan temel düzeni sözleşmesindeki derlemeler <xref:System.Windows.UIElement> ve bir düzen "düzeni yazarların tutarlı bir düzen semantiklerine güdümlü özellik kümesine sahip kolaylaştırır yuvası" kavramı ekler. Gibi özellikleri <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>, ve <xref:System.Windows.FrameworkElement.Margin%2A> (birkaç örnek vermek gerekirse) türetilen tüm bileşenleri vermek <xref:System.Windows.FrameworkElement> Düzen kapsayıcıları içinde tutarlı davranışı.  
  
 <xref:System.Windows.FrameworkElement> Ayrıca daha kolay sağlar [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] birçok özellik maruz bulunan çekirdek katmanında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Örneğin, <xref:System.Windows.FrameworkElement> animasyon doğrudan erişim sağlayan <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> yöntemi. A <xref:System.Windows.Media.Animation.Storyboard> bir özellikler kümesi karşı birden çok animasyon komut dosyası için bir yol sağlar.  
  
 İki en önemli şey, <xref:System.Windows.FrameworkElement> tanıtır veri bağlama ve stiller.  
  
 Veri bağlama alt [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kullandığı herkes için görece tanıdık [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] bir uygulama oluşturmak için [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Her bu sistemleri, bir veri parçası için bağlanması için belirli bir öğenin bir veya daha fazla özelliklerinden istediğiniz express için basit bir yol yoktur. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özellik bağlama, dönüştürme ve liste bağlama için tam destek vardır.  
  
 Veri bağlamanın en ilgi çekici Özellikler [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] veri şablonları giriş değil. Veri şablonları veri parçası nasıl görselleştirilen bildirimli olarak belirtmenizi sağlar. Verilere bağlı bir özel kullanıcı arabirimi oluşturmak yerine, bunun yerine sorunu Kapat ve oluşturulacak görüntü belirlemek veri sağlayabilirsiniz.  
  
 Stil gerçekten basit veri bağlama biçimidir. Bir özellik kümesi, stil oluşturma kullanarak, bir öğenin bir veya daha fazla örneklerine paylaşılan tanımından bağlayabilirsiniz. Stilleri bir öğeye uygulanan ya da açık başvuru (ayarlayarak <xref:System.Windows.FrameworkElement.Style%2A> özelliği) veya bir stille ilişkilendirerek örtük olarak [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] öğe türü.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Denetimin en önemli şablon özelliğidir. WPF'ın birleşim sistem saklama modu oluşturma sistemi olarak hakkında düşünüyorsanız, şablon, işleme parametreli ve bildirim temelli bir şekilde tanımlamak bir denetim sağlar. A <xref:System.Windows.Controls.ControlTemplate> gerçekten denetim tarafından sunulan özelliklerine bağlamalarla öğeleri alt kümesi oluşturmak için bir komut dosyası'den fazla bir şey değildir.  
  
 <xref:System.Windows.Controls.Control> Stok özellikleri, bir dizi sağlar <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, şablon yazarlar sonra bir denetim görüntüsünü özelleştirmek için kullanabileceğiniz, birkaçıdır. Uygulamasını bir denetimin bir veri modeli ile etkileşim modeli sağlar. Etkileşim modelini (örneğin, bir pencereyi kapat) komutları ve bağlamaları (gibi penceresinin üst köşesinde kırmızı X'ı tıklatarak) hareketleri giriş kümesini tanımlar. Veri modeli etkileşim modelini özelleştirmek veya (şablon tarafından belirlenir) görüntüsünü özelleştirmek için özellikler kümesi sağlar.  
  
 Bu bölme veri modeli (Özellikler), etkileşim modelini (komutlar ve olayları) ve görüntü modeli (Şablonları) arasındaki bir denetimin görünümünü ve davranışını tam özelleştirmesini sağlar.  
  
 Bir ortak denetimleri veri modelinin içerik modeli yönüdür. Bir denetimine bakarsanız ister <xref:System.Windows.Controls.Button>, türü "içerik" adlı bir özellik olduğunu görürsünüz <xref:System.Object>. İçinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)], bu özellik genelde bir dize olacaktır – içerik türünü sınırlar ancak bir düğme koyabilirsiniz. Ya da basit bir dize, karmaşık veri nesnesi veya bir öğenin tamamını ağacına bir düğme için içerik olabilir. Bir veri nesnesi söz konusu olduğunda, bir görüntü oluşturmak için veri şablonu kullanılır.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Özet  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Veri sunu sistemleri tabanlı dinamik oluşturmanıza olanak tanımak üzere tasarlanmıştır. Sisteminin her bir parçası, bu sürücü davranışı özellik kümeleri nesnelerde oluşturmak üzere tasarlanmıştır. Veri bağlama sistem temel bir parçasıdır ve her katmanında tümleşiktir.  
  
 Geleneksel uygulama bir görüntü oluşturmak ve bazı verilere bağlayın. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], görüntü, her yönüyle denetimi hakkında her şeyi bazı veri bağlama türü tarafından oluşturulur. Düğmenin içinde bulunan metin düğmesi içinde oluşan bir denetim oluşturma ve görünümünü düğmenin içerik özelliği için bağlama tarafından görüntülenir.  
  
 Geliştirme başladığınızda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tabanlı uygulamaları, çok tanıdık geliyor olmalıdır. Veri bağlama çok aynı şekilde kullanarak yapabilirsiniz ve özellikleri, kullanım nesneleri ayarlayabilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]. Daha kapsamlı bir araştırma mimarisiyle içine ile [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], olasılığını temelde verileri uygulama çekirdek sürücüsü olarak davran çok daha zengin uygulamaları oluşturmak için mevcut bulabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Threading.DispatcherObject>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Controls.Control>  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Düzen](../../../../docs/framework/wpf/advanced/layout.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
