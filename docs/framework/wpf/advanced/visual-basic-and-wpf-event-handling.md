---
title: Visual Basic ve WPF Olay İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 5625b63f2a2162f8f188476bfd61bde4c717f1dd
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559865"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic ve WPF Olay İşleme
Özellikle Microsoft Visual Basic .NET dili için, <xref:System.Windows.UIElement.AddHandler%2A> özniteliklerle olay işleyicileri eklemek yerine, olay işleyicilerini örneklerle ilişkilendirmek için dile özgü `Handles` anahtar sözcüğünü kullanabilirsiniz. Ancak, örnekleri örneklere eklemek için `Handles` tekniği bazı sınırlamalara sahiptir, çünkü `Handles` sözdizimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sisteminin bazı belirli yönlendirilmiş olay özelliklerini destekleyemez.  
  
## <a name="using-handles-in-a-wpf-application"></a>WPF uygulamasında "Handles" kullanma  
 `Handles` olan örneklere ve olaylara bağlı olay işleyicileri, örneğin, öğelerdeki öznitelik değerleri aracılığıyla atanan olay işleyicileri için de bir gereksinim olan Örneğin kısmi sınıf bildiriminde tanımlanmalıdır. Sayfada yalnızca bir <xref:System.Windows.FrameworkContentElement.Name%2A> Özellik değeri (veya [X:Name yönergesinin](../../../desktop-wpf/xaml-services/xname-directive.md) bildirildiği) içeren bir öğe için `Handles` belirtebilirsiniz. Bunun nedeni, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.FrameworkContentElement.Name%2A>, `Handles` sözdizimi için gereken *örneği. Event* başvuru biçimini desteklemek için gereken örnek başvurusunu oluşturmasıdır. <xref:System.Windows.FrameworkContentElement.Name%2A> başvurusu olmadan `Handles` için kullanılabilen tek öğe, kısmi sınıfı tanımlayan kök öğe örneğidir.  
  
 Aynı işleyiciyi birden çok öğeye atayabilirsiniz. `Handles` sonra *örnek. olay* başvurularını virgülle ayırın.  
  
 Aynı örneğe birden fazla işleyici atamak için `Handles` kullanabilirsiniz *. olay*başvurusu. `Handles` başvurusunda işleyicilerin verildiği sıraya herhangi bir önem atamayın; aynı olayı işleyen işleyicilerin herhangi bir sırada çağrılabileceğini varsaymalısınız.  
  
 Bildirimde `Handles` eklenmiş bir işleyiciyi kaldırmak için <xref:System.Windows.UIElement.RemoveHandler%2A>çağırabilirsiniz.  
  
 Üyeler tablolarında işlenmekte olan olayı tanımlayan örneklere eklediğiniz sürece, yönlendirilmiş olaylara yönelik işleyicileri eklemek için `Handles` kullanabilirsiniz. Yönlendirilmiş olaylar için `Handles` ekli işleyiciler, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikleri olarak eklenmiş veya <xref:System.Windows.UIElement.AddHandler%2A>ortak imzasıyla aynı yönlendirme kurallarını izler. Bu, olay zaten işlenmiş olarak işaretlenmişse (olay verilerinde <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliği `True`), bu olay örneğine yanıt olarak `Handles` eklenmiş işleyiciler çağrılmaz. Olay, rotadaki başka bir öğe üzerinde örnek işleyicileri tarafından veya geçerli öğe ya da yol üzerindeki önceki öğeler üzerinde sınıf işlemesi tarafından işlenmiş olarak işaretlenebilir. Eşleştirilmiş tünel/kabarcık olaylarını destekleyen giriş olayları için, tünel rotası işlenen olay çiftini işaretlenmiş olabilir. Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Işleyiciler eklemek için "Handles" sınırlamaları  
 `Handles` ekli olaylar için işleyicilere başvuramaz. Bu ekli olay veya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]*typeName. eventName* olay öznitelikleri için `add` erişimci yöntemini kullanmanız gerekir. Ayrıntılar için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 Yönlendirilmiş olaylar için yalnızca, örnek üyeler tablosunda bu olayın varolduğu örnekleri için işleyiciler atamak üzere `Handles` kullanabilirsiniz. Bununla birlikte, genel olarak, bir üst öğe, alt öğelerinden bir olay için bir dinleyici olabilir ve üst öğe, üyeler tablosunda bu olaya sahip olmasa bile. Öznitelik sözdiziminde, bunu, işlemek istediğiniz olayın gerçekten tanımladığı türü niteleyen bir *typeName. MemberName* öznitelik formu aracılığıyla belirtebilirsiniz. Örneğin, bir üst `Page` (`Click` olayı tanımlanmamış), form `Button.Click`bir öznitelik işleyicisi atayarak düğme tıklamaları için dinleme yapabilir. Ancak `Handles`, çakışan bir *örnek. Event* formunu desteklemesi gerektiğinden *typeName. MemberName* formunu desteklemez. Ayrıntılar için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 `Handles`, zaten işlenmiş olarak işaretlenmiş olaylar için çağrılan işleyiciler iliştirilemiyor. Bunun yerine, kodu kullanmanız ve <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>`handledEventsToo` aşırı yüklemesini çağırmanız gerekir.  
  
> [!NOTE]
> XAML 'de aynı olay için bir olay işleyicisi belirttiğinizde, Visual Basic kodda `Handles` sözdizimini kullanmayın. Bu durumda, olay işleyicisi iki kez çağırılır.  
  
## <a name="how-wpf-implements-handles-functionality"></a>WPF "Handles" Işlevselliğini nasıl uygular  
 Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfası derlendiğinde, ara dosya <xref:System.Windows.FrameworkContentElement.Name%2A> özellik kümesi (veya [X:Name yönergesinin](../../../desktop-wpf/xaml-services/xname-directive.md) bildirildiği) sayfadaki her öğeye `Friend` `WithEvents` başvurularını bildirir. Her adlandırılmış örnek potansiyel olarak `Handles`aracılığıyla bir işleyiciye atanabilecek bir öğedir.  
  
> [!NOTE]
> IntelliSense, Visual Studio 'da sayfada bir `Handles` başvurusu için hangi öğelerin kullanılabildiği hakkında tamamlanmasını gösterebilir. Ancak, bu, ara dosyanın tüm `Friends` başvurularını doldurabilmesi için bir derleme geçişi alabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Yönlendirilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi](marking-routed-events-as-handled-and-class-handling.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
