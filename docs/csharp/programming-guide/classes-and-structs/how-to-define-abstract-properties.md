---
title: "Nasıl yapılır: Soyut Özellikleri Tanımlama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cd8a42c1040180c19bc58627ab0c6a21ace77773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="64f5f-102">Nasıl yapılır: Soyut Özellikleri Tanımlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="64f5f-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="64f5f-103">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir [soyut](../../../csharp/language-reference/keywords/abstract.md) özellikleri.</span><span class="sxs-lookup"><span data-stu-id="64f5f-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="64f5f-104">Bir Özet özellik bildirimi özellik erişimcisi uygulaması sağlamaz--sınıf özelliklerini destekler, ancak türetilmiş sınıflara erişimcisi uygulama bırakır bildirir.</span><span class="sxs-lookup"><span data-stu-id="64f5f-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="64f5f-105">Aşağıdaki örnek, bir taban sınıftan devralınan soyut özellikleri uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="64f5f-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="64f5f-106">Bu örnek, her biri ayrı ayrı derlenir üç dosyaları içerir ve sonuçta elde edilen derleme sonraki derlemesi tarafından başvurulan:</span><span class="sxs-lookup"><span data-stu-id="64f5f-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
-   <span data-ttu-id="64f5f-107">abstractshape.cs: `Shape` içeren bir Özet sınıf `Area` özelliği.</span><span class="sxs-lookup"><span data-stu-id="64f5f-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
-   <span data-ttu-id="64f5f-108">Shapes.cs: sınıfları `Shape` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="64f5f-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
-   <span data-ttu-id="64f5f-109">shapetest.cs: bazı alanları görüntülemek için bir test programı `Shape`-türetilmiş nesneleri.</span><span class="sxs-lookup"><span data-stu-id="64f5f-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="64f5f-110">Örnek derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="64f5f-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="64f5f-111">Bu yürütülebilir dosya shapetest.exe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64f5f-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64f5f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="64f5f-112">Example</span></span>  
 <span data-ttu-id="64f5f-113">Bu dosya bildirir `Shape` içeren sınıf `Area` türündeki özelliği `double`.</span><span class="sxs-lookup"><span data-stu-id="64f5f-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   <span data-ttu-id="64f5f-114">Değiştiriciler özelliği üzerinde özellik bildirimi kendisini yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="64f5f-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="64f5f-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="64f5f-115">For example:</span></span>  
  
    ```  
    public abstract double Area  
    ```  
  
-   <span data-ttu-id="64f5f-116">Bir Özet özelliği bildirirken (gibi `Area` Bu örnekte), yalnızca hangi özellik erişimcisi kullanılabilir olduğunu belirtmek ancak bunları kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="64f5f-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="64f5f-117">Bu örnekte, yalnızca bir [almak](../../../csharp/language-reference/keywords/get.md) erişimci kullanılabilir, böylece özelliği salt okunur.</span><span class="sxs-lookup"><span data-stu-id="64f5f-117">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64f5f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="64f5f-118">Example</span></span>  
 <span data-ttu-id="64f5f-119">Aşağıdaki kod üç alt sınıflarının gösterir `Shape` ve bunların nasıl geçersiz kılma `Area` kendi uygulama sunmak amacıyla özelliği.</span><span class="sxs-lookup"><span data-stu-id="64f5f-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="64f5f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="64f5f-120">Example</span></span>  
 <span data-ttu-id="64f5f-121">Aşağıdaki kod bir dizi oluşturan bir test program gösterir `Shape`-türetilen nesneler ve onların alanları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="64f5f-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="64f5f-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64f5f-122">See Also</span></span>  
 [<span data-ttu-id="64f5f-123">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="64f5f-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="64f5f-124">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="64f5f-124">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="64f5f-125">Soyut ve korumalı sınıflar ve sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="64f5f-125">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [<span data-ttu-id="64f5f-126">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="64f5f-126">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="64f5f-127">Nasıl yapılır: komut satırını kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="64f5f-127">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)
