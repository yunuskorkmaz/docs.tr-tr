---
title: 'Nasıl yapılır: Veritabanı Adları Belirtme'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a43a7ac541adb984eeb8bb88b7ab96db86baf26c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335283"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="ee963-102">Nasıl yapılır: Veritabanı Adları Belirtme</span><span class="sxs-lookup"><span data-stu-id="ee963-102">How to: Specify Database Names</span></span>
<span data-ttu-id="ee963-103">Kullanım <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özelliği bir <xref:System.Data.Linq.Mapping.DatabaseAttribute> bir ad tarafından bağlantı sağlanamadığında bir veritabanının adını belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ee963-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="ee963-104">Kod örnekleri için bkz. <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee963-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="ee963-105">Veritabanının adını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ee963-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="ee963-106">Ekleme <xref:System.Data.Linq.Mapping.DatabaseAttribute> sınıf bildiriminin veritabanı için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ee963-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="ee963-107">Ekleme <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özelliğini <xref:System.Data.Linq.Mapping.DatabaseAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ee963-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="ee963-108">Ayarlama <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özellik değeri, belirtmek istediğiniz adı.</span><span class="sxs-lookup"><span data-stu-id="ee963-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee963-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee963-109">See also</span></span>

- [<span data-ttu-id="ee963-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="ee963-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ee963-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ee963-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
