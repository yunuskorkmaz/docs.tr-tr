---
title: "Sayısal dizisinden ortalama değerini döndürür"
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
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1759ff9ca3bbf5198187d2ec5470718dd1730cff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a><span data-ttu-id="7e0a9-102">Sayısal dizisinden ortalama değerini döndürür</span><span class="sxs-lookup"><span data-stu-id="7e0a9-102">Return the Average Value From a Numeric Sequence</span></span>
<span data-ttu-id="7e0a9-103"><xref:System.Linq.Enumerable.Average%2A> İşleci hesaplar sayısal değerleri dizisi ortalaması.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-103">The <xref:System.Linq.Enumerable.Average%2A> operator computes the average of a sequence of numeric values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e0a9-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çevrilmesi `Average` değerler tamsayı hesaplanan bir çift olarak değil bir tamsayı olarak.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-104">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Average` of integer values is computed as an integer, not as a double.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e0a9-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e0a9-105">Example</span></span>  
 <span data-ttu-id="7e0a9-106">Aşağıdaki örnek ortalamasını döndürür `Freight` değerler `Orders` tablo.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-106">The following example returns the average of `Freight` values in the `Orders` table.</span></span>  
  
 <span data-ttu-id="7e0a9-107">Örnek Northwind veritabanı sonuçlarından olacaktır `78.2442`.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-107">Results from the sample Northwind database would be `78.2442`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="7e0a9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e0a9-108">Example</span></span>  
 <span data-ttu-id="7e0a9-109">Aşağıdaki örnek, tüm birim fiyat ortalamasını döndürür `Products` içinde `Products` tablo.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-109">The following example returns the average of the unit price of all `Products` in the `Products` table.</span></span>  
  
 <span data-ttu-id="7e0a9-110">Örnek Northwind veritabanı sonuçlarından olacaktır `28.8663`.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-110">Results from the sample Northwind database would be `28.8663`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="7e0a9-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e0a9-111">Example</span></span>  
 <span data-ttu-id="7e0a9-112">Aşağıdaki örnek kullanır `Average` bulmak için işleci `Products` olan birim fiyat ait kategorisinin ortalama birim fiyat daha yüksek.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-112">The following example uses the `Average` operator to find those `Products` whose unit price is higher than the average unit price of the category it belongs to.</span></span> <span data-ttu-id="7e0a9-113">Örnek sonuçları grupları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-113">The example then displays the results in groups.</span></span>  
  
 <span data-ttu-id="7e0a9-114">Bu örnek kullanımı gerektirdiğini unutmayın `var` C# anahtar sözcüğü dönüş türü anonim olduğundan.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-114">Note that this example requires the use of the `var` keyword in C#, because the return type is anonymous.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 <span data-ttu-id="7e0a9-115">Northwind örnek veritabanı karşı bu sorguyu çalıştırırsanız, sonuçları aşağıdaki benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="7e0a9-115">If you run this query against the Northwind sample database, the results should resemble of the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e0a9-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e0a9-116">See Also</span></span>  
 [<span data-ttu-id="7e0a9-117">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="7e0a9-117">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
