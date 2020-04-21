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
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="b2cf9-102">Lambda ifadeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b2cf9-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="b2cf9-103">*Lambda ifadesi* aşağıdaki iki formdan herhangi birinin ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-103">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="b2cf9-104">[İfade lambda](#expression-lambdas) kendi gövdesi olarak bir ifade vardır:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-104">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="b2cf9-105">[Beyanı lambda](#statement-lambdas) gövdesi olarak bir ifade bloğu vardır:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-105">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="b2cf9-106">[Lambda'nın `=>` ](../../language-reference/operators/lambda-operator.md) parametre listesini gövdesinden ayırmak için lambda bildirim operatörünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-106">Use the [lambda declaration operator `=>`](../../language-reference/operators/lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="b2cf9-107">Lambda ifadesi oluşturmak için lambda işlecinin sol tarafında giriş parametreleri (varsa) ve diğer tarafta bir ifade veya deyim bloğu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-107">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="b2cf9-108">Herhangi bir lambda ifadesi [bir temsilci](../../language-reference/builtin-types/reference-types.md#the-delegate-type) türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-108">Any lambda expression can be converted to a [delegate](../../language-reference/builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="b2cf9-109">Lambda ifadesinin dönüştürülebileceği temsilci türü, parametrelerinin ve geri dönüş değerinin türlerine göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-109">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="b2cf9-110">Lambda ifadesi bir değer döndürmüyorsa, `Action` temsilci türlerinden birine dönüştürülebilir; aksi takdirde, `Func` temsilci türlerinden birine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-110">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="b2cf9-111">Örneğin, iki parametresi olan ve hiçbir değer döndürmeyen bir <xref:System.Action%602> lambda ifadesi temsilciye dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-111">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="b2cf9-112">Bir parametresi olan ve bir değer döndüren bir <xref:System.Func%602> lambda ifadesi temsilciye dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-112">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="b2cf9-113">Aşağıdaki örnekte, adlandırılmış `x => x * x` `x` bir parametreyi belirten ve `x` kare değerini döndüren lambda ifadesi, temsilci türündeki bir değişkene atanır:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-113">In the following example, the lambda expression `x => x * x`, which specifies a parameter that’s named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="b2cf9-114">İfade lambdas da [ifade ağacı](../concepts/expression-trees/index.md) türlerine dönüştürülebilir, aşağıdaki örnekte görüldüğü gibi:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-114">Expression lambdas can also be converted to the [expression tree](../concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="b2cf9-115">Lambda ifadelerini, örneğin arka planda yürütülmesi gereken kodu geçirmek için <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> yönteme bir argüman olarak, temsilci türleri veya ifade ağaçları örnekleri gerektiren herhangi bir kodda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-115">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="b2cf9-116">Aşağıdaki örnekte görüldüğü [gibi, C#'a LINQ](../../linq/index.md)yazarken lambda ifadelerini de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-116">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="b2cf9-117">Sınıftaki <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> yöntemi çağırmak için yöntem tabanlı sözdizimini kullandığınızda, örneğin LINQ'dan Nesnelere ve LINQ'dan XML'e parametre bir temsilci türüdür. <xref:System.Func%602?displayProperty=nameWithType> <xref:System.Linq.Enumerable?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b2cf9-117">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b2cf9-118">Sınıftaki <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> yöntemi, örneğin LINQ'dan SQL'e çağırdığınızda, parametre türü bir ifade ağacı türüdür. [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) <xref:System.Linq.Queryable?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b2cf9-118">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="b2cf9-119">Her iki durumda da parametre değerini belirtmek için aynı lambda ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-119">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="b2cf9-120">Aslında lambdas oluşturulan nesnelerin türü farklı olmasına rağmen bu iki `Select` çağrı benzer görünmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-120">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="b2cf9-121">İfade lambdas</span><span class="sxs-lookup"><span data-stu-id="b2cf9-121">Expression lambdas</span></span>

<span data-ttu-id="b2cf9-122">Operatörün `=>` sağ tarafında bir ifade ile lambda ifade bir *ifade lambda*denir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-122">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="b2cf9-123">İfade lambdas [ifade ağaçlarının](../concepts/expression-trees/index.md)yapımında yaygın olarak kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-123">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="b2cf9-124">Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="b2cf9-125">Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="b2cf9-126">Boş ayraçlarla sıfır giriş parametrelerini belirtin:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-126">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="b2cf9-127">İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="b2cf9-128">Bazen derleyicinin giriş türlerini çıkarması imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-128">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="b2cf9-129">Türleri aşağıdaki örnekte açıkça gösterildiği gibi belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-129">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="b2cf9-130">Giriş parametresi türlerinin tümü açık veya tamamen örtülü olmalıdır; aksi takdirde, bir [CS0748](../../misc/cs0748.md) derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-130">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="b2cf9-131">Bir ifade lambda gövdesi bir yöntem çağrı oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-131">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="b2cf9-132">Ancak, SQL Server'da olduğu gibi .NET ortak dil çalışma zamanı bağlamı dışında değerlendirilen ifade ağaçları oluşturuyorsanız, lambda ifadelerinde yöntem çağrıları kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-132">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="b2cf9-133">Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-133">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="b2cf9-134">Açıklama lambdas</span><span class="sxs-lookup"><span data-stu-id="b2cf9-134">Statement lambdas</span></span>

<span data-ttu-id="b2cf9-135">Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="b2cf9-136">Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="b2cf9-137">İfade lambdas ifade ağaçları oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-137">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="b2cf9-138">Async lambdas</span><span class="sxs-lookup"><span data-stu-id="b2cf9-138">Async lambdas</span></span>

<span data-ttu-id="b2cf9-139">Kolayca [async](../../language-reference/keywords/async.md) kullanarak asynchronous işleme dahil lambda ifadeler ve ifadeler oluşturabilirsiniz ve anahtar kelimeleri [bekliyor.](../../language-reference/operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="b2cf9-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/operators/await.md) keywords.</span></span> <span data-ttu-id="b2cf9-140">Örneğin, aşağıdaki Windows Forms örneği çağıran ve bir async yöntemi ni `ExampleMethodAsync`bekleyen bir olay işleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-140">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="b2cf9-141">Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-141">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="b2cf9-142">Bu işleyiciyi eklemek `async` için, aşağıdaki örnekte görüldüğü gibi lambda parametre listesinden önce bir değiştirici ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-142">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="b2cf9-143">Async yöntemlerinin nasıl oluşturulup kullanılacağı hakkında daha fazla bilgi için [async ile Asynchronous Programming'e](../concepts/async/index.md)bakın ve bekleyin.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-143">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="b2cf9-144">Lambda ifadeler ve tuples</span><span class="sxs-lookup"><span data-stu-id="b2cf9-144">Lambda expressions and tuples</span></span>

<span data-ttu-id="b2cf9-145">C# 7.0 ile başlayarak, C# dili [tuples](../../tuples.md)için yerleşik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-145">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="b2cf9-146">Bir lambda ifade için bir argüman olarak bir tuple sağlayabilir ve lambda ifade de bir tuple döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-146">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="b2cf9-147">Bazı durumlarda, C# derleyicisi tuple bileşenlerinin türlerini belirlemek için tür çıkarımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-147">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="b2cf9-148">Bileşenlerinin virgülle sınırlı bir listesini parantez içinde ekleyerek bir tuple tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-148">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="b2cf9-149">Aşağıdaki örnekte, bir dizi sayıyı lambda ifadesine geçirmek için üç bileşenden oluşan tuple kullanılır, bu da her değeri ikikatına çıkar ve çarpmaların sonucunu içeren üç bileşenle bir tuple döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-149">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="b2cf9-150">Normalde, bir tuple alanları , , `Item1` `Item2`vb adlandırılır. Ancak, aşağıdaki örnekte olduğu gibi, adlandırılmış bileşenlerle bir tuple tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-150">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="b2cf9-151">C# tuples hakkında daha fazla bilgi için [C# tuple türlerine](../../tuples.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-151">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="b2cf9-152">Standart sorgu operatörleri ile Lambdas</span><span class="sxs-lookup"><span data-stu-id="b2cf9-152">Lambdas with the standard query operators</span></span>

<span data-ttu-id="b2cf9-153">LinQ to Objects, diğer uygulamaların yanı sıra, türü genel <xref:System.Func%601> temsilciler ailesinden biri olan bir giriş parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-153">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="b2cf9-154">Bu temsilciler, giriş parametrelerinin sayısını ve türünü ve temsilcinin dönüş türünü tanımlamak için tür parametrelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-154">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="b2cf9-155">`Func`temsilciler, kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadeleri kapsüllemek için çok yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-155">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="b2cf9-156">Örneğin, <xref:System.Func%602> temsilci türünü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-156">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="b2cf9-157">Temsilci, giriş parametresi olan `Func<int, bool>` ve `int` `bool` iade değeri olan bir örnek olarak anında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-157">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="b2cf9-158">Dönüş değeri her zaman son tür parametresinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-158">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="b2cf9-159">Örneğin, `Func<int, string, bool>` iki giriş paramı `int` ve `string`, bir return türü `bool`olan bir temsilci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-159">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="b2cf9-160">Aşağıdaki `Func` temsilci, çağrıldığı zaman, giriş parametresinin beşe eşit olup olmadığını gösteren Boolean değerini döndürür:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-160">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="b2cf9-161">Bağımsız değişken türü <xref:System.Linq.Expressions.Expression%601>, örneğin <xref:System.Linq.Queryable> türünde tanımlanan standart sorgu işleçlerinde bir lambda ifadesi de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-161">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="b2cf9-162">Bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişken belirttiğiniz zaman, lambda bir ifade ağacına derlenir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-162">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="b2cf9-163">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Count%2A> standart sorgu işleci kullanır:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-163">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="b2cf9-164">Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-164">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="b2cf9-165">Bu özel lambda ifadesi, ikiye`n`bölündüğünde 1'in geri kalanı olan tamsayılar sayar.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-165">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="b2cf9-166">Aşağıdaki örnek, `numbers` dizideki 9'dan önceki tüm öğeleri içeren bir dizi üretir, çünkü bu, dizideki koşula uymayan ilk sayıdır:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-166">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="b2cf9-167">Aşağıdaki örnekte, birden çok giriş parametresini parantez içine ekleyerek belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-167">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="b2cf9-168">Yöntem, değeri dizideki `numbers` ordinal konumundan daha az olan bir sayıyla karşılaşıncaya kadar dizideki tüm öğeleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-168">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="b2cf9-169">Lambda ifadelerinde tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="b2cf9-169">Type inference in lambda expressions</span></span>

<span data-ttu-id="b2cf9-170">Lambdas yazarken, genellikle giriş parametreleri için bir tür belirtmeniz gerekmemektedir, çünkü derleyici lambda gövdesine, parametre türlerine ve C# dil belirtiminde açıklandığı gibi diğer etkenlere göre türü çıkarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-170">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="b2cf9-171">Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-171">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="b2cf9-172">Bir `IEnumerable<Customer>`, giriş değişkenini sorgulıyorsanız, giriş değişkeninin bir `Customer` nesne olduğu ortaya çıkarılır, bu da onun yöntemlerine ve özelliklerine erişiminiz olduğu anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-172">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="b2cf9-173">Lambdas için tip çıkarım için genel kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-173">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="b2cf9-174">Lambda temsilci türüyle aynı sayıda parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-174">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="b2cf9-175">Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-175">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="b2cf9-176">Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-176">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="b2cf9-177">Ortak tür sistemi "lambda ifade" içsel kavramı vardır, çünkü lambda ifadelerinin kendi içinde bir türü olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-177">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="b2cf9-178">Ancak, bazen bir lambda ifade "türü" gayri konuşmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-178">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="b2cf9-179">Bu gibi durumlarda tür, lambda <xref:System.Linq.Expressions.Expression> ifadesinin dönüştürüldüğü temsilci türü veya türü ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-179">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="b2cf9-180">Lambda ifadelerinde dış değişkenlerin ve değişken kapsamın yakalanması</span><span class="sxs-lookup"><span data-stu-id="b2cf9-180">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="b2cf9-181">Lambdas dış *değişkenlere*başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-181">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="b2cf9-182">Lambda ifadesini tanımlayan yöntemde veya lambda ifadesini içeren türde kapsamda olan değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-182">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="b2cf9-183">Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-183">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="b2cf9-184">Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-184">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="b2cf9-185">Aşağıdaki örnek bu kuralları gösterir:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-185">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="b2cf9-186">Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="b2cf9-186">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="b2cf9-187">Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-187">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="b2cf9-188">Lambda ifadesi içinde tanıtılan değişkenler çevre yönteminde görünmez.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-188">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="b2cf9-189">Lambda ifadesi, çevreleyen yöntemden doğrudan bir [in](../../language-reference/keywords/in-parameter-modifier.md) [,](../../language-reference/keywords/ref.md)ref veya [out](../../language-reference/keywords/out-parameter-modifier.md) parametresini yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-189">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="b2cf9-190">Lambda ifadesindeki [bir iade](../../language-reference/keywords/return.md) deyimi, çevreleyen yöntemin geri dönmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-190">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="b2cf9-191">Bir lambda ifadesi [goto](../../language-reference/keywords/goto.md)içeremez , [break](../../language-reference/keywords/break.md), veya bu atlama deyiminin hedefi lambda ifade bloğu dışında ise deyimi [devam.](../../language-reference/keywords/continue.md)</span><span class="sxs-lookup"><span data-stu-id="b2cf9-191">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="b2cf9-192">Hedef bloğun içindeyse lambda ifade bloğunun dışında bir atlama deyimi olması da bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-192">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b2cf9-193">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b2cf9-193">C# language specification</span></span>

<span data-ttu-id="b2cf9-194">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-194">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="b2cf9-195">Seçme kitap bölümü</span><span class="sxs-lookup"><span data-stu-id="b2cf9-195">Featured book chapter</span></span>

<span data-ttu-id="b2cf9-196">C# 3.0 Yemek Kitabında [Delegeler, Etkinlikler ve Lambda İfadeleri,](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [Üçüncü Baskı: C# 3.0 programcıları için 250'den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="b2cf9-196">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2cf9-197">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2cf9-197">See also</span></span>

- [<span data-ttu-id="b2cf9-198">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b2cf9-198">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b2cf9-199">LINQ (Dil-Entegre Sorgu)</span><span class="sxs-lookup"><span data-stu-id="b2cf9-199">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="b2cf9-200">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="b2cf9-200">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="b2cf9-201">Lambda ifadeleri ile karşılaştırıldığında yerel fonksiyonlar</span><span class="sxs-lookup"><span data-stu-id="b2cf9-201">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="b2cf9-202">Örtülü olarak yazılan lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b2cf9-202">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="b2cf9-203">Visual Studio 2008 C# Örnekleri (bkz. LINQ Örnek Sorgular dosyaları ve XQuery programı)</span><span class="sxs-lookup"><span data-stu-id="b2cf9-203">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="b2cf9-204">Özyinelemeli lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b2cf9-204">Recursive lambda expressions</span></span>](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)
