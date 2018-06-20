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
ms.openlocfilehash: 77f69fb73d40c76257accc989d4a9a57ed992cf6
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207657"
---
# <a name="input-overview"></a>Girişe Genel Bakış
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Alt sistemi sağlayan güçlü [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] giriş çeşitli aygıtlar almak için fare, klavye, dokunma ve Kalem de dahil olmak üzere. Bu konu, tarafından sağlanan hizmetlerin açıklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve giriş sistemleri mimarisini açıklar.  
  
  
<a name="input_api"></a>   
## <a name="input-api"></a>Giriş API  
 Birincil Giriş [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] Etkilenme temel öğe sınıfları bulundu: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>, ve <xref:System.Windows.FrameworkContentElement>.  Temel öğeler hakkında daha fazla bilgi için bkz: [temel öğeleri genel bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md).  Bu sınıfların anahtar basarsa, fare düğmeleri, fare tekerleği, fare hareketini, odak yönetimi ve fare yakalama ilgili giriş olayı için işlevsellik sağlar. Giriş yerleştirerek [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] temel öğelerde değerlendirmesini yerine tüm olayları bir hizmet olarak giriş, giriş mimarisi, biri birden çok kullanıcı arabiriminde belirli bir nesne tarafından sağlanmasına olanak ve bir olay yönlendirme düzeni yapabildiği desteklemek için giriş olaylarını sağlar öğesinin bir giriş olayını işlemek için bir fırsat yok. Çok sayıda giriş olaylar bunlarla ilişkilendirilmiş olayları çifti sahiptir.  Örneğin, olay tuşunu ilişkili olduğu <xref:System.Windows.Input.Keyboard.KeyDown> ve <xref:System.Windows.Input.Keyboard.PreviewKeyDown> olaylar.  Bu olaylar'ın nasıl bunlar hedef öğe yönlendirildiği içinde farktır.  Önizleme olayları tünel öğesi kök öğesi ağacından hedef öğe için aşağı.  Kabarcıklanma olayları Kabarcık yukarı hedef öğeden kök öğesi için.  Olay yönlendirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha ayrıntılı olarak daha sonra bu genel bakış ve içinde ele alınmıştır [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
### <a name="keyboard-and-mouse-classes"></a>Klavye ve fare sınıfları  
 Giriş yanı sıra [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] temel öğe sınıfları <xref:System.Windows.Input.Keyboard> sınıfı ve <xref:System.Windows.Input.Mouse> sınıfları sağlar ek [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] klavye ve fare girişi çalışma.  
  
 Giriş örnekleri [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] üzerinde <xref:System.Windows.Input.Keyboard> sınıfı olan <xref:System.Windows.Input.Keyboard.Modifiers%2A> döndürür özelliği <xref:System.Windows.Input.ModifierKeys> şu anda basılı ve <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> belirtilen anahtar basılı olup olmadığını belirleyen yöntemi.  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> yöntemi belirlemek için bir <xref:System.Windows.Input.Key> aşağı durumda.  
  
 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]  
  
 Giriş örnekleri [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] üzerinde <xref:System.Windows.Input.Mouse> sınıfı olan <xref:System.Windows.Input.Mouse.MiddleButton%2A>, orta fare düğmesini durumunu alır ve <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, öğenin fare işaretçisini alır şu anda biter.  
  
 Aşağıdaki örnek belirler olup olmadığını <xref:System.Windows.Input.Mouse.LeftButton%2A> fareyi üzerinde bulunduğu <xref:System.Windows.Input.MouseButtonState.Pressed> durumu.  
  
 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]  
  
 <xref:System.Windows.Input.Mouse> Ve <xref:System.Windows.Input.Keyboard> sınıfları bu genel bakışta boyunca daha ayrıntılı ele alınmıştır.  
  
### <a name="stylus-input"></a>Kalem giriş  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Destek için tümleşik olan <xref:System.Windows.Input.Stylus>.  <xref:System.Windows.Input.Stylus> Popüler tarafından yapılan bir kalem girişi [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları işlemek kalem fare fareyi kullanarak [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıca klavye ve fare benzer bir modelini kullanan bir kalem aygıt soyutlama kullanıma sunar.  Tüm kalem ilgili [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] "Kalem" sözcüğünü içeren.  
  
 Kalem, fare davranamaz olduğundan yalnızca fare girdisi destekleyen uygulamalar hala kalem destek belirli bir düzeyde otomatik olarak elde edebilirsiniz. Bu tür bir şekilde kalem kullanıldığında, uygulama uygun kalem olay işleme fırsatına verilir ve karşılık gelen fare olayını işler. Üst düzey Hizmetleri mürekkep giriş gibi ek olarak, ayrıca kalem aygıt soyutlama olarak kullanılabilir.  Giriş olarak mürekkep hakkında daha fazla bilgi için bkz: [mürekkep ile çalışmaya başlama](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).  
  
<a name="event_routing"></a>   
## <a name="event-routing"></a>Olay yönlendirme  
 A <xref:System.Windows.FrameworkElement> öğeleri ağacının oluşturan kendi içerik modelinde alt öğeleri olarak diğer öğeler içerebilir.  İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], üst öğenin alt öğeleri veya diğer alt olayları teslim etme yönlendirilmiş giriş katılabilirsiniz. Bu küçük denetimleri dışında denetimleri "denetim oluşturma" veya "birleştirme." olarak bilinen bir işlem oluşturmak için özellikle kullanışlıdır Öğe ağaçları ve öğesi ağaçları olay yolları nasıl ilişkili olduğunu hakkında daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
 Belirli nesne veya yol boyunca öğesi tarafından farklı bir öğe kaynaklanan bir olaya (aracılığıyla işleme) önemli bir yanıt sunmaya seçebilmeleri olay yönlendirme birden çok öğe için olayları iletme işlemidir.  Yönlendirilmiş olaylar üç yönlendirme mekanizmaları birini kullanın: tırmanmasını ve tünel doğrudan.  Doğrudan yönlendirme, kaynak öğesi, bildirim yalnızca öğesidir ve olay için diğer öğeleri yönlendirilmedi. Ancak, doğrudan yönlendirilmiş olay yalnızca standart aksine yönlendirilmiş olaylar için mevcut olan bazı ek özellikleri hala sunar [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olaylar. Tırmanmasını öğesi ağacı ilk olay sonra kaynaklanan öğesi üst öğe ve benzeri bildirerek çalışır.  Tünel öğe ağacı kök dizininde başlar ve özgün kaynak öğe ile biten aşağı çalışır.  Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Giriş olayları genellikle tünel olayı ve kabarcıklanma olayı oluşur çiftler halinde gelir.  Tünel olayları "Önizleme" önekiyle kabarcıklanma olaylardan ayırt edilir.  Örneğin, <xref:System.Windows.Input.Mouse.PreviewMouseMove> tünel fare hareketi olayını sürümüdür ve <xref:System.Windows.Input.Mouse.MouseMove> bu olay kabarcıklanma sürümü. Bu olay çifti öğe düzeyinde uygulanır ve devralınan bir özelliği, olmayan bir kuraldır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi. Ayrıntılar için bkz WPF giriş olayları bölümünde [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="handling_input_events"></a>   
## <a name="handling-input-events"></a>Girdi olaylarını işleme  
 Bir öğenin girişte almak için olay işleyici belirli bir olay ile ilişkilendirilmiş olması gerekir.  İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bu basittir: Bu olay için dinleme öğesinin özniteliği olarak olayı'nın adına başvuruyor.  Sonra temsilci üzerinde temel tanımlamak olay işleyicisi adı özniteliğinin değerini ayarlayın.  Olay işleyicisi gibi C# kodunda yazılmış olmalıdır ve bir arka plan kod dosyasına dahil edilebilir.  
  
 İşletim sistemi klavye odağını bir öğede durumdayken oluşan anahtar Eylemler bildirdiğinde klavye olayları oluşur. Fare ve Kalem olayları her iki kategoriye ayrılır: rapor işaretçi konumuna göre öğesi değişiklikleri olaylar ve cihaz düğmeleri durumda raporu değişir olaylar.  
  
### <a name="keyboard-input-event-example"></a>Klavye giriş olayı örneği  
 Aşağıdaki örnek, bir sol ok tuşu için dinler.  A <xref:System.Windows.Controls.StackPanel> oluşturulur sahip bir <xref:System.Windows.Controls.Button>.  Sol Ok tuşu bağlı olduğu için dinlemek için bir olay işleyicisi <xref:System.Windows.Controls.Button> örneği.  
  
 Örneğin ilk bölümü oluşturur <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.Button> ve olay işleyicisi ekler <xref:System.Windows.UIElement.KeyDown>.  
  
 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]  
  
 İkinci bölümü, kodda yazılır ve olay işleyicisini tanımlar.  Sol ok tuşunu basılı ne zaman ve <xref:System.Windows.Controls.Button> klavye odaklı, işleyicisi çalışır ve <xref:System.Windows.Controls.Control.Background%2A> rengini <xref:System.Windows.Controls.Button> değiştirilir.  Tuşuna basılana ancak sol ok tuşunu, değilse <xref:System.Windows.Controls.Control.Background%2A> rengini <xref:System.Windows.Controls.Button> başlangıç rengini değiştirilir.  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]  
  
### <a name="mouse-input-event-example"></a>Fare giriş olayını örneği  
 Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> rengi bir <xref:System.Windows.Controls.Button> fare işaretçisini girdiğinde değiştirilir <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.Control.Background%2A> Renk fare çıktığında geri <xref:System.Windows.Controls.Button>.  
  
 Örneğin ilk bölümü oluşturur <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.Button> denetlemek ve olay işleyicileri iliştirir <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olayları <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]  
  
 Örnek ikinci bölümü kodda yazılır ve olay işleyicileri tanımlar.  Fare girdiğinde <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> rengini <xref:System.Windows.Controls.Button> değiştirilir <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Fare ayrıldığında <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> rengini <xref:System.Windows.Controls.Button> geri değiştirilen <xref:System.Windows.Media.Brushes.AliceBlue%2A>.  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]  
  
<a name="text_input"></a>   
## <a name="text-input"></a>Metin girişi  
 <xref:System.Windows.ContentElement.TextInput> Olay metin girişi için bir CİHAZDAN bağımsız şekilde dinleme olanak sağlar. Klavye girişi, ancak konuşma metin yazısının birincil yoludur ve diğer giriş cihazlar metin de giriş oluşturabilir.  
  
 Klavye girişi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] önce uygun gönderir <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> olaylar. Bu olaylar işlenmiyor ve anahtarı (tek yönlü ok gibi bir denetim anahtarı) veya işlev tuşlarını yerine metinsel ise sonra bir <xref:System.Windows.ContentElement.TextInput> olayı oluşturulur.  Yok. her zaman arasında basit bire bir eşleme <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> ve <xref:System.Windows.ContentElement.TextInput> olayları birden çok tuş vuruşları tek bir karakterin metin giriş oluşturabilir ve tek tuş vuruşları çok karakter oluşturmak için dizeleri.  Kullandığınız diller için Çince, Japonca ve Kore dili gibi özellikle geçerlidir [!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)] bunların karşılık gelen alfabesinde olası karakteri binlerce oluşturulacak.  
  
 Zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gönderir bir <xref:System.Windows.ContentElement.KeyUp> / <xref:System.Windows.ContentElement.KeyDown> olayı <xref:System.Windows.Input.KeyEventArgs.Key%2A> ayarlanır <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> parçası tuş vuruşları haline gelir, bir <xref:System.Windows.ContentElement.TextInput> (ALT + S, örneğin basıldığında varsa) olay. Bu kodda sağlayan bir <xref:System.Windows.ContentElement.KeyDown> denetlemek için olay işleyicisini <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> ve bulundu, daha sonra yükseltilmiş işleyicisini işlenmeye bırakın <xref:System.Windows.ContentElement.TextInput> olay. Bu durumda, çeşitli özelliklerini <xref:System.Windows.Input.TextCompositionEventArgs> bağımsız değişkeni, özgün tuş vuruşları belirlemek için kullanılabilir. Benzer şekilde, bir [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] etkindir <xref:System.Windows.Input.Key> değerine sahip <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>, ve <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> özgün tuş vuruşu veya tuş vuruşları sağlar.  
  
 Aşağıdaki örnek, bir işleyici tanımlar <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay ve için bir işleyici <xref:System.Windows.UIElement.KeyDown> olay.  
  
 Kullanıcı arabirimi kodu veya işaretleme ilk bölümü oluşturur.  
  
 [!code-xaml[InputOvw#Input_OvwTextInputXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]  
  
 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]  
  
 Olay işleyicileri ikinci kesim kod içerir.  
  
 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]  
  
 Giriş olayları olay yolu Kabarcık olduğundan <xref:System.Windows.Controls.StackPanel> bağımsız olarak hangi öğeye sahip klavye odağını giriş alır. <xref:System.Windows.Controls.TextBox> Denetim ilk bildirilir ve `OnTextInputKeyDown` işleyicisi yalnızca çağrılır <xref:System.Windows.Controls.TextBox> giriş işlemedi. Varsa <xref:System.Windows.UIElement.PreviewKeyDown> olay yerine kullanılır <xref:System.Windows.UIElement.KeyDown> olayı `OnTextInputKeyDown` işleyicisi önce çağrılır.  
  
 Bu örnekte, iki kez işleme mantığı yazılır — bir kez CTRL + O ve yeniden düğmenin, olay'ı tıklatın. Bu girdi olaylarını işleme yerine doğrudan komutları kullanarak basit hale getirilebilir.  Bu genel bakış ve komutları ele alınan [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="touch_and_manipulation"></a>   
## <a name="touch-and-manipulation"></a>Dokunma ve düzenleme  
 Yeni donanım ve API Windows 7 işletim sisteminde uygulamalar aynı anda birden çok rötuşları giriş almaya olanağı sunar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları algılamak ve dokunma meydana geldiğinde olayları yükselterek klavye ve fare gibi diğer giriş yanıt için benzer bir şekilde touch yanıtlamak için etkinleştirir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iki tür dokunma oluştuğunda olay sunar: olaylar ve işleme olaylar touch. Dokunma olayları dokunmatik ve hareketini her parmak hakkında ham veriler sağlar. Olayları düzenleme giriş belirli eylemler olarak yorumlayın. Her iki tür olay bu bölümde ele alınmıştır.  
  
### <a name="prerequisites"></a>Önkoşullar  
 Touch yanıtlaması bir uygulama geliştirmek için aşağıdaki bileşenler gerekir.  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7.  
  
-   Windows Touch destekleyen bir dokunmatik ekran gibi bir aygıt.  
  
### <a name="terminology"></a>Terminoloji  
 Dokunma ele alınan aşağıdaki terimler kullanılır.  
  
-   **Touch** Windows 7 tarafından tanınan kullanıcı girişi türüdür. Genellikle, dokunma dokunmatik ekran üzerinde parmakları koyarak başlatılır. Cihaz yalnızca parmak'ın konumunu ve fare girdisi olarak hareket dönüştürür, dizüstü bilgisayarlarda ortak dokunmatik aygıtların dokunma desteklemeyen unutmayın.  
  
-   **Multitouch** aynı anda birden fazla noktasından oluşan dokunma değil. Windows 7 ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] multitouch destekler. Her dokunma ele alınmıştır belgelerine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kavramlar multitouch için geçerlidir.  
  
-   A **işleme** dokunma bir nesneye uygulanan fiziksel bir eylem olarak yorumlanır oluşur. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], olayları düzenleme giriş çevirisi, genişletme veya döndürme düzenleme olarak yorumlar.  
  
-   A `touch device` , dokunmatik üzerinde tek bir parmak gibi dokunma üreten bir aygıtı temsil eder.  
  
### <a name="controls-that-respond-to-touch"></a>Yanıt denetimleri  
 Aşağıdaki denetimleri, görünüm dışında kaydırılan içeriğe sahipse denetimi arasında bir parmak sürükleyerek kaydırılabileceğini.  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.DataGrid>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
 <xref:System.Windows.Controls.ScrollViewer> Tanımlar <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> ekli dokunma kaydırma etkinleştirilip etkinleştirilmediği yatay, dikey, her ikisini birden veya hiçbiri belirtmenize olanak tanıyan özellik. <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> Özelliği, kullanıcı parmak dokunmatik alanından kaldırır olduğunda ne kadar hızlı kaydırma yavaşlar belirtir. <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> Ekli özellik işleme uzaklığı çevirmek için uzaklık kaydırma oranını belirtir.  
  
### <a name="touch-events"></a>Dokunma olayları  
 Temel sınıflar <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>, ve <xref:System.Windows.ContentElement>, uygulamanızın touch yanıt verir, böylece abone olabilirsiniz olayları tanımlayın. Dokunma olayları bir nesne düzenleme dışında bir şey olarak touch uygulamanızı yorumlar olduğunda yararlıdır. Örneğin, bir veya daha fazla parmakları ile çizmek bir kullanıcı sağlayan bir uygulama olayları touch abone.  
  
 Üç tüm sınıflar benzer şekilde, bağımsız olarak tanımlayan sınıf davranır aşağıdaki olaylar tanımlayın.  
  
-   <xref:System.Windows.UIElement.TouchDown>  
  
-   <xref:System.Windows.UIElement.TouchMove>  
  
-   <xref:System.Windows.UIElement.TouchUp>  
  
-   <xref:System.Windows.UIElement.TouchEnter>  
  
-   <xref:System.Windows.UIElement.TouchLeave>  
  
-   <xref:System.Windows.UIElement.PreviewTouchDown>  
  
-   <xref:System.Windows.UIElement.PreviewTouchMove>  
  
-   <xref:System.Windows.UIElement.PreviewTouchUp>  
  
-   <xref:System.Windows.UIElement.GotTouchCapture>  
  
-   <xref:System.Windows.UIElement.LostTouchCapture>  
  
 Klavye ve fare olayları gibi yönlendirilmiş olaylar dokunma olaylardır. İle başlayan olayları `Preview` olaylar ve ile başlayan olaylar tünel `Touch` kabarcıklanma olaylardır. Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md). Bu olaylar uyguluyorsanız çağırarak göre herhangi bir öğe girişi konumunu alabilirsiniz <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> veya <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> yöntemi.  
  
 Dokunma olaylar arasındaki etkileşimi anlamak için burada bir kullanıcı bir öğe üzerinde bir parmak koyar, parmak öğesinde taşır ve parmak öğesinden kaldırır senaryoyu düşünün. Aşağıdaki çizimde (Tünel olayları kolaylık sağlamak için göz ardı edilir) kabarcıklanma olayların yürütülmesine gösterir.  
  
 ![Dokunma olayları dizisi. ] (../../../../docs/framework/wpf/advanced/media/ndp-touchevents.png "NDP_TouchEvents")  
Dokunma olayları  
  
 Aşağıdaki listede önceki çizimde olayların sırası açıklanmaktadır.  
  
1.  <xref:System.Windows.UIElement.TouchEnter> Olay olduğunda kullanıcı koyan bir parmak öğe üzerinde bir kez gerçekleşir.  
  
2.  <xref:System.Windows.UIElement.TouchDown> Olayı, bir kez oluşur.  
  
3.  <xref:System.Windows.UIElement.TouchMove> Olayı, kullanıcı öğe içindeki parmak taşınırken birden çok kez oluşur.  
  
4.  <xref:System.Windows.UIElement.TouchUp> Olay olduğunda kullanıcı kaldırır parmak öğesinden bir kez gerçekleşir.  
  
5.  <xref:System.Windows.UIElement.TouchLeave> Olayı, bir kez oluşur.  
  
 İkiden fazla parmakları kullanıldığında, olaylar için her parmak oluşur.  
  
### <a name="manipulation-events"></a>Olayları düzenleme  
 Burada bir uygulama sağlayan bir nesneyi düzenlemek bir kullanıcı durumlarda <xref:System.Windows.UIElement> sınıfı işleme olayları tanımlar. Yalnızca dokunma konumunu rapor dokunma olaylar farklı olarak, girdi nasıl yorumlanacağını olayları düzenleme bildirin. Üç tür işlemeleri, çevirisi, genişletme ve döndürme vardır. Aşağıdaki listede, işlemeleri üç tür çağrılacak açıklar.  
  
-   Bir nesne üzerinde bir parmak koyun ve parmak çeviri işleme çağırmak için dokunmatik ekran arasında taşıyın. Bu, genellikle nesne taşır.  
  
-   Bir nesne üzerinde iki parmakları koyun ve parmakları yakın birlikte veya başka bir genişletme işleme çağırmak için dışında uzağına taşıyın. Bu genellikle nesne yeniden boyutlandırır.  
  
-   Bir nesne üzerinde iki parmakları koyun ve parmakları birbiri döndürme işleme çağırmak için etrafında döndürün. Bu, genellikle nesne döndürür.  
  
 Birden fazla tür işleme aynı anda ortaya çıkabilir.  
  
 İşlemeleri için yanıt nesnelere neden olduğunda eylemsizlik olmadığı görünüyor nesnesi sahip olabilir. Bu nesnelerinizi Fiziksel dünyadaki benzetimini yapabilirsiniz. Örneğin, sabit itme varsa bir tablo arasında bir kitap bastığınızda serbest sonra taşımak yeterince kitap devam eder. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu davranış kullanıcının parmakları yayımlandıktan sonra nesne olayları düzenleme yükselterek benzetimini sağlar.  
  
 Taşıma, yeniden boyutlandırma ve nesneyi döndürme kullanıcıya sağlayan bir uygulama oluşturma hakkında daha fazla bilgi için bkz: [izlenecek yol: oluşturma ilk Touch uygulamanızı](../../../../docs/framework/wpf/advanced/walkthrough-creating-your-first-touch-application.md).  
  
 <xref:System.Windows.UIElement> Aşağıdaki işleme olayları tanımlar.  
  
-   <xref:System.Windows.UIElement.ManipulationStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationStarted>  
  
-   <xref:System.Windows.UIElement.ManipulationDelta>  
  
-   <xref:System.Windows.UIElement.ManipulationInertiaStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationCompleted>  
  
-   <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>  
  
 Varsayılan olarak, bir <xref:System.Windows.UIElement> bu işleme olayları almaz. Olayları işleme almak için bir <xref:System.Windows.UIElement>ayarlayın <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> için `true`.  
  
#### <a name="the-execution-path-of-manipulation-events"></a>İşleme olayların yürütme yolu  
 Burada bir kullanıcı "bir nesne oluşturur" bir senaryo düşünün. Kullanıcı, nesne üzerinde bir parmak koyar taşır parmak kısa bir mesafe dokunmatik arasında ve onu taşıma sırasında parmak kaldırır. Bu nesne kullanıcının parmak altında taşıyın ve kullanıcı parmak kaldırır sonra taşımak devam sonucudur.  
  
 Aşağıdaki çizimde olayları düzenleme ve her olay hakkında önemli bilgiler yürütme yolunu gösterir.  
  
 ![İşleme olayları dizisi. ] (../../../../docs/framework/wpf/advanced/media/ndp-manipulationevents.png "NDP_ManipulationEvents")  
Olayları düzenleme  
  
 Aşağıdaki listede önceki çizimde olayların sırası açıklanmaktadır.  
  
1.  <xref:System.Windows.UIElement.ManipulationStarting> Olayı, kullanıcı bir nesne üzerinde bir parmak getirdiğinde oluşur. Bunun yanı sıra, bu olay ayarlamanıza olanak tanır <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> özelliği. Sonraki olayları işleme konumunu göreli olacak <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. Olaylarda dışında <xref:System.Windows.UIElement.ManipulationStarting>, bu özellik salt okunur şekilde <xref:System.Windows.UIElement.ManipulationStarting> bu özelliği ayarlamak yalnızca bir kez bir olaydır.  
  
2.  <xref:System.Windows.UIElement.ManipulationStarted> Olay oluştuktan sonra. Bu olay kaynağı düzenleme hakkında raporlar.  
  
3.  <xref:System.Windows.UIElement.ManipulationDelta> Olayı, bir kullanıcının parmakları dokunmatik taşımasında olarak birden çok kez oluşur. <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> Özelliği <xref:System.Windows.Input.ManipulationDeltaEventArgs> sınıfı raporlar işleme taşıma, genişletme veya çeviri yorumlanır. Bir nesne düzenleme işlerin çoğunu gerçekleştirdiğiniz budur.  
  
4.  <xref:System.Windows.UIElement.ManipulationInertiaStarting> Olayı kullanıcının parmakları nesne kişiyle kaybettiğinde oluşur. Bu olay işlemeleri yavaşlama eylemsizlik sırasında belirtmenize olanak sağlar. Bu durum, seçerseniz, nesnenin farklı fiziksel boşluk veya öznitelikleri taklit edebilir kitabıdır. Örneğin, uygulamanızın Fiziksel dünyadaki öğelerini temsil eden iki nesne ve bir diğerinden daha ağır varsayalım. Açık nesne daha hızlı hızını düşürün daha ağır nesne yapabilirsiniz.  
  
5.  <xref:System.Windows.UIElement.ManipulationDelta> Olay eylemsizlik gerçekleştiği sırada birden çok kez oluşur. Bu olay kullanıcının parmakları dokunmatik arasında taşıdığınızda ve ne zaman oluştuğunu not [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eylemsizlik benzetimini yapar. Diğer bir deyişle, <xref:System.Windows.UIElement.ManipulationDelta> önce ve sonra gerçekleşir <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay. <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> Özellik raporları olup olmadığını <xref:System.Windows.UIElement.ManipulationDelta> olayı, bu özellik denetleyin ve değerini bağlı olarak farklı eylemler gerçekleştirmek için eylemsizlik sırasında oluşur.  
  
6.  <xref:System.Windows.UIElement.ManipulationCompleted> Olayı meydana işleme ve tüm eylemsizlik sona erdiğinde. Diğer bir deyişle, sonraki tüm <xref:System.Windows.UIElement.ManipulationDelta> olaylar oluşur, <xref:System.Windows.UIElement.ManipulationCompleted> olay işleme tamamlandığını göstermek için oluşur.  
  
 <xref:System.Windows.UIElement> Ayrıca tanımlar <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olay. Bu olay oluşur zaman <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> yöntemi çağrıldığında <xref:System.Windows.UIElement.ManipulationDelta> olay. <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> Olay, uygulama veya bileşenler bir nesne bir sınırına geldiğinde görsel geribildirim sağlamak etkinleştirir. Örneğin, <xref:System.Windows.Window> sınıf tanıtıcıları <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olay kenarını karşılaşıldığında biraz taşımak için penceresi neden olacak.  
  
 Çağırarak düzenlemeyi iptal edebilirsiniz <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> dışında herhangi bir işleme olayın olay değişkenlerinde yöntemi <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> olay. Çağırdığınızda <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, işleme olaylar artık oluşturulur ve fare olayları için touch oluşur. Aşağıdaki tabloda düzenlemeyi iptal zaman ve ortaya çıkan fare olayları arasındaki ilişkiyi açıklar.  
  
|İptal olay çağrılır.|Gerçekleşmiş giriş için ortaya çıkan fare olayları|  
|----------------------------------------|-----------------------------------------------------------------|  
|<xref:System.Windows.UIElement.ManipulationStarting> Ve <xref:System.Windows.UIElement.ManipulationStarted>|Fare olaylar.|  
|<xref:System.Windows.UIElement.ManipulationDelta>|Fare aşağı ve fare olaylarını taşıyın.|  
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> Ve <xref:System.Windows.UIElement.ManipulationCompleted>|Fare aşağı, fare taşıma ve fare olayları.|  
  
 Çağırırsanız unutmayın <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> işleme eylemsizlik içinde olduğunda, yöntem `false` ve giriş fare olayları oluşturmaz.  
  
### <a name="the-relationship-between-touch-and-manipulation-events"></a>Dokunma ve işleme olaylar arasındaki ilişki  
 A <xref:System.Windows.UIElement> dokunma olaylarına her zaman alabilir. Zaman <xref:System.Windows.UIElement.IsManipulationEnabled%2A> özelliği ayarlanmış `true`, <xref:System.Windows.UIElement> dokunma ve düzenleme olayları alabilirsiniz.  Varsa <xref:System.Windows.UIElement.TouchDown> olay işlenmiyor (diğer bir deyişle, <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği `false`), işleme mantığı öğesine dokunma yakalar ve olayları düzenleme oluşturur. Varsa <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği ayarlanmış `true` içinde <xref:System.Windows.UIElement.TouchDown> olay işleme mantığı olayları düzenleme oluşturmaz. Aşağıdaki çizimde dokunma olaylar ve işleme olaylar arasındaki ilişkiyi gösterir.  
  
 ![Dokunma ve düzenleme olaylar arasındaki ilişki](../../../../docs/framework/wpf/advanced/media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents")  
Dokunma ve düzenleme olayları  
  
 Aşağıdaki liste Yukarıdaki çizimde gösterilen dokunma ve düzenleme olaylar arasındaki ilişkiyi açıklar.  
  
-   İlk dokunma aygıtı oluşturduğunda bir <xref:System.Windows.UIElement.TouchDown> olayda bir <xref:System.Windows.UIElement>, işleme mantığı çağrıları <xref:System.Windows.UIElement.CaptureTouch%2A> oluşturur yöntemi <xref:System.Windows.UIElement.GotTouchCapture> olay.  
  
-   Zaman <xref:System.Windows.UIElement.GotTouchCapture> oluşur, işleme mantığı çağrıları <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> oluşturur yöntemi <xref:System.Windows.UIElement.ManipulationStarting> olay.  
  
-   Zaman <xref:System.Windows.UIElement.TouchMove> olaylar gerçekleştiğinde, işleme mantığı oluşturur <xref:System.Windows.UIElement.ManipulationDelta> önce gerçekleşen olaylara <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay.  
  
-   Son dokunduğunuzda aygıt öğesi başlatır <xref:System.Windows.UIElement.TouchUp> olay işleme mantığı oluşturur <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay.  
  
<a name="focus"></a>   
## <a name="focus"></a>Odağı  
 Odakta ait iki temel kavram vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: klavye odağı ve mantıksal odak.  
  
### <a name="keyboard-focus"></a>Klavye odağı  
 Klavye odağı klavye girişi alma öğesine başvuruyor.  Bütün Masaüstü üzerinde klavye odağı olan tek bir öğe olabilir.  İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], klavye odağı olan öğenin <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> kümesine `true`.  Statik <xref:System.Windows.Input.Keyboard> yöntemi <xref:System.Windows.Input.Keyboard.FocusedElement%2A> klavye odağı olan öğeyi döndürür.  
  
 Bir öğe olarak sekme veya gibi belirli öğelerin üzerinde fareyi tıklatarak klavye odağını elde edilebilir bir <xref:System.Windows.Controls.TextBox>.  Klavye odağı da elde edilebilir program aracılığıyla kullanarak <xref:System.Windows.Input.Keyboard.Focus%2A> yöntemi <xref:System.Windows.Input.Keyboard> sınıfı.  <xref:System.Windows.Input.Keyboard.Focus%2A> Belirtilen öğe klavye odağı vermeye çalışır.  Tarafından döndürülen öğe <xref:System.Windows.Input.Keyboard.Focus%2A> klavye odağı olan öğedir.  
  
 Bir öğenin klavye odağını alabilmesi sırayla <xref:System.Windows.UIElement.Focusable%2A> özelliği ve <xref:System.Windows.UIElement.IsVisible%2A> özellikleri ayarlanmalıdır **doğru**.  Gibi bazı sınıflarda <xref:System.Windows.Controls.Panel>, sahip <xref:System.Windows.UIElement.Focusable%2A> kümesine `false` varsayılan olarak; bu nedenle, bu özelliği ayarlamak için yaptığınız `true` odağı elde edebilmek için bu öğe istiyorsanız.  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Input.Keyboard.Focus%2A> üzerinde klavye odağını ayarlamak için bir <xref:System.Windows.Controls.Button>.  Bir uygulamada ilk odağı ayarlamak için önerilen bir yerdir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 Klavye odağı hakkında daha fazla bilgi için bkz: [odak genel bakış](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
### <a name="logical-focus"></a>Mantıksal odak  
 Mantıksal odak başvurduğu <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> odak kapsamında.  Bir uygulamada mantıksal odağa sahip birden çok öğe olabilir, ancak Ayrıca belirli odak kapsamda mantıksal odağa sahip bir öğe yalnızca olabilir.  
  
 Odak kapsamı izler bir kapsayıcı öğedir <xref:System.Windows.Input.FocusManager.FocusedElement%2A> kendi kapsamı içinde.  Odağı odak kapsamına ayrıldığında, odaklanan öğe klavye odağını kaybeder, ancak mantıksal odağını korur.  Odağı odak kapsamına döndüğünde odaklanılan öğeyi klavye odağını edinir.  Bu klavye odağını arasında birden çok odak kapsamı değiştirilmesine olanak tanır ancak odak döndüğünde odak kapsamında odaklanılan öğeyi odaklanılan öğeyi kalmasını oluşturmasını sağlar.  
  
 Bir öğenin odak kapsamına dönüştürülebilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ayarlayarak <xref:System.Windows.Input.FocusManager> özelliği eklenmiş <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> için `true`, ya da ekli özellik kullanarak ayarlayarak kodda <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> yöntemi.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.StackPanel> ayarlayarak odak kapsamına <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> özelliği eklenmiş.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 Sınıfları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsayılan olarak odak kapsamı olan olan <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, ve <xref:System.Windows.Controls.ContextMenu>.  
  
 Klavye odağı olan bir öğeyi da ait odak kapsamı için mantıksal odağa sahip olur; Bu nedenle, bir öğesiyle odak ayarı <xref:System.Windows.Input.Keyboard.Focus%2A> yöntemi <xref:System.Windows.Input.Keyboard> sınıf veya temel öğe sınıfları öğeye klavye odağı ve mantıksal odak vermeyi deneyecek.  
  
 Odağı kapsamında odaklanılan öğeyi belirlemek için <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Odağı kapsamı için odaklı öğeyi değiştirmek için kullanmak <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.  
  
 Mantıksal odak hakkında daha fazla bilgi için bkz: [odak genel bakış](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
<a name="mouse_position"></a>   
## <a name="mouse-position"></a>Fare konumu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Giriş [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] koordinat ilgili yararlı bilgiler sağlar.  Örneğin, koordine `(0,0)` sol üst koordinat, ancak hangi ağacını öğesinde sol üst? Giriş hedef öğeyi? Öğe, olay işleyicisi bağlı? Veya başka bir şey mi? Karışıklığı önlemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] fareyi elde koordinatları ile çalışırken, çerçeve başvuru belirtmenizi gerektirir. <xref:System.Windows.Input.Mouse.GetPosition%2A> Yöntemi belirtilen öğenin göreli fare işaretçisini koordinatını döndürür.  
  
<a name="mouse_capture"></a>   
## <a name="mouse-capture"></a>Fare yakalama  
 Fare aygıtları özellikle fare yakalama bilinen bir kalıcı karakteristiğini tutun. Fare yakalama sürükle ve bırak işlemi başlatıldığında, böylece nominal ekran ilgili diğer işlemleri fare işaretçisini konumunu mutlaka gerçekleşmez geçici bir giriş durumunu korumak için kullanılır. Sürükleme sırasında kullanıcıya sürükle ve fare yakalama Sürükle kaynağa göre kilitli durumdayken kılan çoğu fare üzerinde yardımlar uygunsuz bırak, iptal etme olmadan tıklayın olamaz. Giriş sistemi sunan [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fare yakalama durumunu belirleyebilir yanı [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , belirli bir öğenin fare yakalama zorlayabilir veya fare yakalama durumunu temizleyin. Sürükle ve bırak işlemleri hakkında daha fazla bilgi için bkz: [sürükle ve bırak genel bakış](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md).  
  
<a name="commands"></a>   
## <a name="commands"></a>Komutlar  
 Komutları cihaz giriş'den fazla anlamsal düzeyde giriş işlenmesini sağlar.  Komutlardır basit yönergeleri gibi `Cut`, `Copy`, `Paste`, veya `Open`.  Komutları, komut mantığınızı merkezileştirme için faydalıdır.  Aynı komutu erişilen bir <xref:System.Windows.Controls.Menu>, bir <xref:System.Windows.Controls.ToolBar>, veya bir klavye kısayolu aracılığıyla. Komut ayrıca komutu kullanılamaz duruma geldiğinde denetimleri devre dışı bırakmak için bir mekanizma sağlar.  
  
 <xref:System.Windows.Input.RoutedCommand> olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uyarlamasını <xref:System.Windows.Input.ICommand>.  Zaman bir <xref:System.Windows.Input.RoutedCommand> yürütüldüğünde, bir <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve bir <xref:System.Windows.Input.CommandManager.Executed> olay hangi tünel ve kabarcık öğe ağacı üzerinden gibi diğer giriş komut hedefinde tetiklenir.  Komut hedefi ayarlanmazsa, klavye odağını öğeyle komut hedefi olacaktır.  Komutu gerçekleştirir mantığı bağlı bir <xref:System.Windows.Input.CommandBinding>.  Zaman bir <xref:System.Windows.Input.CommandManager.Executed> olay ulaştığında bir <xref:System.Windows.Input.CommandBinding> belirli bu komut için <xref:System.Windows.Input.ExecutedRoutedEventHandler> üzerinde <xref:System.Windows.Input.CommandBinding> olarak adlandırılır.  Bu işleyici komutu eylemi gerçekleştirir.  
  
 Komut verme hakkında daha fazla bilgi için bkz: [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşan yaygın komutları kitaplığını sağlar <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, ve <xref:System.Windows.Documents.EditingCommands>, veya kendi tanımlayabilirsiniz.  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir bir <xref:System.Windows.Controls.MenuItem> böylece tıklandığında çağırma <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutunu <xref:System.Windows.Controls.TextBox>olduğunu varsayarak <xref:System.Windows.Controls.TextBox> klavye odağını sahiptir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
 Komutlar hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="the_input_system_and_base_elements"></a>   
## <a name="the-input-system-and-base-elements"></a>Giriş sistemi ve temel öğeler  
 Giriş tarafından tanımlanan ekli olaylar gibi olayların <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, ve <xref:System.Windows.Input.Stylus> sınıfları giriş sistem tarafından gerçekleştirilen ve İsabet görsel ağaç çalışma zamanında sınama temel nesne modeli içindeki belirli bir konuma eklenmiş.  
  
 Olayların her biri, <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, ve <xref:System.Windows.Input.Stylus> ekli olay ayrıca temel öğe sınıfları tarafından yeniden sunulan olarak tanımlayın <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> yeni yönlendirilmiş olay olarak. Yönlendirilmiş temel öğe olayları özgün ekli olay işleme ve olay verileri yeniden kullanma sınıfları tarafından oluşturulur.  
  
 Giriş olayı temel öğe giriş olayı uygulaması aracılığıyla belirli source öğesi ile ilişkili olduğunda, mantıksal ve görsel ağaç nesnelerinin bir birleşimini temel alır ve tarafından işlenen bir olay yolu kalanı üzerinden yönlendirilebilir uygulama kodu.  Genellikle, yönlendirilmiş olaylar kullanarak bu aygıtla ilgili girdi olayları işlemek daha kullanışlı <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement>, daha sezgisel olay işleyicisi sözdiziminde hem kullanabileceğinizden [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod. Bunun yerine işlem başlatılan ekli olayını işlemek seçebilir, ancak çeşitli sorunlar yüz: ekli olay temel öğe sınıfı işleyerek işlenmiş işaretlenmiş olabilir ve doğru olay sözdizimi yerine erişimci yöntemleri sırayla kullanmanız gerekir ekli olaylar için işleyiciler eklemek için.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Sırada ne var?  
 Şimdi girişinde işlemek için çeşitli teknikler vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Giriş olayları ve tarafından kullanılan yönlendirilmiş olay mekanizmaları çeşitli türlerde geliştirilmiş bir anlama sahip olmalıdır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Ek kaynaklar kullanılabilir biçimde açıklayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework öğeleri ve daha ayrıntılı olarak olay yönlendirme. Daha fazla bilgi için şu genel bakışlara bakın [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md), [odak genel bakış](../../../../docs/framework/wpf/advanced/focus-overview.md), [temel öğeleri genel bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md), [WPFağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md), ve [olaylara genel bakış yönlendirilen](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Odağa Genel Bakış](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Temel Öğelere Genel Bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Özellikler](../../../../docs/framework/wpf/advanced/properties-wpf.md)
