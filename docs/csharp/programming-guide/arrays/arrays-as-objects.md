---
title: Nesneler olarak diziler-C# Programlama Kılavuzu
description: C# içindeki diziler soyut temel tür dizisinin nesneleridir. Array öğesinin özelliklerini ve diğer sınıf üyelerini (length özelliği gibi) kullanabilirsiniz.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474728"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="c7252-104">Nesne Olarak Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c7252-104">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="c7252-105">C# ' de, diziler aslında nesneler ve yalnızca C ve C++ ' da olduğu gibi bitişik belleğin adreslenebilir bölgelerini değildir.</span><span class="sxs-lookup"><span data-stu-id="c7252-105">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="c7252-106"><xref:System.Array>tüm dizi türlerinin soyut temel türüdür.</span><span class="sxs-lookup"><span data-stu-id="c7252-106"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="c7252-107">Özellikleri ve olan diğer sınıf üyelerini kullanabilirsiniz <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="c7252-107">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="c7252-108">Bunun bir örneği, <xref:System.Array.Length%2A> bir dizinin uzunluğunu almak için özelliğini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c7252-108">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="c7252-109">Aşağıdaki kod, dizi uzunluğunu, `numbers` yani `5` adlı bir değişkene atar `lengthOfNumbers` :</span><span class="sxs-lookup"><span data-stu-id="c7252-109">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="c7252-110"><xref:System.Array>Sınıfı, dizileri sıralamak, aramak ve kopyalamak için diğer birçok yararlı yöntem ve özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7252-110">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="c7252-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7252-111">Example</span></span>

<span data-ttu-id="c7252-112">Bu örnek, <xref:System.Array.Rank%2A> bir dizinin boyut sayısını göstermek için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7252-112">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="c7252-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7252-113">See also</span></span>

- [<span data-ttu-id="c7252-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7252-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c7252-115">Diziler</span><span class="sxs-lookup"><span data-stu-id="c7252-115">Arrays</span></span>](./index.md)
- [<span data-ttu-id="c7252-116">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="c7252-116">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="c7252-117">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="c7252-117">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="c7252-118">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="c7252-118">Jagged Arrays</span></span>](./jagged-arrays.md)
