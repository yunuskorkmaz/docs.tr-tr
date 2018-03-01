---
title: "Aralık değişkeni &lt;değişkeni&gt; kapsayan bir blok, önceden tanımlı aralık değişkeni ya da örtük olarak bildirilen bir değişken bir sorgu ifadesinde bir değişkeni gizler"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccbac48694a13daa09f2511cf39d5dbd51cdaaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="1bdd8-102">Aralık değişkeni &lt;değişkeni&gt; kapsayan bir blok, önceden tanımlı aralık değişkeni ya da örtük olarak bildirilen bir değişken bir sorgu ifadesinde bir değişkeni gizler</span><span class="sxs-lookup"><span data-stu-id="1bdd8-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="1bdd8-103">Belirtilen aralık değişkeni adı bir `Select`, `From`, `Aggregate`, veya `Let` yan tümcesi çoğaltan zaten sorgu veya sorgu tarafından örtülü olarak bildirilen bir değişken adı daha önce belirtilen aralık değişkeni adı bir alan adı veya bir toplama işlevi adı gibi.</span><span class="sxs-lookup"><span data-stu-id="1bdd8-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="1bdd8-104">**Hata Kimliği:** BC36633</span><span class="sxs-lookup"><span data-stu-id="1bdd8-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1bdd8-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1bdd8-105">To correct this error</span></span>  
  
-   <span data-ttu-id="1bdd8-106">Belirli bir sorgu kapsamdaki tüm aralık değişkenleri benzersiz adlara sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1bdd8-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="1bdd8-107">Sorgu iç içe geçmiş sorgular benzersiz bir kapsama sahip olduğunuzdan emin olmak için ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="1bdd8-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdd8-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bdd8-108">See Also</span></span>  
 [<span data-ttu-id="1bdd8-109">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="1bdd8-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="1bdd8-110">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="1bdd8-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="1bdd8-111">Let tümcesi</span><span class="sxs-lookup"><span data-stu-id="1bdd8-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="1bdd8-112">AGGREGATE tümcesi</span><span class="sxs-lookup"><span data-stu-id="1bdd8-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="1bdd8-113">Select tümcesi</span><span class="sxs-lookup"><span data-stu-id="1bdd8-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
