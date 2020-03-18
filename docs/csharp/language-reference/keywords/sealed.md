---
title: mühürlü değiştirici - C# Referans
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713111"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="16991-102">sealed (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="16991-102">sealed (C# Reference)</span></span>

<span data-ttu-id="16991-103">Bir sınıfa uygulandığında, `sealed` değiştirici diğer sınıfların ondan devralmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="16991-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="16991-104">Aşağıdaki örnekte, `B` sınıf sınıftan `A`devralır, ancak hiçbir `B`sınıf sınıftan devralabilir.</span><span class="sxs-lookup"><span data-stu-id="16991-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="16991-105">`sealed` Değiştiriciyi, temel sınıftaki sanal bir yöntemi veya özelliği geçersiz kılan bir yöntem veya özellik üzerinde de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16991-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="16991-106">Bu, sınıfların sınıfınızdan türemesine izin vermenize ve belirli sanal yöntemleri veya özellikleri geçersiz kılmalarını önlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="16991-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="16991-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="16991-107">Example</span></span>

<span data-ttu-id="16991-108">Aşağıdaki örnekte, `Z` `Y` 'de `Z` bildirilen `F` `X` ve mühürlü olan sanal işlevi geçersiz `Y`kılamaz, devralır, ancak</span><span class="sxs-lookup"><span data-stu-id="16991-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="16991-109">Bir sınıfta yeni yöntemler veya özellikler tanımladığınızda, türeyen sınıfların [bunları sanal](virtual.md)olarak bildirmeyerek bunları geçersiz kılmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16991-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="16991-110">[Soyut](abstract.md) bir sınıf soyut yöntemler veya özelliklerin uygulanmasını sağlayan bir sınıf tarafından devralınması gerektiğinden, soyut değiştiricinin mühürlü bir sınıfla kullanılması bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="16991-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="16991-111">Bir yönteme veya özelliğe `sealed` uygulandığında, değiştirici her zaman [geçersiz kılma](override.md)ile kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16991-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="16991-112">Structs örtülü olduğundan, onlar devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="16991-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="16991-113">Daha fazla bilgi için [Bkz. Kalıtım.](../../programming-guide/classes-and-structs/inheritance.md)</span><span class="sxs-lookup"><span data-stu-id="16991-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="16991-114">Daha fazla örnek için Bkz. [Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri.](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)</span><span class="sxs-lookup"><span data-stu-id="16991-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="16991-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="16991-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="16991-116">Önceki örnekte, aşağıdaki deyimi kullanarak mühürlü sınıftan devralmayı deneyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="16991-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="16991-117">Sonuç bir hata iletisi:</span><span class="sxs-lookup"><span data-stu-id="16991-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="16991-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16991-118">Remarks</span></span>

<span data-ttu-id="16991-119">Bir sınıfı, yöntemi veya özelliği mühürleyip mühürlemeyeceğinibelirlemek için genellikle aşağıdaki iki noktayı göz önünde bulundurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="16991-119">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="16991-120">Sınıfları özelleştirme yeteneği ile elde edebileceği olası faydalar.</span><span class="sxs-lookup"><span data-stu-id="16991-120">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="16991-121">Türeyen sınıfların, sınıflarınızı artık doğru veya beklendiği gibi çalışamayacak şekilde değiştirebilen potansiyel.</span><span class="sxs-lookup"><span data-stu-id="16991-121">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="16991-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="16991-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="16991-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16991-123">See also</span></span>

- [<span data-ttu-id="16991-124">C# Referans</span><span class="sxs-lookup"><span data-stu-id="16991-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="16991-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="16991-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="16991-126">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="16991-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="16991-127">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="16991-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="16991-128">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="16991-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="16991-129">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="16991-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="16991-130">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="16991-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="16991-131">Geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="16991-131">override</span></span>](override.md)
- [<span data-ttu-id="16991-132">virtual</span><span class="sxs-lookup"><span data-stu-id="16991-132">virtual</span></span>](virtual.md)
