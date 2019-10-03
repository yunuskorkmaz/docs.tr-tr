---
title: Kısıtlamalar
description: Genel tür F# veya işlevdeki bir tür bağımsız değişkeni için gereksinimleri belirtmek üzere genel tür parametrelerine uygulanan kısıtlamalar hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 9912ba63138d893a7c616661dd2b1cbdbe51916c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736800"
---
# <a name="constraints"></a><span data-ttu-id="8d56c-103">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="8d56c-103">Constraints</span></span>

<span data-ttu-id="8d56c-104">Bu konu başlığı altında, genel tür parametrelerine uygulayabileceğiniz kısıtlamalar açıklanmakta ve genel tür veya işlevdeki bir tür bağımsız değişkeni için gereksinimleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d56c-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d56c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d56c-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="8d56c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d56c-106">Remarks</span></span>

<span data-ttu-id="8d56c-107">Genel bir türde kullanılabilecek türleri sınırlamak için uygulayabileceğiniz çeşitli farklı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="8d56c-108">Aşağıdaki tabloda bu kısıtlamalar listelenmektedir ve açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="8d56c-109">Kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-109">Constraint</span></span>|<span data-ttu-id="8d56c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d56c-110">Syntax</span></span>|<span data-ttu-id="8d56c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d56c-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="8d56c-112">Tür kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-112">Type Constraint</span></span>|<span data-ttu-id="8d56c-113">*tür-parametresi* : &gt; *tür*</span><span class="sxs-lookup"><span data-stu-id="8d56c-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="8d56c-114">Belirtilen tür, belirtilen türe eşit veya ondan türetilmiş olmalıdır ya da tür bir arabirimse, belirtilen türün arabirimi uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d56c-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="8d56c-115">NULL kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-115">Null Constraint</span></span>|<span data-ttu-id="8d56c-116">*tür parametresi* : null</span><span class="sxs-lookup"><span data-stu-id="8d56c-116">*type-parameter* : null</span></span>|<span data-ttu-id="8d56c-117">Belirtilen tür null sabit değeri desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="8d56c-117">The provided type must support the null literal.</span></span> <span data-ttu-id="8d56c-118">Bu, tüm .NET nesne türlerini içerir ancak F# liste, demet, işlev, sınıf, kayıt veya birleşim türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8d56c-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="8d56c-119">Açık üye kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-119">Explicit Member Constraint</span></span>|<span data-ttu-id="8d56c-120">[(]*tür-parametre* [veya... or *türü-parametresi*)]: (*üye-imza*)</span><span class="sxs-lookup"><span data-stu-id="8d56c-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="8d56c-121">Belirtilen tür bağımsız değişkenlerinden en az biri, belirtilen imzaya sahip bir üyeye sahip olmalıdır; yaygın kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="8d56c-122">Üyeler açık bir üye kısıtlaması için geçerli hedefler olmak üzere tür üzerinde açıkça tanımlanmalıdır veya örtük bir tür uzantısının bir bölümü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="8d56c-123">Oluşturucu kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-123">Constructor Constraint</span></span>|<span data-ttu-id="8d56c-124">*tür-parametresi* : (yeni: birim-&gt; ' a)</span><span class="sxs-lookup"><span data-stu-id="8d56c-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="8d56c-125">Belirtilen türün parametresiz bir oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-125">The provided type must have a parameterless constructor.</span></span>|
|<span data-ttu-id="8d56c-126">Değer türü kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-126">Value Type Constraint</span></span>|<span data-ttu-id="8d56c-127">: struct</span><span class="sxs-lookup"><span data-stu-id="8d56c-127">: struct</span></span>|<span data-ttu-id="8d56c-128">Belirtilen tür bir .NET değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="8d56c-129">Başvuru türü kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-129">Reference Type Constraint</span></span>|<span data-ttu-id="8d56c-130">: struct değil</span><span class="sxs-lookup"><span data-stu-id="8d56c-130">: not struct</span></span>|<span data-ttu-id="8d56c-131">Belirtilen tür bir .NET başvuru türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="8d56c-132">Numaralandırma türü kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="8d56c-133">: enum @ no__t-0*temel türü*&gt;</span><span class="sxs-lookup"><span data-stu-id="8d56c-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="8d56c-134">Belirtilen tür, belirtilen temel alınan türe sahip bir numaralandırılmış tür olmalıdır; yaygın kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="8d56c-135">Temsilci kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-135">Delegate Constraint</span></span>|<span data-ttu-id="8d56c-136">: temsilci @ no__t-0*demet-parametre-türü*, *return-Type*&gt;</span><span class="sxs-lookup"><span data-stu-id="8d56c-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="8d56c-137">Belirtilen tür, belirtilen bağımsız değişkenlere ve dönüş değerine sahip bir temsilci türü olmalıdır; yaygın kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="8d56c-138">Karşılaştırma kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-138">Comparison Constraint</span></span>|<span data-ttu-id="8d56c-139">: karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="8d56c-139">: comparison</span></span>|<span data-ttu-id="8d56c-140">Belirtilen tür karşılaştırmayı desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="8d56c-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="8d56c-141">Eşitlik kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="8d56c-141">Equality Constraint</span></span>|<span data-ttu-id="8d56c-142">: eşitlik</span><span class="sxs-lookup"><span data-stu-id="8d56c-142">: equality</span></span>|<span data-ttu-id="8d56c-143">Belirtilen tür eşitlik desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="8d56c-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="8d56c-144">Yönetilmeyen kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8d56c-144">Unmanaged Constraint</span></span>|<span data-ttu-id="8d56c-145">: yönetilmeyen</span><span class="sxs-lookup"><span data-stu-id="8d56c-145">: unmanaged</span></span>|<span data-ttu-id="8d56c-146">Belirtilen tür, yönetilmeyen bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="8d56c-147">Yönetilmeyen türler, belirli basit türlerdir (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, 0, 1, 2 veya 3), numaralandırma türleri, 4 veya genel olmayan bir alanları tüm yönetilmeyen türler olan yapı.</span><span class="sxs-lookup"><span data-stu-id="8d56c-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="8d56c-148">Kodunuzun kısıtlama türünde kullanılabilir ancak genel olarak türlerde olmayan bir özelliği kullanması gerektiğinde bir kısıtlama eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d56c-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="8d56c-149">Örneğin, bir sınıf türü belirtmek için tür kısıtlaması kullanırsanız, bu sınıfın yöntemlerinden birini genel işlevde veya türünde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d56c-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="8d56c-150">Tür parametreleri açıkça yazılırken kısıtlamaların belirlenmesi bazen gereklidir, çünkü kısıtlama olmadan derleyici, kullanmakta olduğunuz özelliklerin tür için çalışma zamanında sağlanabilecek herhangi bir türde kullanılabilir olacağını doğrulama yöntemine sahip değildir. parametresinin.</span><span class="sxs-lookup"><span data-stu-id="8d56c-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="8d56c-151">F# Kodda kullandığınız en yaygın kısıtlamalar, temel sınıfları veya arabirimleri belirten tür kısıtlamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="8d56c-152">Diğer kısıtlamalar F# kitaplık tarafından, aritmetik işleçler için işleç aşırı yüklemesini uygulamak için kullanılan açık üye kısıtlaması gibi belirli işlevleri uygulamak için kullanılır ya da temel F# olarak sağlanır ortak dil çalışma zamanı tarafından desteklenen tüm kısıtlama kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="8d56c-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="8d56c-153">Tür çıkarımı işlemi sırasında, bazı kısıtlamalar derleyici tarafından otomatik olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="8d56c-154">Örneğin, bir işlevde `+` işlecini kullanırsanız, derleyici ifadede kullanılan değişken türlerinde açık bir üye kısıtlaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d56c-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="8d56c-155">Aşağıdaki kod bazı kısıtlama bildirimlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="8d56c-155">The following code illustrates some constraint declarations:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8d56c-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d56c-156">See also</span></span>

- [<span data-ttu-id="8d56c-157">Tür</span><span class="sxs-lookup"><span data-stu-id="8d56c-157">Generics</span></span>](index.md)
- [<span data-ttu-id="8d56c-158">Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="8d56c-158">Constraints</span></span>](constraints.md)
