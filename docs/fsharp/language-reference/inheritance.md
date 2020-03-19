---
title: Devralma
description: "'Devralma' anahtar sözcük anahtar sözcüklerini kullanarak F# kalıtım ilişkilerini nasıl belirteceklerini öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400290"
---
# <a name="inheritance"></a><span data-ttu-id="7f328-103">Devralma</span><span class="sxs-lookup"><span data-stu-id="7f328-103">Inheritance</span></span>

<span data-ttu-id="7f328-104">Kalıtım, nesne yönelimli programlamada "is-a" ilişkisini veya alt yazımayı modellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f328-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="7f328-105">Kalıtım İlişkileri Belirtme</span><span class="sxs-lookup"><span data-stu-id="7f328-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="7f328-106">Bir sınıf bildiriminde `inherit` anahtar kelimeyi kullanarak devralma ilişkilerini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f328-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="7f328-107">Temel sözdizimsel form aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f328-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="7f328-108">Bir sınıfın en fazla bir doğrudan taban sınıfı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f328-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="7f328-109">`inherit` Anahtar sözcüğü kullanarak bir taban sınıf belirtmezseniz, sınıf örtülü `System.Object`olarak .</span><span class="sxs-lookup"><span data-stu-id="7f328-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="7f328-110">Devralınmış Üyeler</span><span class="sxs-lookup"><span data-stu-id="7f328-110">Inherited Members</span></span>

<span data-ttu-id="7f328-111">Bir sınıf başka bir sınıftan devralıyorsa, taban sınıfın yöntemleri ve üyeleri türemiş sınıfın doğrudan üyeleriymiş gibi türemiş sınıfın kullanıcıları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7f328-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="7f328-112">Herhangi bir izin bağlamaları ve oluşturucu parametreleri bir sınıfa özeldir ve bu nedenle türemiş sınıflardan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="7f328-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="7f328-113">Anahtar kelime `base` türemiş sınıflarda kullanılabilir ve taban sınıf örneğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="7f328-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="7f328-114">Kendini tanımlayıcı gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f328-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="7f328-115">Sanal Yöntemler ve Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="7f328-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="7f328-116">Sanal yöntemler (ve özellikler) F#'da diğer .NET dillerine göre biraz farklı çalışır.</span><span class="sxs-lookup"><span data-stu-id="7f328-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="7f328-117">Yeni bir sanal üye bildirmek `abstract` için anahtar kelimeyi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="7f328-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="7f328-118">Bu yöntem için varsayılan bir uygulama sağlayıp sağlamadığınıza bakılmaksızın bunu yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="7f328-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="7f328-119">Böylece bir taban sınıfta sanal yöntemin tam bir tanımı aşağıdaki şekilde dir:</span><span class="sxs-lookup"><span data-stu-id="7f328-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="7f328-120">Ve türetilmiş bir sınıfta, bu sanal yöntemin geçersiz kılma bu desen izler:</span><span class="sxs-lookup"><span data-stu-id="7f328-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="7f328-121">Taban sınıfta varsayılan uygulamayı atlarsanız, taban sınıf soyut bir sınıf olur.</span><span class="sxs-lookup"><span data-stu-id="7f328-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="7f328-122">Aşağıdaki kod örneği, taban sınıfta yeni `function1` bir sanal yöntemin bildirimini ve türetilmiş bir sınıfta nasıl geçersiz kılındığını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7f328-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="7f328-123">Yapıcılar ve Kalıtım</span><span class="sxs-lookup"><span data-stu-id="7f328-123">Constructors and Inheritance</span></span>

<span data-ttu-id="7f328-124">Taban sınıfın oluşturucusu türemiş sınıfta çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f328-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="7f328-125">Taban sınıf oluşturucuiçin bağımsız değişkenler `inherit` yan tümcedeki bağımsız değişken listesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="7f328-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="7f328-126">Kullanılan değerler türemiş sınıf oluşturucuya sağlanan bağımsız değişkenlerden belirlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="7f328-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="7f328-127">Aşağıdaki kod, türemiş sınıfın devralma yan tümcesinde taban sınıf oluşturucuyu çağırdığı bir taban sınıf ve türetilmiş sınıf gösterir:</span><span class="sxs-lookup"><span data-stu-id="7f328-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="7f328-128">Birden çok oluşturucu söz konusu olduğunda, aşağıdaki kod kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7f328-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="7f328-129">Türemiş sınıf oluşturucularının ilk `inherit` satırı yan tümcedir ve alanlar `val` anahtar sözcükle birlikte bildirilen açık alanlar olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="7f328-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="7f328-130">Daha fazla bilgi için [bkz: Açık Alanlar: `val` Anahtar Kelime.](./members/explicit-fields-the-val-keyword.md)</span><span class="sxs-lookup"><span data-stu-id="7f328-130">For more information, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="7f328-131">Kalıtıma Alternatifler</span><span class="sxs-lookup"><span data-stu-id="7f328-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="7f328-132">Bir türün küçük bir değişiklik gerekli olduğu durumlarda, devralma alternatif olarak bir nesne ifadesi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="7f328-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="7f328-133">Aşağıdaki örnekte, nesne ifadesinin yeni bir türetilmiş tür oluşturmaya alternatif olarak kullanılması gösteriş verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7f328-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="7f328-134">Nesne ifadeleri hakkında daha fazla bilgi için [bkz.](object-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="7f328-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="7f328-135">Nesne hiyerarşileri oluştururken, devralma yerine ayrımcı bir birliktelik kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="7f328-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="7f328-136">Ayrımcı birgörünüm, ortak bir genel türü paylaşan farklı nesnelerin çeşitli davranışlarını da modelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7f328-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="7f328-137">Tek bir ayrımcı birliktelik genellikle birbirinin küçük varyasyonları olan türemiş sınıflar bir dizi ihtiyacını ortadan kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="7f328-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="7f328-138">Ayrımcı sendikalar hakkında bilgi için [bkz.](discriminated-unions.md)</span><span class="sxs-lookup"><span data-stu-id="7f328-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f328-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f328-139">See also</span></span>

- [<span data-ttu-id="7f328-140">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7f328-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="7f328-141">F# Dil Referansı</span><span class="sxs-lookup"><span data-stu-id="7f328-141">F# Language Reference</span></span>](index.md)
