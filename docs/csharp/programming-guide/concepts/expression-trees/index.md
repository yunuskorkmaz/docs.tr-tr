---
title: İfade ağaçları (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: e1ba2ac9107b5c0ab4547bd8cc5f23ca84753951
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969852"
---
# <a name="expression-trees-c"></a><span data-ttu-id="7a8b4-102">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="7a8b4-102">Expression Trees (C#)</span></span>
<span data-ttu-id="7a8b4-103">İfade ağaçları, her düğümün bir ifade olduğu, örneğin bir yöntem çağrısı veya `x < y`gibi bir ikili işlem olduğu ağaç benzeri bir veri yapısında kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="7a8b4-104">İfade ağaçları ile temsil edilen kodu derleyebilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="7a8b4-105">Bu, yürütülebilir kodun dinamik olarak değiştirilmesini, çeşitli veritabanlarındaki LINQ sorgularının yürütülmesini ve dinamik sorguların oluşturulmasını mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="7a8b4-106">LINQ içindeki ifade ağaçları hakkında daha fazla bilgi için bkz. [dinamik sorgular oluşturmak için ifade ağaçları kullanma (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="7a8b4-106">For more information about expression trees in LINQ, see [How to use expression trees to build dynamic queries (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>
  
 <span data-ttu-id="7a8b4-107">İfade ağaçları ayrıca dinamik diller ve .NET Framework arasında birlikte çalışabilirlik sağlamak ve derleyici yazıcılarının Microsoft ara dili (MSIL) yerine ifade ağaçları sunmak için dinamik dil çalışma zamanı (DLR) içinde de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="7a8b4-108">DLR hakkında daha fazla bilgi için bkz. [dinamik dil çalışma zamanına genel bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7a8b4-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="7a8b4-109">C# Veya Visual Basic derleyicisinin anonim lambda ifadesine göre sizin için bir ifade ağacı oluşturmasını sağlayabilir veya <xref:System.Linq.Expressions> ad alanını kullanarak el ile ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="7a8b4-110">Lambda Ifadelerinden Ifade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7a8b4-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="7a8b4-111">Lambda ifadesi <xref:System.Linq.Expressions.Expression%601>türünde bir değişkene atandığında, derleyici lambda ifadesini temsil eden bir ifade ağacı oluşturmak için kodu yayar.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="7a8b4-112">C# Derleyici yalnızca ifade lambdaları (veya tek satırlık Lambdalar) için ifade ağaçları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="7a8b4-113">İfade lambdaları (veya çok satırlı Lambdalar) ayrıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="7a8b4-114">İçindeki C#lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7a8b4-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="7a8b4-115">Aşağıdaki kod örnekleri, C# derleyicinin `num => num < 5`lambda ifadesini temsil eden bir ifade ağacının nasıl oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="7a8b4-116">API kullanarak Ifade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7a8b4-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="7a8b4-117">API kullanarak ifade ağaçları oluşturmak için <xref:System.Linq.Expressions.Expression> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="7a8b4-118">Bu sınıf, bir değişken veya parametre temsil eden <xref:System.Linq.Expressions.ParameterExpression>, ya da bir yöntem çağrısını temsil eden <xref:System.Linq.Expressions.MethodCallExpression>gibi belirli türlerin ifade ağacı düğümlerini oluşturan statik fabrika yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="7a8b4-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>ve diğer ifadeye özgü türler <xref:System.Linq.Expressions> ad alanında da tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="7a8b4-120">Bu türler <xref:System.Linq.Expressions.Expression>soyut türünden türetilir.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="7a8b4-121">Aşağıdaki kod örneği, API kullanarak `num => num < 5` lambda ifadesini temsil eden bir ifade ağacının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="7a8b4-122">.NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API 'SI, döngüleri, koşullu blokları ve `try-catch` blokları gibi atamaları ve denetim akışı ifadelerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="7a8b4-123">API 'yi kullanarak, C# derleyici tarafından lambda ifadelerinden oluşturulanlardan daha karmaşık ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="7a8b4-124">Aşağıdaki örnek, bir sayının faktöriyelini hesaplayan bir ifade ağacının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="7a8b4-125">Daha fazla bilgi için bkz. Visual Studio 'nun sonraki sürümleri için de geçerli olan [Visual studio 2010 ' de Ifade ağaçları Ile dinamik yöntemler üretme](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/).</span><span class="sxs-lookup"><span data-stu-id="7a8b4-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="7a8b4-126">Ifade ağaçlarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="7a8b4-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="7a8b4-127">Aşağıdaki kod örneği, `num => num < 5` lambda ifadesini temsil eden ifade ağacının bölümlerine nasıl parçalanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="7a8b4-128">Ifade ağaçlarının dengeszlik düzeyini bilme</span><span class="sxs-lookup"><span data-stu-id="7a8b4-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="7a8b4-129">İfade ağaçları sabit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-129">Expression trees should be immutable.</span></span> <span data-ttu-id="7a8b4-130">Yani, bir ifade ağacını değiştirmek istiyorsanız, var olan birini kopyalayarak ve içindeki düğümleri değiştirerek yeni bir ifade ağacı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="7a8b4-131">Varolan ifade ağacında çapraz geçiş yapmak için bir ifade ağacı Visitor kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="7a8b4-132">Daha fazla bilgi için bkz. [ifade ağaçlarını değiştirmeC#()](./how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="7a8b4-132">For more information, see [How to modify expression trees (C#)](./how-to-modify-expression-trees.md).</span></span>
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="7a8b4-133">Ifade ağaçlarını derleme</span><span class="sxs-lookup"><span data-stu-id="7a8b4-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="7a8b4-134"><xref:System.Linq.Expressions.Expression%601> türü, bir ifade ağacının temsil ettiği kodu yürütülebilir bir temsilciye derleyen <xref:System.Linq.Expressions.Expression%601.Compile%2A> yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="7a8b4-135">Aşağıdaki kod örneği, bir ifade ağacının nasıl derlendiğini ve sonuçta elde edilen kodu nasıl çalıştıracağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="7a8b4-136">Daha fazla bilgi için bkz. [ifade ağaçlarını yürütmeC#()](./how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="7a8b4-136">For more information, see [How to execute expression trees (C#)](./how-to-execute-expression-trees.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7a8b4-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="7a8b4-138">İfade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="7a8b4-138">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="7a8b4-139">İfade ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="7a8b4-139">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
- [<span data-ttu-id="7a8b4-140">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7a8b4-140">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="7a8b4-141">Dinamik Dil Çalışma Zamanına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7a8b4-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="7a8b4-142">Programlama kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="7a8b4-142">Programming Concepts (C#)</span></span>](../index.md)
