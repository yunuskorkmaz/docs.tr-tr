---
title: Entity SQL Dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: ecbf9bc555594d205281237559037ac2a0e1cdb0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631699"
---
# <a name="entity-sql-language"></a>Entity SQL Dili
Entity SQL SQL'e benzeyen bir depolamadan bağımsız sorgu dilidir. Entity SQL sorgu bir varlığın verilerinin nesneleri ya da tablo biçiminde sağlar. Aşağıdaki durumlarda varlık SQL kullanmayı düşünmeniz gerekir:  
  
- Ne zaman bir sorgunun çalışma zamanında dinamik olarak oluşturulması gerekir. Bu durumda, aynı zamanda sorgu oluşturucu yöntemleri kullanılarak dikkate almanız gereken <xref:System.Data.Objects.ObjectQuery%601> varlık SQL oluşturmak yerine sorgu zamanında dizesi.  
  
- Model tanımının bir parçası bir sorgu tanımlamak istediğinizde. Yalnızca varlık SQL veri modelinde desteklenir. Daha fazla bilgi için [QueryView öğesi (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
- Satır kümeleri kullanarak olarak salt okunur varlık verilerini döndürmek için EntityClient kullanırken bir <xref:System.Data.EntityClient.EntityDataReader>. Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
- SQL tabanlı sorgu dillerde Uzman zaten varsa, size en doğal varlık SQL gibi görünebilir.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Entity SQL EntityClient sağlayıcısı ile kullanma  
 Entity SQL EntityClient sağlayıcısı ile kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Entity Framework için EntityClient Sağlayıcısı](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [Nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Nasıl yapılır: RefType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Nasıl yapılır: Karmaşık türler döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Nasıl yapılır: İç içe geçmiş koleksiyonlar döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli saklı yordam yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Nasıl yapılır: Çok biçimli sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Nasıl yapılır: İle ilişkilerde gezinme işleci gidin](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Entity SQL nesnesi sorgularıyla kullanma  
 Entity SQL ile nesne sorguları kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Nasıl yapılır: Varlık türü nesnesi döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [Nasıl yapılır: Parametreli bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [Nasıl yapılır: Gezinti özellikleri kullanarak ilişkilerde gezinme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [Nasıl yapılır: Bir kullanıcı tanımlı işlevi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [Nasıl yapılır: Verileri filtreleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [Nasıl yapılır: Verileri sıralama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [Nasıl yapılır: Verileri gruplandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [Nasıl yapılır: Veri toplama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [Nasıl yapılır: Anonim türdeki nesneleri döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [Nasıl yapılır: Temel türlerin koleksiyonunu döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [Nasıl yapılır: Bir entitycollection'ın ilgili nesneleri sorgulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [Nasıl yapılır: Sırada iki sorgu birleşimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [Nasıl yapılır: Sorgu sonuçları sayfasından](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
- [Dil Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
