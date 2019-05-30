---
title: C# işleçleri
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
ms.openlocfilehash: c1f891314a2490d6dbf22977ea5a5f69533b330d
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300316"
---
# <a name="c-operators"></a><span data-ttu-id="1c6d4-102">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="1c6d4-102">C# operators</span></span>

<span data-ttu-id="1c6d4-103">C#birkaç yerleşik türleri tarafından desteklenen önceden tanımlı operatörler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-103">C# provides a number of predefined operators supported by the built-in types.</span></span> <span data-ttu-id="1c6d4-104">Örneğin, [aritmetik işleçler](arithmetic-operators.md) yerleşik sayısal türler, işlenenlerin aritmetik işlemler gerçekleştirme ve [Boolean mantıksal işleçler](boolean-logical-operators.md) mantıksal işlemleri ile [bool ](../keywords/bool.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-104">For example, [arithmetic operators](arithmetic-operators.md) perform arithmetic operations with operands of built-in numeric types and [Boolean logical operators](boolean-logical-operators.md) perform logical operations with the [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="1c6d4-105">Kullanıcı tanımlı bir tür o türündeki işlenenler için karşılık gelen davranışını tanımlamak için belirli işleçleri aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-105">A user-defined type can overload certain operators to define the corresponding behavior for the operands of that type.</span></span> <span data-ttu-id="1c6d4-106">Daha fazla bilgi için [işleci](../keywords/operator.md) anahtar sözcüğü makalesi.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-106">For more information, see the [operator](../keywords/operator.md) keyword article.</span></span>

<span data-ttu-id="1c6d4-107">Aşağıdaki bölümlerde liste C# en yüksek önceliğe düşüğe başlayarak işleçleri.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-107">The following sections list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="1c6d4-108">Her bölüm içerisindeki işleçler aynı öncelik düzeyine paylaşın.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-108">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="1c6d4-109">Birincil operatörler</span><span class="sxs-lookup"><span data-stu-id="1c6d4-109">Primary operators</span></span>

<span data-ttu-id="1c6d4-110">En yüksek öncelik işleçleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-110">These are the highest precedence operators.</span></span>

<span data-ttu-id="1c6d4-111">[x.y](member-access-operators.md#member-access-operator-) – üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-111">[x.y](member-access-operators.md#member-access-operator-) – member access.</span></span>

<span data-ttu-id="1c6d4-112">[x? y](member-access-operators.md#null-conditional-operators--and-) – null koşullu üye erişimi.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null conditional member access.</span></span> <span data-ttu-id="1c6d4-113">Döndürür `null` sol işlenen değerlendirilirse `null`.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-113">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="1c6d4-114">[x? [y] ](member-access-operators.md#null-conditional-operators--and-) - koşullu dizi öğesi null veya dizin oluşturucu erişim yazın.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null conditional array element or type indexer access.</span></span> <span data-ttu-id="1c6d4-115">Döndürür `null` sol işlenen değerlendirilirse `null`.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-115">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="1c6d4-116">[f(x)](member-access-operators.md#invocation-operator-) – yöntem çağrısı veya temsilci çağırma.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-116">[f(x)](member-access-operators.md#invocation-operator-) – method call or delegate invocation.</span></span>

<span data-ttu-id="1c6d4-117">[bir&#91;x&#93; ](member-access-operators.md#indexer-operator-) – dizi öğesi veya dizin oluşturucu erişim yazın.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-117">[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – array element or type indexer access.</span></span>

<span data-ttu-id="1c6d4-118">[x ++](arithmetic-operators.md#increment-operator-) – sonek artırma.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-118">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="1c6d4-119">X değerini döndürür ve ardından depolama konumu büyük bir x değeri ile güncelleştirir (genellikle 1 tamsayı ekler).</span><span class="sxs-lookup"><span data-stu-id="1c6d4-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="1c6d4-120">[x--](arithmetic-operators.md#decrement-operator---) – son ek azaltma.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-120">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="1c6d4-121">X değerini döndürür ve ardından depolama konumu bir daha az x değeri ile güncelleştirir (genellikle 1 tamsayı çıkarır).</span><span class="sxs-lookup"><span data-stu-id="1c6d4-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="1c6d4-122">[Yeni](../keywords/new-operator.md) – oluşturmada yazın.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-122">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="1c6d4-123">[typeof](../keywords/typeof.md) – döndürür <xref:System.Type> işlenen temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-123">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="1c6d4-124">[işaretli](../keywords/checked.md) – taşma denetimi için tamsayı işlemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-124">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="1c6d4-125">[denetlenmeyen](../keywords/unchecked.md) – taşma tamsayı işlemlerinde denetimini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-125">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="1c6d4-126">Varsayılan derleyici davranışı budur.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-126">This is the default compiler behavior.</span></span>

<span data-ttu-id="1c6d4-127">[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – t türü varsayılan değerini üretir</span><span class="sxs-lookup"><span data-stu-id="1c6d4-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="1c6d4-128">[nameof](../keywords/nameof.md) -değişken, tür veya üyenin bir sabit dize olarak basit (nitelenmemiş) adını alır.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-128">[nameof](../keywords/nameof.md) - obtains the simple (unqualified) name of a variable, type, or member as a constant string.</span></span>

<span data-ttu-id="1c6d4-129">[Temsilci](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – bildirir ve temsilci örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-129">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="1c6d4-130">[sizeof](../keywords/sizeof.md) -türü işlenen bayt cinsinden boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-130">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="1c6d4-131">[stackalloc](../keywords/stackalloc.md) -bir yığında bellek bloğu ayırır.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-131">[stackalloc](../keywords/stackalloc.md) - allocates a block of memory on the stack.</span></span>

<span data-ttu-id="1c6d4-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – İşaretçi yöneltmesi birleştirilmiş üye erişimi ile.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – pointer indirection combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="1c6d4-133">Birli işleçler</span><span class="sxs-lookup"><span data-stu-id="1c6d4-133">Unary operators</span></span>

<span data-ttu-id="1c6d4-134">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-134">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-135">[+ x](addition-operator.md) – x değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-135">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="1c6d4-136">[-x](subtraction-operator.md) – sayısal olumsuzlama.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-136">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="1c6d4-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – mantıksal olumsuzlama.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="1c6d4-138">[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bit düzeyinde tamamlayıcı.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="1c6d4-139">[++ x](arithmetic-operators.md#increment-operator-) – önek artırma.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-139">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="1c6d4-140">Depolama konumu bir x değeriyle güncelleştirdikten sonra x değerini büyük döndürür (genellikle 1 tamsayı ekler).</span><span class="sxs-lookup"><span data-stu-id="1c6d4-140">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="1c6d4-141">[--x](arithmetic-operators.md#decrement-operator---) – önek azaltma.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-141">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="1c6d4-142">Depolama konumu daha az bir x değeriyle güncelleştirdikten sonra x değeri döndürür (genelde tam sayı 1 çıkarır).</span><span class="sxs-lookup"><span data-stu-id="1c6d4-142">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="1c6d4-143">[(T) x](invocation-operator.md) – atama yazın.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-143">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="1c6d4-144">[await](../keywords/await.md) – bekler bir `Task`.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-144">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="1c6d4-145">[& x](pointer-related-operators.md#address-of-operator-) : değişkenin adresini.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-145">[&x](pointer-related-operators.md#address-of-operator-) – address of a variable.</span></span>

<span data-ttu-id="1c6d4-146">[\* x](pointer-related-operators.md#pointer-indirection-operator-) – işaretçi yöneltmesi veya başvuru.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – pointer indirection, or dereference.</span></span>

<span data-ttu-id="1c6d4-147">[true işleci](true-false-operators.md) -döndürür [bool](../keywords/bool.md) değer `true` işleneni kesinlikle doğru olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-147">[true operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="1c6d4-148">[false işleci](true-false-operators.md) -döndürür [bool](../keywords/bool.md) değer `true` işleneni kesinlikle false olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-148">[false operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="1c6d4-149">Çarpma işleçleri</span><span class="sxs-lookup"><span data-stu-id="1c6d4-149">Multiplicative operators</span></span>

<span data-ttu-id="1c6d4-150">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-150">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – çarpma.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="1c6d4-152">[x / y](arithmetic-operators.md#division-operator-) – bölme.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-152">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="1c6d4-153">İşlenenler tamsayılar, sonuç sıfıra yakınsayarak kesilmiş bir tamsayıdır (örneğin, `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="1c6d4-153">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="1c6d4-154">[% y x](arithmetic-operators.md#remainder-operator-) – kalan.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-154">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="1c6d4-155">İşlenen tamsayılar olursa bu y bölme x geri kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-155">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="1c6d4-156">Varsa `q = x / y` ve `r = x % y`, ardından `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-156">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="1c6d4-157">Toplama işleçleri</span><span class="sxs-lookup"><span data-stu-id="1c6d4-157">Additive operators</span></span>

<span data-ttu-id="1c6d4-158">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-158">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-159">[x + y](arithmetic-operators.md#addition-operator-) – ekleme.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-159">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="1c6d4-160">[x-y](arithmetic-operators.md#subtraction-operator--) – çıkarma.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="1c6d4-161">Kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="1c6d4-161">Shift operators</span></span>

<span data-ttu-id="1c6d4-162">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-162">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-163">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – bitlerini sola kaydırma ve sağ taraftaki sıfır ile doldurun.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="1c6d4-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – sağ shift bitleri.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="1c6d4-165">Sol işlenen ise `int` veya `long`, sonra da sol bit imza biti ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="1c6d4-166">Sol işlenen ise `uint` veya `ulong`, sonra da sol bitler sıfır ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="1c6d4-167">İlişkisel ve tür testi işleçleri</span><span class="sxs-lookup"><span data-stu-id="1c6d4-167">Relational and type-testing operators</span></span>

<span data-ttu-id="1c6d4-168">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-169">[x \< y](comparison-operators.md#less-than-operator-) – (x, y değerinden ise true) küçüktür.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-169">[x \< y](comparison-operators.md#less-than-operator-) – less than (true if x is less than y).</span></span>

<span data-ttu-id="1c6d4-170">[x > y](comparison-operators.md#greater-than-operator-) – büyük (x, y büyükse true).</span><span class="sxs-lookup"><span data-stu-id="1c6d4-170">[x > y](comparison-operators.md#greater-than-operator-) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="1c6d4-171">[x \<y =](comparison-operators.md#less-than-or-equal-operator-) – küçük veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – less than or equal to.</span></span>

<span data-ttu-id="1c6d4-172">[x > y =](comparison-operators.md#greater-than-or-equal-operator-) – büyüktür veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – greater than or equal to.</span></span>

<span data-ttu-id="1c6d4-173">[olan](../keywords/is.md) – uyumluluk yazın.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-173">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="1c6d4-174">Değerlendirilen sol işlenen sağ işlenen (statik türü) belirtilen türe dönüştürülebilir ise true döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-174">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="1c6d4-175">[olarak](../keywords/as.md) – dönüştürmesi yazın.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-175">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="1c6d4-176">(Bir statik türü), sağ işlenen tarafından belirtilen tür için sol işlenen döndürür ancak `as` döndürür `null` burada `(T)x` bir özel durum oluşturması.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-176">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="1c6d4-177">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="1c6d4-177">Equality operators</span></span>

<span data-ttu-id="1c6d4-178">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-178">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-179">[x == y](equality-operators.md#equality-operator-) – eşitlik.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-179">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="1c6d4-180">Varsayılan olarak, başvuru için türleri dışındaki `string`, bu başvuru eşitliği (kimlik test) döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-180">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="1c6d4-181">Ancak, türleri aşırı yüklenebilir `==`, amacınız kimliğini test etmek için ise kullanmak en iyisidir `ReferenceEquals` metodunda `object`.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-181">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="1c6d4-182">[x! = y](equality-operators.md#inequality-operator-) – eşit değil.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-182">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="1c6d4-183">Açıklama için bkz. `==`.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-183">See comment for `==`.</span></span> <span data-ttu-id="1c6d4-184">Bir tür aşırı `==`, aşırı gerekir sonra `!=`.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-184">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="1c6d4-185">Mantıksal AND işleci</span><span class="sxs-lookup"><span data-stu-id="1c6d4-185">Logical AND operator</span></span>

<span data-ttu-id="1c6d4-186">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-187">`x & y` – [mantıksal AND](boolean-logical-operators.md#logical-and-operator-) için `bool` işlenenler veya [mantıksal bit düzeyinde AND](bitwise-and-shift-operators.md#logical-and-operator-) işleneni de integral türleri için.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-187">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="1c6d4-188">Mantıksal XOR işleci</span><span class="sxs-lookup"><span data-stu-id="1c6d4-188">Logical XOR operator</span></span>

<span data-ttu-id="1c6d4-189">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-190">`x ^ y` – [mantıksal XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) için `bool` işlenenler veya [mantıksal bit düzeyinde XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) işleneni de integral türleri için.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-190">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="1c6d4-191">Mantıksal OR işleci</span><span class="sxs-lookup"><span data-stu-id="1c6d4-191">Logical OR operator</span></span>

<span data-ttu-id="1c6d4-192">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-193">`x | y` – [mantıksal OR](boolean-logical-operators.md#logical-or-operator-) için `bool` işlenenler veya [mantıksal bit düzeyinde OR](bitwise-and-shift-operators.md#logical-or-operator-) işleneni de integral türleri için.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-193">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="1c6d4-194">Koşullu AND işleci</span><span class="sxs-lookup"><span data-stu-id="1c6d4-194">Conditional AND operator</span></span>

<span data-ttu-id="1c6d4-195">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-195">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-196">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) – mantıksal and</span><span class="sxs-lookup"><span data-stu-id="1c6d4-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="1c6d4-197">İlk işlenen false olarak değerlendirilirse, ardından C# ikinci işlenenin değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-197">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="1c6d4-198">Koşullu OR işleci</span><span class="sxs-lookup"><span data-stu-id="1c6d4-198">Conditional OR operator</span></span>

<span data-ttu-id="1c6d4-199">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-199">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-200">[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – mantıksal OR.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="1c6d4-201">İlk işlenen true olarak değerlendirilirse, ardından C# ikinci işlenenin değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-201">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="1c6d4-202">Null birleşim işleci</span><span class="sxs-lookup"><span data-stu-id="1c6d4-202">Null-coalescing operator</span></span>

<span data-ttu-id="1c6d4-203">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-204">[x?? y](null-coalescing-operator.md) – döndürür `x` olmayan ise`null`; Aksi halde döndürür `y`.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-204">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="1c6d4-205">Koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="1c6d4-205">Conditional operator</span></span>

<span data-ttu-id="1c6d4-206">Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-206">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-207">[t? x: y](conditional-operator.md) – test `t` true, ardından değerlendirilip döndürülecek değerlendirir `x`; Aksi takdirde, değerlendirilip döndürülecek `y`.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-207">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="1c6d4-208">Atama ve lambda işleçleri</span><span class="sxs-lookup"><span data-stu-id="1c6d4-208">Assignment and lambda operators</span></span>

<span data-ttu-id="1c6d4-209">Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-209">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1c6d4-210">[x = y](assignment-operator.md) – atama.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-210">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="1c6d4-211">[x += y](arithmetic-operators.md#compound-assignment) – artırma.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-211">[x += y](arithmetic-operators.md#compound-assignment) – increment.</span></span> <span data-ttu-id="1c6d4-212">Değerini ekleme `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-212">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="1c6d4-213">Varsa `x` atayan bir [olay](../keywords/event.md), ardından `y` uygun bir yöntem olmalı, C# bir olay işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-213">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# adds as an event handler.</span></span>

<span data-ttu-id="1c6d4-214">[x-= y](arithmetic-operators.md#compound-assignment) – azaltma.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-214">[x -= y](arithmetic-operators.md#compound-assignment) – decrement.</span></span> <span data-ttu-id="1c6d4-215">Değerini çıkarma `y` değerinden `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-215">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="1c6d4-216">Varsa `x` atayan bir [olay](../keywords/event.md), ardından `y` uygun bir yöntem olmalı, C# bir olay işleyicisi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-216">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# removes as an event handler.</span></span>

<span data-ttu-id="1c6d4-217">[x \* y =](arithmetic-operators.md#compound-assignment) – çarpma atama.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-217">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="1c6d4-218">Çarp değeri `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-218">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1c6d4-219">[x / y =](arithmetic-operators.md#compound-assignment) – bölme ataması.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-219">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="1c6d4-220">Değerini ayırmak `x` değeriyle `y`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-220">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1c6d4-221">[%x y =](arithmetic-operators.md#compound-assignment) – kalanını atama.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-221">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="1c6d4-222">Değerini ayırmak `x` değeriyle `y`, kalanı depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-222">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="1c6d4-223">[x & y =](boolean-logical-operators.md#compound-assignment) – ve atama.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="1c6d4-224">DEĞERİ `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-224">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1c6d4-225">[x &#124;y =](boolean-logical-operators.md#compound-assignment) – OR ataması.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="1c6d4-226">YA da değerini `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-226">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1c6d4-227">[x ^ y =](boolean-logical-operators.md#compound-assignment) – XOR atama.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="1c6d4-228">XOR değeri, `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-228">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1c6d4-229">[x << y =](bitwise-and-shift-operators.md#compound-assignment) – sola kaydırma ataması.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="1c6d4-230">Değerini kaydırma `x` sol tarafından `y` yerde depolamak sonucunda `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-230">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1c6d4-231">[x >> y =](bitwise-and-shift-operators.md#compound-assignment) – sağa kaydırma ataması.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="1c6d4-232">Değerini kaydırma `x` sağa `y` yerde depolamak sonucunda `x`ve yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-232">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1c6d4-233">[=>](lambda-operator.md) – lambda bildirimi.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-233">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c6d4-234">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c6d4-234">See also</span></span>

- [<span data-ttu-id="1c6d4-235">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1c6d4-235">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1c6d4-236">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1c6d4-236">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1c6d4-237">C#</span><span class="sxs-lookup"><span data-stu-id="1c6d4-237">C#</span></span>](../../index.md)
- [<span data-ttu-id="1c6d4-238">Fazla yüklenebilir işleçler</span><span class="sxs-lookup"><span data-stu-id="1c6d4-238">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="1c6d4-239">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1c6d4-239">C# Keywords</span></span>](../keywords/index.md)
