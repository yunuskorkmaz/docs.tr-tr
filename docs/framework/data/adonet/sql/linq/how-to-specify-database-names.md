---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veritabanı adlarını belirtme'
title: 'Nasıl yapılır: Veritabanı Adları Belirtme'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 231c78830e009ed3414609eb6dbe05c3745f3e05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785893"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="c01d2-103">Nasıl yapılır: Veritabanı Adları Belirtme</span><span class="sxs-lookup"><span data-stu-id="c01d2-103">How to: Specify Database Names</span></span>

<span data-ttu-id="c01d2-104"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> <xref:System.Data.Linq.Mapping.DatabaseAttribute> Bağlantı tarafından bir ad sağlanmadığında bir veritabanının adını belirtmek için bir öznitelik üzerinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c01d2-104">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="c01d2-105">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> ..</span><span class="sxs-lookup"><span data-stu-id="c01d2-105">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="c01d2-106">Veritabanının adını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c01d2-106">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="c01d2-107"><xref:System.Data.Linq.Mapping.DatabaseAttribute>Özniteliğini veritabanına yönelik sınıf bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c01d2-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="c01d2-108"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>Özelliği <xref:System.Data.Linq.Mapping.DatabaseAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c01d2-108">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="c01d2-109"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>Özellik değerini, belirtmek istediğiniz ad olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c01d2-109">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c01d2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c01d2-110">See also</span></span>

- [<span data-ttu-id="c01d2-111">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="c01d2-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="c01d2-112">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c01d2-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
