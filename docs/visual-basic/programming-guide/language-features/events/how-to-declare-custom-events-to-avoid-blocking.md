---
title: 'Nasıl yapılır: (Visual Basic) engellemekten Kaçınacak şekilde özel olayları bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: e1fed68f4abffb0e20230f55b0ddeffc63f7c78d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691550"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Nasıl yapılır: (Visual Basic) engellemekten Kaçınacak şekilde özel olayları bildirme
Sonraki olay işleyicileri engelleme yapmadığından bu bir olay işleyicisi önemli olduğunda bazı durumlar vardır. Özel olaylar, olay, olay işleyicileri zaman uyumsuz olarak aramak izin verin.  
  
 Varsayılan olarak, bir olay bildirimi için yedekleme depolama alanı, tüm olay işleyicilerine seri olarak birleştiren çok noktaya yayın bir temsilcidir. Bu, bir işleyici tamamlanması uzun sürerse, işlem tamamlanana kadar diğer işleyicilerin engellediği anlamına gelir. (Uyum gösteren olay işleyicileri hiçbir zaman uzun veya olası engelleme işlemleri gerçekleştirmeniz gerekir.)  
  
 Visual Basic sağlayan olaylar varsayılan uygulamasını kullanmak yerine, olay işleyicileri zaman uyumsuz olarak yürütmek için bir özel olay kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `AddHandler` erişimci ekliyor her işleyicisi için temsilci `Click` olayına bir <xref:System.Collections.ArrayList> depolanan `EventHandlerList` alan.  
  
 Harekete geçirirse kod `Click` olay `RaiseEvent` erişimci tüm olay işleyicisi temsilcileri kullanarak zaman uyumsuz olarak çağırır <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> yöntemi. Bu yöntem, her bir iş parçacığı işleyicisini çağırır ve işleyicileri birbirine engellemek için hemen döndürür.  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Nasıl yapılır: Bellekten kazanacak şekilde özel olayları bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
