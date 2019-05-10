---
title: (LINQ to DataSet) DataRow karşılaştırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 0903aac366426e8b4d271ae4bfaa54c79a198e5c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583746"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="60288-102">(LINQ to DataSet) DataRow karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="60288-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] <span data-ttu-id="60288-103">eşit olup olmadığını görmek için kaynak öğeleri karşılaştırmak için çeşitli küme işleci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60288-103">defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] <span data-ttu-id="60288-104">Aşağıdaki işleçler kümesi sağlar:</span><span class="sxs-lookup"><span data-stu-id="60288-104">provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="60288-105">Bu işleçler çağırarak kaynak öğeleri karşılaştırma <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> ve <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> öğelerinin her koleksiyonu yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="60288-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="60288-106">Durumunda, bir <xref:System.Data.DataRow>, genellikle ayarlama işlemleri için ideal davranışı sekmeli veriler üzerinde değil, bir başvuru karşılaştırması, bu işleçler gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="60288-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="60288-107">Ayarlama işlemleri için genellikle öğe değerlerini eşit olup olmadığı ve öğesi başvuruları belirlemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="60288-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="60288-108">Bu nedenle, <xref:System.Data.DataRowComparer> sınıfı eklendi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60288-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="60288-109">Bu sınıf, satır değerlerini karşılaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60288-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="60288-110"><xref:System.Data.DataRowComparer> Sınıfı içeren bir değer karşılaştırma uygulaması <xref:System.Data.DataRow>, böylece bu sınıf kümesi işlemleri için aşağıdaki gibi kullanılabilir <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="60288-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="60288-111">Bu sınıf doğrudan oluşturulamaz; Bunun yerine, <xref:System.Data.DataRowComparer.Default%2A> özelliği örneği döndürmek için kullanılması gereken <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="60288-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="60288-112"><xref:System.Data.DataRowComparer%601.Equals%2A> Yöntemi çağrıldıktan sonra ve iki <xref:System.Data.DataRow> Karşılaştırılacak nesne içinde giriş parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="60288-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="60288-113"><xref:System.Data.DataRowComparer%601.Equals%2A> Yöntemi döndürür `true` sütun kümesini hem de değerleri, <xref:System.Data.DataRow> nesneler eşit; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="60288-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60288-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="60288-114">Example</span></span>  
 <span data-ttu-id="60288-115">Bu örnekte `Intersect` her iki tabloda görünen kişileri dönün.</span><span class="sxs-lookup"><span data-stu-id="60288-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="60288-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="60288-116">Example</span></span>  
 <span data-ttu-id="60288-117">Aşağıdaki örnek, iki satır karşılaştırır ve karma kodlarını alır.</span><span class="sxs-lookup"><span data-stu-id="60288-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="60288-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60288-118">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="60288-119">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="60288-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="60288-120">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="60288-120">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
