---
title: / İşleci (C# Başvurusu)
ms.date: 04/04/2018
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
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b17d122e3e3f75012e084903b6f8975fb53d46c
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="24518-102">/ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="24518-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="24518-103">Bölme işleci (`/`), ilk işlenen ikinci işlenen tarafından böler.</span><span class="sxs-lookup"><span data-stu-id="24518-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="24518-104">Tüm sayısal türler bölme işleçlerini önceden.</span><span class="sxs-lookup"><span data-stu-id="24518-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="24518-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24518-105">Remarks</span></span>  
 <span data-ttu-id="24518-106">Kullanıcı tanımlı türler aşırı yükleme `/` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="24518-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="24518-107">Bir aşırı yüklemesini `/` işleci örtük olarak overloads [/ = işleci](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="24518-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="24518-108">İki tamsayının böldüğünüzde sonucu her zaman bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="24518-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="24518-109">Örneğin, 7 sonucunu / 3: 2.</span><span class="sxs-lookup"><span data-stu-id="24518-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="24518-110">Floored bölme olarak karıştırılmamalıdır budur `/` sıfıra doğru yuvarlar işleci: -7 / 3 -2.</span><span class="sxs-lookup"><span data-stu-id="24518-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="24518-111">Bir sayının bir rasyonel sayı olarak almak için kullanın `float`, `double`, veya `decimal` türleri.</span><span class="sxs-lookup"><span data-stu-id="24518-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="24518-112">Arasında dönüştürme için birçok yolu vardır [yerleşik sayısal türleri](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span><span class="sxs-lookup"><span data-stu-id="24518-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="24518-113">Kalan belirlemek için [kalan işleci](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span><span class="sxs-lookup"><span data-stu-id="24518-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24518-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="24518-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="24518-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24518-115">See Also</span></span>  
 [<span data-ttu-id="24518-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="24518-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="24518-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="24518-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="24518-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="24518-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
