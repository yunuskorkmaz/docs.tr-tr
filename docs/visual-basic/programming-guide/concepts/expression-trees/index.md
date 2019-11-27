---
title: İfade Ağaçları
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: 4ca3b56f48368e465560fc5edd60c0df8dd4e1c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344698"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="d9462-102">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9462-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="d9462-103">İfade ağaçları, her düğümün bir ifade olduğu, örneğin bir yöntem çağrısı veya `x < y`gibi bir ikili işlem olduğu ağaç benzeri bir veri yapısında kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d9462-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="d9462-104">İfade ağaçları ile temsil edilen kodu derleyebilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9462-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="d9462-105">Bu, yürütülebilir kodun dinamik olarak değiştirilmesini, çeşitli veritabanlarındaki LINQ sorgularının yürütülmesini ve dinamik sorguların oluşturulmasını mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="d9462-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="d9462-106">LINQ içindeki ifade ağaçları hakkında daha fazla bilgi için bkz. [nasıl yapılır: dinamik sorgular oluşturmak Için Ifade ağaçları kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="d9462-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="d9462-107">İfade ağaçları ayrıca dinamik diller ve .NET Framework arasında birlikte çalışabilirlik sağlamak ve derleyici yazıcılarının Microsoft ara dili (MSIL) yerine ifade ağaçları sunmak için dinamik dil çalışma zamanı (DLR) içinde de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9462-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="d9462-108">DLR hakkında daha fazla bilgi için bkz. [dinamik dil çalışma zamanına genel bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9462-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="d9462-109">C# Veya Visual Basic derleyicisinin anonim lambda ifadesine göre sizin için bir ifade ağacı oluşturmasını sağlayabilir veya <xref:System.Linq.Expressions> ad alanını kullanarak el ile ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9462-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="d9462-110">Lambda Ifadelerinden Ifade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9462-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="d9462-111">Lambda ifadesi <xref:System.Linq.Expressions.Expression%601>türünde bir değişkene atandığında, derleyici lambda ifadesini temsil eden bir ifade ağacı oluşturmak için kodu yayar.</span><span class="sxs-lookup"><span data-stu-id="d9462-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="d9462-112">Visual Basic Derleyicisi yalnızca ifade lambdaları (veya tek satırlık Lambdalar) için ifade ağaçları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d9462-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="d9462-113">İfade lambdaları (veya çok satırlı Lambdalar) ayrıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="d9462-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="d9462-114">Visual Basic lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d9462-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="d9462-115">Aşağıdaki kod örnekleri, Visual Basic derleyicisinin `Function(num) num < 5`lambda ifadesini temsil eden bir ifade ağacının nasıl oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9462-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="d9462-116">API kullanarak Ifade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9462-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="d9462-117">API kullanarak ifade ağaçları oluşturmak için <xref:System.Linq.Expressions.Expression> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9462-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="d9462-118">Bu sınıf, bir değişken veya parametre temsil eden <xref:System.Linq.Expressions.ParameterExpression>, ya da bir yöntem çağrısını temsil eden <xref:System.Linq.Expressions.MethodCallExpression>gibi belirli türlerin ifade ağacı düğümlerini oluşturan statik fabrika yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d9462-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="d9462-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>ve diğer ifadeye özgü türler <xref:System.Linq.Expressions> ad alanında da tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d9462-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="d9462-120">Bu türler <xref:System.Linq.Expressions.Expression>soyut türünden türetilir.</span><span class="sxs-lookup"><span data-stu-id="d9462-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="d9462-121">Aşağıdaki kod örneği, API kullanarak `Function(num) num < 5` lambda ifadesini temsil eden bir ifade ağacının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d9462-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="d9462-122">.NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API 'SI, döngüleri, koşullu blokları ve `try-catch` blokları gibi atamaları ve denetim akışı ifadelerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="d9462-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="d9462-123">API 'yi kullanarak, Visual Basic Derleyicisi tarafından lambda ifadelerinden oluşturulanlardan daha karmaşık ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9462-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="d9462-124">Aşağıdaki örnek, bir sayının faktöriyelini hesaplayan bir ifade ağacının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d9462-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.   
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="d9462-125">Daha fazla bilgi için bkz. Visual Studio 'nun sonraki sürümleri için de geçerli olan [Visual studio 2010 ' de Ifade ağaçları Ile dinamik yöntemler üretme](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/).</span><span class="sxs-lookup"><span data-stu-id="d9462-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="d9462-126">Ifade ağaçlarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="d9462-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="d9462-127">Aşağıdaki kod örneği, `Function(num) num < 5` lambda ifadesini temsil eden ifade ağacının bölümlerine nasıl parçalanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d9462-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="d9462-128">Ifade ağaçlarının dengeszlik düzeyini bilme</span><span class="sxs-lookup"><span data-stu-id="d9462-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="d9462-129">İfade ağaçları sabit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9462-129">Expression trees should be immutable.</span></span> <span data-ttu-id="d9462-130">Yani, bir ifade ağacını değiştirmek istiyorsanız, var olan birini kopyalayarak ve içindeki düğümleri değiştirerek yeni bir ifade ağacı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9462-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="d9462-131">Varolan ifade ağacında çapraz geçiş yapmak için bir ifade ağacı Visitor kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9462-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="d9462-132">Daha fazla bilgi için bkz. [nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="d9462-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="d9462-133">Ifade ağaçlarını derleme</span><span class="sxs-lookup"><span data-stu-id="d9462-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="d9462-134"><xref:System.Linq.Expressions.Expression%601> türü, bir ifade ağacının temsil ettiği kodu yürütülebilir bir temsilciye derleyen <xref:System.Linq.Expressions.Expression%601.Compile%2A> yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9462-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="d9462-135">Aşağıdaki kod örneği, bir ifade ağacının nasıl derlendiğini ve sonuçta elde edilen kodu nasıl çalıştıracağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9462-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 <span data-ttu-id="d9462-136">Daha fazla bilgi için bkz. [nasıl yapılır: yürütme Ifade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="d9462-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9462-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9462-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="d9462-138">Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9462-138">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="d9462-139">Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9462-139">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="d9462-140">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="d9462-140">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="d9462-141">Dinamik Dil Çalışma Zamanına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d9462-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="d9462-142">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9462-142">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
