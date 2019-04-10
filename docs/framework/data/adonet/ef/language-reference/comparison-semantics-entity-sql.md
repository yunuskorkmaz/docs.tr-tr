---
title: Karşılaştırma semantiği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 6b4c4177ebd6c45e00a1ac7774e40a43e0c14a74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083341"
---
# <a name="comparison-semantics-entity-sql"></a>Karşılaştırma semantiği (varlık SQL)
Aşağıdakilerden herhangi birini gerçekleştiren [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri karşılaştırma türü örnekleri içerir:  
  
## <a name="explicit-comparison"></a>Açık karşılaştırma  
 Eşitlik işlemleri:  
  
-   =  
  
-   !=  
  
 İşlem sırası:  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 Öğesinin işlemler:  
  
-   IS NULL  
  
-   NULL DEĞİL  
  
## <a name="explicit-distinction"></a>Açık ayrımı  
 Eşitlik fark:  
  
-   DISTINCT  
  
-   GROUP BY  
  
 Ayrım sıralama:  
  
-   SIRALAMA ÖLÇÜTÜ  
  
## <a name="implicit-distinction"></a>Örtük ayrımı  
 İşlemler ve koşullarına (eşitlik) ayarlayın:  
  
-   UNION  
  
-   INTERSECT  
  
-   EXCEPT  
  
-   SET  
  
-   OVERLAPS  
  
 Öğe koşullarına (eşitlik):  
  
-   IN  
  
## <a name="supported-combinations"></a>Desteklenen kombinasyonlar  
 Karşılaştırma işleçleri türü her türdeki tüm desteklenen birleşimleri aşağıdaki tabloda gösterilmiştir:  
  
|**Tür**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**SIRALAMA ÖLÇÜTÜ**|**IS NULL**<br /><br /> **NULL DEĞİL**|  
|-|-|-|-|-|-|-|-|  
|varlık türü|Ref<sup>1</sup>|Tüm özellikleri<sup>2</sup>|Tüm özellikleri<sup>2</sup>|Tüm özellikleri<sup>2</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Ref<sup>1</sup>|  
|Karmaşık tür|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Satır|Tüm özellikleri<sup>4</sup>|Tüm özellikleri<sup>4</sup>|Tüm özellikleri<sup>4</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Tüm özellikleri<sup>4</sup>|Throw<sup>3</sup>|  
|temel tür|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|Sağlayıcıya özgü|  
|multiset|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|başvuru|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|Evet<sup>5</sup>|throw|throw|Evet<sup>5</sup>|  
|İlişkilendirme<br /><br />  türü|Throw<sup>3</sup>|throw|throw|throw|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
  
 <sup>1</sup>belirtilen varlık türü örnekleri başvurularına örtük olarak, aşağıdaki örnekte gösterildiği gibi karşılaştırılır:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Bir varlık örneği için açık bir başvuru karşılaştırılamaz. Bu girişiminde bulunulursa, bir özel durum oluşturulur. Örneğin, aşağıdaki sorgu, bir özel durum oluşturur:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>karmaşık türler, Özellikler düzleştirilmiş Mağaza'ya (bunların tüm özelliklerini karşılaştırılabilir olduğu sürece) bunlar karşılaştırılabilir eşlenmelerine gönderilmeden önce. Ayrıca bkz: <sup>4.</sup>  
  
 <sup>3</sup>Entity Framework çalışma zamanı desteklenmeyen durum algılar ve ilgi çekici sağlayıcısı depolama olmadan anlamlı bir özel durum oluşturur.  
  
 <sup>4</sup>tüm özellikleri karşılaştırmak için bir girişimde. Metin, n metin veya görüntü gibi benzer olmayan bir türde bir özellik yoksa, bir sunucu özel durum.  
  
 <sup>5</sup>başvuruları tüm tek tek öğelerine kıyasla (Bu varlık kümesinin adı ve varlık türü tüm anahtar özelliklerini içerir).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
