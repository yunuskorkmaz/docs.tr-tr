---
description: Virtual-C# başvurusu
title: Virtual-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 67bdfcf27bb108ca85e94ba7fdce208e4cd83b80
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141731"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="f8e57-103">virtual (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f8e57-103">virtual (C# Reference)</span></span>

<span data-ttu-id="f8e57-104">`virtual`Anahtar sözcüğü bir yöntemi, özelliği, Dizin Oluşturucuyu veya olay bildirimini değiştirmek ve bir türetilmiş sınıfta geçersiz kılınmasına izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8e57-104">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="f8e57-105">Örneğin, bu yöntem onu devralan herhangi bir sınıf tarafından geçersiz kılınabilir:</span><span class="sxs-lookup"><span data-stu-id="f8e57-105">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area()
{
    return x * y;
}
```

<span data-ttu-id="f8e57-106">Bir sanal üyenin uygulanması türetilmiş bir sınıftaki [geçersiz kılan bir üye](override.md) tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f8e57-106">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="f8e57-107">Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için `virtual` , bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="f8e57-107">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="f8e57-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8e57-108">Remarks</span></span>

<span data-ttu-id="f8e57-109">Bir sanal yöntem çağrıldığında, nesnenin çalışma zamanı türü geçersiz kılan üye için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="f8e57-109">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="f8e57-110">Türetilmiş bir sınıf üye tarafından geçersiz kılınmamışsa, en çok türetilen sınıftaki geçersiz kılan üye çağrılır, bu, özgün üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8e57-110">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="f8e57-111">Varsayılan olarak, metotlar sanal değildir.</span><span class="sxs-lookup"><span data-stu-id="f8e57-111">By default, methods are non-virtual.</span></span> <span data-ttu-id="f8e57-112">Sanal olmayan bir yöntemi geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f8e57-112">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="f8e57-113">Değiştirici,,, `virtual` `static` `abstract` `private` veya `override` değiştiriciyle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f8e57-113">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="f8e57-114">Aşağıdaki örnek bir sanal özelliği gösterir:</span><span class="sxs-lookup"><span data-stu-id="f8e57-114">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="f8e57-115">Sanal özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında sanal yöntemler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="f8e57-115">Virtual properties behave like virtual methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="f8e57-116">`virtual`Değiştirici statik bir özellik üzerinde kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="f8e57-116">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="f8e57-117">Değiştirici kullanan bir özellik bildirimi eklenerek, türetilmiş bir sınıfta sanal devralınmış bir özellik geçersiz kılınabilir `override` .</span><span class="sxs-lookup"><span data-stu-id="f8e57-117">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="f8e57-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8e57-118">Example</span></span>

<span data-ttu-id="f8e57-119">Bu örnekte, `Shape` sınıfı iki koordinat, `x` `y` ve `Area()` sanal yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="f8e57-119">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="f8e57-120">,, Ve gibi farklı şekil sınıfları `Circle` `Cylinder` `Sphere` `Shape` ve yüzey alanı her bir şekil için hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="f8e57-120">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="f8e57-121">Türetilmiş her sınıf kendi geçersiz kılma uygulamasına sahiptir `Area()` .</span><span class="sxs-lookup"><span data-stu-id="f8e57-121">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="f8e57-122">Devralınan sınıfların `Circle` , `Sphere` ve `Cylinder` tümünün, aşağıdaki bildirimde gösterildiği gibi, temel sınıfı başlatacak olan oluşturuculara sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f8e57-122">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="f8e57-123">Aşağıdaki program, yöntemiyle `Area()` ilişkili nesneye göre yönteminin uygun uygulamasını çağırarak her bir şekil için uygun alanı hesaplar ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f8e57-123">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="f8e57-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f8e57-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f8e57-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8e57-125">See also</span></span>

- [<span data-ttu-id="f8e57-126">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="f8e57-126">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="f8e57-127">abstract</span><span class="sxs-lookup"><span data-stu-id="f8e57-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="f8e57-128">override</span><span class="sxs-lookup"><span data-stu-id="f8e57-128">override</span></span>](override.md)
- [<span data-ttu-id="f8e57-129">Yeni (değiştirici)</span><span class="sxs-lookup"><span data-stu-id="f8e57-129">new (modifier)</span></span>](new-modifier.md)
