---
title: Visual Basic ve WPF Olay İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: c6e1863850ebf04408c7ffc7b784e9ca3ca12cf5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078030"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic ve WPF Olay İşleme
Microsoft Visual Basic .NET dil için özellikle, dile özgü kullanabileceğiniz `Handles` öznitelikleri olan olay işleyicileri ekleme veya bu adı kullanıyor yerine örnekleri, olay işleyicileri ilişkilendirmek için anahtar sözcüğü <xref:System.Windows.UIElement.AddHandler%2A> yöntemi. Ancak, `Handles` işleyicileri örneklere ekleme tekniği çünkü bazı sınırlamalara sahip `Handles` söz dizimi özel gönderilmiş olay özelliklerinden bazılarını destekleyemez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi.  
  
## <a name="using-handles-in-a-wpf-application"></a>"İşler" bir WPF uygulamasında kullanma  
 Örnekler ve olaylar ile bağlı olan olay işleyicileri `Handles` tüm öğelerin öznitelik değerleri ile atanan olay işleyicileri için bir gereksinim olan örneğinin kısmi sınıf bildirimi içinde tanımlanmış olmalıdır. Yalnızca belirtebilirsiniz `Handles` sayfasında sahip bir öğe için bir <xref:System.Windows.FrameworkContentElement.Name%2A> özellik değeri (veya [x: Name yönergesi](../../xaml-services/x-name-directive.md) bildirilen). Bunun nedeni, <xref:System.Windows.FrameworkContentElement.Name%2A> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] desteklemek için gerekli olan örneği başvuru oluşturur *Instance.Event* gerektirdiği başvuru biçimi `Handles` söz dizimi. Kullanılabilir tek öğe `Handles` olmadan bir <xref:System.Windows.FrameworkContentElement.Name%2A> kısmi sınıf tanımlayan kök öğesi örneği başvurudur.  
  
 Ayrılarak birden çok öğeyi aynı işleyiciyi atayabilirsiniz *Instance.Event* sonra başvuran `Handles` virgüllerle.  
  
 Kullanabileceğiniz `Handles` birden fazla işleyici aynı atamak için *Instance.Event*başvuru. Herhangi bir önem derecesi, işleyicileri verilen sipariş atamayın `Handles` başvuru; aynı olay işleyen işleyiciler herhangi bir sırada çağrılabilir varsaymanız gerekir.  
  
 İle eklenen bir işleyici kaldırmak için `Handles` bildiriminde çağırabilirsiniz <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Kullanabileceğiniz `Handles` işlenen olayı üyeleri tablolarıyla tanımlayan örneklere işleyicileri eklemek sürece yönlendirilmiş olaylar için işleyiciler eklemek için. Yönlendirilmiş olaylar ile ekli işleyicileri için `Handles` olarak bağlı işleyicileri gibi aynı yönlendirme kurallarına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikleri veya ortak imzası <xref:System.Windows.UIElement.AddHandler%2A>. Olay zaten işlenmiş olarak işaretlenmişse Bunun anlamı ( <xref:System.Windows.RoutedEventArgs.Handled%2A> olay verileri özelliği `True`), iliştirilmiş işleyiciler `Handles` yanıt olarak olay örneğine çağrılmaz. Olay örnek işleyicileri yol başka bir öğedeki ya da sınıf geçerli öğenin veya önceki öğelerin yol boyunca işleme işlenmiş olarak işaretlenebilir. Eşleştirilmiş tünel Kabarcık olayları destekleyen giriş olayları için tünel yolu işlenen olay çifti işaretlenmiş. Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>"İşler" sınırlamaları işleyicileri ekleme  
 `Handles` ekli olayları için işleyiciler başvuramaz. Kullanmalısınız `add` , ekli olay erişimci yöntemi veya *typename.eventname* olay öznitelikleri içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ayrıntılar için bkz [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 Yönlendirilmiş olaylar için yalnızca kullanabilirsiniz `Handles` işleyici atamak için olayın örnek üyeler tablosunda bulunduğu örnekleri. Üst öğenin olay üyeler tablosunda yok bile ancak yönlendirilmiş olaylar ile genel olarak, bir üst öğenin alt öğeleri, bir olay için bir dinleyici olabilir. Nitelik söz dizimindeki bu aracılığıyla belirtebilirsiniz bir *typename.membername* öznitelik türü gerçekten işlemek için istediğiniz olayı tanımlar niteleyen formu. Örneğin, bir üst `Page` (olmadan `Click` tanımlanan olay) biçiminde bir özniteliği işleyici atayarak düğme tıklama olayları dinlenebilir `Button.Click`. Ancak `Handles` desteklemediği *typename.membername* form çakışan bir desteklemesi gerekir çünkü *Instance.Event* formu. Ayrıntılar için bkz [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 `Handles` zaten işlenmiş olarak işaretlenmiş olaylar için çağrılan işleyicileri eklenemiyor. Bunun yerine, kodu ve çağrı kullanmalısınız `handledEventsToo` aşırı yükünü <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
>  Kullanmayın `Handles` XAML içinde aynı etkinlik için bir olay işleyicisi belirttiğinizde, Visual Basic kodundaki söz dizimi. Bu durumda, olay işleyicisi iki kez çağrılır.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Nasıl WPF uygulayan "işleme" işlevi  
 Olduğunda bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfa derlendiğinde, Ara dosyası bildirir `Friend` `WithEvents` başvuruları her öğeye olan sayfasında bir <xref:System.Windows.FrameworkContentElement.Name%2A> özellik kümesi (veya [x: Name yönergesi](../../xaml-services/x-name-directive.md) bildirilen). Her adlandırılmış örneği olabilecek bir işleyici atanabilecek bir öğedir `Handles`.  
  
> [!NOTE]
>  İçinde [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], [!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] tamamlama için öğeleri olduğu için kullanılabilir gösterebilirsiniz bir `Handles` bir sayfa başvurusu. Ancak, tüm ara dosyası doldurabilir, böylece bu bir derleme geçişi sürebilir `Friends` başvuruları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Gönderilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi](marking-routed-events-as-handled-and-class-handling.md)
- [Gönderilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
