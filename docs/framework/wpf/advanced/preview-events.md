---
title: Önizleme Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: 75165df94aa8b508ef85cf970933efb98b9d62ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211406"
---
# <a name="preview-events"></a>Önizleme Olayları
Olaylar, tünel oluşturma olarak da bilinen önizleme, yönlendirilmiş olaylar burada olayı ve olay veri kaynağı olarak bildirilen öğe doğrultusunda uygulama kök rota yönü geçerse olaylardır. Tüm olay senaryosunu desteklemek veya önizleme olayları gerektirir; Bu konuda, burada özel bileşenler veya sınıflara önizleme olayları oluşturma uygun durumlarda olabilir ve önizleme olayları, uygulama veya bileşenleri, nasıl işleyeceğini bulunduğu durumlar açıklanmaktadır.  
  
## <a name="preview-events-and-input"></a>Önizleme olayları ve giriş  
 Önizleme olayları genel olarak, dikkatli işlediğinizde olayları işaretleme veri olay işlenir. Dışında herhangi bir öğede bir Önizleme olay işleme (olay veri kaynağı olarak bildirilen öğe) ortaya çıkan öğe bir öğe, kutucuğun kaynağı olayı işlemek için fırsatı sağlamayan etkisi vardır. Özellikle söz konusu öğeler içinde bir denetimin birleştirme ilişkilerini varsa bazen istenen sonucu budur.  
  
 Giriş olayları için özellikle önizleme olayları da olay veri örnekleri eşdeğer tırmanma olay ile paylaşın. İşlenmiş giriş olayı işaretlemek için Önizleme olay işleyicisi sınıfı kullanırsanız, tırmanma giriş olayı işleyicisi sınıfı çağrılmayacak. Ya da işlenen olay işaretlemek için bir olay örneği işleyicisinin kullanırsanız, tırmanma olay işleyicileri genellikle çağrılmaz. Sınıf veya örnek işleyicileri kayıtlı veya olay işlenmiş olarak işaretlenmiş olsa bile teknik yaygın olarak kullanılmayan ancak bu çağrılacak bir seçenek ile bağlı.  
  
 Sınıf işleme ve önizleme olaylarına nasıl ilişkili olduğu hakkında daha fazla bilgi için bkz. [işaretleme yönlendirilmiş olayları işlenmiş ve bir sınıf olarak](marking-routed-events-as-handled-and-class-handling.md).  
  
### <a name="working-around-event-suppression-by-controls"></a>Denetimleri gizleme olay etrafında çalışma  
 Bileşik denetim için giriş olaylarını işleme, önizleme olayları yaygın olarak kullanıldığı bir senaryodur. Bazı durumlarda, belki de daha belirli bir davranışı ya da daha fazla bilgi taşıyan bir bileşen tarafından tanımlanan olay yerine için kendi denetiminden kaynaklanan gelen belirli bir olay yazar denetimin bastırır. Örneğin, bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> bastırır <xref:System.Windows.UIElement.MouseLeftButtonDown> ve <xref:System.Windows.UIElement.MouseRightButtonDown> tırmanma olayları tarafından gerçekleştirilen <xref:System.Windows.Controls.Button> veya fare yakalama ve yükseltme bileşik öğelerini bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> her zaman tarafından gerçekleştirilen olay <xref:System.Windows.Controls.Button> kendisi. Olay ve verileri yine de yol boyunca devam eder ancak <xref:System.Windows.Controls.Button> olay verileri olarak işaretler <xref:System.Windows.RoutedEventArgs.Handled%2A>, yalnızca özel olarak hareket etmesi belirtilen olay işleyicileri `handledEventsToo` çalışması çağrılır.  Diğer öğeler, uygulamanızın kök hala denetim gizlenen bir olayı işlemek için bir fırsat istediyseniz, ile kod işleyicileri eklemek için bir seçenek olan `handledEventsToo` belirtildiği şekilde `true`. Ancak genellikle daha basit bir teknik önizleme eşdeğer bir giriş olayın olmasını işlemek yönlendirme yönünü değiştirmek için. Örneğin, bir denetim engeller, <xref:System.Windows.UIElement.MouseLeftButtonDown>, işleyici eklemeyi deneyin <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> bunun yerine. Bu teknik yalnızca temel öğe için giriş olayları gibi çalışır <xref:System.Windows.UIElement.MouseLeftButtonDown>. Bu giriş olayları tünel/Kabarcık çiftleri kullanın, her iki olay ve olay verileri paylaşın.  
  
 Her tekniğin yan etkileri ya da sınırlamaları vardır. Bu noktada, olay işleme tırmanma olayı işlemek için beklediğiniz işleyicileri devre dışı bırakabilir ve bu nedenle, genellikle Previ üzerinde devam ederken işlenen olayı işaretlemek için iyi bir fikir olmadığını sınırlamasıdır Önizleme olay işleme yan etkisi olan Rota eni bölümü. SORUMLULUĞUN `handledEventsToo` tekniktir belirtemezsiniz, bir `handledEventsToo` işleyicisinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik olarak, olay işleyicisine kod işleyicinin eklenecek olduğu bir nesne başvurusu öğeye aldıktan sonra kaydetmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi](marking-routed-events-as-handled-and-class-handling.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
