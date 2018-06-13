---
title: Tür Uzantıları (F#)
description: 'Önceden tanımlanmış nesne türü için yeni üye eklemek F # tür uzantıları nasıl izin öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 2181745ea75894fbfe35d5522c130baaf1876455
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566892"
---
# <a name="type-extensions"></a><span data-ttu-id="de069-103">Tür Uzantıları</span><span class="sxs-lookup"><span data-stu-id="de069-103">Type Extensions</span></span>

<span data-ttu-id="de069-104">Tür uzantıları önceden tanımlanmış nesne türü için yeni üyeler eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="de069-104">Type extensions let you add new members to a previously defined object type.</span></span>

## <a name="syntax"></a><span data-ttu-id="de069-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de069-105">Syntax</span></span>

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a><span data-ttu-id="de069-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de069-106">Remarks</span></span>
<span data-ttu-id="de069-107">Biraz farklı bir sözdizimi ve davranış türü uzantıları iki tür vardır.</span><span class="sxs-lookup"><span data-stu-id="de069-107">There are two forms of type extensions that have slightly different syntax and behavior.</span></span> <span data-ttu-id="de069-108">Bir *iç uzantı* aynı ad alanı veya modül, aynı kaynak dosyasını ve aynı derleme (DLL ya da yürütülebilir dosya) görüntülenen genişletilen türü olarak uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="de069-108">An *intrinsic extension* is an extension that appears in the same namespace or module, in the same source file, and in the same assembly (DLL or executable file) as the type being extended.</span></span> <span data-ttu-id="de069-109">Bir *isteğe bağlı uzantı* özgün modülü, ad veya derleme genişletilen türü dışında görünür bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="de069-109">An *optional extension* is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span> <span data-ttu-id="de069-110">İç uzantıları türüne türü tarafından yansıma incelenir, ancak isteğe bağlı uzantılar sağlamadığı görünür.</span><span class="sxs-lookup"><span data-stu-id="de069-110">Intrinsic extensions appear on the type when the type is examined by reflection, but optional extensions do not.</span></span> <span data-ttu-id="de069-111">Uzantıları modülleri olmalıdır ve uzantısını içeren modülü açık olduğunda bunlar yalnızca kapsamda isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="de069-111">Optional extensions must be in modules, and they are only in scope when the module that contains the extension is open.</span></span>

<span data-ttu-id="de069-112">Önceki sözdiziminde *typename* genişletilen türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de069-112">In the previous syntax, *typename* represents the type that is being extended.</span></span> <span data-ttu-id="de069-113">Erişilebilen herhangi bir türü genişletilmiş ancak tür adı türü kısaltması bir gerçek tür adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de069-113">Any type that can be accessed can be extended, but the type name must be an actual type name, not a type abbreviation.</span></span> <span data-ttu-id="de069-114">Birden çok üye bir türü uzantısı'nda tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de069-114">You can define multiple members in one type extension.</span></span> <span data-ttu-id="de069-115">*Kendi kendine tanımlayıcı* yalnızca normal üye olduğu gibi çağrılan nesne örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de069-115">The *self-identifier* represents the instance of the object being invoked, just as in ordinary members.</span></span>

<span data-ttu-id="de069-116">`end` Sözcüktür basit sözdiziminde isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="de069-116">The `end` keyword is optional in lightweight syntax.</span></span>

<span data-ttu-id="de069-117">Üye türü uzantılarında tanımlanmıştır gibi diğer üyeleri bir sınıf türü üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de069-117">Members defined in type extensions can be used just like other members on a class type.</span></span> <span data-ttu-id="de069-118">Diğer üyeleri gibi bunlar statik veya örnek üyeleri.</span><span class="sxs-lookup"><span data-stu-id="de069-118">Like other members, they can be static or instance members.</span></span> <span data-ttu-id="de069-119">Bu yöntemleri olarak da bilinen olan *genişletme yöntemleri*; özellikleri olarak bilinen *uzantısı özellikleri*ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="de069-119">These methods are also known as *extension methods*; properties are known as *extension properties*, and so on.</span></span> <span data-ttu-id="de069-120">İsteğe bağlı uzantı üyeleri statik üyeleri için nesne örneği örtük olarak ilk parametre olarak geçirilen derlenir.</span><span class="sxs-lookup"><span data-stu-id="de069-120">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="de069-121">Ancak, örnek üyelerin veya nasıl bildirilir göre statik üyeler gibi bunlar görür.</span><span class="sxs-lookup"><span data-stu-id="de069-121">However, they act as if they were instance members or static members according to how they are declared.</span></span> <span data-ttu-id="de069-122">Örtük uzantı üyeleri türü bir üyesi olarak dahil edilir ve kısıtlama kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de069-122">Implicit extension members are included as members of the type and can be used without restriction.</span></span>

<span data-ttu-id="de069-123">Genişletme yöntemleri sanal ya da soyut yöntemler olamaz.</span><span class="sxs-lookup"><span data-stu-id="de069-123">Extension methods cannot be virtual or abstract methods.</span></span> <span data-ttu-id="de069-124">Aynı ada sahip başka yöntemler aşırı yüklenebilir, ancak derleyici tercih uzantısı olmayan yöntemlerine belirsiz bir çağrı durumunda sağlar.</span><span class="sxs-lookup"><span data-stu-id="de069-124">They can overload other methods of the same name, but the compiler gives preference to non-extension methods in the case of an ambiguous call.</span></span>

<span data-ttu-id="de069-125">Birden çok geçerli bir tür uzantıları için bir türü yoksa, tüm üyeleri benzersiz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="de069-125">If multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="de069-126">İsteğe bağlı türü uzantıları için aynı türde farklı tür uzantıları üyeleri aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="de069-126">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="de069-127">Yalnızca istemci kodu aynı üye adlarının tanımlayan iki farklı kapsamlar açarsa belirsizlik hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="de069-127">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

<span data-ttu-id="de069-128">Aşağıdaki örnekte, geçerli bir tür uzantı modülünde bir türe sahip.</span><span class="sxs-lookup"><span data-stu-id="de069-128">In the following example, a type in a module has an intrinsic type extension.</span></span> <span data-ttu-id="de069-129">Modül dışındaki istemci kodu için türü uzantısı türünün tüm bakımdan normal bir üyesi olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="de069-129">To client code outside the module, the type extension appears as a regular member of the type in all respects.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

<span data-ttu-id="de069-130">Bir tür bölümlere tanımını ayırmak için geçerli bir tür uzantıları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de069-130">You can use intrinsic type extensions to separate the definition of a type into sections.</span></span> <span data-ttu-id="de069-131">Derleyicinin ürettiği kodu ve yazılan kodu ayrı tutmak için ya da farklı kişiler tarafından oluşturulan ya da farklı işlevselliği ile ilişkili kodu gruplamak için büyük tür tanımları yönetilmesindeki yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="de069-131">This can be useful in managing large type definitions, for example, to keep compiler-generated code and authored code separate or to group together code created by different people or associated with different functionality.</span></span>

<span data-ttu-id="de069-132">Aşağıdaki örnekte, bir isteğe bağlı türü uzantısı genişletir `System.Int32` türü bir genişletme yöntemi ile `FromString` statik üye çağırır `Parse`.</span><span class="sxs-lookup"><span data-stu-id="de069-132">In the following example, an optional type extension extends the `System.Int32` type with an extension method `FromString` that calls the static member `Parse`.</span></span> <span data-ttu-id="de069-133">`testFromString` Yöntemi gösteren yeni üye yalnızca bir örnek üyesine gibi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="de069-133">The `testFromString` method demonstrates that the new member is called just like any instance member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

<span data-ttu-id="de069-134">Yeni örnek üyesine herhangi diğer bir yöntemini gibi görünür `Int32` türü IntelliSense, ancak yalnızca uzantısı içeren modülü kapsamında açık veya aksi durumda olduğunda.</span><span class="sxs-lookup"><span data-stu-id="de069-134">The new instance member will appear like any other method of the `Int32` type in IntelliSense, but only when the module that contains the extension is open or otherwise in scope.</span></span>

## <a name="generic-extension-methods"></a><span data-ttu-id="de069-135">Genel genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="de069-135">Generic Extension Methods</span></span>
<span data-ttu-id="de069-136">F # 3.1 önce C# kullanımını F # derleyici desteklemekteydi-stil genel tür değişkeni, dizi türü, kayıt türü veya bir "Bu" parametresi olarak F # işlev türü ile genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="de069-136">Before F# 3.1, the F# compiler didn't support the use of C#-style extension methods with a generic type variable, array type, tuple type, or an F# function type as the "this" parameter.</span></span> <span data-ttu-id="de069-137">F # 3.1 Bu uzantı üyeleri kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="de069-137">F# 3.1 supports the use of these extension members.</span></span>

<span data-ttu-id="de069-138">Örneğin, F # 3.1 kodda, C# aşağıdaki söz dizimine benzer imzaları ile genişletme yöntemleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="de069-138">For example, in F# 3.1 code, you can use extension methods with signatures that resemble the following syntax in C#:</span></span>

```csharp
static member Method<T>(this T input, T other)
```

<span data-ttu-id="de069-139">Genel tür parametresi kısıtlı kullanılırken, bu yaklaşım özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="de069-139">This approach is particularly useful when the generic type parameter is constrained.</span></span> <span data-ttu-id="de069-140">Ayrıca, artık F # kodunda şöyle uzantı üyeleri bildirme ve ek bir anlam olarak zengin genişletme yöntemleri kümesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="de069-140">Further, you can now declare extension members like this in F# code and define an additional, semantically rich set of extension methods.</span></span> <span data-ttu-id="de069-141">F #'ta, genellikle uzantı üyeleri aşağıdaki örnekte gösterildiği gibi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="de069-141">In F#, you usually define extension members as the following example shows:</span></span>

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

<span data-ttu-id="de069-142">Ancak, genel bir tür için türü değişkeni kısıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="de069-142">However, for a generic type, the type variable may not be constrained.</span></span> <span data-ttu-id="de069-143">Şimdi bir C# bildirebilirsiniz-bu sınırlamaya geçici bir çözüm için F # stili uzantı üyesi.</span><span class="sxs-lookup"><span data-stu-id="de069-143">You can now declare a C#-style extension member in F# to work around this limitation.</span></span> <span data-ttu-id="de069-144">Bu tür bir bildirimi F # satır içi özelliğiyle birleştirdiğinizde uzantısı üye olarak genel algoritmaları sunabilir.</span><span class="sxs-lookup"><span data-stu-id="de069-144">When you combine this kind of declaration with the inline feature of F#, you can present generic algorithms as extension members.</span></span>

<span data-ttu-id="de069-145">Aşağıdaki bildirimi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="de069-145">Consider the following declaration:</span></span>

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="de069-146">Bu bildirim kullanarak, aşağıdaki örneğe benzer bir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de069-146">By using this declaration, you can write code that resembles the following sample.</span></span>

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

<span data-ttu-id="de069-147">Bu kodda, iki tür bir listesi için tek uzantısı üyesi tanımlayarak aşırı olmadan aynı genel aritmetik kod uygulanır.</span><span class="sxs-lookup"><span data-stu-id="de069-147">In this code, the same generic arithmetic code is applied to lists of two types without overloading, by defining a single extension member.</span></span>


## <a name="see-also"></a><span data-ttu-id="de069-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de069-148">See Also</span></span>
[<span data-ttu-id="de069-149">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="de069-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="de069-150">Üyeler</span><span class="sxs-lookup"><span data-stu-id="de069-150">Members</span></span>](members/index.md)
