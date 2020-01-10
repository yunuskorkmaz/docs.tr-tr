---
title: goto bildirisi- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715282"
---
# <a name="goto-c-reference"></a><span data-ttu-id="ee96d-102">goto (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ee96d-102">goto (C# Reference)</span></span>

<span data-ttu-id="ee96d-103">`goto` ifade program denetimini doğrudan etiketli bir ifadeye aktarır.</span><span class="sxs-lookup"><span data-stu-id="ee96d-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="ee96d-104">`goto` ortak kullanımı, denetimin belirli bir anahtar-durum etiketine veya bir `switch` deyimindeki varsayılan etikete aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee96d-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="ee96d-105">`goto` deyimleri, derin iç içe geçmiş döngüler almak için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ee96d-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="ee96d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee96d-106">Example</span></span>

<span data-ttu-id="ee96d-107">Aşağıdaki örnek, bir [Switch](switch.md) deyimindeki `goto` kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee96d-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="ee96d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee96d-108">Example</span></span>

<span data-ttu-id="ee96d-109">Aşağıdaki örnek, iç içe döngülerden kesmek için `goto` kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee96d-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="ee96d-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ee96d-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ee96d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee96d-111">See also</span></span>

- [<span data-ttu-id="ee96d-112">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="ee96d-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ee96d-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ee96d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ee96d-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ee96d-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ee96d-115">goto Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="ee96d-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
