---
title: "Karşılaştırma GUID ve uniqueidentifier değerleri"
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
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0a61556859acec53315147149d67ff4cef493b68
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Karşılaştırma GUID ve uniqueidentifier değerleri
SQL Server'ın genel benzersiz tanıtıcısı (GUID) veri türü tarafından temsil edilen `uniqueidentifier` 16 bayt ikili değer depolayan veri türü. İkili bir sayı GUID'dir ve kendi ana birçok sitelerde çok sayıda bilgisayar olan bir ağda benzersiz bir tanımlayıcı olarak kullanılır. GUID'ler Transact-SQL NEWID işlevini çağırarak oluşturulabilir ve dünyanın her yerinde benzersiz olması garanti edilmez. Daha fazla bilgi için "Kullanma uniqueidentifier veri" SQL Server Books Online'a bakın.  
  
## <a name="working-with-sqlguid-values"></a>SqlGuid değerlerle çalışma  
 GUID değerleri uzun ve belirsiz olduğundan, bunlar kullanıcılar için anlamlı değildir. Rastgele oluşturulmuş GUID'ler anahtar değerleri için kullanılır ve çok satır ekleme, rastgele g/ç performansı olumsuz yönde etkileyebilir dizinlerinizi alın. Ayrıca diğer veri türlerine karşılaştırıldığında görece büyük guıd'lerdir. Genel olarak hangi diğer için hiçbir veri türü uygun yalnızca çok dar senaryolar için GUID'leri kullanmanızı öneririz.  
  
### <a name="comparing-guid-values"></a>GUID değerleri karşılaştırma  
 Karşılaştırma işleçleri ile kullanılabilir `uniqueidentifier` değerleri. Ancak, sıralama iki değer bit desenlerini karşılaştırarak uygulanmadı. Karşı izin verilen işlemler bir `uniqueidentifier` değeri olan karşılaştırmaları (=, <>, \<, >, \<=, > =) ve NULL (IS NULL ve IS NOT NULL) denetleniyor. Başka hiçbir aritmetik işlece izin verilir.  
  
 Her ikisi de <xref:System.Guid> ve <xref:System.Data.SqlTypes.SqlGuid> sahip bir `CompareTo` farklı GUID değerleri karşılaştırmak için yöntem. Ancak, `System.Guid.CompareTo` ve `SqlTypes.SqlGuid.CompareTo` farklı uygulanır. <xref:System.Data.SqlTypes.SqlGuid>uygulayan `CompareTo` bir değerin son altı bayt olarak SQL Server davranışını kullanarak en önemli. <xref:System.Guid>tüm 16 bayt değerlendirir. Aşağıdaki örnek, bu davranış farklılık gösterir. Kod görüntüler ilk bölümü sıralanmamış <xref:System.Guid> değerleri ve kod ikinci bölümü gösterir sıralanmış <xref:System.Guid> değerleri. Üçüncü bölüm sıralanmış gösterir <xref:System.Data.SqlTypes.SqlGuid> değerleri. Çıkış kodu listenin altında görüntülenir.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Bu örnekte aşağıdaki sonuçları verir.  
  
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
 [SQL Server Veri Türleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
