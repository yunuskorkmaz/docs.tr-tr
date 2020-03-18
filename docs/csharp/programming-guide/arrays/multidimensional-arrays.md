---
title: Çok Boyutlu Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: eb49f4386b6106328f1613b5ec70794ac26fc9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715047"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="770e4-102">Çok Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="770e4-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="770e4-103">Dizilerin birden fazla boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="770e4-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="770e4-104">Örneğin, aşağıdaki bildirim dört satır ve iki sütundan oluşan iki boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="770e4-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="770e4-105">Aşağıdaki bildirim, 4, 2 ve 3 olmak üzere üç boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="770e4-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="770e4-106">Dizi Başlatma</span><span class="sxs-lookup"><span data-stu-id="770e4-106">Array Initialization</span></span>

 <span data-ttu-id="770e4-107">Aşağıdaki örnekte gösterildiği gibi, diziyi bildirim üzerine başlatma yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="770e4-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="770e4-108">Ayrıca, sıralamayı belirtmeden diziyi başlatmayapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="770e4-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="770e4-109">Bir dizi değişkenini başlatma olmadan bildirmeyi seçerseniz, değişkene bir dizi atamak için `new` işleci kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="770e4-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="770e4-110">Kullanımı `new` aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="770e4-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="770e4-111">Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="770e4-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="770e4-112">Benzer şekilde, aşağıdaki örnek belirli bir dizi öğesinin değerini `elementValue`alır ve değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="770e4-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="770e4-113">Aşağıdaki kod örneği, dizi öğelerini varsayılan değerlere (pürüzlü diziler hariç) başlarar.</span><span class="sxs-lookup"><span data-stu-id="770e4-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="770e4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="770e4-114">See also</span></span>

- [<span data-ttu-id="770e4-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="770e4-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="770e4-116">Diziler</span><span class="sxs-lookup"><span data-stu-id="770e4-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="770e4-117">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="770e4-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="770e4-118">Basit Diziler</span><span class="sxs-lookup"><span data-stu-id="770e4-118">Jagged Arrays</span></span>](./jagged-arrays.md)
