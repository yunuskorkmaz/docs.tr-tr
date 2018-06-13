---
title: Türler (varlık SQL) oluşturma
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 91ed123132965353ff354282f6850e9ef9cba3d0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765262"
---
# <a name="constructing-types-entity-sql"></a>Türler (varlık SQL) oluşturma
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] üç tür oluşturucular sağlar: satır Oluşturucular, adlandırılmış türü oluşturucuları ve koleksiyon oluşturucular.  
  
## <a name="row-constructors"></a>Satır oluşturucular  
 Satır kurucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir veya daha fazla değer anonim, yapısal olarak yazılan kayıtları oluşturmak için. Bir satır oluşturucusunda sonuç türü, alan türlerini satır oluşturmak için kullanılan değerlerin türleri için karşılık gelen bir satır türüdür. Örneğin, aşağıdaki deyim türünde bir değer oluşturur `Record(a int, b string, c int)`:  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 Row kurucusunda bir ifade için bir diğer ad belirtmezseniz, Entity Framework oluşturur dener. Daha fazla bilgi için bkz: "Diğer ad kuralları" bölümünde [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Row kurucusunda ifade yumuşatma aşağıdaki kurallar geçerlidir:  
  
-   Bir satır oluşturucusunda ifadelerinde başka diğer adlar aynı oluşturucuda başvuruda bulunamaz.  
  
-   İki ifadeye aynı row kurucusunda aynı ada sahip olamaz.  
  
 Satır oluşturucular hakkında daha fazla bilgi için bkz: [satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="collection-constructors"></a>Koleksiyon oluşturucular  
 Koleksiyon kurucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değerler listesinden bir çoklu küme örneği oluşturmak için. Oluşturucu tüm değerleri karşılıklı olarak uyumlu türünde olmalıdır `T`, ve Oluşturucusu türünden bir koleksiyona üretir `Multiset<T>`. Örneğin, aşağıdaki ifade tamsayılar bir koleksiyonunu oluşturur:  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 Boş multiset oluşturucular öğelerin türü belirlenemediğinden izin verilmiyor. Şu geçerli değil:  
  
 `multiset() {}`  
  
 Daha fazla bilgi için bkz: [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).  
  
## <a name="named-type-constructors-namedtype-initializers"></a>Adlandırılmış türü oluşturucuları (NamedType başlatıcıları)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] türü oluşturucuları (adlandırılmış karmaşık türlerin örnekleri oluşturmak için başlatıcıları) ve varlık türleri sağlar. Örneğin, aşağıdaki ifade bir örneğini oluşturur bir `Person` türü.  
  
 `Person("abc", 12)`  
  
 Aşağıdaki ifade, karmaşık türün bir örneğini oluşturur.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Aşağıdaki ifade, iç içe geçmiş bir karmaşık tür bir örneğini oluşturur.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Aşağıdaki ifade ile iç içe geçmiş bir karmaşık türü bir varlığın bir örneğini oluşturur.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Aşağıdaki örnek, bir özellik NULL karmaşık türün başlatmak gösterilmiştir. `MyModel.ZipCode(‘98118’, null)`  
  
 Oluşturucu bağımsız değişken türü özniteliklerini bildirimi aynı sırada olduğu varsayılır.  
  
 Daha fazla bilgi için bkz: [adlı Tür oluşturucu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Tür Sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
