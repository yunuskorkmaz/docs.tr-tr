---
title: Soyut Sınıflar (F#)
description: 'Gerçeklenmemiş bazı veya tüm üyeleri bırakın F # soyut sınıfları hakkında bilgi edinin ve nesne türlerini farklı bir dizi ortak işlevselliğini temsil eder.'
ms.date: 05/16/2016
ms.openlocfilehash: c472e9d164ae78bde716bb5102e54f4e698b61b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562396"
---
# <a name="abstract-classes"></a><span data-ttu-id="bee06-103">Soyut sınıflar</span><span class="sxs-lookup"><span data-stu-id="bee06-103">Abstract Classes</span></span>

<span data-ttu-id="bee06-104">*Soyut sınıflar* gerçeklenmemiş, bazı veya tüm üyeleri bırakın ve böylece uygulamaları türetilmiş sınıfları tarafından sağlanabilir sınıflarıdır.</span><span class="sxs-lookup"><span data-stu-id="bee06-104">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="bee06-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bee06-105">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="bee06-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bee06-106">Remarks</span></span>
<span data-ttu-id="bee06-107">Nesne odaklı programlama, bir Özet sınıf bir hiyerarşinin temel sınıf olarak kullanılan ve farklı nesne türleri birtakım ortak işlevselliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bee06-107">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="bee06-108">"Özet" adı da anlaşılacağı gibi soyut sınıflar doğrudan somut varlıklar sorun etki alanında oturum genellikle benzemez.</span><span class="sxs-lookup"><span data-stu-id="bee06-108">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="bee06-109">Ancak, bunlar ne birçok farklı somut varlıklar ortaktır temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bee06-109">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="bee06-110">Soyut sınıflar olmalıdır `AbstractClass` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bee06-110">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="bee06-111">Bunlar sahip uygulanan ve üyeleri gerçeklenmemiş.</span><span class="sxs-lookup"><span data-stu-id="bee06-111">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="bee06-112">Terimi kullanımını *soyut* uygulandığında bir sınıfı diğer .NET dilleri; olduğu gibi aynıdır ancak terimi kullanımını *soyut* yöntemleri (ve özellikleri) uygulandığında biraz farklı bir F #'olan kendi Diğer .NET dilleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="bee06-112">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="bee06-113">F bir yöntem ile işaretlendiğinde, #, `abstract` anahtar sözcüğü, bu gösteren bir üye olarak bilinen bir giriş olduğunu bir *sanal dağıtım yuvası*, bu tür için sanal işlevleri iç tablosuna.</span><span class="sxs-lookup"><span data-stu-id="bee06-113">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="bee06-114">Diğer bir deyişle, sanal yöntemdir rağmen `virtual` anahtar sözcüğü F # dilinde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="bee06-114">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="bee06-115">Anahtar sözcüğü `abstract` olup yöntemin bağımsız olarak sanal yöntemler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bee06-115">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="bee06-116">Bir sanal dağıtım yuvası bildirimi, o dağıtım yuvası için bir yöntem tanımını ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="bee06-116">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="bee06-117">Bu nedenle, F # sanal yöntem bildirimi ve tanımı başka bir .NET dilinde bir Özet yöntem bildirimi ve ile ya da ayrı bir tanımı bileşimini eşdeğerdir `default` anahtar sözcüğü veya `override` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bee06-117">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="bee06-118">Daha fazla bilgi ve örnekler için bkz: [yöntemleri](members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="bee06-118">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="bee06-119">Bir sınıf bildirildi, ancak tanımlı soyut yöntemler varsa soyut olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="bee06-119">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="bee06-120">Bu nedenle, soyut yöntemler olan sınıfları mutlaka soyut sınıflar değildir.</span><span class="sxs-lookup"><span data-stu-id="bee06-120">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="bee06-121">Bir sınıf soyut yöntemler tanımsız sürece kullanmayın **AbstractClass** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bee06-121">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="bee06-122">Önceki sözdiziminde *erişim değiştiricisi* olabilir `public`, `private` veya `internal`.</span><span class="sxs-lookup"><span data-stu-id="bee06-122">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="bee06-123">Daha fazla bilgi için bkz: [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="bee06-123">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="bee06-124">Soyut sınıflar diğer türleriyle gibi bir taban sınıf ve bir veya daha fazla arabirimleri temel sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="bee06-124">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="bee06-125">Her bir temel sınıf veya arabirim ile birlikte ayrı bir satırda görünen `inherit` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bee06-125">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="bee06-126">Soyut bir sınıf türü tanımını tam olarak tanımlanan üyeler içerebilir, ancak soyut üyelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bee06-126">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="bee06-127">Soyut üyelerini sözdizimi önceki sözdiziminde ayrı olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="bee06-127">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="bee06-128">Bu sözdiziminde *tür imzası* üyesi içeren bir liste sırası ve dönüş türleri parametre türleri ile ayrılır `->` belirteçleri ve/veya `*` belirteçler uygun şekilde curried için ve tupled parametreleri.</span><span class="sxs-lookup"><span data-stu-id="bee06-128">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="bee06-129">Soyut üye türü imzaları sözdizimi imza dosyalarında kullanılan ve IntelliSense Visual Studio Kod Düzenleyicisi'nde gösterilen aynı değil.</span><span class="sxs-lookup"><span data-stu-id="bee06-129">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="bee06-130">Aşağıdaki kod bir Özet sınıf iki Özet olmayan türetilen sınıflar, kare ve daire sahip şekli gösterir.</span><span class="sxs-lookup"><span data-stu-id="bee06-130">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="bee06-131">Örnek soyut sınıfları, yöntemleri ve özellikleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bee06-131">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="bee06-132">Örnekte, soyut sınıf şekli somut varlıklar daire ve kare ortak öğelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bee06-132">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="bee06-133">Tüm şekillerde (iki boyutlu bir koordinat sistemi) ortak özelliklerini out şekli sınıfına soyutlanır: kılavuz, döndürme açısı ve alan ve çevre özellikleri konum.</span><span class="sxs-lookup"><span data-stu-id="bee06-133">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="bee06-134">Bunlar, hangi tek tek şekilleri değiştiremezsiniz davranışı konumu dışında geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="bee06-134">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="bee06-135">Döndürme yöntemi, dönüş değişmez nedeniyle kendi simetrisi olan daire sınıfı olduğu gibi geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="bee06-135">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="bee06-136">Bu nedenle daire sınıfında hiçbir şey yapmaz bir yöntemle döndürme yöntemi değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="bee06-136">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="bee06-137">**Çıktı:**</span><span class="sxs-lookup"><span data-stu-id="bee06-137">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="bee06-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bee06-138">See Also</span></span>
[<span data-ttu-id="bee06-139">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="bee06-139">Classes</span></span>](classes.md)

[<span data-ttu-id="bee06-140">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bee06-140">Members</span></span>](members/index.md)

[<span data-ttu-id="bee06-141">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bee06-141">Methods</span></span>](members/methods.md)

[<span data-ttu-id="bee06-142">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bee06-142">Properties</span></span>](members/Properties.md)
