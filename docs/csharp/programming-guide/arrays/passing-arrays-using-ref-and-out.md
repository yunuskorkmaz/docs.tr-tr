---
title: ref ve out Kullanarak Dizileri Geçirme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
ms.openlocfilehash: 8da3bf9f8eede72a7bc3cf8380eab66ca2b56e86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526771"
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="aad49-102">ref ve out Kullanarak Dizileri Geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="aad49-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>

<span data-ttu-id="aad49-103">Tüm [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri bir `out` kullanılmadan önce bir dizi türünde bir parametresi atanmalıdır; yani, aranan tarafından atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aad49-103">Like all [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="aad49-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="aad49-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 <span data-ttu-id="aad49-105">Tüm [ref](../../../csharp/language-reference/keywords/ref.md) parametreleri bir `ref` bir dizi türünde bir parametresi arayan tarafından kesinlikle da atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aad49-105">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="aad49-106">Bu nedenle, kesinlikle Aranan tarafından atanmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="aad49-106">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="aad49-107">A `ref` bir dizi türünde bir parametresi çağrının bir sonucu olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="aad49-107">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="aad49-108">Örneğin, bir dizi atanabilir [null](../../../csharp/language-reference/keywords/null.md) değer veya farklı bir dizi olarak başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="aad49-108">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="aad49-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="aad49-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 <span data-ttu-id="aad49-110">Aşağıdaki iki örnek arasındaki farkı göstermek `out` ve `ref` dizileri yöntemlere geçirirken kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="aad49-110">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aad49-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="aad49-111">Example</span></span>

 <span data-ttu-id="aad49-112">Bu örnekte, dizi `theArray` arayanda ( `Main` yöntemi) ve içinde başlatılan `FillArray` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aad49-112">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="aad49-113">Sonra, dizi öğeleri arayana döndürülür ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aad49-113">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]

## <a name="example"></a><span data-ttu-id="aad49-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="aad49-114">Example</span></span>

 <span data-ttu-id="aad49-115">Bu örnekte, dizi `theArray` arayanda başlatılır ( `Main` yöntemi) ve geçirilen `FillArray` yöntemi kullanarak `ref` parametresi.</span><span class="sxs-lookup"><span data-stu-id="aad49-115">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="aad49-116">Bazı dizi öğeleri güncellenir `FillArray` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aad49-116">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="aad49-117">Sonra, dizi öğeleri arayana döndürülür ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aad49-117">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="aad49-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aad49-118">See Also</span></span>

- [<span data-ttu-id="aad49-119">ref</span><span class="sxs-lookup"><span data-stu-id="aad49-119">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
- [<span data-ttu-id="aad49-120">out parametresi değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="aad49-120">out parameter modifier</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
- [<span data-ttu-id="aad49-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aad49-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="aad49-122">Diziler</span><span class="sxs-lookup"><span data-stu-id="aad49-122">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="aad49-123">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="aad49-123">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="aad49-124">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="aad49-124">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [<span data-ttu-id="aad49-125">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="aad49-125">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
