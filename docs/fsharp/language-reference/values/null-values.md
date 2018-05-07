---
title: Boş Değerler (F#)
description: 'Nasıl null değer F # programlama dili kullanılır öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 7367b35cb6e910f926179e52992d5533e5cdda0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="null-values"></a>Boş Değerler

Bu konuda nasıl null değer F #'ta kullanıldığını açıklar.


## <a name="null-value"></a>Null değer
Null değer normal olarak F #'ta değerler veya değişkenler için kullanılmaz. Ancak, bazı durumlarda normal olmayan bir değer olarak null görünür. Bir tür F #'ta tanımlanmışsa, null normal bir değeri sürece izin verilmiyor [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) öznitelik türü için uygulanır. Bir tür bazı diğer .NET dilinde tanımlandı, olası bir değer null ise ve bu tür türleri ile birlikte, F # kodunuzu null değerler karşılaşabilirsiniz.

F #'de tanımlanan ve kesinlikle kullanılan F #'türü için F # kitaplığı kullanarak doğrudan bir null değer oluşturmak için tek yolu kullanmaktır [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) veya [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Ancak, diğer .NET dillerinden kullanılan bir F # türü veya F #, .NET Framework gibi yazılmaz bir API ile türü kullanıyorsanız, null değerler ortaya çıkabilir.

Kullanabileceğiniz `option` F başka bir .NET dilinde olası null değerine sahip bir başvuru değişken kullanmak isteyeceğiniz durumların # türü. Null ile bir F # yerine `option` türü, seçenek değeri kullanmak `None` nesnesi yok ise. Seçenek değeri kullanmak `Some(obj)` bir nesneyle `obj` bir nesne olduğunda. Daha fazla bilgi için bkz: [seçenekleri](../options.md).

`null` F # dilinde geçerli bir anahtar sözcüktür ve .NET Framework API'ları veya başka bir .NET dilinde yazılmış diğer API'leri ile çalışırken kullanmak zorunda. Bir null değer gerekebilecek iki .NET API çağrısı ve bağımsız değişken olarak bir null değer geçirmek ve dönüş değeri veya çıktı parametresi .NET yöntemi çağrısından yorumlama durumlardır.

Bir .NET yöntem boş bir değer geçirmek için yalnızca kullanmak `null` arama koddaki anahtar sözcük. Aşağıdaki kod örneği bunu gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Bir .NET yönteminden elde bir null değer yorumlamaya yapabiliyorsanız desen eşleştirme kullanın. Aşağıdaki kod örneğinde desen eşleştirme sunucudan döndürülen değerin null yorumlamak için nasıl kullanılacağını gösterir `ReadLine` zaman çalışır sonunun ötesinde Giriş akışı okunamıyor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

F # türleri için null değerler de oluşturulabilir kullandığınızda gibi diğer yollarla `Array.zeroCreate`, çağıran `Unchecked.defaultof`. Kapsüllenmiş null değerleri tutmak için bu kodla dikkatli olmanız gerekir. Yalnızca F # için amaçlanan bir kitaplıkta her işlevde null değerler olup olmadığını denetlemek yok. Diğer .NET dilleri ile birlikte çalışma için bir kitaplık yazıyorsanız, null denetimlerinin giriş parametreleri ve durum eklemeniz gerekebilir bir `ArgumentNullException`, C# veya Visual Basic kodunda yaptığınız gibi.

Rastgele bir değerin boş olup olmadığını denetlemek için aşağıdaki kodu kullanabilirsiniz.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Ayrıca Bkz.
[Değerler](index.md)

[Eşleşme İfadeleri](../match-expressions.md)
