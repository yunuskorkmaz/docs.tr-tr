---
title: DataRow 'ı karşılaştırma (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 30a782f5e37e867c7a0e4dfd800f4b2c2836d070
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784932"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="7941e-102">DataRow 'ı karşılaştırma (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7941e-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]<span data-ttu-id="7941e-103">eşit olup olmadığını görmek için kaynak öğeleri karşılaştırmak üzere çeşitli küme işleçlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7941e-103">defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]<span data-ttu-id="7941e-104">aşağıdaki küme işleçlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="7941e-104">provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="7941e-105">Bu işleçler, <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> her öğe koleksiyonunda ve <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> yöntemlerini çağırarak kaynak öğeleri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="7941e-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="7941e-106">A <xref:System.Data.DataRow>durumunda, bu işleçler, tablo verileri üzerinden ayarlama işlemlerine yönelik ideal davranış olmayan bir başvuru karşılaştırması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="7941e-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="7941e-107">Ayarlanan işlemler için, genellikle öğe değerlerinin öğe başvurularına eşit olup olmadığını belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="7941e-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="7941e-108">Bu nedenle, <xref:System.Data.DataRowComparer> sınıfı LINQ to DataSet eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="7941e-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to LINQ to DataSet.</span></span> <span data-ttu-id="7941e-109">Bu sınıf, satır değerlerini karşılaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7941e-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="7941e-110">Sınıfı için <xref:System.Data.DataRow>bir değer karşılaştırma uygulamasını içerir, bu nedenle bu sınıf gibi <xref:System.Linq.Enumerable.Distinct%2A>ayarlama işlemleri için kullanılabilir. <xref:System.Data.DataRowComparer></span><span class="sxs-lookup"><span data-stu-id="7941e-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="7941e-111">Bu sınıf doğrudan başlatılamaz; Bunun yerine, <xref:System.Data.DataRowComparer%601>özelliğinin bir örneğini döndürmek için kullanılması gerekir. <xref:System.Data.DataRowComparer.Default%2A></span><span class="sxs-lookup"><span data-stu-id="7941e-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="7941e-112">Daha sonra <xref:System.Data.DataRow> yöntemi çağrılır ve Karşılaştırılacak iki nesne giriş parametresi olarak geçirilir. <xref:System.Data.DataRowComparer%601.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="7941e-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="7941e-113">Yöntemi, her `true` iki <xref:System.Data.DataRow> nesnede sıralı sütun değeri kümesi eşitse döndürür; Aksi takdirde, `false`. <xref:System.Data.DataRowComparer%601.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="7941e-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7941e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="7941e-114">Example</span></span>  
 <span data-ttu-id="7941e-115">Bu örnek, `Intersect` her iki tabloda görünen kişileri döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="7941e-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="7941e-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="7941e-116">Example</span></span>  
 <span data-ttu-id="7941e-117">Aşağıdaki örnek iki satırı karşılaştırır ve karma kodlarını alır.</span><span class="sxs-lookup"><span data-stu-id="7941e-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="7941e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7941e-118">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="7941e-119">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="7941e-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="7941e-120">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="7941e-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
