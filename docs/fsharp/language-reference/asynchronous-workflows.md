---
title: Zaman Uyumsuz İş Akışları
description: Diğer çalışmanın yürütülmesi engellenmeden F# yürütülen hesaplamaları zaman uyumsuz olarak gerçekleştirmeye yönelik programlama dilinde destek hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 2d967f6bfe46b4f3916648b3063210d1ba1c210f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630007"
---
# <a name="asynchronous-workflows"></a>Zaman Uyumsuz İş Akışları

> [!NOTE]
> API başvuru bağlantısı sizi MSDN 'ye götürür.  Docs.microsoft.com API başvurusu tamamlanmadı.

Bu konuda, diğer çalışmanın F# yürütülmesi engellenmeden hesaplamalar zaman uyumsuz olarak gerçekleştirilmesi için ' de destek açıklanmaktadır. Örneğin, zaman uyumsuz hesaplamalar, uygulama diğer işleri gerçekleştirirken kullanıcılara yanıt vermeye devam eden uo uygulamaları yazmak için kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
async { expression }
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde tarafından `expression` temsil edilen hesaplama zaman uyumsuz olarak çalışacak şekilde ayarlanır, yani zaman uyumsuz uyku işlemleri, g/ç ve diğer zaman uyumsuz işlemler gerçekleştirildiğinde geçerli hesaplama iş parçacığını engellemeden yapılır. Zaman uyumsuz hesaplamalar genellikle, yürütme geçerli iş parçacığında devam ederken arka plan iş parçacığında başlatılır. İfadenin `Async<'T>`türü, `'T` , `return` anahtar sözcüğü kullanıldığında ifade tarafından döndürülen türdür. Böyle bir ifadedeki kod, *zaman uyumsuz blok*veya *zaman uyumsuz blok*olarak adlandırılır.

Zaman uyumsuz olarak programlamanın çeşitli yolları vardır ve [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) sınıfı çeşitli senaryoları destekleyen yöntemler sağlar. Genel yaklaşım, zaman uyumsuz olarak `Async` çalıştırmak istediğiniz hesaplamayı veya hesaplamaları temsil eden nesneler oluşturmak ve ardından tetikleme işlevlerinden birini kullanarak bu hesaplamaları başlatmalıdır. Çeşitli tetikleme işlevleri, zaman uyumsuz hesaplamalar çalıştırmanın farklı yollarını sağlar ve hangisini kullandığınıza bağlı olarak, geçerli iş parçacığını, bir arka plan iş parçacığını veya .NET Framework bir görev nesnesini kullanmak istediğinize ve devamlılık olup olmamasına bağlıdır Hesaplama tamamlandığında çalışması gereken işlevler. Örneğin, geçerli iş parçacığında zaman uyumsuz bir hesaplama başlatmak için kullanabilirsiniz [`Async.StartImmediate`](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3). UI iş parçacığından zaman uyumsuz bir hesaplama başlattığınızda, uygulamanızın yanıt vermesi için, tuş vuruşları ve fare etkinlikleri gibi kullanıcı eylemlerini işleyen ana olay döngüsünü engellemez.

## <a name="asynchronous-binding-by-using-let"></a>Let kullanarak zaman uyumsuz bağlama!

Zaman uyumsuz bir iş akışında bazı ifadeler ve işlemler zaman uyumludur ve bazıları zaman uyumsuz olarak bir sonuç döndürmek için tasarlanan hesaplamalar daha uzundur. Sıradan `let` bağlama yerine bir yöntemi zaman uyumsuz olarak çağırdığınızda kullanırsınız `let!`. ' Nin `let!` etkisi, hesaplamanın gerçekleştirildiği için yürütmenin diğer hesaplamalar veya iş parçacıklarında devam etmesine olanak tanır. `let!` Bağlamanın sağ tarafı döndüğünde, zaman uyumsuz iş akışının geri kalanı yürütmeyi sürdürür.

Aşağıdaki kod ve `let` `let!`arasındaki farkı gösterir. Tarafından kullanılan `let` kod satırı, daha sonra, `Async.StartImmediate` örneğin veya [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)kullanarak daha sonra çalıştırabileceğiniz bir nesne olarak zaman uyumsuz bir hesaplama oluşturur. Tarafından kullanılan `let!` kod satırı hesaplamayı başlatır ve ardından sonuç kullanılabilir olana kadar iş parçacığı askıya alınır.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

`let!`' A ek olarak, zaman uyumsuz `use!` bağlamalar gerçekleştirmek için kullanabilirsiniz. Ve `let!` arasındaki`use!` fark, ve `let` arasındakifarklılığıileaynıdır.`use` İçin `use!`, nesnesi geçerli kapsamın kapandığı sırada atıldı. F# Dilin geçerli sürümünde, `use!` bir değerin null olarak başlatılmasına, ancak `use` olsa da izin vermediğini unutmayın.

## <a name="asynchronous-primitives"></a>Zaman uyumsuz temel öğeler

Tek bir zaman uyumsuz görev gerçekleştiren ve sonucu döndüren bir yöntem, *zaman uyumsuz temel*değer olarak adlandırılır ve bunlar özellikle ile `let!`kullanılmak üzere tasarlanmıştır. Birçok zaman uyumsuz temel öğeler F# çekirdek kitaplıkta tanımlanmıştır. Web uygulamaları için iki tür yöntemi, modülünde [`Microsoft.FSharp.Control.WebExtensions`](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003)tanımlanmıştır: [`WebRequest.AsyncGetResponse`](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) ve [`WebClient.AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a). Her iki temel bir Web sayfasından veri indirir. `AsyncGetResponse`bir `System.Net.WebResponse` nesnesi üretir ve `AsyncDownloadString` bir Web sayfası için HTML 'i temsil eden bir dize oluşturur.

Zaman uyumsuz g/ç işlemlerine yönelik çeşitli temel türler [`Microsoft.FSharp.Control.CommonExtensions`](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) modüle dahildir. `System.IO.Stream` Sınıfının bu genişletme yöntemleri ve ' [`Stream.AsyncWrite`](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618)dir [`Stream.AsyncRead`](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) .

Ayrıca, tamamlanmış gövdesi zaman uyumsuz bir blok içinde olan bir işlev tanımlayarak kendi zaman uyumsuz temel temellerinizi de yazabilirsiniz.

Zaman uyumsuz programlama modeliyle diğer zaman uyumsuz modeller F# için tasarlanan .NET Framework zaman uyumsuz yöntemler kullanmak için, bir F# `Async` nesnesi döndüren bir işlev oluşturursunuz. F# Kitaplıkta bunun kolay hale gelen işlevler bulunur.

Zaman uyumsuz iş akışları kullanmanın bir örneği buraya dahildir; [zaman uyumsuz sınıf](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)yöntemlerine ilişkin belgelerde birçok başka tane vardır.

Bu örnekte, hesaplamaları paralel olarak gerçekleştirmek için zaman uyumsuz iş akışlarının nasıl kullanılacağı gösterilmektedir.

Aşağıdaki kod örneğinde, bir işlev `fetchAsync` bir Web isteğinden döndürülen HTML metnini alır. `fetchAsync` İşlev zaman uyumsuz bir kod bloğu içeriyor. Zaman uyumsuz temel nesnenin sonucuna bir bağlama yapıldığında, bu durumda [`AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)izin verin! , izin yerine kullanılır.

İşlevini [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) , zaman uyumsuz bir işlem yürütmek ve bunun sonucunu beklemek için kullanırsınız. Örnek olarak, işlevini [`Async.Parallel`](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) `Async.RunSynchronously` işleviyle birlikte kullanarak birden çok zaman uyumsuz işlemi paralel olarak çalıştırabilirsiniz. İşlevi nesnelerinin bir `Async` listesini `Async` alır, her görev nesnesi için paralel olarak çalışacak kodu ayarlar ve paralel hesaplamayı temsil eden bir nesne döndürür. `Async` `Async.Parallel` Tek bir işlemin olduğu gibi yürütme işlemini başlatmak için `Async.RunSynchronously` öğesini çağırın.

`runAll` İşlevi paralel olarak üç zaman uyumsuz iş akışı başlatır ve hepsini tamamlanana kadar bekler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Hesaplama İfadeleri](computation-expressions.md)
- [Control. Async sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
