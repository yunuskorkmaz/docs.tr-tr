---
title: Entity Framework için EntityClient Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 70cc5a9aaa22cc563c910f9d250ad4565e34a135
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251596"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Entity Framework için EntityClient Sağlayıcısı
EntityClient sağlayıcısı, kavramsal modelde açıklanan verilere erişmek için Entity Framework uygulamalar tarafından kullanılan bir veri sağlayıcısıdır. Kavramsal modeller hakkında daha fazla bilgi için bkz. [modelleme ve eşleme](modeling-and-mapping.md). EntityClient, veri kaynağına erişmek için diğer .NET Framework veri sağlayıcılarını kullanır. Örneğin, EntityClient SQL Server veritabanına erişirken SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı kullanır. SqlClient sağlayıcısı hakkında daha fazla bilgi için bkz. [sqlclient Entity Framework](sqlclient-for-the-entity-framework.md). EntityClient sağlayıcı <xref:System.Data.EntityClient> ad alanında uygulanır.  
  
## <a name="managing-connections"></a>Bağlantıları Yönetme  
 , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Temel alınan bir veri sağlayıcısına ve ilişkisel veritabanına bir <xref:System.Data.EntityClient.EntityConnection> sağlar. Bir <xref:System.Data.EntityClient.EntityConnection> nesne oluşturmak için, gerekli modelleri ve eşlemeyi içeren bir meta veri kümesine başvurmanıza ve ayrıca depolama 'ya özgü veri sağlayıcısı adını ve bağlantı dizesini de yazmanız gerekir. <xref:System.Data.EntityClient.EntityConnection> Oluşturulduktan sonra, varlıklara kavramsal modelden oluşturulan sınıflar aracılığıyla erişilebilir.  
  
 App. config dosyasında bir bağlantı dizesi belirtebilirsiniz.  
  
 , <xref:System.Data.EntityClient> <xref:System.Data.EntityClient.EntityConnectionStringBuilder> Sınıfını da içerir. Bu sınıf, geliştiricilerin programsal olarak doğru bağlantı dizelerini oluşturmasını ve sınıfın özelliklerini ve yöntemlerini kullanarak var olan bağlantı dizelerini ayrıştırmasını ve yeniden oluşturmasını sağlar. Daha fazla bilgi için [nasıl yapılır: Bir EntityConnection bağlantı dizesi](how-to-build-an-entityconnection-connection-string.md)oluşturun.  
  
## <a name="creating-queries"></a>Sorgu oluşturma  
 Dil [!INCLUDE[esql](../../../../../includes/esql-md.md)] , kavramsal varlık şemalarıyla doğrudan çalıştırılan ve devralma ve ilişkiler gibi varlık veri modeli kavramları destekleyen, depolama bağımsız bir SQL diyalekti. Sınıfı bir varlık modeline karşı bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] komut yürütmek için kullanılır. <xref:System.Data.EntityClient.EntityCommand> <xref:System.Data.EntityClient.EntityCommand> Nesneleri oluştururken, bir saklı yordam adı veya bir sorgu metni belirtebilirsiniz. , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Genel[!INCLUDE[esql](../../../../../includes/esql-md.md)] olarak depolamaya özgü sorgulara çevirmek için depolamaya özgü veri sağlayıcılarıyla birlikte çalışarak. Sorgu yazma [!INCLUDE[esql](../../../../../includes/esql-md.md)] hakkında daha fazla bilgi için bkz. [Entity SQL Language](./language-reference/entity-sql-language.md).  
  
 Aşağıdaki örnek bir <xref:System.Data.EntityClient.EntityCommand> nesnesi oluşturur ve bu nesnenin <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> özelliğine [!INCLUDE[esql](../../../../../includes/esql-md.md)] bir sorgu metni atar. Bu [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgu, kavramsal modelden liste fiyatına göre sıralanan ürünleri ister. Aşağıdaki kod, depolama modeli için hiçbir bilgiye sahip değildir.  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a>Sorgular yürütülüyor  
 Bir sorgu yürütüldüğünde, ayrıştırılır ve kurallı bir komut ağacına dönüştürülür. Sonraki tüm işlemler komut ağacında gerçekleştirilir. Komut ağacı, <xref:System.Data.EntityClient> ve gibi temel .NET Framework veri sağlayıcısı <xref:System.Data.SqlClient>arasındaki iletişimin ortalardır.  
  
 , <xref:System.Data.EntityClient.EntityDataReader> Bir<xref:System.Data.EntityClient.EntityCommand> kavramsal modelde yürütme sonuçlarını gösterir. <xref:System.Data.EntityClient.EntityDataReader>Öğesini döndüren komutunu yürütmek için çağrısı <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>yapın. Zengin yapılandırılmış <xref:System.Data.IExtendedDataRecord> sonuçları tanımlamaya yönelik uygular.<xref:System.Data.EntityClient.EntityDataReader>  
  
## <a name="managing-transactions"></a>Işlemleri yönetme  
 Entity Framework, işlemleri kullanmanın iki yolu vardır: otomatik ve açık. Otomatik işlemler <xref:System.Transactions> ad alanını kullanır ve açık işlemler <xref:System.Data.EntityClient.EntityTransaction> sınıfını kullanır.  
  
 Kavramsal model aracılığıyla sunulan verileri güncelleştirmek için bkz [. nasıl yapılır: Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100))işlemleri yönetin.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma](how-to-build-an-entityconnection-connection-string.md)  
  
 [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Nasıl yapılır: RefType sonuçları döndüren bir sorgu yürütme](how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Nasıl yapılır: Karmaşık türler döndüren bir sorgu yürütme](how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Nasıl yapılır: Iç Içe geçmiş Koleksiyonlar döndüren bir sorgu yürütme](how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli Entity SQL sorgusu yürütme](how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli saklı yordam yürütme](how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Nasıl yapılır: Polimorfik sorgu yürütme](how-to-execute-a-polymorphic-query.md)  
  
 [Nasıl yapılır: Gezinme Işleciyle Ilişkilerde gezinme](how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [ADO.NET Entity Framework](index.md)
- [Dil Başvurusu](./language-reference/index.md)
