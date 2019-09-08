---
title: 'Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: bb9510986581ad6d3bcd0711aed681ef3a7c4e45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781788"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="6e755-102">Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="6e755-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="6e755-103">Bir alan veya özelliği veritabanı <xref:System.Data.Linq.Mapping.ColumnAttribute> tarafından oluşturulan bir sütunu temsil edecek şekilde belirlemek için özniteliğinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e755-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="6e755-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e755-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="6e755-105">Bir alanı veya özelliği veritabanı tarafından oluşturulan bir sütunu temsil edecek şekilde belirlemek için</span><span class="sxs-lookup"><span data-stu-id="6e755-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="6e755-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e755-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="6e755-107">Özellik değerini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6e755-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e755-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e755-108">See also</span></span>

- [<span data-ttu-id="6e755-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="6e755-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="6e755-110">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6e755-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
