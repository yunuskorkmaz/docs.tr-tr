---
title: C# başvuru
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: a04105137fad7cd3a25b869c3aa7fcbe91ed20ab
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566314"
---
# <a name="is-c-reference"></a><span data-ttu-id="85913-102">is (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="85913-102">is (C# Reference)</span></span>

<span data-ttu-id="85913-103">İşleci, bir ifadenin sonucunun verilen türle uyumlu olup olmadığını denetler veya (7,0 ile C# başlayarak) bir ifadeyi bir düzene göre sınar. `is`</span><span class="sxs-lookup"><span data-stu-id="85913-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="85913-104">Tür testi `is` işleci hakkında daha fazla bilgi için, [tür-test ve atama işleçleri](../operators/type-testing-and-cast.md) makalesinin [işleç](../operators/type-testing-and-cast.md#is-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="85913-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="85913-105">İle eşleşen desenler`is`</span><span class="sxs-lookup"><span data-stu-id="85913-105">Pattern matching with `is`</span></span>

<span data-ttu-id="85913-106">7,0 ile C# başlayarak, `is` ve [Switch](switch.md) deyimleri, model eşleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="85913-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="85913-107">`is` Anahtar sözcüğü aşağıdaki desenleri destekler:</span><span class="sxs-lookup"><span data-stu-id="85913-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="85913-108">Bir ifadenin belirtilen türe dönüştürülüp dönüştürülebileceğini test eden [tür stili](#type-pattern), bu, bir ifadenin bu türden bir değişkene dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="85913-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="85913-109">Bir ifadenin belirtilen sabit değer olarak değerlendirilip değerlendirilmediğini test eden [sabit bir model](#constant-pattern).</span><span class="sxs-lookup"><span data-stu-id="85913-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="85913-110">[var olan model](#var-pattern), her zaman başarılı olan ve bir ifadenin değerini yeni bir yerel değişkene bağlayan bir eşleşme.</span><span class="sxs-lookup"><span data-stu-id="85913-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="85913-111">Tür stili</span><span class="sxs-lookup"><span data-stu-id="85913-111">Type pattern</span></span>

<span data-ttu-id="85913-112">Model eşleştirmeyi gerçekleştirmek için tür modelini kullanırken, `is` bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülebileceğini ve bu türden bir değişkene bir değişken verip etmediğini test eder.</span><span class="sxs-lookup"><span data-stu-id="85913-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="85913-113">Bu, `is` kısa tür değerlendirmesi ve dönüştürmeyi sağlayan deyimin basit bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="85913-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="85913-114">`is` Tür deseninin genel formu:</span><span class="sxs-lookup"><span data-stu-id="85913-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="85913-115">Burada *Expr* , bir türün bir örneğini değerlendiren bir ifadedir, *tür* , *Expr* 'nin sonucunun dönüştürülecek türün adı, *varname* ise *ifadenin* sonucunun dönüştürüldüğü nesne, `is` test .`true`</span><span class="sxs-lookup"><span data-stu-id="85913-115">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="85913-116">İfade, Expr`null`değilse ve aşağıdakilerden herhangi biri doğru ise geçerlidir: `is` `true`</span><span class="sxs-lookup"><span data-stu-id="85913-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="85913-117">*Expr* , *türü*ile aynı türde bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="85913-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="85913-118">*Expr* *türünden*türetilen bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="85913-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="85913-119">Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="85913-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="85913-120">*ifadenin* türünde bir temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* veya türünden türetilmiş bir çalışma zamanı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="85913-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="85913-121">Bir değişkenin *derleme zamanı türü* , bildiriminde tanımlanan değişkenin türüdür.</span><span class="sxs-lookup"><span data-stu-id="85913-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="85913-122">Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.</span><span class="sxs-lookup"><span data-stu-id="85913-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="85913-123">*Expr* , *tür* arabirimini uygulayan bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="85913-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="85913-124">7,1 ile C# başlayarak, *Expr* genel bir tür parametresi ve kısıtlamaları tarafından tanımlanan bir derleme zamanı türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="85913-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="85913-125">*Expr* ise `true` ve `is` bir `if` ifadesiyle birlikte kullanılırsa, varname yalnızca deyimin içinde atanır. `if`</span><span class="sxs-lookup"><span data-stu-id="85913-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="85913-126">*Varname* kapsamı, `is` ifadeden `if` deyimi kapsayan bloğun sonuna kadar olur.</span><span class="sxs-lookup"><span data-stu-id="85913-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="85913-127">Başka bir konumda *varname* kullanılması atanmamış bir değişkenin kullanımı için derleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85913-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="85913-128">Aşağıdaki örnek, bir `is` <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> türün yönteminin uygulanmasını sağlamak için tür modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="85913-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="85913-129">Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="85913-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="85913-130">Tür deseninin kullanımı, dönüştürmenin sonucunun bir `null`olup olmadığını test etme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir.</span><span class="sxs-lookup"><span data-stu-id="85913-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="85913-131">`is` Tür deseninin de bir değer türünün türü belirlenirken daha kompakt kod üretir.</span><span class="sxs-lookup"><span data-stu-id="85913-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="85913-132">Aşağıdaki örnek, uygun bir `is` özelliğin değerini görüntülemeden önce bir nesnenin bir `Person` mi `Dog` yoksa bir örnek mi olduğunu anlamak için tür modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="85913-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="85913-133">Desenler eşleşmesi olmayan eşdeğer kod, açık bir dönüştürme içeren ayrı bir atama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="85913-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="85913-134">Sabit model</span><span class="sxs-lookup"><span data-stu-id="85913-134">Constant pattern</span></span>

<span data-ttu-id="85913-135">Sabit örüntüyle eşleşen desenler gerçekleştirirken, `is` bir ifadenin belirtilen bir sabit değere eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="85913-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="85913-136">C# 6 ve önceki sürümlerde, sabit model [Switch](switch.md) ifadesiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="85913-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="85913-137">7,0 ' C# den başlayarak, bu, `is` bildiri tarafından da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="85913-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="85913-138">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="85913-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="85913-139">Burada *Expr* , değerlendirilecek ifadedir ve *sabitin* test edilecek değerdir.</span><span class="sxs-lookup"><span data-stu-id="85913-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="85913-140">*sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="85913-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="85913-141">Değişmez değer.</span><span class="sxs-lookup"><span data-stu-id="85913-141">A literal value.</span></span>

- <span data-ttu-id="85913-142">Belirtilen `const` değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="85913-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="85913-143">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="85913-143">An enumeration constant.</span></span>

<span data-ttu-id="85913-144">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="85913-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="85913-145">Eğer *Expr* ve *Constant* integral türse, C# eşitlik işleci ifadenin döndürülüp döndürülmeyeceğini `true` (yani, `expr == constant`ne olduğunu) belirler.</span><span class="sxs-lookup"><span data-stu-id="85913-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="85913-146">Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="85913-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="85913-147">Aşağıdaki örnek, bir nesnenin bir `Dice` örnek olup olmadığını test etmek için tür ve sabit desenleri ve bir zar rulosu değerinin 6 olup olmadığını anlamak için birleştirir.</span><span class="sxs-lookup"><span data-stu-id="85913-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="85913-148">İçin `null` denetim, sabit model kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="85913-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="85913-149">Anahtar sözcüğü, `is` ifadesiyle desteklenir. `null`</span><span class="sxs-lookup"><span data-stu-id="85913-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="85913-150">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="85913-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="85913-151">Aşağıdaki örnek, `null` denetimlerin karşılaştırmasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="85913-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="85913-152">var deseninin</span><span class="sxs-lookup"><span data-stu-id="85913-152">var pattern</span></span>

<span data-ttu-id="85913-153">Bu `var` , herhangi bir tür veya değer için bir catch-all ' dır.</span><span class="sxs-lookup"><span data-stu-id="85913-153">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="85913-154">*Expr* 'nin değeri her zaman bir yerel değişkene, aynı türde *Expr*'nin derleme zamanı türüyle atanır.</span><span class="sxs-lookup"><span data-stu-id="85913-154">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="85913-155">`is` İfadenin sonucu her zaman `true`olur.</span><span class="sxs-lookup"><span data-stu-id="85913-155">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="85913-156">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="85913-156">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="85913-157">Aşağıdaki örnek, adlı `obj`bir değişkene bir ifade atamak için var modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="85913-157">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="85913-158">Daha sonra değerini ve türünü `obj`görüntüler.</span><span class="sxs-lookup"><span data-stu-id="85913-158">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="85913-159">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="85913-159">C# language specification</span></span>
  
<span data-ttu-id="85913-160">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) ve aşağıdaki C# dil tekliflerinin [işleç](~/_csharplang/spec/expressions.md#the-is-operator) bölümüne bakın:</span><span class="sxs-lookup"><span data-stu-id="85913-160">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="85913-161">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="85913-161">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="85913-162">Genel türler ile desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="85913-162">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="85913-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85913-163">See also</span></span>

- [<span data-ttu-id="85913-164">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="85913-164">C# reference</span></span>](../index.md)
- [<span data-ttu-id="85913-165">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="85913-165">C# keywords</span></span>](index.md)
- [<span data-ttu-id="85913-166">Tür testi ve atama işleçleri</span><span class="sxs-lookup"><span data-stu-id="85913-166">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
