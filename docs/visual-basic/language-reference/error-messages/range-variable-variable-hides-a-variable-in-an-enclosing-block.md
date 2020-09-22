---
title: <variable> aralık değişkeni kapsayan bir blok içinde bir değişken, önceden tanımlanmış bir aralık değişkeni veya bir sorgu ifadesinde örtük olarak bildirilmiş bir değişken gizliyor
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: d7399e7f51dc7c00ed903fa74647038009433ac0
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870921"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="4de72-102">\<variable> aralık değişkeni kapsayan bir blok içinde bir değişken, önceden tanımlanmış bir aralık değişkeni veya bir sorgu ifadesinde örtük olarak bildirilmiş bir değişken gizliyor</span><span class="sxs-lookup"><span data-stu-id="4de72-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>

<span data-ttu-id="4de72-103">,, Veya yan tümcesinde belirtilen bir Aralık değişkeni adı, `Select` `From` `Aggregate` `Let` önceden sorguda belirtilen bir aralık değişkeninin adını veya bir alan adı ya da bir toplama işlevinin adı gibi, sorgu tarafından örtük olarak tanımlanan bir değişkenin adını çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="4de72-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="4de72-104">**Hata kimliği:** BC36633</span><span class="sxs-lookup"><span data-stu-id="4de72-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4de72-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4de72-105">To correct this error</span></span>  
  
- <span data-ttu-id="4de72-106">Belirli bir sorgu kapsamındaki tüm Aralık değişkenlerinin benzersiz adlara sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4de72-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="4de72-107">İç içe sorguların benzersiz bir kapsamı olduğundan emin olmak için bir sorguyu parantez içine alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4de72-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de72-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4de72-108">See also</span></span>

- [<span data-ttu-id="4de72-109">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="4de72-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4de72-110">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="4de72-110">From Clause</span></span>](../queries/from-clause.md)
- [<span data-ttu-id="4de72-111">Let yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="4de72-111">Let Clause</span></span>](../queries/let-clause.md)
- [<span data-ttu-id="4de72-112">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="4de72-112">Aggregate Clause</span></span>](../queries/aggregate-clause.md)
- [<span data-ttu-id="4de72-113">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="4de72-113">Select Clause</span></span>](../queries/select-clause.md)
