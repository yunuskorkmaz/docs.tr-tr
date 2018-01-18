---
title: "Nasıl yapılır: temsil eden sınıflar olarak tabloları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 30bdb3334b574053595565e94993563959f49694
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-tables-as-classes"></a>Nasıl yapılır: temsil eden sınıflar olarak tabloları
Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği bir sınıf bir veritabanı tablosu ile ilişkilendirilmiş bir varlık sınıfı olarak belirleyin.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Bir sınıf bir veritabanı tablosuna eşlemek için  
  
-   Ekleme <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği sınıf bildirimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kurar `Customer` sınıf ile ilişkili bir varlık sınıfı olarak `Customers` veritabanı tablosu.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Belirtmek zorunda değilsiniz <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> adı çıkarsanabileceği varsa özelliği. Bir ad belirtmezseniz, adı, özellik veya alan aynı adı olduğu kabul edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
