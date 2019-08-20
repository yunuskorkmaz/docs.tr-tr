---
title: Çok boyutlu diziler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: 63b8729a14e4c309e85a588c5cddc692fb6a6fad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597414"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="efbc9-102">Çok Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="efbc9-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="efbc9-103">Diziler birden fazla boyuta sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="efbc9-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="efbc9-104">Örneğin, aşağıdaki bildirim dört satırlık ve iki sütundan oluşan iki boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="efbc9-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="efbc9-105">Aşağıdaki bildirim üç boyutlu bir dizi oluşturur, 4, 2 ve 3.</span><span class="sxs-lookup"><span data-stu-id="efbc9-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="efbc9-106">Dizi başlatma</span><span class="sxs-lookup"><span data-stu-id="efbc9-106">Array Initialization</span></span>

 <span data-ttu-id="efbc9-107">Aşağıdaki örnekte gösterildiği gibi, bildirimi üzerinde diziyi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efbc9-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="efbc9-108">Ayrıca, sırası belirtmeden diziyi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efbc9-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="efbc9-109">Başlatma olmadan bir dizi değişkeni tanımlamayı seçerseniz, değişkenine bir dizi atamak için `new` işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="efbc9-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="efbc9-110">Öğesinin `new` kullanımı aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="efbc9-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="efbc9-111">Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="efbc9-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="efbc9-112">Benzer şekilde, aşağıdaki örnek, belirli bir dizi öğesinin değerini alır ve bunu değişkenine `elementValue`atar.</span><span class="sxs-lookup"><span data-stu-id="efbc9-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="efbc9-113">Aşağıdaki kod örneği, dizi öğelerini varsayılan değerlere (pürüzlü Diziler hariç) başlatır.</span><span class="sxs-lookup"><span data-stu-id="efbc9-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="efbc9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efbc9-114">See also</span></span>

- [<span data-ttu-id="efbc9-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="efbc9-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="efbc9-116">Diziler</span><span class="sxs-lookup"><span data-stu-id="efbc9-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="efbc9-117">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="efbc9-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="efbc9-118">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="efbc9-118">Jagged Arrays</span></span>](./jagged-arrays.md)
