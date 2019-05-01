---
title: KABUL (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: e1382c4daa513477011a1d1c2132840dfae84de0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879573"
---
# <a name="treat-entity-sql"></a>KABUL (varlık SQL)
Belirli bir temel türü bir nesneyi belirtilen türetilmiş bir türde bir nesne olarak değerlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir varlık döndürür herhangi bir geçerli ifade.  
  
> [!NOTE]
>  Belirtilen ifadenin belirtilen veri türünün bir alt türünde olmalıdır veya veri türü bir alt ifadenin türü olmalıdır.  
  
 `type`  
 Bir varlık türü. Türü bir ad alanı tarafından nitelendirilmelidir.  
  
> [!NOTE]
>  Belirtilen ifade belirtilen veri türünün bir alt türü olmalıdır veya bir alt ifadenin veri türü olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Belirtilen veri türünde bir değer.  
  
## <a name="remarks"></a>Açıklamalar  
 KABUL ilgili sınıflar arasında yukarı çevrim gerçekleştirmek için kullanılır. Örneğin, varsa `Employee` türetildiği `Person` ve p türünü `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts genel bir `Person` için örnek `Employee`; diğer bir deyişle, p değerlendirilecek tanır `Employee`.  
  
 KABUL burada aşağıdaki gibi bir sorguda yapabileceğiniz devralma senaryolarda kullanılır:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 Bu sorgu upcasts `Person` varlıklara `Employee` türü. P değerini değil gerçekten türde ise `Employee`, ifade değerini verir `null`.  
  
> [!NOTE]
>  Belirtilen ifade `Employee` belirtilen veri türünün bir alt türü olmalıdır `Person`, veya bir alt ifadenin veri türü olmalıdır. Aksi takdirde, ifadeyi bir derleme zamanı hataya neden olur.  
  
 Aşağıdaki tabloda, bazı tipik desenleri ve daha az yaygın olan bazı desenleri üzerinden kabul davranışını gösterir. Sağlayıcı çağrılır önce tüm istemci tarafında özel durumlar:  
  
|Desen|Davranış|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Döndürür `DbNull`.|  
|`TREAT (null AS ComplexType)`|Özel durum oluşturur.|  
|`TREAT (null AS RowType)`|Bir özel durum oluşturur /|  
|`TREAT (EntityType AS EntityType)`|Döndürür `EntityType` veya `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Özel durum oluşturur.|  
|`TREAT (RowType AS RowType)`|Özel durum oluşturur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu OnsiteCourse türünden nesnelerin bir koleksiyonunu kurs türdeki bir nesneyi dönüştürmek için kabul işlecini kullanır. Sorgu dayanır [Okul modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
