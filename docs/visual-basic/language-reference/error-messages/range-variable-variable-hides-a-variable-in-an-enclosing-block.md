---
title: Aralık değişkeni &lt;değişkeni&gt; kapsayan bir blok, önceden tanımlı aralık değişkeni ya da örtük olarak bildirilen bir değişken bir sorgu ifadesinde bir değişkeni gizler
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: f02533cf7cb79c34e5bb5a6d445aaef7ab0e86da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593132"
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Aralık değişkeni &lt;değişkeni&gt; kapsayan bir blok, önceden tanımlı aralık değişkeni ya da örtük olarak bildirilen bir değişken bir sorgu ifadesinde bir değişkeni gizler
Belirtilen aralık değişkeni adı bir `Select`, `From`, `Aggregate`, veya `Let` yan tümcesi çoğaltan zaten sorgu veya sorgu tarafından örtülü olarak bildirilen bir değişken adı daha önce belirtilen aralık değişkeni adı bir alan adı veya bir toplama işlevi adı gibi.  
  
 **Hata Kimliği:** BC36633  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Belirli bir sorgu kapsamdaki tüm aralık değişkenleri benzersiz adlara sahip olduğundan emin olun. Sorgu iç içe geçmiş sorgular benzersiz bir kapsama sahip olduğunuzdan emin olmak için ayraç içine alın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Let Yan Tümcesi](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Aggregate Yan Tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
