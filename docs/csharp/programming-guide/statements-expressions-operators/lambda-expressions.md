---
title: Lambda ifadeleri-C# Programlama Kılavuzu
description: Lambda ifadeleri hakkında bilgi edinin. Gövdesi olarak bir ifadesi olan ifade lambdaları veya gövdesi olarak deyim bloğu olan deyim Lambdalar vardır.
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 902a3f63967b371c940693464408ff39534917f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380715"
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda ifadeleri (C# Programlama Kılavuzu)

*Lambda ifadesi* aşağıdaki iki formdan herhangi birinin bir ifadesidir:

- Gövdesi olarak bir ifadeye sahip olan [ifade lambda](#expression-lambdas) :

  ```csharp
  (input-parameters) => expression
  ```

- Gövdesi olarak bir ifade bloğuna sahip olan [ifade lambda](#statement-lambdas) :

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

Lambda parametre listesini gövdesinden ayırmak için [lambda bildirimi işlecini `=>` ](../../language-reference/operators/lambda-operator.md) kullanın. Lambda ifadesi oluşturmak için, lambda işlecinin sol tarafında (varsa) giriş parametrelerini ve diğer tarafta bir ifade ya da deyim bloğunu belirtirsiniz.

Herhangi bir lambda ifadesi, bir [temsilci](../../language-reference/builtin-types/reference-types.md#the-delegate-type) türüne dönüştürülebilir. Lambda ifadesinin dönüştürülebileceği temsilci türü, parametrelerinin ve dönüş değerinin türlerine göre tanımlanır. Lambda ifadesi bir değer döndürmezse, `Action` temsilci türlerinden birine dönüştürülebilir; Aksi takdirde, `Func` temsilci türlerinden birine dönüştürülebilir. Örneğin, iki parametresi olan ve değer döndüren bir lambda ifadesi bir <xref:System.Action%602> temsilciye dönüştürülemez. Bir parametreye sahip olan ve bir değer döndüren bir lambda ifadesi, bir <xref:System.Func%602> temsilciye dönüştürülebilir. Aşağıdaki örnekte, `x => x * x` adlı ve kare değeri döndüren bir parametreyi belirten lambda ifadesi, `x` `x` bir temsilci türü değişkenine atanır:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Aşağıdaki örnekte gösterildiği gibi, ifade lambdaları da [ifade ağacı](../concepts/expression-trees/index.md) türlerine dönüştürülebilir:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Lambda ifadelerini, örneğin, <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> arka planda yürütülmesi gereken kodu geçirmek için yönteme bir bağımsız değişken olarak temsilci türleri veya ifade ağaçları örnekleri gerektiren herhangi bir kodda kullanabilirsiniz. Aşağıdaki örnekte gösterildiği gibi, [C# ' de LINQ](../../linq/index.md)yazdığınızda Lambda ifadelerini de kullanabilirsiniz:

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Sınıfında yöntemi çağırmak için yöntem tabanlı sözdizimi kullandığınızda ( <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable?displayProperty=nameWithType> örneğin, LINQ to Objects ve LINQ to XML, parametresi bir temsilci türüdür <xref:System.Func%602?displayProperty=nameWithType> . <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>Sınıfında yöntemini çağırdığınızda <xref:System.Linq.Queryable?displayProperty=nameWithType> , örneğin LINQ to SQL, parametre türü bir ifade ağacı türüdür [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) . Her iki durumda da, parametre değerini belirtmek için aynı lambda ifadesini kullanabilirsiniz. `Select`Aslında Lambdalar tarafından oluşturulan nesnelerin türü farklı olsa da, bu iki çağrının benzer görünmesini sağlar.
  
## <a name="expression-lambdas"></a>İfade lambdaları

İşlecinin sağ tarafında bir ifade olan bir lambda ifadesine bir `=>` *ifade lambda*adı verilir. İfade lambdaları ifade [ağaçlarının](../concepts/expression-trees/index.md)yapımını yaygın olarak kullanır. Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:

```csharp
(input-parameters) => expression
```

Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.

Boş ayraçlarla sıfır giriş parametrelerini belirtin:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Bazen derleyicinin giriş türlerini çıkarması olanaksızdır. Aşağıdaki örnekte gösterildiği gibi türleri açıkça belirtebilirsiniz:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Giriş parametresi türleri tamamen açık veya tümü örtük olmalıdır; Aksi halde, bir [CS0748](../../misc/cs0748.md) derleyici hatası oluşur.

Lambda ifadesinin gövdesi bir yöntem çağrısından oluşabilir. Ancak, SQL Server gibi .NET ortak dil çalışma zamanının bağlamı dışında değerlendirilen ifade ağaçları oluşturuyorsanız, Lambda ifadelerinde Yöntem çağrılarını kullanmamalısınız. Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.

## <a name="statement-lambdas"></a>İfade lambdaları

Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Deyim lambdaları ifade ağaçları oluşturmak için kullanılamaz.
  
## <a name="async-lambdas"></a>Zaman uyumsuz Lambdalar

[Async](../../language-reference/keywords/async.md) ve [await](../../language-reference/operators/await.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz. Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi çağıran ve bekleden bir olay işleyicisi içerir `ExampleMethodAsync` .

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

Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz. Bu işleyiciyi eklemek için `async` Aşağıdaki örnekte gösterildiği gibi Lambda parametre listesinden önce bir değiştirici ekleyin:

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

Zaman uyumsuz yöntemlerin nasıl oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Lambda ifadeleri ve tanımlama grupları

C# 7,0 ile başlayarak, C# dili [Tanımlama grupları](../../language-reference/builtin-types/value-tuples.md)için yerleşik destek sağlar. Bir lambda ifadesine bağımsız değişken olarak bir tanımlama grubu sağlayabilirsiniz ve lambda ifadeniz de bir tanımlama grubu döndürebilir. Bazı durumlarda, C# derleyicisi demet bileşenleri türlerini belirlemede tür çıkarımı kullanır.

Bir tanımlama grubu, bileşenlerinin virgülle ayrılmış bir listesini parantez içine alarak tanımlarsınız. Aşağıdaki örnek, her bir değeri iki katına çıkarır ve çarpma 'un sonucunu içeren üç bileşeni olan bir tanımlama grubu döndüren bir lambda ifadesine bir dizi sayıyı geçirmek için üç bileşeni olan tanımlama grubunu kullanır.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Normalde, bir tanımlama grubu alanları, `Item1` `Item2` , vb. olarak adlandırılır. Ancak, aşağıdaki örnekte olduğu gibi adlandırılmış bileşenlerle bir tanımlama grubu tanımlayabilirsiniz.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

C# tanımlama bilgileri hakkında daha fazla bilgi için bkz. [demet türleri](../../language-reference/builtin-types/value-tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Standart sorgu işleçleri ile Lambdalar

Diğer uygulamalar arasında LINQ to Objects, türü genel Temsilciler ailesinden olan bir giriş parametresine sahiptir <xref:System.Func%601> . Bu temsilciler, giriş parametrelerinin sayısını ve türünü ve temsilcinin dönüş türünü tanımlamak için tür parametreleri kullanır. `Func`Temsilciler, bir kaynak veri kümesindeki her öğeye uygulanan Kullanıcı tanımlı ifadeleri kapsüllemek için çok yararlıdır. Örneğin, temsilci türünü göz önünde bulundurun <xref:System.Func%602> :  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Temsilci, `Func<int, bool>` `int` giriş parametresi olan ve dönüş değeri olan bir örnek olarak oluşturulabilir `bool` . Dönüş değeri her zaman son tür parametresinde belirtilir. Örneğin, `Func<int, string, bool>` iki giriş parametresi olan bir temsilciyi, `int` ve `string` ve dönüş türünü tanımlar `bool` . Aşağıdaki `Func` temsilci çağrıldığında, giriş parametresinin beş ' a eşit olup olmadığını belirten Boole değeri döndürür:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Bağımsız değişken türü bir olduğunda bir lambda ifadesi de sağlayabilirsiniz <xref:System.Linq.Expressions.Expression%601> , örneğin, tür içinde tanımlanan standart sorgu işleçleri <xref:System.Linq.Queryable> . Bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişken belirttiğinizde, lambda bir ifade ağacına derlenir.
  
Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> Standart sorgu işlecini kullanır:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz. Bu belirli lambda ifadesi `n` , ikiye bölünen 1 ' in geri kalanı olduğunda bu tamsayıları () sayar.

Aşağıdaki örnek, `numbers` koşulu karşılamayan dizideki ilk sayı olduğundan, 9 ' dan önce gelen dizide bulunan tüm öğeleri içeren bir dizi üretir:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Aşağıdaki örnek, birden çok giriş parametresini parantez içine alarak belirtir. Yöntemi, `numbers` değeri dizideki sıra konumundan daha az olan bir sayı ile karşılaşana kadar dizideki tüm öğeleri döndürür:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Lambda ifadelerinde tür çıkarımı

Lambda yazarken genellikle giriş parametreleri için bir tür belirtmeniz gerekmez, derleyici lambda gövdesine, parametre türlerine ve C# dil belirtiminde açıklanan diğer etkenlere göre türü çıkarsabilir. Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür. Bir sorgulama yapıyorsanız `IEnumerable<Customer>` , giriş değişkeni bir nesne olarak algılanır `Customer` ve bu, yöntemlerine ve özelliklerine erişiminiz olduğu anlamına gelir:  

```csharp
customers.Where(c => c.City == "London");
```

Lambdalar için tür çıkarımı için genel kurallar aşağıdaki gibidir:

- Lambda temsilci türüyle aynı sayıda parametre içermelidir.

- Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.

- Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.
  
Ortak tür sisteminin hiçbir "lambda ifadesi" kavramı olmadığından, lambda ifadelerinin bir tür olmadığını unutmayın. Ancak, bazen bir lambda ifadesinin "tür" i resmi olarak konuşmak yararlı olabilir. Bu durumlarda tür, <xref:System.Linq.Expressions.Expression> lambda ifadesinin dönüştürüldüğü temsilci türüne veya türüne başvurur.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Lambda ifadelerinde dış değişkenlerin ve değişken kapsamının yakalanması

Lambdalar, *dış değişkenlere*başvurabilir. Bunlar, lambda ifadesini tanımlayan yöntemde veya lambda ifadesini içeren türde kapsamda kapsam içinde olan değişkenlerdir. Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır. Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir. Aşağıdaki örnek bu kuralları gösterir:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:  

- Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.

- Bir lambda ifadesi içinde tanıtılan değişkenler kapsayan yöntemde görünmez.

- Lambda ifadesi kapsayan yöntemden bir [ın](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresini doğrudan yakalayamaz.

- Lambda ifadesindeki bir [dönüş](../../language-reference/keywords/return.md) deyimi kapsayan metodun dönüşmesine neden olmaz.

- Bir lambda ifadesi, bu sıçrama deyiminin hedefi lambda ifade bloğunun dışındaysa bir [goto](../../language-reference/keywords/goto.md), [Break](../../language-reference/keywords/break.md)veya [Continue](../../language-reference/keywords/continue.md) deyimi içeremez. Ayrıca, hedef bloğun içindeyse lambda ifade bloğunun dışında bir sıçrama deyimine sahip olmak için bir hatadır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="featured-book-chapter"></a>Öne çıkan kitap bölümü

C# 3,0 tanımlama kitabı, üçüncü sürüm 'de [Temsilciler, olaylar ve lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [: c# 3,0 programcıları için 250 ' den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [LINQ (dil ile tümleşik sorgu)](../concepts/linq/index.md)
- [İfade ağaçları](../concepts/expression-trees/index.md)
- [Yerel işlevler ve lambda ifadeleri karşılaştırması](../classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [Visual Studio 2008 C# örnekleri (bkz. LINQ örnek sorguları dosyaları ve XQuery programı)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Özyinelemeli lambda ifadeleri](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)
