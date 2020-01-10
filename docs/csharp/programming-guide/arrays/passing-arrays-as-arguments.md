---
title: Dizileri bağımsız değişkenler olarak geçirme C# -Programlama Kılavuzu
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705697"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="77749-102">Dizileri bağımsız değişkenler olarak geçirmeC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="77749-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="77749-103">Diziler, yöntem parametrelerine bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="77749-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="77749-104">Diziler başvuru türleri olduğundan, yöntemi öğelerinin değerini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="77749-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="77749-105">Tek boyutlu dizileri bağımsız değişkenler olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="77749-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="77749-106">Başlatılmış bir tek boyutlu diziyi bir yönteme geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77749-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="77749-107">Örneğin, aşağıdaki ifade bir PRINT yöntemine bir dizi gönderir.</span><span class="sxs-lookup"><span data-stu-id="77749-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="77749-108">Aşağıdaki kod, Print yönteminin kısmi bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="77749-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="77749-109">Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek bir adımda başlatabilir ve geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77749-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="77749-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="77749-110">Example</span></span>

<span data-ttu-id="77749-111">Aşağıdaki örnekte, dizeler dizisi başlatılır ve dizeler için bir `DisplayArray` metoduna bir bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="77749-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="77749-112">Yöntemi, dizinin öğelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="77749-112">The method displays the elements of the array.</span></span> <span data-ttu-id="77749-113">Sonra `ChangeArray` yöntemi dizi öğelerini tersine çevirir ve sonra `ChangeArrayElements` yöntemi dizinin ilk üç öğesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="77749-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="77749-114">Her yöntemin döndürdüğü `DisplayArray` yöntemi, diziyi değere göre geçirmenin dizi öğelerinde değişiklik yapılmasını önleyemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77749-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="77749-115">Çok boyutlu dizileri bağımsız değişken olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="77749-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="77749-116">Başlatılmış bir çok boyutlu diziyi, tek boyutlu bir diziyi geçirdiğiniz şekilde bir yönteme geçirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77749-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="77749-117">Aşağıdaki kod, bağımsız değişkeni olarak iki boyutlu bir diziyi kabul eden bir Print yönteminin kısmi bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77749-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="77749-118">Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek bir adımda başlatabilir ve geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="77749-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="77749-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="77749-119">Example</span></span>

<span data-ttu-id="77749-120">Aşağıdaki örnekte, iki boyutlu bir tamsayılar dizisi başlatılır ve `Print2DArray` yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="77749-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="77749-121">Yöntemi, dizinin öğelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="77749-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="77749-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77749-122">See also</span></span>

- [<span data-ttu-id="77749-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="77749-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="77749-124">Diziler</span><span class="sxs-lookup"><span data-stu-id="77749-124">Arrays</span></span>](index.md)
- [<span data-ttu-id="77749-125">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="77749-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="77749-126">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="77749-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="77749-127">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="77749-127">Jagged Arrays</span></span>](jagged-arrays.md)
