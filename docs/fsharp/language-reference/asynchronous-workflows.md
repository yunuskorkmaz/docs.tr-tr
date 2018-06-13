---
title: Zaman Uyumsuz İş Akışları (F#)
description: 'F # programlama dili hesaplamalar zaman uyumsuz olarak gerçekleştirmek için destek, diğer iş yürütme engellenmeden yürütme öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 5f7a1a623e143e1bedf51c1a1ed477bb867b280a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566369"
---
# <a name="asynchronous-workflows"></a>Zaman Uyumsuz İş Akışları

> [!NOTE]
API başvuru bağlantısı sizi MSDN'ye götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Bu konu, hesaplamalar zaman uyumsuz olarak, diğer bir deyişle, diğer iş yürütme engellenmeden gerçekleştirmek için destek F # açıklar. Örneğin, uygulama diğer iş gerçekleştirirken, kullanıcılara yanıt verebilir durumda kalması Uı'lar uygulamaları yazmak için zaman uyumsuz hesapları kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
async { expression }
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde hesaplama temsil ettiği `expression` zaman uyumsuz olarak, diğer bir deyişle, uyku zaman uyumsuz işlemler, g/ç ve diğer zaman uyumsuz işlemleri gerçekleştirildiğinde geçerli hesaplama iş parçacığı engellenmeden çalıştırmak için ayarlayın. Geçerli iş parçacığı üzerinde yürütme devam ederken zaman uyumsuz hesapları genellikle arka plan iş parçacığında başlatılır. İfade türü `Async<'T>`, burada `'T` ifadesi tarafından döndürülen tür zaman `return` anahtar sözcüğü kullanılır. Kod içinde bu tür bir ifade olarak adlandırılır bir *zaman uyumsuz blok*, veya *zaman uyumsuz blok*.

Çeşitli şekillerde zaman uyumsuz olarak programlama vardır ve [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) sınıfı çeşitli senaryoları desteklemek yöntemler sağlar. Genel yaklaşım oluşturmaktır `Async` hesaplama veya zaman uyumsuz olarak çalıştırmak istediğiniz hesaplamalar temsil eder ve tetikleme işlevleri birini kullanarak bu hesaplamalar başlatın nesneleri. Zaman uyumsuz hesapları çalışan farklı yollar çeşitli tetikleme işlevleri sağlar ve bir kullandığınız, geçerli iş parçacığı, arka plan iş parçacığı veya .NET Framework görev nesnesi kullanmak isteyip istememenize bağlıdır ve devamlılık olup Hesaplama tamamlandığında çalışması gerektiğini işlevleri. Örneğin, zaman uyumsuz bir hesaplama geçerli iş parçacığı üzerinde başlatmak için kullanabileceğiniz [ `Async.StartImmediate` ](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3). Kullanıcı Arabirimi iş parçacığından zaman uyumsuz bir hesaplama başlattığınızda kullanıcı eylemleri tuş vuruşları ve fare etkinliği gibi uygulamanızı esnek böylece işleyen ana olay döngüsünü engellemez.

## <a name="asynchronous-binding-by-using-let"></a>Let kullanarak zaman uyumsuz bağlama!

Zaman uyumsuz bir iş akışı bazı ifadeleri ve işlemleri zaman uyumlu ve zaman uyumsuz sonuç için tasarlanmış uzun hesaplamalar bazılarıdır. Çağırdığınızda bir yöntem zaman uyumsuz olarak bir sıradan yerine `let` kullandığınız bağlama, `let!`. Etkisini `let!` hesaplama gerçekleştirilir gibi diğer hesaplamalar veya iş parçacığının devam etmek yürütme sağlamaktır. Sağ tarafındaki sonra `let!` bağlama döndürür, zaman uyumsuz iş akışının geri kalanı yürütme devam ettirir.

Aşağıdaki kod arasındaki farkı gösterir `let` ve `let!`. Kullanan kod satırı `let` yalnızca daha sonra kullanarak, örneğin, çalıştırabileceğiniz bir nesne olarak zaman uyumsuz bir hesaplama oluşturur `Async.StartImmediate` veya [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b). Kullanan kod satırı `let!` hesaplama başlar ve ardından sonucu hangi noktası yürütme devam ediyor kullanılabilir oluncaya kadar iş parçacığı askıya alınır.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Ek olarak `let!`, kullanabileceğiniz `use!` zaman uyumsuz bağlamaları gerçekleştirmek için. Arasındaki farkı `let!` ve `use!` arasındaki farkı aynı `let` ve `use`. İçin `use!`, nesne, geçerli kapsamdaki kapanışında atıldı. F # dili, geçerli sürümde unutmayın `use!` değeri null olarak rağmen başlatılması izin verme `use` yapar.

## <a name="asynchronous-primitives"></a>Zaman uyumsuz temelleri

Tek bir zaman uyumsuz görevi gerçekleştirir ve sonuç döndüren bir yöntem olarak adlandırılan bir *zaman uyumsuz ilkel*, ve bunlar ile kullanılmak üzere özel olarak tasarlanmıştır `let!`. Birkaç zaman uyumsuz temelleri F # core Kitaplığı'nda tanımlanır. Web uygulamaları için iki tür yöntem modülde tanımlanan [ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) ve [ `WebClient.AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a). Her iki temelleri veri Web bir URL bir sayfasından indirin. `AsyncGetResponse` üreten bir `System.Net.WebResponse` nesnesi ve `AsyncDownloadString` bir Web sayfasının HTML temsil eden bir dize oluşturur.

Birkaç temel öğeler zaman uyumsuz g/ç işlemleri dahil edilen [ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) modülü. Bu uzantı yöntemleri `System.IO.Stream` sınıfı olan [ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) ve [ `Stream.AsyncWrite` ](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618).

Ek zaman uyumsuz temelleri kullanılabilir [F # PowerTools](https://fsprojects.github.io/VisualFSharpPowerTools/). Zaman uyumsuz kendi temelleri, tam gövdesi bir zaman uyumsuz bloğunda içine bir işlev tanımlayarak de yazabilirsiniz.

F # zaman uyumsuz programlama modeli ile diğer zaman uyumsuz modeller için tasarlanmış .NET Framework zaman uyumsuz yöntemleri kullanmak için bir F # döndüren bir işlev oluşturun. `Async` nesnesi. F # kitaplığı bunu yapmak kolaylaştırmak işlevi vardır.

Zaman uyumsuz iş akışları kullanmaya ilişkin bir örnek buraya dahil edilir; vardır diğer birçok yöntemlerinin belgelerindeki [Async sınıfı](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

Bu örnekte, zaman uyumsuz iş akışları paralel olarak hesaplamalar için nasıl kullanılacağını gösterir.

Aşağıdaki kod örneğinde, bir işlev `fetchAsync` HTML metin Web isteğinden döndürülen alır. `fetchAsync` İşlevi, zaman uyumsuz bir kod bloğunu içeriyor. Ne zaman bir bağlama yapılan zaman uyumsuz bir ilkel sonucuna bu durumda [ `AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a), let! let yerine kullanılır.

İşlevi kullanmak [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) zaman uyumsuz bir işlem çalıştırmak ve sonucu için bekleyin. Örnek olarak, birden çok zaman uyumsuz işlemleri paralel olarak kullanarak yürütebilirsiniz [ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) ile birlikte çalışması `Async.RunSynchronously` işlevi. `Async.Parallel` İşlev listesini alır `Async` nesneleri, kodu her biri için ayarlar `Async` paralel ve döndürür çalıştırmak için görev nesnesi bir `Async` Paralel hesaplama temsil eden nesne. Yalnızca tek bir işlem için olduğu gibi çağrı `Async.RunSynchronously` yürütme başlatmak için.

`runAll` İşlevi üç zaman uyumsuz iş akışları paralel başlatır ve tüm tamamlayıncaya kadar bekler.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Ayrıca Bkz.

[F# Dili Başvurusu](index.md)

[Hesaplama İfadeleri](computation-expressions.md)

[Control.Async sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
