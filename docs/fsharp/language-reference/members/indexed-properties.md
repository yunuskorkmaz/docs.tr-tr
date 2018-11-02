---
title: Dizini Oluşturulan Özellikler (F#)
description: Dizinli Özellikler hakkında bilgi edinin F#, sıralı verilerine dizi benzeri erişim verin.
ms.date: 10/17/2018
ms.openlocfilehash: 3dac60eba3d9e7a9c3e76ad7ee051e6b30b88636
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "49452254"
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

## <a name="indexed-properties-with-multiple-index-variables"></a>Birden çok dizin değişkenleriyle dizini oluşturulan özellikler

Dizinli Özellikler birden fazla dizin değişkeni olabilir. Özelliği kullanıldığında, bu durumda, değişkenlerin virgülle ayrılır. Böyle bir özellik kümesi yöntemi ilki anahtarları içeren bir tanımlama grubu, ve ikinci ayarlanan değer iki curried bağımsız olması gerekir.

Aşağıdaki kod, birden çok dizin değişkenleri içeren bir dizini oluşturulmuş özelliğe kullanımını gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
