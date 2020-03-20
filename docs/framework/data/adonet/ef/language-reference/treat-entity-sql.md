---
title: TREAT (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 06c4200434f443446e8981dcefe2baf43b1af4b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149901"
---
# <a name="treat-entity-sql"></a>TREAT (Varlık SQL)
Belirli bir taban türünden bir nesneyi, belirtilen türemiş türdeki bir nesne olarak davranır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Varlığı döndüren geçerli bir sorgu ifadesi.  
  
> [!NOTE]
> Belirtilen ifadenin türü, belirtilen veri türünün bir alt türü veya veri türü ifade türünün bir alt türü olmalıdır.  
  
 `type`  
 Varlık türü. Tür bir ad alanı tarafından nitelikli olmalıdır.  
  
> [!NOTE]
> Belirtilen ifade, belirtilen veri türünün bir alt türü veya veri türü ifadenin bir alt türü olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Belirtilen veri türünün değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 TREAT ilgili sınıflar arasında upcasting gerçekleştirmek için kullanılır. Örneğin, `Employee` türetilir `Person` ve p türünde `Person` `TREAT(p AS NamespaceName.Employee)` ise, genel `Person` bir `Employee`örnek upcasts; yani, p olarak `Employee`tedavi etmenizi sağlar.  
  
 TREAT, aşağıdaki gibi bir sorgu yapabileceğiniz devralma senaryolarında kullanılır:  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 Bu sorgu, `Person` varlıkları `Employee` türe doğru yükselter. p değeri aslında tür `Employee`değilse, ifade değeri `null`verir.  
  
> [!NOTE]
> Belirtilen ifade, `Employee` belirtilen veri türünün `Person`bir alt türü veya veri türü ifadenin bir alt türü olmalıdır. Aksi takdirde, ifade derleme zamanı hatasına neden olur.  
  
 Aşağıdaki tablo, bazı tipik desenler ve bazı daha az yaygın desenler üzerinde tedavi davranışını gösterir. Sağlayıcı çağrılmadan önce tüm özel durumlar istemci tarafından atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|`DbNull` döndürür.|  
|`TREAT (null AS ComplexType)`|Bir istisna atar.|  
|`TREAT (null AS RowType)`|Bir özel durum atar/|  
|`TREAT (EntityType AS EntityType)`|İade `EntityType` `null`veya .|  
|`TREAT (ComplexType AS ComplexType)`|Bir istisna atar.|  
|`TREAT (RowType AS RowType)`|Bir istisna atar.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, Kurs türündeki bir nesneyi Yerinde Kurs türündeki nesneler koleksiyonuna dönüştürmek için TREAT işleci kullanır. Sorgu [Okul Modeli'ni](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alın.  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)
