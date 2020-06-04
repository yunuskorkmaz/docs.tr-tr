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
ms.openlocfilehash: d8a3c363d1a443db4a0b7633e380562af1913aca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403452"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme (Visual Basic)

[Dize veri türünde](../../../language-reference/data-types/string-data-type.md) bir ifadenin bir kalıbı karşılayıp karşılamadığını öğrenmek Isterseniz, [LIKE işlecini](../../../language-reference/operators/like-operator.md)kullanabilirsiniz.

`Like`iki işlenen alır. Sol işlenen bir dize ifadesidir ve sağ işlenen, eşleştirme için kullanılacak olan kalıbı içeren bir dizedir. `Like``Boolean`dize ifadesinin kalıbı karşılayıp karşılamadığını gösteren bir değer döndürür.

Dize ifadesindeki her karakteri belirli bir karakter, joker karakter, bir karakter listesi veya karakter aralığı ile eşleştirebilirsiniz. Model dizesinde belirtimlerin konumları, dize ifadesinde eşleştirilecek karakterlerin konumlarına karşılık gelir.

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Dize ifadesindeki bir karakteri belirli bir karakterle eşleştirmek için

Belirli karakteri doğrudan model dizesine yerleştirin. Belirli özel karakterlerin köşeli ayraç () içine alınması gerekir `[ ]` . Daha fazla bilgi için bkz. [LIKE işleci](../../../language-reference/operators/like-operator.md).

Aşağıdaki örnek, `myString` tam olarak tek karakter içerip içermediğini sınar `H` .

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Dize ifadesindeki bir karakteri joker karakterle eşleştirmek için

Model dizesine bir soru işareti ( `?` ) koyun. Bu konumdaki geçerli bir karakter, başarılı bir eşleşme yapar.

Aşağıdaki örnek, `myString` tek bir karakteri ve `W` ardından herhangi bir değerin tam olarak iki karakterini içerip içermediğini sınar.

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Dize ifadesindeki bir karakteri bir karakter listesine göre eşleştirmek için

`[ ]`, Model dizesinde köşeli ayraç () koyun ve köşeli ayracın içine karakter listesini koyun. Karakterleri virgülle veya başka bir ayırıcıyla ayırmayın. Listedeki herhangi bir tek karakter başarılı bir eşleşme yapar.

Aşağıdaki örnek, `myString` , veya karakterlerinden yalnızca biri tarafından izlenen geçerli bir karakter olup olmadığını sınar `A` `C` `E` .

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Dize ifadesindeki bir karakteri bir karakter aralığına göre eşleştirmek için

Bir köşeli ayraç ( `[ ]` ) stilini, bir kısa çizgi () ile ayırarak aralığa parantez içine koyun ve parantez içinde en düşük ve en yüksek karakterleri koyun `–` . Aralık içinde herhangi bir tek karakter başarılı bir eşleşme yapar.

Aşağıdaki örnek,,,,, `myString` `num` veya karakterlerinden yalnızca biri tarafından izlenen karakterlerden oluştuğunu sınar `i` `j` `k` `l` `m` `n` .

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.

## <a name="matching-empty-strings"></a>Eşleşen boş dizeler

`Like`diziyi `[]` sıfır uzunluklu bir dize () olarak değerlendirir `""` . `[]`Tüm dize ifadesinin boş olup olmadığını test etmek için kullanabilirsiniz, ancak dize ifadesindeki belirli bir konumun boş olup olmadığını test etmek için kullanamazsınız. Boş bir konum test etmeniz gereken seçeneklerden biri ise, birden `Like` çok kez kullanabilirsiniz.

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Dize ifadesindeki bir karakteri bir karakter listesiyle veya karakter olmadan eşleştirmek için

1. `Like`İşleci aynı dize ifadesinde iki kez çağırın ve iki çağrıyı [OR işleci](../../../language-reference/operators/or-operator.md) ya da [orelı işleciyle](../../../language-reference/operators/orelse-operator.md)bağlayın.

2. İlk yan tümce için model dizesinde `Like` köşeli ayraç () içine alınmış karakter listesini ekleyin `[ ]` .

3. İkinci yan tümce için model dizesinde `Like` , söz konusu konuma herhangi bir karakter yerleştirmeyin.

    Aşağıdaki örnek, yedi basamaklı telefon numarasını `phoneNum` tam olarak üç sayısal basamak, ardından bir boşluk, kısa çizgi ( `–` ), nokta ( `.` ) veya hiç bir karakter ve tam olarak dört sayısal basamakla sınar.

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a>Ayrıca bkz.

- [Karşılaştırma Işleçleri](../../../language-reference/operators/comparison-operators.md)
- [İşleçler ve Ifadeler](index.md)
- [Like İşleci](../../../language-reference/operators/like-operator.md)
- [Dize Veri Türü](../../../language-reference/data-types/string-data-type.md)
