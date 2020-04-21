---
title: İşaretçi ile ilgili işleçler - C# başvurusu
description: İşaretçilerle çalışırken kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 7eb6666d10c44c342f69c7cfc763feb1b7b98c9d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738611"
---
# <a name="pointer-related-operators-c-reference"></a>İşaretçi ile ilgili işleçler (C# başvurusu)

İşaretçilerle çalışmak için aşağıdaki işleçleri kullanabilirsiniz:

- Unary [ `&` (adres-of)](#address-of-operator-) işleci: bir değişkenin adresini almak için
- Unary [ `*` (işaretçi indirection)](#pointer-indirection-operator-) işleci: bir işaretçi tarafından işaret edilen değişkeni elde etmek için
- [ `->` (üye erişimi)](#pointer-member-access-operator--) ve [ `[]` (eleman erişimi)](#pointer-element-access-operator-) işleçleri
- Aritmetik işleçler [ `+`, `-` `++`, , ve`--`](#pointer-arithmetic-operators)
- Karşılaştırma işleçleri [ `==`, `!=` `<`, `>`, , `<=`ve`>=`](#pointer-comparison-operators)

İşaretçi türleri hakkında bilgi için [işaretçi türlerine](../../programming-guide/unsafe-code-pointers/pointer-types.md)bakın.

> [!NOTE]
> İşaretçileri olan herhangi bir işlem [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektirir. Güvenli olmayan bloklar içeren kod [`-unsafe`](../compiler-options/unsafe-compiler-option.md) derleyici seçeneği ile derlenmiş olmalıdır.

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a>İşleticinin adresi&amp;

Unary `&` işleticisi operand adresini döndürür:

[!code-csharp[address of local](snippets/PointerOperators.cs#AddressOf)]

İşleticinin `&` operand sabit bir değişken olmalıdır. *Sabit* [değişkenler, çöp toplayıcısının](../../../standard/garbage-collection/index.md)çalışmasından etkilenmeyen depolama konumlarında bulunan değişkenlerdir. Önceki örnekte, yerel değişken `number` sabit bir değişkendir, çünkü yığında bulunur. Çöp toplayıcıdan etkilenebilecek depolama konumlarında bulunan değişkenlere (örneğin, taşınan) *hareketli* değişkenler denir. Nesne alanları ve dizi öğeleri hareketli değişkenlere örnektir. Eğer "düzeltmek", ya da "pin", bir [ `fixed` deyimi](../keywords/fixed-statement.md)ile taşınır değişkenin adresini alabilirsiniz. Elde edilen adres yalnızca bir `fixed` deyim bloğu içinde geçerlidir. Aşağıdaki örnek, bir `fixed` deyimin ve `&` işlecinin nasıl kullanılacağını gösterir:

[!code-csharp[address of fixed](snippets/PointerOperators.cs#AddressOfFixed)]

Sabitveya değerin adresini alamazsınız.

Sabit ve taşınabilir değişkenler hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Sabit ve taşınabilir değişkenler](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) bölümüne bakın.

İkili `&` işleç, Boolean operandlarının veya [bitwise mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) integral operandlarının mantıksal [ve](boolean-logical-operators.md#logical-and-operator-) mantıksal ve hesaplamasını.

## <a name="pointer-indirection-operator-"></a>İşaretçi indirection işleci *

Unary işaretçi indirection işleci, `*` operand noktaları değişkeni elde eder. Dereference işleci olarak da bilinir. İşleticinin `*` operand bir işaretçi türünde olmalıdır.

[!code-csharp[pointer indirection](snippets/PointerOperators.cs#PointerIndirection)]

İşleç `*` türünü bir ifadeye `void*`uygulayamazsınız.

İkili `*` işleç, sayısal operandlarının [ürününü](arithmetic-operators.md#multiplication-operator-) hesaplar.

## <a name="pointer-member-access-operator--"></a>Pointer üye erişim işleci ->

İşleç `->` [işaretçi yönlendirme](#pointer-indirection-operator-) ve [üye erişimi](member-access-operators.md#member-access-expression-)birleştirir. Diğer bir `x` yazı, bir `T*` tür `y` işaretçisi `T`yse ve türünün erişilebilir bir üyesiyse, formun bir ifadesi

```csharp
x->y
```

eşdeğerdir

```csharp
(*x).y
```

Aşağıdaki örnek, işleç `->` kullanımını gösterir:

[!code-csharp[pointer member access](snippets/PointerOperators.cs#MemberAccess)]

İşleç `->` türünü bir ifadeye `void*`uygulayamazsınız.

## <a name="pointer-element-access-operator-"></a>İşaretçi öğesi erişim işleci []

Bir `p` işaretçi türünün ifadesi için, formun `p[n]` işaretçi `*(p + n)`öğesi `n` erişimi , örtülü olarak dönüştürülebilir `int` `uint`bir `long`tür `ulong`, , , veya . İşaretçilerle `+` ilgili işleç davranışı hakkında bilgi için, [integral değerinin işaretçi bölümüne veya işaretçi bölümüne eklenmesine veya çıkarını](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) görün.

Aşağıdaki örnek, bir işaretçi ve `[]` işleç ile dizi öğelerine nasıl erişilen gösteriş gösterir:

[!code-csharp[pointer element access](snippets/PointerOperators.cs#ElementAccess)]

Önceki örnekte, bir [ `stackalloc` ifade](stackalloc.md) yığınüzerinde bellek bloğu ayırır.

> [!NOTE]
> İşaretçi öğesi erişim işleci, sınır dışı hataları denetlemez.

Bir tür `[]` `void*`ifadesi ile işaretçi öğesi erişimi için kullanamazsınız.

Ayrıca [dizi öğesi veya dizinleyici erişimi](member-access-operators.md#indexer-operator-)için işleci kullanabilirsiniz. `[]`

## <a name="pointer-arithmetic-operators"></a>İşaretçi aritmetik işleçleri

İşaretçilerle aşağıdaki aritmetik işlemleri gerçekleştirebilirsiniz:

- Bir işaretçiye veya işaretçiden integral değeri ekleme veya çıkarma
- İki işaretçi çıkarma
- Bir işaretçiyi artım veya kararname

Bu işlemleri tür `void*`işaretçilerle gerçekleştiremezsiniz.

Sayısal türleri ile desteklenen aritmetik işlemler hakkında bilgi için [bkz.](arithmetic-operators.md)

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Bir integral değerinin bir işaretçiye veya işaretçiden eklenmesi veya çıkarTı

Bir tür `p` `T*` işaretçisi `n` ve örtülü olarak dönüştürülebilen bir tür ifadesi `int`için , , `uint` `long`, ekleme `ulong`ve çıkarma aşağıdaki gibi tanımlanır:

- Hem `p + n` `n + p` de ifadeler tarafından verilen `T*` adrese `n * sizeof(T)` eklenmesinden kaynaklanan `p`bir tür işaretçisi üretir.
- İfade, `p - n` `T*` `n * sizeof(T)` `p`'' tarafından verilen adresten çıkarma sonucu oluşan bir tür işaretçisi üretir.

[ `sizeof` Operatör](sizeof.md) baytlarda bir tür boyutunu elde eder.

Aşağıdaki örnek, `+` işleç bir işaretçi ile kullanımını gösterir:

[!code-csharp[pointer addition](snippets/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>İşaretçi çıkarması

İki işaretçi `p1` `p2` ve `T*`tür `p1 - p2` için, ifade `p1` tarafından verilen ve `p2` `sizeof(T)`bölünen adresler arasındaki farkı üretir. Sonucun türü `long`. Yani, `p1 - p2` olarak `((long)(p1) - (long)(p2)) / sizeof(T)`hesaplanır .

Aşağıdaki örnek, işaretçi çıkarma gösterir:

[!code-csharp[pointer subtraction](snippets/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>İşaretçi artış ve kararname

Artış `++` işleci işaretçisi operand'a 1 [ekler.](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) `--` Decrement işleci işaretçisi operand'Dan 1 [çıkarır.](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer)

Her iki işleç de iki şekilde`p++` `p--`desteklenir: postfix ( ve ) ve önek (`++p` ve `--p`). Sonucu `p++` ve `p--` işlem `p` *öncesi* değeridir. Sonuç `++p` ve `--p` işlem den `p` *sonra* değeridir.

Aşağıdaki örnek, hem postfix hem de önek artış lı işlemenlerin davranışını gösterir:

[!code-csharp[pointer increment](snippets/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>İşaretçi karşılaştırma işleçleri

Herhangi bir `==`işaretçi türündeki operandları karşılaştırmak için , , `!=`, `<` `>`, `<=`, ve `>=` işleçleri `void*`kullanabilirsiniz. Bu işleçler, iki operandtarafından verilen adresleri imzasız birermeçmiş gibi karşılaştırır.

Diğer türlerde operands için bu işleçlerin davranışı hakkında bilgi [için, Eşitlik işleçleri](equality-operators.md) ve [Karşılaştırma işleçleri](comparison-operators.md) makalelere bakın.

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, en yüksek öncelikten en düşük başlayarak ilgili işleçleri işaretçisi sipariş eder:

- Postfix artış `x++` ve decrement `x--` operatörleri `->` `[]` ve ve operatörler
- Önek `++x` artış ve `--x` decrement operatörleri `&` `*` ve ve operatörler
- Katkı `+` `-` maddesi ve operatörler
- Karşılaştırma `<` `>`, `<=`, `>=` , ve işleçler
- Eşitlik `==` ve `!=` operatörler

Operatör önceliği tarafından `()`dayatılan değerlendirme sırasını değiştirmek için parantez kullanın.

Öncelik düzeyine göre sıralanan C# işleçlerinin tam listesi için [C# işleçleri](index.md) makalesinin [Operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür işaretçi `&`yle `*` `->`ilgili `[]`işleçleri aşırı yükleyemez, ve .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Sabit ve taşınabilir değişkenler](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [İşleticinin adresi](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [İşaretçi yönlendirme](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [İşaretçi üye erişimi](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [İşaretçi öğesi erişimi](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [İşaretçi aritmetik](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [İşaretçi artış ve kararname](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [İşaretçi karşılaştırması](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [güvenli olmayan anahtar kelime](../keywords/unsafe.md)
- [sabit anahtar kelime](../keywords/fixed-statement.md)
- [stackalloc](stackalloc.md)
- [sizeof işleci](sizeof.md)
