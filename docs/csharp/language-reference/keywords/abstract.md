---
title: "abstract (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords: abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd26583c42302d8ce9ba4dd22119713548111236
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="abstract-c-reference"></a><span data-ttu-id="88413-102">abstract (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="88413-102">abstract (C# Reference)</span></span>
<span data-ttu-id="88413-103">`abstract` Değiştiricisi değiştirilen bir şey yok veya eksik bir uygulaması olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="88413-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="88413-104">Soyut değiştiricisi sınıfları, yöntemleri, özellikleri, dizin oluşturucular ve olayları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88413-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="88413-105">Kullanım `abstract` bir sınıfı diğer sınıfların temel sınıf yalnızca olması amaçlanmıştır belirtmek için bir sınıf bildirimindeki değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="88413-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.</span></span> <span data-ttu-id="88413-106">Özet olarak işaretlenmiş ya da bir Özet sınıfta dahil üyeleri soyut sınıftan türeyen sınıflar tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88413-106">Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88413-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="88413-107">Example</span></span>  
 <span data-ttu-id="88413-108">Bu örnekte, sınıf `Square` uygulaması sağlamalısınız `Area` öğesinden türetilen çünkü `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="88413-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 <span data-ttu-id="88413-109">Soyut sınıflar, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="88413-109">Abstract classes have the following features:</span></span>  
  
-   <span data-ttu-id="88413-110">Bir Özet sınıfın örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="88413-110">An abstract class cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="88413-111">Bir Özet Sınıf soyut yöntemler ve erişimciler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="88413-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
-   <span data-ttu-id="88413-112">Bir Özet sınıf değiştirmek mümkün değil [korumalı](../../../csharp/language-reference/keywords/sealed.md) değiştiricisi iki modifers ters anlamları olduğundan.</span><span class="sxs-lookup"><span data-stu-id="88413-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifers have opposite meanings.</span></span> <span data-ttu-id="88413-113">`sealed` Değiştiricisi devralınan öğesinden bir sınıf engeller ve `abstract` değiştiricisi devralınan için bir sınıf gerektirir.</span><span class="sxs-lookup"><span data-stu-id="88413-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
-   <span data-ttu-id="88413-114">Bir özet sınıftan türetilen soyut olmayan sınıfı devralınan tüm soyut yöntemler ve erişimciler gerçek uygulamaları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="88413-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="88413-115">Kullanım `abstract` değiştirici yöntemi veya özelliği uygulama içermediğini belirtmek için yöntemi veya özelliği bir bildirimi.</span><span class="sxs-lookup"><span data-stu-id="88413-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="88413-116">Soyut yöntemler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="88413-116">Abstract methods have the following features:</span></span>  
  
-   <span data-ttu-id="88413-117">Soyut bir yöntem örtük olarak sanal bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="88413-117">An abstract method is implicitly a virtual method.</span></span>  
  
-   <span data-ttu-id="88413-118">Özet yöntem bildirimleri yalnızca soyut sınıflarda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="88413-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
-   <span data-ttu-id="88413-119">Bir Özet yöntem bildirimi gerçek uygulaması sağladığından, hiçbir yöntem gövdesi yoktur; yöntem bildirimi yalnızca noktalı virgül ile sona erer ve imza izleyen hiçbir süslü ayraçlar ({}) vardır.</span><span class="sxs-lookup"><span data-stu-id="88413-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="88413-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="88413-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="88413-121">Uygulama bir geçersiz kılma yöntemi tarafından sağlanan[geçersiz kılma](../../../csharp/language-reference/keywords/override.md), soyut olmayan sınıfı üyesi olduğu.</span><span class="sxs-lookup"><span data-stu-id="88413-121">The implementation is provided by an overriding method[override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
-   <span data-ttu-id="88413-122">Kullanmak için bir hata olduğunu [statik](../../../csharp/language-reference/keywords/static.md) veya [sanal](../../../csharp/language-reference/keywords/virtual.md) değiştiricileri bir Özet yöntem bildirimi.</span><span class="sxs-lookup"><span data-stu-id="88413-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="88413-123">Soyut özellikler bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="88413-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="88413-124">Kullanmak için bir hata olduğunu `abstract` bir statik özelliğe değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="88413-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="88413-125">Soyut devralınmış bir özellik türetilen bir sınıfta kullanan bir özellik bildirimi dahil olmak üzere geçersiz kılınabilir [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="88413-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="88413-126">Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="88413-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="88413-127">Soyut bir sınıf uygulama tüm arabirim üyeleri için sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="88413-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="88413-128">Bir arabirimini uygulayan bir Özet Sınıf soyut yöntemler üzerine arabirim yöntemleri eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="88413-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="88413-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="88413-129">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="88413-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="88413-130">Example</span></span>  
 <span data-ttu-id="88413-131">Bu örnekte, sınıf `DerivedClass` bir özet sınıftan türetilen `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="88413-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="88413-132">Soyut bir yöntem soyut sınıf içeren `AbstractMethod`ve iki soyut özellikleri `X` ve `Y`.</span><span class="sxs-lookup"><span data-stu-id="88413-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 <span data-ttu-id="88413-133">Önceki örnekte, böyle bir deyimi kullanarak soyut sınıf örneği çalışırsanız:</span><span class="sxs-lookup"><span data-stu-id="88413-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="88413-134">Derleyici 'BaseClass' bir Özet sınıfın örneği oluşturulamıyor bildiren bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="88413-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="88413-135">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="88413-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="88413-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88413-136">See Also</span></span>  
 [<span data-ttu-id="88413-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="88413-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="88413-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="88413-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="88413-139">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="88413-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="88413-140">virtual</span><span class="sxs-lookup"><span data-stu-id="88413-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="88413-141">override</span><span class="sxs-lookup"><span data-stu-id="88413-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="88413-142">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="88413-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
