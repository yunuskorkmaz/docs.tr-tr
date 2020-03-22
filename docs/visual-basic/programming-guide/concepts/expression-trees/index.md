---
title: İfade Ağaçları
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: b2266cbae0a9a8a07c2a3569efa33d162ffedd1d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266423"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="f15d2-102">İfade Ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15d2-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="f15d2-103">İfade ağaçları, her düğümün bir ifade olduğu ağaç benzeri bir veri yapısındaki kodu temsil ediyor, örneğin bir yöntem çağrısı veya . gibi `x < y`ikili bir işlem.</span><span class="sxs-lookup"><span data-stu-id="f15d2-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="f15d2-104">İfade ağaçları tarafından temsil edilen kodu derleyebilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f15d2-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="f15d2-105">Bu, yürütülebilir kodun dinamik olarak değiştirilmesini, çeşitli veritabanlarında LINQ sorgularının yürütülmesini ve dinamik sorguların oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f15d2-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="f15d2-106">LINQ'daki ifade ağaçları hakkında daha fazla bilgi için [bkz: Dinamik Sorgular Oluşturmak için İfade Ağaçlarını Kullanın (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="f15d2-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="f15d2-107">İfade ağaçları, dinamik diller ve .NET Framework arasında birlikte çalışabilirlik sağlamak ve derleyici yazarların Microsoft ara dili (MSIL) yerine ifade ağaçları yayatmasını sağlamak için dinamik dil çalışma süresinde (DLR) de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f15d2-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="f15d2-108">DLR hakkında daha fazla bilgi için [Dinamik Dil Çalışma Süresine Genel Bakış'a](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f15d2-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="f15d2-109">C# veya Visual Basic derleyicisinin anonim bir lambda ifadesine dayalı olarak sizin için bir ifade ağacı <xref:System.Linq.Expressions> oluşturmasını sağlayabilir veya ad alanını kullanarak ifade ağaçları el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f15d2-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="f15d2-110">Lambda İfadelerinden İfade Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f15d2-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="f15d2-111">Bir lambda ifadesi bir tür <xref:System.Linq.Expressions.Expression%601>değişkenine atandığında, derleyici lambda ifadesini temsil eden bir ifade ağacı oluşturmak için kod yakar.</span><span class="sxs-lookup"><span data-stu-id="f15d2-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="f15d2-112">Visual Basic derleyicisi ifade ağaçları sadece ifade lambdas (veya tek satırlambdas) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f15d2-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="f15d2-113">İfade lambdas (veya çok çizgili lambdas) ayrıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="f15d2-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="f15d2-114">Visual Basic'teki lambda ifadeleri hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="f15d2-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="f15d2-115">Aşağıdaki kod örnekleri, Visual Basic derleyicisinin lambda ifadesini `Function(num) num < 5`temsil eden bir ifade ağacı oluşturmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f15d2-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="f15d2-116">API'yi Kullanarak İfade Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f15d2-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="f15d2-117">API'yi kullanarak ifade ağaçları oluşturmak <xref:System.Linq.Expressions.Expression> için sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f15d2-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="f15d2-118">Bu sınıf, örneğin, <xref:System.Linq.Expressions.ParameterExpression>bir değişken veya parametreyi temsil eden veya <xref:System.Linq.Expressions.MethodCallExpression>bir yöntem çağrısını temsil eden, belirli türlerdeki ifade ağacı düğümlerini oluşturan statik fabrika yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f15d2-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="f15d2-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer ifadeye özgü türleri <xref:System.Linq.Expressions> de ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f15d2-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="f15d2-120">Bu tür soyut türünden <xref:System.Linq.Expressions.Expression>türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f15d2-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="f15d2-121">Aşağıdaki kod örneği, API'yi kullanarak lambda ifadesini `Function(num) num < 5` temsil eden bir ifade ağacının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f15d2-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="f15d2-122">.NET Framework 4 veya sonraki durumlarda, ifade ağaçları API ayrıca döngüler, koşullu bloklar `try-catch` ve bloklar gibi atamaları ve denetim akış ifadelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="f15d2-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="f15d2-123">API'yi kullanarak, Visual Basic derleyicisi tarafından lambda ifadelerinden oluşturulabilen ifadelerden daha karmaşık ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f15d2-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="f15d2-124">Aşağıdaki örnek, bir sayının faktöriyelini hesaplayan bir ifade ağacının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f15d2-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="f15d2-125">Daha fazla bilgi için Visual [Studio 2010'da İfade Ağaçlarıyla Dinamik Yöntemler Oluşturma](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/)bölümüne bakın ve bu yöntemler Visual Studio'nun sonraki sürümleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f15d2-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="f15d2-126">Ayrışma İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="f15d2-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="f15d2-127">Aşağıdaki kod örneği, lambda ifadesini `Function(num) num < 5` temsil eden ifade ağacının parçalarına nasıl ayrıştırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f15d2-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="f15d2-128">İfade Ağaçlarının Değişmezliği</span><span class="sxs-lookup"><span data-stu-id="f15d2-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="f15d2-129">İfade ağaçları değişmez olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f15d2-129">Expression trees should be immutable.</span></span> <span data-ttu-id="f15d2-130">Bu, bir ifade ağacını değiştirmek istiyorsanız, varolan bir ifadeyi kopyalayarak ve düğümleri değiştirerek yeni bir ifade ağacı oluşturmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f15d2-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="f15d2-131">Varolan ifade ağacını geçmek için bir ifade ağacı ziyaretçisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f15d2-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="f15d2-132">Daha fazla bilgi için [bkz: İfade Ağaçlarını Değiştir (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="f15d2-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="f15d2-133">İfade Ağaçlarını Derleme</span><span class="sxs-lookup"><span data-stu-id="f15d2-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="f15d2-134">Tür, <xref:System.Linq.Expressions.Expression%601> bir <xref:System.Linq.Expressions.Expression%601.Compile%2A> ifade ağacı tarafından temsil edilen kodu yürütülebilir bir temsilciye derleyen yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f15d2-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="f15d2-135">Aşağıdaki kod örneği, bir ifade ağacının nasıl derlenebildiğini ve ortaya çıkan kodunasıl çalıştırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f15d2-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="f15d2-136">Daha fazla bilgi için [bkz: İfade Ağaçlarını Yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="f15d2-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15d2-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f15d2-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="f15d2-138">Nasıl Yapılır: İfade Ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15d2-138">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="f15d2-139">Nasıl Yapılır: İfade Ağaçlarını Değiştir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15d2-139">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="f15d2-140">Lambda İfadeler</span><span class="sxs-lookup"><span data-stu-id="f15d2-140">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="f15d2-141">Dinamik Dil Çalışma Süresine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f15d2-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="f15d2-142">Programlama Kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15d2-142">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
