---
title: "let tümcesi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 077c5178946b85d0fb85aa8da94966e4c5821736
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="d60b1-102">let tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d60b1-102">let clause (C# Reference)</span></span>
<span data-ttu-id="d60b1-103">Bir sorgu ifadesinde bazen sonraki yan tümcelerinde kullanmak için bir alt ifade sonucunu depolamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d60b1-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="d60b1-104">Bunu yapmak `let` yeni bir aralık değişkeni oluşturan ve sağladığınız ifade sonucuyla başlatır anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d60b1-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="d60b1-105">Bir değerle başlatıldıktan sonra aralık değişkeni başka bir değeri depolamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d60b1-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="d60b1-106">Ancak, aralık değişkeni sorgulanabilir bir tür barındırıyorsa, sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="d60b1-106">However, if the range variable holds a queryable type, it can be queried.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d60b1-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d60b1-107">Example</span></span>  
 <span data-ttu-id="d60b1-108">Aşağıdaki örnekte `let` iki yolla kullanılır:</span><span class="sxs-lookup"><span data-stu-id="d60b1-108">In the following example `let` is used in two ways:</span></span>  
  
1.  <span data-ttu-id="d60b1-109">Kendisini sorgulanabilir bir numaralandırma türü oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d60b1-109">To create an enumerable type that can itself be queried.</span></span>  
  
2.  <span data-ttu-id="d60b1-110">Aranacak sorgu etkinleştirmek için `ToLower` aralık değişkeni üzerinde yalnızca bir kez `word`.</span><span class="sxs-lookup"><span data-stu-id="d60b1-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="d60b1-111">Kullanmadan `let`, çağrı zorunda `ToLower` her koşulda içinde `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d60b1-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d60b1-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d60b1-112">See Also</span></span>  
 [<span data-ttu-id="d60b1-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d60b1-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d60b1-114">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d60b1-114">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="d60b1-115">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d60b1-115">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="d60b1-116">C# üzerinde LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="d60b1-116">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="d60b1-117">Nasıl yapılır: Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="d60b1-117">How to: Handle Exceptions in Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)
