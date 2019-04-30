---
title: Odağa Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 72b866d714e6a77020bdb74843c3aaa0ba0c3278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703432"
---
# <a name="focus-overview"></a>Odağa Genel Bakış
İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odakla ilgili iki ana kavram vardır: klavye odağı ve mantıksal odak.  Klavye odağı klavye girişini alır öğeye başvuruyor ve odaklı bir odak kapsam içindeki öğeye mantıksal Odaklanıldığında başvurur.  Bu kavramlar, bu genel bakışta ayrıntılı ele alınmıştır.  Bu kavramlar farkını anlama, birden çok bölgede odak burada elde edilebilir sahip karmaşık uygulamalar oluşturmak için önemlidir.  
  
 Odak yönetimine katılan başlıca sınıflardır <xref:System.Windows.Input.Keyboard> sınıfı <xref:System.Windows.Input.FocusManager> sınıfı ve temel öğe sınıfları, gibi <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement>.  Temel öğeler hakkında daha fazla bilgi için bkz. [temel öğelere genel bakış](base-elements-overview.md).  
  
 <xref:System.Windows.Input.Keyboard> Sınıfı öncelikle klavye odağı ile ilgili ve <xref:System.Windows.Input.FocusManager> öncelikle mantıksal odak ile ilgili olan ancak bu mutlak bir ayrım değildir.  Klavye girintisine sahip bir öğe mantıksal odağı da gerekir, ancak mantıksal odağı olan bir öğeyi klavye odağı sahip değil.  Kullandığınızda bu açıktır <xref:System.Windows.Input.Keyboard> klavye odağı olan öğe ayarlanacak sınıfı ayrıca öğede mantıksal Odaklanıldığında ayarlar.  

<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>Klavye odağı  
 Klavye odağı, şu anda klavye girdisi alıyor öğesine başvurur.  Klavye girintisine sahip yalnızca bir öğe tüm masaüstü olabilir.  İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], klavye girintisine sahip öğenin <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> kümesine `true`.  Statik özelliği <xref:System.Windows.Input.Keyboard.FocusedElement%2A> üzerinde <xref:System.Windows.Input.Keyboard> sınıfı, şu anda klavye girintisine sahip öğeyi alır.  
  
 Klavye odağı almak bir öğe için sırayla <xref:System.Windows.UIElement.Focusable%2A> ve <xref:System.Windows.UIElement.IsVisible%2A> temel öğeler özellikleri ayarlanmalıdır `true`.  Gibi bazı sınıflar <xref:System.Windows.Controls.Panel> temel sınıfı <xref:System.Windows.UIElement.Focusable%2A> kümesine `false` tarafından varsayılan; bu nedenle, ayarlamalısınız <xref:System.Windows.UIElement.Focusable%2A> için `true` klavye odağı alabilmesi için bir böyle bir öğe istiyorsanız.  
  
 Klavye odağı ile kullanıcı etkileşimi aracılığıyla edinilebilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bir öğe için sekme veya belirli öğeler üzerinde fareyle tıklamak gibi.  Klavye odağı da elde edilebilir program aracılığıyla kullanarak <xref:System.Windows.Input.Keyboard.Focus%2A> metodunda <xref:System.Windows.Input.Keyboard> sınıfı.  <xref:System.Windows.Input.Keyboard.Focus%2A> Yöntemi belirtilen öğe klavye odaklanmak dener.  Döndürülen öğe eski veya yeni nesne blok isteği odaklanmak, istenenden farklı bir öğe olabilecek klavye girintisine sahip bir öğedir.  
  
 Aşağıdaki örnekte <xref:System.Windows.Input.Keyboard.Focus%2A> klavye odağı ayarlamak için yöntemi bir <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A> Temel öğe sınıfları özelliği, öğe klavye girintisine sahip olup olmadığını belirten bir değer alır.  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> Temel öğe sınıfları özelliği, öğe veya görsel alt öğelerinden biri klavye girintisine sahip olup olmadığını belirten bir değer alır.  
  
 Uygulama başlangıcında ilk odak ayarlama, öğenin odak alıp uygulama tarafından yüklenen ilk penceresinin görsel ağaç olmalıdır ve öğe olmalıdır <xref:System.Windows.UIElement.Focusable%2A> ve <xref:System.Windows.UIElement.IsVisible%2A> kümesine `true`.  İlk odağı ayarlamak için önerilen konum <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.  A <xref:System.Windows.Threading.Dispatcher> geri çağırma de kullanılabilir çağırarak <xref:System.Windows.Threading.Dispatcher.Invoke%2A> veya <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>.  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>Mantıksal odak  
 Mantıksal odak başvurduğu <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> odak kapsamında.  Odak kapsamdır izler bir öğe <xref:System.Windows.Input.FocusManager.FocusedElement%2A> kendi kapsamı içinde.  Klavye odağı odak kapsam dışına çıktığında, odaklanılan öğeyi klavye odağı kaybeder ancak mantıksal odağını korur.  Klavye odağı odak kapsamına geri döndüğünde, odaklanılan öğeyi klavye odağı elde edersiniz.  Bu, klavye odağı arasında birden çok odak kapsam değiştirilmesine izin verir ancak odak odak kapsamına döndürdüğünde odak kapsamdaki odaklanılan öğeyi klavye odağını yeniden gelmesini sağlar.  
  
 Uygulamada mantıksal odağa sahip birden çok öğe olabilir, ancak ayrıca mantıksal Odaklanıldığında belirli odak kapsamına sahip bir öğe yalnızca olabilir.  
  
 Klavye girintisine sahip bir öğe mantıksal odağı ait odak kapsam için vardır.  
  
 Öğenin odak kapsamda dönüştürülebilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ayarlayarak <xref:System.Windows.Input.FocusManager> ekli özellik <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> için `true`.  Kod içinde bir öğenin odak kapsamına çağırarak kapatılabilir <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.StackPanel> ayarlayarak bir odak kapsama <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> ekli özellik.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> Odak kapsamını belirtilen öğeyi döndürür.  
  
 Sınıflar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odak kapsamı varsayılan olarak hangilerinin <xref:System.Windows.Window>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.ToolBar>, ve <xref:System.Windows.Controls.ContextMenu>.  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> odaklanan öğeyi belirtilen odak kapsamını alır.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> odaklanan öğeyi belirtilen odak kapsamındaki ayarlar.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> genellikle ilk odaklanan öğeyi ayarlamak için kullanılır.  
  
 Aşağıdaki örnek, odağı kapsamında odaklanan öğeyi ayarlar ve odak kapsamın odaklanılan öğeyi alır.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>Klavye ile Gezinme  
 <xref:System.Windows.Input.KeyboardNavigation> Sınıftır Gezinti anahtarlarından birini basıldığında varsayılan klavye odağı Gezinti uygulamak için sorumlu.  Gezinti tuşları şunlardır: SEKME, SHIFT + TAB, CTRL + SEKME, CTRL + SHIFT + SEKME, UPARROW, DARALTILDI, sol ok ve sağ ok tuşları.  
  
 Ekli ayarlayarak bir gezinti kapsayıcı gezinme davranışını değiştirilebilir <xref:System.Windows.Input.KeyboardNavigation> özellikleri <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>, <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>, ve <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>.  Bu özellikler, türlerinin <xref:System.Windows.Input.KeyboardNavigationMode> ve olası değerleri <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, <xref:System.Windows.Input.KeyboardNavigationMode.Local>, <xref:System.Windows.Input.KeyboardNavigationMode.Contained>, <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>, <xref:System.Windows.Input.KeyboardNavigationMode.Once>, ve <xref:System.Windows.Input.KeyboardNavigationMode.None>.  Varsayılan değer <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, yani öğe Gezinti kapsayıcı değil.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Menu> çeşitli <xref:System.Windows.Controls.MenuItem> nesneleri.  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> Ekli özelliği <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> üzerinde <xref:System.Windows.Controls.Menu>.  Odağı tab tuşuyla içinde değiştirildiğinde <xref:System.Windows.Controls.Menu>, odağı her öğeyi Taşı ve son öğe ulaşıldığında odak ilk öğeye döndürür.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>Odak gezinme  
 Ek [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] çalışmak için odağı olan <xref:System.Windows.UIElement.MoveFocus%2A> ve <xref:System.Windows.UIElement.PredictFocus%2A>.  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> sonraki öğeye uygulamada odak değiştirir.  A <xref:System.Windows.Input.TraversalRequest> yönünü belirtmek için kullanılır.   <xref:System.Windows.Input.FocusNavigationDirection> Geçirilen <xref:System.Windows.UIElement.MoveFocus%2A> farklı yönleri odağı taşınabilir, gibi belirtir <xref:System.Windows.Input.FocusNavigationDirection.First>, <xref:System.Windows.Input.FocusNavigationDirection.Last>, <xref:System.Windows.Input.FocusNavigationDirection.Up> ve <xref:System.Windows.Input.FocusNavigationDirection.Down>.  
  
 Aşağıdaki örnekte <xref:System.Windows.FrameworkElement.MoveFocus%2A> odaklanan öğeyi değiştirmek için.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> Odak değiştirilmesi gerekiyorsa odak alacak bir nesne döndürür.  Şu anda yalnızca <xref:System.Windows.Input.FocusNavigationDirection.Up>, <xref:System.Windows.Input.FocusNavigationDirection.Down>, <xref:System.Windows.Input.FocusNavigationDirection.Left>, ve <xref:System.Windows.Input.FocusNavigationDirection.Right> tarafından desteklenen <xref:System.Windows.FrameworkElement.PredictFocus%2A>.  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>Odak olayları  
 Klavye odağı ile ilgili olaylar <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>, <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> ve <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>, <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>.  Ekli olaylar tanımlanır olayları <xref:System.Windows.Input.Keyboard> sınıfı, ancak temel öğe sınıflarda eşdeğer yönlendirilmiş olaylar olarak daha kolay erişilebilir.  Olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> öğe klavye odağı aldığında oluşur.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> öğe, klavye odağından çıktığında oluşur.  Varsa <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> olay veya <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> olayı işlenir ve <xref:System.Windows.RoutedEventArgs.Handled%2A> ayarlanır `true`, odağı değişmez.  
  
 Aşağıdaki örnek iliştirir <xref:System.Windows.UIElement.GotKeyboardFocus> ve <xref:System.Windows.UIElement.LostKeyboardFocus> olay işleyicileri için bir <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Zaman <xref:System.Windows.Controls.TextBox> klavye odağını aldığında <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.TextBox> değiştirilir <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Zaman <xref:System.Windows.Controls.TextBox> klavye odağından <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.TextBox> beyaz olarak değiştirilir.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Mantıksal odak ile ilgili olaylar <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus>.  Bu olaylar üzerinde tanımlanan <xref:System.Windows.Input.FocusManager> ekli olaylar olarak ancak <xref:System.Windows.Input.FocusManager> CLR olay sarmalayıcıları kullanıma sunmuyor.  <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> daha rahat bu olayları gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Girişe Genel Bakış](input-overview.md)
- [Temel Öğelere Genel Bakış](base-elements-overview.md)
