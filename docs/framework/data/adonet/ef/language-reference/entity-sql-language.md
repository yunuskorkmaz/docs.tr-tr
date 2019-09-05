---
title: Entity SQL Dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: a2e4b7245dbfccf7864481b52a0e868a85efbca6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251011"
---
# <a name="entity-sql-language"></a>Entity SQL Dili
Entity SQL, SQL 'e benzer bir depolama bağımsız sorgu dilidir. Entity SQL, varlık verilerini nesneler olarak ya da tablolu bir biçimde sorgulamanızı sağlar. Aşağıdaki durumlarda Entity SQL kullanmayı göz önünde bulundurmanız gerekir:  
  
- Bir sorgu, çalışma zamanında dinamik olarak oluşturulmalıdır. Bu durumda, çalışma zamanında Entity SQL bir sorgu dizesi oluşturmak yerine ' ın <xref:System.Data.Objects.ObjectQuery%601> Sorgu Oluşturucu yöntemlerini kullanmayı da göz önünde bulundurmanız gerekir.  
  
- Model tanımının bir parçası olarak bir sorgu tanımlamak istediğinizde. Bir veri modelinde yalnızca Entity SQL desteklenir. Daha fazla bilgi için bkz. [QueryView element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
- ' İ kullanarak <xref:System.Data.EntityClient.EntityDataReader>salt okuma varlık verilerini satır kümesi olarak döndürmek için EntityClient kullanılırken. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](../entityclient-provider-for-the-entity-framework.md).  
  
- SQL tabanlı sorgu dillerinde zaten bir uzman varsa Entity SQL en doğal olarak görünebilir.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>EntityClient sağlayıcı ile Entity SQL kullanma  
 EntityClient sağlayıcı ile Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Entity Framework için EntityClient Sağlayıcısı](../entityclient-provider-for-the-entity-framework.md)  
  
 [Nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma](../how-to-build-an-entityconnection-connection-string.md)  
  
 [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Nasıl yapılır: RefType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Nasıl yapılır: Karmaşık türler döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Nasıl yapılır: Iç Içe geçmiş Koleksiyonlar döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli Entity SQL sorgusu yürütme](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli saklı yordam yürütme](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Nasıl yapılır: Polimorfik sorgu yürütme](../how-to-execute-a-polymorphic-query.md)  
  
 [Nasıl yapılır: Gezinme Işleciyle Ilişkilerde gezinme](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Nesne sorgularıyla Entity SQL kullanma  
 Nesne sorgularıyla Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Nasıl yapılır: Varlık türü nesneleri döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [Nasıl yapılır: Parametreli sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [Nasıl yapılır: Gezinti özelliklerini kullanarak Ilişkilerde gezin](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [Nasıl yapılır: Kullanıcı tanımlı bir Işlev çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [Nasıl yapılır: Verileri Filtrele](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [Nasıl yapılır: Verileri sıralama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [Nasıl yapılır: Verileri gruplandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [Nasıl yapılır: Verileri topla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [Nasıl yapılır: Anonim tür nesneleri döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [Nasıl yapılır: Temel türlerin bir koleksiyonunu döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [Nasıl yapılır: Bir EntityCollection 'da Ilişkili nesneleri sorgulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [Nasıl yapılır: Iki sorgunun birleşimini sıralama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [Nasıl yapılır: Sorgu sonuçları aracılığıyla sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL’e Genel Bakış](entity-sql-overview.md)  
  
 [Entity SQL Başvurusu](entity-sql-reference.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../index.md)
- [Dil Başvurusu](index.md)
