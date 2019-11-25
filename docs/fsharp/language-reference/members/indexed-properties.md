---
title: Dizini Oluşturulan Özellikler
description: İçindeki F#dizinli özellikler hakkında bilgi edinin. Bu, sıralı verilere dizi benzeri erişim sağlar.
ms.date: 11/04/2019
ms.openlocfilehash: f6cf3bfa737d2bf458e379594be5884696cee3e1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976607"
---
# <a name="indexed-properties"></a>Dizini Oluşturulan Özellikler

Sıralı verileri soyutlayan bir sınıf tanımlarken, bu verilere, temel alınan uygulamayı kullanıma açmadan dizin oluşturma erişimi sağlamak bazen yararlı olabilir. Bu, `Item` üyesiyle yapılır.

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

Önceki sözdiziminin formları, hem `get` hem de `set` yöntemi olan dizinli özelliklerin nasıl tanımlanacağını, yalnızca bir `get` yöntemine sahip olduğunu veya yalnızca bir `set` yöntemine sahip olduğunu gösterir. Ayrıca, yalnızca Get için gösterilen sözdizimini ve yalnızca set için gösterilen sözdizimini birleştirebilir ve hem Get hem de set içeren bir özellik oluşturabilirsiniz. Bu ikinci form, Get ve set yöntemlerine farklı erişilebilirlik değiştiricileri ve öznitelikler eklemenizi sağlar.

`Item`adı kullanılarak, derleyici özelliği varsayılan dizinli bir özellik olarak değerlendirir. *Varsayılan dizinli* bir özellik, nesne örneğinde dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir. Örneğin, `o` bu özelliği tanımlayan türün bir nesneslarsa, özelliğe erişmek için `o.[index]` sözdizimi kullanılır.

Varsayılan olmayan bir dizinli özelliğe erişim sözdizimi, bir normal üye gibi, özelliğin adını ve parantez içinde dizin sağlamaktır. Örneğin, `o` özelliği `Ordinal`olarak çağrılırsa, ona erişmek için `o.Ordinal(index)` yazarsınız.

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
    member _.Item
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
