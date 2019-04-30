---
title: 'Kaynak Yönetimi: Use anahtar sözcüğü'
description: Hakkında bilgi edinin F# anahtar sözcüğü 'use' ve yayın kaynakların ve başlatma denetleyebilirsiniz 'using' işlev.
ms.date: 05/16/2016
ms.openlocfilehash: 127877a3823faade9bc3c6aefea655c86cc348e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770493"
---
# <a name="resource-management-the-use-keyword"></a>Kaynak Yönetimi: Use anahtar sözcüğü

Bu konu, anahtar sözcüğünü açıklar `use` ve `using` işlevini başlatma ve kaynakları sürümünü kontrol edebilirsiniz.

## <a name="resources"></a>Kaynaklar

Terim *kaynak* birden fazla yolla kullanılır. Evet, kaynaklar, dizeler, grafik ve benzeri gibi ancak bu bağlamda, bir uygulamanın kullandığı veri olabilir *kaynakları* grafik cihaz bağlamları, dosya tanıtıcıları, ağ, yazılım ve işletim sistemi kaynaklarına başvuruyor ve veritabanı bağlantıları, bekleme tanıtıcıları vb. gibi eşzamanlılık nesneleri. Bu kaynakları uygulamalar tarafından kullanımını, işletim sistemi veya başka bir uygulamaya sağlanabilir böylece kaynak bir sonraki sürümü tarafından havuzuna ve ardından diğer kaynak sağlayıcısı kaynak alımını içerir. Uygulamaların kaynakları ortak havuzuna sunmamayı sorunlar ortaya çıkar.

## <a name="managing-resources"></a>Kaynakları yönetme

Bir uygulamadaki kaynakları depoladığımız ve etkili bir şekilde yönetmek için en kısa sürede ve tahmin edilebilir bir biçimde kaynakları bırakmalıdır. .NET Framework sağlayarak bunu yapmanıza yardımcı olur. `System.IDisposable` arabirimi. Uygulayan bir tür `System.IDisposable` sahip `System.IDisposable.Dispose` yönteminin doğru kaynakları serbest bırakır. İyi yazılmış uygulamalar garanti `System.IDisposable.Dispose` sınırlı bir kaynağı tutuyor herhangi bir nesne artık gerekmediğinde en kısa sürede çağrılır. Neyse ki, çoğu .NET dilleri, kolaylaştırmak için destek sağlar ve F# aynı durum geçerlidir. Dispose deseni destekleyen iki yararlı dil yapıları vardır: `use` bağlama ve `using` işlevi.

## <a name="use-binding"></a>Bağlama kullanın

`use` Anahtar sözcüğü, benzer bir biçime sahip `let` bağlama:

kullanma *değer* = *ifadesi*

Aynı işlevselliği sağlar bir `let` bağlama ancak bir çağrı ekler `Dispose` değeri kapsam dışına çıktığında değeri. Derleyici değeri olması durumunda, bu nedenle, değer üzerinde bir null denetimi ekler Not `null`, çağrı `Dispose` değil denenir.

Aşağıdaki örneği kullanarak bir dosyayı otomatik olarak kapatmak gösterilmektedir `use` anahtar sözcüğü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> Kullanabileceğiniz `use` hesaplama ifadeleri, özelleştirilmiş bir sürümünü durumda içinde `use` ifade kullanılır. Daha fazla bilgi için [dizileri](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).

## <a name="using-function"></a>İşlevini kullanma

`using` İşlevi aşağıdaki biçime sahiptir:

`using` (*expression1*) *function-or-lambda*

İçinde bir `using` ifade *İfade1* çıkarılması gerekir nesnesi oluşturur. Sonucu *İfade1* (çıkarılması gereken nesne) bir bağımsız değişken olur *değer*, *işlevi veya lambda*, tek bir bekliyor ya da bir işlev olan tarafından üretilen değerle eşleşen türünde bağımsız değişken kalan *İfade1*, veya bir lambda ifadesi bu türden bir bağımsız değişken bekliyor. Çalışma zamanı yürütme işlevin sonunda çağırır `Dispose` ve kaynakları serbest bırakan (değer değilse `null`, bu durumda Dispose çağrısı denenmedi).

Aşağıdaki örnek, gösterir `using` ifade bir lambda ifadesi ile.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

Sonraki örnekte gösterildiği `using` ifade bir işlev ile.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

İşlevi uygulanmış bazı bağımsız değişkenlere sahip bir işlev olabileceğini unutmayın. Aşağıdaki kod örneği bunu gösterir. Dize içeren bir dosya oluşturur `XYZ`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` İşlevi ve `use` bağlanır neredeyse eşdeğer yolları aynı görevi gerçekleştirir. `using` Anahtar sözcüğü, ne zaman üzerinde daha fazla denetim sağlar `Dispose` çağrılır. Kullanırken `using`, `Dispose` kullandığınızda işlevi veya lambda ifadesi; sonunda çağrılır `use` anahtar sözcüğü, `Dispose` içeren kod bloğunun sonunda çağrılır. Genel olarak, kullanmaya tercih etmelisiniz `use` yerine `using` işlevi.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)