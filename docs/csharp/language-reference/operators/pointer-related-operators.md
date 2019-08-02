---
title: İşaretçiden ilgili işleçler- C# başvuru
description: İşaretçilerle C# çalışırken kullanabileceğiniz işleçler hakkında bilgi edinin.
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
ms.openlocfilehash: 830aef8546191df3df4a70e350ba561367a9e474
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512347"
---
# <a name="pointer-related-operators-c-reference"></a>İşaretçiden ilgili işleçler (C# başvuru)

İşaretçilerle çalışmak için aşağıdaki işleçleri kullanabilirsiniz:

- [ Birli`&` (Adres-of)](#address-of-operator-) işleci: bir değişkenin adresini almak için
- [ Birli`*` (işaretçi yöneltme)](#pointer-indirection-operator-) işleci: bir işaretçiye işaret eden değişkeni almak için
- (Üye erişimi) ve [ `->` ](#pointer-member-access-operator--) [ `[]` (öğe erişimi)](#pointer-element-access-operator-) işleçleri
- Aritmetik işleçler [ `+` ,`-` ,`++`, ve`--`](#pointer-arithmetic-operators)
- Karşılaştırma işleçleri [ `==` `!=`, ,`<`,,ve `>` `<=``>=`](#pointer-comparison-operators)

İşaretçi türleri hakkında bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> İşaretçilerle herhangi bir işlem [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektirir. Güvenli olmayan bloklar içeren kodun [`-unsafe`](../compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.

## <a name="address-of-operator-"></a>Address-of işleci&amp;

Birli `&` işleç, işleneninin adresini döndürür:

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

`&` İşlecin işleneni sabit bir değişken olmalıdır. *Sabit* değişkenler, [Atık toplayıcısının](../../../standard/garbage-collection/index.md)işleminden etkilenmeyen depolama konumlarında bulunan değişkenlerdir. Yukarıdaki örnekte, yerel değişken `number` yığında bulunduğundan sabit bir değişkendir. Çöp toplayıcısından etkilenebilecek (örneğin, yeniden konumlandırılan) depolama konumlarında bulunan değişkenler *Taşınabilir* değişkenler olarak adlandırılır. Nesne alanları ve dizi öğeleri taşınabilir değişkenlerin örnekleridir. Taşınabilir bir değişkenin adresini, [fixed](../keywords/fixed-statement.md) ifadesiyle "düzeltmenizi" veya "sabitle" yaparsanız alabilirsiniz. Alınan adres yalnızca `fixed` bildiri bloğunun süresi için geçerlidir. Aşağıdaki örnek, `fixed` ifadesinin `&` ve işlecinin nasıl kullanılacağını gösterir:

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

Bir sabit veya bir değerin adresini alamazsınız.

Sabit ve taşınabilir değişkenler hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sabit ve taşınabilir değişkenler](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) bölümüne bakın.

Binary `&` işleci, Boolean işlenenlerinin [mantıksal ve](boolean-logical-operators.md#logical-and-operator-) işlecini ya da tam sayı işlenenlerinin [bit düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar.

## <a name="pointer-indirection-operator-"></a>İşaretçi yöneltme işleci *

Birli işaretçi yöneltme işleci `*` , işleneninin gösterdiği değişkeni edinir. Başvuru operatörü olarak da bilinir. `*` İşlecin işleneni bir işaretçi türünde olmalıdır.

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

`*` İşleci türündeki`void*`bir ifadeye uygulayamazsınız.

İkili `*` işleç, sayısal işlenenlerinin [çarpımını](arithmetic-operators.md#multiplication-operator-) hesaplar.

## <a name="pointer-member-access-operator--"></a>İşaretçi üyesi erişim işleci->

İşleci işaretçi yöneltme ve [üye erişimini](member-access-operators.md#member-access-operator-)birleştirir. [](#pointer-indirection-operator-) `->` Diğer bir deyişle, `x` türü `T*` işaretçisiyse ve `y` ' nin `T`erişilebilir bir üyesi ise, formun bir ifadesi

```csharp
x->y
```

eşdeğerdir

```csharp
(*x).y
```

Aşağıdaki örnek `->` işlecinin kullanımını gösterir:

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

`->` İşleci türündeki`void*`bir ifadeye uygulayamazsınız.

## <a name="pointer-element-access-operator-"></a>İşaretçi öğesi erişim işleci []

İşaretçi türünün bir `p` ifadesi için, formun `p[n]` işaretçi öğesi erişimi olarak `*(p + n)`değerlendirilir; `n` burada `int`, `uint` `long`,, veya ' a örtülü olarak dönüştürülebilir bir tür olması gerekir `ulong`. İşaretçilerle `+` işlecin davranışı hakkında daha fazla bilgi için, [bir tam sayı değerinin bir işaretçi bölümüne eklenmesi veya çıkarılması](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) bölümüne bakın.

Aşağıdaki örnek, bir işaretçi ve `[]` işleçle dizi öğelerine nasıl erişileceğini göstermektedir:

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

Örnek, yığındaki bir bellek bloğunu ayırmak için [ `stackalloc` işlecini](stackalloc.md) kullanır.

> [!NOTE]
> İşaretçi öğesi erişim işleci, sınır dışı hataları denetlemez.

`[]` Türünde`void*`bir ifadeyle işaretçi öğesi erişimi için kullanamazsınız.

`[]` [Dizi öğesi veya Dizin Oluşturucu erişimi](member-access-operators.md#indexer-operator-)için işlecini de kullanabilirsiniz.

## <a name="pointer-arithmetic-operators"></a>İşaretçi aritmetik işleçleri

İşaretçilerle aşağıdaki aritmetik işlemleri gerçekleştirebilirsiniz:

- Bir işaretçiye veya işaretçiden tamsayı değer ekleme veya çıkarma
- İki işaretçileri çıkar
- Bir işaretçiyi artırma veya azaltma

Bu işlemleri türündeki `void*`işaretçilerle gerçekleştiremezsiniz.

Sayısal türlerle desteklenen aritmetik işlemler hakkında daha fazla bilgi için bkz. [Aritmetik işleçler](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Bir işaretçiye veya bir işaretçiye tamsayı değer ekleme veya çıkarma

`p` Türünde `long` `int` `n` `uint` `ulong`bir işaretçi ve bir türün bir ifadesi için örtük olarak dönüştürülebilir,,, veya, toplama ve çıkarma için aşağıdaki gibi tanımlanır: `T*`

- Hem `p + n` hem `n + p` de ifadeleri, tarafından `n * sizeof(T)` `T*` verilen`p`adrese eklenmesinin sonucu olan türünde bir işaretçi üretir.
- İfade `p - n` , `n * sizeof(T)` tarafından `T*` verilenadrestençıkarılmasınanedenolantürde`p`bir işaretçi oluşturur.

İşleci bir türün boyutunu bayt cinsinden edinir. [ `sizeof` ](sizeof.md)

Aşağıdaki örnek, bir işaretçi ile `+` işlecinin kullanımını gösterir:

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>İşaretçi çıkarması

İki `p1` işaretçi ve `p2` türü `T*`için, ifadesi `p1 - p2` tarafından `p1` verilen ve `p2` tarafından bölünenadreslerarasındakifarkıüretir.`sizeof(T)` Sonucun `long`türü. Diğer bir deyişle `p1 - p2` , olarak `((long)(p1) - (long)(p2)) / sizeof(T)`hesaplanır.

Aşağıdaki örnekte işaretçi çıkarma gösterilmektedir:

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>İşaretçi artışı ve azaltma

Artış `++` işleci, işaretçi işleneni 1 [ekler](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) . Azaltma `--` işleci, 1 işaretçi işlenenden [çıkartır](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .

İki tür işleç desteklenir: sonek`p++` (ve `p--`) ve ön ek (`++p` ve `--p`). `p++` `p` Ve sonucu`p--` , işlemden *önceki* değeridir. `++p` `p` Ve sonucu`--p` , işlemden *sonraki* değeridir.

Aşağıdaki örnek, hem sonek hem de önek artırma işleçlerinin davranışını gösterir:

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>İşaretçi karşılaştırma işleçleri

`==` ,`!=` ,,`>=` , Ve işleçlerini, gibi herhangi bir işaretçi türünün`void*`işlenenlerini karşılaştırmak için kullanabilirsiniz. `<` `>` `<=` Bu işleçler, iki işlenen tarafından verilen adresleri işaretsiz tamsayılar gibi karşılaştırır.

Diğer türlerin işlenenleri için bu işleçlerin davranışı hakkında daha fazla bilgi için bkz. [eşitlik işleçleri](equality-operators.md) ve [karşılaştırma işleçleri](comparison-operators.md) makaleleri.

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, işaretçinin ilgili işleçlerini en yüksek öncelikten en düşüğe başlayarak sıralar:

- Sonek artırma `x++` ve azaltma `x--` işleçleri ve `->` ve `[]` işleçleri
- Ön ek `++x` artırma ve `--x` azaltma işleçleri ve `&` ve `*` işleçleri
- Eklenebilir `+` ve `-` işleçler
- Karşılaştırma `<`, `>`, ,`<=`ve işleçler`>=`
- Eşitlik `==` ve `!=` işleçler

İşleç önceliğine göre `()`uygulanan değerlendirmenin sırasını değiştirmek için parantez ' nu kullanın.

Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için bkz [ C# . işleçler](index.md).

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı `&`bir tür, işaretçiyle ilgili işleçleri `->`, `*`, ve ile `[]`aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Sabit ve taşınabilir değişkenler](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Address-of işleci](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [İşaretçi yöneltme](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [İşaretçi üye erişimi](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [İşaretçi öğesi erişimi](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [İşaretçi aritmetik](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [İşaretçi artışı ve azaltma](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [İşaretçi karşılaştırması](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [güvenli olmayan anahtar sözcük](../keywords/unsafe.md)
- [Fixed anahtar sözcüğü](../keywords/fixed-statement.md)
- [stackalloc işleci](stackalloc.md)
- [sizeof işleci](sizeof.md)
