---
title: 'Kaynak yönetimi: Use anahtar sözcüğü'
description: Kaynak başlatma ve F# serbest bırakma işlevlerini denetleyebilen ' Use ' anahtar sözcüğü ve ' Using ' işlevi hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627264"
---
# <a name="resource-management-the-use-keyword"></a>Kaynak yönetimi: Use anahtar sözcüğü

Bu konuda, kaynak başlatma `use` ve serbest `using` bırakma işlevlerini denetleyebilen anahtar sözcüğü ve işlevi açıklanmaktadır.

## <a name="resources"></a>Kaynaklar

*Kaynak* terimi birden çok şekilde kullanılır. Evet, kaynaklar, bir uygulamanın kullandığı dizeler, grafikler ve gibi veriler olabilir, ancak bu bağlamda *kaynaklar* , grafik cihaz bağlamları, dosya tanıtıcıları, ağ ve veritabanı gibi yazılım veya işletim sistemi kaynaklarına başvurur bağlantılar, bekleme tutamaçları gibi eşzamanlılık nesneleri vb. Bu kaynakların uygulamalar tarafından kullanılması, kaynağın işletim sisteminden veya diğer kaynak sağlayıcısından alınması ve daha sonra kaynağın başka bir uygulamaya sağlanması için havuza daha sonraki bir sürümü ile ilgilidir. Uygulamalar, kaynakları ortak havuza geri bırakmayan sorunlar oluşur.

## <a name="managing-resources"></a>Kaynakları yönetme

Bir uygulamadaki kaynakları verimli ve sorumlu bir şekilde yönetmek için kaynakları hemen ve öngörülebilir bir şekilde serbest bırakmanız gerekir. .NET Framework, `System.IDisposable` arabirimi sağlayarak bunu yapmanıza yardımcı olur. Uygulayan `System.IDisposable` bir tür, kaynakları doğru `System.IDisposable.Dispose` bir şekilde serbest bırakma yöntemine sahiptir. İyi yazılmış uygulamalar, sınırlı bir `System.IDisposable.Dispose` kaynağı tutan herhangi bir nesne artık gerekli olmadığında hemen olarak adlandırılan garantisi verir. Neyse ki .NET dillerinin çoğu daha kolay hale getirmek için destek sağlar ve F# özel durum yoktur. Dispose modelini destekleyen iki yararlı dil yapıları vardır: `use` Binding `using` ve function.

## <a name="use-binding"></a>Bağlamayı kullan

Anahtar sözcüğünün `let` bağlamakla benzer bir formu vardır: `use`

*değer* = *ifadesini* kullan

`let` Bağlama ile aynı işlevselliği sağlar, ancak değer kapsam dışına geçtiğinde değere bir `Dispose` çağrı ekler. Derleyicinin değer üzerinde null bir denetim eklediğinden, değeri ise `null`, `Dispose` çağrısının denenmediğini unutmayın.

Aşağıdaki örnek, `use` anahtar sözcüğü kullanılarak bir dosyanın otomatik olarak nasıl kapatılmasını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> Hesaplama ifadelerinde kullanabilirsiniz `use` , bu durumda `use` ifadenin özelleştirilmiş bir sürümü kullanılır. Daha fazla bilgi için bkz. [diziler](sequences.md), [zaman uyumsuz Iş akışları](asynchronous-workflows.md)ve [Hesaplama ifadeleri](computation-expressions.md).

## <a name="using-function"></a>Using Işlevi

`using` İşlevi aşağıdaki biçimdedir:

`using`(*İfade1*) *işlev veya-lambda*

Bir `using` ifadede *İfade1* , atılmalıdır olması gereken nesneyi oluşturur. *İfade1* (atılması gereken nesne) sonucu, tarafından *oluşturulan değerle eşleşen bir türün bir kalan bağımsız değişkenini bekleyen bir işlev olan Function veya-lambda öğesine bir bağımsız değişken, değer olur. İfade1*veya bu tür bir bağımsız değişken bekleyen bir lambda ifadesi. İşlevi yürütmenin sonunda, çalışma zamanı kaynakları çağırır `Dispose` ve serbest bırakır (değer olmadığı `null`takdirde, Dispose çağrısı denenmez).

Aşağıdaki örnek, bir Lambda `using` ifadesi ile ifadeyi gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

Sonraki örnekte, `using` ifadesi bir işlev ile gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

İşlevin, zaten uygulanmış bazı bağımsız değişkenlerin bulunduğu bir işlev olabileceğini unutmayın. Aşağıdaki kod örneği bunu gösterir. Dizeyi `XYZ`içeren bir dosya oluşturur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` İşlevi`use` ve bağlama, aynı şeyi gerçekleştirmenin neredeyse denk bir yollardır. Anahtar sözcüğü çağrıldığında daha fazla denetim `Dispose` sağlar. `using` Kullandığınızda `using`, `Dispose` işlevin veya lambda ifadesinin sonunda çağrılır `use` ; anahtar sözcüğünü kullandığınızda, `Dispose` kapsayan kod bloğunun sonunda çağırılır. Genel olarak, `use` `using` işlevi yerine kullanmayı tercih etmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
