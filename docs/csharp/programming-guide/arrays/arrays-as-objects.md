---
title: Nesneler Olarak Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715100"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="af8d9-102">Nesne Olarak Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="af8d9-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="af8d9-103">C#'da diziler aslında nesnelerdir ve c ve c++'daki gibi bitişik belleğin yalnızca adreslenebilir bölgeleri değildir.</span><span class="sxs-lookup"><span data-stu-id="af8d9-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="af8d9-104"><xref:System.Array>tüm dizi türlerinin soyut temel türüdür.</span><span class="sxs-lookup"><span data-stu-id="af8d9-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="af8d9-105">Özellikleri ve <xref:System.Array> sahip diğer sınıf üyeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af8d9-105">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="af8d9-106">Bunun bir örneği, <xref:System.Array.Length%2A> bir dizinin uzunluğunu almak için özelliği kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="af8d9-106">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="af8d9-107">Aşağıdaki kod, dizinin `numbers` uzunluğunu atar, `5`bu da `lengthOfNumbers`, adlı bir değişkene:</span><span class="sxs-lookup"><span data-stu-id="af8d9-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="af8d9-108">Sınıf, <xref:System.Array> dizileri sıralamak, aramak ve kopyalamak için diğer birçok yararlı yöntem ve özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="af8d9-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="af8d9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="af8d9-109">Example</span></span>

<span data-ttu-id="af8d9-110">Bu örnek, <xref:System.Array.Rank%2A> bir dizinin boyut sayısını görüntülemek için özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="af8d9-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="af8d9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af8d9-111">See also</span></span>

- [<span data-ttu-id="af8d9-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="af8d9-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="af8d9-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="af8d9-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="af8d9-114">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="af8d9-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="af8d9-115">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="af8d9-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="af8d9-116">Basit Diziler</span><span class="sxs-lookup"><span data-stu-id="af8d9-116">Jagged Arrays</span></span>](./jagged-arrays.md)
