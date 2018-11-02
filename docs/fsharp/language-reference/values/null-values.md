---
title: Boş Değerler (F#)
description: 'Nasıl null değerini F # programlama dilinin kullanıldığını öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 8751ac402c43ddb07fb62e08b6c6d5403cbe9acc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43787908"
---
# <a name="null-values"></a>Boş Değerler

Bu konu nasıl null değerini F #'ta kullanıldığını açıklar.

## <a name="null-value"></a>Null değer

Null değeri normalde F # değerleri veya değişkenleri için kullanılmaz. Ancak, bazı durumlarda olağan dışı bir değer olarak null görünür. Bir tür F # içinde tanımlanmış olması durumunda, null normal bir değer sürece izin verilmiyor [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) özniteliği türüne uygulanır. Bir tür içinde başka bir .NET dil tanımlanırsa, bir olası değer null ve böyle türleriyle birlikte çalışırken, F # kodu null değerler karşılaşabilirsiniz.

F #'de tanımlanan ve F #'tan kesin olarak kullanılan bir tür için F # kitaplığı kullanarak doğrudan bir null değer oluşturmak için tek yolu kullanmaktır [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) veya [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Ancak, diğer .NET dillerinden kullanılan bir F # tür veya null değerler, F #, .NET Framework gibi yazılmaz API'ye sahip türü kullanıyorsanız gerçekleşebilir.

Kullanabileceğiniz `option` F #'de başka bir .NET dilinde olası bir null değerine sahip bir başvuru değişkenini kullanmak isteyeceğiniz durumların türü. Bir F # ile bir null yerine `option` türü, seçenek değerini kullanın `None` varsa nesnesi yok. Seçenek değeri kullandığınız `Some(obj)` bir nesneyle `obj` nesneyi olduğunda. Daha fazla bilgi için [seçenekleri](../options.md).

`null` Anahtar sözcüğü, geçerli bir anahtar sözcük F # dilinde ve .NET Framework API'ları veya başka bir .NET dilinde yazılır diğer API'ler ile çalışırken onu kullanmanız gerekir. Bir null değer ihtiyaç duyabileceğiniz iki .NET API'si çağrısı ve null değeri bağımsız değişken geçirin ve dönüş değeri veya çıktı parametresi .NET yöntem çağrısından yorumladığınızda durumlardır.

Bir null değer .NET yönteme geçirmek için yalnızca kullanma `null` çağıran koddaki anahtar sözcüğü. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

.NET yöntemden alınan bir null değeri yorumlamak için mümkünse desen eşleştirme kullanın. Aşağıdaki kod örneği desen eşleştirme öğesinden döndürülen değerin null yorumlamak için nasıl kullanılacağını gösteren `ReadLine` olduğunda çalışır sonunun ötesinde bir giriş akışı okunamadı.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

F # türleri için null değerler da oluşturulabilir kullandığınızda gibi diğer yollarla `Array.zeroCreate`, çağıran `Unchecked.defaultof`. Kapsüllenmiş null değerlerini tutmak için bu kodla dikkatli olmanız gerekir. Yalnızca F # için hedeflenen bir kitaplıkta, null değerler her işlevde denetle gerekmez. Diğer .NET dilleri ile birlikte çalışma için bir kitaplık yazıyorsanız, null denetimleri giriş parametreleri ve durum eklemeniz gerekebilir bir `ArgumentNullException`, C# veya Visual Basic kodunda yaptığınız gibi.

Rastgele bir değer null olup olmadığını denetlemek için aşağıdaki kodu kullanabilirsiniz.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Değerler](index.md)
- [Eşleşme İfadeleri](../match-expressions.md)
