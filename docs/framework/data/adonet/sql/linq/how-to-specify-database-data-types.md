---
title: 'Nasıl yapılır: Veritabanı Veri Türleri Belirtme'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 09ca8dc6fa440138523bcd2905335a04517dd806
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793265"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="f92ec-102">Nasıl yapılır: Veritabanı Veri Türleri Belirtme</span><span class="sxs-lookup"><span data-stu-id="f92ec-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="f92ec-103">Bir T-SQL tablo <xref:System.Data.Linq.Mapping.ColumnAttribute> bildiriminde sütunu tanımlayan tam metni belirtmek için bir öznitelik üzerinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f92ec-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="f92ec-104"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Özelliği yalnızca bir veritabanının örneğini oluşturmak için kullanmayı <xref:System.Data.Linq.DataContext.CreateDatabase%2A> planlıyorsanız belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f92ec-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="f92ec-105">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="f92ec-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="f92ec-106">T-SQL tablosunda veri türü tanımlamak üzere metin belirtmek için</span><span class="sxs-lookup"><span data-stu-id="f92ec-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="f92ec-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f92ec-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="f92ec-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Özelliğin değerini T-SQL tarafından kullanılan tam metin olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f92ec-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f92ec-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f92ec-109">See also</span></span>

- [<span data-ttu-id="f92ec-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="f92ec-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="f92ec-111">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f92ec-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
