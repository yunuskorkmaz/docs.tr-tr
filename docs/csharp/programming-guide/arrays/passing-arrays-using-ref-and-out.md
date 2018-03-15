---
title: "ref ve out Kullanarak Dizileri Geçirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f76f63aee0100c6af6bde73c8543b4e7136b1954
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="7a302-102">ref ve out Kullanarak Dizileri Geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7a302-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>
<span data-ttu-id="7a302-103">Tüm [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri, bir `out` kullanılmadan önce bir dizi türü parametresinin atanmalıdır; diğer bir deyişle, aranan tarafından atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a302-103">Like all [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="7a302-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7a302-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 <span data-ttu-id="7a302-105">Tüm [ref](../../../csharp/language-reference/keywords/ref.md) parametreleri, bir `ref` parametresi bir dizi türü, çağıran tarafından kesinlikle da atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a302-105">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="7a302-106">Bu nedenle, kesinlikle Aranan tarafından atanmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="7a302-106">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="7a302-107">A `ref` parametresi bir dizi türü, çağrı sonucu olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7a302-107">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="7a302-108">Örneğin, dizi atanabilir [null](../../../csharp/language-reference/keywords/null.md) değer veya farklı bir dizi başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a302-108">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="7a302-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7a302-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 <span data-ttu-id="7a302-110">Aşağıdaki iki örnek arasındaki farkı göstermek `out` ve `ref` yöntemlerine dizileri geçirme içinde kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="7a302-110">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a302-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a302-111">Example</span></span>  
 <span data-ttu-id="7a302-112">Bu örnekte, dizi `theArray` çağrı yapan bildirilmiş ( `Main` yöntemi) ve içinde başlatılmış `FillArray` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7a302-112">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="7a302-113">Sonra, dizi öğeleri arayana döndürülür ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7a302-113">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="7a302-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a302-114">Example</span></span>  
 <span data-ttu-id="7a302-115">Bu örnekte, dizi `theArray` çağrı yapan başlatıldı ( `Main` yöntemi) ve geçirilen `FillArray` yöntemi kullanarak `ref` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7a302-115">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="7a302-116">Dizi öğeleri bazıları uygulamasında güncelleştirilir `FillArray` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7a302-116">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="7a302-117">Sonra, dizi öğeleri arayana döndürülür ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7a302-117">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7a302-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a302-118">See Also</span></span>  
 [<span data-ttu-id="7a302-119">ref</span><span class="sxs-lookup"><span data-stu-id="7a302-119">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
 [<span data-ttu-id="7a302-120">out parametresi değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="7a302-120">out parameter modifier</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [<span data-ttu-id="7a302-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7a302-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7a302-122">Diziler</span><span class="sxs-lookup"><span data-stu-id="7a302-122">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="7a302-123">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="7a302-123">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="7a302-124">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="7a302-124">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="7a302-125">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="7a302-125">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
