---
title: soyut - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 5476e99cbd1a5af2acf91ed6bf854fded3425e72
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452455"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="68c37-102">abstract (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="68c37-102">abstract (C# Reference)</span></span>
<span data-ttu-id="68c37-103">`abstract` Değiştiricisi değiştirilmekte olan bir şey yok veya eksik bir uygulama olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="68c37-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="68c37-104">Soyut değiştiricisi sınıflar, yöntemler, özellikler, dizin oluşturucular ve olaylar ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68c37-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="68c37-105">Kullanım `abstract` değiştiricisi bir sınıf yalnızca, kendi örneği değil, diğer sınıfların temel sınıf olarak düşünüldüğünü göstermek için bir sınıf bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="68c37-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="68c37-106">Üyeleri, soyut soyut sınıftan türeyen sınıflar tarafından uygulanması gereken olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="68c37-106">Members marked as abstract must be implemented by classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="68c37-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="68c37-107">Example</span></span>  
 <span data-ttu-id="68c37-108">Bu örnekte, sınıf `Square` uygulaması sağlamalısınız `Area` öğesinden türetildiği için `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="68c37-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="68c37-109">Soyut sınıflar, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="68c37-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="68c37-110">Bir soyut sınıfı oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="68c37-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="68c37-111">Bir Özet sınıf, soyut yöntemler ve erişimcileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="68c37-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="68c37-112">Bir Özet sınıf değiştirmek mümkün değildir [korumalı](../../../csharp/language-reference/keywords/sealed.md) değiştiricisi çünkü iki değiştirici karşı anlamları vardır.</span><span class="sxs-lookup"><span data-stu-id="68c37-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="68c37-113">`sealed` Değiştiricisi devralınan öğesinden bir sınıf engeller ve `abstract` değiştiricisi bir sınıf devralma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="68c37-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="68c37-114">Soyut bir sınıftan bir Özet olmayan sınıftan devralınan tüm soyut yöntemler ve erişimcileri gerçek uygulamaları içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="68c37-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="68c37-115">Kullanım `abstract` yöntemi veya özelliği uygulaması içermiyor belirtmek için bir yöntem veya özellik bildiriminde değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="68c37-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="68c37-116">Soyut yöntemler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="68c37-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="68c37-117">Soyut Metoda örtük olarak sanal bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="68c37-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="68c37-118">Soyut yöntem bildirimleri yalnızca soyut sınıfları izin verilir.</span><span class="sxs-lookup"><span data-stu-id="68c37-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="68c37-119">Bir soyut yöntem bildiriminde gerçek uygulaması sağladığından, herhangi bir yöntem gövdesi yoktur; yöntem bildiriminde yalnızca noktalı virgül ile sona erer ve imza izleyen hiçbir küme ayracı ({}) vardır.</span><span class="sxs-lookup"><span data-stu-id="68c37-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="68c37-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="68c37-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="68c37-121">Uygulama yöntemi tarafından sağlanan [geçersiz kılma](../../../csharp/language-reference/keywords/override.md), soyut olmayan sınıf üyesi olduğu.</span><span class="sxs-lookup"><span data-stu-id="68c37-121">The implementation is provided by a method [override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="68c37-122">Kullanılacak bir hata olduğunu [statik](../../../csharp/language-reference/keywords/static.md) veya [sanal](../../../csharp/language-reference/keywords/virtual.md) soyut yöntem bildiriminde değiştiriciler.</span><span class="sxs-lookup"><span data-stu-id="68c37-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="68c37-123">Soyut özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="68c37-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="68c37-124">Kullanılacak bir hata olduğunu `abstract` değiştirici statik bir özellik.</span><span class="sxs-lookup"><span data-stu-id="68c37-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="68c37-125">Devralınan soyut bir özelliğin kullanan bir özellik bildirimi dahil olmak üzere türetilen bir sınıfta kılınabilir [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="68c37-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="68c37-126">Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="68c37-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="68c37-127">Bir soyut sınıf uygulama için tüm arabirim üyeleri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="68c37-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="68c37-128">Bir arabirimi uygulayan bir Özet sınıf, arabirim yöntemleri soyut yöntemler üzerine eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="68c37-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="68c37-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="68c37-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="68c37-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="68c37-130">Example</span></span>  
 <span data-ttu-id="68c37-131">Bu örnekte, sınıf `DerivedClass` soyut bir sınıftan türetilen `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="68c37-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="68c37-132">Soyut bir yöntemi soyut sınıfını içeren `AbstractMethod`ve iki soyut Özellikler `X` ve `Y`.</span><span class="sxs-lookup"><span data-stu-id="68c37-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="68c37-133">Önceki örnekte, böyle bir deyimi kullanarak soyut sınıfın örneği çalışırsanız:</span><span class="sxs-lookup"><span data-stu-id="68c37-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="68c37-134">Derleyici 'BaseClass' soyut sınıfının bir örneğini oluşturamazsınız belirten bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="68c37-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="68c37-135">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="68c37-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68c37-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68c37-136">See also</span></span>

- [<span data-ttu-id="68c37-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="68c37-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="68c37-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="68c37-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="68c37-139">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="68c37-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
- [<span data-ttu-id="68c37-140">virtual</span><span class="sxs-lookup"><span data-stu-id="68c37-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
- [<span data-ttu-id="68c37-141">override</span><span class="sxs-lookup"><span data-stu-id="68c37-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)
- [<span data-ttu-id="68c37-142">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="68c37-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
