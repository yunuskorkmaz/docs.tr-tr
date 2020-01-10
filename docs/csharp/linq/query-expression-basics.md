---
title: Sorgu ifadesi temelleri (LINQ ın C#)
description: Sorgu ifadeleriyle ilgili kavramları tanıtır
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 5ebe2163df47c60c677d7ac911ce0f65529835eb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635866"
---
# <a name="query-expression-basics"></a>Sorgu ifadesi temelleri

Bu makalede, içindeki C#sorgu ifadeleriyle ilgili temel kavramlar tanıtılmaktadır.

## <a name="what-is-a-query-and-what-does-it-do"></a>Sorgu nedir ve ne yapar?

*Sorgu* , belirli bir veri kaynağından (veya kaynaklardan) hangi verilerin alınması gerektiğini ve döndürülen verilerin hangi şekil ve kuruluşun olması gerektiğini açıklayan bir yönergeler kümesidir. Bir sorgu, ürettiği sonuçlardan farklıdır.

Genellikle, kaynak verileri aynı türdeki öğelerin bir sırası olarak mantıksal olarak düzenlenir. Örneğin, bir SQL veritabanı tablosu bir dizi satır içerir. XML dosyasında, XML öğelerinin bir "sırası" vardır (ancak bunlar bir ağaç yapısında hiyerarşik olarak düzenlenirler). Bellek içi bir koleksiyon, bir dizi nesne içerir.

Uygulamanın bakış açısından, özgün kaynak verilerinin belirli türü ve yapısı önemli değildir. Uygulama, kaynak verileri her zaman bir <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601> koleksiyonu olarak görür. Örneğin, LINQ to XML, kaynak veriler bir `IEnumerable`\<<xref:System.Xml.Linq.XElement>> olarak görünür hale getirilir.

Bu kaynak sırası verildiğinde bir sorgu üç işlemlerden birini alabilir:

- Tek tek öğeleri değiştirmeden yeni bir sıra oluşturmak için öğelerin bir alt kümesini alın. Sorgu daha sonra aşağıdaki örnekte gösterildiği gibi, döndürülen sırayı çeşitli şekillerde sıralayabilir veya gruplandırabilir (`scores` bir `int[]`olduğunu varsayın):

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Önceki örnekte olduğu gibi bir dizi öğe alın, ancak bunları yeni bir nesne türüne dönüştürün. Örneğin, bir sorgu bir veri kaynağındaki belirli müşteri kayıtlarından yalnızca soyadlarını alabilir. Ya da tam kaydı alabilir ve ardından, son sonuç sırasını oluşturmadan önce başka bir bellek içi nesne türü veya hatta XML verisi oluşturmak için bunu kullanabilirsiniz. Aşağıdaki örnek, bir `int` `string`bir yansıtmayı gösterir. `highScoresQuery`yeni türünü aklınızda yazın.

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Kaynak verilerle ilgili bir tekil değer alın, örneğin:

  - Belirli bir koşulla eşleşen öğe sayısı.

  - En büyük veya en az değere sahip öğe.

  - Bir koşulla eşleşen ilk öğe veya belirli bir öğe kümesindeki belirli değerlerin toplamı. Örneğin, aşağıdaki sorgu `scores` tamsayı dizisinden 80 ' den büyük puan sayısını döndürür:

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    Önceki örnekte, `Count` metoduna çağrıdan önce sorgu ifadesinin etrafında parantezler kullanımını aklınızda. Bunu somut sonucu depolamak için yeni bir değişken kullanarak da ifade edebilirsiniz. Bu teknik daha okunabilir çünkü sorguyu depolayan değişkeni bir sonucu depolayan sorgudan ayrı tutar.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

Önceki örnekte sorgu `Count`çağrısında yürütülür, çünkü `Count` `highScoresQuery`tarafından döndürülen öğelerin sayısını belirlemede sonuçları yinelemek zorunda olmalıdır.

## <a name="what-is-a-query-expression"></a>Sorgu ifadesi nedir?

Sorgu *ifadesi* sorgu sözdiziminde ifade edilen bir sorgudur. Sorgu ifadesi birinci sınıf dil yapısıdır. Bu, başka bir ifade gibi olduğu gibi, bir ifadenin geçerli olduğu herhangi bir C# bağlamda kullanılabilir. Sorgu ifadesi SQL veya XQuery ile benzer bir bildirime dayalı sözdiziminde yazılmış bir yan tümce kümesinden oluşur. Sırasıyla her bir yan tümce bir veya daha C# fazla ifade içerir ve bu ifadeler bir sorgu ifadesi veya bir sorgu ifadesi olabilir.

Sorgu ifadesinin [from](../language-reference/keywords/from-clause.md) yan tümcesiyle başlaması ve [Select](../language-reference/keywords/select-clause.md) veya [Group](../language-reference/keywords/group-clause.md) yan tümcesiyle bitmesi gerekir. İlk `from` yan tümcesi ile son `select` veya `group` yan tümcesi arasında bu isteğe bağlı bir veya daha fazla yan tümce bulunabilir: [WHERE](../language-reference/keywords/where-clause.md), [OrderBy](../language-reference/keywords/orderby-clause.md), [JOIN](../language-reference/keywords/join-clause.md), [Let](../language-reference/keywords/let-clause.md) ve [hatta ek yan](../language-reference/keywords/from-clause.md) tümceler. Ayrıca, aynı sorgu ifadesinde ek sorgu yan tümceleri için kaynak olarak kullanılacak bir `join` veya `group` yan tümcesinin sonucunu etkinleştirmek için [into](../language-reference/keywords/into.md) anahtar sözcüğünü kullanabilirsiniz.

### <a name="query-variable"></a>Sorgu değişkeni

LINQ içinde, bir sorgu değişkeni sorgu *sonuçları* yerine *sorgu* depolayan herhangi bir değişkendir. Daha belirgin bir şekilde, bir sorgu değişkeni her zaman sıralanabilir bir tür veya bir `foreach` ifadesinde tekrarlanmıştır veya `IEnumerator.MoveNext` yöntemine doğrudan çağrı yapılır.

Aşağıdaki kod örneği, bir veri kaynağı, bir filtre yan tümcesi, tek bir sıralama yan tümcesi ve kaynak öğelerinin dönüştürülmesine sahip basit bir sorgu ifadesini gösterir. `select` yan tümcesi sorguyu sonlandırır.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

Önceki örnekte `scoreQuery`, bazen yalnızca bir *sorgu*olarak adlandırılan bir *sorgu değişkenidir* . Sorgu değişkeni, `foreach` döngüsünde üretilen gerçek sonuç verilerini depolar. `foreach` deyimleri yürütüldüğünde sorgu sonuçları sorgu değişkeni `scoreQuery`üzerinden döndürülmez. Bunun yerine, `testScore`yineleme değişkeni üzerinden döndürülür. `scoreQuery` değişkeni ikinci bir `foreach` döngüsünde yinelenebilir. Ya da veri kaynağı değiştirilmedikçe aynı sonuçları üretecektir.

Sorgu değişkeni sorgu söz dizimi veya yöntem sözdiziminde ifade edilen bir sorguyu veya ikisinin birleşimini saklayabilir. Aşağıdaki örneklerde hem `queryMajorCities` hem de `queryMajorCities2` sorgu değişkenleridir:

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

Diğer taraftan, aşağıdaki iki örnek, her biri bir sorguyla başlatılmış olsa da, sorgu değişkenleri olmayan değişkenleri gösterir. Sonuçları depoladıklarından sorgu değişkenleri değildir:

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Sorgu sorgularının farklı yolları hakkında daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Sorgu değişkenlerinin açık ve örtük olarak yazılması

Bu belge genellikle sorgu değişkeni ve [Select yan tümcesi](../language-reference/keywords/select-clause.md)arasındaki tür ilişkisini göstermek için sorgu değişkeninin açık türünü sağlar. Ancak, derleyicisine derleme zamanında bir sorgu değişkeni (veya başka bir yerel değişken) türünü çıkarmasını söylemek için [var](../language-reference/keywords/var.md) anahtar sözcüğünü de kullanabilirsiniz. Örneğin, bu konuda daha önce gösterilen sorgu örneği örtük yazma kullanılarak da ifade edilebilir:

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md) [örtük olarak yazılan yerel değişkenler](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve tür ilişkileri.

### <a name="starting-a-query-expression"></a>Sorgu ifadesi başlatılıyor

Sorgu ifadesinin bir `from` yan tümcesiyle başlaması gerekir. Bir veri kaynağını bir Aralık değişkeniyle birlikte belirtir. Aralık değişkeni, kaynak sırası çapraz taşınırken kaynak dizideki birbirini izleyen her öğeyi temsil eder. Aralık değişkeni, veri kaynağındaki öğelerin türüne göre kesin olarak yazılır. Aşağıdaki örnekte, `countries` bir `Country` nesneleri dizisi olduğundan, Aralık değişkeni de `Country`olarak yazılır. Aralık değişkeni kesin olarak yazıldığından, türün kullanılabilir üyelerine erişmek için nokta işlecini kullanabilirsiniz.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

Aralık değişkeni, sorgunun noktalı virgül veya *devamlılık* yan tümcesi ile çıkış yapılıncaya kadar kapsamdadır.

Sorgu ifadesinde birden çok `from` yan tümce bulunabilir. Kaynak dizideki her öğe bir koleksiyon ya da bir koleksiyon içerdiğinde ek `from` yan tümceleri kullanın. Örneğin, her biri `Cities`adlı `City` nesnelerinin bir koleksiyonunu içeren `Country` nesneleri koleksiyonunuz olduğunu varsayalım. Her `Country``City` nesneleri sorgulamak için, burada gösterildiği gibi iki `from` yan tümcesini kullanın:

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Daha fazla bilgi için bkz. [from yan tümcesi](../language-reference/keywords/from-clause.md).

### <a name="ending-a-query-expression"></a>Sorgu ifadesi bitiriliyor

Sorgu ifadesinin bir `group` yan tümcesiyle veya bir `select` yan tümcesiyle bitmesi gerekir.

#### <a name="group-clause"></a>group tümcesi

Belirttiğiniz bir anahtarla düzenlenmiş bir grup sırası oluşturmak için `group` yan tümcesini kullanın. Anahtar herhangi bir veri türü olabilir. Örneğin, aşağıdaki sorgu bir veya daha fazla `Country` nesne içeren ve anahtarı `char` bir değer olan bir grup sırası oluşturur.

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Gruplandırma hakkında daha fazla bilgi için bkz. [Group yan tümcesi](../language-reference/keywords/group-clause.md).

#### <a name="select-clause"></a>select tümcesi

Tüm diğer sıra türlerini oluşturmak için `select` yan tümcesini kullanın. Basit bir `select` yan tümcesi, veri kaynağında bulunan nesnelerle aynı nesne türü dizisini oluşturur. Bu örnekte, veri kaynağı `Country` nesneleri içerir. `orderby` yan tümcesi yalnızca öğeleri yeni bir sıraya göre sıralar ve `select` yan tümcesi, yeniden düzenlenen `Country` nesnelerinin bir dizisini oluşturur.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

`select` yan tümcesi, kaynak verileri yeni türdeki sıralara dönüştürmek için kullanılabilir. Bu dönüşüme Ayrıca bir *projeksiyon*adı verilir. Aşağıdaki örnekte, `select` yan tümcesi, özgün öğedeki alanların *yalnızca bir alt* kümesini içeren anonim türlerin bir dizisini içerir. Yeni nesnelerin bir nesne Başlatıcısı kullanılarak başlatıldığını unutmayın.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

`select` yan tümcesinin kaynak verileri dönüştürmek için kullanılabileceği tüm yollar hakkında daha fazla bilgi için bkz. [Select yan tümcesi](../language-reference/keywords/select-clause.md).

#### <a name="continuations-with-into"></a>"İnto" ile devamlılıklar

Bir sorgu depolayan geçici bir tanımlayıcı oluşturmak için bir `select` veya `group` yan tümcesindeki `into` anahtar sözcüğünü kullanabilirsiniz. Bir gruplandırma veya seçme işleminden sonra sorgu üzerinde ek sorgu işlemleri gerçekleştirmeniz gerektiğinde bunu yapın. Aşağıdaki örnekte `countries`, 10.000.000 aralıklarında popülasyona göre gruplandırılır. Bu gruplar oluşturulduktan sonra, ek yan tümceler bazı grupları filtreleyip grupları artan düzende sıralayacak. Bu ek işlemleri gerçekleştirmek için `countryGroup` tarafından temsil edilen devamlılık gereklidir.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Daha fazla bilgi için bkz [..](../language-reference/keywords/into.md)

### <a name="filtering-ordering-and-joining"></a>Filtreleme, sıralama ve birleştirme

Başlangıç `from` yan tümcesi ve bitiş `select` veya `group` yan tümcesi arasında, diğer tüm yan tümceler (`where`, `join`, `orderby`, `from`, `let`) isteğe bağlıdır. İsteğe bağlı yan tümcelerden herhangi biri, bir sorgu gövdesinde sıfır kez veya birden çok kez kullanılabilir.

#### <a name="where-clause"></a>where tümcesi

Bir veya daha fazla koşul ifadesine göre kaynak verilerden öğeleri filtrelemek için `where` yan tümcesini kullanın. Aşağıdaki örnekteki `where` yan tümcesinin iki koşula sahip bir koşulu vardır.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Daha fazla bilgi için bkz. [WHERE yan tümcesi](../language-reference/keywords/where-clause.md).

#### <a name="orderby-clause"></a>orderby tümcesi

Sonuçları artan veya azalan sırada sıralamak için `orderby` yan tümcesini kullanın. Ayrıca, ikincil sıralama düzenleri de belirtebilirsiniz. Aşağıdaki örnek, `Area` özelliğini kullanarak `country` nesnelerinde birincil bir sıralama gerçekleştirir. Daha sonra `Population` özelliğini kullanarak ikincil bir sıralama gerçekleştirir.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

`ascending` anahtar sözcüğü isteğe bağlıdır; herhangi bir sipariş belirtilmemişse varsayılan sıralama düzeni olur. Daha fazla bilgi için bkz. [OrderBy tümcesi](../language-reference/keywords/orderby-clause.md).

#### <a name="join-clause"></a>join tümcesi

Her bir öğesinde belirtilen anahtarlar arasındaki eşitlik karşılaştırmasına bağlı olarak, bir veri kaynağındaki öğeleri farklı bir veri kaynağındaki öğelerle ilişkilendirmek ve/veya birleştirmek için `join` yan tümcesini kullanın. LINQ ' ta, öğeleri farklı türlerde olan nesne dizileri üzerinde JOIN işlemleri gerçekleştirilir. İki dizinin birleştirildikten sonra, çıkış dizisinde hangi öğenin depolanacağını belirtmek için bir `select` veya `group` ifadesini kullanmanız gerekir. Ayrıca, her bir ilişkili öğe kümesinden özellikleri, çıkış sırası için yeni bir türe birleştirmek üzere anonim bir tür de kullanabilirsiniz. Aşağıdaki örnek, `Category` özelliği `categories` dize dizisindeki kategorilerden biriyle eşleşen `prod` nesneleri ilişkilendirir. `Category` `categories` hiçbir dizeyle eşleşmeyen ürünler filtrelenmez. `select` deyimleri, özellikleri `cat` ve `prod`alınan yeni bir tür.

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Ayrıca, `join` işleminin sonuçlarını, [into](../language-reference/keywords/into.md) anahtar sözcüğünü kullanarak geçici bir değişkende depolayarak da bir grup birleşimi gerçekleştirebilirsiniz. Daha fazla bilgi için bkz. [JOIN yan tümcesi](../language-reference/keywords/join-clause.md).

#### <a name="let-clause"></a>let tümcesi 

Yöntem çağrısı gibi bir ifadenin sonucunu yeni bir Aralık değişkeninde depolamak için `let` yan tümcesini kullanın. Aşağıdaki örnekte, Aralık değişkeni `firstName` `Split`tarafından döndürülen dizelerin dizisinin ilk öğesini depolar.

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Daha fazla bilgi için bkz. [Let yan tümcesi](../language-reference/keywords/let-clause.md).

### <a name="subqueries-in-a-query-expression"></a>Sorgu ifadesinde alt sorgular

Sorgu yan tümcesi, bazen *alt sorgu*olarak adlandırılan bir sorgu ifadesi içerebilir. Her alt sorgu, ilk `from` yan tümcesindeki aynı veri kaynağını işaret etmek zorunda olmayan kendi `from` yan tümcesiyle başlar. Örneğin, aşağıdaki sorgu, Gruplandırma işleminin sonuçlarını almak için SELECT deyiminde kullanılan bir sorgu ifadesini gösterir.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Daha fazla bilgi için bkz. [Gruplandırma işleminde alt sorgu gerçekleştirme](perform-a-subquery-on-a-grouping-operation.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../programming-guide/index.md)
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [Sorgu anahtar sözcükleri (LINQ)](../language-reference/keywords/query-keywords.md)
- [Standart sorgu işleçlerine genel bakış](../programming-guide/concepts/linq/standard-query-operators-overview.md)
