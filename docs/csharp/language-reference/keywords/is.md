---
description: -C# başvurusu
title: -C# başvurusu
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 3508f08857f88fd34478f968a71bae0121d54d1c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134516"
---
# <a name="is-c-reference"></a><span data-ttu-id="a2db2-103">is (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a2db2-103">is (C# Reference)</span></span>

<span data-ttu-id="a2db2-104">`is`İşleci, bir ifadenin sonucunun verilen türle uyumlu olup olmadığını denetler veya (C# 7,0 ' den itibaren) bir ifadeyi bir düzene göre sınar.</span><span class="sxs-lookup"><span data-stu-id="a2db2-104">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="a2db2-105">Tür testi işleci hakkında daha fazla bilgi için, `is` [tür-test ve atama işleçleri](../operators/type-testing-and-cast.md) makalesinin [işleç](../operators/type-testing-and-cast.md#is-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a2db2-105">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="a2db2-106">İle eşleşen desenler `is`</span><span class="sxs-lookup"><span data-stu-id="a2db2-106">Pattern matching with `is`</span></span>

<span data-ttu-id="a2db2-107">C# 7,0 ile başlayarak, `is` ve [Switch](switch.md) deyimleri, model eşleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="a2db2-107">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="a2db2-108">`is`Anahtar sözcüğü aşağıdaki desenleri destekler:</span><span class="sxs-lookup"><span data-stu-id="a2db2-108">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="a2db2-109">Bir ifadenin belirtilen türe dönüştürülüp dönüştürülebileceğini test eden [tür stili](#type-pattern), bu, bir ifadenin bu türden bir değişkene dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2db2-109">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="a2db2-110">Bir ifadenin belirtilen sabit değer olarak değerlendirilip değerlendirilmediğini test eden [sabit bir model](#constant-pattern).</span><span class="sxs-lookup"><span data-stu-id="a2db2-110">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="a2db2-111">[var olan model](#var-pattern), her zaman başarılı olan ve bir ifadenin değerini yeni bir yerel değişkene bağlayan bir eşleşme.</span><span class="sxs-lookup"><span data-stu-id="a2db2-111">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="a2db2-112">Tür stili</span><span class="sxs-lookup"><span data-stu-id="a2db2-112">Type pattern</span></span>

<span data-ttu-id="a2db2-113">Model eşleştirmeyi gerçekleştirmek için tür modelini kullanırken, `is` bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülebileceğini ve bu türden bir değişkene bir değişken verip etmediğini test eder.</span><span class="sxs-lookup"><span data-stu-id="a2db2-113">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="a2db2-114">Bu, `is` kısa tür değerlendirmesi ve dönüştürmeyi sağlayan deyimin basit bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="a2db2-114">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="a2db2-115">`is`Tür deseninin genel formu:</span><span class="sxs-lookup"><span data-stu-id="a2db2-115">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="a2db2-116">Burada *Expr* , bir türün bir örneğini değerlendiren bir ifadedir, *tür* , *ifadenin* sonucunun dönüştürülecek türün adı ve *varname* , test ise *ifadenin* sonucunun dönüştürülebileceği nesnedir `is` `true` .</span><span class="sxs-lookup"><span data-stu-id="a2db2-116">Where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span>

<span data-ttu-id="a2db2-117">`is`İfade, `true` *Expr* değilse `null` ve aşağıdakilerden herhangi biri doğru ise geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="a2db2-117">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="a2db2-118">*Expr* , *türü*ile aynı türde bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-118">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="a2db2-119">*Expr* *türünden*türetilen bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-119">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="a2db2-120">Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-120">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="a2db2-121">*ifadenin* *türünde bir*temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* *veya türünden türetilmiş*bir çalışma zamanı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="a2db2-121">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="a2db2-122">Bir değişkenin *derleme zamanı türü* , bildiriminde tanımlanan değişkenin türüdür.</span><span class="sxs-lookup"><span data-stu-id="a2db2-122">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="a2db2-123">Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.</span><span class="sxs-lookup"><span data-stu-id="a2db2-123">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="a2db2-124">*Expr* , *tür* arabirimini uygulayan bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-124">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="a2db2-125">C# 7,1 ile başlayarak, *Expr* genel bir tür parametresi ve kısıtlamaları tarafından tanımlanan bir derleme zamanı türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-125">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="a2db2-126">*Expr* ise `true` ve `is` bir ifadesiyle birlikte kullanılırsa `if` , *varname* `if` yalnızca deyimin içinde atanır.</span><span class="sxs-lookup"><span data-stu-id="a2db2-126">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="a2db2-127">*Varname* kapsamı, `is` ifadeden deyimi kapsayan bloğun sonuna kadar olur `if` .</span><span class="sxs-lookup"><span data-stu-id="a2db2-127">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="a2db2-128">Başka bir konumda *varname* kullanılması atanmamış bir değişkenin kullanımı için derleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2db2-128">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="a2db2-129">Aşağıdaki örnek, `is` bir türün yönteminin uygulanmasını sağlamak için tür modelini kullanır <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a2db2-129">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="a2db2-130">Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-130">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="a2db2-131">Tür deseninin kullanımı, dönüştürmenin sonucunun bir olup olmadığını test etme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir `null` .</span><span class="sxs-lookup"><span data-stu-id="a2db2-131">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="a2db2-132">`is`Tür deseninin de bir değer türünün türü belirlenirken daha kompakt kod üretir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-132">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="a2db2-133">Aşağıdaki örnek, uygun bir `is` `Person` `Dog` özelliğin değerini görüntülemeden önce bir nesnenin bir mi yoksa bir örnek mi olduğunu anlamak için tür modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a2db2-133">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="a2db2-134">Desenler eşleşmesi olmayan eşdeğer kod, açık bir dönüştürme içeren ayrı bir atama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-134">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="a2db2-135">Sabit model</span><span class="sxs-lookup"><span data-stu-id="a2db2-135">Constant pattern</span></span>

<span data-ttu-id="a2db2-136">Sabit örüntüyle eşleşen desenler gerçekleştirirken, `is` bir ifadenin belirtilen bir sabit değere eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="a2db2-136">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="a2db2-137">C# 6 ve önceki sürümlerinde, sabit model [Switch](switch.md) ifadesiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-137">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="a2db2-138">C# 7,0 ' den başlayarak, bu ifade da desteklenir `is` .</span><span class="sxs-lookup"><span data-stu-id="a2db2-138">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="a2db2-139">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="a2db2-139">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="a2db2-140">Burada *Expr* , değerlendirilecek ifadedir ve *sabitin* test edilecek değerdir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-140">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="a2db2-141">*sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="a2db2-141">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="a2db2-142">Değişmez değer.</span><span class="sxs-lookup"><span data-stu-id="a2db2-142">A literal value.</span></span>

- <span data-ttu-id="a2db2-143">Belirtilen `const` değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="a2db2-143">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="a2db2-144">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="a2db2-144">An enumeration constant.</span></span>

<span data-ttu-id="a2db2-145">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="a2db2-145">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="a2db2-146">*Expr* ve *Constant* Integral türse, C# eşitlik işleci ifadenin döndürülüp döndürülmeyeceğini `true` (yani, ne gibi `expr == constant` ) belirler.</span><span class="sxs-lookup"><span data-stu-id="a2db2-146">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="a2db2-147">Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-147">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="a2db2-148">Aşağıdaki örnek, bir nesnenin bir örnek olup olmadığını test etmek için tür ve sabit desenleri `Dice` ve bir zar rulosu değerinin 6 olup olmadığını anlamak için birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-148">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="a2db2-149">İçin Denetim `null` , sabit model kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-149">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="a2db2-150">`null`Anahtar sözcüğü, `is` ifadesiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-150">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="a2db2-151">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="a2db2-151">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="a2db2-152">Aşağıdaki örnek, denetimlerin karşılaştırmasını gösterir `null` :</span><span class="sxs-lookup"><span data-stu-id="a2db2-152">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="a2db2-153">var deseninin</span><span class="sxs-lookup"><span data-stu-id="a2db2-153">var pattern</span></span>

<span data-ttu-id="a2db2-154">Desenli bir model eşleşmesi `var` her zaman başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="a2db2-154">A pattern match with the `var` pattern always succeeds.</span></span> <span data-ttu-id="a2db2-155">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="a2db2-155">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="a2db2-156">Burada, *ifadenin* değeri her zaman *varname*adlı bir yerel değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="a2db2-156">Where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="a2db2-157">*varname* , *Expr*'nin derleme zamanı türüyle aynı türde bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-157">*varname* is a variable of the same type as the compile-time type of *expr*.</span></span>

<span data-ttu-id="a2db2-158">Eğer *expr* ifadesi olarak değerlendirilirse `null` , `is` ifade, `true` `null` *varname*öğesini üretir ve atar.</span><span class="sxs-lookup"><span data-stu-id="a2db2-158">If *expr* evaluates to `null`, the `is` expression produces `true` and assigns `null` to *varname*.</span></span> <span data-ttu-id="a2db2-159">Var olan model, `is` `true` bir değer için üreten birkaç kullanımdır `null` .</span><span class="sxs-lookup"><span data-stu-id="a2db2-159">The var pattern is one of the few uses of `is` that produces `true` for a `null` value.</span></span>

<span data-ttu-id="a2db2-160">`var`Aşağıdaki örnekte gösterildiği gibi, bir Boolean ifadesinde geçici bir değişken oluşturmak için, bu kalıbı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a2db2-160">You can use the `var` pattern to create a temporary variable within a Boolean expression, as the following example shows:</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="a2db2-161">Önceki örnekte, geçici değişken pahalı bir işlemin sonucunu depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2db2-161">In the preceding example, the temporary variable is used to store the result of an expensive operation.</span></span> <span data-ttu-id="a2db2-162">Değişken daha sonra birden çok kez kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2db2-162">The variable can then be used multiple times.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a2db2-163">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a2db2-163">C# language specification</span></span>
  
<span data-ttu-id="a2db2-164">Daha fazla bilgi için [c# dil belirtiminin](~/_csharplang/spec/introduction.md) ve aşağıdaki c# dil tekliflerinin [, bkz.:](~/_csharplang/spec/expressions.md#the-is-operator)</span><span class="sxs-lookup"><span data-stu-id="a2db2-164">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="a2db2-165">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="a2db2-165">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="a2db2-166">Genel türler ile desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="a2db2-166">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="a2db2-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2db2-167">See also</span></span>

- [<span data-ttu-id="a2db2-168">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a2db2-168">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a2db2-169">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a2db2-169">C# keywords</span></span>](index.md)
- [<span data-ttu-id="a2db2-170">Tür testi ve atama işleçleri</span><span class="sxs-lookup"><span data-stu-id="a2db2-170">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
