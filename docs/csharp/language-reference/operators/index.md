---
title: C#Operators - C# başvurusu
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: fecfe8473a33be1a777fc5dde80c292f940e0d41
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347855"
---
# <a name="c-operators-c-reference"></a>C#işleçler (C# Başvurusu)

C#birkaç yerleşik türleri tarafından desteklenen önceden tanımlı operatörler sağlar. Örneğin, [aritmetik işleçler](arithmetic-operators.md) yerleşik sayısal türler, işlenenlerin aritmetik işlemler gerçekleştirme ve [Boolean mantıksal işleçler](boolean-logical-operators.md) mantıksal işlemleri ile [bool ](../keywords/bool.md) işlenen.

Kullanıcı tanımlı bir tür o türündeki işlenenler için karşılık gelen davranışını tanımlamak için belirli işleçleri aşırı yüklenebilir. Daha fazla bilgi için [işleci](../keywords/operator.md) anahtar sözcüğü makalesi.

Aşağıdaki bölümlerde liste C# en yüksek önceliğe düşüğe başlayarak işleçleri. Her bölüm içerisindeki işleçler aynı öncelik düzeyine paylaşın.

## <a name="primary-operators"></a>Birincil operatörler

En yüksek öncelik işleçleri şunlardır.

[x.y](member-access-operators.md#member-access-operator-) – üye erişimi.

[x? y](member-access-operators.md#null-conditional-operators--and-) – null koşullu üye erişimi. Döndürür `null` sol işlenen değerlendirilirse `null`.

[x? [y] ](member-access-operators.md#null-conditional-operators--and-) - koşullu dizi öğesi null veya dizin oluşturucu erişim yazın. Döndürür `null` sol işlenen değerlendirilirse `null`.

[f(x)](member-access-operators.md#invocation-operator-) – yöntem çağrısı veya temsilci çağırma.

[bir&#91;x&#93; ](member-access-operators.md#indexer-operator-) – dizi öğesi veya dizin oluşturucu erişim yazın.

[x ++](arithmetic-operators.md#increment-operator-) – sonek artırma. X değerini döndürür ve ardından depolama konumu büyük bir x değeri ile güncelleştirir (genellikle 1 tamsayı ekler).

[x--](arithmetic-operators.md#decrement-operator---) – son ek azaltma. X değerini döndürür ve ardından depolama konumu bir daha az x değeri ile güncelleştirir (genellikle 1 tamsayı çıkarır).

[Yeni](../keywords/new-operator.md) – oluşturmada yazın.

[typeof](type-testing-and-conversion-operators.md#typeof-operator) – döndürür <xref:System.Type> işlenen temsil eden nesne.

[işaretli](../keywords/checked.md) – taşma denetimi için tamsayı işlemleri sağlar.

[denetlenmeyen](../keywords/unchecked.md) – taşma tamsayı işlemlerinde denetimini devre dışı bırakır. Varsayılan derleyici davranışı budur.

[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – t türü varsayılan değerini üretir

[nameof](../keywords/nameof.md) -değişken, tür veya üyenin bir sabit dize olarak basit (nitelenmemiş) adını alır.

[Temsilci](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – bildirir ve temsilci örneği döndürür.

[sizeof](../keywords/sizeof.md) -türü işlenen bayt cinsinden boyutunu döndürür.

[stackalloc](stackalloc.md) -bir yığında bellek bloğu ayırır.

[->](pointer-related-operators.md#pointer-member-access-operator--) – İşaretçi yöneltmesi birleştirilmiş üye erişimi ile.

## <a name="unary-operators"></a>Birli işleçler

Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.

[+ x](addition-operator.md) – x değerini döndürür.

[-x](subtraction-operator.md) – sayısal olumsuzlama.

[\!x](boolean-logical-operators.md#logical-negation-operator-) – mantıksal olumsuzlama.

[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bit düzeyinde tamamlayıcı.

[++ x](arithmetic-operators.md#increment-operator-) – önek artırma. Depolama konumu bir x değeriyle güncelleştirdikten sonra x değerini büyük döndürür (genellikle 1 tamsayı ekler).

[--x](arithmetic-operators.md#decrement-operator---) – önek azaltma. Depolama konumu daha az bir x değeriyle güncelleştirdikten sonra x değeri döndürür (genelde tam sayı 1 çıkarır).

[(T) x](type-testing-and-conversion-operators.md#cast-operator-) – atama yazın.

[await](../keywords/await.md) – bekler bir `Task`.

[& x](pointer-related-operators.md#address-of-operator-) : değişkenin adresini.

[* x](pointer-related-operators.md#pointer-indirection-operator-) – işaretçi yöneltmesi veya başvuru.

[true işleci](true-false-operators.md) -döndürür [bool](../keywords/bool.md) değer `true` işleneni kesinlikle doğru olduğunu belirtmek için.

[false işleci](true-false-operators.md) -döndürür [bool](../keywords/bool.md) değer `true` işleneni kesinlikle false olduğunu belirtmek için.

## <a name="multiplicative-operators"></a>Çarpma işleçleri

Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.

[x * y](arithmetic-operators.md#multiplication-operator-) – çarpma.

[x / y](arithmetic-operators.md#division-operator-) – bölme. İşlenenler tamsayılar, sonuç sıfıra yakınsayarak kesilmiş bir tamsayıdır (örneğin, `-7 / 2 is -3`).

[% y x](arithmetic-operators.md#remainder-operator-) – kalan. İşlenen tamsayılar olursa bu y bölme x geri kalanı döndürür.  Varsa `q = x / y` ve `r = x % y`, ardından `x = q * y + r`.

## <a name="additive-operators"></a>Toplama işleçleri

Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.

[x + y](arithmetic-operators.md#addition-operator-) – ekleme.

[x-y](arithmetic-operators.md#subtraction-operator--) – çıkarma.

## <a name="shift-operators"></a>Kaydırma işleçleri

Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.

[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – bitlerini sola kaydırma ve sağ taraftaki sıfır ile doldurun.

[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – sağ shift bitleri. Sol işlenen ise `int` veya `long`, sonra da sol bit imza biti ile doldurulur. Sol işlenen ise `uint` veya `ulong`, sonra da sol bitler sıfır ile doldurulur.

## <a name="relational-and-type-testing-operators"></a>İlişkisel ve tür testi işleçleri

Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.

[x \< y](comparison-operators.md#less-than-operator-) – (x, y değerinden ise true) küçüktür.

[x > y](comparison-operators.md#greater-than-operator-) – büyük (x, y büyükse true).

[x \<y =](comparison-operators.md#less-than-or-equal-operator-) – küçük veya eşittir.

[x > y =](comparison-operators.md#greater-than-or-equal-operator-) – büyüktür veya eşittir.

[olan](type-testing-and-conversion-operators.md#is-operator) – uyumluluk yazın. Döndürür `true` değerlendirilen sol işlenen sağ işlenen tarafından belirtilen türün başvurusuna yayınlanabilir durumunda.

[olarak](type-testing-and-conversion-operators.md#as-operator) – dönüştürmesi yazın. Sol işlenen sağ işlenen tarafından belirtilen türe dönüştürme döndürür ancak `as` döndürür `null` burada `(T)x` bir özel durum oluşturması.

## <a name="equality-operators"></a>Eşitlik İşleçleri

Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.

[x == y](equality-operators.md#equality-operator-) – eşitlik. Varsayılan olarak, başvuru için türleri dışındaki `string`, bu başvuru eşitliği (kimlik test) döndürür. Ancak, türleri aşırı yüklenebilir `==`, amacınız kimliğini test etmek için ise kullanmak en iyisidir `ReferenceEquals` metodunda `object`.

[x! = y](equality-operators.md#inequality-operator-) – eşit değil. Açıklama için bkz. `==`. Bir tür aşırı `==`, aşırı gerekir sonra `!=`.

## <a name="logical-and-operator"></a>Mantıksal AND işleci

Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.

`x & y` – [mantıksal AND](boolean-logical-operators.md#logical-and-operator-) için `bool` işlenenler veya [mantıksal bit düzeyinde AND](bitwise-and-shift-operators.md#logical-and-operator-) işleneni de integral türleri için.

## <a name="logical-xor-operator"></a>Mantıksal XOR işleci

Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.

`x ^ y` – [mantıksal XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) için `bool` işlenenler veya [mantıksal bit düzeyinde XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) işleneni de integral türleri için.

## <a name="logical-or-operator"></a>Mantıksal OR işleci

Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.

`x | y` – [mantıksal OR](boolean-logical-operators.md#logical-or-operator-) için `bool` işlenenler veya [mantıksal bit düzeyinde OR](bitwise-and-shift-operators.md#logical-or-operator-) işleneni de integral türleri için.

## <a name="conditional-and-operator"></a>Koşullu AND işleci

Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.

[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) – mantıksal and Varsa `x` değerlendiren `false`, ardından `y` değerlendirilmez.

## <a name="conditional-or-operator"></a>Koşullu OR işleci

Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.

[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – mantıksal OR. Varsa `x` değerlendiren `true`, ardından `y` değerlendirilmez.

## <a name="null-coalescing-operator"></a>Null birleşim işleci

Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.

[x?? y](null-coalescing-operator.md) – döndürür `x` olmayan ise`null`; Aksi halde döndürür `y`.

## <a name="conditional-operator"></a>Koşullu işleç

Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.

[t? x: y](conditional-operator.md) – test `t` true, ardından değerlendirilip döndürülecek değerlendirir `x`; Aksi takdirde, değerlendirilip döndürülecek `y`.

## <a name="assignment-and-lambda-operators"></a>Atama ve lambda işleçleri

Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.

[x = y](assignment-operator.md) – atama.

[x += y](arithmetic-operators.md#compound-assignment) – artırma. Değerini ekleme `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer. Varsa `x` atayan bir [olay](../keywords/event.md), ardından `y` uygun bir yöntem olmalı, C# bir olay işleyicisi ekler.

[x-= y](arithmetic-operators.md#compound-assignment) – azaltma. Değerini çıkarma `y` değerinden `x`, sonuçta depolamak `x`ve yeni bir değer. Varsa `x` atayan bir [olay](../keywords/event.md), ardından `y` uygun bir yöntem olmalı, C# bir olay işleyicisi kaldırır.

[x * y =](arithmetic-operators.md#compound-assignment) – çarpma atama. Çarp değeri `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer.

[x / y =](arithmetic-operators.md#compound-assignment) – bölme ataması. Değerini ayırmak `x` değeriyle `y`, sonuçta depolamak `x`ve yeni bir değer.

[%x y =](arithmetic-operators.md#compound-assignment) – kalanını atama. Değerini ayırmak `x` değeriyle `y`, kalanı depolamak `x`ve yeni bir değer.

[x & y =](boolean-logical-operators.md#compound-assignment) – ve atama. DEĞERİ `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.

[x &#124;y =](boolean-logical-operators.md#compound-assignment) – OR ataması. YA da değerini `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.

[x ^ y =](boolean-logical-operators.md#compound-assignment) – XOR atama. XOR değeri, `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.

[x << y =](bitwise-and-shift-operators.md#compound-assignment) – sola kaydırma ataması. Değerini kaydırma `x` sol tarafından `y` yerde depolamak sonucunda `x`ve yeni bir değer.

[x >> y =](bitwise-and-shift-operators.md#compound-assignment) – sağa kaydırma ataması. Değerini kaydırma `x` sağa `y` yerde depolamak sonucunda `x`ve yeni bir değer.

[=>](lambda-operator.md) – lambda bildirimi.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [İşleçler](../../programming-guide/statements-expressions-operators/operators.md)
- [Fazla yüklenebilir işleçler](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
