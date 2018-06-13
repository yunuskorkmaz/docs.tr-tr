---
title: Toplama işlevleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: 63e366f323b38a24c4d067681b47d8a8b96125b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765587"
---
# <a name="aggregate-functions-entity-sql"></a>Toplama işlevleri (varlık SQL)
Bir toplama skaler bir koleksiyona bir grup işleminin bir parçası olarak toplar bir dil yapıdır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Toplamlar iki biçimde getirir:  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifadede herhangi bir yerde kullanılan işlevler koleksiyonu. Bu toplama işlevleri tahminleri ve hareket koşulları üzerinde koleksiyonları kullanarak içerir. Koleksiyon işlevlerdir Toplamaların belirtme tercih edilen modu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
-   GROUP BY yan tümcesi bulunan sorgu ifadelerinde Grup toplar. Olarak [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], Grup toplamalar DISTINCT ve tüm değiştiricileri birleşik giriş olarak kabul edin.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İlk ifade bir toplama işlevi olarak yorumlamaya çalışır ve ifade bir SELECT deyimi bağlamında, yorumlar, bir grup toplama olarak.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adlı özel bir toplama işleci tanımlar [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md). Bu işleç gruplandırılmış giriş ayarlamak için bir başvuru sağlar. GROUP BY yan tümcesi sonuçlarını Grup toplama veya toplama işlevleri başka yerde kullanıldığı bu sorgular, gruplandırma daha gelişmiş sağlar.  
  
## <a name="collection-functions"></a>Toplama işlevleri  
 Toplama işlevleri koleksiyonlar üzerinde çalışır ve skaler bir değer döndürür. Örneğin, varsa `orders` tüm oluşan bir koleksiyondur `orders`, aşağıdaki ifade en erken sevk tarihi hesaplayabilirsiniz:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Grup toplar  
 Grup toplamları GROUP BY yan tümcesi tarafından tanımlanan bir grup sonucu üzerinden hesaplanır. GROUP BY yan tümcesi gruplar halinde veri bölümler. Her grup için sonuç, toplama işlevi uygulanır ve ayrı bir toplama giriş toplama hesaplama olarak her grupta öğeleri kullanılarak hesaplanır. GROUP BY yan tümcesi yalnızca ifade adları, toplamalar veya sabit ifadeler gruplandırma bir SELECT ifadesinde kullanıldığında sahip, projeksiyon bulunması veya BY yan tümcesi sipariş.  
  
 Aşağıdaki örnekte, her ürün için sipariş edilen ortalama miktarı hesaplar.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 Bir açık GROUP BY yan tümcesi olmadan birleşik bir grup seçin ifadesinde olması mümkündür. Tüm öğeler tek bir grup, bir sabit üzerinde alan bir gruplama belirtmenin durumuna eşdeğer olarak kabul edilir.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 GROUP BY yan tümcesinde kullanılan ifadeleri, WHERE yan tümcesi ifade görünür olacak aynı ad çözümleme kapsamı kullanarak değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
