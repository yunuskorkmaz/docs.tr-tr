---
title: Zaman Uyumsuz İş Akışları
description: 'Diğer çalışmanın yürütülmesi engellenmeden yürütülen hesaplamaları zaman uyumsuz olarak gerçekleştirmek için F # programlama dilinde destek hakkında bilgi edinin.'
ms.date: 08/15/2020
ms.openlocfilehash: ac727fc630f13db01da964131ab39dc242a12cd1
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557717"
---
# <a name="asynchronous-workflows"></a>Zaman uyumsuz iş akışları

Bu makalede, hesaplamalar zaman uyumsuz olarak, diğer çalışmanın yürütülmesi engellenmeden hesaplamalar gerçekleştirmek için F # desteği açıklanmaktadır. Örneğin, zaman uyumsuz hesaplamalar, uygulama diğer işleri gerçekleştirirken kullanıcılara yanıt vermeye devam eden uo uygulamaları yazmak için kullanılabilir.

## <a name="syntax"></a>Syntax

```fsharp
async { expression }
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde tarafından temsil edilen hesaplama zaman uyumsuz `expression` olarak çalışacak şekilde ayarlanır, yani zaman uyumsuz uyku işlemleri, g/ç ve diğer zaman uyumsuz işlemler gerçekleştirildiğinde geçerli hesaplama iş parçacığını engellemeden yapılır. Zaman uyumsuz hesaplamalar genellikle, yürütme geçerli iş parçacığında devam ederken arka plan iş parçacığında başlatılır. İfadenin türü, `Async<'T>` , `'T` `return` anahtar sözcüğü kullanıldığında ifade tarafından döndürülen türdür. Böyle bir ifadedeki kod, *zaman uyumsuz blok*veya *zaman uyumsuz blok*olarak adlandırılır.

Zaman uyumsuz olarak programlamanın çeşitli yolları vardır ve [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html) sınıfı çeşitli senaryoları destekleyen yöntemler sağlar. Genel yaklaşım, `Async` zaman uyumsuz olarak çalıştırmak istediğiniz hesaplamayı veya hesaplamaları temsil eden nesneler oluşturmak ve ardından tetikleme işlevlerinden birini kullanarak bu hesaplamaları başlatmalıdır. Çeşitli tetikleme işlevleri, zaman uyumsuz hesaplamalar çalıştırmanın farklı yollarını sağlar ve hangisini kullandığınıza bağlı olarak, geçerli iş parçacığını, bir arka plan iş parçacığını veya .NET Framework bir görev nesnesini kullanmak istediğinize ve hesaplama bittiğinde çalışması gereken devamlılık işlevleri olup olmamasına bağlıdır. Örneğin, geçerli iş parçacığında zaman uyumsuz bir hesaplama başlatmak için kullanabilirsiniz [`Async.StartImmediate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#StartImmediate) . UI iş parçacığından zaman uyumsuz bir hesaplama başlattığınızda, uygulamanızın yanıt vermesi için, tuş vuruşları ve fare etkinlikleri gibi kullanıcı eylemlerini işleyen ana olay döngüsünü engellemez.

## <a name="asynchronous-binding-by-using-let"></a>Let kullanarak zaman uyumsuz bağlama!

Zaman uyumsuz bir iş akışında bazı ifadeler ve işlemler zaman uyumludur ve bazıları zaman uyumsuz olarak bir sonuç döndürmek için tasarlanan hesaplamalar daha uzundur. Sıradan bağlama yerine bir yöntemi zaman uyumsuz olarak çağırdığınızda `let` kullanırsınız `let!` . ' Nin etkisi, `let!` hesaplamanın gerçekleştirildiği için yürütmenin diğer hesaplamalar veya iş parçacıklarında devam etmesine olanak tanır. Bağlamanın sağ tarafı `let!` döndüğünde, zaman uyumsuz iş akışının geri kalanı yürütmeyi sürdürür.

Aşağıdaki kod ve arasındaki farkı gösterir `let` `let!` . Tarafından kullanılan kod satırı, `let` daha sonra, örneğin veya kullanarak daha sonra çalıştırabileceğiniz bir nesne olarak zaman uyumsuz bir hesaplama oluşturur `Async.StartImmediate` [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) . Tarafından kullanılan kod satırı `let!` hesaplamayı başlatır ve ardından sonuç kullanılabilir olana kadar iş parçacığı askıya alınır.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

' A ek olarak `let!` , `use!` zaman uyumsuz bağlamalar gerçekleştirmek için kullanabilirsiniz. Ve arasındaki fark `let!` , `use!` ve arasındaki farklılığı ile aynıdır `let` `use` . İçin `use!` , nesnesi geçerli kapsamın kapandığı sırada atıldı. F # dilinin geçerli sürümünde, `use!` bir değerin null olarak başlatılmasına, ancak olsa da izin vermediğini unutmayın `use` .

## <a name="asynchronous-primitives"></a>Zaman uyumsuz temel öğeler

Tek bir zaman uyumsuz görev gerçekleştiren ve sonucu döndüren bir yöntem, *zaman uyumsuz temel*değer olarak adlandırılır ve bunlar özellikle ile kullanılmak üzere tasarlanmıştır `let!` . Çeşitli zaman uyumsuz temel türler, F # Çekirdek Kitaplığı 'nda tanımlanmıştır. Web uygulamaları için iki tür yöntemi, modülünde tanımlanmıştır [`FSharp.Control.WebExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html) : [`WebRequest.AsyncGetResponse`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncGetResponse) ve [`WebClient.AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString) . Her iki temel bir Web sayfasından veri indirir. `AsyncGetResponse` bir `System.Net.WebResponse` nesnesi üretir ve bir `AsyncDownloadString` Web sayfası için HTML 'i temsil eden bir dize oluşturur.

Zaman uyumsuz g/ç işlemlerine yönelik çeşitli temel türler modüle dahildir [`FSharp.Control.CommonExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html) . Sınıfının bu genişletme yöntemleri `System.IO.Stream` [`Stream.AsyncRead`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncRead) ve ' dir [`Stream.AsyncWrite`](hhttps://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncWrite) .

Ayrıca, tamamlanmış gövdesi zaman uyumsuz bir blok içinde olan bir işlev tanımlayarak kendi zaman uyumsuz temel temellerinizi de yazabilirsiniz.

F # zaman uyumsuz programlama modeliyle diğer zaman uyumsuz modeller için tasarlanan .NET Framework zaman uyumsuz yöntemler kullanmak için, F # nesnesi döndüren bir işlev oluşturursunuz `Async` . F # kitaplığı, bunu kolayca yapmayı sağlayan işlevlere sahiptir.

Zaman uyumsuz iş akışları kullanmanın bir örneği buraya dahildir; [zaman uyumsuz sınıf](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html)yöntemlerine ilişkin belgelerde birçok başka tane vardır.

Bu örnekte, hesaplamaları paralel olarak gerçekleştirmek için zaman uyumsuz iş akışlarının nasıl kullanılacağı gösterilmektedir.

Aşağıdaki kod örneğinde, bir işlev `fetchAsync` bir Web isteğinden döndürülen HTML metnini alır. `fetchAsync`İşlev zaman uyumsuz bir kod bloğu içeriyor. Bu durumda, zaman uyumsuz temel öğenin sonucuna bir bağlama yapıldığında, [`AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString) `let!` yerine kullanılır `let` .

İşlevini, [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) zaman uyumsuz bir işlem yürütmek ve bunun sonucunu beklemek için kullanırsınız. Örnek olarak, işlevini işleviyle birlikte kullanarak birden çok zaman uyumsuz işlemi paralel olarak çalıştırabilirsiniz [`Async.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#Parallel) `Async.RunSynchronously` . `Async.Parallel`İşlevi nesnelerinin bir listesini alır `Async` , her `Async` görev nesnesi için paralel olarak çalışacak kodu ayarlar ve `Async` paralel hesaplamayı temsil eden bir nesne döndürür. Tek bir işlemin olduğu gibi `Async.RunSynchronously` yürütme işlemini başlatmak için öğesini çağırın.

`runAll`İşlevi paralel olarak üç zaman uyumsuz iş akışı başlatır ve hepsini tamamlanana kadar bekler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [Hesaplama İfadeleri](computation-expressions.md)
- [Control. Async sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
