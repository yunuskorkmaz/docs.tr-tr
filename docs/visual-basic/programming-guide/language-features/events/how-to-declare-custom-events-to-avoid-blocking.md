---
title: 'Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 3cb66aed71195d2fd2335fbd59cc499b3dbf808e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646932"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme (Visual Basic)
Bu bir olay işleyicisi değil sonraki olay işleyicileri engelle önemli olduğu durumlarda bazı durumlar vardır. Özel olaylar, olay işleyicileri zaman uyumsuz olarak çağırmak olay izin verin.  
  
 Varsayılan olarak, yedekleme deposu için bir olay bildirimi seri olarak tüm olay işleyicileri birleştiren bir çok noktaya yayın temsilci alandır. Bu, bir işleyici tamamlanması uzun sürüyorsa, işlem tamamlanana kadar diğer işleyicilerin engellediği anlamına gelir. (Uyum gösteren olay işleyicileri hiçbir zaman uzun veya olası engelleme işlemleri gerçekleştirmeniz gerekir.)  
  
 Visual Basic sağlar olayları varsayılan uygulaması kullanmak yerine özel bir olay olay işleyicileri yürütülecek zaman uyumsuz olarak kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `AddHandler` erişimci ekler her işleyicisi için temsilci `Click` olaya bir <xref:System.Collections.ArrayList> depolanan `EventHandlerList` alan.  
  
 Ne zaman, başlatır kod `Click` olayı `RaiseEvent` erişimci tüm olay işleyici temsilcileri kullanarak zaman uyumsuz olarak çağırır <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> yöntemi. Bu yöntem, bir çalışan iş parçacığı üzerinde her işleyiciyi çağırır ve işleyicileri birbirine engellemek için hemen döndürür.  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
