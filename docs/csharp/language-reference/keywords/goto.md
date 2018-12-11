---
title: goto deyimi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: bfc997631cc147bf5718ec91a57e2995cead052f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236771"
---
# <a name="goto-c-reference"></a><span data-ttu-id="00935-102">goto (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="00935-102">goto (C# Reference)</span></span>

<span data-ttu-id="00935-103">`goto` Deyimi programın denetimini doğrudan etiketli bir deyime aktarır.</span><span class="sxs-lookup"><span data-stu-id="00935-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="00935-104">Yaygın `goto` belirli bir anahtar durumu etiket ya da varsayılan etiket, denetimin aktarmaktır bir `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="00935-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="00935-105">`goto` Deyimi, ayrıca iç içe döngüleri dışında almak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="00935-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="00935-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="00935-106">Example</span></span>

<span data-ttu-id="00935-107">Aşağıdaki örneği kullanarak göstermektedir `goto` içinde bir [geçiş](switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="00935-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="00935-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="00935-108">Example</span></span>

<span data-ttu-id="00935-109">Aşağıdaki örneği kullanarak göstermektedir `goto` iç içe döngüleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="00935-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="00935-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="00935-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="00935-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00935-111">See also</span></span>

- [<span data-ttu-id="00935-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="00935-112">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="00935-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="00935-113">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="00935-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="00935-114">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="00935-115">goto Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="00935-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)  
- [<span data-ttu-id="00935-116">Atlama Deyimleri</span><span class="sxs-lookup"><span data-stu-id="00935-116">Jump Statements</span></span>](jump-statements.md)  
