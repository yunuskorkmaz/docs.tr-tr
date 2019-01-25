---
title: 'Nasıl yapılır: Veritabanı adları belirtme'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a1198a294cd4921728919981bae213c0ee891da6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556391"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="d3e03-102">Nasıl yapılır: Veritabanı adları belirtme</span><span class="sxs-lookup"><span data-stu-id="d3e03-102">How to: Specify Database Names</span></span>
<span data-ttu-id="d3e03-103">Kullanım <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özelliği bir <xref:System.Data.Linq.Mapping.DatabaseAttribute> bir ad tarafından bağlantı sağlanamadığında bir veritabanının adını belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d3e03-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="d3e03-104">Kod örnekleri için bkz. <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3e03-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="d3e03-105">Veritabanının adını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="d3e03-105">To specify the name of the database</span></span>  
  
1.  <span data-ttu-id="d3e03-106">Ekleme <xref:System.Data.Linq.Mapping.DatabaseAttribute> sınıf bildiriminin veritabanı için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d3e03-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2.  <span data-ttu-id="d3e03-107">Ekleme <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özelliğini <xref:System.Data.Linq.Mapping.DatabaseAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d3e03-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="d3e03-108">Ayarlama <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özellik değeri, belirtmek istediğiniz adı.</span><span class="sxs-lookup"><span data-stu-id="d3e03-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e03-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3e03-109">See also</span></span>
- [<span data-ttu-id="d3e03-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="d3e03-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d3e03-111">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d3e03-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
