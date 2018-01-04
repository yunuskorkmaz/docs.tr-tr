---
title: "Nasıl yapılır: temsil eden sınıflar olarak tabloları"
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
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 27e3d21e42dbf841768e2a68ccbfff62368500bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="b639e-102">Nasıl yapılır: temsil eden sınıflar olarak tabloları</span><span class="sxs-lookup"><span data-stu-id="b639e-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="b639e-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği bir sınıf bir veritabanı tablosu ile ilişkilendirilmiş bir varlık sınıfı olarak belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b639e-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="b639e-104">Bir sınıf bir veritabanı tablosuna eşlemek için</span><span class="sxs-lookup"><span data-stu-id="b639e-104">To map a class to a database table</span></span>  
  
-   <span data-ttu-id="b639e-105">Ekleme <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği sınıf bildirimi.</span><span class="sxs-lookup"><span data-stu-id="b639e-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b639e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b639e-106">Example</span></span>  
 <span data-ttu-id="b639e-107">Aşağıdaki kod kurar `Customer` sınıf ile ilişkili bir varlık sınıfı olarak `Customers` veritabanı tablosu.</span><span class="sxs-lookup"><span data-stu-id="b639e-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="b639e-108">Belirtmek zorunda değilsiniz <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> adı çıkarsanabileceği varsa özelliği.</span><span class="sxs-lookup"><span data-stu-id="b639e-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="b639e-109">Bir ad belirtmezseniz, adı, özellik veya alan aynı adı olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b639e-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b639e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b639e-110">See Also</span></span>  
 [<span data-ttu-id="b639e-111">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="b639e-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="b639e-112">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b639e-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
