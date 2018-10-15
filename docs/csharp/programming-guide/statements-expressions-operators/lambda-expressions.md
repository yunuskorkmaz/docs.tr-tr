---
title: Lambda İfadeleri (C# Programlama Kılavuzu)
ms.date: 03/03/2017
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: c00d28a5339eccda6f45234c70802f014e00ee60
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316278"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="1cf04-102">Lambda İfadeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1cf04-102">Lambda Expressions (C# Programming Guide)</span></span>

<span data-ttu-id="1cf04-103">Bir lambda ifadesi; bir [anonim işlev](anonymous-methods.md) oluşturmak için kullanabileceğiniz [Temsilciler](../delegates/using-delegates.md) veya [ifade ağacı](../concepts/expression-trees/index.md) türleri.</span><span class="sxs-lookup"><span data-stu-id="1cf04-103">A lambda expression is an [anonymous function](anonymous-methods.md) that you can use to create [delegates](../delegates/using-delegates.md) or [expression tree](../concepts/expression-trees/index.md) types.</span></span> <span data-ttu-id="1cf04-104">Lambda ifadeleri kullanarak, bağımsız değişken yerine geçebilecek veya işlev çağrılarının değeri olarak döndürülebilecek, yerel işlevler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cf04-104">By using lambda expressions, you can write local functions that can be passed as arguments or returned as the value of function calls.</span></span> <span data-ttu-id="1cf04-105">Lambda ifadeleri LINQ sorgu ifadeleri yazmak için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1cf04-105">Lambda expressions are particularly helpful for writing LINQ query expressions.</span></span>
  
<span data-ttu-id="1cf04-106">Bir lambda ifadesi oluşturmak için giriş parametrelerini (varsa) lambda işlecinin sol tarafında belirttiğiniz [ => ](../../../csharp/language-reference/operators/lambda-operator.md), ve ifadeyi veya deyim bloğunu diğer tarafa yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1cf04-106">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator [=>](../../../csharp/language-reference/operators/lambda-operator.md), and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="1cf04-107">Örneğin, lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış.</span><span class="sxs-lookup"><span data-stu-id="1cf04-107">For example, the lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="1cf04-108">Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1cf04-108">You can assign this expression to a delegate type, as the following example shows:</span></span>  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 <span data-ttu-id="1cf04-109">Bir ifade ağacı türü oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="1cf04-109">To create an expression tree type:</span></span>  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="1cf04-110">`=>` İşleci atamayla aynı önceliğe sahip (`=`) ve [sağdan birleşir](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (işleçler makalesindeki "Birleşme" bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="1cf04-110">The `=>` operator has the same precedence as assignment (`=`) and is [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (see "Associativity" section of the Operators article).</span></span>  
  
 <span data-ttu-id="1cf04-111">Lambda ifadeleri yöntem tabanlı kullanılan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] gibi sorgularında standart sorgu işleci yöntemlerinin bağımsız değişkenleri olarak <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="1cf04-111">Lambdas are used in method-based [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries as arguments to standard query operator methods such as <xref:System.Linq.Enumerable.Where%2A>.</span></span>  
  
 <span data-ttu-id="1cf04-112">Çağırmak için yöntem tabanlı sözdizimi kullandığınızda <xref:System.Linq.Enumerable.Where%2A> yönteminde <xref:System.Linq.Enumerable> sınıfı (yaptığınız gibi [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesnelere ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) parametre temsilci türüdür <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1cf04-112">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Where%2A> method in the <xref:System.Linq.Enumerable> class (as you do in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1cf04-113">Lambda ifadesi, bu temsilciyi oluşturmak için en kullanışlı yoldur.</span><span class="sxs-lookup"><span data-stu-id="1cf04-113">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="1cf04-114">Aynı yöntemi örneğin çağırdığınızda <xref:System.Linq.Queryable?displayProperty=nameWithType> sınıfı (yaptığınız gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) parametre türü bir <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>< Func\> burada Func, on altı adede kadar giriş parametresi Func temsilcilerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-114">When you call the same method in, for example, the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) then the parameter type is an <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> where Func is any of the Func delegates with up to sixteen input parameters.</span></span> <span data-ttu-id="1cf04-115">Yine, Lambda ifadesi bu ifade ağacını oluşturmanın yalnızca çok kısa bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="1cf04-115">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="1cf04-116">Lambdalar izin `Where` çağrılarının benzer görünmesine, aslında lambdadan oluşturulan nesnenin türü farklı olsa.</span><span class="sxs-lookup"><span data-stu-id="1cf04-116">The lambdas allow the `Where` calls to look similar although in fact the type of object created from the lambda is different.</span></span>  
  
 <span data-ttu-id="1cf04-117">Önceki örnekte, temsilci imzasında örtük olarak dikkat edin giriş parametresi türü `int`ve döndüren bir `int`.</span><span class="sxs-lookup"><span data-stu-id="1cf04-117">In the previous example, notice that the delegate signature has one implicitly-typed input parameter of type `int`, and returns an `int`.</span></span> <span data-ttu-id="1cf04-118">Lambda ifadesi bu türden bir temsilciye dönüştürülebilir çünkü ayrıca bir giriş parametresi vardır (`x`) ve derleyicinin dolaylı olarak türüne çevirebildiği bir dönüş değeri `int`.</span><span class="sxs-lookup"><span data-stu-id="1cf04-118">The lambda expression can be converted to a delegate of that type because it also has one input parameter (`x`) and a return value that the compiler can implicitly convert to type `int`.</span></span> <span data-ttu-id="1cf04-119">(Tür çıkarımı, ilerleyen bölümlerde daha ayrıntılı bir şekilde tartışılmıştır.) Temsilci, giriş parametresi 5 kullanılarak çağrıldığında 25 sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1cf04-119">(Type inference is discussed in more detail in the following sections.) When the delegate is invoked by using an input parameter of 5, it returns a result of 25.</span></span>  
  
 <span data-ttu-id="1cf04-120">Lambda ifadeleri, sol tarafında verilmez [olduğu](../../../csharp/language-reference/keywords/is.md) veya [olarak](../../../csharp/language-reference/keywords/as.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="1cf04-120">Lambdas are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) or [as](../../../csharp/language-reference/keywords/as.md) operator.</span></span>  
  
 <span data-ttu-id="1cf04-121">Anonim yöntemler için uygulanan tüm kısıtlamalar lambda ifadeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-121">All restrictions that apply to anonymous methods also apply to lambda expressions.</span></span> <span data-ttu-id="1cf04-122">Daha fazla bilgi için [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1cf04-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
## <a name="expression-lambdas"></a><span data-ttu-id="1cf04-123">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="1cf04-123">Expression Lambdas</span></span>

 <span data-ttu-id="1cf04-124">Bir lambda ifadesi işlecin sağ tarafındaki bir ifadeyle = > işleci çağrıldığında bir *lambda ifadesi*.</span><span class="sxs-lookup"><span data-stu-id="1cf04-124">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="1cf04-125">İfade lambdaları oluşumunu oluşturulurken sıkça kullanılır [ifade ağaçları](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="1cf04-125">Expression lambdas are used extensively in the construction of [Expression Trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="1cf04-126">Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="1cf04-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>
  
```csharp
(input-parameters) => expression
```

 <span data-ttu-id="1cf04-127">Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="1cf04-128">İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:</span><span class="sxs-lookup"><span data-stu-id="1cf04-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>  
  
```csharp
(x, y) => x == y
```

 <span data-ttu-id="1cf04-129">Bazen derleyicinin giriş türlerini çıkarması zor veya imkansız olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-129">Sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="1cf04-130">Bu durumda türleri aşağıdaki örnekte olduğu gibi açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1cf04-130">When this occurs, you can specify the types explicitly as shown in the following example:</span></span>  
  
```csharp
(int x, string s) => s.Length > x
```
 <span data-ttu-id="1cf04-131">Giriş parametre türlerinin tümü explicit veya tümü implicit olmalıdır; Aksi takdirde, C# oluşturur bir [CS0748](../../misc/cs0748.md) derleyici hatası.</span><span class="sxs-lookup"><span data-stu-id="1cf04-131">Input parameter types must be all explicit or all implicit; otherwise, C# generates a [CS0748](../../misc/cs0748.md) compiler error.</span></span>

 <span data-ttu-id="1cf04-132">Boş ayraçlarla sıfır giriş parametrelerini belirtin:</span><span class="sxs-lookup"><span data-stu-id="1cf04-132">Specify zero input parameters with empty parentheses:</span></span>  
  
```csharp
() => SomeMethod()
```

 <span data-ttu-id="1cf04-133">Önceki örnekte bir lambda ifadesi gövdesinin yöntem çağrısından oluşabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1cf04-133">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="1cf04-134">Ancak, .NET Framework dışında, örneğin SQL Server'da değerlendirilen ifade ağaçları oluşturuyorsanız, lambda ifadelerinde yöntem çağrısı kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-134">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="1cf04-135">Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="1cf04-135">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>  
  
## <a name="statement-lambdas"></a><span data-ttu-id="1cf04-136">Deyim Lambdaları</span><span class="sxs-lookup"><span data-stu-id="1cf04-136">Statement Lambdas</span></span>  
 <span data-ttu-id="1cf04-137">Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:</span><span class="sxs-lookup"><span data-stu-id="1cf04-137">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>  
  
<span data-ttu-id="1cf04-138">(giriş parametreleri) = > {deyimi;}</span><span class="sxs-lookup"><span data-stu-id="1cf04-138">(input-parameters) => { statement; }</span></span>

 <span data-ttu-id="1cf04-139">Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-139">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 <span data-ttu-id="1cf04-140">Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1cf04-140">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="1cf04-141">Zaman Uyumsuz Lambdalar</span><span class="sxs-lookup"><span data-stu-id="1cf04-141">Async Lambdas</span></span>  
 <span data-ttu-id="1cf04-142">İçeren kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) ve [await](../../../csharp/language-reference/keywords/await.md) anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="1cf04-142">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../../csharp/language-reference/keywords/async.md) and [await](../../../csharp/language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="1cf04-143">Örneğin, aşağıdaki Windows Forms örneği, çağıran ve bekleyen zaman uyumsuz bir yöntem, bir olay işleyici içerir `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="1cf04-143">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 <span data-ttu-id="1cf04-144">Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cf04-144">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="1cf04-145">Bu işleyiciyi eklemek için Ekle bir `async` aşağıdaki örnekte göründüğü gibi lambda parametre listesinden önce değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="1cf04-145">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 <span data-ttu-id="1cf04-146">Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="1cf04-146">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="1cf04-147">Standart Sorgu İşlevleriyle Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="1cf04-147">Lambdas with the Standard Query Operators</span></span>  
 <span data-ttu-id="1cf04-148">Standart sorgu işleçlerinin çoğu, türü bir giriş parametresine sahiptir, <xref:System.Func%602> Genel temsilci ailesinden olan.</span><span class="sxs-lookup"><span data-stu-id="1cf04-148">Many Standard query operators have an input parameter whose type is one of the <xref:System.Func%602> family of generic delegates.</span></span> <span data-ttu-id="1cf04-149">Bu temsilciler girdi parametrelerinin sayısını ve türünü ve temsilcinin döndürdüğü değerin türünü tanımlamak için tür parametreleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cf04-149">These delegates use type parameters to define the number and types of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="1cf04-150">`Func` Temsilciler, kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadelerin Kapsüllenmesi için son çok yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="1cf04-150">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="1cf04-151">Örneğin, aşağıdaki temsilci türünü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1cf04-151">For example, consider the following delegate type:</span></span>  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 <span data-ttu-id="1cf04-152">Temsilci olarak oluşturulabilir `Func<int,bool> myFunc` burada `int` giriş parametresi, ve `bool` dönüş değeridir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-152">The delegate can be instantiated as `Func<int,bool> myFunc` where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="1cf04-153">Dönüş değeri her zaman son tür parametresinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-153">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="1cf04-154">`Func<int, string, bool>` iki giriş parametrelerini içeren bir temsilci tanımlar `int` ve `string`ve bir dönüş türü `bool`.</span><span class="sxs-lookup"><span data-stu-id="1cf04-154">`Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="1cf04-155">Aşağıdaki `Func` temsilcisi çağrıldığında, true ya da giriş parametresinin 5'e eşit olup olmadığını belirtmek için false döndürür:</span><span class="sxs-lookup"><span data-stu-id="1cf04-155">The following `Func` delegate, when it is invoked, will return true or false to indicate whether the input parameter is equal to 5:</span></span>  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 <span data-ttu-id="1cf04-156">Ayrıca bağımsız değişken türü bir lambda ifadesi sağlayabilirsiniz bir `Expression<Func>`, örneğin işleçlerinde tanımlı System.Linq.queryable standart sorgu işleçleri içinde.</span><span class="sxs-lookup"><span data-stu-id="1cf04-156">You can also supply a lambda expression when the argument type is an `Expression<Func>`, for example in the standard query operators that are defined in System.Linq.Queryable.</span></span> <span data-ttu-id="1cf04-157">Belirttiğinizde bir `Expression<Func>` bağımsız değişkeni, lambda ifade ağacında derlenecek.</span><span class="sxs-lookup"><span data-stu-id="1cf04-157">When you specify an `Expression<Func>` argument, the lambda will be compiled to an expression tree.</span></span>  
  
 <span data-ttu-id="1cf04-158">Standart sorgu işleci <xref:System.Linq.Enumerable.Count%2A> yöntemi burada gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1cf04-158">A standard query operator, the <xref:System.Linq.Enumerable.Count%2A> method, is shown here:</span></span>  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 <span data-ttu-id="1cf04-159">Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cf04-159">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="1cf04-160">Bu belirli lambda ifadesi tamsayıları sayar (`n`), ikiye bölündüğünde 1 kalan sahip.</span><span class="sxs-lookup"><span data-stu-id="1cf04-160">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>  
  
 <span data-ttu-id="1cf04-161">Aşağıdaki kod satırını tüm öğelerini içeren bir dizi üretir `numbers` , dizisinde koşulu sağlamayan ilk sayı olduğundan 9 sol tarafına olan dizi:</span><span class="sxs-lookup"><span data-stu-id="1cf04-161">The following line of code produces a sequence that contains all elements in the `numbers` array that are to the left side of the 9 because that's the first number in the sequence that doesn't meet the condition:</span></span>  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 <span data-ttu-id="1cf04-162">Bu örnek birden fazla giriş parametrelerini paranteze alarak belirtmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-162">This example shows how to specify multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="1cf04-163">Yöntem, değeri konumundan daha az olan bir sayı ile karşılaşana dek sayı dizisindeki tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1cf04-163">The method returns all the elements in the numbers array until a number is encountered whose value is less than its position.</span></span> <span data-ttu-id="1cf04-164">Lambda işlecini karıştırmayın (`=>`) büyüktür veya eşittir işleciyle (`>=`).</span><span class="sxs-lookup"><span data-stu-id="1cf04-164">Do not confuse the lambda operator (`=>`) with the greater than or equal operator (`>=`).</span></span>  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a><span data-ttu-id="1cf04-165">Lambda İçinde Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="1cf04-165">Type Inference in Lambdas</span></span>  
 <span data-ttu-id="1cf04-166">Lambda ifadeleri yazarken genellikle giriş parametreleri için bir tür belirtmeniz gerekmez; derleyici lambda gövdesine, parametrenin temsilci türüne ve C# Dil Belirtimi'nde açıklanan diğer etkenlere göre türü çıkarsayabilir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-166">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter’s delegate type, and other factors as described in the C# Language Specification.</span></span> <span data-ttu-id="1cf04-167">Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür.</span><span class="sxs-lookup"><span data-stu-id="1cf04-167">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="1cf04-168">Sorguluyorsanız bunu bir `IEnumerable<Customer>`, giriş değişkeni olması sorguluyorsanız bir `Customer` nesne erişim yöntemleri ve özellikleri iznine sahip olduğunuz anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="1cf04-168">So if you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 <span data-ttu-id="1cf04-169">Lambdalar için genel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1cf04-169">The general rules for lambdas are as follows:</span></span>  
  
-   <span data-ttu-id="1cf04-170">Lambda temsilci türüyle aynı sayıda parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-170">The lambda must contain the same number of parameters as the delegate type.</span></span>  
  
-   <span data-ttu-id="1cf04-171">Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1cf04-171">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>  
  
-   <span data-ttu-id="1cf04-172">Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1cf04-172">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>  
  
 <span data-ttu-id="1cf04-173">Ortak tür sisteminin "lambda ifadesi" için iç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1cf04-173">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="1cf04-174">Ancak bazen bir lambda ifadesinin "türünden" resmi olmayan bir şekilde bahsetmek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="1cf04-174">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="1cf04-175">Bu gibi durumlarda, tür temsilci türüne başvuruyor. veya <xref:System.Linq.Expressions.Expression> , lambda ifadesinin dönüştürüldüğü yazın.</span><span class="sxs-lookup"><span data-stu-id="1cf04-175">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>  
  
## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="1cf04-176">Lambda İfadelerinde Değişken Kapsamı</span><span class="sxs-lookup"><span data-stu-id="1cf04-176">Variable Scope in Lambda Expressions</span></span>  
 <span data-ttu-id="1cf04-177">Lambdalar başvurabilir *dış değişkenlere* (bkz [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)), lambda işlevini tanımlayan yöntemin kapsamındaki ya da lambda ifadesini içeren türün kapsamındaki.</span><span class="sxs-lookup"><span data-stu-id="1cf04-177">Lambdas can refer to *outer variables* (see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="1cf04-178">Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="1cf04-178">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="1cf04-179">Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="1cf04-179">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="1cf04-180">Aşağıdaki örnek bu kuralları gösterir:</span><span class="sxs-lookup"><span data-stu-id="1cf04-180">The following example demonstrates these rules:</span></span>  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 <span data-ttu-id="1cf04-181">Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="1cf04-181">The following rules apply to variable scope in lambda expressions:</span></span>  
  
-   <span data-ttu-id="1cf04-182">Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.</span><span class="sxs-lookup"><span data-stu-id="1cf04-182">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>  
  
-   <span data-ttu-id="1cf04-183">Bir lambda ifadesi içinde tanıtılan değişkenler, dış yöntemde görünmez.</span><span class="sxs-lookup"><span data-stu-id="1cf04-183">Variables introduced within a lambda expression are not visible in the outer method.</span></span>  
  
-   <span data-ttu-id="1cf04-184">Bir lambda ifadesini doğrudan yakalayamaz bir `in`, `ref`, veya `out` parametresi kapsayan bir yöntemden alınan.</span><span class="sxs-lookup"><span data-stu-id="1cf04-184">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>  
  
-   <span data-ttu-id="1cf04-185">Lambda ifadesindeki bir dönüş ifadesi, kapsayan yöntemin döndürülmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="1cf04-185">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>  
  
-   <span data-ttu-id="1cf04-186">Bir lambda ifadesi içeremez bir `goto` deyimi `break` deyimi veya `continue` varsa atlama bildiriminin hedefi blok dışındaysa lambda işlevi içinde deyimi.</span><span class="sxs-lookup"><span data-stu-id="1cf04-186">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="1cf04-187">Ayrıca, hedef, blok içinde ise lambda işlev bloğu dışında bir deyim olması bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="1cf04-187">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1cf04-188">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="1cf04-188">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="1cf04-189">Özel Kitap Bölümü</span><span class="sxs-lookup"><span data-stu-id="1cf04-189">Featured Book Chapter</span></span>  
 <span data-ttu-id="1cf04-190">[Temsilciler, olayları ve Lambda ifadeleri](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) içinde [C# 3.0 Cookbook, Third Edition: C# 3.0 programcıları için 250'den fazla çözüm](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="1cf04-190">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf04-191">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1cf04-191">See Also</span></span>

- [<span data-ttu-id="1cf04-192">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1cf04-192">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1cf04-193">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="1cf04-193">LINQ (Language-Integrated Query)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="1cf04-194">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="1cf04-194">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [<span data-ttu-id="1cf04-195">is</span><span class="sxs-lookup"><span data-stu-id="1cf04-195">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="1cf04-196">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="1cf04-196">Expression Trees</span></span>](../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [<span data-ttu-id="1cf04-197">Visual Studio 2008 C# örnekleri (bkz: LINQ örnek sorgular dosyalar ve XQuery programı)</span><span class="sxs-lookup"><span data-stu-id="1cf04-197">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
- [<span data-ttu-id="1cf04-198">Yinelemeli lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1cf04-198">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
