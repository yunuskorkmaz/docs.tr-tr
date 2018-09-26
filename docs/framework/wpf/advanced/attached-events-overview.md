---
title: Ekli Olaylara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
ms.openlocfilehash: c6a8b3b7355d315b83f859e7016018b56ade5484
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112474"
---
# <a name="attached-events-overview"></a>Ekli Olaylara Genel Bakış
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir dil bileşeni ve adlı olayın türünü tanımlayan bir *ekli olay*. Ekli olay kavramını belirli bir olay işleyicisi gerçekten tanımlar veya olay devralan bir öğe yerine rastgele bir öğe eklemenize olanak tanır. Bu durumda, ne potansiyel olarak olayı tetiklenmeden nesnesi veya örneği işleme hedef tanımlar veya aksi takdirde olay "sahip".  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, okuduğunuz varsayılır [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md) ve [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Ekli olay söz dizimi  
 Ekli olaylar sahip bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] söz dizimi ve yedekleme kodu tarafından ekli olay kullanımını desteklemek için kullanılacak kodlama düzeni.  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] söz dizimi, ekli olay, olay adına göre değil, ancak bir nokta (.) ayrılmış alt türü artı tarafından belirtilir. Olay adı, kendi türü adı ile tam olduğundan, oluşturulabilir herhangi bir öğe eklenmesi hiçbir ekli olay ekli olay söz dizimi sağlar.  
  
 Örneğin, aşağıdaki gibidir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özel bir işleyici ekleme söz dizimi `NeedsCleaning` ekli olay:  
  
 [!code-xaml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Not `aqua:` önek; ön eki Bu durumda özel bir eşlenen xmlns gelen özel olay ekli olay olduğu için gereklidir.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Ekli olayları nasıl WPF uygular  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekli olayları tarafından desteklenen bir <xref:System.Windows.RoutedEvent> alan ve oluşturulduktan sonra ağaç yönlendirilir. Genellikle, bir sistem veya hizmet kaynağı (olayı başlatan nesne) ekli olay kaynağıdır ve olayı başlatan kod çalışan nesne bu nedenle öğe ağacında doğrudan bir parçası değil.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Ekli olaylar için senaryolar  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekli olayları belirli özellik alanlarında mevcut olduğu gibi yerlerde hizmet düzeyi soyutlama statik tarafından etkinleştirilen olaylar <xref:System.Windows.Input.Mouse> sınıfı veya <xref:System.Windows.Controls.Validation> sınıfı. Hizmeti kullanmak ya da etkileşime sınıflar ya da ekli olay sözdiziminde olay kullanabilirsiniz veya sınıf özelliklerini nasıl tümleştirildiğini bir parçası olan gönderilmiş bir olay olarak ekli olay yüzey seçebilirsiniz.  
  
 Ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olaylar, burada olacaktır kullanın ya da ekli olay işleyici doğrudan çok sınırlı senaryoları sayısını tanımlar. Genellikle, ekli olay mimarisi amaca hizmet eder, ancak daha sonra bir ekli olmayan iletilen (yedeklenen bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay "sarmalayıcı") yönlendirilmiş olay.  
  
 Ekli olay temel alınan örneği için <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> daha kolayca verilen herhangi işlenebilir <xref:System.Windows.UIElement> kullanarak <xref:System.Windows.UIElement.MouseDown> üzerindeki <xref:System.Windows.UIElement> ekli olay söz dizimi ile baş yerine içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kod. Giriş cihazlarının gelecekteki genişleme için izin verdiğinden ekli olay mimarisinde bir amaca hizmet verir. Yükseltmek kuramsal bir cihazı yalnızca gerekir <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> fare girişi benzetmekte siparişi ve türetilen ihtiyaç duymaz <xref:System.Windows.Input.Mouse> Bunu yapmak için. Ancak, bu senaryo kod olayların işlenmesini içerir ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ekli olay işlemeyi bu senaryoyla ilgili değildir.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>WPF içinde ekli bir olay işleme  
 Ekli olay ve yazılacak, işleyici kodu işleme işlemi temel gönderilmiş bir olay ile aynıdır.  
  
 Genel olarak, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olay çok farklı değil bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş olay. Olay kaynağı nasıl ve ne bir sınıf üyesi tarafından sunulduğunu fark vardır (da etkileyen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işleyici sözdizimi).  
  
 Ancak, daha önce belirtildiği gibi mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olaylar özellikle amaçlanmayan işlemede için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Daha sık amacı olayı, olay durumu genellikle kodda oluşturulur ve ayrıca sınıf ilgili üst sınıfta işleme kullanır birleştirme üst öğede bir durum rapor bileşik bir öğeyi etkinleştirmektir. Örneğin, içindeki öğelerin bir <xref:System.Windows.Controls.Primitives.Selector> ekli oluşturması beklenir <xref:System.Windows.Controls.Primitives.Selector.Selected> sınıfı olayı tarafından işlenir <xref:System.Windows.Controls.Primitives.Selector> sınıfı ve tarafından potansiyel olarak dönüştürülür <xref:System.Windows.Controls.Primitives.Selector> farklı gönderilmiş bir olay sınıfına <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Yönlendirilmiş olaylar ve sınıf işlemesi hakkında daha fazla bilgi için bkz. [işaretleme yönlendirilmiş olayları işlenmiş ve bir sınıf olarak](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Yönlendirilmiş olaylar kendi ekli olaylar olarak tanımlama  
 Ortak türevi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel sınıflar, sınıfınız içinde belirli bir desen yöntemlerini dahil ederek kendi ekli olaylar uygulayabilir ve yardımcı programını kullanarak temel zaten olan yöntemler sunar.  
  
 Desen aşağıdaki gibidir:  
  
-   Bir yöntem **Ekle*EventName*işleyici** iki parametrelere sahip. İlk parametre olay tanımlamanız gerekir ve tanımlanan olay adları ile eşleşmelidir ***EventName*** yöntemi adı. İkinci parametre eklemek için işleyicisidir. Yöntem olmalıdır `public` ve `static`, dönüş değeri ile.  
  
-   Bir yöntem **Kaldır*EventName*işleyici** iki parametrelere sahip. İlk parametre olay tanımlamanız gerekir ve tanımlanan olay adları ile eşleşmelidir ***EventName*** yöntemi adı. Kaldırılacak işleyici ikinci parametredir. Yöntem olmalıdır `public` ve `static`, dönüş değeri ile.  
  
 **Ekle*EventName*işleyici** erişimci yöntemi kolaylaştıran [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemesini ekli olay işleyicisi öznitelikleri bir öğe üzerinde bildirilir. **Ekle*EventName*işleyici** ve **Kaldır*EventName*işleyici** yöntemleri de olay işleyicisi deposu için kod erişimi etkinleştirme ekli olay.  
  
 Bu genel düzen henüz bir çerçeve uygulaması pratik için yeterince kesin değildir çünkü verilen herhangi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu uygulaması mimarisi ve destekleyici dil temelindeki olayları tanımlamak için farklı şemalara sahip. Bu nedenlerden biri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygular ekli olayları yönlendirilmiş olaylar olarak; bir olay için kullanılacak bir tanımlayıcı (<xref:System.Windows.RoutedEvent>) tarafından tanımlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi. Ayrıca, bir olay yönlendirme bir doğal uygulama uzantısıdır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ekli olay kavramını dil düzeyi.  
  
 **Ekle*EventName*işleyici** uygulama için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olay çağırmadan oluşur <xref:System.Windows.UIElement.AddHandler%2A> yönlendirilmiş olay ve bağımsız değişkenler olarak işleyici.  
  
 Bu uygulama stratejisi ve yönlendirilmiş olay sistemi Genel ekli olayları işleme ya da kısıtlama <xref:System.Windows.UIElement> türetilmiş sınıflar veya <xref:System.Windows.ContentElement> sınıfları, çünkü yalnızca söz konusu sınıfın türetilmiş <xref:System.Windows.UIElement.AddHandler%2A> uygulamaları.  
  
 Örneğin, aşağıdaki kod tanımlar `NeedsCleaning` sahip sınıf bir olayda bağlı `Aquarium`kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olay stratejisini gönderilmiş bir olay olarak ekli olay bildirme.  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Ekli olay tanımlayıcı alanı oluşturmak için kullanılan yöntem Not <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, bağlı olmayan yönlendirilmiş olay kaydetmek için kullanılan gerçekten yöntem ile aynıdır. Tüm ekli olaylar ve yönlendirilmiş olaylar için merkezi bir iç deposuna kaydedilir. Bu olay deposu uygulaması içinde ele alınmıştır "olayları için bir arabirim olarak" kavramsal konuları etkinleştirir [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Bir WPF ekli olayı oluşturma  
 Genellikle varolan yükseltme gerekmez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodunuzu ekli olayları tanımlanmış. Bu olaylar "hizmet" genel kavramsal model izleyin ve hizmet sınıfları gibi <xref:System.Windows.Input.InputManager> olayları oluşturma için sorumludur.  
  
 Ancak, temel bir özel ekli olay tanımlıyorsanız, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] alma modelini ekli olayları üzerinde <xref:System.Windows.RoutedEvent>, kullanabilirsiniz <xref:System.Windows.UIElement.RaiseEvent%2A> herhangi bir ekli olay oluşturmak için <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement>. (Veya ekli) gönderilmiş bir olay oluşturma, belirli bir öğe öğe ağacında olay kaynağı olarak bildirilmesini gerektirir; Bu kaynağı olarak bildirilen <xref:System.Windows.UIElement.RaiseEvent%2A> çağırıcı. Hangi öğe belirleme ağacında kaynak hizmetinizin sorumluluğundadır olarak bildirildi  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Ayrıntılı XAML Sözdizimi](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [WPF için XAML ve Özel Sınıflar](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
