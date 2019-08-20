---
title: Soyut ve korumalı sınıflar ve sınıf üyeleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 1c98e2979ee96d4bcc885b8cc797eaac28c8d2ed
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597298"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="210a8-102">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="210a8-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="210a8-103">[Abstract](../../language-reference/keywords/abstract.md) anahtar sözcüğü, tamamlanmamış ve türetilmiş bir sınıfta uygulanması gereken sınıflar ve [sınıf](../../language-reference/keywords/class.md) üyeleri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="210a8-103">The [abstract](../../language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="210a8-104">[Sealed](../../language-reference/keywords/sealed.md) anahtar sözcüğü, bir sınıfın devralınmasını veya daha önce [sanal](../../language-reference/keywords/virtual.md)olarak işaretlenmiş belirli sınıf üyelerini engellemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="210a8-104">The [sealed](../../language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="210a8-105">Soyut sınıflar ve sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="210a8-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="210a8-106">Sınıflar, sınıf tanımından önce anahtar sözcüğü `abstract` yerleştirilerek soyut olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="210a8-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="210a8-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="210a8-107">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 <span data-ttu-id="210a8-108">Soyut bir sınıf örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="210a8-108">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="210a8-109">Soyut bir sınıfın amacı, birden fazla türetilmiş sınıfın paylaşabileceği bir temel sınıfın ortak bir tanımını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="210a8-109">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="210a8-110">Örneğin, bir sınıf kitaplığı, işlevlerinin çoğuna parametre olarak kullanılan bir soyut sınıfı tanımlayabilir ve bir türetilmiş sınıf oluşturarak bu kitaplığı kullanan programcıların, sınıfının kendi uygulamasını sağlamasını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="210a8-110">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="210a8-111">Soyut sınıflar, Soyut yöntemler de tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="210a8-111">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="210a8-112">Bu, yönteminin dönüş türünden önce anahtar `abstract` sözcüğü eklenerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="210a8-112">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="210a8-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="210a8-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 <span data-ttu-id="210a8-114">Soyut yöntemlerin hiçbir uygulamaya sahip olmadığı için, yöntem tanımının normal yöntem bloğu yerine noktalı virgül gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="210a8-114">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="210a8-115">Soyut sınıfın türetilmiş sınıfları tüm soyut yöntemleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="210a8-115">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="210a8-116">Bir soyut sınıf bir temel sınıftan sanal bir yöntemi devralıyorsa, soyut sınıf, soyut bir yöntemle sanal yöntemi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="210a8-116">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="210a8-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="210a8-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 <span data-ttu-id="210a8-118">Bir `virtual` Yöntem bildirilirse `abstract`, soyut sınıftan devralan herhangi bir sınıfta hala sanal olur.</span><span class="sxs-lookup"><span data-stu-id="210a8-118">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="210a8-119">Soyut bir yöntemi devralan sınıf, yöntemin orijinal uygulamasına erişemez — önceki örnekte, F sınıfı üzerinde, `DoWork` D sınıfı üzerinde çağrılamaz. `DoWork` Bu şekilde, soyut bir sınıf, türetilmiş sınıfları sanal yöntemler için yeni yöntem uygulamaları sağlamaya zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="210a8-119">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="210a8-120">Korumalı sınıflar ve sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="210a8-120">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="210a8-121">Sınıflar, sınıf tanımından önce [](../../language-reference/keywords/sealed.md) anahtar sözcüğü `sealed` yerleştirilerek Sealed olarak bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="210a8-121">Classes can be declared as [sealed](../../language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="210a8-122">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="210a8-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 <span data-ttu-id="210a8-123">Sealed bir sınıf temel sınıf olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="210a8-123">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="210a8-124">Bu nedenle, bir soyut sınıf de olamaz.</span><span class="sxs-lookup"><span data-stu-id="210a8-124">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="210a8-125">Sealed sınıflar türetmeye engel.</span><span class="sxs-lookup"><span data-stu-id="210a8-125">Sealed classes prevent derivation.</span></span> <span data-ttu-id="210a8-126">Bunlar hiçbir zaman temel sınıf olarak kullanılabileceğinden, bazı çalışma zamanı iyileştirmeleri sealed sınıf üyelerinin çağrılmasını biraz daha hızlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="210a8-126">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="210a8-127">Temel sınıfın bir sanal üyesini geçersiz kılan türetilmiş bir sınıfta bir yöntem, Dizin Oluşturucu, özellik veya olay bu üyeyi korumalı olarak bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="210a8-127">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="210a8-128">Bu, daha fazla türetilmiş sınıf için üyenin sanal yönünü geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="210a8-128">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="210a8-129">Bu, `sealed` anahtar sözcüğü, sınıf üye bildirimindeki [override](../../language-reference/keywords/override.md) anahtar sözcüğünden önce yerleştirilerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="210a8-129">This is accomplished by putting the `sealed` keyword before the [override](../../language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="210a8-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="210a8-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="210a8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="210a8-131">See also</span></span>

- [<span data-ttu-id="210a8-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="210a8-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="210a8-133">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="210a8-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="210a8-134">Devralma</span><span class="sxs-lookup"><span data-stu-id="210a8-134">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="210a8-135">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="210a8-135">Methods</span></span>](./methods.md)
- [<span data-ttu-id="210a8-136">Alanlar</span><span class="sxs-lookup"><span data-stu-id="210a8-136">Fields</span></span>](./fields.md)
- [<span data-ttu-id="210a8-137">Nasıl yapılır: Soyut özellikleri tanımla</span><span class="sxs-lookup"><span data-stu-id="210a8-137">How to: Define Abstract Properties</span></span>](./how-to-define-abstract-properties.md)
