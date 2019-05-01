---
title: 'Nasıl yapılır: Veritabanı Veri Türleri Belirtme'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 67f23ff06aefbcff4ba7e2eaab63d9b8493b9717
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033676"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="ee4cd-102">Nasıl yapılır: Veritabanı Veri Türleri Belirtme</span><span class="sxs-lookup"><span data-stu-id="ee4cd-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="ee4cd-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> özelliği bir <xref:System.Data.Linq.Mapping.ColumnAttribute> sütunu bir T-SQL tablo bildiriminde tanımlayan tam metni belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ee4cd-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="ee4cd-104">Belirtmelisiniz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> yalnızca kullanmayı planlıyorsanız özelliği <xref:System.Data.Linq.DataContext.CreateDatabase%2A> veritabanı örneği oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="ee4cd-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="ee4cd-105">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee4cd-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="ee4cd-106">Bir T-SQL tablosunu bir veri türü tanımlamak için metin belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ee4cd-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="ee4cd-107">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ee4cd-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="ee4cd-108">Değerini <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> T-SQL tarafından kullanılan tam metin özellik.</span><span class="sxs-lookup"><span data-stu-id="ee4cd-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4cd-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee4cd-109">See also</span></span>

- [<span data-ttu-id="ee4cd-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="ee4cd-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ee4cd-111">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ee4cd-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
