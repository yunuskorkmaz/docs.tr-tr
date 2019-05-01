---
title: İş - C# başvurusu
ms.custom: seodec18
ms.date: 04/09/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 79cc59eb8de513f547a8fd87db8c95dd9af37375
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63774028"
---
# <a name="is-c-reference"></a><span data-ttu-id="85a4b-102">is (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="85a4b-102">is (C# Reference)</span></span>

<span data-ttu-id="85a4b-103">Bir nesne belirli bir tür ile uyumlu olan veya bir ifade belirli bir desene göre testleri (C# 7. 0'dan itibaren) denetler.</span><span class="sxs-lookup"><span data-stu-id="85a4b-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="85a4b-104">Tür uyumluluğu için test etme</span><span class="sxs-lookup"><span data-stu-id="85a4b-104">Testing for type compatibility</span></span>

<span data-ttu-id="85a4b-105">`is` Anahtar sözcüğü, çalışma zamanında tür uyumluluğu değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="85a4b-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="85a4b-106">Bir ifadenin sonucu bir belirtilen türe dönüştürülebilir ya da bir nesne örneği olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="85a4b-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="85a4b-107">Söz dizimine sahiptir</span><span class="sxs-lookup"><span data-stu-id="85a4b-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="85a4b-108">Burada *expr* bazı türünde bir örnek için değerlendirilen bir ifade olan ve *türü* türün adı sonucunu *expr* dönüştürülecek.</span><span class="sxs-lookup"><span data-stu-id="85a4b-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="85a4b-109">`is` Deyimi `true` varsa *expr* null olmayan ve ifade değerlendirme sonuçları dönüştürülebilir nesne *türü*; Aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="85a4b-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="85a4b-110">Örneğin, aşağıdaki kod, belirler `obj` örneğine atanabilecek `Person` türü:</span><span class="sxs-lookup"><span data-stu-id="85a4b-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="85a4b-111">`is` Deyimi değeri true ise:</span><span class="sxs-lookup"><span data-stu-id="85a4b-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="85a4b-112">*Expr* örneği aynı türde olan *türü*.</span><span class="sxs-lookup"><span data-stu-id="85a4b-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="85a4b-113">*Expr* türetilen türün bir örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="85a4b-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="85a4b-114">Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.</span><span class="sxs-lookup"><span data-stu-id="85a4b-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="85a4b-115">*Expr* temel bir sınıfı olan bir derleme zamanı türü sahip *türü*, ve *expr* sahip olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*.</span><span class="sxs-lookup"><span data-stu-id="85a4b-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="85a4b-116">*Derleme zamanı tür* değişkeninin Değişken bildiriminde tanımlanan türüdür.</span><span class="sxs-lookup"><span data-stu-id="85a4b-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="85a4b-117">*Çalışma zamanı türü* bir değişken, bu değişkene atanan örnek türüdür.</span><span class="sxs-lookup"><span data-stu-id="85a4b-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="85a4b-118">*Expr* uygulayan bir tür örneğidir *türü* arabirimi.</span><span class="sxs-lookup"><span data-stu-id="85a4b-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="85a4b-119">Aşağıdaki örnek, gösterir `is` ifadeyi hesaplar için `true` her biri bu dönüştürmeleri için.</span><span class="sxs-lookup"><span data-stu-id="85a4b-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="85a4b-120">`is` Anahtar sözcüğü ifade her zaman ya da olarak bilinen bir derleme zamanı uyarısı oluşturur `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="85a4b-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="85a4b-121">Yalnızca başvuru dönüşümleri, dönüştürmeleri kutulama ve kutudan çıkarma dönüştürme dikkate alır; Kullanıcı tanımlı dönüşümler veya bir türün tarafından tanımlanan dönüştürmeler düşünmez [örtük](implicit.md) ve [açık](explicit.md) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="85a4b-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="85a4b-122">Aşağıdaki örnek, uyarılar oluşturur, bu dönüştürme sonucu olarak, derleme zamanında bilinen çünkü.</span><span class="sxs-lookup"><span data-stu-id="85a4b-122">The following example generates warnings because the result of the conversion is known at compile time.</span></span> <span data-ttu-id="85a4b-123">`is` Dönüştürmelerinde ifade `int` için `long` ve `double` dönüştürmeler tarafından işlendiğinden dolayı false dönüş [örtük](implicit.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="85a4b-123">The `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="85a4b-124">`expr` anonim yöntem veya lambda ifadesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="85a4b-124">`expr` cannot be an anonymous method or lambda expression.</span></span> <span data-ttu-id="85a4b-125">Bu, bir değer döndüren herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="85a4b-125">It can be any other expression that returns a value.</span></span> <span data-ttu-id="85a4b-126">Aşağıdaki örnekte `is` bir yöntem çağrısının dönüş değerini değerlendirilecek.</span><span class="sxs-lookup"><span data-stu-id="85a4b-126">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="85a4b-127">C# 7.0 ile başlayarak, deseni ile eşleşen kullanabilirsiniz [türü deseni](#type) kullanan daha kısa kodu yazmak için `is` deyimi.</span><span class="sxs-lookup"><span data-stu-id="85a4b-127">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="85a4b-128">İle desen eşleştirme `is`</span><span class="sxs-lookup"><span data-stu-id="85a4b-128">Pattern matching with `is`</span></span>

<span data-ttu-id="85a4b-129">C# 7.0 ile başlayan `is` ve [geçiş](../../../csharp/language-reference/keywords/switch.md) ifadeleri desen eşleştirme desteği.</span><span class="sxs-lookup"><span data-stu-id="85a4b-129">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="85a4b-130">`is` Anahtar sözcüğü aşağıdaki düzenini destekler:</span><span class="sxs-lookup"><span data-stu-id="85a4b-130">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="85a4b-131">[Tür deseni](#type), bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve, olabilir, bu türden bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="85a4b-131">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="85a4b-132">[Sabit desen](#constant), belirtilen bir sabit değer için bir ifadeyi değerlendirir olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="85a4b-132">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="85a4b-133">[değişken desen](#var), her zaman yeni bir yerel değişken bir ifadenin değerine bağlar ve başarılı bir eşleşme.</span><span class="sxs-lookup"><span data-stu-id="85a4b-133">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <a name="a-nametype-type-pattern"></a><span data-ttu-id="85a4b-134"><a name="type" />Tür deseni</span><span class="sxs-lookup"><span data-stu-id="85a4b-134"><a name="type" />Type pattern</span></span>

<span data-ttu-id="85a4b-135">Desen eşleştirme, gerçekleştirmek için tür deseni kullanılırken `is` bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve bu olabilir, bu türden bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="85a4b-135">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="85a4b-136">Basit bir uzantısıdır `is` kısa türü değerlendirme ve dönüştürme sağlayan deyimi.</span><span class="sxs-lookup"><span data-stu-id="85a4b-136">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="85a4b-137">Genel formu `is` türü modelidir:</span><span class="sxs-lookup"><span data-stu-id="85a4b-137">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="85a4b-138">Burada *expr* bazı türünde bir örnek için değerlendirilen bir ifade olan *türü* türün adı sonucunu *expr* Boolean'a dönüştürülecek ve *varname* hangi nesne sonucu *expr* aralığındaysa dönüştürülür `is` test `true`.</span><span class="sxs-lookup"><span data-stu-id="85a4b-138">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="85a4b-139">`is` İfade `true` varsa *expr* değil `null`, ve aşağıdakilerden birini doğrudur:</span><span class="sxs-lookup"><span data-stu-id="85a4b-139">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="85a4b-140">*Expr* örneği aynı türde olan *türü*.</span><span class="sxs-lookup"><span data-stu-id="85a4b-140">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="85a4b-141">*Expr* türetilen türün bir örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="85a4b-141">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="85a4b-142">Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.</span><span class="sxs-lookup"><span data-stu-id="85a4b-142">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="85a4b-143">*Expr* temel bir sınıfı olan bir derleme zamanı türü sahip *türü*, ve *expr* sahip olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*.</span><span class="sxs-lookup"><span data-stu-id="85a4b-143">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="85a4b-144">*Derleme zamanı tür* değişkeninin Değişken bildiriminde tanımlanan türüdür.</span><span class="sxs-lookup"><span data-stu-id="85a4b-144">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="85a4b-145">*Çalışma zamanı türü* bir değişken, bu değişkene atanan örnek türüdür.</span><span class="sxs-lookup"><span data-stu-id="85a4b-145">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="85a4b-146">*Expr* uygulayan bir tür örneğidir *türü* arabirimi.</span><span class="sxs-lookup"><span data-stu-id="85a4b-146">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="85a4b-147">İle başlayarak C# 7.1, *expr* genel tür parametresi kısıtlamaları ile tanımlanan bir derleme zamanı türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="85a4b-147">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span> 

<span data-ttu-id="85a4b-148">Varsa *expr* olduğu `true` ve `is` ile kullanılan bir `if` deyimi, *varname* içinde atanan `if` deyimi yalnızca.</span><span class="sxs-lookup"><span data-stu-id="85a4b-148">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="85a4b-149">Kapsamı *varname* dandır `is` ifade kapsayan blok bitişi `if` deyimi.</span><span class="sxs-lookup"><span data-stu-id="85a4b-149">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="85a4b-150">Kullanarak *varname* içindeki herhangi bir konumda değil atanmış olan bir değişkenin kullanım için bir derleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85a4b-150">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="85a4b-151">Aşağıdaki örnekte `is` türün uygulamasını sağlamak üzere tür deseni <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="85a4b-151">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="85a4b-152">Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="85a4b-152">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="85a4b-153">Kullanım türü desen eşleştirme bir dönüştürmenin sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha kompakt ve okunabilir bir kod oluşturur bir `null`.</span><span class="sxs-lookup"><span data-stu-id="85a4b-153">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="85a4b-154">`is` Türü desen türü bir değer türü tespit edilirken daha küçük kod ayrıca oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85a4b-154">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="85a4b-155">Aşağıdaki örnekte `is` türü desen, bir nesne olup olmadığını belirlemek için bir `Person` veya `Dog` uygun bir özelliğin değerini göstermeden önce örneği.</span><span class="sxs-lookup"><span data-stu-id="85a4b-155">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="85a4b-156">Desen eşleştirme olmadan eşdeğer kod, bir açık tür dönüştürme içeren ayrı bir atama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="85a4b-156">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="85a4b-157"><a name="constant" /> Sabit desen</span><span class="sxs-lookup"><span data-stu-id="85a4b-157"><a name="constant" /> Constant pattern</span></span>

<span data-ttu-id="85a4b-158">Sabit desen ile eşleşen deseni gerçekleştirirken `is` belirtilen sabit bir ifade eşit olup olmadığını test eder.</span><span class="sxs-lookup"><span data-stu-id="85a4b-158">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="85a4b-159">C# 6 ve önceki sürümleri, sabit desen tarafından desteklenen [geçiş](switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="85a4b-159">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="85a4b-160">İle başlayarak C# 7.0, onu tarafından desteklenen `is` deyimi de.</span><span class="sxs-lookup"><span data-stu-id="85a4b-160">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="85a4b-161">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="85a4b-161">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="85a4b-162">Burada *expr* değerlendirmek için ifade ve *sabit* sınamak için değer.</span><span class="sxs-lookup"><span data-stu-id="85a4b-162">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="85a4b-163">*Sabit* aşağıdaki sabit ifadeler biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="85a4b-163">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="85a4b-164">Değişmez değer.</span><span class="sxs-lookup"><span data-stu-id="85a4b-164">A literal value.</span></span>

- <span data-ttu-id="85a4b-165">Bildirilen bir adı `const` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="85a4b-165">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="85a4b-166">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="85a4b-166">An enumeration constant.</span></span>

<span data-ttu-id="85a4b-167">Sabit ifade gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="85a4b-167">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="85a4b-168">Varsa *expr* ve *sabit* integral türleri, C# eşitlik işlecini ifade döndürüp döndürmediğini belirler `true` (olup, diğer bir deyişle, `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="85a4b-168">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="85a4b-169">Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="85a4b-169">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="85a4b-170">Aşağıdaki örnek bir nesne olup olmadığını sınamak için tür ve sabit desenler birleştiren bir `Dice` örneği ve ise, belirlemek için bir zar değerini olup 6.</span><span class="sxs-lookup"><span data-stu-id="85a4b-170">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="85a4b-171">Denetleme `null` sabit deseni kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="85a4b-171">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="85a4b-172">`null` Anahtar sözcüğü tarafından desteklenen `is` deyimi.</span><span class="sxs-lookup"><span data-stu-id="85a4b-172">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="85a4b-173">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="85a4b-173">Its syntax is:</span></span>

```csharp 
   expr is null
```

<span data-ttu-id="85a4b-174">Aşağıdaki örnek, bir karşılaştırmasını gösterir `null` denetler:</span><span class="sxs-lookup"><span data-stu-id="85a4b-174">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <span data-ttu-id="85a4b-175"><a name="var" /> değişken deseni </a></span><span class="sxs-lookup"><span data-stu-id="85a4b-175"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="85a4b-176">`var` Herhangi bir türü veya değer için bir catch tüm modelidir.</span><span class="sxs-lookup"><span data-stu-id="85a4b-176">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="85a4b-177">Değerini *expr* derleme zamanı türünü aynı türe her zaman yerel bir değişkene atanan *expr*.</span><span class="sxs-lookup"><span data-stu-id="85a4b-177">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="85a4b-178">Sonucu `is` ifadesidir her zaman `true`.</span><span class="sxs-lookup"><span data-stu-id="85a4b-178">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="85a4b-179">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="85a4b-179">Its syntax is:</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="85a4b-180">Aşağıdaki örnek, bir ifade adlı bir değişkene atayın için değişken deseni kullanır. `obj`.</span><span class="sxs-lookup"><span data-stu-id="85a4b-180">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="85a4b-181">Ardından değerine ve türüne görüntüler `obj`.</span><span class="sxs-lookup"><span data-stu-id="85a4b-181">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="85a4b-182">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="85a4b-182">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="85a4b-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85a4b-183">See also</span></span>

- [<span data-ttu-id="85a4b-184">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="85a4b-184">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="85a4b-185">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="85a4b-185">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="85a4b-186">typeof</span><span class="sxs-lookup"><span data-stu-id="85a4b-186">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)
- [<span data-ttu-id="85a4b-187">as</span><span class="sxs-lookup"><span data-stu-id="85a4b-187">as</span></span>](../../../csharp/language-reference/keywords/as.md)
- [<span data-ttu-id="85a4b-188">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="85a4b-188">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
