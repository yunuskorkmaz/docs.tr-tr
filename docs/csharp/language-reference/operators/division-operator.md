---
title: "/ İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6076e-102">/ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6076e-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="6076e-103">Bölme işleci (`/`), ilk işlenen ikinci işlenen tarafından böler.</span><span class="sxs-lookup"><span data-stu-id="6076e-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="6076e-104">Tüm sayısal türler bölme işleçlerini önceden.</span><span class="sxs-lookup"><span data-stu-id="6076e-104">All numeric types have predefined division operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6076e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6076e-105">Remarks</span></span>  
 <span data-ttu-id="6076e-106">Kullanıcı tanımlı türler aşırı yükleme `/` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6076e-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="6076e-107">Bir aşırı yüklemesini `/` işleci örtük olarak overloads [/ = işleci](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6076e-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="6076e-108">İki tamsayının böldüğünüzde sonucu her zaman bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="6076e-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="6076e-109">Örneğin, 7 sonucunu / 3: 2.</span><span class="sxs-lookup"><span data-stu-id="6076e-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="6076e-110">7 kalanı belirlemek için / 3, kullanımı kalan işleci ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6076e-110">To determine the remainder of 7 / 3, use the remainder operator ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span></span> <span data-ttu-id="6076e-111">Bir sayının bir rasyonel sayı veya kesir olarak edinmek için bölünen veya bölen türü vermek `float` veya türü `double`.</span><span class="sxs-lookup"><span data-stu-id="6076e-111">To obtain a quotient as a rational number or fraction, give the dividend or divisor type `float` or type `double`.</span></span> <span data-ttu-id="6076e-112">Aşağıdaki örnekte gösterildiği gibi Ondalık ayırıcının sağ tarafındaki bir basamak koyarak bölünen veya bölen bir ondalık olarak express durumunda türü örtük olarak atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6076e-112">You can assign the type implicitly if you express the dividend or divisor as a decimal by putting a digit to the right side of the decimal point, as the following example shows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6076e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6076e-113">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6076e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6076e-114">See Also</span></span>  
 [<span data-ttu-id="6076e-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6076e-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6076e-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6076e-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6076e-117">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="6076e-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
