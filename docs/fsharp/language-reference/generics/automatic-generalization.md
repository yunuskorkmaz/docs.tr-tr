---
title: Otomatik Genelleştirme
description: Mümkün olduğunda F# birden çok tür ile çalışacak şekilde işlevlerin bağımsız değişkenlerini ve türlerini otomatik olarak genelleştirir.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630632"
---
# <a name="automatic-generalization"></a>Otomatik Genelleştirme

F#işlev ve ifade türlerini değerlendirmek için tür çıkarımı kullanır. Bu konu, bağımsız F# değişkenleri ve işlev türlerini otomatik olarak genelleştirerek, bu mümkün olduğunda birden çok tür ile çalışabilmesini açıklar.

## <a name="automatic-generalization"></a>Otomatik Genelleştirme

F# Derleyici, bir işlevde tür çıkarımı gerçekleştirdiğinde, belirli bir parametrenin genel olup olmayacağını belirler. Derleyici her parametreyi inceler ve işlevin belirli bir parametre türüne bağımlılığı olup olmadığını belirler. Değilse, tür genel olarak algılanır.

Aşağıdaki kod örneği, derleyicinin genel olmasını sağlayan bir işlevi gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

Türü olarak algılanır `'a -> 'a -> 'a`.

Türü, aynı bilinmeyen türden iki bağımsız değişken alan ve aynı türde bir değer döndüren bir işlev olduğunu belirtir. Önceki işlevin genel olma nedenlerinden biri, büyüktür işlecinin (`>`) kendine genel olmasını sağlayabilir. Büyüktür işleci imzaya `'a -> 'a -> bool`sahiptir. Tüm işleçler geneldir ve bir işlevdeki kod bir parametre türünü genel olmayan bir işlev veya işleçle birlikte kullanıyorsa, bu parametre türü genelleştirilemez.

Genel olduğundan, aşağıdaki örneklerde gösterildiği gibi,, vb. gibi `int`türlerle `float`kullanılabilir. `max`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

Ancak, iki bağımsız değişken aynı türde olmalıdır. İmza `'a -> 'a -> 'a`, değildir `'a -> 'b -> 'a`. Bu nedenle, türler eşleşmediğinden aşağıdaki kod bir hata oluşturur.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

İşlevi `max` , büyüktür işlecini destekleyen her türlü tür ile de çalışır. Bu nedenle, aşağıdaki kodda gösterildiği gibi bir dize üzerinde de kullanabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>Değer kısıtlaması

Derleyici, yalnızca açık bağımsız değişkenlere ve basit sabit değerlere sahip olan tüm işlev tanımlarında otomatik Genelleştirme gerçekleştirir.

Bu, belirli bir tür olarak sınırlı olmayan, ancak genelleştirilebilir bir kod derlemeye çalıştığınızda derleyicinin bir hata verdiği anlamına gelir. Bu sorun için hata iletisi *değer kısıtlaması*olarak değerler için otomatik Genelleştirme üzerinde bu kısıtlamayı ifade eder.

Genellikle, değer kısıtlaması hatası, bir yapının genel olmasını istediğinizde, derleyicinin Bunu genelleştirmek için yeterli bilgiye sahip olması veya genel olmayan bir yapı içinde yeterli tür bilgilerini yanlışlıkla atlarsanız meydana gelir. Değer kısıtlama hatasına çözüm, tür çıkarımı sorununu daha kesin bir şekilde kısıtlamak için aşağıdaki yollarla daha açık bilgi sağlamaktır:

- Bir değere veya parametreye açık bir tür ek açıklaması ekleyerek bir türü genel olmayan olacak şekilde kısıtlayın.

- Sorun, işlev bileşimi veya eksik curried işlev bağımsız değişkenleri gibi genel bir işlev tanımlamak için genelleştirilsel olmayan bir yapı kullanıyorsa, işlevi sıradan bir işlev tanımı olarak yeniden yazmayı deneyin.

- Sorun genelleştirilemeyecek kadar karmaşık bir ifadesiyse, fazladan, kullanılmamış bir parametre ekleyerek onu bir işlev haline getirin.

- Açık genel tür parametreleri ekleyin. Bu seçenek nadiren kullanılır.

- Aşağıdaki kod örnekleri, bu senaryoların her birini gösterir.

Durum 1: İfade çok karmaşık. Bu örnekte, listenin `counter` olması `int option ref`amaçlanmıştır, ancak basit bir sabit değer olarak tanımlanmamıştır.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Durum 2: Genel bir işlev tanımlamak için genelleştirtirilebilir olmayan bir yapı kullanma. Bu örnekte, işlev bağımsız değişkenlerinin kısmi bir uygulaması içerdiğinden, yapı genelleştirilebilir.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Durum 3: Fazladan, kullanılmamış bir parametre ekleniyor. Bu ifade Genelleştirme için yeterince basit olmadığından, derleyici değer kısıtlaması hatası verir.

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

Durum 4: Tür parametreleri ekleniyor.

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

Son durumda, değer bir tür işlevi olur ve örneğin aşağıdaki gibi birçok farklı türde değer oluşturmak için kullanılabilir:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Çıkarımı](../type-inference.md)
- [Genel Türler](index.md)
- [Statik Olarak Çözümlenmiş Tür Parametreleri](statically-resolved-type-parameters.md)
- [Kısıtlamalar](constraints.md)
