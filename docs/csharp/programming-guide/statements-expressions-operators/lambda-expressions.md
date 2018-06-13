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
ms.openlocfilehash: f20ba6845a6a84a57fa7636355d08b2f4e5cea2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340651"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="00d72-102">Lambda İfadeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="00d72-102">Lambda Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="00d72-103">Lambda ifadesi bir [anonim işlevi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) oluşturmak için kullanabileceğiniz [Temsilciler](../../../csharp/programming-guide/delegates/using-delegates.md) veya [ifade ağacına](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) türleri.</span><span class="sxs-lookup"><span data-stu-id="00d72-103">A lambda expression is an [anonymous function](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) that you can use to create [delegates](../../../csharp/programming-guide/delegates/using-delegates.md) or [expression tree](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) types.</span></span> <span data-ttu-id="00d72-104">Lambda ifadeleri kullanarak, bağımsız değişken yerine geçebilecek veya işlev çağrılarının değeri olarak döndürülebilecek, yerel işlevler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00d72-104">By using lambda expressions, you can write local functions that can be passed as arguments or returned as the value of function calls.</span></span> <span data-ttu-id="00d72-105">Lambda ifadeleri LINQ sorgu ifadeleri yazmak için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="00d72-105">Lambda expressions are particularly helpful for writing LINQ query expressions.</span></span>  
  
 <span data-ttu-id="00d72-106">Lambda ifadesi oluşturma için giriş parametreleri (varsa) lambda işlecinin sol tarafında belirtmeniz [ => ](../../../csharp/language-reference/operators/lambda-operator.md), ve diğer tarafta ifade veya deyimin blok yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="00d72-106">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator [=>](../../../csharp/language-reference/operators/lambda-operator.md), and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="00d72-107">Örneğin, lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış.</span><span class="sxs-lookup"><span data-stu-id="00d72-107">For example, the lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="00d72-108">Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="00d72-108">You can assign this expression to a delegate type, as the following example shows:</span></span>  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 <span data-ttu-id="00d72-109">Bir ifade ağacı türü oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="00d72-109">To create an expression tree type:</span></span>  
  
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
  
 <span data-ttu-id="00d72-110">`=>` Atama olarak aynı önceliğe sahip (`=`) ve [sağa ilişkilendirilebilir](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (işleçleri makalenin "Birleşim" bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="00d72-110">The `=>` operator has the same precedence as assignment (`=`) and is [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (see "Associativity" section of the Operators article).</span></span>  
  
 <span data-ttu-id="00d72-111">Lambda'lar yöntemi tabanlı içinde kullanılan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standart sorgu işleci yöntemlerinden bağımsız değişken olarak gibi sorgular <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="00d72-111">Lambdas are used in method-based [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries as arguments to standard query operator methods such as <xref:System.Linq.Enumerable.Where%2A>.</span></span>  
  
 <span data-ttu-id="00d72-112">Çağrılacak yöntem temelli sözdizimini kullandığınızda <xref:System.Linq.Enumerable.Where%2A> yönteminde <xref:System.Linq.Enumerable> sınıfı (yaptığınız gibi [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesnelere ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) bir temsilci türü parametredir <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="00d72-112">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Where%2A> method in the <xref:System.Linq.Enumerable> class (as you do in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="00d72-113">Lambda ifadesi, bu temsilciyi oluşturmak için en kullanışlı yoldur.</span><span class="sxs-lookup"><span data-stu-id="00d72-113">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="00d72-114">Aynı yönteminde, örneğin, çağırdığınızda <xref:System.Linq.Queryable?displayProperty=nameWithType> sınıfı (yaptığınız gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) parametre türü ise bir <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>< Func\> Func olduğu herhangi bir Func temsilcileri en fazla altı giriş parametreleri ile.</span><span class="sxs-lookup"><span data-stu-id="00d72-114">When you call the same method in, for example, the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) then the parameter type is an <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> where Func is any of the Func delegates with up to sixteen input parameters.</span></span> <span data-ttu-id="00d72-115">Yine, Lambda ifadesi bu ifade ağacını oluşturmanın yalnızca çok kısa bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="00d72-115">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="00d72-116">Lambda'lar izin `Where` çağrıları aslında lambda oluşturulan nesne türünü farklı olmasına rağmen benzer.</span><span class="sxs-lookup"><span data-stu-id="00d72-116">The lambdas allow the `Where` calls to look similar although in fact the type of object created from the lambda is different.</span></span>  
  
 <span data-ttu-id="00d72-117">Önceki örnekte, temsilci imza bir örtük olarak yazılan sahip olmadığına dikkat edin giriş parametresi türü `int`ve döndüren bir `int`.</span><span class="sxs-lookup"><span data-stu-id="00d72-117">In the previous example, notice that the delegate signature has one implicitly-typed input parameter of type `int`, and returns an `int`.</span></span> <span data-ttu-id="00d72-118">Lambda ifadesi bir giriş parametresi de içerdiğinden bu tür bir temsilciye dönüştürülebilir (`x`) ve derleyici türüne örtük olarak dönüştürebilirsiniz bir dönüş değeri `int`.</span><span class="sxs-lookup"><span data-stu-id="00d72-118">The lambda expression can be converted to a delegate of that type because it also has one input parameter (`x`) and a return value that the compiler can implicitly convert to type `int`.</span></span> <span data-ttu-id="00d72-119">(Tür çıkarımı, ilerleyen bölümlerde daha ayrıntılı bir şekilde tartışılmıştır.) Temsilci, giriş parametresi 5 kullanılarak çağrıldığında 25 sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="00d72-119">(Type inference is discussed in more detail in the following sections.) When the delegate is invoked by using an input parameter of 5, it returns a result of 25.</span></span>  
  
 <span data-ttu-id="00d72-120">Lambda'lar sol tarafında verilmez [olan](../../../csharp/language-reference/keywords/is.md) veya [olarak](../../../csharp/language-reference/keywords/as.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="00d72-120">Lambdas are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) or [as](../../../csharp/language-reference/keywords/as.md) operator.</span></span>  
  
 <span data-ttu-id="00d72-121">Anonim yöntemler için uygulanan tüm kısıtlamalar lambda ifadeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="00d72-121">All restrictions that apply to anonymous methods also apply to lambda expressions.</span></span> <span data-ttu-id="00d72-122">Daha fazla bilgi için bkz: [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="00d72-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
## <a name="expression-lambdas"></a><span data-ttu-id="00d72-123">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="00d72-123">Expression Lambdas</span></span>  
 <span data-ttu-id="00d72-124">Bir lambda ifadesi ile sağ tarafında bir ifade = > işleci adlı bir *lambda ifadesi*.</span><span class="sxs-lookup"><span data-stu-id="00d72-124">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="00d72-125">İfade lambdas yaygın yapımı içinde kullanılan [ifade ağaçları](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span><span class="sxs-lookup"><span data-stu-id="00d72-125">Expression lambdas are used extensively in the construction of [Expression Trees](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span></span> <span data-ttu-id="00d72-126">Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="00d72-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>  
  
```csharp
(input-parameters) => expression
```

 <span data-ttu-id="00d72-127">Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="00d72-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="00d72-128">İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:</span><span class="sxs-lookup"><span data-stu-id="00d72-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>  
  
```csharp
(x, y) => x == y
```

 <span data-ttu-id="00d72-129">Bazen derleyicinin giriş türlerini çıkarması zor veya imkansız olabilir.</span><span class="sxs-lookup"><span data-stu-id="00d72-129">Sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="00d72-130">Bu durumda türleri aşağıdaki örnekte olduğu gibi açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="00d72-130">When this occurs, you can specify the types explicitly as shown in the following example:</span></span>  
  
```csharp
(int x, string s) => s.Length > x
```

 <span data-ttu-id="00d72-131">Boş ayraçlarla sıfır giriş parametrelerini belirtin:</span><span class="sxs-lookup"><span data-stu-id="00d72-131">Specify zero input parameters with empty parentheses:</span></span>  
  
```csharp
() => SomeMethod()
```

 <span data-ttu-id="00d72-132">Önceki örnekte bir lambda ifadesi gövdesinin yöntem çağrısından oluşabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="00d72-132">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="00d72-133">Ancak, .NET Framework dışında, örneğin SQL Server'da değerlendirilen ifade ağaçları oluşturuyorsanız, lambda ifadelerinde yöntem çağrısı kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="00d72-133">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="00d72-134">Yöntemler .NET ortak dil çalışma zamanı bağlamının dışında anlamlı olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="00d72-134">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>  
  
## <a name="statement-lambdas"></a><span data-ttu-id="00d72-135">Deyim Lambdaları</span><span class="sxs-lookup"><span data-stu-id="00d72-135">Statement Lambdas</span></span>  
 <span data-ttu-id="00d72-136">Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:</span><span class="sxs-lookup"><span data-stu-id="00d72-136">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>  
  
<span data-ttu-id="00d72-137">(giriş parametreleri) = > {deyimi;}</span><span class="sxs-lookup"><span data-stu-id="00d72-137">(input-parameters) => { statement; }</span></span>

 <span data-ttu-id="00d72-138">Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.</span><span class="sxs-lookup"><span data-stu-id="00d72-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 <span data-ttu-id="00d72-139">Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="00d72-139">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="00d72-140">Zaman Uyumsuz Lambdalar</span><span class="sxs-lookup"><span data-stu-id="00d72-140">Async Lambdas</span></span>  
 <span data-ttu-id="00d72-141">Lambda ifadeleri ve kullanarak zaman uyumsuz işleme dahil deyimleri kolayca oluşturabilirsiniz [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) ve [await](../../../csharp/language-reference/keywords/await.md) anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="00d72-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../../csharp/language-reference/keywords/async.md) and [await](../../../csharp/language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="00d72-142">Örneğin, aşağıdaki Windows Forms örnek çağırır ve bir zaman uyumsuz yöntem bekler bir olay işleyiciyi içeriyor `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="00d72-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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

 <span data-ttu-id="00d72-143">Zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00d72-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="00d72-144">Bu işleyici eklemek için Ekle bir `async` lambda parametre listesi, aşağıdaki örnekte gösterildiği gibi önce değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="00d72-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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

 <span data-ttu-id="00d72-145">Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="00d72-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="00d72-146">Standart Sorgu İşlevleriyle Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="00d72-146">Lambdas with the Standard Query Operators</span></span>  
 <span data-ttu-id="00d72-147">Birçok standart sorgu işleçleri türü olan bir giriş parametresi vardır, <xref:System.Func%602> genel temsilciler ailesi.</span><span class="sxs-lookup"><span data-stu-id="00d72-147">Many Standard query operators have an input parameter whose type is one of the <xref:System.Func%602> family of generic delegates.</span></span> <span data-ttu-id="00d72-148">Bu temsilciler girdi parametrelerinin sayısını ve türünü ve temsilcinin döndürdüğü değerin türünü tanımlamak için tür parametreleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="00d72-148">These delegates use type parameters to define the number and types of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="00d72-149">`Func` Temsilciler kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadeleri kapsüllemek için çok kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="00d72-149">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="00d72-150">Örneğin, aşağıdaki temsilci türünü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="00d72-150">For example, consider the following delegate type:</span></span>  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 <span data-ttu-id="00d72-151">Temsilci olarak oluşturulabilir `Func<int,bool> myFunc` nerede `int` giriş parametresidir ve `bool` dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="00d72-151">The delegate can be instantiated as `Func<int,bool> myFunc` where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="00d72-152">Dönüş değeri her zaman son tür parametresinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="00d72-152">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="00d72-153">`Func<int, string, bool>` iki girdi parametresi ile bir temsilci tanımlar `int` ve `string`ve dönüş türü `bool`.</span><span class="sxs-lookup"><span data-stu-id="00d72-153">`Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="00d72-154">Aşağıdaki `Func` temsilci çağrıldığında, döndürecektir true veya false giriş parametresi 5'e eşit olup olmadığını belirtin:</span><span class="sxs-lookup"><span data-stu-id="00d72-154">The following `Func` delegate, when it is invoked, will return true or false to indicate whether the input parameter is equal to 5:</span></span>  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 <span data-ttu-id="00d72-155">Bağımsız değişken türü olduğunda, aynı zamanda bir lambda ifadesi sağlayabilir bir `Expression<Func>`, örneğin System.Linq.Queryable içinde tanımlanan standart sorgu işleçleri içinde.</span><span class="sxs-lookup"><span data-stu-id="00d72-155">You can also supply a lambda expression when the argument type is an `Expression<Func>`, for example in the standard query operators that are defined in System.Linq.Queryable.</span></span> <span data-ttu-id="00d72-156">Belirttiğinizde bir `Expression<Func>` bağımsız değişkeni, bir ifade ağacına lambda derlenecek.</span><span class="sxs-lookup"><span data-stu-id="00d72-156">When you specify an `Expression<Func>` argument, the lambda will be compiled to an expression tree.</span></span>  
  
 <span data-ttu-id="00d72-157">Standart sorgu işleci <xref:System.Linq.Enumerable.Count%2A> yöntemi, burada gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="00d72-157">A standard query operator, the <xref:System.Linq.Enumerable.Count%2A> method, is shown here:</span></span>  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 <span data-ttu-id="00d72-158">Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00d72-158">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="00d72-159">Bu belirli lambda ifadesi bu tamsayılar sayar (`n`), iki tarafından ayrılmış 1 kalanı vardır.</span><span class="sxs-lookup"><span data-stu-id="00d72-159">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>  
  
 <span data-ttu-id="00d72-160">Aşağıdaki kod satırını tüm öğeleri içeren bir dizisi üretir `numbers` 9 sol tarafına bu koşulu karşılamıyor sıradaki ilk sayı olduğundan olan dizi:</span><span class="sxs-lookup"><span data-stu-id="00d72-160">The following line of code produces a sequence that contains all elements in the `numbers` array that are to the left side of the 9 because that's the first number in the sequence that doesn't meet the condition:</span></span>  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 <span data-ttu-id="00d72-161">Bu örnek birden fazla giriş parametrelerini paranteze alarak belirtmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="00d72-161">This example shows how to specify multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="00d72-162">Yöntem, değeri konumundan daha az olan bir sayı ile karşılaşana dek sayı dizisindeki tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="00d72-162">The method returns all the elements in the numbers array until a number is encountered whose value is less than its position.</span></span> <span data-ttu-id="00d72-163">Lambda işleci karıştırmayın (`=>`) değerinden büyük veya eşit işleciyle (`>=`).</span><span class="sxs-lookup"><span data-stu-id="00d72-163">Do not confuse the lambda operator (`=>`) with the greater than or equal operator (`>=`).</span></span>  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a><span data-ttu-id="00d72-164">Lambda İçinde Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="00d72-164">Type Inference in Lambdas</span></span>  
 <span data-ttu-id="00d72-165">Lambda ifadeleri yazarken genellikle giriş parametreleri için bir tür belirtmeniz gerekmez; derleyici lambda gövdesine, parametrenin temsilci türüne ve C# Dil Belirtimi'nde açıklanan diğer etkenlere göre türü çıkarsayabilir.</span><span class="sxs-lookup"><span data-stu-id="00d72-165">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter’s delegate type, and other factors as described in the C# Language Specification.</span></span> <span data-ttu-id="00d72-166">Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür.</span><span class="sxs-lookup"><span data-stu-id="00d72-166">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="00d72-167">Bunu, sorgu oluşturuyorsanız bir `IEnumerable<Customer>`, giriş değişkeni olarak algılanır sonra bir `Customer` erişiminiz yöntemleri ve özellikleri anlamına gelir nesnesi:</span><span class="sxs-lookup"><span data-stu-id="00d72-167">So if you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 <span data-ttu-id="00d72-168">Lambdalar için genel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="00d72-168">The general rules for lambdas are as follows:</span></span>  
  
-   <span data-ttu-id="00d72-169">Lambda temsilci türüyle aynı sayıda parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="00d72-169">The lambda must contain the same number of parameters as the delegate type.</span></span>  
  
-   <span data-ttu-id="00d72-170">Lambdadaki her giriş parametresi, denk gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00d72-170">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>  
  
-   <span data-ttu-id="00d72-171">Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00d72-171">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>  
  
 <span data-ttu-id="00d72-172">Ortak tür sisteminin "lambda ifadesi" için iç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="00d72-172">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="00d72-173">Ancak bazen bir lambda ifadesinin "türünden" resmi olmayan bir şekilde bahsetmek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="00d72-173">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="00d72-174">Bu durumlarda türü temsilci türüne başvuruyor veya <xref:System.Linq.Expressions.Expression> yazın lambda ifadesi dönüştürülen.</span><span class="sxs-lookup"><span data-stu-id="00d72-174">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>  
  
## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="00d72-175">Lambda İfadelerinde Değişken Kapsamı</span><span class="sxs-lookup"><span data-stu-id="00d72-175">Variable Scope in Lambda Expressions</span></span>  
 <span data-ttu-id="00d72-176">Lambda'lar başvurabilir *dış değişkenleri* (bkz [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) lambda işlevi tanımlar yöntemi kapsamında olan ya da lambda ifadesi içeren kapsamında yazın.</span><span class="sxs-lookup"><span data-stu-id="00d72-176">Lambdas can refer to *outer variables* (see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="00d72-177">Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="00d72-177">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="00d72-178">Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="00d72-178">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="00d72-179">Aşağıdaki örnek bu kuralları gösterir:</span><span class="sxs-lookup"><span data-stu-id="00d72-179">The following example demonstrates these rules:</span></span>  
  
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
  
 <span data-ttu-id="00d72-180">Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="00d72-180">The following rules apply to variable scope in lambda expressions:</span></span>  
  
-   <span data-ttu-id="00d72-181">Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.</span><span class="sxs-lookup"><span data-stu-id="00d72-181">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>  
  
-   <span data-ttu-id="00d72-182">Bir lambda ifadesi içinde tanıtılan değişkenler, dış yöntemde görünmez.</span><span class="sxs-lookup"><span data-stu-id="00d72-182">Variables introduced within a lambda expression are not visible in the outer method.</span></span>  
  
-   <span data-ttu-id="00d72-183">Lambda ifadesi doğrudan yakalayamazsınız bir `in`, `ref`, veya `out` kapsayan bir yöntem parametresi.</span><span class="sxs-lookup"><span data-stu-id="00d72-183">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>  
  
-   <span data-ttu-id="00d72-184">Lambda ifadesindeki bir dönüş ifadesi, kapsayan yöntemin döndürülmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="00d72-184">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>  
  
-   <span data-ttu-id="00d72-185">Lambda ifadesi içeremez bir `goto` deyimi, `break` deyimi veya `continue` atlama deyiminin hedef dışında blok ise, lambda işlevinde deyimi.</span><span class="sxs-lookup"><span data-stu-id="00d72-185">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="00d72-186">Ayrıca, hedef, blok içinde ise lambda işlev bloğu dışında bir deyim olması bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="00d72-186">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="00d72-187">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="00d72-187">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="00d72-188">Özel Kitap Bölümü</span><span class="sxs-lookup"><span data-stu-id="00d72-188">Featured Book Chapter</span></span>  
 <span data-ttu-id="00d72-189">[Temsilciler ve olaylar Lambda ifadeleri](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) içinde [C# 3.0 Kılavuzu, üçüncü baskı: C# 3.0 programcıları için 250'den fazla çözüm](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="00d72-189">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d72-190">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00d72-190">See Also</span></span>  
 [<span data-ttu-id="00d72-191">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="00d72-191">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="00d72-192">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="00d72-192">LINQ (Language-Integrated Query)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="00d72-193">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="00d72-193">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="00d72-194">is</span><span class="sxs-lookup"><span data-stu-id="00d72-194">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="00d72-195">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="00d72-195">Expression Trees</span></span>](../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="00d72-196">Visual Studio 2008 C# örnekleri (bkz: LINQ örnek sorgular dosyaları ve XQuery program)</span><span class="sxs-lookup"><span data-stu-id="00d72-196">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
 [<span data-ttu-id="00d72-197">Özyinelemeli lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="00d72-197">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
