---
title: GROUPPARTITION (varlık SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774731"
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (varlık SQL)
Toplama ilişkili olduğunu geçerli grubu bölümü öngörülen bağımsız değişken değerleri koleksiyonunu döndürür. `GroupPartition` Toplama grup tabanlı bir toplama ve hiçbir koleksiyon tabanlı bir biçimde.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki sorgu, ürün ve sipariş satırı miktarları her ürün başına koleksiyonunu bir liste oluşturur:  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 Aşağıdaki iki sorguları anlamsal olarak eşit:  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 `GROUPPARTITION` İşleci, kullanıcı tanımlı toplama işlevleri ile birlikte kullanılabilir.  
  
 `GROUPPARTITION` Gruplandırılmış giriş kümesinde bir başvuru tutan bir özel toplama işlecidir. Bu başvuru, sorguda GROUP BY kapsamında olduğu her yerde kullanılabilir. Örneğin,  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Bir normal GROUP BY, gruplandırma sonuçlarını gizlidir. Bu gibi durumlarda, sonuçları yalnızca bir toplama işlevinde kullanabilirsiniz. Gruplandırma sonuçlarını görmek için gruplandırma ve bir alt sorgu kullanarak giriş sonuçları ilişkilendirin gerekir. Aşağıdaki iki sorguları eşdeğerdir:  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Örnekte görüldüğü gibi toplama GROUPPARTITION işleci sonra GROUPING set giriş için bir başvuru almak kolaylaştırır.  
  
 GROUPPARTITION işleci belirtebilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleç bir ifadede giriş kullandığınızda `expression` parametresi.  
  
 Örneği için tüm Grup bölümüne aşağıdaki giriş ifadelerin geçerli şunlardır:  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, GROUP BY yan tümcesi ile GROUPPARTITION yan tümcesini kullanmayı gösterir. GROUP BY yan tümcesi grupları `SalesOrderHeader` varlıklar tarafından kendi `Contact`. GROUPPARTITION yan tümcesi sonra projeleri `TotalDue` ondalık bir koleksiyonda bunun sonucunda, her grup için özellik.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
