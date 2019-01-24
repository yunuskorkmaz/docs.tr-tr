---
title: 'Nasıl yapılır: Birincil anahtarları temsil eder'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: a7cea40b30243c6b15da0500a59ba801f2c8da68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687433"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="eebe7-102">Nasıl yapılır: Birincil anahtarları temsil eder</span><span class="sxs-lookup"><span data-stu-id="eebe7-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="eebe7-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> bir özellik veya alan için bir veritabanı sütunu birincil anahtar temsil etmek için belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="eebe7-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="eebe7-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="eebe7-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="eebe7-105">Hesaplanan sütunlar, birincil anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="eebe7-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="eebe7-106">Bir özellik veya alan bir birincil anahtar olarak atamak için</span><span class="sxs-lookup"><span data-stu-id="eebe7-106">To designate a property or field as a primary key</span></span>  
  
1.  <span data-ttu-id="eebe7-107">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="eebe7-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="eebe7-108">Değeri olarak belirtin `true`.</span><span class="sxs-lookup"><span data-stu-id="eebe7-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebe7-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eebe7-109">See also</span></span>
- [<span data-ttu-id="eebe7-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="eebe7-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="eebe7-111">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="eebe7-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
