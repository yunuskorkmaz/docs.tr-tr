---
title: Lambda ifadeler - C# Programlama Kılavuzu
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 44d6ed9ac6e1c3c4d08bbd69ca808d2e740f0c4e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738326"
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda ifadeleri (C# Programlama Kılavuzu)

*Lambda ifadesi* aşağıdaki iki formdan herhangi birinin ifadesidir:

- [İfade lambda](#expression-lambdas) kendi gövdesi olarak bir ifade vardır:

  ```csharp
  (input-parameters) => expression
  ```

- [Beyanı lambda](#statement-lambdas) gövdesi olarak bir ifade bloğu vardır:

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

[Lambda'nın `=>` ](../../language-reference/operators/lambda-operator.md) parametre listesini gövdesinden ayırmak için lambda bildirim operatörünü kullanın. Lambda ifadesi oluşturmak için lambda işlecinin sol tarafında giriş parametreleri (varsa) ve diğer tarafta bir ifade veya deyim bloğu belirtirsiniz.

Herhangi bir lambda ifadesi [bir temsilci](../../language-reference/builtin-types/reference-types.md#the-delegate-type) türüne dönüştürülebilir. Lambda ifadesinin dönüştürülebileceği temsilci türü, parametrelerinin ve geri dönüş değerinin türlerine göre tanımlanır. Lambda ifadesi bir değer döndürmüyorsa, `Action` temsilci türlerinden birine dönüştürülebilir; aksi takdirde, `Func` temsilci türlerinden birine dönüştürülebilir. Örneğin, iki parametresi olan ve hiçbir değer döndürmeyen bir <xref:System.Action%602> lambda ifadesi temsilciye dönüştürülebilir. Bir parametresi olan ve bir değer döndüren bir <xref:System.Func%602> lambda ifadesi temsilciye dönüştürülebilir. Aşağıdaki örnekte, adlandırılmış `x => x * x` `x` bir parametreyi belirten ve `x` kare değerini döndüren lambda ifadesi, temsilci türündeki bir değişkene atanır:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

İfade lambdas da [ifade ağacı](../concepts/expression-trees/index.md) türlerine dönüştürülebilir, aşağıdaki örnekte görüldüğü gibi:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Lambda ifadelerini, örneğin arka planda yürütülmesi gereken kodu geçirmek için <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> yönteme bir argüman olarak, temsilci türleri veya ifade ağaçları örnekleri gerektiren herhangi bir kodda kullanabilirsiniz. Aşağıdaki örnekte görüldüğü [gibi, C#'a LINQ](../../linq/index.md)yazarken lambda ifadelerini de kullanabilirsiniz:

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Sınıftaki <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> yöntemi çağırmak için yöntem tabanlı sözdizimini kullandığınızda, örneğin LINQ'dan Nesnelere ve LINQ'dan XML'e parametre bir temsilci türüdür. <xref:System.Func%602?displayProperty=nameWithType> <xref:System.Linq.Enumerable?displayProperty=nameWithType> Sınıftaki <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> yöntemi, örneğin LINQ'dan SQL'e çağırdığınızda, parametre türü bir ifade ağacı türüdür. [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) <xref:System.Linq.Queryable?displayProperty=nameWithType> Her iki durumda da parametre değerini belirtmek için aynı lambda ifadesini kullanabilirsiniz. Aslında lambdas oluşturulan nesnelerin türü farklı olmasına rağmen bu iki `Select` çağrı benzer görünmesini sağlar.
  
## <a name="expression-lambdas"></a>İfade lambdas

Operatörün `=>` sağ tarafında bir ifade ile lambda ifade bir *ifade lambda*denir. İfade lambdas [ifade ağaçlarının](../concepts/expression-trees/index.md)yapımında yaygın olarak kullanılmaktadır. Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:

```csharp
(input-parameters) => expression
```

Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.

Boş ayraçlarla sıfır giriş parametrelerini belirtin:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Bazen derleyicinin giriş türlerini çıkarması imkansızdır. Türleri aşağıdaki örnekte açıkça gösterildiği gibi belirtebilirsiniz:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Giriş parametresi türlerinin tümü açık veya tamamen örtülü olmalıdır; aksi takdirde, bir [CS0748](../../misc/cs0748.md) derleyici hatası oluşur.

Bir ifade lambda gövdesi bir yöntem çağrı oluşabilir. Ancak, SQL Server'da olduğu gibi .NET ortak dil çalışma zamanı bağlamı dışında değerlendirilen ifade ağaçları oluşturuyorsanız, lambda ifadelerinde yöntem çağrıları kullanmamalısınız. Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.

## <a name="statement-lambdas"></a>Açıklama lambdas

Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

İfade lambdas ifade ağaçları oluşturmak için kullanılamaz.
  
## <a name="async-lambdas"></a>Async lambdas

Kolayca [async](../../language-reference/keywords/async.md) kullanarak asynchronous işleme dahil lambda ifadeler ve ifadeler oluşturabilirsiniz ve anahtar kelimeleri [bekliyor.](../../language-reference/operators/await.md) Örneğin, aşağıdaki Windows Forms örneği çağıran ve bir async yöntemi ni `ExampleMethodAsync`bekleyen bir olay işleyicisi içerir.

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz. Bu işleyiciyi eklemek `async` için, aşağıdaki örnekte görüldüğü gibi lambda parametre listesinden önce bir değiştirici ekleyin:

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

Async yöntemlerinin nasıl oluşturulup kullanılacağı hakkında daha fazla bilgi için [async ile Asynchronous Programming'e](../concepts/async/index.md)bakın ve bekleyin.

## <a name="lambda-expressions-and-tuples"></a>Lambda ifadeler ve tuples

C# 7.0 ile başlayarak, C# dili [tuples](../../tuples.md)için yerleşik destek sağlar. Bir lambda ifade için bir argüman olarak bir tuple sağlayabilir ve lambda ifade de bir tuple döndürebilir. Bazı durumlarda, C# derleyicisi tuple bileşenlerinin türlerini belirlemek için tür çıkarımını kullanır.

Bileşenlerinin virgülle sınırlı bir listesini parantez içinde ekleyerek bir tuple tanımlarsınız. Aşağıdaki örnekte, bir dizi sayıyı lambda ifadesine geçirmek için üç bileşenden oluşan tuple kullanılır, bu da her değeri ikikatına çıkar ve çarpmaların sonucunu içeren üç bileşenle bir tuple döndürür.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Normalde, bir tuple alanları , , `Item1` `Item2`vb adlandırılır. Ancak, aşağıdaki örnekte olduğu gibi, adlandırılmış bileşenlerle bir tuple tanımlayabilirsiniz.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

C# tuples hakkında daha fazla bilgi için [C# tuple türlerine](../../tuples.md)bakın.

## <a name="lambdas-with-the-standard-query-operators"></a>Standart sorgu operatörleri ile Lambdas

LinQ to Objects, diğer uygulamaların yanı sıra, türü genel <xref:System.Func%601> temsilciler ailesinden biri olan bir giriş parametresi vardır. Bu temsilciler, giriş parametrelerinin sayısını ve türünü ve temsilcinin dönüş türünü tanımlamak için tür parametrelerini kullanır. `Func`temsilciler, kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadeleri kapsüllemek için çok yararlıdır. Örneğin, <xref:System.Func%602> temsilci türünü göz önünde bulundurun:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Temsilci, giriş parametresi olan `Func<int, bool>` ve `int` `bool` iade değeri olan bir örnek olarak anında kullanılabilir. Dönüş değeri her zaman son tür parametresinde belirtilir. Örneğin, `Func<int, string, bool>` iki giriş paramı `int` ve `string`, bir return türü `bool`olan bir temsilci tanımlar. Aşağıdaki `Func` temsilci, çağrıldığı zaman, giriş parametresinin beşe eşit olup olmadığını gösteren Boolean değerini döndürür:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Bağımsız değişken türü <xref:System.Linq.Expressions.Expression%601>, örneğin <xref:System.Linq.Queryable> türünde tanımlanan standart sorgu işleçlerinde bir lambda ifadesi de sağlayabilirsiniz. Bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişken belirttiğiniz zaman, lambda bir ifade ağacına derlenir.
  
Aşağıdaki örnekte <xref:System.Linq.Enumerable.Count%2A> standart sorgu işleci kullanır:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz. Bu özel lambda ifadesi, ikiye`n`bölündüğünde 1'in geri kalanı olan tamsayılar sayar.

Aşağıdaki örnek, `numbers` dizideki 9'dan önceki tüm öğeleri içeren bir dizi üretir, çünkü bu, dizideki koşula uymayan ilk sayıdır:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Aşağıdaki örnekte, birden çok giriş parametresini parantez içine ekleyerek belirtir. Yöntem, değeri dizideki `numbers` ordinal konumundan daha az olan bir sayıyla karşılaşıncaya kadar dizideki tüm öğeleri döndürür:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Lambda ifadelerinde tür çıkarımı

Lambdas yazarken, genellikle giriş parametreleri için bir tür belirtmeniz gerekmemektedir, çünkü derleyici lambda gövdesine, parametre türlerine ve C# dil belirtiminde açıklandığı gibi diğer etkenlere göre türü çıkarabilirsiniz. Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür. Bir `IEnumerable<Customer>`, giriş değişkenini sorgulıyorsanız, giriş değişkeninin bir `Customer` nesne olduğu ortaya çıkarılır, bu da onun yöntemlerine ve özelliklerine erişiminiz olduğu anlamına gelir:  

```csharp
customers.Where(c => c.City == "London");
```

Lambdas için tip çıkarım için genel kurallar aşağıdaki gibidir:

- Lambda temsilci türüyle aynı sayıda parametre içermelidir.

- Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.

- Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.
  
Ortak tür sistemi "lambda ifade" içsel kavramı vardır, çünkü lambda ifadelerinin kendi içinde bir türü olmadığını unutmayın. Ancak, bazen bir lambda ifade "türü" gayri konuşmak için uygundur. Bu gibi durumlarda tür, lambda <xref:System.Linq.Expressions.Expression> ifadesinin dönüştürüldüğü temsilci türü veya türü ifade eder.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Lambda ifadelerinde dış değişkenlerin ve değişken kapsamın yakalanması

Lambdas dış *değişkenlere*başvurabilir. Lambda ifadesini tanımlayan yöntemde veya lambda ifadesini içeren türde kapsamda olan değişkenlerdir. Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır. Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir. Aşağıdaki örnek bu kuralları gösterir:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:  

- Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.

- Lambda ifadesi içinde tanıtılan değişkenler çevre yönteminde görünmez.

- Lambda ifadesi, çevreleyen yöntemden doğrudan bir [in](../../language-reference/keywords/in-parameter-modifier.md) [,](../../language-reference/keywords/ref.md)ref veya [out](../../language-reference/keywords/out-parameter-modifier.md) parametresini yakalayamaz.

- Lambda ifadesindeki [bir iade](../../language-reference/keywords/return.md) deyimi, çevreleyen yöntemin geri dönmesine neden olmaz.

- Bir lambda ifadesi [goto](../../language-reference/keywords/goto.md)içeremez , [break](../../language-reference/keywords/break.md), veya bu atlama deyiminin hedefi lambda ifade bloğu dışında ise deyimi [devam.](../../language-reference/keywords/continue.md) Hedef bloğun içindeyse lambda ifade bloğunun dışında bir atlama deyimi olması da bir hatadır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="featured-book-chapter"></a>Seçme kitap bölümü

C# 3.0 Yemek Kitabında [Delegeler, Etkinlikler ve Lambda İfadeleri,](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [Üçüncü Baskı: C# 3.0 programcıları için 250'den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [LINQ (Dil-Entegre Sorgu)](../concepts/linq/index.md)
- [İfade Ağaçları](../concepts/expression-trees/index.md)
- [Lambda ifadeleri ile karşılaştırıldığında yerel fonksiyonlar](../../local-functions-vs-lambdas.md)
- [Örtülü olarak yazılan lambda ifadeleri](../../implicitly-typed-lambda-expressions.md)
- [Visual Studio 2008 C# Örnekleri (bkz. LINQ Örnek Sorgular dosyaları ve XQuery programı)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Özyinelemeli lambda ifadeleri](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)
