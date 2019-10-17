---
title: sanal C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: d5e087647adced0b41cc6e42fcf534b274c70592
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395156"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="9275f-102">virtual (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9275f-102">virtual (C# Reference)</span></span>

<span data-ttu-id="9275f-103">@No__t-0 anahtar sözcüğü, bir yöntemi, özelliği, Dizin Oluşturucuyu veya olay bildirimini değiştirmek ve bir türetilmiş sınıfta geçersiz kılınabilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9275f-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="9275f-104">Örneğin, bu yöntem onu devralan herhangi bir sınıf tarafından geçersiz kılınabilir:</span><span class="sxs-lookup"><span data-stu-id="9275f-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area() 
{
    return x * y;
}
```

<span data-ttu-id="9275f-105">Bir sanal üyenin uygulanması türetilmiş bir sınıftaki [geçersiz kılan bir üye](override.md) tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9275f-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="9275f-106">@No__t-0 anahtar sözcüğünü kullanma hakkında daha fazla bilgi için bkz. geçersiz kılma ve [Yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="9275f-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="9275f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9275f-107">Remarks</span></span>

<span data-ttu-id="9275f-108">Bir sanal yöntem çağrıldığında, nesnenin çalışma zamanı türü geçersiz kılan üye için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="9275f-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="9275f-109">Türetilmiş bir sınıf üye tarafından geçersiz kılınmamışsa, en çok türetilen sınıftaki geçersiz kılan üye çağrılır, bu, özgün üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="9275f-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="9275f-110">Varsayılan olarak, metotlar sanal değildir.</span><span class="sxs-lookup"><span data-stu-id="9275f-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="9275f-111">Sanal olmayan bir yöntemi geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9275f-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="9275f-112">@No__t-0 değiştiricisini `static`, `abstract`, `private` veya `override` değiştiricisiyle kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9275f-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="9275f-113">Aşağıdaki örnek bir sanal özelliği gösterir:</span><span class="sxs-lookup"><span data-stu-id="9275f-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="9275f-114">Sanal özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında sanal yöntemler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="9275f-114">Virtual properties behave like virtual methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="9275f-115">Statik bir özellikte `virtual` değiştiricisinin kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="9275f-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="9275f-116">Bir sanal devralınmış özellik, `override` değiştiricisini kullanan bir özellik bildirimi eklenerek, türetilmiş sınıfta geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="9275f-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="9275f-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="9275f-117">Example</span></span>

<span data-ttu-id="9275f-118">Bu örnekte, `Shape` sınıfı iki koordinat `x`, `y` ve `Area()` sanal yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="9275f-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="9275f-119">@No__t-0, `Cylinder` ve `Sphere` gibi farklı şekil sınıfları `Shape` sınıfını miras alır ve yüzey alanı her bir şekil için hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="9275f-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="9275f-120">Her türetilmiş sınıfın kendi geçersiz kılma `Area()` ' dır.</span><span class="sxs-lookup"><span data-stu-id="9275f-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="9275f-121">Devralınan sınıfların `Circle`, `Sphere` ve `Cylinder` ' nin, aşağıdaki bildirimde gösterildiği gibi, temel sınıfı başlatacak olan oluşturuculara sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9275f-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="9275f-122">Aşağıdaki program, yöntemiyle ilişkili nesneye göre `Area()` yönteminin uygun uygulamasını çağırarak her bir şekil için uygun alanı hesaplar ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9275f-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="9275f-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9275f-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9275f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9275f-124">See also</span></span>

- [<span data-ttu-id="9275f-125">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="9275f-125">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="9275f-126">abstract</span><span class="sxs-lookup"><span data-stu-id="9275f-126">abstract</span></span>](abstract.md)
- [<span data-ttu-id="9275f-127">override</span><span class="sxs-lookup"><span data-stu-id="9275f-127">override</span></span>](override.md)
- [<span data-ttu-id="9275f-128">Yeni (değiştirici)</span><span class="sxs-lookup"><span data-stu-id="9275f-128">new (modifier)</span></span>](new-modifier.md)
