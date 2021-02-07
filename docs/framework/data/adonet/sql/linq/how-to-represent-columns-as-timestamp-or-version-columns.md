---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sütunları zaman damgası veya sürüm sütunları olarak temsil etme'
title: 'Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 042e6a62c66b3f1ef522453157560e5e4c0f7de6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712512"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> Veritabanı zaman damgalarını veya sürüm numaralarını tutan bir veritabanı sütununu temsil eden bir alanı veya özelliği belirlemek için özniteliğinin özelliğini kullanın.  
  
 Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> ..  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>Bir alan veya özelliği bir zaman damgasını veya sürüm sütununu temsil edecek şekilde belirlemek için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>Özellik değerini olarak ayarlayın `true` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
