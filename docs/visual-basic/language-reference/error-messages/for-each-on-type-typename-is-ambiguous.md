---
title: Tür birden fazla 'System.Collections.Generic.IEnumerable(Of T)' örneği uyguladığından '<typename>' türü üzerindeki 'For Each' belirsiz
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: af2340e8e514391503d5f9b706d13ba93336698e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662112"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>'For Each' türündeki '\<typename >' türü '.IEnumerable (Of T) örneği' öğesinin birden çok örneklemesini uyguladığından belirsiz
A `For Each` deyimi birden fazla olan bir yineleyici değişkeni belirtir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi.  
  
 Yineleyici değişkeni uygulayan bir türü olmalıdır <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi biriyle `Collections` isim [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Her yapı için farklı tür bağımsız değişkeni kullanarak birden fazla oluşturulmuş genel arabirim uygulamak bir sınıf mümkündür. Yineleyici değişken için bunu yapan bir sınıfı kullandıysanız, bu değişkeni birden fazla sahip <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi. Böyle bir durumda, Visual Basic çağırmak için kullanılacak yöntemi seçin.  
  
 **Hata Kimliği:** BC32096  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Kullanma [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) veya [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md) arabirimi tanımlama yineleyici değişken türü olarak atanamadı <xref:System.Collections.IEnumerable.GetEnumerator%2A> kullanmak istediğiniz yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
