---
title: '>> Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 703d4ee50bb9f49c66df029de9c5a280449d11fa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255321"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7ec48-102">>> işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7ec48-102">>> operator (C# Reference)</span></span>

<span data-ttu-id="7ec48-103">Sağa kaydırma işleci (`>>`) ilk işlenenin, ikinci işlenen tarafından belirtilen bit sayısının sağa kaydırır.</span><span class="sxs-lookup"><span data-stu-id="7ec48-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ec48-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ec48-104">Remarks</span></span>

<span data-ttu-id="7ec48-105">Birinci işlenenin ise bir [int](../keywords/int.md) veya [uint](../keywords/uint.md) (32-bit miktarı), kaydırma sayısı tarafından düşük sıra beş bitleri ikinci işlenenin verilmiştir (ikinci işlenen & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="7ec48-105">If the first operand is an [int](../keywords/int.md) or [uint](../keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>

<span data-ttu-id="7ec48-106">Birinci işlenenin ise bir [uzun](../keywords/long.md) veya [ulong](../keywords/ulong.md) (64-bit miktarı), kaydırma sayısı tarafından düşük sıra altı bitleri ikinci işlenenin verilmiştir (ikinci işlenen & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="7ec48-106">If the first operand is a [long](../keywords/long.md) or [ulong](../keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>

<span data-ttu-id="7ec48-107">Birinci işlenenin ise bir [int](../keywords/int.md) veya [uzun](../keywords/long.md), sağa kaydırma aritmetik bir kaydırmadır (imza biti için yüksek düzeyli boş bit ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="7ec48-107">If the first operand is an [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="7ec48-108">Birinci işlenenin türü ise [uint](../keywords/uint.md) veya [ulong](../keywords/ulong.md), sağa kaydırma mantıksal bir kaydırmadır (yüksek düzeyli bitler sıfır dolgulu).</span><span class="sxs-lookup"><span data-stu-id="7ec48-108">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>

<span data-ttu-id="7ec48-109">Kullanıcı tanımlı türler aşırı yükleme `>>` işleci; birinci işlenenin türü kullanıcı tanımlı bir tür olmalı ve ikinci işlenenin türünde olmalıdır [int](../keywords/int.md). Daha fazla bilgi için [işleci](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="7ec48-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../keywords/int.md). For more information, see [operator](../keywords/operator.md).</span></span> <span data-ttu-id="7ec48-110">İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="7ec48-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="7ec48-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ec48-111">Example</span></span>

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a><span data-ttu-id="7ec48-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ec48-112">See also</span></span>

- [<span data-ttu-id="7ec48-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7ec48-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7ec48-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7ec48-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7ec48-115">C#işleçleri</span><span class="sxs-lookup"><span data-stu-id="7ec48-115">C# operators</span></span>](index.md)