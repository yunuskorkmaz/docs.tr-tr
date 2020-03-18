---
title: Dizileri bağımsız değişken olarak geçirme - C# Programlama Kılavuzu
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705697"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="8a776-102">Dizileri bağımsız değişken olarak geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8a776-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="8a776-103">Diziler yöntem parametrelerine bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8a776-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="8a776-104">Diziler başvuru türleri olduğundan, yöntem öğelerin değerini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="8a776-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="8a776-105">Tek boyutlu dizileri bağımsız değişken olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="8a776-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="8a776-106">Başharfe bıyılan tek boyutlu bir diziyi bir yönteme geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a776-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="8a776-107">Örneğin, aşağıdaki deyim bir diziyi yazdırma yöntemine gönderir.</span><span class="sxs-lookup"><span data-stu-id="8a776-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="8a776-108">Aşağıdaki kod yazdırma yönteminin kısmi bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a776-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="8a776-109">Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek adımda başolarak açabilir ve geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a776-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="8a776-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a776-110">Example</span></span>

<span data-ttu-id="8a776-111">Aşağıdaki örnekte, dizeleri bir dizi baş harfe ve `DisplayArray` dizeleri için bir yöntemiçin bir bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8a776-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="8a776-112">Yöntem, dizinin öğelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8a776-112">The method displays the elements of the array.</span></span> <span data-ttu-id="8a776-113">Daha sonra, `ChangeArray` yöntem dizi öğelerini tersine `ChangeArrayElements` çevirir ve ardından yöntem dizinin ilk üç öğesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8a776-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="8a776-114">Her yöntem döndükten `DisplayArray` sonra, yöntem bir diziyi değere aktarmanın dizi öğelerinde değişiklikleri engellemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a776-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="8a776-115">Çok boyutlu dizileri bağımsız değişken olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="8a776-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="8a776-116">Başharfli çok boyutlu bir diziyi, tek boyutlu bir diziyi geçtiğin gibi bir yönteme geçirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a776-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="8a776-117">Aşağıdaki kod, iki boyutlu bir diziyi bağımsız değişken olarak kabul eden bir yazdırma yönteminin kısmi bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a776-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="8a776-118">Aşağıdaki örnekte gösterildiği gibi, yeni bir diziyi tek adımda başolarak açabilir ve geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8a776-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="8a776-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a776-119">Example</span></span>

<span data-ttu-id="8a776-120">Aşağıdaki örnekte, iki boyutlu bir tamsayı dizisi baş harfe `Print2DArray` getirilmiş ve yönteme geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8a776-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="8a776-121">Yöntem, dizinin öğelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8a776-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="8a776-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a776-122">See also</span></span>

- [<span data-ttu-id="8a776-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8a776-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8a776-124">Diziler</span><span class="sxs-lookup"><span data-stu-id="8a776-124">Arrays</span></span>](index.md)
- [<span data-ttu-id="8a776-125">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="8a776-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="8a776-126">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="8a776-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="8a776-127">Basit Diziler</span><span class="sxs-lookup"><span data-stu-id="8a776-127">Jagged Arrays</span></span>](jagged-arrays.md)
