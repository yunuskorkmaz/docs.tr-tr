---
title: is - C# Referans
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: e64b690482419963a92764b2c97a42dbb231fbfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399639"
---
# <a name="is-c-reference"></a><span data-ttu-id="e063a-102">is (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e063a-102">is (C# Reference)</span></span>

<span data-ttu-id="e063a-103">İşleç, `is` bir ifadenin sonucunun belirli bir türle uyumlu olup olmadığını denetler veya (C# 7.0 ile başlayarak) bir ifadeyi desenle test eder.</span><span class="sxs-lookup"><span data-stu-id="e063a-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="e063a-104">Tür testi `is` işleci hakkında daha fazla bilgi [için, Tür testi ve döküm işleçleri](../operators/type-testing-and-cast.md) makalesinin [operatör](../operators/type-testing-and-cast.md#is-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e063a-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="e063a-105">Desen ile eşleşen`is`</span><span class="sxs-lookup"><span data-stu-id="e063a-105">Pattern matching with `is`</span></span>

<span data-ttu-id="e063a-106">C# 7.0 ile `is` başlayarak, ve [anahtar](switch.md) ifadeleri deseni eşleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="e063a-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="e063a-107">Anahtar `is` kelime aşağıdaki desenleri destekler:</span><span class="sxs-lookup"><span data-stu-id="e063a-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="e063a-108">Bir ifadenin belirli bir türe dönüştürülüp dönüştürülemeyeceğini sınayan ve olabilirse, bu tür bir değişkene dönüştüren [tür deseni.](#type-pattern)</span><span class="sxs-lookup"><span data-stu-id="e063a-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="e063a-109">Bir ifadenin belirli bir sabit değere değerlendirilip değerlendirmediğini sınayan [sabit desen.](#constant-pattern)</span><span class="sxs-lookup"><span data-stu-id="e063a-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="e063a-110">[var deseni,](#var-pattern)her zaman başarılı olan ve bir ifadenin değerini yeni bir yerel değişkene bağlayan bir eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="e063a-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="e063a-111">Tür deseni</span><span class="sxs-lookup"><span data-stu-id="e063a-111">Type pattern</span></span>

<span data-ttu-id="e063a-112">Desen eşleştirmesini gerçekleştirmek için tür `is` deseni kullanırken, bir ifadenin belirli bir türe dönüştürülüp dönüştürülemeyeceğini sınar ve olabilirse, bu tür bir değişkene dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e063a-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="e063a-113">Kısa tür değerlendirmesi ve `is` dönüştürme sağlayan ifadenin basit bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="e063a-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="e063a-114">Tür deseninin `is` genel biçimi:</span><span class="sxs-lookup"><span data-stu-id="e063a-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="e063a-115">*Expr'ın* bazı türde bir örneği değerlendiren bir ifade olduğu durumlarda, *tür,* *expr* sonucunun dönüştürüldüğü türün adıdır ve *varname,* `is` test ise *expr* sonucunun dönüştürüldüğü `true`nesnedir.</span><span class="sxs-lookup"><span data-stu-id="e063a-115">Where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span>

<span data-ttu-id="e063a-116">`is` İfade, `true` *expr* değilse `null`ve aşağıdakilerden herhangi biri doğrudur:</span><span class="sxs-lookup"><span data-stu-id="e063a-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="e063a-117">*expr* *türü*olarak aynı türde bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e063a-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="e063a-118">*expr* *türünden*türetilen bir tür örneğidir.</span><span class="sxs-lookup"><span data-stu-id="e063a-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="e063a-119">Başka bir deyişle, *expr* sonucu *türü*bir örnek için upcast olabilir.</span><span class="sxs-lookup"><span data-stu-id="e063a-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="e063a-120">*expr* *türü*bir taban sınıf olan bir derleme-zaman türü vardır ve *expr* *türü* veya *türünden*türetilen bir çalışma zamanı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="e063a-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="e063a-121">Bir değişkenin *derleme zamanı türü,* değişkenin bildiriminde tanımlandığı şekilde türüdür.</span><span class="sxs-lookup"><span data-stu-id="e063a-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="e063a-122">Bir değişkenin *çalışma zamanı türü,* bu değişkene atanan örneğin türüdür.</span><span class="sxs-lookup"><span data-stu-id="e063a-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="e063a-123">*expr* *türü* arabirimi uygulayan bir tür örneğidir.</span><span class="sxs-lookup"><span data-stu-id="e063a-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="e063a-124">C# 7.1 ile başlayarak, *expr* genel bir tür parametresi ve kısıtlamaları tarafından tanımlanan bir derleme-zaman türü ne olabilir.</span><span class="sxs-lookup"><span data-stu-id="e063a-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="e063a-125">*Expr* bir `true` `if` `is` deyimle kullanılıyorsa ve deyimle `if` kullanılıyorsa, *varname* yalnızca deyim içinde atanır.</span><span class="sxs-lookup"><span data-stu-id="e063a-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="e063a-126">*Varnamenin* kapsamı `is` ifadeden `if` ifadeyi çevreleyen bloğun sonuna kadardır.</span><span class="sxs-lookup"><span data-stu-id="e063a-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="e063a-127">*Varname'nin* başka bir konumda kullanılması, atanmamış bir değişkenin kullanımı için derleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e063a-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="e063a-128">Aşağıdaki örnek, `is` bir tür <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yönteminin uygulanmasını sağlamak için tür deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="e063a-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="e063a-129">Desen eşleştirme olmadan, bu kod aşağıdaki gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="e063a-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="e063a-130">Tür deseni eşleştirmekullanımı, bir dönüştürmenin sonucunun bir `null`.</span><span class="sxs-lookup"><span data-stu-id="e063a-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="e063a-131">Tür `is` deseni, değer türünün türünü belirlerken daha kompakt kod da üretir.</span><span class="sxs-lookup"><span data-stu-id="e063a-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="e063a-132">Aşağıdaki örnek, `is` uygun bir özelliğin değerini `Person` görüntülemeden `Dog` önce bir nesnenin bir örnek mi yoksa örnek mi olduğunu belirlemek için tür deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="e063a-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="e063a-133">Desen eşleştirmesi olmayan eşdeğer kod, açık bir döküm içeren ayrı bir atama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e063a-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="e063a-134">Sabit desen</span><span class="sxs-lookup"><span data-stu-id="e063a-134">Constant pattern</span></span>

<span data-ttu-id="e063a-135">Sabit desenle eşleşen desen `is` gerçekleştirirken, bir ifadenin belirtilen bir sabite eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="e063a-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="e063a-136">C# 6 ve önceki sürümlerde, sabit desen [anahtar](switch.md) deyimi tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e063a-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="e063a-137">C# 7.0 ile başlayarak, `is` ifade tarafından da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e063a-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="e063a-138">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="e063a-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="e063a-139">*expr* değerlendirmek için ifade ve *sabit* için test etmek için değerdir.</span><span class="sxs-lookup"><span data-stu-id="e063a-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="e063a-140">*sabit* aşağıdaki sabit ifadelerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="e063a-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="e063a-141">Gerçek bir değer.</span><span class="sxs-lookup"><span data-stu-id="e063a-141">A literal value.</span></span>

- <span data-ttu-id="e063a-142">Bildirilen `const` değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="e063a-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="e063a-143">Numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="e063a-143">An enumeration constant.</span></span>

<span data-ttu-id="e063a-144">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="e063a-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="e063a-145">*Expr* ve *constant* integral türleri ise, C# eşitlik işleci `true` ifadenin döndürüp döndürülmediğini (yani, olup olmadığını) `expr == constant`belirler.</span><span class="sxs-lookup"><span data-stu-id="e063a-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="e063a-146">Aksi takdirde, ifadenin değeri statik [Object.Equals (expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemine yapılan bir çağrı ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e063a-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="e063a-147">Aşağıdaki örnek, bir nesnenin bir `Dice` örnek olup olmadığını sınamak ve bir zar rulosu değerinin 6 olup olmadığını belirlemek için türü ve sabit desenleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="e063a-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="e063a-148">Kontrol `null` sabit desen kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="e063a-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="e063a-149">Anahtar `null` kelime `is` deyim tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e063a-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="e063a-150">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="e063a-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="e063a-151">Aşağıdaki örnek, denetimlerin `null` karşılaştırılmasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e063a-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="e063a-152">var deseni</span><span class="sxs-lookup"><span data-stu-id="e063a-152">var pattern</span></span>

<span data-ttu-id="e063a-153">Desenile eşleşen `var` bir desen her zaman başarılı dır.</span><span class="sxs-lookup"><span data-stu-id="e063a-153">A pattern match with the `var` pattern always succeeds.</span></span> <span data-ttu-id="e063a-154">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="e063a-154">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="e063a-155">Expr değeri *expr* her zaman *varname*adlı yerel bir değişkene atanır nerede.</span><span class="sxs-lookup"><span data-stu-id="e063a-155">Where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="e063a-156">*varname,* *expr*derleme-zaman türü ile aynı türde bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="e063a-156">*varname* is a variable of the same type as the compile-time type of *expr*.</span></span>

<span data-ttu-id="e063a-157">*Expr* değerlendirirse `null`, `is` ifade `true` üretir `null` ve *varname*ye atar.</span><span class="sxs-lookup"><span data-stu-id="e063a-157">If *expr* evaluates to `null`, the `is` expression produces `true` and assigns `null` to *varname*.</span></span> <span data-ttu-id="e063a-158">Var deseni, bir `is` `true` `null` değer için üreten birkaç kullanımdan biridir.</span><span class="sxs-lookup"><span data-stu-id="e063a-158">The var pattern is one of the few uses of `is` that produces `true` for a `null` value.</span></span>

<span data-ttu-id="e063a-159">Aşağıdaki örnekte `var` görüldüğü gibi, Boolean ifadesi içinde geçici bir değişken oluşturmak için deseni kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e063a-159">You can use the `var` pattern to create a temporary variable within a Boolean expression, as the following example shows:</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="e063a-160">Önceki örnekte, geçici değişken pahalı bir işlemin sonucunu depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e063a-160">In the preceding example, the temporary variable is used to store the result of an expensive operation.</span></span> <span data-ttu-id="e063a-161">Değişken daha sonra birden çok kez kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e063a-161">The variable can then be used multiple times.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e063a-162">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e063a-162">C# language specification</span></span>
  
<span data-ttu-id="e063a-163">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [operatör](~/_csharplang/spec/expressions.md#the-is-operator) bölümüne ve aşağıdaki C# dil önerilerine bakın:</span><span class="sxs-lookup"><span data-stu-id="e063a-163">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="e063a-164">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="e063a-164">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="e063a-165">Genel türler ile desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="e063a-165">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="e063a-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e063a-166">See also</span></span>

- [<span data-ttu-id="e063a-167">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e063a-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e063a-168">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e063a-168">C# keywords</span></span>](index.md)
- [<span data-ttu-id="e063a-169">Tür testi ve atama işleçleri</span><span class="sxs-lookup"><span data-stu-id="e063a-169">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
