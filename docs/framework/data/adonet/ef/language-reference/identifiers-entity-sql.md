---
title: "Tanımlayıcılar (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 21518cad85ebcfc4c326e99d615b4f2dfccf6a2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="identifiers-entity-sql"></a>Tanımlayıcılar (varlık SQL)
Tanımlayıcılar kullanılır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ifadesi diğer adlar, değişken başvuruları, nesneler, İşlevler ve benzeri özelliklerini temsil etmek için. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]iki tür tanımlayıcıları sağlar: Basit tanımlayıcıları ve tırnak işaretli tanımlayıcılar.  
  
## <a name="simple-identifiers"></a>Basit tanımlayıcıları  
 Basit bir tanımlayıcı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alfasayısal dizisini ve alt çizgi karakteri. Tanımlayıcı ilk karakteri bir alfabetik karakterler (a-z veya A-Z) olması gerekir.  
  
## <a name="quoted-identifiers"></a>Tırnak işaretli tanımlayıcılar  
 Bir dizi köşeli parantez ([]) içine karakteri buna tırnak içine alınmış bir tanımlayıcıdır. Tanımlayıcıları let tırnak içine alınmış tanımlayıcıları tanımlayıcılarının geçerli olmayan karakterler ile belirtin. Tüm karakterleri köşeli ayraçlar arasında tüm boşluklar dahil olmak üzere tanımlayıcı, bir parçası haline gelir.  
  
 Tırnak içine alınmış bir tanımlayıcı şu karakterleri içeremez:  
  
-   Yeni satır.  
  
-   Satır başı.  
  
-   Sekmeleri.  
  
-   Geri Al.  
  
-   Ek köşeli ayraç (diğer bir deyişle, köşeli tanımlayıcı ayırmak köşeli ayraç içinde).  
  
 Tırnak içine alınmış tanımlayıcı Unicode karakterler içerebilir.  
  
 Tırnak işaretli tanımlayıcılar aşağıdaki örnekte gösterildiği gibi tanımlayıcılarının, geçerli olmayan özellik adı karakterleri oluşturmanızı sağlar:  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 Ayrılmış bir anahtar sözcük, bir tanımlayıcı belirtin için tırnak işaretli tanımlayıcılar kullanabilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Örneğin, varsa türü `Email` özelliğine "Kimden" olarak adlandırılan, ayrılmış bir anahtar sözcük gelen köşeli şekilde kullanarak belirsizliğini ortadan kaldırmak:  
  
 `SELECT e.[From] FROM emails AS e`  
  
 Tırnak içine alınmış bir tanımlayıcı bir nokta (.) işlecinin sağ tarafta kullanabilirsiniz.  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 Köşeli ayraç tanımlayıcıda kullanmak için ek bir köşeli ayraç ekleyin. Aşağıdaki örnekte "`abc]`" tanımlayıcısı:  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 Tırnak içine alınmış tanımlayıcı karşılaştırma semantiği için bkz: [giriş karakter kümesi](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="aliasing-rules"></a>Diğer ad kuralları  
 Diğer adlar belirtme öneririz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aşağıdakiler de dahil olmak üzere gerektiğinde sorgular [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturur:  
  
-   Bir satır oluşturucusunda alanları.  
  
-   Bir sorgu ifadesi öğelerinin FROM yan tümcesinde.  
  
-   Bir sorgu ifadesi öğelerin SELECT yan tümcesinde.  
  
-   Bir sorgu ifadesi öğelerinin GROUP BY yan tümcesinde.  
  
### <a name="valid-aliases"></a>Geçerli diğer adlar  
 Geçerli adlarda [!INCLUDE[esql](../../../../../../includes/esql-md.md)] basit tanımlayıcı ya da alıntı tanımlayıcısı.  
  
### <a name="alias-generation"></a>Diğer adı oluşturma  
 Diğer ad alanında belirtilmişse, bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ifadesi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki basit kurallara göre bir diğer ad oluşturmak çalışır:  
  
-   Bu tanımlayıcı (diğer ad belirtilmeyen olduğu) sorgu ifadesi basit ya da tırnak içine alınmış bir tanımlayıcı ise, diğer ad olarak kullanılır. Örneğin, `ROW(a, [b])` hale `ROW(a AS a, [b] AS [b])`.  
  
-   Sorgu ifadesi daha karmaşık bir ifade, ancak bu sorgu ifadesi son bileşeni basit bir tanımlayıcı tanımlayıcıyı diğer ad olarak kullanılır. Örneğin, `ROW(a.a1, b.[b1])` hale `ROW(a.a1 AS a1, b.[b1] AS [b1])`.  
  
 Daha sonra diğer ad kullanmak istiyorsanız, örtük yumuşatma kullanmamanızı öneririz. Diğer adlar (örtük veya açık) çakışma veya olan aynı kapsamda yinelenen her zaman, bir derleme hatası olacaktır. Açık veya örtülü bir diğer ad aynı ada sahip olsa bile örtük bir diğer ad derleme geçer.  
  
 Örtük adlardır kullanıcı girişini temel alarak otomatik olarak oluşturulur. Örneğin, aşağıdaki kod satırını adı hem de sütunlar için diğer ad olarak oluşturur ve bu nedenle çakışır.  
  
```  
SELECT product.NAME, person.NAME  
```  
  
 Açık diğer adlar kullanır, kod, aşağıdaki satırı de başarısız olacak. Ancak, hata kodu okuyarak daha belirgin olacaktır.  
  
```  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a>Kapsam kuralları  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]belirli değişkenleri sorgu dilde görünür olduğunda belirleyen ölçüm kuralları tanımlar. Bazı ifadeler veya deyimleri yeni adları tanıtır. Kapsam kuralları bu adlar kullanıldığı ve ne zaman veya burada başka aynı ada sahip yeni bir bildirimde öncülü gizleyebilirsiniz belirler.  
  
 Ne zaman adları tanımlanmış bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir kapsam içinde tanımlanan söylenir. Bir kapsam sorgunun tüm bir bölgeyi kapsar. Tüm ifadeler veya belirli bir kapsam adı başvurulara bu kapsam içinde tanımlanan adlarını görebilirsiniz. Bir kapsam başlamadan önce ve bittikten sonra kapsam içinde tanımlanan adları başvurulamaz.  
  
 Kapsamlar iç içe. Bölümlerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm bölgeler kapak yeni kapsamlar getirir ve bu bölge diğer içerebilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de kapsamları tanıtmak ifadeler. Kapsamlar iç içe geçmiş zaman başvurular başvuru içeren en içteki kapsamda tanımlanan adlarına yapılamaz. Başvurular, herhangi bir dış kapsam içinde tanımlanan herhangi bir ad için de yapılabilir. Aynı kapsamda tanımlanan herhangi bir iki kapsam eşdüzey kapsamlar olarak kabul edilir. Başvuruları eşdüzey kapsamlarında tanımlanan adlarına yapılamaz.  
  
 Bir iç kapsamda bildirilen ad dış kapsamda bildirilen bir ad eşleşirse, iç kapsamında veya bu kapsamı içinde bildirilen kapsamlarında başvuruları yalnızca yeni bildirilen adına bakın. Dış kapsamdaki adı gizlenir.  
  
 Tanımlanmadan önce bile aynı kapsamda adları başvurulamaz.  
  
 Global adlar Yürütme Ortamı'nın bir parçası olarak bulunabilir. Bu adları kalıcı koleksiyonları veya ortam değişkenleri içerebilir. Genel olması için bir ad, en dıştaki kapsamda bildirilmelidir.  
  
 Parametreler bir kapsamda değildir. Parametrelere başvurular özel sözdizimi içerdiğinden parametrelerinin adları asla sorgudaki diğer adlarıyla birbiriyle çakışır.  
  
### <a name="query-expressions"></a>Sorgu İfadeleri  
 Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ifadesi yeni bir kapsam tanıtır. FROM yan tümcesinde tanımlanan adları halinde sunulan seyri içinde kapsamdan soldan sağa. Birleşim listesinde ifadeleri listede daha önce tanımlanan adlarını başvurabilir. FROM yan tümcesinde tanımlanan öğelerin ortak özellikleri (alanlar ve benzeri) gelen-kapsamına eklenmez. Diğer ad tam adıyla her zaman başvurulmalıdır. Genellikle, SELECT ifadesi tüm parçalarını gelen-kapsamı içinde olarak kabul edilir.  
  
 GROUP BY yan tümcesi, aynı zamanda yeni bir eş kapsamı sunar. Her Grup grubunda öğe koleksiyonunu başvurduğu bir grup adı olabilir. Her gruplandırma ifadesi, Grup kapsamı içine yeni bir ad da tanıtılacaktır. Ayrıca, iç içe toplama (veya adlandırılmış grup) kapsamına eklenir. Gruplandırma ifadeleri gelen-kapsamı içinde kullanılan. GROUP BY yan tümcesi kullanıldığında, ancak Seç-LIST (yansıtma), HAVING yan tümcesi ve ORDER BY yan tümcesi Grup kapsamı ve değil gelen kapsamı içinde olduğu varsayılır. Toplamalar, aşağıdaki madde işaretli listede açıklandığı gibi özel işleme alırsınız.  
  
 Kapsamları hakkında ek notlar şunlardır:  
  
-   Select listesi sırayla kapsam içine yeni adları ortaya çıkarabilir. Projeksiyon ifadeleri sağa sol tarafta öngörülen adlarını başvurabilir.  
  
-   ORDER BY yan tümcesi select listesinde belirtilen adları (diğer adları) başvurabilirsiniz.  
  
-   SELECT deyimi içinde yan tümceleri Değerlendirme sırasını adları kapsam içine sunulan sırasını belirler. FROM yan tümcesi, ilk olarak, WHERE yan tümcesi, GROUP BY yan tümcesi, HAVING yan tümcesi, SELECT yan tümcesi ve ORDER BY yan tümcesi tarafından son ardından değerlendirilir.  
  
### <a name="aggregate-handling"></a>İşleme toplama  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Toplamalar, iki biçimlerini destekler: Koleksiyon tabanlı toplamlar ve grup tabanlı toplar. Koleksiyon tabanlı toplamalar olan tercih edilen yapı [!INCLUDE[esql](../../../../../../includes/esql-md.md)], ve grup tabanlı toplamalar SQL Uyumluluk için desteklenir.  
  
 Bir toplama çözülürken [!INCLUDE[esql](../../../../../../includes/esql-md.md)] koleksiyon tabanlı bir toplama olarak işlemek önce çalışır. Başarısız olursa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iç içe toplama başvuru birleşik giriş dönüştüren ve bu yeni ifade çözümlemek aşağıdaki örnekte gösterildiği gibi çalışır.  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Varlık SQL genel bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Giriş karakter kümesi](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)
