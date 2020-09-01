---
description: Let yan tümcesi-C# başvurusu
title: Let yan tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3767b9745cccd9802374a8100de19f286c9b55ea
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139599"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="018a6-103">let tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="018a6-103">let clause (C# Reference)</span></span>

<span data-ttu-id="018a6-104">Bir sorgu ifadesinde, alt ifadenin sonucunu izleyen yan tümcelerde kullanmak üzere depolamak bazen yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="018a6-104">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="018a6-105">Bunu `let` , yeni bir Aralık değişkeni oluşturan ve bunu sağladığınız ifadenin sonucuyla Başlatan anahtar sözcüğü ile yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="018a6-105">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="018a6-106">Bir değerle başlatıldıktan sonra, Aralık değişkeni başka bir değeri depolamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="018a6-106">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="018a6-107">Ancak, Aralık değişkeni sorgulanabilir bir tür içeriyorsa, bu, sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="018a6-107">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="018a6-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="018a6-108">Example</span></span>

<span data-ttu-id="018a6-109">Aşağıdaki örnekte `let` iki şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="018a6-109">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="018a6-110">Kendisi için sorgulanabilen bir sıralanabilir tür oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="018a6-110">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="018a6-111">Sorgunun, `ToLower` Aralık değişkeninde yalnızca bir kez çağırmasını sağlamak için `word` .</span><span class="sxs-lookup"><span data-stu-id="018a6-111">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="018a6-112">Kullanmadan `let` , `ToLower` yan tümcesindeki her bir koşula çağrı yapmanız gerekir `where` .</span><span class="sxs-lookup"><span data-stu-id="018a6-112">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="018a6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="018a6-113">See also</span></span>

- [<span data-ttu-id="018a6-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="018a6-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="018a6-115">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="018a6-115">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="018a6-116">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="018a6-116">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="018a6-117">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="018a6-117">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="018a6-118">Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="018a6-118">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
