---
title: << işleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 0271c97bc624a8946b90508e9ce39d217a128c05
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261756"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="816f2-102">\<\< İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="816f2-102">\<\< operator (C# Reference)</span></span>

<span data-ttu-id="816f2-103">Sola kaydırma işleci (`<<`) ilk işlenenin sol tarafından ikinci işlenen tarafından belirtilen bit sayısı kadar kaydırır.</span><span class="sxs-lookup"><span data-stu-id="816f2-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="816f2-104">İkinci işlenenin türünde olmalıdır bir [int](../keywords/int.md) veya önceden tanımlanmış bir örtük sayısal dönüştürme için olan bir türü `int`.</span><span class="sxs-lookup"><span data-stu-id="816f2-104">The type of the second operand must be an [int](../keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>

## <a name="remarks"></a><span data-ttu-id="816f2-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="816f2-105">Remarks</span></span>

<span data-ttu-id="816f2-106">Birinci işlenenin ise bir [int](../keywords/int.md) veya [uint](../keywords/uint.md) (32-bit miktarı), kaydırma sayısı tarafından düşük sıra beş bitleri ikinci işlenenin verilir.</span><span class="sxs-lookup"><span data-stu-id="816f2-106">If the first operand is an [int](../keywords/int.md) or [uint](../keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="816f2-107">Diğer bir deyişle, gerçek kaydırma sayısı 0-31 bittir.</span><span class="sxs-lookup"><span data-stu-id="816f2-107">That is, the actual shift count is 0 to 31 bits.</span></span>

<span data-ttu-id="816f2-108">Birinci işlenenin ise bir [uzun](../keywords/long.md) veya [ulong](../keywords/ulong.md) (64-bit miktarı), kaydırma sayısı tarafından düşük sıra altı bitleri ikinci işlenenin verilir.</span><span class="sxs-lookup"><span data-stu-id="816f2-108">If the first operand is a [long](../keywords/long.md) or [ulong](../keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="816f2-109">Diğer bir deyişle, gerçek kaydırma sayısı 0 ila 63 bittir.</span><span class="sxs-lookup"><span data-stu-id="816f2-109">That is, the actual shift count is 0 to 63 bits.</span></span>

<span data-ttu-id="816f2-110">Shift sonra birinci işlenenin türü aralık içinde değil olan herhangi bir yüksek sıra bitleri atılır ve düşük düzey boş bitler sıfır dolguludur.</span><span class="sxs-lookup"><span data-stu-id="816f2-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="816f2-111">Kaydırma işleçlerini, hiçbir zaman taşıyor neden.</span><span class="sxs-lookup"><span data-stu-id="816f2-111">Shift operations never cause overflows.</span></span>

<span data-ttu-id="816f2-112">Kullanıcı tanımlı türler aşırı yükleme `<<` işleci (bkz [işleci](../keywords/operator.md)); birinci işlenenin türü kullanıcı tanımlı bir tür olmalı ve ikinci işlenenin türünde olmalıdır `int`.</span><span class="sxs-lookup"><span data-stu-id="816f2-112">User-defined types can overload the `<<` operator (see [operator](../keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="816f2-113">İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="816f2-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="816f2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="816f2-114">Example</span></span>

[!code-csharp[csRefOperators#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#14)]

## <a name="comments"></a><span data-ttu-id="816f2-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="816f2-115">Comments</span></span>

<span data-ttu-id="816f2-116">Unutmayın `i<<1` ve `i<<33` aynı düşük sıra beş bitleri 1 ve 33 olduğundan aynı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="816f2-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>

## <a name="see-also"></a><span data-ttu-id="816f2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="816f2-117">See also</span></span>

- [<span data-ttu-id="816f2-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="816f2-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="816f2-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="816f2-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="816f2-120">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="816f2-120">C# Operators</span></span>](index.md)
