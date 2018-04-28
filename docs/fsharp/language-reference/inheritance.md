---
title: Devralma (F#)
description: "Devralma 'devralmak' anahtar sözcüğünü kullanarak F # ilişkileri belirleme konusunda bilgi edinin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4ad1494071cabb2a89321d653ec23ad513a46ef1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="inheritance"></a>Devralma

Devralma "olduğunu-a" ilişkileri modellemek için kullanılan veya, nesne odaklı programlama subtyping.


## <a name="specifying-inheritance-relationships"></a>Devralma ilişkisi belirtme
Devralma ilişkisi kullanarak belirttiğiniz `inherit` anahtar sözcüğü bir sınıf bildirimindeki. Temel söz dizimi form aşağıdaki örnekte gösterilir.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Bir sınıf en fazla bir doğrudan temel sınıfı olabilir. Bir taban sınıf kullanarak belirtmezseniz `inherit` anahtar sözcüğü, örtük olarak sınıfının devraldığı `System.Object`.


## <a name="inherited-members"></a>Devralınan üyeleri
Başka bir sınıftan bir sınıf, yöntemleri ve taban sınıfı üyeleri türetilmiş sınıf doğrudan üyesi değilmiş gibi türetilmiş sınıf kullanıcıları için kullanılabilir.

Let bağlamaları ve Oluşturucu parametreleri bir sınıfa özel olan ve, bu nedenle, türetilmiş sınıflarından erişilemez.

Anahtar sözcüğü `base` türetilmiş sınıflarda kullanılabilir ve temel sınıf örneğine başvurur. Kendi kendine tanımlayıcı gibi kullanılır.


## <a name="virtual-methods-and-overrides"></a>Sanal yöntemler ve geçersiz kılmalar
Sanal yöntemler (ve özellikleri) biraz farklı F #'ta diğer .NET dilleri ile karşılaştırıldığında çalışır. Yeni bir sanal üye bildirmek için kullandığınız `abstract` anahtar sözcüğü. Bunun için bu yöntem için bir varsayılan uygulama sağlamak bağımsız olarak. Bu nedenle tam bir temel sınıf sanal bir yöntem tanımının bu deseni izler:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

Ve türetilen bir sınıfta geçersiz kılma sanal bu yöntemin bu deseni izler:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Varsayılan uygulaması temel sınıf atlarsanız, temel sınıf soyut bir sınıf haline gelir.

Yeni sanal bir yöntem bildirimi aşağıdaki kod örneği gösterilmektedir `function1` bir taban sınıf ve türetilen bir sınıfta geçersiz kılmak nasıl.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a>Oluşturucular ve devralma
Taban sınıfı oluşturucusu türetilen sınıfta çağrılmalıdır. İçin temel sınıf oluşturucu bağımsız değişken listesinde görünür `inherit` yan tümcesi. Türetilmiş sınıf oluşturucu sağlanan bağımsız değişkenler gelen kullanılan değerleri belirlenmesi gerekir.

Aşağıdaki kod, burada türetilmiş sınıf devralma yan tümcesinde temel sınıf oluşturucu çağırır bir taban sınıf ve türetilmiş bir sınıf gösterir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

Birden çok oluşturucular söz konusu olduğunda, aşağıdaki kod kullanılabilir. Türetilmiş sınıf oluşturucu ilk satırı `inherit` yan tümcesi ve alanlar görünür ile bildirilen açık alanlar olarak `val` anahtar sözcüğü. Daha fazla bilgi için bkz: [açık alanlar: `val` anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).

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
Küçük bir değişiklik türünün gerekli olduğu durumlarda, bir nesne ifadesi devralma alternatif olarak düşünün. Aşağıdaki örnek yeni türetilmiş bir tür oluşturma alternatif olarak bir nesne ifadesi kullanımını göstermektedir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Nesne ifadeleri hakkında daha fazla bilgi için bkz: [nesne ifadeleri](object-expressions.md).

Nesne Hiyerarşileri oluştururken, ayrılmış bir birleşim yerine devralma kullanmayı düşünün. Ayrılmış birleşimler de ortak bir genel tür paylaşmak farklı nesneleri değişmesi modeli davranışını görüntüleyebilirsiniz. Tek bir ayrılmış birleşim genellikle birbiriyle küçük farklılıkları olan türetilmiş sınıfları sayısı gereksinimini ortadan kaldırabilirsiniz. Ayrılmış birleşimler hakkında daha fazla bilgi için bkz: [ayrılmış birleşimler](discriminated-unions.md).


## <a name="see-also"></a>Ayrıca Bkz.
[Nesne İfadeleri](object-expressions.md)

[F# Dili Başvurusu](index.md)
