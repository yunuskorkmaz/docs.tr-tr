---
title: 'Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3cc2d3ea57f1a8daf704c2c929baf3f2acf78c17
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345126"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)
Bir uygulamanın bellek kullanımını düşük tutması önemli olduğunda bazı durumlar vardır. Özel olaylar, uygulamanın yalnızca işlediği olaylar için belleği kullanmasına izin verir.  
  
 Varsayılan olarak, bir sınıf bir olay bildirdiğini derleyici, olay bilgilerini depolamak için bir alan için bellek ayırır. Bir sınıfta çok sayıda kullanılmamış olay varsa, bu, belleğin sorunsuz bir şekilde sürmasını isterler.  
  
 Visual Basic sağladığı olayların varsayılan uygulamasını kullanmak yerine, bellek kullanımını daha dikkatli bir şekilde yönetmek için özel olayları kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıfı, kullanımdaki olaylar hakkında bilgi depolamak için `Events` alanında depolanan <xref:System.ComponentModel.EventHandlerList> sınıfının bir örneğini kullanır. <xref:System.ComponentModel.EventHandlerList> sınıfı, temsilcileri tutmak için tasarlanan iyileştirilmiş bir liste sınıfıdır.  
  
 Sınıftaki tüm olaylar, her bir olayın hangi yöntemlerin işleme olduğunu izlemek için `Events` alanını kullanır.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.EventHandlerList>
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
