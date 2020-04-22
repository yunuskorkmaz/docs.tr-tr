---
title: Çok Boyutlu Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: ee5fae36ff844fadad7e1b6a766020319b67a83c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021749"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="d4696-102">Çok Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d4696-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="d4696-103">Dizilerin birden fazla boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4696-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="d4696-104">Örneğin, aşağıdaki bildirim dört satır ve iki sütundan oluşan iki boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4696-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="d4696-105">Aşağıdaki bildirim, 4, 2 ve 3 olmak üzere üç boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4696-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="d4696-106">Dizi Başlatma</span><span class="sxs-lookup"><span data-stu-id="d4696-106">Array Initialization</span></span>

 <span data-ttu-id="d4696-107">Aşağıdaki örnekte gösterildiği gibi, diziyi bildirim üzerine başlatma yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4696-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="d4696-108">Sıralamayı belirtmeden diziyi de başharfe alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4696-108">You can also initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="d4696-109">Bir dizi değişkenini başlatma olmadan bildirmeyi seçerseniz, değişkene bir dizi atamak için `new` işleci kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4696-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="d4696-110">Kullanımı `new` aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d4696-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="d4696-111">Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="d4696-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="d4696-112">Benzer şekilde, aşağıdaki örnek belirli bir dizi öğesinin değerini `elementValue`alır ve değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="d4696-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="d4696-113">Aşağıdaki kod örneği, dizi öğelerini varsayılan değerlere (pürüzlü diziler hariç) başlarar.</span><span class="sxs-lookup"><span data-stu-id="d4696-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="d4696-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4696-114">See also</span></span>

- [<span data-ttu-id="d4696-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d4696-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d4696-116">Diziler</span><span class="sxs-lookup"><span data-stu-id="d4696-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="d4696-117">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="d4696-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="d4696-118">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="d4696-118">Jagged Arrays</span></span>](./jagged-arrays.md)
