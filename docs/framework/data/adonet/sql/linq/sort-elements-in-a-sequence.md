---
description: 'Daha fazla bilgi edinin: bir dizideki öğeleri sıralama'
title: Dizideki Öğeleri Sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: 337afe79826e9a9584a5fc3ed3980341dda1b4d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803769"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="fdfe6-103">Dizideki Öğeleri Sıralama</span><span class="sxs-lookup"><span data-stu-id="fdfe6-103">Sort Elements in a Sequence</span></span>

<span data-ttu-id="fdfe6-104">Bir <xref:System.Linq.Enumerable.OrderBy%2A> veya daha fazla anahtara göre bir diziyi sıralamak için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fdfe6-104">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="fdfe6-105">, ve gibi basit temel türler tarafından sıralamayı destekleyecek şekilde tasarlanmıştır `string` `int` .</span><span class="sxs-lookup"><span data-stu-id="fdfe6-105">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="fdfe6-106">Anonim türler gibi karmaşık çok değerli sınıfların sıralamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fdfe6-106">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="fdfe6-107">Ayrıca, `byte` veri türlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fdfe6-107">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdfe6-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdfe6-108">Example</span></span>  

 <span data-ttu-id="fdfe6-109">Aşağıdaki örnek, `Employees` işe alma tarihine göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="fdfe6-109">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="fdfe6-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdfe6-110">Example</span></span>  

 <span data-ttu-id="fdfe6-111">Aşağıdaki örnek, `where` `Orders` nakliye tarafından sevk edilen sıralama için kullanır `London` .</span><span class="sxs-lookup"><span data-stu-id="fdfe6-111">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="fdfe6-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdfe6-112">Example</span></span>  

 <span data-ttu-id="fdfe6-113">Aşağıdaki örnek `Products` birim fiyatına göre en yüksekten en düşüğe göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="fdfe6-113">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="fdfe6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdfe6-114">Example</span></span>  

 <span data-ttu-id="fdfe6-115">Aşağıdaki örnek, `OrderBy` `Customers` şehir ve sonra kişi adına göre sıralamak için bir bileşik kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdfe6-115">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="fdfe6-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdfe6-116">Example</span></span>  

 <span data-ttu-id="fdfe6-117">Aşağıdaki örnek `EmployeeID 1` `ShipCountry` , öğesinden ve daha sonra en düşük navlun Için olan siparişleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="fdfe6-117">The following example sorts Orders from `EmployeeID 1` by `ShipCountry`, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="fdfe6-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdfe6-118">Example</span></span>  

 <span data-ttu-id="fdfe6-119">Aşağıdaki örnek,, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.Max%2A> ve işleçlerini birleştirerek, <xref:System.Linq.Enumerable.GroupBy%2A> `Products` her kategoride en yüksek birim fiyatına sahip olan öğesini bulur ve sonra grubu kategori kimliğine göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="fdfe6-119">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="fdfe6-120">Önceki sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar aşağıdakine benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="fdfe6-120">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="fdfe6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdfe6-121">See also</span></span>

- [<span data-ttu-id="fdfe6-122">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="fdfe6-122">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="fdfe6-123">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="fdfe6-123">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
