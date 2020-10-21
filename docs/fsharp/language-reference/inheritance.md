---
title: Devralma
description: "' İnherit ' anahtar sözcüğünü kullanarak F # devralma ilişkilerini belirtmeyi öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223850"
---
# <a name="inheritance"></a>Devralma

Devralma, nesne odaklı programlamada "a-a" ilişkisini veya alt yazmayı modellemek için kullanılır.

## <a name="specifying-inheritance-relationships"></a>Devralma Ilişkilerini belirtme

Devralma ilişkilerini `inherit` bir sınıf bildiriminde anahtar sözcüğünü kullanarak belirtirsiniz. Temel sözdizimsel form aşağıdaki örnekte gösterilmiştir.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Bir sınıf en fazla bir doğrudan temel sınıfa sahip olabilir. Anahtar sözcüğünü kullanarak bir temel sınıf belirtmezseniz `inherit` , sınıf dolaylı olarak öğesinden devralır `System.Object` .

## <a name="inherited-members"></a>Devralınmış Üyeler

Bir sınıf başka bir sınıftan devralırsa, temel sınıfın yöntemleri ve üyeleri türetilmiş sınıfın doğrudan üyeleri gibi türetilmiş sınıfın kullanıcıları tarafından kullanılabilir.

Tüm Let bağlamaları ve Oluşturucu parametreleri bir sınıfa özeldir ve bu nedenle türetilmiş sınıflardan erişilemez.

Anahtar sözcüğü `base` türetilmiş sınıflarda kullanılabilir ve temel sınıf örneğine başvurur. Kendi kendine tanımlayıcı gibi kullanılır.

## <a name="virtual-methods-and-overrides"></a>Sanal yöntemler ve geçersiz kılmalar

Sanal Yöntemler (ve Özellikler) F # ' da diğer .NET dillerine kıyasla biraz farklı şekilde çalışır. Yeni bir sanal üye bildirmek için `abstract` anahtar sözcüğünü kullanırsınız. Bu yöntem için varsayılan bir uygulama sağlayıp sağlamadığına bakılmaksızın bunu yapabilirsiniz. Bu nedenle, bir temel sınıftaki sanal bir yöntemin tüm tanımı bu modele uyar:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

Türetilmiş bir sınıfta, bu sanal yöntemin bir geçersiz kılma bu düzene uyar:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Temel sınıfta varsayılan uygulamayı atlarsanız, temel sınıf bir soyut sınıf olur.

Aşağıdaki kod örneği, bir temel sınıftaki yeni bir sanal yöntemin bildirimini `function1` ve türetilmiş bir sınıfta bunun nasıl geçersiz kılınacağını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Oluşturucular ve devralma

Temel sınıfa yönelik oluşturucunun türetilmiş sınıfta çağrılması gerekir. Temel sınıf oluşturucusunun bağımsız değişkenleri, yan tümcesindeki bağımsız değişken listesinde görünür `inherit` . Kullanılan değerlerin, türetilmiş sınıf oluşturucusuna sağlanan bağımsız değişkenlerden belirlenmesi gerekir.

Aşağıdaki kod, bir temel sınıf ve türetilmiş bir sınıf gösterir; burada türetilmiş sınıf, devralma yan tümcesinde temel sınıf oluşturucusunu çağırır:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

Birden çok Oluşturucu söz konusu olduğunda, aşağıdaki kod kullanılabilir. Türetilmiş sınıf oluşturucularının ilk satırı `inherit` yan tümcelerdir ve alanlar, anahtar sözcüğüyle belirtilen açık alanlar olarak görünür `val` . Daha fazla bilgi için bkz. [açık alanlar: `val` anahtar sözcük](./members/explicit-fields-the-val-keyword.md).

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

Bir tür için küçük bir değişikliğin gerekli olduğu durumlarda, devralma için alternatif olarak bir nesne ifadesi kullanmayı düşünün. Aşağıdaki örnek, yeni bir türetilmiş tür oluşturmaya alternatif olarak bir nesne ifadesinin kullanımını göstermektedir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Nesne ifadeleri hakkında daha fazla bilgi için bkz. [nesne ifadeleri](object-expressions.md).

Nesne hiyerarşileri oluştururken, devralma yerine ayrılmış bir birleşim kullanmayı göz önünde bulundurun. Ayırt edici birleşimler ayrıca ortak bir genel türü paylaşan farklı nesnelerin değişen davranışlarını modelleyebilir. Tek bir ayırt edici birleşim genellikle birbirleriyle ilgili küçük farklılıklar olan bir dizi türetilmiş sınıfa gereksinimi ortadan kaldırabilir. Ayrılmış birleşimler hakkında daha fazla bilgi için bkz. [ayırt edici birleşimler](discriminated-unions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne İfadeleri](object-expressions.md)
- [F # dil başvurusu](index.md)
