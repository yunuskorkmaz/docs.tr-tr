---
title: Lambda ifadeleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 786c2937a3f413170665c39464dc2c94417008ad
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331377"
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda ifadeleri (C# Programlama Kılavuzu)

*Lambda ifadesi* , nesne olarak kabul edilen bir kod bloğu (bir ifade veya deyim bloğu). Yöntemlere bir bağımsız değişken olarak geçirilebilir ve Yöntem çağrıları tarafından da döndürülebilir. Lambda ifadeleri için kapsamlı olarak kullanılır:

- Yürütülecek kodu, <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>gibi zaman uyumsuz yöntemlere geçirme.

- [LINQ sorgu ifadeleri](../../linq/index.md)yazılıyor.

- [İfade ağaçları](../concepts/expression-trees/index.md)oluşturma.

Lambda ifadeleri, bir temsilci olarak ya da bir temsilciye derlenen bir ifade ağacı olarak temsil edilebilir koddur. Bir lambda ifadesinin belirli temsilci türü, parametrelerine ve dönüş değerine bağlıdır. Değer döndürmeyen lambda ifadeleri, parametre sayısına bağlı olarak belirli `Action` bir temsilciye karşılık gelir. Değer döndüren lambda ifadeleri, parametre sayısına bağlı olarak belirli `Func` bir temsilciye karşılık gelir. Örneğin, iki parametresi olan bir lambda ifadesi, ancak bir <xref:System.Action%602> temsilciye karşılık gelen hiçbir değer döndürmez. Bir parametreye sahip olan ve <xref:System.Func%602> temsilciye karşılık gelen bir değer döndüren bir lambda ifadesi.

Lambda ifadesi, Lambda `=>`parametre listesini yürütülebilir kodundan ayırmak için [lambda bildirim işlecini](../../language-reference/operators/lambda-operator.md)kullanır. Lambda ifadesi oluşturmak için, lambda işlecinin sol tarafındaki giriş parametrelerini (varsa) belirtirsiniz ve ifadeyi veya deyim bloğunu diğer tarafa yerleştirebilirsiniz. Örneğin, tek satırlık lambda ifadesi `x => x * x` adlı `x` bir parametreyi belirtir `x` ve kare değerlerini döndürür. Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Ayrıca, bir ifade ağaç türüne bir lambda ifadesi atayabilirsiniz:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Ya da doğrudan yöntem bağımsız değişkeni olarak geçirebilirsiniz:

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Sınıfında yöntemi çağırmak için yöntem tabanlı sözdizimi kullandığınızda (LINQ to Objects ve LINQ to XML) parametre bir temsilci türüdür <xref:System.Func%602?displayProperty=nameWithType>. <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable?displayProperty=nameWithType> Lambda ifadesi, bu temsilciyi oluşturmak için en kullanışlı yoldur. Sınıfında yöntemini çağırdığınızda (LINQ to SQL içinde yaptığınız gibi) parametre türü bir ifade ağacı türüdür [`Expression<Func<TSource,TResult>>`.](<xref:System.Linq.Expressions.Expression%601>) <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> <xref:System.Linq.Queryable?displayProperty=nameWithType> Yine, Lambda ifadesi bu ifade ağacını oluşturmanın yalnızca çok kısa bir yoludur. Lambda tarafından oluşturulan nesnenin türü `Select` farklı olsa da Lambdalar, çağrıların benzer görünmesine izin verir.

[Anonim yöntemler](anonymous-methods.md) için uygulanan tüm kısıtlamalar lambda ifadeleri için de geçerlidir.
  
## <a name="expression-lambdas"></a>İfade lambdaları

`=>` İşlecinin sağ tarafında bir ifade olan bir lambda ifadesine bir *ifade lambda*adı verilir. İfade lambdaları ifade [ağaçlarının](../concepts/expression-trees/index.md)yapımını yaygın olarak kullanır. Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:

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
(input-parameters) => { statement; }
```

Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.
  
## <a name="async-lambdas"></a>Zaman uyumsuz Lambdalar

[Async](../../language-reference/keywords/async.md) ve [await](../../language-reference/keywords/await.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz. Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi `ExampleMethodAsync`çağıran ve bekleden bir olay işleyicisi içerir.

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

Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz. Bu işleyiciyi eklemek için aşağıdaki örnekte gösterildiği `async` gibi Lambda parametre listesinden önce bir değiştirici ekleyin:

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

Dil, C# 7,0 ile başlayarak, [Tanımlama grupları](../../tuples.md)için yerleşik destek sağlar. C# Bir lambda ifadesine bağımsız değişken olarak bir tanımlama grubu sağlayabilirsiniz ve lambda ifadeniz de bir tanımlama grubu döndürebilir. Bazı durumlarda, C# derleyici demet bileşenleri türlerini belirlemekte tür çıkarımı kullanır.

Bir tanımlama grubu, bileşenlerinin virgülle ayrılmış bir listesini parantez içine alarak tanımlarsınız. Aşağıdaki örnek, her bir değeri iki katına çıkarır ve çarpma 'un sonucunu içeren üç bileşeni olan bir tanımlama grubu döndüren bir lambda ifadesine bir dizi sayıyı geçirmek için üç bileşeni olan tanımlama grubunu kullanır.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Normalde, bir tanımlama grubu alanları, `Item1` `Item2`, vb. olarak adlandırılır. Ancak, aşağıdaki örnekte olduğu gibi adlandırılmış bileşenlerle bir tanımlama grubu tanımlayabilirsiniz.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Tanımlama grupları hakkında C# daha fazla bilgi için bkz [ C# . demet türleri](../../tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Standart sorgu işleçleri ile Lambdalar

Diğer uygulamalar arasında LINQ to Objects, türü <xref:System.Func%601> Genel Temsilciler ailesinden olan bir giriş parametresine sahiptir. Bu temsilciler, giriş parametrelerinin sayısını ve türünü ve temsilcinin dönüş türünü tanımlamak için tür parametreleri kullanır. `Func`Temsilciler, bir kaynak veri kümesindeki her öğeye uygulanan Kullanıcı tanımlı ifadeleri kapsüllemek için çok yararlıdır. Örneğin, <xref:System.Func%602> temsilci türünü göz önünde bulundurun:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Temsilci, giriş parametresi `Func<int, bool>` `int` olan ve `bool` dönüş değeri olan bir örnek olarak oluşturulabilir. Dönüş değeri her zaman son tür parametresinde belirtilir. Örneğin `Func<int, string, bool>` , iki giriş parametresi olan bir temsilciyi, `int` ve `string`ve dönüş türünü `bool`tanımlar. Aşağıdaki `Func` temsilci çağrıldığında, giriş parametresinin beş ' a eşit olup olmadığını belirten Boole değeri döndürür:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Bağımsız değişken türü bir <xref:System.Linq.Expressions.Expression%601>olduğunda bir lambda ifadesi de sağlayabilirsiniz, örneğin, <xref:System.Linq.Queryable> tür içinde tanımlanan standart sorgu işleçleri. Bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişken belirttiğinizde, lambda bir ifade ağacına derlenir.
  
Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> standart sorgu işlecini kullanır:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz. Bu belirli lambda ifadesi, ikiye bölünen 1`n`' in geri kalanı olduğunda bu tamsayıları () sayar.

Aşağıdaki örnek, koşulu karşılamayan dizideki ilk sayı olduğundan, 9 ' `numbers` dan önce gelen dizide bulunan tüm öğeleri içeren bir dizi üretir:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Aşağıdaki örnek, birden çok giriş parametresini parantez içine alarak belirtir. Yöntemi, değeri dizideki sıra konumundan daha az `numbers` olan bir sayı ile karşılaşana kadar dizideki tüm öğeleri döndürür:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Lambda ifadelerinde tür çıkarımı

Lambda yazarken genellikle giriş parametreleri için bir tür belirtmeniz gerekmez, derleyici lambda gövdesine, parametre türlerine ve C# dil belirtiminde açıklanan diğer etkenlere göre türü çıkarsabilir. Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür. Bir `IEnumerable<Customer>`sorgulama yapıyorsanız, giriş değişkeni bir `Customer` nesne olarak algılanır ve bu, yöntemlerine ve özelliklerine erişiminiz olduğu anlamına gelir:  

```csharp
customers.Where(c => c.City == "London");
```

Lambdalar için tür çıkarımı için genel kurallar aşağıdaki gibidir:

- Lambda temsilci türüyle aynı sayıda parametre içermelidir.

- Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.

- Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.
  
Ortak tür sisteminin hiçbir "lambda ifadesi" kavramı olmadığından, lambda ifadelerinin bir tür olmadığını unutmayın. Ancak, bazen bir lambda ifadesinin "tür" i resmi olarak konuşmak yararlı olabilir. Bu durumlarda tür, lambda ifadesinin dönüştürüldüğü temsilci türüne veya <xref:System.Linq.Expressions.Expression> türüne başvurur.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Lambda ifadelerinde dış değişkenlerin ve değişken kapsamının yakalanması

Lambdalar, lambda ifadesini tanımlayan yöntemde veya lambda ifadesini içeren türdeki kapsamda kapsamda olan *dış değişkenlere* (bkz. [Anonim yöntemler](anonymous-methods.md)) başvurabilir. Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır. Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir. Aşağıdaki örnek bu kuralları gösterir:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:  

- Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.

- Bir lambda ifadesi içinde tanıtılan değişkenler kapsayan yöntemde görünmez.

- Lambda ifadesi kapsayan yöntemden bir [ın](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresini doğrudan yakalayamaz.

- Lambda ifadesindeki bir [dönüş](../../language-reference/keywords/return.md) deyimi kapsayan metodun dönüşmesine neden olmaz.

- Bir lambda ifadesi, bu sıçrama deyiminin hedefi lambda ifade bloğunun dışındaysa bir [goto](../../language-reference/keywords/goto.md), [Break](../../language-reference/keywords/break.md)veya [Continue](../../language-reference/keywords/continue.md) deyimi içeremez. Ayrıca, hedef bloğun içindeyse lambda ifade bloğunun dışında bir sıçrama deyimine sahip olmak için bir hatadır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="featured-book-chapter"></a>Öne çıkan kitap bölümü

3,0 tanımlama kitabı, üçüncü sürüm 'de [ C# [Temsilciler, olaylar ve lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) : 3,0 programcıları için C# 250 'den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [LINQ (dil ile tümleşik sorgu)](../concepts/linq/index.md)
- [Anonim Metotlar](anonymous-methods.md)
- [İfade Ağaçları](../concepts/expression-trees/index.md)
- [Yerel işlevler lambda ifadeleriyle karşılaştırılır](../../local-functions-vs-lambdas.md)
- [Örtük olarak yazılan lambda ifadeleri](../../implicitly-typed-lambda-expressions.md)
- [Visual Studio 2008 C# örnekleri (bkz. LINQ örnek sorguları dosyaları ve XQuery programı)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Özyinelemeli lambda ifadeleri](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
