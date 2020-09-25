---
title: DataRow 'ı karşılaştırma (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 8cce52734c83e42312d71806d4151ef21e4df0ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203806"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="d20c2-102">DataRow 'ı karşılaştırma (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d20c2-102">Comparing DataRows (LINQ to DataSet)</span></span>

<span data-ttu-id="d20c2-103">Dil ile tümleşik sorgu (LINQ), eşit olup olmadığını görmek için kaynak öğeleri karşılaştırmak üzere çeşitli küme işleçlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d20c2-103">Language-Integrated Query (LINQ) defines various set operators to compare source elements to see if they are equal.</span></span> <span data-ttu-id="d20c2-104">LINQ aşağıdaki set işleçlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="d20c2-104">LINQ provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="d20c2-105">Bu işleçler, <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> her öğe koleksiyonunda ve yöntemlerini çağırarak kaynak öğeleri karşılaştırır <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> .</span><span class="sxs-lookup"><span data-stu-id="d20c2-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="d20c2-106">A durumunda <xref:System.Data.DataRow> , bu işleçler, tablo verileri üzerinden ayarlama işlemlerine yönelik ideal davranış olmayan bir başvuru karşılaştırması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d20c2-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="d20c2-107">Ayarlanan işlemler için, genellikle öğe değerlerinin öğe başvurularına eşit olup olmadığını belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="d20c2-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="d20c2-108">Bu nedenle, <xref:System.Data.DataRowComparer> sınıfı LINQ to DataSet eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d20c2-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to LINQ to DataSet.</span></span> <span data-ttu-id="d20c2-109">Bu sınıf, satır değerlerini karşılaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d20c2-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="d20c2-110"><xref:System.Data.DataRowComparer>Sınıfı için bir değer karşılaştırma uygulamasını içerir <xref:System.Data.DataRow> , bu nedenle bu sınıf gibi ayarlama işlemleri için kullanılabilir <xref:System.Linq.Enumerable.Distinct%2A> .</span><span class="sxs-lookup"><span data-stu-id="d20c2-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="d20c2-111">Bu sınıf doğrudan başlatılamaz; Bunun yerine, <xref:System.Data.DataRowComparer.Default%2A> özelliğinin bir örneğini döndürmek için kullanılması gerekir <xref:System.Data.DataRowComparer%601> .</span><span class="sxs-lookup"><span data-stu-id="d20c2-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="d20c2-112"><xref:System.Data.DataRowComparer%601.Equals%2A>Daha sonra yöntemi çağrılır ve <xref:System.Data.DataRow> Karşılaştırılacak iki nesne giriş parametresi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d20c2-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="d20c2-113"><xref:System.Data.DataRowComparer%601.Equals%2A>Yöntemi, `true` her iki nesnede sıralı sütun değeri kümesi eşitse döndürür <xref:System.Data.DataRow> ; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="d20c2-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d20c2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="d20c2-114">Example</span></span>  

 <span data-ttu-id="d20c2-115">Bu örnek `Intersect` , her iki tabloda görünen kişileri döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d20c2-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="d20c2-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d20c2-116">Example</span></span>  

 <span data-ttu-id="d20c2-117">Aşağıdaki örnek iki satırı karşılaştırır ve karma kodlarını alır.</span><span class="sxs-lookup"><span data-stu-id="d20c2-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="d20c2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d20c2-118">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="d20c2-119">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="d20c2-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="d20c2-120">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="d20c2-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
