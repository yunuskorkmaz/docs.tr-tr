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
ms.openlocfilehash: 586e50818fc8ceaad5ca1925c0636b31015d81d4
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925367"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="af02c-102">virtual (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="af02c-102">virtual (C# Reference)</span></span>

<span data-ttu-id="af02c-103">`virtual` Anahtar sözcüğü bir yöntemi, özelliği, Dizin Oluşturucuyu veya olay bildirimini değiştirmek ve bir türetilmiş sınıfta geçersiz kılınmasına izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af02c-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="af02c-104">Örneğin, bu yöntem onu devralan herhangi bir sınıf tarafından geçersiz kılınabilir:</span><span class="sxs-lookup"><span data-stu-id="af02c-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area() 
{
    return x * y;
}
```

<span data-ttu-id="af02c-105">Bir sanal üyenin uygulanması türetilmiş bir sınıftaki [geçersiz kılan bir üye](override.md) tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="af02c-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="af02c-106">`virtual` Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için, bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="af02c-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="af02c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af02c-107">Remarks</span></span>

<span data-ttu-id="af02c-108">Bir sanal yöntem çağrıldığında, nesnenin çalışma zamanı türü geçersiz kılan üye için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="af02c-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="af02c-109">Türetilmiş bir sınıf üye tarafından geçersiz kılınmamışsa, en çok türetilen sınıftaki geçersiz kılan üye çağrılır, bu, özgün üye olabilir.</span><span class="sxs-lookup"><span data-stu-id="af02c-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="af02c-110">Varsayılan olarak, metotlar sanal değildir.</span><span class="sxs-lookup"><span data-stu-id="af02c-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="af02c-111">Sanal olmayan bir yöntemi geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="af02c-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="af02c-112">`virtual` Değiştirici `static`, ,`abstract`, veya`override` değiştiriciyle kullanılamaz. `private`</span><span class="sxs-lookup"><span data-stu-id="af02c-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="af02c-113">Aşağıdaki örnek bir sanal özelliği gösterir:</span><span class="sxs-lookup"><span data-stu-id="af02c-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="af02c-114">Bildirim ve çağırma sözdiziminde farklılıklar dışında, sanal Özellikler soyut yöntemler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="af02c-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="af02c-115">`virtual` Değiştirici statik bir özellik üzerinde kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="af02c-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="af02c-116">`override` Değiştirici kullanan bir özellik bildirimi eklenerek, türetilmiş bir sınıfta sanal devralınmış bir özellik geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="af02c-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="af02c-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="af02c-117">Example</span></span>

<span data-ttu-id="af02c-118">Bu örnekte `Shape` , sınıfı iki `y`koordinat `x`, ve `Area()` sanal yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="af02c-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="af02c-119">`Circle`, ,`Cylinder`Ve gibifarklışekil`Shape` sınıfları ve yüzey alanı her bir şekil için hesaplanır. `Sphere`</span><span class="sxs-lookup"><span data-stu-id="af02c-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="af02c-120">Türetilmiş her sınıf kendi geçersiz kılma uygulamasına `Area()`sahiptir.</span><span class="sxs-lookup"><span data-stu-id="af02c-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="af02c-121">Devralınan sınıfların `Circle`, `Sphere`ve `Cylinder` tümünün, aşağıdaki bildirimde gösterildiği gibi, temel sınıfı başlatacak olan oluşturuculara sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="af02c-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="af02c-122">Aşağıdaki program, yöntemiyle ilişkili nesneye göre `Area()` yönteminin uygun uygulamasını çağırarak her bir şekil için uygun alanı hesaplar ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="af02c-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="af02c-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="af02c-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="af02c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af02c-124">See also</span></span>

- [<span data-ttu-id="af02c-125">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="af02c-125">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="af02c-126">abstract</span><span class="sxs-lookup"><span data-stu-id="af02c-126">abstract</span></span>](abstract.md)
- [<span data-ttu-id="af02c-127">override</span><span class="sxs-lookup"><span data-stu-id="af02c-127">override</span></span>](override.md)
- [<span data-ttu-id="af02c-128">Yeni (değiştirici)</span><span class="sxs-lookup"><span data-stu-id="af02c-128">new (modifier)</span></span>](new-modifier.md)
