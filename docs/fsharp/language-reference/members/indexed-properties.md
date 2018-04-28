---
title: Dizini Oluşturulan Özellikler (F#)
description: 'Sıralı verilerine dizi benzeri erişim sağlayan özellikleri olan F # dizin oluşturulmuş özellikleri hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 39396b3a5ec43f9a8ab0df96afeb69e05801c752
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="indexed-properties"></a>Dizini Oluşturulan Özellikler

*Dizin oluşturulmuş özellikleri* dizi benzeri erişim sağlayan özellikler veri sıralanır.


## <a name="syntax"></a>Sözdizimi

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>Açıklamalar
Üç tür önceki sözdizimi hem de Dizinlenmiş özelliklerin nasıl tanımlanacağı Göster bir `get` ve `set` yöntemi, sahip bir `get` yöntemi yalnızca, veya bir `set` yalnızca yöntemi. Her ikisi de yalnızca get ve yalnızca kümesi için sözdizimini sözdizimini birleştirebilir ve hem get hem de kümesine sahip bir özellik üretir. Bu ikinci form farklı erişilebilirlik değiştiricileri ve öznitelikleri almada yerleştirin ve yöntemleri ayarlamanıza olanak sağlar.

Zaman *PropertyName* olan `Item`, derleyici özelliği bir varsayılan dizin oluşturulmuş özellik olarak değerlendirir. A *varsayılan dizin oluşturulmuş özellik* nesne örneğinde dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir. Örneğin, varsa `obj` bu özellik, söz dizimi tanımlayan türünde bir nesne `obj.[index]` özelliğine erişmek için kullanılır.

Varsayılan olmayan dizin oluşturulmuş özellik erişmek için söz dizimi özelliğin adını ve parantez içinde dizin sağlamaktır. Örneğin, özellik ise `Ordinal`, yazdığınız `obj.Ordinal(index)` erişmek için.

Kullandığınız formdan bağımsız olarak, curried form için her zaman kullanmalısınız `set` dizinlenmiş özelliğine yöntemi. Curried işlevleri hakkında daha fazla bilgi için bkz: [işlevler](../functions/index.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, tanım ve varsayılan ve get ve set yöntemlerinin varsayılan olmayan Dizinli Özellikler kullanımını gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Çıkış

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>Birden çok dizin değişkenleriyle Dizinli Özellikler
Dizinli Özellikler birden fazla dizin değişkeni olabilir. Özelliği kullanıldığında, bu durumda, değişkenleri virgülle ayrılır. Böyle bir özellik kümesi yönteminde anahtarları içeren bir tanımlama grubu ilki, ikinci ayarlanan değer ise iki curried bağımsız olması gerekir.

Aşağıdaki kod, birden çok dizin değişkenleriyle dizinli bir özelliği kullanımını göstermektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[Üyeler](index.md)
