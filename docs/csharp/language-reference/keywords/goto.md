---
title: goto deyimi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: d4fd9f1f26b82b409d704c45e4bcf18cceef8282
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507529"
---
# <a name="goto-c-reference"></a><span data-ttu-id="df8e5-102">goto (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="df8e5-102">goto (C# Reference)</span></span>

<span data-ttu-id="df8e5-103">`goto` Deyimi programın denetimini doğrudan etiketli bir deyime aktarır.</span><span class="sxs-lookup"><span data-stu-id="df8e5-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="df8e5-104">Yaygın `goto` belirli bir anahtar durumu etiket ya da varsayılan etiket, denetimin aktarmaktır bir `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="df8e5-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="df8e5-105">`goto` Deyimi, ayrıca iç içe döngüleri dışında almak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="df8e5-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="df8e5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="df8e5-106">Example</span></span>

<span data-ttu-id="df8e5-107">Aşağıdaki örneği kullanarak göstermektedir `goto` içinde bir [geçiş](switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="df8e5-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="df8e5-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="df8e5-108">Example</span></span>

<span data-ttu-id="df8e5-109">Aşağıdaki örneği kullanarak göstermektedir `goto` iç içe döngüleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="df8e5-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="df8e5-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="df8e5-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="df8e5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df8e5-111">See also</span></span>

- [<span data-ttu-id="df8e5-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="df8e5-112">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="df8e5-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="df8e5-113">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="df8e5-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="df8e5-114">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="df8e5-115">goto Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="df8e5-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)  
- [<span data-ttu-id="df8e5-116">Atlama Deyimleri</span><span class="sxs-lookup"><span data-stu-id="df8e5-116">Jump Statements</span></span>](jump-statements.md)  
