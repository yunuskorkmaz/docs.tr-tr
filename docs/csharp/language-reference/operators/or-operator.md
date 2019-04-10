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
ms.openlocfilehash: 38f8e21dbd07868441e0c4fbb6074f9897905222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312884"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="5f37b-102">| işleç (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5f37b-102">| operator (C# Reference)</span></span>

<span data-ttu-id="5f37b-103">İkili `|` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`.</span><span class="sxs-lookup"><span data-stu-id="5f37b-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="5f37b-104">İntegral türleri için `|` kendi işlenenden bit seviyesinde veya hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5f37b-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="5f37b-105">İçin `bool` işlenenini `|` işlenenleri; mantıksal OR hesaplar diğer bir deyişle, sonucudur `false` , her iki işlenen ve yalnızca, `false`.</span><span class="sxs-lookup"><span data-stu-id="5f37b-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f37b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f37b-106">Remarks</span></span>

<span data-ttu-id="5f37b-107">İkili `|` işleci, birinci bağımsız olarak her iki işlenen değerlendirilir değerini, buna için [koşullu-OR işleci](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.</span><span class="sxs-lookup"><span data-stu-id="5f37b-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.</span></span>

<span data-ttu-id="5f37b-108">Kullanıcı tanımlı türler aşırı yükleme `|` işleci (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="5f37b-108">User-defined types can overload the `|` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="5f37b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f37b-109">Example</span></span>

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a><span data-ttu-id="5f37b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f37b-110">See also</span></span>

- [<span data-ttu-id="5f37b-111">C# Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5f37b-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5f37b-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5f37b-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5f37b-113">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="5f37b-113">C# operators</span></span>](index.md)