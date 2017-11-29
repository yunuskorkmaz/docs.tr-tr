---
title: "Varlık SQL dili"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 08e366e8bbd9df31f367496ca5e106b876921896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-sql-language"></a>Varlık SQL dili
Varlık SQL SQL benzer bir depolama bağımsız sorgu dildir. Varlık SQL sorgu bir varlığın verilerinin nesneler olarak veya bir tablo formunda sağlar. Varlık SQL aşağıdaki durumlarda kullanmayı düşünmeniz gerekir:  
  
-   Ne zaman bir sorgu çalışma zamanında dinamik olarak oluşturulması gerekir. Bu durumda, aynı zamanda sorgu oluşturucu yöntemleri kullanmayı düşünmelisiniz <xref:System.Data.Objects.ObjectQuery%601> Sorgu dizesinden çalışma zamanında bir varlık SQL oluşturmak yerine.  
  
-   Bir sorgu modelini tanımının bir parçası tanımlamak istediğinizde. Yalnızca varlık SQL veri modelinde desteklenir. Daha fazla bilgi için bkz: [QueryView öğesi (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)  
  
-   EntityClient satır kümeleri kullanarak olarak salt okunur varlık verileri döndürmek için kullanılırken bir <xref:System.Data.EntityClient.EntityDataReader>. Daha fazla bilgi için bkz: [EntityClient sağlayıcısı için Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
-   SQL tabanlı sorgu dillerde uzmanı zaten varsa, size en doğal varlık SQL gibi görünebilir.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Varlık SQL EntityClient sağlayıcısı ile kullanma  
 Varlık SQL EntityClient sağlayıcısı ile kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Entity Framework için EntityClient sağlayıcısı](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [Nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Nasıl yapılır: RefType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Nasıl yapılır: karmaşık türleri döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Nasıl yapılır: iç içe geçmiş koleksiyonları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Nasıl yapılır: EntityCommand kullanarak parametreli bir saklı yordamı yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Nasıl yapılır: çok biçimli bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Nasıl yapılır: ilişkileriyle gidin işleci gidin](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Varlık SQL nesne sorgularıyla kullanma  
 Varlık SQL nesne sorgularıyla kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Nasıl yapılır: varlık türü nesnesi döndüren bir sorgu yürütme](http://msdn.microsoft.com/en-us/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [Nasıl yapılır: parametreleştirilmiş sorgu yürütme](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [Nasıl yapılır: Gezinti özellikleri kullanarak ilişkiler gidin](http://msdn.microsoft.com/en-us/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [Nasıl yapılır: bir kullanıcı tanımlı işlev çağrısı](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [Nasıl yapılır: verileri filtreleme](http://msdn.microsoft.com/en-us/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [Nasıl yapılır: verileri sıralama](http://msdn.microsoft.com/en-us/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [Nasıl yapılır: veri grubu](http://msdn.microsoft.com/en-us/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [Nasıl yapılır: veri toplama](http://msdn.microsoft.com/en-us/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [Nasıl yapılır: Anonim türde nesne döndüren bir sorgu yürütme](http://msdn.microsoft.com/en-us/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [Nasıl yapılır: basit türler koleksiyonu döndüren bir sorgu yürütme](http://msdn.microsoft.com/en-us/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [Nasıl yapılır: bir Entitycollection'a ilgili nesneleri sorgulama](http://msdn.microsoft.com/en-us/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [Nasıl yapılır: iki sorguları birleşimi sipariş](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313)  
  
 [Nasıl yapılır: sonuçları sorgu aracılığıyla sayfası](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Varlık SQL genel bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [Dil Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
