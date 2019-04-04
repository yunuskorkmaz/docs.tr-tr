---
title: C#işleçleri
ms.date: 04/04/2018
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
ms.openlocfilehash: 7666918cbff7a395a93a274629fe574ff20e170c
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545695"
---
# <a name="c-operators"></a><span data-ttu-id="2424e-102">C#işleçleri</span><span class="sxs-lookup"><span data-stu-id="2424e-102">C# operators</span></span>

<span data-ttu-id="2424e-103">C# (matematik, dizin oluşturma, işlev çağrısı, vb.) bir ifadede gerçekleştirilecek işlemleri belirten simgelerdir birçok işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2424e-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="2424e-104">Yapabilecekleriniz [aşırı](../../programming-guide/statements-expressions-operators/overloadable-operators.md) işleçlerinin çoğu kullanıcı tanımlı bir türe başvurulduğunda anlamının değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2424e-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="2424e-105">Tamsayı türlerinde işlemler (gibi `==`, `!=`, `<`, `>`, `&`, `|`) genellikle numaralandırma üzerinde izin verilir (`enum`) türleri.</span><span class="sxs-lookup"><span data-stu-id="2424e-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="2424e-106">Aşağıdaki bölümlerde, en yüksek önceliğe düşüğe başlayarak C# işleçleri listeler.</span><span class="sxs-lookup"><span data-stu-id="2424e-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="2424e-107">Her bölüm içerisindeki işleçler aynı öncelik düzeyine paylaşın.</span><span class="sxs-lookup"><span data-stu-id="2424e-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="2424e-108">Birincil operatörler</span><span class="sxs-lookup"><span data-stu-id="2424e-108">Primary operators</span></span>

<span data-ttu-id="2424e-109">En yüksek öncelik işleçleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="2424e-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="2424e-110">[x.y](member-access-operator.md) – üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="2424e-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="2424e-111">[x? y](null-conditional-operators.md) – null koşullu üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="2424e-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="2424e-112">Döndürür `null` sol işlenen değerlendirilirse `null`.</span><span class="sxs-lookup"><span data-stu-id="2424e-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="2424e-113">[x? [y] ](null-conditional-operators.md) -null koşullu dizin erişim.</span><span class="sxs-lookup"><span data-stu-id="2424e-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="2424e-114">Döndürür `null` sol işlenen değerlendirilirse `null`.</span><span class="sxs-lookup"><span data-stu-id="2424e-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="2424e-115">[f(x)](invocation-operator.md) – işlev çağırma.</span><span class="sxs-lookup"><span data-stu-id="2424e-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="2424e-116">[bir&#91;x&#93; ](index-operator.md) – toplama nesnesi dizin oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2424e-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="2424e-117">[x ++](arithmetic-operators.md#increment-operator-) – sonek artırma.</span><span class="sxs-lookup"><span data-stu-id="2424e-117">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="2424e-118">X değerini döndürür ve ardından depolama konumu büyük bir x değeri ile güncelleştirir (genellikle 1 tamsayı ekler).</span><span class="sxs-lookup"><span data-stu-id="2424e-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="2424e-119">[x--](arithmetic-operators.md#decrement-operator---) – son ek azaltma.</span><span class="sxs-lookup"><span data-stu-id="2424e-119">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="2424e-120">X değerini döndürür ve ardından depolama konumu bir daha az x değeri ile güncelleştirir (genellikle 1 tamsayı çıkarır).</span><span class="sxs-lookup"><span data-stu-id="2424e-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="2424e-121">[Yeni](../keywords/new-operator.md) – oluşturmada yazın.</span><span class="sxs-lookup"><span data-stu-id="2424e-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="2424e-122">[typeof](../keywords/typeof.md) – döndürür <xref:System.Type> işlenen temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="2424e-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="2424e-123">[işaretli](../keywords/checked.md) – taşma denetimi için tamsayı işlemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2424e-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="2424e-124">[denetlenmeyen](../keywords/unchecked.md) – taşma tamsayı işlemlerinde denetimini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="2424e-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="2424e-125">Varsayılan derleyici davranışı budur.</span><span class="sxs-lookup"><span data-stu-id="2424e-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="2424e-126">[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – t türü varsayılan değerini üretir</span><span class="sxs-lookup"><span data-stu-id="2424e-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="2424e-127">[Temsilci](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – bildirir ve temsilci örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="2424e-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="2424e-128">[sizeof](../keywords/sizeof.md) -türü işlenen bayt cinsinden boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2424e-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="2424e-129">[->](dereference-operator.md) – Birleştirilmiş üye erişimi ile işaretçiye başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="2424e-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="2424e-130">Birli işleçler</span><span class="sxs-lookup"><span data-stu-id="2424e-130">Unary operators</span></span>

<span data-ttu-id="2424e-131">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="2424e-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-132">[+ x](addition-operator.md) – x değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2424e-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="2424e-133">[-x](subtraction-operator.md) – sayısal olumsuzlama.</span><span class="sxs-lookup"><span data-stu-id="2424e-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="2424e-134">[\!x](logical-negation-operator.md) – mantıksal olumsuzlama.</span><span class="sxs-lookup"><span data-stu-id="2424e-134">[\!x](logical-negation-operator.md) – logical negation.</span></span>

<span data-ttu-id="2424e-135">[~ x](bitwise-complement-operator.md) – bit düzeyinde tamamlayıcı.</span><span class="sxs-lookup"><span data-stu-id="2424e-135">[~x](bitwise-complement-operator.md) – bitwise complement.</span></span>

<span data-ttu-id="2424e-136">[++ x](arithmetic-operators.md#increment-operator-) – önek artırma.</span><span class="sxs-lookup"><span data-stu-id="2424e-136">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="2424e-137">Depolama konumu bir x değeriyle güncelleştirdikten sonra x değerini büyük döndürür (genellikle 1 tamsayı ekler).</span><span class="sxs-lookup"><span data-stu-id="2424e-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="2424e-138">[--x](arithmetic-operators.md#decrement-operator---) – önek azaltma.</span><span class="sxs-lookup"><span data-stu-id="2424e-138">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="2424e-139">Depolama konumu daha az bir x değeriyle güncelleştirdikten sonra x değeri döndürür (genelde tam sayı 1 çıkarır).</span><span class="sxs-lookup"><span data-stu-id="2424e-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="2424e-140">[(T) x](invocation-operator.md) – atama yazın.</span><span class="sxs-lookup"><span data-stu-id="2424e-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="2424e-141">[await](../keywords/await.md) – bekler bir `Task`.</span><span class="sxs-lookup"><span data-stu-id="2424e-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="2424e-142">[& x](and-operator.md) – adresidir.</span><span class="sxs-lookup"><span data-stu-id="2424e-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="2424e-143">[\* x](multiplication-operator.md) – başvurusunu kaldırma.</span><span class="sxs-lookup"><span data-stu-id="2424e-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="2424e-144">Çarpma işleçleri</span><span class="sxs-lookup"><span data-stu-id="2424e-144">Multiplicative operators</span></span>

<span data-ttu-id="2424e-145">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="2424e-145">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-146">[x \* y](arithmetic-operators.md#multiplication-operator-) – çarpma.</span><span class="sxs-lookup"><span data-stu-id="2424e-146">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="2424e-147">[x / y](arithmetic-operators.md#division-operator-) – bölme.</span><span class="sxs-lookup"><span data-stu-id="2424e-147">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="2424e-148">İşlenenler tamsayılar, sonuç sıfıra yakınsayarak kesilmiş bir tamsayıdır (örneğin, `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="2424e-148">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="2424e-149">[% y x](arithmetic-operators.md#remainder-operator-) – kalan.</span><span class="sxs-lookup"><span data-stu-id="2424e-149">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="2424e-150">İşlenen tamsayılar olursa bu y bölme x geri kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="2424e-150">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="2424e-151">Varsa `q = x / y` ve `r = x % y`, ardından `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="2424e-151">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="2424e-152">Toplama işleçleri</span><span class="sxs-lookup"><span data-stu-id="2424e-152">Additive operators</span></span>

<span data-ttu-id="2424e-153">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="2424e-153">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-154">[x + y](arithmetic-operators.md#addition-operator-) – ekleme.</span><span class="sxs-lookup"><span data-stu-id="2424e-154">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="2424e-155">[x-y](arithmetic-operators.md#subtraction-operator--) – çıkarma.</span><span class="sxs-lookup"><span data-stu-id="2424e-155">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="2424e-156">Kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="2424e-156">Shift operators</span></span>

<span data-ttu-id="2424e-157">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="2424e-157">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-158">[x <\< y](left-shift-operator.md) – bitlerini sola kaydırma ve sağ taraftaki sıfır ile doldurun.</span><span class="sxs-lookup"><span data-stu-id="2424e-158">[x <\<  y](left-shift-operator.md) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="2424e-159">[x >> y](right-shift-operator.md) – sağ shift bitleri.</span><span class="sxs-lookup"><span data-stu-id="2424e-159">[x >> y](right-shift-operator.md) – shift bits right.</span></span> <span data-ttu-id="2424e-160">Sol işlenen ise `int` veya `long`, sonra da sol bit imza biti ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="2424e-160">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="2424e-161">Sol işlenen ise `uint` veya `ulong`, sonra da sol bitler sıfır ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="2424e-161">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="2424e-162">İlişkisel ve tür testi işleçleri</span><span class="sxs-lookup"><span data-stu-id="2424e-162">Relational and type-testing operators</span></span>

<span data-ttu-id="2424e-163">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="2424e-163">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-164">[x \< y](less-than-operator.md) – (x, y değerinden ise true) küçüktür.</span><span class="sxs-lookup"><span data-stu-id="2424e-164">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="2424e-165">[x > y](greater-than-operator.md) – büyük (x, y büyükse true).</span><span class="sxs-lookup"><span data-stu-id="2424e-165">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="2424e-166">[x \<y =](less-than-equal-operator.md) – küçük veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="2424e-166">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="2424e-167">[x > y =](greater-than-equal-operator.md) – büyüktür veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="2424e-167">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="2424e-168">[olan](../keywords/is.md) – uyumluluk yazın.</span><span class="sxs-lookup"><span data-stu-id="2424e-168">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="2424e-169">Değerlendirilen sol işlenen sağ işlenen (statik türü) belirtilen türe dönüştürülebilir ise true döndürür.</span><span class="sxs-lookup"><span data-stu-id="2424e-169">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="2424e-170">[olarak](../keywords/as.md) – dönüştürmesi yazın.</span><span class="sxs-lookup"><span data-stu-id="2424e-170">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="2424e-171">(Bir statik türü), sağ işlenen tarafından belirtilen tür için sol işlenen döndürür ancak `as` döndürür `null` burada `(T)x` bir özel durum oluşturması.</span><span class="sxs-lookup"><span data-stu-id="2424e-171">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="2424e-172">Eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="2424e-172">Equality operators</span></span>

<span data-ttu-id="2424e-173">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="2424e-173">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-174">[x == y](equality-operators.md#equality-operator-) – eşitlik.</span><span class="sxs-lookup"><span data-stu-id="2424e-174">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="2424e-175">Varsayılan olarak, başvuru için türleri dışındaki `string`, bu başvuru eşitliği (kimlik test) döndürür.</span><span class="sxs-lookup"><span data-stu-id="2424e-175">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="2424e-176">Ancak, türleri aşırı yüklenebilir `==`, amacınız kimliğini test etmek için ise kullanmak en iyisidir `ReferenceEquals` metodunda `object`.</span><span class="sxs-lookup"><span data-stu-id="2424e-176">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="2424e-177">[x! = y](equality-operators.md#inequality-operator-) – eşit değil.</span><span class="sxs-lookup"><span data-stu-id="2424e-177">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="2424e-178">Açıklama için bkz. `==`.</span><span class="sxs-lookup"><span data-stu-id="2424e-178">See comment for `==`.</span></span> <span data-ttu-id="2424e-179">Bir tür aşırı `==`, aşırı gerekir sonra `!=`.</span><span class="sxs-lookup"><span data-stu-id="2424e-179">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="2424e-180">Mantıksal AND işleci</span><span class="sxs-lookup"><span data-stu-id="2424e-180">Logical AND operator</span></span>

<span data-ttu-id="2424e-181">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2424e-181">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-182">[x ve y](and-operator.md) – mantıksal ve bit düzeyinde and</span><span class="sxs-lookup"><span data-stu-id="2424e-182">[x & y](and-operator.md) – logical or bitwise AND.</span></span> <span data-ttu-id="2424e-183">Bu genellikle tamsayı türleri ile kullanabilirsiniz ve `enum` türleri.</span><span class="sxs-lookup"><span data-stu-id="2424e-183">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="2424e-184">Mantıksal XOR işleci</span><span class="sxs-lookup"><span data-stu-id="2424e-184">Logical XOR operator</span></span>

<span data-ttu-id="2424e-185">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2424e-185">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-186">[x ^ y](xor-operator.md) – mantıksal ve bit düzeyinde XOR.</span><span class="sxs-lookup"><span data-stu-id="2424e-186">[x ^ y](xor-operator.md) – logical or bitwise XOR.</span></span> <span data-ttu-id="2424e-187">Bu genellikle tamsayı türleri ile kullanabilirsiniz ve `enum` türleri.</span><span class="sxs-lookup"><span data-stu-id="2424e-187">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="2424e-188">Mantıksal OR işleci</span><span class="sxs-lookup"><span data-stu-id="2424e-188">Logical OR operator</span></span>

<span data-ttu-id="2424e-189">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2424e-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-190">[x &#124; y](or-operator.md) – mantıksal ve bit düzeyinde OR.</span><span class="sxs-lookup"><span data-stu-id="2424e-190">[x &#124; y](or-operator.md) – logical or bitwise OR.</span></span> <span data-ttu-id="2424e-191">Bu genellikle tamsayı türleri ile kullanabilirsiniz ve `enum` türleri.</span><span class="sxs-lookup"><span data-stu-id="2424e-191">You can generally use this with integer types and `enum` types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="2424e-192">Koşullu AND işleci</span><span class="sxs-lookup"><span data-stu-id="2424e-192">Conditional AND operator</span></span>

<span data-ttu-id="2424e-193">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2424e-193">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-194">[x & & y](conditional-and-operator.md) – mantıksal and</span><span class="sxs-lookup"><span data-stu-id="2424e-194">[x && y](conditional-and-operator.md) – logical AND.</span></span> <span data-ttu-id="2424e-195">İlk işlenen false olarak değerlendirilirse, ardından C# ikinci işlenenin değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="2424e-195">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="2424e-196">Koşullu OR işleci</span><span class="sxs-lookup"><span data-stu-id="2424e-196">Conditional OR operator</span></span>

<span data-ttu-id="2424e-197">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2424e-197">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-198">[x &#124; &#124; y](conditional-or-operator.md) – mantıksal OR.</span><span class="sxs-lookup"><span data-stu-id="2424e-198">[x &#124;&#124; y](conditional-or-operator.md) – logical OR.</span></span> <span data-ttu-id="2424e-199">İlk işlenen true olarak değerlendirilirse, ardından C# ikinci işlenenin değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="2424e-199">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="2424e-200">Null birleşim işleci</span><span class="sxs-lookup"><span data-stu-id="2424e-200">Null-coalescing operator</span></span>

<span data-ttu-id="2424e-201">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2424e-201">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-202">[x?? y](null-coalescing-operator.md) – döndürür `x` olmayan ise`null`; Aksi halde döndürür `y`.</span><span class="sxs-lookup"><span data-stu-id="2424e-202">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="2424e-203">Koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="2424e-203">Conditional operator</span></span>

<span data-ttu-id="2424e-204">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2424e-204">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-205">[t? x: y](conditional-operator.md) – test `t` true, ardından değerlendirilip döndürülecek değerlendirir `x`; Aksi takdirde, değerlendirilip döndürülecek `y`.</span><span class="sxs-lookup"><span data-stu-id="2424e-205">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="2424e-206">Atama ve Lambda işleçleri</span><span class="sxs-lookup"><span data-stu-id="2424e-206">Assignment and Lambda operators</span></span>

<span data-ttu-id="2424e-207">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="2424e-207">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="2424e-208">[x = y](assignment-operator.md) – atama.</span><span class="sxs-lookup"><span data-stu-id="2424e-208">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="2424e-209">[x += y](addition-assignment-operator.md) – artırma.</span><span class="sxs-lookup"><span data-stu-id="2424e-209">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="2424e-210">Değerini ekleme `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-210">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="2424e-211">Varsa `x` atayan bir `event`, ardından `y` C# bir olay işleyicisi ekler uygun bir işlev olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2424e-211">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="2424e-212">[x-= y](subtraction-assignment-operator.md) – azaltma.</span><span class="sxs-lookup"><span data-stu-id="2424e-212">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="2424e-213">Değerini çıkarma `y` değerinden `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-213">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="2424e-214">Varsa `x` atayan bir `event`, ardından `y` C# kaldıran bir olay işleyicisi uygun bir işlev olmalıdır</span><span class="sxs-lookup"><span data-stu-id="2424e-214">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler</span></span>

<span data-ttu-id="2424e-215">[x \* y =](multiplication-assignment-operator.md) – çarpma atama.</span><span class="sxs-lookup"><span data-stu-id="2424e-215">[x \*= y](multiplication-assignment-operator.md) – multiplication assignment.</span></span> <span data-ttu-id="2424e-216">Çarp değeri `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-216">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="2424e-217">[x / y =](arithmetic-operators.md#compound-assignment) – bölme ataması.</span><span class="sxs-lookup"><span data-stu-id="2424e-217">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="2424e-218">Değerini ayırmak `x` değeriyle `y`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-218">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="2424e-219">[%x y =](arithmetic-operators.md#compound-assignment) – kalanını atama.</span><span class="sxs-lookup"><span data-stu-id="2424e-219">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="2424e-220">Değerini ayırmak `x` değeriyle `y`, kalanı depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-220">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="2424e-221">[x & y =](and-assignment-operator.md) – ve atama.</span><span class="sxs-lookup"><span data-stu-id="2424e-221">[x &= y](and-assignment-operator.md) – AND assignment.</span></span> <span data-ttu-id="2424e-222">DEĞERİ `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-222">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="2424e-223">[x &#124;y =](or-assignment-operator.md) – OR ataması.</span><span class="sxs-lookup"><span data-stu-id="2424e-223">[x &#124;= y](or-assignment-operator.md) – OR assignment.</span></span> <span data-ttu-id="2424e-224">YA da değerini `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-224">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="2424e-225">[x ^ y =](xor-assignment-operator.md) – XOR atama.</span><span class="sxs-lookup"><span data-stu-id="2424e-225">[x ^= y](xor-assignment-operator.md) – XOR assignment.</span></span> <span data-ttu-id="2424e-226">XOR değeri, `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-226">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="2424e-227">[x << y =](left-shift-assignment-operator.md) – sola kaydırma ataması.</span><span class="sxs-lookup"><span data-stu-id="2424e-227">[x <<= y](left-shift-assignment-operator.md) – left-shift assignment.</span></span> <span data-ttu-id="2424e-228">Değerini kaydırma `x` sol tarafından `y` yerde depolamak sonucunda `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-228">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="2424e-229">[x >> y =](right-shift-assignment-operator.md) – sağa kaydırma ataması.</span><span class="sxs-lookup"><span data-stu-id="2424e-229">[x >>= y](right-shift-assignment-operator.md) – right-shift assignment.</span></span> <span data-ttu-id="2424e-230">Değerini kaydırma `x` sağa `y` yerde depolamak sonucunda `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="2424e-230">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="2424e-231">[=>](lambda-operator.md) – lambda bildirimi.</span><span class="sxs-lookup"><span data-stu-id="2424e-231">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="2424e-232">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2424e-232">See also</span></span>

- [<span data-ttu-id="2424e-233">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2424e-233">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2424e-234">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2424e-234">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2424e-235">C#</span><span class="sxs-lookup"><span data-stu-id="2424e-235">C#</span></span>](../../index.md)
- [<span data-ttu-id="2424e-236">Aşırı Yüklenebilir İşleçler</span><span class="sxs-lookup"><span data-stu-id="2424e-236">Overloadable Operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="2424e-237">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2424e-237">C# Keywords</span></span>](../keywords/index.md)