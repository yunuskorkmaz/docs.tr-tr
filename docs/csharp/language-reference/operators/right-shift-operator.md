---
title: '&gt;&gt; İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 7a2992befcacfdc1d9bb968b611051e15702cca8
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924830"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="8b908-102">&gt;&gt; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8b908-102">&gt;&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="8b908-103">Sağa kaydırma işleci (`>>`) ilk işlenenin, ikinci işlenen tarafından belirtilen bit sayısının sağa kaydırır.</span><span class="sxs-lookup"><span data-stu-id="8b908-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b908-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b908-104">Remarks</span></span>  
 <span data-ttu-id="8b908-105">Birinci işlenenin ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit miktarı), kaydırma sayısı tarafından düşük sıra beş bitleri ikinci işlenenin verilmiştir (ikinci işlenen & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="8b908-105">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>  
  
 <span data-ttu-id="8b908-106">Birinci işlenenin ise bir [uzun](../../../csharp/language-reference/keywords/long.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit miktarı), kaydırma sayısı tarafından düşük sıra altı bitleri ikinci işlenenin verilmiştir (ikinci işlenen & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="8b908-106">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>  
  
 <span data-ttu-id="8b908-107">Birinci işlenenin ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uzun](../../../csharp/language-reference/keywords/long.md), sağa kaydırma aritmetik bir kaydırmadır (imza biti için yüksek düzeyli boş bit ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="8b908-107">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [long](../../../csharp/language-reference/keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="8b908-108">Birinci işlenenin türü ise [uint](../../../csharp/language-reference/keywords/uint.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md), sağa kaydırma mantıksal bir kaydırmadır (yüksek düzeyli bitler sıfır dolgulu).</span><span class="sxs-lookup"><span data-stu-id="8b908-108">If the first operand is of type [uint](../../../csharp/language-reference/keywords/uint.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>  
  
 <span data-ttu-id="8b908-109">Kullanıcı tanımlı türler aşırı yükleme `>>` işleci; birinci işlenenin türü kullanıcı tanımlı bir tür olmalı ve ikinci işlenenin türünde olmalıdır [int](../../../csharp/language-reference/keywords/int.md). Daha fazla bilgi için [işleci](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="8b908-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../../../csharp/language-reference/keywords/int.md). For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="8b908-110">İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="8b908-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b908-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b908-111">Example</span></span>  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8b908-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b908-112">See Also</span></span>

- [<span data-ttu-id="8b908-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8b908-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8b908-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8b908-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8b908-115">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8b908-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
