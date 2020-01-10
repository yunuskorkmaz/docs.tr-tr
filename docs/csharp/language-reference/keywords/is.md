---
title: C# başvuru
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 1a1f539e80f8d843f40640fa798cf6122f316a9f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715231"
---
# <a name="is-c-reference"></a><span data-ttu-id="947a1-102">is (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="947a1-102">is (C# Reference)</span></span>

<span data-ttu-id="947a1-103">`is` işleci, bir ifadenin sonucunun verilen türle uyumlu olup olmadığını denetler veya (7,0 ile C# başlayarak) bir ifadeyi bir düzene göre sınar.</span><span class="sxs-lookup"><span data-stu-id="947a1-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="947a1-104">Tür-test `is` işleci hakkında daha fazla bilgi için, [tür-test ve atama işleçleri](../operators/type-testing-and-cast.md) makalesinin [işleç](../operators/type-testing-and-cast.md#is-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="947a1-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="947a1-105">`is` ile eşleşen desenler</span><span class="sxs-lookup"><span data-stu-id="947a1-105">Pattern matching with `is`</span></span>

<span data-ttu-id="947a1-106">7,0 ile C# başlayarak, `is` ve [Switch](switch.md) deyimleri, model eşleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="947a1-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="947a1-107">`is` anahtar sözcüğü aşağıdaki desenleri destekler:</span><span class="sxs-lookup"><span data-stu-id="947a1-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="947a1-108">Bir ifadenin belirtilen türe dönüştürülüp dönüştürülebileceğini test eden [tür stili](#type-pattern), bu, bir ifadenin bu türden bir değişkene dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="947a1-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="947a1-109">Bir ifadenin belirtilen sabit değer olarak değerlendirilip değerlendirilmediğini test eden [sabit bir model](#constant-pattern).</span><span class="sxs-lookup"><span data-stu-id="947a1-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="947a1-110">[var olan model](#var-pattern), her zaman başarılı olan ve bir ifadenin değerini yeni bir yerel değişkene bağlayan bir eşleşme.</span><span class="sxs-lookup"><span data-stu-id="947a1-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="947a1-111">Tür stili</span><span class="sxs-lookup"><span data-stu-id="947a1-111">Type pattern</span></span>

<span data-ttu-id="947a1-112">Model eşleştirmeyi gerçekleştirmek için tür deseninin kullanıldığı zaman `is`, bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülmeyeceğini test eder ve bu şekilde, bu tür bir değişkene bu değeri verebilir.</span><span class="sxs-lookup"><span data-stu-id="947a1-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="947a1-113">Bu, kısa tür değerlendirmesi ve dönüştürmeyi sağlayan `is` deyimin basit bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="947a1-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="947a1-114">`is` Type deseninin genel formu:</span><span class="sxs-lookup"><span data-stu-id="947a1-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="947a1-115">Burada *Expr* , bir türün bir örneğini değerlendiren bir ifadedir, *tür* , *ifadenin* sonucunun dönüştürülecek türün adı, *varname* ise `is` testi `true`olduğunda, *ifadenin* sonucunun dönüştürüldüğü nesnedir.</span><span class="sxs-lookup"><span data-stu-id="947a1-115">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="947a1-116">`is` ifadesi, *expr* `null`değilse `true` ve aşağıdakilerden herhangi biri true 'dur:</span><span class="sxs-lookup"><span data-stu-id="947a1-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="947a1-117">*Expr* , *türü*ile aynı türde bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="947a1-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="947a1-118">*Expr* *türünden*türetilen bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="947a1-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="947a1-119">Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="947a1-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="947a1-120">*ifadenin* *türünde bir*temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* *veya türünden türetilmiş*bir çalışma zamanı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="947a1-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="947a1-121">Bir değişkenin *derleme zamanı türü* , bildiriminde tanımlanan değişkenin türüdür.</span><span class="sxs-lookup"><span data-stu-id="947a1-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="947a1-122">Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.</span><span class="sxs-lookup"><span data-stu-id="947a1-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="947a1-123">*Expr* , *tür* arabirimini uygulayan bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="947a1-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="947a1-124">7,1 ile C# başlayarak, *Expr* genel bir tür parametresi ve kısıtlamaları tarafından tanımlanan bir derleme zamanı türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="947a1-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="947a1-125">*Expr* `true` ve `is` bir `if` ifadesiyle kullanılırsa, *varname* yalnızca `if` ifadesinde atanır.</span><span class="sxs-lookup"><span data-stu-id="947a1-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="947a1-126">*Varname* kapsamı `is` ifadeden `if` deyimini kapsayan bloğun sonuna kadar olur.</span><span class="sxs-lookup"><span data-stu-id="947a1-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="947a1-127">Başka bir konumda *varname* kullanılması atanmamış bir değişkenin kullanımı için derleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="947a1-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="947a1-128">Aşağıdaki örnek, bir türün <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yönteminin uygulanmasını sağlamak için `is` tür modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="947a1-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="947a1-129">Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="947a1-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="947a1-130">Tür deseninin kullanımı, dönüştürmenin sonucunun `null`olup olmadığını test etme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir.</span><span class="sxs-lookup"><span data-stu-id="947a1-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="947a1-131">`is` tür deseninin değeri, bir değer türünün türü belirlenirken daha Compact kod da üretir.</span><span class="sxs-lookup"><span data-stu-id="947a1-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="947a1-132">Aşağıdaki örnek, uygun bir özelliğin değerini görüntülemeden önce bir nesnenin `Person` mi yoksa bir `Dog` örneği mi olduğunu anlamak için `is` tür modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="947a1-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="947a1-133">Desenler eşleşmesi olmayan eşdeğer kod, açık bir dönüştürme içeren ayrı bir atama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="947a1-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="947a1-134">Sabit model</span><span class="sxs-lookup"><span data-stu-id="947a1-134">Constant pattern</span></span>

<span data-ttu-id="947a1-135">Sabit örüntüyle eşleşen desenler gerçekleştirirken, bir ifadenin belirtilen bir sabit değere eşit olup olmadığını sınar `is`.</span><span class="sxs-lookup"><span data-stu-id="947a1-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="947a1-136">C# 6 ve önceki sürümlerde, sabit model [Switch](switch.md) ifadesiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="947a1-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="947a1-137">7,0 ' C# den başlayarak `is` bildiri de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="947a1-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="947a1-138">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="947a1-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="947a1-139">Burada *Expr* , değerlendirilecek ifadedir ve *sabitin* test edilecek değerdir.</span><span class="sxs-lookup"><span data-stu-id="947a1-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="947a1-140">*sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="947a1-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="947a1-141">Değişmez değer.</span><span class="sxs-lookup"><span data-stu-id="947a1-141">A literal value.</span></span>

- <span data-ttu-id="947a1-142">Belirtilen bir `const` değişkeninin adı.</span><span class="sxs-lookup"><span data-stu-id="947a1-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="947a1-143">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="947a1-143">An enumeration constant.</span></span>

<span data-ttu-id="947a1-144">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="947a1-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="947a1-145">*Expr* ve *Constant* integral türse, C# eşitlik işleci ifadenin `true` (yani `expr == constant`) döndürüp döndürmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="947a1-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="947a1-146">Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="947a1-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="947a1-147">Aşağıdaki örnek, bir nesnenin `Dice` bir örnek olup olmadığını test etmek için tür ve sabit desenleri, bir zar rulosu değerinin 6 olup olmadığını anlamak için birleştirir.</span><span class="sxs-lookup"><span data-stu-id="947a1-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="947a1-148">`null` denetimi, sabit model kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="947a1-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="947a1-149">`null` anahtar sözcüğü `is` ifadesiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="947a1-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="947a1-150">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="947a1-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="947a1-151">Aşağıdaki örnekte `null` denetimlerinin karşılaştırması gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="947a1-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="947a1-152">var deseninin</span><span class="sxs-lookup"><span data-stu-id="947a1-152">var pattern</span></span>

<span data-ttu-id="947a1-153">`var` model her tür veya değer için bir catch-all ' dır.</span><span class="sxs-lookup"><span data-stu-id="947a1-153">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="947a1-154">*Expr* 'nin değeri her zaman bir yerel değişkene, aynı türde *Expr*'nin derleme zamanı türüyle atanır.</span><span class="sxs-lookup"><span data-stu-id="947a1-154">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="947a1-155">`is` ifadesinin sonucu her zaman `true`.</span><span class="sxs-lookup"><span data-stu-id="947a1-155">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="947a1-156">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="947a1-156">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="947a1-157">Aşağıdaki örnek, `obj`adlı bir değişkene bir ifade atamak için var modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="947a1-157">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="947a1-158">Sonra değeri ve `obj`türünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="947a1-158">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="947a1-159">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="947a1-159">C# language specification</span></span>
  
<span data-ttu-id="947a1-160">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) ve aşağıdaki C# dil tekliflerinin [işleç](~/_csharplang/spec/expressions.md#the-is-operator) bölümüne bakın:</span><span class="sxs-lookup"><span data-stu-id="947a1-160">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="947a1-161">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="947a1-161">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="947a1-162">Genel türler ile desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="947a1-162">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="947a1-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="947a1-163">See also</span></span>

- [<span data-ttu-id="947a1-164">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="947a1-164">C# reference</span></span>](../index.md)
- [<span data-ttu-id="947a1-165">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="947a1-165">C# keywords</span></span>](index.md)
- [<span data-ttu-id="947a1-166">Tür testi ve atama işleçleri</span><span class="sxs-lookup"><span data-stu-id="947a1-166">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
