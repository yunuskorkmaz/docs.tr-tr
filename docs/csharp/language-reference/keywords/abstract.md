---
description: abstract-C# başvurusu
title: abstract-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 095c4dea838aff4f14833d78fb10a2f831cf5173
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127210"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="73bd6-103">abstract (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="73bd6-103">abstract (C# Reference)</span></span>
<span data-ttu-id="73bd6-104">`abstract`Değiştirici, değiştirilmekte olan bir uygulamanın eksik veya tamamlanmamış bir uygulamasına sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-104">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="73bd6-105">Soyut değiştirici sınıflar, Yöntemler, özellikler, Dizin oluşturucular ve olaylar ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-105">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="73bd6-106">Bir `abstract` sınıfın yalnızca diğer sınıfların temel sınıfı olduğunu göstermek için bir sınıf bildiriminde değiştiricisini kullanın, kendi kendine örneği değildir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-106">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="73bd6-107">Soyut olarak işaretlenen Üyeler soyut sınıftan türetilen soyut olmayan sınıflar tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73bd6-107">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="73bd6-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="73bd6-108">Example</span></span>  
 <span data-ttu-id="73bd6-109">Bu örnekte, sınıfının `Square` türettiği için bir uygulamasını sağlaması gerekir `GetArea` `Shape` :</span><span class="sxs-lookup"><span data-stu-id="73bd6-109">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="73bd6-110">Soyut sınıflar aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="73bd6-110">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="73bd6-111">Soyut bir sınıf örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="73bd6-111">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="73bd6-112">Soyut bir sınıf, Soyut yöntemler ve erişimciler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-112">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="73bd6-113">İki değiştiricinin ters anlamları olduğundan, [soyut değiştirici içeren](./sealed.md) bir soyut sınıfı değiştirmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-113">It is not possible to modify an abstract class with the [sealed](./sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="73bd6-114">`sealed`Değiştirici bir sınıfın devralınmasını engeller ve `abstract` değiştirici bir sınıfın devralınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-114">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="73bd6-115">Soyut bir sınıftan türetilmiş soyut olmayan bir sınıf, devralınan tüm soyut yöntemlerin ve erişimcilerinin gerçek uygulamalarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-115">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="73bd6-116">Yöntemin veya `abstract` özelliğin uygulama içermediğini belirtmek için yöntem veya özellik bildiriminde değiştirici kullanın.</span><span class="sxs-lookup"><span data-stu-id="73bd6-116">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="73bd6-117">Soyut yöntemler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="73bd6-117">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="73bd6-118">Soyut bir yöntem örtük olarak sanal bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-118">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="73bd6-119">Soyut yöntem bildirimlerine yalnızca soyut sınıflarda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-119">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="73bd6-120">Soyut bir yöntem bildirimi gerçek uygulama sunmadığından, hiçbir Yöntem gövdesi yoktur; Yöntem bildirimi yalnızca noktalı virgül ile sona erer ve imzadan sonra küme ayracı ({}) yoktur.</span><span class="sxs-lookup"><span data-stu-id="73bd6-120">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="73bd6-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="73bd6-121">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="73bd6-122">Uygulama, soyut olmayan bir sınıfın üyesi olan bir yöntem [geçersiz kılma](./override.md)tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="73bd6-122">The implementation is provided by a method [override](./override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="73bd6-123">Soyut bir yöntem bildiriminde [statik](./static.md) veya [sanal](./virtual.md) değiştiricilerin kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="73bd6-123">It is an error to use the [static](./static.md) or [virtual](./virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="73bd6-124">Özet özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="73bd6-124">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="73bd6-125">`abstract`Değiştirici statik bir özellik üzerinde kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="73bd6-125">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="73bd6-126">Bir soyut devralınmış özellik, [geçersiz kılma](./override.md) değiştiricisini kullanan bir özellik bildirimi eklenerek, türetilmiş bir sınıfta geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-126">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](./override.md) modifier.</span></span>  
  
 <span data-ttu-id="73bd6-127">Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="73bd6-127">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="73bd6-128">Soyut bir sınıf tüm arabirim üyeleri için uygulama sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="73bd6-128">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="73bd6-129">Arabirim uygulayan bir soyut sınıf, arabirim yöntemlerini soyut yöntemlerle eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="73bd6-129">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="73bd6-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="73bd6-130">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="73bd6-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="73bd6-131">Example</span></span>  
 <span data-ttu-id="73bd6-132">Bu örnekte, sınıfı `DerivedClass` soyut bir sınıftan türetilir `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="73bd6-132">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="73bd6-133">Soyut sınıf soyut bir yöntem, `AbstractMethod` ve iki soyut özellik içerir `X` ve `Y` .</span><span class="sxs-lookup"><span data-stu-id="73bd6-133">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="73bd6-134">Yukarıdaki örnekte, aşağıdaki gibi bir ifade kullanarak soyut sınıfı örneğini oluşturmaya çalışırsanız:</span><span class="sxs-lookup"><span data-stu-id="73bd6-134">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="73bd6-135">Derleyicinin ' BaseClass ' soyut sınıfının bir örneğini oluşturkullanılamadığını belirten bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="73bd6-135">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="73bd6-136">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="73bd6-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73bd6-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73bd6-137">See also</span></span>

- [<span data-ttu-id="73bd6-138">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="73bd6-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="73bd6-139">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="73bd6-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="73bd6-140">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="73bd6-140">Modifiers</span></span>](index.md)
- [<span data-ttu-id="73bd6-141">virtual</span><span class="sxs-lookup"><span data-stu-id="73bd6-141">virtual</span></span>](./virtual.md)
- [<span data-ttu-id="73bd6-142">override</span><span class="sxs-lookup"><span data-stu-id="73bd6-142">override</span></span>](./override.md)
- [<span data-ttu-id="73bd6-143">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="73bd6-143">C# Keywords</span></span>](./index.md)
