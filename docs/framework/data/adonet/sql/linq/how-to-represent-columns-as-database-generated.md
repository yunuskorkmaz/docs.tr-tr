---
title: 'Nasıl yapılır: Sütunları veritabanında oluşturulmuş olarak temsil eder.'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 572da93c216694b496dc5220af66bc00229ccd00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518351"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="612af-102">Nasıl yapılır: Sütunları veritabanında oluşturulmuş olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="612af-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="612af-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> bir alan veya özellik veritabanında oluşturulmuş bir sütunu temsil eden olarak belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="612af-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="612af-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="612af-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="612af-105">Bir alan veya özellik veritabanında oluşturulmuş bir sütunu temsil eden olarak atamak için</span><span class="sxs-lookup"><span data-stu-id="612af-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="612af-106">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="612af-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="612af-107">Özellik değerini ayarlamak `true`.</span><span class="sxs-lookup"><span data-stu-id="612af-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612af-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="612af-108">See also</span></span>
- [<span data-ttu-id="612af-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="612af-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="612af-110">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="612af-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
