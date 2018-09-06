---
title: let tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 62294df7f0f2ebb3249dffd72ba4910fbae984c8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881791"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="182fc-102">let tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="182fc-102">let clause (C# Reference)</span></span>

<span data-ttu-id="182fc-103">Bir sorgu ifadesinde bazen sonraki yan tümcelerinde kullanmak için bir alt ifadenin sonucu depolamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="182fc-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="182fc-104">İle bunu yapabilirsiniz `let` yeni bir aralık değişkenine oluşturan ve sağladığınız ifadenin sonucu ile başlatır anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="182fc-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="182fc-105">Bir değerle başlatıldıktan sonra başka bir değeri depolamak için aralık değişkeni kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="182fc-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="182fc-106">Ancak, aralık değişkeni bir sorgulanabilir tür tutar, sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="182fc-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="182fc-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="182fc-107">Example</span></span>

<span data-ttu-id="182fc-108">Aşağıdaki örnekte `let` iki şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="182fc-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="182fc-109">Kendisini sorgulanabilir bir numaralandırma türü oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="182fc-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="182fc-110">Aranacak sorgu etkinleştirmek için `ToLower` aralık değişkeni üzerinde yalnızca bir kez `word`.</span><span class="sxs-lookup"><span data-stu-id="182fc-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="182fc-111">Kullanmadan `let`, çağırmak zorunda `ToLower` her koşulda içinde `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="182fc-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="182fc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="182fc-112">See also</span></span>

- [<span data-ttu-id="182fc-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="182fc-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="182fc-114">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="182fc-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="182fc-115">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="182fc-115">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="182fc-116">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="182fc-116">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="182fc-117">Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="182fc-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)