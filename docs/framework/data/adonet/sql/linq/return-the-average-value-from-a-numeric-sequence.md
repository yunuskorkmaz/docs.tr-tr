---
title: Sayısal Diziden Ortalama Değer Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 56fe777a3bca1e2b54b61d1586f78a2df4fb475f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963817"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a><span data-ttu-id="2be27-102">Sayısal Diziden Ortalama Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="2be27-102">Return the Average Value From a Numeric Sequence</span></span>
<span data-ttu-id="2be27-103"><xref:System.Linq.Enumerable.Average%2A> İşleci bir sayısal değer dizisinin ortalamasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="2be27-103">The <xref:System.Linq.Enumerable.Average%2A> operator computes the average of a sequence of numeric values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2be27-104">Tamsayı [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değerlerinin`Average` çevirisi, Double olarak değil, tamsayı olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2be27-104">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Average` of integer values is computed as an integer, not as a double.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2be27-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="2be27-105">Example</span></span>  
 <span data-ttu-id="2be27-106">Aşağıdaki örnek `Freight` `Orders` tablodaki değerlerin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2be27-106">The following example returns the average of `Freight` values in the `Orders` table.</span></span>  
  
 <span data-ttu-id="2be27-107">Örnek Northwind veritabanının sonuçları olacaktır `78.2442`.</span><span class="sxs-lookup"><span data-stu-id="2be27-107">Results from the sample Northwind database would be `78.2442`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="2be27-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2be27-108">Example</span></span>  
 <span data-ttu-id="2be27-109">Aşağıdaki örnek, `Products` `Products` tablosundaki tüm birim fiyatının ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2be27-109">The following example returns the average of the unit price of all `Products` in the `Products` table.</span></span>  
  
 <span data-ttu-id="2be27-110">Örnek Northwind veritabanının sonuçları olacaktır `28.8663`.</span><span class="sxs-lookup"><span data-stu-id="2be27-110">Results from the sample Northwind database would be `28.8663`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="2be27-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2be27-111">Example</span></span>  
 <span data-ttu-id="2be27-112">Aşağıdaki örnek, birim fiyatının `Average` ait olduğu kategorinin ortalama `Products` birim fiyatından daha yüksek olan olanları bulmak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2be27-112">The following example uses the `Average` operator to find those `Products` whose unit price is higher than the average unit price of the category it belongs to.</span></span> <span data-ttu-id="2be27-113">Örnek, sonuçları gruplar halinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2be27-113">The example then displays the results in groups.</span></span>  
  
 <span data-ttu-id="2be27-114">Bu örnek, dönüş türü anonim olduğundan, içindeki `var` C#anahtar sözcüğünün kullanılmasını gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2be27-114">Note that this example requires the use of the `var` keyword in C#, because the return type is anonymous.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 <span data-ttu-id="2be27-115">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar aşağıdakine benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="2be27-115">If you run this query against the Northwind sample database, the results should resemble of the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a><span data-ttu-id="2be27-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2be27-116">See also</span></span>

- [<span data-ttu-id="2be27-117">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="2be27-117">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
