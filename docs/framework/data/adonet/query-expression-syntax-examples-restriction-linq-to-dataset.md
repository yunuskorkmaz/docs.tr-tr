---
description: 'Hakkında daha fazla bilgi edinin: sorgu Ifadesi sözdizimi örnekleri: kısıtlama (LINQ to DataSet)'
title: 'Sorgu Ifadesi söz dizimi örnekleri: kısıtlama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 06ffaa782a02191be4c9568587824ec1767f1249
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695989"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="bdb9f-103">Sorgu Ifadesi söz dizimi örnekleri: kısıtlama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="bdb9f-103">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>

<span data-ttu-id="bdb9f-104">Bu konudaki örneklerde <xref:System.Linq.Enumerable.Where%2A> <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak bir sorgusu sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bdb9f-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="bdb9f-105">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bdb9f-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="bdb9f-106">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bdb9f-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="bdb9f-107">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="bdb9f-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
  
 <span data-ttu-id="bdb9f-108">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="bdb9f-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="bdb9f-109">Konum</span><span class="sxs-lookup"><span data-stu-id="bdb9f-109">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="bdb9f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdb9f-110">Example</span></span>  

 <span data-ttu-id="bdb9f-111">Bu örnek tüm çevrimiçi siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bdb9f-111">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
### <a name="example"></a><span data-ttu-id="bdb9f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdb9f-112">Example</span></span>  

 <span data-ttu-id="bdb9f-113">Bu örnek, sipariş miktarının 2 ' den büyük ve 6 ' dan küçük olduğu siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bdb9f-113">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]
  
### <a name="example"></a><span data-ttu-id="bdb9f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdb9f-114">Example</span></span>  

 <span data-ttu-id="bdb9f-115">Bu örnek, tüm kırmızı renkli ürünleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bdb9f-115">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]
  
### <a name="example"></a><span data-ttu-id="bdb9f-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdb9f-116">Example</span></span>  

 <span data-ttu-id="bdb9f-117">Bu örnek, <xref:System.Linq.Enumerable.Where%2A> 1 aralık 2002 ' den sonra yapılan siparişleri bulmak için yöntemini kullanır ve sonra <xref:System.Data.DataRow.GetChildRows%2A> her bir siparişin ayrıntılarını almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bdb9f-117">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="bdb9f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdb9f-118">See also</span></span>

- [<span data-ttu-id="bdb9f-119">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="bdb9f-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="bdb9f-120">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="bdb9f-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="bdb9f-121">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="bdb9f-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="bdb9f-122">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdb9f-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
