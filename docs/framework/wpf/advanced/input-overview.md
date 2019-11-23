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
ms.openlocfilehash: a90c74542c1a6604ed27d37f882385b67402dd92
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005031"
---
# <a name="input-overview"></a>Girişe Genel Bakış
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] alt sistemi, fare, klavye, dokunmatik ve ekran kalemi dahil olmak üzere çeşitli cihazlardan giriş almak için güçlü bir API sağlar. Bu konuda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tarafından sunulan hizmetler açıklanmakta ve giriş sistemlerinin mimarisi açıklanmaktadır.

<a name="input_api"></a>
## <a name="input-api"></a>Giriş API 'SI
 Ana öğe sınıflarında birincil giriş API 'SI pozlaması bulunur: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>ve <xref:System.Windows.FrameworkContentElement>.  Temel öğeler hakkında daha fazla bilgi için bkz. [temel öğelere genel bakış](base-elements-overview.md).  Bu sınıflar, birkaç kez ad vermek üzere tuş basma, fare düğmeleri, fare tekerleği, fare hareketi, odak yönetimi ve fare yakalama ile ilgili giriş olayları için işlevsellik sağlar. Giriş API 'sini bir hizmet olarak tüm giriş olaylarını kabul etmek yerine temel öğelere yerleştirerek, giriş mimarisi giriş olaylarının Kullanıcı arabirimindeki belirli bir nesne tarafından kaynağını oluşturmasını ve birden fazla öğenin bir opp 'si olduğunu bir olay yönlendirme şemasını desteklemeyi sağlar bir giriş olayını işlemek için daha fazla bakış. Birçok giriş olayının kendileriyle ilişkili bir çift olay vardır.  Örneğin, anahtar aşağı olayı <xref:System.Windows.Input.Keyboard.KeyDown> ve <xref:System.Windows.Input.Keyboard.PreviewKeyDown> olayları ile ilişkilendirilir.  Bu olaylardaki fark, hedef öğeye yönlendirildikleri bir öğedir.  Önizleme olayları, öğe ağacını, kök öğeden hedef öğeye tünel.  Kabarcıklanma olayları, hedef öğeden kök öğeye kadar kabarcık.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içindeki olay yönlendirme, bu genel bakışın ilerleyen kısımlarında ve [yönlendirilmiş olaylara genel bakış](routed-events-overview.md)bölümünde daha ayrıntılı bir şekilde ele alınmıştır.

### <a name="keyboard-and-mouse-classes"></a>Klavye ve fare sınıfları
 Temel öğe sınıflarında giriş API 'sine ek olarak, <xref:System.Windows.Input.Keyboard> sınıfı ve <xref:System.Windows.Input.Mouse> sınıfları, klavye ve fare girişi ile çalışmaya yönelik ek API sağlar.

 <xref:System.Windows.Input.Keyboard> sınıfında giriş API 'SI örnekleri, şu anda basılan <xref:System.Windows.Input.ModifierKeys> döndüren <xref:System.Windows.Input.Keyboard.Modifiers%2A> özelliğidir ve belirtilen anahtarın basılı olup olmadığını belirleyen <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> yöntemidir.

 Aşağıdaki örnek, bir <xref:System.Windows.Input.Key> aşağı durumda olup olmadığını anlamak için <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> yöntemini kullanır.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 <xref:System.Windows.Input.Mouse> sınıfında giriş API 'SI örnekleri <xref:System.Windows.Input.Mouse.MiddleButton%2A>, orta fare düğmesinin durumunu ve <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, fare işaretçisinin Şu anda üzerinde olduğu öğeyi alan alır.

 Aşağıdaki örnek, fare üzerindeki <xref:System.Windows.Input.Mouse.LeftButton%2A> <xref:System.Windows.Input.MouseButtonState.Pressed> durumunda olup olmadığını belirler.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 <xref:System.Windows.Input.Mouse> ve <xref:System.Windows.Input.Keyboard> sınıfları, bu genel bakış boyunca daha ayrıntılı bir şekilde ele alınmıştır.

### <a name="stylus-input"></a>Stilus girişi
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Input.Stylus>için tümleşik desteğe sahiptir.  <xref:System.Windows.Input.Stylus>, Tablet PC tarafından popüler hale getirilen bir kalem girişi olur.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, fare API 'sini kullanarak ekran kalemini fare olarak kabul edebilir, ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klavye ve fareye benzer bir model kullanan bir ekran kalemi cihaz soyutlamasını da kullanıma sunar.  Ekran kalemi ile ilgili tüm API 'Ler "ekran kalemi" sözcüğünü içerir.

 Ekran kalemi bir fare gibi davrandığı için, yalnızca fare girişini destekleyen uygulamalar otomatik olarak belirli bir ekran kalemi desteği elde edebilir. Ekran kalemi böyle bir şekilde kullanıldığında, uygulamaya uygun ekran kalemi olayını işleme ve ardından karşılık gelen fare olayını işleme fırsatı verilir. Ayrıca, mürekkep girişi gibi daha üst düzey hizmetler de ekran kalemi cihaz soyutlama yoluyla kullanılabilir.  Giriş olarak mürekkep hakkında daha fazla bilgi için bkz. [mürekkeple çalışmaya](getting-started-with-ink.md)başlama.

<a name="event_routing"></a>
## <a name="event-routing"></a>Olay yönlendirme
 Bir <xref:System.Windows.FrameworkElement>, bir öğe ağacı oluşturan içerik modelinde alt öğeler olarak diğer öğeleri içerebilir.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], üst öğe, olayları teslim ederek alt öğelerine veya diğer alt öğelere yönlendirilen girişe katılabilir. Bu özellikle, "denetim oluşturma" veya "birleştirme" olarak bilinen küçük denetimlerden denetimleri oluşturmak için kullanışlıdır. Öğe ağaçları ve öğe ağaçlarının olay rotalarıyla ilgisi hakkında daha fazla bilgi için bkz. [WPF Içindeki ağaçlar](trees-in-wpf.md).

 Olay yönlendirme, olayları birden çok öğeye iletme sürecidir, böylece yol boyunca belirli bir nesne veya öğe, farklı bir öğe tarafından kaynaklı olabilecek bir olaya önemli bir yanıt (işleme aracılığıyla) sunmayı tercih edebilir.  Yönlendirilmiş olaylar üç yönlendirme mekanizmalarından birini kullanır: Direct, kabarcıklanma ve tünelleme.  Doğrudan yönlendirme içinde, kaynak öğe yalnızca bildirilen tek öğedir ve olay başka hiçbir öğeye yönlendirilmez. Ancak doğrudan yönlendirilmiş olay hala standart CLR olayları yerine yalnızca yönlendirilmiş olaylar için mevcut olan bazı ek yetenekler sunmaktadır. Kabarcıklanma, önce olayı oluşturan öğeyi, sonra üst öğeyi vb. bildirerek öğe ağacını çalışır.  Tünel oluşturma, öğe ağacının kökünde başlar ve özgün kaynak öğesiyle biten, aşağı doğru çalışacaktır.  Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş olayları genellikle bir tünel olayından ve kabarcıklanma olayından oluşan çiftler halinde gelir.  Tünel olayları, "Önizleme" önekiyle birlikte kabarcıklanma olaylarından ayırt edilir.  Örneğin, <xref:System.Windows.Input.Mouse.PreviewMouseMove> bir fare taşıma olayının tünel sürümüdür ve <xref:System.Windows.Input.Mouse.MouseMove> bu olayın kabarcıklanma sürümüdür. Bu olay eşleştirme, öğe düzeyinde uygulanan ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sisteminin devralınmış bir özelliği olmayan bir kuraldır. Ayrıntılar için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md)Içindeki WPF giriş olayları bölümü.

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Giriş olaylarını işleme
 Bir öğe üzerinde giriş almak için, bir olay işleyicisinin bu belirli olayla ilişkilendirilmesi gerekir.  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bu basit bir işlemdir: olayın adına, bu olayı dinleyerek öğenin bir özniteliği olarak başvuracaktır.  Daha sonra, bir temsilciyi temel alarak, özniteliğinin değerini tanımladığınız olay işleyicisinin adına ayarlarsınız.  Olay işleyicisi, gibi bir kodda yazılmalıdır C# ve arka plan kod dosyasına eklenebilir.

 Klavye odağı bir öğe üzerinde olduğunda, işletim sistemi tarafından oluşan önemli eylemleri rapor ederken klavye olayları meydana gelir. Fare ve Stilus olayları, her biri iki kategoriye ayrılır: öğeye göre işaretçi konumunda değişiklikleri rapor eden olaylar ve cihaz düğmelerinin durumunda değişiklikleri rapor eden olaylar.

### <a name="keyboard-input-event-example"></a>Klavye girişi olay örneği
 Aşağıdaki örnek bir sol ok tuşuna basarak dinler.  <xref:System.Windows.Controls.Button>olan <xref:System.Windows.Controls.StackPanel> oluşturulur.  Sol ok tuşuna basarak dinlenecek bir olay işleyicisi <xref:System.Windows.Controls.Button> örneğine iliştirilir.

 Örneğin ilk bölümü <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.Button> oluşturur ve <xref:System.Windows.UIElement.KeyDown>için olay işleyicisini ekler.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 İkinci bölüm kodda yazılır ve olay işleyicisini tanımlar.  Sol ok tuşuna basıldığında ve <xref:System.Windows.Controls.Button> klavye odağa sahip olduğunda, işleyici çalışır ve <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A> rengi değiştirilir.  Anahtara basıldığında, ancak sol ok tuşu değilse, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A> rengi başlangıç rengine geri dönüştürülür.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Fare girişi olay örneği
 Aşağıdaki örnekte, fare işaretçisi <xref:System.Windows.Controls.Button>girdiğinde bir <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A> rengi değiştirilir.  <xref:System.Windows.Controls.Control.Background%2A> rengi, fare <xref:System.Windows.Controls.Button>ayrıldığında geri yüklenir.

 Örneğin ilk bölümü <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.Button> denetimini oluşturur ve <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olayları için olay işleyicilerini <xref:System.Windows.Controls.Button>ekler.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 Örneğin ikinci bölümü kodda yazılır ve olay işleyicilerini tanımlar.  Fare <xref:System.Windows.Controls.Button>girdiğinde <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A> rengi <xref:System.Windows.Media.Brushes.SlateGray%2A>olarak değiştirilir.  Fare <xref:System.Windows.Controls.Button>ayrıldığında <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A> rengi <xref:System.Windows.Media.Brushes.AliceBlue%2A>olarak değişir.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Metin Girişi
 <xref:System.Windows.ContentElement.TextInput> olay, metin girişini cihazdan bağımsız şekilde dinlemenize olanak sağlar. Klavye, metin girişinin birincil yöntemidir, ancak konuşma, el yazısı ve diğer giriş cihazları da metin girişi oluşturabilir.

 Klavye girişi için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] önce <xref:System.Windows.ContentElement.KeyDown>/<xref:System.Windows.ContentElement.KeyUp> olayları gönderir. Bu olaylar işlenmezse ve anahtar metinsel ise (yön okları veya işlev anahtarları gibi bir denetim anahtarı yerine), <xref:System.Windows.ContentElement.TextInput> bir olay tetiklenir.  Birden çok tuş vuruşu tek bir karakter girişi oluşturabileceği ve tek tuş vuruşlarının çok karakterli dizeler oluşturabileceği için <xref:System.Windows.ContentElement.KeyDown>/<xref:System.Windows.ContentElement.KeyUp> ve <xref:System.Windows.ContentElement.TextInput> olayları arasında her zaman basit bir bire bir eşleme yoktur.  Bu özellikle, ilgili harflerden itibaren binlerce olası karakteri oluşturmak için giriş yöntemi düzenleyicileri (IME 'Ler) kullanan Çince, Japonca ve Korece gibi diller için geçerlidir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir <xref:System.Windows.ContentElement.KeyUp>/<xref:System.Windows.ContentElement.KeyDown> olayı gönderdiğinde, tuş vuruşları <xref:System.Windows.Input.KeyEventArgs.Key%2A> olayının parçası haline gelirse (örneğin, ALT + S basılıysa) <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> olarak ayarlanır.<xref:System.Windows.ContentElement.TextInput> Bu, <xref:System.Windows.ContentElement.KeyDown> olay işleyicisindeki kodun <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> denetlemesini sağlar ve bulunursa, daha sonra oluşturulan <xref:System.Windows.ContentElement.TextInput> olayının işleyicisi için işlemeyi bırakır. Bu durumlarda, <xref:System.Windows.Input.TextCompositionEventArgs> bağımsız değişkeninin çeşitli özellikleri orijinal tuş vuruşlarını belirlemede kullanılabilir. Benzer şekilde, bir IME etkinse, <xref:System.Windows.Input.Key> <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>değerine sahiptir ve <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> özgün tuş vuruşunu veya tuş vuruşlarını verir.

 Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir işleyici ve <xref:System.Windows.UIElement.KeyDown> olayı için bir işleyici tanımlar.

 İlk kod veya biçimlendirme segmenti Kullanıcı arabirimini oluşturur.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 İkinci kod segmenti olay işleyicilerini içerir.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Giriş olayları olay yolunu kabarcık olarak <xref:System.Windows.Controls.StackPanel>, klavye odağına sahip olan öğeden bağımsız olarak girişi alır. <xref:System.Windows.Controls.TextBox> denetimi önce bilgilendirilir ve `OnTextInputKeyDown` işleyicisi yalnızca <xref:System.Windows.Controls.TextBox> girişi gerçekleştirmediği durumlarda çağırılır. <xref:System.Windows.UIElement.KeyDown> olayı yerine <xref:System.Windows.UIElement.PreviewKeyDown> olayı kullanılırsa, önce `OnTextInputKeyDown` işleyicisi çağırılır.

 Bu örnekte, işleme mantığı iki kez yazılır — CTRL + O için bir kez ve düğmenin Click olayı için bir kez. Bu, giriş olaylarını doğrudan işlemek yerine komutları kullanılarak basitleştirilebilir.  Komutlar bu genel bakışta ve komut, komuta [genel bakış](commanding-overview.md)bölümünde ele alınmıştır.

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Dokunmatik ve düzenleme
 Windows 7 işletim sistemindeki yeni donanım ve API, uygulamaların birden çok dokunduğundan aynı anda giriş almasına olanak sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dokunma gerçekleştiğinde uygulamaların, fare veya klavye gibi diğer girişe yanıt vermeye benzer şekilde algılamasına ve yanıt vermesine olanak sağlar.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dokunma gerçekleştiğinde iki tür olay sunar: dokunma olayları ve işleme olayları. Dokunma olayları, dokunmatik ekranda ve hareket üzerindeki her parmakla ilgili ham verileri sağlar. İşleme olayları, girişi belirli eylemler olarak yorumlar. Her iki olay türü de bu bölümde ele alınmıştır.

### <a name="prerequisites"></a>Önkoşullar
 Dokunarak yanıt veren bir uygulama geliştirmek için aşağıdaki bileşenlere ihtiyacınız vardır.

- Visual Studio 2010.

- Windows 7.

- Windows Touch 'ı destekleyen bir dokunmatik ekran gibi bir cihaz.

### <a name="terminology"></a>Terminoloji
 Dokunma ele alındığı zaman aşağıdaki terimler kullanılır.

- **Touch** , Windows 7 tarafından tanınan bir kullanıcı girişi türüdür. Genellikle dokunma duyarlı bir ekrana parmakları yerleştirerek dokunmatik başlatılır. Cihaz yalnızca parmak konumunu ve hareketini fare girişi olarak dönüştürdüğünde dizüstü bilgisayarlarda ortak bir dokunmatik yüzey gibi cihazların dokunma desteği olmadığını unutmayın.

- **Multitouch** , aynı anda birden fazla noktadan oluşan bir dokunmatik. Windows 7 ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoklu dokunmayı destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]belgelerde her iletişim konusu olduğunda, kavramlar çok dokunma için geçerlidir.

- Dokunma bir nesneye uygulanan fiziksel eylem olarak yorumlanırken bir **düzenleme** oluşur. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], işleme olayları girişi bir çeviri, genişletme veya döndürme düzenlemesi olarak yorumlar.

- `touch device` bir dokunmatik ekranda tek bir parmak gibi dokunma girişi üreten bir cihazı temsil eder.

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

 <xref:System.Windows.Controls.ScrollViewer>, dokunma dikey kaydırmanın yatay, dikey, her ikisi veya hiçbirini etkin yapıp belirtmeyeceğini belirtmenizi sağlayan <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> iliştirilmiş özelliği tanımlar. <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> özelliği, Kullanıcı dokunmatik ekranda parmak ömrü geldiğinde kaydırmanın ne kadar hızlı bir şekilde yavaştığını belirtir. <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> ekli özelliği, işleme sapmasını çevirecek kaydırma kaydırmanın oranını belirtir.

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

 Klavye ve fare olayları gibi, dokunma olayları yönlendirilmiş olaylardır. `Preview` ile başlayan olaylar, tünel olayları ve `Touch` ile başlayan olaylar köpürme olaylardır. Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md). Bu olayları işlerken, <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> veya <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> metodunu çağırarak, girişin konumunu herhangi bir öğeye göre alabilirsiniz.

 Dokunma olayları arasındaki etkileşimi anlamak için, bir kullanıcının bir öğeye bir Finger yerleştirdiği, parmak öğesini öğe içinde taşıcağı ve sonra parmağı öğeden parmak taşıdığı senaryoya göz önünde bulundurun. Aşağıdaki çizimde, kabarcıklanma olaylarının yürütülmesi gösterilmektedir (basitlik için tünel olayları atlanır).

 ![Dokunma olaylarının sırası.](./media/ndp-touchevents.png "NDP_TouchEvents") Dokunma olayları

 Aşağıdaki listede, önceki çizimdeki olayların sırası açıklanmaktadır.

1. <xref:System.Windows.UIElement.TouchEnter> olay, Kullanıcı öğeye bir parmak koyarken bir kez gerçekleşir.

2. <xref:System.Windows.UIElement.TouchDown> olay bir kez gerçekleşir.

3. <xref:System.Windows.UIElement.TouchMove> olay, Kullanıcı Finger 'yi öğe içinde taşıdıkça birden çok kez meydana gelir.

4. <xref:System.Windows.UIElement.TouchUp> olay, Kullanıcı öğeden parmak süresini bir kez ortaya çıkarır.

5. <xref:System.Windows.UIElement.TouchLeave> olay bir kez gerçekleşir.

 İki parmağınızla daha fazla kullanıldığında, her parmak için olaylar oluşur.

### <a name="manipulation-events"></a>Olayları işleme
 Bir uygulamanın bir kullanıcının bir nesneyi işlemesini mümkün olduğu durumlarda <xref:System.Windows.UIElement> sınıfı, işleme olaylarını tanımlar. Dokunma konumunu gösteren dokunma olaylarının aksine, işleme olayları girişin nasıl yorumlandığını bildirir. Üç tür işleyici, çeviri, genişletme ve döndürme vardır. Aşağıdaki listede, üç tür işleyici çağırma açıklanmaktadır.

- Bir nesneye parmak koyun ve bir çeviri düzenlemesi çağırmak için parmak izi üzerine taşıyın. Bu genellikle nesneyi taşımıştır.

- Bir nesneye iki parmak koyun ve bir genişletme düzenlemesi çağırmak için parmakları birbirine yaklaştırın veya bir diğerine uzaklaştırın. Bu genellikle nesneyi yeniden boyutlandırır.

- Bir nesneye iki parmak koyun ve bir döndürme düzenlemesi çağırmak için parmakları birbirlerine döndürün. Bu genellikle nesneyi döndürür.

 Aynı anda birden fazla düzenleme türü olabilir.

 Nesnelerin değişikliklere yanıt vermesini sağlamak için, nesneyi eylemsizlik 'e sahip olacak şekilde görünmesini sağlayabilirsiniz. Bu, nesnelerinizi fiziksel dünyanın benzetimini yapabilir. Örneğin, bir tabloya bir kitabı gönderdiğinizde, yeterince zor hale getirmeniz halinde kitabı, serbest bırakdıktan sonra taşımaya devam edecektir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kullanıcının parmaklarınızın nesneyi serbest bırakmasından sonra işleme olaylarını yükselterek bu davranışın benzetimini yapmanızı sağlar.

 Kullanıcının bir nesneyi taşıma, yeniden boyutlandırma ve döndürme imkanı sağlayan bir uygulama oluşturma hakkında bilgi için bkz. [Izlenecek yol: Ilk dokunmatik uygulamanızı oluşturma](walkthrough-creating-your-first-touch-application.md).

 <xref:System.Windows.UIElement> aşağıdaki işleme olaylarını tanımlar.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Varsayılan olarak, <xref:System.Windows.UIElement> bu işleme olaylarını almaz. <xref:System.Windows.UIElement>işleme olaylarını almak için <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> `true`olarak ayarlayın.

#### <a name="the-execution-path-of-manipulation-events"></a>Işleme olaylarının yürütme yolu
 Bir kullanıcının bir nesne "oluşturduğunda" bir senaryo düşünün. Kullanıcı nesneye bir parmak koyar, parmak izi üzerine kısa bir mesafe boyunca taşınır ve sonra taşırken parmak süresini çıkarır. Bunun sonucu, nesnenin kullanıcının parmak altına taşınması ve Kullanıcı Finger 'tan sonra taşınmaya devam edecektir.

 Aşağıdaki çizimde, işleme olaylarının yürütme yolu ve her olayla ilgili önemli bilgiler gösterilmektedir.

 ![İşleme olaylarının sırası.](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") Olayları işleme

 Aşağıdaki listede, önceki çizimdeki olayların sırası açıklanmaktadır.

1. <xref:System.Windows.UIElement.ManipulationStarting> olay, Kullanıcı nesneye bir Finger yerleştirmediğinde oluşur. Diğer şeyler arasında bu olay <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> özelliğini ayarlamanıza olanak sağlar. Sonraki olaylarda, düzenleme konumu <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>göre değişir. <xref:System.Windows.UIElement.ManipulationStarting>dışındaki olaylarda, bu özellik salt okunurdur, bu nedenle <xref:System.Windows.UIElement.ManipulationStarting> olay bu özelliği ayarlayabileceğiniz tek zaman olur.

2. <xref:System.Windows.UIElement.ManipulationStarted> olay bir sonraki oluşur. Bu olay, işleme kaynağını rapor edin.

3. <xref:System.Windows.UIElement.ManipulationDelta> olay, kullanıcının parmakları bir dokunmatik ekranda hareket eden birden çok kez oluşur. <xref:System.Windows.Input.ManipulationDeltaEventArgs> sınıfının <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> özelliği, işleme, genişletme veya çeviri olarak yorumlanıp yorumlanmadığını bildirir. Bu, bir nesneyi düzenleme işinin çoğunu gerçekleştirdiğiniz yerdir.

4. <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay, kullanıcının parmakları nesneyle iletişim kesildiğinde oluşur. Bu olay, eylemsizlik sırasında işlemelerin yavaşlamasını belirtmenizi sağlar. Bu, nesnenizin farklı fiziksel alanlara veya özniteliklerine kadar benzebilmesini sağlayacak. Örneğin, uygulamanızda fiziksel dünyadaki öğeleri temsil eden iki nesne olduğunu ve biri diğerinin daha ağır olduğunu varsayalım. Daha ağır nesnenin daha hızlı yavaşlamasını sağlayabilirsiniz.

5. <xref:System.Windows.UIElement.ManipulationDelta> olay, eylemsizlik oluştuğunda birden çok kez meydana gelir. Bu olay, kullanıcının parmakları dokunmatik ekranda taşındığında ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eylemsizlik benzetimi yaparken meydana gelir. Diğer bir deyişle, <xref:System.Windows.UIElement.ManipulationInertiaStarting> olayından önce ve sonra <xref:System.Windows.UIElement.ManipulationDelta> oluşur. <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> özelliği, <xref:System.Windows.UIElement.ManipulationDelta> olayının eylemsizlik sırasında oluşup oluşmadığını bildirirse, bu özelliği denetleyebilir ve değerine bağlı olarak farklı eylemler gerçekleştirebilir.

6. <xref:System.Windows.UIElement.ManipulationCompleted> olayı, düzenleme ve herhangi bir eylemsizlik sona erdiğinde oluşur. Diğer bir deyişle, tüm <xref:System.Windows.UIElement.ManipulationDelta> olayları oluştuktan sonra, <xref:System.Windows.UIElement.ManipulationCompleted> olay, işleme tamamlandığını işaret etmek için gerçekleşir.

 <xref:System.Windows.UIElement> Ayrıca <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olayını tanımlar. Bu olay, <xref:System.Windows.UIElement.ManipulationDelta> olayında <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> yöntemi çağrıldığında oluşur. <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olay, uygulama veya bileşenlerin bir nesne bir sınırı ziyaret edildiğinde görsel geri bildirim sağlamasına olanak sağlar. Örneğin, <xref:System.Windows.Window> sınıfı, Edge ile karşılaşıldığında pencerenin biraz zaman taşımaya neden olacak <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olayını işler.

 <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olayı hariç herhangi bir işleme olayında olay bağımsız değişkenlerinde <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> yöntemini çağırarak, düzenlemeyi iptal edebilirsiniz. <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>çağırdığınızda, işleme olayları artık oluşturulmaz ve dokunma için fare olayları oluşur. Aşağıdaki tabloda, işleme iptal edilme zamanı ve gerçekleşen fare olayları arasındaki ilişki açıklanmaktadır.

|Iptal eden olay içinde çağrılır|Zaten oluşan giriş için oluşan fare olayları|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> ve <xref:System.Windows.UIElement.ManipulationStarted>|Fare aşağı olayları.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Fare tuşu ve fare taşıma olayları.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> ve <xref:System.Windows.UIElement.ManipulationCompleted>|Fare tuşu, fare hareketi ve fare yukarı olayları.|

 Düzenleme işlemi eylemsizlik içinde olduğunda <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> çağırırsanız, yöntemin `false` döndürdüğünü ve girişin fare olaylarını yükseltmediğini unutmayın.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Dokunma ve Işleme olayları arasındaki Ilişki
 <xref:System.Windows.UIElement>, her zaman dokunma olayları alabilir. <xref:System.Windows.UIElement.IsManipulationEnabled%2A> özelliği `true`olarak ayarlandığında, bir <xref:System.Windows.UIElement> hem dokunma hem de işleme olaylarını alabilir.  <xref:System.Windows.UIElement.TouchDown> olayı işlenmezse (yani, <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği `false`), işleme mantığı öğeye dokunur ve işleme olaylarını oluşturur. <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği <xref:System.Windows.UIElement.TouchDown> olayında `true` olarak ayarlanırsa, işleme mantığı işleme olayları oluşturmaz. Aşağıdaki çizimde, dokunma olayları ve işleme olayları arasındaki ilişki gösterilmektedir.

 Dokunma ve işleme olayları(./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") ![dokunma ve Işleme olayları arasındaki ilişki]

 Aşağıdaki listede, önceki çizimde gösterilen dokunma ve işleme olayları arasındaki ilişki açıklanmaktadır.

- İlk dokunma aygıtı bir <xref:System.Windows.UIElement><xref:System.Windows.UIElement.TouchDown> olayı oluşturduğunda, işleme mantığı <xref:System.Windows.UIElement.GotTouchCapture> olayını üreten <xref:System.Windows.UIElement.CaptureTouch%2A> yöntemini çağırır.

- <xref:System.Windows.UIElement.GotTouchCapture> gerçekleştiğinde, işleme mantığı <xref:System.Windows.UIElement.ManipulationStarting> olayını üreten <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> yöntemini çağırır.

- <xref:System.Windows.UIElement.TouchMove> olayları gerçekleştiğinde, işleme mantığı <xref:System.Windows.UIElement.ManipulationInertiaStarting> olayından önce oluşan <xref:System.Windows.UIElement.ManipulationDelta> olaylarını oluşturur.

- Öğedeki son dokunmatik cihaz <xref:System.Windows.UIElement.TouchUp> olayını oluşturduğunda, düzenleme mantığı <xref:System.Windows.UIElement.ManipulationInertiaStarting> olayını oluşturur.

<a name="focus"></a>
## <a name="focus"></a>Çı
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]odaklanmak için ilgili iki ana kavram vardır: klavye odağı ve mantıksal odak.

### <a name="keyboard-focus"></a>Klavye odağı
 Klavye odağı, klavye girişi alan öğe anlamına gelir.  Klavye odaklı bütün masaüstünde yalnızca bir öğe olabilir.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], klavye odağına sahip öğe <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> `true`olarak ayarlanmıştır.  Statik <xref:System.Windows.Input.Keyboard> yöntemi <xref:System.Windows.Input.Keyboard.FocusedElement%2A> Şu anda klavye odağına sahip olan öğeyi döndürür.

 Klavye odağı bir öğeye sekme ile veya <xref:System.Windows.Controls.TextBox>gibi belirli öğelerde fareyle tıklanarak elde edilebilir.  Klavye odağı Ayrıca, <xref:System.Windows.Input.Keyboard> sınıfında <xref:System.Windows.Input.Keyboard.Focus%2A> yöntemi kullanılarak programlı olarak elde edilebilir.  <xref:System.Windows.Input.Keyboard.Focus%2A> belirtilen öğeye klavye odağını verme girişiminde bulunur.  <xref:System.Windows.Input.Keyboard.Focus%2A> tarafından döndürülen öğe, şu anda klavye odağına sahip olan öğedir.

 Bir öğenin klavye odağını alması için <xref:System.Windows.UIElement.Focusable%2A> özelliği ve <xref:System.Windows.UIElement.IsVisible%2A> özellikleri **true**olarak ayarlanmalıdır.  <xref:System.Windows.Controls.Panel>gibi bazı sınıfların varsayılan olarak `false` <xref:System.Windows.UIElement.Focusable%2A> ayarlanmıştır; Bu nedenle, bu öğenin odağı alabilmesini istiyorsanız bu özelliği `true` olarak ayarlamanız gerekebilir.

 Aşağıdaki örnek, klavye odağını bir <xref:System.Windows.Controls.Button>ayarlamak için <xref:System.Windows.Input.Keyboard.Focus%2A> kullanır.  Bir uygulamada ilk odağı ayarlamak için önerilen yer <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisidir.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Klavye odağı hakkında daha fazla bilgi için bkz. [odağa genel bakış](focus-overview.md).

### <a name="logical-focus"></a>Mantıksal odak
 Mantıksal odak, odak kapsamındaki <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> anlamına gelir.  Bir uygulamada mantıksal odağa sahip birden fazla öğe olabilir, ancak yalnızca belirli bir odak kapsamında mantıksal odağa sahip bir öğe olabilir.

 Odak kapsamı, kapsamı içinde <xref:System.Windows.Input.FocusManager.FocusedElement%2A> izlemeyi tutan bir kapsayıcı öğesidir.  Odak bir odak kapsamından ayrıldığında, odaklanmış öğe klavye odağını kaybedecektir ancak mantıksal odağı korur.  Odak odak kapsamına döndüğünde, odaklanmış öğe klavye odağını elde eder.  Bu, klavye odağının birden çok odak kapsamı arasında değiştirilmesini sağlar, ancak odak kapsamındaki Yöntem odaklanan öğe, odak döndürüldüğünde odaklanmış öğe olarak kalır.

 Bir öğe, <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> yöntemi kullanılarak iliştirilmiş özelliği ayarlanarak <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> <xref:System.Windows.Input.FocusManager> iliştirilmiş özelliği `true`veya kodda ayarlayarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir odak kapsamına açılabilir.

 Aşağıdaki örnek, <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> iliştirilmiş özelliğini ayarlayarak bir <xref:System.Windows.Controls.StackPanel> odağı bir kapsama yapar.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içindeki sınıflar, varsayılan olarak odak kapsamları olan <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>ve <xref:System.Windows.Controls.ContextMenu>.

 Klavye odağına sahip bir öğe, ait olduğu odak kapsamı için mantıksal odağa de sahip olur; Bu nedenle, <xref:System.Windows.Input.Keyboard> sınıfında veya temel öğe sınıflarında <xref:System.Windows.Input.Keyboard.Focus%2A> yöntemi olan bir öğeye odak ayarlandığında, öğe klavyesi odağa ve mantıksal odağa izin vermeyecektir.

 Odaklanan öğeyi odak kapsamında tespit etmek için <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>kullanın. Odak kapsamı için odaklanmış öğeyi değiştirmek için <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>kullanın.

 Mantıksal odak hakkında daha fazla bilgi için bkz. [odağa genel bakış](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Fare konumu
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Input API 'SI, alanları koordine etmek için faydalı bilgiler sağlar.  Örneğin, koordinat `(0,0)` üst sol koordinatı, ancak ağacın sol üst öğesi mi? Giriş hedefi olan öğe? Olay işleyicinizi eklediğiniz öğe? Veya başka bir şey var mı? Karışıklığın önüne geçmek için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Input API 'SI, fare aracılığıyla elde edilen koordinatlarla çalışırken başvuru çerçevenize belirtmenizi gerektirir. <xref:System.Windows.Input.Mouse.GetPosition%2A> yöntemi, belirtilen öğeye göre fare işaretçisinin koordinatını döndürür.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Fare yakalama
 Fare cihazları özellikle, fare yakalama olarak bilinen kalıcı bir özelliği tutar. Fare yakalama, bir sürükle ve bırak işlemi başlatıldığında geçici giriş durumunu korumak için kullanılır. böylece, fare işaretçisinin nominal ekran üzerindeki konumunu içeren diğer işlemler gerçekleşmeyebilir. Sürükleme sırasında, Kullanıcı sürükle ve bırak işlemi iptal etmeden tıklalayamaz ve fare yakalama, sürükleme kökeni tarafından bekletilirken birçok gelme olayından simgesini uygunsuz hale getirir. Giriş sistemi, fare yakalama durumunu belirleyebilen API 'Leri ve belirli bir öğeye fare yakalamayı zorlayabileceğiniz API 'leri ve fare yakalama durumunu temizleyebilir. Sürükle ve bırak işlemleri hakkında daha fazla bilgi için bkz. [sürükleyip bırakma genel bakış](drag-and-drop-overview.md).

<a name="commands"></a>
## <a name="commands"></a>Komutlar
 Komutlar, giriş işlemesini cihaz girişinden daha anlamsal bir düzeyde etkinleştirir.  Komutlar `Cut`, `Copy`, `Paste`veya `Open`gibi basit yönergelerden.  Komutlar, komut mantığınızı merkezileştirirken faydalıdır.  Aynı komuta bir <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>veya klavye kısayolu aracılığıyla erişilebilir. Komutlar Ayrıca, komut kullanılamaz hale geldiğinde denetimleri devre dışı bırakmak için bir mekanizma sağlar.

 <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.ICommand>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasıdır.  Bir <xref:System.Windows.Input.RoutedCommand> yürütüldüğünde, komut hedefi üzerinde bir <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> olayı oluşturulur. Bu, diğer giriş gibi öğe ağacı aracılığıyla tünel ve kabarcık olur.  Bir komut hedefi ayarlanmamışsa, klavye odaklı öğe komut hedefi olacaktır.  Komutu gerçekleştiren mantık bir <xref:System.Windows.Input.CommandBinding>eklenir.  <xref:System.Windows.Input.CommandManager.Executed> bir olay bu belirli komut için bir <xref:System.Windows.Input.CommandBinding> ulaştığında, <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.ExecutedRoutedEventHandler> çağrılır.  Bu işleyici komutun eylemini gerçekleştirir.

 Verme hakkında daha fazla bilgi için bkz. [komutlama genel bakış](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>ve <xref:System.Windows.Documents.EditingCommands>oluşan ortak komutların bir kitaplığını sağlar veya kendi kendinizinkini tanımlayabilirsiniz.

 Aşağıdaki örnek, <xref:System.Windows.Controls.TextBox> klavye odağına sahip olduğu varsayılarak, tıklandığı zaman, <xref:System.Windows.Controls.TextBox><xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutunu çağıracağı bir <xref:System.Windows.Controls.MenuItem> ayarlamayı gösterir.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]komutlar hakkında daha fazla bilgi için bkz. [komutlama genel bakış](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>Giriş sistemi ve temel öğeler
 <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>ve <xref:System.Windows.Input.Stylus> sınıfları tarafından tanımlanan ekli olaylar gibi giriş olayları, giriş sistemi tarafından oluşturulur ve çalışma zamanında görsel ağacı isabet testi temelinde nesne modelinde belirli bir konuma eklenir.

 <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>ve <xref:System.Windows.Input.Stylus> eklenmiş bir olay olarak tanımlayan olayların her biri, temel öğe <xref:System.Windows.UIElement> sınıfları tarafından da yeniden sunulur ve yeni bir yönlendirilmiş olay olarak <xref:System.Windows.ContentElement>. Temel öğe yönlendirilmiş olayları, özgün ekli olayı işleyen ve olay verilerini yeniden çalıştıran sınıflar tarafından oluşturulur.

 Giriş olayı, temel öğe girişi olay uygulamasıyla belirli bir kaynak öğesiyle ilişkili olduğunda, mantıksal ve görsel ağaç nesnelerinin birleşimini temel alan bir olay yolunun geri kalanı aracılığıyla yönlendirilebilir ve şu şekilde işlenir uygulama kodu.  Genellikle, hem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hem de kodunda daha sezgisel olay işleyicisi sözdizimini kullanabileceğiniz <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement>' de yönlendirilmiş olayları kullanarak cihazla ilgili bu giriş olaylarını işlemek daha uygundur. Bunun yerine işlemi başlatan ekli olayı işlemeyi seçebilirsiniz, ancak çeşitli sorunlar yaşayabilirsiniz: Ekli olay, temel öğe sınıfı işlemesi tarafından işlenmiş olarak işaretlenebilir ve sırasıyla doğru olay sözdizimi yerine erişimci yöntemlerini kullanmanız gerekir Ekli olaylara yönelik işleyiciler eklemek için.

<a name="whats_next"></a>
## <a name="whats-next"></a>Sıradaki
 Artık [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]girişi işlemenin birkaç tekniği vardır.  Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tarafından kullanılan çeşitli giriş olayları ve yönlendirilmiş olay mekanizmaları hakkında gelişmiş bir bilgiye sahip olmanız gerekir.

 Daha ayrıntılı bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Framework öğelerini ve olay yönlendirmeyi açıklayan ek kaynaklar mevcuttur. Daha fazla bilgi, [komut veren genel](commanding-overview.md)bakış, [odağa genel](focus-overview.md)bakış, [temel öğelere genel bakış](base-elements-overview.md), [WPF 'deki ağaçlar](trees-in-wpf.md)ve [yönlendirilmiş olaylara genel](routed-events-overview.md)bakış için aşağıdaki genel bakışlara bakın

## <a name="see-also"></a>Ayrıca bkz.

- [Odağa Genel Bakış](focus-overview.md)
- [Komut Vermeye Genel Bakış](commanding-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Temel Öğelere Genel Bakış](base-elements-overview.md)
- [Özellikler](properties-wpf.md)
