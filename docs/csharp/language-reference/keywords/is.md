---
title: İş - C# başvurusu
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 45e37dcb15e178fe37907e00cc14ef48c1bf230d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306588"
---
# <a name="is-c-reference"></a><span data-ttu-id="6fe22-102">is (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6fe22-102">is (C# Reference)</span></span>

<span data-ttu-id="6fe22-103">`is` İşleci denetleyen bir ifade sonucunu belirli bir tür ile uyumlu olup olmadığını veya (başlayarak C# 7.0) belirli bir desene göre bir ifade eder.</span><span class="sxs-lookup"><span data-stu-id="6fe22-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="6fe22-104">Tür testi hakkında bilgi için `is` işleci bakın [işleci](../operators/type-testing-and-conversion-operators.md#is-operator) bölümünü [türünü test etme ve dönüştürme işleçleri](../operators/type-testing-and-conversion-operators.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="6fe22-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-conversion-operators.md#is-operator) section of the [Type-testing and conversion operators](../operators/type-testing-and-conversion-operators.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="6fe22-105">İle desen eşleştirme `is`</span><span class="sxs-lookup"><span data-stu-id="6fe22-105">Pattern matching with `is`</span></span>

<span data-ttu-id="6fe22-106">C# 7.0 ile başlayan `is` ve [geçiş](switch.md) ifadeleri desen eşleştirme desteği.</span><span class="sxs-lookup"><span data-stu-id="6fe22-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="6fe22-107">`is` Anahtar sözcüğü aşağıdaki düzenini destekler:</span><span class="sxs-lookup"><span data-stu-id="6fe22-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="6fe22-108">[Tür deseni](#type-pattern), bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve, olabilir, bu türden bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="6fe22-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="6fe22-109">[Sabit desen](#constant-pattern), belirtilen bir sabit değer için bir ifadeyi değerlendirir olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="6fe22-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="6fe22-110">[değişken desen](#var-pattern), her zaman yeni bir yerel değişken bir ifadenin değerine bağlar ve başarılı bir eşleşme.</span><span class="sxs-lookup"><span data-stu-id="6fe22-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="6fe22-111">Tür deseni</span><span class="sxs-lookup"><span data-stu-id="6fe22-111">Type pattern</span></span>

<span data-ttu-id="6fe22-112">Desen eşleştirme, gerçekleştirmek için tür deseni kullanılırken `is` bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve bu olabilir, bu türden bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="6fe22-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="6fe22-113">Basit bir uzantısıdır `is` kısa türü değerlendirme ve dönüştürme sağlayan deyimi.</span><span class="sxs-lookup"><span data-stu-id="6fe22-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="6fe22-114">Genel formu `is` türü modelidir:</span><span class="sxs-lookup"><span data-stu-id="6fe22-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="6fe22-115">Burada *expr* bazı türünde bir örnek için değerlendirilen bir ifade olan *türü* türün adı sonucunu *expr* Boolean'a dönüştürülecek ve *varname* hangi nesne sonucu *expr* aralığındaysa dönüştürülür `is` test `true`.</span><span class="sxs-lookup"><span data-stu-id="6fe22-115">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="6fe22-116">`is` İfade `true` varsa *expr* değil `null`, ve aşağıdakilerden birini doğrudur:</span><span class="sxs-lookup"><span data-stu-id="6fe22-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="6fe22-117">*Expr* örneği aynı türde olan *türü*.</span><span class="sxs-lookup"><span data-stu-id="6fe22-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="6fe22-118">*Expr* türetilen türün bir örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="6fe22-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="6fe22-119">Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.</span><span class="sxs-lookup"><span data-stu-id="6fe22-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="6fe22-120">*Expr* temel bir sınıfı olan bir derleme zamanı türü sahip *türü*, ve *expr* sahip olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*.</span><span class="sxs-lookup"><span data-stu-id="6fe22-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="6fe22-121">*Derleme zamanı tür* değişkeninin Değişken bildiriminde tanımlanan türüdür.</span><span class="sxs-lookup"><span data-stu-id="6fe22-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="6fe22-122">*Çalışma zamanı türü* bir değişken, bu değişkene atanan örnek türüdür.</span><span class="sxs-lookup"><span data-stu-id="6fe22-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="6fe22-123">*Expr* uygulayan bir tür örneğidir *türü* arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6fe22-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="6fe22-124">İle başlayarak C# 7.1, *expr* genel tür parametresi kısıtlamaları ile tanımlanan bir derleme zamanı türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6fe22-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="6fe22-125">Varsa *expr* olduğu `true` ve `is` ile kullanılan bir `if` deyimi, *varname* içinde atanan `if` deyimi yalnızca.</span><span class="sxs-lookup"><span data-stu-id="6fe22-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="6fe22-126">Kapsamı *varname* dandır `is` ifade kapsayan blok bitişi `if` deyimi.</span><span class="sxs-lookup"><span data-stu-id="6fe22-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="6fe22-127">Kullanarak *varname* içindeki herhangi bir konumda değil atanmış olan bir değişkenin kullanım için bir derleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6fe22-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="6fe22-128">Aşağıdaki örnekte `is` türün uygulamasını sağlamak üzere tür deseni <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6fe22-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="6fe22-129">Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="6fe22-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="6fe22-130">Kullanım türü desen eşleştirme bir dönüştürmenin sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha kompakt ve okunabilir bir kod oluşturur bir `null`.</span><span class="sxs-lookup"><span data-stu-id="6fe22-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="6fe22-131">`is` Türü desen türü bir değer türü tespit edilirken daha küçük kod ayrıca oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6fe22-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="6fe22-132">Aşağıdaki örnekte `is` türü desen, bir nesne olup olmadığını belirlemek için bir `Person` veya `Dog` uygun bir özelliğin değerini göstermeden önce örneği.</span><span class="sxs-lookup"><span data-stu-id="6fe22-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="6fe22-133">Desen eşleştirme olmadan eşdeğer kod, bir açık tür dönüştürme içeren ayrı bir atama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6fe22-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="6fe22-134">Sabit desen</span><span class="sxs-lookup"><span data-stu-id="6fe22-134">Constant pattern</span></span>

<span data-ttu-id="6fe22-135">Sabit desen ile eşleşen deseni gerçekleştirirken `is` belirtilen sabit bir ifade eşit olup olmadığını test eder.</span><span class="sxs-lookup"><span data-stu-id="6fe22-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="6fe22-136">C# 6 ve önceki sürümleri, sabit desen tarafından desteklenen [geçiş](switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="6fe22-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="6fe22-137">İle başlayarak C# 7.0, onu tarafından desteklenen `is` deyimi de.</span><span class="sxs-lookup"><span data-stu-id="6fe22-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="6fe22-138">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6fe22-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="6fe22-139">Burada *expr* değerlendirmek için ifade ve *sabit* sınamak için değer.</span><span class="sxs-lookup"><span data-stu-id="6fe22-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="6fe22-140">*Sabit* aşağıdaki sabit ifadeler biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="6fe22-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="6fe22-141">Değişmez değer.</span><span class="sxs-lookup"><span data-stu-id="6fe22-141">A literal value.</span></span>

- <span data-ttu-id="6fe22-142">Bildirilen bir adı `const` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="6fe22-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="6fe22-143">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="6fe22-143">An enumeration constant.</span></span>

<span data-ttu-id="6fe22-144">Sabit ifade gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="6fe22-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="6fe22-145">Varsa *expr* ve *sabit* integral türleri, C# eşitlik işlecini ifade döndürüp döndürmediğini belirler `true` (olup, diğer bir deyişle, `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="6fe22-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="6fe22-146">Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6fe22-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="6fe22-147">Aşağıdaki örnek bir nesne olup olmadığını sınamak için tür ve sabit desenler birleştiren bir `Dice` örneği ve ise, belirlemek için bir zar değerini olup 6.</span><span class="sxs-lookup"><span data-stu-id="6fe22-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="6fe22-148">Denetleme `null` sabit deseni kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6fe22-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="6fe22-149">`null` Anahtar sözcüğü tarafından desteklenen `is` deyimi.</span><span class="sxs-lookup"><span data-stu-id="6fe22-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="6fe22-150">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6fe22-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="6fe22-151">Aşağıdaki örnek, bir karşılaştırmasını gösterir `null` denetler:</span><span class="sxs-lookup"><span data-stu-id="6fe22-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="6fe22-152">değişken deseni</span><span class="sxs-lookup"><span data-stu-id="6fe22-152">var pattern</span></span>

<span data-ttu-id="6fe22-153">`var` Herhangi bir türü veya değer için bir catch tüm modelidir.</span><span class="sxs-lookup"><span data-stu-id="6fe22-153">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="6fe22-154">Değerini *expr* derleme zamanı türünü aynı türe her zaman yerel bir değişkene atanan *expr*.</span><span class="sxs-lookup"><span data-stu-id="6fe22-154">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="6fe22-155">Sonucu `is` ifadesidir her zaman `true`.</span><span class="sxs-lookup"><span data-stu-id="6fe22-155">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="6fe22-156">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6fe22-156">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="6fe22-157">Aşağıdaki örnek, bir ifade adlı bir değişkene atayın için değişken deseni kullanır. `obj`.</span><span class="sxs-lookup"><span data-stu-id="6fe22-157">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="6fe22-158">Ardından değerine ve türüne görüntüler `obj`.</span><span class="sxs-lookup"><span data-stu-id="6fe22-158">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="6fe22-159">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6fe22-159">C# language specification</span></span>
  
<span data-ttu-id="6fe22-160">Daha fazla bilgi için [işleci](~/_csharplang/spec/expressions.md#the-is-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md) ve aşağıdaki C# dil teklifleri:</span><span class="sxs-lookup"><span data-stu-id="6fe22-160">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="6fe22-161">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="6fe22-161">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="6fe22-162">Genel türler ile desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="6fe22-162">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="6fe22-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fe22-163">See also</span></span>

- [<span data-ttu-id="6fe22-164">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="6fe22-164">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6fe22-165">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6fe22-165">C# keywords</span></span>](index.md)
- [<span data-ttu-id="6fe22-166">Tür test etme ve dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="6fe22-166">Type-testing and conversion operators</span></span>](../operators/type-testing-and-conversion-operators.md)
