---
title: Sayısal Dizideki En Büyük Değeri Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: ebef8cb373da4021fd68fd7ce38de8cb06eb81ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782178"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="32c25-102">Sayısal Dizideki En Büyük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="32c25-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="32c25-103">En yüksek değeri bir sayısal değer dizisinde bulmak için işlecinikullanın.<xref:System.Linq.Enumerable.Max%2A></span><span class="sxs-lookup"><span data-stu-id="32c25-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32c25-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="32c25-104">Example</span></span>  
 <span data-ttu-id="32c25-105">Aşağıdaki örnek, herhangi bir çalışan için en son işe alım tarihini bulur.</span><span class="sxs-lookup"><span data-stu-id="32c25-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="32c25-106">Bu sorguyu örnek Northwind veritabanında çalıştırırsanız, çıkış şu şekilde olur: `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="32c25-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="32c25-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="32c25-107">Example</span></span>  
 <span data-ttu-id="32c25-108">Aşağıdaki örnek, her bir ürün için Stoktaki en fazla birimi bulur.</span><span class="sxs-lookup"><span data-stu-id="32c25-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="32c25-109">Bu örneği örnek Northwind veritabanına karşı çalıştırırsanız, çıkış şu şekilde olur: `125`.</span><span class="sxs-lookup"><span data-stu-id="32c25-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="32c25-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="32c25-110">Example</span></span>  
 <span data-ttu-id="32c25-111">Aşağıdaki örnek, `Products` her kategoride en yüksek birim fiyata sahip olan öğesini bulmak için Max kullanır.</span><span class="sxs-lookup"><span data-stu-id="32c25-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="32c25-112">Daha sonra çıktı, sonuçları kategoriye göre listeler.</span><span class="sxs-lookup"><span data-stu-id="32c25-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="32c25-113">Önceki sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlarınız aşağıdakine benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="32c25-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32c25-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32c25-114">See also</span></span>

- [<span data-ttu-id="32c25-115">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="32c25-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="32c25-116">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="32c25-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
