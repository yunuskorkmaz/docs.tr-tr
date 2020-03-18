---
title: İfade sorgusu temelleri (C#'da LINQ)
description: Sorgu ifadelerle ilgili kavramları tanır
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 83beaa82d4b4b42ff9da5230edddd391b33a0717
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173360"
---
# <a name="query-expression-basics"></a>Sorgu ifadesi temelleri

Bu makalede, C#'daki sorgu ifadelerle ilgili temel kavramlar tanıtışlar.

## <a name="what-is-a-query-and-what-does-it-do"></a>Sorgu nedir ve ne işe yarar?

*Sorgu,* belirli bir veri kaynağından (veya kaynaklardan) hangi verilerin alınacağını ve döndürülen verilerin hangi şekil ve kuruluşa sahip olması gerektiğini açıklayan bir yönerge kümesidir. Sorgu, ürettiği sonuçlardan farklıdır.

Genellikle, kaynak veriler mantıksal olarak aynı türöğelerdizisi olarak düzenlenir. Örneğin, bir SQL veritabanı tablosu bir satır sırası içerir. Bir XML dosyasında, XML öğelerinin bir "sırası" vardır (ancak bunlar bir ağaç yapısında hiyerarşik olarak düzenlenir). Bellek içi koleksiyon bir nesne dizisi içerir.

Bir uygulamanın bakış açısından, özgün kaynak verilerin belirli türü ve yapısı önemli değildir. Uygulama her zaman kaynak verileri <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> bir veya koleksiyon olarak görür. Örneğin, LINQ'dan XML'e kadar kaynak veriler `IEnumerable` \< <xref:System.Xml.Linq.XElement>> olarak görünür hale getirilir.

Bu kaynak sırası göz önüne alındığında, bir sorgu üç şeyden birini yapabilir:

- Tek tek öğeleri değiştirmeden yeni bir dizi oluşturmak için öğelerin bir alt kümesini alın. Sorgu daha sonra aşağıdaki örnekte gösterildiği gibi döndürülen sırayı çeşitli `scores` şekillerde `int[]`sıralayabilir veya gruplayabilir (varsayalım bir):

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Önceki örnekte olduğu gibi bir öğe dizisi alın, ancak bunları yeni bir nesne türüne dönüştürün. Örneğin, bir sorgu bir veri kaynağındaki belirli müşteri kayıtlarından yalnızca son adları alabilir. Veya tam kaydı alabilir ve son sonuç sırasını oluşturmadan önce başka bir bellek nesne si veya xml veri oluşturmak için kullanabilirsiniz. Aşağıdaki örnek, bir 'den `int` `string`bir'e bir projeksiyon gösterir. Yeni türe `highScoresQuery`dikkat edin.

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Kaynak veriler le ilgili tek ton değerinde aşağıdakiler gibi alın:

  - Belirli bir koşulla eşleşen öğelerin sayısı.

  - En büyük veya en az değeri olan öğe.

  - Bir koşulla eşleşen ilk öğe veya belirli bir öğe kümesindeki belirli değerlerin toplamı. Örneğin, aşağıdaki sorgu, sonda dizisinden `scores` 80'den büyük puan sayısını döndürür:

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    Önceki örnekte, yönteme çağrıdan önce sorgu ifadesi etrafında parantez `Count` kullanımına dikkat edin. Ayrıca somut sonucu depolamak için yeni bir değişken kullanarak bunu ifade edebilirsiniz. Sorguyu depolayan değişkeni bir sonucu depolayan sorgudan ayrı tuttuğundan, bu teknik daha okunabilir.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

Önceki örnekte, sorgu , `Count`tarafından döndürülen `Count` öğelerin sayısını belirlemek için sonuçlar üzerinde yinelemek gerekir, çünkü çağrı yürütülür `highScoresQuery`.

## <a name="what-is-a-query-expression"></a>Sorgu ifadesi nedir?

*Sorgu ifadesi* sorgu sözdiziminde ifade edilen bir sorgudur. Sorgu ifadesi birinci sınıf bir dil yapısıdır. Diğer ifadeler gibi ve C# ifadesinin geçerli olduğu herhangi bir bağlamda kullanılabilir. Sorgu ifadesi, SQL veya XQuery'ye benzer bir bildirim sözdiziminde yazılmış bir yan tümce kümesinden oluşur. Sırayla her yan tümce bir veya daha fazla C# ifadeleri içerir ve bu ifadeler kendilerini bir sorgu ifadesi olabilir veya bir sorgu ifadesi içerir.

Sorgu ifadesi [bir from](../language-reference/keywords/from-clause.md) yan tümcesi ile başlamalı ve bir [seçme](../language-reference/keywords/select-clause.md) veya [grup](../language-reference/keywords/group-clause.md) yan tümcesi ile bitmelidir. `from` İlk yan tümce `select` ile `group` son veya yan tümce arasında, bu isteğe bağlı yan tümcelerden bir veya daha fazlasını içerebilir: [burada,](../language-reference/keywords/where-clause.md) [orderby,](../language-reference/keywords/orderby-clause.md) [join,](../language-reference/keywords/join-clause.md) [let](../language-reference/keywords/let-clause.md) ve hatta yan [tümcelerden](../language-reference/keywords/from-clause.md) ek. Bir `join` veya `group` yan tümcenin sonucunu, aynı sorgu ifadesinde ek sorgu yan tümceleri için kaynak olarak kullanmak için de anahtar kelimeyi kullanabilirsiniz. [into](../language-reference/keywords/into.md)

### <a name="query-variable"></a>Sorgu değişkeni

LINQ'da, sorgu değişkeni, *sorgunun sonuçları* yerine *sorgu* depolayan herhangi bir değişkendir. Daha spesifik olarak, bir sorgu değişkeni her zaman bir `foreach` deyim veya `IEnumerator.MoveNext` yöntemine doğrudan çağrı üzerinde yinelemeli öğelerin bir dizi üretecek numaralandırılabilir türüdür.

Aşağıdaki kod örneği, bir veri kaynağı, bir filtreleme yan tümcesi, bir sipariş tümcesi ve kaynak öğelerinin dönüşümü olmayan basit bir sorgu ifadesini gösterir. Yan `select` tümce sorguyu sona erdirer.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

Önceki örnekte, `scoreQuery` bazen sadece bir sorgu olarak adlandırılan bir *sorgu değişkeni* dir. *query* Sorgu değişkeni, döngüde üretilen hiçbir gerçek `foreach` sonuç verisini depolar. Ve `foreach` deyim yürütüldüğünde, sorgu sonuçları sorgu değişkeni `scoreQuery`üzerinden döndürülmez. Bunun yerine, yineleme değişkeni `testScore`üzerinden döndürülürler. `scoreQuery` Değişken ikinci `foreach` bir döngü içinde yinelenebilir. Ne o ne de veri kaynağı değiştirilmediğinden aynı sonuçları verir.

Sorgu değişkeni sorgu sözdizimi veya yöntem sözdizimi veya ikisinin bir arada ifade edilen bir sorgu saklayabilir. Aşağıdaki örneklerde, `queryMajorCities` hem `queryMajorCities2` ve sorgu değişkenleri vardır:

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

Diğer taraftan, aşağıdaki iki örnek, her biri bir sorguyla baş harfe getiriliyor olsa bile sorgu değişkeni olmayan değişkenleri gösterir. Sonuçları depoladıkları için sorgu değişkenleri değildir:

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Sorguları ifade etmenin farklı yolları hakkında daha fazla bilgi için [LINQ'da Sorgu sözdizimi ve yöntem sözdizimi'ne](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)bakın.

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Sorgu değişkenlerinin açık ve örtülü olarak yazması

Bu belge genellikle sorgu değişkeni ve [select yan tümcesi](../language-reference/keywords/select-clause.md)arasındaki tür ilişkisini göstermek için sorgu değişkeninin açık türünü sağlar. Ancak, derleyiciye bir sorgu değişkeninin (veya başka bir yerel değişkenin) türünü derleme zamanında çıkarmasını öğretmek için [var](../language-reference/keywords/var.md) anahtar sözcüklerini de kullanabilirsiniz. Örneğin, bu konuda daha önce gösterilen sorgu örneği de örtülü yazı kullanılarak ifade edilebilir:

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Daha fazla bilgi için, [LINQ sorgu işlemlerinde](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md) [örtük olarak yazılan yerel değişkenler](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve Tür ilişkileri'ne bakın.

### <a name="starting-a-query-expression"></a>Sorgu ifadesini başlatma

Sorgu ifadesi bir `from` yan tümceyle başlamalıdır. Bir veri kaynağını bir aralık değişkeni ile birlikte belirtir. Aralık değişkeni, kaynak sırası geçerken kaynak dizideki her ardışık öğeyi temsil eder. Aralık değişkeni, veri kaynağındaki öğelerin türüne göre güçlü bir şekilde yazılır. Aşağıdaki örnekte, `countries` `Country` nesnelerin bir dizi olduğundan, aralık değişkeni de `Country`. Aralık değişkeni güçlü bir şekilde yazıldığı için, türün kullanılabilir üyelerine erişmek için nokta işleci'ni kullanabilirsiniz.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

Aralık değişkeni, sorgu yarım sütunlu veya *devam* yan tümcesi ile çıkana kadar kapsamdadır.

Sorgu ifadesi birden `from` çok yan tümce içerebilir. Kaynak `from` dizideki her öğe bir koleksiyon olduğunda veya bir koleksiyon içeriyorsa ek yan tümceler kullanın. Örneğin, `Country` her biri `City` . `Cities` Her `City` `Country`bir innesneleri sorgulamak `from` için, burada gösterildiği gibi iki yan tümce kullanın:

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Daha fazla bilgi [için, yan tümceye](../language-reference/keywords/from-clause.md)bakın.

### <a name="ending-a-query-expression"></a>Sorgu ifadesini sonlandırma

Sorgu ifadesi bir `group` yan tümce `select` veya yan tümceyle sona ermelidir.

#### <a name="group-clause"></a>group tümcesi

Belirttiğiniz `group` bir anahtar tarafından düzenlenen gruplar dizisi oluşturmak için yan tümceyi kullanın. Anahtar herhangi bir veri türü olabilir. Örneğin, aşağıdaki sorgu, bir veya daha fazla `Country` nesne içeren ve anahtarı `char` bir değer olan bir grup dizisi oluşturur.

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Gruplandırma hakkında daha fazla bilgi için [grup yan tümcesi'ne](../language-reference/keywords/group-clause.md)bakın.

#### <a name="select-clause"></a>select tümcesi

Diğer `select` tüm dizi türlerini oluşturmak için yan tümceyi kullanın. Basit `select` bir yan tümce yalnızca veri kaynağında bulunan nesnelerle aynı türde bir nesne dizisi üretir. Bu örnekte, veri `Country` kaynağı nesneleri içerir. Yan `orderby` tümce yalnızca öğeleri yeni bir `select` düzene sıralar ve `Country` yan tümce yeniden sıralanan nesnelerin bir dizi üretir.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

Yan `select` tümce, kaynak verileri yeni türler dizilerine dönüştürmek için kullanılabilir. Bu dönüşüm de bir *projeksiyon*olarak adlandırılır. Aşağıdaki örnekte, `select` yan tümce, özgün öğedeki alanların yalnızca bir alt kümesini içeren bir dizi anonim tür *de yeğler.* Yeni nesnelerin bir nesne başharfi kullanılarak baş harflere başharfe çarptırılmış olduğunu unutmayın.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

Bir `select` yan tümcenin kaynak verileri dönüştürmek için kullanılabilme yolları hakkında daha fazla bilgi için [select yan tümcesine](../language-reference/keywords/select-clause.md)bakın.

#### <a name="continuations-with-into"></a>"Into" ile devam eder

Bir `select` veya `group` `into` yan tümcedeki anahtar sözcüğü, sorgu yu saklayan geçici bir tanımlayıcı oluşturmak için kullanabilirsiniz. Gruplandırma veya seçme işleminden sonra sorguda ek sorgu işlemleri gerçekleştirmeniz gerektiğinde bunu yapın. Aşağıdaki örnekte `countries` 10 milyon aralığındanüfusa göre gruplandırılır. Bu gruplar oluşturulduktan sonra, ek yan tümceler bazı grupları filtreler ve ardından grupları artan sırada sırayla sıralar. Bu ek işlemleri gerçekleştirmek için, `countryGroup` temsil edilen devamı gereklidir.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Daha fazla bilgi için [bkz.](../language-reference/keywords/into.md)

### <a name="filtering-ordering-and-joining"></a>Filtreleme, sıralama ve birleştirme

`from` Başlangıç yan tümcesi `select` `group` ile bitiş veya yan`where` `join`tümce arasında, diğer tüm yan tümceler (, `orderby`, , `from`, `let`) isteğe bağlıdır. İsteğe bağlı yan tümcelerden herhangi biri sorgu gövdesinde sıfır kez veya birden çok kez kullanılabilir.

#### <a name="where-clause"></a>where tümcesi

Bir `where` veya daha fazla yüklem ifadesini temel alan kaynak verilerdeki öğeleri filtrelemek için yan tümceyi kullanın. Aşağıdaki `where` örnekteki tümcenin iki koşullu bir yüklemi vardır.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Daha fazla bilgi için [bkz.](../language-reference/keywords/where-clause.md)

#### <a name="orderby-clause"></a>orderby tümcesi

Sonuçları `orderby` artan veya azalan sırada sıralamak için yan tümceyi kullanın. İkincil sıralama siparişleri de belirtebilirsiniz. Aşağıdaki örneközelliği kullanarak `country` `Area` nesneler üzerinde birincil sıralama gerçekleştirir. Daha sonra `Population` özelliği kullanarak ikincil bir sıralama gerçekleştirir.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

Anahtar `ascending` kelime isteğe bağlıdır; sipariş belirtilmemişse varsayılan sıralama sırasıdır. Daha fazla bilgi için [orderby yan tümcesi'ne](../language-reference/keywords/orderby-clause.md)bakın.

#### <a name="join-clause"></a>join tümcesi

Her `join` öğede belirtilen anahtarlar arasında eşitlik karşılaştırması dayalı bir veri kaynağıöğeleri ile ilişkilendirmek ve / veya bir veri kaynağı öğeleri birleştirmek için yan tümceyi kullanın. LINQ'da birleştirme işlemleri, öğeleri farklı türde olan nesne dizileri üzerinde gerçekleştirilir. İki diziyi birleştirdikten sonra, çıktı `select` `group` dizisinde hangi öğeyi depolayacağınızı belirtmek için bir veya deyim kullanmanız gerekir. Ayrıca, ilişkili öğelerin her kümesindeki özellikleri çıktı dizisi için yeni bir türde birleştirmek için anonim bir tür de kullanabilirsiniz. Aşağıdaki örnek, `prod` `Category` özelliği `categories` dize dizisindeki kategorilerden biriyle eşleşen nesneleri ilişkilendirir. Herhangi `Category` bir dize `categories` yle eşleşmeyen ürünler filtrelenir. İfade, `select` özellikleri her ikisinden de `cat` alınan `prod`yeni bir tür ve .

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Ayrıca, `join` işlemin sonuçlarını anahtar [kelimeye kullanarak](../language-reference/keywords/into.md) geçici bir değişkene depolayarak bir grup birleştirme gerçekleştirebilirsiniz. Daha fazla bilgi için [ara yan tümcesi'ne](../language-reference/keywords/join-clause.md)bakın.

#### <a name="let-clause"></a>let tümcesi

Yöntem `let` çağrısı gibi bir ifadenin sonucunu yeni bir aralık değişkeninde depolamak için yan tümceyi kullanın. Aşağıdaki örnekte, aralık `firstName` değişkeni tarafından `Split`döndürülen dize dizisinin ilk öğesini depolar.

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Daha fazla bilgi için [bkz.](../language-reference/keywords/let-clause.md)

### <a name="subqueries-in-a-query-expression"></a>Sorgu ifadesindeki alt sorgular

Sorgu yan tümcesi, bazen *alt sorgu*olarak adlandırılan bir sorgu ifadesi içerebilir. Her alt sorgu, `from` ilk `from` yan tümcedeki aynı veri kaynağını mutlaka işaret etmeyen kendi yan tümcesiyle başlar. Örneğin, aşağıdaki sorgu, bir gruplandırma işleminin sonuçlarını almak için select deyiminde kullanılan bir sorgu ifadesini gösterir.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Daha fazla bilgi için bkz. [Gruplandırma işleminde bir alt sorgu yap.](perform-a-subquery-on-a-grouping-operation.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../programming-guide/index.md)
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [Anahtar kelimeleri sorgula (LINQ)](../language-reference/keywords/query-keywords.md)
- [Standart sorgu operatörlerine genel bakış](../programming-guide/concepts/linq/standard-query-operators-overview.md)
