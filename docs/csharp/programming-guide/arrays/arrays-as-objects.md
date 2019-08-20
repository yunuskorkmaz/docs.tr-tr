---
title: Nesneler olarak diziler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: fd4496e0f84953204ad8c3f40db699e911c3f477
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597354"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="6d63c-102">Nesne Olarak Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6d63c-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="6d63c-103">' C#De, diziler aslında nesneler ve yalnızca C ve C++' de olduğu gibi bitişik belleğin adreslenebilir bölgelerini içermez.</span><span class="sxs-lookup"><span data-stu-id="6d63c-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="6d63c-104"><xref:System.Array>tüm dizi türlerinin soyut temel türüdür.</span><span class="sxs-lookup"><span data-stu-id="6d63c-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="6d63c-105">Özellikleri ve olan <xref:System.Array> diğer sınıf üyelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d63c-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="6d63c-106">Bunun bir örneği, <xref:System.Array.Length%2A> bir dizinin uzunluğunu almak için özelliğini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6d63c-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="6d63c-107">Aşağıdaki kod, `numbers` dizi uzunluğunu, yani `5`adlı `lengthOfNumbers`bir değişkene atar:</span><span class="sxs-lookup"><span data-stu-id="6d63c-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <span data-ttu-id="6d63c-108"><xref:System.Array> Sınıfı, dizileri sıralamak, aramak ve kopyalamak için diğer birçok yararlı yöntem ve özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d63c-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d63c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d63c-109">Example</span></span>

 <span data-ttu-id="6d63c-110">Bu örnek, <xref:System.Array.Rank%2A> bir dizinin boyut sayısını göstermek için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6d63c-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6d63c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d63c-111">See also</span></span>

- [<span data-ttu-id="6d63c-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6d63c-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6d63c-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="6d63c-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="6d63c-114">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="6d63c-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="6d63c-115">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="6d63c-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="6d63c-116">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="6d63c-116">Jagged Arrays</span></span>](./jagged-arrays.md)
