---
title: Soyut- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: a6c0ac86689c5d095fc077beb39d6281f77aab24
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422949"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="9feed-102">abstract (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9feed-102">abstract (C# Reference)</span></span>
<span data-ttu-id="9feed-103">`abstract` değiştirici, değiştirilmekte olan bir uygulamanın eksik veya tamamlanmamış bir uygulamasına sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9feed-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="9feed-104">Soyut değiştirici sınıflar, Yöntemler, özellikler, Dizin oluşturucular ve olaylar ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9feed-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="9feed-105">Bir sınıfın yalnızca diğer sınıfların temel sınıfı olduğunu göstermek için bir sınıf bildiriminde `abstract` değiştiricisini kullanın, kendi kendine örneği değildir.</span><span class="sxs-lookup"><span data-stu-id="9feed-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="9feed-106">Soyut olarak işaretlenen Üyeler soyut sınıftan türetilen soyut olmayan sınıflar tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9feed-106">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="9feed-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9feed-107">Example</span></span>  
 <span data-ttu-id="9feed-108">Bu örnekte, sınıf `Square`, `Shape`türettiği için `GetArea` uygulamasını sağlamalıdır:</span><span class="sxs-lookup"><span data-stu-id="9feed-108">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="9feed-109">Soyut sınıflar aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9feed-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="9feed-110">Soyut bir sınıf örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="9feed-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="9feed-111">Soyut bir sınıf, Soyut yöntemler ve erişimciler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9feed-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="9feed-112">İki değiştiricinin ters anlamları olduğundan, [soyut değiştirici içeren](./sealed.md) bir soyut sınıfı değiştirmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="9feed-112">It is not possible to modify an abstract class with the [sealed](./sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="9feed-113">`sealed` değiştiricisi bir sınıfın devralınmasını engeller ve `abstract` değiştiricisi bir sınıfın devralınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9feed-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="9feed-114">Soyut bir sınıftan türetilmiş soyut olmayan bir sınıf, devralınan tüm soyut yöntemlerin ve erişimcilerinin gerçek uygulamalarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="9feed-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="9feed-115">Yöntemin veya özelliğin uygulama içermediğini belirtmek için bir yöntem veya özellik bildiriminde `abstract` değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9feed-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="9feed-116">Soyut yöntemler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9feed-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="9feed-117">Soyut bir yöntem örtük olarak sanal bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9feed-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="9feed-118">Soyut yöntem bildirimlerine yalnızca soyut sınıflarda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9feed-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="9feed-119">Soyut bir yöntem bildirimi gerçek uygulama sunmadığından, hiçbir Yöntem gövdesi yoktur; Yöntem bildirimi yalnızca noktalı virgül ile sona erer ve imzadan sonra küme ayracı ({}) yoktur.</span><span class="sxs-lookup"><span data-stu-id="9feed-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="9feed-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9feed-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="9feed-121">Uygulama, soyut olmayan bir sınıfın üyesi olan bir yöntem [geçersiz kılma](./override.md)tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9feed-121">The implementation is provided by a method [override](./override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="9feed-122">Soyut bir yöntem bildiriminde [statik](./static.md) veya [sanal](./virtual.md) değiştiricilerin kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="9feed-122">It is an error to use the [static](./static.md) or [virtual](./virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="9feed-123">Özet özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="9feed-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="9feed-124">Statik bir özellik üzerinde `abstract` değiştiricisinin kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="9feed-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="9feed-125">Bir soyut devralınmış özellik, [geçersiz kılma](./override.md) değiştiricisini kullanan bir özellik bildirimi eklenerek, türetilmiş bir sınıfta geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="9feed-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](./override.md) modifier.</span></span>  
  
 <span data-ttu-id="9feed-126">Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="9feed-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="9feed-127">Soyut bir sınıf tüm arabirim üyeleri için uygulama sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9feed-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="9feed-128">Arabirim uygulayan bir soyut sınıf, arabirim yöntemlerini soyut yöntemlerle eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9feed-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="9feed-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9feed-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="9feed-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="9feed-130">Example</span></span>  
 <span data-ttu-id="9feed-131">Bu örnekte, sınıf `DerivedClass` `BaseClass`soyut bir sınıftan türetilir.</span><span class="sxs-lookup"><span data-stu-id="9feed-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="9feed-132">Soyut sınıf soyut bir yöntem, `AbstractMethod`ve iki soyut özellik içerir `X` ve `Y`.</span><span class="sxs-lookup"><span data-stu-id="9feed-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="9feed-133">Yukarıdaki örnekte, aşağıdaki gibi bir ifade kullanarak soyut sınıfı örneğini oluşturmaya çalışırsanız:</span><span class="sxs-lookup"><span data-stu-id="9feed-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="9feed-134">Derleyicinin ' BaseClass ' soyut sınıfının bir örneğini oluşturkullanılamadığını belirten bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="9feed-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9feed-135">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9feed-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9feed-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9feed-136">See also</span></span>

- [<span data-ttu-id="9feed-137">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9feed-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9feed-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9feed-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9feed-139">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="9feed-139">Modifiers</span></span>](index.md)
- [<span data-ttu-id="9feed-140">virtual</span><span class="sxs-lookup"><span data-stu-id="9feed-140">virtual</span></span>](./virtual.md)
- [<span data-ttu-id="9feed-141">override</span><span class="sxs-lookup"><span data-stu-id="9feed-141">override</span></span>](./override.md)
- [<span data-ttu-id="9feed-142">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9feed-142">C# Keywords</span></span>](./index.md)
