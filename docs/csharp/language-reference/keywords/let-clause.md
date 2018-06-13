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
ms.openlocfilehash: 9d625db1231687cdad2e24303b2e08ecf736a50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269646"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="4dfde-102">let tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4dfde-102">let clause (C# Reference)</span></span>
<span data-ttu-id="4dfde-103">Bir sorgu ifadesinde bazen sonraki yan tümcelerinde kullanmak için bir alt ifade sonucunu depolamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4dfde-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="4dfde-104">Bunu yapmak `let` yeni bir aralık değişkeni oluşturan ve sağladığınız ifade sonucuyla başlatır anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="4dfde-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="4dfde-105">Bir değerle başlatıldıktan sonra aralık değişkeni başka bir değeri depolamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4dfde-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="4dfde-106">Ancak, aralık değişkeni sorgulanabilir bir tür barındırıyorsa, sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="4dfde-106">However, if the range variable holds a queryable type, it can be queried.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dfde-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4dfde-107">Example</span></span>  
 <span data-ttu-id="4dfde-108">Aşağıdaki örnekte `let` iki yolla kullanılır:</span><span class="sxs-lookup"><span data-stu-id="4dfde-108">In the following example `let` is used in two ways:</span></span>  
  
1.  <span data-ttu-id="4dfde-109">Kendisini sorgulanabilir bir numaralandırma türü oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="4dfde-109">To create an enumerable type that can itself be queried.</span></span>  
  
2.  <span data-ttu-id="4dfde-110">Aranacak sorgu etkinleştirmek için `ToLower` aralık değişkeni üzerinde yalnızca bir kez `word`.</span><span class="sxs-lookup"><span data-stu-id="4dfde-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="4dfde-111">Kullanmadan `let`, çağrı zorunda `ToLower` her koşulda içinde `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4dfde-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4dfde-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4dfde-112">See Also</span></span>  
 [<span data-ttu-id="4dfde-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4dfde-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4dfde-114">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="4dfde-114">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="4dfde-115">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="4dfde-115">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="4dfde-116">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="4dfde-116">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="4dfde-117">Nasıl yapılır: Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="4dfde-117">How to: Handle Exceptions in Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)
