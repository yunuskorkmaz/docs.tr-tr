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
# <a name="how-to-specify-database-names"></a>Nasıl yapılır: Veritabanı Adları Belirtme
Bağlantı tarafından bir ad sağlanmadığında bir veritabanının adını belirtmek için bir <xref:System.Data.Linq.Mapping.DatabaseAttribute> öznitelik üzerinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>  
  
 Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### <a name="to-specify-the-name-of-the-database"></a>Veritabanının adını belirtmek için  
  
1. <xref:System.Data.Linq.Mapping.DatabaseAttribute> Özniteliğini veritabanına yönelik sınıf bildirimine ekleyin.  
  
2. <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> Özelliği<xref:System.Data.Linq.Mapping.DatabaseAttribute> özniteliğine ekleyin.  
  
3. <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> Özellik değerini, belirtmek istediğiniz ad olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
