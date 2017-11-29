---
title: Sorgu ifadesi temelleri
description: "Sorgu ifadeleri ilgili kavramları tanıtır"
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: dbb77f57c7f3484930e1639da501ab828e1c2070
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-basics"></a>Sorgu ifadesi temelleri

## <a name="what-is-a-query-and-what-does-it-do"></a>Bir sorgu nedir ve ne işe yarar? 

 A *sorgu* verilen veri kaynağı (veya kaynakları) almak ve hangi şekli ve kuruluş için hangi verilerin döndürülen verileri olmalıdır açıklayan yönergeler kümesidir. Bir sorgu bu üretir sonuçlarından farklıdır.  
  
 Genellikle, veri kaynağını mantıksal olarak aynı türdeki öğeleri dizisi olarak düzenlenir. Örneğin, bir SQL veritabanı tablosunda satır dizisini içerir. Bir XML dosyasında yoktur XML öğelerinin "sırası" (bunlar hiyerarşik ağaç yapısında düzenlenir rağmen). Bellek içi koleksiyon nesnelerinin bir dizisi içerir. 
  
 Bir uygulamanın görüş açısından belirli türünü ve özgün kaynak verilerin yapısını önemli olmadığı. Uygulama her zaman kaynak verisi olarak görür bir <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601> koleksiyonu. Örneğin, LINQ-XML, kaynak veriler olarak görünür hale gelir bir `IEnumerable` \< <xref:System.Xml.Linq.XElement>>.  
  
 Bu kaynak sırası göz önüne alındığında, bir sorgu işlemlerden birini yapabilirsiniz:  
  
-   Bir alt öğeleri ayrı ayrı öğeler değiştirmeden yeni sırası üretmek için kümesini alır. Sorgu sonra sıralama veya aşağıdaki örnekte gösterildiği gibi çeşitli şekillerde döndürülen dizi Grup (varsayın `scores` olan bir `int[]`):  
  
     [!code-csharp[csrefQueryExpBasics#45](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]  
  
-   Önceki örnekte olduğu gibi öğeleri dizisi alabilir, ancak bunları yeni bir nesne türüne dönüştürün. Örneğin, bir sorgu, veri kaynağındaki belirli bir müşteri kayıt yalnızca son adlarını alabilirsiniz. Veya tam kayıt almak ve hatta başka bir bellek içi nesne türü oluşturmak kullanın nihai sonucu dizisi oluşturmadan XML verileri. Aşağıdaki örnek, bir projeksiyondan gösterir bir `int` için bir `string`. Yeni tür Not `highScoresQuery`.  
  
     [!code-csharp[csrefQueryExpBasics#46](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]  
  
-   Bir tek değer kaynak verilerle ilgili gibi alın:  
  
    -   Belirli bir koşulla eşleşen öğe sayısı.  
  
    -   Değeri en büyük ya da en az öğe.  
  
    -   Bir koşul veya öğelerin belirtilen kümedeki belirli değerlerinin toplamı eşleşen ilk öğe. Örneğin, aşağıdaki sorguyu puan sayısı 80'den büyük döndürür `scores` tamsayı dizisi:  
  
     [!code-csharp[csrefQueryExpBasics#47](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]  
  
     Önceki örnekte, sorgu ifadesinde çağırmadan önce parantezler kullanımına dikkat edin `Count` yöntemi. Bu, somut sonucu depolamak için yeni bir değişken kullanarak da açıklayabilir. Bu teknik daha okunabilir çünkü sorgu depolar değişkeni bir sonuç depolayan sorgudan birbirinden ayrı tutar.  
  
     [!code-csharp[csrefQueryExpBasics#48](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]  
  
 Önceki örnekte çağrısında sorgu yürütülür `Count`, çünkü `Count` sonuçlarda tarafından döndürülen öğe sayısını belirlemek için yineleme gerekir `highScoresQuery`.  
  
## <a name="what-is-a-query-expression"></a>Bir sorgu ifadesi nedir?  

 A *sorgu ifadesi* olan sorgu söz dizimi ifade edilen bir sorgu. Bir sorgu ifadesi bir birinci sınıf dil yapıdır. Diğer ifadesi gibi ve C# ifade geçerli bağlamda kullanılabilir. SQL veya XQuery benzer bir tanımlayıcı sözdizimi yazılmış yan tümceleri kümesi, bir sorgu ifadesi oluşur. Her yan tümcesi bir veya daha fazla C# ifadeler sırayla içeriyor ve bu ifadeler kendilerini bir sorgu ifadesi olabilir veya bir sorgu ifadesi içeriyor.  
  
 Bir sorgu ifadesi ile başlamalıdır bir [gelen](../language-reference/keywords/from-clause.md) yan tümcesi ile bitmelidir bir [seçin](../language-reference/keywords/select-clause.md) veya [grup](../language-reference/keywords/group-clause.md) yan tümcesi. İlk arasında `from` yan tümcesi ve son `select` veya `group` yan tümcesi, bir veya daha fazla isteğe bağlı bu yan tümceleri içerebilir: [nerede](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [birleştirme ](../language-reference/keywords/join-clause.md), [izin](../language-reference/keywords/let-clause.md) ve hatta ek [gelen](../language-reference/keywords/from-clause.md) yan tümceleri. De kullanabilirsiniz [içine](../language-reference/keywords/into.md) sonucu etkinleştirmek için anahtar sözcüğü bir `join` veya `group` ek sorgu yan tümceleri aynı sorgu ifadesinde için kaynak olarak hizmet vermek için yan tümcesi.  
  
### <a name="query-variable"></a>Sorgu değişkeni  
 
 LINQ to depolayan herhangi bir değişken bir sorgu değişkeni olan bir *sorgu* yerine *sonuçları* sorgu. Daha açık belirtmek gerekirse bir sorgu değişkeni her zaman bu üzerinden içinde yinelendiğinde öğe dizisi üretir bir numaralandırılabilir türüdür bir `foreach` deyimi veya doğrudan arama kendi `IEnumerator.MoveNext` yöntemi.  
  
 Aşağıdaki kod örneği, bir basit sorgu ifadesi bir veri kaynağı ile bir filtre yan tümcesi, bir sıralama yan tümce ve kaynak öğelerinin hiçbir dönüştürme gösterir. `select` Yan tümcesi sorgu sona erer.  
  
 [!code-csharp[csrefQueryExpBasics#49](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]  
  
 Önceki örnekte, `scoreQuery` olan bir *sorgu değişkeni* bazen adlandırılır olarak yalnızca bir *sorgu*. Sorgu değişkeni içinde üretilen hiçbir gerçek sonuç verileri depolayan `foreach` döngü. Ve ne zaman `foreach` deyimini yürütür, sorgu sonuçları için sorgu değişken üzerinden döndürülmez `scoreQuery`. Yineleme değişkeni yerine, döndürülen `testScore`. `scoreQuery` Değişkeni bir saniyede yinelendiğinde `foreach` döngü. Bu ne veri kaynağı değiştirilmiş sürece aynı sonuçları oluşturur.  
  
 Bir sorgu değişkeni ifade edilen bir sorgu, sorgu söz dizimi veya yöntem sözdizimi veya ikisinin birleşimini depolayabilir. Aşağıdaki örneklerde, her ikisi de `queryMajorCities` ve `queryMajorCities2` sorgu değişkenleri şunlardır:  
  
 [!code-csharp[csrefQueryExpBasics#50](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]  
  
 Öte yandan, aşağıdaki iki örnek sorgu değişkenleri bile her aracılığıyla olmayan değişkenleri, bir sorgu başlatılır gösterir. Sonuçları deposunu çünkü bunlar sorgu değişkenleri değildir:  
  
 [!code-csharp[csrefQueryExpBasics#51](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]  
  
 Express sorgular için farklı yollar hakkında daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Sorgu değişkenlerinin açık ve kapalı yazma  
 
 Bu belge sorgu değişkeni arasındaki türü ilişkiyi göstermek için sorgu değişkeni açık türü genellikle sağlar ve [select yan tümcesi](../language-reference/keywords/select-clause.md). Ancak, aynı zamanda kullanabileceğiniz [var](../language-reference/keywords/var.md) derleme zamanında türü bir sorgu değişkeni (veya herhangi bir yerel değişken) anlamak için derleyici istemek üzere anahtar sözcük. Örneğin, bu konuda daha önce gösterildiği sorgu örnek de örtülü yazma kullanarak belirtilebilir:  
  
 [!code-csharp[csrefQueryExpBasics#52](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]  
  
 Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [tür ilişkileri LINQ Sorgu işlemleri](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
### <a name="starting-a-query-expression"></a>Bir sorgu ifadesi başlatılıyor  
 
 Bir sorgu ifadesi ile başlamalıdır bir `from` yan tümcesi. Aralık değişkeni ile birlikte bir veri kaynağını belirtir. Aralık değişkeni kaynak sıradaki geçiş kaynak sıradaki art arda gelen her bir öğesinde temsil eder. Aralık değişkeni kesinlikle veri kaynağındaki öğelerin türü göre yazılmış. Aşağıdaki örnekte, çünkü `countries` dizisidir `Country` nesneleri aralık değişkeni olarak yazılan de `Country`. Aralık değişkeni kesin türü belirtilmiş olduğundan, dot işleci türü kullanılabilir tüm üyelerine erişmek için kullanabilirsiniz.  
  
 [!code-csharp[csrefQueryExpBasics#53](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]  
  
 Sorgu noktalı virgül ile veya ile çıkıldı kadar aralık değişkeni kapsamında olan bir *devamlılık* yan tümcesi.  
  
 Birden çok sorgu ifadesi içerebilir `from` yan tümceleri. Ek kullanım `from` yan tümceleri kaynak sıradaki her bir öğesinde kendisini koleksiyonu olduğunda veya bir koleksiyonu içerir. Örneğin, koleksiyonu sahip olduğunuzu varsayın `Country` nesneleri, her biri bir koleksiyonunu içeren `City` adlı nesneleri `Cities`. Sorgu için `City` nesneleri her `Country`, iki kullanmak `from` aşağıda gösterildiği gibi yan tümceleri:  
  
 [!code-csharp[csrefQueryExpBasics#54](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]  
  
 Daha fazla bilgi için bkz: [from yan tümcesi](../language-reference/keywords/from-clause.md).  
  
### <a name="ending-a-query-expression"></a>Bir sorgu ifadesi bitiş  
 
 Bir sorgu ifadesi ile bitmelidir bir `group` yan tümcesinin veya bir `select` yan tümcesi.  
  
#### <a name="group-clause"></a>group tümcesi  
 
 Kullanım `group` grupları dizisi üretmek için yan tümceyi belirttiğiniz bir anahtar tarafından düzenlenir. Anahtar herhangi bir veri türü olabilir. Örneğin, aşağıdaki sorguda bir veya daha fazla bilgi içeren bir dizi grupları oluşturur `Country` nesneleri ve, anahtarı bir `char` değeri.  
  
 [!code-csharp[csrefQueryExpBasics#55](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]  
  
 Gruplama hakkında daha fazla bilgi için bkz: [group yan tümcesi](../language-reference/keywords/group-clause.md).  
  
#### <a name="select-clause"></a>select tümcesi  
 Kullanım `select` sıralarının tüm diğer türleri oluşturmak için yan tümcesi. Basit bir `select` yan tümcesi yalnızca veri kaynağında bulunan nesneleri aynı türde nesneler dizisi üretir. Bu örnekte, veri kaynağını içeren `Country` nesneleri. `orderby` Yan tümcesi yalnızca yeni bir sipariş öğeleri sıralar ve `select` yan tümcesi üreten bir dizi yeniden düzenlenen `Country` nesneleri.  
  
 [!code-csharp[csrefQueryExpBasics#56](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]  
  
 `select` Yan tümcesi, yeni türleri dizileri kaynak verileri dönüştürmek için kullanılabilir. Bu dönüşüm de adlı bir *projeksiyon*. Aşağıdaki örnekte, `select` yan tümcesi *projeleri* yalnızca bir alt kümesini özgün öğesi alanları içeren bir dizi anonim türler. Yeni nesneler nesne Başlatıcı kullanarak başlatılmış olduğunu unutmayın.  
  
 [!code-csharp[csrefQueryExpBasics#57](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]  
  
 Tüm yolları hakkında daha fazla bilgi için bir `select` yan tümcesi, kaynak verileri dönüştürmek için bkz: kullanılabilir [select yan tümcesi](../language-reference/keywords/select-clause.md).  
  
#### <a name="continuations-with-into"></a>Devamlılıklar "içine" ile  
 
 Kullanabileceğiniz `into` in anahtar sözcüğü bir `select` veya `group` bir sorgu depolayan geçici bir tanımlayıcı oluşturmaya yan tümcesi. Bunu bir gruplandırma sonra bir sorgu ek sorgu işlemleri gerçekleştirmek veya işlemi seçin. Aşağıdaki örnekte `countries` popülasyon 10 milyon aralıklara göre gruplandırılır. Bu gruplar oluşturulan, ek yan tümceleri filtre bazı grupları out ve sıralama için sonra sipariş artan grupları. Bu ek işlemler gerçekleştirmek üzere devamlılık temsil ettiği `countryGroup` gereklidir.  
  
 [!code-csharp[csrefQueryExpBasics#58](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]  
  
 Daha fazla bilgi için bkz: [içine](../language-reference/keywords/into.md).  
  
### <a name="filtering-ordering-and-joining"></a>Filtreleme, sıralama ve birleştirme

 Başlangıç arasında `from` yan tümcesi ve bitiş `select` veya `group` yan tümcesi, diğer tüm yan tümceleri (`where`, `join`, `orderby`, `from`, `let`) isteğe bağlıdır. İsteğe bağlı bir yan tümceleri hiçbirini sıfır veya birden çok kez sorgu gövdesinde kullanılabilir.  
  
#### <a name="where-clause"></a>where tümcesi  

 Kullanım `where` veri kaynağını öğeleri filtrelemek için yan tümceyi dayalı bir veya daha fazla koşullu ifadeler. `where` Yan tümcesi aşağıdaki örnekte iki koşul ile bir koşul bulunmaktadır.  
  
 [!code-csharp[csrefQueryExpBasics#59](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]  
  
 Daha fazla bilgi için bkz: [burada yan tümcesi](../language-reference/keywords/where-clause.md).  
  
#### <a name="orderby-clause"></a>orderby tümcesi

 Kullanım `orderby` artan veya azalan sonuçları sıralamak için yan tümcesi. İkincil sıralamalar de belirtebilirsiniz. Aşağıdaki örnekte birincil sıralama gerçekleştirir `country` kullanarak nesneleri `Area` özelliği. Kullanarak ardından bir ikincil sıralama gerçekleştirir `Population` özelliği.  
  
 [!code-csharp[csrefQueryExpBasics#60](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]  
  
 `ascending` Anahtar sözcüğü isteğe bağlıdır; hiçbir sipariş belirtilmezse varsayılan sıralama düzeni kullanılır. Daha fazla bilgi için bkz: [orderby yan tümcesinin](../language-reference/keywords/orderby-clause.md).  
  
#### <a name="join-clause"></a>join tümcesi

 Kullanım `join` bir eşitlik karşılaştırması her öğesinde belirtilen anahtarlar arasındaki temel yan tümcesini ilişkilendirmek ve/veya başka bir veri kaynağından alınan öğeleri ile bir veri kaynağından alınan öğeleri birleştirin. LINQ, birleştirme işlemleri öğeleri farklı olan nesneler dizisi üzerinde gerçekleştirilir. İki sıraları katıldıktan sonra kullanmanız gerekir bir `select` veya `group` deyimi çıktı sırayla depolamak için hangi öğesi belirtin. Anonim bir tür, çıktı sırası için yeni bir tür her ilişkili öğe kümesi özelliklerinden birleştirebilirsiniz için de kullanabilirsiniz. Aşağıdaki örnek ilişkilendirir `prod` özelliği nesneleri `Category` özelliği kategorileri birine eşleşen `categories` dize dizisi. Ürünler, `Category` herhangi bir dize eşleşmiyor `categories` filtrelenir. `select` Deyimi özellikleri hem de alınır yeni bir tür projeleri `cat` ve `prod`.  
  
 [!code-csharp[csrefQueryExpBasics#61](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]  
  
 Bir grup birleştirme sonuçlarını depolayarak da gerçekleştirebilirsiniz `join` işlemi kullanarak geçici bir değişken içine [içine](../language-reference/keywords/into.md) anahtar sözcüğü. Daha fazla bilgi için bkz: [JOIN yan tümcesi](../language-reference/keywords/join-clause.md).  
  
#### <a name="let-clause"></a>let tümcesi 

 Kullanım `let` içinde yeni bir aralık değişkeni bir yöntem çağrısı gibi bir ifadenin sonucunu depolamak için yan tümcesi. Aşağıdaki örnekte, aralık değişkeni `firstName` tarafından döndürülen dize dizisi ilk öğesi depolar `Split`.  
  
 [!code-csharp[csrefQueryExpBasics#62](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]  
  
 Daha fazla bilgi için bkz: [let tümcesi](../language-reference/keywords/let-clause.md).  
  
### <a name="subqueries-in-a-query-expression"></a>Bir sorgu ifadesinde alt sorgular  

 Bir sorgu yan tümcesi kendisini bazen olarak adlandırılır bir sorgu ifadesi içeriyor olabilir bir *alt sorgu*. Her alt sorgu kendi ile başlayan `from` ilk aynı veri kaynağına mutlaka göstermiyor yan tümcesi `from` yan tümcesi. Örneğin, aşağıdaki sorguda kullanılan sorgu ifadesi gruplandırma işlemi sonuçları almak için select deyiminde gösterir.  
  
 [!code-csharp[csrefQueryExpBasics#63](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: gruplandırma işleminde alt sorgu gerçekleştirme](perform-a-subquery-on-a-grouping-operation.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../programming-guide/index.md)  
 [LINQ Sorgu ifadeleri](index.md)  
 [Sorgu anahtar sözcükleri (LINQ)](../language-reference/keywords/query-keywords.md)  
 [Standart sorgu işleçlerine genel bakış](../programming-guide/concepts/linq/standard-query-operators-overview.md)
