---
title: Visual Basic ve WPF Olay İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 321b4547bffbbae3c16ef8dd046bdff65ebe0bf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic ve WPF Olay İşleme
Microsoft Visual Basic .NET dil için özellikle dile özgü kullanabileceğiniz `Handles` öznitelikleri ile olay işleyicileri ekleme veya kullanma yerine örnekleri, olay işleyicileri ilişkilendirmek için anahtar sözcüğü <xref:System.Windows.UIElement.AddHandler%2A> yöntemi. Ancak, `Handles` örneklerine işleyicileri iliştirmek için teknik çünkü bazı sınırlamalar vardır `Handles` sözdizimi belirli yönlendirilmiş olay özelliklerinden bazıları destekleyemez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi.  
  
## <a name="using-handles-in-a-wpf-application"></a>"Tanıtıcıları" bir WPF uygulamasında kullanma  
 Örnekler ve olaylar ile bağlı olay işleyicileri `Handles` tüm parçalı sınıf bildirimi de öğelerin öznitelik değerleri aracılığıyla atanan olay işleyicileri için bir gereksinimdir örneği içinde tanımlanması gerekir. Yalnızca belirtebilirsiniz `Handles` sahip sayfasında bir öğe için bir <xref:System.Windows.FrameworkContentElement.Name%2A> özellik değeri (veya [x: Name yönergesi](../../../../docs/framework/xaml-services/x-name-directive.md) bildirilen). Bunun nedeni, <xref:System.Windows.FrameworkContentElement.Name%2A> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] desteklemek gerekli olan örnek başvuru oluşturmasıdır *Instance.Event* gerektirdiği başvuru biçimi `Handles` sözdizimi. İçin kullanılan tek öğe `Handles` olmadan bir <xref:System.Windows.FrameworkContentElement.Name%2A> başvurudur kısmi sınıfı tanımlayan kök öğesi örneği.  
  
 Ayırarak birden çok öğe aynı işleyici atayabilirsiniz *Instance.Event* sonra başvuran `Handles` virgüllerle.  
  
 Kullanabileceğiniz `Handles` birden fazla işleyici aynı atamak için *Instance.Event*başvuru. Herhangi bir önem derecesi, işleyicileri verilir, sipariş atamayın `Handles` başvuru; aynı olayını işle işleyicileri herhangi bir sırada çağrılabilir varsayın.  
  
 İle eklenen işleyiciyi kaldırmak için `Handles` bildiriminde çağırabilirsiniz <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Kullanabileceğiniz `Handles` işlenen olay üyeleri tablolarıyla tanımlayan örneklere işleyicileri ekleme sürece yönlendirilmiş olaylar için işleyiciler eklemek için. Yönlendirilmiş olaylar, ile bağlı işleyicileri için `Handles` olarak bağlı işleyicileri gibi aynı yönlendirme kurallarına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikleri veya ortak imzası ile <xref:System.Windows.UIElement.AddHandler%2A>. Bunun anlamı olay zaten işlenmiş olarak işaretlenmişse ( <xref:System.Windows.RoutedEventArgs.Handled%2A> olay verilerini bir özellik olan `True`), iliştirilmiş işleyiciler `Handles` olay örneğine yanıt olarak çağrılmaz. Olay rota başka bir öğe örnek işleyicileri veya geçerli öğe veya yol boyunca önceki öğeleri işleme sınıfı tarafından işlenmiş işaretlenebilir. Eşleştirilmiş tünel/Kabarcık olaylarını destekleyen giriş olayları için olay çiftini işlenen tünel yolu işaretlenmiş. Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>"Tanıtıcıları" sınırlamaları işleyicileri ekleme  
 `Handles` ekli olaylar için işleyiciler başvuramaz. Kullanmalısınız `add` bu ekli olay erişimci yöntemi veya *typename.eventname* olay öznitelikleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ayrıntılar için bkz [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Yönlendirilmiş olaylar için yalnızca kullanabileceğiniz `Handles` işleyici atamak için olayın örnek üyeler tablosunda bulunduğu örnekleri. Üst öğenin üyeler tablosunda olay yoksa bile ancak, yönlendirilmiş olaylarla genel olarak, bir üst öğesi alt öğe, bir olay için bir dinleyici olabilir. Bu işlemlerde belirtin öznitelik sözdiziminde bir *typename.membername* özniteliği hangi tür gerçekte işlemek istediğiniz olay tanımlar niteleyen formu. Örneğin, bir üst `Page` (hiçbir `Click` tanımlanan olay) biçiminde öznitelik işleyicisi atayarak düğme tıklama olaylarını dinleme `Button.Click`. Ancak `Handles` desteklemediği *typename.membername* formunda, çünkü bir çakışan desteklemesi gerekir *Instance.Event* formu. Ayrıntılar için bkz [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 `Handles` zaten işlenmiş olarak işaretlenmiş olaylar için çağırılan işleyicileri eklenemiyor. Bunun yerine, kod ve çağrı kullanmalısınız `handledEventsToo` , aşırı <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
>  Kullanmayın `Handles` XAML'deki aynı olay için olay işleyicisi belirttiğinizde, Visual Basic kodundaki sözdizimi. Bu durumda, olay işleyicisi iki kez çağrılır.  
  
## <a name="how-wpf-implements-handles-functionality"></a>WPF Implements "işleme biçimini" işlevi  
 Zaman bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfa derlenmiş, Ara dosyayı bildirir `Friend` `WithEvents` başvuruları her öğeye sahip sayfasında bir <xref:System.Windows.FrameworkContentElement.Name%2A> özellik kümesi (veya [x: Name yönergesi](../../../../docs/framework/xaml-services/x-name-directive.md) bildirilen). Her adlandırılmış örnek potansiyel olarak yoluyla işleyiciye atanan bir öğedir `Handles`.  
  
> [!NOTE]
>  İçinde [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], [!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] öğeleri olduğu için kullanılabilir tamamlanmasını gösterebilir bir `Handles` sayfasındaki başvuru. Ancak, böylece Ara dosyası tümünü doldurur bu bir derleme geçişi sürebilir `Friends` başvuruları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.UIElement.AddHandler%2A>  
 [Yönlendirilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
