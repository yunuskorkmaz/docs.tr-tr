---
title: Mimari
description: Büyük alt sistemlerin çoğunu ve bunların nasıl etkileşime gireceğini de içeren Windows Presentation Foundation sınıf hiyerarşisi hakkında bilgi edinin.
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
ms.openlocfilehash: a67709283b4b664e7b9ca0dced9154a43fcae8a5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166319"
---
# <a name="wpf-architecture"></a>WPF Mimarisi
Bu konu, Windows Presentation Foundation (WPF) sınıf hiyerarşisinde kılavuzlu bir tur sağlar. WPF 'nin büyük alt sistemlerinin çoğunu kapsamakta ve nasıl etkileşime gireceğini anlatmaktadır. Ayrıca WPF 'nin mimarları tarafından yapılan seçimlerin bazılarını da ayrıntılarıyla görebilirsiniz.  

<a name="System_Object"></a>
## <a name="systemobject"></a>System.Object  
 Birincil WPF programlama modeli, yönetilen kod aracılığıyla sunulur. WPF 'nin tasarım aşamasının başlarında, sistemin yönetilen bileşenleri ve yönetilmeyen bileşenler arasında çizginin nerede çizildiğini öğrenmek için bir dizi yorumladığınıza vardı. CLR, geliştirmeyi daha üretken ve sağlam hale getirmek (bellek yönetimi, hata işleme, ortak tür sistemi vb. dahil olmak üzere), ancak bir maliyetle karşılaştıkları bir dizi özellik sağlar.  
  
 WPF 'nin ana bileşenleri aşağıdaki şekilde gösterilmiştir. Diyagramın kırmızı bölümleri (PresentationFramework, PresentationCore ve milcore) WPF 'nin önemli kod bölümlerinden oluşur. Bunlardan yalnızca biri yönetilmeyen bir bileşen-milcore ' dır. Milcore, DirectX ile sıkı tümleştirmeyi sağlamak için yönetilmeyen koda yazılır. WPF 'deki tüm görüntüler DirectX altyapısı aracılığıyla yapılır, bu da etkili donanım ve yazılım işleme sağlar. WPF ayrıca bellek ve yürütme üzerinde ince denetim gerektirir. Frecore 'daki bileşim altyapısı son derece performansa duyarlıdır ve performans kazanmak için CLR 'nin pek çok avantaj elde etmek için gereklidir.  
  
 ![.NET Framework içinde WPF 'nin konumu.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 WPF 'nin yönetilen ve yönetilmeyen kısımları arasındaki iletişim, bu konunun ilerleyen kısımlarında ele alınmıştır. Yönetilen programlama modelinin geri kalanı aşağıda açıklanmaktadır.  
  
<a name="System_Threading_DispatcherObject"></a>
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 WPF 'deki çoğu nesne <xref:System.Windows.Threading.DispatcherObject> , eşzamanlılık ve iş parçacığı oluşturma ile ilgili temel yapılar sağlayan öğesinden türetilir. WPF, dağıtıcı tarafından uygulanan bir mesajlaşma sistemini temel alır. Bu, tanıdık Win32 ileti göndericisi gibi çok daha iyi çalışabilir; Aslında, WPF dağıtıcısı çapraz iş parçacığı çağrılarını gerçekleştirmek için User32 iletileri kullanır.  
  
 WPF 'de eşzamanlılık, dağıtıcı ve iş parçacığı benzeşimi ile tartışırken anlaşılması için aslında iki temel kavram vardır.  
  
 WPF 'in tasarım aşamasında, amaç tek bir yürütme iş parçacığına, ancak iş parçacığı olmayan "bir" uyumsuz "modele geçmektir. İş parçacığı benzeşimi, bir bileşen bir tür durum depolamak için yürütülen iş parçacığının kimliğini kullandığında oluşur. Bunun en yaygın biçimi, durumu depolamak için iş parçacığı yerel deposu (TLS) kullanmaktır. İş parçacığı benzeşimi, her bir mantıksal iş parçacığının işletim sisteminde yalnızca bir fiziksel iş parçacığından sahip olmasını gerektirir, bu da bellek yoğunluğu haline gelebilir. Son olarak, WPF 'in iş parçacığı modeli, iş parçacığı benzeşimi ile tek iş parçacıklı yürütmenin mevcut User32 iş parçacığı modeliyle eşitlenmiş olarak tutulmuştur. Bunun birincil nedeni, birlikte çalışabilirlik – OLE 2,0, pano ve Internet Explorer gibi sistemlerin hepsi tek iş parçacığı benzeşimi (STA) yürütmeyi gerektirir.  
  
 STA iş parçacıklı nesneleriniz olduğundan, iş parçacıkları arasında iletişim kurmak ve doğru iş parçacığında olduğunu doğrulamak için bir yol gerekir. Buradaki dağıtıcı rolünü alır. Dağıtıcı, birden çok önceliklendirilmiş kuyruğu olan temel bir ileti gönderme sistemidir. İleti örnekleri arasında ham giriş bildirimleri (fare taşınan), çerçeve işlevleri (Düzen) veya Kullanıcı komutları (bu yöntemi Yürüt) verilebilir. Öğesinden türeterek <xref:System.Windows.Threading.DispatcherObject> , STA davranışına sahip BIR CLR nesnesi oluşturursunuz ve oluşturma zamanında dağıtıcı için bir işaretçi verilecek.  
  
<a name="System_Windows_DependencyObject"></a>
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 WPF oluştururken kullanılan birincil mimari felsefeleri, Yöntemler veya olaylar üzerinde özellikler için bir tercihiydi. Özellikler bildirime sahiptir ve eylem yerine daha kolay bir amaç belirtmenize olanak tanır. Bu, Kullanıcı arabirimi içeriğini görüntülemek için model temelli veya veri odaklı bir sistem de destekliyordu. Bu FIN, bir uygulamanın davranışını daha iyi denetlemek için, bağlayacağınız daha fazla özelliği oluşturma amacını taşımaktadır.  
  
 Özelliklerden daha fazlasına sahip olmak için, CLR 'nin sağladığı daha zengin bir özellik sistemi gerekir. Bu zenginleştirme için basit bir örnek, değişiklik bildirimlerinden oluşur. İki yönlü bağlamayı etkinleştirmek için, bağlantı değişikliği bildirimini destekleyen her iki tarafa de ihtiyacınız vardır. Özellik değerlerine bağlı davranışa sahip olmak için, özellik değeri değiştiğinde bildirilmesi gerekir. Microsoft .NET Framework, bir nesnenin değişiklik bildirimlerini yayımlamasına izin veren **INotifyPropertyChange**arabirimine sahiptir, ancak isteğe bağlıdır.  
  
 WPF, türden türetilmiş daha zengin bir özellik sistemi sağlar <xref:System.Windows.DependencyObject> . Özellik sistemi gerçek anlamda Özellik ifadeleri arasındaki bağımlılıkları izleyen ve bağımlılıklar değiştiğinde özellik değerlerini otomatik olarak yeniden doğrulayan bir "bağımlılık" özellik sistemidir. Örneğin, (gibi) devralınan bir özelliğe sahipseniz <xref:System.Windows.Controls.Control.FontSize%2A> , özelliği değeri devralan bir öğenin üst öğesinde değişirse sistem otomatik olarak güncelleştirilir.  
  
 WPF özellik sisteminin temeli bir özellik ifadesinin kavramıdır. WPF 'in bu ilk sürümünde, özellik ifadesi sistemi kapatılır ve ifadeler Framework 'ün bir parçası olarak sağlanır. İfadeler, özellik sisteminde neden veri bağlama, stil oluşturma veya devralma sabit kodlanmış değil, ancak Framework içindeki daha sonraki katmanlar tarafından sağlanmıyor.  
  
 Özellik sistemi, özellik değerlerinin seyrek depolanması için de sağlar. Nesneler, özelliklerinde (yüzlerce değilse) bir özellik olabileceğinden ve değerlerin çoğunun varsayılan durumunda (devralınan, stiller, vb.) olması nedeniyle, bir nesnenin her örneğinin, üzerinde tanımlanan her özelliğin tam ağırlığına sahip olması gerekir.  
  
 Özellik sisteminin son yeni özelliği, eklenen özelliklerin kavramından oluşur. WPF öğeleri, bileşim ve bileşen yeniden kullanım prensibi temel alınarak oluşturulmuştur. Genellikle kapsayan bir öğenin (bir <xref:System.Windows.Controls.Grid> düzen öğesi gibi), davranışını denetlemek için alt öğelerde ek verilere ihtiyacı vardır (satır/sütun bilgileri gibi). Tüm bu özellikleri her öğe ile ilişkilendirmek yerine, herhangi bir nesnenin başka bir nesne için özellik tanımları sağlamasına izin verilir. Bu, JavaScript 'in "özelliği" özelliğine benzer.  
  
<a name="System_Windows_Media_Visual"></a>
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Bir sistem tanımlı olarak, bir sonraki adım ekrana çizilen pikselleri alıyor. <xref:System.Windows.Media.Visual>Sınıfı, isteğe bağlı olarak, bu yönergelerin nasıl işlendiğine ilişkin çizim talimatlarını ve meta verileri içeren bir görsel nesne ağacı oluşturmak için sağlar (kırpma, dönüşüm, vb.). <xref:System.Windows.Media.Visual>Son derece hafif ve esnek olacak şekilde tasarlanmıştır. bu nedenle özelliklerin çoğu ortak API pozlaması yoktur ve korumalı geri çağırma işlevlerini yoğun bir şekilde kullanır.  
  
 <xref:System.Windows.Media.Visual>, WPF bileşim sistemine gerçekten giriş noktasıdır. <xref:System.Windows.Media.Visual>Bu iki alt sistemi, yönetilen API ve yönetilmeyen milcore arasındaki bağlantı noktasıdır.  
  
 WPF, milcore tarafından yönetilen yönetilmeyen veri yapılarına geçiş yaparak verileri görüntüler. Kompozisyon düğümleri olarak adlandırılan bu yapılar, her düğümdeki işleme talimatlarıyla hiyerarşik bir görüntüleme ağacını temsil eder. Aşağıdaki şeklin sağ tarafında gösterilen bu ağaca yalnızca bir mesajlaşma protokolü aracılığıyla erişilebilir.  
  
 WPF programlama yaparken, <xref:System.Windows.Media.Visual> Bu mesajlaşma protokolü aracılığıyla iç birleşim ağacıyla iletişim kuran öğeler ve türetilmiş türler oluşturulur. <xref:System.Windows.Media.Visual>WPF içinde her biri bir, hiçbiri veya birkaç bileşim düğümü oluşturabilir.  
  
 ![Windows Presentation Foundation görsel ağacı.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Burada bildirimde bulunan çok önemli bir mimari ayrıntısı vardır: tüm görsellerin ve çizim yönergelerinin tamamı önbelleğe alınır. Grafik koşullarında WPF, korunan bir işleme sistemi kullanır. Bu, sistemin, geri çağırmalar üzerinde kullanıcı koduna çağrı yapmadan yüksek yenileme hızlarında yeniden örneklemesinin yapılmasını sağlar. Bu, yanıt vermeyen bir uygulamanın görünümünü önlemeye yardımcı olur.  
  
 Diyagramda gerçekten fark olmayan önemli bir ayrıntı, sistemin aslında oluşturma işlemini nasıl gerçekleştirdiğine ilişkin bir şeydir.  
  
 User32 ve GDI 'da sistem, bir anlık mod kırpma sisteminde çalışmaktadır. Bir bileşenin işlenmesi gerektiğinde, sistem, bileşenin piksellere dokunmasına izin verilmeyen bir kırpma sınırları oluşturur ve ardından bileşene bu kutudaki pikselleri boyamak istenir. Bu sistem, yalnızca etkilenen bileşene dokunmanız gerektiğinde hiçbir değişiklik yapıldığında, her zaman tek bir pikselin rengine katkıda bulunmadığı için bellek kısıtlı sistemlerde çok iyi çalışmaktadır.  
  
 WPF, "boyacısı 'nın algoritması" boyama modelini kullanır. Bu, her bir bileşenin kırpılması yerine her bileşenin geri dönerek ekran önüne işlenmesi istenir. Bu, her bir bileşenin önceki bileşenin görüntüsüne göre boyamasına olanak tanır. Bu modelin avantajı karmaşık, kısmen saydam şekillere sahip olabilirsiniz. Günümüzün modern grafik donanımıyla, bu model görece hızlıdır (User32/GDI oluşturulduğunda bu durum değildir).  
  
 Daha önce belirtildiği gibi, WPF 'nin çekirdek felseı daha bildirime dayalı, "Özellik merkezli" programlama modeline geçmektedir. Görsel sistemde bu, birkaç ilginç yerde görüntülenir.  
  
 İlk olarak, korunan mod grafik sistemi hakkında düşündüğünüzde bu aslında kesin bir DrawLine/DrawLine tür modelinden veri yönelimli bir modele (yeni satır ()/New Line () kadar geçiş yapılmakta. Veri odaklı işleme taşıma, çizim yönergelerindeki karmaşık işlemlere özellikler kullanılarak ifade yapılmasına izin verir. Öğesinden türetilen türler, <xref:System.Windows.Media.Drawing> işleme için etkin bir şekilde nesne modelidir.  
  
 İkinci olarak, animasyon sistemini değerlendirdiğiniz takdirde neredeyse tamamen bildirime dayalı olduğunu görürsünüz. Bir geliştiricinin bir sonraki konumu veya bir sonraki rengi hesaplamasını gerektirmek yerine, animasyonları bir animasyon nesnesi üzerinde özellikler kümesi olarak ifade edebilirsiniz. Bu animasyonlar daha sonra geliştirici veya tasarımcı amacını ifade edebilir (bu düğmeyi 5 saniye içinde buraya taşıyın) ve sistem bunu gerçekleştirmek için en verimli yolu belirleyebilir.  
  
<a name="System_Windows_UIElement"></a>
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>Düzen, giriş ve olaylar dahil olmak üzere çekirdek alt sistemlerini tanımlar.  
  
 Düzen, WPF 'de temel bir kavramdır. Birçok sistemde, sabit bir düzen modeli kümesi vardır (HTML, düzen için üç modeli destekler; Flow, mutlak ve tablolar) ya da düzen için model yoktur (User32 gerçekten mutlak konumlandırmayı destekler). WPF, geliştiricilerin ve tasarımcıların, kesinlik mantığı yerine özellik değerleri tarafından yönetilen esnek, genişletilebilir bir düzen modeli istediği varsayımıyla başladı. Bu <xref:System.Windows.UIElement> düzeyde, düzen için temel sözleşme, ve ile iki aşamalı bir model kullanıma sunulmuştur <xref:System.Windows.UIElement.Measure%2A> <xref:System.Windows.UIElement.Arrange%2A> .  
  
 <xref:System.Windows.UIElement.Measure%2A>bir bileşenin ne kadar boyutta almak istediğinizi belirlemesine izin verir. Bu, <xref:System.Windows.UIElement.Arrange%2A> bir üst öğenin en iyi konumunu ve boyutunu belirlemesi için birkaç kez ölçüm yapmasını isteyeceğinden oluşan birçok durum olduğundan, bu öğeden ayrı bir aşamadır. Üst öğelerin ölçü için alt öğelere sormasını gerektiren olgu, WPF 'nin başka bir önemli felsefını içeriğe göre boyutlanacağını gösterir. WPF 'deki tüm denetimler içeriklerinin doğal boyutuna göre boyut yeteneğini destekler. Bu, yerelleştirmeyi çok daha kolay hale getirir ve öğelerin yeniden boyutlandırılması halinde dinamik düzen oluşturulmasına olanak sağlar. <xref:System.Windows.UIElement.Arrange%2A>Aşama, bir üst öğenin, her bir alt öğenin son boyutunu konumlandırabilmesine ve belirlemesine izin verir.  
  
 Genellikle WPF ve ilgili nesnelerin çıktı tarafı hakkında konuşacak kadar çok zaman harcanmıştır <xref:System.Windows.Media.Visual> . Ancak giriş tarafında çok fazla yenilik de vardır. WPF için giriş modelinde en temel değişiklik büyük olasılıkla, giriş olaylarının sistem aracılığıyla yönlendirildiği tutarlı modeldir.  
  
 Giriş, bir çekirdek modu cihaz sürücüsünde sinyal olarak gelir ve Windows çekirdeği ve User32 ile ilgili karmaşık bir süreç aracılığıyla doğru işleme ve iş parçacığına yönlendirilir. Girişe karşılık gelen User32 iletisi WPF 'e yönlendirildikten sonra WPF ham giriş iletisine dönüştürülür ve dağıtıcıya gönderilir. WPF, ham giriş olaylarının birden çok gerçek olaya dönüştürülmesini sağlar ve bu sayede "MouseEnter" gibi özelliklerin, garantili teslimin bulunduğu düşük düzeyde sisteme uygulanması sağlanır.  
  
 Her giriş olayı en az iki olaya dönüştürülür: bir "Önizleme" olayı ve gerçek olay. WPF 'deki tüm olayların, öğe ağacı aracılığıyla yönlendirme kavramı vardır. Olaylar, bir hedeften köke kadar geziniyorlarsa "kabarcık" olarak bildirilir ve kökte başlayıp bir hedefe geçiş yaptıysanız "tünel" olarak kabul edilir. Giriş önizleme olayları tüneli, ağaçtaki herhangi bir öğenin olayı filtreleme veya eylem üzerinde işlem yapması için bir fırsat sağlar. Normal (Önizleme dışı) olaylar bundan sonra hedeften köke kadar kabarcık sağlar.  
  
 Bu, tünel ve kabarcık aşaması arasında bölünen, klavye hızlandırıcıları gibi özelliklerin uygulanması bileşik bir dünyada tutarlı bir biçimde çalışır. User32 ' de, desteklemek istediğiniz tüm Hızlandırıcılar içeren tek bir genel tabloya sahip olarak klavye hızlandırıcılarını (CTRL + N "yeni" ile eşleme) uygulayabilirsiniz. Uygulamanıza yönelik dağıtıcıda, User32 'deki giriş iletilerini saptayabilir ve herhangi bir kayıtlı hızlandırıcı ile eşleşen bir hızlandırıcının olduğunu tespit eden **TranslateAccelerator** öğesini çağırırdı. WPF 'de, sistem tamamen "birleştirilebilen" olduğundan çalışmaz; herhangi bir öğe herhangi bir klavye hızlandırıcıyı işleyebilir ve kullanabilir. Bu iki aşama modelinin giriş için olması, bileşenlerin kendi "TranslateAccelerator" uygulamasını uygulamasına izin verir.  
  
 Bu adımı daha fazla yapmak için, <xref:System.Windows.UIElement> CommandBindings kavramını da tanıtır. WPF komut sistemi, geliştiricilerin komut bitiş noktası açısından, uygulayan bir şey olarak işlevsellik tanımlamasına olanak tanır <xref:System.Windows.Input.ICommand> . Komut bağlamaları bir giriş hareketi (CTRL + N) ile bir komut (yeni) arasında eşleme tanımlamak için bir öğe etkinleştirir. Hem giriş hareketleri hem de komut tanımları genişletilebilir ve kullanım zamanında birbirine bağlanabilir. Bu, örneğin, son kullanıcının bir uygulama içinde kullanmak istedikleri anahtar bağlamalarını özelleştirmesini sağlamak gibi basit hale getirir.  
  
 Bu noktaya kadar, WPF 'nin "çekirdek" özellikleri – PresentationCore derlemesinde uygulanan özellikler odağa sahiptir. WPF oluştururken, temel parçalar ( **Ölçü** ve **düzenleme**ile düzen için anlaşma gibi) ve çerçeve parçaları (örneğin, gibi belirli bir düzenin uygulanması gibi) arasında temiz bir ayrım, <xref:System.Windows.Controls.Grid> istenen sonuç idi. Amaç, bir yığında düşük bir genişletilebilirlik noktası sağlamaktır. Bu, dış geliştiricilerin gerekirse kendi çerçevelerini oluşturmalarına olanak tanır.  
  
<a name="System_Windows_FrameworkElement"></a>
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>, iki farklı şekilde aranabilir. WPF 'nin alt katmanlarında tanıtılan alt sistemler üzerinde bir ilke ve özelleştirme kümesi sunar. Ayrıca yeni alt sistemler kümesi de sağlar.  
  
 Tarafından tanıtılan birincil ilke, <xref:System.Windows.FrameworkElement> uygulama düzeni etrafında. <xref:System.Windows.FrameworkElement>tarafından tanıtılan temel düzen sözleşmesi üzerinde yapılar <xref:System.Windows.UIElement> ve düzen yazarlarının bir dizi özellik temelli düzen semantiğini daha kolay hale getiren bir "yuva" düzeni kavramı ekler. ,, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> , Ve gibi özellikler <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.Margin%2A> (bir ad vermek için), tüm bileşenlere <xref:System.Windows.FrameworkElement> Düzen kapsayıcıları içindeki tutarlı bir davranıştan türetilmiş tüm bileşenleri verir.  
  
 <xref:System.Windows.FrameworkElement>Ayrıca, WPF 'nin temel katmanlarında bulunan birçok özelliğe daha kolay API pozlaması sağlar. Örneğin, <xref:System.Windows.FrameworkElement> yöntemi aracılığıyla animasyonuna doğrudan erişim sağlar <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> . , Bir <xref:System.Windows.Media.Animation.Storyboard> dizi özellik için birden çok animasyonları betiğe yönelik bir yol sağlar.  
  
 ' İ tanıtan en önemli iki nokta, <xref:System.Windows.FrameworkElement> veri bağlama ve stillerdir.  
  
 WPF 'deki veri bağlama alt sistemi, bir uygulama oluşturmak için Windows Forms veya ASP.NET kullanan herkese görece tanıdık olmalıdır [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . Bu sistemlerin her birinde, belirli bir öğeden bir veya daha fazla özelliği bir veri parçasına bağlamak istediğinizi ifade etmek için basit bir yol vardır. WPF özellik bağlama, dönüştürme ve liste bağlama için tam desteğe sahiptir.  
  
 WPF 'deki veri bağlamasının en ilginç özelliklerinden biri veri şablonlarının sunumlarıdır. Veri şablonları, verilerin bir parçasının görselleştirme şeklini bildirimli olarak belirtmenize olanak tanır. Verilere bağlanabilen özel bir kullanıcı arabirimi oluşturmak yerine, bunun yerine sorunu açıp verilerin oluşturulacak görüntüyü belirlemesine izin verebilirsiniz.  
  
 Stil oluşturma aslında veri bağlamanın hafif bir biçimidir. Stil oluşturma kullanarak, paylaşılan bir tanımdan bir veya daha fazla öğe örneğine bir özellik kümesi bağlayabilirsiniz. Stiller bir öğeye açık başvuruya göre ( <xref:System.Windows.FrameworkElement.Style%2A> özelliği ayarlanarak) veya bir stili ÖĞENIN clr türüyle ilişkilendirerek dolaylı olarak uygulanır.  
  
<a name="System_Windows_Controls_Control"></a>
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Denetimin en önemli özelliği şablon oluşturma ' dır. WPF 'in bileşim sistemini bir tutulan mod işleme sistemi olarak düşünüyorsanız, şablon oluşturma bir denetimin işlemesini parametreli, bildirime dayalı bir şekilde açıklamaya olanak sağlar. <xref:System.Windows.Controls.ControlTemplate>, Bir alt öğe kümesi oluşturmak için bir betikten fazla değil, denetimin sunduğu özelliklerin bağlamalarıyla birlikte.  
  
 <xref:System.Windows.Controls.Control><xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.Background%2A> daha sonra bir denetimin görüntülenmesini özelleştirmek için,,,,,,, ve daha sonra bir şablon yazarı tarafından kullanılabilecek bir stok özellikleri kümesi sağlar <xref:System.Windows.Controls.Control.Padding%2A> . Bir denetimin uygulanması bir veri modeli ve etkileşim modeli sağlar. Etkileşim modeli, giriş hareketlerine (pencerenin üst köşesindeki kırmızı X simgesine tıklanması gibi) bir dizi komut (pencere için yakın) ve bağlamalar tanımlar. Veri modeli, etkileşim modelini özelleştirmek veya görüntülemeyi özelleştirmek (şablon tarafından belirlenir) için bir özellikler kümesi sağlar.  
  
 Veri modeli (Özellikler), etkileşim modeli (komutlar ve olaylar) ve görüntüleme modeli (şablonlar) arasında bölünen bu, bir denetimin görünüm ve davranışının tamamen özelleştirilmesine izin vermez.  
  
 Denetimlerin veri modelinin ortak bir yönü, içerik modelidir. Benzer bir denetime bakarsanız <xref:System.Windows.Controls.Button> , türünün "content" adlı bir özellik olduğunu görürsünüz <xref:System.Object> . Windows Forms ve ASP.NET içinde, bu özellik genellikle bir dize olur, ancak bir düğmeye koyabileceğiniz içerik türünü sınırlar. Bir düğmenin içeriği basit bir dize, karmaşık veri nesnesi veya bir öğe ağacının tamamı olabilir. Veri nesnesi söz konusu olduğunda, veri şablonu bir görüntü oluşturmak için kullanılır.  
  
<a name="Summary"></a>
## <a name="summary"></a>Özet  
 WPF, dinamik, veri odaklı sunum sistemleri oluşturmanıza olanak tanımak için tasarlanmıştır. Sistemin her bölümü, davranışını oluşturan özellik kümeleri aracılığıyla nesne oluşturmak için tasarlanmıştır. Veri bağlama, sistemin temel bir parçasıdır ve her katmanda tümleşiktir.  
  
 Geleneksel uygulamalar bir görüntü oluşturup daha sonra bazı verilere bağlar. WPF 'de, denetimle ilgili her şey, her bir veri bağlama türü tarafından oluşturulur. Düğme içinde bulunan metin, düğmenin içinde oluşturulan bir denetim oluşturularak ve görünümünü düğmenin içerik özelliğine bağlayarak görüntülenir.  
  
 WPF tabanlı uygulamalar geliştirmeye başladığınızda çok tanıdık gelmelidir. Windows Forms veya ASP.NET kullanarak özellikleri, nesneleri ve veri bağlamayı birçok şekilde ayarlayabilirsiniz. WPF mimarisine daha derin bir araştırma sayesinde, uygulamanın çekirdek sürücüsü olarak verileri temel alan çok daha zengin uygulamalar oluşturmak için bir olasılık olduğunu fark edeceksiniz.  
  
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
