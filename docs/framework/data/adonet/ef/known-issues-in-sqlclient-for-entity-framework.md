---
title: Entity Framework SqlClient bilinen sorunlar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3fb62e266ee6f0ca7957667d7c41fbd90dd34d32
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Entity Framework SqlClient bilinen sorunlar
Bu bölümde, .NET Framework veri sağlayıcısı için SQL Server (SqlClient) ilgili bilinen sorunlar açıklanmaktadır.  
  
## <a name="trailing-spaces-in-string-functions"></a>Dize işlevleri boşluk  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]dize değerlerini boşluk yok sayar. Bu nedenle, dize boşluk geçirme öngörülemeyen sonuçlara, hatta hataları neden olabilir.  
  
 Sonunda boşluk dizenizi sahip olmanız, en sonda boşluk karakteri ekleme düşünmelisiniz böylece [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] dize kırpma değil. Sondaki boşlukları gerekli değilse, sorgu ardışık düzen geçirilmeden önce bunlar kırpılmış olması.  
  
## <a name="right-function"></a>RIGHT işlevi  
 Olmayan bir varsa`null` ilk bağımsız değişken olarak geçirilen değer ve 0, ikinci bağımsız değişkeni olarak geçirilir `RIGHT(nvarchar(max)`, 0`)` veya `RIGHT(varchar(max)`, 0`)`, `NULL` değeri yerine döndürülecek bir `empty` dize.  
  
## <a name="cross-and-outer-apply-operators"></a>Çapraz ve OUTER APPLY işleçleri  
 Çapraz ve OUTER APPLY işleçleri sunuldu [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]. Bazı durumlarda çapraz uygulamak ve/veya OUTER APPLY işleçleri içeren bir Transact-SQL deyimini sorgu ardışık düzen üretebilir. Çünkü sürümleri dahil olmak üzere bazı arka uç sağlayıcıları [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] öncesi [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], bu işleçlere desteklemez, bu tür sorgular bu arka uç sağlayıcılarının yürütülemez.  
  
 Çıktı sorgusunda ARASI uygulamak ve/veya OUTER APPLY işleçleri varlığını neden bazı tipik senaryolar şunlardır:  
  
-   Disk belleği ile ilişkili alt sorgu.  
  
-   Bir `AnyElement` ilişkili bir alt sorgu üzerinden ya da gezinti tarafından üretilen bir koleksiyon üzerinden.  
  
-   LINQ bir öğe Seçicisi kabul yöntemleri gruplandırma kullanan sorgular.  
  
-   İçinde bir çapraz veya bir dış UYGULAMALISINIZ açıkça belirtilen bir sorgu  
  
-   Bir DEREF olan bir sorgu REF yapısı oluşturun.  
  
## <a name="skip-operator"></a>Atla işleci  
 Kullanıyorsanız [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)], anahtar olmayan sütunlarda ORDER BY ile Atla kullanarak hatalı sonuçlar döndürebilir. Anahtar olmayan sütun yinelenen verileri varsa satır belirtilen sayıdan daha fazla atlanabilir. Nasıl Atla için çevrilir nedeniyle budur [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]. Örneğin, aşağıdaki sorguda beşten fazla satır, atlanabilir `E.NonKeyColumn` yinelenen değerleri içeriyor:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Doğru SQL Server sürümünü hedefleme  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Hedefleri [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] belirtilen SQL Server sürümünü temel sorgu `ProviderManifestToken` depolama modeli (.ssdl) dosyasındaki şema öğesinin özniteliği. Bu sürüm, bağlı gerçek SQL Server sürümünden farklı olabilir. Örneğin, SQL Server 2005 kullanıyorsanız, ancak, `ProviderManifestToken` özniteliği 2008'e, oluşturulan ayarlanmış [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] sorgu sunucuda değil yürütme. Örneğin, SQL Server 2008'de sunulan yeni bir tarih saat türleri kullanan bir sorgu SQL Server'ın önceki sürümlerinde çalıştırmaz. SQL Server 2005 kullanıyorsanız, ancak, `ProviderManifestToken` özniteliği 2000, oluşturulan ayarlanmış [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] sorgu daha az en iyi duruma getirilmiş veya sorgu desteklenmiyor bildiren bir özel durum alabilirsiniz olabilir. Daha fazla bilgi için çapraz ve OUTER APPLY işleçleri bölümünde, bu konunun önceki kısımlarında bakın.  
  
 Veritabanı uyumluluk düzeyi belirli veritabanı davranışları bağlıdır. Varsa, `ProviderManifestToken` özniteliğini 2005'e ayarlayın ve 2005, SQL Server sürümüdür, ancak bir veritabanı uyumluluk düzeyi "80" (SQL Server 2000) oluşturulan ayarlamak [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SQL Server 2005 hedefleme ancak nedeniyle beklendiği gibi yürütebilir değil uyumluluk düzeyi ayarı. Örneğin, bir sütun adı ORDER BY listesinde Seçici içinde bir sütun adı eşleşirse, sipariş bilgilerini kaybedebilirsiniz.  
  
## <a name="nested-queries-in-projection"></a>İç içe yerleştirilmiş sorguda projeksiyon  
 Projeksiyon yan tümcesi iç içe geçmiş sorguları Kartezyen ürün sorguları sunucuda içine çevrilmiş. SQL Server dahil olmak üzere bazı arka uç sunucularda, bu oldukça büyük almak TempDB tablo neden olabilir. Bu sunucu performansını düşürebilir.  
  
 İç içe bir sorgu projeksiyon yan tümcesindeki bir örneği verilmiştir:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Sunucu tarafından üretilen GUID kimlik değerleri  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Destekleyen sunucu tarafından üretilen GUID türü kimlik değerleri, ancak sağlayıcı desteklemelidir bir satır girildikten sonra sunucu tarafından üretilen kimlik değeri döndürüyor. İle başlayarak [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2005, sunucu tarafından üretilen GUID türünde döndürebilir bir [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] aracılığıyla veritabanı [OUTPUT yan tümcesi](http://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)  
 [LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
