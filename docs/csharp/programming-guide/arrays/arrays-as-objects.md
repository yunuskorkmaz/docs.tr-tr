---
title: "Nesne Olarak Diziler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e29685af509009f42f38ba2dbf8524075e880ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="f8ff6-102">Nesne Olarak Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f8ff6-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="f8ff6-103">C# ' ta gerçekte nesneleri ve bitişik bellek C ve C++ olduğu gibi yalnızca adreslenebilir bölümlerinin dizidir.</span><span class="sxs-lookup"><span data-stu-id="f8ff6-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="f8ff6-104"><xref:System.Array>soyut taban tüm dizi türleri türüdür.</span><span class="sxs-lookup"><span data-stu-id="f8ff6-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="f8ff6-105">Özelliklerini ve diğer sınıf üyeleri kullanabilirsiniz, <xref:System.Array> sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f8ff6-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="f8ff6-106">Bunun bir örneğini kullanarak <xref:System.Array.Length%2A> bir dizi uzunluğu, alınacağı özellik.</span><span class="sxs-lookup"><span data-stu-id="f8ff6-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="f8ff6-107">Aşağıdaki kod uzunluğu atar `numbers` olan dizi `5`, adlı bir değişkene `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="f8ff6-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="f8ff6-108"><xref:System.Array> Sınıfı, diğer birçok kullanışlı yöntemler ve sıralama, arama ve dizileri kopyalamak için özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8ff6-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8ff6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8ff6-109">Example</span></span>  
 <span data-ttu-id="f8ff6-110">Bu örnekte <xref:System.Array.Rank%2A> bir dizinin boyut sayısını görüntülemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="f8ff6-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f8ff6-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8ff6-111">See Also</span></span>  
 [<span data-ttu-id="f8ff6-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f8ff6-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f8ff6-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="f8ff6-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="f8ff6-114">Tek boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="f8ff6-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="f8ff6-115">Çok boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="f8ff6-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="f8ff6-116">Basit diziler</span><span class="sxs-lookup"><span data-stu-id="f8ff6-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
