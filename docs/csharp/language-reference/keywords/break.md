---
title: kesme deyimi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713761"
---
# <a name="break-c-reference"></a><span data-ttu-id="4bdaa-102">break (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4bdaa-102">break (C# Reference)</span></span>

<span data-ttu-id="4bdaa-103">İfade, `break` göründüğü en yakın çevreleyen döngü veya [anahtar](./switch.md) deyimini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="4bdaa-104">Denetim, varsa sonlandırılan deyimi izleyen bildirime aktarılır.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="4bdaa-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bdaa-105">Example</span></span>

<span data-ttu-id="4bdaa-106">Bu örnekte, koşullu deyim 1 ile 100 arasında sayması gereken bir sayaç içerir; ancak, `break` deyim 4 sayar sonra döngü sona erer.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="4bdaa-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bdaa-107">Example</span></span>

<span data-ttu-id="4bdaa-108">Bu örnek, bir `break` [anahtar](./switch.md) deyiminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="4bdaa-109">Girdiyseniz, `4`çıktı:</span><span class="sxs-lookup"><span data-stu-id="4bdaa-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="4bdaa-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bdaa-110">Example</span></span>

<span data-ttu-id="4bdaa-111">Bu örnekte, `break` deyim iç içe bir döngüden çıkmak ve denetimi dış döngüye döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="4bdaa-112">Denetim iç içe döngülerde _yalnızca_ bir seviye yukarı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="4bdaa-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bdaa-113">Example</span></span>

<span data-ttu-id="4bdaa-114">Bu örnekte, `break` deyim yalnızca döngüher yineleme sırasında geçerli dalı kırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="4bdaa-115">Döngünün kendisi iç içe anahtar `break` deyimine ait [switch](./switch.md) olan örneklerden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="4bdaa-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4bdaa-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4bdaa-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bdaa-117">See also</span></span>

- [<span data-ttu-id="4bdaa-118">C# Referans</span><span class="sxs-lookup"><span data-stu-id="4bdaa-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4bdaa-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4bdaa-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4bdaa-120">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="4bdaa-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4bdaa-121">Anahtarı</span><span class="sxs-lookup"><span data-stu-id="4bdaa-121">switch</span></span>](./switch.md)
