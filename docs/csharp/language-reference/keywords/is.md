---
title: is (C# Başvurusu)
keywords: anahtar sözcüğü (C#) olduğundan, (C#)
ms.date: 02/17/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f0242439caa21268a6c314409f41587890c4126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="is-c-reference"></a><span data-ttu-id="0388d-103">is (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0388d-103">is (C# Reference)</span></span> #

<span data-ttu-id="0388d-104">Bir nesneyi belirtilen bir türle uyumlu değil veya (C# 7 ile başlayan) belirli bir desene göre bir ifade testleri olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="0388d-104">Checks if an object is compatible with a given type, or (starting with C# 7) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="0388d-105">Tür uyumluluk için test etme</span><span class="sxs-lookup"><span data-stu-id="0388d-105">Testing for type compatibility</span></span> ##

<span data-ttu-id="0388d-106">`is` Anahtar sözcüğü çalışma zamanında tür uyumluluğu değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0388d-106">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="0388d-107">Bir ifadenin sonucu belirtilen türe dönüştürülebilir veya bir nesne örneği olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="0388d-107">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="0388d-108">Sözdizimine sahip</span><span class="sxs-lookup"><span data-stu-id="0388d-108">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="0388d-109">Burada *expr* bazı türünün bir örneği için değerlendirilen ifade olan ve *türü* türün adı sonucu *expr* dönüştürülecek.</span><span class="sxs-lookup"><span data-stu-id="0388d-109">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="0388d-110">`is` İfadesi `true` varsa *expr* null olmayan ve ifade değerlendirmede sonuçlarına dönüştürülebilir nesne *türü*; Aksi takdirde döndürdüğü `false`.</span><span class="sxs-lookup"><span data-stu-id="0388d-110">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="0388d-111">Örneğin, aşağıdaki kodu belirler. `obj` örneğine cast `Person` türü:</span><span class="sxs-lookup"><span data-stu-id="0388d-111">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="0388d-112">`is` Deyimi doğruysa varsa:</span><span class="sxs-lookup"><span data-stu-id="0388d-112">The `is` statement is true if:</span></span>

- <span data-ttu-id="0388d-113">*Expr* aynı türde örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="0388d-113">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="0388d-114">*Expr* türeyen bir tür örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="0388d-114">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="0388d-115">Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.</span><span class="sxs-lookup"><span data-stu-id="0388d-115">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="0388d-116">*Expr* bir taban sınıf, derleme zamanı türüne sahip *türü*, ve *expr* olan bir çalışma zamanı türü *türü* veya türetilmiş *türü* .</span><span class="sxs-lookup"><span data-stu-id="0388d-116">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="0388d-117">*Derleme zamanı tür* bir değişken değişkenin bildiriminde tanımlandığı gibi türüdür.</span><span class="sxs-lookup"><span data-stu-id="0388d-117">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="0388d-118">*Çalışma zamanı tür* bir değişken bu değişkenine atanan örnek türüdür.</span><span class="sxs-lookup"><span data-stu-id="0388d-118">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="0388d-119">*Expr* uygulayan bir tür örneği *türü* arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0388d-119">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="0388d-120">Aşağıdaki örnekte gösterilir `is` ifadeyi hesaplar için `true` her dönüştürmeler.</span><span class="sxs-lookup"><span data-stu-id="0388d-120">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="0388d-121">`is` Anahtar sözcüğü her zaman ya da olacak şekilde ifade biliniyorsa bir derleme zamanı uyarı oluşturur `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="0388d-121">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="0388d-122">Yalnızca başvuru dönüşümleri, kutulama dönüşümler ve kutudan çıkarma dönüşümleri dikkate alır; Kullanıcı tanımlı dönüşümler veya bir tür tarafından tanımlanan dönüşümleri düşünmez [örtük](implicit.md) ve [açık](explicit.md) işleçler.</span><span class="sxs-lookup"><span data-stu-id="0388d-122">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="0388d-123">Dönüştürme işleminin sonucu derleme zamanında bilindiğinden aşağıdaki örnekte uyarılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0388d-123">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="0388d-124">Unutmayın `is` dönüştürmeleri için ifade `int` için `long` ve `double` return dönüştürmeler tarafından işlenen beri false, [örtük](implicit.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="0388d-124">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="0388d-125">`expr`anonim yöntemler dışında bir değer döndüren ifadeye ve lambda ifadeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0388d-125">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="0388d-126">Aşağıdaki örnek kullanır `is` bir yöntem çağrısının dönüş değerini değerlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="0388d-126">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="0388d-127">C# 7 ile başlayan, deseni ile eşleşen kullanabilirsiniz [türü düzeni](#type) kullanan daha kısa kod yazmaya `is` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0388d-127">Starting with C# 7, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="0388d-128">Desen ile eşleştirme`is`</span><span class="sxs-lookup"><span data-stu-id="0388d-128">Pattern matching with `is`</span></span> ##

<span data-ttu-id="0388d-129">C# 7 ile başlayan `is` ve [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimleri destek desen eşleştirme.</span><span class="sxs-lookup"><span data-stu-id="0388d-129">Starting with C# 7, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="0388d-130">`is` Anahtar sözcüğünü aşağıdaki desenleri destekler:</span><span class="sxs-lookup"><span data-stu-id="0388d-130">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="0388d-131">[Tür deseni](#type), bir ifade belirtilen türe dönüştürülüp dönüştürülemeyeceğini test eder ve, olabiliyorsa, bu tür bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="0388d-131">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="0388d-132">[Sabit düzeni](#constant), belirtilen bir sabit değer için bir ifadeyi değerlendirir olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="0388d-132">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="0388d-133">[var deseni](#var), her zaman başarılı olur ve bir ifadenin değerini yeni yerel bir değişkene bağlayan bir eşleşme.</span><span class="sxs-lookup"><span data-stu-id="0388d-133">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="0388d-134"><a name="type" />Tür deseni</a></span><span class="sxs-lookup"><span data-stu-id="0388d-134"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="0388d-135">Tür deseni desen eşleştirme gerçekleştirmek için kullanılırken `is` bir ifade belirtilen türe dönüştürülüp dönüştürülemeyeceğini test eder ve olabiliyorsa, bu tür bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="0388d-135">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="0388d-136">Basit bir uzantısıdır `is` kısa türü değerlendirme ve dönüştürme sağlayan deyimi.</span><span class="sxs-lookup"><span data-stu-id="0388d-136">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="0388d-137">Genel biçiminde `is` türü deseni:</span><span class="sxs-lookup"><span data-stu-id="0388d-137">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="0388d-138">Burada *expr* bazı türünün bir örneği için değerlendirilen ifade *türü* türün adı sonucu *expr* dönüştürülmekte olan ve *varname* hangi nesne sonucu *expr* dönüştürülür `is` test `true`.</span><span class="sxs-lookup"><span data-stu-id="0388d-138">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="0388d-139">`is` İfade `true` aşağıdakilerden biri doğruysa:</span><span class="sxs-lookup"><span data-stu-id="0388d-139">The `is` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="0388d-140">*Expr* aynı türde örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="0388d-140">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="0388d-141">*Expr* türeyen bir tür örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="0388d-141">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="0388d-142">Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.</span><span class="sxs-lookup"><span data-stu-id="0388d-142">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="0388d-143">*Expr* bir taban sınıf, derleme zamanı türüne sahip *türü*, ve *expr* olan bir çalışma zamanı türü *türü* veya türetilmiş *türü* .</span><span class="sxs-lookup"><span data-stu-id="0388d-143">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="0388d-144">*Derleme zamanı tür* bir değişken değişkenin bildiriminde tanımlandığı gibi türüdür.</span><span class="sxs-lookup"><span data-stu-id="0388d-144">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="0388d-145">*Çalışma zamanı tür* bir değişken bu değişkenine atanan örnek türüdür.</span><span class="sxs-lookup"><span data-stu-id="0388d-145">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="0388d-146">*Expr* uygulayan bir tür örneği *türü* arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0388d-146">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="0388d-147">Varsa *exp* olan `true` ve `is` ile kullanılan bir `if` deyimi, *varname* atanır ve yerel kapsamda sahip `if` deyimi yalnızca.</span><span class="sxs-lookup"><span data-stu-id="0388d-147">If *exp* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="0388d-148">Aşağıdaki örnek kullanır `is` bir türün uygulamasını sağlamak için türü desen <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0388d-148">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="0388d-149">Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="0388d-149">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="0388d-150">Bir dönüştürme sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha küçük, okunabilir kod türü desen eşleştirme kullanımını üreten bir `null`.</span><span class="sxs-lookup"><span data-stu-id="0388d-150">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="0388d-151">`is` Türü desen türündeki bir değer belirlerken daha küçük kod da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0388d-151">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="0388d-152">Aşağıdaki örnek kullanır `is` bir nesne olup olmadığını belirlemek için türü desen bir `Person` veya `Dog` uygun bir özelliğin değerini göstermeden önce örneği.</span><span class="sxs-lookup"><span data-stu-id="0388d-152">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="0388d-153">Desen eşleştirme olmadan eşdeğer kodu içeren bir açık atama ayrı bir atama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0388d-153">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="0388d-154"><a name="constant" />Sabit düzeni</span><span class="sxs-lookup"><span data-stu-id="0388d-154"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="0388d-155">Sabit desenle eşleşen kalıbı gerçekleştirirken `is` belirtilen bir sabit bir ifade eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="0388d-155">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="0388d-156">C# 6 ve önceki sürümlerinde, sabit düzeni tarafından desteklenen [geçiş](switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="0388d-156">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="0388d-157">C# 7 ile başlayan, onu tarafından desteklenen `is` de deyimi.</span><span class="sxs-lookup"><span data-stu-id="0388d-157">Starting with C# 7, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="0388d-158">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0388d-158">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="0388d-159">Burada *expr* değerlendirmek için ifade ve *sabit* sınamak için bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="0388d-159">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="0388d-160">*Sabit* aşağıdaki sabit ifadelerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="0388d-160">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="0388d-161">Değişmez değer.</span><span class="sxs-lookup"><span data-stu-id="0388d-161">A literal value.</span></span>

- <span data-ttu-id="0388d-162">Bir bildirilen adını `const` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0388d-162">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="0388d-163">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="0388d-163">An enumeration constant.</span></span>

<span data-ttu-id="0388d-164">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="0388d-164">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="0388d-165">Varsa *expr* ve *sabit* tam sayı türleri, C# eşitlik işleci ifade döndürüp döndürmediğini belirler `true` (diğer bir deyişle, olup olmadığını `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="0388d-165">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="0388d-166">Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0388d-166">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="0388d-167">Aşağıdaki örnekte bir nesne olup olmadığını sınamak için türü ve sabiti desenleri birleştiren bir `Dice` örneği ve, varsa, belirlemek için bölmek toplama değeri olup 6.</span><span class="sxs-lookup"><span data-stu-id="0388d-167">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <span data-ttu-id="0388d-168"><a name="var" />var deseni</a></span><span class="sxs-lookup"><span data-stu-id="0388d-168"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="0388d-169">Desen eşleştirme var deseni ile her zaman başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="0388d-169">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="0388d-170">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0388d-170">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="0388d-171">Burada değerini *expr* her zaman adlı yerel bir değişkene atanır *varname*.</span><span class="sxs-lookup"><span data-stu-id="0388d-171">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="0388d-172">*varName* statik bir değişken aynı türde *expr*.</span><span class="sxs-lookup"><span data-stu-id="0388d-172">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="0388d-173">Aşağıdaki örnek, bir ifade adlı bir değişkene atamak var deseni kullanır. `obj`.</span><span class="sxs-lookup"><span data-stu-id="0388d-173">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="0388d-174">Ardından değerini ve türünü görüntüler `obj`.</span><span class="sxs-lookup"><span data-stu-id="0388d-174">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="0388d-175">Unutmayın *expr* olan `null`, `is` ifade hala geçerlidir ve atar `null` için *varname*.</span><span class="sxs-lookup"><span data-stu-id="0388d-175">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="0388d-176">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0388d-176">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0388d-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0388d-177">See also</span></span>  
 [<span data-ttu-id="0388d-178">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0388d-178">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0388d-179">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0388d-179">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0388d-180">typeof</span><span class="sxs-lookup"><span data-stu-id="0388d-180">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="0388d-181">olarak</span><span class="sxs-lookup"><span data-stu-id="0388d-181">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="0388d-182">İşleç anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0388d-182">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
