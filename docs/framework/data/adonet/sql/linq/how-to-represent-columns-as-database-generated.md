---
title: 'Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 2803697c668a8e1dbbeb426ea41b64878f70c145
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903493"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="0c16b-102">Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="0c16b-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="0c16b-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> bir alan veya özellik veritabanında oluşturulmuş bir sütunu temsil eden olarak belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0c16b-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="0c16b-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c16b-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="0c16b-105">Bir alan veya özellik veritabanında oluşturulmuş bir sütunu temsil eden olarak atamak için</span><span class="sxs-lookup"><span data-stu-id="0c16b-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="0c16b-106">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0c16b-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="0c16b-107">Özellik değerini ayarlamak `true`.</span><span class="sxs-lookup"><span data-stu-id="0c16b-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c16b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c16b-108">See also</span></span>

- [<span data-ttu-id="0c16b-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="0c16b-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="0c16b-110">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0c16b-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
