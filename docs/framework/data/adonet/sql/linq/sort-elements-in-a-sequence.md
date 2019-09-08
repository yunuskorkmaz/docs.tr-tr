---
title: Dizideki Öğeleri Sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: 21fa2f9e1dc2f255fe94f2420ba90a809ab5b05e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792668"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="dcefa-102">Dizideki Öğeleri Sıralama</span><span class="sxs-lookup"><span data-stu-id="dcefa-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="dcefa-103">Bir veya daha fazla anahtara göre bir diziyi sıralamak için işlecinikullanın.<xref:System.Linq.Enumerable.OrderBy%2A></span><span class="sxs-lookup"><span data-stu-id="dcefa-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="dcefa-104">, ve gibi basit temel türler `string` `int`tarafından sıralamayı destekleyecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dcefa-104">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="dcefa-105">Anonim türler gibi karmaşık çok değerli sınıfların sıralamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="dcefa-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="dcefa-106">Ayrıca, veri türlerini desteklemez `byte` .</span><span class="sxs-lookup"><span data-stu-id="dcefa-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcefa-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcefa-107">Example</span></span>  
 <span data-ttu-id="dcefa-108">Aşağıdaki örnek, işe `Employees` alma tarihine göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="dcefa-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="dcefa-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcefa-109">Example</span></span>  
 <span data-ttu-id="dcefa-110">Aşağıdaki örnek, nakliye `where` `London` tarafından sevk `Orders` edilen sıralama için kullanır.</span><span class="sxs-lookup"><span data-stu-id="dcefa-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="dcefa-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcefa-111">Example</span></span>  
 <span data-ttu-id="dcefa-112">Aşağıdaki örnek birim fiyatına `Products` göre en yüksekten en düşüğe göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="dcefa-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="dcefa-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcefa-113">Example</span></span>  
 <span data-ttu-id="dcefa-114">Aşağıdaki örnek, şehir ve sonra `OrderBy` kişi adına `Customers` göre sıralamak için bir bileşik kullanır.</span><span class="sxs-lookup"><span data-stu-id="dcefa-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="dcefa-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcefa-115">Example</span></span>  
 <span data-ttu-id="dcefa-116">Aşağıdaki örnek `ShipCountry`, öğesinden ve daha `EmployeeID 1` sonra en düşük navlun için olan siparişleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="dcefa-116">The following example sorts Orders from `EmployeeID 1` by `ShipCountry`, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="dcefa-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcefa-117">Example</span></span>  
 <span data-ttu-id="dcefa-118">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.GroupBy%2A>veişleçlerini birleştirerek, her kategoride en yüksek birim fiyatına sahip olanöğesinibulurvesonragrubukategorikimliğinegöresıralar.`Products`</span><span class="sxs-lookup"><span data-stu-id="dcefa-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="dcefa-119">Önceki sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar aşağıdakine benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="dcefa-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dcefa-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcefa-120">See also</span></span>

- [<span data-ttu-id="dcefa-121">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="dcefa-121">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="dcefa-122">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="dcefa-122">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
