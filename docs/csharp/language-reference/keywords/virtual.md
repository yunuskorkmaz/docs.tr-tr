---
title: sanal - C# Referans
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 883e0a7f833c15d2c1cce6b3d52d16aad01a5cd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173464"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="3ede0-102">virtual (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3ede0-102">virtual (C# Reference)</span></span>

<span data-ttu-id="3ede0-103">Anahtar `virtual` kelime, bir yöntemi, özelliği, dizinleyiciyi veya olay bildirimini değiştirmek ve türetilmiş bir sınıfta geçersiz kılınmasını sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ede0-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="3ede0-104">Örneğin, bu yöntem, onu devralan herhangi bir sınıf tarafından geçersiz kılınabilir:</span><span class="sxs-lookup"><span data-stu-id="3ede0-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area()
{
    return x * y;
}
```

<span data-ttu-id="3ede0-105">Sanal bir üyenin uygulanması, türetilmiş bir [sınıftaki geçersiz bir üye](override.md) tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3ede0-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="3ede0-106">Anahtar kelimenin `virtual` nasıl kullanılacağı hakkında daha fazla bilgi için, [Geçersiz Kılma ve Yeni Anahtar Kelimelerle Sürümleme ve](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) Geçersiz Kılma ve Yeni Anahtar Kelimeleri Ne Zaman [Kullanılacağını Bilmek](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)'e bakın.</span><span class="sxs-lookup"><span data-stu-id="3ede0-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="3ede0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ede0-107">Remarks</span></span>

<span data-ttu-id="3ede0-108">Sanal bir yöntem çağrıldığında, nesnenin çalışma zamanı türü geçersiz bir üye için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="3ede0-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="3ede0-109">En çok türetilmiş sınıftaki geçersiz olan üye, türetilmiş sınıf üyeyi geçersiz kılmamışsa, özgün üye olabilecek çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3ede0-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="3ede0-110">Varsayılan olarak, yöntemler sanal değildir.</span><span class="sxs-lookup"><span data-stu-id="3ede0-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="3ede0-111">Sanal olmayan bir yöntemi geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3ede0-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="3ede0-112">`virtual` Değiştiriciyi `static`, `abstract`, `private`veya `override` değiştiriciler ile kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3ede0-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="3ede0-113">Aşağıdaki örnekte sanal bir özellik gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3ede0-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="3ede0-114">Sanal özellikler, bildirim ve çağırma sözdiziminde olan farklılıklar dışında sanal yöntemler gibi olur.</span><span class="sxs-lookup"><span data-stu-id="3ede0-114">Virtual properties behave like virtual methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="3ede0-115">`virtual` Statik bir özellik üzerinde değiştirici kullanmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="3ede0-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="3ede0-116">Sanal devralınan özellik, `override` değiştiriciyi kullanan bir özellik bildirimi ekleyerek türetilmiş bir sınıfta geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="3ede0-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="3ede0-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ede0-117">Example</span></span>

<span data-ttu-id="3ede0-118">Bu örnekte, `Shape` sınıf iki koordinat `x` `y`, ve `Area()` sanal yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="3ede0-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="3ede0-119">Sınıf , , `Circle` `Cylinder`ve `Sphere` devralma `Shape` gibi farklı şekil sınıfları ve yüzey alanı her şekil için hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="3ede0-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="3ede0-120">Her türetilmiş sınıfın kendi `Area()`geçersiz kılma uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="3ede0-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="3ede0-121">Aşağıdaki bildirimde gösterildiği `Circle` `Sphere`gibi, `Cylinder` devralınan sınıfların ve tüm bunların temel sınıfı açan yapıcılar kullandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3ede0-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="3ede0-122">Aşağıdaki program, `Area()` yöntemle ilişkili nesneye göre yöntemin uygun uygulamasını çağırarak her şekil için uygun alanı hesaplar ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3ede0-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="3ede0-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3ede0-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3ede0-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ede0-124">See also</span></span>

- [<span data-ttu-id="3ede0-125">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="3ede0-125">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="3ede0-126">Soyut</span><span class="sxs-lookup"><span data-stu-id="3ede0-126">abstract</span></span>](abstract.md)
- [<span data-ttu-id="3ede0-127">Geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="3ede0-127">override</span></span>](override.md)
- [<span data-ttu-id="3ede0-128">yeni (değiştirici)</span><span class="sxs-lookup"><span data-stu-id="3ede0-128">new (modifier)</span></span>](new-modifier.md)
