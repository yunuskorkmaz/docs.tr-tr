---
title: 'Nasıl yapılır: Sütun Null değerlere izin verecek şekilde temsil eder.'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: ba362e45c8694dbb30e977b3d9f25702ee9dea48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715536"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="5a73e-102">Nasıl yapılır: Sütun Null değerlere izin verecek şekilde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a73e-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="5a73e-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> ilişkili veritabanı sütunu null değerler tutabilir belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5a73e-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="5a73e-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a73e-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="5a73e-105">Bir sütunu null değerlere izin verecek şekilde belirlemek için</span><span class="sxs-lookup"><span data-stu-id="5a73e-105">To designate a column as allowing null values</span></span>  
  
1.  <span data-ttu-id="5a73e-106">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5a73e-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="5a73e-107">Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> özellik değerini `true`.</span><span class="sxs-lookup"><span data-stu-id="5a73e-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a73e-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a73e-108">See also</span></span>
- [<span data-ttu-id="5a73e-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="5a73e-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="5a73e-110">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5a73e-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
