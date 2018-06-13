---
title: is (C# Başvurusu)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: c01152d016a852c15ffa1d1c82c16d6795965f31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289223"
---
# <a name="is-c-reference"></a><span data-ttu-id="d6b5d-102">is (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d6b5d-102">is (C# Reference)</span></span> #

<span data-ttu-id="d6b5d-103">Bir nesneyi belirtilen bir türle uyumlu değil veya (C# 7. 0'dan başlayarak) belirli bir desene göre bir ifade testleri olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="d6b5d-104">Tür uyumluluk için test etme</span><span class="sxs-lookup"><span data-stu-id="d6b5d-104">Testing for type compatibility</span></span> ##

<span data-ttu-id="d6b5d-105">`is` Anahtar sözcüğü çalışma zamanında tür uyumluluğu değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="d6b5d-106">Bir ifadenin sonucu belirtilen türe dönüştürülebilir veya bir nesne örneği olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="d6b5d-107">Sözdizimine sahip</span><span class="sxs-lookup"><span data-stu-id="d6b5d-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="d6b5d-108">Burada *expr* bazı türünün bir örneği için değerlendirilen ifade olan ve *türü* türün adı sonucu *expr* dönüştürülecek.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="d6b5d-109">`is` İfadesi `true` varsa *expr* null olmayan ve ifade değerlendirmede sonuçlarına dönüştürülebilir nesne *türü*; Aksi takdirde döndürdüğü `false`.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="d6b5d-110">Örneğin, aşağıdaki kodu belirler. `obj` örneğine cast `Person` türü:</span><span class="sxs-lookup"><span data-stu-id="d6b5d-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="d6b5d-111">`is` Deyimi doğruysa varsa:</span><span class="sxs-lookup"><span data-stu-id="d6b5d-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="d6b5d-112">*Expr* aynı türde örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="d6b5d-113">*Expr* türeyen bir tür örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="d6b5d-114">Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="d6b5d-115">*Expr* bir taban sınıf, derleme zamanı türüne sahip *türü*, ve *expr* olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="d6b5d-116">*Derleme zamanı tür* bir değişken değişkenin bildiriminde tanımlandığı gibi türüdür.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="d6b5d-117">*Çalışma zamanı tür* bir değişken bu değişkenine atanan örnek türüdür.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="d6b5d-118">*Expr* uygulayan bir tür örneği *türü* arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="d6b5d-119">Aşağıdaki örnekte gösterilir `is` ifadeyi hesaplar için `true` her dönüştürmeler.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="d6b5d-120">`is` Anahtar sözcüğü her zaman ya da olacak şekilde ifade biliniyorsa bir derleme zamanı uyarı oluşturur `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="d6b5d-121">Yalnızca başvuru dönüşümleri, kutulama dönüşümler ve kutudan çıkarma dönüşümleri dikkate alır; Kullanıcı tanımlı dönüşümler veya bir tür tarafından tanımlanan dönüşümleri düşünmez [örtük](implicit.md) ve [açık](explicit.md) işleçler.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="d6b5d-122">Dönüştürme işleminin sonucu derleme zamanında bilindiğinden aşağıdaki örnekte uyarılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-122">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="d6b5d-123">Unutmayın `is` dönüştürmeleri için ifade `int` için `long` ve `double` return dönüştürmeler tarafından işlenen beri false, [örtük](implicit.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-123">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="d6b5d-124">`expr` anonim yöntemler dışında bir değer döndüren ifadeye ve lambda ifadeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-124">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="d6b5d-125">Aşağıdaki örnek kullanır `is` bir yöntem çağrısının dönüş değerini değerlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-125">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="d6b5d-126">C# 7. 0'dan başlayarak, deseni ile eşleşen kullanabilirsiniz [türü düzeni](#type) kullanan daha kısa kod yazmaya `is` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-126">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="d6b5d-127">Desen ile eşleştirme `is`</span><span class="sxs-lookup"><span data-stu-id="d6b5d-127">Pattern matching with `is`</span></span> ##

<span data-ttu-id="d6b5d-128">C# 7.0 ile başlayan `is` ve [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimleri destek desen eşleştirme.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-128">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="d6b5d-129">`is` Anahtar sözcüğünü aşağıdaki desenleri destekler:</span><span class="sxs-lookup"><span data-stu-id="d6b5d-129">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="d6b5d-130">[Tür deseni](#type), bir ifade belirtilen türe dönüştürülüp dönüştürülemeyeceğini test eder ve, olabiliyorsa, bu tür bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-130">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="d6b5d-131">[Sabit düzeni](#constant), belirtilen bir sabit değer için bir ifadeyi değerlendirir olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-131">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="d6b5d-132">[var deseni](#var), her zaman başarılı olur ve bir ifadenin değerini yeni yerel bir değişkene bağlayan bir eşleşme.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-132">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="d6b5d-133"><a name="type" /> Tür deseni </a></span><span class="sxs-lookup"><span data-stu-id="d6b5d-133"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="d6b5d-134">Tür deseni desen eşleştirme gerçekleştirmek için kullanılırken `is` bir ifade belirtilen türe dönüştürülüp dönüştürülemeyeceğini test eder ve olabiliyorsa, bu tür bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-134">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="d6b5d-135">Basit bir uzantısıdır `is` kısa türü değerlendirme ve dönüştürme sağlayan deyimi.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-135">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="d6b5d-136">Genel biçiminde `is` türü deseni:</span><span class="sxs-lookup"><span data-stu-id="d6b5d-136">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="d6b5d-137">Burada *expr* bazı türünün bir örneği için değerlendirilen ifade *türü* türün adı sonucu *expr* dönüştürülmekte olan ve *varname* hangi nesne sonucu *expr* dönüştürülür `is` test `true`.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-137">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="d6b5d-138">`is` İfade `true` aşağıdakilerden biri doğruysa:</span><span class="sxs-lookup"><span data-stu-id="d6b5d-138">The `is` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="d6b5d-139">*Expr* aynı türde örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-139">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="d6b5d-140">*Expr* türeyen bir tür örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-140">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="d6b5d-141">Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-141">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="d6b5d-142">*Expr* bir taban sınıf, derleme zamanı türüne sahip *türü*, ve *expr* olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-142">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="d6b5d-143">*Derleme zamanı tür* bir değişken değişkenin bildiriminde tanımlandığı gibi türüdür.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-143">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="d6b5d-144">*Çalışma zamanı tür* bir değişken bu değişkenine atanan örnek türüdür.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-144">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="d6b5d-145">*Expr* uygulayan bir tür örneği *türü* arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-145">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="d6b5d-146">Varsa *exp* olan `true` ve `is` ile kullanılan bir `if` deyimi, *varname* atanır ve yerel kapsamda sahip `if` deyimi yalnızca.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-146">If *exp* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="d6b5d-147">Aşağıdaki örnek kullanır `is` bir türün uygulamasını sağlamak için türü desen <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-147">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="d6b5d-148">Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-148">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="d6b5d-149">Bir dönüştürme sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha küçük, okunabilir kod türü desen eşleştirme kullanımını üreten bir `null`.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-149">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="d6b5d-150">`is` Türü desen türündeki bir değer belirlerken daha küçük kod da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-150">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="d6b5d-151">Aşağıdaki örnek kullanır `is` bir nesne olup olmadığını belirlemek için türü desen bir `Person` veya `Dog` uygun bir özelliğin değerini göstermeden önce örneği.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-151">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="d6b5d-152">Desen eşleştirme olmadan eşdeğer kodu içeren bir açık atama ayrı bir atama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-152">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="d6b5d-153"><a name="constant" /> Sabit düzeni</span><span class="sxs-lookup"><span data-stu-id="d6b5d-153"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="d6b5d-154">Sabit desenle eşleşen kalıbı gerçekleştirirken `is` belirtilen bir sabit bir ifade eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-154">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="d6b5d-155">C# 6 ve önceki sürümlerinde, sabit düzeni tarafından desteklenen [geçiş](switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-155">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="d6b5d-156">C# 7. 0'dan başlayarak, onu tarafından desteklenen `is` de deyimi.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-156">Starting with C# 7.0, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="d6b5d-157">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d6b5d-157">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="d6b5d-158">Burada *expr* değerlendirmek için ifade ve *sabit* sınamak için bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-158">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="d6b5d-159">*Sabit* aşağıdaki sabit ifadelerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="d6b5d-159">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="d6b5d-160">Değişmez değer.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-160">A literal value.</span></span>

- <span data-ttu-id="d6b5d-161">Bir bildirilen adını `const` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-161">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="d6b5d-162">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-162">An enumeration constant.</span></span>

<span data-ttu-id="d6b5d-163">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="d6b5d-163">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="d6b5d-164">Varsa *expr* ve *sabit* tam sayı türleri, C# eşitlik işleci ifade döndürüp döndürmediğini belirler `true` (diğer bir deyişle, olup olmadığını `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="d6b5d-164">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="d6b5d-165">Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-165">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="d6b5d-166">Aşağıdaki örnekte bir nesne olup olmadığını sınamak için türü ve sabiti desenleri birleştiren bir `Dice` örneği ve, varsa, belirlemek için bölmek toplama değeri olup 6.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-166">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <span data-ttu-id="d6b5d-167"><a name="var" /> var deseni </a></span><span class="sxs-lookup"><span data-stu-id="d6b5d-167"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="d6b5d-168">Desen eşleştirme var deseni ile her zaman başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-168">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="d6b5d-169">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d6b5d-169">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="d6b5d-170">Burada değerini *expr* her zaman adlı yerel bir değişkene atanır *varname*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-170">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="d6b5d-171">*varName* statik bir değişken aynı türde *expr*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-171">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="d6b5d-172">Aşağıdaki örnek, bir ifade adlı bir değişkene atamak var deseni kullanır. `obj`.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-172">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="d6b5d-173">Ardından değerini ve türünü görüntüler `obj`.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-173">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="d6b5d-174">Unutmayın *expr* olan `null`, `is` ifade hala geçerlidir ve atar `null` için *varname*.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-174">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="d6b5d-175">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d6b5d-175">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d6b5d-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6b5d-176">See also</span></span>  
 [<span data-ttu-id="d6b5d-177">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d6b5d-177">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d6b5d-178">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d6b5d-178">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d6b5d-179">typeof</span><span class="sxs-lookup"><span data-stu-id="d6b5d-179">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="d6b5d-180">as</span><span class="sxs-lookup"><span data-stu-id="d6b5d-180">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="d6b5d-181">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d6b5d-181">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
