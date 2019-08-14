---
title: Visual Basic ve WPF Olay İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 4ff006099dd2fa706cb575eec18e135d6e74ad46
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972316"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic ve WPF Olay İşleme
Özel olarak Microsoft Visual Basic .net dili için, özniteliklerle olay işleyicileri eklemek veya `Handles` <xref:System.Windows.UIElement.AddHandler%2A> yöntemi kullanmak yerine, olay işleyicilerini örneklerle ilişkilendirmek için dile özgü anahtar sözcüğünü kullanabilirsiniz. Ancak, `Handles` işleyicileri örneklere ekleme tekniği bazı sınırlamalara sahiptir, `Handles` çünkü söz dizimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sisteminin bazı belirli yönlendirilmiş olay özelliklerini desteklenemez.  
  
## <a name="using-handles-in-a-wpf-application"></a>WPF uygulamasında "Handles" kullanma  
 Örneklerine ve olaylarına `Handles` bağlı olan olay işleyicileri, örneğin, öğeleri üzerinde öznitelik değerleri aracılığıyla atanan olay işleyicileri için de bir gereksinim olan örnek sınıfının kısmi sınıf bildiriminde tanımlanmalıdır. Yalnızca bir `Handles` <xref:System.Windows.FrameworkContentElement.Name%2A> özellik değerine (veya [x:Name yönergesinin](../../xaml-services/x-name-directive.md) bildirildiği) sahip sayfada bir öğe için belirtebilirsiniz. Bunun nedeni, ' <xref:System.Windows.FrameworkContentElement.Name%2A> ın [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , `Handles` sözdizimi için gereken *örneği. Event* başvuru biçimini desteklemek için gereken örnek başvurusunu oluşturmasıdır. Başvuru olmadan için `Handles` kullanılabilecek tek öğe, kısmi sınıfı tanımlayan kök öğe örneğidir. <xref:System.Windows.FrameworkContentElement.Name%2A>  
  
 Aynı işleyiciyi birden çok öğeye atayabilir ve sonra `Handles` *örnek. olay* başvurularını virgülle ayırarak atayabilirsiniz.  
  
 Aynı örneğe birden `Handles` fazla işleyici atamak için ' i kullanabilirsiniz *. olay*başvurusu. `Handles` Başvuru içinde işleyicilerin verildiği sıraya herhangi bir önem atamayın; aynı olayı işleyen işleyicilerin herhangi bir sırada çağrılabileceğini varsaymalısınız.  
  
 Bildiriminde ile `Handles` eklenmiş bir işleyiciyi kaldırmak için öğesini çağırabilirsiniz <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Öğeleri, Üyeler `Handles` tablolarında işlenmekte olan olayı tanımlayan örneklere eklediğiniz sürece, yönlendirilmiş olaylara yönelik işleyiciler eklemek için ' yi kullanabilirsiniz. Yönlendirilmiş olaylar için, ile birlikte `Handles` eklenmiş olan işleyiciler, öznitelik olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] eklenmiş veya ortak imzasıyla <xref:System.Windows.UIElement.AddHandler%2A>aynı yönlendirme kurallarını izler. Bu, olay zaten işlenmiş olarak işaretlenmişse ( <xref:System.Windows.RoutedEventArgs.Handled%2A> olay verilerinde özelliği ise `True`), bu olay örneğine karşılık ile `Handles` eklenen işleyiciler çağrılmaz. Olay, rotadaki başka bir öğe üzerinde örnek işleyicileri tarafından veya geçerli öğe ya da yol üzerindeki önceki öğeler üzerinde sınıf işlemesi tarafından işlenmiş olarak işaretlenebilir. Eşleştirilmiş tünel/kabarcık olaylarını destekleyen giriş olayları için, tünel rotası işlenen olay çiftini işaretlenmiş olabilir. Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Işleyiciler eklemek için "Handles" sınırlamaları  
 `Handles`Ekli olaylar için işleyicilere başvuru yapılamaz. Bu ekli olay veya `add` ' de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] *typeName. eventName* olay öznitelikleri için erişimci yöntemini kullanmanız gerekir. Ayrıntılar için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 Yönlendirilmiş olaylar için yalnızca `Handles` , örnek üyeler tablosunda bu olayın varolduğu örnekleri için işleyiciler atamak üzere kullanabilirsiniz. Bununla birlikte, genel olarak, bir üst öğe, alt öğelerinden bir olay için bir dinleyici olabilir ve üst öğe, üyeler tablosunda bu olaya sahip olmasa bile. Öznitelik sözdiziminde, bunu, işlemek istediğiniz olayın gerçekten tanımladığı türü niteleyen bir *typeName. MemberName* öznitelik formu aracılığıyla belirtebilirsiniz. Örneğin, bir üst öğe `Page` (hiçbir olay `Click` tanımlanmadığında), formda `Button.Click`bir öznitelik işleyicisi atayarak düğme tıklamalı olaylar için dinleme yapabilir. Ancak `Handles` , çakışan bir *örnek. Event* formunu desteklemesi gerektiğinden *typeName. MemberName* formunu desteklemez. Ayrıntılar için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 `Handles`zaten işlenmiş olarak işaretlenmiş olaylar için çağrılan işleyiciler iliştirilemez. Bunun yerine, kodu kullanmanız ve ' nin `handledEventsToo` <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>aşırı yüklemesini çağırmanız gerekir.  
  
> [!NOTE]
>  XAML 'de aynı olay `Handles` için bir olay işleyicisi belirttiğinizde Visual Basic kodunuzda söz dizimini kullanmayın. Bu durumda, olay işleyicisi iki kez çağırılır.  
  
## <a name="how-wpf-implements-handles-functionality"></a>WPF "Handles" Işlevselliğini nasıl uygular  
 Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfa derlendiğinde, ara dosya sayfadaki bir <xref:System.Windows.FrameworkContentElement.Name%2A> özellik kümesi `Friend` (veya [x:Name yönergesinin](../../xaml-services/x-name-directive.md) bildirildiği) bulunan her öğeye başvuruları bildirir `WithEvents` . Her bir adlandırılmış örnek potansiyel olarak bir işleyiciye `Handles`atanabileceği bir öğedir.  
  
> [!NOTE]
>  IntelliSense [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]içinde, bir sayfada bir başvuru için hangi öğelerin kullanılabildiği hakkında bir `Handles` tamamlama gösterebilir. Ancak, bu, ara dosyanın tüm `Friends` başvuruları doldurabilmesi için bir derleme geçişi alabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Yönlendirilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi](marking-routed-events-as-handled-and-class-handling.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
