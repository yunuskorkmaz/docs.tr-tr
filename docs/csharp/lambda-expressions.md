---
title: Lambda İfadeleri
description: Bağımsız değişken olarak geçirilebilir yürütülebilir kod blokları lambda ifadeleri kullanma edinin.
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 642422a4cc077ffebb5ee6db9d7ffb937fc1e173
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212358"
---
# <a name="lambda-expressions"></a>Lambda ifadeleri

A *lambda ifadesi* (bir ifadeyi veya deyim bloğunu) bir nesne olarak işlem kod bloğudur. Yöntemi için bağımsız değişken olarak geçirilebilir ve yöntem çağrıları tarafından da döndürülebilir. Lambda ifadeleri için yaygın olarak kullanılır:

- Kod geçirmeden olduğu gibi zaman uyumsuz yöntemler için yürütülecek <xref:System.Threading.Tasks.Task.Run(System.Action)>.

- Yazma [LINQ Sorgu ifadeleri](linq/index.md).

- Oluşturma [ifade ağaçları](expression-trees-building.md).

Lambda ifadeleri temsilci olarak veya bir ifade ağacına derleyen bir temsilciye olarak gösterilen kodu var. Bir lambda ifadesinin özel temsilci türü kendi parametrelerine göre değişir ve dönüş değeri. Bir değer döndürmeyen bir lambda ifadeleri, belirli bir karşılık gelen `Action` , parametreleri, sayısına bağlı olarak temsilci. Bir değer döndüren bir lambda ifadeleri, belirli bir karşılık gelen `Func` , parametreleri, sayısına bağlı olarak temsilci. Örneğin, iki parametreye sahip ancak hiçbir değer döndürmeyen bir lambda ifadesi için karşılık gelen bir <xref:System.Action%602> temsilci. Bir parametreye sahiptir ve bir değer döndüren bir lambda ifadesi karşılık gelen <xref:System.Func%602> temsilci.

Bir lambda ifadesi kullanır `=>`, [lambda bildirimi işleci](language-reference/operators/lambda-operator.md), lambdanın parametre listesi, yürütülebilir kodundan ayırın. Bir lambda ifadesi oluşturmak için giriş parametreleri (varsa) lambda işlecinin sol tarafında belirtin ve ifadeyi veya deyim bloğunu diğer tarafa yerleştirin. Örneğin, tek satırlı lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış. Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

Veya doğrudan bir yöntemi bağımsız değişken geçirin:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>Expression lambdas

 Bir lambda ifadesi işlecin sağ tarafındaki bir ifadeyle = > işleci çağrıldığında bir *lambda ifadesi*. İfade lambdaları oluşumunu oluşturulurken sıkça kullanılır [ifade ağaçları](expression-trees.md). Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:

```csharp
(input parameters) => expression
```

Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir. Boş ayraçlarla sıfır giriş parametrelerini belirtin:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

Normalde, derleyici tür çıkarımı, parametre türleri belirlemede kullanır. Ancak, bazen zor veya imkansız derleyicinin giriş türlerini çıkarması öyledir. Bu durumda türleri aşağıdaki örnekte olduğu gibi açıkça belirtebilirsiniz:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

Önceki örnekte bir lambda ifadesi gövdesinin yöntem çağrısından oluşabileceğini unutmayın. .NET Framework dışında değerlendirilen ifade ağaçları oluşturuyorsanız, ancak gibi SQL Server veya Entity Framework (EF), yöntem bağlamı dışında anlamlı olabileceği yöntem çağrıları lambda ifadelerinde kullanmadığınızdan .NET uygulaması. Bu durumda yöntem çağrılarını kullanmayı seçerseniz, bunları çağrıları başarıyla çözümlenip yöntemi kapsamlı emin olmak için test etmeyi unutmayın.

## <a name="statement-lambdas"></a>Deyim lambdaları

Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:

```csharp
(input parameters) => { statement; }
```

Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.

## <a name="async-lambdas"></a>Async lambdas

İçeren kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz [zaman uyumsuz](language-reference/keywords/async.md) ve [await](language-reference/keywords/await.md) anahtar sözcükleri. Örneğin, örnek çağıran bir `ShowSquares` yöntemi zaman uyumsuz olarak yürütür.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama ile zaman uyumsuz ve await](programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Lambda ifadeleri ve diziler

C# 7.0 ile başlayarak, C# dili diziler için yerleşik destek sağlar. Bir lambda ifadesi bağımsız değişkeni olarak bir tanımlama grubu sağlayabilir ve, lambda ifadesi, ayrıca bir demet döndürebilir. Bazı durumlarda, tanımlama grubu bileşenleri türlerini belirlemek için tür çıkarımı C# derleyicisini kullanır.

Bir dizi, parantez içine alarak bileşenlerinden virgülle ayrılmış bir listesini tanımlayın. Aşağıdaki örnek, her değerin iki katına çıkar ve multiplications sonucunu içeren bir tanımlama grubu 5 bileşenlerle döndüren bir lambda ifadesi için bir sayı dizisi üzerinde geçirilecek 5 bileşenleri ile tanımlama grubu kullanır.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

Normalde, bir kayıt düzeni alanlarını olarak da adlandırılır `Item1`, `Item2`vb. Ancak, aşağıdaki örnekte olduğu gibi bir dizi adlandırılmış bileşenlerle tanımlayabilirsiniz.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

C# ' de tanımlama gruplarına yönelik destek hakkında daha fazla bilgi için bkz. [C# demet türleri](tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Standart sorgu işleçleri ile lambda ifadeleri

LINQ to Objects'in, diğer uygulamalar arasında olması, türü giriş parametresi, <xref:System.Func%601> Genel temsilci ailesinden olan. Bu Temsilciler, tür parametreleri sayısı ve girdi parametrelerinin türünü ve temsilcinin dönüş türünü tanımlamak için kullanın. `Func` Temsilciler, kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadelerin Kapsüllenmesi için son çok yararlı olur. Örneğin, düşünün <xref:System.Func%601> temsilci, söz dizimi şu şekildedir:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

Temsilci, aşağıdaki gibi kod kullanılarak oluşturulabilir.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

Burada `int` bir giriş parametresi ve `bool` dönüş değeridir. Dönüş değeri her zaman son tür parametresinde belirtilir. Aşağıdaki `Func` temsilcisi çağrıldığında, true veya false giriş parametresinin 5'e eşit olup olmadığını belirtmek için döndürür:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

Ayrıca bağımsız değişken türü bir lambda ifadesi sağlayabilirsiniz bir <xref:System.Linq.Expressions.Expression%601>, örneğin tanımlanan standart sorgu işleçleri içinde <xref:System.Linq.Queryable> türü. Belirttiğinizde bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişkeni, lambda ifade ağacında derlenmiştir. Aşağıdaki örnekte [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standart sorgu işleci.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz. Bu belirli lambda ifadesi tamsayıları sayar (`n`), ikiye bölündüğünde 1 kalan sahip.

Aşağıdaki örnekte tüm öğelerini içeren bir dizi üretir `numbers` , dizisinde koşulu sağlamayan ilk sayı olduğundan 9 önünde bir dizi.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

Aşağıdaki örnek, birden fazla giriş parametrelerini paranteze tarafından belirtir. Yöntem dizi içindeki sıralı konumu'den küçük sayılar dizi değeri bir sayı karşılaşana kadar tüm öğeleri döndürür.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>Lambda ifadeleri içinde tür çıkarımı

Lambda ifadeleri yazarken, genellikle C# dil Belirtimi'nde açıklanan derleyici lambda gövdesine, parametre türleri ve diğer etkenlere göre türü belirleyebilir giriş parametreleri için bir tür belirtmeniz gerekmez. Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür. Sorguluyorsanız bir `IEnumerable<Customer>`, giriş değişkeni olması sorguluyorsanız bir `Customer` nesne erişim yöntemleri ve özellikleri iznine sahip olduğunuz anlamına gelir:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

Lambdalar için tür çıkarımı için genel kurallar şunlardır:

- Lambda temsilci türüyle aynı sayıda parametre içermelidir.

- Lambdadaki her bir giriş bağımsız değişkeni, karşılık gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.

- Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.

Ortak tür sisteminin "lambda ifadesi" için iç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü olmadığını unutmayın. Ancak bazen bir lambda ifadesinin "türünden" resmi olmayan bir şekilde bahsetmek daha kolaydır. Bu gibi durumlarda, tür temsilci türüne başvuruyor. veya <xref:System.Linq.Expressions.Expression> , lambda ifadesinin dönüştürüldüğü yazın.

## <a name="variable-scope-in-lambda-expressions"></a>Lambda İfadelerinde Değişken Kapsamı

Lambdalar başvurabilir *dış değişkenlere* (bkz [anonim yöntemler](programming-guide/statements-expressions-operators/anonymous-methods.md)), lambda işlevini tanımlayan yöntemin kapsamındaki ya da lambda ifadesini içeren türün kapsamındaki. Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır. Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir. Aşağıdaki örnek bu kuralları gösterir.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:

- Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.

- Bir lambda ifadesi içinde tanıtılan değişkenler, dış yöntemde görünmez.

- Bir lambda ifadesini doğrudan yakalayamaz bir `in`, `ref`, veya `out` parametresi kapsayan bir yöntemden alınan.

- Lambda ifadesindeki bir dönüş ifadesi, kapsayan yöntemin döndürülmesine neden olmaz.

- Bir lambda ifadesi içeremez bir `goto` deyimi `break` deyimi veya `continue` varsa atlama bildiriminin hedefi blok dışındaysa lambda işlevi içinde deyimi. Ayrıca, hedef, blok içinde ise lambda işlev bloğu dışında bir deyim olması bir hatadır.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ (dil ile tümleşik sorgu)](../standard/using-linq.md)
- [Anonim yöntemler](programming-guide/statements-expressions-operators/anonymous-methods.md)
- [İfade ağaçları](expression-trees.md)
