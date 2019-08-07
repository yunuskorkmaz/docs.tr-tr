---
title: Girişe Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [WPF]
- input [WPF], overview
- keyboard focus [WPF]
- keyboard input [WPF]
- touch events [WPF]
- event routing [WPF]
- touch input [WPF]
- manipulation [WPF]
- logical focus [WPF]
- stylus input [WPF]
- text input [WPF]
- input events [WPF], handling
- WPF [WPF], input overview
- manipulation events [WPF]
- mouse input [WPF]
- mouse capture [WPF]
- focus [WPF]
- mouse position [WPF]
ms.assetid: ee5258b7-6567-415a-9b1c-c0cbe46e79ef
ms.openlocfilehash: 8fa9f2dd668efca6a3108973ff792cc17b37b410
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68818046"
---
# <a name="input-overview"></a>Girişe Genel Bakış
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Alt sistem, fare, klavye, dokunmatik ve ekran kalemi dahil olmak üzere çeşitli cihazlardan giriş almak için güçlü bir API sağlar. Bu konuda tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunulan hizmetler açıklanmakta ve giriş sistemlerinin mimarisi açıklanmaktadır.

<a name="input_api"></a>
## <a name="input-api"></a>Giriş API 'SI
 Birincil giriş API 'si pozlaması temel öğe sınıflarında <xref:System.Windows.UIElement>bulunur:, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>, ve <xref:System.Windows.FrameworkContentElement>.  Temel öğeler hakkında daha fazla bilgi için bkz. [temel öğelere genel bakış](base-elements-overview.md).  Bu sınıflar, birkaç kez ad vermek üzere tuş basma, fare düğmeleri, fare tekerleği, fare hareketi, odak yönetimi ve fare yakalama ile ilgili giriş olayları için işlevsellik sağlar. Giriş API 'sini bir hizmet olarak tüm giriş olaylarını kabul etmek yerine temel öğelere yerleştirerek, giriş mimarisi giriş olaylarının Kullanıcı arabirimindeki belirli bir nesne tarafından kaynağını oluşturmasını ve birden fazla öğenin bir opp 'si olduğunu bir olay yönlendirme şemasını desteklemeyi sağlar bir giriş olayını işlemek için daha fazla bakış. Birçok giriş olayının kendileriyle ilişkili bir çift olay vardır.  Örneğin, anahtar aşağı olayı <xref:System.Windows.Input.Keyboard.KeyDown> ve <xref:System.Windows.Input.Keyboard.PreviewKeyDown> olayları ile ilişkilendirilir.  Bu olaylardaki fark, hedef öğeye yönlendirildikleri bir öğedir.  Önizleme olayları, öğe ağacını, kök öğeden hedef öğeye tünel.  Kabarcıklanma olayları, hedef öğeden kök öğeye kadar kabarcık.  İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay yönlendirme, bu genel bakışın ilerleyen kısımlarında ve [yönlendirilmiş olaylara genel bakış](routed-events-overview.md)bölümünde daha ayrıntılı bir şekilde ele alınmıştır.

### <a name="keyboard-and-mouse-classes"></a>Klavye ve fare sınıfları
 Temel öğe sınıflarında giriş API 'sine ek olarak <xref:System.Windows.Input.Keyboard> sınıf ve <xref:System.Windows.Input.Mouse> sınıflar, klavye ve fare girişi ile çalışmaya yönelik ek API sağlar.

 <xref:System.Windows.Input.Keyboard> Sınıftaki <xref:System.Windows.Input.ModifierKeys> giriş API 'si örnekleri, şu anda basılmış olan <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> özelliktirvebelirtilenbirtuşabasıldığınıbelirleyenyönteminibelirtir.<xref:System.Windows.Input.Keyboard.Modifiers%2A>

 Aşağıdaki örnek, bir <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> <xref:System.Windows.Input.Key> durumunun aşağı durumunda olup olmadığını anlamak için yöntemini kullanır.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 <xref:System.Windows.Input.Mouse>Sınıfüzerinde giriş API 'si örnekleri <xref:System.Windows.Input.Mouse.DirectlyOver%2A> ,ortafaredüğmesinindurumunualanvefareişaretçisininŞuandaüzerindeolduğuöğeyialanöğeolan.<xref:System.Windows.Input.Mouse.MiddleButton%2A>

 Aşağıdaki örnek, fare <xref:System.Windows.Input.Mouse.LeftButton%2A> <xref:System.Windows.Input.MouseButtonState.Pressed> üzerinde, durumunda olup olmadığını belirler.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 <xref:System.Windows.Input.Mouse> Ve<xref:System.Windows.Input.Keyboard> sınıfları, bu genel bakış boyunca daha ayrıntılı bir şekilde ele alınmıştır.

### <a name="stylus-input"></a>Stilus girişi
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Input.Stylus>için tümleşik destek içerir.  , Tarafından popüler hale getirilen bir kalem girişi <xref:System.Windows.Input.Stylus>olur. [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)]  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamalar, fare API 'sini kullanarak ekran kalemini fare olarak kabul edebilir, ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aynı zamanda klavye ve fareye benzer bir model kullanan bir ekran kalemi cihaz soyutlamasını açığa çıkarır.  Ekran kalemi ile ilgili tüm API 'Ler "ekran kalemi" sözcüğünü içerir.

 Ekran kalemi bir fare gibi davrandığı için, yalnızca fare girişini destekleyen uygulamalar otomatik olarak belirli bir ekran kalemi desteği elde edebilir. Ekran kalemi böyle bir şekilde kullanıldığında, uygulamaya uygun ekran kalemi olayını işleme ve ardından karşılık gelen fare olayını işleme fırsatı verilir. Ayrıca, mürekkep girişi gibi daha üst düzey hizmetler de ekran kalemi cihaz soyutlama yoluyla kullanılabilir.  Giriş olarak mürekkep hakkında daha fazla bilgi için bkz. [mürekkeple çalışmaya](getting-started-with-ink.md)başlama.

<a name="event_routing"></a>
## <a name="event-routing"></a>Olay yönlendirme
 <xref:System.Windows.FrameworkElement> , Diğer öğeleri içerik modelinde bir öğe ağacı oluşturan alt öğeler olarak içerebilir.  ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, üst öğe, olayları teslim ederek alt öğelerine veya diğer alt öğelere yönlendirilen girişe katılabilir. Bu özellikle, "denetim oluşturma" veya "birleştirme" olarak bilinen küçük denetimlerden denetimleri oluşturmak için kullanışlıdır. Öğe ağaçları ve öğe ağaçlarının olay rotalarıyla ilgisi hakkında daha fazla bilgi için bkz. [WPF Içindeki ağaçlar](trees-in-wpf.md).

 Olay yönlendirme, olayları birden çok öğeye iletme sürecidir, böylece yol boyunca belirli bir nesne veya öğe, farklı bir öğe tarafından kaynaklı olabilecek bir olaya önemli bir yanıt (işleme aracılığıyla) sunmayı tercih edebilir.  Yönlendirilmiş olaylar üç yönlendirme mekanizmalarından birini kullanır: Direct, kabarcıklanma ve tünelleme.  Doğrudan yönlendirme içinde, kaynak öğe yalnızca bildirilen tek öğedir ve olay başka hiçbir öğeye yönlendirilmez. Ancak doğrudan yönlendirilmiş olay hala standart CLR olayları yerine yalnızca yönlendirilmiş olaylar için mevcut olan bazı ek yetenekler sunmaktadır. Kabarcıklanma, önce olayı oluşturan öğeyi, sonra üst öğeyi vb. bildirerek öğe ağacını çalışır.  Tünel oluşturma, öğe ağacının kökünde başlar ve özgün kaynak öğesiyle biten, aşağı doğru çalışacaktır.  Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]giriş olayları genellikle bir tünel olayından ve kabarcıklanma olayından oluşan çiftler halinde gelir.  Tünel olayları, "Önizleme" önekiyle birlikte kabarcıklanma olaylarından ayırt edilir.  Örneğin, <xref:System.Windows.Input.Mouse.PreviewMouseMove> bir fare taşıma olayının tünel oluşturma sürümüdür ve <xref:System.Windows.Input.Mouse.MouseMove> bu olayın kabarcıklanma sürümüdür. Bu olay eşleştirme, öğe düzeyinde uygulanan ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sisteminin devralınmış bir özelliği olmayan bir kuraldır. Ayrıntılar için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md)Içindeki WPF giriş olayları bölümü.

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Giriş olaylarını işleme
 Bir öğe üzerinde giriş almak için, bir olay işleyicisinin bu belirli olayla ilişkilendirilmesi gerekir.  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Bu basit bir işlemdir: olayın adına, bu olay için dinlenen öğenin bir özniteliği olarak başvuracaktır.  Daha sonra, bir temsilciyi temel alarak, özniteliğinin değerini tanımladığınız olay işleyicisinin adına ayarlarsınız.  Olay işleyicisi, gibi bir kodda yazılmalıdır C# ve arka plan kod dosyasına eklenebilir.

 Klavye odağı bir öğe üzerinde olduğunda, işletim sistemi tarafından oluşan önemli eylemleri rapor ederken klavye olayları meydana gelir. Fare ve Stilus olayları, her biri iki kategoriye ayrılır: öğeye göre işaretçi konumunda değişiklikleri rapor eden olaylar ve cihaz düğmelerinin durumunda değişiklikleri rapor eden olaylar.

### <a name="keyboard-input-event-example"></a>Klavye girişi olay örneği
 Aşağıdaki örnek bir sol ok tuşuna basarak dinler.  ' <xref:System.Windows.Controls.StackPanel> A<xref:System.Windows.Controls.Button>sahip olan bir oluşturulur.  Sol ok tuşuna basarak dinlenecek bir olay işleyicisi <xref:System.Windows.Controls.Button> örneğe iliştirilir.

 Örneğin ilk bölümü, öğesini oluşturur <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Button> ve için <xref:System.Windows.UIElement.KeyDown>olay işleyicisini iliştirir.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 İkinci bölüm kodda yazılır ve olay işleyicisini tanımlar.  Sol ok tuşuna basıldığında ve <xref:System.Windows.Controls.Button> klavye odağı varsa, işleyici çalışır <xref:System.Windows.Controls.Control.Background%2A> ve rengi <xref:System.Windows.Controls.Button> değiştirilir.  Anahtara basıldığında, ancak sol ok tuşu <xref:System.Windows.Controls.Control.Background%2A> değilse, rengi <xref:System.Windows.Controls.Button> başlangıç rengine geri dönüştürülür.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Fare girişi olay örneği
 Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> fare işaretçisi öğesine girdiğinde <xref:System.Windows.Controls.Button>bir a <xref:System.Windows.Controls.Button> rengi değişir.  Fare öğesinden<xref:System.Windows.Controls.Button>ayrıldığında <xref:System.Windows.Controls.Control.Background%2A> renk geri yüklenir.

 Örneğin ilk <xref:System.Windows.Controls.StackPanel> bölümü, <xref:System.Windows.Controls.Button> ve denetimini oluşturur ve olay işleyicilerini <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olaylarını öğesine <xref:System.Windows.Controls.Button>ekler.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 Örneğin ikinci bölümü kodda yazılır ve olay işleyicilerini tanımlar.  Fare <xref:System.Windows.Controls.Button>öğesine girdiğinde <xref:System.Windows.Controls.Control.Background%2A> , rengi <xref:System.Windows.Controls.Button> olarak <xref:System.Windows.Media.Brushes.SlateGray%2A>değiştirilir.  Fare <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Button> <xref:System.Windows.Media.Brushes.AliceBlue%2A>' ı terk ettiğinde, rengiöğesinegerideğişir.<xref:System.Windows.Controls.Control.Background%2A>

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Metin Girişi
 Olay <xref:System.Windows.ContentElement.TextInput> , metin girişini cihazdan bağımsız şekilde dinlemenize olanak sağlar. Klavye, metin girişinin birincil yöntemidir, ancak konuşma, el yazısı ve diğer giriş cihazları da metin girişi oluşturabilir.

 Klavye girişi için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] önce uygun <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> olayları gönderir. Bu olaylar işlenmezse ve anahtar metinsel ise (yön okları veya işlev anahtarları gibi bir denetim anahtarı yerine), bir <xref:System.Windows.ContentElement.TextInput> olay tetiklenir.  Birden çok tuş vuruşu metin girişi için tek bir karakter oluşturabileceği ve tek <xref:System.Windows.ContentElement.KeyDown> tuş <xref:System.Windows.ContentElement.TextInput> vuruşlarının birden çok karakter oluşturabileceği için, ve olayları arasında / <xref:System.Windows.ContentElement.KeyUp> her zaman bir tane basit eşleme yoktur Strings.  Bu özellikle, ilgili harflerden itibaren binlerce olası karakteri oluşturmak için giriş yöntemi düzenleyicileri (IME 'Ler) kullanan Çince, Japonca ve Korece gibi diller için geçerlidir.

 <xref:System.Windows.Input.KeyEventArgs.Key%2A> Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayıgönderdiğinde<xref:System.Windows.ContentElement.KeyUp> , <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> tuş vuruşları bir olayınparçasıhalinegelirse(örneğin,alt+Sbasılıysa),olarakayarlanır.<xref:System.Windows.ContentElement.TextInput> / <xref:System.Windows.ContentElement.KeyDown> Bu, bir <xref:System.Windows.ContentElement.KeyDown> olay işleyicisindeki kodun <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> olup olmadığını kontrol etmesine izin verir ve bulunursa, daha sonra oluşturulan <xref:System.Windows.ContentElement.TextInput> etkinliğin işleyicisi için işlemeyi bırakır. Bu durumlarda, <xref:System.Windows.Input.TextCompositionEventArgs> bağımsız değişkenin çeşitli özellikleri orijinal tuş vuruşlarını belirlemede kullanılabilir. Benzer şekilde, bir [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] <xref:System.Windows.Input.Key> etkin ise değerine <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>sahiptir ve <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> özgün tuş vuruşunu veya tuş vuruşlarını verir.

 Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir işleyici ve <xref:System.Windows.UIElement.KeyDown> olay için bir işleyici tanımlar.

 İlk kod veya biçimlendirme segmenti Kullanıcı arabirimini oluşturur.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 İkinci kod segmenti olay işleyicilerini içerir.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Giriş olayları, olay yolunu kabarcıkdığı için <xref:System.Windows.Controls.StackPanel> , hangi öğenin klavye odağına sahip olduğuna bakılmaksızın girişi alır. Önce denetim bilgilendirilir `OnTextInputKeyDown` ve işleyici yalnızca <xref:System.Windows.Controls.TextBox> girişi gerçekleştirmediyseniz çağrılır. <xref:System.Windows.Controls.TextBox> Olay yerine <xref:System.Windows.UIElement.PreviewKeyDown> <xref:System.Windows.UIElement.KeyDown> olay kullanılıyorsa, `OnTextInputKeyDown` işleyici ilk olarak çağırılır.

 Bu örnekte, işleme mantığı iki kez yazılır — CTRL + O için bir kez ve düğmenin Click olayı için bir kez. Bu, giriş olaylarını doğrudan işlemek yerine komutları kullanılarak basitleştirilebilir.  Komutlar bu genel bakışta ve komut, komuta [genel bakış](commanding-overview.md)bölümünde ele alınmıştır.

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Dokunmatik ve düzenleme
 Windows 7 işletim sistemindeki yeni donanım ve API, uygulamaların birden çok dokunduğundan aynı anda giriş almasına olanak sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamaların, dokunma gerçekleştiğinde olayları yükselterek, fare veya klavye gibi diğer girişe yanıt vermeye benzer şekilde, dokunmatik bir şekilde algılamasına ve yanıt vermesine olanak sağlar.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dokunma gerçekleştiğinde iki tür olay sunar: dokunma olayları ve işleme olayları. Dokunma olayları, dokunmatik ekranda ve hareket üzerindeki her parmakla ilgili ham verileri sağlar. İşleme olayları, girişi belirli eylemler olarak yorumlar. Her iki olay türü de bu bölümde ele alınmıştır.

### <a name="prerequisites"></a>Önkoşullar
 Dokunarak yanıt veren bir uygulama geliştirmek için aşağıdaki bileşenlere ihtiyacınız vardır.

- Visual Studio 2010.

- Windows 7.

- Windows Touch 'ı destekleyen bir dokunmatik ekran gibi bir cihaz.

### <a name="terminology"></a>Terminoloji
 Dokunma ele alındığı zaman aşağıdaki terimler kullanılır.

- **Touch** , Windows 7 tarafından tanınan bir kullanıcı girişi türüdür. Genellikle dokunma duyarlı bir ekrana parmakları yerleştirerek dokunmatik başlatılır. Cihaz yalnızca parmak konumunu ve hareketini fare girişi olarak dönüştürdüğünde dizüstü bilgisayarlarda ortak bir dokunmatik yüzey gibi cihazların dokunma desteği olmadığını unutmayın.

- **Multitouch** , aynı anda birden fazla noktadan oluşan bir dokunmatik. Windows 7 ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoklu dokunmayı destekler. İle ilgili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]belgelerde her ne kadar bilgi ele alınmaktadır, kavramlar çok dokunma için geçerlidir.

- Dokunma bir nesneye uygulanan fiziksel eylem olarak yorumlanırken bir **düzenleme** oluşur. ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, işleme olayları girişi bir çeviri, genişletme veya döndürme düzenlemesi olarak yorumlar.

- Bir `touch device` dokunmatik ekranda tek bir parmak gibi dokunma girişi üreten bir cihazı temsil eder.

### <a name="controls-that-respond-to-touch"></a>Dokunma yanıtı veren denetimler
 Aşağıdaki denetimler, görünümün dışına kaydırılan içeriğe sahipse, denetimin tamamında bir parmakla sürüklenerek kaydırılabilirler.

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.ContextMenu>

- <xref:System.Windows.Controls.DataGrid>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListView>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.TextBox>

- <xref:System.Windows.Controls.ToolBar>

- <xref:System.Windows.Controls.TreeView>

 , <xref:System.Windows.Controls.ScrollViewer> Dokunma dikey <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> kaydırmanın yatay, dikey, her ikisi veya hiçbirini etkin yapıp belirtmeyeceğini belirtmenize olanak sağlayan iliştirilmiş özelliği tanımlar. <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> Özelliği, Kullanıcı dokunmatik ekranda parmak ömrü geldiğinde kaydırmanın ne kadar hızlı bir şekilde yavaştığını belirtir. <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> İliştirilmiş özelliği, işleme sapmasını çevirecek kaydırma kaydırmanın oranını belirtir.

### <a name="touch-events"></a>Dokunma olayları
 Temel sınıflar, <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>ve <xref:System.Windows.ContentElement>, abone olabileceğiniz olayları tanımlar, böylece uygulamanız dokunarak iletişime yanıt verir. Dokunma olayları, uygulamanız bir nesneyi düzenleme dışında bir şey olarak Touch ' i yorumlayacağından kullanışlıdır. Örneğin, bir kullanıcının bir veya daha fazla parmağınızla çizmesini sağlayan bir uygulama, dokunma olaylarına abone olur.

 Üç sınıf de, tanımlama sınıfına bakılmaksızın benzer şekilde davranan aşağıdaki olayları tanımlar.

- <xref:System.Windows.UIElement.TouchDown>

- <xref:System.Windows.UIElement.TouchMove>

- <xref:System.Windows.UIElement.TouchUp>

- <xref:System.Windows.UIElement.TouchEnter>

- <xref:System.Windows.UIElement.TouchLeave>

- <xref:System.Windows.UIElement.PreviewTouchDown>

- <xref:System.Windows.UIElement.PreviewTouchMove>

- <xref:System.Windows.UIElement.PreviewTouchUp>

- <xref:System.Windows.UIElement.GotTouchCapture>

- <xref:System.Windows.UIElement.LostTouchCapture>

 Klavye ve fare olayları gibi, dokunma olayları yönlendirilmiş olaylardır. İle `Preview` başlayan olaylar, tünel olayları ve ile `Touch` başlayan olaylar köpürme olaylardır. Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md). Bu olayları işlerken, <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> veya <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> yöntemini çağırarak girişin konumunu herhangi bir öğeye göre alabilirsiniz.

 Dokunma olayları arasındaki etkileşimi anlamak için, bir kullanıcının bir öğeye bir Finger yerleştirdiği, parmak öğesini öğe içinde taşıcağı ve sonra parmağı öğeden parmak taşıdığı senaryoya göz önünde bulundurun. Aşağıdaki çizimde, kabarcıklanma olaylarının yürütülmesi gösterilmektedir (basitlik için tünel olayları atlanır).

 ![Dokunma olaylarının sırası.](./media/ndp-touchevents.png "NDP_TouchEvents") Dokunma olayları

 Aşağıdaki listede, önceki çizimdeki olayların sırası açıklanmaktadır.

1. Kullanıcı öğeye bir Finger yerleştiriyorsa olaybirkezgerçekleşir.<xref:System.Windows.UIElement.TouchEnter>

2. <xref:System.Windows.UIElement.TouchDown> Olay bir kez gerçekleşir.

3. Kullanıcı, parmak öğesini öğe içinde taşıdıkça olaybirdençokkezmeydanagelir.<xref:System.Windows.UIElement.TouchMove>

4. <xref:System.Windows.UIElement.TouchUp> Olay, kullanıcının öğeden parmak süresini bir kez ortaya çıkarır.

5. <xref:System.Windows.UIElement.TouchLeave> Olay bir kez gerçekleşir.

 İki parmağınızla daha fazla kullanıldığında, her parmak için olaylar oluşur.

### <a name="manipulation-events"></a>Olayları işleme
 Bir uygulamanın bir kullanıcının bir nesneyi işlemesini mümkün olduğu durumlarda, <xref:System.Windows.UIElement> sınıfı işleme olaylarını tanımlar. Dokunma konumunu gösteren dokunma olaylarının aksine, işleme olayları girişin nasıl yorumlandığını bildirir. Üç tür işleyici, çeviri, genişletme ve döndürme vardır. Aşağıdaki listede, üç tür işleyici çağırma açıklanmaktadır.

- Bir nesneye parmak koyun ve bir çeviri düzenlemesi çağırmak için parmak izi üzerine taşıyın. Bu genellikle nesneyi taşımıştır.

- Bir nesneye iki parmak koyun ve bir genişletme düzenlemesi çağırmak için parmakları birbirine yaklaştırın veya bir diğerine uzaklaştırın. Bu genellikle nesneyi yeniden boyutlandırır.

- Bir nesneye iki parmak koyun ve bir döndürme düzenlemesi çağırmak için parmakları birbirlerine döndürün. Bu genellikle nesneyi döndürür.

 Aynı anda birden fazla düzenleme türü olabilir.

 Nesnelerin değişikliklere yanıt vermesini sağlamak için, nesneyi eylemsizlik 'e sahip olacak şekilde görünmesini sağlayabilirsiniz. Bu, nesnelerinizi fiziksel dünyanın benzetimini yapabilir. Örneğin, bir tabloya bir kitabı gönderdiğinizde, yeterince zor hale getirmeniz halinde kitabı, serbest bırakdıktan sonra taşımaya devam edecektir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanıcının parmaklarınızın nesneyi serbest bırakmasından sonra işleme olaylarını yükselterek bu davranışın benzetimini yapmanızı sağlar.

 Kullanıcının bir nesneyi taşıma, yeniden boyutlandırma ve döndürme imkanı sağlayan bir uygulama oluşturma hakkında bilgi için bkz [. İzlenecek yol: Ilk dokunmatik uygulamanızı](walkthrough-creating-your-first-touch-application.md)oluşturma.

 , <xref:System.Windows.UIElement> Aşağıdaki işleme olaylarını tanımlar.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Varsayılan olarak, <xref:System.Windows.UIElement> bu işleme olaylarını almaz. Üzerinde <xref:System.Windows.UIElement>işleme olaylarını almak için, olarak `true`ayarlayın <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> .

#### <a name="the-execution-path-of-manipulation-events"></a>Işleme olaylarının yürütme yolu
 Bir kullanıcının bir nesne "oluşturduğunda" bir senaryo düşünün. Kullanıcı nesneye bir parmak koyar, parmak izi üzerine kısa bir mesafe boyunca taşınır ve sonra taşırken parmak süresini çıkarır. Bunun sonucu, nesnenin kullanıcının parmak altına taşınması ve Kullanıcı Finger 'tan sonra taşınmaya devam edecektir.

 Aşağıdaki çizimde, işleme olaylarının yürütme yolu ve her olayla ilgili önemli bilgiler gösterilmektedir.

 ![İşleme olaylarının sırası.](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") Olayları işleme

 Aşağıdaki listede, önceki çizimdeki olayların sırası açıklanmaktadır.

1. <xref:System.Windows.UIElement.ManipulationStarting> Olay, Kullanıcı nesneye bir Finger yerleştirmediğinde meydana gelir. Diğer şeyler arasında bu olay <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> özelliği ayarlamanıza olanak sağlar. Sonraki olaylarda, düzenleme konumu öğesine <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>göre değişir. Dışındaki <xref:System.Windows.UIElement.ManipulationStarting>olaylarda, bu özellik salt okunurdur, bu <xref:System.Windows.UIElement.ManipulationStarting> nedenle olay bu özelliği ayarlayabilmeniz için tek zaman olur.

2. Daha <xref:System.Windows.UIElement.ManipulationStarted> sonra olay oluşur. Bu olay, işleme kaynağını rapor edin.

3. Bir <xref:System.Windows.UIElement.ManipulationDelta> kullanıcının parmakları bir dokunmatik ekranda hareket ediyorsa, olay birden çok kez meydana gelir. <xref:System.Windows.Input.ManipulationDeltaEventArgs> Sınıfının özelliği, işleme, genişletme veya çeviri olarak yorumlanıp <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> yorumlanmadığını bildirir. Bu, bir nesneyi düzenleme işinin çoğunu gerçekleştirdiğiniz yerdir.

4. Bu <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay, kullanıcının parmakları nesneyle iletişim kesildiğinde oluşur. Bu olay, eylemsizlik sırasında işlemelerin yavaşlamasını belirtmenizi sağlar. Bu, nesnenizin farklı fiziksel alanlara veya özniteliklerine kadar benzebilmesini sağlayacak. Örneğin, uygulamanızda fiziksel dünyadaki öğeleri temsil eden iki nesne olduğunu ve biri diğerinin daha ağır olduğunu varsayalım. Daha ağır nesnenin daha hızlı yavaşlamasını sağlayabilirsiniz.

5. Etkinlik <xref:System.Windows.UIElement.ManipulationDelta> , eylemsizlik gerçekleştiği zaman birden çok kez meydana gelir. Bu olayın kullanıcının parmakları dokunmatik ekranda hareket ediyorsa ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eylemsizlik 'in benzetimini yaparken oluştuğunu unutmayın. Diğer bir deyişle, <xref:System.Windows.UIElement.ManipulationDelta> <xref:System.Windows.UIElement.ManipulationInertiaStarting> olaydan önce ve sonra gerçekleşir. Özelliği, <xref:System.Windows.UIElement.ManipulationDelta> olayın eylemsizlik sırasında oluşup oluşmadığını bildirir ve bu özelliği, değerine bağlı olarak, bu özelliği denetleyebilir ve farklı eylemler gerçekleştirebilir. <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType>

6. <xref:System.Windows.UIElement.ManipulationCompleted> Olay, işleme ve herhangi bir eylemsizlik sona erdiğinde oluşur. Diğer bir deyişle, tüm <xref:System.Windows.UIElement.ManipulationDelta> olaylar oluştuktan sonra <xref:System.Windows.UIElement.ManipulationCompleted> , olay, işleme tamamlandığını işaret etmek için oluşur.

 , <xref:System.Windows.UIElement> <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> Olayını da tanımlar. Bu olay, <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> yöntemi <xref:System.Windows.UIElement.ManipulationDelta> olayda çağrıldığında oluşur. Bu <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olay, bir nesne bir sınırı ziyaret edildiğinde uygulamaların veya bileşenlerin görsel geri bildirim sağlamasına olanak sağlar. Örneğin, <xref:System.Windows.Window> sınıfı, kenarına rastlanınca pencerenin biraz hareket vermesine neden olacak şekilde <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olayı işler.

 <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> Yöntemi olay hariç <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> herhangi bir işleme olayında olay bağımsız değişkenlerinde çağırarak, işleme iptal edebilirsiniz. ' İ çağırdığınızda <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, işleme olayları artık oluşturulmaz ve dokunma için fare olayları oluşur. Aşağıdaki tabloda, işleme iptal edilme zamanı ve gerçekleşen fare olayları arasındaki ilişki açıklanmaktadır.

|Iptal eden olay içinde çağrılır|Zaten oluşan giriş için oluşan fare olayları|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> ve <xref:System.Windows.UIElement.ManipulationStarted>|Fare aşağı olayları.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Fare tuşu ve fare taşıma olayları.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> ve <xref:System.Windows.UIElement.ManipulationCompleted>|Fare tuşu, fare hareketi ve fare yukarı olayları.|

 Eğer <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> düzenleme işlemi eylemsizlik içinde olduğunda, yöntemin döndüğünü `false` ve girişin fare olaylarını yükseltmediğini unutmayın.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Dokunma ve Işleme olayları arasındaki Ilişki
 <xref:System.Windows.UIElement> , Her zaman dokunma olayları alabilir. Özelliği olarak `true`ayarlandığında, bir <xref:System.Windows.UIElement> , hem dokunma hem de işleme olaylarını alabilir. <xref:System.Windows.UIElement.IsManipulationEnabled%2A>  Olay işlenmezse (yani <xref:System.Windows.RoutedEventArgs.Handled%2A> , özelliği ise `false`), işleme mantığı öğesine dokunarak öğesini yakalar ve işleme olaylarını oluşturur. <xref:System.Windows.UIElement.TouchDown> Özelliği olayda olarak `true` ayarlandıysa, işleme mantığı işleme olayları oluşturmaz. <xref:System.Windows.UIElement.TouchDown> <xref:System.Windows.RoutedEventArgs.Handled%2A> Aşağıdaki çizimde, dokunma olayları ve işleme olayları arasındaki ilişki gösterilmektedir.

 ![Dokunma ve işleme olayları arasındaki ilişki](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") Dokunmatik ve işleme olayları

 Aşağıdaki listede, önceki çizimde gösterilen dokunma ve işleme olayları arasındaki ilişki açıklanmaktadır.

- İlk dokunma <xref:System.Windows.UIElement.TouchDown> aygıtı bir üzerinde bir <xref:System.Windows.UIElement>olay oluşturduğunda, işleme mantığı <xref:System.Windows.UIElement.GotTouchCapture> olayı oluşturan <xref:System.Windows.UIElement.CaptureTouch%2A> yöntemini çağırır.

- Gerçekleştiğinde, işleme mantığı <xref:System.Windows.UIElement.ManipulationStarting> olayı oluşturan <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> yöntemini çağırır. <xref:System.Windows.UIElement.GotTouchCapture>

- Olaylar gerçekleştiğinde, işleme mantığı <xref:System.Windows.UIElement.ManipulationInertiaStarting> olaydan önce oluşan <xref:System.Windows.UIElement.ManipulationDelta> olayları oluşturur. <xref:System.Windows.UIElement.TouchMove>

- Öğedeki <xref:System.Windows.UIElement.TouchUp> son dokunma aygıtı olayı <xref:System.Windows.UIElement.ManipulationInertiaStarting> oluşturduğunda, işleme mantığı olayı oluşturur.

<a name="focus"></a>
## <a name="focus"></a>Çı
 Odaklanmanız gereken iki ana kavram vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: klavye odağı ve mantıksal odak.

### <a name="keyboard-focus"></a>Klavye odağı
 Klavye odağı, klavye girişi alan öğe anlamına gelir.  Klavye odaklı bütün masaüstünde yalnızca bir öğe olabilir.  ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, klavye odağına <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> sahip olan öğe olarak `true`ayarlanır.  Static <xref:System.Windows.Input.Keyboard> yöntemi<xref:System.Windows.Input.Keyboard.FocusedElement%2A> Şu anda klavye odağına sahip olan öğeyi döndürür.

 Klavye odağı bir öğeye sekme ile veya gibi <xref:System.Windows.Controls.TextBox>belirli öğelerde fareyle tıklanarak elde edilebilir.  Klavye odağı Ayrıca, <xref:System.Windows.Input.Keyboard.Focus%2A> <xref:System.Windows.Input.Keyboard> sınıfındaki yöntemi kullanılarak programlı bir şekilde elde edilebilir.  <xref:System.Windows.Input.Keyboard.Focus%2A>belirtilen öğeye klavye odağı verme girişiminde bulunur.  Tarafından <xref:System.Windows.Input.Keyboard.Focus%2A> döndürülen öğe, şu anda klavye odağına sahip olan öğedir.

 Bir öğenin klavye odağını <xref:System.Windows.UIElement.Focusable%2A> alması için özelliği <xref:System.Windows.UIElement.IsVisible%2A> ve özellikleri **true**olarak ayarlanmalıdır.  Gibi <xref:System.Windows.Controls.Panel>bazı sınıflar <xref:System.Windows.UIElement.Focusable%2A> varsayılan olarak olarak ayarlanmıştır `false` ; bu nedenle, bu öğenin odağı elde edebilmesini istiyorsanız, bu özelliği olarak `true` ayarlamanız gerekebilir.

 Aşağıdaki örnek bir <xref:System.Windows.Controls.Button>üzerinde <xref:System.Windows.Input.Keyboard.Focus%2A> klavye odağı ayarlamak için kullanır.  Bir uygulamada <xref:System.Windows.FrameworkElement.Loaded> ilk odağı ayarlamak için önerilen yer olay işleyicisidir.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Klavye odağı hakkında daha fazla bilgi için bkz. [odağa genel bakış](focus-overview.md).

### <a name="logical-focus"></a>Mantıksal odak
 Mantıksal odak, <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> bir odak kapsamındaki öğesine başvurur.  Bir uygulamada mantıksal odağa sahip birden fazla öğe olabilir, ancak yalnızca belirli bir odak kapsamında mantıksal odağa sahip bir öğe olabilir.

 Odak kapsamı, <xref:System.Windows.Input.FocusManager.FocusedElement%2A> kapsamı içinde izlemeyi tutan bir kapsayıcı öğesidir.  Odak bir odak kapsamından ayrıldığında, odaklanmış öğe klavye odağını kaybedecektir ancak mantıksal odağı korur.  Odak odak kapsamına döndüğünde, odaklanmış öğe klavye odağını elde eder.  Bu, klavye odağının birden çok odak kapsamı arasında değiştirilmesini sağlar, ancak odak kapsamındaki Yöntem odaklanan öğe, odak döndürüldüğünde odaklanmış öğe olarak kalır.

 Bir öğe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] `true`, ekli özelliği olarak ayarlanarak <xref:System.Windows.Input.FocusManager> <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> veyakullanılarakiliştirilmişözelliğiayarlanarakbir<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> odak kapsamına eklenebilir.

 Aşağıdaki örnek, <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> ekli özelliği <xref:System.Windows.Controls.StackPanel> ayarlayarak bir odak kapsamı içinde oluşturur.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>İçindeki, ,,<xref:System.Windows.Controls.ToolBar>ve Varsayılanolarakodak<xref:System.Windows.Controls.ContextMenu>kapsamları olan sınıflar. <xref:System.Windows.Controls.Menu>

 Klavye odağına sahip bir öğe, ait olduğu odak kapsamı için mantıksal odağa de sahip olur; Bu nedenle, <xref:System.Windows.Input.Keyboard.Focus%2A> <xref:System.Windows.Input.Keyboard> sınıf veya temel öğe sınıflarında yöntemi olan bir öğe üzerinde odağı ayarlamak, öğe klavyesi odağı ve mantıksal odağı vermenizi dener.

 Odaklanmış öğeyi bir odak kapsamında tespit etmek için kullanın <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Odak kapsamı için odaklanmış öğeyi değiştirmek için kullanın <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.

 Mantıksal odak hakkında daha fazla bilgi için bkz. [odağa genel bakış](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Fare konumu
 Giriş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'si, boşluk koordinasyonu ile ilgili yararlı bilgiler sağlar.  Örneğin, koordinat `(0,0)` üst sol koordinatı, ancak ağacın sol üst öğesi mi? Giriş hedefi olan öğe? Olay işleyicinizi eklediğiniz öğe? Veya başka bir şey var mı? Karışıklık olmaması için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş API 'si, fare aracılığıyla elde edilen koordinatlarla çalışırken başvuru çerçevenize belirtmenizi gerektirir. <xref:System.Windows.Input.Mouse.GetPosition%2A> Yöntemi, belirtilen öğeye göre fare işaretçisinin koordinatını döndürür.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Fare yakalama
 Fare cihazları özellikle, fare yakalama olarak bilinen kalıcı bir özelliği tutar. Fare yakalama, bir sürükle ve bırak işlemi başlatıldığında geçici giriş durumunu korumak için kullanılır. böylece, fare işaretçisinin nominal ekran üzerindeki konumunu içeren diğer işlemler gerçekleşmeyebilir. Sürükleme sırasında, Kullanıcı sürükle ve bırak işlemi iptal etmeden tıklalayamaz ve fare yakalama, sürükleme kökeni tarafından bekletilirken birçok gelme olayından simgesini uygunsuz hale getirir. Giriş sistemi, fare yakalama durumunu belirleyebilen API 'Leri ve belirli bir öğeye fare yakalamayı zorlayabileceğiniz API 'leri ve fare yakalama durumunu temizleyebilir. Sürükle ve bırak işlemleri hakkında daha fazla bilgi için bkz. [sürükleyip bırakma genel bakış](drag-and-drop-overview.md).

<a name="commands"></a>
## <a name="commands"></a>Komutlar
 Komutlar, giriş işlemesini cihaz girişinden daha anlamsal bir düzeyde etkinleştirir.  Komutları `Cut`,,, veya `Copy` `Paste` gibi`Open`basit yönergelerden yapılır.  Komutlar, komut mantığınızı merkezileştirirken faydalıdır.  Aynı komuta, bir veya bir klavye kısayolu <xref:System.Windows.Controls.Menu>aracılığıyla bir <xref:System.Windows.Controls.ToolBar>veya ' den erişilebilir. Komutlar Ayrıca, komut kullanılamaz hale geldiğinde denetimleri devre dışı bırakmak için bir mekanizma sağlar.

 <xref:System.Windows.Input.RoutedCommand>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ,<xref:System.Windows.Input.ICommand>uygulamasıdır.  Bir <xref:System.Windows.Input.RoutedCommand> yürütüldüğünde <xref:System.Windows.Input.CommandManager.PreviewExecuted> bir ve<xref:System.Windows.Input.CommandManager.Executed> olayı, komut hedefinde tetiklenir ve bu, diğer giriş gibi öğe ağacı aracılığıyla tünel ve balon alır.  Bir komut hedefi ayarlanmamışsa, klavye odaklı öğe komut hedefi olacaktır.  Komutunu gerçekleştiren mantığı öğesine <xref:System.Windows.Input.CommandBinding>iliştirilir.  Bir olay o belirli bir <xref:System.Windows.Input.CommandBinding> komut<xref:System.Windows.Input.CommandBinding> için bir öğesine ulaştığında, ' <xref:System.Windows.Input.ExecutedRoutedEventHandler> <xref:System.Windows.Input.CommandManager.Executed> nde çağrılır.  Bu işleyici komutun eylemini gerçekleştirir.

 Verme hakkında daha fazla bilgi için bkz. [komutlama genel bakış](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.ApplicationCommands> ,<xref:System.Windows.Input.MediaCommands>,, ,ve<xref:System.Windows.Documents.EditingCommands>' den oluşan ortak komutların bir kitaplığını sağlar veya kendi kendinizinkini tanımlayabilirsiniz. <xref:System.Windows.Input.NavigationCommands> <xref:System.Windows.Input.ComponentCommands>

 Aşağıdaki örnek <xref:System.Windows.Controls.MenuItem> , bir, tıklatılınca, klavye odağına <xref:System.Windows.Controls.TextBox> sahip olduğunu varsayarak, üzerinde <xref:System.Windows.Input.ApplicationCommands.Paste%2A> <xref:System.Windows.Controls.TextBox>komutunu çağıracağı için nasıl ayarlanacağını gösterir.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]komutlar hakkında daha fazla bilgi için bkz. [komutlama genel bakış](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>Giriş sistemi ve temel öğeler
 <xref:System.Windows.Input.Mouse> ,<xref:System.Windows.Input.Keyboard>, Ve<xref:System.Windows.Input.Stylus> sınıfları tarafından tanımlanan ekli olaylar gibi giriş olayları, giriş sistemi tarafından oluşturulur ve çalışma zamanında görsel ağacı isabet testi temelinde nesne modelinde belirli bir konuma eklenir.

 , <xref:System.Windows.Input.Mouse>Ve <xref:System.Windows.ContentElement> <xref:System.Windows.UIElement> <xref:System.Windows.Input.Keyboard>ekli olay olarak tanımlayan olayların her biri, temel öğe sınıfları ve yeni bir yönlendirilmiş olay olarak da yeniden kullanıma sunulur. <xref:System.Windows.Input.Stylus> Temel öğe yönlendirilmiş olayları, özgün ekli olayı işleyen ve olay verilerini yeniden çalıştıran sınıflar tarafından oluşturulur.

 Giriş olayı, temel öğe girişi olay uygulamasıyla belirli bir kaynak öğesiyle ilişkili olduğunda, mantıksal ve görsel ağaç nesnelerinin birleşimini temel alan bir olay yolunun geri kalanı aracılığıyla yönlendirilebilir ve şu şekilde işlenir uygulama kodu.  Genellikle, ve ' de <xref:System.Windows.UIElement> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kodunda daha sezgisel olay işleyicisi sözdizimi kullanabileceğiniz için, bu cihazla ilgili giriş olaylarını <xref:System.Windows.ContentElement>ve üzerinde yönlendirilmiş olayları kullanarak işlemek daha uygundur. Bunun yerine işlemi başlatan ekli olayı işlemeyi seçebilirsiniz, ancak çeşitli sorunlar yaşayabilirsiniz: Ekli olay, temel öğe sınıfı işlemesi tarafından işlenmiş olarak işaretlenebilir ve sırasıyla doğru olay sözdizimi yerine erişimci yöntemlerini kullanmanız gerekir Ekli olaylara yönelik işleyiciler eklemek için.

<a name="whats_next"></a>
## <a name="whats-next"></a>Sıradaki
 Şimdi girişi işlemek için birkaç teknikte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]sahipsiniz.  Ayrıca, çeşitli giriş olayları türleri ve tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanılan yönlendirilmiş olay mekanizmaları hakkında gelişmiş bir bilgiye sahip olmanız gerekir.

 Daha ayrıntılı olarak Framework öğelerini ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay yönlendirmeyi açıklayan ek kaynaklar mevcuttur. Daha fazla bilgi, [komut veren genel](commanding-overview.md)bakış, [odağa genel](focus-overview.md)bakış, [temel öğelere genel bakış](base-elements-overview.md), [WPF 'deki ağaçlar](trees-in-wpf.md)ve [yönlendirilmiş olaylara genel](routed-events-overview.md)bakış için aşağıdaki genel bakışlara bakın

## <a name="see-also"></a>Ayrıca bkz.

- [Odağa Genel Bakış](focus-overview.md)
- [Komut Vermeye Genel Bakış](commanding-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Temel Öğelere Genel Bakış](base-elements-overview.md)
- [Özellikler](properties-wpf.md)
