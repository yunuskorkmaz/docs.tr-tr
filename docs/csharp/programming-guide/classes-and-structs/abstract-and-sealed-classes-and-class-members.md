---
title: Soyut ve korumalı sınıflar ve sınıf üyeleri-C# Programlama Kılavuzu
description: C# içindeki abstract anahtar sözcüğü tamamlanmamış sınıflar ve sınıf üyeleri oluşturur. Sealed anahtar sözcüğü, daha önce sanal sınıfların veya sınıf üyelerinin devralınmasını önler.
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: ccbc6734d4e9bafe059dd45bfdf82af7c84438a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204040"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="a152c-104">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a152c-104">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>

<span data-ttu-id="a152c-105">[Abstract](../../language-reference/keywords/abstract.md) anahtar sözcüğü, tamamlanmamış ve türetilmiş bir sınıfta uygulanması gereken sınıflar ve [sınıf](../../language-reference/keywords/class.md) üyeleri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a152c-105">The [abstract](../../language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="a152c-106">[Sealed](../../language-reference/keywords/sealed.md) anahtar sözcüğü, bir sınıfın devralınmasını veya daha önce [sanal](../../language-reference/keywords/virtual.md)olarak işaretlenmiş belirli sınıf üyelerini engellemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a152c-106">The [sealed](../../language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="a152c-107">Soyut sınıflar ve sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="a152c-107">Abstract Classes and Class Members</span></span>  

 <span data-ttu-id="a152c-108">Sınıflar, sınıf tanımından önce anahtar sözcüğü yerleştirilerek soyut olarak bildirilemez `abstract` .</span><span class="sxs-lookup"><span data-stu-id="a152c-108">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="a152c-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a152c-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 <span data-ttu-id="a152c-110">Soyut bir sınıf örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="a152c-110">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="a152c-111">Soyut bir sınıfın amacı, birden fazla türetilmiş sınıfın paylaşabileceği bir temel sınıfın ortak bir tanımını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a152c-111">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="a152c-112">Örneğin, bir sınıf kitaplığı, işlevlerinin çoğuna parametre olarak kullanılan bir soyut sınıfı tanımlayabilir ve bir türetilmiş sınıf oluşturarak bu kitaplığı kullanan programcıların, sınıfının kendi uygulamasını sağlamasını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="a152c-112">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="a152c-113">Soyut sınıflar, Soyut yöntemler de tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a152c-113">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="a152c-114">Bu, `abstract` yönteminin dönüş türünden önce anahtar sözcüğü eklenerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="a152c-114">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="a152c-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a152c-115">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 <span data-ttu-id="a152c-116">Soyut yöntemlerin hiçbir uygulamaya sahip olmadığı için, yöntem tanımının normal yöntem bloğu yerine noktalı virgül gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="a152c-116">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="a152c-117">Soyut sınıfın türetilmiş sınıfları tüm soyut yöntemleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a152c-117">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="a152c-118">Bir soyut sınıf bir temel sınıftan sanal bir yöntemi devralıyorsa, soyut sınıf, soyut bir yöntemle sanal yöntemi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="a152c-118">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="a152c-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a152c-119">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 <span data-ttu-id="a152c-120">Bir `virtual` Yöntem bildirilirse `abstract` , soyut sınıftan devralan herhangi bir sınıfta hala sanal olur.</span><span class="sxs-lookup"><span data-stu-id="a152c-120">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="a152c-121">Soyut bir yöntemi devralan sınıf, yöntemin orijinal uygulamasına erişemez — önceki örnekte, `DoWork` F sınıfı üzerinde, `DoWork` D sınıfı üzerinde çağrılamaz. Bu şekilde, soyut bir sınıf, türetilmiş sınıfları sanal yöntemler için yeni yöntem uygulamaları sağlamaya zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a152c-121">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="a152c-122">Korumalı sınıflar ve sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="a152c-122">Sealed Classes and Class Members</span></span>  

 <span data-ttu-id="a152c-123">Sınıflar, sınıf tanımından önce anahtar sözcüğü yerleştirilerek [Sealed](../../language-reference/keywords/sealed.md) olarak bildirilebilecek `sealed` .</span><span class="sxs-lookup"><span data-stu-id="a152c-123">Classes can be declared as [sealed](../../language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="a152c-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a152c-124">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 <span data-ttu-id="a152c-125">Sealed bir sınıf temel sınıf olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a152c-125">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="a152c-126">Bu nedenle, bir soyut sınıf de olamaz.</span><span class="sxs-lookup"><span data-stu-id="a152c-126">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="a152c-127">Sealed sınıflar türetmeye engel.</span><span class="sxs-lookup"><span data-stu-id="a152c-127">Sealed classes prevent derivation.</span></span> <span data-ttu-id="a152c-128">Bunlar hiçbir zaman temel sınıf olarak kullanılabileceğinden, bazı çalışma zamanı iyileştirmeleri sealed sınıf üyelerinin çağrılmasını biraz daha hızlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a152c-128">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="a152c-129">Temel sınıfın bir sanal üyesini geçersiz kılan türetilmiş bir sınıfta bir yöntem, Dizin Oluşturucu, özellik veya olay bu üyeyi korumalı olarak bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="a152c-129">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="a152c-130">Bu, daha fazla türetilmiş sınıf için üyenin sanal yönünü geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a152c-130">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="a152c-131">Bu, `sealed` anahtar sözcüğü, sınıf üye bildirimindeki [override](../../language-reference/keywords/override.md) anahtar sözcüğünden önce yerleştirilerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a152c-131">This is accomplished by putting the `sealed` keyword before the [override](../../language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="a152c-132">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a152c-132">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="a152c-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a152c-133">See also</span></span>

- [<span data-ttu-id="a152c-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a152c-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a152c-135">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="a152c-135">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="a152c-136">Devralma</span><span class="sxs-lookup"><span data-stu-id="a152c-136">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="a152c-137">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a152c-137">Methods</span></span>](./methods.md)
- [<span data-ttu-id="a152c-138">Alanlar</span><span class="sxs-lookup"><span data-stu-id="a152c-138">Fields</span></span>](./fields.md)
- [<span data-ttu-id="a152c-139">Soyut özellikleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="a152c-139">How to define abstract properties</span></span>](./how-to-define-abstract-properties.md)
