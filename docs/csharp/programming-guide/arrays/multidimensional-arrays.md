---
title: Çok boyutlu diziler-C# Programlama Kılavuzu
description: C# içindeki diziler birden fazla boyuta sahip olabilir. Bu örnek bildirim dört satırlık ve iki sütundan oluşan iki boyutlu bir dizi oluşturur.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a2f204c0866672b317569fbc620aa8af60829ffd
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475014"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="3d666-104">Çok Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3d666-104">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="3d666-105">Diziler birden fazla boyuta sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d666-105">Arrays can have more than one dimension.</span></span> <span data-ttu-id="3d666-106">Örneğin, aşağıdaki bildirim dört satırlık ve iki sütundan oluşan iki boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d666-106">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="3d666-107">Aşağıdaki bildirim üç boyutlu bir dizi oluşturur, 4, 2 ve 3.</span><span class="sxs-lookup"><span data-stu-id="3d666-107">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="3d666-108">Dizi başlatma</span><span class="sxs-lookup"><span data-stu-id="3d666-108">Array Initialization</span></span>

 <span data-ttu-id="3d666-109">Aşağıdaki örnekte gösterildiği gibi, bildirimi üzerinde diziyi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d666-109">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="3d666-110">Ayrıca, sırası belirtmeden diziyi de başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d666-110">You can also initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="3d666-111">Başlatma olmadan bir dizi değişkeni tanımlamayı seçerseniz, `new` değişkenine bir dizi atamak için işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d666-111">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="3d666-112">Öğesinin kullanımı `new` Aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d666-112">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="3d666-113">Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="3d666-113">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="3d666-114">Benzer şekilde, aşağıdaki örnek, belirli bir dizi öğesinin değerini alır ve bunu değişkenine atar `elementValue` .</span><span class="sxs-lookup"><span data-stu-id="3d666-114">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="3d666-115">Aşağıdaki kod örneği, dizi öğelerini varsayılan değerlere (pürüzlü Diziler hariç) başlatır.</span><span class="sxs-lookup"><span data-stu-id="3d666-115">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="3d666-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d666-116">See also</span></span>

- [<span data-ttu-id="3d666-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3d666-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3d666-118">Diziler</span><span class="sxs-lookup"><span data-stu-id="3d666-118">Arrays</span></span>](./index.md)
- [<span data-ttu-id="3d666-119">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="3d666-119">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="3d666-120">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="3d666-120">Jagged Arrays</span></span>](./jagged-arrays.md)
