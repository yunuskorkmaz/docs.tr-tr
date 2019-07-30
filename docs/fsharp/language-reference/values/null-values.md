---
title: Boş Değerler
description: Null değerin F# programlama dilinde nasıl kullanıldığını öğrenin.
ms.date: 03/22/2019
ms.openlocfilehash: 2038c0a461fec9884c51edd50c3c9f336104e30e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630810"
---
# <a name="null-values"></a>Boş Değerler

Bu konu, içinde F#null değerin nasıl kullanıldığını açıklar.

## <a name="null-value"></a>Null değer

Null değer, normal olarak değerler veya değişkenler F# için kullanılmaz. Ancak, bazı durumlarda null değeri anormal bir değer olarak görüntülenir. İçinde F#tanımlı bir tür varsa, [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) özniteliği türüne uygulanmamışsa, null değeri normal bir değer olarak izin verilmez. Bir tür başka bir .NET dilinde tanımlanırsa null değeri olası bir değerdir ve bu tür türlerle birlikte çalışırken F# kodunuz null değerlerle karşılaşabilir.

İçinde F# tanımlı ve F#tamamen ' den kullanılan bir tür için, F# kitaplığı doğrudan kullanarak null değer oluşturmanın tek yolu [Unchecked. defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) veya [Array. sıfırlaması Create](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)kullanmaktır. Ancak, diğer .NET F# dillerinden kullanılan bir tür için veya bu türü, .NET Framework gibi ' de F#yazılı olmayan bir API ile kullanıyorsanız, null değerler oluşabilir.

İçindeki `option` F# türü, başka bir .net dilinde olası bir null değeri ile bir başvuru değişkeni kullandığınızda kullanabilirsiniz. Null yerine, bir F# `option` tür ile, nesne yoksa seçenek değerini `None` kullanırsınız. Bir nesne olduğunda, seçenek `Some(obj)` değerini nesnesiyle `obj` birlikte kullanırsınız. Daha fazla bilgi için bkz. [Seçenekler](../options.md). İçin, `null` ,,, için `Some x` `null`bir değeri yine de bir seçeneğe pakettemediğini unutmayın. `x` Bu nedenle, bir `None` `null`değer olduğunda kullanmanız önemlidir.

Anahtar sözcüğü, F# dilde geçerli bir anahtar sözcüktür ve .NET Framework API 'leri ya da başka bir .net dilinde yazılmış diğer API 'lerle çalışırken kullanmanız gerekir. `null` Bir .NET API çağırdığınızda ve dönüş değerini ya da bir çıkış parametresini bir .NET yöntem çağrısından yorumlayacağınız zaman, null değere ihtiyacınız olabilecek iki durum vardır.

Bir .net yöntemine null değer geçirmek için, çağıran koddaki `null` anahtar sözcüğünü kullanmanız yeterlidir. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

.NET yönteminden alınan null bir değeri yorumlamak için, varsa, model eşleştirmeyi kullanın. Aşağıdaki kod örneği, bir giriş akışının sonunu okumayı denediğinde ' den `ReadLine` döndürülen null değeri yorumlamak için model eşleştirmeyi nasıl kullanacağınızı gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Türler için F# null değerler, ' ı kullandığınızda `Array.zeroCreate` `Unchecked.defaultof`gibi başka yollarla da oluşturulabilir. Null değerleri kapsüllenmeye devam etmek için bu tür koda dikkatli olmanız gerekir. Yalnızca için F#tasarlanan bir kitaplıkta, her işlevde null değerler denetlemeniz gerekmez. Diğer .NET dilleri ile birlikte çalışabilirlik için bir kitaplık yazıyorsanız, null giriş parametrelerine yönelik denetimler eklemeniz ve yalnızca Visual Basic içinde `ArgumentNullException` C# yaptığınız gibi bir kod oluşturmanız gerekebilir.

Rastgele bir değerin null olup olmadığını denetlemek için aşağıdaki kodu kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Değerler](index.md)
- [Eşleşme İfadeleri](../match-expressions.md)
