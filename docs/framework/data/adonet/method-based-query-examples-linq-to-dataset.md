---
title: Yöntem tabanlı sorgu örnekleri (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
ms.openlocfilehash: 3cda55457df4157f1b0d2cdef1f857cfe6540c66
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783740"
---
# <a name="method-based-query-examples-linq-to-dataset"></a>Yöntem tabanlı sorgu örnekleri (LINQ to DataSet)
Bu bölümde, standart sorgu işleçlerini kullanan Yöntem tabanlı sorgu sözdiziminde LINQ to DataSet programlama örnekleri verilmiştir. Bu örneklerde `FillDataSet`kullanılanyöntemi kullanılarak doldurulur ve [veri kümesine veri yükleme](loading-data-into-a-dataset.md)sırasında belirtilir. <xref:System.Data.DataSet> Daha fazla bilgi için bkz. [Standart sorgu işleçlerineC#genel bakış ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçleri genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Projeksiyon](method-based-query-syntax-examples-projection.md)  
 Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Select%2A> bir <xref:System.Data.DataSet>sorgulamak için ve <xref:System.Linq.Enumerable.SelectMany%2A> yöntemlerinin nasıl kullanılacağı gösterilmektedir.  
  
 [Bölümlendirme](method-based-query-syntax-examples-partitioning-linq.md)  
 Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Skip%2A> ve sonuçlarını sorgulamak <xref:System.Data.DataSet> ve sonuçları bölümlemek için <xref:System.Linq.Enumerable.Take%2A> ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.  
  
 [Sıralama](method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 Bu konudaki örneklerde,,, <xref:System.Linq.Enumerable.OrderBy%2A>ve <xref:System.Linq.Enumerable.ThenByDescending%2A> yöntemlerinin bir <xref:System.Data.DataSet> sorgulamak ve <xref:System.Linq.Enumerable.OrderByDescending%2A>sonuçları <xref:System.Linq.Enumerable.Reverse%2A>sıralamak için nasıl kullanılacağı gösterilmektedir.  
  
 [Ayarlama İşleçleri](method-based-query-syntax-examples-set-operators.md)  
 Bu konudaki örneklerde, veri satırı kümelerinde değer tabanlı karşılaştırma <xref:System.Linq.Enumerable.Distinct%2A>işlemleri <xref:System.Linq.Enumerable.Except%2A>gerçekleştirmek <xref:System.Linq.Enumerable.Intersect%2A>için, <xref:System.Linq.Enumerable.Union%2A> , ve işleçlerinin nasıl kullanılacağı gösterilmektedir.  
  
 [Dönüştürme İşleçleri](method-based-query-syntax-examples-conversion-operators.md)  
 Bu konudaki örneklerde <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, ve <xref:System.Linq.Enumerable.ToList%2A> yöntemlerinin hemen bir sorgu ifadesini yürütmek için nasıl kullanılacağı gösterilmektedir.  
  
 [Öğe İşleçleri](method-based-query-syntax-examples-element-operators.md)  
 Bu konudaki örneklerde <xref:System.Linq.Enumerable.First%2A> , öğelerinden öğeleri almak <xref:System.Linq.Enumerable.ElementAt%2A> <xref:System.Data.DataRow> <xref:System.Data.DataSet>için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.  
  
 [Toplama İşleçleri](method-based-query-syntax-examples-aggregate-operators.md)  
 Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Count%2A> veverilerisorgulamak<xref:System.Data.DataSet> için,,, ve <xref:System.Linq.Enumerable.Sum%2A> yöntemlerinin nasıl kullanılacağı gösterilmektedir.  
  
 [Birleştirme](method-based-query-syntax-examples-join-linq-to-dataset.md)  
 Bu konudaki örneklerde, <xref:System.Linq.Enumerable.GroupJoin%2A> bir <xref:System.Data.DataSet>sorgulamak için ve <xref:System.Linq.Enumerable.Join%2A> yöntemlerinin nasıl kullanılacağı gösterilmektedir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu İfadesi Örnekleri](query-expression-examples-linq-to-dataset.md)
- [DataSet’e Özgü İşleç Örnekleri](dataset-specific-operator-examples-linq-to-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
