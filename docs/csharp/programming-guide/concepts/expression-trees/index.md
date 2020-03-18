---
title: İfade Ağaçları (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: f425ab38bf7bb54814fe777b7cb02180d022a8af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169642"
---
# <a name="expression-trees-c"></a><span data-ttu-id="4ebbf-102">İfade Ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="4ebbf-102">Expression Trees (C#)</span></span>
<span data-ttu-id="4ebbf-103">İfade ağaçları, her düğümün bir ifade olduğu ağaç benzeri bir veri yapısındaki kodu temsil ediyor, örneğin bir yöntem çağrısı veya . gibi `x < y`ikili bir işlem.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="4ebbf-104">İfade ağaçları tarafından temsil edilen kodu derleyebilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="4ebbf-105">Bu, yürütülebilir kodun dinamik olarak değiştirilmesini, çeşitli veritabanlarında LINQ sorgularının yürütülmesini ve dinamik sorguların oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="4ebbf-106">LINQ'daki ifade ağaçları hakkında daha fazla bilgi [için, dinamik sorgular (C#) oluşturmak için ifade ağaçlarının nasıl kullanılacağına](./how-to-use-expression-trees-to-build-dynamic-queries.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-106">For more information about expression trees in LINQ, see [How to use expression trees to build dynamic queries (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>
  
 <span data-ttu-id="4ebbf-107">İfade ağaçları, dinamik diller ve .NET Framework arasında birlikte çalışabilirlik sağlamak ve derleyici yazarların Microsoft ara dili (MSIL) yerine ifade ağaçları yayatmasını sağlamak için dinamik dil çalışma süresinde (DLR) de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="4ebbf-108">DLR hakkında daha fazla bilgi için [Dinamik Dil Çalışma Süresine Genel Bakış'a](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="4ebbf-109">C# veya Visual Basic derleyicisinin anonim bir lambda ifadesine dayalı olarak sizin için bir ifade ağacı <xref:System.Linq.Expressions> oluşturmasını sağlayabilir veya ad alanını kullanarak ifade ağaçları el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="4ebbf-110">Lambda İfadelerinden İfade Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ebbf-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="4ebbf-111">Bir lambda ifadesi bir tür <xref:System.Linq.Expressions.Expression%601>değişkenine atandığında, derleyici lambda ifadesini temsil eden bir ifade ağacı oluşturmak için kod yakar.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="4ebbf-112">C# derleyicisi ifade ağaçları sadece ifade lambdas (veya tek satırlambdas) üretebilir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="4ebbf-113">İfade lambdas (veya çok çizgili lambdas) ayrıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="4ebbf-114">C#'daki lambda ifadeleri hakkında daha fazla bilgi için [Lambda İfadeleri'ne](../../statements-expressions-operators/lambda-expressions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="4ebbf-115">Aşağıdaki kod örnekleri, C# derleyicisinin lambda ifadesini `num => num < 5`temsil eden bir ifade ağacı oluşturmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="4ebbf-116">API'yi Kullanarak İfade Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ebbf-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="4ebbf-117">API'yi kullanarak ifade ağaçları oluşturmak <xref:System.Linq.Expressions.Expression> için sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="4ebbf-118">Bu sınıf, örneğin, <xref:System.Linq.Expressions.ParameterExpression>bir değişken veya parametreyi temsil eden veya <xref:System.Linq.Expressions.MethodCallExpression>bir yöntem çağrısını temsil eden, belirli türlerdeki ifade ağacı düğümlerini oluşturan statik fabrika yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="4ebbf-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer ifadeye özgü türleri <xref:System.Linq.Expressions> de ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="4ebbf-120">Bu tür soyut türünden <xref:System.Linq.Expressions.Expression>türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="4ebbf-121">Aşağıdaki kod örneği, API'yi kullanarak lambda ifadesini `num => num < 5` temsil eden bir ifade ağacının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="4ebbf-122">.NET Framework 4 veya sonraki durumlarda, ifade ağaçları API ayrıca döngüler, koşullu bloklar `try-catch` ve bloklar gibi atamaları ve denetim akış ifadelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="4ebbf-123">API'yi kullanarak, C# derleyicisi tarafından lambda ifadelerinden oluşturulabilenifadelerden daha karmaşık ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="4ebbf-124">Aşağıdaki örnek, bir sayının faktöriyelini hesaplayan bir ifade ağacının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="4ebbf-125">Daha fazla bilgi için Visual [Studio 2010'da İfade Ağaçlarıyla Dinamik Yöntemler Oluşturma](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/)bölümüne bakın ve bu yöntemler Visual Studio'nun sonraki sürümleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="4ebbf-126">Ayrışma İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="4ebbf-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="4ebbf-127">Aşağıdaki kod örneği, lambda ifadesini `num => num < 5` temsil eden ifade ağacının parçalarına nasıl ayrıştırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="4ebbf-128">İfade Ağaçlarının Değişmezliği</span><span class="sxs-lookup"><span data-stu-id="4ebbf-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="4ebbf-129">İfade ağaçları değişmez olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-129">Expression trees should be immutable.</span></span> <span data-ttu-id="4ebbf-130">Bu, bir ifade ağacını değiştirmek istiyorsanız, varolan bir ifadeyi kopyalayarak ve düğümleri değiştirerek yeni bir ifade ağacı oluşturmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="4ebbf-131">Varolan ifade ağacını geçmek için bir ifade ağacı ziyaretçisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="4ebbf-132">Daha fazla bilgi için [ifade ağaçlarını (C#) nasıl değiştirebilirsiniz'](./how-to-modify-expression-trees.md)e bakın.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-132">For more information, see [How to modify expression trees (C#)](./how-to-modify-expression-trees.md).</span></span>
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="4ebbf-133">İfade Ağaçlarını Derleme</span><span class="sxs-lookup"><span data-stu-id="4ebbf-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="4ebbf-134">Tür, <xref:System.Linq.Expressions.Expression%601> bir <xref:System.Linq.Expressions.Expression%601.Compile%2A> ifade ağacı tarafından temsil edilen kodu yürütülebilir bir temsilciye derleyen yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="4ebbf-135">Aşağıdaki kod örneği, bir ifade ağacının nasıl derlenebildiğini ve ortaya çıkan kodunasıl çalıştırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="4ebbf-136">Daha fazla bilgi için [ifade ağaçlarının (C#) nasıl yürütüldürüne](./how-to-execute-expression-trees.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-136">For more information, see [How to execute expression trees (C#)](./how-to-execute-expression-trees.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4ebbf-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ebbf-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="4ebbf-138">İfade ağaçları nasıl yürütülür (C#)</span><span class="sxs-lookup"><span data-stu-id="4ebbf-138">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="4ebbf-139">İfade ağaçları nasıl değiştirilir (C#)</span><span class="sxs-lookup"><span data-stu-id="4ebbf-139">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
- [<span data-ttu-id="4ebbf-140">Lambda İfadeler</span><span class="sxs-lookup"><span data-stu-id="4ebbf-140">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="4ebbf-141">Dinamik Dil Çalışma Süresine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4ebbf-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="4ebbf-142">Programlama Kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="4ebbf-142">Programming Concepts (C#)</span></span>](../index.md)
