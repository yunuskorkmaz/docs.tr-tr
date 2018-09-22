---
title: BREAK deyimi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 9dc71cce3cc0ca4035df483d2b3a3ab9a3bab9c5
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46695834"
---
# <a name="break-c-reference"></a><span data-ttu-id="95a25-102">break (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="95a25-102">break (C# Reference)</span></span>

<span data-ttu-id="95a25-103">`break` Deyimi en yakın kapsayan döngüyü sonlandırır veya [geçiş](../../../csharp/language-reference/keywords/switch.md) göründüğü deyimi.</span><span class="sxs-lookup"><span data-stu-id="95a25-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="95a25-104">Denetim, varsa, sonlandırılmış deyimi takip eden deyime geçirilir.</span><span class="sxs-lookup"><span data-stu-id="95a25-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="95a25-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="95a25-105">Example</span></span>

<span data-ttu-id="95a25-106">Bu örnekte, 100'e 1 ila count için beklenen sayaç koşullu deyim içerir. Ancak, `break` deyimi sonra 4 sayıları döngüyü sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="95a25-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="95a25-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="95a25-107">Example</span></span>

<span data-ttu-id="95a25-108">Bu örnekte, `break` deyimi bir iç iç içe geçmiş döngüden ve denetim için dış döngü döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95a25-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="95a25-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="95a25-109">Example</span></span>

<span data-ttu-id="95a25-110">Bu örnek kullanımını gösterir `break` içinde bir [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="95a25-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="95a25-111">Girerseniz `4`, çıktı aşağıdaki gibi olur:</span><span class="sxs-lookup"><span data-stu-id="95a25-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="95a25-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="95a25-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="95a25-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95a25-113">See Also</span></span>

- [<span data-ttu-id="95a25-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="95a25-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="95a25-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="95a25-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="95a25-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="95a25-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="95a25-117">switch</span><span class="sxs-lookup"><span data-stu-id="95a25-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
- [<span data-ttu-id="95a25-118">Atlama Deyimleri</span><span class="sxs-lookup"><span data-stu-id="95a25-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
- [<span data-ttu-id="95a25-119">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="95a25-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
