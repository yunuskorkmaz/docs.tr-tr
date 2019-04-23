---
title: 'Nasıl yapılır: Bir dizeyi belirli bir desene (Visual Basic) göre eşleştirme'
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
ms.openlocfilehash: c14aa35ce15549ad9eccabe2330a7c43b6795140
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316277"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Nasıl yapılır: Bir dizeyi belirli bir desene (Visual Basic) göre eşleştirme
Bir ifade kaydolmadığı istiyorsanız [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md) sonra kullanabileceğiniz bir desen karşılayan [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like` iki işlenen alır. Sol işlenen bir dize ifadesi ve sağ işlenen eşleştirmek için kullanılacak bir desen içeren bir dizedir. `Like` döndürür bir `Boolean` dize ifade desenini karşılayıp karşılamadığını belirten değer.  
  
 Belirli bir karakter, bir joker karakter, karakter listesini veya bir karakter aralığı dize ifadeyi her karaktere eşleştirir. Desen dizesi belirtimlerinde konumlarını dize ifadesinin eşleştirilecek karakterleri konumlarını karşılık gelir.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Bir karakter, belirli bir karakter dizesi ifadeyi eşleştirilecek  
  
-   Belirli karakter doğrudan deseni dizesinde yerleştirin. Özel karakterleri ayraçlar içine alınmalıdır (`[ ]`). Daha fazla bilgi için [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     Aşağıdaki örnek testleri olmadığını `myString` tam olarak tek karakterden oluşan `H`.  
  
     [!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Bir karakter, bir joker karakter dizesi ifadeyi eşleştirilecek  
  
-   Bir soru işareti (`?`) deseni dizesi içinde. Bu konumda herhangi bir geçerli karakter başarılı bir eşleşme yapar.  
  
     Aşağıdaki örnek testleri olmadığını `myString` tek karakterden oluşan `W` herhangi bir değeri tam olarak iki karakterlerle devam eder.  
  
     [!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Bir karakter, karakter dize ifadesinin bir listeyle eşleşecek şekilde  
  
-   Köşeli ayraçlar yerleştirin (`[ ]`) desen dizesi ve karakterlerin listesini put köşeli ayraçlar içinde. Karakterleri, virgül veya başka bir ayırıcı ile ayırmayın. Herhangi bir tek karakterle başarılı bir eşleşme yapar.  
  
     Aşağıdaki örnek testleri olmadığını `myString` karakter tam olarak biri tarafından izlenen herhangi bir geçerli karakter oluşan `A`, `C`, veya `E`.  
  
     [!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]  
  
     Bu eşleşme büyük küçük harfe duyarlı olduğunu unutmayın.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Bir karakter, karakter aralığı dize ifadeyi eşleştirilecek  
  
-   Köşeli ayraçlar yerleştirin (`[ ]`) deseni dizesinde ve en düşük ve en yüksek karakter aralığında put köşeli ayraçlar içinde ayrılmış bir tire işaretiyle (`–`). Herhangi bir tek karakterle aralıktaki başarılı bir eşleşme yapar.  
  
     Aşağıdaki örnek testleri olmadığını `myString` karakterden oluşan `num` karakter tam olarak biri tarafından izlenen `i`, `j`, `k`, `l`, `m`, veya `n`.  
  
     [!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]  
  
     Bu eşleşme büyük küçük harfe duyarlı olduğunu unutmayın.  
  
## <a name="matching-empty-strings"></a>Eşleşen boş dizeler  
 `Like` sıra işler `[]` sıfır uzunlukta bir dize olarak (`""`). Kullanabileceğiniz `[]` tüm dize ifadesi boş, ancak dize ifadesi belirli bir konumda boş olup olmadığını test etmek için kullanamazsınız olup olmadığını test etmek için. Boş bir konum seçenekleri ise kullanabileceğiniz için test etmeniz `Like` birden çok kez.  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Bir karakter, karakter veya hiçbir karakter dize ifadesi bir listesiyle eşleşecek şekilde  
  
1. Çağrı `Like` işlecinin iki kez aynı dize ifadesi ve iki çağrıları ile bağlanma [veya işleci](../../../../visual-basic/language-reference/operators/or-operator.md) veya [OrElse işleci](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2. İlk kez deseni dizesinde `Like` yan tümcesi, parantez içine alınmış karakter listede yer (`[ ]`).  
  
3. İkinci deseni dizesinde `Like` yan tümcesi, herhangi bir karakter konumunda söz konusu koymayın.  
  
     Aşağıdaki örnek, yedi rakamlı bir telefon numarasını testleri `phoneNum` için tam olarak üç sayısal basamak, ardından bir boşluk, tire (`–`), nokta (`.`), veya hiçbir karakter tam olarak dört sayısal basamak, ardından.  
  
     [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Karşılaştırma İşleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Like İşleci](../../../../visual-basic/language-reference/operators/like-operator.md)
- [String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)
