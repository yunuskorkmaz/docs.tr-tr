---
title: -Nesne olarak diziler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 8500cf508b77a0fa7e348ce0fe6b1f16fd2bab25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683983"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="1625f-102">Nesne Olarak Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1625f-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="1625f-103">C# ' ta aslında nesneler ve yalnızca adreslenebilir C ve C++ gibi bitişik bellek bölümlerinin dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="1625f-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="1625f-104"><xref:System.Array> Tüm dizi türleri soyut temel türüdür.</span><span class="sxs-lookup"><span data-stu-id="1625f-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="1625f-105">Özellikleri ve diğer sınıf üyeleri kullanabilirsiniz, <xref:System.Array> sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1625f-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="1625f-106">Bunun bir örneğini kullanarak <xref:System.Array.Length%2A> dizinin uzunluğunu alınacağı özellik.</span><span class="sxs-lookup"><span data-stu-id="1625f-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="1625f-107">Aşağıdaki kod uzunluğunu atar `numbers` dizisi `5`, adında bir değişkene `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="1625f-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <span data-ttu-id="1625f-108"><xref:System.Array> Diğer birçok kullanışlı yöntemler ve Özellikler diziler kopyalama sıralama ve arama için sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="1625f-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1625f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1625f-109">Example</span></span>

 <span data-ttu-id="1625f-110">Bu örnekte <xref:System.Array.Rank%2A> bir dizinin boyut sayısını görüntülemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="1625f-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1625f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1625f-111">See also</span></span>

- [<span data-ttu-id="1625f-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1625f-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1625f-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="1625f-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="1625f-114">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="1625f-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="1625f-115">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="1625f-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [<span data-ttu-id="1625f-116">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="1625f-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
