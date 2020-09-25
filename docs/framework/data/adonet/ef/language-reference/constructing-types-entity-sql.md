---
title: Türleri oluşturma (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 82c8e3f2bac0d13da4870e90878e0de6fc9ec063
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177533"
---
# <a name="constructing-types-entity-sql"></a>Türleri oluşturma (Entity SQL)

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Üç tür Oluşturucu sağlar: satır oluşturucular, adlandırılmış tür oluşturucular ve koleksiyon oluşturucuları.  
  
## <a name="row-constructors"></a>Satır oluşturucuları  

 ' De satır oluşturucuları kullanarak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturun. Bir satır oluşturucusunun sonuç türü, alan türleri satırı oluşturmak için kullanılan değerlerin türlerine karşılık gelen bir satır türüdür. Örneğin, aşağıdaki ifade türünde bir değer oluşturur `Record(a int, b string, c int)` :  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 Bir satır oluşturucusunda ifade için bir diğer ad sağlamazsanız, Entity Framework bir tane oluşturmaya çalışacaktır. Daha fazla bilgi için, [tanımlayıcılardaki](identifiers-entity-sql.md)"diğer ad kuralları" bölümüne bakın.  
  
 Aşağıdaki kurallar, bir satır oluşturucusunda ifade diğer ad için geçerlidir:  
  
- Bir satır oluşturucudaki ifadeler aynı oluşturucuda diğer diğer adlara başvuramaz.  
  
- Aynı satır oluşturucusunun iki ifadesi aynı diğer ada sahip olamaz.  
  
 Satır oluşturucular hakkında daha fazla bilgi için bkz. [Row](row-entity-sql.md).  
  
## <a name="collection-constructors"></a>Koleksiyon oluşturucuları  

 ' De koleksiyon oluşturucuları kullanarak bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değer listesinden bir çoklu küme örneği oluşturabilirsiniz. Oluşturucudaki tüm değerler karşılıklı olarak uyumlu türde olmalıdır `T` ve Oluşturucu türünde bir koleksiyon oluşturur `Multiset<T>` . Örneğin, aşağıdaki ifade bir tamsayılar koleksiyonu oluşturur:  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 Öğelerin türü belirlenemediğinden boş çok kümeli oluşturuculara izin verilmez. Aşağıdakiler geçerli değil:  
  
 `multiset() {}`  
  
 Daha fazla bilgi için bkz. [Çoklu küme](multiset-entity-sql.md).  
  
## <a name="named-type-constructors-namedtype-initializers"></a>Adlandırılmış tür oluşturucuları (NamedType başlatıcıları)  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adlandırılmış karmaşık türlerin ve varlık türlerinin örneklerini oluşturmak için tür oluşturucuların (başlatıcılar) kullanılmasına izin verir. Örneğin, aşağıdaki ifade bir türün örneğini oluşturur `Person` .  
  
 `Person("abc", 12)`  
  
 Aşağıdaki ifade, karmaşık bir türün bir örneğini oluşturur.  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Aşağıdaki ifade, iç içe geçmiş karmaşık bir türün örneğini oluşturur.  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Aşağıdaki ifade, iç içe geçmiş karmaşık türe sahip bir varlık örneği oluşturur.  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Aşağıdaki örnek, bir karmaşık türün özelliğinin null olarak nasıl başlatılacağını gösterir. `MyModel.ZipCode(‘98118’, null)`  
  
 Oluşturucunun bağımsız değişkenlerinin, türün özniteliklerinin bildirimiyle aynı sırada olduğu varsayılır.  
  
 Daha fazla bilgi için bkz. [adlandırılmış tür Oluşturucu](named-type-constructor-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Tür sistemi](type-system-entity-sql.md)
