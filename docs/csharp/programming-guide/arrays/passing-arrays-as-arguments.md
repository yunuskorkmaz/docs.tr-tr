---
title: Dizileri bağımsız değişkenler (C# programlama Kılavuzu) olarak geçirme
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 0289297be9d7b4989cc95d2b50b92dae9ee831f7
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199237"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="d41c9-102">Dizileri bağımsız değişkenler (C# programlama Kılavuzu) olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="d41c9-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="d41c9-103">Dizileri bağımsız değişkenler olarak yöntemi parametrelerine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d41c9-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="d41c9-104">Yöntemi, diziler, başvuru türleri olduğundan, öğelerin değerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d41c9-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="d41c9-105">Tek boyutlu dizileri bağımsız değişkenler olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="d41c9-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="d41c9-106">Başlatılmış bir tek boyutlu dizi için bir yöntem geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d41c9-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="d41c9-107">Örneğin, aşağıdaki deyim, yazdırma bir yönteme bir dizi gönderir.</span><span class="sxs-lookup"><span data-stu-id="d41c9-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="d41c9-108">Aşağıdaki kod, yazdırma yöntemin kısmi bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d41c9-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="d41c9-109">Başlatın ve aşağıdaki örnekte gösterildiği gibi bir adım, yeni bir dizi geçirin.</span><span class="sxs-lookup"><span data-stu-id="d41c9-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="d41c9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d41c9-110">Example</span></span>

<span data-ttu-id="d41c9-111">Aşağıdaki örnekte, dize dizisi başlatılır ve bağımsız değişken olarak geçirilen bir `DisplayArray` dizeler için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d41c9-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="d41c9-112">Yöntemi, dizinin öğeleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d41c9-112">The method displays the elements of the array.</span></span> <span data-ttu-id="d41c9-113">Ardından, `ChangeArray` yöntemi, dizi öğelerinin tersine çevirir ve ardından `ChangeArrayElements` yöntemi, dizinin ilk üç öğeleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d41c9-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="d41c9-114">Her yöntemin dönüşünün ardından `DisplayArray` yöntemi bir dizi değere göre geçirme değişiklikleri dizi öğelerine engellemez olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d41c9-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="d41c9-115">Çok boyutlu diziler bağımsız değişken olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="d41c9-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="d41c9-116">Başlatılmış bir çok boyutlu dizi tek boyutlu dizi geçirdiğiniz aynı şekilde bir yönteme geçirin.</span><span class="sxs-lookup"><span data-stu-id="d41c9-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="d41c9-117">Aşağıdaki kod iki boyutlu bir dizi bağımsız değişken olarak kabul eden bir yazdırma yöntemin kısmi bir bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d41c9-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="d41c9-118">Başlatın ve aşağıdaki örnekte gösterildiği gibi bir adım, yeni bir dizi geçirin:</span><span class="sxs-lookup"><span data-stu-id="d41c9-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="d41c9-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d41c9-119">Example</span></span>

<span data-ttu-id="d41c9-120">Aşağıdaki örnekte, iki boyutlu bir tamsayı dizisi başlatılır ve geçirilen `Print2DArray` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d41c9-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="d41c9-121">Yöntemi, dizinin öğeleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d41c9-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="d41c9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d41c9-122">See also</span></span>

[<span data-ttu-id="d41c9-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d41c9-123">C# Programming Guide</span></span>](../index.md)  
[<span data-ttu-id="d41c9-124">Diziler</span><span class="sxs-lookup"><span data-stu-id="d41c9-124">Arrays</span></span>](index.md)  
[<span data-ttu-id="d41c9-125">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="d41c9-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
[<span data-ttu-id="d41c9-126">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="d41c9-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
[<span data-ttu-id="d41c9-127">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="d41c9-127">Jagged Arrays</span></span>](jagged-arrays.md)  