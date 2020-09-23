---
title: 'Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 78934e3e5ae7d5a3f5867c99a9f1db760c65ecbf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075128"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)

Bir uygulamanın bellek kullanımını düşük tutması önemli olduğunda bazı durumlar vardır. Özel olaylar, uygulamanın yalnızca işlediği olaylar için belleği kullanmasına izin verir.  
  
 Varsayılan olarak, bir sınıf bir olay bildirdiğini derleyici, olay bilgilerini depolamak için bir alan için bellek ayırır. Bir sınıfta çok sayıda kullanılmamış olay varsa, bu, belleğin sorunsuz bir şekilde sürmasını isterler.  
  
 Visual Basic sağladığı olayların varsayılan uygulamasını kullanmak yerine, bellek kullanımını daha dikkatli bir şekilde yönetmek için özel olayları kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  

 Bu örnekte, sınıfı, <xref:System.ComponentModel.EventHandlerList> `Events` Kullanımdaki olaylar hakkında bilgi depolamak için, alanında depolanan sınıfının bir örneğini kullanır. <xref:System.ComponentModel.EventHandlerList>Sınıfı, temsilcileri tutmak için tasarlanan iyileştirilmiş bir liste sınıfıdır.  
  
 Sınıftaki tüm olaylar, `Events` her bir olayın hangi yöntemlerin işleme olduğunu izlemek için alanını kullanır.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.EventHandlerList>
- [Ekinlikler](index.md)
- [Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme](how-to-declare-custom-events-to-avoid-blocking.md)
