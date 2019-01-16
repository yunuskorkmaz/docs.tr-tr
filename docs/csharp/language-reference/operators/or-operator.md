---
title: '| operator - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 185ea3aabff4794ec08cca541773dbec3574ab4b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333518"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="fcc2d-102">| işleç (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fcc2d-102">| operator (C# Reference)</span></span>

<span data-ttu-id="fcc2d-103">İkili `|` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`.</span><span class="sxs-lookup"><span data-stu-id="fcc2d-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="fcc2d-104">İntegral türleri için `|` kendi işlenenden bit seviyesinde veya hesaplar.</span><span class="sxs-lookup"><span data-stu-id="fcc2d-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="fcc2d-105">İçin `bool` işlenenini `|` işlenenleri; mantıksal OR hesaplar diğer bir deyişle, sonucudur `false` , her iki işlenen ve yalnızca, `false`.</span><span class="sxs-lookup"><span data-stu-id="fcc2d-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcc2d-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcc2d-106">Remarks</span></span>

<span data-ttu-id="fcc2d-107">İkili `|` işleci, birinci bağımsız olarak her iki işlenen değerlendirilir değerini, buna için [koşullu-OR işleci](conditional-or-operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="fcc2d-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](conditional-or-operator.md) `||`.</span></span>

<span data-ttu-id="fcc2d-108">Kullanıcı tanımlı türler aşırı yükleme `|` işleci (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="fcc2d-108">User-defined types can overload the `|` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="fcc2d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcc2d-109">Example</span></span>

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a><span data-ttu-id="fcc2d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcc2d-110">See also</span></span>

- [<span data-ttu-id="fcc2d-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fcc2d-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fcc2d-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fcc2d-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fcc2d-113">C#işleçleri</span><span class="sxs-lookup"><span data-stu-id="fcc2d-113">C# operators</span></span>](index.md)