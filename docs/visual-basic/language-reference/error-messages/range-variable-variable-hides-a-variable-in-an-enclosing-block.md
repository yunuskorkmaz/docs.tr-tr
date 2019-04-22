---
title: <variable> aralık değişkeni kapsayan bir blok içinde bir değişken, önceden tanımlanmış bir aralık değişkeni veya bir sorgu ifadesinde örtük olarak bildirilmiş bir değişken gizliyor
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: e31f728de228bea743f6c7b5cbfef3cd73367262
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822719"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="45053-102">Aralık değişkeni \<değişkeni > kapsayan bir blok, önceden tanımlanmış bir aralık değişkeni veya sorgu ifadesinde örtük olarak bildirilmiş bir değişken içinde bir değişken gizliyor</span><span class="sxs-lookup"><span data-stu-id="45053-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="45053-103">Belirtilen bir aralık değişkeni adı bir `Select`, `From`, `Aggregate`, veya `Let` yan tümcesi yineleme sorgu veya sorgu tarafından örtük olarak bildirilen bir değişken adı zaten daha önce belirtilen bir aralık değişkeni adı bir alan adı veya bir toplama işlevi adı gibi.</span><span class="sxs-lookup"><span data-stu-id="45053-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="45053-104">**Hata Kimliği:** BC36633</span><span class="sxs-lookup"><span data-stu-id="45053-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="45053-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="45053-105">To correct this error</span></span>  
  
-   <span data-ttu-id="45053-106">Belirli bir sorgu kapsamındaki tüm aralık değişkenleri benzersiz adlara sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="45053-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="45053-107">Sorguda iç içe geçmiş sorgular benzersiz bir kapsama sahip olmasını sağlamak için parantez içine.</span><span class="sxs-lookup"><span data-stu-id="45053-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45053-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45053-108">See also</span></span>

- [<span data-ttu-id="45053-109">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="45053-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="45053-110">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="45053-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="45053-111">Let Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="45053-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="45053-112">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="45053-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="45053-113">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="45053-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
