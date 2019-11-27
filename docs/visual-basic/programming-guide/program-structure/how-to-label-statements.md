---
title: 'Nasıl yapılır: Etiket Deyimleri'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: be116ac8046c43e89e44c2d9127c6131e4dfaa52
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347376"
---
# <a name="how-to-label-statements-visual-basic"></a>Nasıl yapılır: Deyimler (Visual Basic)

Ekstre blokları, iki nokta üst üste ile ayrılmış kod satırlarından oluşur. Bir tanımlayıcı dize veya tamsayının önünde bulunan kod satırları *etiketlenecek*şekilde söylenir. Deyim etiketleri, `On Error Goto`gibi deyimlerle kullanım için tanımlamak üzere bir kod satırı işaretlemek için kullanılır.

Etiketler, programlama öğelerini tanımlayan ya da tamsayı değişmez değerleri gibi geçerli Visual Basic tanımlayıcı olabilir. Bir etiket, kaynak kodu satırının başında görünmelidir ve bunun ardından iki nokta üst üste gelmelidir ve bunun ardından aynı satırdaki bir deyimin takip edilip edilmeyeceğini dikkate alınmalıdır.

Derleyici, satırın başlangıcının önceden tanımlanmış tanımlayıcıyla eşleşip eşleşmediğini denetleyerek etiketleri tanımlar. Değilse, derleyici bir etiket olduğunu varsayar.

Etiketler kendi bildirim alanına sahiptir ve diğer tanımlayıcılarla karışmaz. Etiketin kapsamı yöntemin gövdesidir. Etiket bildirimi herhangi bir belirsiz durumda önceliklidir.

> [!NOTE]
> Etiketler yalnızca yöntemlerin içindeki yürütülebilir deyimlerde kullanılabilir.

## <a name="to-label-a-line-of-code"></a>Bir kod satırını etiketlemek için

Kaynak kodu satırının başında bir tanımlayıcı ve sonra iki nokta üst üste koyun.

Örneğin, aşağıdaki kod satırları sırasıyla `Jump` ve `120`etiketlidir:

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a>Ayrıca bkz.

- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
