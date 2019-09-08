---
title: 'Nasıl yapılır: Birincil Anahtarları Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 5df82292f000d7f5e61cab699237b86de30bda70
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793436"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="7792e-102">Nasıl yapılır: Birincil Anahtarları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="7792e-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="7792e-103">Bir veritabanı sütunu için birincil <xref:System.Data.Linq.Mapping.ColumnAttribute> anahtarı temsil etmek üzere bir özellik veya alan belirlemek için özniteliğinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7792e-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="7792e-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="7792e-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7792e-105">, hesaplanan sütunları birincil anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7792e-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="7792e-106">Bir özelliği veya alanı birincil anahtar olarak belirlemek için</span><span class="sxs-lookup"><span data-stu-id="7792e-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="7792e-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7792e-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="7792e-108">Değeri olarak `true`belirtin.</span><span class="sxs-lookup"><span data-stu-id="7792e-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7792e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7792e-109">See also</span></span>

- [<span data-ttu-id="7792e-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="7792e-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="7792e-111">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7792e-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
