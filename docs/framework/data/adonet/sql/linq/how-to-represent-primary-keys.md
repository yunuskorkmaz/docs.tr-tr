---
title: 'Nasıl yapılır: Birincil Anahtarları Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 5df82292f000d7f5e61cab699237b86de30bda70
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793436"
---
# <a name="how-to-represent-primary-keys"></a>Nasıl yapılır: Birincil Anahtarları Temsil Etme
Bir veritabanı sütunu için birincil <xref:System.Data.Linq.Mapping.ColumnAttribute> anahtarı temsil etmek üzere bir özellik veya alan belirlemek için özniteliğinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], hesaplanan sütunları birincil anahtar olarak desteklemez.  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>Bir özelliği veya alanı birincil anahtar olarak belirlemek için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. Değeri olarak `true`belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
