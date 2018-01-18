---
title: "GROUPPARTITION (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09d4d1e6d2e69d805c316f60e6d6e91d094e68cb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (varlık SQL)
Toplama ilişkili olduğunu geçerli Grup bölümünün öngörülen bağımsız değişken değerleri koleksiyonunu döndürür. `GroupPartition` Toplama bir grup tabanlı toplama olduğundan ve hiçbir koleksiyon tabanlı bir biçime sahip.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki sorgu, ürünler ve her ürün başına sipariş satırı miktarları koleksiyonu listesini üretir:  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 Aşağıdaki iki sorgular anlamsal olarak eşit:  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 `GROUPPARTITION` İşleci, kullanıcı tanımlı toplama işlevleri ile birlikte kullanılabilir.  
  
 `GROUPPARTITION`Gruplandırılmış giriş kümesine başvuru tutan bir özel toplama işlecidir. Bu başvuru, sorguya grupla kapsam içinde olduğu herhangi bir yerde kullanılabilir. Örneğin,  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Normal GROUP BY ile gruplandırma sonuçlarını gizlenir. Sonuçları bir toplama işlevinde yalnızca kullanabilirsiniz. Gruplandırma sonuçlarını görmek için gruplandırma ve bir alt sorgu kullanarak ayarlamak giriş sonuçları ilişkilendirmek sahip. Aşağıdaki iki sorgular eşdeğerdir:  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Örnekte görüldüğü gibi GROUPPARTITION Toplama işleci sonra GROUPING set giriş için bir başvuru almak kolaylaştırır.  
  
 GROUPPARTITION işleci belirtebilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlecindeki ifade giriş kullandığınızda `expression` parametresi.  
  
 Örneği için tüm Grup bölümü aşağıdaki giriş ifadeleri geçerlidir:  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek GROUP BY yan tümcesinde GROUPPARTITION yan tümcesi kullanmayı gösterir. GROUP BY yan tümcesi grupları `SalesOrderHeader` varlıklar tarafından kendi `Contact`. GROUPPARTITION yan tümcesi sonra projeleri `TotalDue` ondalık koleksiyonunda kaynaklanan her grup için özelliği.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
