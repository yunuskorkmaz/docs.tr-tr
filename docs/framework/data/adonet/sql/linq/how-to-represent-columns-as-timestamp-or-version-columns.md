---
title: 'Nasıl yapılır: Sütun olarak zaman damgası veya sürüm sütunları temsil eder'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: fa9ffe01c45df3ce0342b62e12007ddf88ee412d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674576"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="75fb9-102">Nasıl yapılır: Sütun olarak zaman damgası veya sürüm sütunları temsil eder</span><span class="sxs-lookup"><span data-stu-id="75fb9-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="75fb9-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> bir alan veya özellik veritabanı zaman damgası veya sürüm numaraları içeren bir veritabanı sütunu temsil eden olarak belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="75fb9-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="75fb9-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="75fb9-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="75fb9-105">Bir alanı veya özelliği temsil eden bir zaman damgası veya sürüm sütunu olarak atamak için</span><span class="sxs-lookup"><span data-stu-id="75fb9-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="75fb9-106">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="75fb9-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="75fb9-107">Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özellik değerini `true`.</span><span class="sxs-lookup"><span data-stu-id="75fb9-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75fb9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75fb9-108">See also</span></span>
- [<span data-ttu-id="75fb9-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="75fb9-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="75fb9-110">Nasıl yapılır: Üyeleri eşzamanlılık çakışmaları için test edildiğini belirtme</span><span class="sxs-lookup"><span data-stu-id="75fb9-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="75fb9-111">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="75fb9-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
