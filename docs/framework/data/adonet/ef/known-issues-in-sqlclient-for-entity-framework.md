---
title: Entity Framework için SqlClient’ta Bilinen Sorunlar
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 0938c57f48a062082fe973a670eb6a9b9fc4ed3c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395515"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Entity Framework için SqlClient’ta Bilinen Sorunlar
Bu bölümde SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı ilgili bilinen sorunlar açıklanmaktadır.  
  
## <a name="trailing-spaces-in-string-functions"></a>Dize Işlevlerinde sondaki boşluklar  
 SQL Server dize değerlerinde sondaki boşlukları yoksayar. Bu nedenle, dizede sondaki boşlukları geçirmek öngörülemeyen sonuçlara, hatta hatalara neden olabilir.  
  
 Dizeniz sonunda boşluklar olması gerekiyorsa, SQL Server dizeyi kırpmaması için sonuna bir boşluk karakteri eklemeyi göz önünde bulundurmanız gerekir. Sondaki boşluklar gerekmiyorsa, bunlar sorgu işlem hattının geçirilmeden önce kırpılmalıdır.  
  
## <a name="right-function"></a>RIGHT Işlevi  
 @No__t-0 olmayan bir değer ilk bağımsız değişken olarak geçirilmezse ve 0 `RIGHT(nvarchar(max)`, 0 @ no__t-2 veya `RIGHT(varchar(max)`, 0 @ no__t-4 ' e ikinci bir bağımsız değişken olarak geçirilirse, @no__t 6 dizesi yerine bir `NULL` değeri döndürülür.  
  
## <a name="cross-and-outer-apply-operators"></a>ÇAPRAZ ve dış uygulama Işleçleri  
 SQL Server 2005 ' de çapraz ve dış uygulama işleçleri tanıtılmıştı. Bazı durumlarda, sorgu işlem hattı, çapraz uygulama ve/veya dış uygulama işleçlerini içeren bir Transact-SQL ifadesini oluşturabilir. SQL Server 2005 ' den önceki SQL Server sürümleri de dahil olmak üzere bazı arka uç sağlayıcılar bu işleçleri desteklemediğinden, bu arka uç sağlayıcılarında bu sorgular yürütülemez.  
  
 Aşağıdakiler, çıkış sorgusundaki çapraz uygulama ve/veya dış uygulama işleçleri varlığına neden olabilecek bazı tipik senaryolardır:  
  
- Sayfalama ile bağıntılı alt sorgu.  
  
- Bağıntılı bir alt sorgu üzerinde veya gezinti tarafından üretilen bir koleksiyon üzerinde `AnyElement`.  
  
- Öğe seçiciyi kabul eden gruplandırma yöntemlerini kullanan LINQ sorguları.  
  
- Bir çapraz uygulama veya dış uygulama uygulanan bir sorgu açıkça belirtilir  
  
- Bir başvuru yapısı üzerinde DEREF yapısına sahip bir sorgu.  
  
## <a name="skip-operator"></a>SKIP Işleci  
 SQL Server 2000 kullanıyorsanız, anahtar olmayan sütunlarda SıRALAMA ile atla kullanılması yanlış sonuçlar döndürebilir. Anahtar olmayan sütunda Yinelenen veriler varsa, belirtilen sayıda satırdan daha fazla satır atlanmayabilir. Bunun nedeni, atlama 'nin SQL Server 2000 ' de çevrilmesine neden olur. Örneğin, aşağıdaki sorguda, `E.NonKeyColumn` yinelenen değerlere sahipse, beş satırdan fazla satır atlanabilir.  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Doğru SQL Server sürümünü hedefleme  
 Entity Framework, Transact-SQL sorgusunu, depolama modeli (. ssdl) dosyasındaki şema öğesinin `ProviderManifestToken` özniteliğinde belirtilen SQL Server sürümüne göre hedefler. Bu sürüm, bağlandığınız gerçek SQL Server sürümüne göre farklılık gösterebilir. Örneğin, SQL Server 2005 kullanıyorsanız, ancak `ProviderManifestToken` öznitemeniz 2008 olarak ayarlandıysa, oluşturulan Transact-SQL sorgusu sunucuda yürütülemeyebilir. Örneğin, SQL Server 2008 ' de tanıtılan yeni tarih saat türlerini kullanan bir sorgu, SQL Server önceki sürümlerinde yürütülmez. SQL Server 2005 kullanıyorsanız, ancak `ProviderManifestToken` öznitebir değer 2000 olarak ayarlandıysa, oluşturulan Transact-SQL sorgusu daha az iyileştirilebilir veya sorgunun desteklenmediğini belirten bir özel durum elde edebilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer aldığı çapraz ve dış uygulama Işleçleri bölümüne bakın.  
  
 Belirli veritabanı davranışları, veritabanı için ayarlanan uyumluluk düzeyine bağlıdır. @No__t-0 öznitelemeniz 2005 olarak ayarlanmışsa ve SQL Server sürümünüz 2005 ise, ancak bir veritabanının uyumluluk düzeyi "80" (SQL Server 2000) olarak ayarlanırsa, oluşturulan Transact-SQL SQL Server 2005 hedefleyecek, ancak bu durum nedeniyle beklendiği gibi yürütülemeyebilir Uyumluluk düzeyi ayarı. Örneğin, ORDER BY listesindeki bir sütun adı seçicideki bir sütun adıyla eşleşiyorsa sıralama bilgilerini kaybedebilirsiniz.  
  
## <a name="nested-queries-in-projection"></a>Yansıtmada iç içe geçmiş sorgular  
 Bir projeksiyon yan tümcesindeki iç içe geçmiş sorgular, sunucuda Kartezyen ürün sorgularına çevrilebilir. SQL Server dahil bazı arka uç sunucularında, bu, TempDB tablosunun çok büyük sürmesine neden olabilir. Bu, sunucu performansını düşürebilir.  
  
 Aşağıda, bir izdüşüm yan tümcesindeki iç içe sorgu örneği verilmiştir:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Sunucu tarafından oluşturulan GUID kimlik değerleri  
 Entity Framework, sunucu tarafından üretilen GUID türü kimlik değerlerini destekler, ancak sağlayıcının bir satır eklendikten sonra sunucu tarafından oluşturulan kimlik değerini döndürmeyi desteklemesi gerekir. SQL Server 2005 ' den başlayarak, [Çıkış yan tümcesi](https://go.microsoft.com/fwlink/?LinkId=169400) aracılığıyla bir SQL Server veritabanında sunucu tarafından oluşturulan GUID türünü döndürebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için SqlClient](sqlclient-for-the-entity-framework.md)
- [LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler](./language-reference/known-issues-and-considerations-in-linq-to-entities.md)
