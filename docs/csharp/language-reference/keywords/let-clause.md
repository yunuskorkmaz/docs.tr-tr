---
title: let yan tümcesi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173594"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="40272-102">let tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="40272-102">let clause (C# Reference)</span></span>

<span data-ttu-id="40272-103">Sorgu ifadesinde, bir alt ifadenin sonucunu sonraki tümcelerde kullanmak için depolamak bazen yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="40272-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="40272-104">Bunu, yeni bir `let` aralık değişkeni oluşturan ve sağladığınız ifadenin sonucuyla baş harfe çeken anahtar kelimeyle yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40272-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="40272-105">Bir değerle baş harfe büründükten sonra, aralık değişkeni başka bir değeri depolamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="40272-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="40272-106">Ancak, aralık değişkeni sorgulanabilir bir tür tutuyorsa, sorgulanabilir bir tür sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="40272-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="40272-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="40272-107">Example</span></span>

<span data-ttu-id="40272-108">Aşağıdaki örnekte `let` iki şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="40272-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="40272-109">Kendisi sorgulanabilir bir sayısal olabilir türü oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="40272-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="40272-110">Sorgunun aralık değişkeninde `ToLower` `word`yalnızca bir kez aramasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="40272-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="40272-111">Kullanmadan, `let`yan tümcedeki her yüklemi `where` çağırmanız `ToLower` gerekir.</span><span class="sxs-lookup"><span data-stu-id="40272-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="40272-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40272-112">See also</span></span>

- [<span data-ttu-id="40272-113">C# Referans</span><span class="sxs-lookup"><span data-stu-id="40272-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="40272-114">Sorgu Anahtar Kelimeleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="40272-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="40272-115">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="40272-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="40272-116">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="40272-116">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="40272-117">Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="40272-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
