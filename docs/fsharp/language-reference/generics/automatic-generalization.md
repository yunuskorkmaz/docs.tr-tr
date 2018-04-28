---
title: Otomatik Genelleştirme (F#)
description: 'Böylece birden çok tür mümkün olduğunda çalıştıkları nasıl F # otomatik olarak işlevleri türünü ve bağımsız değişkenler genelleştirir öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 9b599fd9fe1220b41987bc14a420ed5740aa05f5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="automatic-generalization"></a>Otomatik Genelleştirme

F # tür çıkarımı türlerini işlevleri ve ifadeler değerlendirmek için kullanır. Bu konu, mümkün olduğunda bunlar birden çok tür çalışmak üzere nasıl F # otomatik olarak işlevleri türünü ve bağımsız değişkenler genelleştirir açıklar.


## <a name="automatic-generalization"></a>Otomatik Genelleştirme
Tür çıkarımı işlevi üzerinde gerçekleştirdiğinde, F # derleyici, verilen bir parametrenin genel olup olamayacağını belirler. Derleyici her bir parametreyi inceler ve işlevi bu parametrenin belirli türüne bir bağımlılığa sahip olup olmadığını belirler. Yoksa, türü genel olarak algılanır.

Aşağıdaki kod örneğinde genel olarak derleyici oluşturur bir işlev gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

Tür çıkarımı yapılan olmasını `'a -> 'a -> 'a`.

Türü bu aynı bilinmeyen türde iki bağımsız değişken alan ve aynı türde bir değer döndüren bir işlev gösterir. Önceki işlevi olabilir nedenlerden biri dolayısıyla genel daha büyük olan-işleci'den (`>`) kendisi geneldir. Büyük-işleci imza varolandan `'a -> 'a -> bool`. Tüm işleçleri geneldir ve kod işlevinin parametre türü bir genel olmayan işlev veya işleci birlikte kullanıyorsa, bu parametre türü genelleştirilmiş olamaz.

Çünkü `max` olan genel, bu tür gibi kullanılabilir `int`, `float`ve benzeri, aşağıdaki örneklerde gösterildiği gibi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

Ancak, iki bağımsız değişkenleri aynı türde olmalıdır. İmza `'a -> 'a -> 'a`değil `'a -> 'b -> 'a`. Bu nedenle, türleri eşleşmediği için aşağıdaki kodu bir hata oluşturur.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max` İşlevi de büyük destekleyen herhangi bir türü ile çalışır-işleci daha. Bu nedenle, ayrıca, bir dizesine, aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a>Değer kısıtlama
Derleyici otomatik Genelleştirme yalnızca açık bağımsız değişkenlerinin tam işlev tanımları ve basit değişmez değerleri gerçekleştirir.

Başka bir deyişle, yeterince belirli bir tür olması zorunlu değildir, ancak aynı zamanda genelleştirilebilir Kodu derlemek çalışırsanız derleyici bir hata verir. Bu kısıtlama değerleri için otomatik Genelleştirme üzerinde bu sorun için hata iletisini başvurduğu *değer kısıtlaması*.

Genellikle, genel olarak bir yapı istiyor ancak derleyici onu genelleştirmek için yeterli bilgiye sahip olduğunda veya yeterli türü bilgileri nongeneric yapısında istemeden atladığınızda değer kısıtlama hatası oluşur. Değer kısıtlama hatası çözüme daha eksiksiz türü çıkarımı sorunu aşağıdaki yollardan biriyle sınırlamak için daha açık bilgilerini sağlamaktır:


- Bir tür değeri veya parametre için bir açık tür ek açıklama ekleyerek nongeneric olacak şekilde kısıtlar.

- Sorun kullanıyorsa, genel işlevi, bir işlev oluşturma gibi ya da eksik olarak tanımlamak için bir nongeneralizable yapısı curried işlev bağımsız değişkenleri uygulanır, bir sıradan işlev tanımı işlevi yeniden deneyin.

- Sorun genelleştirilmiş için çok karmaşık bir ifade ise, bir ek, kullanılmayan parametresini ekleyerek bir işlevdeki olun.

- Açık genel tür parametreleri ekleyin. Bu seçenek nadiren kullanılır.

- Aşağıdaki kod örnekleri bu senaryoların her biri gösterilmektedir.

Durum 1: Çok karmaşık bir ifade. Bu örnekte, listenin `counter` olması amaçlanmıştır `int option ref`, ancak basit bir sabit değer tanımlı değil.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Durum 2: nongeneralizable yapı genel işlevi tanımlamak için kullanma. İşlev bağımsız değişkenleri kısmi uygulaması içerdiğinden bu örnekte, nongeneralizable yapıdır.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Durum 3: bir ek, kullanılmayan parametresi ekleniyor. Bu ifade için genelleştirme kadar basit olmadığından derleyici değer kısıtlama hatası verir.

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

Durum 4: Tür parametreleri ekleme.

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

Son durumda, aşağıdaki gibi birçok farklı türlerde değerler örneğin oluşturmak için kullanılabilir bir tür işlevi değeri olur:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Ayrıca Bkz.
[Tür Çıkarımı](../type-inference.md)

[Genel Türler](index.md)

[Statik Olarak Çözümlenmiş Tür Parametreleri](statically-resolved-type-parameters.md)

[Kısıtlamalar](constraints.md)

