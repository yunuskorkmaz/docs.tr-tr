---
title: 'Kaynak Yönetimi: use Anahtar Sözcüğü (F#)'
description: "F # anahtar sözcüğü 'use' ve yayın kaynakların ve başlatma denetleyebilirsiniz 'kullanılarak' işlevi hakkında bilgi edinin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0e134bf5b302911324dd224316941fee693b787b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="resource-management-the-use-keyword"></a>Kaynak Yönetimi: use Anahtar Sözcüğü

Bu konu, anahtar sözcüğü açıklar `use` ve `using` başlatma ve kaynakları sürümü kontrol edebilirsiniz işlevi.

## <a name="resources"></a>Kaynaklar
Terim *kaynak* birden fazla şekilde kullanılır. Kaynak dizeleri, grafik ve benzeri gibi ancak bu bağlamda bir uygulamanın kullandığı veri Evet, olabilir *kaynakları* grafik cihaz bağlamları, dosya tanıtıcısı, ağ gibi yazılım ve işletim sistemi kaynaklarına başvuruyor ve veritabanı bağlantıları, bekleme tanıtıcıları vb. gibi eşzamanlılık nesneleri. Bu kaynakların uygulamalar tarafından kullanımını işletim sistemi veya başka bir uygulamaya sağlanan böylece daha sonraki bir sürümü kaynak tarafından havuzuna ve ardından diğer kaynak sağlayıcısı kaynaktan alımını içerir. Uygulamaları ortak havuzuna kaynakları serbest bırakmak değil sorunları oluşur.

## <a name="managing-resources"></a>Kaynakları yönetme
Bir uygulamadaki kaynakları verimli bir şekilde ve sorumlu bir şekilde yönetmek için hemen ve tahmin edilebilir bir şekilde kaynakları serbest bırakmalısınız. .NET Framework sağlayarak bunu yardımcı olan `System.IDisposable` arabirimi. Uygulayan bir tür `System.IDisposable` sahip `System.IDisposable.Dispose` doğru kaynakları serbest bırakır yöntemi. İyi yazılmış uygulamalar garanti `System.IDisposable.Dispose` sınırlı bir kaynağa tutan herhangi bir nesne artık gerekli olmadığında derhal denir. Neyse ki, çoğu .NET dillerini kolaylaştırmak için destek sağlar ve F # aynı durum geçerlidir. Dispose deseni destekleyen iki yararlı dil yapıları vardır: `use` bağlama ve `using` işlevi.

## <a name="use-binding"></a>Bağlama kullanın
`use` Anahtar sözcüğü vardır, benzer bir form `let` bağlama:

kullanmak *değeri* = *ifadesi*

İle aynı işlevselliği sağlayan bir `let` bağlama ancak yapılan bir çağrı ekler `Dispose` değeri kapsam dışına çıktığında değeri. Değeri olması durumunda olacak şekilde derleyici değeri, null denetimi ekler Not `null`, çağrısı `Dispose` değil denenir.

Aşağıdaki örnek, bir dosyayı kullanarak otomatik olarak kapatmak gösterilmiştir `use` anahtar sözcüğü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
Kullanabileceğiniz `use` hesaplama ifadelerde özelleştirilmiş bir sürümünü durumda içinde `use` ifade kullanılır. Daha fazla bilgi için bkz: [sıraları](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).


## <a name="using-function"></a>using işlevi
`using` İşlevi aşağıdaki biçime sahiptir:

`using` (*İfade1*) *işlevi veya lambda*

İçinde bir `using` ifadesi *İfade1* çıkarılması gerekir nesnesi oluşturur. Sonucu *İfade1* (çıkarılması gerekir nesnesi) bir bağımsız değişken hale *değeri*, *işlevi veya lambda*, tek bir bekliyor ya da bir işlevi olan bağımsız değişken değeri ile eşleşen bir tür kalan üretilen *İfade1*, ya da bu türünde bir bağımsız değişken bekler bir lambda ifadesi. Çalışma zamanı yürütme işlevi işlemi sonunda, çağıran `Dispose` ve kaynakları serbest bırakır (değer değilse `null`, bu durumda Dispose çağrısı bulunulmadı).

Aşağıdaki örnekte gösterilmiştir `using` lambda ifadesi ile ifadesi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

Sonraki örnekte gösterildiği `using` bir işlevi olan ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Not işlevi bazı bağımsız değişkenler uygulanmış olan bir işlev olabilir. Aşağıdaki kod örneğinde bu gösterir. Dizeyi içeren bir dosya oluşturur `XYZ`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` İşlevi ve `use` aynı şeyi yapmanın neredeyse eşdeğer yolu bağlanır. `using` Anahtar sözcüğü ne zaman üzerinde daha fazla denetim sağlar `Dispose` olarak adlandırılır. Kullandığınızda `using`, `Dispose` kullandığınızda işlevi veya lambda ifadesi; sonunda çağrılır `use` anahtar sözcüğü, `Dispose` içeren kod bloğu sonunda çağrılır. Genel olarak, kullanmayı tercih ederseniz `use` yerine `using` işlevi.


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)
