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
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="198ca-102">Lambda ifadeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="198ca-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="198ca-103">*Lambda ifadesi* , nesne olarak kabul edilen bir kod bloğu (bir ifade veya deyim bloğu).</span><span class="sxs-lookup"><span data-stu-id="198ca-103">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="198ca-104">Yöntemlere bir bağımsız değişken olarak geçirilebilir ve Yöntem çağrıları tarafından da döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="198ca-104">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="198ca-105">Lambda ifadeleri için kapsamlı olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="198ca-105">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="198ca-106">Yürütülecek kodu, <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>gibi zaman uyumsuz yöntemlere geçirme.</span><span class="sxs-lookup"><span data-stu-id="198ca-106">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="198ca-107">[LINQ sorgu ifadeleri](../../linq/index.md)yazılıyor.</span><span class="sxs-lookup"><span data-stu-id="198ca-107">Writing [LINQ query expressions](../../linq/index.md).</span></span>

- <span data-ttu-id="198ca-108">[İfade ağaçları](../concepts/expression-trees/index.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="198ca-108">Creating [expression trees](../concepts/expression-trees/index.md).</span></span>

<span data-ttu-id="198ca-109">Lambda ifadeleri, bir temsilci olarak ya da bir temsilciye derlenen bir ifade ağacı olarak temsil edilebilir koddur.</span><span class="sxs-lookup"><span data-stu-id="198ca-109">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="198ca-110">Bir lambda ifadesinin belirli temsilci türü, parametrelerine ve dönüş değerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="198ca-110">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="198ca-111">Değer döndürmeyen lambda ifadeleri, parametre sayısına bağlı olarak belirli `Action` bir temsilciye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="198ca-111">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="198ca-112">Değer döndüren lambda ifadeleri, parametre sayısına bağlı olarak belirli `Func` bir temsilciye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="198ca-112">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="198ca-113">Örneğin, iki parametresi olan bir lambda ifadesi, ancak bir <xref:System.Action%602> temsilciye karşılık gelen hiçbir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="198ca-113">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="198ca-114">Bir parametreye sahip olan ve <xref:System.Func%602> temsilciye karşılık gelen bir değer döndüren bir lambda ifadesi.</span><span class="sxs-lookup"><span data-stu-id="198ca-114">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="198ca-115">Lambda ifadesi, Lambda `=>`parametre listesini yürütülebilir kodundan ayırmak için [lambda bildirim işlecini](../../language-reference/operators/lambda-operator.md)kullanır.</span><span class="sxs-lookup"><span data-stu-id="198ca-115">A lambda expression uses `=>`, the [lambda declaration operator](../../language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="198ca-116">Lambda ifadesi oluşturmak için, lambda işlecinin sol tarafındaki giriş parametrelerini (varsa) belirtirsiniz ve ifadeyi veya deyim bloğunu diğer tarafa yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="198ca-116">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="198ca-117">Örneğin, tek satırlık lambda ifadesi `x => x * x` adlı `x` bir parametreyi belirtir `x` ve kare değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="198ca-117">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="198ca-118">Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="198ca-118">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="198ca-119">Ayrıca, bir ifade ağaç türüne bir lambda ifadesi atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="198ca-119">You also can assign a lambda expression to an expression tree type:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="198ca-120">Ya da doğrudan yöntem bağımsız değişkeni olarak geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="198ca-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="198ca-121">Sınıfında yöntemi çağırmak için yöntem tabanlı sözdizimi kullandığınızda (LINQ to Objects ve LINQ to XML) parametre bir temsilci türüdür <xref:System.Func%602?displayProperty=nameWithType>. <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="198ca-121">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class (as you do in LINQ to Objects and LINQ to XML) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="198ca-122">Lambda ifadesi, bu temsilciyi oluşturmak için en kullanışlı yoldur.</span><span class="sxs-lookup"><span data-stu-id="198ca-122">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="198ca-123">Sınıfında yöntemini çağırdığınızda (LINQ to SQL içinde yaptığınız gibi) parametre türü bir ifade ağacı türüdür [`Expression<Func<TSource,TResult>>`.](<xref:System.Linq.Expressions.Expression%601>) <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> <xref:System.Linq.Queryable?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="198ca-123">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in LINQ to SQL) the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="198ca-124">Yine, Lambda ifadesi bu ifade ağacını oluşturmanın yalnızca çok kısa bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="198ca-124">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="198ca-125">Lambda tarafından oluşturulan nesnenin türü `Select` farklı olsa da Lambdalar, çağrıların benzer görünmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="198ca-125">The lambdas allow the `Select` calls to look similar although in fact the type of object created from the lambda is different.</span></span>

<span data-ttu-id="198ca-126">[Anonim yöntemler](anonymous-methods.md) için uygulanan tüm kısıtlamalar lambda ifadeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="198ca-126">All restrictions that apply to [anonymous methods](anonymous-methods.md) also apply to lambda expressions.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="198ca-127">İfade lambdaları</span><span class="sxs-lookup"><span data-stu-id="198ca-127">Expression lambdas</span></span>

<span data-ttu-id="198ca-128">`=>` İşlecinin sağ tarafında bir ifade olan bir lambda ifadesine bir *ifade lambda*adı verilir.</span><span class="sxs-lookup"><span data-stu-id="198ca-128">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="198ca-129">İfade lambdaları ifade [ağaçlarının](../concepts/expression-trees/index.md)yapımını yaygın olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="198ca-129">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="198ca-130">Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="198ca-130">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="198ca-131">Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="198ca-131">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="198ca-132">Boş ayraçlarla sıfır giriş parametrelerini belirtin:</span><span class="sxs-lookup"><span data-stu-id="198ca-132">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="198ca-133">İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:</span><span class="sxs-lookup"><span data-stu-id="198ca-133">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="198ca-134">Bazen derleyicinin giriş türlerini çıkarması olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="198ca-134">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="198ca-135">Aşağıdaki örnekte gösterildiği gibi türleri açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="198ca-135">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="198ca-136">Giriş parametresi türleri tamamen açık veya tümü örtük olmalıdır; Aksi halde, bir [CS0748](../../misc/cs0748.md) derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="198ca-136">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="198ca-137">Lambda ifadesinin gövdesi bir yöntem çağrısından oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="198ca-137">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="198ca-138">Ancak, SQL Server gibi .NET ortak dil çalışma zamanının bağlamı dışında değerlendirilen ifade ağaçları oluşturuyorsanız, Lambda ifadelerinde Yöntem çağrılarını kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="198ca-138">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="198ca-139">Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="198ca-139">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="198ca-140">İfade lambdaları</span><span class="sxs-lookup"><span data-stu-id="198ca-140">Statement lambdas</span></span>

<span data-ttu-id="198ca-141">Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:</span><span class="sxs-lookup"><span data-stu-id="198ca-141">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { statement; }
```

<span data-ttu-id="198ca-142">Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.</span><span class="sxs-lookup"><span data-stu-id="198ca-142">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="198ca-143">Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="198ca-143">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="198ca-144">Zaman uyumsuz Lambdalar</span><span class="sxs-lookup"><span data-stu-id="198ca-144">Async lambdas</span></span>

<span data-ttu-id="198ca-145">[Async](../../language-reference/keywords/async.md) ve [await](../../language-reference/keywords/await.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="198ca-145">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="198ca-146">Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi `ExampleMethodAsync`çağıran ve bekleden bir olay işleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="198ca-146">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="198ca-147">Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="198ca-147">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="198ca-148">Bu işleyiciyi eklemek için aşağıdaki örnekte gösterildiği `async` gibi Lambda parametre listesinden önce bir değiştirici ekleyin:</span><span class="sxs-lookup"><span data-stu-id="198ca-148">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="198ca-149">Zaman uyumsuz yöntemlerin nasıl oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="198ca-149">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="198ca-150">Lambda ifadeleri ve tanımlama grupları</span><span class="sxs-lookup"><span data-stu-id="198ca-150">Lambda expressions and tuples</span></span>

<span data-ttu-id="198ca-151">Dil, C# 7,0 ile başlayarak, [Tanımlama grupları](../../tuples.md)için yerleşik destek sağlar. C#</span><span class="sxs-lookup"><span data-stu-id="198ca-151">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="198ca-152">Bir lambda ifadesine bağımsız değişken olarak bir tanımlama grubu sağlayabilirsiniz ve lambda ifadeniz de bir tanımlama grubu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="198ca-152">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="198ca-153">Bazı durumlarda, C# derleyici demet bileşenleri türlerini belirlemekte tür çıkarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="198ca-153">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="198ca-154">Bir tanımlama grubu, bileşenlerinin virgülle ayrılmış bir listesini parantez içine alarak tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="198ca-154">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="198ca-155">Aşağıdaki örnek, her bir değeri iki katına çıkarır ve çarpma 'un sonucunu içeren üç bileşeni olan bir tanımlama grubu döndüren bir lambda ifadesine bir dizi sayıyı geçirmek için üç bileşeni olan tanımlama grubunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="198ca-155">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="198ca-156">Normalde, bir tanımlama grubu alanları, `Item1` `Item2`, vb. olarak adlandırılır. Ancak, aşağıdaki örnekte olduğu gibi adlandırılmış bileşenlerle bir tanımlama grubu tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="198ca-156">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="198ca-157">Tanımlama grupları hakkında C# daha fazla bilgi için bkz [ C# . demet türleri](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="198ca-157">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="198ca-158">Standart sorgu işleçleri ile Lambdalar</span><span class="sxs-lookup"><span data-stu-id="198ca-158">Lambdas with the standard query operators</span></span>

<span data-ttu-id="198ca-159">Diğer uygulamalar arasında LINQ to Objects, türü <xref:System.Func%601> Genel Temsilciler ailesinden olan bir giriş parametresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="198ca-159">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="198ca-160">Bu temsilciler, giriş parametrelerinin sayısını ve türünü ve temsilcinin dönüş türünü tanımlamak için tür parametreleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="198ca-160">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="198ca-161">`Func`Temsilciler, bir kaynak veri kümesindeki her öğeye uygulanan Kullanıcı tanımlı ifadeleri kapsüllemek için çok yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="198ca-161">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="198ca-162">Örneğin, <xref:System.Func%602> temsilci türünü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="198ca-162">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="198ca-163">Temsilci, giriş parametresi `Func<int, bool>` `int` olan ve `bool` dönüş değeri olan bir örnek olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="198ca-163">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="198ca-164">Dönüş değeri her zaman son tür parametresinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="198ca-164">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="198ca-165">Örneğin `Func<int, string, bool>` , iki giriş parametresi olan bir temsilciyi, `int` ve `string`ve dönüş türünü `bool`tanımlar.</span><span class="sxs-lookup"><span data-stu-id="198ca-165">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="198ca-166">Aşağıdaki `Func` temsilci çağrıldığında, giriş parametresinin beş ' a eşit olup olmadığını belirten Boole değeri döndürür:</span><span class="sxs-lookup"><span data-stu-id="198ca-166">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="198ca-167">Bağımsız değişken türü bir <xref:System.Linq.Expressions.Expression%601>olduğunda bir lambda ifadesi de sağlayabilirsiniz, örneğin, <xref:System.Linq.Queryable> tür içinde tanımlanan standart sorgu işleçleri.</span><span class="sxs-lookup"><span data-stu-id="198ca-167">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="198ca-168">Bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişken belirttiğinizde, lambda bir ifade ağacına derlenir.</span><span class="sxs-lookup"><span data-stu-id="198ca-168">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="198ca-169">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> standart sorgu işlecini kullanır:</span><span class="sxs-lookup"><span data-stu-id="198ca-169">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="198ca-170">Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="198ca-170">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="198ca-171">Bu belirli lambda ifadesi, ikiye bölünen 1`n`' in geri kalanı olduğunda bu tamsayıları () sayar.</span><span class="sxs-lookup"><span data-stu-id="198ca-171">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="198ca-172">Aşağıdaki örnek, koşulu karşılamayan dizideki ilk sayı olduğundan, 9 ' `numbers` dan önce gelen dizide bulunan tüm öğeleri içeren bir dizi üretir:</span><span class="sxs-lookup"><span data-stu-id="198ca-172">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="198ca-173">Aşağıdaki örnek, birden çok giriş parametresini parantez içine alarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="198ca-173">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="198ca-174">Yöntemi, değeri dizideki sıra konumundan daha az `numbers` olan bir sayı ile karşılaşana kadar dizideki tüm öğeleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="198ca-174">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="198ca-175">Lambda ifadelerinde tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="198ca-175">Type inference in lambda expressions</span></span>

<span data-ttu-id="198ca-176">Lambda yazarken genellikle giriş parametreleri için bir tür belirtmeniz gerekmez, derleyici lambda gövdesine, parametre türlerine ve C# dil belirtiminde açıklanan diğer etkenlere göre türü çıkarsabilir.</span><span class="sxs-lookup"><span data-stu-id="198ca-176">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="198ca-177">Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür.</span><span class="sxs-lookup"><span data-stu-id="198ca-177">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="198ca-178">Bir `IEnumerable<Customer>`sorgulama yapıyorsanız, giriş değişkeni bir `Customer` nesne olarak algılanır ve bu, yöntemlerine ve özelliklerine erişiminiz olduğu anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="198ca-178">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="198ca-179">Lambdalar için tür çıkarımı için genel kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="198ca-179">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="198ca-180">Lambda temsilci türüyle aynı sayıda parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="198ca-180">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="198ca-181">Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="198ca-181">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="198ca-182">Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="198ca-182">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="198ca-183">Ortak tür sisteminin hiçbir "lambda ifadesi" kavramı olmadığından, lambda ifadelerinin bir tür olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="198ca-183">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="198ca-184">Ancak, bazen bir lambda ifadesinin "tür" i resmi olarak konuşmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="198ca-184">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="198ca-185">Bu durumlarda tür, lambda ifadesinin dönüştürüldüğü temsilci türüne veya <xref:System.Linq.Expressions.Expression> türüne başvurur.</span><span class="sxs-lookup"><span data-stu-id="198ca-185">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="198ca-186">Lambda ifadelerinde dış değişkenlerin ve değişken kapsamının yakalanması</span><span class="sxs-lookup"><span data-stu-id="198ca-186">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="198ca-187">Lambdalar, lambda ifadesini tanımlayan yöntemde veya lambda ifadesini içeren türdeki kapsamda kapsamda olan *dış değişkenlere* (bkz. [Anonim yöntemler](anonymous-methods.md)) başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="198ca-187">Lambdas can refer to *outer variables* (see [Anonymous methods](anonymous-methods.md)) that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="198ca-188">Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="198ca-188">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="198ca-189">Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="198ca-189">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="198ca-190">Aşağıdaki örnek bu kuralları gösterir:</span><span class="sxs-lookup"><span data-stu-id="198ca-190">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="198ca-191">Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="198ca-191">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="198ca-192">Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.</span><span class="sxs-lookup"><span data-stu-id="198ca-192">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="198ca-193">Bir lambda ifadesi içinde tanıtılan değişkenler kapsayan yöntemde görünmez.</span><span class="sxs-lookup"><span data-stu-id="198ca-193">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="198ca-194">Lambda ifadesi kapsayan yöntemden bir [ın](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresini doğrudan yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="198ca-194">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="198ca-195">Lambda ifadesindeki bir [dönüş](../../language-reference/keywords/return.md) deyimi kapsayan metodun dönüşmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="198ca-195">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="198ca-196">Bir lambda ifadesi, bu sıçrama deyiminin hedefi lambda ifade bloğunun dışındaysa bir [goto](../../language-reference/keywords/goto.md), [Break](../../language-reference/keywords/break.md)veya [Continue](../../language-reference/keywords/continue.md) deyimi içeremez.</span><span class="sxs-lookup"><span data-stu-id="198ca-196">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="198ca-197">Ayrıca, hedef bloğun içindeyse lambda ifade bloğunun dışında bir sıçrama deyimine sahip olmak için bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="198ca-197">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="198ca-198">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="198ca-198">C# language specification</span></span>

<span data-ttu-id="198ca-199">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="198ca-199">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="198ca-200">Öne çıkan kitap bölümü</span><span class="sxs-lookup"><span data-stu-id="198ca-200">Featured book chapter</span></span>

<span data-ttu-id="198ca-201">3,0 tanımlama kitabı, üçüncü sürüm 'de [ C# [Temsilciler, olaylar ve lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) : 3,0 programcıları için C# 250 'den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="198ca-201">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198ca-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="198ca-202">See also</span></span>

- [<span data-ttu-id="198ca-203">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="198ca-203">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="198ca-204">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="198ca-204">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="198ca-205">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="198ca-205">Anonymous Methods</span></span>](anonymous-methods.md)
- [<span data-ttu-id="198ca-206">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="198ca-206">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="198ca-207">Yerel işlevler lambda ifadeleriyle karşılaştırılır</span><span class="sxs-lookup"><span data-stu-id="198ca-207">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="198ca-208">Örtük olarak yazılan lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="198ca-208">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="198ca-209">Visual Studio 2008 C# örnekleri (bkz. LINQ örnek sorguları dosyaları ve XQuery programı)</span><span class="sxs-lookup"><span data-stu-id="198ca-209">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="198ca-210">Özyinelemeli lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="198ca-210">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
