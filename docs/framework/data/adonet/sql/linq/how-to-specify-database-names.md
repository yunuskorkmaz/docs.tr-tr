---
title: 'Nasıl yapılır: Veritabanı Adları Belirtme'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 0daf754edf624410e0ea725acd6c266ccb7828dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781582"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="74757-102">Nasıl yapılır: Veritabanı Adları Belirtme</span><span class="sxs-lookup"><span data-stu-id="74757-102">How to: Specify Database Names</span></span>
<span data-ttu-id="74757-103">Bağlantı tarafından bir ad sağlanmadığında bir veritabanının adını belirtmek için bir <xref:System.Data.Linq.Mapping.DatabaseAttribute> öznitelik üzerinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A></span><span class="sxs-lookup"><span data-stu-id="74757-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="74757-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="74757-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="74757-105">Veritabanının adını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="74757-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="74757-106"><xref:System.Data.Linq.Mapping.DatabaseAttribute> Özniteliğini veritabanına yönelik sınıf bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74757-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="74757-107"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> Özelliği<xref:System.Data.Linq.Mapping.DatabaseAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74757-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="74757-108"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> Özellik değerini, belirtmek istediğiniz ad olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="74757-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74757-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74757-109">See also</span></span>

- [<span data-ttu-id="74757-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="74757-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="74757-111">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="74757-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
