---
title: Dizini Oluşturulan Özellikler
description: İçindeki F#dizinli özellikler hakkında bilgi edinin. Bu, sıralı verilere dizi benzeri erişim sağlar.
ms.date: 10/17/2018
ms.openlocfilehash: 379417e31b8e178d8c939e5b23dc144bfb17e562
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627562"
---
# <a name="indexed-properties"></a>Dizini Oluşturulan Özellikler

Sıralı verileri soyutlayan bir sınıf tanımlarken, bu verilere, temel alınan uygulamayı kullanıma açmadan dizin oluşturma erişimi sağlamak bazen yararlı olabilir. Bu, `Item` üyeyle yapılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminin `get` formları, hem a `set` hem de yöntemine sahip dizinlenmiş özelliklerin nasıl tanımlanacağını, yalnızca bir `get` yöntemine sahip olduğunu veya yalnızca bir `set` yöntemine sahip olduğunu gösterir. Ayrıca, yalnızca Get için gösterilen sözdizimini ve yalnızca set için gösterilen sözdizimini birleştirebilir ve hem Get hem de set içeren bir özellik oluşturabilirsiniz. Bu ikinci form, Get ve set yöntemlerine farklı erişilebilirlik değiştiricileri ve öznitelikler eklemenizi sağlar.

Ad `Item`kullanıldığında, derleyici özelliği varsayılan dizinli bir özellik olarak değerlendirir. *Varsayılan dizinli* bir özellik, nesne örneğinde dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir. Örneğin, bu özelliği `o` tanımlayan türün bir nesneslarsa, özelliğine erişmek için sözdizimi `o.[index]` kullanılır.

Varsayılan olmayan bir dizinli özelliğe erişim sözdizimi, bir normal üye gibi, özelliğin adını ve parantez içinde dizin sağlamaktır. Örneğin, üzerindeki `o` özelliği çağrılırsa `Ordinal`, ona erişmek için yazarsınız `o.Ordinal(index)` .

Kullandığınız formdan bağımsız olarak, dizinlenmiş bir özellikte set yöntemi için her zaman curried formunu kullanmanız gerekir. Curried işlevleri hakkında bilgi için bkz. [işlevler](../functions/index.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, Get ve set yöntemlerine sahip varsayılan ve varsayılan olmayan dizinli özelliklerin tanımını ve kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Çıkış

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Birden çok dizin değeri olan dizinli Özellikler

Dizinli Özellikler birden fazla dizin değerine sahip olabilir. Bu durumda, özellik kullanıldığında değerler virgülle ayrılır. Böyle bir özelliğindeki set yöntemi iki curried bağımsız değişkene sahip olmalıdır, ilki anahtarları içeren bir tanımlama grubu ve ikincisinin ayarlandığı değer.

Aşağıdaki kod, birden çok dizin değeri olan dizinli bir özelliğin kullanımını gösterir.

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
