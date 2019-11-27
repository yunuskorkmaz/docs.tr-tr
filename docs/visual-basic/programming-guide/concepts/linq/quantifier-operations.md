---
title: Niceleyici İşlemleri
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: f5b98ec09405ca4b8c715dc7da342e66a5d434d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346591"
---
# <a name="quantifier-operations-visual-basic"></a>Nicelik belirteci Işlemleri (Visual Basic)
Nicelik belirteci işlemleri bir dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten <xref:System.Boolean> bir değer döndürür.  
  
 Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir. İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç `true`. İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını sorar ve sonuç `true`.  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Tümü|Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Tümü|Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|İçerir|Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri  
 Bu örnekler, bir LINQ sorgusunda filtreleme koşulunun bir parçası olarak Visual Basic `Aggregate` yan tümcesini kullanır.  
  
 Aşağıdaki örnek, pelleri belirtilen bir Age den daha eski olan kişilerden gelen bir koleksiyondan geri dönmek için `Aggregate` yan tümcesini ve <xref:System.Linq.Enumerable.All%2A> genişletme yöntemini kullanır.  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 Sonraki örnekte, belirli bir yaşından daha eski olan en az bir evcil hayvan olan kişilerden gelen bir koleksiyondan geri dönmek için `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.Any%2A> genişletme yöntemi kullanılmaktadır.  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Aggregate Yan Tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
