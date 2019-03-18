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
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="992a5-102">Lambda ifadeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="992a5-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="992a5-103">A *lambda ifadesi* (bir ifadeyi veya deyim bloğunu) bir nesne olarak işlem kod bloğudur.</span><span class="sxs-lookup"><span data-stu-id="992a5-103">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="992a5-104">Yöntemi için bağımsız değişken olarak geçirilebilir ve yöntem çağrıları tarafından da döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="992a5-104">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="992a5-105">Lambda ifadeleri için yaygın olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="992a5-105">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="992a5-106">Kod geçirmeden olduğu gibi zaman uyumsuz yöntemler için yürütülecek <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="992a5-106">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="992a5-107">Yazma [LINQ Sorgu ifadeleri](../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="992a5-107">Writing [LINQ query expressions](../../linq/index.md).</span></span>

- <span data-ttu-id="992a5-108">Oluşturma [ifade ağaçları](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="992a5-108">Creating [expression trees](../concepts/expression-trees/index.md).</span></span>

<span data-ttu-id="992a5-109">Lambda ifadeleri temsilci olarak veya bir ifade ağacına derleyen bir temsilciye olarak gösterilen kodu var.</span><span class="sxs-lookup"><span data-stu-id="992a5-109">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="992a5-110">Bir lambda ifadesinin özel temsilci türü kendi parametrelerine göre değişir ve dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="992a5-110">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="992a5-111">Bir değer döndürmeyen bir lambda ifadeleri, belirli bir karşılık gelen `Action` , parametreleri, sayısına bağlı olarak temsilci.</span><span class="sxs-lookup"><span data-stu-id="992a5-111">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="992a5-112">Bir değer döndüren bir lambda ifadeleri, belirli bir karşılık gelen `Func` , parametreleri, sayısına bağlı olarak temsilci.</span><span class="sxs-lookup"><span data-stu-id="992a5-112">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="992a5-113">Örneğin, iki parametreye sahip ancak hiçbir değer döndürmeyen bir lambda ifadesi için karşılık gelen bir <xref:System.Action%602> temsilci.</span><span class="sxs-lookup"><span data-stu-id="992a5-113">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="992a5-114">Bir parametreye sahiptir ve bir değer döndüren bir lambda ifadesi karşılık gelen <xref:System.Func%602> temsilci.</span><span class="sxs-lookup"><span data-stu-id="992a5-114">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="992a5-115">Bir lambda ifadesi kullanır `=>`, [lambda bildirimi işleci](../../language-reference/operators/lambda-operator.md), lambdanın parametre listesi, yürütülebilir kodundan ayırın.</span><span class="sxs-lookup"><span data-stu-id="992a5-115">A lambda expression uses `=>`, the [lambda declaration operator](../../language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="992a5-116">Bir lambda ifadesi oluşturmak için giriş parametreleri (varsa) lambda işlecinin sol tarafında belirtin ve ifadeyi veya deyim bloğunu diğer tarafa yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="992a5-116">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="992a5-117">Örneğin, tek satırlı lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış.</span><span class="sxs-lookup"><span data-stu-id="992a5-117">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="992a5-118">Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="992a5-118">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="992a5-119">Ayrıca, bir lambda ifadesi bir ifade ağacı türüne atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="992a5-119">You also can assign a lambda expression to an expression tree type:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="992a5-120">Veya doğrudan bir yöntemi bağımsız değişken geçirin:</span><span class="sxs-lookup"><span data-stu-id="992a5-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="992a5-121">Çağırmak için yöntem tabanlı sözdizimi kullandığınızda <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> yönteminde <xref:System.Linq.Enumerable?displayProperty=nameWithType> sınıfı (LINQ to nesneleri ve LINQ to XML için yaptığınız gibi) parametre temsilci türüdür <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="992a5-121">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class (as you do in LINQ to Objects and LINQ to XML) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="992a5-122">Lambda ifadesi, bu temsilciyi oluşturmak için en kullanışlı yoldur.</span><span class="sxs-lookup"><span data-stu-id="992a5-122">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="992a5-123">Çağırdığınızda <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> yönteminde <xref:System.Linq.Queryable?displayProperty=nameWithType> sınıfı (LINQ to SQL için yaptığınız gibi) parametre türü bir ifade ağacı türü olan [ `Expression<Func<TSource,TResult>>` ](<xref:System.Linq.Expressions.Expression%601>).</span><span class="sxs-lookup"><span data-stu-id="992a5-123">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in LINQ to SQL) the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="992a5-124">Yine, Lambda ifadesi bu ifade ağacını oluşturmanın yalnızca çok kısa bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="992a5-124">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="992a5-125">Lambdalar izin `Select` çağrılarının benzer görünmesine, aslında lambdadan oluşturulan nesnenin türü farklı olsa.</span><span class="sxs-lookup"><span data-stu-id="992a5-125">The lambdas allow the `Select` calls to look similar although in fact the type of object created from the lambda is different.</span></span>

<span data-ttu-id="992a5-126">İçin tüm kısıtlamalar [anonim yöntemler](anonymous-methods.md) lambda ifadeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="992a5-126">All restrictions that apply to [anonymous methods](anonymous-methods.md) also apply to lambda expressions.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="992a5-127">Expression lambdas</span><span class="sxs-lookup"><span data-stu-id="992a5-127">Expression lambdas</span></span>

<span data-ttu-id="992a5-128">Sağ alt tarafında bir ifade olan bir lambda ifadesine `=>` işleci çağrıldığında bir *lambda ifadesi*.</span><span class="sxs-lookup"><span data-stu-id="992a5-128">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="992a5-129">İfade lambdaları oluşumunu oluşturulurken sıkça kullanılır [ifade ağaçları](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="992a5-129">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="992a5-130">Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="992a5-130">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="992a5-131">Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="992a5-131">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="992a5-132">Boş ayraçlarla sıfır giriş parametrelerini belirtin:</span><span class="sxs-lookup"><span data-stu-id="992a5-132">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="992a5-133">İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:</span><span class="sxs-lookup"><span data-stu-id="992a5-133">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="992a5-134">Bazen derleyicinin giriş türlerini çıkarması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="992a5-134">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="992a5-135">Türleri aşağıdaki örnekte gösterildiği gibi açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="992a5-135">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="992a5-136">Giriş parametre türlerinin tümü explicit veya tümü implicit olmalıdır; Aksi takdirde, bir [CS0748](../../misc/cs0748.md) derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="992a5-136">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="992a5-137">Bir lambda ifadesi gövdesinin yöntem çağrısından oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="992a5-137">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="992a5-138">.NET ortak dil çalışma zamanı bağlamı dışında değerlendirilen ifade ağaçları oluşturuyorsanız, ancak gibi SQL Server'da, yöntem çağrılarını lambda ifadelerinde kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="992a5-138">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="992a5-139">Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="992a5-139">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="992a5-140">Deyim lambdaları</span><span class="sxs-lookup"><span data-stu-id="992a5-140">Statement lambdas</span></span>

<span data-ttu-id="992a5-141">Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:</span><span class="sxs-lookup"><span data-stu-id="992a5-141">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { statement; }
```

<span data-ttu-id="992a5-142">Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.</span><span class="sxs-lookup"><span data-stu-id="992a5-142">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="992a5-143">Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="992a5-143">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="992a5-144">Async lambdas</span><span class="sxs-lookup"><span data-stu-id="992a5-144">Async lambdas</span></span>

<span data-ttu-id="992a5-145">İçeren kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz [zaman uyumsuz](../../language-reference/keywords/async.md) ve [await](../../language-reference/keywords/await.md) anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="992a5-145">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="992a5-146">Örneğin, aşağıdaki Windows Forms örneği, çağıran ve bekleyen zaman uyumsuz bir yöntem, bir olay işleyici içerir `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="992a5-146">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="992a5-147">Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="992a5-147">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="992a5-148">Bu işleyiciyi eklemek için Ekle bir `async` değiştiricisi, aşağıdaki örnekte göründüğü gibi lambda parametre listesinden önce:</span><span class="sxs-lookup"><span data-stu-id="992a5-148">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="992a5-149">Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="992a5-149">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="992a5-150">Lambda ifadeleri ve diziler</span><span class="sxs-lookup"><span data-stu-id="992a5-150">Lambda expressions and tuples</span></span>

<span data-ttu-id="992a5-151">İle başlayarak C# 7.0 C# dil için yerleşik destek sağlar [diziler](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="992a5-151">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="992a5-152">Bir lambda ifadesi bağımsız değişkeni olarak bir tanımlama grubu sağlayabilir ve, lambda ifadesi, ayrıca bir demet döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="992a5-152">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="992a5-153">Bazı durumlarda, tanımlama grubu bileşenleri türlerini belirlemek için tür çıkarımı C# derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="992a5-153">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="992a5-154">Bir dizi, parantez içine alarak bileşenlerinden virgülle ayrılmış bir listesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="992a5-154">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="992a5-155">Aşağıdaki örnek, her değerin iki katına çıkar ve multiplications sonucunu içeren bir tanımlama grubu üç bileşeni ile döndüren bir lambda ifadesi için bir sayı dizisi üzerinde geçirmek için üç bileşeni ile tanımlama grubu kullanır.</span><span class="sxs-lookup"><span data-stu-id="992a5-155">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="992a5-156">Normalde, bir kayıt düzeni alanlarını olarak da adlandırılır `Item1`, `Item2`vb. Ancak, aşağıdaki örnekte olduğu gibi bir dizi adlandırılmış bileşenlerle tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="992a5-156">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="992a5-157">Hakkında daha fazla bilgi için C# diziler için bkz: [ C# tanımlama grubu türleri](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="992a5-157">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="992a5-158">Standart sorgu işleçleri ile lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="992a5-158">Lambdas with the standard query operators</span></span>

<span data-ttu-id="992a5-159">LINQ to Objects'in, diğer uygulamalar arasında olması, türü giriş parametresi, <xref:System.Func%601> Genel temsilci ailesinden olan.</span><span class="sxs-lookup"><span data-stu-id="992a5-159">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="992a5-160">Bu Temsilciler, tür parametreleri sayısı ve girdi parametrelerinin türünü ve temsilcinin dönüş türünü tanımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="992a5-160">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="992a5-161">`Func` Temsilciler, kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadelerin Kapsüllenmesi için son çok yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="992a5-161">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="992a5-162">Örneğin, düşünün <xref:System.Func%602> temsilci türü:</span><span class="sxs-lookup"><span data-stu-id="992a5-162">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="992a5-163">Temsilci olarak oluşturulabilir bir `Func<int, bool>` örneğinde `int` giriş parametresi, ve `bool` dönüş değeridir.</span><span class="sxs-lookup"><span data-stu-id="992a5-163">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="992a5-164">Dönüş değeri her zaman son tür parametresinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="992a5-164">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="992a5-165">Örneğin, `Func<int, string, bool>` iki giriş parametrelerini içeren bir temsilci tanımlar `int` ve `string`ve bir dönüş türü `bool`.</span><span class="sxs-lookup"><span data-stu-id="992a5-165">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="992a5-166">Aşağıdaki `Func` temsilcisi çağrıldığında, giriş parametresinin 5 için eşit olup olmadığını gösteren Boole değeri döndürür:</span><span class="sxs-lookup"><span data-stu-id="992a5-166">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="992a5-167">Ayrıca bağımsız değişken türü bir lambda ifadesi sağlayabilirsiniz bir <xref:System.Linq.Expressions.Expression%601>, örneğin tanımlanan standart sorgu işleçleri içinde <xref:System.Linq.Queryable> türü.</span><span class="sxs-lookup"><span data-stu-id="992a5-167">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="992a5-168">Belirttiğinizde bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişkeni, lambda ifade ağacında derlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="992a5-168">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="992a5-169">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Count%2A> standart sorgu işleci:</span><span class="sxs-lookup"><span data-stu-id="992a5-169">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="992a5-170">Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="992a5-170">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="992a5-171">Bu belirli lambda ifadesi tamsayıları sayar (`n`), ikiye bölündüğünde 1 kalan sahip.</span><span class="sxs-lookup"><span data-stu-id="992a5-171">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="992a5-172">Aşağıdaki örnekte tüm öğelerini içeren bir dizi üretir `numbers` , dizisinde koşulu sağlamayan ilk sayı olduğundan 9 önünde dizinin:</span><span class="sxs-lookup"><span data-stu-id="992a5-172">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="992a5-173">Aşağıdaki örnek, birden fazla giriş parametrelerini paranteze tarafından belirtir.</span><span class="sxs-lookup"><span data-stu-id="992a5-173">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="992a5-174">Bu yöntem tüm öğeleri döndürür `numbers` sıralı konumuna dizideki değerinden bir sayı değeri karşılaşana kadar dizisi:</span><span class="sxs-lookup"><span data-stu-id="992a5-174">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="992a5-175">Lambda ifadeleri içinde tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="992a5-175">Type inference in lambda expressions</span></span>

<span data-ttu-id="992a5-176">Lambda ifadeleri yazarken, genellikle derleyici açıklandığı lambda gövdesi, parametre türleri ve diğer etkenlere göre türü çıkarsayabilir giriş parametreleri için bir tür belirtmeniz gerekmez C# dil belirtimi.</span><span class="sxs-lookup"><span data-stu-id="992a5-176">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="992a5-177">Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür.</span><span class="sxs-lookup"><span data-stu-id="992a5-177">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="992a5-178">Sorguluyorsanız bir `IEnumerable<Customer>`, giriş değişkeni olması sorguluyorsanız bir `Customer` nesne erişim yöntemleri ve özellikleri iznine sahip olduğunuz anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="992a5-178">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="992a5-179">Lambdalar için tür çıkarımı için genel kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="992a5-179">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="992a5-180">Lambda temsilci türüyle aynı sayıda parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="992a5-180">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="992a5-181">Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="992a5-181">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="992a5-182">Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="992a5-182">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="992a5-183">Ortak tür sistemi "lambda ifadesi" İç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü yüklü olmadığını unutmayın</span><span class="sxs-lookup"><span data-stu-id="992a5-183">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="992a5-184">Ancak, bazen "türü" bir lambda ifadesinin peter'in konuşmak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="992a5-184">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="992a5-185">Bu gibi durumlarda, tür temsilci türüne başvuruyor. veya <xref:System.Linq.Expressions.Expression> , lambda ifadesinin dönüştürüldüğü yazın.</span><span class="sxs-lookup"><span data-stu-id="992a5-185">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="992a5-186">Lambda ifadelerinde değişken kapsamı</span><span class="sxs-lookup"><span data-stu-id="992a5-186">Variable scope in lambda expressions</span></span>

<span data-ttu-id="992a5-187">Lambdalar başvurabilir *dış değişkenlere* (bkz [anonim yöntemler](anonymous-methods.md)), lambda ifadesi tanımlayan yöntemin kapsamındaki ya da lambda ifadesini içeren türün kapsamındaki.</span><span class="sxs-lookup"><span data-stu-id="992a5-187">Lambdas can refer to *outer variables* (see [Anonymous methods](anonymous-methods.md)) that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="992a5-188">Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="992a5-188">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="992a5-189">Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="992a5-189">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="992a5-190">Aşağıdaki örnek bu kuralları gösterir:</span><span class="sxs-lookup"><span data-stu-id="992a5-190">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="992a5-191">Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="992a5-191">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="992a5-192">Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.</span><span class="sxs-lookup"><span data-stu-id="992a5-192">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="992a5-193">Bir lambda ifadesi içinde tanıtılan değişkenler, kapsayan yöntemin görünmez.</span><span class="sxs-lookup"><span data-stu-id="992a5-193">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="992a5-194">Bir lambda ifadesini doğrudan yakalayamaz bir [içinde](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), veya [kullanıma](../../language-reference/keywords/out-parameter-modifier.md) parametresi kapsayan bir yöntemden alınan.</span><span class="sxs-lookup"><span data-stu-id="992a5-194">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="992a5-195">A [dönüş](../../language-reference/keywords/return.md) deyiminde bir lambda ifadesi kapsayan yöntemin dönüş neden değil.</span><span class="sxs-lookup"><span data-stu-id="992a5-195">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="992a5-196">Bir lambda ifadesi içeremez bir [goto](../../language-reference/keywords/goto.md), [sonu](../../language-reference/keywords/break.md), veya [devam](../../language-reference/keywords/continue.md) hedefi, atlama deyimi, deyimi, lambda ifadesi blok dışındaysa.</span><span class="sxs-lookup"><span data-stu-id="992a5-196">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="992a5-197">Ayrıca hedef blok içinde ise lambda ifadesi bloğu dışında bir deyim olması hatadır.</span><span class="sxs-lookup"><span data-stu-id="992a5-197">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="992a5-198">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="992a5-198">C# language specification</span></span>

<span data-ttu-id="992a5-199">Daha fazla bilgi için [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="992a5-199">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="992a5-200">Özel Kitap bölümü</span><span class="sxs-lookup"><span data-stu-id="992a5-200">Featured book chapter</span></span>

<span data-ttu-id="992a5-201">[Temsilciler, olayları ve Lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) içinde [ C# 3.0 Cookbook, Third Edition: İçin 250'den fazla çözüm C# 3.0 programcıları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="992a5-201">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992a5-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="992a5-202">See also</span></span>

- [<span data-ttu-id="992a5-203">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="992a5-203">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="992a5-204">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="992a5-204">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="992a5-205">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="992a5-205">Anonymous Methods</span></span>](anonymous-methods.md)
- [<span data-ttu-id="992a5-206">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="992a5-206">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="992a5-207">Lambda ifadeleri karşılaştırma yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="992a5-207">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="992a5-208">Türü örtük olarak belirlenmiş lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="992a5-208">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="992a5-209">Visual Studio 2008 C# örnekleri (bkz: LINQ örnek sorgular dosyalar ve XQuery programı)</span><span class="sxs-lookup"><span data-stu-id="992a5-209">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="992a5-210">Yinelemeli lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="992a5-210">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
