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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394859"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="57b5f-102">/ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="57b5f-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="57b5f-103">Bölme işleci (`/`) ilk işlenenin ikinci işleneni olarak böler.</span><span class="sxs-lookup"><span data-stu-id="57b5f-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="57b5f-104">Tüm sayısal türlerin bölme işleçlerini önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="57b5f-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="57b5f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57b5f-105">Remarks</span></span>  
 <span data-ttu-id="57b5f-106">Kullanıcı tanımlı türler aşırı yükleme `/` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="57b5f-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="57b5f-107">Bir aşırı yüklemesini `/` işleci örtük aşırı [/ = işleci](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="57b5f-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="57b5f-108">İki tamsayının ayırdığınızda, sonucu her zaman bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="57b5f-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="57b5f-109">Örneğin, 7 sonucunu / 3, 2.</span><span class="sxs-lookup"><span data-stu-id="57b5f-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="57b5f-110">Floored bölme olarak karıştırılmamalıdır budur `/` işleci, sıfıra doğru yuvarlar: -7 / 3 -2.</span><span class="sxs-lookup"><span data-stu-id="57b5f-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="57b5f-111">Bir sayının rasyonel sayı olarak almak için kullanın `float`, `double`, veya `decimal` türleri.</span><span class="sxs-lookup"><span data-stu-id="57b5f-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="57b5f-112">Arasında dönüştürmek için birçok yolu vardır [yerleşik sayısal türleri](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span><span class="sxs-lookup"><span data-stu-id="57b5f-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="57b5f-113">Kalan belirlemek için [kalan işleci](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span><span class="sxs-lookup"><span data-stu-id="57b5f-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57b5f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="57b5f-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="57b5f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57b5f-115">See Also</span></span>

- [<span data-ttu-id="57b5f-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="57b5f-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="57b5f-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57b5f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="57b5f-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="57b5f-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
