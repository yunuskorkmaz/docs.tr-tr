---
title: Zaman Uyumsuz İş Akışları (F#)
description: Desteği hakkında bilgi edinin F# programlama diğer iş yürütme engellemeden yürütülen zaman uyumsuz olarak hesaplamalar gerçekleştirmek için dili.
ms.date: 05/16/2016
ms.openlocfilehash: 720996106d2b90392eacc75eb99147691ee83334
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127751"
---
# <a name="asynchronous-workflows"></a>Zaman Uyumsuz İş Akışları

> [!NOTE]
> MSDN için API başvuru bağlantısı sizi yönlendirir.  Docs.microsoft.com API başvuru tamamlanmadı.

Bu konuda desteği açıklanmaktadır F# zaman uyumsuz hesaplamalar gerçekleştirmek için diğer bir deyişle, diğer yürütülmesini engellenmeden çalışır. Örneğin, zaman uyumsuz hesaplamalar, diğer iş uygulamanın gerçekleştirdiği gibi kullanıcıya hassas kalması kullanıcı arabirimleri olan uygulamaları yazmak için kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
async { expression }
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, hesaplama temsil ettiği `expression` zaman uyumsuz olarak diğer bir deyişle, uyku zaman uyumsuz işlemler, g/ç ve diğer zaman uyumsuz işlemleri gerçekleştirildiğinde geçerli hesaplama iş parçacığını engellemeden çalıştırmak için ayarlanır. Geçerli iş parçacığı üzerinde yürütme devam ederken, zaman uyumsuz hesaplamalar genellikle arka plan iş parçacığında başlatılır. İfade türü `Async<'T>`burada `'T` ifadesi tarafından döndürülen bir tür olduğunda `return` anahtar sözcüğü kullanılır. Böyle bir ifade kod şeklinde adlandırılan bir *zaman uyumsuz blok*, veya *zaman uyumsuz blok*.

Çeşitli şekillerde zaman uyumsuz olarak programlama vardır ve [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) sınıfı birkaç senaryo destekleyen yöntemler sağlar. Genel yaklaşım oluşturmaktır `Async` nesneleri hesaplama veya zaman uyumsuz olarak çalıştırmak istediğiniz hesaplamalar temsil eder ve bu hesaplamalar tetikleyici işlevlerinden birini kullanarak başlatın. Zaman uyumsuz hesapları çalıştırma için farklı yollar çeşitli tetikleyici işlevleri sağlar ve hangisini kullandığınız, geçerli iş parçacığı, bir arka plan iş parçacığı veya bir .NET Framework görev nesnesi kullanmak istediğiniz bağlıdır ve devamlılık olup olmadığı Hesaplama tamamlandığında çalışması gereken işlevler. Örneğin, geçerli iş parçacığında zaman uyumsuz bir hesaplama başlatmak için kullanabileceğiniz [ `Async.StartImmediate` ](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3). Zaman uyumsuz bir hesaplama UI iş parçacığından başlattığınızda, uygulamanızın yanıt verebilecek duruma gelir. Bu nedenle, tuş vuruşlarınızı ve fare etkinliği gibi kullanıcı eylemlerini işleyen ana olay döngüsünü engellemez.

## <a name="asynchronous-binding-by-using-let"></a>Let kullanarak zaman uyumsuz bağlama!

Zaman uyumsuz iş akışı bazı ifadeler ve işlemleri zaman uyumlu ve zaman uyumsuz olarak bir sonuç döndürmek için tasarlanmış uzun hesaplamalar bazılarıdır. Çağırdığınızda bir yöntemin zaman uyumsuz olarak bir sıradan yerine `let` kullandığınız bağlamayı `let!`. Etkisini `let!` hesaplama gerçekleştirilir gibi diğer hesaplamaları veya iş parçacığı devam etmek için yürütmeye olanak sağlamasıdır. Sonra sağ tarafında `let!` bağlama döndürür, zaman uyumsuz iş akışının geri kalanı, yürütme devam eder.

Aşağıdaki kod arasındaki farkı gösterir `let` ve `let!`. Kullanan kod satırının `let` yalnızca daha sonra kullanarak, örneğin, çalıştırabileceğiniz bir nesne olarak zaman uyumsuz bir hesaplama oluşturur `Async.StartImmediate` veya [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b). Kullanan kod satırının `let!` hesaplamayı başlatır ve ardından sonuç hangi noktası yürütme devam eder kullanılabilir oluncaya kadar iş parçacığını askıya alındı.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Ek olarak `let!`, kullanabileceğiniz `use!` zaman uyumsuz bağlamaları gerçekleştirilecek. Arasındaki fark `let!` ve `use!` arasındaki farkı aynı `let` ve `use`. İçin `use!`, nesne, geçerli kapsamdaki kapanışında atıldı. Geçerli sürüm olduğunu unutmayın F# dil `use!` null olarak olsa bile başlatılacak bir değere izin vermiyor `use` yapar.

## <a name="asynchronous-primitives"></a>Zaman uyumsuz temelleri

Tek bir zaman uyumsuz görev gerçekleştirir ve sonuç döndüren bir yöntem olarak adlandırılan bir *zaman uyumsuz temel*, ve bu ile kullanılmak üzere özel olarak tasarlanmıştır `let!`. Birden çok zaman uyumsuz temelleri tanımlanan F# çekirdek kitaplığı. Web uygulamaları için iki tür yöntemler modülde tanımlanan [ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) ve [ `WebClient.AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a). Her iki ilkel veri Web verilen URL bir sayfasından indirin. `AsyncGetResponse` üreten bir `System.Net.WebResponse` nesnesi ve `AsyncDownloadString` HTML Web sayfası için temsil eden bir dize oluşturur.

Zaman uyumsuz g/ç işlemleri için birkaç temelleri dahil [ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) modülü. Bu uzantı yöntemleri `System.IO.Stream` sınıfı [ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) ve [ `Stream.AsyncWrite` ](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618).

Ayrıca, tam gövde, bir zaman uyumsuz bloğunda alınmış bir işlevi tanımlayarak kendi zaman uyumsuz temelleri yazabilirsiniz.

Diğer zaman uyumsuz modeller ile tasarlanmış zaman uyumsuz yöntemler .NET Framework'teki kullanılmak üzere F# zaman uyumsuz programlama modeli döndüren bir işlev oluşturma bir F# `Async` nesne. F# Kitaplığı, bunu yapmak kolaylaştıran işlevleri vardır.

Zaman uyumsuz iş akışları kullanmaya ilişkin bir örnek burada bulunur; vardır birçok diğer yöntemleri için belgelerinde [Async sınıfı](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

Bu örnek, zaman uyumsuz iş akışları paralel hesaplamalar gerçekleştirmek için nasıl kullanılacağını gösterir.

Aşağıdaki kod örneğinde, bir işlev `fetchAsync` HTML metni döndürülen bir Web isteğinde alır. `fetchAsync` İşlevi içeren zaman uyumsuz bir kod bloğu. Ne zaman bir bağlama yapılan zaman uyumsuz bir primitive sonucunu bu durumda [ `AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a), let! let yerine kullanılır.

İşlevini [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) sonucunun beklendiğini ve zaman uyumsuz bir işlemi yürütmek için. Örneğin, birden çok zaman uyumsuz işlemler paralel olarak kullanarak yürütebilirsiniz [ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) ile birlikte çalışması `Async.RunSynchronously` işlevi. `Async.Parallel` İşlevi bir listesini alır `Async` nesneleri, kodu her biri için ayarlar `Async` paralel ve döndürür çalıştırılacak görev nesnesi bir `Async` Paralel hesaplama temsil eden nesne. Yalnızca tek bir işlem olduğu gibi çağırmanızı `Async.RunSynchronously` yürütme başlatılamadı.

`runAll` İşlevi üç zaman uyumsuz iş akışları paralel başlatır ve tüm tamamlanana kadar bekler.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Hesaplama İfadeleri](computation-expressions.md)
- [Control.Async sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
