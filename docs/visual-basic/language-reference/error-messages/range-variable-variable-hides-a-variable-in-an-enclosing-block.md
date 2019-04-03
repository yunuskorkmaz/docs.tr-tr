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
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822719"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Aralık değişkeni \<değişkeni > kapsayan bir blok, önceden tanımlanmış bir aralık değişkeni veya sorgu ifadesinde örtük olarak bildirilmiş bir değişken içinde bir değişken gizliyor
Belirtilen bir aralık değişkeni adı bir `Select`, `From`, `Aggregate`, veya `Let` yan tümcesi yineleme sorgu veya sorgu tarafından örtük olarak bildirilen bir değişken adı zaten daha önce belirtilen bir aralık değişkeni adı bir alan adı veya bir toplama işlevi adı gibi.  
  
 **Hata Kimliği:** BC36633  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Belirli bir sorgu kapsamındaki tüm aralık değişkenleri benzersiz adlara sahip olduğundan emin olun. Sorguda iç içe geçmiş sorgular benzersiz bir kapsama sahip olmasını sağlamak için parantez içine.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Let Yan Tümcesi](../../../visual-basic/language-reference/queries/let-clause.md)
- [Aggregate Yan Tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
