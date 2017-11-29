---
title: "&lt;&lt;İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 400dbc799c68bb9e1bc00695954115f2eb6af7c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="03ef9-102">&lt;&lt;İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="03ef9-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="03ef9-103">Sola kaydırma işleci (`<<`) ilk işlenen sola bit sayısı kadar ikinci işlenen tarafından belirtilen kaydırır.</span><span class="sxs-lookup"><span data-stu-id="03ef9-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="03ef9-104">İkinci işlenen türünde olmalıdır bir [int](../../../csharp/language-reference/keywords/int.md) veya önceden tanımlanmış bir örtük sayısal dönüştürme için olan bir türü `int`.</span><span class="sxs-lookup"><span data-stu-id="03ef9-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03ef9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03ef9-105">Remarks</span></span>  
 <span data-ttu-id="03ef9-106">İlk işlenen ise bir [int](../../../csharp/language-reference/keywords/int.md) veya [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitlik bir miktar), üst karakter sayısı tarafından düşük düzey beş BITS ikinci işleneninin verilir.</span><span class="sxs-lookup"><span data-stu-id="03ef9-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="03ef9-107">Diğer bir deyişle, gerçek üst karakter sayısı 0-31 bittir.</span><span class="sxs-lookup"><span data-stu-id="03ef9-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="03ef9-108">İlk işlenen ise bir [uzun](../../../csharp/language-reference/keywords/long.md) veya [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitlik bir miktar), üst karakter sayısı tarafından düşük düzey altı BITS ikinci işleneninin verilir.</span><span class="sxs-lookup"><span data-stu-id="03ef9-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="03ef9-109">Diğer bir deyişle, gerçek üst karakter sayısı 0-63 bittir.</span><span class="sxs-lookup"><span data-stu-id="03ef9-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="03ef9-110">Olan herhangi bir yüksek düzey BITS shift sonra ilk işlenen türü aralık içinde değil atılır ve düşük düzey boş BITS sıfırla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="03ef9-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="03ef9-111">Shift işlemleri hiçbir zaman taşan neden olur.</span><span class="sxs-lookup"><span data-stu-id="03ef9-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="03ef9-112">Kullanıcı tanımlı türler aşırı yükleme `<<` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)); ilk işlenen türü kullanıcı tanımlı tür olmalıdır ve ikinci işlenen türünde olmalıdır `int`.</span><span class="sxs-lookup"><span data-stu-id="03ef9-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="03ef9-113">İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="03ef9-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03ef9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="03ef9-114">Example</span></span>  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="03ef9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03ef9-115">Comments</span></span>  
 <span data-ttu-id="03ef9-116">Unutmayın `i<<1` ve `i<<33` 1 ve 33 aynı düşük düzey beş BITS olduğu için aynı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="03ef9-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ef9-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03ef9-117">See Also</span></span>  
 [<span data-ttu-id="03ef9-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="03ef9-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="03ef9-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="03ef9-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="03ef9-120">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="03ef9-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
