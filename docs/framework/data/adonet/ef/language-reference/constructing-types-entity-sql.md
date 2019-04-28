---
title: Oluşturma türleri (SQL varlık)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 53aa7fcc82a476c8b8bd87b059e08bee6741c0d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605838"
---
# <a name="constructing-types-entity-sql"></a>Oluşturma türleri (SQL varlık)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] üç tür oluşturucular sağlar: Oluşturucular, adlandırılmış Tür oluşturucu ve koleksiyon oluşturucular satır.  
  
## <a name="row-constructors"></a>Satır oluşturucular  
 Satır oluşturucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] anonim, yapısal olarak belirlenmiş bir veya daha fazla değer kayıtları oluşturmak için. Bir satır oluşturucusunda sonuç türü, alan türlerini satır oluşturmak için kullanılan değerleri türlerine karşılık gelen bir satır türüdür. Örneğin, aşağıdaki ifade türünde bir değer oluşturur `Record(a int, b string, c int)`:  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 Row oluşturucusunda bir ifade için bir diğer ad belirtmezseniz, Entity Framework bir çalışacaktır. "Diğer ad kuralları" bölümünde daha fazla bilgi için bkz. [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Row oluşturucusunda ifade yumuşatma aşağıdaki kurallar geçerlidir:  
  
- Row oluşturucusunda ifadeleri başka diğer adlar aynı oluşturucu içinde başvurulamaz.  
  
- Aynı row oluşturucusunda iki ifadeler aynı ada sahip olamaz.  
  
 Satır oluşturucular hakkında daha fazla bilgi için bkz. [satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="collection-constructors"></a>Koleksiyon oluşturucular  
 Koleksiyon oluşturucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değerler listesinden bir çoklu küme örneği oluşturmak için. Oluşturucu tüm değerleri karşılıklı olarak uyumlu türünde olmalıdır `T`, oluşturucu türü bir koleksiyon oluşturur `Multiset<T>`. Örneğin, aşağıdaki ifade, tamsayı bir koleksiyonunu oluşturur:  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 Öğelerin türü belirlenemiyor çünkü boş multiset oluşturuculara izin verilmez. Aşağıdakiler geçerli değil:  
  
 `multiset() {}`  
  
 Daha fazla bilgi için [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).  
  
## <a name="named-type-constructors-namedtype-initializers"></a>Adlandırılmış Tür oluşturucu (NamedType başlatıcılar)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tür oluşturucular (başlatıcılar adlandırılmış karmaşık türlerin örneklerini oluşturmak için) ve varlık türleri sağlar. Örneğin, aşağıdaki ifade bir örneği oluşturan bir `Person` türü.  
  
 `Person("abc", 12)`  
  
 Aşağıdaki ifade, karmaşık bir türün örneğini oluşturur.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Aşağıdaki ifade, iç içe geçmiş bir karmaşık türün örneğini oluşturur.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Aşağıdaki ifade ile iç içe geçmiş bir karmaşık türü bir varlık örneği oluşturur.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Aşağıdaki örnek, bir karmaşık türü null bir özelliğini başlatmak gösterilmektedir. `MyModel.ZipCode(‘98118’, null)`  
  
 Oluşturucusuna bağımsız değişken türü özniteliklerini bildirimi aynı sırada olduğu varsayılır.  
  
 Daha fazla bilgi için [adlandırılmış Tür oluşturucu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Tür Sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
