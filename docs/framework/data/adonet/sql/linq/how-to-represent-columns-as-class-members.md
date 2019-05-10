---
title: 'Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 009da2579a6fe15cea3913ae5844fc886da2586c
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910739"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="6ac48-102">Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="6ac48-102">How to: Represent Columns as Class Members</span></span>
<span data-ttu-id="6ac48-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> bir alan veya özellik bir veritabanı sütunu ile ilişkilendirmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6ac48-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="6ac48-104">Bir alan veya özellik bir veritabanı sütununa eşlemek için</span><span class="sxs-lookup"><span data-stu-id="6ac48-104">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="6ac48-105">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği için özellik veya alan bildirimi.</span><span class="sxs-lookup"><span data-stu-id="6ac48-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ac48-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ac48-106">Example</span></span>  
 <span data-ttu-id="6ac48-107">Aşağıdaki kod haritaları `CustomerID` alanındaki `Customer` sınıfının `CustomerID` sütununda `Customers` veritabanı tablosu.</span><span class="sxs-lookup"><span data-stu-id="6ac48-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="6ac48-108">Belirtmek zorunda değilsiniz <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> adı çıkarılan varsa özelliği.</span><span class="sxs-lookup"><span data-stu-id="6ac48-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="6ac48-109">Bir ad belirtmezseniz, adı, özellik veya alan aynı ada olduğu varsayılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6ac48-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac48-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ac48-110">See also</span></span>

- [<span data-ttu-id="6ac48-111">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="6ac48-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="6ac48-112">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6ac48-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
