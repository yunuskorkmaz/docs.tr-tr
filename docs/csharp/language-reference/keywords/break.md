---
title: Break ekstresi- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713761"
---
# <a name="break-c-reference"></a><span data-ttu-id="41e95-102">break (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="41e95-102">break (C# Reference)</span></span>

<span data-ttu-id="41e95-103">`break` ifadesi göründüğü en yakın kapsayan döngüyü veya [Switch](./switch.md) ifadesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="41e95-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="41e95-104">Denetim, varsa, sonlandırılmış deyimden sonraki ifadeye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="41e95-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="41e95-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="41e95-105">Example</span></span>

<span data-ttu-id="41e95-106">Bu örnekte, koşullu ifade 1 ile 100 arasında bir sayı olması beklenen bir sayaç içerir; Ancak, `break` ifade döngüyü 4 saydan sonra sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="41e95-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="41e95-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="41e95-107">Example</span></span>

<span data-ttu-id="41e95-108">Bu örnek, bir [Switch](./switch.md) deyimindeki `break` kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="41e95-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="41e95-109">`4`girdiyseniz, çıkış şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="41e95-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="41e95-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="41e95-110">Example</span></span>

<span data-ttu-id="41e95-111">Bu örnekte `break` deyimleri, iç içe geçmiş bir döngüyü bölmek için kullanılır ve denetimin dıştaki döngüye dönmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="41e95-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="41e95-112">Denetim, iç içe Döngülerde _yalnızca_ bir düzey yukarı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="41e95-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="41e95-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="41e95-113">Example</span></span>

<span data-ttu-id="41e95-114">Bu örnekte, `break` deyimleri yalnızca döngünün her yinelemesi sırasında geçerli dalı bölmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41e95-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="41e95-115">Döngünün kendisi, iç içe geçmiş [anahtar](./switch.md) ifadesine ait `break` örneklerinden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="41e95-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="41e95-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="41e95-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="41e95-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41e95-117">See also</span></span>

- [<span data-ttu-id="41e95-118">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="41e95-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="41e95-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="41e95-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="41e95-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="41e95-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="41e95-121">switch</span><span class="sxs-lookup"><span data-stu-id="41e95-121">switch</span></span>](./switch.md)
