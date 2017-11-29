---
title: "Çok Boyutlu Diziler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab3a93c21ddb9541a6149967605b851ea5a50a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="79ede-102">Çok Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="79ede-102">Multidimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="79ede-103">Diziler, birden fazla boyuta sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="79ede-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="79ede-104">Örneğin, aşağıdaki bildirimi dört satır ve iki sütun iki boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="79ede-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 <span data-ttu-id="79ede-105">Üç dizisi şu bildirimi oluşturur boyutları, 4, 2 ve 3.</span><span class="sxs-lookup"><span data-stu-id="79ede-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="79ede-106">Dizi başlatma</span><span class="sxs-lookup"><span data-stu-id="79ede-106">Array Initialization</span></span>  
 <span data-ttu-id="79ede-107">Aşağıdaki örnekte gösterildiği gibi bildirimi bağlı dizi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79ede-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 <span data-ttu-id="79ede-108">Dizi derecesini belirtmeden de başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79ede-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 <span data-ttu-id="79ede-109">Bir dizi değişkeni başlatma olmadan bildirmek isterseniz, kullanmalısınız `new` bir dizi değişkenine atamak için işleci.</span><span class="sxs-lookup"><span data-stu-id="79ede-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="79ede-110">Kullanımını `new` aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="79ede-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 <span data-ttu-id="79ede-111">Aşağıdaki örnek bir değer belirli bir dizi öğesine atar.</span><span class="sxs-lookup"><span data-stu-id="79ede-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 <span data-ttu-id="79ede-112">Benzer şekilde, aşağıdaki örnekte belirli bir dizi öğenin değerini alır ve değişkenine atar `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="79ede-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 <span data-ttu-id="79ede-113">Aşağıdaki kod örneğinde dizi öğeleri (dışında basit Diziler) varsayılan değerlerine başlatır.</span><span class="sxs-lookup"><span data-stu-id="79ede-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="79ede-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79ede-114">See Also</span></span>  
 [<span data-ttu-id="79ede-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="79ede-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="79ede-116">Diziler</span><span class="sxs-lookup"><span data-stu-id="79ede-116">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="79ede-117">Tek boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="79ede-117">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="79ede-118">Basit diziler</span><span class="sxs-lookup"><span data-stu-id="79ede-118">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
