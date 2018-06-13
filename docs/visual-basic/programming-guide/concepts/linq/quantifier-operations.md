---
title: Niceleyici işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0a0a5fae35a14ab6451f2f56fb2eedd92ac437e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645840"
---
# <a name="quantifier-operations-visual-basic"></a>Niceleyici işlemleri (Visual Basic)
Niceleyici işlemleri dönüş bir <xref:System.Boolean> bazı veya tüm öğeleri bir sırada bir koşulu karşılıyor olup olmadığını belirten değer.  
  
 Aşağıdaki çizimde, iki farklı kaynak sıraları üzerinde iki farklı niceleyici işlemleri gösterilmektedir. İlk işlemi bir veya daha fazla öğe karakter 'A' olan ve sonucu olup olmadığını soran `true`. İkinci bir işlem tüm öğeleri karakter 'A' olan ve sonucu olup olmadığını soran `true`.  
  
 ![LINQ Niceleyici işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Tümü|Bir dizi tüm öğeler bir koşulu karşılıyor olup olmadığını belirler.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|tüm|Bir dizisinde herhangi bir öğenin bir koşulu karşılıyor olup olmadığını belirler.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|İçerir|Bir dizi belirtilen öğeyi içerip içermediğini belirler.|Yok.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifade sözdizimi örnekleri  
 Bu örneklerde `Aggregate` yan tümcesi Visual Basic'te LINQ Sorgu filtre koşulu bir parçası olarak.  
  
 Aşağıdaki örnek kullanır `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.All%2A> genişletme yöntemi, Evcil Hayvanlar belirtilen yaşından tüm eski kişilerle koleksiyondan döndürülecek.  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 Sonraki örnek kullanır `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.Any%2A> en az bir tane bu kişilerin pet koleksiyondan dönmek için genişletme yöntemi belirtilen bir geçerlilik süresi eski.  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Aggregate Yan Tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Nasıl yapılır: sözcükleri (LINQ) (Visual Basic) belirtilen bir kümesini içeren cümleleri sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
