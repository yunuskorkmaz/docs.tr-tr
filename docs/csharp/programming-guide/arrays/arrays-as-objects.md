---
title: Nesne Olarak Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 07e824d21ffc02ba7a3c33507d22d1dc7a1ac638
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33312614"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="f7724-102">Nesne Olarak Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f7724-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="f7724-103">C# ' ta gerçekte nesneleri ve bitişik bellek C ve C++ olduğu gibi yalnızca adreslenebilir bölümlerinin dizidir.</span><span class="sxs-lookup"><span data-stu-id="f7724-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="f7724-104"><xref:System.Array> soyut taban tüm dizi türleri türüdür.</span><span class="sxs-lookup"><span data-stu-id="f7724-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="f7724-105">Özelliklerini ve diğer sınıf üyeleri kullanabilirsiniz, <xref:System.Array> sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7724-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="f7724-106">Bunun bir örneğini kullanarak <xref:System.Array.Length%2A> bir dizi uzunluğu, alınacağı özellik.</span><span class="sxs-lookup"><span data-stu-id="f7724-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="f7724-107">Aşağıdaki kod uzunluğu atar `numbers` olan dizi `5`, adlı bir değişkene `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="f7724-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="f7724-108"><xref:System.Array> Sınıfı, diğer birçok kullanışlı yöntemler ve sıralama, arama ve dizileri kopyalamak için özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7724-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7724-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7724-109">Example</span></span>  
 <span data-ttu-id="f7724-110">Bu örnekte <xref:System.Array.Rank%2A> bir dizinin boyut sayısını görüntülemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="f7724-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f7724-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7724-111">See Also</span></span>  
 [<span data-ttu-id="f7724-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f7724-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f7724-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="f7724-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="f7724-114">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="f7724-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="f7724-115">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="f7724-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="f7724-116">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="f7724-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
