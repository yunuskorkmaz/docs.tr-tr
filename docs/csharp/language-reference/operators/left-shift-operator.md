---
title: '&lt;&lt; İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 036acd6159bcf5ca1677ee6383c9db357625cd67
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276818"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="e0334-102">&lt;&lt; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e0334-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="e0334-103">Sola kaydırma işleci (`<<`) ilk işlenenin sol tarafından ikinci işlenen tarafından belirtilen bit sayısı kadar kaydırır.</span><span class="sxs-lookup"><span data-stu-id="e0334-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="e0334-104">İkinci işlenenin türünde olmalıdır bir [int](../../../csharp/language-reference/keywords/int.md) veya önceden tanımlanmış bir örtük sayısal dönüştürme için olan bir türü `int`.</span><span class="sxs-lookup"><span data-stu-id="e0334-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0334-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0334-105">Remarks</span></span>  
 <span data-ttu-id="e0334-106">Birinci işlenenin ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit miktarı), kaydırma sayısı tarafından düşük sıra beş bitleri ikinci işlenenin verilir.</span><span class="sxs-lookup"><span data-stu-id="e0334-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="e0334-107">Diğer bir deyişle, gerçek kaydırma sayısı 0-31 bittir.</span><span class="sxs-lookup"><span data-stu-id="e0334-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="e0334-108">Birinci işlenenin ise bir [uzun](../../../csharp/language-reference/keywords/long.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit miktarı), kaydırma sayısı tarafından düşük sıra altı bitleri ikinci işlenenin verilir.</span><span class="sxs-lookup"><span data-stu-id="e0334-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="e0334-109">Diğer bir deyişle, gerçek kaydırma sayısı 0 ila 63 bittir.</span><span class="sxs-lookup"><span data-stu-id="e0334-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="e0334-110">Shift sonra birinci işlenenin türü aralık içinde değil olan herhangi bir yüksek sıra bitleri atılır ve düşük düzey boş bitler sıfır dolguludur.</span><span class="sxs-lookup"><span data-stu-id="e0334-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="e0334-111">Kaydırma işleçlerini, hiçbir zaman taşıyor neden.</span><span class="sxs-lookup"><span data-stu-id="e0334-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="e0334-112">Kullanıcı tanımlı türler aşırı yükleme `<<` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)); birinci işlenenin türü kullanıcı tanımlı bir tür olmalı ve ikinci işlenenin türünde olmalıdır `int`.</span><span class="sxs-lookup"><span data-stu-id="e0334-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="e0334-113">İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="e0334-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0334-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0334-114">Example</span></span>  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="e0334-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0334-115">Comments</span></span>  
 <span data-ttu-id="e0334-116">Unutmayın `i<<1` ve `i<<33` aynı düşük sıra beş bitleri 1 ve 33 olduğundan aynı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="e0334-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0334-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0334-117">See Also</span></span>

- [<span data-ttu-id="e0334-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e0334-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="e0334-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e0334-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e0334-120">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="e0334-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
