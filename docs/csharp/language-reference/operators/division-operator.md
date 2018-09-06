---
title: / İşleci (C# Başvurusu)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: bddf6d234f3536ad64f0cd876cc7ade4494916d9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800761"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9ac71-102">/ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9ac71-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="9ac71-103">Bölme işleci (`/`) ilk işlenenin ikinci işleneni olarak böler.</span><span class="sxs-lookup"><span data-stu-id="9ac71-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="9ac71-104">Tüm sayısal türlerin bölme işleçlerini önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="9ac71-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="9ac71-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ac71-105">Remarks</span></span>  
 <span data-ttu-id="9ac71-106">Kullanıcı tanımlı türler aşırı yükleme `/` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="9ac71-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="9ac71-107">Bir aşırı yüklemesini `/` işleci örtük aşırı [/ = işleci](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="9ac71-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="9ac71-108">İki tamsayının ayırdığınızda, sonucu her zaman bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="9ac71-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="9ac71-109">Örneğin, 7 sonucunu / 3, 2.</span><span class="sxs-lookup"><span data-stu-id="9ac71-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="9ac71-110">Floored bölme olarak karıştırılmamalıdır budur `/` işleci, sıfıra doğru yuvarlar: -7 / 3 -2.</span><span class="sxs-lookup"><span data-stu-id="9ac71-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="9ac71-111">Bir sayının rasyonel sayı olarak almak için kullanın `float`, `double`, veya `decimal` türleri.</span><span class="sxs-lookup"><span data-stu-id="9ac71-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="9ac71-112">Arasında dönüştürmek için birçok yolu vardır [yerleşik sayısal türleri](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span><span class="sxs-lookup"><span data-stu-id="9ac71-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="9ac71-113">Kalan belirlemek için [kalan işleci](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span><span class="sxs-lookup"><span data-stu-id="9ac71-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ac71-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ac71-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9ac71-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ac71-115">See Also</span></span>

- [<span data-ttu-id="9ac71-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9ac71-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9ac71-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9ac71-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9ac71-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9ac71-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
