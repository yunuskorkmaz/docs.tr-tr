---
title: 'Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793493"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme
Veritabanı zaman damgalarını veya sürüm <xref:System.Data.Linq.Mapping.ColumnAttribute> numaralarını tutan bir veritabanı sütununu temsil eden bir alanı veya özelliği belirlemek için özniteliğinin özelliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>Bir alan veya özelliği bir zaman damgasını veya sürüm sütununu temsil edecek şekilde belirlemek için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. Özellik değerini olarak `true`ayarlayın. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Eşzamanlılık çakışmaları için hangi üyelerin test edildiğini belirtin](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
