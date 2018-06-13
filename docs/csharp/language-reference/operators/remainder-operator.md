---
title: '% İşleci (C# Başvurusu)'
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: b906feb22aaec97e58da562b615baae01f3e0719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271083"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0a64a-102">% İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0a64a-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="0a64a-103">Kalan işleci (`%`) ilk işlenen kendi ikinciye bölmenin sonra kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="0a64a-103">The remainder operator (`%`) computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="0a64a-104">Tüm sayısal türler kalan işleçleri önceden.</span><span class="sxs-lookup"><span data-stu-id="0a64a-104">All numeric types have predefined remainder operators.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="0a64a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a64a-105">Remarks</span></span>  
 <span data-ttu-id="0a64a-106">Formül `a % b` her zaman aralığı bir değer döndürür `(-b, b)`, özel (hiçbir zaman dönebilirsiniz `b` veya `-b`), bölünen oturum tutma.</span><span class="sxs-lookup"><span data-stu-id="0a64a-106">The formula `a % b` will always return a value on the range `(-b, b)`, exclusive (it can never return `b` or `-b`), keeping the sign of the dividend.</span></span> <span data-ttu-id="0a64a-107">Tamsayı bölme için kalan işleci kural karşılayan `a % b = a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="0a64a-107">For integer division, the remainder operator satisfies the rule `a % b = a - (a / b) * b`.</span></span>
  
 <span data-ttu-id="0a64a-108">Benzer bir kural karşılayan kurallı mod ile ancak aralıkta floored bölme ve döndürür değerleri karıştırılmamalıdır budur `[0, b)`.</span><span class="sxs-lookup"><span data-stu-id="0a64a-108">This is not to be confused with canonical modulus, which satisfies a similar rule but with floored division and returns values on the range `[0, b)`.</span></span> <span data-ttu-id="0a64a-109">C# kurallı modül için bir işleç yok.</span><span class="sxs-lookup"><span data-stu-id="0a64a-109">C# does not have an operator for canonical modulus.</span></span> <span data-ttu-id="0a64a-110">Ancak, davranışı pozitif yararınıza olur; aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0a64a-110">However, the behavior is the same for positive dividends.</span></span>
  
 <span data-ttu-id="0a64a-111">Kullanıcı tanımlı türler aşırı yükleme `%` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0a64a-111">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="0a64a-112">İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="0a64a-112">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a64a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a64a-113">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="0a64a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a64a-114">Comments</span></span>  
 <span data-ttu-id="0a64a-115">Çift türüyle ilişkili yuvarlama hataları not alın.</span><span class="sxs-lookup"><span data-stu-id="0a64a-115">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a64a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a64a-116">See Also</span></span>  
 [<span data-ttu-id="0a64a-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0a64a-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0a64a-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0a64a-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0a64a-119">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="0a64a-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
