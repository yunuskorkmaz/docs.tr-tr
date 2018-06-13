---
title: Devralma (F#)
description: "Devralma 'devralmak' anahtar sözcüğünü kullanarak F # ilişkileri belirleme konusunda bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: 3d0c0785fc595315a8283979b99d0ec4fc5cbc0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564801"
---
# <a name="inheritance"></a><span data-ttu-id="25f77-103">Devralma</span><span class="sxs-lookup"><span data-stu-id="25f77-103">Inheritance</span></span>

<span data-ttu-id="25f77-104">Devralma "olduğunu-a" ilişkileri modellemek için kullanılan veya, nesne odaklı programlama subtyping.</span><span class="sxs-lookup"><span data-stu-id="25f77-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>


## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="25f77-105">Devralma ilişkisi belirtme</span><span class="sxs-lookup"><span data-stu-id="25f77-105">Specifying Inheritance Relationships</span></span>
<span data-ttu-id="25f77-106">Devralma ilişkisi kullanarak belirttiğiniz `inherit` anahtar sözcüğü bir sınıf bildirimindeki.</span><span class="sxs-lookup"><span data-stu-id="25f77-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="25f77-107">Temel söz dizimi form aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="25f77-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="25f77-108">Bir sınıf en fazla bir doğrudan temel sınıfı olabilir.</span><span class="sxs-lookup"><span data-stu-id="25f77-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="25f77-109">Bir taban sınıf kullanarak belirtmezseniz `inherit` anahtar sözcüğü, örtük olarak sınıfının devraldığı `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="25f77-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>


## <a name="inherited-members"></a><span data-ttu-id="25f77-110">Devralınan üyeleri</span><span class="sxs-lookup"><span data-stu-id="25f77-110">Inherited Members</span></span>
<span data-ttu-id="25f77-111">Başka bir sınıftan bir sınıf, yöntemleri ve taban sınıfı üyeleri türetilmiş sınıf doğrudan üyesi değilmiş gibi türetilmiş sınıf kullanıcıları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25f77-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="25f77-112">Let bağlamaları ve Oluşturucu parametreleri bir sınıfa özel olan ve, bu nedenle, türetilmiş sınıflarından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="25f77-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="25f77-113">Anahtar sözcüğü `base` türetilmiş sınıflarda kullanılabilir ve temel sınıf örneğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="25f77-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="25f77-114">Kendi kendine tanımlayıcı gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25f77-114">It is used like the self-identifier.</span></span>


## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="25f77-115">Sanal yöntemler ve geçersiz kılmalar</span><span class="sxs-lookup"><span data-stu-id="25f77-115">Virtual Methods and Overrides</span></span>
<span data-ttu-id="25f77-116">Sanal yöntemler (ve özellikleri) biraz farklı F #'ta diğer .NET dilleri ile karşılaştırıldığında çalışır.</span><span class="sxs-lookup"><span data-stu-id="25f77-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="25f77-117">Yeni bir sanal üye bildirmek için kullandığınız `abstract` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="25f77-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="25f77-118">Bunun için bu yöntem için bir varsayılan uygulama sağlamak bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="25f77-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="25f77-119">Bu nedenle tam bir temel sınıf sanal bir yöntem tanımının bu deseni izler:</span><span class="sxs-lookup"><span data-stu-id="25f77-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="25f77-120">Ve türetilen bir sınıfta geçersiz kılma sanal bu yöntemin bu deseni izler:</span><span class="sxs-lookup"><span data-stu-id="25f77-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="25f77-121">Varsayılan uygulaması temel sınıf atlarsanız, temel sınıf soyut bir sınıf haline gelir.</span><span class="sxs-lookup"><span data-stu-id="25f77-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="25f77-122">Yeni sanal bir yöntem bildirimi aşağıdaki kod örneği gösterilmektedir `function1` bir taban sınıf ve türetilen bir sınıfta geçersiz kılmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="25f77-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a><span data-ttu-id="25f77-123">Oluşturucular ve devralma</span><span class="sxs-lookup"><span data-stu-id="25f77-123">Constructors and Inheritance</span></span>
<span data-ttu-id="25f77-124">Taban sınıfı oluşturucusu türetilen sınıfta çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25f77-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="25f77-125">İçin temel sınıf oluşturucu bağımsız değişken listesinde görünür `inherit` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="25f77-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="25f77-126">Türetilmiş sınıf oluşturucu sağlanan bağımsız değişkenler gelen kullanılan değerleri belirlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="25f77-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="25f77-127">Aşağıdaki kod, burada türetilmiş sınıf devralma yan tümcesinde temel sınıf oluşturucu çağırır bir taban sınıf ve türetilmiş bir sınıf gösterir:</span><span class="sxs-lookup"><span data-stu-id="25f77-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="25f77-128">Birden çok oluşturucular söz konusu olduğunda, aşağıdaki kod kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25f77-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="25f77-129">Türetilmiş sınıf oluşturucu ilk satırı `inherit` yan tümcesi ve alanlar görünür ile bildirilen açık alanlar olarak `val` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="25f77-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="25f77-130">Daha fazla bilgi için bkz: [açık alanlar: `val` anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="25f77-130">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="25f77-131">Devralma alternatifleri</span><span class="sxs-lookup"><span data-stu-id="25f77-131">Alternatives to Inheritance</span></span>
<span data-ttu-id="25f77-132">Küçük bir değişiklik türünün gerekli olduğu durumlarda, bir nesne ifadesi devralma alternatif olarak düşünün.</span><span class="sxs-lookup"><span data-stu-id="25f77-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="25f77-133">Aşağıdaki örnek yeni türetilmiş bir tür oluşturma alternatif olarak bir nesne ifadesi kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="25f77-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="25f77-134">Nesne ifadeleri hakkında daha fazla bilgi için bkz: [nesne ifadeleri](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="25f77-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="25f77-135">Nesne Hiyerarşileri oluştururken, ayrılmış bir birleşim yerine devralma kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="25f77-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="25f77-136">Ayrılmış birleşimler de ortak bir genel tür paylaşmak farklı nesneleri değişmesi modeli davranışını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25f77-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="25f77-137">Tek bir ayrılmış birleşim genellikle birbiriyle küçük farklılıkları olan türetilmiş sınıfları sayısı gereksinimini ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25f77-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="25f77-138">Ayrılmış birleşimler hakkında daha fazla bilgi için bkz: [ayrılmış birleşimler](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="25f77-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="25f77-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25f77-139">See Also</span></span>
[<span data-ttu-id="25f77-140">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="25f77-140">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="25f77-141">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="25f77-141">F# Language Reference</span></span>](index.md)
