---
title: Dizini Oluşturulan Özellikler
description: Dizinli Özellikler hakkında bilgi edinin F#, sıralı verilerine dizi benzeri erişim verin.
ms.date: 10/17/2018
ms.openlocfilehash: bc330641c451973ddefa0a34fe6e757a808f6cb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903831"
---
# <a name="indexed-properties"></a>Dizini Oluşturulan Özellikler

Sıralanmış veriler üzerinde soyutlayan bir sınıf tanımlanırken, bazen temel uygulamayı sokmadan verileri dizinlenmiş erişim sağlamak yararlı olabilir. Bunun `Index` üyesi.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Açıklamalar

Her ikisi de Dizinlenmiş özelliklerin nasıl tanımlanacağı önceki sözdizimi formlarda gösterilen bir `get` ve `set` yöntemi sahip bir `get` yöntemi yalnızca veya bir `set` yalnızca yöntemi. Her ikisi de yalnızca get ve yalnızca kümesi için sözdizimini sözdizimini birleştirin ve hem get hem de kümesi olan bir özellik oluşturur. Bu ikinci form üzerinde get farklı erişilebilirlik değiştiricileri ve öznitelikleri yerleştirin ve yöntemleri ayarlamanıza olanak sağlar.

Adını kullanarak `Item`, derleyici özelliği bir varsayılan dizini oluşturulan özellik olarak değerlendirir. A *varsayılan dizini oluşturulan özellik* Pro instanci objektu dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir. Örneğin, varsa `o` bu özellik, söz dizimi tanımlayan türünde bir nesnedir `o.[index]` özelliğine erişmek için kullanılır.

Varsayılan olmayan bir dizinlenmiş özellik erişmek için söz dizimi, özellik ve normal üye olduğu gibi parantez içinde dizin adını sağlamaktır. Örneğin, özellikte `o` çağrılır `Ordinal`, yazdığınız `o.Ordinal(index)` erişmek için.

Kullandığınız formdan bakılmaksızın, bir dizinlenmiş özellik kümesi yöntemi için curried formu her zaman kullanmalısınız. Curried işlevleri hakkında daha fazla bilgi için bkz: [işlevleri](../functions/index.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, varsayılan ve get ve set yöntemlerinin varsayılan olmayan Dizinli Özellikler ve tanımı gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Çıkış

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Birden çok dizin değerlerle dizini oluşturulan özellikler

Dizinli Özellikler birden fazla dizin değeri olabilir. Özelliği kullanıldığında, bu durumda, değerler virgülle ayrılır. Böyle bir özellik kümesi yöntemi bilgisayarının ilki anahtarları içeren bir tanımlama grubu ve ikinci değer ayarlamak için iki curried bağımsız olması gerekir.

Aşağıdaki kod, birden çok dizin değerlerini içeren bir dizini oluşturulmuş özelliğe kullanımını gösterir.

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
