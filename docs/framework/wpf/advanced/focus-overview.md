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
ms.openlocfilehash: de788ec3f0628ff2f7c422c76c73ff7985424113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186662"
---
# <a name="focus-overview"></a>Odağa Genel Bakış
Burada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odaklama ile ilgili iki ana kavram vardır: klavye odak lama ve mantıksal odak.  Klavye odağı, klavye girişi alan öğeyi ifade eder ve mantıksal odaklama, odak noktası olan bir odak kapsamındaki öğeyi ifade eder.  Bu kavramlar bu genel bakışta ayrıntılı olarak ele alınmıştır.  Bu kavramlararasındaki farkı anlamak, odak noktasının elde edilebildiği birden çok bölgeye sahip karmaşık uygulamalar oluşturmak için önemlidir.  
  
 Odak yönetimine katılan ana sınıflar <xref:System.Windows.Input.Keyboard> sınıf, <xref:System.Windows.Input.FocusManager> sınıf ve temel öğe sınıflarıdır. <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement>  Temel öğeler hakkında daha fazla bilgi için [Temel Öğelere Genel Bakış'a](base-elements-overview.md)bakın.  
  
 Sınıf <xref:System.Windows.Input.Keyboard> öncelikle klavye odak ile <xref:System.Windows.Input.FocusManager> ilgilidir ve öncelikle mantıksal odak ile ilgilidir, ama bu mutlak bir ayrım değildir.  Klavye odağı olan bir öğe de mantıksal odak lama özelliğine sahip olur, ancak mantıksal odaklama olan bir öğenin mutlaka klavye odağı olması gerekmez.  Bu, <xref:System.Windows.Input.Keyboard> klavye odağı olan öğeyi ayarlamak için sınıfı kullandığınızda belirgindir, çünkü bu öğenin mantıksal odağı da belirler.  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>Klavye Odağı  
 Klavye odağı, şu anda klavye girişi alan öğeyi ifade eder.  Tüm masaüstünde klavye odağı olan tek bir öğe olabilir.  Içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], klavye odak noktası <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> olan `true`öğe .  Sınıftaki <xref:System.Windows.Input.Keyboard> <xref:System.Windows.Input.Keyboard.FocusedElement%2A> statik özellik, şu anda klavye odağı olan öğeyi alır.  
  
 Bir öğenin klavye odağı edinebilmesi <xref:System.Windows.UIElement.Focusable%2A> <xref:System.Windows.UIElement.IsVisible%2A> için, temel öğelerdeki ve `true`özelliklerinin .  <xref:System.Windows.Controls.Panel> Taban sınıf gibi bazı sınıflar varsayılan olarak ayarlanmıştır; <xref:System.Windows.UIElement.Focusable%2A> `false` bu nedenle, <xref:System.Windows.UIElement.Focusable%2A> böyle `true` bir öğeklavye odak elde edebilmek için istiyorsanız ayarlamak gerekir.  
  
 Klavye [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]odağı, kullanıcı etkileşimi yoluyla, bir öğeyi sekme veya belirli öğeler üzerinde fareyi tıklatma gibi elde edilebilir.  Klavye odağı da <xref:System.Windows.Input.Keyboard.Focus%2A> <xref:System.Windows.Input.Keyboard> programlı sınıf yöntemi kullanılarak elde edilebilir.  Yöntem, <xref:System.Windows.Input.Keyboard.Focus%2A> belirtilen öğeklavye odağı vermeye çalışır.  Döndürülen öğe, eski veya yeni odak nesnesi isteği engelliyorsa istenenden farklı bir öğe olabilecek klavye odağı olan öğedir.  
  
 Aşağıdaki örnekte <xref:System.Windows.Input.Keyboard.Focus%2A> klavye odağı ayarlamak için <xref:System.Windows.Controls.Button>yöntem kullanır .  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 Temel <xref:System.Windows.UIElement.IsKeyboardFocused%2A> öğe sınıflarında özellik öğe klavye odak olup olmadığını gösteren bir değer alır.  Temel <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> öğe sınıflarında özellik, öğenin veya görsel alt öğelerinden herhangi birinin klavye odağına sahip olup olmadığını gösteren bir değer alır.  
  
 Uygulama başlangıcında ilk odaklama yı ayarlarken, odaklanacak öğe uygulama tarafından yüklenen ilk pencerenin görsel <xref:System.Windows.UIElement.Focusable%2A> ağacında `true`olmalı ve öğe <xref:System.Windows.UIElement.IsVisible%2A> .  İlk odak ayarlamak için önerilen <xref:System.Windows.FrameworkElement.Loaded> yer olay işleyicisi içindedir.  Geri <xref:System.Windows.Threading.Dispatcher> arama da arayarak <xref:System.Windows.Threading.Dispatcher.Invoke%2A> veya <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>.  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>Mantıksal Odak  
 Mantıksal odak bir <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> odak kapsamı anlamına gelir.  Odak kapsamı, kapsamının <xref:System.Windows.Input.FocusManager.FocusedElement%2A> kapsamını izleyen bir öğedir.  Klavye odağı bir odak kapsamı bıraktığında, odaklanmış öğe klavye odağı kaybeder, ancak mantıksal odak korur.  Klavye odağı odak kapsamına döndüğünde, odaklanmış öğe klavye odağı elde edecektir.  Bu, klavye odağının birden çok odak kapsamı arasında değiştirilmesine olanak sağlar, ancak odak kapsamındaki odaklanmış öğenin odak kapsamına döndüğünde klavye odağının yeniden kazanmasını sağlar.  
  
 Bir uygulamada mantıksal odak noktası olan birden çok öğe olabilir, ancak belirli bir odaklama kapsamında mantıksal odaklama olan yalnızca bir öğe olabilir.  
  
 Klavye odağı olan bir öğe, ait olduğu odak kapsamı için mantıksal odak vardır.  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Bir <xref:System.Windows.Input.FocusManager> öğe, ekli özelliği <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> ' ne `true`ayarlayarak bir odak kapsamına dönüştürülebilir.  Kodda, bir öğe çağırılarak <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>odak kapsamına dönüştürülebilir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> ekli özelliği ayarlayarak bir odak kapsamına ayapar.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>belirtilen öğenin odak kapsamını döndürür.  
  
 Varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olarak odak kapsamları olan <xref:System.Windows.Window> <xref:System.Windows.Controls.MenuItem>sınıflar <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.ContextMenu>, ve .  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>belirtilen odak kapsamı için odaklanmış öğeyi alır.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>belirtilen odak kapsamındaki odaklanmış öğeyi ayarlar.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>genellikle ilk odaklanmış öğeyi ayarlamak için kullanılır.  
  
 Aşağıdaki örnek, odaklanmış öğeyi bir odak kapsamı üzerinde ayarlar ve odak kapsamının odaklanmış öğesini alır.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>Klavye ile Gezinme  
 Sınıf, <xref:System.Windows.Input.KeyboardNavigation> gezinti tuşlarından birine basıldığında varsayılan klavye odak gezintisini uygulamaktan sorumludur.  Navigasyon tuşları şunlardır: TAB, SHIFT+TAB, CTRL+TAB, CTRL+SHIFT+TAB, UPARROW, DOWNARROW, LEFTARROW ve RIGHTARROW tuşları.  
  
 Bir gezinti kapsayıcısının gezinti davranışı ekli <xref:System.Windows.Input.KeyboardNavigation> özellikleri <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>ayarlayarak <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>değiştirilebilir <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>, ve .  Bu özellikler türü <xref:System.Windows.Input.KeyboardNavigationMode> ndedir ve <xref:System.Windows.Input.KeyboardNavigationMode.Continue> <xref:System.Windows.Input.KeyboardNavigationMode.Local>olası <xref:System.Windows.Input.KeyboardNavigationMode.Contained> <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>değerler <xref:System.Windows.Input.KeyboardNavigationMode.Once>, <xref:System.Windows.Input.KeyboardNavigationMode.None>, , , ve .  Varsayılan değer, <xref:System.Windows.Input.KeyboardNavigationMode.Continue>öğenin bir gezinti kapsayıcısı olmadığı anlamına gelir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Menu> dizi <xref:System.Windows.Controls.MenuItem> nesneyle a oluşturur.  Ekli <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> özellik üzerinde <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Controls.Menu>ayarlanır.  Odak sekmesi tuşu kullanılarak <xref:System.Windows.Controls.Menu>değiştirildiğinde, odak her öğeden hareket edecek ve son öğeye ulaşıldığında odak ilk öğeye geri dönecektir.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>Odakta Programlı Gezinme  
 Ek API odak ile <xref:System.Windows.UIElement.MoveFocus%2A> <xref:System.Windows.UIElement.PredictFocus%2A>çalışmak ve .  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>değiştirir uygulamadaki bir sonraki öğeye odaklanır.  A <xref:System.Windows.Input.TraversalRequest> yönünü belirtmek için kullanılır.   <xref:System.Windows.Input.FocusNavigationDirection> Geçirilen <xref:System.Windows.UIElement.MoveFocus%2A> farklı yönodak belirtebilir, <xref:System.Windows.Input.FocusNavigationDirection.First>gibi <xref:System.Windows.Input.FocusNavigationDirection.Last>, <xref:System.Windows.Input.FocusNavigationDirection.Up> , ve <xref:System.Windows.Input.FocusNavigationDirection.Down>.  
  
 Aşağıdaki örnek, <xref:System.Windows.FrameworkElement.MoveFocus%2A> odaklanmış öğeyi değiştirmek için kullanır.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>odak değiştirilecek olsaydı odak alacak nesneyi döndürür.  Şu anda, <xref:System.Windows.Input.FocusNavigationDirection.Left>sadece <xref:System.Windows.Input.FocusNavigationDirection.Right> <xref:System.Windows.Input.FocusNavigationDirection.Up>, <xref:System.Windows.Input.FocusNavigationDirection.Down>, <xref:System.Windows.FrameworkElement.PredictFocus%2A>, ve tarafından desteklenir .  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>Odak Etkinlikleri  
 Klavye odağı ile ilgili <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> olaylar <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>, ve , .  Olaylar <xref:System.Windows.Input.Keyboard> sınıftaekli olaylar olarak tanımlanır, ancak temel öğe sınıflarında eşdeğer yönlendirilmiş olaylar olarak daha kolay erişilebilir.  Olaylar hakkında daha fazla bilgi için [Yönlendirilmiş Olaylara Genel Bakış'a](routed-events-overview.md)bakın.  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>öğe klavye odağı elde ettiğinde yükseltilir.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>öğe klavye odağı kaybettiğinde yükseltilir.  <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> Olay veya <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> olay işlenir <xref:System.Windows.RoutedEventArgs.Handled%2A> ve `true`ayarlanırsa, odak değişmez.  
  
 Aşağıdaki örnek <xref:System.Windows.UIElement.GotKeyboardFocus> <xref:System.Windows.UIElement.LostKeyboardFocus> bir <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Klavye <xref:System.Windows.Controls.TextBox> odağı elde edildiğinde, <xref:System.Windows.Controls.Control.Background%2A> klavyenin <xref:System.Windows.Controls.TextBox> özelliği <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Klavye <xref:System.Windows.Controls.TextBox> odağı kaybedildiğinde, <xref:System.Windows.Controls.Control.Background%2A> klavyenin <xref:System.Windows.Controls.TextBox> özelliği beyaza döner.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Mantıksal odak ile ilgili <xref:System.Windows.UIElement.GotFocus> <xref:System.Windows.UIElement.LostFocus>olaylar ve .  Bu olaylar ekli <xref:System.Windows.Input.FocusManager> olaylar olarak tanımlanır, <xref:System.Windows.Input.FocusManager> ancak CLR olay sarmalayıcıları ortaya çıkarmaz.  <xref:System.Windows.UIElement>ve <xref:System.Windows.ContentElement> bu olayları daha rahat bir şekilde ortaya çıkarmak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Girişe Genel Bakış](input-overview.md)
- [Temel Öğelere Genel Bakış](base-elements-overview.md)
