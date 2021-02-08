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
# <a name="bc36633-range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>BC36633: Range değişkeni \<variable> kapsayan bir blok içinde bir değişken, önceden tanımlanmış bir Aralık değişkeni veya bir sorgu ifadesinde örtük olarak tanımlanmış bir değişken gizliyor

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
