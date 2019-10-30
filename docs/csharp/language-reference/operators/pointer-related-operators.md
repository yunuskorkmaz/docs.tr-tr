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
ms.openlocfilehash: 9851fcd056eeee33b8f3d7e9d541f9fa43b36d29
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036159"
---
# <a name="pointer-related-operators-c-reference"></a>İşaretçiden ilgili işleçler (C# başvuru)

İşaretçilerle çalışmak için aşağıdaki işleçleri kullanabilirsiniz:

- Birli [`&` (Adres-of)](#address-of-operator-) işleci: bir değişkenin adresini almak için
- Birli [`*` (işaretçi yöneltme)](#pointer-indirection-operator-) işleci: bir işaretçiye göre işaret eden değişkeni elde etmek için
- [`->` (üye erişimi)](#pointer-member-access-operator--) ve [`[]` (öğe erişimi)](#pointer-element-access-operator-) işleçleri
- Aritmetik işleçler [`+`, `-`, `++`ve `--`](#pointer-arithmetic-operators)
- Karşılaştırma işleçleri [`==`, `!=`, `<`, `>`, `<=`ve `>=`](#pointer-comparison-operators)

İşaretçi türleri hakkında bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> İşaretçilerle herhangi bir işlem [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektirir. Güvenli olmayan bloklar içeren kodun [`-unsafe`](../compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.

## <a name="address-of-operator-"></a>Address-of işleci &amp;

Birli `&` işleci, işleneninin adresini döndürür:

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

`&` işlecinin işleneni sabit bir değişken olmalıdır. *Sabit* değişkenler, [Atık toplayıcısının](../../../standard/garbage-collection/index.md)işleminden etkilenmeyen depolama konumlarında bulunan değişkenlerdir. Yukarıdaki örnekte, `number` yerel değişkeni yığında bulunduğundan sabit bir değişkendir. Çöp toplayıcısından etkilenebilecek (örneğin, yeniden konumlandırılan) depolama konumlarında bulunan değişkenler *Taşınabilir* değişkenler olarak adlandırılır. Nesne alanları ve dizi öğeleri taşınabilir değişkenlerin örnekleridir. Taşınabilir bir değişkenin adresini, bir [`fixed` ifadesiyle](../keywords/fixed-statement.md)"düzelmiyor" veya "sabitle" yaparsanız alabilirsiniz. Alınan adres yalnızca bir `fixed` deyimin bloğu içinde geçerlidir. Aşağıdaki örnek, bir `fixed` deyimin ve `&` işlecinin nasıl kullanılacağını gösterir:

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

Bir sabit veya bir değerin adresini alamazsınız.

Sabit ve taşınabilir değişkenler hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sabit ve taşınabilir değişkenler](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) bölümüne bakın.

İkili `&` işleci, Boolean işlenenlerinin [MANTıKSAL ve](boolean-logical-operators.md#logical-and-operator-) [mantıksal değerini](bitwise-and-shift-operators.md#logical-and-operator-) ya da tam sayı işlenenlerini hesaplar.

## <a name="pointer-indirection-operator-"></a>İşaretçi yöneltme işleci *

Birli işaretçi yöneltme işleci `*` işleneninin gösterdiği değişkeni alır. Başvuru operatörü olarak da bilinir. `*` işlecinin işleneni bir işaretçi türünde olmalıdır.

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

`void*`türündeki bir ifadeye `*` işlecini uygulayamazsınız.

İkili `*` işleci, sayısal işlenenlerinin [çarpımını](arithmetic-operators.md#multiplication-operator-) hesaplar.

## <a name="pointer-member-access-operator--"></a>İşaretçi üyesi erişim işleci->

`->` işleci, [işaretçi yöneltme](#pointer-indirection-operator-) ve [üye erişimini](member-access-operators.md#member-access-operator-)birleştirir. Diğer bir deyişle, `x` `T*` türünde bir işaretçisiyse ve `y` `T`türü bir ifade olan erişilebilir bir üyedir.

```csharp
x->y
```

eşdeğerdir

```csharp
(*x).y
```

Aşağıdaki örnek `->` işlecinin kullanımını gösterir:

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

`void*`türündeki bir ifadeye `->` işlecini uygulayamazsınız.

## <a name="pointer-element-access-operator-"></a>İşaretçi öğesi erişim işleci []

İşaretçi türünün bir ifadesi `p` için, form `p[n]` bir işaretçi öğesi erişimi `*(p + n)`olarak değerlendirilir, burada `n` örtük olarak `int`, `uint`, `long`bir türde olmalıdır veya `ulong`. İşaretçilerle `+` işlecinin davranışı hakkında daha fazla bilgi için, [bir tam sayı değerini bir işaretçi bölümüne ekleme veya çıkarma](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) bölümüne bakın.

Aşağıdaki örnek, bir işaretçi ve `[]` işleci ile dizi öğelerine nasıl erişileceğini gösterir:

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

Örnek, yığında bir bellek bloğu ayırmak için [`stackalloc` işlecini](stackalloc.md) kullanır.

> [!NOTE]
> İşaretçi öğesi erişim işleci, sınır dışı hataları denetlemez.

`void*`türünde bir ifadeyle işaretçi öğesi erişimi için `[]` kullanamazsınız.

[Dizi öğesi veya Dizin Oluşturucu erişimi](member-access-operators.md#indexer-operator-)için `[]` işlecini de kullanabilirsiniz.

## <a name="pointer-arithmetic-operators"></a>İşaretçi aritmetik işleçleri

İşaretçilerle aşağıdaki aritmetik işlemleri gerçekleştirebilirsiniz:

- Bir işaretçiye veya işaretçiden tamsayı değer ekleme veya çıkarma
- İki işaretçileri çıkar
- Bir işaretçiyi artırma veya azaltma

`void*`türündeki işaretçilerle bu işlemleri gerçekleştiremezsiniz.

Sayısal türlerle desteklenen aritmetik işlemler hakkında daha fazla bilgi için bkz. [Aritmetik işleçler](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Bir işaretçiye veya bir işaretçiye tamsayı değer ekleme veya çıkarma

`T*` türü bir işaretçi `p` ve `int`, `uint`, `long`, veya `ulong`, toplama ve çıkarma için örtük olarak dönüştürülebilir bir türün `n` ifadesi aşağıdaki gibi tanımlanır:

- Hem `p + n` hem de `n + p` ifadeleri, `p`tarafından verilen adrese `n * sizeof(T)` eklemenin sonucu `T*` türünde bir işaretçi üretir.
- `p - n` ifade, `p`tarafından verilen adresten `n * sizeof(T)` çıkarılmasına neden olan `T*` türünde bir işaretçi üretir.

[`sizeof` işleci](sizeof.md) , bir türün boyutunu bayt cinsinden alır.

Aşağıdaki örnek bir işaretçiyle `+` işlecinin kullanımını gösterir:

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>İşaretçi çıkarması

İki işaretçi `p1` ve `T*`türünde `p2`, ifade `p1 - p2` `p1` ve `p2` tarafından verilen adresler arasındaki farkı `sizeof(T)`tarafından bölünür. Sonucun türü `long`. Diğer bir deyişle, `p1 - p2` `((long)(p1) - (long)(p2)) / sizeof(T)`olarak hesaplanır.

Aşağıdaki örnekte işaretçi çıkarma gösterilmektedir:

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>İşaretçi artışı ve azaltma

`++` artım işleci, işaretçi işleneni 1 [ekler](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) . `--` azaltma işleci, işaretçi işlenenden 1 [çıkartır](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .

İki tür işleç desteklenir: sonek (`p++` ve `p--`) ve önek (`++p` ve `--p`). `p++` ve `p--` sonucu, işlemden *önceki* `p` değeridir. `++p` ve `--p` sonucu, işlem *sonrasında* `p` değeridir.

Aşağıdaki örnek, hem sonek hem de önek artırma işleçlerinin davranışını gösterir:

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>İşaretçi karşılaştırma işleçleri

`<=`dahil olmak üzere herhangi bir işaretçi türündeki işlenenleri karşılaştırmak için `==`, `!=`, `<`, `>`, `>=` ve `void*`işleçlerini kullanabilirsiniz. Bu işleçler, iki işlenen tarafından verilen adresleri işaretsiz tamsayılar gibi karşılaştırır.

Diğer türlerin işlenenleri için bu işleçlerin davranışı hakkında daha fazla bilgi için bkz. [eşitlik işleçleri](equality-operators.md) ve [karşılaştırma işleçleri](comparison-operators.md) makaleleri.

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, işaretçinin ilgili işleçlerini en yüksek öncelikten en düşüğe başlayarak sıralar:

- Sonek artırma `x++` ve azaltma `x--` işleçleri ve `->` ve `[]` işleçleri
- Önek artırma `++x` ve azaltma `--x` işleçleri ve `&` ve `*` işleçleri
- Adli `+` ve `-` işleçleri
- Karşılaştırma `<`, `>`, `<=`ve `>=` işleçleri
- Eşitlik `==` ve `!=` işleçleri

İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantez, `()`kullanın.

Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için, [ C# işleçler](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür, işaretçi ile ilgili işleçleri `&`, `*`, `->`ve `[]`aşırı yükleyemez.

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
