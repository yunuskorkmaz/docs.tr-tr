---
title: Devralma
description: Nasıl belirleyeceğinizi öğrenin F# kalıtım ilişkileri Devral' anahtar sözcüğü kullanılarak.
ms.date: 05/16/2016
ms.openlocfilehash: 775ee52039caf4c4ab65f82fa21d4e536135a12a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937468"
---
# <a name="inheritance"></a>Devralma

Devralma "olan bir" ilişkileri modellemek için kullanılan veya, nesne yönelimli programlama subtyping.

## <a name="specifying-inheritance-relationships"></a>Kalıtım ilişkileri belirtme

Devralma ilişkilerinde kullanarak belirttiğiniz `inherit` anahtar sözcüğü bir sınıf bildiriminde. Temel söz dizimi biçimi, aşağıdaki örnekte gösterilmiştir.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Bir sınıf, en fazla bir doğrudan temel sınıf olabilir. Bir taban sınıfı kullanarak belirtmezseniz `inherit` anahtar sözcüğü, örtük olarak sınıfının devraldığı `System.Object`.

## <a name="inherited-members"></a>Devralınan üyeler

Bir sınıf başka bir sınıftan devralınırsa, yöntemleri ve temel sınıfın üyelerine doğrudan üyesi türetilmiş sınıf değilmiş gibi türetilmiş sınıf kullanıcıları için kullanılabilir.

Let bağlamaları ve oluşturucu parametresi bir sınıfa özeldir ve bu nedenle, türetilmiş sınıflardan erişilemez.

Anahtar sözcüğü `base` türetilmiş sınıflarda kullanılabilir ve temel sınıf örneğine başvurur. Bu gibi kendi kendine tanımlayıcı kullanılır.

## <a name="virtual-methods-and-overrides"></a>Sanal yöntemleri ve geçersiz kılmaları

Sanal yöntemler (ve Özellikler) iş içinde biraz farklı F# diğer .NET dilleri ile karşılaştırıldığında. Yeni bir sanal üye bildirmek için kullandığınız `abstract` anahtar sözcüğü. Bunun için bu yöntem için varsayılan bir uygulama sağlamak ne olursa olsun. Bu nedenle tam bir temel sınıf sanal yöntemin tanımı bu düzen aşağıdaki gibidir:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

Ve türetilen bir sınıfta sanal bu yöntemin bir geçersiz kılma şu desene uygun olmalıdır:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Varsayılan uygulama temel sınıfta atlarsanız, temel sınıfı soyut bir sınıf olur.

Aşağıdaki kod örneğinde yeni bir sanal yöntemle bildirimi gösterilmektedir `function1` bir temel sınıf ve türetilen bir sınıfta geçersiz öğrenin.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Oluşturucular ve devralma

Türetilmiş sınıf içinde temel sınıf için oluşturucu çağrılmalıdır. Temel sınıf oluşturucusu için bağımsız değişken listesinde görünür `inherit` yan tümcesi. Öğesinden türetilen sınıf oluşturucusu için sağlanan bağımsız değişkenler kullanılan değerleri belirlenmesi gerekir.

Aşağıdaki kod, burada türetilmiş sınıf devralma yan tümcesinde temel sınıf oluşturucusunu çağırır, bir temel sınıf ve türetilmiş bir sınıf gösterir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

Birden çok Oluşturucu söz konusu olduğunda, aşağıdaki kod kullanılabilir. Türetilmiş sınıf oluşturucular ilk satırının `inherit` yan tümcesi ve alanları ile bildirilen açık alanlar olarak görünür `val` anahtar sözcüğü. Daha fazla bilgi için [açık alanlar: `val` Anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>Devralma alternatifleri

Küçük bir değişiklik türünün gerekli olduğu durumlarda, devralma alternatif olarak bir nesne ifadesi kullanmayı göz önünde bulundurun. Aşağıdaki örnek, bir nesne ifadesi yeni bir türetilmiş tür oluşturma için alternatif olarak kullanımını gösterir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Nesne ifadeleri hakkında daha fazla bilgi için bkz: [nesne ifadeleri](object-expressions.md).

Nesne Hiyerarşileri oluştururken, devralma yerine ayrılmış bir birleşim kullanarak göz önünde bulundurun. Ayrılmış birleşimler, ortak bir genel türü farklı nesne modeli değiştirilen davranışı da yapabilirsiniz. Tek bir birleşimdir genellikle birkaç küçük farklılıklar birbiriyle olan türetilen sınıfların gereksinimini ortadan kaldırabilirsiniz. Ayrılmış birleşimler hakkında daha fazla bilgi için bkz. [ayırt edici birleşimler](discriminated-unions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne İfadeleri](object-expressions.md)
- [F# Dili Başvurusu](index.md)