---
title: IŞLE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 38099fa83ed78b40d46faeb5e617157f7aa7c1a1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319256"
---
# <a name="treat-entity-sql"></a>IŞLE (Entity SQL)
Belirli bir temel türdeki bir nesneyi belirtilen türetilmiş türün bir nesnesi olarak değerlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Arguments  
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
 IŞLE ilgili sınıflar arasında yukarı atama gerçekleştirmek için kullanılır. Örneğin, `Employee` `Person` ' den türetilse ve p `Person` türündedir, `TREAT(p AS NamespaceName.Employee)` bir genel `Person` örneğini `Employee` ' e aktarır; Yani, p 'yi `Employee` olarak değerlendirmesine olanak tanır.  
  
 DEĞERLENDIR, aşağıdaki gibi bir sorgu yapabileceğiniz devralma senaryolarında kullanılır:  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 Bu sorgu `Person` varlıklarını `Employee` türüne yukarı aktarır. P değeri gerçekten `Employee` türünde değilse, ifade `null` değerini verir.  
  
> [!NOTE]
> @No__t-0 belirtilen ifadesi belirtilen veri türünün bir alt türü olmalıdır `Person` veya veri türü ifadenin bir alt türü olmalıdır. Aksi takdirde, ifade derleme zamanı hatasına neden olur.  
  
 Aşağıdaki tabloda, bazı tipik desenler ve bazı daha az ortak desenler üzerinde işleme davranışı gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|@No__t-0 döndürür.|  
|`TREAT (null AS ComplexType)`|Bir özel durum oluşturur.|  
|`TREAT (null AS RowType)`|Bir özel durum oluşturur/|  
|`TREAT (EntityType AS EntityType)`|@No__t-0 veya `null` döndürür.|  
|`TREAT (ComplexType AS ComplexType)`|Bir özel durum oluşturur.|  
|`TREAT (RowType AS RowType)`|Bir özel durum oluşturur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir nesne türünün bir nesnesini Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek için DEĞERLENDIR işlecini kullanır. Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)
