---
description: Break ekstresi-C# başvurusu
title: Break ekstresi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134750"
---
# <a name="break-c-reference"></a><span data-ttu-id="85bc3-103">break (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="85bc3-103">break (C# Reference)</span></span>

<span data-ttu-id="85bc3-104">`break`İfadesi göründüğü en yakın kapsayan döngüyü veya [Switch](./switch.md) ifadesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="85bc3-104">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="85bc3-105">Denetim, varsa, sonlandırılmış deyimden sonraki ifadeye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="85bc3-105">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="85bc3-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="85bc3-106">Example</span></span>

<span data-ttu-id="85bc3-107">Bu örnekte, koşullu ifade 1 ile 100 arasında bir sayı olması beklenen bir sayaç içerir; Ancak, `break` ifade 4 saydıktan sonra döngüyü sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="85bc3-107">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="85bc3-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="85bc3-108">Example</span></span>

<span data-ttu-id="85bc3-109">Bu örnek, `break` bir [Switch](./switch.md) deyimindeki öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="85bc3-109">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="85bc3-110">Girdiğinizde `4` , çıkış şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="85bc3-110">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="85bc3-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="85bc3-111">Example</span></span>

<span data-ttu-id="85bc3-112">Bu örnekte, `break` iç içe geçmiş bir döngüyü bölmek ve denetimi dış döngüye döndürmek için ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85bc3-112">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="85bc3-113">Denetim, iç içe Döngülerde _yalnızca_ bir düzey yukarı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="85bc3-113">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="85bc3-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="85bc3-114">Example</span></span>

<span data-ttu-id="85bc3-115">Bu örnekte, `break` ifade yalnızca döngünün her yinelemesi sırasında geçerli dalı bölmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85bc3-115">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="85bc3-116">Döngünün kendisi, `break` iç içe geçmiş [anahtar](./switch.md) ifadesine ait örneklerinden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="85bc3-116">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="85bc3-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="85bc3-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="85bc3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85bc3-118">See also</span></span>

- [<span data-ttu-id="85bc3-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="85bc3-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="85bc3-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="85bc3-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="85bc3-121">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="85bc3-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="85bc3-122">değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="85bc3-122">switch</span></span>](./switch.md)
