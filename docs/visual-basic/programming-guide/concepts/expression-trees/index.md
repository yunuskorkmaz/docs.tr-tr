---
title: İfade ağaçları (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: babee41f7df48f270d0c56cb2af91e463407d5c1
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696955"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="b98a6-102">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b98a6-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="b98a6-103">İfade ağaçları her düğüm olduğu bir ifade, örneğin bir ağaç benzeri veri yapısı, bir yöntem çağrısı veya bir ikili işlem kodu gibi temsil eden `x < y`.</span><span class="sxs-lookup"><span data-stu-id="b98a6-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="b98a6-104">Derleme ve ifade ağaçları tarafından temsil edilen kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b98a6-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="b98a6-105">Bu, dinamik yürütülebilir kodunun değiştirilmesini LINQ yürütülmesi çeşitli veritabanları ve dinamik sorgular oluşturulmasını sorgular sağlar.</span><span class="sxs-lookup"><span data-stu-id="b98a6-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="b98a6-106">İfade ağaçları LINQ hakkında daha fazla bilgi için bkz: [nasıl yapılır: dinamik sorgular derleme (Visual Basic) için kullanımı ifade ağaçları](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="b98a6-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="b98a6-107">İfade ağaçları, aynı zamanda dinamik diller ve .NET Framework birlikte çalışabilirliği sağlamak için ve Microsoft Ara dili (MSIL) yerine ifade ağaçları yaymak üzere derleyici yazıcılarının etkinleştirmek için dinamik dil çalışma zamanı (DLR) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b98a6-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="b98a6-108">DLR hakkında daha fazla bilgi için bkz: [dinamik dil çalışma zamanına genel bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b98a6-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="b98a6-109">Bir ifade ağacına oluşturduğunuz bir anonim lambda ifadesi temelinde veya kullanarak ifade ağaçları el ile oluşturabilirsiniz için C# veya Visual Basic derleyici olabilir <xref:System.Linq.Expressions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b98a6-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="b98a6-110">İfade ağaçları gelen Lambda ifadeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="b98a6-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="b98a6-111">Lambda ifadesi türü değişkenine atanan zaman <xref:System.Linq.Expressions.Expression%601>, lambda ifadesi temsil eden bir ifade ağacına oluşturmak için kod derleyicisi yayar.</span><span class="sxs-lookup"><span data-stu-id="b98a6-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="b98a6-112">Visual Basic derleyici ifade ağaçları yalnızca ifade Lambda'lar (veya tek satırlık Lambda'lar) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b98a6-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="b98a6-113">Deyimi Lambda'lar (veya birden çok satırlı lambda) ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b98a6-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="b98a6-114">Visual Basic'te lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b98a6-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="b98a6-115">Aşağıdaki kod örneği temsil eden lambda ifadesi bir ifade ağacına oluşturma Visual Basic derleyici nasıl göstermek `Function(num) num < 5`.</span><span class="sxs-lookup"><span data-stu-id="b98a6-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="b98a6-116">İfade ağaçları API'yi kullanarak oluşturma</span><span class="sxs-lookup"><span data-stu-id="b98a6-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="b98a6-117">İfade ağaçları API'yi kullanarak oluşturmak için kullanın <xref:System.Linq.Expressions.Expression> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b98a6-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="b98a6-118">Bu sınıf belirli türlerinin ağaç düğümleri ifade oluşturun; Örneğin, statik Fabrika yöntemler içerir <xref:System.Linq.Expressions.ParameterExpression>, temsil eden bir değişken ya da parametre veya <xref:System.Linq.Expressions.MethodCallExpression>, yöntem çağrısı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b98a6-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="b98a6-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer ifade özgü türleri de tanımlanan <xref:System.Linq.Expressions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b98a6-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="b98a6-120">Bu tür soyut türden türetilmiş <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="b98a6-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="b98a6-121">Aşağıdaki kod örneğinde nasıl temsil eden lambda ifadesi bir ifade ağacına oluşturulduğunu gösteren `Function(num) num < 5` API'yi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b98a6-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="b98a6-122">.NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API de atamaları ve denetim akışı ifadeleri döngüler, koşullu blokları gibi destekler ve `try-catch` engeller.</span><span class="sxs-lookup"><span data-stu-id="b98a6-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="b98a6-123">API'yi kullanarak gelen lambda ifadeleri Visual Basic derleyici tarafından oluşturulabilen olandan daha karmaşık ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b98a6-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="b98a6-124">Aşağıdaki örnek, bir sayı çarpımını hesaplar bir ifade ağacına oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b98a6-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="b98a6-125">Daha fazla bilgi için bkz: [oluşturma dinamik yöntemler ifade ağaçları Visual Studio 2010 ile](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010), Visual Studio'nun daha yeni sürümleri da geçerli.</span><span class="sxs-lookup"><span data-stu-id="b98a6-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="b98a6-126">İfade ağaçları ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="b98a6-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="b98a6-127">Aşağıdaki kod örneğinde nasıl ifade ağaç, gösterilmektedir temsil eden lambda ifadesi `Function(num) num < 5` , bölümlere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="b98a6-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="b98a6-128">İfade ağaçları girişi</span><span class="sxs-lookup"><span data-stu-id="b98a6-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="b98a6-129">İfade ağaçları sabit olmalı.</span><span class="sxs-lookup"><span data-stu-id="b98a6-129">Expression trees should be immutable.</span></span> <span data-ttu-id="b98a6-130">Bu, bir ifade ağacına değiştirmek istiyorsanız, yeni bir ifade ağacına mevcut kopyalayarak ve bu düğümler değiştirme oluşturmalıdır, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b98a6-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="b98a6-131">Bir ifade ağacına ziyaretçi varolan ifade ağacına gezme için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b98a6-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="b98a6-132">Daha fazla bilgi için bkz: [nasıl yapılır: ifade ağaçlarını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="b98a6-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="b98a6-133">İfade ağaçları derleme</span><span class="sxs-lookup"><span data-stu-id="b98a6-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="b98a6-134"><xref:System.Linq.Expressions.Expression%601> Türü sağlar <xref:System.Linq.Expressions.Expression%601.Compile%2A> yürütülebilir bir temsilci bir ifade ağacına tarafından temsil edilen kodu derler yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b98a6-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="b98a6-135">Aşağıdaki kod örneği, bir ifade ağacına derlemek ve ortaya çıkan kodu çalıştırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b98a6-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="b98a6-136">Daha fazla bilgi için bkz: [nasıl yapılır: ifade ağaçlarını yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="b98a6-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98a6-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b98a6-137">See Also</span></span>  
 <xref:System.Linq.Expressions>  
 [<span data-ttu-id="b98a6-138">Nasıl yapılır: ifade ağaçlarını (Visual Basic) yürütme</span><span class="sxs-lookup"><span data-stu-id="b98a6-138">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="b98a6-139">Nasıl yapılır: ifade ağaçlarını (Visual Basic) değiştirme</span><span class="sxs-lookup"><span data-stu-id="b98a6-139">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [<span data-ttu-id="b98a6-140">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="b98a6-140">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="b98a6-141">Dinamik Dil Çalışma Zamanına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b98a6-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
 [<span data-ttu-id="b98a6-142">Programlama Kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b98a6-142">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
