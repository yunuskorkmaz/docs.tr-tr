---
title: Odağa Genel Bakış
description: 'Windows Presentation Foundation odağıyla ilgili olan iki ana kavram hakkında bilgi edinin: klavye odağı ve mantıksal odak.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 71aeb577cccd2c3b16df1c5a3cb772dd1f5479e2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165113"
---
# <a name="focus-overview"></a>Odağa Genel Bakış
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Odağıyla ilgili iki ana kavram vardır: klavye odağı ve mantıksal odak.  Klavye odağı, klavye girişini alan ve mantıksal odak, odağı olan bir odak kapsamındaki öğeyi ifade eden öğe anlamına gelir.  Bu kavramlar, bu genel bakışta ayrıntılı olarak ele alınmıştır.  Bu kavramların farkını anlamak, odağın elde edilmesi gereken birden çok bölgeye sahip karmaşık uygulamalar oluşturmak için önemlidir.  
  
 Odak yönetimine katılan ana sınıflar, <xref:System.Windows.Input.Keyboard> ve gibi sınıf, <xref:System.Windows.Input.FocusManager> sınıf ve temel öğe sınıflarıdır <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> .  Temel öğeler hakkında daha fazla bilgi için bkz. [temel öğelere genel bakış](base-elements-overview.md).  
  
 <xref:System.Windows.Input.Keyboard>Sınıf öncelikle klavye odağıyla ilgilidir ve <xref:System.Windows.Input.FocusManager> öncelikle mantıksal odak ile ilgilidir, ancak bu mutlak bir ayrım değildir.  Klavye odağına sahip bir öğe ayrıca mantıksal odağa sahip olur, ancak mantıksal odağa sahip bir öğenin klavye odağı olması gerekmez.  Bu, <xref:System.Windows.Input.Keyboard> klavye odağı olan öğeyi ayarlamak için sınıfını kullandığınızda görünür ve ayrıca öğesi için mantıksal odağı de belirler.  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>Klavye odağı  
 Klavye odağı, şu anda klavye girişi alan öğeyi ifade eder.  Klavye odaklı bütün masaüstünde yalnızca bir öğe olabilir.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]' De, klavye odağına sahip olan öğe <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> olarak ayarlanır `true` .  Sınıftaki static özelliği, <xref:System.Windows.Input.Keyboard.FocusedElement%2A> <xref:System.Windows.Input.Keyboard> Şu anda klavye odağına sahip olan öğeyi alır.  
  
 Bir öğenin klavye odağını alması için, <xref:System.Windows.UIElement.Focusable%2A> ve <xref:System.Windows.UIElement.IsVisible%2A> temel öğelerdeki özellikler olarak ayarlanmalıdır `true` .  Temel sınıf gibi bazı sınıflar <xref:System.Windows.Controls.Panel> <xref:System.Windows.UIElement.Focusable%2A> Varsayılan olarak olarak ayarlanmıştır `false` ; Bu nedenle, bu <xref:System.Windows.UIElement.Focusable%2A> `true` tür bir öğenin klavye odağını alabilmesini istiyorsanız olarak ayarlamanız gerekir.  
  
 Klavye odağı, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir öğeye sekme veya belirli öğelerde fareyle tıklanması gibi ile Kullanıcı etkileşimi aracılığıyla elde edilebilir.  Klavye odağı Ayrıca, sınıfındaki yöntemi kullanılarak programlı bir şekilde elde edilebilir <xref:System.Windows.Input.Keyboard.Focus%2A> <xref:System.Windows.Input.Keyboard> .  <xref:System.Windows.Input.Keyboard.Focus%2A>Yöntemi, belirtilen öğeye klavye odağı verme girişiminde bulunur.  Döndürülen öğe,, eski veya yeni odak nesnesi isteği engelleyediyse, istenen farklı bir öğe olabilecek klavye odağına sahip olan öğedir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Input.Keyboard.Focus%2A> bir üzerinde klavye odağı ayarlamak için yöntemini kullanır <xref:System.Windows.Controls.Button> .  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>Temel öğe sınıflarında özelliği, öğenin klavye odağına sahip olup olmadığını gösteren bir değer alır.  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>Temel öğe sınıflarında özelliği, öğenin veya görsel alt öğelerinden birinin klavye odağına sahip olup olmadığını gösteren bir değer alır.  
  
 Uygulama başlangıcında ilk odağı ayarlarken, odağı alacak olan öğe, uygulama tarafından yüklenen ilk pencerenin görsel ağacında olmalıdır ve öğesi, <xref:System.Windows.UIElement.Focusable%2A> ve <xref:System.Windows.UIElement.IsVisible%2A> olarak ayarlanmalıdır `true` .  İlk odağı ayarlamak için önerilen yer <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisidir.  <xref:System.Windows.Threading.Dispatcher>Ya da çağırarak bir geri çağırma kullanılabilir <xref:System.Windows.Threading.Dispatcher.Invoke%2A> <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> .  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>Mantıksal odak  
 Mantıksal odak, <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> bir odak kapsamındaki öğesine başvurur.  Odak kapsamı, kapsamı içinde takip eden bir öğedir <xref:System.Windows.Input.FocusManager.FocusedElement%2A> .  Klavye odağı bir odak kapsamından ayrıldığında, odaklanmış öğe klavye odağını kaybeder ancak mantıksal odağı korur.  Klavye odağı odak kapsamına döndüğünde, odaklanmış öğe klavye odağını elde eder.  Bu, klavye odağının birden çok odak kapsamı arasında değiştirilmesini sağlar, ancak odak kapsamındaki öğenin odak kapsamına dönüşmesini sağlayan odak kapsamı klavye odağı.  
  
 Bir uygulamada mantıksal odağa sahip birden fazla öğe olabilir, ancak yalnızca belirli bir odak kapsamında mantıksal odağa sahip bir öğe olabilir.  
  
 Klavye odağına sahip bir öğe, ait olduğu odak kapsamı için mantıksal odağa sahiptir.  
  
 Öğesi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Input.FocusManager> ekli özelliği olarak ayarlanarak içindeki bir odak kapsamına açılabilir <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> `true` .  Kodda, bir öğe çağırarak bir odak kapsamına açılabilir <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> .  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.StackPanel> ekli özelliği ayarlayarak bir odak kapsamı içinde oluşturur <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> .  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>Belirtilen öğe için odak kapsamını döndürür.  
  
 İçindeki,,, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve varsayılan olarak odak kapsamları olan sınıflar <xref:System.Windows.Window> <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ToolBar> <xref:System.Windows.Controls.ContextMenu> .  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>belirtilen odak kapsamı için odaklanmış öğeyi alır.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>belirtilen odak kapsamındaki odaklanmış öğeyi ayarlar.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>genellikle ilk odaklanan öğeyi ayarlamak için kullanılır.  
  
 Aşağıdaki örnek, bir odak kapsamındaki odaklı öğeyi ayarlar ve odak kapsamının odaklanmış öğesini alır.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>Klavye ile Gezinme  
 Bu <xref:System.Windows.Input.KeyboardNavigation> sınıf, gezinti tuşlarından birine basıldığında varsayılan klavye odağı gezintisini uygulamaktan sorumludur.  Gezinti tuşları şunlardır: sekme, SHIFT + SEKME, CTRL + TAB, CTRL + SHIFT + TAB, UPOK, DOWNOK, LEFTARROW ve ıltarrow tuşları.  
  
 Gezinti kapsayıcısının gezinti davranışı, ve ekli özellikleri ayarlanarak değiştirilebilir <xref:System.Windows.Input.KeyboardNavigation> <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A> <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> .  Bu özellikler türündedir <xref:System.Windows.Input.KeyboardNavigationMode> ve olası değerler,,,, <xref:System.Windows.Input.KeyboardNavigationMode.Continue> ve ' dir <xref:System.Windows.Input.KeyboardNavigationMode.Local> <xref:System.Windows.Input.KeyboardNavigationMode.Contained> <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Input.KeyboardNavigationMode.Once> <xref:System.Windows.Input.KeyboardNavigationMode.None> .  Varsayılan değer <xref:System.Windows.Input.KeyboardNavigationMode.Continue> , öğesinin bir gezinti kapsayıcısı olmadığı anlamına gelir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Menu> dizi nesne içeren bir oluşturur <xref:System.Windows.Controls.MenuItem> .  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>İliştirilmiş özelliği üzerinde olarak ayarlanır <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Controls.Menu> .  Odak, içindeki sekme tuşu kullanılarak değiştirildiğinde <xref:System.Windows.Controls.Menu> , odak her öğeden taşınır ve son öğeye ulaşıldığında odak ilk öğeye döndürülür.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>Program aracılığıyla odağa gitme  
 Odak ile çalışmak için ek API şunlardır <xref:System.Windows.UIElement.MoveFocus%2A> <xref:System.Windows.UIElement.PredictFocus%2A> .  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>değişiklikleri uygulamadaki Next öğesine odaklayın.  <xref:System.Windows.Input.TraversalRequest>Yönü belirtmek için kullanılır.   <xref:System.Windows.Input.FocusNavigationDirection>Geçirilen,, <xref:System.Windows.UIElement.MoveFocus%2A> ve gibi farklı yönlerinin taşınabileceği farklı yönleri belirtir <xref:System.Windows.Input.FocusNavigationDirection.First> <xref:System.Windows.Input.FocusNavigationDirection.Last> <xref:System.Windows.Input.FocusNavigationDirection.Up> <xref:System.Windows.Input.FocusNavigationDirection.Down> .  
  
 Aşağıdaki örnek, <xref:System.Windows.FrameworkElement.MoveFocus%2A> odaklanmış öğeyi değiştirmek için kullanır.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>odak değiştirilse, odağı alacak nesneyi döndürür.  Şu anda, <xref:System.Windows.Input.FocusNavigationDirection.Up> , <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left> ve <xref:System.Windows.Input.FocusNavigationDirection.Right> tarafından desteklenir <xref:System.Windows.FrameworkElement.PredictFocus%2A> .  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>Odak olayları  
 Klavye odağıyla ilgili olaylar <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> ve <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> , <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> .  Olaylar, sınıf üzerinde ekli olaylar olarak tanımlanır <xref:System.Windows.Input.Keyboard> , ancak temel öğe sınıflarında eşdeğer yönlendirilmiş olaylar olarak daha kolay erişilebilir.  Olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>öğesi klavye odağını aldığında tetiklenir.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>öğe, klavye odağını kaybettiğinde tetiklenir.  <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>Olay veya <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> olay işlenirse ve <xref:System.Windows.RoutedEventArgs.Handled%2A> olarak ayarlanırsa `true` , odak değişmez.  
  
 Aşağıdaki örnek, <xref:System.Windows.UIElement.GotKeyboardFocus> ve <xref:System.Windows.UIElement.LostKeyboardFocus> olay işleyicilerini öğesine ekler <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 <xref:System.Windows.Controls.TextBox>Klavye odağı aldığında, <xref:System.Windows.Controls.Control.Background%2A> öğesinin özelliği <xref:System.Windows.Controls.TextBox> olarak değiştirilir <xref:System.Windows.Media.Brushes.LightBlue%2A> .  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 <xref:System.Windows.Controls.TextBox>Klavye odağı kaybettiğinde, <xref:System.Windows.Controls.Control.Background%2A> öğesinin özelliği <xref:System.Windows.Controls.TextBox> beyaza geri değişir.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Mantıksal odak ile ilgili olaylar <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> .  Bu olaylar, <xref:System.Windows.Input.FocusManager> ekli olaylar olarak tanımlanmıştır, ancak <xref:System.Windows.Input.FocusManager> clr olay sarmalayıcıları sunmaz.  <xref:System.Windows.UIElement>ve <xref:System.Windows.ContentElement> Bu olayları daha kolay bir şekilde kullanıma sunun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Girişe Genel Bakış](input-overview.md)
- [Temel Öğelere Genel Bakış](base-elements-overview.md)
