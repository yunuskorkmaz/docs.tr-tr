---
title: Soyut özellikler nasıl tanımlanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705619"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="53b42-102">Soyut özellikler nasıl tanımlanır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="53b42-102">How to define abstract properties (C# Programming Guide)</span></span>
<span data-ttu-id="53b42-103">Aşağıdaki örnek, [soyut](../../language-reference/keywords/abstract.md) özelliklerin nasıl tanımlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="53b42-103">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="53b42-104">Soyut bir özellik bildirimi özellik erişime girenlerin bir uygulamasını sağlamaz - sınıfın özellikleri desteklediğini, ancak erişime açan uygulamayı türetilmiş sınıflara bıraktığını beyan eder.</span><span class="sxs-lookup"><span data-stu-id="53b42-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="53b42-105">Aşağıdaki örnek, taban sınıftan devralınan soyut özelliklerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="53b42-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="53b42-106">Bu örnek, her biri ayrı ayrı derlenen ve ortaya çıkan derleme sonraki derleme ile başvurulan üç dosyadan oluşur:</span><span class="sxs-lookup"><span data-stu-id="53b42-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="53b42-107">abstractshape.cs: `Shape` soyut `Area` bir özellik içeren sınıf.</span><span class="sxs-lookup"><span data-stu-id="53b42-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="53b42-108">shapes.cs: `Shape` Sınıfın alt sınıfları.</span><span class="sxs-lookup"><span data-stu-id="53b42-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="53b42-109">shapetest.cs: Bazı `Shape`türetilmiş nesnelerin alanlarını görüntülemek için bir test programı.</span><span class="sxs-lookup"><span data-stu-id="53b42-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="53b42-110">Örneği derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="53b42-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="53b42-111">Bu, yürütülebilir dosya shapetest.exe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53b42-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53b42-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="53b42-112">Example</span></span>  
 <span data-ttu-id="53b42-113">Bu dosya, `Shape` türünün `Area` `double`özelliğini içeren sınıfı bildirir.</span><span class="sxs-lookup"><span data-stu-id="53b42-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="53b42-114">Mülküzerindeki değiştiriciler mülk beyannamesinin kendisine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="53b42-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="53b42-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="53b42-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="53b42-116">Soyut bir özellik (bu `Area` örnekte olduğu gibi) bildirirken, yalnızca hangi özellik erişime erişime erişimsağlayanların kullanılabildiğini belirtirsiniz, ancak bunları uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="53b42-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="53b42-117">Bu örnekte, yalnızca [get](../../language-reference/keywords/get.md) accessor kullanılabilir, bu nedenle özellik salt okunur.</span><span class="sxs-lookup"><span data-stu-id="53b42-117">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53b42-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="53b42-118">Example</span></span>  
 <span data-ttu-id="53b42-119">Aşağıdaki kod, kendi uygulamalarını `Shape` sağlamak için `Area` özelliği nasıl geçersiz kıldıklarını ve üç alt sınıflarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="53b42-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="53b42-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="53b42-120">Example</span></span>  
 <span data-ttu-id="53b42-121">Aşağıdaki kod, bir dizi `Shape`türetilmiş nesne oluşturan ve alanlarını yazdıran bir test programı gösterir.</span><span class="sxs-lookup"><span data-stu-id="53b42-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="53b42-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53b42-122">See also</span></span>

- [<span data-ttu-id="53b42-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="53b42-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="53b42-124">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="53b42-124">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="53b42-125">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="53b42-125">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="53b42-126">Özellikler</span><span class="sxs-lookup"><span data-stu-id="53b42-126">Properties</span></span>](./properties.md)
