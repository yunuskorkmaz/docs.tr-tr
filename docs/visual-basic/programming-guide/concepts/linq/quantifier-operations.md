---
title: Niceleyici işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: e871a77caf0b7cfe361f11462085180c17bf2057
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816050"
---
# <a name="quantifier-operations-visual-basic"></a>Niceleyici işlemleri (Visual Basic)
Niceleyici işlemleri dönüş bir <xref:System.Boolean> bazılarını veya tümünü bir dizideki öğelerin bir koşulu karşılayan olup olmadığını gösteren değer.  
  
 Aşağıdaki çizimde, iki farklı kaynak diziler üzerinde iki farklı niceleyici işlemleri gösterilmektedir. İlk işlem bir veya daha fazla öğe olan karakter 'A' ve sonucu olup olmadığını soran `true`. İkinci işlem tüm öğeleri karakter 'A' olan ve sonucu olup olmadığını soran `true`.  
  
 ![LINQ Niceleyici işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Tümü|Bir dizideki tüm öğeler bir koşulu karşılayan olup olmadığını belirler.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Tüm|Bir dizideki herhangi bir öğe bir koşulu karşılayan olup olmadığını belirler.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|İçerir|Bir dizi belirtilen öğeyi içerip içermediğini belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifadesi söz dizimi örnekleri  
 Bu örneklerde `Aggregate` Visual Basic'te LINQ sorgusundaki filtre koşulu bir parçası olarak yan tümcesi.  
  
 Aşağıdaki örnekte `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.All%2A> genişletme yöntemi bu kişilere, Evcil Hayvanlar belirtilen yaşından tüm eski bir koleksiyondan döndürülecek.  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 Sonraki örnekte `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.Any%2A> en az bir sahip bu kişileri hayvan koleksiyondan döndürmek için genişletme yöntemi belirtilen bir geçerlilik süresi eski.  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Aggregate Yan Tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Nasıl yapılır: Belirli bir sözcükler (LINQ) (Visual Basic) kümesini içeren cümleleri sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
