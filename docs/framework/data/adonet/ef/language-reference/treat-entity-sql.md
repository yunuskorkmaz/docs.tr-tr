---
title: KABUL (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 932f335bf6a502b031dcf09b8050e278a0bbe9f8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763982"
---
# <a name="treat-entity-sql"></a>KABUL (varlık SQL)
Belirli bir temel türdeki bir nesneyi belirtilen türetilen türde bir nesne olarak değerlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir varlık döndüren herhangi bir geçerli sorgu ifade.  
  
> [!NOTE]
>  Belirtilen ifade türü bir alt belirtilen veri türü olmalıdır veya veri türünün bir alt tür bir ifade olması gerekir.  
  
 `type`  
 Bir varlık türü. Türü bir ad alanı tarafından nitelenmiş olmalıdır.  
  
> [!NOTE]
>  Belirtilen ifade belirtilen veri türünün bir alt olmalıdır veya alt ifade türünün veri türü olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Belirtilen veri türünde bir değer.  
  
## <a name="remarks"></a>Açıklamalar  
 KABUL üst türe çevirme ilgili sınıflar arasındaki gerçekleştirmek için kullanılır. Örneğin, varsa `Employee` türetilen `Person` ve p türü `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts genel bir `Person` için örnek `Employee`; diğer bir deyişle, p davranmanız tanır `Employee`.  
  
 KABUL aşağıdaki gibi bir sorgu burada yapabileceğiniz devralma senaryolarda kullanılır:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 Bu sorgu upcasts `Person` varlıklara `Employee` türü. P değeri değil gerçekte türü olup olmadığını `Employee`, ifade değerini verir `null`.  
  
> [!NOTE]
>  Belirtilen ifade `Employee` belirtilen veri türünün bir alt olmalıdır `Person`, veya alt ifade türünün veri türü olmalıdır. Aksi takdirde, ifade bir derleme zamanı hataya neden olur.  
  
 Aşağıdaki tabloda, bazı tipik desenleri ve daha az görülen bazı desenleri kabul davranışını gösterir. Sağlayıcı çağrılır önce tüm istemci tarafındaki özel durumlar:  
  
|Desen|Davranış|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Döndürür `DbNull`.|  
|`TREAT (null AS ComplexType)`|Bir özel durum oluşturur.|  
|`TREAT (null AS RowType)`|Bir özel durum oluşturur /|  
|`TREAT (EntityType AS EntityType)`|Döndürür `EntityType` veya `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Bir özel durum oluşturur.|  
|`TREAT (RowType AS RowType)`|Bir özel durum oluşturur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu indirmelere türünde bir nesne OnsiteCourse türündeki nesneler koleksiyonuna dönüştürmek için kabul işleci kullanır. Sorgu dayanır [Okul modeli](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Null Değer Atanabilir Yapılandırılmış Türler](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
