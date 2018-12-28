---
title: Devralma
description: Nasıl belirleyeceğinizi öğrenin F# kalıtım ilişkileri Devral' anahtar sözcüğü kullanılarak.
ms.date: 05/16/2016
ms.openlocfilehash: 775ee52039caf4c4ab65f82fa21d4e536135a12a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610144"
---
# <a name="inheritance"></a><span data-ttu-id="5d6ea-103">Devralma</span><span class="sxs-lookup"><span data-stu-id="5d6ea-103">Inheritance</span></span>

<span data-ttu-id="5d6ea-104">Devralma "olan bir" ilişkileri modellemek için kullanılan veya, nesne yönelimli programlama subtyping.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="5d6ea-105">Kalıtım ilişkileri belirtme</span><span class="sxs-lookup"><span data-stu-id="5d6ea-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="5d6ea-106">Devralma ilişkilerinde kullanarak belirttiğiniz `inherit` anahtar sözcüğü bir sınıf bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="5d6ea-107">Temel söz dizimi biçimi, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="5d6ea-108">Bir sınıf, en fazla bir doğrudan temel sınıf olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="5d6ea-109">Bir taban sınıfı kullanarak belirtmezseniz `inherit` anahtar sözcüğü, örtük olarak sınıfının devraldığı `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="5d6ea-110">Devralınan üyeler</span><span class="sxs-lookup"><span data-stu-id="5d6ea-110">Inherited Members</span></span>

<span data-ttu-id="5d6ea-111">Bir sınıf başka bir sınıftan devralınırsa, yöntemleri ve temel sınıfın üyelerine doğrudan üyesi türetilmiş sınıf değilmiş gibi türetilmiş sınıf kullanıcıları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="5d6ea-112">Let bağlamaları ve oluşturucu parametresi bir sınıfa özeldir ve bu nedenle, türetilmiş sınıflardan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="5d6ea-113">Anahtar sözcüğü `base` türetilmiş sınıflarda kullanılabilir ve temel sınıf örneğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="5d6ea-114">Bu gibi kendi kendine tanımlayıcı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="5d6ea-115">Sanal yöntemleri ve geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="5d6ea-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="5d6ea-116">Sanal yöntemler (ve Özellikler) iş içinde biraz farklı F# diğer .NET dilleri ile karşılaştırıldığında.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="5d6ea-117">Yeni bir sanal üye bildirmek için kullandığınız `abstract` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="5d6ea-118">Bunun için bu yöntem için varsayılan bir uygulama sağlamak ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="5d6ea-119">Bu nedenle tam bir temel sınıf sanal yöntemin tanımı bu düzen aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5d6ea-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="5d6ea-120">Ve türetilen bir sınıfta sanal bu yöntemin bir geçersiz kılma şu desene uygun olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="5d6ea-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="5d6ea-121">Varsayılan uygulama temel sınıfta atlarsanız, temel sınıfı soyut bir sınıf olur.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="5d6ea-122">Aşağıdaki kod örneğinde yeni bir sanal yöntemle bildirimi gösterilmektedir `function1` bir temel sınıf ve türetilen bir sınıfta geçersiz öğrenin.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="5d6ea-123">Oluşturucular ve devralma</span><span class="sxs-lookup"><span data-stu-id="5d6ea-123">Constructors and Inheritance</span></span>

<span data-ttu-id="5d6ea-124">Türetilmiş sınıf içinde temel sınıf için oluşturucu çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="5d6ea-125">Temel sınıf oluşturucusu için bağımsız değişken listesinde görünür `inherit` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="5d6ea-126">Öğesinden türetilen sınıf oluşturucusu için sağlanan bağımsız değişkenler kullanılan değerleri belirlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="5d6ea-127">Aşağıdaki kod, burada türetilmiş sınıf devralma yan tümcesinde temel sınıf oluşturucusunu çağırır, bir temel sınıf ve türetilmiş bir sınıf gösterir:</span><span class="sxs-lookup"><span data-stu-id="5d6ea-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="5d6ea-128">Birden çok Oluşturucu söz konusu olduğunda, aşağıdaki kod kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="5d6ea-129">Türetilmiş sınıf oluşturucular ilk satırının `inherit` yan tümcesi ve alanları ile bildirilen açık alanlar olarak görünür `val` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="5d6ea-130">Daha fazla bilgi için [açık alanlar: `val` Anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ea-130">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="5d6ea-131">Devralma alternatifleri</span><span class="sxs-lookup"><span data-stu-id="5d6ea-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="5d6ea-132">Küçük bir değişiklik türünün gerekli olduğu durumlarda, devralma alternatif olarak bir nesne ifadesi kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="5d6ea-133">Aşağıdaki örnek, bir nesne ifadesi yeni bir türetilmiş tür oluşturma için alternatif olarak kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5d6ea-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="5d6ea-134">Nesne ifadeleri hakkında daha fazla bilgi için bkz: [nesne ifadeleri](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ea-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="5d6ea-135">Nesne Hiyerarşileri oluştururken, devralma yerine ayrılmış bir birleşim kullanarak göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="5d6ea-136">Ayrılmış birleşimler, ortak bir genel türü farklı nesne modeli değiştirilen davranışı da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="5d6ea-137">Tek bir birleşimdir genellikle birkaç küçük farklılıklar birbiriyle olan türetilen sınıfların gereksinimini ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="5d6ea-138">Ayrılmış birleşimler hakkında daha fazla bilgi için bkz. [ayırt edici birleşimler](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ea-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d6ea-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d6ea-139">See also</span></span>

- [<span data-ttu-id="5d6ea-140">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="5d6ea-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="5d6ea-141">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5d6ea-141">F# Language Reference</span></span>](index.md)