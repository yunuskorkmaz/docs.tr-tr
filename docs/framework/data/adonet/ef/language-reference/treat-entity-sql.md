---
title: IŞLE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 566ac875aec17e4d0aa22ec1962053aeb6ae2a2e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558855"
---
# <a name="treat-entity-sql"></a>IŞLE (Entity SQL)
Belirli bir temel türdeki bir nesneyi belirtilen türetilmiş türün bir nesnesi olarak değerlendirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `expression`  
 Bir varlık döndüren geçerli bir sorgu ifadesi.  
  
> [!NOTE]
> Belirtilen ifadenin türü, belirtilen veri türünün bir alt türü olmalıdır veya veri türü, ifadenin türünün bir alt türü olmalıdır.  
  
 `type`  
 Bir varlık türü. Tür bir ad alanı tarafından nitelenmelidir.  
  
> [!NOTE]
> Belirtilen ifade, belirtilen veri türünün bir alt türü olmalıdır veya veri türü ifadenin bir alt türü olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Belirtilen veri türünde bir değer.  
  
## <a name="remarks"></a>Açıklamalar  
 IŞLE ilgili sınıflar arasında yukarı atama gerçekleştirmek için kullanılır. Örneğin, `Employee` ve p türünden türetürse `Person` `Person` , `TREAT(p AS NamespaceName.Employee)` genel bir örneği ' a aktarır `Person` `Employee` ; Yani, p 'yi kabul etmenizi sağlar `Employee` .  
  
 DEĞERLENDIR, aşağıdaki gibi bir sorgu yapabileceğiniz devralma senaryolarında kullanılır:  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 Bu sorgu `Person` , varlıkları `Employee` türüne aktarır. P değeri gerçekten tür değilse `Employee` , ifade değeri verir `null` .  
  
> [!NOTE]
> Belirtilen ifade, `Employee` belirtilen veri türünün bir alt türü olmalıdır `Person` veya veri türü ifadenin bir alt türü olmalıdır. Aksi takdirde, ifade derleme zamanı hatasına neden olur.  
  
 Aşağıdaki tabloda, bazı tipik desenler ve bazı daha az ortak desenler üzerinde işleme davranışı gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|`DbNull` döndürür.|  
|`TREAT (null AS ComplexType)`|Bir özel durum oluşturur.|  
|`TREAT (null AS RowType)`|Bir özel durum oluşturur/|  
|`TREAT (EntityType AS EntityType)`|`EntityType`Veya döndürür `null` .|  
|`TREAT (ComplexType AS ComplexType)`|Bir özel durum oluşturur.|  
|`TREAT (RowType AS RowType)`|Bir özel durum oluşturur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir nesne türünü Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek IÇIN değerlendir işlecini kullanır. Sorgu, [okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)
