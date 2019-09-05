---
title: Karşılaştırma semantiği (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: da7b8f662d10376abd649e674701b43b7b740a6f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251190"
---
# <a name="comparison-semantics-entity-sql"></a>Karşılaştırma semantiği (Entity SQL)
Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçlerden herhangi birini gerçekleştirmek, tür örneklerinin karşılaştırmasını içerir:  
  
## <a name="explicit-comparison"></a>Açık karşılaştırma  
 Eşitlik işlemleri:  
  
- =  
  
- !=  
  
 Sıralama işlemleri:  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 Null değer alabilirlik işlemleri:  
  
- NULL  
  
- NULL DEĞIL  
  
## <a name="explicit-distinction"></a>Açık ayrım  
 Eşitlik ayrımı:  
  
- AYRI  
  
- GROUP BY  
  
 Sıralama ayrımı:  
  
- SIRALAMA ÖLÇÜTÜ  
  
## <a name="implicit-distinction"></a>Örtük ayrım  
 İşlemleri ve koşulları ayarlama (eşitlik):  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 Öğe doğrulamaları (eşitlik):  
  
- IN  
  
## <a name="supported-combinations"></a>Desteklenen birleşimler  
 Aşağıdaki tabloda her tür türü için karşılaştırma işleçleri 'nin desteklenen tüm birleşimleri gösterilmektedir:  
  
|**Tür**|**=**<br /><br /> **\!=**|**GROUP BY**<br /><br /> **AYRI**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**NULL**<br /><br /> **NULL DEĞIL**|  
|-|-|-|-|-|-|-|-|  
|Varlık türü|Başvuru<sup>1</sup>|Tüm Özellikler<sup>2</sup>|Tüm Özellikler<sup>2</sup>|Tüm Özellikler<sup>2</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Başvuru<sup>1</sup>|  
|Karmaşık tür|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Satır|Tüm Özellikler<sup>4</sup>|Tüm Özellikler<sup>4</sup>|Tüm Özellikler<sup>4</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Tüm Özellikler<sup>4</sup>|Throw<sup>3</sup>|  
|İlkel tür|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|  
|Değerlerden|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Ref|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|Throw|Throw|Evet<sup>5</sup>|  
|Kaldırma<br /><br /> türü|Throw<sup>3</sup>|Throw|Throw|Throw|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
  
 <sup>1</sup> Aşağıdaki örnekte gösterildiği gibi, belirtilen varlık türü örneklerinin başvuruları örtük olarak karşılaştırılır:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Bir varlık örneği açık bir başvuruyla karşılaştırılamaz. Bu denendiğinde, bir özel durum oluşturulur. Örneğin, aşağıdaki sorgu bir özel durum oluşturur:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup> Karmaşık türlerin özellikleri depoya gönderilmeden önce düzleştirilir, bu nedenle karşılaştırılabilir hale gelir (tüm özellikleri karşılaştırılabilir olduğu sürece). Ayrıca bkz <sup>. 4.</sup>  
  
 <sup>3</sup> Entity Framework çalışma zamanı, desteklenmeyen durumu algılar ve sağlayıcıyı/mağazayı bildirmeden anlamlı bir özel durum oluşturur.  
  
 <sup>4</sup> Tüm özellikleri karşılaştırmak için bir girişimde bulunuldu. Metin, n metin veya görüntü gibi karşılaştırılabilir olmayan bir türde bir özellik varsa sunucu özel durumu oluşabilir.  
  
 <sup>5</sup> Başvuruların tüm ayrı öğeleri karşılaştırılır (Bu, varlık kümesi adını ve varlık türünün tüm anahtar özelliklerini içerir).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
