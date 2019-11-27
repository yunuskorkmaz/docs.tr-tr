---
title: 'Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme'
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
ms.openlocfilehash: 49328a72c2cff78b8fe13ca73209d224495ad7a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343632"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme (Visual Basic)

[Dize veri türünde](../../../../visual-basic/language-reference/data-types/string-data-type.md) bir ifadenin bir kalıbı karşılayıp karşılamadığını öğrenmek Isterseniz, [LIKE işlecini](../../../../visual-basic/language-reference/operators/like-operator.md)kullanabilirsiniz.

`Like` iki işlenen alır. Sol işlenen bir dize ifadesidir ve sağ işlenen, eşleştirme için kullanılacak olan kalıbı içeren bir dizedir. `Like`, dize ifadesinin kalıbı karşılayıp karşılamadığını gösteren bir `Boolean` değeri döndürür.

Dize ifadesindeki her karakteri belirli bir karakter, joker karakter, bir karakter listesi veya karakter aralığı ile eşleştirebilirsiniz. Model dizesinde belirtimlerin konumları, dize ifadesinde eşleştirilecek karakterlerin konumlarına karşılık gelir.

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Dize ifadesindeki bir karakteri belirli bir karakterle eşleştirmek için

Belirli karakteri doğrudan model dizesine yerleştirin. Belirli özel karakterler köşeli ayraç içine alınmalıdır (`[ ]`). Daha fazla bilgi için bkz. [LIKE işleci](../../../../visual-basic/language-reference/operators/like-operator.md).

Aşağıdaki örnek, `myString` tam olarak tek karakter `H`mi oluştuğunu sınar.

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Dize ifadesindeki bir karakteri joker karakterle eşleştirmek için

Bir soru işareti (`?`), model dizesine koyun. Bu konumdaki geçerli bir karakter, başarılı bir eşleşme yapar.

Aşağıdaki örnek, `myString` tek karakterlik `W` ve ardından her değerin tam olarak iki karakterini içerip içermediğini sınar.

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Dize ifadesindeki bir karakteri bir karakter listesine göre eşleştirmek için

Köşeli parantezleri (`[ ]`), model dizesine koyun ve köşeli ayracın içine karakter listesini koyun. Karakterleri virgülle veya başka bir ayırıcıyla ayırmayın. Listedeki herhangi bir tek karakter başarılı bir eşleşme yapar.

Aşağıdaki örnek, `myString` `A`, `C`veya `E`karakterlerden yalnızca birini içeren herhangi bir geçerli karakterden oluştuğunu sınar.

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Dize ifadesindeki bir karakteri bir karakter aralığına göre eşleştirmek için

Köşeli parantezleri (`[ ]`), model dizesine koyun ve köşeli ayraçlar içinde, kısa çizgi (`–`) ile ayırarak aralığa en düşük ve en yüksek karakterleri koyun. Aralık içinde herhangi bir tek karakter başarılı bir eşleşme yapar.

Aşağıdaki örnek, `myString` karakterlerin `num` ve `i`, `j`, `k`, `l`, `m`veya `n`karakterlerinden birini içerip içermediğini sınar.

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.

## <a name="matching-empty-strings"></a>Eşleşen boş dizeler

`Like`, dizi `[]` sıfır uzunluklu bir dize (`""`) olarak değerlendirir. Tüm dize ifadesinin boş olup olmadığını test etmek için `[]` kullanabilirsiniz, ancak dize ifadesindeki belirli bir konumun boş olup olmadığını test etmek için kullanamazsınız. Boş bir konum için test etmeniz gereken seçeneklerden biri ise, `Like` birden çok kez kullanabilirsiniz.

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Dize ifadesindeki bir karakteri bir karakter listesiyle veya karakter olmadan eşleştirmek için

1. Aynı dize ifadesinde `Like` işlecini iki kez çağırın ve iki çağrıyı [OR işleci](../../../../visual-basic/language-reference/operators/or-operator.md) ya da [Orelu işleciyle](../../../../visual-basic/language-reference/operators/orelse-operator.md)bağlayın.

2. İlk `Like` yan tümcesinin örüntüsünün dizesinde, köşeli ayraç içine alınmış karakter listesini ekleyin (`[ ]`).

3. İkinci `Like` yan tümcesinin model dizesinde, söz konusu konuma herhangi bir karakter yerleştirmeyin.

    Aşağıdaki örnek, yedi basamaklı telefon numarası `phoneNum` tam olarak üç sayısal basamak, ardından bir boşluk, kısa çizgi (`–`), bir nokta (`.`) veya hiç karakter ve tam olarak dört sayısal basamak için sınar.

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a>Ayrıca bkz.

- [Karşılaştırma İşleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Like İşleci](../../../../visual-basic/language-reference/operators/like-operator.md)
- [String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)
