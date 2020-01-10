---
title: Let yan tümcesi C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 32bb5d2138c0b86bf58d26015aa208f655229129
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715221"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="0afe7-102">let tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0afe7-102">let clause (C# Reference)</span></span>

<span data-ttu-id="0afe7-103">Bir sorgu ifadesinde, alt ifadenin sonucunu izleyen yan tümcelerde kullanmak üzere depolamak bazen yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="0afe7-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="0afe7-104">Bunu, yeni bir Aralık değişkeni oluşturan ve bunu sağladığınız ifadenin sonucuyla Başlatan `let` anahtar sözcüğüyle yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0afe7-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="0afe7-105">Bir değerle başlatıldıktan sonra, Aralık değişkeni başka bir değeri depolamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0afe7-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="0afe7-106">Ancak, Aralık değişkeni sorgulanabilir bir tür içeriyorsa, bu, sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="0afe7-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="0afe7-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0afe7-107">Example</span></span>

<span data-ttu-id="0afe7-108">Aşağıdaki örnekte `let` iki şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="0afe7-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="0afe7-109">Kendisi için sorgulanabilen bir sıralanabilir tür oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0afe7-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="0afe7-110">Sorgunun `ToLower` Aralık değişkeninde yalnızca bir kez çağırmasını sağlamak için `word`.</span><span class="sxs-lookup"><span data-stu-id="0afe7-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="0afe7-111">`let`kullanmadan, `where` yan tümcesindeki her koşulda `ToLower` çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0afe7-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="0afe7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0afe7-112">See also</span></span>

- [<span data-ttu-id="0afe7-113">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="0afe7-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="0afe7-114">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0afe7-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="0afe7-115">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0afe7-115">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="0afe7-116">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="0afe7-116">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
- [<span data-ttu-id="0afe7-117">Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="0afe7-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
