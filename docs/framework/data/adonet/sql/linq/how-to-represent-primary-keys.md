---
title: 'Nasıl yapılır: Birincil Anahtarları Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 02570176c8aef5cfdc7ba09fd6976f430900e8df
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166241"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="94e76-102">Nasıl yapılır: Birincil Anahtarları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="94e76-102">How to: Represent Primary Keys</span></span>

<span data-ttu-id="94e76-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> Bir veritabanı sütunu için birincil anahtarı temsil etmek üzere bir özellik veya alan belirlemek için özniteliğinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="94e76-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="94e76-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> ..</span><span class="sxs-lookup"><span data-stu-id="94e76-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="94e76-105">, hesaplanan sütunları birincil anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="94e76-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="94e76-106">Bir özelliği veya alanı birincil anahtar olarak belirlemek için</span><span class="sxs-lookup"><span data-stu-id="94e76-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="94e76-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="94e76-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="94e76-108">Değeri olarak belirtin `true` .</span><span class="sxs-lookup"><span data-stu-id="94e76-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e76-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94e76-109">See also</span></span>

- [<span data-ttu-id="94e76-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="94e76-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="94e76-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="94e76-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
