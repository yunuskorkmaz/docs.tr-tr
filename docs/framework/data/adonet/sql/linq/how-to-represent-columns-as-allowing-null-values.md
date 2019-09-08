---
title: 'Nasıl yapılır: Sütunları Null Değerlere İzin Verecek Şekilde Temsil Etme'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 00a837467010c2d8a9f0ca16d6aba2fc5f4c973f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781815"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a>Nasıl yapılır: Sütunları Null Değerlere İzin Verecek Şekilde Temsil Etme
İlişkili veritabanı sütununun null değerleri <xref:System.Data.Linq.Mapping.ColumnAttribute> tutabilmek için özniteliğinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a>Bir sütunu null değerlere izin verecek şekilde belirlemek için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. Özellik değerini olarak `true`ayarlayın. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
