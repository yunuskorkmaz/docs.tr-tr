---
title: Nesne Olarak Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: f1abe10839c30d48f56ac6044d75d290a59b4cce
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505565"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="7a57b-102">Nesne Olarak Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7a57b-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="7a57b-103">C# ' ta aslında nesneler ve yalnızca adreslenebilir C ve C++ gibi bitişik bellek bölümlerinin dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="7a57b-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="7a57b-104"><xref:System.Array> Tüm dizi türleri soyut temel türüdür.</span><span class="sxs-lookup"><span data-stu-id="7a57b-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="7a57b-105">Özellikleri ve diğer sınıf üyeleri kullanabilirsiniz, <xref:System.Array> sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7a57b-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="7a57b-106">Bunun bir örneğini kullanarak <xref:System.Array.Length%2A> dizinin uzunluğunu alınacağı özellik.</span><span class="sxs-lookup"><span data-stu-id="7a57b-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="7a57b-107">Aşağıdaki kod uzunluğunu atar `numbers` dizisi `5`, adında bir değişkene `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="7a57b-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="7a57b-108"><xref:System.Array> Diğer birçok kullanışlı yöntemler ve Özellikler diziler kopyalama sıralama ve arama için sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a57b-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a57b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a57b-109">Example</span></span>

 <span data-ttu-id="7a57b-110">Bu örnekte <xref:System.Array.Rank%2A> bir dizinin boyut sayısını görüntülemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="7a57b-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7a57b-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a57b-111">See Also</span></span>

- [<span data-ttu-id="7a57b-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7a57b-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7a57b-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="7a57b-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="7a57b-114">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="7a57b-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="7a57b-115">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="7a57b-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [<span data-ttu-id="7a57b-116">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="7a57b-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
