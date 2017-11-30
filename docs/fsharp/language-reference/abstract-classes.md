---
title: "Soyut Sınıflar (F#)"
description: "Gerçeklenmemiş bazı veya tüm üyeleri bırakın F # soyut sınıfları hakkında bilgi edinin ve nesne türlerini farklı bir dizi ortak işlevselliğini temsil eder."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 209bcca70318db59506011b1f2bb74a09bf3814a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="abstract-classes"></a><span data-ttu-id="8f19a-104">Soyut sınıflar</span><span class="sxs-lookup"><span data-stu-id="8f19a-104">Abstract Classes</span></span>

<span data-ttu-id="8f19a-105">*Soyut sınıflar* gerçeklenmemiş, bazı veya tüm üyeleri bırakın ve böylece uygulamaları türetilmiş sınıfları tarafından sağlanabilir sınıflarıdır.</span><span class="sxs-lookup"><span data-stu-id="8f19a-105">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f19a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f19a-106">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="8f19a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f19a-107">Remarks</span></span>
<span data-ttu-id="8f19a-108">Nesne odaklı programlama, bir Özet sınıf bir hiyerarşinin temel sınıf olarak kullanılan ve farklı nesne türleri birtakım ortak işlevselliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f19a-108">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="8f19a-109">"Özet" adı da anlaşılacağı gibi soyut sınıflar doğrudan somut varlıklar sorun etki alanında oturum genellikle benzemez.</span><span class="sxs-lookup"><span data-stu-id="8f19a-109">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="8f19a-110">Ancak, bunlar ne birçok farklı somut varlıklar ortaktır temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f19a-110">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="8f19a-111">Soyut sınıflar olmalıdır `AbstractClass` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8f19a-111">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="8f19a-112">Bunlar sahip uygulanan ve üyeleri gerçeklenmemiş.</span><span class="sxs-lookup"><span data-stu-id="8f19a-112">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="8f19a-113">Terimi kullanımını *soyut* uygulandığında bir sınıfı diğer .NET dilleri; olduğu gibi aynıdır ancak terimi kullanımını *soyut* yöntemleri (ve özellikleri) uygulandığında biraz farklı bir F #'olan kendi Diğer .NET dilleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="8f19a-113">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="8f19a-114">F bir yöntem ile işaretlendiğinde, #, `abstract` anahtar sözcüğü, bu gösteren bir üye olarak bilinen bir giriş olduğunu bir *sanal dağıtım yuvası*, bu tür için sanal işlevleri iç tablosuna.</span><span class="sxs-lookup"><span data-stu-id="8f19a-114">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="8f19a-115">Diğer bir deyişle, sanal yöntemdir rağmen `virtual` anahtar sözcüğü F # dilinde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="8f19a-115">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="8f19a-116">Anahtar sözcüğü `abstract` olup yöntemin bağımsız olarak sanal yöntemler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f19a-116">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="8f19a-117">Bir sanal dağıtım yuvası bildirimi, o dağıtım yuvası için bir yöntem tanımını ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="8f19a-117">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="8f19a-118">Bu nedenle, F # sanal yöntem bildirimi ve tanımı başka bir .NET dilinde bir Özet yöntem bildirimi ve ile ya da ayrı bir tanımı bileşimini eşdeğerdir `default` anahtar sözcüğü veya `override` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8f19a-118">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="8f19a-119">Daha fazla bilgi ve örnekler için bkz: [yöntemleri](members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="8f19a-119">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="8f19a-120">Bir sınıf bildirildi, ancak tanımlı soyut yöntemler varsa soyut olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-120">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="8f19a-121">Bu nedenle, soyut yöntemler olan sınıfları mutlaka soyut sınıflar değildir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-121">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="8f19a-122">Bir sınıf soyut yöntemler tanımsız sürece kullanmayın **AbstractClass** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8f19a-122">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="8f19a-123">Önceki sözdiziminde *erişim değiştiricisi* olabilir `public`, `private` veya `internal`.</span><span class="sxs-lookup"><span data-stu-id="8f19a-123">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="8f19a-124">Daha fazla bilgi için bkz: [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="8f19a-124">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="8f19a-125">Soyut sınıflar diğer türleriyle gibi bir taban sınıf ve bir veya daha fazla arabirimleri temel sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-125">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="8f19a-126">Her bir temel sınıf veya arabirim ile birlikte ayrı bir satırda görünen `inherit` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8f19a-126">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="8f19a-127">Soyut bir sınıf türü tanımını tam olarak tanımlanan üyeler içerebilir, ancak soyut üyelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-127">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="8f19a-128">Soyut üyelerini sözdizimi önceki sözdiziminde ayrı olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-128">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="8f19a-129">Bu sözdiziminde *tür imzası* üyesi içeren bir liste sırası ve dönüş türleri parametre türleri ile ayrılır `->` belirteçleri ve/veya `*` belirteçler uygun şekilde curried için ve tupled parametreleri.</span><span class="sxs-lookup"><span data-stu-id="8f19a-129">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="8f19a-130">Soyut üye türü imzaları sözdizimi imza dosyalarında kullanılan ve IntelliSense Visual Studio Kod Düzenleyicisi'nde gösterilen aynı değil.</span><span class="sxs-lookup"><span data-stu-id="8f19a-130">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="8f19a-131">Aşağıdaki kod bir Özet sınıf iki Özet olmayan türetilen sınıflar, kare ve daire sahip şekli gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-131">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="8f19a-132">Örnek soyut sınıfları, yöntemleri ve özellikleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-132">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="8f19a-133">Örnekte, soyut sınıf şekli somut varlıklar daire ve kare ortak öğelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f19a-133">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="8f19a-134">Tüm şekillerde (iki boyutlu bir koordinat sistemi) ortak özelliklerini out şekli sınıfına soyutlanır: kılavuz, döndürme açısı ve alan ve çevre özellikleri konum.</span><span class="sxs-lookup"><span data-stu-id="8f19a-134">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="8f19a-135">Bunlar, hangi tek tek şekilleri değiştiremezsiniz davranışı konumu dışında geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-135">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="8f19a-136">Döndürme yöntemi, dönüş değişmez nedeniyle kendi simetrisi olan daire sınıfı olduğu gibi geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-136">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="8f19a-137">Bu nedenle daire sınıfında hiçbir şey yapmaz bir yöntemle döndürme yöntemi değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="8f19a-137">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="8f19a-138">**Çıktı:**</span><span class="sxs-lookup"><span data-stu-id="8f19a-138">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="8f19a-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f19a-139">See Also</span></span>
[<span data-ttu-id="8f19a-140">Sınıfları</span><span class="sxs-lookup"><span data-stu-id="8f19a-140">Classes</span></span>](classes.md)

[<span data-ttu-id="8f19a-141">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="8f19a-141">Members</span></span>](members/index.md)

[<span data-ttu-id="8f19a-142">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="8f19a-142">Methods</span></span>](members/methods.md)

[<span data-ttu-id="8f19a-143">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="8f19a-143">Properties</span></span>](members/Properties.md)
