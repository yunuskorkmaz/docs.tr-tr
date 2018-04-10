---
title: '&gt;&gt;İşleci (C# Başvurusu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7c2eddf06d7b8417c9fcb0fed395b2bf51e07144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="41af2-102">&gt;&gt;İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="41af2-102">&gt;&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="41af2-103">Sağa kaydırma işleci (`>>`) ilk işlenen kendi ikinci işlenen tarafından belirtilen BITS sayısına göre sağa kaydırır.</span><span class="sxs-lookup"><span data-stu-id="41af2-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41af2-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41af2-104">Remarks</span></span>  
 <span data-ttu-id="41af2-105">İlk işlenen ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitlik bir miktar), üst karakter sayısı tarafından düşük düzey beş BITS ikinci işleneninin verilmiştir (ikinci işleneni & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="41af2-105">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>  
  
 <span data-ttu-id="41af2-106">İlk işlenen ise bir [uzun](../../../csharp/language-reference/keywords/long.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitlik bir miktar), üst karakter sayısı tarafından düşük düzey altı BITS ikinci işleneninin verilmiştir (ikinci işleneni & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="41af2-106">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>  
  
 <span data-ttu-id="41af2-107">İlk işlenen ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uzun](../../../csharp/language-reference/keywords/long.md), aritmetik kaydırma sağa kaydırma olduğu (yüksek düzey boş BITS oturum bit ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="41af2-107">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [long](../../../csharp/language-reference/keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="41af2-108">İlk işlenen türü ise [uint](../../../csharp/language-reference/keywords/uint.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md), sağa kaydırma olduğundan mantıksal shift (yüksek düzey BITS sıfır doldurulmuş).</span><span class="sxs-lookup"><span data-stu-id="41af2-108">If the first operand is of type [uint](../../../csharp/language-reference/keywords/uint.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>  
  
 <span data-ttu-id="41af2-109">Kullanıcı tanımlı türler aşırı yükleme `>>` işleci; ilk işlenen türü kullanıcı tanımlı tür olmalıdır ve ikinci işlenen türünde olmalıdır [int](../../../csharp/language-reference/keywords/int.md). Daha fazla bilgi için bkz: [işleci](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="41af2-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../../../csharp/language-reference/keywords/int.md). For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="41af2-110">İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="41af2-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41af2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="41af2-111">Example</span></span>  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="41af2-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41af2-112">See Also</span></span>  
 [<span data-ttu-id="41af2-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="41af2-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="41af2-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="41af2-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="41af2-115">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="41af2-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
