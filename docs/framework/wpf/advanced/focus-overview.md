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
ms.openlocfilehash: 620839a0060469604d0affa6637c3cafac0f62c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548116"
---
# <a name="focus-overview"></a>Odağa Genel Bakış
İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odakla ilgili iki ana kavram vardır: klavye odağı ve mantıksal odak.  Klavye odağı klavye girişi alan öğesiyle ve mantıksal odak odaklanmış bir odak kapsamında öğesine başvuruyor.  Bu kavramlar bu genel bakış içindeki ayrıntısı ele alınmıştır.  Bu kavramlar farkı anlama odak burada alınabilir birden çok bölgeye sahip karmaşık uygulamalar oluşturmak için önemlidir.  
  
 Odak yönetimine katılan ana sınıflar <xref:System.Windows.Input.Keyboard> sınıfı, <xref:System.Windows.Input.FocusManager> sınıfı ve temel öğe sınıfları, gibi <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement>.  Temel öğeler hakkında daha fazla bilgi için bkz: [temel öğeleri genel bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md).  
  
 <xref:System.Windows.Input.Keyboard> Sınıfı öncelikle klavye odağını ile ilgilenir ve <xref:System.Windows.Input.FocusManager> öncelikle mantıksal odak ile ilgili olan ancak bu mutlak bir ayrım değildir.  Klavye odağı olan bir öğeyi mantıksal odağa sahip, ancak mantıksal odağa sahip bir öğe klavye odağını sahip değil.  Kullandığınızda bu açıktır <xref:System.Windows.Input.Keyboard> klavye odağı olan öğesini ayarlamak için sınıf öğede ayrıca mantıksal odak ayarlar.  
  

  
<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>Klavye odağı  
 Klavye odağı klavye girişi şu anda alıyor öğesine başvuruyor.  Bütün Masaüstü üzerinde klavye odağı olan tek bir öğe olabilir.  İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], klavye odağı olan öğenin <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> kümesine `true`.  Statik özelliği <xref:System.Windows.Input.Keyboard.FocusedElement%2A> üzerinde <xref:System.Windows.Input.Keyboard> sınıfı klavye odağı olan öğeyi alır.  
  
 Bir öğenin klavye odağını alabilmesi sırayla <xref:System.Windows.UIElement.Focusable%2A> ve <xref:System.Windows.UIElement.IsVisible%2A> temel öğeler özellikleri ayarlanmalıdır `true`.  Gibi bazı sınıflarda <xref:System.Windows.Controls.Panel> temel sınıfı <xref:System.Windows.UIElement.Focusable%2A> kümesine `false` varsayılan olarak; bu nedenle, ayarlamalısınız <xref:System.Windows.UIElement.Focusable%2A> için `true` klavye odağını elde edebilmek için bir tür öğe istiyorsanız.  
  
 Klavye odağı aracılığıyla elde edilebilir ile kullanıcı etkileşimi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bir öğe olarak sekme veya belirli öğelerin üzerinde fareyi tıklatarak gibi.  Klavye odağı da elde edilebilir program aracılığıyla kullanarak <xref:System.Windows.Input.Keyboard.Focus%2A> yöntemi <xref:System.Windows.Input.Keyboard> sınıfı.  <xref:System.Windows.Input.Keyboard.Focus%2A> Yöntemi, belirtilen öğeye klavye odağı vermeye çalışır.  Döndürülen öğe eski veya Yeni Nesne bloğunda istek odaklanmanıza, istenenden farklı bir öğe olabilir klavye odağı olan öğedir.  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Input.Keyboard.Focus%2A> klavye odağını ayarlamak için yöntemini bir <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A> Temel öğe sınıfları özelliği öğe klavye odağını olup olmadığını gösteren bir değeri alır.  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> Temel öğe sınıfları özelliği öğe veya herhangi bir görsel alt öğeleri klavye odağını olup olmadığını gösteren bir değeri alır.  
  
 İlk odağı uygulama başlangıcında ayarlarken, odak alacak öğe uygulama tarafından yüklenen ilk pencerenin görsel ağaç olmalıdır ve öğe olmalı <xref:System.Windows.UIElement.Focusable%2A> ve <xref:System.Windows.UIElement.IsVisible%2A> kümesine `true`.  İlk odağı ayarlamak için önerilen bir yerdir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.  A <xref:System.Windows.Threading.Dispatcher> geri çağırma de kullanılabilir çağırarak <xref:System.Windows.Threading.Dispatcher.Invoke%2A> veya <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>.  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>Mantıksal odak  
 Mantıksal odak başvurduğu <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> odak kapsamında.  Odak kapsamı izler bir öğedir <xref:System.Windows.Input.FocusManager.FocusedElement%2A> kendi kapsamı içinde.  Klavye odağı odak kapsamına ayrıldığında, odaklanan öğe klavye odağını kaybeder, ancak mantıksal odağını korur.  Klavye odağı odak kapsamına döndüğünde odaklanılan öğeyi klavye odağını edinir.  Bu klavye odağını arasında birden çok odak kapsamı değiştirilmesine izin verir, ancak odak odak kapsamına döndüğünde odak kapsamını odaklanan öğesinde klavye odağını yeniden kazanabilmesi sağlar.  
  
 Bir uygulamada mantıksal odağa sahip birden çok öğe olabilir, ancak Ayrıca belirli odak kapsamda mantıksal odağa sahip bir öğe yalnızca olabilir.  
  
 Klavye odağı olan bir öğeyi ait odak kapsamı için mantıksal odağa sahip.  
  
 Bir öğenin odak kapsamına dönüştürülebilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ayarlayarak <xref:System.Windows.Input.FocusManager> özelliği eklenmiş <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> için `true`.  Kod içinde bir öğe odak kapsamına çağrılarak etkinleştirilebilir <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.StackPanel> ayarlayarak odak kapsamına <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> özelliği eklenmiş.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> Belirtilen öğenin odak kapsamını döndürür.  
  
 Sınıfları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsayılan olarak odak kapsamı olan olan <xref:System.Windows.Window>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.ToolBar>, ve <xref:System.Windows.Controls.ContextMenu>.  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> Belirtilen odak kapsamındaki odaklanan öğeyi alır.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> Belirtilen odak kapsamındaki odaklanan öğeyi ayarlar.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> genellikle ilk odaklanan öğeyi ayarlamak için kullanılır.  
  
 Aşağıdaki örnek, bir odak kapsamında odaklanan öğeyi ayarlar ve odak kapsamından odaklanılan öğeyi alır.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>Klavye gezinme  
 <xref:System.Windows.Input.KeyboardNavigation> Sınıftır Gezinti anahtarlarından birini basıldığında varsayılan klavye odağı Gezinti uygulamak için sorumlu.  Gezinti tuşları şunlardır: SEKMESİ, üst karakter + sekme, CTRL + SEKME, CTRL + SHIFT + SEKME, UPARROW, DOWNARROW, sol ok ve sağ ok tuşları.  
  
 Gezinti kapsayıcı Gezinti davranışını ekli ayarlayarak değiştirilebilir <xref:System.Windows.Input.KeyboardNavigation> özellikleri <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>, <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>, ve <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>.  Bu özellikleri türlerinin <xref:System.Windows.Input.KeyboardNavigationMode> ve olası değerleri <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, <xref:System.Windows.Input.KeyboardNavigationMode.Local>, <xref:System.Windows.Input.KeyboardNavigationMode.Contained>, <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>, <xref:System.Windows.Input.KeyboardNavigationMode.Once>, ve <xref:System.Windows.Input.KeyboardNavigationMode.None>.  Varsayılan değer <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, öğe başka bir deyişle, gezinti kapsayıcı değil.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Menu> sayıda <xref:System.Windows.Controls.MenuItem> nesneleri.  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> Ekli özellik ayarlanmış <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> üzerinde <xref:System.Windows.Controls.Menu>.  Odağı içinde SEKME tuşu kullanılarak değiştirildiğinde, <xref:System.Windows.Controls.Menu>, odağı her öğeden taşınır ve son öğe ulaşıldığında odak ilk öğesini döndürür.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>Odak gezinme  
 Ek [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] çalışmak için odak olan <xref:System.Windows.UIElement.MoveFocus%2A> ve <xref:System.Windows.UIElement.PredictFocus%2A>.  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> uygulamadaki sonraki öğeye odak değiştirir.  A <xref:System.Windows.Input.TraversalRequest> yönünü belirtmek için kullanılır.   <xref:System.Windows.Input.FocusNavigationDirection> Geçirilen <xref:System.Windows.UIElement.MoveFocus%2A> farklı yönleri odak değiştirilebileceği gibi belirtir <xref:System.Windows.Input.FocusNavigationDirection.First>, <xref:System.Windows.Input.FocusNavigationDirection.Last>, <xref:System.Windows.Input.FocusNavigationDirection.Up> ve <xref:System.Windows.Input.FocusNavigationDirection.Down>.  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.FrameworkElement.MoveFocus%2A> odaklanılan öğeyi değiştirmek için.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> Odak değiştirilmesi gerekiyorsa, odak alacak nesneyi döndürür.  Şu anda yalnızca <xref:System.Windows.Input.FocusNavigationDirection.Up>, <xref:System.Windows.Input.FocusNavigationDirection.Down>, <xref:System.Windows.Input.FocusNavigationDirection.Left>, ve <xref:System.Windows.Input.FocusNavigationDirection.Right> tarafından desteklenen <xref:System.Windows.FrameworkElement.PredictFocus%2A>.  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>Odak olayları  
 Klavye odağı ile ilgili olaylar <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>, <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> ve <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>, <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>.  Ekli olaylar tanımlanır olayları <xref:System.Windows.Input.Keyboard> sınıfı, ancak temel öğe sınıfları üzerindeki eşdeğer yönlendirilmiş olaylar daha kolay erişilebilir.  Olaylar hakkında daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> öğe klavye odağını aldığında oluşur.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> öğe klavye odağı kaybettiğinde oluşur.  Varsa <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> olay veya <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> olayı işlenir ve <xref:System.Windows.RoutedEventArgs.Handled%2A> ayarlanır `true`, odak değişmez.  
  
 Aşağıdaki örnek iliştirir <xref:System.Windows.UIElement.GotKeyboardFocus> ve <xref:System.Windows.UIElement.LostKeyboardFocus> olay işleyicilerine bir <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Zaman <xref:System.Windows.Controls.TextBox> klavye odağını aldığında <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.TextBox> değiştirilir <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Zaman <xref:System.Windows.Controls.TextBox> klavye odağı kaybettiğinde <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.TextBox> beyaza geri değişir.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Mantıksal odak ile ilgili olaylar <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus>.  Bu olaylar üzerinde tanımlanan <xref:System.Windows.Input.FocusManager> ekli olaylar olarak ancak <xref:System.Windows.Input.FocusManager> CLR olay sarmalayıcılarını göstermez.  <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> bu olayları daha rahat gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Input.FocusManager>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.ContentElement>  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Temel Öğelere Genel Bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md)
