---
description: goto ekstresi-C# başvurusu
title: goto ekstresi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: de95e477bd7e76f549130643c8d4b70a0e2f015c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128432"
---
# <a name="goto-c-reference"></a><span data-ttu-id="89ffb-103">goto (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="89ffb-103">goto (C# Reference)</span></span>

<span data-ttu-id="89ffb-104">`goto`İfade program denetimini doğrudan etiketli bir ifadeye aktarır.</span><span class="sxs-lookup"><span data-stu-id="89ffb-104">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="89ffb-105">Öğesinin yaygın kullanımı `goto` , denetimin belirli bir anahtar-durum etiketine veya bir deyimdeki varsayılan etikete aktarılmalıdır `switch` .</span><span class="sxs-lookup"><span data-stu-id="89ffb-105">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="89ffb-106">`goto`Deyimden daha fazla iç içe geçmiş döngüler almak için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="89ffb-106">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="89ffb-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="89ffb-107">Example</span></span>

<span data-ttu-id="89ffb-108">Aşağıdaki örnek, `goto` bir [Switch](switch.md) deyimindeki kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89ffb-108">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="89ffb-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="89ffb-109">Example</span></span>

<span data-ttu-id="89ffb-110">Aşağıdaki örnek, `goto` iç içe döngülerden ayırmak için kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89ffb-110">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="89ffb-111">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="89ffb-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="89ffb-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89ffb-112">See also</span></span>

- [<span data-ttu-id="89ffb-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="89ffb-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="89ffb-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="89ffb-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="89ffb-115">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="89ffb-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="89ffb-116">goto Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="89ffb-116">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
