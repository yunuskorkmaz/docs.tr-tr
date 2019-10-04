---
title: Karşılaştırma semantiği (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 8d7868b0166f0a18824ec25e6cdf639deec665ac
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833940"
---
# <a name="comparison-semantics-entity-sql"></a>Karşılaştırma semantiği (Entity SQL)
Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçlerinden herhangi birini gerçekleştirmek, tür örneklerinin karşılaştırmasını içerir:  
  
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
  
- AYRı  
  
- GROUP BY  
  
 Sıralama ayrımı:  
  
- SİPARİŞ VEREN  
  
## <a name="implicit-distinction"></a>Örtük ayrım  
 İşlemleri ve koşulları ayarlama (eşitlik):  
  
- UNION  
  
- KESIŞ  
  
- KULLANıLDıKLARı  
  
- KURMAK  
  
- ÇAKıŞ  
  
 Öğe doğrulamaları (eşitlik):  
  
- IN  
  
## <a name="supported-combinations"></a>Desteklenen birleşimler  
 Aşağıdaki tabloda her tür türü için karşılaştırma işleçleri 'nin desteklenen tüm birleşimleri gösterilmektedir:  
  
|**Tür**|**=**<br /><br /> **!=**|**GRUPLANDıRMA ÖLÇÜTÜ**<br /><br /> **AYRı**|**BIRLEŞIM**<br /><br /> **KESIŞ**<br /><br /> **KULLANıLDıKLARı**<br /><br /> **KURMAK**<br /><br /> **ÇAKıŞ**|**'NDAKI**|**< < =**<br /><br /> **> > =**|**SıRALAMA ÖLÇÜTÜ**|**NULL**<br /><br /> **NULL DEĞIL**|  
|-|-|-|-|-|-|-|-|  
|varlık türü|Başvuru<sup>1</sup>|Tüm Özellikler<sup>2</sup>|Tüm Özellikler<sup>2</sup>|Tüm Özellikler<sup>2</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Başvuru<sup>1</sup>|  
|karmaşık tür|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Sırada|Tüm Özellikler<sup>4</sup>|Tüm Özellikler<sup>4</sup>|Tüm Özellikler<sup>4</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Tüm Özellikler<sup>4</sup>|Throw<sup>3</sup>|  
|İlkel tür|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|  
|Değerlerden|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|ref|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|yaratır|yaratır|Evet<sup>5</sup>|  
|kaldırma<br /><br /> type|Throw<sup>3</sup>|yaratır|yaratır|yaratır|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
  
 <sup>1</sup> Aşağıdaki örnekte gösterildiği gibi, belirtilen varlık türü örneklerinin başvuruları örtük olarak karşılaştırılır:  
  
```sql  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Bir varlık örneği açık bir başvuruyla karşılaştırılamaz. Bu denendiğinde, bir özel durum oluşturulur. Örneğin, aşağıdaki sorgu bir özel durum oluşturur:  
  
```sql  
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

- [Entity SQL genel bakış](entity-sql-overview.md)
