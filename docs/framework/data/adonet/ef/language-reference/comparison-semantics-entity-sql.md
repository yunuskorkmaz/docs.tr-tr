---
title: Karşılaştırma semantiği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 2184f86ee43f88b0c4cfc1b96e42e2486c17fe5f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765561"
---
# <a name="comparison-semantics-entity-sql"></a>Karşılaştırma semantiği (varlık SQL)
Aşağıdakilerden herhangi birini gerçekleştirme [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri karşılaştırma türü örnekleri içerir:  
  
## <a name="explicit-comparison"></a>Açık karşılaştırma  
 Eşitlik işlemleri:  
  
-   =  
  
-   !=  
  
 Operations sıralama:  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 Null atanabilirlik işlemleri:  
  
-   NULL  
  
-   NULL OLMAYAN  
  
## <a name="explicit-distinction"></a>Açık ayrım  
 Eşitlik fark:  
  
-   FARKLI  
  
-   GRUPLANDIRMA ÖLÇÜTÜ  
  
 Ayrım sıralama:  
  
-   SIRALAMA ÖLÇÜTÜ  
  
## <a name="implicit-distinction"></a>Örtük ayrım  
 İşlemler ve koşulları (eşitlik) ayarlayın:  
  
-   UNION  
  
-   INTERSECT  
  
-   DIŞINDA  
  
-   AYARLAMA  
  
-   ÇAKIŞIYOR  
  
 Öğe koşulları (eşitlik):  
  
-   IN  
  
## <a name="supported-combinations"></a>Desteklenen birleşimleri  
 Aşağıdaki tabloda her türde Karşılaştırma işleçleri tüm desteklenen birleşimleri gösterilmektedir:  
  
|**Türü**|**=**<br /><br /> **\!=**|**GROUP BY**<br /><br /> **FARKLI**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**NULL**<br /><br /> **NULL OLMAYAN**|  
|-|-|-|-|-|-|-|-|  
|Varlık türü|Ref<sup>1</sup>|Tüm özellikleri<sup>2</sup>|Tüm özellikleri<sup>2</sup>|Tüm özellikleri<sup>2</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Ref<sup>1</sup>|  
|karmaşık türü|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Satır|Tüm özellikleri<sup>4</sup>|Tüm özellikleri<sup>4</sup>|Tüm özellikleri<sup>4</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Tüm özellikleri<sup>4</sup>|Throw<sup>3</sup>|  
|ilkel tür|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|  
|Multiset|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Ref|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|Throw|Throw|Evet<sup>5</sup>|  
|İlişkilendirme<br /><br /> türü|Throw<sup>3</sup>|Throw|Throw|Throw|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
  
 <sup>1</sup>belirtilen varlık türü örnekleri başvuruları örtük olarak, aşağıdaki örnekte gösterildiği gibi karşılaştırılır:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Bir varlık örneği için açık bir başvuru karşılaştırılamaz. Bu denenirse özel durum oluşur. Örneğin, aşağıdaki sorguyu bir özel durum oluşturur:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>karmaşık türlerin özellikleri düzleştirilmiş deposuna (tüm özelliklerini karşılaştırılabilir sürece) karşılaştırılabilir olduklarında şekilde gönderilmeden önce. Ayrıca bkz. <sup>4.</sup>  
  
 <sup>3</sup>Entity Framework çalışma zamanı desteklenmeyen durum algılar ve sağlayıcı/deposu çekici olmadan anlamlı bir özel durum oluşturur.  
  
 <sup>4</sup>tüm özellikleri karşılaştırmak için bir girişimde. Text, ntext veya image, gibi karşılaştırılabilir olmayan bir türde bir özellik varsa, bir sunucu özel durum.  
  
 <sup>5</sup>başvuruları tüm ayrı ayrı öğeler karşılaştırılır (Bu varlık kümesi adı ve varlık türünün tüm anahtar özellikleri içerir).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
