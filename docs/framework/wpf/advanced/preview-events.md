---
title: Önizleme Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: 2d6c1ab32cb43730af2f935f4bd4405059994c12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="preview-events"></a>Önizleme Olayları
Tünel olayları olarak da bilinen önizleme olayları yönlendirilmiş burada olayı ve olay veri kaynağı olarak bildirilen öğe doğru uygulama kökünden rota yönü geçen olaylardır. Tüm olay senaryoları desteklemek veya önizleme olayları gerektirir; Bu konuda, burada özel bileşenlerde veya sınıflarda önizleme olayları oluşturma uygun durumlarda olabilir ve önizleme olayları, uygulama veya bileşenler bunları nasıl yöneteceğini var olduğu durumlar açıklanmaktadır.  
  
## <a name="preview-events-and-input"></a>Önizleme olayları ve giriş  
 Önizleme olayları genel olarak, dikkatli olun uyguluyorsanız olayları işaretleme veri olay işlenir. Dışındaki herhangi bir öğe üzerinde Önizleme olayı işleme (olay veri kaynağı olarak bildirilen öğe) ortaya çıkan öğesi bir öğe, kaynaklanan olayını işlemek için fırsatı sağlamayan etkisi vardır. Özellikle söz konusu öğeler Denetim birleştirme içinde ilişkileri varsa bazen istenen sonucu budur.  
  
 Giriş olayları için özellikle, önizleme olayları ayrıca olay veri örneklerini eşdeğer kabarcıklanma olayı ile paylaşır. İşlenen girdi olayını işaretlemek için Önizleme olay sınıfı işleyicisi kullanırsanız, kabarcıklanma girdi olay sınıfı işleyicisi çağrılır değil. Veya, işlenen olayı işaretlemek için Önizleme olay örneği işleyicisi kullanırsanız, kabarcıklanma olayı için işleyiciler genellikle çağrılmaz. Sınıf veya örnek işleyicileri kayıtlı veya olay işlenmiş olarak işaretlenmiş olsa bile teknik yaygın olarak kullanılmayan ancak bu çağrılacak bir seçenek ile bağlı.  
  
 Sınıf işleme ve önizleme olayları nasıl ilişkili olduğu hakkında daha fazla bilgi için bkz: [işlenmiş ve sınıf işleme olarak yönlendirilmiş olayların](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
### <a name="working-around-event-suppression-by-controls"></a>Denetimleri tarafından olay bastırma çevresinde çalışma  
 Önizleme olayları yaygın olarak kullanıldığı bir giriş olaylarını bileşik denetim işleme için bir senaryodur. Bazı durumlarda, belki de daha fazla bilgi taşıyan veya daha fazla belirli bir davranışı olan bileşenle tanımlanan bir olayın yerine için kendi denetiminden kaynaklanan gelen belirli bir olay denetimi yazarı gizler. Örneğin, bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> bastırır <xref:System.Windows.UIElement.MouseLeftButtonDown> ve <xref:System.Windows.UIElement.MouseLeftButtonDown> tarafından gerçekleştirilen kabarcıklanma olaylarını <xref:System.Windows.Controls.Button> veya fare yakalamak ve yükseltme bileşik öğelerini bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> her zaman tarafından gerçekleştirilen olay <xref:System.Windows.Controls.Button> kendisi. Olay ve verileri yine de rota boyunca devam eder ancak çünkü <xref:System.Windows.Controls.Button> olay verisi olarak işaretler <xref:System.Windows.RoutedEventArgs.Handled%2A>, yalnızca özellikle hareket etmesi belirtilen olay işleyicileri `handledEventsToo` durumda çağrılır.  Diğer öğeler, uygulamanızın kök hala denetim gizlenen olayını işlemek için Fırsat isterlerse ile kod işleyicileri eklemek için bir alternatifi: `handledEventsToo` belirtildiği şekilde `true`. Ancak genellikle daha basit bir teknik bir girdi olayının Önizleme denk olarak işlemek yönlendirme yönünü değiştirmek için. Örneğin, bir denetim bastırır varsa <xref:System.Windows.UIElement.MouseLeftButtonDown>, için bir işleyici eklemeyi deneyin <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> yerine. Bu teknik yalnızca temel öğe girdi olayları gibi çalışır <xref:System.Windows.UIElement.MouseLeftButtonDown>. Bu girdi olaylar tünel/Kabarcık çiftleri kullanır, her iki olayı oluşturur ve olay verilerini paylaşır.  
  
 Her tekniğin yan etkileri veya sınırlamaları vardır. Bu noktada olay işleme kabarcıklanma olayını işlemek için beklediğiniz işleyicileri devre dışı bırakabilir ve bu nedenle, genellikle Previ üzerinde hala durumdayken işlenen olayı işaretlemek için iyi bir fikir olmadığını kısıtlamadır Önizleme olay işlemenin yan etkisi olan Rota eni bölümü. Sınırlama `handledEventsToo` tekniği olan, belirtemezsiniz bir `handledEventsToo` işleyicisinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik olarak, olay işleyicisi kodunda işleyici bağlı olduğu bir nesne başvurusu öğesine aldıktan sonra kaydetmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
