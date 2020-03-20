---
title: Karşılaştırma Semantik (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150460"
---
# <a name="comparison-semantics-entity-sql"></a>Karşılaştırma Semantik (Varlık SQL)
Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçlerden herhangi birinin gerçekleştirimi, tür örneklerinin karşılaştırmasını içerir:  
  
## <a name="explicit-comparison"></a>Açık karşılaştırma  
 Eşitlik işlemleri:  
  
- =  
  
- !=  
  
 Sipariş işlemleri:  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 Nullability işlemleri:  
  
- NULL MU  
  
- NULL Değİl  
  
## <a name="explicit-distinction"></a>Açık ayrım  
 Eşitlik ayrımı:  
  
- DISTINCT  
  
- GROUP BY  
  
 Sıralama ayrımı:  
  
- SİPARİŞ VEREN  
  
## <a name="implicit-distinction"></a>Örtük ayrım  
 İşlemleri ve yüklemleri (eşitlik) ayarlama:  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 Madde yüklemleri (eşitlik):  
  
- IN  
  
## <a name="supported-combinations"></a>Desteklenen Kombinasyonlar  
 Aşağıdaki tablo, her tür için karşılaştırma işleçlerinin desteklenen tüm birleşimlerini gösterir:  
  
|**Tür**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **Farklı**|**Birliği**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **Ayarlamak**<br /><br /> **OVERLAPS**|**Inç**|**< <=**<br /><br /> **> >=**|**SİPARİŞ VEREN**|**NULL MU**<br /><br /> **NULL Değİl**|  
|-|-|-|-|-|-|-|-|  
|Varlık türü|Hakem<sup>1</sup>|Tüm özellikler<sup>2</sup>|Tüm özellikler<sup>2</sup>|Tüm özellikler<sup>2</sup>|<sup>3'e</sup> at|<sup>3'e</sup> at|Hakem<sup>1</sup>|  
|Karmaşık tür|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|  
|Satır|Tüm özellikler<sup>4</sup>|Tüm özellikler<sup>4</sup>|Tüm özellikler<sup>4</sup>|<sup>3'e</sup> at|<sup>3'e</sup> at|Tüm özellikler<sup>4</sup>|<sup>3'e</sup> at|  
|İlkel tip|Sağlayıcıya özel|Sağlayıcıya özel|Sağlayıcıya özel|Sağlayıcıya özel|Sağlayıcıya özel|Sağlayıcıya özel|Sağlayıcıya özel|  
|Multiset|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|  
|Referans|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|Throw|Throw|Evet<sup>5</sup>|  
|Derneği<br /><br /> type|<sup>3'e</sup> at|Throw|Throw|Throw|<sup>3'e</sup> at|<sup>3'e</sup> at|<sup>3'e</sup> at|  
  
 <sup>1.1.2</sup> Verilen varlık türü örneklerinin başvuruları, aşağıdaki örnekte gösterildiği gibi örtülü olarak karşılaştırılır:  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Varlık örneği açık bir başvuruyla karşılaştırılamaz. Bu denenirse, bir özel durum atılır. Örneğin, aşağıdaki sorgu bir özel durum atar:  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <sup>2.000</sup> Karmaşık türlerin özellikleri mağazaya gönderilmeden önce düzleşir, böylece karşılaştırılabilir hale gelir (tüm özellikleri karşılaştırılabilir olduğu sürece). Ayrıca <sup>bkz. 4.</sup>  
  
 <sup>3.2.2</sup> Varlık Çerçevesi çalışma zamanı, desteklenmeyen servis talebialgılar ve sağlayıcı/mağazayla etkileşime girmeden anlamlı bir özel durum oluşturur.  
  
 <sup>4.2.2</sup> Tüm özellikleri karşılaştırmak için bir girişimde bulunulr. Metin, metin veya resim gibi karşılaştırılabilir olmayan bir türde bir özellik varsa, sunucu özel durumu atılabilir.  
  
 <sup>5.000</sup> Başvuruların tüm bireysel öğeleri karşılaştırılır (bu varlık kümesi adını ve varlık türünün tüm temel özelliklerini içerir).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
