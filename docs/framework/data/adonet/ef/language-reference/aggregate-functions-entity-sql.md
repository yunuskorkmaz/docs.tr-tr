---
title: Toplama işlevleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: b01c7dca675e79c61b87bcc1fb30455286db3118
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489969"
---
# <a name="aggregate-functions-entity-sql"></a>Toplama işlevleri (varlık SQL)
Toplama, bir skaler bir koleksiyona bir grup işleminin bir parçası olarak basit bir dil yapıdır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki biçimde toplamlar gelir:  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifadede herhangi bir yere kullanılabilir işlevler koleksiyonu. Bu toplama işlevleri projeksiyonlar ve hareket doğrulamaları koleksiyonlarda kullanarak içerir. Koleksiyon işlevlerdir toplamalar belirtme tercih edilen modu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
- GROUP BY yan tümcesine sahip sorgu ifadelerinde Grup toplar. Transact-SQL olduğu gibi Grup toplamları DISTINCT ve tüm değiştiricilere birleşik giriş olarak kabul edin.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifade bir toplama işlevi olarak yorumlamak ilk olarak çalışır ve deyim bir SELECT deyimi bağlamında, yorumlar, bir grup toplama.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak adlandırılan özel bir toplama işleci tanımlar [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md). Bu işleç, gruplandırılmış giriş kümesinde bir başvuru almak sağlar. GROUP BY yan tümcesinin sonuçlarını grubu toplama veya toplama işlevleri başka yerde nerede kullanılabilir bu daha gelişmiş sorgular, gruplandırma sağlar.  
  
## <a name="collection-functions"></a>Toplama işlevleri  
 Toplama işlevleri koleksiyonlarda çalışır ve bir skaler değer döndürür. Örneğin, varsa `orders` tüm oluşan bir koleksiyondur `orders`, sevk tarihten şu ifadeyle hesaplayabilirsiniz:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Grup toplamları  
 Grup toplamalar, GROUP BY yan tümcesi tarafından tanımlanan bir grup sonucu üzerinden hesaplanır. GROUP BY yan tümcesi veri gruplara böler. Her grup için sonuç, toplama işlevi uygulanır ve ayrı bir toplama toplam hesaplaması için girdi olarak her gruba öğeleri kullanılarak hesaplanır. GROUP BY yan tümcesi ifade adlarının, toplamlar ve sabit ifadeler yalnızca gruplandırma seçin ifadesinde kullanıldığında sahip, projeksiyonda bulunması veya ORDER BY yan tümcesi.  
  
 Aşağıdaki örnek, her ürün için sıralı ortalama miktarı hesaplar.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 Bir açık GROUP BY yan tümcesi olmadan toplama grubu SELECT deyimini olması mümkündür. Tüm öğeleri, eşdeğer bir sabit üzerinde temel alan bir gruplama belirtme kullanım durumu için tek bir grup olarak kabul edilir.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 WHERE yan tümcesi ifade görünür olur aynı ad çözümleme kapsamı kullanarak GROUP BY yan tümcesinde kullanılan ifadeler değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
