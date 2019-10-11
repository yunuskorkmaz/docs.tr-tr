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
ms.openlocfilehash: 2628da73364cf94a52e2862d349243c100d4afaf
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179929"
---
# <a name="break-c-reference"></a><span data-ttu-id="62a80-102">Break (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="62a80-102">break (C# Reference)</span></span>

<span data-ttu-id="62a80-103">@No__t-0 ifadesi, göründüğü en yakın kapsayan döngüyü veya [Switch](./switch.md) ifadesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="62a80-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="62a80-104">Denetim, varsa, sonlandırılmış deyimden sonraki ifadeye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="62a80-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="62a80-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="62a80-105">Example</span></span>

<span data-ttu-id="62a80-106">Bu örnekte, koşullu ifade 1 ile 100 arasında bir sayı olması beklenen bir sayaç içerir; Ancak `break` ifadesinde, döngü 4 saydıktan sonra sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="62a80-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="62a80-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="62a80-107">Example</span></span>

<span data-ttu-id="62a80-108">Bu örnek, [Switch](./switch.md) ifadesinde `break` ' ın kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="62a80-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="62a80-109">@No__t-0 girdiyseniz, çıkış şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="62a80-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="62a80-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="62a80-110">Example</span></span>

<span data-ttu-id="62a80-111">Bu örnekte, `break`, iç içe geçmiş bir döngüyü bölmek için kullanılır ve denetimin dıştaki döngüye dönmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="62a80-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="62a80-112">Denetim, iç içe Döngülerde _yalnızca_ bir düzey yukarı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="62a80-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="62a80-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="62a80-113">Example</span></span>

<span data-ttu-id="62a80-114">Bu örnekte, `break` deyimleri yalnızca döngünün her yinelemesi sırasında geçerli dalı bölmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62a80-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="62a80-115">Döngünün kendisi, iç içe geçmiş [anahtar](./switch.md) ifadesine ait olan `break` örneklerinden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="62a80-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="62a80-116">C#dil belirtimi</span><span class="sxs-lookup"><span data-stu-id="62a80-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="62a80-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62a80-117">See also</span></span>

- [<span data-ttu-id="62a80-118">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="62a80-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="62a80-119">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="62a80-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="62a80-120">C#Lerimi</span><span class="sxs-lookup"><span data-stu-id="62a80-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="62a80-121">değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="62a80-121">switch</span></span>](./switch.md)
