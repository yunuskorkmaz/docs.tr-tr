---
title: "Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)"
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
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eec9a2fc687f481ab40313e35cbde81c25b81ae8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Olayları](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Nasıl yapılır: engellemekten Kaçınacak şekilde özel olayları bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
