---
title: "Ekli Olaylara Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcfe0d97b86a27859d79685e035d8f3f765a965b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="attached-events-overview"></a>Ekli Olaylara Genel Bakış
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir dil bileşeni ve adlı olay türünü tanımlayan bir *ekli olayı*. Ekli olay kavramı, belirli bir olay için bir işleyici rasgele öğenin yerine gerçekten tanımlayan veya olaydan devralınan bir öğe eklemenize olanak tanır. Bu durumda, ne olası olayı tetiklenmeden nesne ne de hedef işleme örneği tanımlar veya aksi halde olay "sahibi".  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, okuduğunuz varsayılır [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md) ve [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Ekli olay sözdizimi  
 Ekli olaylar sahip bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sözdizimi ve yedekleme kodu tarafından ekli olay kullanımını desteklemek için kullanılması gereken bir kodlama düzeni.  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sözdizimi, ekli olay Olay adı tarafından değil, ancak bir nokta (.) ile ayrılmış kendi türü artı tarafından belirtilir. Olay adı kendi türü adı ile tam olduğundan, ekli olay sözdizimi oluşturulabilir herhangi bir öğeye eklenmiş tüm ekli olay sağlar.  
  
 Örneğin, aşağıdaki gibidir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özel bir işleyici ekleme söz dizimi `NeedsCleaning` ekli olayı:  
  
 [!code-xaml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Not `aqua:` önek; önek bu durumda özel bir eşlenen xmlns gelen özel bir olay ekli olay olduğu için gereklidir.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Nasıl WPF Implements ekli olaylar  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ekli olaylar tarafından desteklenen bir <xref:System.Windows.RoutedEvent> alan ve oluşturulduktan sonra ağaç yönlendirilir. Genellikle, ekli olay (olayını nesnesi) sistemi veya hizmet kaynağı kaynağıdır ve olayı oluşturan kodu çalıştıran nesne bu nedenle öğesi ağacının doğrudan bir parçası değil.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Ekli olay senaryoları  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ekli olaylar belirli özellik alanlarında mevcut olduğu gibi yerlerde hizmet düzeyi soyutlama statik tarafından etkinleştirilen olaylar <xref:System.Windows.Input.Mouse> sınıfı veya <xref:System.Windows.Controls.Validation> sınıfı. Etkileşim ya da hizmeti kullanmak sınıflar ya da ekli olay sözdiziminde olayı kullanabilirsiniz veya ekli olay sınıfı hizmet özelliklerini nasıl tümleşik çalıştığını bir parçası olan yönlendirilmiş olay olarak ortaya çıkarma seçebilirsiniz.  
  
 Ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olaylar, burada şunları yapacaksınız kullanın ya da ekli olay işleyici doğrudan çok sınırlı senaryoları sayısını tanımlar. Genellikle, ekli olay mimari amaca hizmet eder, ancak daha sonra bir ekli olmayan iletilir (ile yedeklenen bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay "sarmalayıcı") yönlendirilmiş olay.  
  
 Örneğin, arka plandaki olay bağlı <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> daha kolayca herhangi verilen işlenebilir <xref:System.Windows.UIElement> kullanarak <xref:System.Windows.UIElement.MouseDown> üzerindeki <xref:System.Windows.UIElement> ekli olay sözdizimiyle baş yerine içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kod. Giriş aygıtları gelecekteki genişleme için izin verdiğinden ekli olay mimarisinde bir amaca hizmet eder. Kuramsal aygıt yükseltmek yalnızca gerekir <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> fare girdisi benzetimini yapmak için sipariş ve türetilen ihtiyaç duymaz <xref:System.Windows.Input.Mouse> Bunu yapmak için. Ancak, bu senaryo olayların kod işlemesini içerir ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ekli olay işleme bu senaryoyla ilgili değildir.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>WPF içinde ekli olay işleme  
 Ekli olay ve yazacağınız işleyici kodu işleme işlemi temelde yönlendirilmiş olay ile aynıdır.  
  
 Genel olarak, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olay çok farklı değildir bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş olay. Olay nasıl kaynaklıdır ve nasıl bir üye olarak bir sınıf tarafından sunulur fark var (da etkileyen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işleyici sözdizimi).  
  
 Ancak, daha önce belirtildiği gibi varolan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olaylar değil özellikle yöneliktir işlemede için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Daha sık olayın amacı durum olay genellikle kodda tetiklenir ve aynı zamanda ilgili üst sınıfında sınıf kullanır birleştirme, bir üst öğeye bir durum raporu için bileşik öğeyi etkinleştirmektir. Örneği için içindeki öğelerin bir <xref:System.Windows.Controls.Primitives.Selector> ekli oluşturması beklenir <xref:System.Windows.Controls.Primitives.Selector.Selected> sınıfı olay işlenmiş tarafından <xref:System.Windows.Controls.Primitives.Selector> sınıfı ve tarafından potansiyel olarak dönüştürülen <xref:System.Windows.Controls.Primitives.Selector> farklı bir yönlendirilmiş olay sınıfına <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Yönlendirilmiş olaylar ve sınıf işleme hakkında daha fazla bilgi için bkz: [işlenmiş ve sınıf işleme olarak yönlendirilmiş olayların](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Yönlendirilmiş olaylar kendi ekli olaylar olarak tanımlama  
 Ortak türetme, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel sınıflar sınıfınızda belirli model yöntemlerini dahil olmak üzere kendi ekli olaylar uygulayabilirsiniz ve yardımcı programını kullanarak temel sınıfları üzerinde zaten yöntemleri sunmak.  
  
 Desen aşağıdaki gibidir:  
  
-   Bir yöntem `Add*Handler` iki parametrelere sahip. İlk parametre olay tanımlamanız gerekir ve tanımlanan olayın adlarıyla eşleşmelidir * yöntemi adı. İkinci parametre eklemek için işleyicisidir. Yöntemi, ortak ve statik bir dönüş değerine sahip olması gerekir.  
  
-   Bir yöntem `Remove*Handler` iki parametrelere sahip. İlk parametre olay tanımlamanız gerekir ve tanımlanan olayın adlarıyla eşleşmelidir * yöntemi adı. İkinci parametre kaldırılacak işleyicidir. Yöntemi, ortak ve statik bir dönüş değerine sahip olması gerekir.  
  
 `Add*Handler` Erişimci yöntemi kolaylaştıran [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemesini bağlı öznitelikleri öğe üzerinde bildirildiğinde olay işleyicisi. `Add*Handler` Ve `Remove*Handler` yöntemleri ekli olay için olay işleyici deposuna kod erişimi de sağlar.  
  
 Bu genel model henüz bir çerçeve içinde pratik uygulama için yeterince kesin değildir çünkü herhangi verilen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu uygulaması destekleyici dil ve mimari temelindeki olayları tanımlamak için farklı şemalara sahip. Bu nedenlerinden biri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağlı Implements olayları yönlendirilmiş olaylar olarak; bir olay için kullanılacak tanımlayıcısı (<xref:System.Windows.RoutedEvent>) tarafından tanımlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistem. Ayrıca, bir olayı yönlendirme bir doğal uygulama uzantısıdır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ekli olay kavramı dil düzeyi.  
  
 `Add*Handler` Uygulama için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olay çağırmadan oluşur <xref:System.Windows.UIElement.AddHandler%2A> yönlendirilmiş olay ve bağımsız değişkenler olarak işleyici ile.  
  
 Bu uygulama stratejisi ve yönlendirilmiş olay sistemi Genel ekli olay işleme ya da kısıtlama <xref:System.Windows.UIElement> türetilmiş sınıfları veya <xref:System.Windows.ContentElement> sadece bu sınıfların olduğundan türetilmiş sınıfları, <xref:System.Windows.UIElement.AddHandler%2A> uygulamaları.  
  
 Örneğin, aşağıdaki kod tanımlar `NeedsCleaning` sahip sınıf olayda bağlı `Aquarium`kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekli olay stratejisini yönlendirilmiş olay olarak ekli olay bildirme.  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Ekli olay tanımlayıcı alanı oluşturmak için kullanılan yöntem Not <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, ekli olmayan yönlendirilmiş olay kaydetmek için kullanılan gerçekte yöntem ile aynıdır. Tüm ekli olaylar ve yönlendirilmiş olaylar merkezi içi depoya kaydedilir. Bu olay deposu uygulaması içinde ele alınmıştır "arayüz olarak olaylar" kavramsal dikkate etkinleştirir [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Bir WPF ekli olayı oluşturma  
 Genellikle varolan Yükselt gerekmez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodunuzdan ekli olaylar tanımlı. Bu olaylar genel "hizmet" kavramsal modelini izler ve hizmet sınıfları gibi <xref:System.Windows.Input.InputManager> olayları oluşturmadan sorumludur.  
  
 Ancak, dayalı özel bir ekli olay tanımlıyorsanız, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] üzerinde alma modeli ekli olayların <xref:System.Windows.RoutedEvent>, kullanabileceğiniz <xref:System.Windows.UIElement.RaiseEvent%2A> herhangi bir ekli olay oluşturmak için <xref:System.Windows.UIElement> veya <xref:System.Windows.ContentElement>. (Bağlı veya değil) yönlendirilmiş bir olayı tetiklenmeden belirli bir öğe öğe ağacında olay kaynağı olarak bildirilmesini gerektirir; kaynak olarak bildirilen <xref:System.Windows.UIElement.RaiseEvent%2A> çağıran. Hangi öğesi belirleme ağacında kaynak hizmetinizin sorumluluk olarak bildirilir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Ayrıntılı XAML Sözdizimi](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [WPF için XAML ve Özel Sınıflar](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
