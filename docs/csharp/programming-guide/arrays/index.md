---
title: Diziler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 24c6d54c3fe92ada661e732adec582e87ab62417
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597523"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="dbc49-102">Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="dbc49-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="dbc49-103">Aynı türde birden çok değişkeni bir dizi veri yapısına saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbc49-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="dbc49-104">Öğelerinin türünü belirterek bir dizi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbc49-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="dbc49-105">Aşağıdaki örnek, tek boyutlu, çok boyutlu ve pürüzlü Diziler oluşturur:</span><span class="sxs-lookup"><span data-stu-id="dbc49-105">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a><span data-ttu-id="dbc49-106">Diziye genel bakış</span><span class="sxs-lookup"><span data-stu-id="dbc49-106">Array Overview</span></span>

 <span data-ttu-id="dbc49-107">Bir dizi aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="dbc49-107">An array has the following properties:</span></span>  
  
- <span data-ttu-id="dbc49-108">Bir dizi [tek boyutlu](./single-dimensional-arrays.md), [çok boyutlu](./multidimensional-arrays.md) veya [pürüzlü](./jagged-arrays.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="dbc49-108">An array can be [Single-Dimensional](./single-dimensional-arrays.md), [Multidimensional](./multidimensional-arrays.md) or [Jagged](./jagged-arrays.md).</span></span>  
  
- <span data-ttu-id="dbc49-109">Boyut sayısı ve her boyutun uzunluğu, dizi örneği oluşturulduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dbc49-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="dbc49-110">Bu değerler, örneğin kullanım ömrü boyunca değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="dbc49-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
- <span data-ttu-id="dbc49-111">Sayısal dizi öğelerinin varsayılan değerleri sıfır olarak ayarlanır ve başvuru öğeleri null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dbc49-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
- <span data-ttu-id="dbc49-112">Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve olarak `null`başlatılır.</span><span class="sxs-lookup"><span data-stu-id="dbc49-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
- <span data-ttu-id="dbc49-113">Diziler sıfır dizinli: öğeleri olan `n` bir dizi ' `n-1`dan `0` ' a dizinlenir.</span><span class="sxs-lookup"><span data-stu-id="dbc49-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
- <span data-ttu-id="dbc49-114">Dizi öğeleri, bir dizi türü de dahil olmak üzere herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="dbc49-114">Array elements can be of any type, including an array type.</span></span>  
  
- <span data-ttu-id="dbc49-115">Dizi türleri, soyut temel türden <xref:System.Array>türetilmiş [başvuru türleridir](../../language-reference/keywords/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="dbc49-115">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="dbc49-116">Bu tür ve <xref:System.Collections.Generic.IEnumerable%601>uyguladığından <xref:System.Collections.IEnumerable> , içindeki C#tüm dizilerde [foreach](../../language-reference/keywords/foreach-in.md) yineleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbc49-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dbc49-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="dbc49-117">Related Sections</span></span>  
  
- [<span data-ttu-id="dbc49-118">Nesne Olarak Diziler</span><span class="sxs-lookup"><span data-stu-id="dbc49-118">Arrays as Objects</span></span>](./arrays-as-objects.md)  
  
- [<span data-ttu-id="dbc49-119">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="dbc49-119">Using foreach with Arrays</span></span>](./using-foreach-with-arrays.md)  
  
- [<span data-ttu-id="dbc49-120">Dizileri Bağımsız Değişkenler Olarak Geçirme</span><span class="sxs-lookup"><span data-stu-id="dbc49-120">Passing Arrays as Arguments</span></span>](./passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="dbc49-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="dbc49-121">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dbc49-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbc49-122">See also</span></span>

- [<span data-ttu-id="dbc49-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dbc49-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dbc49-124">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="dbc49-124">Collections</span></span>](../concepts/collections.md)
