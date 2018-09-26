---
title: Karşılaştırma GUID ve uniqueidentifier değerlerini
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 7d982b73332a2629ccd32c409e0de6fe1ce6eb98
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087258"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Karşılaştırma GUID ve uniqueidentifier değerlerini
SQL Server genel benzersiz tanıtıcısı (GUID) veri türü tarafından temsil edilen `uniqueidentifier` veri türü, 16 baytlık bir ikili değeri depolar. Bir ikili sayı bir GUID'dir ve onun ana birçok sitelerde çok sayıda bilgisayar olan bir ağa benzersiz bir tanımlayıcı olarak kullanılır. GUID'ler Transact-SQL NEWID işlevi çağrılarak oluşturulan ve dünya genelinde benzersiz olması garanti edilmez. Daha fazla bilgi için [benzersiz tanımlayıcı (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql).  
  
## <a name="working-with-sqlguid-values"></a>SqlGuid değerleri ile çalışma  
 GUID değerleri, uzun ve belirsiz olduğundan, bunlar kullanıcılar için anlamlı değildir. Rastgele oluşturulan Guıd'lar anahtar değerler için kullanılır ve çok sayıda satır ekleme, rastgele g/ç performansı olumsuz yönde etkileyebilir dizinlerinizi alın. Ayrıca diğer veri türlerine karşılaştırıldığında oldukça büyük guıd'lerdir. Genel olarak hangi diğer veri türü uygun yalnızca çok dar senaryolar için GUID'leri kullanmanızı öneririz.  
  
### <a name="comparing-guid-values"></a>GUID değerleri karşılaştırma  
 Karşılaştırma işleçleri ile kullanılabilir `uniqueidentifier` değerleri. Ancak, sıralama iki değerlerinin bit düzenleri karşılaştırarak uygulanmadı. Göre izin verilen işlemler bir `uniqueidentifier` değerlerdir karşılaştırmaları (=, <>, \<, >, \<=, > =) ve NULL (IS NULL ve IS NOT NULL) denetleniyor. Hiçbir aritmetik işlece izin verilir.  
  
 Her ikisi de <xref:System.Guid> ve <xref:System.Data.SqlTypes.SqlGuid> sahip bir `CompareTo` farklı GUID değerleri karşılaştırmak için yöntemi. Ancak, `System.Guid.CompareTo` ve `SqlTypes.SqlGuid.CompareTo` farklı uygulanır. <xref:System.Data.SqlTypes.SqlGuid> uygulayan `CompareTo` SQL Server davranışını kullanarak bir değerin son altı bayt cinsinden en önemli. <xref:System.Guid> tüm 16 bayt değerlendirir. Aşağıdaki örnek, bu davranış farklılık gösterir. Kod görüntüler ilk bölümünü sıralanmamış <xref:System.Guid> değerleri ve ikinci kod bölümünü gösterir sıralanmış <xref:System.Guid> değerleri. Üçüncü bölüm sıralanmış gösterir <xref:System.Data.SqlTypes.SqlGuid> değerleri. Çıkış kodu listenin altında görüntülenir.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Bu örnek, aşağıdaki sonuçları üretir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  

[SQL Server Veri Türleri ve ADO.NET](sql-server-data-types.md)  
[ADO.NET’e Genel Bakış](../ado-net-overview.md)  
