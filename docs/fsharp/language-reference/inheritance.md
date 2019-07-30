---
title: Devralma
description: "' İnherit ' anahtar F# sözcüğünü kullanarak devralma ilişkilerini belirtmeyi öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627657"
---
# <a name="inheritance"></a><span data-ttu-id="8ca8a-103">Devralma</span><span class="sxs-lookup"><span data-stu-id="8ca8a-103">Inheritance</span></span>

<span data-ttu-id="8ca8a-104">Devralma, nesne odaklı programlamada "a-a" ilişkisini veya alt yazmayı modellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="8ca8a-105">Devralma Ilişkilerini belirtme</span><span class="sxs-lookup"><span data-stu-id="8ca8a-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="8ca8a-106">Devralma ilişkilerini bir sınıf bildiriminde `inherit` anahtar sözcüğünü kullanarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="8ca8a-107">Temel sözdizimsel form aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="8ca8a-108">Bir sınıf en fazla bir doğrudan temel sınıfa sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="8ca8a-109">`inherit` Anahtar sözcüğünü kullanarak bir temel sınıf belirtmezseniz, sınıf dolaylı olarak öğesinden `System.Object`devralır.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="8ca8a-110">Devralınan Üyeler</span><span class="sxs-lookup"><span data-stu-id="8ca8a-110">Inherited Members</span></span>

<span data-ttu-id="8ca8a-111">Bir sınıf başka bir sınıftan devralırsa, temel sınıfın yöntemleri ve üyeleri türetilmiş sınıfın doğrudan üyeleri gibi türetilmiş sınıfın kullanıcıları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="8ca8a-112">Tüm Let bağlamaları ve Oluşturucu parametreleri bir sınıfa özeldir ve bu nedenle türetilmiş sınıflardan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="8ca8a-113">Anahtar sözcüğü `base` türetilmiş sınıflarda kullanılabilir ve temel sınıf örneğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="8ca8a-114">Kendi kendine tanımlayıcı gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="8ca8a-115">Sanal yöntemler ve geçersiz kılmalar</span><span class="sxs-lookup"><span data-stu-id="8ca8a-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="8ca8a-116">Sanal Yöntemler (ve Özellikler), diğer .NET dilleri F# ile karşılaştırıldığında ' de biraz farklı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="8ca8a-117">Yeni bir sanal üye bildirmek için `abstract` anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="8ca8a-118">Bu yöntem için varsayılan bir uygulama sağlayıp sağlamadığına bakılmaksızın bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="8ca8a-119">Bu nedenle, bir temel sınıftaki sanal bir yöntemin tüm tanımı bu modele uyar:</span><span class="sxs-lookup"><span data-stu-id="8ca8a-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="8ca8a-120">Türetilmiş bir sınıfta, bu sanal yöntemin bir geçersiz kılma bu düzene uyar:</span><span class="sxs-lookup"><span data-stu-id="8ca8a-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="8ca8a-121">Temel sınıfta varsayılan uygulamayı atlarsanız, temel sınıf bir soyut sınıf olur.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="8ca8a-122">Aşağıdaki kod örneği, bir temel sınıftaki yeni bir sanal yöntemin `function1` bildirimini ve türetilmiş bir sınıfta bunun nasıl geçersiz kılınacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="8ca8a-123">Oluşturucular ve devralma</span><span class="sxs-lookup"><span data-stu-id="8ca8a-123">Constructors and Inheritance</span></span>

<span data-ttu-id="8ca8a-124">Temel sınıfa yönelik oluşturucunun türetilmiş sınıfta çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="8ca8a-125">Temel sınıf oluşturucusunun bağımsız değişkenleri, `inherit` yan tümcesindeki bağımsız değişken listesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="8ca8a-126">Kullanılan değerlerin, türetilmiş sınıf oluşturucusuna sağlanan bağımsız değişkenlerden belirlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="8ca8a-127">Aşağıdaki kod, bir temel sınıf ve türetilmiş bir sınıf gösterir; burada türetilmiş sınıf, devralma yan tümcesinde temel sınıf oluşturucusunu çağırır:</span><span class="sxs-lookup"><span data-stu-id="8ca8a-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="8ca8a-128">Birden çok Oluşturucu söz konusu olduğunda, aşağıdaki kod kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="8ca8a-129">Türetilmiş sınıf oluşturucularının ilk satırı `inherit` yan tümcelerdir ve alanlar, `val` anahtar sözcüğüyle belirtilen açık alanlar olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="8ca8a-130">Daha fazla bilgi için bkz [. açık alanlar: `val` Anahtar sözcüğü](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="8ca8a-130">For more information, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="8ca8a-131">Devralma alternatifleri</span><span class="sxs-lookup"><span data-stu-id="8ca8a-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="8ca8a-132">Bir tür için küçük bir değişikliğin gerekli olduğu durumlarda, devralma için alternatif olarak bir nesne ifadesi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="8ca8a-133">Aşağıdaki örnek, yeni bir türetilmiş tür oluşturmaya alternatif olarak bir nesne ifadesinin kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8ca8a-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="8ca8a-134">Nesne ifadeleri hakkında daha fazla bilgi için bkz. [nesne ifadeleri](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8ca8a-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="8ca8a-135">Nesne hiyerarşileri oluştururken, devralma yerine ayrılmış bir birleşim kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="8ca8a-136">Ayırt edici birleşimler ayrıca ortak bir genel türü paylaşan farklı nesnelerin değişen davranışlarını modelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="8ca8a-137">Tek bir ayırt edici birleşim genellikle birbirleriyle ilgili küçük farklılıklar olan bir dizi türetilmiş sınıfa gereksinimi ortadan kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="8ca8a-138">Ayrılmış birleşimler hakkında daha fazla bilgi için bkz. [ayırt edici birleşimler](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="8ca8a-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ca8a-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-139">See also</span></span>

- [<span data-ttu-id="8ca8a-140">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="8ca8a-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="8ca8a-141">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8ca8a-141">F# Language Reference</span></span>](index.md)
