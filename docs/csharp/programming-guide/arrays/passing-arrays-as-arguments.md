---
title: Dizileri bağımsız değişkenler olarak geçirme-C# Programlama Kılavuzu
description: C# içindeki diziler, yöntem parametrelerine bağımsız değişken olarak geçirilebilir. Diziler başvuru türleri olduğundan, yöntemi öğelerinin değerini değiştirebilir.
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 68f174421e56e2cf082fe670f93c4f6627d7c17b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474637"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="3b42e-104">Dizileri bağımsız değişkenler olarak geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3b42e-104">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="3b42e-105">Diziler, yöntem parametrelerine bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3b42e-105">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="3b42e-106">Diziler başvuru türleri olduğundan, yöntemi öğelerinin değerini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="3b42e-106">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="3b42e-107">Tek boyutlu dizileri bağımsız değişkenler olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="3b42e-107">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="3b42e-108">Başlatılmış bir tek boyutlu diziyi bir yönteme geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b42e-108">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="3b42e-109">Örneğin, aşağıdaki ifade bir PRINT yöntemine bir dizi gönderir.</span><span class="sxs-lookup"><span data-stu-id="3b42e-109">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="3b42e-110">Aşağıdaki kod, Print yönteminin kısmi bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b42e-110">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="3b42e-111">Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek bir adımda başlatabilir ve geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b42e-111">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="3b42e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b42e-112">Example</span></span>

<span data-ttu-id="3b42e-113">Aşağıdaki örnekte, dizeler dizisi başlatılır ve dizeler için bir yönteme bağımsız değişken olarak geçirilir `DisplayArray` .</span><span class="sxs-lookup"><span data-stu-id="3b42e-113">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="3b42e-114">Yöntemi, dizinin öğelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3b42e-114">The method displays the elements of the array.</span></span> <span data-ttu-id="3b42e-115">Sonra, `ChangeArray` yöntemi dizi öğelerini tersine çevirir ve sonra `ChangeArrayElements` yöntemin ilk üç öğesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3b42e-115">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="3b42e-116">Her yöntemin döndürdüğü `DisplayArray` Yöntem, bir diziyi değere göre geçirmenin dizi öğelerinde değişiklik yapılmasını önleyemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b42e-116">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="3b42e-117">Çok boyutlu dizileri bağımsız değişken olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="3b42e-117">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="3b42e-118">Başlatılmış bir çok boyutlu diziyi, tek boyutlu bir diziyi geçirdiğiniz şekilde bir yönteme geçirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b42e-118">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="3b42e-119">Aşağıdaki kod, bağımsız değişkeni olarak iki boyutlu bir diziyi kabul eden bir Print yönteminin kısmi bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b42e-119">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="3b42e-120">Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek bir adımda başlatabilir ve geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b42e-120">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="3b42e-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b42e-121">Example</span></span>

<span data-ttu-id="3b42e-122">Aşağıdaki örnekte, iki boyutlu bir tamsayılar dizisi başlatılır ve `Print2DArray` yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3b42e-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="3b42e-123">Yöntemi, dizinin öğelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3b42e-123">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="3b42e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b42e-124">See also</span></span>

- [<span data-ttu-id="3b42e-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3b42e-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3b42e-126">Diziler</span><span class="sxs-lookup"><span data-stu-id="3b42e-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="3b42e-127">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="3b42e-127">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="3b42e-128">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="3b42e-128">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="3b42e-129">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="3b42e-129">Jagged Arrays</span></span>](jagged-arrays.md)
