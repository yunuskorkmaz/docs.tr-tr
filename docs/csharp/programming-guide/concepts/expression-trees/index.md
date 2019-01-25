---
title: İfade ağaçları (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 7744954d3a3f552d5765e6e7085950f08a5adf55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720934"
---
# <a name="expression-trees-c"></a><span data-ttu-id="fd498-102">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="fd498-102">Expression Trees (C#)</span></span>
<span data-ttu-id="fd498-103">İfade ağaçları her bir düğümü olduğu bir ifade, örneğin bir ağaç benzeri veri yapısı, bir yöntem çağrısı veya bir ikili işlem kodu gibi temsil eden `x < y`.</span><span class="sxs-lookup"><span data-stu-id="fd498-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="fd498-104">Derleme ve ifade ağaçları tarafından temsil edilen kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fd498-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="fd498-105">Bu, çeşitli veritabanları ve dinamik sorgular oluşturulmasını yürütme LINQ sorguları yürütülebilir kodun dinamik değişikliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd498-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="fd498-106">LINQ ifade ağaçları hakkında daha fazla bilgi için bkz: [nasıl yapılır: Dinamik sorgular derlemek için ifade ağaçları kullanma (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="fd498-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="fd498-107">İfade ağaçları ayrıca dinamik dil çalışma zamanı (DLR) dinamik dilleri ve .NET Framework arasında birlikte çalışabilirliği sağlamak ve Microsoft Ara dilini (MSIL) yerine ifade ağaçları yaymak derleyici yazıcıları etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd498-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="fd498-108">DLR hakkında daha fazla bilgi için bkz: [dinamik dil çalışma zamanına genel bakış](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fd498-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="fd498-109">Bir lambda anonim ifadeye dayalı veya kullanarak, el ile bir ifade ağaçları oluşturabilirsiniz bir ifade ağacı oluşturma C# veya Visual Basic derleyici olabilir <xref:System.Linq.Expressions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fd498-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="fd498-110">Gelen Lambda ifadeleri ifade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd498-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="fd498-111">Bir lambda ifadesi türden bir değişkene atanmış zaman <xref:System.Linq.Expressions.Expression%601>, derleyici lambda ifadeyi temsil eden bir ifade ağacı oluşturmak için kod gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd498-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="fd498-112">C# derleyicisi, ifade ağaçları yalnızca ifade lambdaları (veya tek satırlı lambdalar) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd498-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="fd498-113">Deyim lambdaları (veya çok satırlı lambdalar) ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="fd498-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="fd498-114">C# ' deki lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fd498-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="fd498-115">Aşağıdaki kod örnekleri, C# Derleyici lambda ifadeyi temsil eden bir ifade ağacı oluşturmak göstermektedir `num => num < 5`.</span><span class="sxs-lookup"><span data-stu-id="fd498-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="fd498-116">İfade ağaçları API'sini kullanarak oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd498-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="fd498-117">İfade ağaçları API'sini kullanarak oluşturmak için kullanın <xref:System.Linq.Expressions.Expression> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fd498-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="fd498-118">Bu sınıf, ağaç düğümleri belirli türlerin ifade oluşturun, örneğin, statik Fabrika yöntemleri içerir. <xref:System.Linq.Expressions.ParameterExpression>, temsil eden bir değişken veya parametre, veya <xref:System.Linq.Expressions.MethodCallExpression>, bir yöntem çağrısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd498-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="fd498-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer özel ifade türleri ayrıca tanımlanan <xref:System.Linq.Expressions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fd498-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="fd498-120">Bu tür soyut türünden türetilmesi <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="fd498-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="fd498-121">Aşağıdaki kod örneği temsil eden lambda ifadesi ifade ağacı oluşturma işlemini gösterir `num => num < 5` API'yi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="fd498-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Manually build the expression tree for   
// the lambda expression num => num < 5.  
ParameterExpression numParam = Expression.Parameter(typeof(int), "num");  
ConstantExpression five = Expression.Constant(5, typeof(int));  
BinaryExpression numLessThanFive = Expression.LessThan(numParam, five);  
Expression<Func<int, bool>> lambda1 =  
    Expression.Lambda<Func<int, bool>>(  
        numLessThanFive,  
        new ParameterExpression[] { numParam });  
```  
  
 <span data-ttu-id="fd498-122">.NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API aynı zamanda atamaları ve Döngüler, koşullu blokları gibi denetim akışı ifadeler destekler ve `try-catch` engeller.</span><span class="sxs-lookup"><span data-stu-id="fd498-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="fd498-123">API'yi kullanarak gelen lambda ifadeleri için C# Derleyici tarafından oluşturulan olandan daha karmaşık bir ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd498-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="fd498-124">Aşağıdaki örnek, bir sayının faktöriyelini hesaplar bir ifade ağacı oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd498-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```csharp  
// Creating a parameter expression.  
ParameterExpression value = Expression.Parameter(typeof(int), "value");  
  
// Creating an expression to hold a local variable.   
ParameterExpression result = Expression.Parameter(typeof(int), "result");  
  
// Creating a label to jump to from a loop.  
LabelTarget label = Expression.Label(typeof(int));  
  
// Creating a method body.  
BlockExpression block = Expression.Block(  
    // Adding a local variable.  
    new[] { result },  
    // Assigning a constant to a local variable: result = 1  
    Expression.Assign(result, Expression.Constant(1)),  
    // Adding a loop.  
        Expression.Loop(  
    // Adding a conditional block into the loop.  
           Expression.IfThenElse(  
    // Condition: value > 1  
               Expression.GreaterThan(value, Expression.Constant(1)),  
    // If true: result *= value --  
               Expression.MultiplyAssign(result,  
                   Expression.PostDecrementAssign(value)),  
    // If false, exit the loop and go to the label.  
               Expression.Break(label, result)  
           ),  
    // Label to jump to.  
       label  
    )  
);  
  
// Compile and execute an expression tree.  
int factorial = Expression.Lambda<Func<int, int>>(block, value).Compile()(5);  
  
Console.WriteLine(factorial);  
// Prints 120.  
```

<span data-ttu-id="fd498-125">Daha fazla bilgi için [oluşturma dinamik yöntemler ifade ağaçlarında Visual Studio 2010 ile](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), Visual Studio'nun daha sonraki sürümlere da geçerli.</span><span class="sxs-lookup"><span data-stu-id="fd498-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="fd498-126">İfade ağaçları ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="fd498-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="fd498-127">Aşağıdaki kod örneğinde nasıl ifade ağacı, gösterir temsil eden lambda ifadesi `num => num < 5` parçasına ayrıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="fd498-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Create an expression tree.  
Expression<Func<int, bool>> exprTree = num => num < 5;  
  
// Decompose the expression tree.  
ParameterExpression param = (ParameterExpression)exprTree.Parameters[0];  
BinaryExpression operation = (BinaryExpression)exprTree.Body;  
ParameterExpression left = (ParameterExpression)operation.Left;  
ConstantExpression right = (ConstantExpression)operation.Right;  
  
Console.WriteLine("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value);  
  
// This code produces the following output:  
  
// Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="fd498-128">İfade ağaçları değiştirilemezlik</span><span class="sxs-lookup"><span data-stu-id="fd498-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="fd498-129">İfade ağaçları sabit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fd498-129">Expression trees should be immutable.</span></span> <span data-ttu-id="fd498-130">Bu, bir ifade ağacı değiştirmek istiyorsanız, size yeni bir ifade ağacı var olan bir kopyalama ve bu düğümler değiştirerek oluşturmalıdır, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fd498-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="fd498-131">Bir ifade ağacı ziyaretçi var olan bir ifade ağacı geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd498-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="fd498-132">Daha fazla bilgi için [nasıl yapılır: İfade ağaçlarını değiştirme (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="fd498-132">For more information, see [How to: Modify Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="fd498-133">İfade ağaçları derleme</span><span class="sxs-lookup"><span data-stu-id="fd498-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="fd498-134"><xref:System.Linq.Expressions.Expression%601> Sağlayan türü <xref:System.Linq.Expressions.Expression%601.Compile%2A> yürütülebilir bir temsilciye bir ifade ağacı tarafından temsil edilen kod derlenir yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fd498-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="fd498-135">Aşağıdaki kod örneği, bir ifade ağacı derlemek ve sonuç kodu çalıştırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd498-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```csharp  
// Creating an expression tree.  
Expression<Func<int, bool>> expr = num => num < 5;  
  
// Compiling the expression tree into a delegate.  
Func<int, bool> result = expr.Compile();  
  
// Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4));  
  
// Prints True.  
  
// You can also use simplified syntax  
// to compile and run an expression tree.  
// The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4));  
  
// Also prints True.  
```  
  
 <span data-ttu-id="fd498-136">Daha fazla bilgi için [nasıl yapılır: İfade ağaçlarını yürütme (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="fd498-136">For more information, see [How to: Execute Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd498-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd498-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="fd498-138">Nasıl yapılır: İfade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="fd498-138">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="fd498-139">Nasıl yapılır: İfade ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="fd498-139">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="fd498-140">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="fd498-140">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="fd498-141">Dinamik Dil Çalışma Zamanına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fd498-141">Dynamic Language Runtime Overview</span></span>](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="fd498-142">Programlama Kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="fd498-142">Programming Concepts (C#)</span></span>](../../../../csharp/programming-guide/concepts/index.md)
