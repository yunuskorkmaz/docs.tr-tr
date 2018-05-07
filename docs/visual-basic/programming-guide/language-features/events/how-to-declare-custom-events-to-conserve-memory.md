---
title: 'Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: d19c91d66e458ca2317dc049d517b92fa7406ef6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)
Bir uygulama bellek kullanımı düşük tutmak önemlidir, çeşitli koşullar vardır. Özel olaylar, işleme olayları yalnızca bellek kullanmak için uygulamayı izin verin.  
  
 Bir sınıf bir olay bildirir, varsayılan olarak, derleyicinin olay bilgilerini depolamak bir alan için bellek ayırır. Bir sınıf çok sayıda kullanılmayan olay varsa, bunlar gereksiz yere bellekte alın.  
  
 Visual Basic sağlar olayları varsayılan uygulaması kullanmak yerine, bellek kullanımı daha dikkatli bir şekilde yönetmek için özel olaylar kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıfı tek bir örneğini kullanır. <xref:System.ComponentModel.EventHandlerList> sınıfı, depolanan `Events` kullanımda olaylar hakkında bilgi depolamak için alan. <xref:System.ComponentModel.EventHandlerList> Sınıftır temsilciler tutmak için tasarlanmış bir en iyi duruma getirilmiş listesi.  
  
 Tüm olayları sınıfı kullanımda `Events` hangi yöntemlerin her olay işleme izlemek için alan.  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.EventHandlerList>  
 [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
