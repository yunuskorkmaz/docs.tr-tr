---
title: Devralma
description: "'Devralma' anahtar sözcük anahtar sözcüklerini kullanarak F# kalıtım ilişkilerini nasıl belirteceklerini öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400290"
---
# <a name="inheritance"></a>Devralma

Kalıtım, nesne yönelimli programlamada "is-a" ilişkisini veya alt yazımayı modellemek için kullanılır.

## <a name="specifying-inheritance-relationships"></a>Kalıtım İlişkileri Belirtme

Bir sınıf bildiriminde `inherit` anahtar kelimeyi kullanarak devralma ilişkilerini belirtirsiniz. Temel sözdizimsel form aşağıdaki örnekte gösterilmiştir.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Bir sınıfın en fazla bir doğrudan taban sınıfı olabilir. `inherit` Anahtar sözcüğü kullanarak bir taban sınıf belirtmezseniz, sınıf örtülü `System.Object`olarak .

## <a name="inherited-members"></a>Devralınmış Üyeler

Bir sınıf başka bir sınıftan devralıyorsa, taban sınıfın yöntemleri ve üyeleri türemiş sınıfın doğrudan üyeleriymiş gibi türemiş sınıfın kullanıcıları tarafından kullanılabilir.

Herhangi bir izin bağlamaları ve oluşturucu parametreleri bir sınıfa özeldir ve bu nedenle türemiş sınıflardan erişilemez.

Anahtar kelime `base` türemiş sınıflarda kullanılabilir ve taban sınıf örneğine başvurur. Kendini tanımlayıcı gibi kullanılır.

## <a name="virtual-methods-and-overrides"></a>Sanal Yöntemler ve Geçersiz Kılmalar

Sanal yöntemler (ve özellikler) F#'da diğer .NET dillerine göre biraz farklı çalışır. Yeni bir sanal üye bildirmek `abstract` için anahtar kelimeyi kullanırsınız. Bu yöntem için varsayılan bir uygulama sağlayıp sağlamadığınıza bakılmaksızın bunu yaparsınız. Böylece bir taban sınıfta sanal yöntemin tam bir tanımı aşağıdaki şekilde dir:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

Ve türetilmiş bir sınıfta, bu sanal yöntemin geçersiz kılma bu desen izler:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Taban sınıfta varsayılan uygulamayı atlarsanız, taban sınıf soyut bir sınıf olur.

Aşağıdaki kod örneği, taban sınıfta yeni `function1` bir sanal yöntemin bildirimini ve türetilmiş bir sınıfta nasıl geçersiz kılındığını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Yapıcılar ve Kalıtım

Taban sınıfın oluşturucusu türemiş sınıfta çağrılmalıdır. Taban sınıf oluşturucuiçin bağımsız değişkenler `inherit` yan tümcedeki bağımsız değişken listesinde görünür. Kullanılan değerler türemiş sınıf oluşturucuya sağlanan bağımsız değişkenlerden belirlenmelidir.

Aşağıdaki kod, türemiş sınıfın devralma yan tümcesinde taban sınıf oluşturucuyu çağırdığı bir taban sınıf ve türetilmiş sınıf gösterir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

Birden çok oluşturucu söz konusu olduğunda, aşağıdaki kod kullanılabilir. Türemiş sınıf oluşturucularının ilk `inherit` satırı yan tümcedir ve alanlar `val` anahtar sözcükle birlikte bildirilen açık alanlar olarak görünür. Daha fazla bilgi için [bkz: Açık Alanlar: `val` Anahtar Kelime.](./members/explicit-fields-the-val-keyword.md)

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

## <a name="alternatives-to-inheritance"></a>Kalıtıma Alternatifler

Bir türün küçük bir değişiklik gerekli olduğu durumlarda, devralma alternatif olarak bir nesne ifadesi kullanmayı düşünün. Aşağıdaki örnekte, nesne ifadesinin yeni bir türetilmiş tür oluşturmaya alternatif olarak kullanılması gösteriş verilmiştir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Nesne ifadeleri hakkında daha fazla bilgi için [bkz.](object-expressions.md)

Nesne hiyerarşileri oluştururken, devralma yerine ayrımcı bir birliktelik kullanmayı düşünün. Ayrımcı birgörünüm, ortak bir genel türü paylaşan farklı nesnelerin çeşitli davranışlarını da modelleyebilir. Tek bir ayrımcı birliktelik genellikle birbirinin küçük varyasyonları olan türemiş sınıflar bir dizi ihtiyacını ortadan kaldırabilir. Ayrımcı sendikalar hakkında bilgi için [bkz.](discriminated-unions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne İfadeleri](object-expressions.md)
- [F# Dil Referansı](index.md)
