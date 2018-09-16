---
title: Dizini Oluşturulan Özellikler (F#)
description: 'Sıralı verilerine dizi benzeri erişim sağlayan özellikleri olan F # dizinli özellikleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: e56e4e2ea3f35df4c8ec46012357242cb6ce69f3
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45686173"
---
# <a name="indexed-properties"></a>Dizini Oluşturulan Özellikler

*Dizin oluşturulmuş özellikleri* dizi benzeri erişim sağlayan özellikler veri sıralanır. Üç formlarında geldikleri:

* `Item`
* `Ordinal`
* `Cardinal`

Bir F # üye bir dizi benzeri erişim sağlamak için bu üç ad adlandırılmalıdır. `IndexerName` Aşağıdaki üç seçenekten birini temsil etmek için kullanılır:

## <a name="syntax"></a>Sözdizimi

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>Açıklamalar

Her ikisi de Dizinlenmiş özelliklerin nasıl tanımlanacağı önceki sözdizimi formlarda gösterilen bir `get` ve `set` yöntemi sahip bir `get` yöntemi yalnızca veya bir `set` yalnızca yöntemi. Her ikisi de yalnızca get ve yalnızca kümesi için sözdizimini sözdizimini birleştirin ve hem get hem de kümesi olan bir özellik oluşturur. Bu ikinci form üzerinde get farklı erişilebilirlik değiştiricileri ve öznitelikleri yerleştirin ve yöntemleri ayarlamanıza olanak sağlar.

Zaman *IndexerName* olduğu `Item`, derleyici özelliği bir varsayılan dizini oluşturulan özellik olarak değerlendirir. A *varsayılan dizini oluşturulan özellik* Pro instanci objektu dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir. Örneğin, varsa `obj` bu özellik, söz dizimi tanımlayan türünde bir nesnedir `obj.[index]` özelliğine erişmek için kullanılır.

Varsayılan olmayan dizine özelliğine erişmek için söz dizimi, özelliğin adını ve parantez içinde dizin sağlamaktır. Örneğin, özellik ise `Ordinal`, yazdığınız `obj.Ordinal(index)` erişmek için.

Kullandığınız formdan ne olursa olsun, curried form için her zaman kullanmalısınız `set` bir dizinlenmiş özellik yöntemi. Curried işlevleri hakkında daha fazla bilgi için bkz: [işlevleri](../functions/index.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, varsayılan ve get ve set yöntemlerinin varsayılan olmayan Dizinli Özellikler ve tanımı gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Çıkış

```
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
