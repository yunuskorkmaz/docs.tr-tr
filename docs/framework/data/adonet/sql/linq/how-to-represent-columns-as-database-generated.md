---
title: 'Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 914fdcb78efbaaddf08330e32e1d7f7c4e62436e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166323"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="2f286-102">Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="2f286-102">How to: Represent Columns as Database-Generated</span></span>

<span data-ttu-id="2f286-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> Bir alan veya özelliği veritabanı tarafından oluşturulan bir sütunu temsil edecek şekilde belirlemek için özniteliğinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f286-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="2f286-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> ..</span><span class="sxs-lookup"><span data-stu-id="2f286-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="2f286-105">Bir alanı veya özelliği veritabanı tarafından oluşturulan bir sütunu temsil edecek şekilde belirlemek için</span><span class="sxs-lookup"><span data-stu-id="2f286-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="2f286-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f286-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="2f286-107">Özellik değerini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="2f286-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f286-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f286-108">See also</span></span>

- [<span data-ttu-id="2f286-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="2f286-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="2f286-110">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2f286-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
