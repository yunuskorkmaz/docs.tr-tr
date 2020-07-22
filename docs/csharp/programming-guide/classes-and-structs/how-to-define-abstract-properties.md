---
title: Özet özelliklerini tanımlama-C# Programlama Kılavuzu
description: C# ' de soyut özellikler tanımlama hakkında bilgi edinin. Bir soyut özelliği bildirmek, bir sınıfın bir özelliği desteklediği anlamına gelir. Türetilmiş sınıflar erişimcileri uygular.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 4db71721495857c634e8090b986704d8a592b4e2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864403"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="961ae-105">Özet özellikleri tanımlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="961ae-105">How to define abstract properties (C# Programming Guide)</span></span>
<span data-ttu-id="961ae-106">Aşağıdaki örnek, [soyut](../../language-reference/keywords/abstract.md) özelliklerin nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="961ae-106">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="961ae-107">Soyut özellik bildirimi, özellik erişimcilerinin bir uygulamasını sağlamaz--sınıfın özellikleri desteklediğini bildirir, ancak erişimci uygulamasını türetilmiş sınıflara bırakır.</span><span class="sxs-lookup"><span data-stu-id="961ae-107">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="961ae-108">Aşağıdaki örnek, temel bir sınıftan devralınan soyut özelliklerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="961ae-108">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="961ae-109">Bu örnek, her biri ayrı ayrı derlenen üç dosyadan oluşur ve sonuçta elde edilen derlemeye sonraki derleme tarafından başvurulur:</span><span class="sxs-lookup"><span data-stu-id="961ae-109">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="961ae-110">abstractshape.cs: `Shape` bir soyut özellik içeren sınıf `Area` .</span><span class="sxs-lookup"><span data-stu-id="961ae-110">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="961ae-111">shapes.cs: sınıfının alt sınıfları `Shape` .</span><span class="sxs-lookup"><span data-stu-id="961ae-111">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="961ae-112">shapetest.cs: bazı türetilmiş nesnelerin bölümlerini görüntüleyen bir test programı `Shape` .</span><span class="sxs-lookup"><span data-stu-id="961ae-112">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="961ae-113">Örneği derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="961ae-113">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="961ae-114">Bu işlem yürütülebilir dosya shapetest.exe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="961ae-114">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="961ae-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="961ae-115">Example</span></span>  
 <span data-ttu-id="961ae-116">Bu dosya, `Shape` türünün özelliğini içeren sınıfını bildirir `Area` `double` .</span><span class="sxs-lookup"><span data-stu-id="961ae-116">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="961ae-117">Özelliğindeki değiştiriciler Özellik bildiriminin kendine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="961ae-117">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="961ae-118">Örnek:</span><span class="sxs-lookup"><span data-stu-id="961ae-118">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="961ae-119">Soyut bir özellik bildirirken ( `Area` Bu örnekte olduğu gibi), yalnızca hangi özellik erişimcilerinin kullanılabilir olduğunu, ancak uygulamadıklarını belirtmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="961ae-119">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="961ae-120">Bu örnekte, yalnızca bir [Get](../../language-reference/keywords/get.md) erişimcisi bulunur, bu nedenle özellik salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="961ae-120">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="961ae-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="961ae-121">Example</span></span>  
 <span data-ttu-id="961ae-122">Aşağıdaki kod, öğesinin üç alt kümesini `Shape` ve `Area` kendi uygulamasını sağlamak için özelliği nasıl geçersiz kıladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="961ae-122">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="961ae-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="961ae-123">Example</span></span>  
 <span data-ttu-id="961ae-124">Aşağıdaki kod, bir dizi `Shape` türetilmiş nesne oluşturan ve alanlarının baskılarını yazdıran bir test programı gösterir.</span><span class="sxs-lookup"><span data-stu-id="961ae-124">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="961ae-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="961ae-125">See also</span></span>

- [<span data-ttu-id="961ae-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="961ae-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="961ae-127">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="961ae-127">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="961ae-128">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="961ae-128">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="961ae-129">Özellikler</span><span class="sxs-lookup"><span data-stu-id="961ae-129">Properties</span></span>](./properties.md)
