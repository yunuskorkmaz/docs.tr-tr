---
title: GUID ve uniqueidentifier Değerlerini Karşılaştırma
description: Benzersiz tanımlayıcı veri türü tarafından temsil edilen SQL Server için .NET Framework Veri Sağlayıcısı GUID değerlerini oluşturmayı ve karşılaştırmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 245b7246712822043d302c43a765c29ac2090e00
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286513"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>GUID ve uniqueidentifier Değerlerini Karşılaştırma
SQL Server genel benzersiz tanımlayıcı (GUID) veri türü, `uniqueidentifier` 16 baytlık ikili değer depolayan veri türü tarafından temsil edilir. GUID, ikili bir sayıdır ve ana kullanımı, birçok sitede çok sayıda bilgisayarı olan bir ağda benzersiz olması gereken bir tanımlayıcı olarak kullanılır. GUID 'Ler Transact-SQL NEıD işlevi çağırarak oluşturulabilir ve dünyanın tamamında benzersiz olması garanti edilir. Daha fazla bilgi için bkz. [uniqueidentifier (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql).  
  
## <a name="working-with-sqlguid-values"></a>Sqlguıd değerleriyle çalışma  
 GUID değerleri uzun ve belirsiz olduğundan, kullanıcılar için anlamlı değildir. Rastgele oluşturulan GUID 'Ler anahtar değerleri için kullanılırsa ve çok sayıda satır eklerseniz dizinlerinizle rastgele g/ç elde edersiniz ve bu da performansı olumsuz etkileyebilir. Diğer veri türleriyle karşılaştırıldığında, GUID 'Ler de nispeten büyük. Genel olarak, yalnızca başka bir veri türü uygun olmayan dar senaryolar için GUID 'Leri kullanmanızı öneririz.  
  
### <a name="comparing-guid-values"></a>GUID değerlerini karşılaştırma  
 Karşılaştırma işleçleri, değerlerle birlikte kullanılabilir `uniqueidentifier` . Ancak sıralama, iki değerin bit desenleri karşılaştırılmasıyla uygulanmaz. Bir değere karşı izin verilen tek işlemler `uniqueidentifier` karşılaştırmalar (=,  <>, \<, > , \<=, > =) ve null olup OLMADıĞıNı denetler (null ve null değildir). Başka aritmetik işleçlere izin verilmez.  
  
 Her ikisi de <xref:System.Guid> <xref:System.Data.SqlTypes.SqlGuid> `CompareTo` farklı GUID değerlerini karşılaştırmak için bir yönteme sahiptir. Ancak, `System.Guid.CompareTo` ve `SqlTypes.SqlGuid.CompareTo` farklı şekilde uygulanır. <xref:System.Data.SqlTypes.SqlGuid>`CompareTo`, bir değerin son altı baytında SQL Server davranışı kullanılarak uygulanır. <xref:System.Guid>Tüm 16 baytları değerlendirir. Aşağıdaki örnekte bu davranış farkı gösterilmektedir. Kodun ilk bölümünde sıralanmamış <xref:System.Guid> değerler görüntülenir ve kodun ikinci bölümünde sıralanmış <xref:System.Guid> değerler gösterilir. Üçüncü bölümde sıralanan <xref:System.Data.SqlTypes.SqlGuid> değerler gösterilir. Çıktı, kod listesinin altında görüntülenir.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Bu örnek aşağıdaki sonuçları üretir.  
  
```output  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türleri ve ADO.NET](sql-server-data-types.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
