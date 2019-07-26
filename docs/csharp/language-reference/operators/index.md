---
title: C#işleçler- C# başvuru
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
ms.openlocfilehash: b6a1cc3ced3205037eb5b83ac3841efbfbd1b5b9
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331223"
---
# <a name="c-operators-c-reference"></a>C#İşleçler (C# başvuru)

C#Yerleşik türler tarafından desteklenen bir dizi önceden tanımlanmış işleç sağlar. Örneğin, [Aritmetik işleçler](arithmetic-operators.md) , yerleşik sayısal türlerin işlenenleriyle aritmetik işlemler gerçekleştirir ve [Boole mantıksal işleçleri](boolean-logical-operators.md) [bool](../keywords/bool.md) işlenenleri ile mantıksal işlemler gerçekleştirir.

Kullanıcı tanımlı bir tür, bu türün işlenenleri için karşılık gelen davranışı tanımlamak üzere bazı işleçleri aşırı yükleyebilir. Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](operator-overloading.md).

Aşağıdaki bölümlerde en düşük önceliğe C# göre başlayan işleçler listelenmektedir. Her bölümün içindeki işleçler aynı öncelik düzeyini paylaşır.

## <a name="primary-operators"></a>Birincil işleçler

Bunlar en yüksek öncelik işleçleridir.

[x. y](member-access-operators.md#member-access-operator-) – üye erişimi.

[x?. y](member-access-operators.md#null-conditional-operators--and-) – null koşullu üye erişimi. Sol `null` işlenenin olarak `null`değerlendirilip değerlendirilmeyeceğini döndürür.

[x? [y]](member-access-operators.md#null-conditional-operators--and-) -null koşullu dizi öğesi veya tür Dizin Oluşturucu erişimi. Sol `null` işlenenin olarak `null`değerlendirilip değerlendirilmeyeceğini döndürür.

[f (x)](member-access-operators.md#invocation-operator-) – Yöntem çağrısı veya temsilci çağırma.

x – Array öğesi veya tür Dizin Oluşturucu erişimi. [&#91;&#93; ](member-access-operators.md#indexer-operator-)

[x + +](arithmetic-operators.md#increment-operator-) – Sonek artışı. X değerini döndürür ve ardından depolama konumunu bir daha büyük olan x değeriyle güncelleştirir (genellikle 1 tamsayı ekler).

[x--](arithmetic-operators.md#decrement-operator---) – sonek azalış. X değerini döndürür ve ardından depolama konumunu daha az olan x değeriyle güncelleştirir (genellikle 1 tamsayı çıkartır).

[New](new-operator.md) – örneklemeyi yazın.

[typeof](type-testing-and-conversion-operators.md#typeof-operator) : işleneni temsil <xref:System.Type> eden nesneyi döndürür.

[Checked](../keywords/checked.md) : tamsayı işlemleri için taşma denetimini etkinleştirilir.

[unchecked](../keywords/unchecked.md) : tamsayı işlemleri için taşma denetimini devre dışı bırakır. Bu, varsayılan derleyici davranışıdır.

[varsayılan (t)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) : T türünde varsayılan değeri üretir.

[NameOf](nameof.md) -bir değişkenin, türün veya üyenin basit (nitelenmemiş) adını sabit bir dize olarak alır.

[Delegate](delegate-operator.md) : bir temsilci örneği bildirir ve döndürür.

[sizeof](../keywords/sizeof.md) : tür işleneninin bayt cinsinden boyutunu döndürür.

[stackalloc](stackalloc.md) -yığında bellek bloğunu ayırır.

[->](pointer-related-operators.md#pointer-member-access-operator--)– işaretçi yöneltme, üye erişimiyle birleştirilir.

## <a name="unary-operators"></a>Birli İşleçler

Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.

[+ x](addition-operator.md) : x değerini döndürür.

[-x](subtraction-operator.md) – sayısal değilleme.

x – mantıksal değilleme. [ \!](boolean-logical-operators.md#logical-negation-operator-)

[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bit düzeyinde tamamlama.

[+ + x](arithmetic-operators.md#increment-operator-) – ön ek artışı. Depolama konumunu bir daha büyük olan x değeriyle güncelleştirdikten sonra x değerini döndürür (genellikle 1 tamsayı ekler).

[--x](arithmetic-operators.md#decrement-operator---) – ön ek azalış. Depolama konumu daha az olan x değeriyle güncelleştirildikten sonra x değerini döndürür (genellikle 1 tamsayı çıkartır).

[(T) x](type-testing-and-conversion-operators.md#cast-operator-) – tür atama.

[await](../keywords/await.md) – bir a `Task`bekler.

[& x](pointer-related-operators.md#address-of-operator-) – bir değişkenin adresi.

[* x](pointer-related-operators.md#pointer-indirection-operator-) – işaretçi yöneltme veya başvuru.

[true işleci](true-false-operators.md) -bir işlenenin [](../keywords/bool.md) kesinlikle doğru `true` olduğunu göstermek için bool değeri döndürür.

[false işleci](true-false-operators.md) -bir işlenenin [](../keywords/bool.md) kesinlikle yanlış `true` olduğunu göstermek için bool değeri döndürür.

## <a name="multiplicative-operators"></a>Çarpma işleçleri

Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.

[x * y](arithmetic-operators.md#multiplication-operator-) – çarpma.

[x/y](arithmetic-operators.md#division-operator-) – bölüm. İşlenenler tamsayılar ise, sonuç sıfır (örneğin, `-7 / 2 is -3`) ile kesilmiş bir tamsayıdır.

[x% y](arithmetic-operators.md#remainder-operator-) – geri kalanı. İşlenenler tamsayı ise bu, x ve y 'nin bölünen kalanı döndürür.  Ve `q = x / y` ise`r = x % y`, .`x = q * y + r`

## <a name="additive-operators"></a>Toplama işleçleri

Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.

[x + y](arithmetic-operators.md#addition-operator-) – ekleme.

[x – y](arithmetic-operators.md#subtraction-operator--) – çıkarma.

## <a name="shift-operators"></a>Kaydırma işleçleri

Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.

[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) : bitleri sola Ötele ve sağ tarafta sıfır ile doldur.

[x > > y](bitwise-and-shift-operators.md#right-shift-operator-) – bit kaydır sağ. Sol işlenen veya `int` `long`ise, sol bitler işaret biti ile doldurulur. Sol işlenen veya `uint` `ulong`ise, sol bitler sıfır ile doldurulur.

## <a name="relational-and-type-testing-operators"></a>İlişkisel ve tür testi işleçleri

Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.

[ x\< y](comparison-operators.md#less-than-operator-) – küçüktür (x, y 'den küçükse true).

[x > y](comparison-operators.md#greater-than-operator-) – büyüktür (x y 'den büyükse true).

[ x\<= y](comparison-operators.md#less-than-or-equal-operator-) – küçüktür veya eşittir.

[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – büyük veya eşittir.

[,](type-testing-and-conversion-operators.md#is-operator) – tür uyumluluğu. Değerlendirilen `true` sol işlenenin sağ işlenen tarafından belirtilen türe tür ataması olup olmadığını döndürür.

[as](type-testing-and-conversion-operators.md#as-operator) -tür dönüşümü. Sol işlenenin sağ işlenen tarafından belirtilen türe saçılması, ancak `as` bir özel durum oluşturması gereken yeri `(T)x` döndürür. `null`

## <a name="equality-operators"></a>Eşitlik İşleçleri

Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.

[x = = y](equality-operators.md#equality-operator-) – eşitlik. Varsayılan olarak, dışındaki başvuru türleri `string`için başvuru eşitlik (kimlik testi) döndürür. Ancak, türleri aşırı `==`yükleyebilir, bu nedenle amaç test kimliğini test etmek için en iyisi, üzerinde `ReferenceEquals` `object`yöntemi kullanmaktır.

[x! = y](equality-operators.md#inequality-operator-) – eşit değildir. İçin `==`bkz. açıklaması. Bir tür aşırı `==`yüklendiğinde, aşırı yüklemesi `!=`gerekir.

## <a name="logical-and-operator"></a>Mantıksal AND işleci

Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.

`x & y`– [](boolean-logical-operators.md#logical-and-operator-) `bool` işlenenler için ve işlenenleri veya [bit düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) integral türlerinin işlenenleri için mantıksal ve.

## <a name="logical-xor-operator"></a>Mantıksal XOR işleci

Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.

`x ^ y`– `bool` işlenen için [Mantıksal xor](boolean-logical-operators.md#logical-exclusive-or-operator-) veya integral türlerinin işlenenleri için [bit düzeyinde mantıksal XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) .

## <a name="logical-or-operator"></a>Mantıksal OR işleci

Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.

`x | y`– [](boolean-logical-operators.md#logical-or-operator-) `bool` işlenenler veya integral türlerinin işlenenleri için mantıksal or veya [bit düzeyinde mantıksal veya](bitwise-and-shift-operators.md#logical-or-operator-) .

## <a name="conditional-and-operator"></a>Koşullu AND işleci

Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.

[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) : mantıksal ve. , `x` Olarak `false`değerlendirilirse ,`y` değerlendirilmez.

## <a name="conditional-or-operator"></a>Koşullu OR işleci

Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.

[ &#124; x &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – mantıksal veya. , `x` Olarak `true`değerlendirilirse ,`y` değerlendirilmez.

## <a name="null-coalescing-operator"></a>Null birleşim işleci

Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.

[x?? y](null-coalescing-operator.md) :- `x` `null`değilse döndürür; Aksi takdirde, döndürür `y`.

## <a name="conditional-operator"></a>Koşullu işleç

Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.

[t? x: y](conditional-operator.md) – test `t` doğru olarak değerlendirilirse, değerlendirin ve döndürün `x`; Aksi takdirde, değerlendirin ve geri döndürün `y`.

## <a name="assignment-and-lambda-operators"></a>Atama ve lambda işleçleri

Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.

[x = y](assignment-operator.md) – atama.

[x + = y](arithmetic-operators.md#compound-assignment) – artış. Değerini değerine ekleyin `x`, sonucu içinde depolayın ve yeni değeri döndürün. `x` `y` Bir olayı [](../keywords/event.md) `y` belirtir, ardından olay işleyicisi olarak C# ekleyen uygun bir yöntem olmalıdır. `x`

[x-= y](arithmetic-operators.md#compound-assignment) – azaltma. Değerini değerinden çıkarın `x`, sonucu içinde depolayın ve yeni değeri döndürün. `x` `y` Bir `x` [olayı belirtir](../keywords/event.md) C# , birolayişleyicisiolarakkaldıranuygunbiryöntem`y` olmalıdır.

[x * = y](arithmetic-operators.md#compound-assignment) – çarpma ataması. Değerini `y` `x`değerine çarpın, sonucunu içinde depolayın ve yeni değeri döndürün. `x`

[x/= y](arithmetic-operators.md#compound-assignment) – bölüm atama. Değerini değerine göre bölün, sonucu içinde `x`depolayın ve yeni değeri döndürün. `y` `x`

[x% = y](arithmetic-operators.md#compound-assignment) – kalan atama. Değerini değerine göre bölün `x`,kalanısaklayın ve yeni değeri döndürün. `y` `x`

[x & = y](boolean-logical-operators.md#compound-assignment) ve atama. Ve değeri `y` ile `x`değerini, sonucunu içinde `x`depolayın ve yeni değeri döndürün.

[x &#124;= y](boolean-logical-operators.md#compound-assignment) – veya atama. Ya da değeri `y` ile `x`değerini, sonucunu içinde `x`depolayın ve yeni değeri döndürün.

[x ^ = y](boolean-logical-operators.md#compound-assignment) – XOR ataması. Değerini değeri ile XOR değeri `x` ,sonucunudepolarveyenideğeridöndürür.`x` `y`

[x < < = y](bitwise-and-shift-operators.md#compound-assignment) – sola kaydırma ataması. Değeri `x` konumlarına göre `y` sola kaydırın, sonucu içinde `x`depolayın ve yeni değeri döndürün.

[x > > = y](bitwise-and-shift-operators.md#compound-assignment) – sağ Shift atama. Değeri `x` konumlarına göre `y` Sağa Ötele, sonucu ' de `x`depolayın ve yeni değeri döndürün.

[=>](lambda-operator.md)– Lambda bildirimi.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [İşleçler](../../programming-guide/statements-expressions-operators/operators.md)
