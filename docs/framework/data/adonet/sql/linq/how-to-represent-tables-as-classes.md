---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: tabloları sınıf olarak temsil etme'
title: 'Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 9ec5b7309d7d10eaa6e4da6cd6fe4b1d03df1dd9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723588"
---
# <a name="how-to-represent-tables-as-classes"></a>Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme

Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> sınıfı bir veritabanı tablosuyla ilişkili bir varlık sınıfı olarak belirlemek için özniteliğini kullanın.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Bir sınıfı bir veritabanı tablosuyla eşlemek için  
  
- <xref:System.Data.Linq.Mapping.TableAttribute>Özniteliği sınıf bildirimine ekleyin.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `Customer` sınıfını veritabanı tablosuyla ilişkili bir varlık sınıfı olarak oluşturur `Customers` .  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>Ad çıkarsancan özelliğini belirtmeniz gerekmez. Bir ad belirtmezseniz, ad, özellik veya alanla aynı ada sahip olacak şekilde adlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
