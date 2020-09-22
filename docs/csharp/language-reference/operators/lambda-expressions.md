---
title: Lambda ifadeleri-C# başvurusu
description: Lambda ifadeleri hakkında bilgi edinin. Gövdesi olarak bir ifadesi olan ifade lambdaları veya gövdesi olarak deyim bloğu olan deyim Lambdalar vardır.
ms.date: 09/22/2020
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: afabca0b4ba4d5f7c6f4a7ba8aa97301456b0941
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871718"
---
# <a name="lambda-expressions-c-reference"></a>Lambda ifadeleri (C# Başvurusu)

*Lambda ifadesi* aşağıdaki iki formdan herhangi birinin bir ifadesidir:

- Gövdesi olarak bir ifadeye sahip olan [ifade lambda](#expression-lambdas) :

  ```csharp
  (input-parameters) => expression
  ```

- Gövdesi olarak bir ifade bloğuna sahip olan [ifade lambda](#statement-lambdas) :

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

Lambda parametre listesini gövdesinden ayırmak için [lambda bildirimi işlecini `=>` ](lambda-operator.md) kullanın. Lambda ifadesi oluşturmak için, lambda işlecinin sol tarafında (varsa) giriş parametrelerini ve diğer tarafta bir ifade ya da deyim bloğunu belirtirsiniz.

Herhangi bir lambda ifadesi, bir [temsilci](../builtin-types/reference-types.md#the-delegate-type) türüne dönüştürülebilir. Lambda ifadesinin dönüştürülebileceği temsilci türü, parametrelerinin ve dönüş değerinin türlerine göre tanımlanır. Lambda ifadesi bir değer döndürmezse, `Action` temsilci türlerinden birine dönüştürülebilir; Aksi takdirde, `Func` temsilci türlerinden birine dönüştürülebilir. Örneğin, iki parametresi olan ve değer döndüren bir lambda ifadesi bir <xref:System.Action%602> temsilciye dönüştürülemez. Bir parametreye sahip olan ve bir değer döndüren bir lambda ifadesi, bir <xref:System.Func%602> temsilciye dönüştürülebilir. Aşağıdaki örnekte, `x => x * x` adlı ve kare değeri döndüren bir parametreyi belirten lambda ifadesi, `x` `x` bir temsilci türü değişkenine atanır:

[!code-csharp-interactive[lambda is delegate](snippets/lambda-expressions/Introduction.cs#Delegate)]

Aşağıdaki örnekte gösterildiği gibi, ifade lambdaları da [ifade ağacı](../../programming-guide/concepts/expression-trees/index.md) türlerine dönüştürülebilir:

[!code-csharp-interactive[lambda is expression tree](snippets/lambda-expressions/Introduction.cs#ExpressionTree)]

Lambda ifadelerini, örneğin, <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> arka planda yürütülmesi gereken kodu geçirmek için yönteme bir bağımsız değişken olarak temsilci türleri veya ifade ağaçları örnekleri gerektiren herhangi bir kodda kullanabilirsiniz. Aşağıdaki örnekte gösterildiği gibi, [C# ' de LINQ](../../linq/index.md)yazdığınızda Lambda ifadelerini de kullanabilirsiniz:

[!code-csharp-interactive[lambda is argument in LINQ](snippets/lambda-expressions/Introduction.cs#Argument)]

Sınıfında yöntemi çağırmak için yöntem tabanlı sözdizimi kullandığınızda ( <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable?displayProperty=nameWithType> örneğin, LINQ to Objects ve LINQ to XML, parametresi bir temsilci türüdür <xref:System.Func%602?displayProperty=nameWithType> . <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>Sınıfında yöntemini çağırdığınızda <xref:System.Linq.Queryable?displayProperty=nameWithType> , örneğin LINQ to SQL, parametre türü bir ifade ağacı türüdür [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) . Her iki durumda da, parametre değerini belirtmek için aynı lambda ifadesini kullanabilirsiniz. `Select`Aslında Lambdalar tarafından oluşturulan nesnelerin türü farklı olsa da, bu iki çağrının benzer görünmesini sağlar.
  
## <a name="expression-lambdas"></a>İfade lambdaları

İşlecinin sağ tarafında bir ifade olan bir lambda ifadesine bir `=>` *ifade lambda*adı verilir. Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:

```csharp
(input-parameters) => expression
```

Lambda ifadesinin gövdesi bir yöntem çağrısından oluşabilir. Ancak, SQL Server gibi .NET ortak dil çalışma zamanının bağlamı dışında değerlendirilen [ifade ağaçları](../../programming-guide/concepts/expression-trees/index.md) oluşturuyorsanız, Lambda ifadelerinde Yöntem çağrılarını kullanmamalısınız. Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.

## <a name="statement-lambdas"></a>İfade lambdaları

Deyimler, deyimlerinin ayraç içine alınması dışında bir ifade lambda öğesine benzer:

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.

:::code interactive="try-dotnet" source="snippets/lambda-expressions/ExpressionAndStatementLambdas.cs" id="SnippetStatementLambda":::

İfade ağaçları oluşturmak için deyim lambdaları kullanamazsınız.

## <a name="input-parameters-of-a-lambda-expression"></a>Lambda ifadesinin giriş parametreleri

Lambda ifadesinin giriş parametrelerini parantez içine alın. Boş ayraçlarla sıfır giriş parametrelerini belirtin:  

[!code-csharp[zero parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

Lambda ifadesinde yalnızca bir giriş parametresi varsa, parantezler isteğe bağlıdır:

[!code-csharp[one parameter](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#OneParameter)]

İki veya daha fazla giriş parametresi virgülle ayrılır:

[!code-csharp[two parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Bazen derleyici giriş parametrelerinin türlerini çıkarsamaz. Aşağıdaki örnekte gösterildiği gibi türleri açıkça belirtebilirsiniz:

[!code-csharp[explicitly typed parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Giriş parametresi türleri tamamen açık veya tümü örtük olmalıdır; Aksi halde, bir [CS0748](../../misc/cs0748.md) derleyici hatası oluşur.

C# 9,0 ' den başlayarak, ifadede kullanılmayan bir lambda ifadesinin iki veya daha fazla giriş parametresini belirtmek için [atarsa](../../discards.md) ' ı kullanabilirsiniz:

:::code language="csharp" source="snippets/lambda-expressions/ExpressionAndStatementLambdas.cs" id="SnippetDiscards":::

Lambda atma parametreleri, bir [olay işleyicisi sağlamak](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)için bir lambda ifadesi kullandığınızda yararlı olabilir.

> [!NOTE]
> Geriye dönük uyumluluk için, yalnızca tek bir giriş parametresi adlandırılmışsa, `_` bir lambda ifadesi içinde `_` Bu parametrenin adı olarak değerlendirilir.

## <a name="async-lambdas"></a>Zaman uyumsuz Lambdalar

[Async](../keywords/async.md) ve [await](await.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz. Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi çağıran ve bekleden bir olay işleyicisi içerir `ExampleMethodAsync` .

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

Zaman uyumsuz yöntemlerin nasıl oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Lambda ifadeleri ve tanımlama grupları

C# 7,0 ile başlayarak, C# dili [Tanımlama grupları](../builtin-types/value-tuples.md)için yerleşik destek sağlar. Bir lambda ifadesine bağımsız değişken olarak bir tanımlama grubu sağlayabilirsiniz ve lambda ifadeniz de bir tanımlama grubu döndürebilir. Bazı durumlarda, C# derleyicisi demet bileşenleri türlerini belirlemede tür çıkarımı kullanır.

Bir tanımlama grubu, bileşenlerinin virgülle ayrılmış bir listesini parantez içine alarak tanımlarsınız. Aşağıdaki örnek, her bir değeri iki katına çıkarır ve çarpma 'un sonucunu içeren üç bileşeni olan bir tanımlama grubu döndüren bir lambda ifadesine bir dizi sayıyı geçirmek için üç bileşeni olan tanımlama grubunu kullanır.

[!code-csharp-interactive[lambda and tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Normalde, bir tanımlama grubu alanları, `Item1` `Item2` , vb. olarak adlandırılır. Ancak, aşağıdaki örnekte olduğu gibi adlandırılmış bileşenlerle bir tanımlama grubu tanımlayabilirsiniz.

[!code-csharp-interactive[lambda and named tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

C# tanımlama bilgileri hakkında daha fazla bilgi için bkz. [demet türleri](../../language-reference/builtin-types/value-tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Standart sorgu işleçleri ile Lambdalar

Diğer uygulamalar arasında LINQ to Objects, türü genel Temsilciler ailesinden olan bir giriş parametresine sahiptir <xref:System.Func%601> . Bu temsilciler, giriş parametrelerinin sayısını ve türünü ve temsilcinin dönüş türünü tanımlamak için tür parametreleri kullanır. `Func` Temsilciler, bir kaynak veri kümesindeki her öğeye uygulanan Kullanıcı tanımlı ifadeleri kapsüllemek için çok yararlıdır. Örneğin, temsilci türünü göz önünde bulundurun <xref:System.Func%602> :  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Temsilci, `Func<int, bool>` `int` giriş parametresi olan ve dönüş değeri olan bir örnek olarak oluşturulabilir `bool` . Dönüş değeri her zaman son tür parametresinde belirtilir. Örneğin, `Func<int, string, bool>` iki giriş parametresi olan bir temsilciyi, `int` ve `string` ve dönüş türünü tanımlar `bool` . Aşağıdaki `Func` temsilci çağrıldığında, giriş parametresinin beş ' a eşit olup olmadığını belirten Boole değeri döndürür:

[!code-csharp-interactive[Func example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Bağımsız değişken türü bir olduğunda bir lambda ifadesi de sağlayabilirsiniz <xref:System.Linq.Expressions.Expression%601> , örneğin, tür içinde tanımlanan standart sorgu işleçleri <xref:System.Linq.Queryable> . Bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişken belirttiğinizde, lambda bir ifade ağacına derlenir.
  
Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> Standart sorgu işlecini kullanır:

[!code-csharp-interactive[Count example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz. Bu belirli lambda ifadesi `n` , ikiye bölünen 1 ' in geri kalanı olduğunda bu tamsayıları () sayar.

Aşağıdaki örnek, `numbers` koşulu karşılamayan dizideki ilk sayı olduğundan, 9 ' dan önce gelen dizide bulunan tüm öğeleri içeren bir dizi üretir:

[!code-csharp-interactive[TakeWhile example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Aşağıdaki örnek, birden çok giriş parametresini parantez içine alarak belirtir. Yöntemi, `numbers` değeri dizideki sıra konumundan daha az olan bir sayı ile karşılaşana kadar dizideki tüm öğeleri döndürür:

[!code-csharp-interactive[TakeWhile example 2](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

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

[!code-csharp[variable scope](snippets/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:  

- Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.

- Bir lambda ifadesi içinde tanıtılan değişkenler kapsayan yöntemde görünmez.

- Lambda ifadesi kapsayan yöntemden bir [ın](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md)veya [Out](../keywords/out-parameter-modifier.md) parametresini doğrudan yakalayamaz.

- Lambda ifadesindeki bir [dönüş](../keywords/return.md) deyimi kapsayan metodun dönüşmesine neden olmaz.

- Bir lambda ifadesi, bu sıçrama deyiminin hedefi lambda ifade bloğunun dışındaysa bir [goto](../keywords/goto.md), [Break](../keywords/break.md)veya [Continue](../keywords/continue.md) deyimi içeremez. Ayrıca, hedef bloğun içindeyse lambda ifade bloğunun dışında bir sıçrama deyimine sahip olmak için bir hatadır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

Lambda atma parametreleri hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-9.0/lambda-discard-parameters.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [LINQ (dil ile tümleşik sorgu)](../../programming-guide/concepts/linq/index.md)
- [İfade ağaçları](../../programming-guide/concepts/expression-trees/index.md)
- [Yerel işlevler ve lambda ifadeleri karşılaştırması](../../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [Visual Studio 2008 C# örnekleri (bkz. LINQ örnek sorguları dosyaları ve XQuery programı)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
