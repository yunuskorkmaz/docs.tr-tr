---
title: Tanımlayıcılar (varlık SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: 702a9c69c37b572fde18dd57c44608678174fb15
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204906"
---
# <a name="identifiers-entity-sql"></a>Tanımlayıcılar (varlık SQL)
Tanımlayıcılar kullanılır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ifadesi diğer adlar, değişken başvuruları, nesneleri, işlevleri ve benzeri özelliklerini göstermek için. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür tanımlayıcıları sağlar: Basit tanımlayıcıları ve tırnak işaretli tanımlayıcılar.  
  
## <a name="simple-identifiers"></a>Basit tanımlayıcı  
 Basit bir tanımlayıcı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alfasayısal oluşan bir dizidir ve alt çizgi karakterleri. Bir tanımlayıcının ilk karakteri alfabetik bir karakterle (a-z veya A-Z) olmalıdır.  
  
## <a name="quoted-identifiers"></a>Tırnak işaretli tanımlayıcıları  
 Dizi köşeli ayraçlar ([]) içine alınmış karakter bir tırnak işaretli tanımlayıcıdır. Tanımlayıcıları let sınırlandırılmış tanımlayıcıları tanımlayıcıları geçerli olmayan karakterler ile belirtin. Tüm karakterleri köşeli ayraçlar arasındaki tüm boşluk da dahil olmak üzere, tanımlayıcı bir parçası haline gelir.  
  
 Tırnak işaretli tanımlayıcı şu karakterleri içeremez:  
  
-   Yeni satır.  
  
-   Satır başı döndürür.  
  
-   Sekmeler.  
  
-   Geri Al.  
  
-   Ek köşeli ayraç (diğer bir deyişle,. köşeli parantez tanımlayıcıyı ayırmak köşeli ayraç içinde).  
  
 Teklif tanımlayıcısı, Unicode karakterler içerebilir.  
  
 Tırnak işaretli tanımlayıcıları aşağıdaki örnekte gösterildiği gibi tanımlayıcıların başında geçerli olmayan özellik adı karakterleri oluşturmanıza olanak sağlar:  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 Tırnak işaretli tanımlayıcıları, ayrılmış bir anahtar sözcük tanımlayıcı belirtmek için de kullanabilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Örneğin, türü `Email` bir özelliğe sahip "Kimden" adlı, bu ayrılmış anahtar sözcüğü gelen köşeli parantezler, aşağıdaki gibi kullanarak ayırt etmek:  
  
 `SELECT e.[From] FROM emails AS e`  
  
 Tırnak işaretli tanımlayıcı bir nokta (.) işlecinin sağ tarafta kullanabilirsiniz.  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 Köşeli ayraç bir tanımlayıcıda kullanmak için fazladan bir köşeli ayraç ekleyin. Aşağıdaki örnekte "`abc]`" tanımlayıcısı:  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 Tırnak işaretli tanımlayıcı karşılaştırma semantiği için bkz: [giriş karakter kümesi](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="aliasing-rules"></a>Diğer ad kuralları  
 Diğer adlar belirtme öneririz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aşağıdakiler dahil olmak üzere gerektiğinde sorgular [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturur:  
  
-   Bir satır oluşturucusunda alanları.  
  
-   Sorgu ifadesinin FROM yan tümcesi içindeki öğeler.  
  
-   Sorgu ifadesinin öğeleri SELECT yan tümcesinde.  
  
-   Sorgu ifadesinin öğeleri GROUP BY yan tümcesinde.  
  
### <a name="valid-aliases"></a>Geçerli diğer adlar  
 Geçerli diğer adlar [!INCLUDE[esql](../../../../../../includes/esql-md.md)] herhangi bir basit tanımlayıcı ya da tırnak işaretli tanımlayıcı.  
  
### <a name="alias-generation"></a>Diğer ad oluşturma  
 Takma ad belirtilmişse bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ifadesi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] basit aşağıdaki kurallara göre bir diğer ad oluşturmak çalışır:  
  
-   Bu tanımlayıcı, sorgu ifadesi (diğer ad belirsiz olduğu) bir basit veya tırnak işaretli tanımlayıcı ise, diğer ad olarak kullanılır. Örneğin, `ROW(a, [b])` olur `ROW(a AS a, [b] AS [b])`.  
  
-   Sorgu ifadesi daha karmaşık bir ifade, ancak bu sorgu ifadesinin son bileşeni basit bir tanımlayıcı tanımlayıcı diğer adı olarak kullanılır. Örneğin, `ROW(a.a1, b.[b1])` olur `ROW(a.a1 AS a1, b.[b1] AS [b1])`.  
  
 Daha sonra diğer ad kullanmak istiyorsanız, örtük yumuşatma kullanmamanızı öneririz. Diğer adları (örtük veya açık) çakışma veya olan aynı kapsam içinde yinelenen zaman bir derleme hatası olur. Açık veya örtülü bir diğer ad aynı ada sahip olsa bile örtük bir diğer ad, derleme geçer.  
  
 Kullanıcı girişini temel alarak otomatik olarak oluşturulan örtük adlardır. Örneğin, aşağıdaki kod satırını adı hem de sütunlar için diğer ad olarak oluşturur ve bu nedenle çakışır.  
  
```  
SELECT product.NAME, person.NAME  
```  
  
 Aşağıdaki açık diğer adları kullanan kod satırını de başarısız olur. Ancak, hata kodu okuyarak daha belirgin olur.  
  
```  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a>Kapsam kuralları  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] belirli değişkenleri sorgu dilinde görünür olduğunda belirleyen ölçüm kuralları tanımlar. Bazı ifadeler veya deyimler yeni adlar sunar. Kapsam kuralları, bu adları kullanıldığı ve ne zaman ya da burada başka aynı ada sahip yeni bir bildirim, öncülü gizleyebilirsiniz belirler.  
  
 Ne zaman adları tanımlanmış bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir kapsam içinde tanımlanması söylenir. Bir kapsam sorgunun tüm bir bölgeyi kapsar. Tüm ifadeler veya belirli bir kapsam içindeki başvurular adı bu kapsamda tanımlanan adları görebilirsiniz. Bir kapsam başlamadan önce ve bittikten sonra kapsam içinde tanımlanan adları başvurulamaz.  
  
 Kapsamları yuvalanabilir. Bölümleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm bölgeleri kapsayan yeni kapsamlar tanıtır ve bu bölgeler diğer içerebilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sıra kapsamı uygular ifadeler. İç içe kapsamları, başvuruları içeren reference en içteki kapsamda tanımlanan adları yapılabilir. Başvurular, herhangi bir dış kapsam içinde tanımlanan herhangi bir adı için de yapılabilir. Eşdüzey kapsamları, aynı kapsam içinde tanımlanan herhangi bir iki kapsam olarak kabul edilir. Eşdüzey kapsamlarda tanımlanan adlarına başvurular yapılamaz.  
  
 Bir iç kapsamda bildirilen bir ad dış bir kapsamda bildirilen bir adla eşleşirse, başvurular, kapsamı içinde bildirilen kapsamları veya iç kapsamı içinde yalnızca yeni bildirilen adına bakın. Kapsam adı gizlenir.  
  
 Tanımlanmadan önce bile aynı kapsamda adları başvurulamaz.  
  
 Global adlar Yürütme Ortamı'nın bir parçası olarak bulunabilir. Bu adları kalıcı koleksiyonları veya ortam değişkenleri içerebilir. Bir ad genel olarak, en dıştaki kapsamda bildirilmelidir.  
  
 Parametreleri bir kapsamda değildir. Parametrelere yapılan başvurular özel sözdizimi içerdiğinden parametrelerinin adları hiçbir zaman sorgudaki diğer adları birbiriyle çakışır.  
  
### <a name="query-expressions"></a>Sorgu İfadeleri  
 Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ifadesi, yeni bir kapsam tanıtır. FROM yan tümcesinde tanımlı adları içinde sunulmuştur kapsamından görünümünü sırayla soldan sağa. Birleştirme listesinde ifadeleri, listede daha önce tanımlanan adları başvurabilir. FROM yan tümcesinde belirtilen öğelerin ortak özellikleri (alanlar ve benzeri) öğesinden-kapsama eklenmez. Diğer adla nitelenmiş ada göre her zaman başvurulmalıdır. Genellikle, SELECT deyimini tüm parçalarını gelen kapsam içinde olarak kabul edilir.  
  
 GROUP BY yan tümcesi, yeni bir eş kapsamı da tanıtılmaktadır. Her grupta gruptaki öğelerin koleksiyonunu gösteren bir grup adı olabilir. Her gruplandırma ifadesi Grup kapsamı yeni bir ad kullanıma sunacak. Ayrıca, iç içe toplama (veya adlandırılmış grubuyla) kapsamına eklenir. Gruplandırma ifadeleri gelen-kapsamındaki. GROUP BY yan tümcesi kullanıldığında, ancak seçim listesi (yansıtma), HAVING yan tümcesi ve ORDER BY yan tümcesi Grup kapsamı ve olmayan öğesinden kapsam içinde olarak değerlendirilir. Toplamlar, aşağıdaki madde işaretli listede açıklandığı gibi özel işleme alırsınız.  
  
 Kapsamlar hakkında ek notlar şunlardır:  
  
-   Select listesi, yeni adları sırayla kapsama çıkarabilir. Projeksiyon ifadeleri sağ, sol taraftaki öngörülen adlarına başvurabilir.  
  
-   ORDER BY yan tümcesi select listesinde belirtilen adlardır (takma adlardır) başvurabilir.  
  
-   Yan tümce seçme içinde değerlendirilme sırasını adları kapsamına sunulan sırasını belirler. FROM yan tümcesi, WHERE yan tümcesi, GROUP BY yan tümcesi, HAVING yan tümcesi, SELECT yan tümcesi ORDER BY yan tümcesi son ardından ve ilk olarak değerlendirilir.  
  
### <a name="aggregate-handling"></a>Toplam işleme  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Toplamlar iki biçimini destekler: Koleksiyon tabanlı toplamlar ve grup tabanlı toplar. Koleksiyon tabanlı toplamaları olan tercih edilen yapısında [!INCLUDE[esql](../../../../../../includes/esql-md.md)], ve grup tabanlı toplamlar SQL Uyumluluk için desteklenir.  
  
 Bir toplama çözülürken [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ilk olarak koleksiyon tabanlı bir toplam değerlendirilecek çalışır. Bu başarısız olursa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iç içe toplama başvuru birleşik giriş dönüştüren ve bu yeni ifade aşağıdaki örnekte gösterildiği gibi çalışır.  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Giriş Karakter Kümesi](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)
