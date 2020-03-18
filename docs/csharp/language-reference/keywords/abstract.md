---
title: özet - C# Referans
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 96e8bbce2e67c316d5cd1cd78e3e2506dabead25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713858"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="97d62-102">abstract (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="97d62-102">abstract (C# Reference)</span></span>
<span data-ttu-id="97d62-103">Değiştirici, `abstract` değiştirilen şeyin eksik veya eksik bir uygulaması olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="97d62-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="97d62-104">Soyut değiştirici sınıflar, yöntemler, özellikler, dizinleyiciler ve olaylar la kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97d62-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="97d62-105">Bir `abstract` sınıfın yalnızca kendi başına anlık değil, diğer sınıfların taban sınıfı olması amaçlandığını belirtmek için sınıf bildiriminde değiştiriyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="97d62-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="97d62-106">Soyut olarak işaretlenmiş üyeler, soyut sınıftan türeyen soyut olmayan sınıflar tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97d62-106">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="97d62-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="97d62-107">Example</span></span>  
 <span data-ttu-id="97d62-108">Bu örnekte, `Square` sınıf aşağıdakilerden `GetArea` türediği için `Shape`bir uygulama sağlamalıdır:</span><span class="sxs-lookup"><span data-stu-id="97d62-108">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="97d62-109">Soyut sınıflar aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="97d62-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="97d62-110">Soyut bir sınıf anında alınamaz.</span><span class="sxs-lookup"><span data-stu-id="97d62-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="97d62-111">Soyut bir sınıf soyut yöntemler ve erişimciler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="97d62-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="97d62-112">İki değiştiricinin zıt anlamları [olduğundan, soyut](./sealed.md) bir sınıfı mühürlü değiştirici ile değiştirmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="97d62-112">It is not possible to modify an abstract class with the [sealed](./sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="97d62-113">`sealed` Değiştirici bir sınıfın devralınmasını `abstract` engeller ve değiştirici bir sınıfın devralınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="97d62-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="97d62-114">Soyut bir sınıftan türetilen soyut olmayan bir sınıf, devralınan tüm soyut yöntemlerin ve erişimcilerin gerçek uygulamalarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="97d62-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="97d62-115">Yöntemin `abstract` veya özelliğin uygulama içermediğini belirtmek için bir yöntem veya özellik bildiriminde değiştiriyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="97d62-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="97d62-116">Soyut yöntemler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="97d62-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="97d62-117">Soyut bir yöntem dolaylı olarak sanal bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="97d62-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="97d62-118">Soyut yöntem bildirimlerine yalnızca soyut sınıflarda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="97d62-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="97d62-119">Soyut bir yöntem bildirimi gerçek bir uygulama sağlamadığından, yöntem gövdesi yoktur; yöntem bildirimi sadece bir semicolon ile sona erer ve imzadan sonra kıvırcık ayraç ({ }) yoktur.</span><span class="sxs-lookup"><span data-stu-id="97d62-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="97d62-120">Örnek:</span><span class="sxs-lookup"><span data-stu-id="97d62-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="97d62-121">Uygulama, soyut olmayan bir sınıfın üyesi olan bir yöntem [geçersiz kılma](./override.md)tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="97d62-121">The implementation is provided by a method [override](./override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="97d62-122">Statik [veya](./static.md) [sanal](./virtual.md) değiştiriciler soyut bir yöntem bildiriminde kullanmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="97d62-122">It is an error to use the [static](./static.md) or [virtual](./virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="97d62-123">Soyut özellikler, bildirim ve çağırma sözdiziminde yapılan farklılıklar dışında soyut yöntemler gibi olur.</span><span class="sxs-lookup"><span data-stu-id="97d62-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="97d62-124">`abstract` Statik bir özellik üzerinde değiştirici kullanmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="97d62-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="97d62-125">Soyut bir devralınan [özellik, geçersiz kılma değiştiricisini](./override.md) kullanan bir özellik bildirimi ekleyerek türetilmiş bir sınıfta geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="97d62-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](./override.md) modifier.</span></span>  
  
 <span data-ttu-id="97d62-126">Soyut sınıflar hakkında daha fazla bilgi için [Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri'ne](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="97d62-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="97d62-127">Soyut bir sınıf tüm arabirim üyeleri için uygulama sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="97d62-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="97d62-128">Arabirim uygulayan soyut bir sınıf, arabirim yöntemlerini soyut yöntemlerle eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="97d62-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="97d62-129">Örnek:</span><span class="sxs-lookup"><span data-stu-id="97d62-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="97d62-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="97d62-130">Example</span></span>  
 <span data-ttu-id="97d62-131">Bu örnekte, `DerivedClass` sınıf soyut bir `BaseClass`sınıftan türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="97d62-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="97d62-132">Soyut sınıf soyut bir `AbstractMethod`yöntem ve iki `X` soyut `Y`özellikleri içerir ve .</span><span class="sxs-lookup"><span data-stu-id="97d62-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="97d62-133">Önceki örnekte, aşağıdaki gibi bir ifade kullanarak soyut sınıfı anında kullanmaya çalışırsanız:</span><span class="sxs-lookup"><span data-stu-id="97d62-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="97d62-134">Derleyicinin soyut sınıf 'BaseClass' bir örnek oluşturamayacağını söyleyerek bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="97d62-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="97d62-135">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="97d62-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="97d62-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97d62-136">See also</span></span>

- [<span data-ttu-id="97d62-137">C# Referans</span><span class="sxs-lookup"><span data-stu-id="97d62-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="97d62-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="97d62-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="97d62-139">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="97d62-139">Modifiers</span></span>](index.md)
- [<span data-ttu-id="97d62-140">virtual</span><span class="sxs-lookup"><span data-stu-id="97d62-140">virtual</span></span>](./virtual.md)
- [<span data-ttu-id="97d62-141">Geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="97d62-141">override</span></span>](./override.md)
- [<span data-ttu-id="97d62-142">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="97d62-142">C# Keywords</span></span>](./index.md)
