---
title: Sorgu ifadesi temelleri (C# üzerinde LINQ)
description: Sorgu ifadeleri ilgili kavramlar tanıtılmaktadır.
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 68f338381e354f4944539d63ca3a3cc3500031c1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192742"
---
# <a name="query-expression-basics"></a>Sorgu ifadesi temelleri

Bu makalede, C# sorgu ifadeleri ilgili temel kavramlar tanıtılmaktadır.

## <a name="what-is-a-query-and-what-does-it-do"></a>Bir sorgu nedir ve ne işe yarar?

A *sorgu* döndürülen verileri hangi verilerin belirli bir veri kaynağı (veya kaynaklarından) almak ve hangi şekli ve kuruluş için olmalıdır açıklayan yönergeler kümesidir. Bir sorgu ürettiği sonuçlardan farklıdır.

Genel olarak, kaynak verileri mantıksal olarak aynı türden bir öğe dizisi düzenlenmiştir. Örneğin, bir SQL veritabanı tablosunda bir dizi satır içerir. Bir XML dosyasında yoktur bir "dizisi" XML öğesi (bunlar hiyerarşik bir ağaç yapısında düzenlenmiş rağmen). Bir bellek içi koleksiyon nesneleri dizisi içerir.

Bir uygulamanın bakış açısından belirli türüne ve yapısına özgün kaynak verilerin önemli olmadığından. Uygulama her zaman kaynak verisi olarak gördüğü bir <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601> koleksiyonu. Örneğin, LINQ to XML, kaynak veriler olarak görünür hale gelir bir `IEnumerable` \< <xref:System.Xml.Linq.XElement>>.

Bu kaynak dizisi göz önünde bulundurulduğunda, bir sorgu işlemlerden birini yapabilirsiniz:

- Tek tek öğelerine değiştirmeden yeni bir sıra oluşturmak için öğeleri kümesini alır. Sorgu sonra sıralama veya aşağıdaki örnekte gösterildiği gibi çeşitli şekillerde döndürülen dizi Grup (varsayar `scores` olduğu bir `int[]`):

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Önceki örnekte olduğu gibi öğeleri dizisi alabilir, ancak bunları yeni bir nesne türüne dönüştürün. Örneğin, bir sorgu, bir veri kaynağındaki belirli bir müşteri kayıt yalnızca son adlarını alabilirsiniz. Kaydın tamamına almak ve başka bir bellek içi nesne türü veya hatta kullanmak Sonuç dizisi oluşturmadan XML verileri. Aşağıdaki örnek, bir projeksiyon gelen gösterir. bir `int` için bir `string`. Yeni Not `highScoresQuery`.

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Kaynak veriler hakkında bir tekil değer gibi alın:

  - Belirli bir koşulu karşılayan bir öğe sayısı.

  - En yüksek veya en düşük değere sahip öğe.

  - Bir koşul ya da belirtilen öğeleri kümesi içinde belirli değerlerin toplamını eşleşen ilk öğe. Örneğin, aşağıdaki sorguyu puanları 80'den büyüktür döndürür `scores` tamsayı dizisi:

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    Önceki örnekte, parantezler çağırmadan önce sorgu ifadesinde kullanımına dikkat edin `Count` yöntemi. Bu, somut sonucu depolamak için yeni bir değişken kullanarak da koyabilirsiniz. Sorguyu depolayan değişken sorgudan bir sonuç depolar ayrı tuttuğu bu daha okunabilir bir tekniktir.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

Önceki örnekte, sorgu çağrısında yürütüldüğü `Count`, çünkü `Count` tarafından döndürülen öğe sayısını belirlemek için sonuçları üzerinde yinelenmelidir `highScoresQuery`.

## <a name="what-is-a-query-expression"></a>Sorgu ifadesi nedir?

A *sorgu ifadesi* sorgu söz diziminde ifade bir sorgu verilmiştir. Birinci sınıf dil yapısı bir sorgu ifadesidir. Bu diğer ifade gibi ve bir C# ifadesi geçerli olduğu her bağlamda kullanılabilir. Sorgu ifadesi tümceleri SQL veya XQuery benzer bir bildirim temelli söz yazılan bir dizi oluşur. Her yan tümcesi sırayla bir veya daha fazla C# ifadeleri içeriyor ve bu ifadeler kendilerini bir sorgu ifadesi veya olabilir bir sorgu ifadesi içerir.

Sorgu ifadesi ile başlamalıdır bir [gelen](../language-reference/keywords/from-clause.md) yan tümcesi ve ile sona ermelidir bir [seçin](../language-reference/keywords/select-clause.md) veya [grubu](../language-reference/keywords/group-clause.md) yan tümcesi. İlk arasında `from` yan tümcesi ve son `select` veya `group` yan tümcesi, bir veya daha fazla isteğe bağlı bu yan tümceleri içerebilir: [burada](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [birleştirme ](../language-reference/keywords/join-clause.md), [izin](../language-reference/keywords/let-clause.md) ve hatta ek [gelen](../language-reference/keywords/from-clause.md) yan tümceleri. Ayrıca [içine](../language-reference/keywords/into.md) sonucunu etkinleştirmek için anahtar sözcüğü bir `join` veya `group` ek sorgu yan tümceleri aynı sorgu ifadesinde kaynağı olarak görev yapacak yan tümcesi.

### <a name="query-variable"></a>Sorgu değişkeni

LINQ içinde bir sorgu değişkeni depolar herhangi bir değişken olduğu bir *sorgu* yerine *sonuçları* sorgu. Özellikle, bir sorgu değişkeni her zaman bu yinelenir, bir dizi öğe üretir bir numaralandırılabilir türüdür bir `foreach` deyimi veya doğrudan bir çağrı ile kendi `IEnumerator.MoveNext` yöntemi.

Aşağıdaki kod örneği, bir basit bir sorgu ifadesi bir veri kaynağı ile bir filtre yan tümcesi, bir sipariş yan tümce ve kaynak öğeleri herhangi bir dönüşüm gösterir. `select` Sorgu yan tümcesi sonlandırır.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

Önceki örnekte, `scoreQuery` olduğu bir *sorgu değişkeni* bazen adlandırılır olarak yalnızca bir *sorgu*. Sorgu değişkeni içinde oluşturulan hiçbir gerçek sonuç verileri depolayan `foreach` döngü. Ve ne zaman `foreach` deyimi yürütür, sorgu değişkeni sorgu sonuçları döndürülmez `scoreQuery`. Bunun yerine, yineleme değişkeni döndürülür `testScore`. `scoreQuery` Değişkeni bir saniye içinde yinelenir `foreach` döngü. Bu ne veri kaynağı değiştirilmiş sürece aynı sonuçları oluşturur.

Bir sorgu değişkeni sorgu söz dizimi veya yöntem sözdizimi veya ikisinin birleşimini ifade edilen bir sorgu depolayabiliriz. Aşağıdaki örneklerde, her ikisi de `queryMajorCities` ve `queryMajorCities2` sorgu değişkenleri:

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

Öte yandan, aşağıdaki iki örnek, her bir sorgu ile başlatılır olsa bile, sorgu değişkenleri olmayan değişkenlerini gösterir. Sonuçları depoladıkları çünkü bunlar sorgu değişkenleri değildir:

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Hızlı sorgular için farklı yollar hakkında daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Açık ve örtük değişkenler sorgu yazma

Bu belgeler, açık tür sorgu değişkeni sorgu değişkeninin türü ilişkisi göstermek için genellikle sağlar ve [select yan tümcesi](../language-reference/keywords/select-clause.md). Ancak, ayrıca kullanabileceğiniz [var](../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak derleyicinin derleme zamanında bir sorgu değişkeni (veya herhangi bir yerel değişken) türünü çıkarsamak için. Örneğin, bu konuda daha önce gösterilen sorgusu örneği de örtülü yazma'yı kullanarak ifade edilebilir:

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Daha fazla bilgi için [örtülü olarak yazılan yerel değişkenler](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [tür ilişkileri LINQ Sorgu işlemleri](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

### <a name="starting-a-query-expression"></a>Sorgu ifadesi başlatılıyor

Sorgu ifadesi ile başlamalıdır bir `from` yan tümcesi. Bu, bir aralık değişkeni ile birlikte bir veri kaynağını belirtir. Aralık değişkeni kaynak sırası geçiş kaynak sırası art arda gelen her öğeyi temsil eder. Aralık değişkeni bağlı olarak veri kaynağındaki öğelerin türü kesin. Aşağıdaki örnekte, çünkü `countries` dizisidir `Country` nesneleri olarak de Aralık değişkeninin türü `Country`. Aralık değişkeninin türü kesin olarak belirtilmiş olduğundan, nokta işleci türü kullanılabilir tüm üyelerine erişmek için kullanabilirsiniz.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

Sorgu veya noktalı virgül ile çıkıldı kadar aralık değişkeni kapsamları dahilinde olması bir *devamlılık* yan tümcesi.

Sorgu ifadesi birden çok içerebilir `from` yan tümceleri. Ek kullanım `from` tümceleri kaynak dizideki her öğe kendisi bir koleksiyon olduğunda veya bir koleksiyonu içerir. Örneğin, koleksiyonu olduğunu varsayın `Country` nesneleri, her biri bir koleksiyonunu içeren `City` adlı nesneleri `Cities`. Sorgulanacak `City` nesneleri her `Country`, iki kullanın `from` burada gösterildiği şekilde yan tümceleri:

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Daha fazla bilgi için [from yan tümcesinde](../language-reference/keywords/from-clause.md).

### <a name="ending-a-query-expression"></a>Sorgu ifadesi bitiş

Sorgu ifadesi ile bitmelidir bir `group` yan tümcesi veya `select` yan tümcesi.

#### <a name="group-clause"></a>group tümcesi

Kullanım `group` grupları dizisini üretmek için yan, belirttiğiniz bir anahtar tarafından düzenlenir. Herhangi bir veri türü olabilir. Örneğin, bir veya daha fazla bilgi içeren bir dizi gruplarının aşağıdaki sorguyu oluşturur `Country` nesneleri ve anahtarı olan bir `char` değeri.

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Gruplama hakkında daha fazla bilgi için bkz: [group yan tümcesi](../language-reference/keywords/group-clause.md).

#### <a name="select-clause"></a>select tümcesi

Kullanım `select` dizileri diğer tüm türleri üretmek için yan tümcesi. Basit bir `select` yan tümcesi yalnızca bir veri kaynağında bulunan nesneleri aynı türde nesneler dizisi üretir. Bu örnekte, veri kaynağını içeren `Country` nesneleri. `orderby` Yan tümcesi yalnızca yeni bir düzen ile öğeleri sıralar ve `select` yan tümcesi yeniden düzenlenen bir dizi üretir `Country` nesneleri.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

`select` Yan tümcesi, kaynak verileri yeni türleri sıralarına dönüştürmek için kullanılabilir. Bu dönüştürme de adlı bir *projeksiyon*. Aşağıdaki örnekte, `select` yan tümcesi *projeleri* yalnızca özgün öğesi alanları kümesini içeren bir anonim türleri dizisi. Yeni nesneler bir nesne Başlatıcı kullanarak başlatılır unutmayın.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

Tüm yollar hakkında daha fazla bilgi için bir `select` yan tümcesi, kaynak verileri dönüştürür, görmek için kullanılabilir [select yan tümcesi](../language-reference/keywords/select-clause.md).

#### <a name="continuations-with-into"></a>"İçinde" devamlılıklarla

Kullanabileceğiniz `into` anahtar sözcüğü bir `select` veya `group` yan tümcesi bir sorgu depolayan geçici bir tanımlayıcı. Bunu bir gruplandırma sonra bir sorgu ek sorgu işlemleri gerçekleştirmek veya işlemi seçin. Aşağıdaki örnekte `countries` 10 milyon aralığı içinde popülasyon göre gruplandırılır. Sonra bu gruplara bazı Gruplar'kullanıma ve sıralama için oluşturulmuş, ek yan tümceleri filtre sipariş artan grupları. Bu ek işlemleri gerçekleştirmek için devamlılık temsil ettiği `countryGroup` gereklidir.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Daha fazla bilgi için [içine](../language-reference/keywords/into.md).

### <a name="filtering-ordering-and-joining"></a>Filtreleme, sıralama ve birleştirme

Başlangıç arasında `from` yan tümcesi ve bitiş `select` veya `group` yan tümcesi, diğer tüm yan tümceleri (`where`, `join`, `orderby`, `from`, `let`) isteğe bağlıdır. Herhangi bir isteğe bağlı yan tümceleri sıfır veya birden çok kez bir sorgu gövdesi içinde kullanılabilir.

#### <a name="where-clause"></a>where tümcesi

Kullanım `where` veriler kaynak veri öğeleri filtrelemek için yan tümcesi bir veya daha fazla koşul ifadeleri temel. `where` Yan tümcesi aşağıdaki örnekte bir koşula sahip iki koşul vardır.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Daha fazla bilgi için [burada yan tümcesi](../language-reference/keywords/where-clause.md).

#### <a name="orderby-clause"></a>orderby tümcesi

Kullanım `orderby` sonuçları artan veya azalan düzende sıralamak için yan tümcesi. İkincil sıralamalar de belirtebilirsiniz. Aşağıdaki örnekte birincil sıralama gerçekleştirir `country` kullanarak nesneleri `Area` özelliği. Kullanarak ardından bir ikincil sıralama gerçekleştirir `Population` özelliği.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

`ascending` Anahtar sözcüğü isteğe bağlı; hiçbir sırası belirtilmezse, varsayılan sıralama düzeni. Daha fazla bilgi için [orderby yan tümcesinin](../language-reference/keywords/orderby-clause.md).

#### <a name="join-clause"></a>join tümcesi

Kullanım `join` her öğeyi belirtilen anahtarlarında bir eşitlik karşılaştırması temel ilişkilendirmek ve/veya başka bir veri kaynağındaki öğeleri içeren bir veri kaynağındaki öğeleri birleştirme yan tümcesi. LINQ içinde öğeleri farklı türleri olan nesneler dizisi üzerinde birleştirme işlemleri gerçekleştirilir. İki sıranın katıldıktan sonra kullanmalısınız bir `select` veya `group` deyimi bir çıkış dizisinde depolamak için hangi öğesi belirtin. Anonim bir tür, çıkış sırası için yeni bir türü her ilişkili öğeleri kümesi özelliklerinden birleştirin için de kullanabilirsiniz. Aşağıdaki örnek ilişkilendirir `prod` ayarlanmış nesneleri `Category` özelliği eşleşen kategoride birini `categories` dize dizisi. Ürünler olan `Category` herhangi bir dize eşleşmiyor `categories` filtrelenir. `select` Deyimi özellikleri hem de alınır, yeni bir tür projeleri `cat` ve `prod`.

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Grup birleştirme sonuçlarının depolayarak de gerçekleştirebilirsiniz `join` işlemi kullanarak geçici bir değişken içine [içine](../language-reference/keywords/into.md) anahtar sözcüğü. Daha fazla bilgi için [JOIN yan tümcesi](../language-reference/keywords/join-clause.md).

#### <a name="let-clause"></a>let tümcesi 

Kullanım `let` yan gibi bir yöntem çağrısının bir ifadenin sonucu yeni bir aralık değişkeninde depolar. Aşağıdaki örnekte, aralık değişkeni `firstName` tarafından döndürülen dizenin dizinin ilk öğesi depolar `Split`.

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Daha fazla bilgi için [let yan tümcesi](../language-reference/keywords/let-clause.md).

### <a name="subqueries-in-a-query-expression"></a>Bir sorgu ifadesinde alt sorgular

Sorgu yan tümcesi kendisini bazen olarak adlandırılan bir sorgu ifadesi içerebilir bir *alt sorgu*. Her alt sorgu kendi ile başlayan `from` mutlaka aynı veri kaynağına ilk göstermiyor yan tümcesi `from` yan tümcesi. Örneğin, aşağıdaki sorguyu bir gruplandırma işlemi sonuçlarını almak için select deyiminde kullanılan bir sorgu ifadesini gösterir.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Daha fazla bilgi için [nasıl yapılır: gruplandırma işleminde alt sorgu gerçekleştirme](perform-a-subquery-on-a-grouping-operation.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../programming-guide/index.md)  
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)  
- [Sorgu anahtar sözcükleri (LINQ)](../language-reference/keywords/query-keywords.md)  
- [Standart sorgu işleçlerine genel bakış](../programming-guide/concepts/linq/standard-query-operators-overview.md)  