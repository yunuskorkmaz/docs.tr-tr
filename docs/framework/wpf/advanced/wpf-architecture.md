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
ms.openlocfilehash: 50a7e1b08c31b5d0fb779dabf617a08bbb4c6cf4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195924"
---
# <a name="wpf-architecture"></a>WPF Mimarisi
Bu konu, Windows Presentation Foundation (WPF) sınıf hiyerarşisi Kılavuzlu bir turu sağlar. Ana alt çoğunu kapsar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ve nasıl etkileşim kurduklarını açıklar. Bu ayrıca mimarları tarafından yapılan seçimleri bazıları ayrıntılı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
  
<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Birincil [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programlama modeli yönetilen kod gösterilir. Tasarım aşamasında başlarında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] birkaç satırı sistem yönetilen bileşenleri yönetilmeyen olanları arasında nerede çizileceğini hakkında tartışmalarını somut vardı. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Daha üretken ve daha güçlü (dahil, bellek yönetimi, hata işleme, ortak tür sistemi, vb.) geliştirme sağlayan özellikler sunar ancak bunlar bir bedeli.  
  
 Ana bileşenleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki çizimde gösterilmiştir. Kırmızı (PresentationFramework PresentationCore ve milcore) diyagramın ana kod bölümlerini bölümleridir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Bu tek bir yönetilmeyen – milcore bileşendir. Milcore ile olan sıkı entegrasyonundan etkinleştirmek için yönetilmeyen kodda yazıldığı [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Tümünü Göster [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aracılığıyla gerçekleştirilir [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] altyapısı, etkili donanım ve yazılım işlemeye olanak tanır. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bellek ve yürütmesi üzerinde ayrıntılı denetim de gereklidir. Milcore bileşim motoru son derece hassas ve gerekli birçok avantaj sunar performans olduğundan [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] performans elde etmek için.  
  
 ![WPF, .NET Framework içindeki konumu. ](../../../../docs/framework/wpf/advanced/media/wpf-architect1.PNG "wpf_architect1")  
  
 Yönetilen ve yönetilmeyen bölümleri arasındaki iletişimi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bu konunun ilerleyen bölümlerinde ele alınmıştır. Yönetilen bir programlama modeli geri kalanında, aşağıda açıklanmıştır.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Nesnelerin çoğu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğesinden türetilen <xref:System.Windows.Threading.DispatcherObject>, iş parçacığı oluşturma ve eşzamanlılık ile ilgili temel yapılarından sağlar. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gönderici tarafından uygulanan bir Mesajlaşma sistemi temel alır. Bu gibi tanıdık çalışır [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ileti pompası; aslında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dağıtıcı User32 iletileri arası iş parçacığı çağrı yapmak için kullanır.  
  
 İçinde eşzamanlılık tartışırken anlaşılması gereken kavramlar gerçekten iki çekirdek vardır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – dispatcher ve iş parçacığı benzeşimini.  
  
 Tasarım aşaması sırasında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], yürütme için tek bir diziyi hedefi olan ancak bir iş parçacığı olmayan "Benzetilen" modeli. Bir bileşen durumu herhangi bir türde depolamak için çalışan bir iş parçacığı kimliğini kullanır. iş parçacığı benzeşimini olur. Bu en yaygın formun durumunu depolamak için iş parçacığı yerel deposu (TLS) kullanmaktır. İş parçacığı benzeşimini her mantıksal iş parçacığı, yoğun bellek dönüşebilir işletim sisteminde yalnızca bir fiziksel iş parçacığına göre ait olmasını da gerektirir. Sonunda WPF'nin iş parçacığı modeli tek iş parçacıklı yürütme iş parçacığı benzeşimini ile mevcut User32 iş parçacığı modeli ile eşitlenmiş kalmasını. Birincil nedeni birlikte çalışabilirlik – sistemleri [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], Pano ve Internet gerektiren tek iş parçacığı benzeşimini (STA) yürütme Explorer tüm.  
  
 STA iş parçacığı ile nesneleri düşünüldüğünde olduğuna göre iş parçacıkları arasında iletişim kurmak ve doğrulamak için bir yol doğru iş parçacığı üzerinde olan gerekir. Burada dağıtıcı rolü arasındadır. Dağıtıcı sistemiyle birden fazla öncelikli kuyruk gönderme temel bir iletidir. Ham giriş bildirimleri (fare taşındı), framework işlevleri (Düzen) veya kullanıcı komutları iletileri örneklerini içerir (Bu yöntemi yürütme). Türetilen <xref:System.Windows.Threading.DispatcherObject>, oluşturduğunuz bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] STA davranışı olan nesne ve bir işaretçi bir dağıtıcı için oluşturma sırasında sunulur.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Bir yapı içinde kullanılan birincil mimari felsefeleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yöntemleri veya olayları üzerinden özellikleri için bir tercih edildi. Özellikler bildirim temelli ve izin daha kolayca eylemi yerine hedefi belirtin. Bu da bir model temelli veya veri odaklı, sistem kullanıcı arabirimi içeriği görüntülemek için desteklenir. Bu anlayışın, hedeflenen etkisini daha iyi bir uygulamanın davranışını denetlemek için bağlama yapılamadı daha fazla özellik oluşturma vardı.  
  
 Özellikler, miktardan daha zengin bir özellik sistemi tarafından sistemin daha fazla bilgi için [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] sağlar gerekiyordu. Bir basit bu zenginliğini değişiklik bildirimleri örneğidir. İki yönlü bağlama etkinleştirmek için her iki tarafında bir değişiklik bildirimi desteklemek için bağlama gerekir. Özellik değerlerine bağlı davranışı için özellik değeri değiştiğinde bildirim almak gerekir. Microsoft .NET Framework bir arabirime sahip **INotifyPropertyChange**, isteğe bağlıdır ancak değişiklik bildirimleri yayımlamak bir nesne sağlar.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğesinden türetilen daha zengin bir özellik sistemi sağlar <xref:System.Windows.DependencyObject> türü. Özellik ifadeleri bağımlılıkları izler ve bağımlılıkları değiştirdiğinizde, özellik değerlerini otomatik olarak yeniden doğrular, özellik sistemi gerçek anlamda bir "bağımlılık" özelliği sistemidir. Örneğin, devralan bir özellik varsa (gibi <xref:System.Windows.Controls.Control.FontSize%2A>), özellik değeri devralan bir öğenin bir üst öğede değişirse sistem otomatik olarak güncelleştirilir.  
  
 Temelini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özelliği sistemidir kavramı, bir özellik ifadesi. Bu ilk sürümünde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]özellik ifadesi sistem kapatıldıktan ve ifadelerin tüm framework'ün bir parçası olarak sağlanır. Stil oluşturma, veri bağlama, özellik sistemi yok veya devralma sabit kodlanmış, ancak bunun yerine framework içindeki sonraki katmanları tarafından sağlanan nedenini ifadelerdir.  
  
 Özellik sistemi özellik değerlerini seyrek depolama için de sağlar. Nesneleri, düzinelerce (değilse yüzlerce) özelliklerinin olabilir ve değerleri çoğunu varsayılan durumlarına (devralınan, stilleri tarafından ayarlayın vb.), her bir nesnenin örneğine tam ağırlığını üzerinde tanımlanan her bir özellik olması gerekir.  
  
 Son yeni özellik sistemi iliştirilmiş özellikler kavramı özelliğidir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğeleri oluşturma ve bileşeni yeniden ilkesini üzerinde oluşturulur. Bu durum bazı genellikle öğeyi içeren (gibi bir <xref:System.Windows.Controls.Grid> Düzen öğesi) alt öğeleri (örneğin, satır/sütun bilgileri) davranışını denetlemek için ek veriler gerekiyor. Bu özelliklerin tümünü her öğe ile ilişkilendirilmek yerine, herhangi bir nesnenin herhangi bir nesne için özellik tanımları sağlamak izin verilmez. Bu JavaScript "expando" özelliklerine benzer.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Sistem tanımlı bir sonraki adıma ekrana çizilmiş piksel almaktır. <xref:System.Windows.Media.Visual> Sınıfı, görsel nesneler bir ağaç her isteğe bağlı olarak çizim yönergeleri ve bu yönergeleri (kırpma, dönüştürme, vb.) işlemek nasıl hakkındaki meta verileri içeren oluşturmak için sağlar. <xref:System.Windows.Media.Visual> son derece basit ve esnek, böylece hiçbir genel özelliklerin çoğunu sahip olacak şekilde tasarlanan [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] Etkilenme ve yoğun olarak korumalı bir geri çağırma işlevleri kullanır.  
  
 <xref:System.Windows.Media.Visual> gerçekten giriş noktası olan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oluşturma sistemi. <xref:System.Windows.Media.Visual> yönetilen iki bu sistemler arasında bağlantı noktasıdır [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] ve yönetilmeyen milcore.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarafından yönetilen milcore tarafından yönetilmeyen veri yapılarını geçiş verilerini görüntüler. Birleşim düğüm olarak adlandırılan bu yapılar, her düğümde işleme yönergeleri içeren bir hiyerarşik görünüm ağacı temsil eder. Sağ tarafta, aşağıdaki şekilde gösterilen bu ağaç, yalnızca bir Mesajlaşma protokolü aracılığıyla erişilebilir.  
  
 Programlamada [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], oluşturduğunuz <xref:System.Windows.Media.Visual> öğeleri ve dahili olarak kompozisyon ağacı bu Mesajlaşma protokolü üzerinden iletişim türetilen türler. Her <xref:System.Windows.Media.Visual> içinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] birini, yok veya birkaç bileşim düğümleri oluşturabilir.  
  
 ![Windows Presentation Foundation görsel ağaç. ](../../../../docs/framework/wpf/advanced/media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Burada – görsel ağacının tümünü fark için çok önemli bir mimari ayrıntı yoktur ve yönergeleri çizim önbelleğe alınır. Grafik koşullarında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tutulan işleme sistemi kullanır. Bu, sistemin kullanıcı kodu geri çağırmalarına üzerinde engelleme oluşturma sistemi olmadan yüksek yenileme hızı repaint sağlar. Bu durum, yanıt vermeyen bir uygulamanın görünümünü önlemeye yardımcı olur.  
  
 Sistem aslında oluşturma performansını diyagramda gerçekten belirgin olmayan başka bir önemli ayrıntı olur.  
  
 User32 içinde ve [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], sistemin bir anlık mod kırpma sistemde çalışır. İşlenecek bir bileşen gerektiğinde sistem dışında bileşen piksel dokunmaya izin verilmiyor ve kutunun piksellerde boyamak için bileşen sonra kullanıcıdan bir kırpma sınırları belirler. Bir şey değiştiğinde, yalnızca etkilenen bileşeni touch gerektiği için bu sistemin kısıtlanmış belleğe sistemlerinde çok iyi çalışır: her zamankinden katkıda bulunan tek bir piksel rengi için iki bileşen yok.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] "model boyama painter'ın algoritması" kullanır. Bu, her bileşen kırpma yerine her bileşen arkadan öne görüntü işlemek için sorulur olduğunu anlamına gelir. Bu, her bileşen önceki bileşenin görüntü boyama sağlar. Bu modelin avantajı, karmaşık, kısmen saydam şekiller sahip olduğunu belirtir. Günümüzün modern grafik donanımı ile bu model görece hızlı çalışır (durum vektöre olduğunda User32 / [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] oluşturulan).  
  
 Bir çekirdek felsefesini daha önce de belirtildiği [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programlama için bir daha bildirimsel "özelliği merkezli" modeli taşımaktır. Görsel sistemde bu ilgi çekici birkaç içinde gösterilir.  
  
 Tutulan modu grafik sistemi hakkında düşünüyorsanız, öncelikle bu gerçekten bir kesinlik temelli DrawLine/DrawLine türü modeli uzağa yönlendirilmiş bir veri modeli için – taşınıyor yeni satır () / yeni Line(). Bu veri tabanlı işleme geçmeye özellikleri kullanılarak ifade için çizim yönergeleri üzerinde karmaşık işlemlere izin verir. Öğesinden türetilen türler <xref:System.Windows.Media.Drawing> etkili bir şekilde işleme için nesne modeli olan.  
  
 İkinci animasyon sistemi değerlendiriliyorsa neredeyse tamamen bildirim temelli olduğunu görürsünüz. Sonraki konuma ya da sonraki renk hesaplamak bir geliştirici gerektiren yerine bir animasyon nesne üzerinde bir özellikler kümesi animasyonları koyabilirsiniz. Bu animasyonları amacı geliştirici veya Tasarımcısı, ardından ifade edebilirsiniz (taşıma bu düğmeyi buradan oraya için 5 saniye içinde) ve sistem bunu yapmaya yönelik en verimli şekilde belirleyebilirsiniz.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> Düzen, giriş ve olaylar gibi temel alt sistemlerin tanımlar.  
  
 Temel kavram olarak düzendir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Birçok sistemde Düzen modellerin düzeltildi ayarlanmış yok (HTML düzeni için üç modeli destekler; akış, mutlak ve tablolar) veya düzeni için hiçbir modeli (User32 aslında yalnızca destekler mutlak konumlandırma). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geliştiricilerin ve tasarımcıların kesin mantık yerine özellik değerleri tarafından yönlendirilen bir esnek, Genişletilebilir düzen modeli istiyordu varsayımına başladı. Konumunda <xref:System.Windows.UIElement> düzeyi, sunulan düzeni için temel sözleşmesi – iki aşama modeliyle <xref:System.Windows.UIElement.Measure%2A> ve <xref:System.Windows.UIElement.Arrange%2A> geçirir.  
  
 <xref:System.Windows.UIElement.Measure%2A> Bunu yapmak istiyorsunuz ne kadar boyutunu belirlemek bir bileşen sağlar. Bu, bir ayrı aşama <xref:System.Windows.UIElement.Arrange%2A> burada bir ana öğeye sorar kendi en iyi konumunu ve boyutunu belirlemek için birkaç kez ölçmek için bir alt pek çok durumda olduğundan. Üst öğeler alt öğeleri ölçmek için sorun olgu başka bir anahtar felsefesini gösterir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] -içerik boyutu. Tüm denetimleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriklerinin doğal boyutu özelliğini destekler. Bu durum, yerelleştirme çok daha kolay hale getirir ve öğeleri yeniden boyutlandırdığınızda öğelerin dinamik düzen için sağlar. <xref:System.Windows.UIElement.Arrange%2A> Aşaması yerleştirin ve her alt son boyutunu belirlemek bir üst sağlar.  
  
 Çıkış tarafı hakkında konuşmak çok zaman genellikle harcandığını [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> ve ilgili nesneleri. Ancak yenilik İnanılmaz derecede giriş tarafında de yoktur. Büyük olasılıkla en temel değişikliği için giriş modelinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tutarlı model olarak giriş olayları sistem üzerinden yönlendirilir.  
  
 Giriş olarak bir çekirdek modu cihaz sürücüsünü bir sinyal kaynaklanan ve doğru işlem ve iş parçacığı User32 ve Windows çekirdek içeren karmaşık bir işlem aracılığıyla yönlendirilecek. Girişin karşılık gelen User32 ileti yönlendirilir sonra [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], dönüştürülür bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ham giriş iletisi ve dağıtıcı için gönderilir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] garantili teslim sistemiyle düşük düzeyde uygulanacak "MouseEnter" gibi özellikleri etkinleştirmek, birden çok gerçek olaylara dönüştürülecek ham giriş olayları sağlar.  
  
 Her giriş olayı, en az iki olay için – bir "Önizleme" ve gerçek olaya dönüştürülür. Tüm olaylar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğe ağacı üzerinden yönlendirme bir kavram vardır. Bir hedefin ağacı kök çapraz geçiş yapma ve kök dizininde başlatın ve bir hedef Aşağı Çapraz "tünel oluşturmak için" söylenir olayları "Kabarcık" söylenir. Önizleme olayları tünel filtreleyin veya olayı harekete fırsatı ağacındaki herhangi bir öğeyi etkinleştirmeden, giriş. Normal (ön izlemesiz) olayları, ardından hedef kök kadar Kabarcık.  
  
 Bu bölünmüş tüneli ve kabarcık aşaması arasında tutarlı bir şekilde bir bileşik dünyada klavye Hızlandırıcılar çalışmak gibi özelliklerinin uygulamasını sağlar. User32 desteklemek istediğiniz tüm Hızlandırıcıları içeren tek bir genel tablo (Ctrl + N eşleme "Yeni") sağlayarak klavye Hızlandırıcılar uygulayabilir. Uygulamanız için dağıtıcı olarak, çağıracak **TranslateAccelerator** User32 giriş iletileri bulmak ve herhangi bir kayıtlı Hızlandırıcı eşleşen belirlemek. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bu çalışmaz çünkü sistem tam olarak "birleştirilebilir" – herhangi bir öğenin işlemek ve tüm klavye kısayol tuşu kullanın. Bu giriş için iki aşaması modeli kendi "TranslateAccelerator" uygulamak bileşenleri sağlar.  
  
 Bunu bir adım ileriye için <xref:System.Windows.UIElement> CommandBindings kavramı da tanıtılmaktadır. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Komut sistemi uygulayan bir şey komut bitiş noktası – açısından işlevselliği tanımlamak için geliştiriciler sağlar <xref:System.Windows.Input.ICommand>. Komut bağlamaları bir giriş hareket (Ctrl + N) ve bir komut (yeni) arasında bir eşleme tanımlamak bir öğe sağlar. Giriş hareketlerini ve komutu tanımları genişletilebilir ve birlikte kullanım zamanında kablolu. Bu Önemsiz, örneğin, bunlar bir uygulamadaki kullanmak istediğiniz anahtar bağlamalarını özelleştirmek bir son kullanıcı olanak sağlar.  
  
 Bu noktada konusunda, "temel" özellikleri [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – PresentationCore derlemesinde uygulanmış özellikler odağı olmuştur. Oluşturma sırasında [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], temiz temel parçalar arasında ayrım (ister düzeniyle sözleşmesi **ölçü** ve **Düzenle**) ve (örneğin, bir özel uygulanışı framework parçaları Düzen gibi <xref:System.Windows.Controls.Grid>) arzu edilen sonucu oluştu. Hedef, kendi çerçeveleri oluşturmak dış geliştiriciler izin yığınında düşük bir genişletilebilirlik noktası gerekli sağlamaktı.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> iki farklı yolla attınız. İlkeleri ve alt sistemlerin daha düşük katmanında sunulan özelleştirme kümesi sunar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ayrıca, yeni bir alt kümesini sunar.  
  
 Birincil ilke tarafından tanıtılan <xref:System.Windows.FrameworkElement> geçici bir çözüm uygulama düzeni. <xref:System.Windows.FrameworkElement> tarafından sunulan temel düzeni sözleşme üzerine inşa edilmiştir <xref:System.Windows.UIElement> ve bir düzen "özelliği düzeni semantiği temelli tutarlı özellik kümesi Düzen yazarlar kolaylaştırır yuvası" kavramı ekler. Özellikleri gibi <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>, ve <xref:System.Windows.FrameworkElement.Margin%2A> (birkaç örnek vermek gerekirse) öğesinden türetilen tüm bileşenleri vermek <xref:System.Windows.FrameworkElement> Düzen kapsayıcıları içinde tutarlı bir davranış.  
  
 <xref:System.Windows.FrameworkElement> Ayrıca daha kolay sağlar [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] maruz kalma riskinizi birçok özelliği temel katmanda bulunan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Örneğin, <xref:System.Windows.FrameworkElement> animasyon doğrudan erişim sağlayan <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> yöntemi. A <xref:System.Windows.Media.Animation.Storyboard> birden çok animasyon bir özellikler kümesini karşı komut dosyası için bir yol sağlar.  
  
 İki en önemli şey, <xref:System.Windows.FrameworkElement> tanıtır veri bağlama ve stilleri.  
  
 Veri bağlama alt [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kullandığı herhangi biri için nispeten tanıdık [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] uygulama oluşturmak için [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Her birinde bu sistemler, istediğiniz bir veri parçasını bağlanması için belirli bir öğeyi özelliklerinden bir veya daha fazla ifade etmek için basit bir yolu yoktur. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özellik bağlama, Dönüşüm ve liste bağlama için tam destek sunar.  
  
 Bir veri bağlamanın en ilginç özelliklerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] veri şablonlarının giriş niteliğindedir. Veri şablonları, bir veri parçasını nasıl görselleştirilmiş bildirimli olarak belirtmenize olanak sağlar. Verilere bağlı bir özel kullanıcı arabirimi oluşturmak yerine, bunun yerine sorunu geri dönüş ve belirleyin oluşturulur görüntü verileri sağlar.  
  
 Stil gerçekten bir basit veri bağlama biçimidir. Stil kullanarak bir özellikler kümesi paylaşılan bir tanımdan bir öğenin bir veya daha fazla örneklerine bağlayabilirsiniz. Stilleri bir öğeye uygulanan ya da açık bir başvuru (ayarlayarak <xref:System.Windows.FrameworkElement.Style%2A> özelliği) veya bir stil ile ilişkilendirerek örtük olarak [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] öğe türü.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Denetimin en önemli şablon oluşturma özelliğidir. WPF'nin oluşturma sistemi saklama modu oluşturma sistemi olarak düşünüyorsanız, şablon oluşturma, işleme parametreli, bildirim temelli bir biçimde açıklamak bir denetim sağlar. A <xref:System.Windows.Controls.ControlTemplate> gerçekten daha fazla denetim tarafından sunulan özelliklere bağlamalarla öğeler bir alt kümesini oluşturmak için bir komut dosyası bir şey değildir.  
  
 <xref:System.Windows.Controls.Control> Stok özellikleri sunmaktadır <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, şablon yazarlar sonra bir denetim görüntüsünü özelleştirmek için kullanabileceğiniz birkaç. Uygulamasını bir denetimin, bir veri modeli ile etkileşim modeli sağlar. (Kapanış penceresi için gibi) komutlar ve bağlamaları (penceresinin üst köşesindeki kırmızı X simgesine tıklandığında gibi) hareketler girişi için bir dizi etkileşimi modelini tanımlar. Veri modeli etkileşim modelini özelleştirin veya (şablon tarafından belirlenir) görüntüsünü özelleştirmek için özellikler kümesi sağlar.  
  
 Bu bölme (Özellikler) veri modeli, etkileşim modeli (komutlar ve olayları) ve görüntü modeli (şablon) arasındaki bir denetimin görünümünü ve davranışını tamamen özelleştirme sağlar.  
  
 Bir ortak denetimleri ve veri modelinin içerik modeli yönüdür. Bir denetimi bakarsanız ister <xref:System.Windows.Controls.Button>, türü "içerik" adlı bir özellik olduğunu göreceksiniz <xref:System.Object>. İçinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)], bu özellik genelde bir dize olacaktır –, içerik türü sınırlar ancak de bir düğme koyabilirsiniz. Ya da basit bir dize, bir karmaşık veri nesnesi veya tüm öğe ağacı bir düğme için içerik olabilir. Bir veri nesnesi söz konusu olduğunda, bir görüntü oluşturmak için veri şablonunu kullanılır.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Özet  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Sunu sistemleri verilerle dinamik oluşturmanıza olanak tanımak üzere tasarlanmıştır. Sistemin her bölüm, özellik kümeleri nesnelerde bu davranışı oluşturmak için tasarlanmıştır. Veri bağlama, sistem temel bir parçasıdır ve her katmanında tümleşiktir.  
  
 Geleneksel uygulamaları bir görüntü oluşturun ve ardından bazı verilere bağlayın. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], her yönüyle görüntü denetimi ile ilgili her şeyi herhangi bir türde veri bağlama oluşturulur. Bir düğme içinde bulunan metin, düğme içinde oluşan bir denetim oluşturarak ve görünümünü düğmenin içerik özelliğine bağlama görüntülenir.  
  
 Geliştirme başladığınızda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tabanlı uygulamalar, tanıdık gelecektir. Özellikleri, nesneleri kullanma ayarlayabilirsiniz ve veri bağlama çok benzer şekilde kullanarak yapabilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]. Daha ayrıntılı bir araştırma mimarisi ile [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], olasılığını temelde veri uygulamanın çekirdek sürücüsü olarak ele almanız çok daha zengin uygulamalar oluşturmak için var olduğunu göreceksiniz.  
  
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
