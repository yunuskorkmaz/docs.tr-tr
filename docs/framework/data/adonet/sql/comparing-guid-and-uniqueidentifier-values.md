---
title: GUID ve uniqueidentifier Değerlerini Karşılaştırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 18f7ad8f6ef9cdf726bdf606ab108e2c5140aed7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040458"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>GUID ve uniqueidentifier Değerlerini Karşılaştırma
SQL Server genel benzersiz tanımlayıcı (GUID) veri türü, 16 baytlık ikili değer depolayan `uniqueidentifier` veri türü tarafından temsil edilir. GUID, ikili bir sayıdır ve ana kullanımı, birçok sitede çok sayıda bilgisayarı olan bir ağda benzersiz olması gereken bir tanımlayıcı olarak kullanılır. GUID 'Ler Transact-SQL NEıD işlevi çağırarak oluşturulabilir ve dünyanın tamamında benzersiz olması garanti edilir. Daha fazla bilgi için bkz. [uniqueidentifier (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql).  
  
## <a name="working-with-sqlguid-values"></a>Sqlguıd değerleriyle çalışma  
 GUID değerleri uzun ve belirsiz olduğundan, kullanıcılar için anlamlı değildir. Rastgele oluşturulan GUID 'Ler anahtar değerleri için kullanılırsa ve çok sayıda satır eklerseniz dizinlerinizle rastgele g/ç elde edersiniz ve bu da performansı olumsuz etkileyebilir. Diğer veri türleriyle karşılaştırıldığında, GUID 'Ler de nispeten büyük. Genel olarak, yalnızca başka bir veri türü uygun olmayan dar senaryolar için GUID 'Leri kullanmanızı öneririz.  
  
### <a name="comparing-guid-values"></a>GUID değerlerini karşılaştırma  
 Karşılaştırma işleçleri, `uniqueidentifier` değerleriyle birlikte kullanılabilir. Ancak sıralama, iki değerin bit desenleri karşılaştırılmasıyla uygulanmaz. `uniqueidentifier` bir değere karşı izin verilen tek işlemler karşılaştırmalar (=, < >, \<, >, \<=, > =) ve NULL olup olmadığını denetler (NULL ve NULL değildir). Başka aritmetik işleçlere izin verilmez.  
  
 Hem <xref:System.Guid> hem de <xref:System.Data.SqlTypes.SqlGuid>, farklı GUID değerlerini karşılaştırmak için bir `CompareTo` metoduna sahiptir. Ancak, `System.Guid.CompareTo` ve `SqlTypes.SqlGuid.CompareTo` farklı şekilde uygulanır. <xref:System.Data.SqlTypes.SqlGuid>, bir değerin son altı baytında en önemli olan SQL Server davranışını kullanarak `CompareTo` uygular. <xref:System.Guid> tüm 16 baytları değerlendirir. Aşağıdaki örnekte bu davranış farkı gösterilmektedir. Kodun ilk bölümünde sıralanmamış <xref:System.Guid> değerleri görüntülenir ve kodun ikinci bölümü sıralanmış <xref:System.Guid> değerlerini gösterir. Üçüncü bölümde sıralanmış <xref:System.Data.SqlTypes.SqlGuid> değerleri gösterilir. Çıktı, kod listesinin altında görüntülenir.  
  
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
