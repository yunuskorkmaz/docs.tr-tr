---
title: 'Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: aef378bfc32d6deff431a2caac1261a6cd7520c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655218"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme (Visual Basic)
Bir ifadenin olmadığını öğrenmek istiyorsanız [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md) kullanabileceğiniz sonra bir desen karşılayan [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like` iki işlenen alır. Sol işleneni bir dize ifadesi ve sağ işleneni eşleştirmek için kullanılacak bir desen içeren bir dizedir. `Like` döndüren bir `Boolean` dize ifadesi düzeni karşılayıp karşılamadığını belirten değer.  
  
 Belirli bir karakter, bir joker karakter, karakter listesini veya bir karakter aralığı karşı dize ifadesindeki her karakter eşleştirebilirsiniz. Desen dizesinde belirtimleri konumlarını string ifadesinde eşleştirilmesini karakterleri konumlarını karşılık gelir.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Belirli bir karakterin karşı string ifadesinde bir karakterle eşleştirmek için  
  
-   Belirli karakterlerin doğrudan düzeni dizesinde yerleştirin. Özel karakterleri parantez içine alınmalıdır (`[ ]`). Daha fazla bilgi için bkz: [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     Aşağıdaki örnek testleri olup olmadığını `myString` tam olarak tek karakterinin oluşur `H`.  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Bir joker karakter karşı string ifadesinde bir karakterle eşleştirmek için  
  
-   Bir soru işareti koyma (`?`) desen dizesi içinde. Bu konumda herhangi bir geçerli karakter başarılı bir eşleşme yapar.  
  
     Aşağıdaki örnek testleri olup olmadığını `myString` tek karakteri oluşur `W` herhangi bir değeri tam olarak iki karakterle devam etmelidir.  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Karakterden oluşan bir liste karşı dize ifadesinde bir karakterle eşleştirmek için  
  
-   Köşeli ayraçlar put (`[ ]`) deseni dize ve karakter listesinin put ayraç içinde. Karakterleri, virgül veya başka bir ayırıcı ayırmayın. Herhangi bir tek karakteri başarılı bir eşleşme yapar.  
  
     Aşağıdaki örnek testleri olup olmadığını `myString` karakterleri tam olarak biri tarafından izlenen herhangi bir geçerli karakter oluşan `A`, `C`, veya `E`.  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     Bu eşleştirme büyük küçük harfe duyarlı olduğunu unutmayın.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Karakter aralığı karşı string ifadesinde bir karakterle eşleştirmek için  
  
-   Köşeli ayraçlar put (`[ ]`) desen dizesi ve en düşük ve en yüksek karakter aralığı içinde put ayraç içinde bir tire ile ayrılmış (`–`). Aralık içinde herhangi bir tek karakteri başarılı bir eşleşme yapar.  
  
     Aşağıdaki örnek testleri olup olmadığını `myString` karakterden oluşan `num` karakterleri tam olarak biri tarafından izlenen `i`, `j`, `k`, `l`, `m`, veya `n`.  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     Bu eşleştirme büyük küçük harfe duyarlı olduğunu unutmayın.  
  
## <a name="matching-empty-strings"></a>Eşleşen boş dizeler  
 `Like` sıra işler `[]` sıfır uzunlukta bir dize olarak (`""`). Kullanabileceğiniz `[]` tüm dize ifadesi boş olan, ancak dize ifadesi belirli bir konumda boşsa, test etmek için kullanamazsınız olup olmadığını sınamak için. Boş bir konum seçeneklerden birini ise kullanabileceğiniz için test yapmanız `Like` birden çok kez.  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Bir karakter dizesi bir ifade listesini karşı karakterleri veya herhangi bir karakter eşleştirmek için  
  
1.  Çağrı `Like` işlecinin iki kere aynı dize ifadesi ve iki çağrıları biriyle bağlanmak [veya işleci](../../../../visual-basic/language-reference/operators/or-operator.md) veya [OrElse işleci](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2.  İlk düzeni dizesinde `Like` yan tümcesi, ayraç karakter listede yer (`[ ]`).  
  
3.  İkinci düzeni dizesinde `Like` yan tümcesi, herhangi bir karakter konumunda söz konusu koymayın.  
  
     Aşağıdaki örnekte yedi basamaklı telefon numarasını testleri `phoneNum` için tam olarak üç Sayısal basamaklar, ardından bir boşluk, tire (`–`), nokta (`.`), veya hiçbir karakter tarafından tam olarak dört Sayısal basamaklar, ardından.  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Karşılaştırma İşleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Like İşleci](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)
