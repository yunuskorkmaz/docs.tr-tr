---
title: 'Nasıl yapılır: birincil anahtarlar temsil eder'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: dae8603a18318f45182c7148b10b8194e67fd017
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352596"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="05e7e-102">Nasıl yapılır: birincil anahtarlar temsil eder</span><span class="sxs-lookup"><span data-stu-id="05e7e-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="05e7e-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özellikte <xref:System.Data.Linq.Mapping.ColumnAttribute> bir özellik veya alan bir veritabanı sütununa birincil anahtarını temsil eden atamak özniteliği.</span><span class="sxs-lookup"><span data-stu-id="05e7e-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="05e7e-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="05e7e-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="05e7e-105"> Hesaplanan sütunlar birincil anahtarlar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="05e7e-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="05e7e-106">Bir özellik veya alan birincil anahtarı olarak belirtmek için</span><span class="sxs-lookup"><span data-stu-id="05e7e-106">To designate a property or field as a primary key</span></span>  
  
1.  <span data-ttu-id="05e7e-107">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="05e7e-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="05e7e-108">Değer olarak belirtin `true`.</span><span class="sxs-lookup"><span data-stu-id="05e7e-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e7e-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05e7e-109">See Also</span></span>  
 [<span data-ttu-id="05e7e-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="05e7e-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="05e7e-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="05e7e-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
