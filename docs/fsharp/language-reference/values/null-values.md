---
title: Boş Değerler
description: Null değer nasıl kullanıldığını öğrenin F# programlama dilidir.
ms.date: 03/22/2019
ms.openlocfilehash: 93ac48eddf36981b9df550e76405c3175ae92e0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902284"
---
# <a name="null-values"></a>Boş Değerler

Bu konu, null değeri nasıl kullanıldığını açıklar F#.

## <a name="null-value"></a>Null değer

Null değeri içinde genellikle kullanılmaz F# değerler veya değişkenleri. Ancak, bazı durumlarda olağan dışı bir değer olarak null görünür. Bir tür içinde tanımlı ise F#, null sürece normal bir değer olarak verilmez [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) özniteliği türüne uygulanır. Bir tür içinde başka bir .NET dil tanımlanırsa, bir olası değer null olur ve bu türler ile birlikte çalışırken, F# kod, null değerler çalıştırdığınızca.

Tanımlanan bir tür için F# ve kesinlikle gelen kullanılan F#, tek yolu kullanarak bir null değer oluşturmak için F# kitaplığı doğrudan, kullanılacak [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) veya [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Ancak, bir F# diğer .NET dillerinden kullanılan türü veya türü de yazılmaz bir API ile kullanıyorsanız, F#, .NET Framework gibi null değerleri ortaya çıkabilir.

Kullanabileceğiniz `option` yazın F# zaman ile kullanıyor olabileceğiniz bir başvuru değişkenini başka bir .NET dil olası bir null değer. Null, yerine ile bir F# `option` türü, seçenek değerini kullanın `None` varsa nesnesi yok. Seçenek değeri kullandığınız `Some(obj)` bir nesneyle `obj` nesneyi olduğunda. Daha fazla bilgi için [seçenekleri](../options.md). Yine de paketi Not bir `null` değerde bir seçenek ise için `Some x`, `x` özelleştirmede `null`. Bu nedenle, kullandığınız önemli `None` bir değer `null`.

`null` Anahtar sözcüğü, geçerli bir anahtar sözcük F# dili ve .NET Framework API'ları veya başka bir .NET dilinde yazılır diğer API'ler ile çalışırken kullanmak zorunda. Bir null değer ihtiyaç duyabileceğiniz iki .NET API'si çağrısı ve null değeri bağımsız değişken geçirin ve dönüş değeri veya çıktı parametresi .NET yöntem çağrısından yorumladığınızda durumlardır.

Bir null değer .NET yönteme geçirmek için yalnızca kullanma `null` çağıran koddaki anahtar sözcüğü. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

.NET yöntemden alınan bir null değeri yorumlamak için mümkünse desen eşleştirme kullanın. Aşağıdaki kod örneği desen eşleştirme öğesinden döndürülen değerin null yorumlamak için nasıl kullanılacağını gösteren `ReadLine` olduğunda çalışır sonunun ötesinde bir giriş akışı okunamadı.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Null değerler için F# türleri da oluşturulabilir kullandığınızda gibi diğer yollarla `Array.zeroCreate`, çağıran `Unchecked.defaultof`. Kapsüllenmiş null değerlerini tutmak için bu kodla dikkatli olmanız gerekir. Yalnızca hedeflenen bir kitaplıkta F#, her işlev null değerleri denetlemek erişiminiz yok. Diğer .NET dilleri ile birlikte çalışma için bir kitaplık yazıyorsanız, null denetimleri giriş parametreleri ve durum eklemeniz gerekebilir bir `ArgumentNullException`, C# veya Visual Basic kodunda yaptığınız gibi.

Rastgele bir değer null olup olmadığını denetlemek için aşağıdaki kodu kullanabilirsiniz.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Değerler](index.md)
- [Eşleşme İfadeleri](../match-expressions.md)
