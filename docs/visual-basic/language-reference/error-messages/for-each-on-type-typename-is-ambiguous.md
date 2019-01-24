---
title: '&#39;Her&#39; türündeki &#39; &lt;typename&gt; &#39; türü, birden çok örneklemesini uyguladığından belirsiz &#39;.IEnumerable (Of T) örneği&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 7fd779ba34afa2a59fa6c42971597df8ce01495a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597352"
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39;Her&#39; türündeki &#39; &lt;typename&gt; &#39; türü, birden çok örneklemesini uyguladığından belirsiz &#39;.IEnumerable (Of T) örneği&#39;
A `For Each` deyimi birden fazla olan bir yineleyici değişkeni belirtir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi.  
  
 Yineleyici değişkeni uygulayan bir türü olmalıdır <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi biriyle `Collections` isim [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Her yapı için farklı tür bağımsız değişkeni kullanarak birden fazla oluşturulmuş genel arabirim uygulamak bir sınıf mümkündür. Yineleyici değişken için bunu yapan bir sınıfı kullandıysanız, bu değişkeni birden fazla sahip <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi. Böyle bir durumda, Visual Basic çağırmak için kullanılacak yöntemi seçin.  
  
 **Hata Kimliği:** BC32096  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kullanma [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) veya [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md) arabirimi tanımlama yineleyici değişken türü olarak atanamadı <xref:System.Collections.IEnumerable.GetEnumerator%2A> kullanmak istediğiniz yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
