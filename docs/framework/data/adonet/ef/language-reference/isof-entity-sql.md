---
title: ISOF (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: dbea0c3a0087c88bf5ffda7b921764b8a0f9f21d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465453"
---
# <a name="isof-entity-sql"></a>ISOF (varlık SQL)
Belirtilen tür veya onun alt türlerinden birini bir ifadenin türü olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Türünü belirlemek için tüm geçerli sorgu ifadesi.  
  
 DEĞİL  
 EDM olumsuz duruma getirir. Boolean sonucu olduğundan.  
  
 YALNIZCA  
 OLDUĞUNDAN, döndüren belirtir `true` yalnızca `expression` türünde `type` ve herhangi bir alt türleri.  
  
 `type`  
 Sınanacak tür `expression` karşı. İsim uzayıyla nitelenmiş tür olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` varsa `expression` olan türü T, T bir taban türü veya türetilmiş bir tür ise `type`; null ise `expression` çalışma zamanında null; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İfadeleri `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` sözdizimsel olarak eşdeğer `NOT (expression IS OF (type))` ve `NOT (expression IS OF (ONLY type))`sırasıyla.  
  
 Aşağıdaki tabloda davranışını gösteren `IS OF` bazı tipik ve köşe desenleri üzerinden işleci. Sağlayıcı çağrılır önce tüm istemci tarafında özel durumlar:  
  
|Desen|Davranış|  
|-------------|--------------|  
|null olduğundan, (EntityType)|Oluşturur|  
|null olduğundan, (ComplexType)|Oluşturur|  
|null olduğundan, (RowType)|Oluşturur|  
|KABUL (null AS EntityType) olduğundan, (EntityType)|DBNull döndürür|  
|KABUL (null AS ComplexType) olduğundan, (ComplexType)|Oluşturur|  
|KABUL (null AS RowType) olduğundan, (RowType)|Oluşturur|  
|EntityType olan (EntityType),|True/false döndürür|  
|ComplexType olduğu (ComplexType),|Oluşturur|  
|RowType olduğu (RowType),|Oluşturur|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu olan işlecini bir sorgu ifadesinde türü belirlemek için kullanır ve ardından OnsiteCourse türünden nesnelerin bir koleksiyonunu kurs türdeki bir nesneyi dönüştürmek için kabul işlecini kullanır. Sorgu dayanır [Okul modeli](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
