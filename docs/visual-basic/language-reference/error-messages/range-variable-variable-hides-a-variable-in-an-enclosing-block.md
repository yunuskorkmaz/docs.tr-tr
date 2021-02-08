---
description: 'Hakkında daha fazla bilgi edinin: BC36633: Range değişkeni <variable> kapsayan bir blok içinde bir değişken, önceden tanımlanmış bir Aralık değişkeni veya bir sorgu ifadesinde örtük olarak tanımlanmış bir değişken gizliyor'
title: <variable> aralık değişkeni kapsayan bir blok içinde bir değişken, önceden tanımlanmış bir aralık değişkeni veya bir sorgu ifadesinde örtük olarak bildirilmiş bir değişken gizliyor
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: f8e5c109274af9c00963e8a9f18384a299d17a4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792082"
---
# <a name="bc36633-range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="fa920-103">BC36633: Range değişkeni \<variable> kapsayan bir blok içinde bir değişken, önceden tanımlanmış bir Aralık değişkeni veya bir sorgu ifadesinde örtük olarak tanımlanmış bir değişken gizliyor</span><span class="sxs-lookup"><span data-stu-id="fa920-103">BC36633: Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>

<span data-ttu-id="fa920-104">,, Veya yan tümcesinde belirtilen bir Aralık değişkeni adı, `Select` `From` `Aggregate` `Let` önceden sorguda belirtilen bir aralık değişkeninin adını veya bir alan adı ya da bir toplama işlevinin adı gibi, sorgu tarafından örtük olarak tanımlanan bir değişkenin adını çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="fa920-104">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>

 <span data-ttu-id="fa920-105">**Hata kimliği:** BC36633</span><span class="sxs-lookup"><span data-stu-id="fa920-105">**Error ID:** BC36633</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fa920-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fa920-106">To correct this error</span></span>

- <span data-ttu-id="fa920-107">Belirli bir sorgu kapsamındaki tüm Aralık değişkenlerinin benzersiz adlara sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fa920-107">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="fa920-108">İç içe sorguların benzersiz bir kapsamı olduğundan emin olmak için bir sorguyu parantez içine alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa920-108">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa920-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa920-109">See also</span></span>

- [<span data-ttu-id="fa920-110">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="fa920-110">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="fa920-111">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="fa920-111">From Clause</span></span>](../queries/from-clause.md)
- [<span data-ttu-id="fa920-112">Let yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="fa920-112">Let Clause</span></span>](../queries/let-clause.md)
- [<span data-ttu-id="fa920-113">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="fa920-113">Aggregate Clause</span></span>](../queries/aggregate-clause.md)
- [<span data-ttu-id="fa920-114">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="fa920-114">Select Clause</span></span>](../queries/select-clause.md)
