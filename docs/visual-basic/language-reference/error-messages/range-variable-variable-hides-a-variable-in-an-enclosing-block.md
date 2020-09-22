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
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>\<variable> aralık değişkeni kapsayan bir blok içinde bir değişken, önceden tanımlanmış bir aralık değişkeni veya bir sorgu ifadesinde örtük olarak bildirilmiş bir değişken gizliyor

,, Veya yan tümcesinde belirtilen bir Aralık değişkeni adı, `Select` `From` `Aggregate` `Let` önceden sorguda belirtilen bir aralık değişkeninin adını veya bir alan adı ya da bir toplama işlevinin adı gibi, sorgu tarafından örtük olarak tanımlanan bir değişkenin adını çoğaltır.  
  
 **Hata kimliği:** BC36633  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Belirli bir sorgu kapsamındaki tüm Aralık değişkenlerinin benzersiz adlara sahip olduğundan emin olun. İç içe sorguların benzersiz bir kapsamı olduğundan emin olmak için bir sorguyu parantez içine alabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [From yan tümcesi](../queries/from-clause.md)
- [Let yan tümcesi](../queries/let-clause.md)
- [Aggregate Yan Tümcesi](../queries/aggregate-clause.md)
- [Select yan tümcesi](../queries/select-clause.md)
