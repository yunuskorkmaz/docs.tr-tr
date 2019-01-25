---
title: 'Nasıl yapılır: Tabloları sınıf olarak temsil eder.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 307356e056aae29af7c8ceafae0ca02604658aab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509616"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="fecc8-102">Nasıl yapılır: Tabloları sınıf olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fecc8-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="fecc8-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> bir sınıf, bir veritabanı tablosu ile ilişkili bir varlık sınıfı olarak belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fecc8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="fecc8-104">Bir sınıf için bir veritabanı tablosu eşlemek için</span><span class="sxs-lookup"><span data-stu-id="fecc8-104">To map a class to a database table</span></span>  
  
-   <span data-ttu-id="fecc8-105">Ekleme <xref:System.Data.Linq.Mapping.TableAttribute> sınıf bildirimine özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fecc8-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fecc8-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fecc8-106">Example</span></span>  
 <span data-ttu-id="fecc8-107">Aşağıdaki kod kurar `Customer` sınıf ile ilişkili bir varlık sınıfı olarak `Customers` veritabanı tablosu.</span><span class="sxs-lookup"><span data-stu-id="fecc8-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="fecc8-108">Belirtmek zorunda değilsiniz <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> adı çıkarılan varsa özelliği.</span><span class="sxs-lookup"><span data-stu-id="fecc8-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="fecc8-109">Bir ad belirtmezseniz, adı, özellik veya alan aynı ada olduğu varsayılmıştır.</span><span class="sxs-lookup"><span data-stu-id="fecc8-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fecc8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fecc8-110">See also</span></span>
- [<span data-ttu-id="fecc8-111">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="fecc8-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="fecc8-112">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="fecc8-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
