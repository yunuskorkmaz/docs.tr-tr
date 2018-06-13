---
title: SATIR (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: eb5062399eec9d8453d8922e05698ca9124d94d7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765613"
---
# <a name="row-entity-sql"></a>SATIR (varlık SQL)
Bir veya daha fazla değer anonim, yapısal olarak yazılan kayıtları oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir satır türü oluşturmak için bir değer döndürür herhangi bir geçerli sorgu ifade.  
  
 `alias`  
 Bir satır türü için belirtilen değer için bir diğer ad belirtir. Bir diğer ad sağlanmazsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dayalı bir diğer ad oluşturmak çalışır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer adı oluşturma kuralları.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Satır türü.  
  
## <a name="remarks"></a>Açıklamalar  
 Satır kurucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir veya daha fazla değer anonim, yapısal olarak yazılan kayıtları oluşturmak için. Bir satır oluşturucusunda sonuç türü, alan türlerini satır oluşturmak için kullanılan değerlerin türü için karşılık gelen bir satır türüdür. Örneğin, aşağıdaki deyim türünde bir değer oluşturur `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Row kurucusunda bir ifade için bir diğer ad belirtmezseniz, Entity Framework oluşturur dener. Daha fazla bilgi için "Diğer ad kuralları" bölümüne bakın [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) konu.  
  
 Row kurucusunda ifade yumuşatma aşağıdaki kurallar geçerlidir:  
  
-   Bir satır oluşturucusunda ifadelerinde başka diğer adlar aynı oluşturucuda başvuruda bulunamaz.  
  
-   İki ifadeye aynı row kurucusunda aynı ada sahip olamaz.  
  
 Sorgu oluşturucular hakkında daha fazla bilgi için bkz: [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgu satırı işleci anonim, yapısal olarak yazılan kayıtları oluşturmak için kullanılır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oluşturma Türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Tür Tanımları](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
