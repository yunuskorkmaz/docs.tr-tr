---
title: Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 07738031f1dec05424f7c3756f49a8f1f9a2c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715003"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="bb31c-102">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bb31c-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="bb31c-103">[Soyut](../../language-reference/keywords/abstract.md) anahtar kelime, eksik olan ve türemiş bir sınıfta uygulanması gereken sınıflar ve [sınıf](../../language-reference/keywords/class.md) üyeleri oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bb31c-103">The [abstract](../../language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="bb31c-104">[Mühürlü](../../language-reference/keywords/sealed.md) anahtar kelime, daha önce [sanal](../../language-reference/keywords/virtual.md)olarak işaretlenmiş bir sınıfın veya belirli sınıf üyelerinin devrinin engellenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb31c-104">The [sealed](../../language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="bb31c-105">Soyut Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="bb31c-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="bb31c-106">Sınıflar, anahtar sözcüğü `abstract` sınıf tanımının önüne koyarak soyut olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="bb31c-107">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bb31c-107">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 <span data-ttu-id="bb31c-108">Soyut bir sınıf anında alınamaz.</span><span class="sxs-lookup"><span data-stu-id="bb31c-108">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="bb31c-109">Soyut sınıfın amacı, birden çok türetilmiş sınıfın paylaşabileceği bir taban sınıfın ortak bir tanımını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="bb31c-109">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="bb31c-110">Örneğin, bir sınıf kitaplığı, işlevlerinin çoğu için parametre olarak kullanılan soyut bir sınıf tanımlayabilir ve türemiş bir sınıf oluşturarak sınıfın kendi uygulamasını sağlamak için bu kitaplığı kullanan programcılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-110">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="bb31c-111">Soyut sınıflar soyut yöntemleri de tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-111">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="bb31c-112">Bu yöntemin dönüş türünden `abstract` önce anahtar kelime ekleyerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-112">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="bb31c-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bb31c-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 <span data-ttu-id="bb31c-114">Soyut yöntemlerin uygulanması yoktur, bu nedenle yöntem tanımı normal bir yöntem bloğu yerine bir yarı kolon tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-114">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="bb31c-115">Soyut sınıfın türemiş sınıfları tüm soyut yöntemleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb31c-115">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="bb31c-116">Soyut bir sınıf bir temel sınıftan sanal bir yöntem devraldığında, soyut sınıf soyut bir yöntemle sanal yöntemi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-116">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="bb31c-117">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bb31c-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 <span data-ttu-id="bb31c-118">Bir `virtual` yöntem bildirilirse, `abstract`soyut sınıftan devralan herhangi bir sınıf için hala sanaldır.</span><span class="sxs-lookup"><span data-stu-id="bb31c-118">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="bb31c-119">Soyut bir yöntem devralan bir sınıf yöntemin özgün uygulamasına `DoWork` erişemez—önceki `DoWork` örnekte, F sınıfında D sınıfı çağrı yapamaz. Bu şekilde, soyut bir sınıf türemiş sınıfları sanal yöntemler için yeni yöntem uygulamaları sağlamaya zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-119">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="bb31c-120">Mühürlü Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="bb31c-120">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="bb31c-121">Sınıflar, anahtar kelime `sealed` sınıf tanımının önüne konularak [mühürlenmiş](../../language-reference/keywords/sealed.md) olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-121">Classes can be declared as [sealed](../../language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="bb31c-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bb31c-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 <span data-ttu-id="bb31c-123">Mühürlü bir sınıf taban sınıf olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bb31c-123">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="bb31c-124">Bu nedenle, aynı zamanda soyut bir sınıf olamaz.</span><span class="sxs-lookup"><span data-stu-id="bb31c-124">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="bb31c-125">Mühürlü sınıflar türeciliği önler.</span><span class="sxs-lookup"><span data-stu-id="bb31c-125">Sealed classes prevent derivation.</span></span> <span data-ttu-id="bb31c-126">Hiçbir zaman taban sınıf olarak kullanılamayacağından, bazı çalışma zamanı optimizasyonları mühürlü sınıf üyelerini biraz daha hızlı çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-126">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="bb31c-127">Taban sınıfın sanal bir üyesini geçersiz kılan türemiş bir sınıftaki yöntem, dizinleyici, özellik veya olay, bu üyenin mühürlü olduğunu bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-127">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="bb31c-128">Bu, başka türemiş herhangi bir sınıf için üyenin sanal yönünü inkâr eder.</span><span class="sxs-lookup"><span data-stu-id="bb31c-128">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="bb31c-129">Bu, `sealed` anahtar sözcüğü sınıf üye bildiriminde [geçersiz kılma](../../language-reference/keywords/override.md) anahtar sözcüğünün önüne koyarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bb31c-129">This is accomplished by putting the `sealed` keyword before the [override](../../language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="bb31c-130">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bb31c-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="bb31c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb31c-131">See also</span></span>

- [<span data-ttu-id="bb31c-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bb31c-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bb31c-133">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="bb31c-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="bb31c-134">Devralma</span><span class="sxs-lookup"><span data-stu-id="bb31c-134">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="bb31c-135">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bb31c-135">Methods</span></span>](./methods.md)
- [<span data-ttu-id="bb31c-136">Alanlar</span><span class="sxs-lookup"><span data-stu-id="bb31c-136">Fields</span></span>](./fields.md)
- [<span data-ttu-id="bb31c-137">Soyut özellikleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="bb31c-137">How to define abstract properties</span></span>](./how-to-define-abstract-properties.md)
