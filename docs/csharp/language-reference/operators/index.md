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
ms.openlocfilehash: bc5e2c88314c2f590aeddcfd37bd04c3a7400804
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796483"
---
# <a name="c-operators-c-reference"></a><span data-ttu-id="20e0a-102">C#İşleçler (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="20e0a-102">C# operators (C# reference)</span></span>

<span data-ttu-id="20e0a-103">C#Yerleşik türler tarafından desteklenen bir dizi önceden tanımlanmış işleç sağlar.</span><span class="sxs-lookup"><span data-stu-id="20e0a-103">C# provides a number of predefined operators supported by the built-in types.</span></span> <span data-ttu-id="20e0a-104">Örneğin, [Aritmetik işleçler](arithmetic-operators.md) , yerleşik sayısal türlerin işlenenleriyle aritmetik işlemler gerçekleştirir ve [Boole mantıksal işleçleri](boolean-logical-operators.md) [bool](../keywords/bool.md) işlenenleri ile mantıksal işlemler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-104">For example, [arithmetic operators](arithmetic-operators.md) perform arithmetic operations with operands of built-in numeric types and [Boolean logical operators](boolean-logical-operators.md) perform logical operations with the [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="20e0a-105">Kullanıcı tanımlı bir tür, bu türün işlenenleri için karşılık gelen davranışı tanımlamak üzere bazı işleçleri aşırı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-105">A user-defined type can overload certain operators to define the corresponding behavior for the operands of that type.</span></span> <span data-ttu-id="20e0a-106">Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="20e0a-106">For more information, see [Operator overloading](operator-overloading.md).</span></span>

<span data-ttu-id="20e0a-107">Aşağıdaki bölümlerde en düşük önceliğe C# göre başlayan işleçler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-107">The following sections list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="20e0a-108">Her bölümün içindeki işleçler aynı öncelik düzeyini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="20e0a-108">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="20e0a-109">Birincil işleçler</span><span class="sxs-lookup"><span data-stu-id="20e0a-109">Primary operators</span></span>

<span data-ttu-id="20e0a-110">Bunlar en yüksek öncelik işleçleridir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-110">These are the highest precedence operators.</span></span>

<span data-ttu-id="20e0a-111">[x. y](member-access-operators.md#member-access-operator-) – üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="20e0a-111">[x.y](member-access-operators.md#member-access-operator-) – member access.</span></span>

<span data-ttu-id="20e0a-112">[x?. y](member-access-operators.md#null-conditional-operators--and-) – null koşullu üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="20e0a-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null conditional member access.</span></span> <span data-ttu-id="20e0a-113">Sol `null` işlenenin olarak `null`değerlendirilip değerlendirilmeyeceğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-113">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="20e0a-114">[x? [y]](member-access-operators.md#null-conditional-operators--and-) -null koşullu dizi öğesi veya tür Dizin Oluşturucu erişimi.</span><span class="sxs-lookup"><span data-stu-id="20e0a-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null conditional array element or type indexer access.</span></span> <span data-ttu-id="20e0a-115">Sol `null` işlenenin olarak `null`değerlendirilip değerlendirilmeyeceğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-115">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="20e0a-116">[f (x)](member-access-operators.md#invocation-operator-) – Yöntem çağrısı veya temsilci çağırma.</span><span class="sxs-lookup"><span data-stu-id="20e0a-116">[f(x)](member-access-operators.md#invocation-operator-) – method call or delegate invocation.</span></span>

<span data-ttu-id="20e0a-117">x – Array öğesi veya tür Dizin Oluşturucu erişimi. [&#91;&#93; ](member-access-operators.md#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="20e0a-117">[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – array element or type indexer access.</span></span>

<span data-ttu-id="20e0a-118">[x + +](arithmetic-operators.md#increment-operator-) – Sonek artışı.</span><span class="sxs-lookup"><span data-stu-id="20e0a-118">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="20e0a-119">X değerini döndürür ve ardından depolama konumunu bir daha büyük olan x değeriyle güncelleştirir (genellikle 1 tamsayı ekler).</span><span class="sxs-lookup"><span data-stu-id="20e0a-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="20e0a-120">[x--](arithmetic-operators.md#decrement-operator---) – sonek azalış.</span><span class="sxs-lookup"><span data-stu-id="20e0a-120">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="20e0a-121">X değerini döndürür ve ardından depolama konumunu daha az olan x değeriyle güncelleştirir (genellikle 1 tamsayı çıkartır).</span><span class="sxs-lookup"><span data-stu-id="20e0a-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="20e0a-122">[New](new-operator.md) – örneklemeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="20e0a-122">[new](new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="20e0a-123">[typeof](type-testing-and-conversion-operators.md#typeof-operator) : işleneni temsil <xref:System.Type> eden nesneyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-123">[typeof](type-testing-and-conversion-operators.md#typeof-operator) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="20e0a-124">[Checked](../keywords/checked.md) : tamsayı işlemleri için taşma denetimini etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-124">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="20e0a-125">[unchecked](../keywords/unchecked.md) : tamsayı işlemleri için taşma denetimini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="20e0a-125">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="20e0a-126">Bu, varsayılan derleyici davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="20e0a-126">This is the default compiler behavior.</span></span>

<span data-ttu-id="20e0a-127">[varsayılan (t)](default.md) : T türünde varsayılan değeri üretir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-127">[default(T)](default.md) – produces the default value of type T.</span></span>

<span data-ttu-id="20e0a-128">[NameOf](nameof.md) -bir değişkenin, türün veya üyenin basit (nitelenmemiş) adını sabit bir dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="20e0a-128">[nameof](nameof.md) - obtains the simple (unqualified) name of a variable, type, or member as a constant string.</span></span>

<span data-ttu-id="20e0a-129">[Delegate](delegate-operator.md) : bir temsilci örneği bildirir ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-129">[delegate](delegate-operator.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="20e0a-130">[sizeof](sizeof.md) : tür işleneninin bayt cinsinden boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-130">[sizeof](sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="20e0a-131">[stackalloc](stackalloc.md) -yığında bellek bloğunu ayırır.</span><span class="sxs-lookup"><span data-stu-id="20e0a-131">[stackalloc](stackalloc.md) - allocates a block of memory on the stack.</span></span>

<span data-ttu-id="20e0a-132">[->](pointer-related-operators.md#pointer-member-access-operator--)– işaretçi yöneltme, üye erişimiyle birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – pointer indirection combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="20e0a-133">Birli İşleçler</span><span class="sxs-lookup"><span data-stu-id="20e0a-133">Unary operators</span></span>

<span data-ttu-id="20e0a-134">Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-134">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-135">[+ x](addition-operator.md) : x değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-135">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="20e0a-136">[-x](subtraction-operator.md) – sayısal değilleme.</span><span class="sxs-lookup"><span data-stu-id="20e0a-136">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="20e0a-137">x – mantıksal değilleme. [ \!](boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="20e0a-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="20e0a-138">[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bit düzeyinde tamamlama.</span><span class="sxs-lookup"><span data-stu-id="20e0a-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="20e0a-139">[+ + x](arithmetic-operators.md#increment-operator-) – ön ek artışı.</span><span class="sxs-lookup"><span data-stu-id="20e0a-139">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="20e0a-140">Depolama konumunu bir daha büyük olan x değeriyle güncelleştirdikten sonra x değerini döndürür (genellikle 1 tamsayı ekler).</span><span class="sxs-lookup"><span data-stu-id="20e0a-140">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="20e0a-141">[--x](arithmetic-operators.md#decrement-operator---) – ön ek azalış.</span><span class="sxs-lookup"><span data-stu-id="20e0a-141">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="20e0a-142">Depolama konumu daha az olan x değeriyle güncelleştirildikten sonra x değerini döndürür (genellikle 1 tamsayı çıkartır).</span><span class="sxs-lookup"><span data-stu-id="20e0a-142">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="20e0a-143">[(T) x](type-testing-and-conversion-operators.md#cast-operator-) – tür atama.</span><span class="sxs-lookup"><span data-stu-id="20e0a-143">[(T)x](type-testing-and-conversion-operators.md#cast-operator-) – type casting.</span></span>

<span data-ttu-id="20e0a-144">[await](../keywords/await.md) – bir a `Task`bekler.</span><span class="sxs-lookup"><span data-stu-id="20e0a-144">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="20e0a-145">[& x](pointer-related-operators.md#address-of-operator-) – bir değişkenin adresi.</span><span class="sxs-lookup"><span data-stu-id="20e0a-145">[&x](pointer-related-operators.md#address-of-operator-) – address of a variable.</span></span>

<span data-ttu-id="20e0a-146">[\* x](pointer-related-operators.md#pointer-indirection-operator-) – işaretçi yöneltme veya başvuru.</span><span class="sxs-lookup"><span data-stu-id="20e0a-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – pointer indirection, or dereference.</span></span>

<span data-ttu-id="20e0a-147">[true işleci](true-false-operators.md) -bir işlenenin [](../keywords/bool.md) kesinlikle doğru `true` olduğunu göstermek için bool değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-147">[true operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="20e0a-148">[false işleci](true-false-operators.md) -bir işlenenin [](../keywords/bool.md) kesinlikle yanlış `true` olduğunu göstermek için bool değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-148">[false operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="20e0a-149">Çarpma işleçleri</span><span class="sxs-lookup"><span data-stu-id="20e0a-149">Multiplicative operators</span></span>

<span data-ttu-id="20e0a-150">Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-150">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – çarpma.</span><span class="sxs-lookup"><span data-stu-id="20e0a-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="20e0a-152">[x/y](arithmetic-operators.md#division-operator-) – bölüm.</span><span class="sxs-lookup"><span data-stu-id="20e0a-152">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="20e0a-153">İşlenenler tamsayılar ise, sonuç sıfır (örneğin, `-7 / 2 is -3`) ile kesilmiş bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="20e0a-153">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="20e0a-154">[x% y](arithmetic-operators.md#remainder-operator-) – geri kalanı.</span><span class="sxs-lookup"><span data-stu-id="20e0a-154">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="20e0a-155">İşlenenler tamsayı ise bu, x ve y 'nin bölünen kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-155">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="20e0a-156">Ve `q = x / y` ise`r = x % y`, .`x = q * y + r`</span><span class="sxs-lookup"><span data-stu-id="20e0a-156">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="20e0a-157">Toplama işleçleri</span><span class="sxs-lookup"><span data-stu-id="20e0a-157">Additive operators</span></span>

<span data-ttu-id="20e0a-158">Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-158">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-159">[x + y](arithmetic-operators.md#addition-operator-) – ekleme.</span><span class="sxs-lookup"><span data-stu-id="20e0a-159">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="20e0a-160">[x – y](arithmetic-operators.md#subtraction-operator--) – çıkarma.</span><span class="sxs-lookup"><span data-stu-id="20e0a-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="20e0a-161">Kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="20e0a-161">Shift operators</span></span>

<span data-ttu-id="20e0a-162">Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-162">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-163">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) : bitleri sola Ötele ve sağ tarafta sıfır ile doldur.</span><span class="sxs-lookup"><span data-stu-id="20e0a-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="20e0a-164">[x > > y](bitwise-and-shift-operators.md#right-shift-operator-) – bit kaydır sağ.</span><span class="sxs-lookup"><span data-stu-id="20e0a-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="20e0a-165">Sol işlenen veya `int` `long`ise, sol bitler işaret biti ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="20e0a-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="20e0a-166">Sol işlenen veya `uint` `ulong`ise, sol bitler sıfır ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="20e0a-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="20e0a-167">İlişkisel ve tür testi işleçleri</span><span class="sxs-lookup"><span data-stu-id="20e0a-167">Relational and type-testing operators</span></span>

<span data-ttu-id="20e0a-168">Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-169">[ x\< y](comparison-operators.md#less-than-operator-) – küçüktür (x, y 'den küçükse true).</span><span class="sxs-lookup"><span data-stu-id="20e0a-169">[x \< y](comparison-operators.md#less-than-operator-) – less than (true if x is less than y).</span></span>

<span data-ttu-id="20e0a-170">[x > y](comparison-operators.md#greater-than-operator-) – büyüktür (x y 'den büyükse true).</span><span class="sxs-lookup"><span data-stu-id="20e0a-170">[x > y](comparison-operators.md#greater-than-operator-) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="20e0a-171">[ x\<= y](comparison-operators.md#less-than-or-equal-operator-) – küçüktür veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – less than or equal to.</span></span>

<span data-ttu-id="20e0a-172">[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – büyük veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – greater than or equal to.</span></span>

<span data-ttu-id="20e0a-173">[,](type-testing-and-conversion-operators.md#is-operator) – tür uyumluluğu.</span><span class="sxs-lookup"><span data-stu-id="20e0a-173">[is](type-testing-and-conversion-operators.md#is-operator) – type compatibility.</span></span> <span data-ttu-id="20e0a-174">Değerlendirilen `true` sol işlenenin sağ işlenen tarafından belirtilen türe tür ataması olup olmadığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-174">Returns `true` if the evaluated left operand can be cast to the type specified by the right operand.</span></span>

<span data-ttu-id="20e0a-175">[as](type-testing-and-conversion-operators.md#as-operator) -tür dönüşümü.</span><span class="sxs-lookup"><span data-stu-id="20e0a-175">[as](type-testing-and-conversion-operators.md#as-operator) – type conversion.</span></span> <span data-ttu-id="20e0a-176">Sol işlenenin sağ işlenen tarafından belirtilen türe saçılması, ancak `as` bir özel durum oluşturması gereken yeri `(T)x` döndürür. `null`</span><span class="sxs-lookup"><span data-stu-id="20e0a-176">Returns the left operand cast to the type specified by the right operand, but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="20e0a-177">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="20e0a-177">Equality operators</span></span>

<span data-ttu-id="20e0a-178">Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-178">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-179">[x = = y](equality-operators.md#equality-operator-) – eşitlik.</span><span class="sxs-lookup"><span data-stu-id="20e0a-179">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="20e0a-180">Varsayılan olarak, dışındaki başvuru türleri `string`için başvuru eşitlik (kimlik testi) döndürür.</span><span class="sxs-lookup"><span data-stu-id="20e0a-180">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="20e0a-181">Ancak, türleri aşırı `==`yükleyebilir, bu nedenle amaç test kimliğini test etmek için en iyisi, üzerinde `ReferenceEquals` `object`yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="20e0a-181">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="20e0a-182">[x! = y](equality-operators.md#inequality-operator-) – eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-182">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="20e0a-183">İçin `==`bkz. açıklaması.</span><span class="sxs-lookup"><span data-stu-id="20e0a-183">See comment for `==`.</span></span> <span data-ttu-id="20e0a-184">Bir tür aşırı `==`yüklendiğinde, aşırı yüklemesi `!=`gerekir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-184">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="20e0a-185">Mantıksal AND işleci</span><span class="sxs-lookup"><span data-stu-id="20e0a-185">Logical AND operator</span></span>

<span data-ttu-id="20e0a-186">Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-187">`x & y`– [](boolean-logical-operators.md#logical-and-operator-) `bool` işlenenler için ve işlenenleri veya [bit düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) integral türlerinin işlenenleri için mantıksal ve.</span><span class="sxs-lookup"><span data-stu-id="20e0a-187">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="20e0a-188">Mantıksal XOR işleci</span><span class="sxs-lookup"><span data-stu-id="20e0a-188">Logical XOR operator</span></span>

<span data-ttu-id="20e0a-189">Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-190">`x ^ y`– `bool` işlenen için [Mantıksal xor](boolean-logical-operators.md#logical-exclusive-or-operator-) veya integral türlerinin işlenenleri için [bit düzeyinde mantıksal XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="20e0a-190">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="20e0a-191">Mantıksal OR işleci</span><span class="sxs-lookup"><span data-stu-id="20e0a-191">Logical OR operator</span></span>

<span data-ttu-id="20e0a-192">Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-193">`x | y`– [](boolean-logical-operators.md#logical-or-operator-) `bool` işlenenler veya integral türlerinin işlenenleri için mantıksal or veya [bit düzeyinde mantıksal veya](bitwise-and-shift-operators.md#logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="20e0a-193">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="20e0a-194">Koşullu AND işleci</span><span class="sxs-lookup"><span data-stu-id="20e0a-194">Conditional AND operator</span></span>

<span data-ttu-id="20e0a-195">Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-195">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-196">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) : mantıksal ve.</span><span class="sxs-lookup"><span data-stu-id="20e0a-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="20e0a-197">, `x` Olarak `false`değerlendirilirse ,`y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="20e0a-197">If `x` evaluates to `false`, then `y` is not evaluated.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="20e0a-198">Koşullu OR işleci</span><span class="sxs-lookup"><span data-stu-id="20e0a-198">Conditional OR operator</span></span>

<span data-ttu-id="20e0a-199">Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-199">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-200">[ &#124; x &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – mantıksal veya.</span><span class="sxs-lookup"><span data-stu-id="20e0a-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="20e0a-201">, `x` Olarak `true`değerlendirilirse ,`y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="20e0a-201">If `x` evaluates to `true`, then `y` is not evaluated.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="20e0a-202">Null birleşim işleci</span><span class="sxs-lookup"><span data-stu-id="20e0a-202">Null-coalescing operator</span></span>

<span data-ttu-id="20e0a-203">Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-204">[x?? y](null-coalescing-operator.md) :- `x` `null`değilse döndürür; Aksi takdirde, döndürür `y`.</span><span class="sxs-lookup"><span data-stu-id="20e0a-204">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="20e0a-205">Koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="20e0a-205">Conditional operator</span></span>

<span data-ttu-id="20e0a-206">Bu operatör, sonraki bölümden daha yüksek önceliğe ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-206">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-207">[t? x: y](conditional-operator.md) – test `t` doğru olarak değerlendirilirse, değerlendirin ve döndürün `x`; Aksi takdirde, değerlendirin ve geri döndürün `y`.</span><span class="sxs-lookup"><span data-stu-id="20e0a-207">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="20e0a-208">Atama ve lambda işleçleri</span><span class="sxs-lookup"><span data-stu-id="20e0a-208">Assignment and lambda operators</span></span>

<span data-ttu-id="20e0a-209">Bu işleçler, sonraki bölümden daha önceliklidir ve önceki bölümden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="20e0a-209">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="20e0a-210">[x = y](assignment-operator.md) – atama.</span><span class="sxs-lookup"><span data-stu-id="20e0a-210">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="20e0a-211">[x + = y](arithmetic-operators.md#compound-assignment) – artış.</span><span class="sxs-lookup"><span data-stu-id="20e0a-211">[x += y](arithmetic-operators.md#compound-assignment) – increment.</span></span> <span data-ttu-id="20e0a-212">Değerini değerine ekleyin `x`, sonucu içinde depolayın ve yeni değeri döndürün. `x` `y`</span><span class="sxs-lookup"><span data-stu-id="20e0a-212">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="20e0a-213">Bir olayı [](../keywords/event.md) `y` belirtir, ardından olay işleyicisi olarak C# ekleyen uygun bir yöntem olmalıdır. `x`</span><span class="sxs-lookup"><span data-stu-id="20e0a-213">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# adds as an event handler.</span></span>

<span data-ttu-id="20e0a-214">[x-= y](arithmetic-operators.md#compound-assignment) – azaltma.</span><span class="sxs-lookup"><span data-stu-id="20e0a-214">[x -= y](arithmetic-operators.md#compound-assignment) – decrement.</span></span> <span data-ttu-id="20e0a-215">Değerini değerinden çıkarın `x`, sonucu içinde depolayın ve yeni değeri döndürün. `x` `y`</span><span class="sxs-lookup"><span data-stu-id="20e0a-215">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="20e0a-216">Bir `x` [olayı belirtir](../keywords/event.md) C# , birolayişleyicisiolarakkaldıranuygunbiryöntem`y` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20e0a-216">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# removes as an event handler.</span></span>

<span data-ttu-id="20e0a-217">[x \* = y](arithmetic-operators.md#compound-assignment) – çarpma ataması.</span><span class="sxs-lookup"><span data-stu-id="20e0a-217">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="20e0a-218">Değerini `y` `x`değerine çarpın, sonucunu içinde depolayın ve yeni değeri döndürün. `x`</span><span class="sxs-lookup"><span data-stu-id="20e0a-218">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="20e0a-219">[x/= y](arithmetic-operators.md#compound-assignment) – bölüm atama.</span><span class="sxs-lookup"><span data-stu-id="20e0a-219">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="20e0a-220">Değerini değerine göre bölün, sonucu içinde `x`depolayın ve yeni değeri döndürün. `y` `x`</span><span class="sxs-lookup"><span data-stu-id="20e0a-220">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="20e0a-221">[x% = y](arithmetic-operators.md#compound-assignment) – kalan atama.</span><span class="sxs-lookup"><span data-stu-id="20e0a-221">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="20e0a-222">Değerini değerine göre bölün `x`,kalanısaklayın ve yeni değeri döndürün. `y` `x`</span><span class="sxs-lookup"><span data-stu-id="20e0a-222">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="20e0a-223">[x & = y](boolean-logical-operators.md#compound-assignment) ve atama.</span><span class="sxs-lookup"><span data-stu-id="20e0a-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="20e0a-224">Ve değeri `y` ile `x`değerini, sonucunu içinde `x`depolayın ve yeni değeri döndürün.</span><span class="sxs-lookup"><span data-stu-id="20e0a-224">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="20e0a-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – veya atama.</span><span class="sxs-lookup"><span data-stu-id="20e0a-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="20e0a-226">Ya da değeri `y` ile `x`değerini, sonucunu içinde `x`depolayın ve yeni değeri döndürün.</span><span class="sxs-lookup"><span data-stu-id="20e0a-226">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="20e0a-227">[x ^ = y](boolean-logical-operators.md#compound-assignment) – XOR ataması.</span><span class="sxs-lookup"><span data-stu-id="20e0a-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="20e0a-228">Değerini değeri ile XOR değeri `x` ,sonucunudepolarveyenideğeridöndürür.`x` `y`</span><span class="sxs-lookup"><span data-stu-id="20e0a-228">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="20e0a-229">[x < < = y](bitwise-and-shift-operators.md#compound-assignment) – sola kaydırma ataması.</span><span class="sxs-lookup"><span data-stu-id="20e0a-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="20e0a-230">Değeri `x` konumlarına göre `y` sola kaydırın, sonucu içinde `x`depolayın ve yeni değeri döndürün.</span><span class="sxs-lookup"><span data-stu-id="20e0a-230">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="20e0a-231">[x > > = y](bitwise-and-shift-operators.md#compound-assignment) – sağ Shift atama.</span><span class="sxs-lookup"><span data-stu-id="20e0a-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="20e0a-232">Değeri `x` konumlarına göre `y` Sağa Ötele, sonucu ' de `x`depolayın ve yeni değeri döndürün.</span><span class="sxs-lookup"><span data-stu-id="20e0a-232">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="20e0a-233">[=>](lambda-operator.md)– Lambda bildirimi.</span><span class="sxs-lookup"><span data-stu-id="20e0a-233">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="20e0a-234">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20e0a-234">See also</span></span>

- [<span data-ttu-id="20e0a-235">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="20e0a-235">C# reference</span></span>](../index.md)
- [<span data-ttu-id="20e0a-236">İşleçler</span><span class="sxs-lookup"><span data-stu-id="20e0a-236">Operators</span></span>](../../programming-guide/statements-expressions-operators/operators.md)
