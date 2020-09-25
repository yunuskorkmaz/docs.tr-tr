---
title: SıRALAMA ölçütü (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 5e1c418a7f2bd40a42b259fb3784794b13098d7f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173685"
---
# <a name="order-by-entity-sql"></a>SıRALAMA ölçütü (Entity SQL)

Bir SELECT ifadesinde döndürülen nesnelerde kullanılan sıralama düzenini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `order_by_expression`  
 Üzerinde sıralanacak bir özellik belirten geçerli bir sorgu ifadesi. Birden çok sıralama ifadesi belirlenebilir. ORDER BY yan tümcesindeki sıralama ifadelerinin sırası, sıralanmış sonuç kümesinin organizasyonunu tanımlar.  
  
 HARMANLAMA {collation_name}  
 ORDER BY işleminin ' de belirtilen harmanlamaya göre gerçekleştirilmesi gerektiğini belirtir `collation_name` . HARMANLAMA yalnızca dize ifadeleri için geçerlidir.  
  
 ASC  
 Belirtilen özelliğindeki değerlerin, en düşük değerden en yüksek değere göre artan sırada sıralanması gerektiğini belirtir. Bu varsayılan seçenektir.  
  
 DESC  
 Belirtilen özelliğindeki değerlerin, en yüksek değerden en düşük değere göre azalan sırada sıralanması gerektiğini belirtir.  
  
 SıNıRLı `n`  
 Yalnızca ilk `n` öğeler seçilecek.  
  
 ŞIMDILIK `n`  
 İlk öğeleri atlar `n` .  
  
## <a name="remarks"></a>Açıklamalar  

 ORDER BY yan tümcesi, SELECT yan tümcesinin sonucuna mantıksal olarak uygulanır. ORDER BY yan tümcesi, seçim listesindeki öğelere diğer adlarını kullanarak başvurabilir. ORDER BY yan tümcesi, şu anda kapsamda olan diğer değişkenlere de başvurabilir. Ancak, SELECT yan tümcesi ayrı bir değiştiriciyle belirtilmişse, ORDER BY yan tümcesi yalnızca SELECT yan tümcesindeki diğer adlara başvurabilir.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 ORDER BY yan tümcesindeki her bir ifade, sıralı eşitsizlik (küçüktür veya büyüktür, vb.) için karşılaştırılabileceğiniz bazı tür olarak değerlendirilmelidir. Bu türler genellikle sayılar, dizeler ve tarihler gibi skaler temel öğelerdir. Karşılaştırılabilir türlerin RowTypes da sıralı karşılaştırılabilir.  
  
 Kodunuz, üst düzey projeksiyon için dışında, sıralı bir küme üzerinde yinelenir, çıkışın sırasının korunması garanti edilmez.  

Aşağıdaki örnekte, siparişin korunması garanti edilir:

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

Aşağıdaki sorguda, iç içe geçmiş sorgunun sıralaması yok sayılır:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Sıralı bir UNıON, UNıON ALL, EXCEPT veya ıNTERSECT işlemine sahip olmak için aşağıdaki kalıbı kullanın:  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Kısıtlanmış anahtar sözcükler  

 Aşağıdaki anahtar sözcükler, bir yan tümcesinde kullanıldığında tırnak işaretleri içine alınmalıdır `ORDER BY` :  
  
- ÜSTÜNÜ  
  
- TÜMÜNÜ  
  
- KEY  
  
- LEFT  
  
- SIPARIŞI  
  
- Dış  
  
- RIGHT  
  
- ROW  
  
- DEĞER  
  
## <a name="ordering-nested-queries"></a>Iç Içe sorguları sıralama  

 Entity Framework, iç içe geçmiş bir ifade sorgunun herhangi bir yerine yerleştirilebilir; iç içe geçmiş bir sorgunun sırası korunmaz.  

Aşağıdaki sorgu sonuçları en son ada göre sıraya alacak:  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

Aşağıdaki sorguda, iç içe geçmiş sorgunun sıralaması yok sayılır:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, Select ifadesinde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtmek IÇIN order by işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu İfadeleri](query-expressions-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [ŞIMDILIK](skip-entity-sql.md)
- [SıNıRLı](limit-entity-sql.md)
- [Sayfanın Üstü](top-entity-sql.md)
