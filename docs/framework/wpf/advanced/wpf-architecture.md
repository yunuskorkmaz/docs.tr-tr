---
title: Mimari
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
ms.openlocfilehash: b16be8470a47f3e8e362feb0b13e10aa901baacb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187126"
---
# <a name="wpf-architecture"></a>WPF Mimarisi
Bu konu, Windows Sunu Temeli (WPF) sınıf hiyerarşisinin rehberli bir tur sağlar. WPF'nin ana alt sistemlerinin çoğunu kapsar ve nasıl etkileşime girdiklerini açıklar. Ayrıca WPF'nin mimarları tarafından yapılan bazı seçimleri ayrıntılarıyla anlatır.  

<a name="System_Object"></a>
## <a name="systemobject"></a>System.Object  
 Birincil WPF programlama modeli yönetilen kod aracılığıyla ortaya çıkarır. WPF'nin tasarım aşamasının başlarında, sistemin yönetilen bileşenleri ile yönetilmeyen bileşenler arasında çizginin nerede çizilmesi gerektiği konusunda bir dizi tartışma vardı. CLR geliştirmeyi daha üretken ve sağlam hale getiren bir dizi özellik sağlar (bellek yönetimi, hata işleme, ortak tür sistemi, vb. dahil) ancak bunun bir bedeli vardır.  
  
 WPF'nin ana bileşenleri aşağıdaki şekilde gösterilmiştir. Diyagramın kırmızı bölümleri (PresentationFramework, PresentationCore ve milcore) WPF'nin ana kod bölümleridir. Bunlardan sadece bir tanesi yönetilmeyen bir bileşendir – milcore. Milcore, DirectX ile sıkı entegrasyon sağlamak için yönetilmeyen kodla yazılmıştır. WPF'deki tüm ekran, DirectX motoru aracılığıyla yapılır ve verimli donanım ve yazılım işleme sağlar. WPF ayrıca bellek ve yürütme üzerinde ince kontrol gerektiriyor. Milcore kompozisyon motoru son derece performansduyarlı, ve performans kazanmak için CLR birçok avantajı vazgeçmek gereklidir.  
  
 ![WPF'nin .NET Çerçevesi içindeki konumu.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 WPF'nin yönetilen ve yönetilmeyen bölümleri arasındaki iletişim daha sonra bu bölümde ele alınmıştır. Yönetilen programlama modelinin geri kalanı aşağıda açıklanmıştır.  
  
<a name="System_Threading_DispatcherObject"></a>
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 WPF'deki çoğu <xref:System.Windows.Threading.DispatcherObject>nesne, eşzamanlılık ve iş parçacığı ile başa çıkmak için temel yapıları sağlayan, türetilmiştir. WPF, gönderici tarafından uygulanan bir mesajlaşma sistemine dayanır. Bu çok tanıdık Win32 mesaj pompası gibi çalışır; aslında, WPF gönderici çapraz iş parçacığı aramaları gerçekleştirmek için User32 iletileri kullanır.  
  
 WPF eşzamanlılık tartışırken anlamak için gerçekten iki temel kavramlar vardır - sevk ve iş parçacığı yakınlık.  
  
 WPF'nin tasarım aşamasında amaç, tek bir yürütme iş parçacığına, ancak iş parçacığı olmayan "affinitized" modeline geçmekti. İş parçacığı afinite bir bileşen durum bazı tür depolamak için yürütme iş parçacığı kimliğini kullandığında olur. Bunun en yaygın biçimi, durumu depolamak için iş parçacığı yerel deposunu (TLS) kullanmaktır. İş parçacığı yakınlığı, yürütmenin her mantıksal iş parçacığının işletim sisteminde yalnızca bir fiziksel iş parçacığına sahip olmasını gerektirir ve bu da bellek yoğun olabilir. Sonunda, WPF'nin iş parçacığı modeli, iş parçacığı yakınlığı ile tek iş parçacığı yürütme mevcut User32 iş parçacığı modeli ile senkronize tutuldu. Bunun birincil nedeni birlikte çalışabilirlikti – OLE 2.0, pano ve Internet Explorer gibi sistemlerin tümü tek bir iş parçacığı afiyeti (STA) yürütmegerektirir.  
  
 STA iş parçacığı olan nesnelerinvarsa, iş parçacıkları arasında iletişim kurmak ve doğru iş parçacığı üzerinde olduğunuzu doğrulamak için bir yol gerekir. Burada sevk memuru rolü yatıyor. Sevk irsaliyesi, birden çok öncelikli sıraya sahip temel bir ileti gönderme sistemidir. İletilere örnek olarak ham giriş bildirimleri (fare taşınmış), çerçeve işlevleri (düzen) veya kullanıcı komutları (bu yöntemi uygulayın) verilebilir. Bu nedenle, <xref:System.Windows.Threading.DispatcherObject>STA davranışı olan bir CLR nesnesi oluşturursunuz ve oluşturma zamanında bir sevk irsaliyesi için bir işaretçi verilir.  
  
<a name="System_Windows_DependencyObject"></a>
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 WPF'nin oluşturulmasında kullanılan başlıca mimari felsefelerden biri, metotlar avesi ya da olaylar yerine özellikleri tercih etmekti. Özellikler bildirimseldir ve eylem yerine niyeti daha kolay belirtmenize olanak sağlar. Bu, kullanıcı arabirimi içeriğini görüntülemek için bir model veya veri odaklı sistemi de destekledi. Bu felsefe, bir uygulamanın davranışını daha iyi denetlemek için bağlanabileceğiniz daha fazla özellik oluşturma amacına sahipti.  
  
 Sistemin daha fazla özellikleri tarafından tahrik olması için, CLR ne sağlar daha zengin bir özellik sistemi gerekli ydi. Bu zenginliğin basit bir örneği değişim bildirimleridir. İki yol bağlamayı etkinleştirmek için, değişiklik bildirimini desteklemek için bağlamanın her iki tarafına da ihtiyacınız vardır. Davranış özelliği değerlerine bağlı olması için, özellik değeri değiştiğinde bildirimde bulunulması gerekir. Microsoft .NET Framework bir arabirime sahiptir, **INotifyPropertyChange**, bir nesne değişiklik bildirimleri yayımlamak için izin verir, ancak isteğe bağlıdır.  
  
 WPF <xref:System.Windows.DependencyObject> türünden türetilen daha zengin bir özellik sistemi sağlar. Özellik sistemi, özellik ifadeleri arasındaki bağımlılıkları izleyen ve bağımlılıklar değiştiğinde özellik değerlerini otomatik olarak yeniden geçersiz kıldığında gerçekten bir "bağımlılık" özellik sistemidir. Örneğin, devralan bir özelliğiniz varsa <xref:System.Windows.Controls.Control.FontSize%2A>(örneğin), değeri devralan bir öğenin üst öğesinde özellik değişirse sistem otomatik olarak güncelleştirilir.  
  
 WPF özellik sisteminin temeli bir özellik ifadesi kavramıdır. WPF'nin bu ilk sürümünde, özellik ifade sistemi kapatılır ve tüm ifadeler çerçevenin bir parçası olarak sağlanır. İfadeler, özellik sisteminin veri bağlama, stil veya devralma sabit kodlu olmamasının, daha çok çerçeve içinde sonraki katmanlar tarafından sağlanmalarının nedenidir.  
  
 Özellik sistemi ayrıca özellik değerlerinin seyrek depolanmasını da sağlar. Nesnelerin düzinelerce (yüzlerce değilse) özellikleri olabilir ve değerlerin çoğu varsayılan durumda (kalıtsal, stiller tarafından ayarlanmış, vb), bir nesnenin her örneği üzerinde tanımlanan her özelliğin tam ağırlığına sahip olması gerekmez.  
  
 Özellik sisteminin son yeni özelliği ekli özellikler kavramıdır. WPF elemanları kompozisyon ve bileşen yeniden ilkesi üzerine inşa edilmiştir. Genellikle bazı içeren öğe (bir <xref:System.Windows.Controls.Grid> düzen öğesi gibi) davranışını denetlemek için alt öğeler (Satır/ Sütun bilgileri gibi) ek veri gerekir durumda. Bu özelliklerin tümünün her öğeyle ilişkiiçinde olması yerine, herhangi bir nesnenin başka bir nesne için özellik tanımları sağlamasına izin verilir. Bu JavaScript "expando" özelliklerine benzer.  
  
<a name="System_Windows_Media_Visual"></a>
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Tanımlanan bir sistemle, bir sonraki adım pikselleri ekrana çektiriyor. Sınıf, <xref:System.Windows.Media.Visual> her biri isteğe bağlı olarak çizim yönergeleri ve bu yönergelerin nasıl işlenecek (kırpma, dönüştürme, vb.) hakkında meta veriler içeren görsel nesnelerden oluşan bir ağaç oluşturmayı sağlar. <xref:System.Windows.Media.Visual>son derece hafif ve esnek olacak şekilde tasarlanmıştır, bu nedenle özelliklerin çoğu genel API maruziyetine sahip değildir ve korumalı geri arama işlevlerine büyük ölçüde güvenir.  
  
 <xref:System.Windows.Media.Visual>gerçekten WPF kompozisyon sisteminin giriş noktasıdır. <xref:System.Windows.Media.Visual>bu iki alt sistem, yönetilen API ve yönetilmeyen milcore arasındaki bağlantı noktasıdır.  
  
 WPF, milcore tarafından yönetilen yönetilmeyen veri yapılarını geçerek verileri görüntüler. Kompozisyon düğümleri olarak adlandırılan bu yapılar, her düğümde işleme yönergeleri ile hiyerarşik bir görüntü ağacı temsil eder. Aşağıdaki şeklin sağ tarafında gösterilen bu ağaca yalnızca bir ileti protokolü aracılığıyla erişilebilir.  
  
 WPF'yi programlarken, <xref:System.Windows.Media.Visual> bu ileti protokolü aracılığıyla kompozisyon ağacına dahili olarak iletişim sağlayan öğeler ve türemiş türler oluşturursunuz. WPF'deki her <xref:System.Windows.Media.Visual> biri bir, hiç veya birkaç kompozisyon düğümü oluşturabilir.  
  
 ![Windows Sunum Vakfı Görsel Ağaç.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Burada dikkat edilmesi gereken çok önemli bir mimari detay vardır – görsellerin ve çizim talimatlarının tüm ağacı önbelleğe alınr. Grafik açısından, WPF korunmuş bir işleme sistemi kullanır. Bu, kompozisyon sistemi kullanıcı koduna geri aramaları engellemeden sistemin yüksek yenileme hızlarında yeniden boyamasını sağlar. Bu, yanıt vermeyen bir uygulamanın görünümünü önlemeye yardımcı olur.  
  
 Diyagramda gerçekten fark edilmez başka bir önemli ayrıntı sistemin aslında kompozisyon nasıl performans gösterdiğidir.  
  
 User32 ve GDI'de sistem hemen mod kırpma sistemi üzerinde çalışır. Bir bileşenin işlenmesi gerektiğinde, sistem, bileşenin piksellere dokunmasına izin verilmeyen bir kırpma sınırı kurar ve ardından bileşenden bu kutudaki pikselleri boyaması istenir. Bu sistem bellek kısıtlı sistemlerde çok iyi çalışır, çünkü bir şey değiştiğinde yalnızca etkilenen bileşene dokunmanız gerekir – iki bileşen tek bir pikselin rengine katkıda bulunmaz.  
  
 WPF bir "ressam algoritması" boyama modeli kullanır. Bu, her bileşenin kırpma yerine, her bileşenin arkadan ekranın önüne işlemesi istendiği anlamına gelir. Bu, her bileşenin önceki bileşenin ekranı nın üzerine boyamasına olanak tanır. Bu modelin avantajı karmaşık, kısmen saydam şekiller olabilir. Bugünün modern grafik donanımı ile, bu model nispeten hızlı (User32 / GDI oluşturulduğunda durum böyle değildi).  
  
 Daha önce de belirtildiği gibi, WPF'nin temel felsefesi daha açıklayıcı, "özellik merkezli" bir programlama modeline geçmektir. Görsel sistemde, bu birkaç ilginç yerde ortaya çıkıyor.  
  
 İlk olarak, eğer korunan mod grafik sistemi hakkında düşünüyorsanız, bu gerçekten uzak bir zorunlu DrawLine / DrawLine türü modeli, bir veri odaklı modele hareket ediyor - yeni Line()/yeni Line(). Veri odaklı işlemeye yapılan bu hareket, çizim yönergelerindeki karmaşık işlemlerin özellikler kullanılarak ifade edilmesine olanak tanır. Türlerden kaynaklanan türler <xref:System.Windows.Media.Drawing> etkili bir şekilde işleme için nesne modelidir.  
  
 İkinci olarak, animasyon sistemini değerlendirirseniz, neredeyse tamamen bildirimsel olduğunu görürsünüz. Bir geliştiricinin bir sonraki konumu veya sonraki rengi hesaplamasını gerektirmek yerine, animasyon nesnesi üzerinde bir özellik kümesi olarak animasyonları ifade edebilirsiniz. Bu animasyonlar daha sonra geliştirici veya tasarımcının amacını ifade edebilir (bu düğmeyi buradan oraya 5 saniyede taşıyın) ve sistem bunu başarmanın en etkili yolunu belirleyebilir.  
  
<a name="System_Windows_UIElement"></a>
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>Düzen, Giriş ve Olaylar dahil olmak üzere temel alt sistemleri tanımlar.  
  
 Düzen WPF bir çekirdek kavramdır. Birçok sistemde sabit bir düzen modeli kümesi vardır (HTML düzen için üç modeli destekler; akış, mutlak ve tablolar) veya düzen için hiçbir model (User32 gerçekten yalnızca mutlak konumlandırmayı destekler). WPF, geliştiricilerin ve tasarımcıların zorunlu mantık yerine özellik değerleri tarafından yönlendirilebilen esnek ve genişletilebilir bir düzen modeli istediği varsayımıyla başladı. <xref:System.Windows.UIElement> Düzeyde, düzen için temel sözleşme tanıtıldı - ile <xref:System.Windows.UIElement.Measure%2A> iki fazlı model ve <xref:System.Windows.UIElement.Arrange%2A> geçer.  
  
 <xref:System.Windows.UIElement.Measure%2A>bir bileşenin ne kadar boyut almak istediğini belirlemesini sağlar. Bu ayrı bir <xref:System.Windows.UIElement.Arrange%2A> aşamadır, çünkü bir üst öğenin en uygun konumunu ve boyutunu belirlemek için bir çocuktan birkaç kez ölçmesini isteyeceği birçok durum vardır. Üst öğelerin alt öğeleri ölçmek için sormak aslında WPF başka bir önemli felsefesi gösterir - içerik boyutu. WPF'deki tüm denetimler, içeriklerinin doğal boyutuna kadar boyutlandırma yeteneğini destekler. Bu, yerelleştirmeyi çok daha kolay hale getirir ve öğeler yeniden boyutlandıkça öğelerin dinamik düzenine olanak tanır. Aşama, <xref:System.Windows.UIElement.Arrange%2A> bir ebeveynin her çocuğun son boyutunu konumlandırmasını ve belirlemesini sağlar.  
  
 WPF'nin çıkış tarafı <xref:System.Windows.Media.Visual> ve ilgili nesneler hakkında konuşmak için çok zaman harcanıyor. Ancak giriş tarafında da muazzam bir yenilik miktarı vardır. WPF giriş modelindeki muhtemelen en temel değişiklik, giriş olaylarının sistem üzerinden yönlendirildiği tutarlı modeldir.  
  
 Giriş çekirdek modu aygıt sürücüsünde bir sinyal olarak kaynaklanır ve Windows çekirdeği ve User32 içeren karmaşık bir işlem yoluyla doğru işlem ve iş parçacığı yönlendirilir alır. Girişe karşılık gelen User32 iletisi WPF'ye yönlendirildikten sonra WPF ham giriş iletisine dönüştürülür ve gönderene gönderilir. WPF, ham giriş olaylarının birden çok gerçek olaya dönüştürülmesini sağlayarak "MouseEnter" gibi özelliklerin garantili teslimatla sistemin düşük bir düzeyinde uygulanmasını sağlar.  
  
 Her giriş olayı en az iki olaya dönüştürülür – bir "önizleme" olayı ve gerçek olay. WPF'deki tüm olaylar, öğe ağacı nın üzerinden yönlendirme kavramına sahiptir. Olaylar, bir hedeften ağaca doğru bir şekilde köke doğru iletilirse "kabarcık" olarak söylenir ve kökten başlayıp hedefe doğru iletilirlerse "tünel" olarak söylenir. Ağaçtaki herhangi bir öğeyi olay üzerinde filtreleme veya eyleme geçme fırsatı sağlayan önizleme olayları tünelini girin. Düzenli (önizleme olmayan) olaylar daha sonra hedeften köküne kadar kabarcık.  
  
 Tünel ve kabarcık aşaması arasındaki bu bölünme, klavye hızlandırıcıları gibi özelliklerin kompozit bir dünyada tutarlı bir şekilde çalışmasını sağlar. User32'de, desteklemek istediğiniz tüm hızlandırıcıları içeren tek bir küresel tabloya sahip olarak klavye hızlandırıcılarını uygularsınız (Ctrl+N haritalamadan "Yeni"ye). Uygulamanızın sevkiyatçısında, User32'deki giriş iletilerini koklayan ve kayıtlı bir hızlandırıcıyla eşleşen olup olmadığını belirleyen **TranslateAccelerator'ı** ararsınız. WPF'de sistem tamamen "birleştirilebilir" olduğundan bu çalışmaz – herhangi bir öğe herhangi bir klavye hızlandırıcısını kullanabilir ve kullanabilir. Giriş için bu iki fazlı modele sahip olmak, bileşenlerin kendi "TranslateAccelerator"larını uygulamalarını sağlar.  
  
 Bu bir adımı daha <xref:System.Windows.UIElement> ileri götürmek için, aynı zamanda CommandBindings kavramını tanıttı. WPF komut sistemi geliştiricilerbir komut bitiş noktası açısından işlevselliği tanımlamak <xref:System.Windows.Input.ICommand>için izin verir - uygulayan bir şey . Komut bağlamaları, bir öğenin giriş hareketi (Ctrl+N) ve komut (Yeni) arasında eşleme tanımlamasını sağlar. Hem giriş hareketleri hem de komut tanımları genişletilebilir ve kullanım sırasında birbirine bağlanabilir. Bu, örneğin, son kullanıcının bir uygulama içinde kullanmak istedikleri anahtar bağlamaları özelleştirmesine izin vermeyi önemsiz kılar.  
  
 Konuyla ilgili olarak, WPF'nin "çekirdek" özellikleri – PresentationCore derlemesinde uygulanan özellikler, odak noktası olmuştur. WPF oluştururken, temel parçalar **(Ölçü** ve **Düzenle**ile düzen sözleşmesi gibi) ve çerçeve parçaları (belirli bir düzenin uygulanması gibi) <xref:System.Windows.Controls.Grid>arasında temiz bir ayrım istenen sonuçtu. Amaç, dış geliştiricilerin gerekirse kendi çerçevelerini oluşturmalarına olanak sağlayacak yığında düşük bir genişletilebilirlik noktası sağlamaktı.  
  
<a name="System_Windows_FrameworkElement"></a>
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>iki farklı şekilde bakılabilir. WPF'nin alt katmanlarında tanıtılan alt sistemlerde bir dizi ilke ve özelleştirme sunar. Ayrıca yeni alt sistemler bir dizi tanıttı.  
  
 Tarafından <xref:System.Windows.FrameworkElement> sunulan birincil ilke, uygulama düzeni etrafındadır. <xref:System.Windows.FrameworkElement>tarafından <xref:System.Windows.UIElement> tanıtılan temel düzen sözleşmesi üzerine inşa ve daha kolay düzen yazarları için özellik odaklı düzen semantiği tutarlı bir dizi olmasını sağlayan bir düzen "yuvası" kavramını ekler. , <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> , ve (birkaç ad) gibi <xref:System.Windows.FrameworkElement> özellikler, düzen kapsayıcıları içinde tutarlı davranış türetilen tüm bileşenleri verir.  
  
 <xref:System.Windows.FrameworkElement>ayrıca WPF'nin çekirdek katmanlarında bulunan birçok özelliğe daha kolay API maruziyeti sağlar. Örneğin, <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> yöntem aracılığıyla animasyona doğrudan erişim sağlar. A, <xref:System.Windows.Media.Animation.Storyboard> birden çok animasyonu bir dizi özelliye karşı komut dosyası na göre komut dosyası sağlar.  
  
 <xref:System.Windows.FrameworkElement> Tanıtan en kritik iki şey veri bağlama ve stilleri vardır.  
  
 WPF'deki veri bağlama alt sistemi, bir uygulama [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]oluşturmak için Windows Formlarını veya ASP.NET kullanan herkes tarafından nispeten tanıdık olmalıdır. Bu sistemlerin her birinde, belirli bir öğeden bir veya daha fazla özelliğin bir veri parçasına bağlanmasını istediğinizi ifade etmenin basit bir yolu vardır. WPF, özellik bağlama, dönüştürme ve liste bağlama için tam destek vardır.  
  
 WPF'de veri bağlamanın en ilginç özelliklerinden biri veri şablonlarının sunulmasıdır. Veri şablonları, bir veri parçasının nasıl görüntülenmesi gerektiğini bildirimsel olarak belirtmenize olanak sağlar. Verilere bağlanabilen özel bir kullanıcı arabirimi oluşturmak yerine, sorunu tersine çevirebilir ve verilerin oluşturulacak ekranı belirlemesine izin verebilirsiniz.  
  
 Şekillendirme gerçekten veri bağlama hafif bir şeklidir. Stili kullanarak, bir dizi özelliği paylaşılan bir tanımdan bir veya daha fazla öğe örneğine bağlayabilirsiniz. Stiller, bir öğeye açık başvuru <xref:System.Windows.FrameworkElement.Style%2A> (özelliği ayarlayarak) veya bir stili öğenin CLR türüyle ilişkilendirerek uygulanır.  
  
<a name="System_Windows_Controls_Control"></a>
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Kontrolün en önemli özelliği baştan çıkarıcıdır. WPF'nin kompozisyon sistemini korunmuş bir mod oluşturma sistemi olarak düşünürseniz, templating bir denetimin işlemesini parametreli, bildirimsel bir şekilde tanımlamasına olanak tanır. A, <xref:System.Windows.Controls.ControlTemplate> denetim tarafından sunulan özelliklere bağlanan bir alt öğe kümesi oluşturmak için bir komut dosyasından başka bir şey değildir.  
  
 <xref:System.Windows.Controls.Control>bir dizi stok özellikleri <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.Background%2A>sağlar, , , <xref:System.Windows.Controls.Control.Padding%2A>, birkaç isim, hangi şablon yazarlar daha sonra bir denetimin ekranını özelleştirmek için kullanabilirsiniz. Denetimin uygulanması bir veri modeli ve etkileşim modeli sağlar. Etkileşim modeli bir komut kümesini (pencere için Kapat gibi) tanımlar ve giriş hareketlerine (pencerenin üst köşesindeki kırmızı X'i tıklatmak gibi) bağlanır. Veri modeli, etkileşim modelini özelleştirmek veya ekranı özelleştirmek için (şablon tarafından belirlenir) bir dizi özellik sağlar.  
  
 Veri modeli (özellikler), etkileşim modeli (komutlar ve olaylar) ve görüntü modeli (şablonlar) arasındaki bu bölünme, denetimin görünümünün ve davranışının tam olarak özelleştirilmesini sağlar.  
  
 Denetimlerin veri modelinin ortak bir yönü içerik modelidir. Gibi <xref:System.Windows.Controls.Button>bir denetime bakarsanız, "İçerik" türünde <xref:System.Object>bir özelliği olduğunu görürsünüz. Windows Formlar ve ASP.NET bu özellik genellikle bir dize olur – ancak bu düğmeye koyabileceğiniz içerik türünü sınırlar. Bir düğmenin içeriği basit bir dize, karmaşık bir veri nesnesi veya tüm öğe ağacı olabilir. Bir veri nesnesi durumunda, veri şablonu bir ekran oluşturmak için kullanılır.  
  
<a name="Summary"></a>
## <a name="summary"></a>Özet  
 WPF, dinamik, veri odaklı sunum sistemleri oluşturmanıza olanak sağlayacak şekilde tasarlanmıştır. Sistemin her bölümü, davranışı yönlendiren özellik kümeleri aracılığıyla nesneler oluşturmak üzere tasarlanmıştır. Veri bağlama sistemin temel bir parçasıdır ve her katmanda entegre edilmiştir.  
  
 Geleneksel uygulamalar bir ekran oluşturur ve sonra bazı verilere bağlanır. WPF'de, denetimle ilgili her şey, ekranın her yönü, bir tür veri bağlama tarafından oluşturulur. Düğmenin içinde bulunan metin, düğmenin içinde oluşturulmuş bir denetim oluşturularak ve ekranı düğmenin içerik özelliğine bağlayarak görüntülenir.  
  
 WPF tabanlı uygulamalar geliştirmeye başladığınızda, çok tanıdık hissetmeniz gerekir. Özellikleri ayarlayabilir, nesneleri kullanabilir ve veri bağlamayı Windows Formlarını veya ASP.NET kullanarak aynı şekilde ayarlayabilirsiniz. WPF mimarisi ne daha derin bir araştırma ile, temelde uygulamanın temel sürücüsü olarak veri tedavi çok daha zengin uygulamalar oluşturmak için olasılığı var bulacaksınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Düzen](layout.md)
- [Animasyona Genel bakış](../graphics-multimedia/animation-overview.md)
