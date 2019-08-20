---
title: Break ekstresi- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 77d18d12cd0fabb26906a5b58dc3939da6214a29
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602251"
---
# <a name="break-c-reference"></a><span data-ttu-id="aa116-102">break (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="aa116-102">break (C# Reference)</span></span>

<span data-ttu-id="aa116-103">İfadesi göründüğü en yakın kapsayan döngüyü veya switch ifadesini sonlandırır. [](./switch.md) `break`</span><span class="sxs-lookup"><span data-stu-id="aa116-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="aa116-104">Denetim, varsa, sonlandırılmış deyimden sonraki ifadeye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="aa116-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="aa116-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa116-105">Example</span></span>

<span data-ttu-id="aa116-106">Bu örnekte, koşullu ifade 1 ile 100 arasında bir sayı olması beklenen bir sayaç içerir; Ancak, `break` ifade 4 saydıktan sonra döngüyü sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="aa116-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="aa116-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa116-107">Example</span></span>

<span data-ttu-id="aa116-108">Bu örnekte, `break` iç içe geçmiş bir döngüyü bölmek ve denetimi dış döngüye döndürmek için ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa116-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="aa116-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa116-109">Example</span></span>

<span data-ttu-id="aa116-110">Bu örnek, bir [Switch](./switch.md) deyimindeki `break` öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa116-110">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="aa116-111">Girdiğinizde `4`, çıkış şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="aa116-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="aa116-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="aa116-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="aa116-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa116-113">See also</span></span>

- [<span data-ttu-id="aa116-114">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="aa116-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aa116-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aa116-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aa116-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="aa116-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="aa116-117">switch</span><span class="sxs-lookup"><span data-stu-id="aa116-117">switch</span></span>](./switch.md)
