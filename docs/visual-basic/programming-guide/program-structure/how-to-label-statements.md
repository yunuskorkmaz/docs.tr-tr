---
title: 'Nasıl yapılır: Label deyimleri (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 6b442b5a0ad731cfc490a7387c78ac9279dddaf0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961331"
---
# <a name="how-to-label-statements-visual-basic"></a>Nasıl yapılır: Label deyimleri (Visual Basic)
Ekstre blokları, iki nokta üst üste ile ayrılmış kod satırlarından oluşur. Bir tanımlayıcı dize veya tamsayının önünde bulunan kod satırları etiketlenecek şekilde söylenir. Deyim etiketleri, bir kod satırını, gibi deyimlerle `On Error Goto`kullanılmak üzere belirlemek üzere işaretlemek için kullanılır.  
  
 Etiketler, programlama öğelerini tanımlayan ya da tamsayı değişmez değerleri gibi geçerli Visual Basic tanımlayıcı olabilir. Bir etiket, kaynak kodu satırının başında görünmelidir ve bunun ardından iki nokta üst üste gelmelidir ve bunun ardından aynı satırdaki bir deyimin takip edilip edilmeyeceğini dikkate alınmalıdır.  
  
 Derleyici, satırın başlangıcının önceden tanımlanmış tanımlayıcıyla eşleşip eşleşmediğini denetleyerek etiketleri tanımlar. Değilse, derleyici bir etiket olduğunu varsayar.  
  
 Etiketler kendi bildirim alanına sahiptir ve diğer tanımlayıcılarla karışmaz. Etiketin kapsamı yöntemin gövdesidir. Etiket bildirimi herhangi bir belirsiz durumda önceliklidir.  
  
> [!NOTE]
> Etiketler yalnızca yöntemlerin içindeki yürütülebilir deyimlerde kullanılabilir.  
  
### <a name="to-label-a-line-of-code"></a>Bir kod satırını etiketlemek için  
  
- Kaynak kodu satırının başında bir tanımlayıcı ve sonra iki nokta üst üste koyun.  
  
     Örneğin, aşağıdaki kod satırları sırasıyla ve `Jump` `120`ile etiketlidir:  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
