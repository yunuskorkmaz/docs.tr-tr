---
title: "Bir sıralamada sıralama öğeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2f4f89c1391b6582d77acccb8b256bef617ecff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="7a461-102">Bir sıralamada sıralama öğeleri</span><span class="sxs-lookup"><span data-stu-id="7a461-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="7a461-103">Kullanım <xref:System.Linq.Enumerable.OrderBy%2A> dizisi bir veya daha fazla anahtarı göre sıralamak için işleci.</span><span class="sxs-lookup"><span data-stu-id="7a461-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7a461-104">Basit ilkel türler tarafından gibi sıralama desteklemek üzere tasarlanmış `string`, `int`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="7a461-104"> is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="7a461-105">Anonim türleri gibi karmaşık birden çok değerli sınıfları için sıralamayı desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="7a461-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="7a461-106">Ayrıca desteklemediği `byte` veri türleri.</span><span class="sxs-lookup"><span data-stu-id="7a461-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a461-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a461-107">Example</span></span>  
 <span data-ttu-id="7a461-108">Aşağıdaki örnek sıralar `Employees` tarafından işe alma tarihi.</span><span class="sxs-lookup"><span data-stu-id="7a461-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="7a461-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a461-109">Example</span></span>  
 <span data-ttu-id="7a461-110">Aşağıdaki örnek kullanır `where` sıralamak için `Orders` sevk `London` nakliye tarafından.</span><span class="sxs-lookup"><span data-stu-id="7a461-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="7a461-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a461-111">Example</span></span>  
 <span data-ttu-id="7a461-112">Aşağıdaki örnek sıralar `Products` birim fiyat yüksekten çok düşük.</span><span class="sxs-lookup"><span data-stu-id="7a461-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="7a461-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a461-113">Example</span></span>  
 <span data-ttu-id="7a461-114">Aşağıdaki örnek, bir bileşik kullanır `OrderBy` sıralamak için `Customers` Şehir ve ardından ilgili kişi adı göre.</span><span class="sxs-lookup"><span data-stu-id="7a461-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="7a461-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a461-115">Example</span></span>  
 <span data-ttu-id="7a461-116">Aşağıdaki örnek siparişleri sıralar `EmployeeID 1` sevk ülkeye göre ve ardından küçüğe nakliye göre.</span><span class="sxs-lookup"><span data-stu-id="7a461-116">The following example sorts Orders from `EmployeeID 1` by ship-to country, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="7a461-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a461-117">Example</span></span>  
 <span data-ttu-id="7a461-118">Aşağıdaki örnek birleştirir <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, ve <xref:System.Linq.Enumerable.GroupBy%2A> bulmak için işleçleri `Products` , her kategoride en yüksek birim fiyat varsa ve sonra Grup kategori kimliğine göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="7a461-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="7a461-119">Northwind örnek veritabanı karşı önceki sorgu çalıştırırsanız, sonuçları şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="7a461-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a461-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a461-120">See Also</span></span>  
 [<span data-ttu-id="7a461-121">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="7a461-121">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="7a461-122">Örnek veritabanları yükleme</span><span class="sxs-lookup"><span data-stu-id="7a461-122">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
