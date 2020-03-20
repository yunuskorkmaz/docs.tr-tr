---
title: SİPARİş TARAFINDAN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 1233971b172079aa48227d0ec520068afbdf0952
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150075"
---
# <a name="order-by-entity-sql"></a>SİPARİş TARAFINDAN (Entity SQL)
SELECT deyiminde döndürülen nesnelerde kullanılan sıralama sırasını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `order_by_expression`  
 Sıralamak için bir özellik belirten geçerli bir sorgu ifadesi. Birden çok sıralama ifadeleri belirtilebilir. ORDER BY yan tümcesindeki tür ifadelerinin sırası, sıralanmış sonuç kümesinin organizasyonunu tanımlar.  
  
 HARM {collation_name}  
 Order BY işleminin belirtilen harmanlama göre yapılması gerektiğini `collation_name`belirtir. COLLATE yalnızca dize ifadeleri için geçerlidir.  
  
 ASC  
 Belirtilen özellikteki değerlerin artan sırada, en düşük değerden en yüksek değere sıralanması gerektiğini belirtir. Bu varsayılandır.  
  
 DESC  
 Belirtilen özellikteki değerlerin azalan sırada, en yüksek değerden en düşük değere sıralanması gerektiğini belirtir.  
  
 Sınırı`n`  
 Yalnızca ilk `n` öğeler seçilir.  
  
 Atlamak`n`  
 İlk `n` öğeleri atlar.  
  
## <a name="remarks"></a>Açıklamalar  
 ORDER BY yan tümcesi, SELECT yan tümcesinin sonucuna mantıksal olarak uygulanır. ORDER BY yan tümcesi, diğer adlarını kullanarak seçili listedeki öğelere başvuru yapabilir. ORDER BY yan tümcesi, şu anda kapsam içinde olan diğer değişkenlere de başvuruyapabilir. Ancak, SELECT yan tümcesi DISTINCT değiştirici ile belirtilmişse, ORDER BY yan tümcesi yalnızca SELECT yan tümcesi diğer adlarını kullanabilir.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 ORDER BY yan tümcesindeki her ifade, sipariş edilen eşitsizlik için karşılaştırılabilen bazı türe (daha az veya daha büyük vb.) değerlendirilmelidir. Bu türler genellikle sayılar, dizeleri ve tarihler gibi skaler ilkel vardır. Karşılaştırılabilir türlerin RowTypes da karşılaştırılabilir sipariş vardır.  
  
 Kodunuz, üst düzey bir projeksiyon dışında sıralı bir küme üzerinde yinelenirse, çıktının siparişinin korunduğu garanti edilmez.  

Aşağıdaki örnekte, siparişin korunması garanti edilir:

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

Aşağıdaki sorguda, iç içe olan sorgunun sırası yoksayılır:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Sipariş edilmiş bir BİrLİk, UNION ALL, EXCEPT veya INTERSECT işlemine sahip olmak için aşağıdaki deseni kullanın:  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Kısıtlı anahtar kelimeler  
 Aşağıdaki anahtar kelimeler, bir `ORDER BY` yan tümcede kullanıldığında tırnak işaretlerine eklenmelidir:  
  
- Çapraz  
  
- Tam  
  
- KEY  
  
- LEFT  
  
- Sipariş  
  
- Dış  
  
- RIGHT  
  
- ROW  
  
- DEĞER  
  
## <a name="ordering-nested-queries"></a>İç Içe Sorguları Sıralama  
 Varlık Çerçevesi'nde, iç içe bir ifade sorguda herhangi bir yere yerleştirilebilir; iç içe geçme sırası korunmaz.  

Aşağıdaki sorgu sonuçları soyadına göre sıralar:  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

Aşağıdaki sorguda, iç içe olan sorgunun sırası yoksayılır:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, SELECT deyiminde döndürülen nesnelerde kullanılan sıralama sırasını belirtmek için ORDER BY işlecikullanır. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu İfadeleri](query-expressions-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Atlamak](skip-entity-sql.md)
- [Sınırı](limit-entity-sql.md)
- [Sayfanın Üstü](top-entity-sql.md)
