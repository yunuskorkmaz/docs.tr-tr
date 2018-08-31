---
title: Entity SQL dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 1df5372bed2c4c4b026662e0d1912683dd8752e9
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331960"
---
# <a name="entity-sql-language"></a>Entity SQL dili
Entity SQL SQL'e benzeyen bir depolamadan bağımsız sorgu dilidir. Entity SQL sorgu bir varlığın verilerinin nesneleri ya da tablo biçiminde sağlar. Aşağıdaki durumlarda varlık SQL kullanmayı düşünmeniz gerekir:  
  
-   Ne zaman bir sorgunun çalışma zamanında dinamik olarak oluşturulması gerekir. Bu durumda, aynı zamanda sorgu oluşturucu yöntemleri kullanılarak dikkate almanız gereken <xref:System.Data.Objects.ObjectQuery%601> varlık SQL oluşturmak yerine sorgu zamanında dizesi.  
  
-   Model tanımının bir parçası bir sorgu tanımlamak istediğinizde. Yalnızca varlık SQL veri modelinde desteklenir. Daha fazla bilgi için [QueryView öğesi (MSL)](https://msdn.microsoft.com/library/f0426b34-45cb-4fd7-9777-e0570c5e0e80)  
  
-   Satır kümeleri kullanarak olarak salt okunur varlık verilerini döndürmek için EntityClient kullanırken bir <xref:System.Data.EntityClient.EntityDataReader>. Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
-   SQL tabanlı sorgu dillerde Uzman zaten varsa, size en doğal varlık SQL gibi görünebilir.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Entity SQL EntityClient sağlayıcısı ile kullanma  
 Entity SQL EntityClient sağlayıcısı ile kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
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
  
## <a name="using-entity-sql-with-object-queries"></a>Entity SQL nesnesi sorgularıyla kullanma  
 Entity SQL ile nesne sorguları kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Nasıl yapılır: varlık türü nesnesi döndüren bir sorgu yürütme](https://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [Nasıl yapılır: bir parametreli sorguyu yürütme](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [Nasıl yapılır: Gezinti özelliklerini kullanarak ilişkilerde gezinme](https://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [Nasıl yapılır: bir kullanıcı tanımlı işlevi çağırma](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [Nasıl yapılır: verileri filtreleme](https://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [Nasıl yapılır: verileri sıralama](https://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [Nasıl yapılır: verileri gruplandırma](https://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [Nasıl yapılır: veri toplama](https://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [Nasıl yapılır: Anonim türde nesneleri döndüren bir sorgu yürütme](https://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [Nasıl yapılır: temel türlerin koleksiyonunu döndüren bir sorgu yürütme](https://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [Nasıl yapılır: bir entitycollection'ın ilgili nesneleri sorgulama](https://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [Nasıl yapılır: UNION iki sorgunun sıralama](https://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [Nasıl yapılır: sorgu aracılığıyla sayfa sonuçları](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [Dil Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
