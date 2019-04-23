---
title: C# işleçleri
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
ms.openlocfilehash: f4267caeb6301950b9f6a8b9545a47b9f48e7920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977385"
---
# <a name="c-operators"></a><span data-ttu-id="ab932-102">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="ab932-102">C# operators</span></span>

<span data-ttu-id="ab932-103">C# (matematik, dizin oluşturma, işlev çağrısı, vb.) bir ifadede gerçekleştirilecek işlemleri belirten simgelerdir birçok işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab932-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="ab932-104">Yapabilecekleriniz [aşırı](../../programming-guide/statements-expressions-operators/overloadable-operators.md) işleçlerinin çoğu kullanıcı tanımlı bir türe başvurulduğunda anlamının değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ab932-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="ab932-105">Tamsayı türlerinde işlemler (gibi `==`, `!=`, `<`, `>`, `&`, `|`) genellikle numaralandırma üzerinde izin verilir (`enum`) türleri.</span><span class="sxs-lookup"><span data-stu-id="ab932-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="ab932-106">Aşağıdaki bölümlerde, en yüksek önceliğe düşüğe başlayarak C# işleçleri listeler.</span><span class="sxs-lookup"><span data-stu-id="ab932-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="ab932-107">Her bölüm içerisindeki işleçler aynı öncelik düzeyine paylaşın.</span><span class="sxs-lookup"><span data-stu-id="ab932-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="ab932-108">Birincil operatörler</span><span class="sxs-lookup"><span data-stu-id="ab932-108">Primary operators</span></span>

<span data-ttu-id="ab932-109">En yüksek öncelik işleçleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="ab932-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="ab932-110">[x.y](member-access-operator.md) – üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="ab932-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="ab932-111">[x? y](null-conditional-operators.md) – null koşullu üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="ab932-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="ab932-112">Döndürür `null` sol işlenen değerlendirilirse `null`.</span><span class="sxs-lookup"><span data-stu-id="ab932-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="ab932-113">[x? [y] ](null-conditional-operators.md) -null koşullu dizin erişim.</span><span class="sxs-lookup"><span data-stu-id="ab932-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="ab932-114">Döndürür `null` sol işlenen değerlendirilirse `null`.</span><span class="sxs-lookup"><span data-stu-id="ab932-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="ab932-115">[f(x)](invocation-operator.md) – işlev çağırma.</span><span class="sxs-lookup"><span data-stu-id="ab932-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="ab932-116">[bir&#91;x&#93; ](index-operator.md) – toplama nesnesi dizin oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ab932-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="ab932-117">[x ++](arithmetic-operators.md#increment-operator-) – sonek artırma.</span><span class="sxs-lookup"><span data-stu-id="ab932-117">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="ab932-118">X değerini döndürür ve ardından depolama konumu büyük bir x değeri ile güncelleştirir (genellikle 1 tamsayı ekler).</span><span class="sxs-lookup"><span data-stu-id="ab932-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="ab932-119">[x--](arithmetic-operators.md#decrement-operator---) – son ek azaltma.</span><span class="sxs-lookup"><span data-stu-id="ab932-119">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="ab932-120">X değerini döndürür ve ardından depolama konumu bir daha az x değeri ile güncelleştirir (genellikle 1 tamsayı çıkarır).</span><span class="sxs-lookup"><span data-stu-id="ab932-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="ab932-121">[Yeni](../keywords/new-operator.md) – oluşturmada yazın.</span><span class="sxs-lookup"><span data-stu-id="ab932-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="ab932-122">[typeof](../keywords/typeof.md) – döndürür <xref:System.Type> işlenen temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="ab932-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="ab932-123">[işaretli](../keywords/checked.md) – taşma denetimi için tamsayı işlemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab932-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="ab932-124">[denetlenmeyen](../keywords/unchecked.md) – taşma tamsayı işlemlerinde denetimini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="ab932-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="ab932-125">Varsayılan derleyici davranışı budur.</span><span class="sxs-lookup"><span data-stu-id="ab932-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="ab932-126">[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – t türü varsayılan değerini üretir</span><span class="sxs-lookup"><span data-stu-id="ab932-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="ab932-127">[Temsilci](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – bildirir ve temsilci örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab932-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="ab932-128">[sizeof](../keywords/sizeof.md) -türü işlenen bayt cinsinden boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab932-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="ab932-129">[->](dereference-operator.md) – Birleştirilmiş üye erişimi ile işaretçiye başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="ab932-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="ab932-130">Birli işleçler</span><span class="sxs-lookup"><span data-stu-id="ab932-130">Unary operators</span></span>

<span data-ttu-id="ab932-131">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ab932-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-132">[+ x](addition-operator.md) – x değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab932-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="ab932-133">[-x](subtraction-operator.md) – sayısal olumsuzlama.</span><span class="sxs-lookup"><span data-stu-id="ab932-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="ab932-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – mantıksal olumsuzlama.</span><span class="sxs-lookup"><span data-stu-id="ab932-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="ab932-135">[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bit düzeyinde tamamlayıcı.</span><span class="sxs-lookup"><span data-stu-id="ab932-135">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="ab932-136">[++ x](arithmetic-operators.md#increment-operator-) – önek artırma.</span><span class="sxs-lookup"><span data-stu-id="ab932-136">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="ab932-137">Depolama konumu bir x değeriyle güncelleştirdikten sonra x değerini büyük döndürür (genellikle 1 tamsayı ekler).</span><span class="sxs-lookup"><span data-stu-id="ab932-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="ab932-138">[--x](arithmetic-operators.md#decrement-operator---) – önek azaltma.</span><span class="sxs-lookup"><span data-stu-id="ab932-138">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="ab932-139">Depolama konumu daha az bir x değeriyle güncelleştirdikten sonra x değeri döndürür (genelde tam sayı 1 çıkarır).</span><span class="sxs-lookup"><span data-stu-id="ab932-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="ab932-140">[(T) x](invocation-operator.md) – atama yazın.</span><span class="sxs-lookup"><span data-stu-id="ab932-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="ab932-141">[await](../keywords/await.md) – bekler bir `Task`.</span><span class="sxs-lookup"><span data-stu-id="ab932-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="ab932-142">[& x](and-operator.md) – adresidir.</span><span class="sxs-lookup"><span data-stu-id="ab932-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="ab932-143">[\* x](multiplication-operator.md) – başvurusunu kaldırma.</span><span class="sxs-lookup"><span data-stu-id="ab932-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

<span data-ttu-id="ab932-144">[true işleci](../keywords/true-false-operators.md) -döndürür [bool](../keywords/bool.md) değer `true` işleneni kesinlikle doğru olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="ab932-144">[true operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="ab932-145">[false işleci](../keywords/true-false-operators.md) -döndürür [bool](../keywords/bool.md) değer `true` işleneni kesinlikle false olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="ab932-145">[false operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="ab932-146">Çarpma işleçleri</span><span class="sxs-lookup"><span data-stu-id="ab932-146">Multiplicative operators</span></span>

<span data-ttu-id="ab932-147">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ab932-147">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-148">[x \* y](arithmetic-operators.md#multiplication-operator-) – çarpma.</span><span class="sxs-lookup"><span data-stu-id="ab932-148">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="ab932-149">[x / y](arithmetic-operators.md#division-operator-) – bölme.</span><span class="sxs-lookup"><span data-stu-id="ab932-149">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="ab932-150">İşlenenler tamsayılar, sonuç sıfıra yakınsayarak kesilmiş bir tamsayıdır (örneğin, `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="ab932-150">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="ab932-151">[% y x](arithmetic-operators.md#remainder-operator-) – kalan.</span><span class="sxs-lookup"><span data-stu-id="ab932-151">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="ab932-152">İşlenen tamsayılar olursa bu y bölme x geri kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab932-152">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="ab932-153">Varsa `q = x / y` ve `r = x % y`, ardından `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="ab932-153">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="ab932-154">Toplama işleçleri</span><span class="sxs-lookup"><span data-stu-id="ab932-154">Additive operators</span></span>

<span data-ttu-id="ab932-155">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ab932-155">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-156">[x + y](arithmetic-operators.md#addition-operator-) – ekleme.</span><span class="sxs-lookup"><span data-stu-id="ab932-156">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="ab932-157">[x-y](arithmetic-operators.md#subtraction-operator--) – çıkarma.</span><span class="sxs-lookup"><span data-stu-id="ab932-157">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="ab932-158">Kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="ab932-158">Shift operators</span></span>

<span data-ttu-id="ab932-159">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ab932-159">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-160">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – bitlerini sola kaydırma ve sağ taraftaki sıfır ile doldurun.</span><span class="sxs-lookup"><span data-stu-id="ab932-160">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="ab932-161">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – sağ shift bitleri.</span><span class="sxs-lookup"><span data-stu-id="ab932-161">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="ab932-162">Sol işlenen ise `int` veya `long`, sonra da sol bit imza biti ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ab932-162">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="ab932-163">Sol işlenen ise `uint` veya `ulong`, sonra da sol bitler sıfır ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ab932-163">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="ab932-164">İlişkisel ve tür testi işleçleri</span><span class="sxs-lookup"><span data-stu-id="ab932-164">Relational and type-testing operators</span></span>

<span data-ttu-id="ab932-165">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ab932-165">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-166">[x \< y](less-than-operator.md) – (x, y değerinden ise true) küçüktür.</span><span class="sxs-lookup"><span data-stu-id="ab932-166">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="ab932-167">[x > y](greater-than-operator.md) – büyük (x, y büyükse true).</span><span class="sxs-lookup"><span data-stu-id="ab932-167">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="ab932-168">[x \<y =](less-than-equal-operator.md) – küçük veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="ab932-168">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="ab932-169">[x > y =](greater-than-equal-operator.md) – büyüktür veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="ab932-169">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="ab932-170">[olan](../keywords/is.md) – uyumluluk yazın.</span><span class="sxs-lookup"><span data-stu-id="ab932-170">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="ab932-171">Değerlendirilen sol işlenen sağ işlenen (statik türü) belirtilen türe dönüştürülebilir ise true döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab932-171">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="ab932-172">[olarak](../keywords/as.md) – dönüştürmesi yazın.</span><span class="sxs-lookup"><span data-stu-id="ab932-172">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="ab932-173">(Bir statik türü), sağ işlenen tarafından belirtilen tür için sol işlenen döndürür ancak `as` döndürür `null` burada `(T)x` bir özel durum oluşturması.</span><span class="sxs-lookup"><span data-stu-id="ab932-173">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="ab932-174">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="ab932-174">Equality operators</span></span>

<span data-ttu-id="ab932-175">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ab932-175">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-176">[x == y](equality-operators.md#equality-operator-) – eşitlik.</span><span class="sxs-lookup"><span data-stu-id="ab932-176">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="ab932-177">Varsayılan olarak, başvuru için türleri dışındaki `string`, bu başvuru eşitliği (kimlik test) döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab932-177">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="ab932-178">Ancak, türleri aşırı yüklenebilir `==`, amacınız kimliğini test etmek için ise kullanmak en iyisidir `ReferenceEquals` metodunda `object`.</span><span class="sxs-lookup"><span data-stu-id="ab932-178">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="ab932-179">[x! = y](equality-operators.md#inequality-operator-) – eşit değil.</span><span class="sxs-lookup"><span data-stu-id="ab932-179">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="ab932-180">Açıklama için bkz. `==`.</span><span class="sxs-lookup"><span data-stu-id="ab932-180">See comment for `==`.</span></span> <span data-ttu-id="ab932-181">Bir tür aşırı `==`, aşırı gerekir sonra `!=`.</span><span class="sxs-lookup"><span data-stu-id="ab932-181">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="ab932-182">Mantıksal AND işleci</span><span class="sxs-lookup"><span data-stu-id="ab932-182">Logical AND operator</span></span>

<span data-ttu-id="ab932-183">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab932-183">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-184">`x & y` – [mantıksal AND](boolean-logical-operators.md#logical-and-operator-) için `bool` işlenenler veya [mantıksal bit düzeyinde AND](bitwise-and-shift-operators.md#logical-and-operator-) işleneni de integral türleri için.</span><span class="sxs-lookup"><span data-stu-id="ab932-184">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="ab932-185">Mantıksal XOR işleci</span><span class="sxs-lookup"><span data-stu-id="ab932-185">Logical XOR operator</span></span>

<span data-ttu-id="ab932-186">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab932-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-187">`x ^ y` – [mantıksal XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) için `bool` işlenenler veya [mantıksal bit düzeyinde XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) işleneni de integral türleri için.</span><span class="sxs-lookup"><span data-stu-id="ab932-187">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="ab932-188">Mantıksal OR işleci</span><span class="sxs-lookup"><span data-stu-id="ab932-188">Logical OR operator</span></span>

<span data-ttu-id="ab932-189">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab932-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-190">`x | y` – [mantıksal OR](boolean-logical-operators.md#logical-or-operator-) için `bool` işlenenler veya [mantıksal bit düzeyinde OR](bitwise-and-shift-operators.md#logical-or-operator-) işleneni de integral türleri için.</span><span class="sxs-lookup"><span data-stu-id="ab932-190">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="ab932-191">Koşullu AND işleci</span><span class="sxs-lookup"><span data-stu-id="ab932-191">Conditional AND operator</span></span>

<span data-ttu-id="ab932-192">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab932-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-193">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) – mantıksal and</span><span class="sxs-lookup"><span data-stu-id="ab932-193">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="ab932-194">İlk işlenen false olarak değerlendirilirse, ardından C# ikinci işlenenin değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="ab932-194">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="ab932-195">Koşullu OR işleci</span><span class="sxs-lookup"><span data-stu-id="ab932-195">Conditional OR operator</span></span>

<span data-ttu-id="ab932-196">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab932-196">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-197">[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – mantıksal OR.</span><span class="sxs-lookup"><span data-stu-id="ab932-197">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="ab932-198">İlk işlenen true olarak değerlendirilirse, ardından C# ikinci işlenenin değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="ab932-198">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="ab932-199">Null birleşim işleci</span><span class="sxs-lookup"><span data-stu-id="ab932-199">Null-coalescing operator</span></span>

<span data-ttu-id="ab932-200">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab932-200">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-201">[x?? y](null-coalescing-operator.md) – döndürür `x` olmayan ise`null`; Aksi halde döndürür `y`.</span><span class="sxs-lookup"><span data-stu-id="ab932-201">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="ab932-202">Koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="ab932-202">Conditional operator</span></span>

<span data-ttu-id="ab932-203">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab932-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-204">[t? x: y](conditional-operator.md) – test `t` true, ardından değerlendirilip döndürülecek değerlendirir `x`; Aksi takdirde, değerlendirilip döndürülecek `y`.</span><span class="sxs-lookup"><span data-stu-id="ab932-204">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="ab932-205">Atama ve Lambda işleçleri</span><span class="sxs-lookup"><span data-stu-id="ab932-205">Assignment and Lambda operators</span></span>

<span data-ttu-id="ab932-206">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ab932-206">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="ab932-207">[x = y](assignment-operator.md) – atama.</span><span class="sxs-lookup"><span data-stu-id="ab932-207">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="ab932-208">[x += y](addition-assignment-operator.md) – artırma.</span><span class="sxs-lookup"><span data-stu-id="ab932-208">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="ab932-209">Değerini ekleme `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-209">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="ab932-210">Varsa `x` atayan bir `event`, ardından `y` C# bir olay işleyicisi ekler uygun bir işlev olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab932-210">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="ab932-211">[x-= y](subtraction-assignment-operator.md) – azaltma.</span><span class="sxs-lookup"><span data-stu-id="ab932-211">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="ab932-212">Değerini çıkarma `y` değerinden `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-212">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="ab932-213">Varsa `x` atayan bir `event`, ardından `y` uygun bir işlev olmalıdır C# bir olay işleyicisi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ab932-213">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler.</span></span>

<span data-ttu-id="ab932-214">[x \* y =](arithmetic-operators.md#compound-assignment) – çarpma atama.</span><span class="sxs-lookup"><span data-stu-id="ab932-214">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="ab932-215">Çarp değeri `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-215">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="ab932-216">[x / y =](arithmetic-operators.md#compound-assignment) – bölme ataması.</span><span class="sxs-lookup"><span data-stu-id="ab932-216">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="ab932-217">Değerini ayırmak `x` değeriyle `y`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-217">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="ab932-218">[%x y =](arithmetic-operators.md#compound-assignment) – kalanını atama.</span><span class="sxs-lookup"><span data-stu-id="ab932-218">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="ab932-219">Değerini ayırmak `x` değeriyle `y`, kalanı depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-219">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="ab932-220">[x & y =](boolean-logical-operators.md#compound-assignment) – ve atama.</span><span class="sxs-lookup"><span data-stu-id="ab932-220">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="ab932-221">DEĞERİ `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-221">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="ab932-222">[x &#124;y =](boolean-logical-operators.md#compound-assignment) – OR ataması.</span><span class="sxs-lookup"><span data-stu-id="ab932-222">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="ab932-223">YA da değerini `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-223">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="ab932-224">[x ^ y =](boolean-logical-operators.md#compound-assignment) – XOR atama.</span><span class="sxs-lookup"><span data-stu-id="ab932-224">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="ab932-225">XOR değeri, `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-225">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="ab932-226">[x << y =](bitwise-and-shift-operators.md#compound-assignment) – sola kaydırma ataması.</span><span class="sxs-lookup"><span data-stu-id="ab932-226">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="ab932-227">Değerini kaydırma `x` sol tarafından `y` yerde depolamak sonucunda `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-227">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="ab932-228">[x >> y =](bitwise-and-shift-operators.md#compound-assignment) – sağa kaydırma ataması.</span><span class="sxs-lookup"><span data-stu-id="ab932-228">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="ab932-229">Değerini kaydırma `x` sağa `y` yerde depolamak sonucunda `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab932-229">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="ab932-230">[=>](lambda-operator.md) – lambda bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ab932-230">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab932-231">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab932-231">See also</span></span>

- [<span data-ttu-id="ab932-232">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ab932-232">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ab932-233">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ab932-233">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ab932-234">C#</span><span class="sxs-lookup"><span data-stu-id="ab932-234">C#</span></span>](../../index.md)
- [<span data-ttu-id="ab932-235">Fazla yüklenebilir işleçler</span><span class="sxs-lookup"><span data-stu-id="ab932-235">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="ab932-236">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ab932-236">C# Keywords</span></span>](../keywords/index.md)
