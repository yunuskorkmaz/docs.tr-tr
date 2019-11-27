---
title: 'Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 8d73d9c4590afb33e7176f647069cafcb3a9d7d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345142"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme (Visual Basic)
Bir olay işleyicisinin sonraki olay işleyicilerini engellemediğinden çok önemli olduğu durumlar vardır. Özel olaylar olayın olay işleyicilerini zaman uyumsuz olarak çağırmasını sağlar.  
  
 Varsayılan olarak, bir olay bildirimi için yedekleme depolama alanı, tüm olay işleyicilerini tamamen birleştiren bir çok noktaya yayın temsilcisidir. Bu, bir işleyicinin tamamlanması uzun zaman alıyorsa, diğer işleyicileri tamamlanana kadar engeller. (İyi davranmış olay işleyicileri asla uzun veya olası engelleme işlemleri gerçekleştirmemelidir.)  
  
 Visual Basic tarafından sağlanan varsayılan olay uygulamasını kullanmak yerine, olay işleyicilerini zaman uyumsuz olarak yürütmek için özel bir olay kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `AddHandler` erişimcisi, `Click` olayının her işleyicisi için temsilciyi `EventHandlerList` alanında depolanan bir <xref:System.Collections.ArrayList> ekler.  
  
 Kod `Click` olayını harekete geçirirse, `RaiseEvent` erişimci <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> yöntemini kullanarak tüm olay işleyicisi temsilcilerinizi zaman uyumsuz olarak çağırır. Bu yöntem bir çalışan iş parçacığında her işleyiciyi çağırır ve hemen döndürür, bu nedenle işleyiciler birbirini engelleyemez.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
