---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 19df566c254a3f3202eb3554ab43ee0d7c944181
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833757"
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (Entity SQL)
Toplamanın ilgili olduğu geçerli grup bölümünün yansıtıldıkları bağımsız değişken değerlerinin bir koleksiyonunu döndürür. @No__t-0 toplama, grup tabanlı bir kümedir ve koleksiyon tabanlı bir form içermez.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki sorgu ürünlerin bir listesini ve her bir ürün için sipariş satırı miktarları koleksiyonunu üretir:  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 Aşağıdaki iki sorgu anlamsal olarak eşittir:  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 @No__t-0 işleci Kullanıcı tanımlı toplama işlevleriyle birlikte kullanılabilir.  
  
`GROUPPARTITION`, gruplandırılmış giriş kümesine yönelik bir başvuruyu tutan özel bir toplama işleçtir. Bu başvuru, GROUP BY Scope içinde olan sorguda herhangi bir yerde kullanılabilir. Örneğin:
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 Normal `GROUP BY` ile gruplandırma sonuçları gizlidir. Sonuçları yalnızca bir toplama işlevinde kullanabilirsiniz. Gruplandırmanın sonuçlarını görmek için gruplandırma sonuçlarını ve giriş kümesini bir alt sorgu kullanarak ilişkilendirmeniz gerekir. Aşağıdaki iki sorgu eşdeğerdir:  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 Bu örnekte görüldüğü gibi, GROUPPARTITION toplama operatörü, gruplandırma işleminden sonra giriş kümesine bir başvuru almayı kolaylaştırır.  
  
 GROUPPARTITION işleci, `expression` parametresini kullandığınızda işleç girişinde herhangi bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifadesi belirtebilir.  
  
 Örneğin, grup bölümüne aşağıdaki giriş ifadelerinin tümü geçerlidir:  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, GROUP BY yan tümcesi ile GROUPPARTITION yan tümcesinin nasıl kullanılacağını göstermektedir. GROUP BY yan tümcesi, `SalesOrderHeader` varlıklarını `Contact` olarak gruplandırır. GROUPPARTITION yan tümcesi daha sonra her grup için `TotalDue` özelliğini projeler, bu da ondalık bir toplama sonucu oluşur.  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
