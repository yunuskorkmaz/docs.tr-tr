---
title: Lambda İfadeleri
description: Bağımsız değişken olarak geçirilen yürütülebilir kod blokları lambda ifadeleri kullanma yalın.
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: e37f0e72ee02915d16509fb2ff48bd114e8ad466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217980"
---
# <a name="lambda-expressions"></a>Lambda ifadeleri #

A *lambda ifadesi* bir nesne olarak kabul edilir kodu (bir deyim veya bir ifade bloğu) bloğudur. Yöntemlere bağımsız değişken olarak geçirilebilir ve ayrıca yöntem çağrıları tarafından döndürülebilir. Lambda ifadeleri için yaygın olarak kullanılır:

- Kod geçirme olduğu gibi zaman uyumsuz yöntemleri için yürütülecek <xref:System.Threading.Tasks.Task.Run(System.Action)>.

- Yazma [LINQ Sorgu ifadeleri](linq/index.md).

- Oluşturma [ifade ağaçları](expression-trees-building.md).

Lambda ifadeleri temsilci olarak ya da bir temsilciye derlenen bir ifade ağacına olarak temsil edilebilir kodu var. Lambda ifadesi belirli temsilci türü kendi parametrelerine göre değişir ve değeri döndürür. Bir değer döndürmez lambda ifadeleri karşılık gelen belirli bir `Action` , parametreleri, sayısına bağlı olarak temsilci. Bir değer döndürmesi lambda ifadeleri karşılık gelen belirli bir `Func` , parametreleri, sayısına bağlı olarak temsilci. Örneğin, iki parametreye sahip ancak hiçbir değer döndürmeyen bir lambda ifadesi için karşılık gelen bir <xref:System.Action%602> temsilci. Bir parametre içeriyor ve bir değer döndüren bir lambda ifadesi karşılık gelen <xref:System.Func%602> temsilci.

Lambda ifadesi kullanan `=>`, [lambda bildirimi işleci](language-reference/operators/lambda-operator.md), yürütülebilir koddan lambda ait parametre listesi ayırmak için. Lambda ifadesi oluşturmak için giriş parametreleri (varsa) lambda işlecinin sol tarafında belirtin ve diğer tarafta ifade veya deyimin blok yerleştirin. Örneğin, tek satırlı lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış. Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

Veya doğrudan bir yöntem bağımsız değişken olarak geçirebilirsiniz:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>İfade lambdas ##

 Bir lambda ifadesi ile sağ tarafında bir ifade = > işleci adlı bir *lambda ifadesi*. İfade lambdas yaygın yapımı içinde kullanılan [ifade ağaçları](expression-trees.md). Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:

```csharp
(input parameters) => expression
```

Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir. Boş ayraçlarla sıfır giriş parametrelerini belirtin:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

Normalde, derleyici tür çıkarımı parametre türleri belirlemede kullanır. Ancak bazen zor veya giriş türlerinin gerçekleştirip derleyici mümkün olur. Bu durumda, aşağıdaki örnekte olduğu gibi açıkça olarak türü belirtebilirsiniz:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

Önceki örnekte bir lambda ifadesi gövdesinin yöntem çağrısından oluşabileceğini unutmayın. .NET Framework dışında değerlendirilen ifade ağaçları oluşturuyorsanız, ancak gibi SQL Server veya Entity Framework (EF), yöntem bağlamı dışında hiçbir anlamı sağlanmış olabileceği yöntem çağrıları lambda ifadeleri kullanmamalıdır .NET uygulaması. Yöntem çağrıları bu durumda kullanmayı seçerseniz, onları çağrıları başarıyla çözülebilir yöntemi baştan sona emin olmak için test emin olun.

## <a name="statement-lambdas"></a>Deyimi lambdas ##

Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:

```csharp
(input parameters) => { statement; }
```

Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.

## <a name="async-lambdas"></a>Zaman uyumsuz lambdas ##

Lambda ifadeleri ve kullanarak zaman uyumsuz işleme dahil deyimleri kolayca oluşturabilirsiniz [zaman uyumsuz](language-reference/keywords/async.md) ve [await](language-reference/keywords/await.md) anahtar sözcükler. Örneğin, örnek çağıran bir `ShowSquares` yöntemi zaman uyumsuz olarak yürütür.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz [zaman uyumsuz programlama ile async ve await](programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Lambda ifadeleri ve diziler ##

C# 7. 0'dan başlayarak, C# dili diziler için yerleşik destek sağlar. Lambda ifadesi bağımsız değişkeni olarak bir tanımlama grubu sağlayabilir ve lambda ifadesi bir tanımlama grubu geri dönebilirsiniz. Bazı durumlarda, C# derleyici tür çıkarımı tanımlama grubu bileşenleri türlerini belirlemek için kullanır. 

Parantez içinde virgülle ayrılmış bir liste bileşenlerini kapsayan tarafından bir tanımlama grubu tanımlayın. Aşağıdaki örnek, her değerin iki katına çıkar ve multiplications sonucunu içeren bir tanımlama grubu 5 bileşenlerle döndüren bir lambda ifadesi için sayılardan oluşan bir dizi geçirmek için 5 bileşenleri ile tanımlama grubu kullanır.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

Normalde, bir tanımlama grubu alanlarının adlı `Item1`, `Item2`vb. Ancak, aşağıdaki örnekte olduğu gibi bir tanımlama grubu adlandırılmış bileşenlerle tanımlayabilirsiniz.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

C# diziler desteği hakkında daha fazla bilgi için bkz: [C# kayıt türlerinin](tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Standart sorgu işleçleri ile Lambdas ##

Diğer uygulamalardan arasında nesnelere LINQ türü olan bir giriş parametresi vardır, <xref:System.Func%601> genel temsilciler ailesi. Bu temsilci tür parametreleri sayısı ve türü giriş parametreleri ve temsilci dönüş türünü tanımlamak için kullanın. `Func` Temsilciler kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadeleri kapsüllemek için çok kullanışlıdır. Örneğin, göz önünde bulundurun <xref:System.Func%601> temsilci, olan sözdizimi aşağıdaki gibidir:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

Temsilci, aşağıdaki gibi bir kod kullanılarak oluşturulabilir.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

Burada `int` bir girdi parametresi ve `bool` dönüş değeri. Dönüş değeri her zaman son tür parametresinde belirtilir. Aşağıdaki `Func` temsilci çağrıldığında, true veya false giriş parametresi 5'e eşit olup olmadığını belirtmek için döndürür:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

Bağımsız değişken türü olduğunda, aynı zamanda bir lambda ifadesi sağlayabilir bir <xref:System.Linq.Expressions.Expression%601>, örneğin tanımlanan standart sorgu işleçleri içinde <xref:System.Linq.Queryable> türü. Belirttiğinizde bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişkeni, lambda bir ifade ağacına derlenmiştir. Aşağıdaki örnek kullanır [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standart sorgu işleci.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz. Bu belirli lambda ifadesi bu tamsayılar sayar (`n`), iki tarafından bölünmüş olduğunda 1 kalanı vardır.

Aşağıdaki örnek, tüm öğeleri içeren bir sıra üretir `numbers` bu koşulu karşılamıyor sıradaki ilk sayı olduğundan, 9 koyun dizi.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

Aşağıdaki örnek, parantez içinde kapsayan tarafından birden çok giriş parametreleri belirtir. Metodu tüm öğeleri sıralı konumuna dizideki'den küçük değeri bir sayı bulduğu kadar numaraları dizisi döndürür.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>Lambda ifadeleri tür çıkarımı ##

Lambda'lar yazarken, genellikle C# dil belirtimi içinde açıklandığı gibi derleyici lambda gövdesi, parametre türleri ve diğer etkenlere göre türü çıkarımını çünkü giriş parametreleri için bir tür belirtin gerekmez. Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür. Sizin için sorgu oluşturuyorsanız bir `IEnumerable<Customer>`, giriş değişkeni olarak algılanır sonra bir `Customer` erişiminiz yöntemleri ve özellikleri anlamına gelir nesnesi:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

Tür çıkarımı Lambda'lar için genel kurallar şunlardır:

- Lambda temsilci türüyle aynı sayıda parametre içermelidir.

- Lambda her giriş bağımsız değişkeni, karşılık gelen bir temsilci parametre örtük olarak dönüştürülebilir olmalıdır.

- Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.

Ortak tür sisteminin "lambda ifadesi" için iç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü olmadığını unutmayın. Ancak bazen bir lambda ifadesinin "türünden" resmi olmayan bir şekilde bahsetmek daha kolaydır. Bu durumlarda türü temsilci türüne başvuruyor veya <xref:System.Linq.Expressions.Expression> yazın lambda ifadesi dönüştürülen.

## <a name="variable-scope-in-lambda-expressions"></a>Lambda İfadelerinde Değişken Kapsamı ##

Lambda'lar başvurabilir *dış değişkenleri* (bkz [anonim yöntemler](programming-guide/statements-expressions-operators/anonymous-methods.md)) lambda işlevi tanımlar yöntemi kapsamında olan ya da lambda ifadesi içeren kapsamında yazın. Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır. Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir. Aşağıdaki örnek, bu kuralları gösterir.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:

- Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.

- Bir lambda ifadesi içinde tanıtılan değişkenler, dış yöntemde görünmez.

- Lambda ifadesi doğrudan yakalayamazsınız bir `in`, `ref`, veya `out` kapsayan bir yöntem parametresi.

- Lambda ifadesindeki bir dönüş ifadesi, kapsayan yöntemin döndürülmesine neden olmaz.

- Lambda ifadesi içeremez bir `goto` deyimi, `break` deyimi veya `continue` atlama deyiminin hedef dışında blok ise, lambda işlevinde deyimi. Ayrıca, hedef, blok içinde ise lambda işlev bloğu dışında bir deyim olması bir hatadır.

## <a name="see-also"></a>Ayrıca bkz. ##

[LINQ (dil ile tümleşik sorgu)](../standard/using-linq.md)   
[Anonim yöntemler](programming-guide/statements-expressions-operators/anonymous-methods.md)   
[İfade ağaçları](expression-trees.md)
