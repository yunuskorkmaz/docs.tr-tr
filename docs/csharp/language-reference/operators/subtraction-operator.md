---
title: '- Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 920981addd5c779c9ad1c666ef45e1de5cd23408
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633012"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="e0c2b-102">-işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-102">- operator (C# Reference)</span></span>

<span data-ttu-id="e0c2b-103">`-` İşleci bir birli veya ikili işleç olarak işlev görebilir.</span><span class="sxs-lookup"><span data-stu-id="e0c2b-103">The `-` operator can function as either a unary or a binary operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0c2b-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0c2b-104">Remarks</span></span>

<span data-ttu-id="e0c2b-105">Birli `-` işleçleri tüm sayısal türler için önceden tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e0c2b-105">Unary `-` operators are predefined for all numeric types.</span></span> <span data-ttu-id="e0c2b-106">Bir tekli sonucunu `-` işlemdir üzerinde bir sayısal tür işleneni sayısal negation.</span><span class="sxs-lookup"><span data-stu-id="e0c2b-106">The result of a unary `-` operation on a numeric type is the numeric negation of the operand.</span></span>

<span data-ttu-id="e0c2b-107">İkili `-` işleçleri ikinci işlenen ilk çıkarılacak tüm sayısal ve sabit listesi türleri için önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="e0c2b-107">Binary `-` operators are predefined for all numeric and enumeration types to subtract the second operand from the first.</span></span>

<span data-ttu-id="e0c2b-108">Temsilci türleri de sağlayan bir ikili `-` işleci, temsilci kaldırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e0c2b-108">Delegate types also provide a binary `-` operator, which performs delegate removal.</span></span>

<span data-ttu-id="e0c2b-109">Kullanıcı tanımlı türler aşırı yükleme birli `-` ve ikili `-` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="e0c2b-109">User-defined types can overload the unary `-` and binary `-` operators.</span></span> <span data-ttu-id="e0c2b-110">Daha fazla bilgi için [işleç anahtar sözcüğü](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="e0c2b-110">For more information, see [operator keyword](../keywords/operator.md).</span></span>

## <a name="example"></a><span data-ttu-id="e0c2b-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0c2b-111">Example</span></span>

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a><span data-ttu-id="e0c2b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0c2b-112">See also</span></span>

- [<span data-ttu-id="e0c2b-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e0c2b-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0c2b-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e0c2b-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e0c2b-115">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="e0c2b-115">C# operators</span></span>](index.md)
