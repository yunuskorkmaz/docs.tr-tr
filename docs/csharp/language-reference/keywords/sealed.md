---
title: Sealed değiştirici- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713111"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="95f7d-102">sealed (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="95f7d-102">sealed (C# Reference)</span></span>

<span data-ttu-id="95f7d-103">Bir sınıfa uygulandığında `sealed` değiştiricisi diğer sınıfların bundan devralınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="95f7d-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="95f7d-104">Aşağıdaki örnekte, sınıf `B` sınıf `A`devralır, ancak sınıf `B`sınıfından hiçbir sınıf devralamıyor.</span><span class="sxs-lookup"><span data-stu-id="95f7d-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="95f7d-105">Bir temel sınıftaki sanal bir yöntemi veya özelliği geçersiz kılan bir yöntem veya özellik üzerinde `sealed` değiştiricisini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f7d-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="95f7d-106">Bu, sınıfların sınıfınızdan türetmesine izin verir ve belirli sanal yöntemlerin veya özelliklerin geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="95f7d-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="95f7d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="95f7d-107">Example</span></span>

<span data-ttu-id="95f7d-108">Aşağıdaki örnekte, `Z` `Y` devralır, ancak `Z` `X` ve mühürlenen `F` sanal işlevi geçersiz kılamaz.</span><span class="sxs-lookup"><span data-stu-id="95f7d-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="95f7d-109">Bir sınıfta yeni yöntemler veya özellikler tanımladığınızda, türetilen sınıfların bunları [sanal](virtual.md)olarak bildirmeyerek geçersiz kılmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f7d-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="95f7d-110">Soyut bir sınıf, soyut yöntemlerin veya özelliklerin bir uygulamasını sağlayan bir sınıf tarafından devralınamadığı için Sealed bir sınıf ile [soyut](abstract.md) değiştiricinin kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="95f7d-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="95f7d-111">Bir yönteme veya özelliğe uygulandığında, `sealed` değiştiricisi her zaman [geçersiz kılma](override.md)ile kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95f7d-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="95f7d-112">Yapılar örtük olarak mühürlenmediğinden devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="95f7d-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="95f7d-113">Daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="95f7d-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="95f7d-114">Daha fazla örnek için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="95f7d-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="95f7d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="95f7d-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="95f7d-116">Önceki örnekte, aşağıdaki ifadeyi kullanarak Sealed sınıfından devralmayı deneyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="95f7d-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="95f7d-117">Sonuç bir hata iletisidir:</span><span class="sxs-lookup"><span data-stu-id="95f7d-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="95f7d-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95f7d-118">Remarks</span></span>

<span data-ttu-id="95f7d-119">Bir sınıfın, yöntemin veya özelliğin mühürlendirilip zorlanmayacağını anlamak için genellikle aşağıdaki iki noktayı dikkate almalısınız:</span><span class="sxs-lookup"><span data-stu-id="95f7d-119">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="95f7d-120">Sınıfların türetireceği olası avantajlar, sınıfınızı özelleştirme özelliği aracılığıyla elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="95f7d-120">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="95f7d-121">Sınıfları Türetmenin olasılığı, sınıflarınızı daha sonra düzgün şekilde veya beklendiği gibi çalışmayacak şekilde değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="95f7d-121">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="95f7d-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="95f7d-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="95f7d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95f7d-123">See also</span></span>

- [<span data-ttu-id="95f7d-124">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="95f7d-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="95f7d-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="95f7d-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="95f7d-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="95f7d-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="95f7d-127">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="95f7d-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="95f7d-128">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="95f7d-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="95f7d-129">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="95f7d-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="95f7d-130">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="95f7d-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="95f7d-131">override</span><span class="sxs-lookup"><span data-stu-id="95f7d-131">override</span></span>](override.md)
- [<span data-ttu-id="95f7d-132">virtual</span><span class="sxs-lookup"><span data-stu-id="95f7d-132">virtual</span></span>](virtual.md)
