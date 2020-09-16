---
title: Entity SQL Dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 2600b7626ebc5196c702f2d1e3159fd9549227f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553388"
---
# <a name="entity-sql-language"></a>Entity SQL Dili
Entity SQL, SQL 'e benzer bir depolama bağımsız sorgu dilidir. Entity SQL, varlık verilerini nesneler olarak ya da tablolu bir biçimde sorgulamanızı sağlar. Aşağıdaki durumlarda Entity SQL kullanmayı göz önünde bulundurmanız gerekir:  
  
- Bir sorgu, çalışma zamanında dinamik olarak oluşturulmalıdır. Bu durumda, <xref:System.Data.Objects.ObjectQuery%601> çalışma zamanında Entity SQL bir sorgu dizesi oluşturmak yerine ' ın Sorgu Oluşturucu yöntemlerini kullanmayı da göz önünde bulundurmanız gerekir.  
  
- Model tanımının bir parçası olarak bir sorgu tanımlamak istediğinizde. Bir veri modelinde yalnızca Entity SQL desteklenir. Daha fazla bilgi için bkz. [QueryView element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
- ' İ kullanarak salt okuma varlık verilerini satır kümesi olarak döndürmek için EntityClient kullanılırken <xref:System.Data.EntityClient.EntityDataReader> . Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](../entityclient-provider-for-the-entity-framework.md).  
  
- SQL tabanlı sorgu dillerinde zaten bir uzman varsa Entity SQL en doğal olarak görünebilir.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>EntityClient sağlayıcı ile Entity SQL kullanma  
 EntityClient sağlayıcı ile Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Entity Framework için EntityClient Sağlayıcısı](../entityclient-provider-for-the-entity-framework.md)  
  
 [Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma](../how-to-build-an-entityconnection-connection-string.md)  
  
 [Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Nasıl yapılır: EntityCommand Kullanarak Parametreli Entity SQL Sorgusu Yürütme](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Nasıl yapılır: Çok Biçimli Sorgu Yürütme](../how-to-execute-a-polymorphic-query.md)  
  
 [Nasıl yapılır: Nasıl yapılır: Navigate İşleci ile İlişkilerde Gezinme](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Nesne sorgularıyla Entity SQL kullanma  
 Nesne sorgularıyla Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Nasıl yapılır: varlık türü nesneleri döndüren bir sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [Nasıl yapılır: Parametreli sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [Nasıl yapılır: gezinme özelliklerini kullanarak Ilişkilerde gezinme](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [Nasıl yapılır: Kullanıcı tanımlı bir Işlevi çağırma](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [Nasıl yapılır: verileri filtreleme](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [Nasıl yapılır: verileri sıralama](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [Nasıl yapılır: verileri gruplandırma](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [Nasıl yapılır: verileri toplama](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [Nasıl yapılır: anonim tür nesneleri döndüren bir sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [Nasıl yapılır: temel türlerin bir koleksiyonunu döndüren bir sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [Nasıl yapılır: bir EntityCollection 'da Ilgili nesneleri sorgulama](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [Nasıl yapılır: Iki sorgunun birleşimini sıralama](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL’e Genel Bakış](entity-sql-overview.md)  
  
 [Entity SQL Başvurusu](entity-sql-reference.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../index.md)
- [Dil Başvurusu](index.md)
