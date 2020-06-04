---
title: 'Nasıl yapılır: Etiket Deyimleri'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 8f04d592c51b6a0630bfe623fd3574555aef9ff8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403219"
---
# <a name="how-to-label-statements-visual-basic"></a>Nasıl yapılır: Deyimler (Visual Basic)

Ekstre blokları, iki nokta üst üste ile ayrılmış kod satırlarından oluşur. Bir tanımlayıcı dize veya tamsayının önünde bulunan kod satırları *etiketlenecek*şekilde söylenir. Deyim etiketleri, bir kod satırını, gibi deyimlerle kullanılmak üzere belirlemek üzere işaretlemek için kullanılır `On Error Goto` .

Etiketler, programlama öğelerini tanımlayan ya da tamsayı değişmez değerleri gibi geçerli Visual Basic tanımlayıcı olabilir. Bir etiket, kaynak kodu satırının başında görünmelidir ve bunun ardından iki nokta üst üste gelmelidir ve bunun ardından aynı satırdaki bir deyimin takip edilip edilmeyeceğini dikkate alınmalıdır.

Derleyici, satırın başlangıcının önceden tanımlanmış tanımlayıcıyla eşleşip eşleşmediğini denetleyerek etiketleri tanımlar. Değilse, derleyici bir etiket olduğunu varsayar.

Etiketler kendi bildirim alanına sahiptir ve diğer tanımlayıcılarla karışmaz. Etiketin kapsamı yöntemin gövdesidir. Etiket bildirimi herhangi bir belirsiz durumda önceliklidir.

> [!NOTE]
> Etiketler yalnızca yöntemlerin içindeki yürütülebilir deyimlerde kullanılabilir.

## <a name="to-label-a-line-of-code"></a>Bir kod satırını etiketlemek için

Kaynak kodu satırının başında bir tanımlayıcı ve sonra iki nokta üst üste koyun.

Örneğin, aşağıdaki kod satırları sırasıyla ve ile etiketlidir `Jump` `120` :

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a>Ayrıca bkz.

- [Deyimler](../language-features/statements.md)
- [Bildirilen Öğe Adları](../language-features/declared-elements/declared-element-names.md)
- [Program yapısı ve kod kuralları](program-structure-and-code-conventions.md)
