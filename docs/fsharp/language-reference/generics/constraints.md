---
title: Kısıtlamalar (F#)
description: 'Genel tür parametreleri bir genel tür veya işleve tür bağımsız değişkeni için gereksinimleri belirt uygulamak F # kısıtlamaları hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 65f648d39cf7c3dedf5e558c2ed35337a12efe4a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="constraints"></a><span data-ttu-id="02647-103">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="02647-103">Constraints</span></span>

<span data-ttu-id="02647-104">Bu konuda, genel için uygulayabileceğiniz kısıtlamasını açıklayan tür parametrelerindeki bir genel tür veya işleve tür bağımsız değişkeni için gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="02647-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>


## <a name="syntax"></a><span data-ttu-id="02647-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02647-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="02647-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02647-106">Remarks</span></span>
<span data-ttu-id="02647-107">Genel bir tür kullanılabilir türleri sınırlamak için uygulayabilirsiniz birçok farklı sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="02647-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="02647-108">Aşağıdaki tabloda listelenmekte ve bu kısıtlamaların açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02647-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="02647-109">Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="02647-109">Constraint</span></span>|<span data-ttu-id="02647-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02647-110">Syntax</span></span>|<span data-ttu-id="02647-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02647-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="02647-112">Tür sınırlaması</span><span class="sxs-lookup"><span data-stu-id="02647-112">Type Constraint</span></span>|<span data-ttu-id="02647-113">*tür parametresi* :&gt; *türü*</span><span class="sxs-lookup"><span data-stu-id="02647-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="02647-114">Sağlanan türü belirtilen türden eşit veya türetilmiş olmalıdır ya da bir arabirim türündeyse sağlanan türü arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="02647-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="02647-115">Null kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="02647-115">Null Constraint</span></span>|<span data-ttu-id="02647-116">*tür parametresi* : null</span><span class="sxs-lookup"><span data-stu-id="02647-116">*type-parameter* : null</span></span>|<span data-ttu-id="02647-117">Sağlanan türü null sabit değer desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="02647-117">The provided type must support the null literal.</span></span> <span data-ttu-id="02647-118">Bu tüm .NET nesne türlerini ancak değil F # listesi, tanımlama grubu, işlevi, sınıf, kayıt veya birleşim türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="02647-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="02647-119">Açık üye kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="02647-119">Explicit Member Constraint</span></span>|<span data-ttu-id="02647-120">([)]*tür parametresi* [veya... veya *tür parametresi*)]: (* üye imza *)</span><span class="sxs-lookup"><span data-stu-id="02647-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature *)</span></span>|<span data-ttu-id="02647-121">Sağlanan tür bağımsız değişkenleri en az birinin belirtilen imzaya sahip bir üye olması gerekir; Genel kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="02647-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="02647-122">Üyeleri ya da açıkça türü veya bir örtük türü uzantısı parçası açık bir üye kısıtlaması için geçerli hedefler için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02647-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="02647-123">Oluşturucu kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="02647-123">Constructor Constraint</span></span>|<span data-ttu-id="02647-124">*tür parametresi* : (yeni: birim -&gt; ' bir)</span><span class="sxs-lookup"><span data-stu-id="02647-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="02647-125">Sağlanan tür varsayılan bir oluşturucu sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02647-125">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="02647-126">Değer türü kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="02647-126">Value Type Constraint</span></span>|<span data-ttu-id="02647-127">: yapısı</span><span class="sxs-lookup"><span data-stu-id="02647-127">: struct</span></span>|<span data-ttu-id="02647-128">Sağlanan türü bir .NET değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02647-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="02647-129">Başvuru türü kısıtlama</span><span class="sxs-lookup"><span data-stu-id="02647-129">Reference Type Constraint</span></span>|<span data-ttu-id="02647-130">: değil yapısı</span><span class="sxs-lookup"><span data-stu-id="02647-130">: not struct</span></span>|<span data-ttu-id="02647-131">Sağlanan tür .NET başvuru türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02647-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="02647-132">Numaralandırma türü kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="02647-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="02647-133">: enum&lt;*temel alınan türü*&gt;</span><span class="sxs-lookup"><span data-stu-id="02647-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="02647-134">Sağlanan türü belirtilen temel alınan türü olan bir enum türü olmalıdır; Genel kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="02647-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="02647-135">Temsilci kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="02647-135">Delegate Constraint</span></span>|<span data-ttu-id="02647-136">: temsilci&lt;*tanımlama grubu parametre türü*, *dönüş türü*&gt;</span><span class="sxs-lookup"><span data-stu-id="02647-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="02647-137">Sağlanan türü belirtilen bağımsız olan bir temsilci türü ve değer döndürmesi gerekir; Genel kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="02647-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="02647-138">Karşılaştırma kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="02647-138">Comparison Constraint</span></span>|<span data-ttu-id="02647-139">: karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="02647-139">: comparison</span></span>|<span data-ttu-id="02647-140">Sağlanan türü karşılaştırma desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="02647-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="02647-141">Eşitlik kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="02647-141">Equality Constraint</span></span>|<span data-ttu-id="02647-142">: Eşitlik</span><span class="sxs-lookup"><span data-stu-id="02647-142">: equality</span></span>|<span data-ttu-id="02647-143">Sağlanan türü eşitlik desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="02647-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="02647-144">Yönetilmeyen kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="02647-144">Unmanaged Constraint</span></span>|<span data-ttu-id="02647-145">: Yönetilmeyen</span><span class="sxs-lookup"><span data-stu-id="02647-145">: unmanaged</span></span>|<span data-ttu-id="02647-146">Sağlanan türü yönetilmeyen bir türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02647-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="02647-147">Yönetilmeyen türleridir belirli ilkel türler (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, veya `decimal`), numaralandırma türleri `nativeptr&lt;_&gt;`, veya genel olmayan yapısı, alanları olan tüm yönetilmeyen tür.</span><span class="sxs-lookup"><span data-stu-id="02647-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr&lt;_&gt;`, or a non-generic structure whose fields are all unmanaged types.</span></span>|
<span data-ttu-id="02647-148">Genel kısıtlama türü ancak çalıştırılmadı türleri kullanılabilir bir özelliği kullanmak kodunuzu sahip olduğunda bir kısıtlama eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="02647-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="02647-149">Örneğin, bir sınıf türü belirtmek için tür sınırlaması kullanıyorsanız o sınıfın genel işlevi veya türü yöntemlerden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02647-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="02647-150">Bir kısıtlama, kullandığınız özellikleri türü için çalışma zamanında sağlanması herhangi bir türü üzerinde kullanılabilir olacağını doğrulama hiçbir şekilde derleyici olduğundan kısıtlamaları belirtme bazen tür parametreleri açıkça yazılırken gereklidir parametre.</span><span class="sxs-lookup"><span data-stu-id="02647-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="02647-151">F # kodunda kullanmak en sık kullanılan temel sınıfları veya arabirimleri belirtin türü kısıtlamaları sınırlamalardır.</span><span class="sxs-lookup"><span data-stu-id="02647-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="02647-152">Diğer kısıtlamaları ya da İşleç aşırı yüklemesi aritmetik işleçler için uygulamak için kullanılan ya da çoğunlukla F # tam desteklediği için sağlanan açık üye kısıtlaması gibi bazı işlevleri uygulamak için F # kitaplığı tarafından kullanılır Ortak dil çalışma zamanı tarafından desteklenen kısıtlamaları kümesi.</span><span class="sxs-lookup"><span data-stu-id="02647-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="02647-153">Tür çıkarımı işlemi sırasında bazı kısıtlamalar derleyici tarafından otomatik olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="02647-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="02647-154">Örneğin, kullanırsanız `+` işleci bir işlevdeki derleyici bir açık üye kısıtlaması ifadede kullanılan değişken türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="02647-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="02647-155">Aşağıdaki kod bazı kısıtlaması bildirimleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="02647-155">The following code illustrates some constraint declarations.</span></span>

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a><span data-ttu-id="02647-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02647-156">See Also</span></span>
[<span data-ttu-id="02647-157">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="02647-157">Generics</span></span>](index.md)

[<span data-ttu-id="02647-158">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="02647-158">Constraints</span></span>](constraints.md)
