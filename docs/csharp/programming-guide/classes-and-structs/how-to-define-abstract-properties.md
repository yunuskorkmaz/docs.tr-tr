---
title: Özet özelliklerini tanımlama- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705619"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="21039-102">Özet özellikleri tanımlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="21039-102">How to define abstract properties (C# Programming Guide)</span></span>
<span data-ttu-id="21039-103">Aşağıdaki örnek, [soyut](../../language-reference/keywords/abstract.md) özelliklerin nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21039-103">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="21039-104">Soyut özellik bildirimi, özellik erişimcilerinin bir uygulamasını sağlamaz--sınıfın özellikleri desteklediğini bildirir, ancak erişimci uygulamasını türetilmiş sınıflara bırakır.</span><span class="sxs-lookup"><span data-stu-id="21039-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="21039-105">Aşağıdaki örnek, temel bir sınıftan devralınan soyut özelliklerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21039-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="21039-106">Bu örnek, her biri ayrı ayrı derlenen üç dosyadan oluşur ve sonuçta elde edilen derlemeye sonraki derleme tarafından başvurulur:</span><span class="sxs-lookup"><span data-stu-id="21039-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="21039-107">abstractshape.cs: soyut bir `Area` özelliği içeren `Shape` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21039-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="21039-108">shapes.cs: `Shape` sınıfının alt sınıfları.</span><span class="sxs-lookup"><span data-stu-id="21039-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="21039-109">shapetest.cs: bazı `Shape`türetilmiş nesnelerin bölümlerini görüntüleyen bir test programı.</span><span class="sxs-lookup"><span data-stu-id="21039-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="21039-110">Örneği derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="21039-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="21039-111">Bu, shapetest. exe yürütülebilir dosyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21039-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21039-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="21039-112">Example</span></span>  
 <span data-ttu-id="21039-113">Bu dosya, `double`türünün `Area` özelliğini içeren `Shape` sınıfını bildirir.</span><span class="sxs-lookup"><span data-stu-id="21039-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="21039-114">Özelliğindeki değiştiriciler Özellik bildiriminin kendine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="21039-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="21039-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="21039-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="21039-116">Soyut bir özellik bildirirken (Bu örnekte `Area` gibi), yalnızca hangi özellik erişimcilerinin kullanılabildiğini, ancak uygulamadığını belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21039-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="21039-117">Bu örnekte, yalnızca bir [Get](../../language-reference/keywords/get.md) erişimcisi bulunur, bu nedenle özellik salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="21039-117">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21039-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="21039-118">Example</span></span>  
 <span data-ttu-id="21039-119">Aşağıdaki kod `Shape` üç alt kümesini ve kendi uygulamasını sağlamak için `Area` özelliğini nasıl geçersiz kıladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21039-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="21039-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="21039-120">Example</span></span>  
 <span data-ttu-id="21039-121">Aşağıdaki kod `Shape`türetilmiş bir nesne oluşturan bir test programı gösterir ve kendi alanını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="21039-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="21039-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21039-122">See also</span></span>

- [<span data-ttu-id="21039-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="21039-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="21039-124">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="21039-124">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="21039-125">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="21039-125">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="21039-126">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="21039-126">Properties</span></span>](./properties.md)
