---
title: Tanımlayıcılar (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: b467a42ed0a0083b9e72037f437dd70aa6b46390
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833705"
---
# <a name="identifiers-entity-sql"></a>Tanımlayıcılar (Entity SQL)
Tanımlayıcılar, sorgu ifadesi diğer adlarını, değişken başvurularını, nesnelerin özelliklerini ve benzerlerini göstermek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' da kullanılır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür tanımlayıcı sağlar: basit tanımlayıcılar ve alıntılanmış tanımlayıcılar.  
  
## <a name="simple-identifiers"></a>Basit tanımlayıcılar  
 @No__t-0 ' daki basit bir tanımlayıcı, alfasayısal ve alt çizgi karakterlerinden oluşan bir dizidir. Tanımlayıcının ilk karakteri alfabetik bir karakter (a-z veya A-Z) olmalıdır.  
  
## <a name="quoted-identifiers"></a>Tırnak içinde tanımlayıcılar  
 Tırnak işareti, köşeli ayraçlar ([]) içine alınmış herhangi bir karakter dizisidir. Tırnak içinde tanımlayıcılar, tanımlayıcılarında geçerli olmayan karakterler içeren tanımlayıcılar belirtmenize olanak tanır. Köşeli ayraçlar arasındaki tüm karakterler, tüm boşluk dahil olmak üzere tanımlayıcının bir parçası haline gelir.  
  
 Tırnak işaretli bir tanımlayıcı aşağıdaki karakterleri içeremez:  
  
- Metninde.  
  
- Satır başı.  
  
- Sıralanan.  
  
- Geri al.  
  
- Ek köşeli parantezler (yani, tanımlayıcıyı tanımlayan köşeli ayraç içinde köşeli ayraçlar).  
  
 Tırnak içinde tanımlayıcı, Unicode karakterler içerebilir.  
  
 Alıntılanmış tanımlayıcılar, aşağıdaki örnekte gösterildiği gibi tanımlayıcılarında geçerli olmayan özellik adı karakterleri oluşturmanızı sağlar:  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 Ayrıca, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' ın ayrılmış anahtar sözcüğü olan tanımlayıcıyı belirtmek için tırnak işaretleri de kullanabilirsiniz. Örneğin, `Email` türünün "from" adlı bir özelliği varsa, köşeli parantezler kullanarak aşağıdaki şekilde, ÖĞESINDEN ayrılmış anahtar sözcükten ayırt edebilirsiniz:  
  
 `SELECT e.[From] FROM emails AS e`  
  
 Nokta (.) işlecinin sağ tarafında tırnak içine alınmış tanımlayıcıyı kullanabilirsiniz.  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 Bir tanımlayıcıda köşeli ayraç kullanmak için, ek köşeli ayraç ekleyin. Aşağıdaki örnekte, "`abc]`" tanımlayıcıdır:  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 Alıntılanmış tanımlayıcı karşılaştırma semantiği için bkz. [giriş karakter kümesi](input-character-set-entity-sql.md).  
  
## <a name="aliasing-rules"></a>Diğer ad kuralları  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] yapıları dahil olmak üzere gerektiğinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgularında diğer adlar belirtilmesini öneririz:  
  
- Bir satır oluşturucusunun alanları.  
  
- Bir sorgu ifadesinin FROM yan tümcesindeki öğeler.  
  
- Bir sorgu ifadesinin SELECT yan tümcesindeki öğeler.  
  
- Sorgu ifadesinin GROUP BY yan tümcesinde bulunan öğeler.  
  
### <a name="valid-aliases"></a>Geçerli diğer adlar  
 @No__t-0 ' daki geçerli diğer adlar herhangi bir basit tanımlayıcı veya tırnak içinde tanımlayıcıdır.  
  
### <a name="alias-generation"></a>Diğer ad oluşturma  
 @No__t-0 sorgu ifadesinde diğer ad belirtilmemişse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki basit kurallara göre bir diğer ad oluşturmaya çalışır:  
  
- Sorgu ifadesi (diğer ad belirtilmemiş olan) basit veya tırnaklı bir tanımlayıcı ise, bu tanımlayıcı diğer ad olarak kullanılır. Örneğin, `ROW(a, [b])` `ROW(a AS a, [b] AS [b])` olur.  
  
- Sorgu ifadesi daha karmaşık bir ifade ise, ancak bu sorgu ifadesinin son bileşeni basit bir tanımlayıcı ise, bu tanımlayıcı diğer ad olarak kullanılır. Örneğin, `ROW(a.a1, b.[b1])` `ROW(a.a1 AS a1, b.[b1] AS [b1])` olur.  
  
 Daha sonra diğer adı kullanmak istiyorsanız örtük diğer adlar kullanmayın. Her zaman diğer adlar (örtük veya açık) çakışması veya aynı kapsamda tekrarlanıyor, bir derleme hatası olacaktır. Bir örtük diğer ad, aynı ada sahip açık veya örtük bir diğer ad olsa bile derlemeyi geçicektir.  
  
 Örtük diğer adlar Kullanıcı girişine göre otomatik olarak oluşturulur. Örneğin, aşağıdaki kod satırı her iki sütun için bir diğer ad olarak ad oluşturacak ve bu nedenle çakışacaktır.  
  
```sql  
SELECT product.NAME, person.NAME  
```  
  
 Açık diğer adlar kullanan aşağıdaki kod satırı da başarısız olur. Ancak, hata kodu okuyarak hata daha belirgin olacaktır.  
  
```sql  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a>Kapsam oluşturma kuralları  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], belirli değişkenlerin sorgu dilinde görünür olduğunu belirleyen kapsam kurallarını tanımlar. Bazı ifadeler veya deyimler yeni adlar sağlar. Kapsam kuralları, bu adların nerede kullanılabileceğini ve diğeri ile aynı ada sahip yeni bir bildirimin öncülü gizleyemeyeceğini tespit edebilir.  
  
 Adlar [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusunda tanımlandığında, bir kapsam içinde tanımlanmaları söylenir. Kapsam, sorgunun tamamına ait bir bölgenin tamamını içerir. Belirli bir kapsamdaki tüm ifadeler veya ad başvuruları, bu kapsam içinde tanımlanan adları görebilir. Kapsam başlamadan önce ve sona erdikten sonra, kapsam içinde tanımlı adlara başvurulamaz.  
  
 Kapsamlar iç içe olabilir. @No__t kısımları, tüm bölgeleri kapsayan yeni kapsamlar sunar ve bu bölgeler Ayrıca kapsamları da tanıtan diğer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifadeleri içerebilir. Kapsamlar iç içe olduğunda, başvuruyu içeren en içteki kapsamda tanımlanmış adlara başvurular yapılabilir. Ayrıca, herhangi bir dış kapsamlarda tanımlanmış adlara başvurular yapılabilir. Aynı kapsam içinde tanımlanan herhangi iki kapsam eşdüzey kapsamlar olarak değerlendirilir. Eşdüzey kapsamlar içinde tanımlanan adlara başvurular yapılamaz.  
  
 Bir iç kapsamda belirtilen bir ad, dış kapsamda belirtilen bir adla eşleşiyorsa, iç kapsamdaki veya bu kapsamda belirtilen kapsamların içindeki başvurular yalnızca yeni belirtilen ada başvurur. Dış kapsamdaki ad gizlenir.  
  
 Aynı kapsam içinde bile, tanımlanmadan önce adlara başvurulamaz.  
  
 Genel adlar, yürütme ortamının bir parçası olarak bulunabilir. Bu, kalıcı koleksiyonların veya ortam değişkenlerinin adlarını içerebilir. Bir adın genel olması için en dıştaki kapsamda bildirilmelidir.  
  
 Parametreler bir kapsamda değil. Parametrelere başvurular özel söz dizimi içerdiğinden, parametrelerin adları sorgudaki diğer adlarla çakışmayacaktır.  
  
### <a name="query-expressions"></a>Sorgu İfadeleri  
 @No__t-0 sorgu ifadesi yeni bir kapsam sunar. FROM yan tümcesinde tanımlanan adlar, kimden kapsamından, soldan sağa doğru görünüm sırasına göre tanıtılmıştır. JOIN listesinde, ifadeler listede daha önce tanımlanmış adlara başvurabilir. FROM yan tümcesinde tanımlanan öğelerin ortak özellikleri (alanları vb.), from kapsamına eklenmez. Her zaman diğer ad tarafından nitelenmiş ad tarafından başvurulmalıdır. Genellikle, SELECT ifadesinin tüm parçaları from-Scope içinde değerlendirilir.  
  
 GROUP BY yan tümcesi Ayrıca yeni bir eşdüzey kapsam da sunar. Her grup, gruptaki öğelerin koleksiyonuna başvuran bir grup adına sahip olabilir. Her gruplandırma ifadesi Ayrıca grup kapsamına yeni bir ad da getirir. Ayrıca, iç içe toplama (veya adlandırılmış grup) de kapsama eklenir. Gruplandırma ifadeleri kendi kapsamı içinde bulunur. Ancak, GROUP BY yan tümcesi kullanıldığında, select-List (Projection), HAVING yan tümcesi ve ORDER BY yan tümcesi, kapsam içinde değil, Grup kapsamı içinde olarak değerlendirilir. Toplamalar, aşağıdaki madde işaretli listede açıklandığı gibi özel bir işleme alır.  
  
 Kapsamlar hakkında ek notlar aşağıda verilmiştir:  
  
- Seçim listesi, kapsama göre yeni adlar ekleyebilir. Sağdaki İzdüşüm ifadeleri, sol tarafta yansıtılan adlara başvurabilir.  
  
- ORDER BY yan tümcesi, seçim listesinde belirtilen adlara (diğer adlar) başvurabilir.  
  
- SELECT ifadesinin içindeki yan tümceler değerlendirmesi sırası, adların kapsama tanıtılme sırasını belirler. FROM yan tümcesi önce değerlendirilir, ardından WHERE yan tümcesi, GROUP BY yan tümcesi, HAVING yan tümcesi, SELECT yan tümcesi ve son olarak ORDER BY yan tümcesi gelir.  
  
### <a name="aggregate-handling"></a>Toplu Işleme  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür toplamaları destekler: koleksiyon tabanlı toplamalar ve grup tabanlı toplamalar. Koleksiyon tabanlı toplamalar [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' da tercih edilen yapıdır ve SQL uyumluluğu için grup tabanlı toplamalar desteklenir.  
  
 Bir toplama çözümlenirken [!INCLUDE[esql](../../../../../../includes/esql-md.md)], ilk olarak onu koleksiyon tabanlı bir toplama olarak kabul etmeye çalışır. Bu başarısız olursa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] toplama girişini iç içe toplama bir başvuruya dönüştürür ve aşağıdaki örnekte gösterildiği gibi bu yeni ifadeyi çözümlemeye çalışır.  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Giriş Karakter Kümesi](input-character-set-entity-sql.md)
