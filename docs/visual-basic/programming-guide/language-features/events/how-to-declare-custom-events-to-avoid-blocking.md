---
title: "Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a36c855efb67752674615a61f2fa701974ce5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Olayları](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Nasıl yapılır: bellekten kazanacak şekilde özel olayları bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
