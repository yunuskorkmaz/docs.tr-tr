---
title: Sanal - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 2568eed5a889f6c03e237875194b8adcb9334ef7
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401820"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="2ab13-102">virtual (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2ab13-102">virtual (C# Reference)</span></span>

<span data-ttu-id="2ab13-103">`virtual` Anahtar sözcüğü, bir yöntemi, özelliği, dizin oluşturucu veya olay bildirimini değiştirmek ve türetilen bir sınıfta geçersiz kılınması için izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2ab13-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="2ab13-104">Örneğin, bu yöntem devraldığı herhangi bir sınıf tarafından geçersiz kılınabilir:</span><span class="sxs-lookup"><span data-stu-id="2ab13-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area() 
{
    return x * y;
}
```

<span data-ttu-id="2ab13-105">Uygulamasını bir sanal üye tarafından değiştirilebilen bir [geçersiz kılan üye](override.md) türetilen bir sınıfta.</span><span class="sxs-lookup"><span data-stu-id="2ab13-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="2ab13-106">Nasıl kullanılacağı hakkında daha fazla bilgi için `virtual` anahtar sözcüğü, bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [bilerek, geçersiz kılma kullanın ve yeni anahtar sözcüklerle](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="2ab13-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="2ab13-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ab13-107">Remarks</span></span>

<span data-ttu-id="2ab13-108">Sanal bir yöntem çağrıldığında, nesnenin çalışma zamanı türü için geçersiz kılan bir üye denetlenir.</span><span class="sxs-lookup"><span data-stu-id="2ab13-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="2ab13-109">Türetilmiş sınıf üyesi kıldıysa, özgün üyesi olabilir. en çok türetilen bir sınıfta geçersiz kılan üye çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2ab13-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="2ab13-110">Varsayılan olarak, sanal olmayan yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="2ab13-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="2ab13-111">Sanal olmayan bir yöntemi geçersiz kılınamıyor.</span><span class="sxs-lookup"><span data-stu-id="2ab13-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="2ab13-112">Kullanamazsınız `virtual` değiştiriciyle `static`, `abstract`, `private`, veya `override` değiştiriciler.</span><span class="sxs-lookup"><span data-stu-id="2ab13-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="2ab13-113">Aşağıdaki örnek, sanal bir özellik gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2ab13-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="2ab13-114">Sanal özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="2ab13-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="2ab13-115">Kullanılacak bir hata olduğunu `virtual` değiştirici statik bir özellik.</span><span class="sxs-lookup"><span data-stu-id="2ab13-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="2ab13-116">Sanal bir devralınan özelliği kullanan bir özellik bildirimi dahil olmak üzere türetilen bir sınıfta kılınabilir `override` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="2ab13-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="2ab13-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ab13-117">Example</span></span>

<span data-ttu-id="2ab13-118">Bu örnekte, `Shape` sınıfı içeren iki koordinat `x`, `y`ve `Area()` sanal yöntem.</span><span class="sxs-lookup"><span data-stu-id="2ab13-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="2ab13-119">Farklı şekil sınıflar gibi `Circle`, `Cylinder`, ve `Sphere` devral `Shape` sınıfı ve yüzey her şekil için hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2ab13-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="2ab13-120">Her bir türetilmiş sınıf kendi geçersiz kılma uygulaması olan `Area()`.</span><span class="sxs-lookup"><span data-stu-id="2ab13-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="2ab13-121">Dikkat devralınan sınıflar `Circle`, `Sphere`, ve `Cylinder` tüm taban sınıf başlatma oluşturucular aşağıdaki bildirimde gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ab13-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="2ab13-122">Aşağıdaki program hesaplar ve her bir şekil için uygun alan uygun uygulama çağırarak görüntüler `Area()` yöntemiyle ilişkili nesne göre yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2ab13-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="2ab13-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2ab13-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2ab13-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ab13-124">See also</span></span>

- [<span data-ttu-id="2ab13-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2ab13-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2ab13-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2ab13-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2ab13-127">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="2ab13-127">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="2ab13-128">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2ab13-128">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2ab13-129">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="2ab13-129">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="2ab13-130">abstract</span><span class="sxs-lookup"><span data-stu-id="2ab13-130">abstract</span></span>](abstract.md)
- [<span data-ttu-id="2ab13-131">override</span><span class="sxs-lookup"><span data-stu-id="2ab13-131">override</span></span>](override.md)
- [<span data-ttu-id="2ab13-132">Yeni (değiştirici)</span><span class="sxs-lookup"><span data-stu-id="2ab13-132">new (modifier)</span></span>](new-modifier.md)
