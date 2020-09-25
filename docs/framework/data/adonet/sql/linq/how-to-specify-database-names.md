---
title: 'Nasıl yapılır: Veritabanı Adları Belirtme'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 82cb3f8f31af433b0299b4fec742b548d61921e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197163"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="d1380-102">Nasıl yapılır: Veritabanı Adları Belirtme</span><span class="sxs-lookup"><span data-stu-id="d1380-102">How to: Specify Database Names</span></span>

<span data-ttu-id="d1380-103"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> <xref:System.Data.Linq.Mapping.DatabaseAttribute> Bağlantı tarafından bir ad sağlanmadığında bir veritabanının adını belirtmek için bir öznitelik üzerinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1380-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="d1380-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> ..</span><span class="sxs-lookup"><span data-stu-id="d1380-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="d1380-105">Veritabanının adını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="d1380-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="d1380-106"><xref:System.Data.Linq.Mapping.DatabaseAttribute>Özniteliğini veritabanına yönelik sınıf bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1380-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="d1380-107"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>Özelliği <xref:System.Data.Linq.Mapping.DatabaseAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1380-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="d1380-108"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>Özellik değerini, belirtmek istediğiniz ad olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d1380-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1380-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1380-109">See also</span></span>

- [<span data-ttu-id="d1380-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="d1380-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d1380-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d1380-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
