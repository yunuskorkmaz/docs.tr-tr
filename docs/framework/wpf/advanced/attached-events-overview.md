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
ms.openlocfilehash: a3a2f711840ad7f6e28443dac3c18501cd4400e0
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401409"
---
# <a name="attached-events-overview"></a>Ekli Olaylara Genel Bakış
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir dil bileşeni ve *ekli olay*olarak adlandırılan olay türünü tanımlar. Ekli bir olay kavramı, olayı gerçekten tanımlayan veya devralan bir öğe yerine, belirli bir olaya yönelik bir işleyiciyi rastgele bir öğeye eklemenizi sağlar. Bu durumda, nesne potansiyel olarak ne tür bir şekilde tetiklemez ve hedef işleme örneği, olayı tanımlar veya başka bir şekilde "sahip değildir".  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, [yönlendirilmiş olaylara genel bakış](routed-events-overview.md) ve [xaml 'ye Genel Bakış (WPF)](xaml-overview-wpf.md)okumanız varsayılmaktadır.  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Ekli olay sözdizimi  
 Ekli olaylarda, ekli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olay kullanımını desteklemek için, yedekleme kodu tarafından kullanılması gereken bir sözdizimi ve kodlama düzeni vardır.  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Sözdiziminde, ekli olay yalnızca kendi olay adı tarafından değil, sahip türü ve bir noktayla (.) ayrılmış olan olay adı ile belirtilir. Olay adı, sahip olduğu türün adıyla nitelenbildiğinden, ekli olay sözdizimi, hiçbir ekli olayın, örneklenebilir herhangi bir öğeye eklenmesini sağlar.  
  
 Örneğin, özel `NeedsCleaning` ekli bir olay için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir işleyici eklemek için sözdizimi aşağıdaki gibidir:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 `aqua:` Ön eke göz önünde, ekli olay özel eşlenmiş bir xmlns 'den gelen özel bir olay olduğundan, bu örnekte önek gereklidir.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>WPF ekli olayları nasıl uygular  
 ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, ekli olaylar bir <xref:System.Windows.RoutedEvent> alan tarafından desteklenir ve oluşturulduktan sonra ağaç üzerinden yönlendirilir. Genellikle, ekli olayın kaynağı (olayı oluşturan nesnesi) bir sistem veya hizmet kaynağıdır ve olayı oluşturan kodu çalıştıran nesne bu nedenle öğe ağacının doğrudan bir parçası değildir.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Ekli olaylara yönelik senaryolar  
 ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, ekli olaylar, statik <xref:System.Windows.Input.Mouse> sınıf veya <xref:System.Windows.Controls.Validation> sınıf tarafından etkinleştirilen olaylar gibi, hizmet düzeyi soyutlama olan belirli özellik alanlarında mevcuttur. Ya da hizmetini kullanan sınıflar, ekli olay söz diziminde olayını kullanabilir ya da ekli olayı sınıfın hizmetin yeteneklerini nasıl tümleştirdiğini gösteren yönlendirilmiş bir olay olarak yüzey seçebilirler.  
  
 , [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Eklenen olayların bir sayısını tanımlar, ancak doğrudan ekli olayı kullanacağınız veya işleyebileceğiniz senaryolar çok sınırlı olur. Genellikle, ekli olay bir mimari amaca hizmet eder, ancak daha sonra eklenmemiş (CLR olayı "sarmalayıcı") yönlendirilmiş bir olayla iletilir.  
  
 Örneğin, temel alınan eklenen <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> olay, veya kodu içindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ekli olay sözdizimi ile uğraşmaktansa <xref:System.Windows.UIElement.MouseDown> , üzerinde <xref:System.Windows.UIElement> kullanılarak <xref:System.Windows.UIElement> herhangi bir şekilde daha kolay işlenebilir. Eklenen olay, giriş cihazlarının gelecekteki genişlemesine izin verdiğinden, mimaride bir amaca hizmet eder. Kuramsal cihazın yalnızca fare girişinin benzetimini yapmak için <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> yapması gerekir ve ' dan <xref:System.Windows.Input.Mouse> ' a türetmeleri gerekmez. Ancak, bu senaryo olayların kod işlemesini içerir ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ekli olayın işlenmesi Bu senaryoyla ilgili değildir.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>WPF 'de ekli olay işleme  
 Ekli olayı işleme işlemi ve yazacağınız işleyici kodu, bir yönlendirilmiş olayla aynı şekilde temelde aynıdır.  
  
 Genel olarak, ekli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir olay, yönlendirilmiş bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olaydan çok farklı değildir. Farklar, olayın kaynağını belirleme ve bir sınıf tarafından bir üye olarak nasıl sunulduğunu (Ayrıca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işleyici söz dizimini da etkiler) belirler.  
  
 Ancak, daha önce belirtildiği gibi, mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olaylar özellikle içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]işleme için tasarlanmamıştır. Daha sık, olayın amacı, bir örneği birleştirme sırasında bir üst öğeye raporlamak için bir Oluşturucu bir öğe sağlamaktır, bu durumda olay genellikle kodda tetiklenir ve ayrıca ilgili üst sınıfta sınıf işlemeye dayanır. <xref:System.Windows.Controls.Primitives.Selector> Örneğin, bir içindeki öğelerin, <xref:System.Windows.Controls.Primitives.Selector> daha sonra sınıf tarafından işlenen ve <xref:System.Windows.Controls.Primitives.Selector.Selected> daha sonra <xref:System.Windows.Controls.Primitives.Selector> sınıf tarafından farklı bir yönlendirilmiş olaya <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> dönüştürüldüğü, eklenen olayı oluşturması beklenir. . Yönlendirilmiş olaylar ve sınıf işlemesi hakkında daha fazla bilgi için bkz. [yönlendirilmiş olayları işlenmiş olarak işaretleme ve sınıf işleme](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Kendi ekli olaylarınızı yönlendirilmiş olaylar olarak tanımlama  
 Ortak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel sınıflardan türetmeniz durumunda, sınıfınıza belirli model yöntemlerini ekleyerek ve temel sınıflarda zaten mevcut olan yardımcı program yöntemlerini kullanarak kendi ekli olaylarınızı uygulayabilirsiniz.  
  
 Bu model aşağıdaki gibidir:  
  
- Bir yöntem, iki parametreli bir ***EventName*işleyicisi ekler** . İlk parametre olay işleyicisinin eklendiği örneğidir. İkinci parametre, eklenecek olay işleyicisidir. Yöntemi, dönüş değeri `public` olmadan `static`ve olmalıdır.  
  
- Bir yöntem **,*EventName*Işleyicisini** iki parametreyle kaldırır. İlk parametre olay işleyicisinin kaldırıldığı örneğidir. İkinci parametre, kaldırılacak olay işleyicisidir. Yöntemi, dönüş değeri `public` olmadan `static`ve olmalıdır.  
  
 ***EventName*işleyicisi ekleme** erişimcisi yöntemi, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ekli olay işleyicisi öznitelikleri bir öğede bildirildiğinde işlemeyi kolaylaştırır. ***EventName*Handler** ve **Remove*EventName*Handler** yöntemleri, ekli olay için olay işleyicisi deposuna kod erişimini de etkinleştirir.  
  
 Bu genel düzen, bir çerçevede pratik uygulama için yeterince kesin değildir, çünkü belirli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir okuyucu uygulamasının destekleyici dilde ve mimaride temel olayları belirlemek için farklı şemaları olabilir. Bu, ekli olayları yönlendirilmiş olaylar olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulayan nedenlerinden biridir; bir olay (<xref:System.Windows.RoutedEvent>) için kullanılacak tanımlayıcı zaten [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi tarafından tanımlandı. Ayrıca, bir olayı yönlendirme, eklenen bir olayın [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dil düzeyi kavramında doğal bir uygulama uzantısıdır.  
  
 Ekli bir[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay için ***EventName*işleyici ekleme** , bağımsız değişken olarak yönlendirilmiş olay ve işleyici ileçağırmabilgisindenoluşur.<xref:System.Windows.UIElement.AddHandler%2A>  
  
 Bu uygulama stratejisi ve yönlendirilmiş olay sistemi, yalnızca bu sınıfların <xref:System.Windows.UIElement> <xref:System.Windows.UIElement.AddHandler%2A> uygulamaları olduğundan, eklenen olaylar için türetilmiş sınıflara veya <xref:System.Windows.ContentElement> türetilmiş sınıflara yönelik işlemeyi kısıtlar.  
  
 Örneğin, aşağıdaki kod, ekli olayı bir `NeedsCleaning` yönlendirilmiş olay olarak bildiren ekli olay `Aquarium`stratejisini kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sahip sınıfında ekli olayı tanımlar.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Ekli olay tanımlayıcı alanını <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>oluşturmak için kullanılan yöntemin gerçekten, eklenmemiş bir yönlendirilmiş olayı kaydetmek için kullanılan yöntem olduğunu unutmayın. Ekli olaylar ve yönlendirilmiş olaylar, merkezi bir dahili depoya kaydedilir. Bu olay depolama uygulama, [yönlendirilmiş olaylara genel bakış](routed-events-overview.md)bölümünde ele alınan "arabirim olarak olaylar" kavramsal değerlendirmesi sunar.  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>WPF ekli olayını yükseltme  
 Genellikle, kodınızdan mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tanımlanmış ekli olayları yükseltmeniz gerekmez. Bu olaylar genel "hizmet" kavramsal modelini izler ve gibi hizmet sınıfları <xref:System.Windows.Input.InputManager> olayları oluşturmaktan sorumludur.  
  
 Bununla birlikte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , ekli <xref:System.Windows.RoutedEvent>olayları temel alan modele göre özel bir ekli olay tanımlıyorsanız, herhangi <xref:System.Windows.UIElement> bir veya <xref:System.Windows.ContentElement>arasında ekli olay yükseltmek için <xref:System.Windows.UIElement.RaiseEvent%2A> kullanabilirsiniz. Yönlendirilmiş bir olayı (ekli veya değil) yükseltmek için, öğe ağacında olay kaynağı olarak belirli bir öğeyi bildirmeniz gerekir; Bu kaynak <xref:System.Windows.UIElement.RaiseEvent%2A> çağıran olarak bildirilir. Ağaçta kaynak olarak hangi öğenin bildirileceğini belirleme hizmetinizin sorumluluğu  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
- [WPF için XAML ve Özel Sınıflar](xaml-and-custom-classes-for-wpf.md)
