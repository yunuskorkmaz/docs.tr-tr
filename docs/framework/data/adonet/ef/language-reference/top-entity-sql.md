---
title: ÜST (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 25afda64aafcd5a97dee7ad4cee25b152ef55907
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764664"
---
# <a name="top-entity-sql"></a>ÜST (varlık SQL)
SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştiricisi izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir. TOP alt yan tümcesi, yalnızca ilk satır kümesini sorgu sonuç döndürülür belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Sayısal ifade döndürülecek satır sayısını belirtir. `n` tek bir sayısal dize veya tek bir parametre olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 TOP ifadesi tek sayısal sabit değer ya da tek bir parametre olması gerekir. Bir sabit değişmez değeri kullanılırsa, değişmez değer türü örtük olarak yükseltilebilir EDM.Int64 (bayt, int16, int32 veya Int64 veya EDM.Int64 için yükseltilebilir türü eşlendiği herhangi bir sağlayıcı türü) için olmalıdır ve değeri sıfırdan büyük veya sıfıra eşit olmalıdır. Aksi takdirde bir özel durum oluşturulur. Bir ifade olarak kullanılan bir parametre, parametre türü de EDM.Int64 için örtük olarak yükseltilebilir olmalıdır, ancak parametre değerlerini geç ilişkisindeki çünkü asıl parametre değerinin hiçbir doğrulama derleme sırasında olacaktır.  
  
 Sabit TOP ifadesi örneği verilmiştir:  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 Parametreli TOP ifadesi örneği verilmiştir:  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 Sorgu sıralanmış sürece üst belirleyici değildir. Belirleyici bir sonuç gerekiyorsa kullanın [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi. TOP ve SKIP/LIMIT karşılıklı olarak birbirini dışlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu üst sorgu sonuç döndürülecek üst bir satır belirlemek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
