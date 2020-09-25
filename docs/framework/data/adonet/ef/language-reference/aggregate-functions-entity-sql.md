---
title: Toplama Işlevleri (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: 308670f04b9a04b1fff77ece08deb39c8c4081d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198086"
---
# <a name="aggregate-functions-entity-sql"></a>Toplama Işlevleri (Entity SQL)

Toplama, bir koleksiyonu bir grup işleminin parçası olarak skaler olarak sıkıştırmak için bir dil yapısıdır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] toplamalar iki biçimde gelir:  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifadede herhangi bir yerde kullanılabilecek olan koleksiyon işlevleri. Bu, toplamalar üzerinde işlem yapan projeksiyonlar ve koşullarda toplama işlevlerinin kullanılmasını içerir. Koleksiyon işlevleri, içinde toplamalar belirtmenin tercih edilen modudur [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
- GROUP BY yan tümcesine sahip sorgu ifadelerinde grup toplamaları. Transact-SQL ' de olduğu gibi, Grup toplamaları toplama girişi için DISTINCT ve ALL olarak değiştirici kabul eder.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İlk olarak bir ifadeyi koleksiyon işlevi olarak yorumlamaya çalışır ve ifade bir SELECT ifadesinin bağlamında ise, bunu bir grup toplaması olarak yorumlar.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)][Grouppartition](grouppartition-entity-sql.md)adlı özel bir toplama işleci tanımlar. Bu işleç, gruplandırılmış giriş kümesine bir başvuru almanızı sağlar. Bu, GROUP BY yan tümcesinin sonuçlarının grup toplama veya toplama işlevleri dışında bir yerde kullanılabileceği daha gelişmiş gruplandırma sorgularına izin verir.  
  
## <a name="collection-functions"></a>Koleksiyon Işlevleri  

 Koleksiyon işlevleri koleksiyonlar üzerinde çalışır ve skaler bir değer döndürür. Örneğin, `orders` bir koleksiyonu ise `orders` , en erken sevk tarihini aşağıdaki ifadeyle hesaplayabilirsiniz:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Grup toplamaları  

 Grup toplamaları GROUP BY yan tümcesi tarafından tanımlanan bir grup sonucu üzerinden hesaplanır. GROUP BY yan tümcesi, verileri gruplar halinde gruplandırır. Sonuç içindeki her grup için, toplama işlevi uygulanır ve ayrı bir toplama, her bir gruptaki öğeler toplam hesaplamaya giriş olarak kullanılarak hesaplanır. Bir GROUP BY yan tümcesi bir SELECT ifadesinde kullanıldığında, Projection, HAVING veya ORDER BY yan tümcesinde yalnızca gruplama ifadesi adları, toplamalar veya sabit ifadeler bulunabilir.  
  
 Aşağıdaki örnek, her ürün için sipariş edilen ortalama miktarı hesaplar.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 SELECT ifadesinde açık bir GROUP BY yan tümcesi olmadan bir grup toplaması olması mümkündür. Tüm öğeler tek bir grup olarak değerlendirilir, bu da bir sabiti temel alan bir gruplama belirtme durumuna eşdeğerdir.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 GROUP BY yan tümcesinde kullanılan ifadeler WHERE yan tümcesi ifadesinde görünür olacak aynı ad çözümleme kapsamı kullanılarak değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](functions-entity-sql.md)
