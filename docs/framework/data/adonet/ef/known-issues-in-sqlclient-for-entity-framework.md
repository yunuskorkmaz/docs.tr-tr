---
title: Entity Framework için SqlClient’ta Bilinen Sorunlar
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 8cadb234ffc0f00049edd0c09475031eeec275df
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662265"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Entity Framework için SqlClient’ta Bilinen Sorunlar
Bu bölümde, .NET Framework veri sağlayıcısı için SQL Server (SqlClient) ilgili bilinen sorunlar açıklanmaktadır.  
  
## <a name="trailing-spaces-in-string-functions"></a>Dize işlevleri boşluk  
 SQL Server dize değerleri boşluk yok sayar. Bu nedenle, boşluk dizesi geçirerek öngörülemeyen sonuçlara, hatta hataları neden olabilir.  
  
 Dizenizi boşluk varsa, böylece SQL Server dizeyi kırpmak değil, sonunda boşluk karakterinin düşünmelisiniz. Sondaki boşlukları gerekli değilse, bunlar sorgu işlem hattını geçirilmeden önce bunlar kırpılmış olması gerekir.  
  
## <a name="right-function"></a>RIGHT işlevi  
 Olmayan bir varsa`null` 0, ikinci bağımsız değişkeni olarak geçirilir ve ilk bağımsız değişken olarak geçirilen değer `RIGHT(nvarchar(max)`, 0`)` veya `RIGHT(varchar(max)`, 0`)`, `NULL` değeri yerine döndürüleceği bir `empty` dize.  
  
## <a name="cross-and-outer-apply-operators"></a>Çapraz ve OUTER APPLY işleçleri  
 Çapraz ve OUTER APPLY işleçleri, SQL Server 2005'te sunulmuştur. Bazı durumlarda, CROSS APPLY ve/veya OUTER APPLY işleç içeren bir Transact-SQL deyimini sorgu işlem hattındaki üretebilir. SQL Server'ın SQL Server 2005'ten önceki sürümlerinde de dahil olmak üzere bazı arka uç sağlayıcıları bu işleçler desteklemediğinden, bu arka uç sağlayıcılarında sorgularını yürütülemez.  
  
 Çıkış sorgu CROSS APPLY ve/veya OUTER APPLY işleci varlığını neden bazı tipik senaryolar şunlardır:  
  
- Disk belleği ile ilişkili alt sorgu.  
  
- Bir `AnyElement` bir bağıntılı alt sorguya üzerinden ya da gezinti tarafından üretilen bir koleksiyon üzerinden.  
  
- LINQ öğe Seçici kabul yöntemleri gruplandırma kullanan sorgular.  
  
- İçinde bir CROSS APPLY veya OUTER APPLY açıkça belirtilen bir sorgu  
  
- Bir DEREF olan bir sorgu bir başvuru yapısı oluşturun.  
  
## <a name="skip-operator"></a>SKIP işleci  
 SQL Server 2000'i kullanıyorsanız, anahtar olmayan sütun ORDER BY ile Atla kullanarak hatalı sonuçlar döndürebilir. Anahtar olmayan sütun yinelenen veri varsa birden çok belirtilen sayıda satırı atlanabilir. SQL Server 2000 için Atla nasıl çevrilir nedeniyle budur. Örneğin, aşağıdaki sorguda, beşten fazla satır varsa atlanabilir `E.NonKeyColumn` yinelenen değerlere sahip:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Doğru SQL Server sürümünü hedefleme  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Belirtilen SQL Server sürümünü temel Transact-SQL sorgusu hedefleyen `ProviderManifestToken` depolama modeli (.ssdl) dosyasında şema öğesinin özniteliği. Bu sürüm, bağlı olduğunuz gerçek SQL Server sürümünden farklı olabilir. Örneğin, SQL Server 2005 kullanıyorsanız ancak sizin `ProviderManifestToken` 2008'e ayarlandığında, oluşturulan Transact-SQL sorgusunun sunucuda yürütülemeyebilir. Örneğin, SQL Server 2008'de tanıtılan yeni bir tarih saat türleri kullanan bir sorgu, SQL Server'ın önceki sürümlerinde yürütülmez. SQL Server 2005 kullanıyorsanız ancak sizin `ProviderManifestToken` 2000'e ayarlandığında, oluşturulan Transact-SQL sorgusu daha az iyileştirilebilir veya sorgu desteklenmediğini söyleyen özel durum alabilir. Çapraz ve dış UYGULA işleçleri bölümünde, bu konunun önceki kısımlarında daha fazla bilgi için bkz.  
  
 Veritabanı uyumluluk düzeyini belirli veritabanı davranışları bağlıdır. Varsa, `ProviderManifestToken` 2005'e ayarlandığında ve 2005, SQL Server sürümünüz olduğunu ancak bir veritabanının uyumluluk düzeyini "80" (SQL Server 2000) ayarlandığında, oluşturulan Transact-SQL, SQL Server 2005 hedefliyor olabilir, ancak nedeniyle beklendiği gibi yürütülemeyebilir uyumluluk düzeyi ayarı. Örneğin, bir sütun adı Seçici içinde ORDER BY listesinde bir sütun adı eşleşiyorsa, sipariş bilgileri kaybedilebilir.  
  
## <a name="nested-queries-in-projection"></a>İç içe geçmiş sorgularda projeksiyonu  
 Bir projeksiyon yan tümcesi iç içe geçmiş sorgularda sunucuda Kartezyen ürün sorgulara çevrilmiş. SQL Server dahil olmak üzere bazı arka uç sunucularda, TempDB tablonun oldukça büyük almak bu neden olabilir. Bu sunucu performansını düşürebilir.  
  
 Bir projeksiyon yan tümcesi iç içe bir sorgu örneği verilmiştir:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Sunucu oluşturulan GUID kimlik değerleri  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Destekleyen sunucu tarafından oluşturulan GUID türü kimlik değerleri, ancak sağlayıcı desteklemelidir bir satır takıldıktan sonra sunucu tarafından oluşturulan kimlik değeri döndürüyor. SQL Server 2005 ile başlayarak, bir SQL Server veritabanında sunucu tarafından oluşturulan GUID türü döndürebilir [OUTPUT yan tümcesi](https://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
- [LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
