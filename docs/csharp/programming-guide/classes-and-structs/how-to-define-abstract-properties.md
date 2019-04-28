---
title: 'Nasıl yapılır: -Soyut özellikleri tanımlama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 98a535f68efc50c2ff7409d8eadf52f9e7549566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646442"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="a3351-102">Nasıl yapılır: Soyut özellikleri tanımlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a3351-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="a3351-103">Aşağıdaki örnek nasıl tanımlanacağını gösterir [soyut](../../../csharp/language-reference/keywords/abstract.md) özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a3351-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="a3351-104">Bir soyut özellik bildiriminde özellik erişimcileri uygulaması sağlamaz--sınıf özelliklerini destekler, ancak türetilmiş sınıfları için erişimci uygulama bırakır bildirir.</span><span class="sxs-lookup"><span data-stu-id="a3351-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="a3351-105">Aşağıdaki örnek, bir temel sınıftan devralınan soyut Özellikler uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a3351-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="a3351-106">Bu örnek, her biri ayrı ayrı derlenmiş üç dosyasından oluşur ve sonuçta elde edilen derlemesi sonraki derleme tarafından başvuruluyor:</span><span class="sxs-lookup"><span data-stu-id="a3351-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="a3351-107">abstractshape.cs: `Shape` içeren bir soyut sınıf `Area` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a3351-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="a3351-108">Shapes.cs: Alt sınıflarından birini `Shape` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a3351-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="a3351-109">shapetest.cs: Bazı alanları görüntülemek için bir test programı `Shape`-türetilmiş nesneler.</span><span class="sxs-lookup"><span data-stu-id="a3351-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="a3351-110">Örneği derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a3351-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="a3351-111">Bu yürütülebilir dosya shapetest.exe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3351-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3351-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3351-112">Example</span></span>  
 <span data-ttu-id="a3351-113">Bu dosya bildirir `Shape` içeren sınıf `Area` türünün özelliği `double`.</span><span class="sxs-lookup"><span data-stu-id="a3351-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="a3351-114">Modifiers özelliğini özellik bildiriminde kendisini yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a3351-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="a3351-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a3351-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="a3351-116">Bir soyut özelliğini bildirirken (gibi `Area` Bu örnekte), yalnızca hangi özellik erişimcileri kullanılabilir gösterir ancak bunları kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a3351-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="a3351-117">Bu örnekte, yalnızca bir [alma](../../../csharp/language-reference/keywords/get.md) özelliği salt okunur şekilde erişimci kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3351-117">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3351-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3351-118">Example</span></span>  
 <span data-ttu-id="a3351-119">Aşağıdaki kod üç alt sınıflarını gösterir `Shape` ve bunların nasıl geçersiz `Area` kendi uygulamasını sağlamak üzere özelliği.</span><span class="sxs-lookup"><span data-stu-id="a3351-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="a3351-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3351-120">Example</span></span>  
 <span data-ttu-id="a3351-121">Aşağıdaki kod bir dizi oluşturur. bir test programı gösterir `Shape`-türetilmiş nesneler ve onların alanları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a3351-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a3351-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3351-122">See also</span></span>

- [<span data-ttu-id="a3351-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a3351-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a3351-124">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="a3351-124">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="a3351-125">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="a3351-125">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="a3351-126">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a3351-126">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="a3351-127">Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="a3351-127">How to: Create and Use Assemblies Using the Command Line</span></span>](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
