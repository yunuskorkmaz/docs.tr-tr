---
title: goto deyimi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715282"
---
# <a name="goto-c-reference"></a><span data-ttu-id="10a06-102">goto (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="10a06-102">goto (C# Reference)</span></span>

<span data-ttu-id="10a06-103">İfade, `goto` program denetimini doğrudan etiketli bir bildirime aktarMaktadır.</span><span class="sxs-lookup"><span data-stu-id="10a06-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="10a06-104">Denetimin `goto` yaygın kullanımı, denetimi belirli bir anahtar-servis talebi etiketine veya bir `switch` deyimdeki varsayılan etikete aktarmaktır.</span><span class="sxs-lookup"><span data-stu-id="10a06-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="10a06-105">İfade, `goto` derin iç içe giden döngülerden çıkmak için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="10a06-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="10a06-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="10a06-106">Example</span></span>

<span data-ttu-id="10a06-107">Aşağıdaki örnek, bir `goto` [anahtar](switch.md) deyiminde kullanımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="10a06-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="10a06-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="10a06-108">Example</span></span>

<span data-ttu-id="10a06-109">Aşağıdaki örnek, iç `goto` içe giden döngülerden çıkmak için kullanımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="10a06-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="10a06-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="10a06-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="10a06-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10a06-111">See also</span></span>

- [<span data-ttu-id="10a06-112">C# Referans</span><span class="sxs-lookup"><span data-stu-id="10a06-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="10a06-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="10a06-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="10a06-114">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="10a06-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="10a06-115">goto Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="10a06-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
