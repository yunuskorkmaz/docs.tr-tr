---
title: IŞLE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 15664da02189dd618784d55c07aaf4db38a2f656
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929298"
---
# <a name="treat-entity-sql"></a>IŞLE (Entity SQL)
Belirli bir temel türdeki bir nesneyi belirtilen türetilmiş türün bir nesnesi olarak değerlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 IŞLE ilgili sınıflar arasında yukarı atama gerçekleştirmek için kullanılır. Örneğin `Employee` , `TREAT(p AS NamespaceName.Employee)` `Person` `Employee` vep`Employee`türünden türetürse, genel bir örneği ' a aktarır; Yani, p 'yi kabul etmenizi sağlar. `Person` `Person`  
  
 DEĞERLENDIR, aşağıdaki gibi bir sorgu yapabileceğiniz devralma senaryolarında kullanılır:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 Bu sorgu, `Person` `Employee` varlıkları türüne aktarır. P değeri gerçekten tür `Employee`değilse, ifade değeri `null`verir.  
  
> [!NOTE]
> Belirtilen ifade `Employee` , belirtilen veri türünün `Person`bir alt türü olmalıdır veya veri türü ifadenin bir alt türü olmalıdır. Aksi takdirde, ifade derleme zamanı hatasına neden olur.  
  
 Aşağıdaki tabloda, bazı tipik desenler ve bazı daha az ortak desenler üzerinde işleme davranışı gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Döndürür `DbNull`.|  
|`TREAT (null AS ComplexType)`|Bir özel durum oluşturur.|  
|`TREAT (null AS RowType)`|Bir özel durum oluşturur/|  
|`TREAT (EntityType AS EntityType)`|`EntityType` Veya`null`döndürür.|  
|`TREAT (ComplexType AS ComplexType)`|Bir özel durum oluşturur.|  
|`TREAT (RowType AS RowType)`|Bir özel durum oluşturur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir nesne türünü onsitekurs türünde bir nesne koleksiyonuna dönüştürmek için değerlendir işlecini kullanır. Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
