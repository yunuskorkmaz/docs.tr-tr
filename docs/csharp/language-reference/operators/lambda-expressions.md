---
title: Lambda ifadeleri-C# başvurusu
description: Lambda ifadeleri hakkında bilgi edinin. Gövdesi olarak bir ifadesi olan ifade lambdaları veya gövdesi olarak deyim bloğu olan deyim Lambdalar vardır.
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 7f80c1a5d9136609935b25b5cce3792e80b9ac94
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536450"
---
# <a name="lambda-expressions-c-reference"></a><span data-ttu-id="22370-104">Lambda ifadeleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="22370-104">Lambda expressions (C# reference)</span></span>

<span data-ttu-id="22370-105">*Lambda ifadesi* aşağıdaki iki formdan herhangi birinin bir ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="22370-105">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="22370-106">Gövdesi olarak bir ifadeye sahip olan [ifade lambda](#expression-lambdas) :</span><span class="sxs-lookup"><span data-stu-id="22370-106">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="22370-107">Gövdesi olarak bir ifade bloğuna sahip olan [ifade lambda](#statement-lambdas) :</span><span class="sxs-lookup"><span data-stu-id="22370-107">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="22370-108">Lambda parametre listesini gövdesinden ayırmak için [lambda bildirimi işlecini `=>` ](lambda-operator.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="22370-108">Use the [lambda declaration operator `=>`](lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="22370-109">Lambda ifadesi oluşturmak için, lambda işlecinin sol tarafında (varsa) giriş parametrelerini ve diğer tarafta bir ifade ya da deyim bloğunu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22370-109">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="22370-110">Herhangi bir lambda ifadesi, bir [temsilci](../builtin-types/reference-types.md#the-delegate-type) türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="22370-110">Any lambda expression can be converted to a [delegate](../builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="22370-111">Lambda ifadesinin dönüştürülebileceği temsilci türü, parametrelerinin ve dönüş değerinin türlerine göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="22370-111">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="22370-112">Lambda ifadesi bir değer döndürmezse, `Action` temsilci türlerinden birine dönüştürülebilir; Aksi takdirde, `Func` temsilci türlerinden birine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="22370-112">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="22370-113">Örneğin, iki parametresi olan ve değer döndüren bir lambda ifadesi bir <xref:System.Action%602> temsilciye dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="22370-113">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="22370-114">Bir parametreye sahip olan ve bir değer döndüren bir lambda ifadesi, bir <xref:System.Func%602> temsilciye dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="22370-114">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="22370-115">Aşağıdaki örnekte, `x => x * x` adlı ve kare değeri döndüren bir parametreyi belirten lambda ifadesi, `x` `x` bir temsilci türü değişkenine atanır:</span><span class="sxs-lookup"><span data-stu-id="22370-115">In the following example, the lambda expression `x => x * x`, which specifies a parameter that's named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](snippets/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="22370-116">Aşağıdaki örnekte gösterildiği gibi, ifade lambdaları da [ifade ağacı](../../programming-guide/concepts/expression-trees/index.md) türlerine dönüştürülebilir:</span><span class="sxs-lookup"><span data-stu-id="22370-116">Expression lambdas can also be converted to the [expression tree](../../programming-guide/concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](snippets/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="22370-117">Lambda ifadelerini, örneğin, <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> arka planda yürütülmesi gereken kodu geçirmek için yönteme bir bağımsız değişken olarak temsilci türleri veya ifade ağaçları örnekleri gerektiren herhangi bir kodda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22370-117">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="22370-118">Aşağıdaki örnekte gösterildiği gibi, [C# ' de LINQ](../../linq/index.md)yazdığınızda Lambda ifadelerini de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="22370-118">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](snippets/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="22370-119">Sınıfında yöntemi çağırmak için yöntem tabanlı sözdizimi kullandığınızda ( <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable?displayProperty=nameWithType> örneğin, LINQ to Objects ve LINQ to XML, parametresi bir temsilci türüdür <xref:System.Func%602?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="22370-119">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="22370-120"><xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>Sınıfında yöntemini çağırdığınızda <xref:System.Linq.Queryable?displayProperty=nameWithType> , örneğin LINQ to SQL, parametre türü bir ifade ağacı türüdür [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) .</span><span class="sxs-lookup"><span data-stu-id="22370-120">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="22370-121">Her iki durumda da, parametre değerini belirtmek için aynı lambda ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22370-121">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="22370-122">`Select`Aslında Lambdalar tarafından oluşturulan nesnelerin türü farklı olsa da, bu iki çağrının benzer görünmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="22370-122">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="22370-123">İfade lambdaları</span><span class="sxs-lookup"><span data-stu-id="22370-123">Expression lambdas</span></span>

<span data-ttu-id="22370-124">İşlecinin sağ tarafında bir ifade olan bir lambda ifadesine bir `=>` *ifade lambda*adı verilir.</span><span class="sxs-lookup"><span data-stu-id="22370-124">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="22370-125">İfade lambdaları ifade [ağaçlarının](../../programming-guide/concepts/expression-trees/index.md)yapımını yaygın olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="22370-125">Expression lambdas are used extensively in the construction of [expression trees](../../programming-guide/concepts/expression-trees/index.md).</span></span> <span data-ttu-id="22370-126">Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="22370-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="22370-127">Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="22370-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="22370-128">Boş ayraçlarla sıfır giriş parametrelerini belirtin:</span><span class="sxs-lookup"><span data-stu-id="22370-128">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="22370-129">İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:</span><span class="sxs-lookup"><span data-stu-id="22370-129">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="22370-130">Bazen derleyicinin giriş türlerini çıkarması olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="22370-130">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="22370-131">Aşağıdaki örnekte gösterildiği gibi türleri açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="22370-131">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="22370-132">Giriş parametresi türleri tamamen açık veya tümü örtük olmalıdır; Aksi halde, bir [CS0748](../../misc/cs0748.md) derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="22370-132">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="22370-133">Lambda ifadesinin gövdesi bir yöntem çağrısından oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="22370-133">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="22370-134">Ancak, SQL Server gibi .NET ortak dil çalışma zamanının bağlamı dışında değerlendirilen ifade ağaçları oluşturuyorsanız, Lambda ifadelerinde Yöntem çağrılarını kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="22370-134">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="22370-135">Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="22370-135">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="22370-136">İfade lambdaları</span><span class="sxs-lookup"><span data-stu-id="22370-136">Statement lambdas</span></span>

<span data-ttu-id="22370-137">Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:</span><span class="sxs-lookup"><span data-stu-id="22370-137">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="22370-138">Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.</span><span class="sxs-lookup"><span data-stu-id="22370-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="22370-139">Deyim lambdaları ifade ağaçları oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="22370-139">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="22370-140">Zaman uyumsuz Lambdalar</span><span class="sxs-lookup"><span data-stu-id="22370-140">Async lambdas</span></span>

<span data-ttu-id="22370-141">[Async](../keywords/async.md) ve [await](await.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22370-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../keywords/async.md) and [await](await.md) keywords.</span></span> <span data-ttu-id="22370-142">Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi çağıran ve bekleden bir olay işleyicisi içerir `ExampleMethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="22370-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="22370-143">Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22370-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="22370-144">Bu işleyiciyi eklemek için `async` Aşağıdaki örnekte gösterildiği gibi Lambda parametre listesinden önce bir değiştirici ekleyin:</span><span class="sxs-lookup"><span data-stu-id="22370-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="22370-145">Zaman uyumsuz yöntemlerin nasıl oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="22370-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="22370-146">Lambda ifadeleri ve tanımlama grupları</span><span class="sxs-lookup"><span data-stu-id="22370-146">Lambda expressions and tuples</span></span>

<span data-ttu-id="22370-147">C# 7,0 ile başlayarak, C# dili [Tanımlama grupları](../builtin-types/value-tuples.md)için yerleşik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="22370-147">Starting with C# 7.0, the C# language provides built-in support for [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="22370-148">Bir lambda ifadesine bağımsız değişken olarak bir tanımlama grubu sağlayabilirsiniz ve lambda ifadeniz de bir tanımlama grubu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="22370-148">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="22370-149">Bazı durumlarda, C# derleyicisi demet bileşenleri türlerini belirlemede tür çıkarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="22370-149">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="22370-150">Bir tanımlama grubu, bileşenlerinin virgülle ayrılmış bir listesini parantez içine alarak tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="22370-150">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="22370-151">Aşağıdaki örnek, her bir değeri iki katına çıkarır ve çarpma 'un sonucunu içeren üç bileşeni olan bir tanımlama grubu döndüren bir lambda ifadesine bir dizi sayıyı geçirmek için üç bileşeni olan tanımlama grubunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="22370-151">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="22370-152">Normalde, bir tanımlama grubu alanları, `Item1` `Item2` , vb. olarak adlandırılır. Ancak, aşağıdaki örnekte olduğu gibi adlandırılmış bileşenlerle bir tanımlama grubu tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22370-152">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="22370-153">C# tanımlama bilgileri hakkında daha fazla bilgi için bkz. [demet türleri](../../language-reference/builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="22370-153">For more information about C# tuples, see [Tuple types](../../language-reference/builtin-types/value-tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="22370-154">Standart sorgu işleçleri ile Lambdalar</span><span class="sxs-lookup"><span data-stu-id="22370-154">Lambdas with the standard query operators</span></span>

<span data-ttu-id="22370-155">Diğer uygulamalar arasında LINQ to Objects, türü genel Temsilciler ailesinden olan bir giriş parametresine sahiptir <xref:System.Func%601> .</span><span class="sxs-lookup"><span data-stu-id="22370-155">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="22370-156">Bu temsilciler, giriş parametrelerinin sayısını ve türünü ve temsilcinin dönüş türünü tanımlamak için tür parametreleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="22370-156">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="22370-157">`Func` Temsilciler, bir kaynak veri kümesindeki her öğeye uygulanan Kullanıcı tanımlı ifadeleri kapsüllemek için çok yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="22370-157">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="22370-158">Örneğin, temsilci türünü göz önünde bulundurun <xref:System.Func%602> :</span><span class="sxs-lookup"><span data-stu-id="22370-158">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="22370-159">Temsilci, `Func<int, bool>` `int` giriş parametresi olan ve dönüş değeri olan bir örnek olarak oluşturulabilir `bool` .</span><span class="sxs-lookup"><span data-stu-id="22370-159">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="22370-160">Dönüş değeri her zaman son tür parametresinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="22370-160">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="22370-161">Örneğin, `Func<int, string, bool>` iki giriş parametresi olan bir temsilciyi, `int` ve `string` ve dönüş türünü tanımlar `bool` .</span><span class="sxs-lookup"><span data-stu-id="22370-161">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="22370-162">Aşağıdaki `Func` temsilci çağrıldığında, giriş parametresinin beş ' a eşit olup olmadığını belirten Boole değeri döndürür:</span><span class="sxs-lookup"><span data-stu-id="22370-162">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="22370-163">Bağımsız değişken türü bir olduğunda bir lambda ifadesi de sağlayabilirsiniz <xref:System.Linq.Expressions.Expression%601> , örneğin, tür içinde tanımlanan standart sorgu işleçleri <xref:System.Linq.Queryable> .</span><span class="sxs-lookup"><span data-stu-id="22370-163">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="22370-164">Bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişken belirttiğinizde, lambda bir ifade ağacına derlenir.</span><span class="sxs-lookup"><span data-stu-id="22370-164">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="22370-165">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> Standart sorgu işlecini kullanır:</span><span class="sxs-lookup"><span data-stu-id="22370-165">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="22370-166">Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22370-166">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="22370-167">Bu belirli lambda ifadesi `n` , ikiye bölünen 1 ' in geri kalanı olduğunda bu tamsayıları () sayar.</span><span class="sxs-lookup"><span data-stu-id="22370-167">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="22370-168">Aşağıdaki örnek, `numbers` koşulu karşılamayan dizideki ilk sayı olduğundan, 9 ' dan önce gelen dizide bulunan tüm öğeleri içeren bir dizi üretir:</span><span class="sxs-lookup"><span data-stu-id="22370-168">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="22370-169">Aşağıdaki örnek, birden çok giriş parametresini parantez içine alarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="22370-169">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="22370-170">Yöntemi, `numbers` değeri dizideki sıra konumundan daha az olan bir sayı ile karşılaşana kadar dizideki tüm öğeleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="22370-170">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="22370-171">Lambda ifadelerinde tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="22370-171">Type inference in lambda expressions</span></span>

<span data-ttu-id="22370-172">Lambda yazarken genellikle giriş parametreleri için bir tür belirtmeniz gerekmez, derleyici lambda gövdesine, parametre türlerine ve C# dil belirtiminde açıklanan diğer etkenlere göre türü çıkarsabilir.</span><span class="sxs-lookup"><span data-stu-id="22370-172">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="22370-173">Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür.</span><span class="sxs-lookup"><span data-stu-id="22370-173">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="22370-174">Bir sorgulama yapıyorsanız `IEnumerable<Customer>` , giriş değişkeni bir nesne olarak algılanır `Customer` ve bu, yöntemlerine ve özelliklerine erişiminiz olduğu anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="22370-174">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="22370-175">Lambdalar için tür çıkarımı için genel kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="22370-175">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="22370-176">Lambda temsilci türüyle aynı sayıda parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="22370-176">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="22370-177">Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22370-177">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="22370-178">Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22370-178">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="22370-179">Ortak tür sisteminin hiçbir "lambda ifadesi" kavramı olmadığından, lambda ifadelerinin bir tür olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="22370-179">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="22370-180">Ancak, bazen bir lambda ifadesinin "tür" i resmi olarak konuşmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="22370-180">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="22370-181">Bu durumlarda tür, <xref:System.Linq.Expressions.Expression> lambda ifadesinin dönüştürüldüğü temsilci türüne veya türüne başvurur.</span><span class="sxs-lookup"><span data-stu-id="22370-181">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="22370-182">Lambda ifadelerinde dış değişkenlerin ve değişken kapsamının yakalanması</span><span class="sxs-lookup"><span data-stu-id="22370-182">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="22370-183">Lambdalar, *dış değişkenlere*başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="22370-183">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="22370-184">Bunlar, lambda ifadesini tanımlayan yöntemde veya lambda ifadesini içeren türde kapsamda kapsam içinde olan değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="22370-184">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="22370-185">Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="22370-185">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="22370-186">Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="22370-186">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="22370-187">Aşağıdaki örnek bu kuralları gösterir:</span><span class="sxs-lookup"><span data-stu-id="22370-187">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](snippets/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="22370-188">Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="22370-188">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="22370-189">Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.</span><span class="sxs-lookup"><span data-stu-id="22370-189">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="22370-190">Bir lambda ifadesi içinde tanıtılan değişkenler kapsayan yöntemde görünmez.</span><span class="sxs-lookup"><span data-stu-id="22370-190">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="22370-191">Lambda ifadesi kapsayan yöntemden bir [ın](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md)veya [Out](../keywords/out-parameter-modifier.md) parametresini doğrudan yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="22370-191">A lambda expression cannot directly capture an [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md), or [out](../keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="22370-192">Lambda ifadesindeki bir [dönüş](../keywords/return.md) deyimi kapsayan metodun dönüşmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="22370-192">A [return](../keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="22370-193">Bir lambda ifadesi, bu sıçrama deyiminin hedefi lambda ifade bloğunun dışındaysa bir [goto](../keywords/goto.md), [Break](../keywords/break.md)veya [Continue](../keywords/continue.md) deyimi içeremez.</span><span class="sxs-lookup"><span data-stu-id="22370-193">A lambda expression cannot contain a [goto](../keywords/goto.md), [break](../keywords/break.md), or [continue](../keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="22370-194">Ayrıca, hedef bloğun içindeyse lambda ifade bloğunun dışında bir sıçrama deyimine sahip olmak için bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="22370-194">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="22370-195">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="22370-195">C# language specification</span></span>

<span data-ttu-id="22370-196">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="22370-196">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="22370-197">Öne çıkan kitap bölümü</span><span class="sxs-lookup"><span data-stu-id="22370-197">Featured book chapter</span></span>

<span data-ttu-id="22370-198">C# 3,0 tanımlama kitabı, üçüncü sürüm 'de [Temsilciler, olaylar ve lambda ifadeleri](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) [: c# 3,0 programcıları için 250 ' den fazla çözüm](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span><span class="sxs-lookup"><span data-stu-id="22370-198">[Delegates, Events, and Lambda Expressions](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22370-199">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22370-199">See also</span></span>

- [<span data-ttu-id="22370-200">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="22370-200">C# reference</span></span>](../index.md)
- [<span data-ttu-id="22370-201">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="22370-201">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="22370-202">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="22370-202">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="22370-203">İfade ağaçları</span><span class="sxs-lookup"><span data-stu-id="22370-203">Expression Trees</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="22370-204">Yerel işlevler ve lambda ifadeleri karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="22370-204">Local functions vs. lambda expressions</span></span>](../../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [<span data-ttu-id="22370-205">Visual Studio 2008 C# örnekleri (bkz. LINQ örnek sorguları dosyaları ve XQuery programı)</span><span class="sxs-lookup"><span data-stu-id="22370-205">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
