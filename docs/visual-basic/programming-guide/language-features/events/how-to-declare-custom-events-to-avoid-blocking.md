---
title: 'Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: a9f9529d468a036d81c4e436429cbdb3207efd6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405163"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme (Visual Basic)
Bir olay işleyicisinin sonraki olay işleyicilerini engellemediğinden çok önemli olduğu durumlar vardır. Özel olaylar olayın olay işleyicilerini zaman uyumsuz olarak çağırmasını sağlar.  
  
 Varsayılan olarak, bir olay bildirimi için yedekleme depolama alanı, tüm olay işleyicilerini tamamen birleştiren bir çok noktaya yayın temsilcisidir. Bu, bir işleyicinin tamamlanması uzun zaman alıyorsa, diğer işleyicileri tamamlanana kadar engeller. (İyi davranmış olay işleyicileri asla uzun veya olası engelleme işlemleri gerçekleştirmemelidir.)  
  
 Visual Basic tarafından sağlanan varsayılan olay uygulamasını kullanmak yerine, olay işleyicilerini zaman uyumsuz olarak yürütmek için özel bir olay kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, erişimci, `AddHandler` olayın her işleyicisine ait temsilciyi `Click` <xref:System.Collections.ArrayList> alanında depolanan öğesine ekler `EventHandlerList` .  
  
 Kod olayı harekete geçirirse `Click` , `RaiseEvent` erişimci yöntemini kullanarak tüm olay işleyicisi temsilcilerinizi zaman uyumsuz olarak çağırır <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> . Bu yöntem bir çalışan iş parçacığında her işleyiciyi çağırır ve hemen döndürür, bu nedenle işleyiciler birbirini engelleyemez.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Olaylar](index.md)
- [Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](how-to-declare-custom-events-to-conserve-memory.md)
