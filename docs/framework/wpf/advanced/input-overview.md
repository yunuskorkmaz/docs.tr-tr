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
ms.openlocfilehash: defce7949bff47ef109e81d03894b13d95ba4c3d
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238503"
---
# <a name="input-overview"></a>Girişe Genel Bakış
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Alt sistemi, fare, klavye, dokunmatik ve Kalem dahil olmak üzere çeşitli arasından giriş almak için güçlü bir API sağlar. Bu konu tarafından sağlanan hizmetleri açıklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve giriş sistemleri mimarisini açıklar.

<a name="input_api"></a>
## <a name="input-api"></a>Giriş API'si
 API Etkilenme temel öğe sınıflarında bulunan birincil giriş: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>, ve <xref:System.Windows.FrameworkContentElement>.  Temel öğeler hakkında daha fazla bilgi için bkz. [temel öğelere genel bakış](base-elements-overview.md).  Bu sınıflar, tuş basışlarını, fare düğmesini, fare tekerleğini, fare hareketini, odak yönetim ve fare yakalama için ilgili giriş olayları için işlevsellik sağlar. Temel öğeler üzerinde ' % s'giriş API yerleştirme yerine hizmet olarak tüm giriş olayları değerlendirmek, giriş mimarisi, kullanıcı arabiriminde belirli bir nesnenin tarafından sağlanmasına ve verebileceğiniz bir opp birden fazla öğeye sahip bir olay yönlendirme düzenini desteklemek için giriş olayları sağlar. bir giriş olayı işlemek için ortunity. Birçok giriş olayları, bir çift bunlarla ilişkilendirilmiş olayları vardır.  Örneğin, olay tuşunu ilişkili olduğu <xref:System.Windows.Input.Keyboard.KeyDown> ve <xref:System.Windows.Input.Keyboard.PreviewKeyDown> olayları.  Bu olaylar, nasıl bunlar hedef öğeye yönlendirilir farktır.  Önizleme olayları tünel öğesi ağaç kök öğeden hedef öğeye.  Tırmanma olayları Kabarcık ayarlama hedef öğesinden için kök öğe.  Olay yönlendirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ilerleyen bölümlerinde bu genel bakış ve daha ayrıntılı anlatılan [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).

### <a name="keyboard-and-mouse-classes"></a>Klavye ve fare sınıfları
 Temel öğe sınıfları, giriş API yanı sıra <xref:System.Windows.Input.Keyboard> sınıfı ve <xref:System.Windows.Input.Mouse> sınıfları, klavye ve fare girişi ile çalışmak için ek bir API sağlar.

 API giriş örnekleri <xref:System.Windows.Input.Keyboard> sınıfı <xref:System.Windows.Input.Keyboard.Modifiers%2A> döndüren özellik <xref:System.Windows.Input.ModifierKeys> şu anda basılı ve <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> yöntemi belirtilen bir tuşa basıldığında olup olmadığını belirler.

 Aşağıdaki örnekte <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> belirlemek için yöntemi bir <xref:System.Windows.Input.Key> aşağı durumdadır.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 API giriş örnekleri <xref:System.Windows.Input.Mouse> sınıfı <xref:System.Windows.Input.Mouse.MiddleButton%2A>, orta fare düğmesi durumunu alır ve <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, fare işaretçisi öğenin alır şu anda biter.

 Aşağıdaki örnek belirler olmadığını <xref:System.Windows.Input.Mouse.LeftButton%2A> üzerinde fareyi bulunduğu <xref:System.Windows.Input.MouseButtonState.Pressed> durumu.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 <xref:System.Windows.Input.Mouse> Ve <xref:System.Windows.Input.Keyboard> sınıfları bu genel bakış içindeki daha ayrıntılı ele alınmıştır.

### <a name="stylus-input"></a>İğne girişi
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Destek için tümleşik olan <xref:System.Windows.Input.Stylus>.  <xref:System.Windows.Input.Stylus> Popüler tarafından yapılan bir kalem girişi [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar kabul ekran kalemi fare API, fareyi kullanarak ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de kullanan bir model klavye ve fare benzer bir ekran kalemi cihaz soyutlamayı kullanıma sunar.  Ekran kalemi ile ilgili tüm API'leri "Kalem" sözcük içerir.

 Ekran kalemi fare davranıp çünkü yalnızca fare girişi destekleyen uygulamalar yine de bazı ekran kalemi destek düzeyini otomatik olarak edinebilirsiniz. Ekran kalemi bu tür bir şekilde kullanıldığında, uygulama uygun ekran kalemi olayı işlemek için fırsatı verilir ve daha sonra karşılık gelen bir fare olayını işler. Mürekkep giriş gibi daha üst düzey hizmetler buna Ayrıca ekran kalemi cihaz soyutlamayı olarak kullanılabilir.  Giriş olarak mürekkep hakkında daha fazla bilgi için bkz. [mürekkep ile çalışmaya başlama](getting-started-with-ink.md).

<a name="event_routing"></a>
## <a name="event-routing"></a>Olay yönlendirme
 A <xref:System.Windows.FrameworkElement> öğe ağacındaki oluşturan kendi içerik modelinde, alt öğeleri olarak diğer öğelerini içerebilir.  İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], üst öğenin alt öğelerini veya diğer alt öğeleri için olayları gönderdikten tarafından yönlendirilen giriş katılabilir. Bu denetimler daha küçük denetimleri dışında "Denetim bileşiminin" veya "birleştirme" olarak da bilinen bir işlem oluşturmak için kullanışlıdır Öğe ağacı ve öğe ağaçları olay yolları nasıl ilişki kuracağını hakkında daha fazla bilgi için bkz. [WPF içinde ağaçlar](trees-in-wpf.md).

 Olay yönlendirme birden çok öğe olayları iletme işlemi, böylelikle tarafından farklı bir öğe konağı kaynağı bir olaya (aracılığıyla işlemeyi) önemli bir yanıt sunmak belirli bir nesne veya yol boyunca öğesi seçebilirsiniz.  Yönlendirilmiş olaylar üç yönlendirme mekanizmaları birini kullanın: doğrudan, tırmanma ve tünel oluşturma.  Doğrudan yönlendirme, kaynak öğesi bildirim tek öğe ise ve olay için diğer öğeleri yönlendirilmez. Ancak, doğrudan yönlendirilmiş olay yalnızca standart'ın aksine yönlendirilmiş olaylar için mevcut olan bazı ek özellikler hala sunar [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olayları. Tırmanma, ilk olay ardından kaynaklanan öğesi üst öğe ve benzeri bildirerek öğesi ağacı çalışır.  Tünel öğe ağacı kök dizininde başlar ve özgün kaynak öğesi ile biten aşağı çalışır.  Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Giriş olayları, genellikle bir tünel olayı ve tırmanma olay oluşan çiftlerini gelir.  Tünel olayları "Önizleme" önekiyle tırmanma olaylardan ayırt edilir.  Örneğin, <xref:System.Windows.Input.Mouse.PreviewMouseMove> tünel fare hareketi olayını sürümüdür ve <xref:System.Windows.Input.Mouse.MouseMove> tırmanma bu olay sürümüdür. Bu olay öğe düzeyinde uygulanır ve belirli bir yeteneği değil bir kuralı eşleşmesidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi. Ayrıntılar için bkz WPF giriş olayları bölümünde [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Giriş olaylarını işleme
 Bir öğe üzerinde girişi almak için bir olay işleyicisi belirli bir olay ile ilişkilendirilmiş olması gerekir.  İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bu oldukça basittir: olay adı için bu olayı dinleyen öğesinin özniteliği olarak başvuru.  Sonra adına dayalı bir Temsilcide tanımlayan olay işleyicisinin özniteliğinin değerini ayarlayın.  Olay işleyicisi, C# gibi kodda yazılmış olmalıdır ve bir arka plan kod dosyasında dahil edilebilir.

 İşletim sistemi klavye odağı bir öğede olsa da, temel eylemi raporları klavye olaylarını ortaya çıkar. Fare ve ekran kalemi olayları her iki kategoriye ayrılır: rapor öğesi göre işaretçisi konumunun değişiklikleri olayları ve cihaz düğmelerinin durumunda rapor değişiklikleri olayları.

### <a name="keyboard-input-event-example"></a>Klavye giriş olayı örneği
 Aşağıdaki örnek, bir sol ok tuşu için dinler.  A <xref:System.Windows.Controls.StackPanel> oluşturulur sahip bir <xref:System.Windows.Controls.Button>.  Sol Ok tuşu iliştirildiği için dinlenecek olay işleyicisi <xref:System.Windows.Controls.Button> örneği.

 Örneğin ilk bölümünü oluşturur <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.Button> ve olay işleyicisi ekler <xref:System.Windows.UIElement.KeyDown>.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 İkinci bölüm kodda yazılır ve olay işleyicisini tanımlar.  Sol Ok tuşu basılı olduğunda ve <xref:System.Windows.Controls.Button> klavye odaklı, işleyici çalıştırır ve <xref:System.Windows.Controls.Control.Background%2A> rengini <xref:System.Windows.Controls.Button> değiştirilir.  Tuşuna basıldığında, ancak sol ok tuşu değil <xref:System.Windows.Controls.Control.Background%2A> rengini <xref:System.Windows.Controls.Button> başlangıç rengini değiştirilir.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Fare giriş olayını örneği
 Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> rengi bir <xref:System.Windows.Controls.Button> fare işaretçisi girdiğinde değiştirildiğinde <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.Control.Background%2A> Renk fare çıktığında geri <xref:System.Windows.Controls.Button>.

 Örneğin ilk bölümünü oluşturur <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.Button> denetlemek ve ekler için olay işleyicileri <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olayları <xref:System.Windows.Controls.Button>.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 İkinci bölümü Örneğin, kodda yazılır ve olay işleyicilerini tanımlar.  Fare girdiğinde <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> rengini <xref:System.Windows.Controls.Button> değiştirilir <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Fare ayrıldığında <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> rengini <xref:System.Windows.Controls.Button> geri değiştirildiğinde <xref:System.Windows.Media.Brushes.AliceBlue%2A>.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Metin Girişi
 <xref:System.Windows.ContentElement.TextInput> Olay metin girişi için bir CİHAZDAN bağımsız şekilde dinleme olanak sağlar. Klavye metin girişi, ancak okuma, el yazısı birincil yoludur ve diğer giriş cihazları metin de girişi oluşturabilir.

 Klavye girişi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] önce uygun gönderir <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> olayları. Bu olayları işlenmeyen ve anahtarı (Denetim anahtar yönlü ok gibi) veya işlev tuşlarını yerine metinsel ise bir <xref:System.Windows.ContentElement.TextInput> olayı oluşturulur.  Yok her zaman basit bire bir eşleme arasında <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> ve <xref:System.Windows.ContentElement.TextInput> olayları çünkü birden çok tuş vuruşları tek bir karakter, metin girişi oluşturabilir ve tek bir tuş vuruşları çok karakter üretebilir dizeleri.  Bu kullandığınız diller için Çince, Japonca ve Korece gibi özellikle doğrudur [!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)] karşılık gelen kendi alfabelerde mümkün karakterlerin binlerce oluşturulacak.

 Zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gönderen bir <xref:System.Windows.ContentElement.KeyUp> / <xref:System.Windows.ContentElement.KeyDown> olay <xref:System.Windows.Input.KeyEventArgs.Key%2A> ayarlanır <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> tuş vuruşları parçası olabilir, bir <xref:System.Windows.ContentElement.TextInput> (ALT + S, örneğin basıldıysa) olay. Bu kodda sağlar bir <xref:System.Windows.ContentElement.KeyDown> denetlemek için olay işleyicisi <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> ve bulundu, işlenmek üzere daha sonra yükseltilmiş işleyicisini bırakın <xref:System.Windows.ContentElement.TextInput> olay. Bu gibi durumlarda, çeşitli özelliklerini <xref:System.Windows.Input.TextCompositionEventArgs> bağımsız değişkeni, özgün tuş vuruşları belirlemek için kullanılabilir. Benzer şekilde, bir [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] etkin olup <xref:System.Windows.Input.Key> sahip <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>, ve <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> özgün tuş vuruşu veya tuş vuruşlarını sağlar.

 Aşağıdaki örnek için bir işleyici tanımlar <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay ve için bir işleyici <xref:System.Windows.UIElement.KeyDown> olay.

 İlk kesimi başladığınız kodun veya kullanıcı arabirimi oluşturur.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 İkinci kod parçası, olay işleyicilerini içerir.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Giriş olayları olay yol ayarlama Kabarcık çünkü <xref:System.Windows.Controls.StackPanel> bağımsız olarak hangi öğeye sahip klavye odağı giriş alır. <xref:System.Windows.Controls.TextBox> Denetim ilk bildirilir ve `OnTextInputKeyDown` işleyicisi yalnızca çağrılır <xref:System.Windows.Controls.TextBox> giriş işlemedi. Varsa <xref:System.Windows.UIElement.PreviewKeyDown> olayının yerine kullanıldığı <xref:System.Windows.UIElement.KeyDown> olay `OnTextInputKeyDown` işleyicisi önce çağrılır.

 Bu örnekte, iki kez işleme mantığı yazılır; bir kez CTRL + O ve yeniden düğmenin, olay'ı tıklatın. Bu, doğrudan giriş olaylarını işleme yerine komutları kullanarak basitleştirilebilir.  Bu genel bakış ve komutlar ele alınan [komut vermeye genel genel bakış](commanding-overview.md).

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Dokunma ve düzenleme
 Yeni donanım ve Windows 7 işletim sistemindeki API uygulamaları giriş aynı anda birden çok dokunmalar alma olanağı sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaların algılamasını ve Dokunmatik meydana geldiğinde olayları yükselterek, klavye ve fare gibi diğer girişler yanıt için benzer bir şekilde touch yanıtlamasını sağlar.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iki tür touch oluştuğunda olay kullanıma sunar: olayları ve olayları düzenleme dokunma. Dokunma olayları, dokunmatik ve hareketini her parmak hakkında ham veriler sağlar. Olayları düzenleme giriş belirli eylemleri yorumlayın. Her iki olay türlerini, bu bölümde ele alınmıştır.

### <a name="prerequisites"></a>Önkoşullar
 Dokunmaya yanıt veren bir uygulama geliştirmek için aşağıdaki bileşenlere ihtiyacınız var.

- Visual Studio 2010.

- Windows 7.

- Windows dokunmatik destekleyen bir dokunmatik gibi bir cihaz.

### <a name="terminology"></a>Terminoloji
 Dokunma işlemi tartışılırken aşağıdaki terimler kullanılır.

- **Touch** Windows 7 tarafından tanınan bir kullanıcı girişi türü. Genellikle, dokunma dokunmatik ekranda parmağınızı koyarak başlatılır. Cihazın parmak'ın konumunu ve taşıma fare giriş olarak yalnızca dönüştürüldüyse dizüstü bilgisayarlarına ortak olan dokunmatik gibi cihazları touch desteklemez unutmayın.

- **Multitouch** aynı anda birden fazla noktasından oluşan touch olduğu. Windows 7 ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] multitouch destekler. Her dokunma ele alınmıştır belgelerine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kavramlar multitouch için geçerlidir.

- A **işleme** touch bir nesneye uygulanan fiziksel bir eylem olarak yorumlanıp yorumlanmadığını oluşur. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], olayları düzenleme giriş çeviri, genişletme veya döndürme düzenleme olarak yorumlayın.

- A `touch device` dokunma girişini dokunmatik üzerinde tek bir parmak gibi üreten bir cihazı temsil eder.

### <a name="controls-that-respond-to-touch"></a>Yanıt denetimleri
 Aşağıdaki denetimler görünümden kaydırılan içerik varsa bir parmak denetimi arasında sürükleyerek kaydırılabileceğini.

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.ContextMenu>

- <xref:System.Windows.Controls.DataGrid>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListView>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.TextBox>

- <xref:System.Windows.Controls.ToolBar>

- <xref:System.Windows.Controls.TreeView>

 <xref:System.Windows.Controls.ScrollViewer> Tanımlar <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> ekli touch kaydırma etkinleştirilip etkinleştirilmediği yatay, dikey, her ikisi de veya hiçbiri belirtmenize olanak tanıyan özellik. <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> Özelliği, kullanıcı dokunmatik ekranı gelen parmak kaldırıncaya olduğunda ne kadar hızlı kaydırma yavaşlar belirtir. <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> Ekli özellik düzenleme uzaklığı çevrilecek uzaklığı kayan oranını belirtir.

### <a name="touch-events"></a>Dokunma olayları
 Temel sınıflar <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>, ve <xref:System.Windows.ContentElement>, uygulamanızın dokunmaya yanıt verir, böylece abone olabileceğiniz olayları tanımlayın. Dokunma olayları, uygulamanızın touch nesneyi düzenleme dışında bir şey olarak yorumlar olduğunda yararlıdır. Örneğin, bir kullanıcı bir veya daha fazla parmağınızla çizmek sağlayan bir uygulama dokunma olayları için abone.

 Üç bağımsız olarak tanımlayan sınıf benzer şekilde davranır aşağıdaki olaylar tanımlayın.

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

 Klavye ve fare olayları gibi yönlendirilmiş olaylar touch olaylardır. İle başlayan olayları `Preview` olayları ve ile başlayan olayları tünel `Touch` tırmanma olaylardır. Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md). Bu olayları işlediğinizde, giriş, herhangi bir öğenin göreli konumunu çağırarak alabilirsiniz <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> veya <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> yöntemi.

 Dokunma olayları arasındaki etkileşimi anlamak için burada bir kullanıcı bir öğede bir parmak koyar, parmak öğesinde taşır ve ardından öğeden parmak kaldırıncaya senaryoyu göz önünde bulundurun. Aşağıdaki çizimde, tırmanma olayları (Tünel olayları kolaylık olması için göz ardı edilir) yürütülmesini gösterir.

 ![Dokunma olayları dizisi. ](./media/ndp-touchevents.png "NDP_TouchEvents") dokunma olayları

 Önceki çizimde olayların sırası aşağıdaki listede açıklanmaktadır.

1. <xref:System.Windows.UIElement.TouchEnter> Olay olduğunda kullanıcı koyar nabzını öğe üzerinde bir kez gerçekleşir.

2. <xref:System.Windows.UIElement.TouchDown> Olayı, bir kez oluşur.

3. <xref:System.Windows.UIElement.TouchMove> Olay kullanıcı öğesinin içine parmağınızı hareket ederken birden çok kez gerçekleşir.

4. <xref:System.Windows.UIElement.TouchUp> Olay kullanıcı kaldırıncaya öğeden parmak ne zaman bir kez gerçekleşir.

5. <xref:System.Windows.UIElement.TouchLeave> Olayı, bir kez oluşur.

 İkiden fazla parmağınızı kullanıldığında olaylar için her parmak gerçekleşir.

### <a name="manipulation-events"></a>Olayları düzenleme
 Burada bir uygulamasını etkinleştiren bir kullanıcı, nesneyi işlemek durumlarda <xref:System.Windows.UIElement> olayları düzenleme sınıfı tanımlar. Dokunma konumu yalnızca rapor dokunma olayları, giriş nasıl yorumlanacağını olayları düzenleme bildirin. İşlemeleri, çeviri, genişletme ve döndürme üç tür vardır. Aşağıdaki liste, üç tür işlemeleri çağırmayı açıklar.

- Bir nesne üzerinde bir parmak koyun ve parmak çeviri işleme çağırmak için dokunmatik ekran arasında taşıyın. Bu, genellikle nesne taşır.

- Bir nesne üzerinde iki yola yerleştirin ve yaklaşacak şekilde veya başka bir genişletme işleme çağrılacak dışında küçüldükleri parmağınızı taşıyın. Bu genellikle nesne yeniden boyutlandırır.

- Bir nesne üzerinde iki yola yerleştirin ve diğer döndürme düzenleme çağrılacak etrafında parmağınızı döndürün. Bu, genellikle nesne döndürür.

 Aynı anda birden fazla işleme türünü ortaya çıkabilir.

 İşlemeleri için yanıt nesnelere neden zaman için Eylemsizliği görünür nesne olabilir. Bu, nesnelerinizi fiziksel dünyaya benzetimini yapabilirsiniz. Örneğin, sabit gönderirseniz bir tablo arasında bir kitap gönderdiğinizde bu yayın yeterince kitap devam eder. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıcının parmağınızı serbest sonra nesneyi düzenleme olayları yükselterek bu davranışını benzetmekte sağlar.

 Taşıma, yeniden boyutlandırma ve nesneyi döndürmek kullanıcının sağlayan bir uygulama oluşturma hakkında daha fazla bilgi için bkz: [izlenecek yol: İlk dokunmatik uygulamanızı oluşturma](walkthrough-creating-your-first-touch-application.md).

 <xref:System.Windows.UIElement> Aşağıdaki olayları düzenleme tanımlar.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Varsayılan olarak, bir <xref:System.Windows.UIElement> bu olayları düzenleme almaz. Olayları işleme almak için bir <xref:System.Windows.UIElement>ayarlayın <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> için `true`.

#### <a name="the-execution-path-of-manipulation-events"></a>Olayları düzenleme yürütme yolu
 Burada bir kullanıcı "bir nesne oluşturur" bir senaryo düşünün. Kullanıcı nesnesi üzerinde bir parmak koyar taşır parmak kısa bir mesafe için dokunmatik ekranı arasında ve parmağınızı hareket ediyor ancak ardından kaldırıncaya. Bu nesne altında kullanıcının parmak taşıyın ve sonra kullanıcı parmağınızı kaldırıncaya taşımak devam ' dir.

 Aşağıdaki çizim, olayları düzenleme ve her olay hakkında önemli bilgiler yürütme yolunu gösterir.

 ![Olayları düzenleme dizisi. ](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") olayları düzenleme

 Önceki çizimde olayların sırası aşağıdaki listede açıklanmaktadır.

1. <xref:System.Windows.UIElement.ManipulationStarting> Olayı, kullanıcı nesne üzerinde bir parmak verdiğinde oluşur. Diğerlerinin yanı sıra bu olay ayarlamanıza olanak tanır <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> özelliği. Sonraki olayları işleme konumunu göreli olacaktır <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. Olay dışında <xref:System.Windows.UIElement.ManipulationStarting>, bu özellik salt okunur şekilde <xref:System.Windows.UIElement.ManipulationStarting> olaydır bu özelliği ayarlayabilirsiniz. yalnızca bir kez.

2. <xref:System.Windows.UIElement.ManipulationStarted> Sonraki olayı oluşur. Bu olay işleme kaynağı raporlar.

3. <xref:System.Windows.UIElement.ManipulationDelta> Olayı, bir kullanıcının parmağınızı hareket dokunmatik olarak birden çok kez oluşur. <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> Özelliği <xref:System.Windows.Input.ManipulationDeltaEventArgs> sınıfı raporlar düzenlenmesini taşıma, genişletme veya çeviri yorumlanır. Nesneyi düzenleme işin çoğu burada gerçekleştirdiğiniz budur.

4. <xref:System.Windows.UIElement.ManipulationInertiaStarting> Olay kullanıcının parmağınızı nesne ile iletişimi kaybettiğinde gerçekleşir. Bu olay, işlemeleri, yavaşlama Eylemsizliği sırasında belirtmenizi sağlar. Bu durum, seçerseniz nesnenizin farklı fiziksel alanları veya öznitelikleri öykünebileceği olduğundan. Örneğin, uygulamanızın Fiziksel dünyada öğeleri temsil eden iki nesne varsa ve biri diğerinden daha ağır varsayalım. Açık nesne hızlıdır yavaşlatma daha ağır nesne yapabilirsiniz.

5. <xref:System.Windows.UIElement.ManipulationDelta> Olay Eylemsizliği gerçekleştiği sırada birden çok kez gerçekleşir. Bu olay kullanıcının parmağınızı dokunmatik ekranı arasında taşıdığınız zaman ve ne zaman oluştuğunu not [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Eylemsizliği benzetimini yapar. Diğer bir deyişle, <xref:System.Windows.UIElement.ManipulationDelta> önce ve sonra gerçekleşir <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay. <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> Özelliği raporlar olup olmadığını <xref:System.Windows.UIElement.ManipulationDelta> olayı bu özelliği kontrol edin ve kendi değerine bağlı olarak farklı eylemleri gerçekleştirmek için Eylemsizliği sırasında oluşur.

6. <xref:System.Windows.UIElement.ManipulationCompleted> Olay işleme ve tüm Eylemsizliği sona erdiğinde. Diğer bir deyişle, sonra tüm <xref:System.Windows.UIElement.ManipulationDelta> olaylar meydana, <xref:System.Windows.UIElement.ManipulationCompleted> düzenlenmesini tamamlandığını göstermek için olayı oluşur.

 <xref:System.Windows.UIElement> Ayrıca tanımlar <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olay. Bu gerçekleştiğinde, <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> yöntemi çağrıldığında <xref:System.Windows.UIElement.ManipulationDelta> olay. <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> Olay, bir nesne sınırına geldiğinde görsel geri bildirim sağlamak, uygulamaları veya bileşenleri sağlar. Örneğin, <xref:System.Windows.Window> sınıfı tanıtıcıları <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olay, edge ile karşılaşıldığında biraz taşımak için penceresi neden olacak.

 Çağırarak düzenlemeyi iptal edebilirsiniz <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> yöntemi dışında herhangi bir işleme olayın olay bağımsız değişkenlerde <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olay. Çağırdığınızda <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>işleme olaylar artık oluşturulur ve fare olayları için dokunma oluşur. Aşağıdaki tabloda, düzenlemeyi iptal süresi ve oluşan bir fare olayları arasındaki ilişkiyi açıklar.

|İptal Olayı çağrılma yeri|Zaten oluşan giriş gerçekleşen fare olayları|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> ve <xref:System.Windows.UIElement.ManipulationStarted>|Olayları fare.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Fare aşağı ve fare olayları taşıyın.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> ve <xref:System.Windows.UIElement.ManipulationCompleted>|Fare aşağı, fare taşıma ve fare olayları.|

 Çağırırsanız unutmayın <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> düzenlenmesini Eylemsizliği içinde olduğunda, yöntemin döndürür `false` ve fare olayları giriş oluşturmaz.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Dokunma ve olayları düzenleme arasındaki ilişki
 A <xref:System.Windows.UIElement> dokunma olayları her zaman alabilir. Zaman <xref:System.Windows.UIElement.IsManipulationEnabled%2A> özelliği `true`, <xref:System.Windows.UIElement> touch hem düzenleme olayları alabilirsiniz.  Varsa <xref:System.Windows.UIElement.TouchDown> olay işlenmez (diğer bir deyişle, <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği `false`), işleme mantığı öğeye dokunma yakalar ve olayları düzenleme oluşturur. Varsa <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği `true` içinde <xref:System.Windows.UIElement.TouchDown> olay işleme mantığı olayları düzenleme oluşturmaz. Dokunma olayları ve işleme olayları arasındaki ilişki aşağıda gösterilmiştir.

 ![Dokunma ve düzenleme olayları arasındaki ilişki](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") dokunma ve düzenleme olayları

 Aşağıdaki listede, önceki resimde gösterilen dokunma ve düzenleme olayları arasındaki ilişkiyi açıklar.

- İlk dokunmatik cihazın ne zaman oluşturur bir <xref:System.Windows.UIElement.TouchDown> olayda bir <xref:System.Windows.UIElement>, işleme mantığı çağrıları <xref:System.Windows.UIElement.CaptureTouch%2A> oluşturan yöntemi <xref:System.Windows.UIElement.GotTouchCapture> olay.

- Zaman <xref:System.Windows.UIElement.GotTouchCapture> gerçekleşir, işleme mantığı çağrıları <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> oluşturan yöntemi <xref:System.Windows.UIElement.ManipulationStarting> olay.

- Zaman <xref:System.Windows.UIElement.TouchMove> işleme mantığı oluşturur, olaylar meydana <xref:System.Windows.UIElement.ManipulationDelta> önce meydana gelen olayları <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay.

- Son dokunduğunuzda cihaz öğe başlatır <xref:System.Windows.UIElement.TouchUp> olay işleme mantığı oluşturur <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay.

<a name="focus"></a>
## <a name="focus"></a>Odağı
 Odak ilgilidir iki ana kavram vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: klavye odağı ve mantıksal odak.

### <a name="keyboard-focus"></a>Klavye odağı
 Klavye odağı, klavye girişi alan öğesine başvurur.  Klavye girintisine sahip yalnızca bir öğe tüm masaüstü olabilir.  İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], klavye girintisine sahip öğenin <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> kümesine `true`.  Statik <xref:System.Windows.Input.Keyboard> yöntemi <xref:System.Windows.Input.Keyboard.FocusedElement%2A> şu anda klavye girintisine sahip öğeyi döndürür.

 Bir öğe için sekme veya gibi belirli öğeleri üzerinde fareyi tıklatarak klavye odağı elde edilebilir bir <xref:System.Windows.Controls.TextBox>.  Klavye odağı da elde edilebilir program aracılığıyla kullanarak <xref:System.Windows.Input.Keyboard.Focus%2A> metodunda <xref:System.Windows.Input.Keyboard> sınıfı.  <xref:System.Windows.Input.Keyboard.Focus%2A> Belirtilen öğe klavye odaklanmak çalışır.  Tarafından döndürülen öğe <xref:System.Windows.Input.Keyboard.Focus%2A> şu anda klavye girintisine sahip öğe.

 Klavye odağı almak bir öğe için sırayla <xref:System.Windows.UIElement.Focusable%2A> özelliği ve <xref:System.Windows.UIElement.IsVisible%2A> özellikler ayarlanmalıdır **true**.  Gibi bazı sınıflar <xref:System.Windows.Controls.Panel>, sahip <xref:System.Windows.UIElement.Focusable%2A> kümesine `false` tarafından varsayılan; bu nedenle, bu özelliği ayarlamak gerekebilir `true` odak alabilmesi için bu öğeye istiyorsanız.

 Aşağıdaki örnekte <xref:System.Windows.Input.Keyboard.Focus%2A> klavye odağı ayarlamak için bir <xref:System.Windows.Controls.Button>.  Bir uygulamada ilk odağı ayarlamak için önerilen konum <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Klavye odağı hakkında daha fazla bilgi için bkz: [odağa genel bakış](focus-overview.md).

### <a name="logical-focus"></a>Mantıksal odak
 Mantıksal odak başvurduğu <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> odak kapsamında.  Uygulamada mantıksal odağa sahip birden çok öğe olabilir, ancak ayrıca mantıksal Odaklanıldığında belirli odak kapsamına sahip bir öğe yalnızca olabilir.

 Odak kapsamdır izler bir kapsayıcı öğenin <xref:System.Windows.Input.FocusManager.FocusedElement%2A> kendi kapsamı içinde.  Odak odak kapsam dışına çıktığında, odaklanılan öğeyi klavye odağı kaybeder ancak mantıksal odağını korur.  Odak odak kapsamına geri döndüğünde, odaklanılan öğeyi klavye odağı elde edersiniz.  Bu, klavye odağı arasında birden çok odak kapsam değiştirilmesine izin verir ancak odak döndürdüğünde odak kapsamında odaklanılan öğeyi odaklanan öğeyi kalmasını oluşturmasını sağlar.

 Öğenin odak kapsamda dönüştürülebilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ayarlayarak <xref:System.Windows.Input.FocusManager> ekli özellik <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> için `true`, ekli özellik kullanarak ayarlayarak kod <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> yöntemi.

 Aşağıdaki örnekte bir <xref:System.Windows.Controls.StackPanel> ayarlayarak bir odak kapsama <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> ekli özellik.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 Sınıflar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odak kapsamı varsayılan olarak hangilerinin <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, ve <xref:System.Windows.Controls.ContextMenu>.

 Klavye girintisine sahip bir öğe mantıksal odağı ait odak kapsam için de bulunur; Bu nedenle, bir öğe üzerinde odak ayarlama <xref:System.Windows.Input.Keyboard.Focus%2A> metodunda <xref:System.Windows.Input.Keyboard> mantıksal Odaklanıldığında ve öğe klavye odağı vermek sınıf veya temel öğe sınıfları deneyecek.

 Odaklanan öğeyi odak kapsamında belirlemek için <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Odak kapsamı odaklanan öğeyi değiştirmek için kullanın <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.

 Mantıksal odak hakkında daha fazla bilgi için bkz: [odağa genel bakış](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Fare konumu
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Giriş API koordinat ilgili yararlı bilgiler sağlar.  Örneğin, koordine `(0,0)` sol üst koordinat ancak hangi öğe ağacında sol üst? Girişi hedef öğesi? Öğe, olay işleyicisine bağlı? Veya başka bir şey mi? Karışıklığı önlemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş API gerektirir fareyi elde edilen koordinatları ile çalışırken, referans çerçevesi belirtin. <xref:System.Windows.Input.Mouse.GetPosition%2A> Yöntemi koordinat fare işaretçisinin göreli belirtilen öğeyi döndürür.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Fare yakalama
 Fare cihazlarına özellikle fare yakalamayı bilinen bir kalıcı özellik tutun. Fare yakalama, bir Sürükle ve bırak işlemi başlatıldığında, böylece nominal ekrandaki ilgili diğer işlemleri fare işaretçisi konumunun mutlaka gerçekleşmez bir geçiş giriş durumunu korumak için kullanılır. Sürükleme sırasında sürükle ve fare yakalama sürüklemenin çıkış noktası tarafından açık tutulduğu sürece çoğu fareyi üzerine getirme ipuçları uygun hale getiren bırak, durduruluyor olmadan kullanıcı tıklayamazsınız. Giriş sistemi, fare yakalamayı zorlamak için belirli bir öğe veya fare yakalama durumunu temizlemeniz API'leri yanı sıra, fare yakalama durumu belirlemek API'leri kullanıma sunar. Sürükle ve bırak işlemleri hakkında daha fazla bilgi için bkz. [sürükle ve bırak genel bakış](drag-and-drop-overview.md).

<a name="commands"></a>
## <a name="commands"></a>Komutlar
 Komutlar, cihaz giriş daha fazla anlam düzeyinde giriş işlemeyi etkinleştirin.  Komutlardır basit yönergeleri gibi `Cut`, `Copy`, `Paste`, veya `Open`.  Komutlar, komut mantığınızı merkezileştirerek için kullanışlıdır.  Aynı komutu erişiyor olabilir bir <xref:System.Windows.Controls.Menu>, bir <xref:System.Windows.Controls.ToolBar>, veya bir klavye kısayolu aracılığıyla. Komutları da komutu kullanılamaz hale geldiğinde denetimleri devre dışı bırakmak için bir mekanizma sağlar.

 <xref:System.Windows.Input.RoutedCommand> olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması <xref:System.Windows.Input.ICommand>.  Olduğunda bir <xref:System.Windows.Input.RoutedCommand> yürütüldüğünde, bir <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> olayı hangi tüneli ve kabarcık öğe ağacı üzerinden gibi diğer girişler komut hedefi üzerinde oluşturulur.  Bir komut hedefi ayarlanmazsa, klavye odaklı öğe komut hedefi olacaktır.  Komut gerçekleştiren mantıksal bağlı olduğu bir <xref:System.Windows.Input.CommandBinding>.  Olduğunda bir <xref:System.Windows.Input.CommandManager.Executed> olay ulaştığında bir <xref:System.Windows.Input.CommandBinding> o belirli komutla ilgili <xref:System.Windows.Input.ExecutedRoutedEventHandler> üzerinde <xref:System.Windows.Input.CommandBinding> çağrılır.  Bu işleyici, komutun eylemi gerçekleştirir.

 Komut vermeye genel ile ilgili daha fazla bilgi için bkz: [komut vermeye genel genel bakış](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşan yaygın komutları içeren bir kitaplık sağlar <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, ve <xref:System.Windows.Documents.EditingCommands>, ya da kendi tanımlayabilirsiniz.

 Aşağıdaki örnek nasıl ayarlanacağını gösterir. bir <xref:System.Windows.Controls.MenuItem> tıklandığında böylece çağırma <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutunu <xref:System.Windows.Controls.TextBox>olduğunu varsayarak <xref:System.Windows.Controls.TextBox> klavye girintisine sahip.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 Komutlar hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [komut vermeye genel genel bakış](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>Giriş sistemi ve temel öğeler
 Giriş olayları tarafından tanımlanan ekli olaylar gibi <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, ve <xref:System.Windows.Input.Stylus> sınıflar giriş sistem tarafından gerçekleştirilen ve görsel ağaç çalışma zamanında test isabet temel nesne modelinde belirli bir konuma eklenmiş.

 Olayların her biri, <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, ve <xref:System.Windows.Input.Stylus> ekli olay ayrıca temel öğe sınıfları tarafından yeniden kullanıma sunulduğunu olarak tanımladığınız <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> yeni yönlendirilmiş olay olarak. Temel öğe yönlendirilmiş olaylar, özgün ekli olay işleme ve olay verileri yeniden sınıfları tarafından oluşturulur.

 Giriş olayı, bir temel öğe giriş olayı uygulaması aracılığıyla belirli bir kaynak öğesi ile ilişkili olduğunda, geri kalanında üzerindeki mantıksal ve görsel ağaç nesnelerin bir birleşimini temel alır ve tarafından işlenen bir olay yönlendirme üzerinden yönlendirilebilir uygulama kodu.  Genellikle, yönlendirilmiş olaylar kullanarak bu cihaz ile ilgili giriş olaylarını işlemek daha kullanışlı olan <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement>, daha sezgisel olay işleyici söz dizimi hem de kullanabileceğinizden [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod. Bunun yerine işlem tarafından başlatılan ekli olayı işlemek seçebilirsiniz, ancak birkaç bir sorunla karşılaşırsanız: ekli olay temel öğe sınıfı işleyerek işlenmiş işaretlenmiş olabilir ve sırayla true olay söz dizimi yerine erişimci yöntemlerini kullanmanız gerekir ekli olayları için işleyiciler eklemek için.

<a name="whats_next"></a>
## <a name="whats-next"></a>Yenilikler
 Artık girişinde işlemek için çeşitli teknikler vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Giriş olayları ve tarafından kullanılan yönlendirilmiş olay mekanizmaları çeşitli türlerde geliştirilmiş bilginizin olması [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Ek kaynaklar kullanılabilir biçimde açıklayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework öğeleri ve daha ayrıntılı olarak olay yönlendirme. Daha fazla bilgi için şu genel bakışlara bakın [komut vermeye genel genel bakış](commanding-overview.md), [odağa genel bakış](focus-overview.md), [temel öğelere genel bakış](base-elements-overview.md), [WPFiçindeağaçlar](trees-in-wpf.md), ve [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Odağa Genel Bakış](focus-overview.md)
- [Komut Vermeye Genel Bakış](commanding-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Temel Öğelere Genel Bakış](base-elements-overview.md)
- [Özellikler](properties-wpf.md)
