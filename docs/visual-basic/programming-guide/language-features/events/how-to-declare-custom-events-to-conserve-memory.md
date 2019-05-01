---
title: 'Nasıl yapılır: (Visual Basic) bellekten kazanacak şekilde özel olayları bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: e4132f51f4dd85ad964042d05f7c5bc0a2e6e3cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973166"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Nasıl yapılır: (Visual Basic) bellekten kazanacak şekilde özel olayları bildirme
Uygulamanın bellek kullanımı düşük tutmak önemlidir, çeşitli koşullar vardır. Özel olaylar yalnızca işleme olayları için bellek kullanmak için uygulamayı sağlar.  
  
 Bir sınıf bir olay bildirir, varsayılan olarak, derleyici olay bilgilerini depolamak bir alan için bellek ayırır. Bir sınıf birçok kullanılmayan olay varsa, bunlar gereksiz yere belleği yararlanın.  
  
 Visual Basic sağlayan olaylar varsayılan uygulamasını kullanmak yerine, bellek kullanımı daha dikkatli bir şekilde yönetmek için özel olaylar kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıfın bir örneğini kullanır. <xref:System.ComponentModel.EventHandlerList> depolanan sınıfı `Events` alan, kullanım olaylarına ilişkin bilgileri depolamak için. <xref:System.ComponentModel.EventHandlerList> Temsilciler tutmak için tasarlanan bir en iyi duruma getirilmiş listesi sınıfı.  
  
 Tüm olayları sınıfı kullanımda `Events` her bir olay işleme hangi yöntemi izlemek için alan.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.EventHandlerList>
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Nasıl yapılır: Engellemekten Kaçınacak şekilde özel olayları bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
