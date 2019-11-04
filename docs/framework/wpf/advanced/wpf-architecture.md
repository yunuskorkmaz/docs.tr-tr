---
title: WPF Mimarisi
ms.date: 03/30/2017
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
ms.openlocfilehash: 02a70e65cd53a8998395987770cd32efc82293d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459598"
---
# <a name="wpf-architecture"></a>WPF Mimarisi
Bu konu, Windows Presentation Foundation (WPF) sınıf hiyerarşisinde kılavuzlu bir tur sağlar. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ana alt sistemlerinin çoğunu kapsamakta ve nasıl etkileşime gireceğini anlatmaktadır. Ayrıca, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]mimarları tarafından yapılan seçimlerin bazılarını da ayrıntılarıyla görebilirsiniz.  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Birincil [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programlama modeli, yönetilen kod aracılığıyla sunulur. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tasarım aşamasında erken, satırın yönetilen bileşenleri ve yönetilmeyen bileşenler arasında çizilmesi gereken bir kaç tane Bates vardı. CLR, geliştirmeyi daha üretken ve sağlam hale getirmek (bellek yönetimi, hata işleme, ortak tür sistemi vb. dahil olmak üzere), ancak bir maliyetle karşılaştıkları bir dizi özellik sağlar.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ana bileşenleri aşağıdaki şekilde gösterilmiştir. Diyagramın kırmızı bölümleri (PresentationFramework, PresentationCore ve milcore) [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ana kod bölümlerinden oluşur. Bunlardan yalnızca biri yönetilmeyen bir bileşen-milcore ' dır. Milcore, DirectX ile sıkı tümleştirmeyi sağlamak için yönetilmeyen koda yazılır. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 'daki tüm görüntüler DirectX altyapısı aracılığıyla yapılır ve bu da etkili donanım ve yazılım işleme sağlar. Ayrıca, bellek ve yürütme üzerinde ince denetim de gerekli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Frecore 'daki bileşim altyapısı son derece performansa duyarlıdır ve performans kazanmak için CLR 'nin pek çok avantaj elde etmek için gereklidir.  
  
 ![.NET Framework içinde WPF 'nin konumu.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yönetilen ve yönetilmeyen kısımları arasında iletişim bu konunun ilerleyen kısımlarında açıklanmıştır. Yönetilen programlama modelinin geri kalanı aşağıda açıklanmaktadır.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çoğu nesne, eşzamanlılık ve akıtma ile ilgili temel yapılar sağlayan <xref:System.Windows.Threading.DispatcherObject>türetilir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dağıtıcı tarafından uygulanan bir mesajlaşma sistemini temel alır. Bu, tanıdık [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ileti göndericisi gibi çok daha iyi bir şekilde çalışabilir. Aslında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dağıtıcısı, çapraz iş parçacığı çağrılarını gerçekleştirmek için User32 iletileri kullanır.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]-dağıtıcı ve iş parçacığı benzeşimi ile tartışırken anlaşılması için önemli iki temel kavram vardır.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]tasarım aşamasında, amaç tek bir yürütme iş parçacığına, ancak iş parçacığı olmayan "bir" uyumsuz "modele geçmektir. İş parçacığı benzeşimi, bir bileşen bir tür durum depolamak için yürütülen iş parçacığının kimliğini kullandığında oluşur. Bunun en yaygın biçimi, durumu depolamak için iş parçacığı yerel deposu (TLS) kullanmaktır. İş parçacığı benzeşimi, her bir mantıksal iş parçacığının işletim sisteminde yalnızca bir fiziksel iş parçacığından sahip olmasını gerektirir, bu da bellek yoğunluğu haline gelebilir. Son olarak, WPF 'in iş parçacığı modeli, iş parçacığı benzeşimi ile tek iş parçacıklı yürütmenin mevcut User32 iş parçacığı modeliyle eşitlenmiş olarak tutulmuştur. Bunun birincil nedeni [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], pano ve Internet Explorer 'ın hepsi için tek iş parçacığı benzeşimi (STA) yürütmeyi gerektirir.  
  
 STA iş parçacıklı nesneleriniz olduğundan, iş parçacıkları arasında iletişim kurmak ve doğru iş parçacığında olduğunu doğrulamak için bir yol gerekir. Buradaki dağıtıcı rolünü alır. Dağıtıcı, birden çok önceliklendirilmiş kuyruğu olan temel bir ileti gönderme sistemidir. İleti örnekleri arasında ham giriş bildirimleri (fare taşınan), çerçeve işlevleri (Düzen) veya Kullanıcı komutları (bu yöntemi Yürüt) verilebilir. <xref:System.Windows.Threading.DispatcherObject>türettikten sonra, STA davranışına sahip bir CLR nesnesi oluşturursunuz ve oluşturma zamanında dağıtıcı için bir işaretçi verilecek.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oluşturmakta kullanılan birincil mimari felsefeleri, Yöntemler veya olaylar üzerinde özellikler için bir tercihiydi. Özellikler bildirime sahiptir ve eylem yerine daha kolay bir amaç belirtmenize olanak tanır. Bu, Kullanıcı arabirimi içeriğini görüntülemek için model temelli veya veri odaklı bir sistem de destekliyordu. Bu FIN, bir uygulamanın davranışını daha iyi denetlemek için, bağlayacağınız daha fazla özelliği oluşturma amacını taşımaktadır.  
  
 Özelliklerden daha fazlasına sahip olmak için, CLR 'nin sağladığı daha zengin bir özellik sistemi gerekir. Bu zenginleştirme için basit bir örnek, değişiklik bildirimlerinden oluşur. İki yönlü bağlamayı etkinleştirmek için, bağlantı değişikliği bildirimini destekleyen her iki tarafa de ihtiyacınız vardır. Özellik değerlerine bağlı davranışa sahip olmak için, özellik değeri değiştiğinde bildirilmesi gerekir. Microsoft .NET Framework, bir nesnenin değişiklik bildirimlerini yayımlamasına izin veren **INotifyPropertyChange**arabirimine sahiptir, ancak isteğe bağlıdır.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.DependencyObject> türünden türetilmiş daha zengin bir özellik sistemi sağlar. Özellik sistemi gerçek anlamda Özellik ifadeleri arasındaki bağımlılıkları izleyen ve bağımlılıklar değiştiğinde özellik değerlerini otomatik olarak yeniden doğrulayan bir "bağımlılık" özellik sistemidir. Örneğin, devralınan bir özelliği varsa (<xref:System.Windows.Controls.Control.FontSize%2A>gibi), özelliği değeri devralan bir öğenin üst öğesinde değişirse sistem otomatik olarak güncelleştirilir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özellik sisteminin temeli bir özellik ifadesi kavramıdır. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ilk sürümünde, özellik ifadesi sistemi kapatılır ve ifadeler Framework 'ün bir parçası olarak sağlanır. İfadeler, özellik sisteminde neden veri bağlama, stil oluşturma veya devralma sabit kodlanmış değil, ancak Framework içindeki daha sonraki katmanlar tarafından sağlanmıyor.  
  
 Özellik sistemi, özellik değerlerinin seyrek depolanması için de sağlar. Nesneler, özelliklerinde (yüzlerce değilse) bir özellik olabileceğinden ve değerlerin çoğunun varsayılan durumunda (devralınan, stiller, vb.) olması nedeniyle, bir nesnenin her örneğinin, üzerinde tanımlanan her özelliğin tam ağırlığına sahip olması gerekir.  
  
 Özellik sisteminin son yeni özelliği, eklenen özelliklerin kavramından oluşur. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğeler, bileşim ve bileşen yeniden kullanım prensibi temel alınarak oluşturulmuştur. Genellikle kapsayan bir öğenin (bir <xref:System.Windows.Controls.Grid> düzeni öğesi gibi), davranışını denetlemek için alt öğelerde ek verilere ihtiyacı vardır (satır/sütun bilgileri gibi). Tüm bu özellikleri her öğe ile ilişkilendirmek yerine, herhangi bir nesnenin başka bir nesne için özellik tanımları sağlamasına izin verilir. Bu, JavaScript 'in "özelliği" özelliğine benzer.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Bir sistem tanımlı olarak, bir sonraki adım ekrana çizilen pikselleri alıyor. <xref:System.Windows.Media.Visual> sınıfı, her isteğe bağlı olarak, bu yönergelerin nasıl işlendiğine ilişkin çizim talimatlarını ve meta verileri içeren bir görsel nesne ağacı oluşturmak için sağlar (kırpma, dönüşüm, vb.). <xref:System.Windows.Media.Visual> son derece hafif ve esnek olacak şekilde tasarlanmıştır. bu sayede özelliklerin çoğu ortak API pozlaması yoktur ve korumalı geri arama işlevlerini yoğun bir şekilde kullanır.  
  
 <xref:System.Windows.Media.Visual>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bileşim sistemine gerçekten giriş noktasıdır. <xref:System.Windows.Media.Visual>, bu iki alt sistemi, yönetilen API ve yönetilmeyen milcore arasındaki bağlantı noktasıdır.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], milcore tarafından yönetilen yönetilmeyen veri yapılarına geçiş yaparak verileri görüntüler. Kompozisyon düğümleri olarak adlandırılan bu yapılar, her düğümdeki işleme talimatlarıyla hiyerarşik bir görüntüleme ağacını temsil eder. Aşağıdaki şeklin sağ tarafında gösterilen bu ağaca yalnızca bir mesajlaşma protokolü aracılığıyla erişilebilir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programlarken, bu mesajlaşma protokolü aracılığıyla iç birleşim ağacıyla iletişim kuran <xref:System.Windows.Media.Visual> öğeleri ve türetilmiş türler oluşturursunuz. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] her <xref:System.Windows.Media.Visual> bir, yok veya birkaç bileşim düğümü oluşturabilir.  
  
 ![Windows Presentation Foundation görsel ağacı.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Burada bildirimde bulunan çok önemli bir mimari ayrıntısı vardır: tüm görsellerin ve çizim yönergelerinin tamamı önbelleğe alınır. Grafik koşullarında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], korunan bir işleme sistemi kullanır. Bu, sistemin, geri çağırmalar üzerinde kullanıcı koduna çağrı yapmadan yüksek yenileme hızlarında yeniden örneklemesinin yapılmasını sağlar. Bu, yanıt vermeyen bir uygulamanın görünümünü önlemeye yardımcı olur.  
  
 Diyagramda gerçekten fark olmayan önemli bir ayrıntı, sistemin aslında oluşturma işlemini nasıl gerçekleştirdiğine ilişkin bir şeydir.  
  
 User32 ve GDI 'da sistem, bir anlık mod kırpma sisteminde çalışmaktadır. Bir bileşenin işlenmesi gerektiğinde, sistem, bileşenin piksellere dokunmasına izin verilmeyen bir kırpma sınırları oluşturur ve ardından bileşene bu kutudaki pikselleri boyamak istenir. Bu sistem, yalnızca etkilenen bileşene dokunmanız gerektiğinde hiçbir değişiklik yapıldığında, her zaman tek bir pikselin rengine katkıda bulunmadığı için bellek kısıtlı sistemlerde çok iyi çalışmaktadır.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], "boyacısı 'nın algoritması" boyama modelini kullanır. Bu, her bir bileşenin kırpılması yerine her bileşenin geri dönerek ekran önüne işlenmesi istenir. Bu, her bir bileşenin önceki bileşenin görüntüsüne göre boyamasına olanak tanır. Bu modelin avantajı karmaşık, kısmen saydam şekillere sahip olabilirsiniz. Günümüzün modern grafik donanımıyla, bu model görece hızlıdır (User32/GDI oluşturulduğunda bu durum değildir).  
  
 Daha önce belirtildiği gibi, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çekirdek felseı daha açıklayıcı, "Özellik merkezli" programlama modeline geçmektedir. Görsel sistemde bu, birkaç ilginç yerde görüntülenir.  
  
 İlk olarak, korunan mod grafik sistemi hakkında düşündüğünüzde bu aslında kesin bir DrawLine/DrawLine tür modelinden veri yönelimli bir modele (yeni satır ()/New Line () kadar geçiş yapılmakta. Veri odaklı işleme taşıma, çizim yönergelerindeki karmaşık işlemlere özellikler kullanılarak ifade yapılmasına izin verir. <xref:System.Windows.Media.Drawing> türetilen türler, işleme için nesne modelidir.  
  
 İkinci olarak, animasyon sistemini değerlendirdiğiniz takdirde neredeyse tamamen bildirime dayalı olduğunu görürsünüz. Bir geliştiricinin bir sonraki konumu veya bir sonraki rengi hesaplamasını gerektirmek yerine, animasyonları bir animasyon nesnesi üzerinde özellikler kümesi olarak ifade edebilirsiniz. Bu animasyonlar daha sonra geliştirici veya tasarımcı amacını ifade edebilir (bu düğmeyi 5 saniye içinde buraya taşıyın) ve sistem bunu gerçekleştirmek için en verimli yolu belirleyebilir.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> düzen, giriş ve olaylar dahil olmak üzere çekirdek alt sistemlerini tanımlar.  
  
 Düzen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]bir temel kavramdır. Birçok sistemde, sabit bir düzen modeli kümesi vardır (HTML, düzen için üç modeli destekler; Flow, mutlak ve tablolar) ya da düzen için model yoktur (User32 gerçekten mutlak konumlandırmayı destekler). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], geliştiricilerin ve tasarımcıların, kesinlik mantığı yerine özellik değerleri tarafından yönetilen esnek, genişletilebilir bir düzen modeli istediği varsayımıyla başlatılır. <xref:System.Windows.UIElement> düzeyinde, düzen için temel sözleşme, <xref:System.Windows.UIElement.Measure%2A> ve <xref:System.Windows.UIElement.Arrange%2A> geçişleri olan iki aşamalı bir modeldir.  
  
 <xref:System.Windows.UIElement.Measure%2A>, bir bileşenin ne kadar boyutta gelmesi gerektiğini belirlemesine izin verir. Bir üst öğenin en iyi konumunu ve boyutunu belirlemesi için birkaç kez bir alt öğe ölçmesini isteyeceğinden, bu <xref:System.Windows.UIElement.Arrange%2A> ayrı bir aşamadır. Üst öğelerin ölçü için alt öğelere sormasını gerektiren olgu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]-içeriğe kadar olan başka bir önemli FIN olduğunu gösterir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içindeki tüm denetimler, içeriklerinin doğal boyutuna göre boyut yeteneğini destekler. Bu, yerelleştirmeyi çok daha kolay hale getirir ve öğelerin yeniden boyutlandırılması halinde dinamik düzen oluşturulmasına olanak sağlar. <xref:System.Windows.UIElement.Arrange%2A> aşaması üst öğenin, her bir alt öğenin son boyutunu değiştirmesine ve belirlemesine izin verir.  
  
 Genellikle [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> ve ilgili nesnelerin çıkış tarafı hakkında konuşuyor olmak için çok zaman harcanacak. Ancak giriş tarafında çok fazla yenilik de vardır. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] için giriş modelindeki en temel değişiklik büyük olasılıkla, giriş olaylarının sistem aracılığıyla yönlendirildiği tutarlı modeldir.  
  
 Giriş, bir çekirdek modu cihaz sürücüsünde sinyal olarak gelir ve Windows çekirdeği ve User32 ile ilgili karmaşık bir süreç aracılığıyla doğru işleme ve iş parçacığına yönlendirilir. Girişe karşılık gelen User32 iletisi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]yönlendirildikten sonra, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ham giriş iletisine dönüştürülür ve dağıtıcıya gönderilir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ham giriş olaylarının birden çok gerçek olaya dönüştürülmesini sağlar ve bu sayede "MouseEnter" gibi özelliklerin, garantili teslimin bulunduğu düşük düzeyde sisteme uygulanması sağlanır.  
  
 Her giriş olayı en az iki olaya dönüştürülür: bir "Önizleme" olayı ve gerçek olay. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tüm olayların, öğe ağacı aracılığıyla yönlendirme kavramı vardır. Olaylar, bir hedeften köke kadar geziniyorlarsa "kabarcık" olarak bildirilir ve kökte başlayıp bir hedefe geçiş yaptıysanız "tünel" olarak kabul edilir. Giriş önizleme olayları tüneli, ağaçtaki herhangi bir öğenin olayı filtreleme veya eylem üzerinde işlem yapması için bir fırsat sağlar. Normal (Önizleme dışı) olaylar bundan sonra hedeften köke kadar kabarcık sağlar.  
  
 Bu, tünel ve kabarcık aşaması arasında bölünen, klavye hızlandırıcıları gibi özelliklerin uygulanması bileşik bir dünyada tutarlı bir biçimde çalışır. User32 ' de, desteklemek istediğiniz tüm Hızlandırıcılar içeren tek bir genel tabloya sahip olarak klavye hızlandırıcılarını (CTRL + N "yeni" ile eşleme) uygulayabilirsiniz. Uygulamanıza yönelik dağıtıcıda, User32 'deki giriş iletilerini saptayabilir ve herhangi bir kayıtlı hızlandırıcı ile eşleşen bir hızlandırıcının olduğunu tespit eden **TranslateAccelerator** öğesini çağırırdı. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], sistem tamamen "birleştirilebilen" olduğundan çalışmaz; herhangi bir öğe herhangi bir klavye hızlandırıcıyı işleyebilir ve kullanabilir. Bu iki aşama modelinin giriş için olması, bileşenlerin kendi "TranslateAccelerator" uygulamasını uygulamasına izin verir.  
  
 Bu adımı daha fazla yapmak için, <xref:System.Windows.UIElement> CommandBindings kavramını da tanıtır. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] komut sistemi, geliştiricilerin bir komut uç noktası açısından işlevselliği tanımlamasına olanak tanır. Bu, <xref:System.Windows.Input.ICommand>uygulayan bir şeydir. Komut bağlamaları bir giriş hareketi (CTRL + N) ile bir komut (yeni) arasında eşleme tanımlamak için bir öğe etkinleştirir. Hem giriş hareketleri hem de komut tanımları genişletilebilir ve kullanım zamanında birbirine bağlanabilir. Bu, örneğin, son kullanıcının bir uygulama içinde kullanmak istedikleri anahtar bağlamalarını özelleştirmesini sağlamak gibi basit hale getirir.  
  
 Bu noktaya, konusunun "çekirdek" özellikleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – PresentationCore derlemesinde uygulanan özellikler, odağa sahip. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]oluştururken, temel parçalar ( **Ölçü** ve **düzenleme**ile düzen sözleşmesi gibi) ve çerçeve parçaları arasında (<xref:System.Windows.Controls.Grid>gibi belirli bir düzenin uygulanması gibi) bir temiz ayrım, istenen sonuç idi. Amaç, bir yığında düşük bir genişletilebilirlik noktası sağlamaktır. Bu, dış geliştiricilerin gerekirse kendi çerçevelerini oluşturmalarına olanak tanır.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>, iki farklı şekilde aranabilir. Daha düşük [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]alt sistemlerinde tanıtılan bir ilke ve özelleştirme kümesi sunar. Ayrıca yeni alt sistemler kümesi de sağlar.  
  
 <xref:System.Windows.FrameworkElement> tarafından tanıtılan birincil ilke, uygulama düzeni etrafında. <xref:System.Windows.FrameworkElement>, <xref:System.Windows.UIElement> tarafından tanıtılan temel düzen sözleşmesinde yapılar ve düzen yazarlarının bir dizi özellik temelli düzen semantiğini daha kolay hale getiren bir "yuva" düzeni kavramı ekler. <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>ve <xref:System.Windows.FrameworkElement.Margin%2A> gibi Özellikler (bir ad vermek için), tüm bileşenlere, Düzen kapsayıcıları içindeki <xref:System.Windows.FrameworkElement> tutarlı bir davranışdan türetilmiş tüm bileşenleri verir.  
  
 <xref:System.Windows.FrameworkElement> Ayrıca, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]temel katmanlarında bulunan birçok özelliğe daha kolay API pozlaması sağlar. Örneğin, <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> yöntemi aracılığıyla animasyonuna doğrudan erişim sağlar. <xref:System.Windows.Media.Animation.Storyboard>, bir dizi özellik için birden çok animasyonları betiğe yönelik bir yol sağlar.  
  
 <xref:System.Windows.FrameworkElement> tanıtılmakta olan en önemli iki şey veri bağlama ve stillerdir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] veri bağlama alt sistemi, uygulama [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]oluşturmak için [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya ASP.NET kullanmış olan herkese görece tanıdık olmalıdır. Bu sistemlerin her birinde, belirli bir öğeden bir veya daha fazla özelliği bir veri parçasına bağlamak istediğinizi ifade etmek için basit bir yol vardır. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Özellik bağlama, dönüştürme ve liste bağlama için tam destek içerir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] veri bağlamanın en ilginç özelliklerinden biri, veri şablonlarının sunumundan biridir. Veri şablonları, verilerin bir parçasının görselleştirme şeklini bildirimli olarak belirtmenize olanak tanır. Verilere bağlanabilen özel bir kullanıcı arabirimi oluşturmak yerine, bunun yerine sorunu açıp verilerin oluşturulacak görüntüyü belirlemesine izin verebilirsiniz.  
  
 Stil oluşturma aslında veri bağlamanın hafif bir biçimidir. Stil oluşturma kullanarak, paylaşılan bir tanımdan bir veya daha fazla öğe örneğine bir özellik kümesi bağlayabilirsiniz. Stiller bir öğeye açık başvuruya göre (<xref:System.Windows.FrameworkElement.Style%2A> özelliği ayarlanarak) veya bir stili öğenin CLR türüyle ilişkilendirerek dolaylı olarak uygulanır.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Denetimin en önemli özelliği şablon oluşturma ' dır. WPF 'in bileşim sistemini bir tutulan mod işleme sistemi olarak düşünüyorsanız, şablon oluşturma bir denetimin işlemesini parametreli, bildirime dayalı bir şekilde açıklamaya olanak sağlar. Bir <xref:System.Windows.Controls.ControlTemplate>, bir alt öğe kümesi oluşturmak için bir betikten fazla değil, denetimin sunduğu özelliklerin bağlamalarıyla birlikte.  
  
 <xref:System.Windows.Controls.Control>, bazı şablon yazarlarının bir denetimin görüntülenmesini özelleştirmek için kullanabileceği bir dizi hisse senedi özelliği, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>sağlar. Bir denetimin uygulanması bir veri modeli ve etkileşim modeli sağlar. Etkileşim modeli, giriş hareketlerine (pencerenin üst köşesindeki kırmızı X simgesine tıklanması gibi) bir dizi komut (pencere için yakın) ve bağlamalar tanımlar. Veri modeli, etkileşim modelini özelleştirmek veya görüntülemeyi özelleştirmek (şablon tarafından belirlenir) için bir özellikler kümesi sağlar.  
  
 Veri modeli (Özellikler), etkileşim modeli (komutlar ve olaylar) ve görüntüleme modeli (şablonlar) arasında bölünen bu, bir denetimin görünüm ve davranışının tamamen özelleştirilmesine izin vermez.  
  
 Denetimlerin veri modelinin ortak bir yönü, içerik modelidir. <xref:System.Windows.Controls.Button>gibi bir denetime bakarsanız, <xref:System.Object>türünün "Içerik" adlı bir özelliğe sahip olduğunu görürsünüz. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve ASP.NET içinde, bu özellik genellikle bir dize olur, ancak bir düğmeye koyabileceğiniz içerik türünü sınırlar. Bir düğmenin içeriği basit bir dize, karmaşık veri nesnesi veya bir öğe ağacının tamamı olabilir. Veri nesnesi söz konusu olduğunda, veri şablonu bir görüntü oluşturmak için kullanılır.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Özet  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], dinamik, veri odaklı sunum sistemleri oluşturmanıza olanak tanımak için tasarlanmıştır. Sistemin her bölümü, davranışını oluşturan özellik kümeleri aracılığıyla nesne oluşturmak için tasarlanmıştır. Veri bağlama, sistemin temel bir parçasıdır ve her katmanda tümleşiktir.  
  
 Geleneksel uygulamalar bir görüntü oluşturup daha sonra bazı verilere bağlar. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], denetimle ilgili her şey, her bir veri bağlama türü tarafından oluşturulur. Düğme içinde bulunan metin, düğmenin içinde oluşturulan bir denetim oluşturularak ve görünümünü düğmenin içerik özelliğine bağlayarak görüntülenir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tabanlı uygulamalar geliştirmeye başladığınızda çok tanıdık gelmelidir. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya ASP.NET kullanarak özellikleri, nesneleri ve veri bağlamayı birçok şekilde ayarlayabilirsiniz. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]mimarisine daha derin bir araştırma sayesinde, uygulamanın çekirdek sürücüsü olarak verileri temel alan çok daha zengin uygulamalar oluşturmak için bu olasılığa sahip olduğunu fark edeceksiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Düzen](layout.md)
- [Animasyona Genel bakış](../graphics-multimedia/animation-overview.md)
