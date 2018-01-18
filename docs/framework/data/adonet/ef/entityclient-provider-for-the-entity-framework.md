---
title: "Entity Framework için EntityClient sağlayıcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eaccace7a333903e236107a72dbc17e19dc8d48a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Entity Framework için EntityClient sağlayıcısı
EntityClient sağlayıcısı, kavramsal modelde tanımlanan verilere erişmek için Entity Framework uygulamaları tarafından kullanılan veri sağlayıcıdır. Kavramsal modelleri hakkında daha fazla bilgi için bkz: [modelleme ve eşleme](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md). EntityClient diğer .NET Framework veri sağlayıcıları veri kaynağına erişmek için kullanır. Örneğin, EntityClient .NET Framework veri sağlayıcısı (SqlClient) SQL Server için bir SQL Server veritabanına erişirken kullanır. SqlClient sağlayıcısı hakkında daha fazla bilgi için bkz: [Entity Framework SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md). EntityClient sağlayıcısı uygulanan <xref:System.Data.EntityClient> ad alanı.  
  
## <a name="managing-connections"></a>Bağlantıları yönetme  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Depolama özgü üstünde derlemeler [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] sağlayarak veri sağlayıcıları bir <xref:System.Data.EntityClient.EntityConnection> bir temel alınan veri sağlayıcı ve ilişkisel veritabanı. Oluşturmak için bir <xref:System.Data.EntityClient.EntityConnection> nesnesi, gerekli modelleri ve eşleme ve ayrıca depolama özgü veri sağlayıcı adı ve bağlantı dizesi içeren bir meta veri kümesi başvurusu zorunda. Sonra <xref:System.Data.EntityClient.EntityConnection> olduğu yerde varlıkları kavramsal modelinden oluşturulan sınıflar aracılığıyla erişilebilir.  
  
 App.config dosyasında bir bağlantı dizesi belirtebilirsiniz.  
  
 <xref:System.Data.EntityClient> De içeren <xref:System.Data.EntityClient.EntityConnectionStringBuilder> sınıfı. Bu sınıf, program aracılığıyla sözdizimsel olarak doğru bağlantı dizelerini oluşturmak ve ayrıştırma ve özellikleri ve yöntemleri sınıfının kullanarak, varolan bağlantı dizeleri, yeniden oluşturulması geliştiricilerin sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Sorgular oluşturma  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] Depolama bağımsız dialect doğrudan kavramsal varlık şemalarda çalışır ve varlık veri modeli kavramları devralma ve ilişkileri gibi destekleyen SQL bir dildir. <xref:System.Data.EntityClient.EntityCommand> Sınıfı yürütmek için kullanılan bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] bir varlık modeli karşı komutu. Oluşturduğunuzda <xref:System.Data.EntityClient.EntityCommand> nesneleri, bir saklı yordam adı veya bir sorgu metni belirtebilirsiniz. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Çalışır genel çevirmek için depolama özgü veri sağlayıcılarıyla [!INCLUDE[esql](../../../../../includes/esql-md.md)] içine depolama özgü sorgular. Yazma hakkında daha fazla bilgi için [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorguları, bkz: [varlık SQL dil](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
 Aşağıdaki örnekte bir <xref:System.Data.EntityClient.EntityCommand> nesne ve atar bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgu metni kendi <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> özelliği. Bu [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgu kavramsal modelden fiyat listesi göre sıralanmış ürünleri ister. Aşağıdaki kod depolama modelinin olanağıyla hiç sahiptir.  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"``SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## <a name="executing-queries"></a>Sorgular yürütme  
 Bir sorgu çalıştırıldığında, ayrıştırılmış ve kurallı komut ağacına dönüştürülemiyor. Tüm sonraki işleme, komut ağacı üzerinde gerçekleştirilir. Komut ağacı arasındaki iletişimi araçtır <xref:System.Data.EntityClient> ve arka plandaki [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı gibi <xref:System.Data.SqlClient>.  
  
 <xref:System.Data.EntityClient.EntityDataReader> Yürütme sonuçlarını gösterir bir <xref:System.Data.EntityClient.EntityCommand> kavramsal model karşı. Döndürür komutu çalıştırmak için <xref:System.Data.EntityClient.EntityDataReader>, çağrı <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. <xref:System.Data.EntityClient.EntityDataReader> Uygulayan <xref:System.Data.IExtendedDataRecord> zengin açıklamak için sonuçları yapılandırılmış.  
  
## <a name="managing-transactions"></a>İşlemleri yönetme  
 Entity Framework hareketleri kullanmak için iki yolu vardır: otomatik ve açık. Otomatik işlemleri kullanmak <xref:System.Transactions> ad alanı ve açık işlemleri kullanmak <xref:System.Data.EntityClient.EntityTransaction> sınıfı.  
  
 Kavramsal modeli aracılığıyla kullanıma sunulan verileri güncelleştirmek için; bkz: [nasıl yapılır: Entity Framework yönetme işlemlerinde](http://msdn.microsoft.com/en-us/4a55eb7f-f826-4a48-9df1-aebe2352ebef).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Nasıl yapılır: EntityCommand Kullanarak Parametreli Varlık SQL Sorgusu Yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Nasıl yapılır: Çok Biçimli Sorgu Yürütme](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Nasıl yapılır: Navigate İşleci ile İlişkilerde Gezinme](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantılarını yönetme ve işlemler](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Dil Başvurusu](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
