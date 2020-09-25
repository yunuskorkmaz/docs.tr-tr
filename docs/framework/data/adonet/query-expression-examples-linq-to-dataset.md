---
title: Sorgu Ifadesi örnekleri (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
ms.openlocfilehash: 1671769871d8c224391a34f5a6294bb6015cafdc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177377"
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="61839-102">Sorgu Ifadesi örnekleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="61839-102">Query Expression Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="61839-103">Bu bölümde, sorgu ifadesi sözdiziminde standart sorgu işleçlerini kullanan LINQ to DataSet programlama örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="61839-103">This section provides LINQ to DataSet programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="61839-104"><xref:System.Data.DataSet>Bu örneklerde kullanılan yöntemi kullanılarak doldurulur ve `FillDataSet` [veri kümesine veri yükleme](loading-data-into-a-dataset.md)sırasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="61839-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="61839-105">Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="61839-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61839-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="61839-106">In This Section</span></span>  

 [<span data-ttu-id="61839-107">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="61839-107">Projection</span></span>](query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="61839-108">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Select%2A> <xref:System.Linq.Enumerable.SelectMany%2A> bir sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="61839-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="61839-109">Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="61839-109">Restriction</span></span>](query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="61839-110">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Where%2A> yöntemini sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="61839-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="61839-111">Bölümleme</span><span class="sxs-lookup"><span data-stu-id="61839-111">Partitioning</span></span>](query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="61839-112">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> <xref:System.Data.DataSet> sonuçlarını sorgulamak ve sonuçları bölümlemek için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61839-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="61839-113">Sıralama</span><span class="sxs-lookup"><span data-stu-id="61839-113">Ordering</span></span>](query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="61839-114">Bu konudaki örneklerde,,, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> <xref:System.Linq.Enumerable.Reverse%2A> ve <xref:System.Linq.Enumerable.ThenByDescending%2A> yöntemlerinin bir sorgulamak <xref:System.Data.DataSet> ve sonuçları sıralamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61839-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="61839-115">Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="61839-115">Element Operators</span></span>](query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="61839-116">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.ElementAt%2A> öğelerinden öğeleri almak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir <xref:System.Data.DataRow> <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="61839-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="61839-117">Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="61839-117">Aggregate Operators</span></span>](query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="61839-118">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Sum%2A> <xref:System.Data.DataSet> ve verileri sorgulamak için,,, ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61839-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="61839-119">Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="61839-119">Join Operators</span></span>](query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="61839-120">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.GroupJoin%2A> <xref:System.Linq.Enumerable.Join%2A> bir sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="61839-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61839-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61839-121">See also</span></span>

- [<span data-ttu-id="61839-122">Yöntem Tabanlı Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="61839-122">Method-Based Query Examples</span></span>](method-based-query-examples-linq-to-dataset.md)
- [<span data-ttu-id="61839-123">DataSet’e Özgü İşleç Örnekleri</span><span class="sxs-lookup"><span data-stu-id="61839-123">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="61839-124">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="61839-124">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
