---
title: Boş Değerler
description: 'F # programlama dilinde null değerin nasıl kullanıldığını öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 3b2c7ebe7b8eff08f7c3e76b9715ccab1bbd5d36
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558354"
---
# <a name="null-values"></a>Boş Değerler

Bu konu, F # içinde null değerin nasıl kullanıldığını açıklar.

## <a name="null-value"></a>Null değer

Null değer, normal olarak değerler veya değişkenler için F # içinde kullanılmaz. Ancak, bazı durumlarda null değeri anormal bir değer olarak görüntülenir. F # içinde tanımlı bir tür varsa, [AllowNullLiteral](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-allownullliteralattribute.html#Value) özniteliği türüne uygulanmadığı sürece null değeri normal bir değer olarak izin verilmez. Bir tür başka bir .NET dilinde tanımlanırsa null değeri olası bir değerdir ve bu tür türlerle birlikte çalışırken, F # kodunuz null değerlerle karşılaşabilir.

F # ' da tanımlanan ve tamamen F # ' dan kullanılan bir tür için, F # kitaplığını doğrudan kullanarak null değer oluşturmanın tek yolu [Unchecked. defaultof](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators-unchecked.html#defaultof) veya [Array. sıfırlaması Create](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate)kullanmaktır. Ancak, diğer .NET dillerinden kullanılan bir F # türü için veya bu türü F .NET Framework # ' da yazılı olmayan bir API ile kullanıyorsanız, null değerler oluşabilir.

`option`Başka bir .net dilinde olası null değeri olan bir başvuru değişkeni kullandığınızda, F # türünü kullanabilirsiniz. Null yerine bir F # `option` türüyle, nesne yoksa seçenek değerini kullanırsınız `None` . Bir nesne olduğunda, seçenek değerini `Some(obj)` nesnesiyle birlikte kullanırsınız `obj` . Daha fazla bilgi için bkz. [Seçenekler](../options.md). İçin,,,, için bir değeri yine de bir seçeneğe pakettemediğini unutmayın `null` `Some x` `x` `null` . Bu nedenle, `None` bir değer olduğunda kullanmanız önemlidir `null` .

`null`Anahtar sözcüğü, F # dilinde geçerli bir anahtar sözcüktür ve .NET Framework API 'leri ya da başka bir .net dilinde yazılmış diğer API 'lerle çalışırken kullanmanız gerekir. Bir .NET API çağırdığınızda ve dönüş değerini ya da bir çıkış parametresini bir .NET yöntem çağrısından yorumlayacağınız zaman, null değere ihtiyacınız olabilecek iki durum vardır.

Bir .NET yöntemine null değer geçirmek için, `null` çağıran koddaki anahtar sözcüğünü kullanmanız yeterlidir. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

.NET yönteminden alınan null bir değeri yorumlamak için, varsa, model eşleştirmeyi kullanın. Aşağıdaki kod örneği, `ReadLine` bir giriş akışının sonunu okumayı denediğinde ' den döndürülen null değeri yorumlamak için model eşleştirmeyi nasıl kullanacağınızı gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

F # türleri için null değerler, ' ı kullandığınızda gibi başka yollarla da oluşturulabilir `Array.zeroCreate` `Unchecked.defaultof` . Null değerleri kapsüllenmeye devam etmek için bu tür koda dikkatli olmanız gerekir. Yalnızca F # için tasarlanan bir kitaplıkta, her işlevde null değerler denetlemeniz gerekmez. Diğer .NET dilleri ile birlikte çalışabilirlik için bir kitaplık yazıyorsanız, null giriş parametrelerine yönelik denetimler eklemeniz ve `ArgumentNullException` C# veya Visual Basic kodunda olduğu gibi bir oluşturmanız gerekebilir.

Rastgele bir değerin null olup olmadığını denetlemek için aşağıdaki kodu kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Değerler](index.md)
- [Eşleşme İfadeleri](../match-expressions.md)
