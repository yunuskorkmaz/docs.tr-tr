---
title: Entity Framework için EntityClient sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: b094f6d0fbd7c1dc8d56fc43a05fc4d22a80e981
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826453"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Entity Framework için EntityClient sağlayıcısı
EntityClient sağlayıcısı kavramsal modelde tanımlanan veri erişimi için Entity Framework uygulamaları tarafından kullanılan veri sağlayıcıdır. Kavramsal modeller hakkında daha fazla bilgi için bkz. [modelleme ve eşleme](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md). EntityClient, diğer .NET Framework veri sağlayıcıları, veri kaynağına erişmek için kullanır. Örneğin, EntityClient .NET Framework veri sağlayıcısı (SqlClient) SQL Server için SQL Server veritabanına erişirken kullanır. SqlClient sağlayıcısı hakkında daha fazla bilgi için bkz: [Entity Framework için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md). EntityClient sağlayıcı uygulanan <xref:System.Data.EntityClient> ad alanı.  
  
## <a name="managing-connections"></a>Bağlantıları yönetme  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Üzerinde depolama özel yapılar [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] sağlayarak veri sağlayıcıları bir <xref:System.Data.EntityClient.EntityConnection> ilişkisel veritabanı ve temel alınan veri sağlayıcısı. Oluşturmak için bir <xref:System.Data.EntityClient.EntityConnection> nesnesi, bir dizi gerekli model ve eşleme ve ayrıca depolama özgü veri sağlayıcı adı ve bağlantı dizesi içeren bir meta veri başvurusu gerekir. Sonra <xref:System.Data.EntityClient.EntityConnection> olduğu yerde varlıkları kavramsal model oluşturulan sınıfların aracılığıyla erişilebilir.  
  
 App.config dosyasında bir bağlantı dizesi belirtebilirsiniz.  
  
 <xref:System.Data.EntityClient> Yöntemlerine <xref:System.Data.EntityClient.EntityConnectionStringBuilder> sınıfı. Bu sınıf, program aracılığıyla sözdizimsel olarak doğru bağlantı dizesi oluşturmak ve ayrıştırmak ve özellikleri ve sınıfının yöntemlerini kullanarak mevcut bağlantı dizelerini yeniden geliştiricilerin sağlar. Daha fazla bilgi için [nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Sorgu oluşturma  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] Doğrudan kavramsal varlık şemalarıyla çalışan ve devralma ve ilişkiler gibi varlık veri modeli kavramları destekleyen SQL depolamadan bağımsız SQL diyalektiği dilidir. <xref:System.Data.EntityClient.EntityCommand> Sınıfı yürütmek için kullanılan bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] varlık modeli karşı komutu. Oluşturduğunuzda <xref:System.Data.EntityClient.EntityCommand> nesneleri bir saklı yordam adı veya bir sorgu metni belirtebilirsiniz. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Çalışır genel çevirmek için depolama özgü veri sağlayıcılarıyla [!INCLUDE[esql](../../../../../includes/esql-md.md)] depolama özgü sorgulara. Yazma hakkında daha fazla bilgi için [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgularını görmek [Entity SQL dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.EntityClient.EntityCommand> nesne ve atadıkları kişiler bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgu metni için kendi <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> özelliği. Bu [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgu kavramsal model liste fiyatından göre sıralanmış ürünleri ister. Aşağıdaki kod, depolama modelinin olanağıyla hiç sahiptir.  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"``SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## <a name="executing-queries"></a>Sorgular yürütme  
 Bir sorgu yürütüldüğünde, ayrıştırılmış ve kurallı komut ağacına dönüştürülür. Tüm sonraki işleme, komut ağacı üzerinde gerçekleştirilir. Komut ağacı olduğu anlamına gelir iletişimin <xref:System.Data.EntityClient> ve arka plandaki [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı gibi <xref:System.Data.SqlClient>.  
  
 <xref:System.Data.EntityClient.EntityDataReader> Çalıştırma sonuçlarını gösteren bir <xref:System.Data.EntityClient.EntityCommand> kavramsal modeline karşı. Döndüren komutu yürütmek için <xref:System.Data.EntityClient.EntityDataReader>, çağrı <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. <xref:System.Data.EntityClient.EntityDataReader> Uygulayan <xref:System.Data.IExtendedDataRecord> sonuçları zengin açıklamak için yapılandırılmış.  
  
## <a name="managing-transactions"></a>İşlemleri yönetme  
 Varlık Çerçevesi'nde, işlem kullanmanın iki yolu vardır: otomatik ve açık. Otomatik işlemleri kullanma <xref:System.Transactions> ad alanı ve açık işlemleri <xref:System.Data.EntityClient.EntityTransaction> sınıfı.  
  
 Kavramsal bir modeli aracılığıyla sunulan verileri güncelleştirmek için bkz: [nasıl yapılır: Entity Framework işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100)).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Nasıl yapılır: RefType sonuçları döndüren bir sorgu yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Nasıl yapılır: Karmaşık türler döndüren bir sorgu yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Nasıl yapılır: İç içe geçmiş koleksiyonlar döndüren bir sorgu yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli saklı yordam yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Nasıl yapılır: Çok biçimli sorgu yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Nasıl yapılır: İle ilişkilerde gezinme işleci gidin](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantılarını yönetme ve işlemler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
- [Dil Başvurusu](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
