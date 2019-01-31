---
title: <variable> aralık değişkeni kapsayan bir blok içinde bir değişken, önceden tanımlanmış bir aralık değişkeni veya bir sorgu ifadesinde örtük olarak bildirilmiş bir değişken gizliyor
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 8d898d2d3c5f36177a6363c1a24940fe46de83d3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259890"
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
