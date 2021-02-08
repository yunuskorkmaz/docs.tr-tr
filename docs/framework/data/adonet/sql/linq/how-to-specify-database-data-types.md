---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veritabanı veri türlerini belirtme'
title: 'Nasıl yapılır: Veritabanı Veri Türleri Belirtme'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 004a16fe9dd0cda608485b13b03ce922d6a9f671
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785919"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="9ac06-103">Nasıl yapılır: Veritabanı Veri Türleri Belirtme</span><span class="sxs-lookup"><span data-stu-id="9ac06-103">How to: Specify Database Data Types</span></span>

<span data-ttu-id="9ac06-104">Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> T-SQL tablo bildiriminde sütunu tanımlayan tam metni belirtmek için bir öznitelik üzerinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ac06-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="9ac06-105"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>Özelliği yalnızca <xref:System.Data.Linq.DataContext.CreateDatabase%2A> bir veritabanının örneğini oluşturmak için kullanmayı planlıyorsanız belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ac06-105">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="9ac06-106">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> ..</span><span class="sxs-lookup"><span data-stu-id="9ac06-106">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="9ac06-107">T-SQL tablosunda veri türü tanımlamak üzere metin belirtmek için</span><span class="sxs-lookup"><span data-stu-id="9ac06-107">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="9ac06-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9ac06-108">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="9ac06-109"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>Özelliğin değerini T-SQL tarafından kullanılan tam metin olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9ac06-109">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac06-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ac06-110">See also</span></span>

- [<span data-ttu-id="9ac06-111">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="9ac06-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="9ac06-112">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="9ac06-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
