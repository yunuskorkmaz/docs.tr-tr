---
title: Entity Framework için EntityClient Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: cd02f2ede37ef3518071b5d4c79cdffe2e2f1b5d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542600"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Entity Framework için EntityClient Sağlayıcısı
EntityClient sağlayıcısı, kavramsal modelde açıklanan verilere erişmek için Entity Framework uygulamalar tarafından kullanılan bir veri sağlayıcısıdır. Kavramsal modeller hakkında daha fazla bilgi için bkz. [modelleme ve eşleme](modeling-and-mapping.md). EntityClient, veri kaynağına erişmek için diğer .NET Framework veri sağlayıcılarını kullanır. Örneğin, EntityClient SQL Server veritabanına erişirken SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı kullanır. SqlClient sağlayıcısı hakkında daha fazla bilgi için bkz. [sqlclient Entity Framework](sqlclient-for-the-entity-framework.md). EntityClient sağlayıcı <xref:System.Data.EntityClient> ad alanında uygulanır.  
  
## <a name="managing-connections"></a>Bağlantıları Yönetme  
 Entity Framework, <xref:System.Data.EntityClient.EntityConnection> temel alınan bir veri sağlayıcısına ve ilişkisel veritabanına bir sağlayan, depolama 'ya özgü ADO.NET veri sağlayıcılarının üzerine oluşturulur. Bir nesne oluşturmak için <xref:System.Data.EntityClient.EntityConnection> , gerekli modelleri ve eşlemeyi içeren bir meta veri kümesine başvurmanıza ve ayrıca depolama 'ya özgü veri sağlayıcısı adını ve bağlantı dizesini de yazmanız gerekir. Oluşturulduktan sonra <xref:System.Data.EntityClient.EntityConnection> , varlıklara kavramsal modelden oluşturulan sınıflar aracılığıyla erişilebilir.  
  
 app.config dosyasında bir bağlantı dizesi belirtebilirsiniz.  
  
 , <xref:System.Data.EntityClient> Sınıfını da içerir <xref:System.Data.EntityClient.EntityConnectionStringBuilder> . Bu sınıf, geliştiricilerin programsal olarak doğru bağlantı dizelerini oluşturmasını ve sınıfın özelliklerini ve yöntemlerini kullanarak var olan bağlantı dizelerini ayrıştırmasını ve yeniden oluşturmasını sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma](how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Sorgu oluşturma  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)]Dil, kavramsal varlık şemalarıyla doğrudan çalıştırılan ve devralma ve ilişkiler gibi varlık veri modeli kavramları destekleyen, depolama bağımsız BIR SQL diyalekti. <xref:System.Data.EntityClient.EntityCommand>Sınıfı [!INCLUDE[esql](../../../../../includes/esql-md.md)] bir varlık modeline karşı bir komut yürütmek için kullanılır. <xref:System.Data.EntityClient.EntityCommand>Nesneleri oluştururken, bir saklı yordam adı veya bir sorgu metni belirtebilirsiniz. Entity Framework, genel olarak depolamaya özgü sorgulara çevirmek için depolama 'ya özgü veri sağlayıcılarıyla birlikte kullanılabilir [!INCLUDE[esql](../../../../../includes/esql-md.md)] . Sorgu yazma hakkında daha fazla bilgi için [!INCLUDE[esql](../../../../../includes/esql-md.md)] bkz. [Entity SQL Language](./language-reference/entity-sql-language.md).  
  
 Aşağıdaki örnek bir nesnesi oluşturur <xref:System.Data.EntityClient.EntityCommand> ve bu nesnenin [!INCLUDE[esql](../../../../../includes/esql-md.md)] özelliğine bir sorgu metni atar <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> . Bu [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgu, kavramsal modelden liste fiyatına göre sıralanan ürünleri ister. Aşağıdaki kod, depolama modeli için hiçbir bilgiye sahip değildir.  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a>Sorgular yürütülüyor  
 Bir sorgu yürütüldüğünde, ayrıştırılır ve kurallı bir komut ağacına dönüştürülür. Sonraki tüm işlemler komut ağacında gerçekleştirilir. Komut ağacı, <xref:System.Data.EntityClient> ve gibi temel .NET Framework veri sağlayıcısı arasındaki iletişimin ortalardır <xref:System.Data.SqlClient> .  
  
 , <xref:System.Data.EntityClient.EntityDataReader> Bir kavramsal modelde yürütme sonuçlarını gösterir <xref:System.Data.EntityClient.EntityCommand> . Öğesini döndüren komutunu yürütmek için <xref:System.Data.EntityClient.EntityDataReader> çağrısı yapın <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> . <xref:System.Data.EntityClient.EntityDataReader> <xref:System.Data.IExtendedDataRecord> Zengin yapılandırılmış sonuçları tanımlamaya yönelik uygular.  
  
## <a name="managing-transactions"></a>Işlemleri yönetme  
 Entity Framework, işlemleri kullanmanın iki yolu vardır: otomatik ve açık. Otomatik işlemler <xref:System.Transactions> ad alanını kullanır ve açık işlemler <xref:System.Data.EntityClient.EntityTransaction> sınıfını kullanır.  
  
 Kavramsal model aracılığıyla kullanıma sunulan verileri güncelleştirmek için bkz. [nasıl yapılır: yönetimi işlemleri Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100)).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma](how-to-build-an-entityconnection-connection-string.md)  
  
 [Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme](how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme](how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme](how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme](how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme](how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Nasıl yapılır: EntityCommand Kullanarak Parametreli Entity SQL Sorgusu Yürütme](how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme](how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Nasıl yapılır: Çok Biçimli Sorgu Yürütme](how-to-execute-a-polymorphic-query.md)  
  
 [Nasıl yapılır: Nasıl yapılır: Navigate İşleci ile İlişkilerde Gezinme](how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantıları ve Işlemleri yönetme](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [ADO.NET Entity Framework](index.md)
- [Dil Başvurusu](./language-reference/index.md)
