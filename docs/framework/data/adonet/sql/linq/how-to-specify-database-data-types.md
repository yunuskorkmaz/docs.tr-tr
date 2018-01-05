---
title: "Nasıl yapılır: veritabanı veri türlerini belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 60f07a629c981eb0ad72f7c3e2d8537d5ca77515
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="a673c-102">Nasıl yapılır: veritabanı veri türlerini belirtme</span><span class="sxs-lookup"><span data-stu-id="a673c-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="a673c-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> özelliği bir <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği bir T-SQL tablosu bildiriminde sütunu tanımlayan tam metni belirtin.</span><span class="sxs-lookup"><span data-stu-id="a673c-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="a673c-104">Belirtmeniz gerekir <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> yalnızca kullanmayı planlıyorsanız özelliği <xref:System.Data.Linq.DataContext.CreateDatabase%2A> veritabanı örneği oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="a673c-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="a673c-105">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="a673c-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="a673c-106">Bir veri türü bir T-SQL tablosuna tanımlamak için metin belirtmek için</span><span class="sxs-lookup"><span data-stu-id="a673c-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1.  <span data-ttu-id="a673c-107">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a673c-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="a673c-108">Değerini <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> T-SQL tarafından kullanılan tam metin özelliğine.</span><span class="sxs-lookup"><span data-stu-id="a673c-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a673c-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a673c-109">See Also</span></span>  
 [<span data-ttu-id="a673c-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="a673c-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="a673c-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a673c-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
