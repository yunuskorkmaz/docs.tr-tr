---
title: 'Nasıl yapılır: Birincil Anahtarları Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: dcb8929c9cd9a7b88f19d760b70117a1092760f9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295594"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="41c94-102">Nasıl yapılır: Birincil Anahtarları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="41c94-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="41c94-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> bir özellik veya alan için bir veritabanı sütunu birincil anahtar temsil etmek için belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="41c94-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="41c94-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="41c94-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="41c94-105">Hesaplanan sütunlar, birincil anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="41c94-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="41c94-106">Bir özellik veya alan bir birincil anahtar olarak atamak için</span><span class="sxs-lookup"><span data-stu-id="41c94-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="41c94-107">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="41c94-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="41c94-108">Değeri olarak belirtin `true`.</span><span class="sxs-lookup"><span data-stu-id="41c94-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c94-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41c94-109">See also</span></span>

- [<span data-ttu-id="41c94-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="41c94-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="41c94-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="41c94-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
