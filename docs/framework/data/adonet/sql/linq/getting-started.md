---
title: "Başlarken"
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
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e05ede0981a066abd72aafa81478d6c84342d18f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started"></a><span data-ttu-id="2c4f5-102">Başlarken</span><span class="sxs-lookup"><span data-stu-id="2c4f5-102">Getting Started</span></span>
<span data-ttu-id="2c4f5-103">Kullanarak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], kullanabileceğiniz [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] SQL erişmek için teknoloji veritabanları bir bellek içi koleksiyonu erişim.</span><span class="sxs-lookup"><span data-stu-id="2c4f5-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="2c4f5-104">Örneğin, `nw` nesnesi aşağıdaki kodda temsil etmek üzere oluşturulur `Northwind` veritabanı `Customers` tablo hedeflediği, satırları için filtrelenir `Customers` gelen `London`ve bir dize `CompanyName` seçilir alma işlemi.</span><span class="sxs-lookup"><span data-stu-id="2c4f5-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="2c4f5-105">Döngü zaman yürütülür, koleksiyonunu `CompanyName` değerleri alınır.</span><span class="sxs-lookup"><span data-stu-id="2c4f5-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="2c4f5-106">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="2c4f5-106">Next Steps</span></span>  
 <span data-ttu-id="2c4f5-107">Ekleme ve güncelleştirme de dahil olmak üzere bazı ek örnekler için bkz [ne siz yapabilirsiniz yapmak ile LINQ-SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2c4f5-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="2c4f5-108">Ardından, bazı izlenecek yollar ve öğreticiler kullanarak uygulamalı deneyim sahibi deneyin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c4f5-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2c4f5-109">Bkz: [tarafından izlenecek yollar öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="2c4f5-109">See [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="2c4f5-110">Son olarak, kendi nasıl başlayacağınızı öğrenin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] okuyarak proje [kullanarak LINQ-SQL için tipik adımları](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2c4f5-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4f5-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c4f5-111">See Also</span></span>  
 [<span data-ttu-id="2c4f5-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2c4f5-112">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="2c4f5-113">LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="2c4f5-113">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 [<span data-ttu-id="2c4f5-114">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="2c4f5-114">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
