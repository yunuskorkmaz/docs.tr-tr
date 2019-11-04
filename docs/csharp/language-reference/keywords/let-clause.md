---
title: Let yan tümcesi C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: df3df279d2dbdb59a0a94d9afad37d1a7ddf7b57
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422692"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="bd269-102">let tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bd269-102">let clause (C# Reference)</span></span>

<span data-ttu-id="bd269-103">Bir sorgu ifadesinde, alt ifadenin sonucunu izleyen yan tümcelerde kullanmak üzere depolamak bazen yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="bd269-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="bd269-104">Bunu, yeni bir Aralık değişkeni oluşturan ve bunu sağladığınız ifadenin sonucuyla Başlatan `let` anahtar sözcüğüyle yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd269-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="bd269-105">Bir değerle başlatıldıktan sonra, Aralık değişkeni başka bir değeri depolamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bd269-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="bd269-106">Ancak, Aralık değişkeni sorgulanabilir bir tür içeriyorsa, bu, sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="bd269-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="bd269-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd269-107">Example</span></span>

<span data-ttu-id="bd269-108">Aşağıdaki örnekte `let` iki şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="bd269-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="bd269-109">Kendisi için sorgulanabilen bir sıralanabilir tür oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="bd269-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="bd269-110">Sorgunun `ToLower` Aralık değişkeninde yalnızca bir kez çağırmasını sağlamak için `word`.</span><span class="sxs-lookup"><span data-stu-id="bd269-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="bd269-111">`let`kullanmadan, `where` yan tümcesindeki her koşulda `ToLower` çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd269-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="bd269-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd269-112">See also</span></span>

- [<span data-ttu-id="bd269-113">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="bd269-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="bd269-114">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="bd269-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="bd269-115">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="bd269-115">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="bd269-116">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="bd269-116">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
- [<span data-ttu-id="bd269-117">Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="bd269-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
