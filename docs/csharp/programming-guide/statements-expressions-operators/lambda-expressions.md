---
title: Lambda ifadeleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: dd9b77a90030a96d17104c8c0e48964b6a85d165
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125739"
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda ifadeleri (C# Programlama Kılavuzu)

A *lambda ifadesi* (bir ifadeyi veya deyim bloğunu) bir nesne olarak işlem kod bloğudur. Yöntemi için bağımsız değişken olarak geçirilebilir ve yöntem çağrıları tarafından da döndürülebilir. Lambda ifadeleri için yaygın olarak kullanılır:

- Kod geçirmeden olduğu gibi zaman uyumsuz yöntemler için yürütülecek <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.

- Yazma [LINQ Sorgu ifadeleri](../../linq/index.md).

- Oluşturma [ifade ağaçları](../concepts/expression-trees/index.md).

Lambda ifadeleri temsilci olarak veya bir ifade ağacına derleyen bir temsilciye olarak gösterilen kodu var. Bir lambda ifadesinin özel temsilci türü kendi parametrelerine göre değişir ve dönüş değeri. Bir değer döndürmeyen bir lambda ifadeleri, belirli bir karşılık gelen `Action` , parametreleri, sayısına bağlı olarak temsilci. Bir değer döndüren bir lambda ifadeleri, belirli bir karşılık gelen `Func` , parametreleri, sayısına bağlı olarak temsilci. Örneğin, iki parametreye sahip ancak hiçbir değer döndürmeyen bir lambda ifadesi için karşılık gelen bir <xref:System.Action%602> temsilci. Bir parametreye sahiptir ve bir değer döndüren bir lambda ifadesi karşılık gelen <xref:System.Func%602> temsilci.

Bir lambda ifadesi kullanır `=>`, [lambda bildirimi işleci](../../language-reference/operators/lambda-operator.md), lambdanın parametre listesi, yürütülebilir kodundan ayırın. Bir lambda ifadesi oluşturmak için giriş parametreleri (varsa) lambda işlecinin sol tarafında belirtin ve ifadeyi veya deyim bloğunu diğer tarafa yerleştirin. Örneğin, tek satırlı lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış. Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Ayrıca, bir lambda ifadesi bir ifade ağacı türüne atayabilirsiniz:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Veya doğrudan bir yöntemi bağımsız değişken geçirin:

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Çağırmak için yöntem tabanlı sözdizimi kullandığınızda <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> yönteminde <xref:System.Linq.Enumerable?displayProperty=nameWithType> sınıfı (LINQ to nesneleri ve LINQ to XML için yaptığınız gibi) parametre temsilci türüdür <xref:System.Func%602?displayProperty=nameWithType>. Lambda ifadesi, bu temsilciyi oluşturmak için en kullanışlı yoldur. Çağırdığınızda <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> yönteminde <xref:System.Linq.Queryable?displayProperty=nameWithType> sınıfı (LINQ to SQL için yaptığınız gibi) parametre türü bir ifade ağacı türü olan [ `Expression<Func<TSource,TResult>>` ](<xref:System.Linq.Expressions.Expression%601>). Yine, Lambda ifadesi bu ifade ağacını oluşturmanın yalnızca çok kısa bir yoludur. Lambdalar izin `Select` çağrılarının benzer görünmesine, aslında lambdadan oluşturulan nesnenin türü farklı olsa.

İçin tüm kısıtlamalar [anonim yöntemler](anonymous-methods.md) lambda ifadeleri için de geçerlidir.
  
## <a name="expression-lambdas"></a>Expression lambdas

Sağ alt tarafında bir ifade olan bir lambda ifadesine `=>` işleci çağrıldığında bir *lambda ifadesi*. İfade lambdaları oluşumunu oluşturulurken sıkça kullanılır [ifade ağaçları](../concepts/expression-trees/index.md). Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:

```csharp
(input-parameters) => expression
```

Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.

Boş ayraçlarla sıfır giriş parametrelerini belirtin:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Bazen derleyicinin giriş türlerini çıkarması mümkün değildir. Türleri aşağıdaki örnekte gösterildiği gibi açıkça belirtebilirsiniz:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Giriş parametre türlerinin tümü explicit veya tümü implicit olmalıdır; Aksi takdirde, bir [CS0748](../../misc/cs0748.md) derleyici hatası oluşur.

Bir lambda ifadesi gövdesinin yöntem çağrısından oluşabilir. .NET ortak dil çalışma zamanı bağlamı dışında değerlendirilen ifade ağaçları oluşturuyorsanız, ancak gibi SQL Server'da, yöntem çağrılarını lambda ifadelerinde kullanmamanız gerekir. Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.

## <a name="statement-lambdas"></a>Deyim lambdaları

Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:

```csharp  
(input-parameters) => { statement; }
```

Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.
  
## <a name="async-lambdas"></a>Async lambdas

İçeren kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz [zaman uyumsuz](../../language-reference/keywords/async.md) ve [await](../../language-reference/keywords/await.md) anahtar sözcükleri. Örneğin, aşağıdaki Windows Forms örneği, çağıran ve bekleyen zaman uyumsuz bir yöntem, bir olay işleyici içerir `ExampleMethodAsync`.

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

Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz. Bu işleyiciyi eklemek için Ekle bir `async` değiştiricisi, aşağıdaki örnekte göründüğü gibi lambda parametre listesinden önce:

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

Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await](../concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Lambda ifadeleri ve diziler

İle başlayarak C# 7.0 C# dil için yerleşik destek sağlar [diziler](../../tuples.md). Bir lambda ifadesi bağımsız değişkeni olarak bir tanımlama grubu sağlayabilir ve, lambda ifadesi, ayrıca bir demet döndürebilir. Bazı durumlarda, tanımlama grubu bileşenleri türlerini belirlemek için tür çıkarımı C# derleyicisini kullanır.

Bir dizi, parantez içine alarak bileşenlerinden virgülle ayrılmış bir listesini tanımlayın. Aşağıdaki örnek, her değerin iki katına çıkar ve multiplications sonucunu içeren bir tanımlama grubu üç bileşeni ile döndüren bir lambda ifadesi için bir sayı dizisi üzerinde geçirmek için üç bileşeni ile tanımlama grubu kullanır.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Normalde, bir kayıt düzeni alanlarını olarak da adlandırılır `Item1`, `Item2`vb. Ancak, aşağıdaki örnekte olduğu gibi bir dizi adlandırılmış bileşenlerle tanımlayabilirsiniz.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Hakkında daha fazla bilgi için C# diziler için bkz: [ C# tanımlama grubu türleri](../../tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Standart sorgu işleçleri ile lambda ifadeleri

LINQ to Objects'in, diğer uygulamalar arasında olması, türü giriş parametresi, <xref:System.Func%601> Genel temsilci ailesinden olan. Bu Temsilciler, tür parametreleri sayısı ve girdi parametrelerinin türünü ve temsilcinin dönüş türünü tanımlamak için kullanın. `Func` Temsilciler, kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadelerin Kapsüllenmesi için son çok yararlı olur. Örneğin, düşünün <xref:System.Func%602> temsilci türü:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Temsilci olarak oluşturulabilir bir `Func<int, bool>` örneğinde `int` giriş parametresi, ve `bool` dönüş değeridir. Dönüş değeri her zaman son tür parametresinde belirtilir. Örneğin, `Func<int, string, bool>` iki giriş parametrelerini içeren bir temsilci tanımlar `int` ve `string`ve bir dönüş türü `bool`. Aşağıdaki `Func` temsilcisi çağrıldığında, giriş parametresinin 5 için eşit olup olmadığını gösteren Boole değeri döndürür:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Ayrıca bağımsız değişken türü bir lambda ifadesi sağlayabilirsiniz bir <xref:System.Linq.Expressions.Expression%601>, örneğin tanımlanan standart sorgu işleçleri içinde <xref:System.Linq.Queryable> türü. Belirttiğinizde bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişkeni, lambda ifade ağacında derlenmiştir.
  
Aşağıdaki örnekte <xref:System.Linq.Enumerable.Count%2A> standart sorgu işleci:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz. Bu belirli lambda ifadesi tamsayıları sayar (`n`), ikiye bölündüğünde 1 kalan sahip.

Aşağıdaki örnekte tüm öğelerini içeren bir dizi üretir `numbers` , dizisinde koşulu sağlamayan ilk sayı olduğundan 9 önünde dizinin:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Aşağıdaki örnek, birden fazla giriş parametrelerini paranteze tarafından belirtir. Bu yöntem tüm öğeleri döndürür `numbers` sıralı konumuna dizideki değerinden bir sayı değeri karşılaşana kadar dizisi:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Lambda ifadeleri içinde tür çıkarımı

Lambda ifadeleri yazarken, genellikle derleyici açıklandığı lambda gövdesi, parametre türleri ve diğer etkenlere göre türü çıkarsayabilir giriş parametreleri için bir tür belirtmeniz gerekmez C# dil belirtimi. Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür. Sorguluyorsanız bir `IEnumerable<Customer>`, giriş değişkeni olması sorguluyorsanız bir `Customer` nesne erişim yöntemleri ve özellikleri iznine sahip olduğunuz anlamına gelir:  

```csharp
customers.Where(c => c.City == "London");
```

Lambdalar için tür çıkarımı için genel kurallar aşağıdaki gibidir:

- Lambda temsilci türüyle aynı sayıda parametre içermelidir.

- Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.

- Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.
  
Ortak tür sistemi "lambda ifadesi" İç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü yüklü olmadığını unutmayın Ancak, bazen "türü" bir lambda ifadesinin peter'in konuşmak kullanışlı olabilir. Bu gibi durumlarda, tür temsilci türüne başvuruyor. veya <xref:System.Linq.Expressions.Expression> , lambda ifadesinin dönüştürüldüğü yazın.

## <a name="variable-scope-in-lambda-expressions"></a>Lambda ifadelerinde değişken kapsamı

Lambdalar başvurabilir *dış değişkenlere* (bkz [anonim yöntemler](anonymous-methods.md)), lambda ifadesi tanımlayan yöntemin kapsamındaki ya da lambda ifadesini içeren türün kapsamındaki. Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır. Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir. Aşağıdaki örnek bu kuralları gösterir:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:  

- Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.

- Bir lambda ifadesi içinde tanıtılan değişkenler, kapsayan yöntemin görünmez.

- Bir lambda ifadesini doğrudan yakalayamaz bir [içinde](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), veya [kullanıma](../../language-reference/keywords/out-parameter-modifier.md) parametresi kapsayan bir yöntemden alınan.

- A [dönüş](../../language-reference/keywords/return.md) deyiminde bir lambda ifadesi kapsayan yöntemin dönüş neden değil.

- Bir lambda ifadesi içeremez bir [goto](../../language-reference/keywords/goto.md), [sonu](../../language-reference/keywords/break.md), veya [devam](../../language-reference/keywords/continue.md) hedefi, atlama deyimi, deyimi, lambda ifadesi blok dışındaysa. Ayrıca hedef blok içinde ise lambda ifadesi bloğu dışında bir deyim olması hatadır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="featured-book-chapter"></a>Özel Kitap bölümü

[Temsilciler, olayları ve Lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) içinde [ C# 3.0 Cookbook, Third Edition: İçin 250'den fazla çözüm C# 3.0 programcıları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [LINQ (dil ile tümleşik sorgu)](../concepts/linq/index.md)
- [Anonim Metotlar](anonymous-methods.md)
- [İfade Ağaçları](../concepts/expression-trees/index.md)
- [Lambda ifadeleri karşılaştırma yerel işlevler](../../local-functions-vs-lambdas.md)
- [Türü örtük olarak belirlenmiş lambda ifadeleri](../../implicitly-typed-lambda-expressions.md)
- [Visual Studio 2008 C# örnekleri (bkz: LINQ örnek sorgular dosyalar ve XQuery programı)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Yinelemeli lambda ifadeleri](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
