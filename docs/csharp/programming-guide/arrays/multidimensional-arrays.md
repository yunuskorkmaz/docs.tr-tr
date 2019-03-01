---
title: Çok boyutlu diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: df9063d0616b72ad15c9c48fa4459a6dc98b77c1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972618"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="360f0-102">Çok Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="360f0-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="360f0-103">Diziler, birden fazla boyuta sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="360f0-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="360f0-104">Örneğin, aşağıdaki bildirimi dört satır ve iki sütunlu iki boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="360f0-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="360f0-105">Aşağıdaki bildirim üç bir dizi oluşturur boyutları, 4, 2 ve 3.</span><span class="sxs-lookup"><span data-stu-id="360f0-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="360f0-106">Dizi başlatma</span><span class="sxs-lookup"><span data-stu-id="360f0-106">Array Initialization</span></span>

 <span data-ttu-id="360f0-107">Aşağıdaki örnekte gösterildiği gibi dizi bildirimi üzerine başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="360f0-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="360f0-108">Dizi boyut belirtilmeden de başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="360f0-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="360f0-109">Bir dizi değişkeni başlatma olmadan belirtmek isterseniz, kullanmalısınız `new` dizi değişkenine atamak için işleç.</span><span class="sxs-lookup"><span data-stu-id="360f0-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="360f0-110">Kullanımını `new` aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="360f0-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="360f0-111">Aşağıdaki örnek, belirli bir dizi öğesine bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="360f0-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="360f0-112">Benzer şekilde, aşağıdaki örnekte belirli bir dizi öğenin değerini alır ve değişkenine atar `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="360f0-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="360f0-113">Aşağıdaki kod örneği, dizi öğeleri (hariç basit Diziler) varsayılan değerlerine başlatır.</span><span class="sxs-lookup"><span data-stu-id="360f0-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="360f0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="360f0-114">See also</span></span>

- [<span data-ttu-id="360f0-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="360f0-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="360f0-116">Diziler</span><span class="sxs-lookup"><span data-stu-id="360f0-116">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="360f0-117">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="360f0-117">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="360f0-118">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="360f0-118">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
