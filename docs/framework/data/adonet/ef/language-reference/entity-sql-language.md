---
title: Varlık SQL dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: dbc44189634f4548b97647d19465e28ee343635d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="entity-sql-language"></a>Varlık SQL dili
Varlık SQL SQL benzer bir depolama bağımsız sorgu dildir. Varlık SQL sorgu bir varlığın verilerinin nesneler olarak veya bir tablo formunda sağlar. Varlık SQL aşağıdaki durumlarda kullanmayı düşünmeniz gerekir:  
  
-   Ne zaman bir sorgu çalışma zamanında dinamik olarak oluşturulması gerekir. Bu durumda, aynı zamanda sorgu oluşturucu yöntemleri kullanmayı düşünmelisiniz <xref:System.Data.Objects.ObjectQuery%601> Sorgu dizesinden çalışma zamanında bir varlık SQL oluşturmak yerine.  
  
-   Bir sorgu modelini tanımının bir parçası tanımlamak istediğinizde. Yalnızca varlık SQL veri modelinde desteklenir. Daha fazla bilgi için bkz: [QueryView öğesi (MSL)](http://msdn.microsoft.com/library/f0426b34-45cb-4fd7-9777-e0570c5e0e80)  
  
-   EntityClient satır kümeleri kullanarak olarak salt okunur varlık verileri döndürmek için kullanılırken bir <xref:System.Data.EntityClient.EntityDataReader>. Daha fazla bilgi için bkz: [EntityClient sağlayıcısı için Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
-   SQL tabanlı sorgu dillerde uzmanı zaten varsa, size en doğal varlık SQL gibi görünebilir.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Varlık SQL EntityClient sağlayıcısı ile kullanma  
 Varlık SQL EntityClient sağlayıcısı ile kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Entity Framework için EntityClient Sağlayıcısı](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Nasıl yapılır: EntityCommand Kullanarak Parametreli Varlık SQL Sorgusu Yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Nasıl yapılır: Çok Biçimli Sorgu Yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Nasıl yapılır: Navigate İşleci ile İlişkilerde Gezinme](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Varlık SQL nesne sorgularıyla kullanma  
 Varlık SQL nesne sorgularıyla kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Nasıl yapılır: varlık türü nesnesi döndüren bir sorgu yürütme](http://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [Nasıl yapılır: parametreleştirilmiş sorgu yürütme](http://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [Nasıl yapılır: Gezinti özellikleri kullanarak ilişkiler gidin](http://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [Nasıl yapılır: bir kullanıcı tanımlı işlev çağrısı](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [Nasıl yapılır: verileri filtreleme](http://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [Nasıl yapılır: verileri sıralama](http://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [Nasıl yapılır: veri grubu](http://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [Nasıl yapılır: veri toplama](http://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [Nasıl yapılır: Anonim türde nesne döndüren bir sorgu yürütme](http://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [Nasıl yapılır: basit türler koleksiyonu döndüren bir sorgu yürütme](http://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [Nasıl yapılır: bir Entitycollection'a ilgili nesneleri sorgulama](http://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [Nasıl yapılır: iki sorguları birleşimi sipariş](http://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [Nasıl yapılır: sonuçları sorgu aracılığıyla sayfası](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [Dil Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
