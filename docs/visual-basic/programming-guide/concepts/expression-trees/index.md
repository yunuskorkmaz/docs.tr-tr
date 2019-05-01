---
title: İfade ağaçları (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: c1e576439956a735962978d37430949ed6bc39d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021875"
---
# <a name="expression-trees-visual-basic"></a>İfade ağaçları (Visual Basic)
İfade ağaçları her bir düğümü olduğu bir ifade, örneğin bir ağaç benzeri veri yapısı, bir yöntem çağrısı veya bir ikili işlem kodu gibi temsil eden `x < y`.  
  
 Derleme ve ifade ağaçları tarafından temsil edilen kodu çalıştırın. Bu, çeşitli veritabanları ve dinamik sorgular oluşturulmasını yürütme LINQ sorguları yürütülebilir kodun dinamik değişikliğini sağlar. LINQ ifade ağaçları hakkında daha fazla bilgi için bkz: [nasıl yapılır: (Visual Basic) dinamik sorgular derlemek için ifade ağaçları kullanma](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 İfade ağaçları ayrıca dinamik dil çalışma zamanı (DLR) dinamik dilleri ve .NET Framework arasında birlikte çalışabilirliği sağlamak ve Microsoft Ara dilini (MSIL) yerine ifade ağaçları yaymak derleyici yazıcıları etkinleştirmek için kullanılır. DLR hakkında daha fazla bilgi için bkz: [dinamik dil çalışma zamanına genel bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Bir lambda anonim ifadeye dayalı veya kullanarak, el ile bir ifade ağaçları oluşturabilirsiniz bir ifade ağacı oluşturma C# veya Visual Basic derleyici olabilir <xref:System.Linq.Expressions> ad alanı.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Gelen Lambda ifadeleri ifade ağaçları oluşturma  
 Bir lambda ifadesi türden bir değişkene atanmış zaman <xref:System.Linq.Expressions.Expression%601>, derleyici lambda ifadeyi temsil eden bir ifade ağacı oluşturmak için kod gösterir.  
  
 Visual Basic Derleyicisi, ifade ağaçları yalnızca ifade lambdaları (veya tek satırlı lambdalar) oluşturabilirsiniz. Deyim lambdaları (veya çok satırlı lambdalar) ayrıştırılamıyor. Visual Basic'te lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Aşağıdaki kod örnekleri, Visual Basic derleyici lambda ifadeyi temsil eden bir ifade ağacı oluşturmak göstermektedir `Function(num) num < 5`.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>İfade ağaçları API'sini kullanarak oluşturma  
 İfade ağaçları API'sini kullanarak oluşturmak için kullanın <xref:System.Linq.Expressions.Expression> sınıfı. Bu sınıf, ağaç düğümleri belirli türlerin ifade oluşturun, örneğin, statik Fabrika yöntemleri içerir. <xref:System.Linq.Expressions.ParameterExpression>, temsil eden bir değişken veya parametre, veya <xref:System.Linq.Expressions.MethodCallExpression>, bir yöntem çağrısını temsil eder. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer özel ifade türleri ayrıca tanımlanan <xref:System.Linq.Expressions> ad alanı. Bu tür soyut türünden türetilmesi <xref:System.Linq.Expressions.Expression>.  
  
 Aşağıdaki kod örneği temsil eden lambda ifadesi ifade ağacı oluşturma işlemini gösterir `Function(num) num < 5` API'yi kullanarak.  
  
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
  
 .NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API aynı zamanda atamaları ve Döngüler, koşullu blokları gibi denetim akışı ifadeler destekler ve `try-catch` engeller. API'yi kullanarak lambda ifadeleri ' Visual Basic derleyici tarafından oluşturulabilen olandan daha karmaşık bir ifade ağaçları oluşturabilirsiniz. Aşağıdaki örnek, bir sayının faktöriyelini hesaplar bir ifade ağacı oluşturma işlemini gösterir.  
  
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

Daha fazla bilgi için [oluşturma dinamik yöntemler ifade ağaçlarında Visual Studio 2010 ile](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), Visual Studio'nun daha sonraki sürümlere da geçerli.
  
## <a name="parsing-expression-trees"></a>İfade ağaçları ayrıştırma  
 Aşağıdaki kod örneğinde nasıl ifade ağacı, gösterir temsil eden lambda ifadesi `Function(num) num < 5` parçasına ayrıştırıldı.  
  
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
  
## <a name="immutability-of-expression-trees"></a>İfade ağaçları değiştirilemezlik  
 İfade ağaçları sabit olmalıdır. Bu, bir ifade ağacı değiştirmek istiyorsanız, size yeni bir ifade ağacı var olan bir kopyalama ve bu düğümler değiştirerek oluşturmalıdır, anlamına gelir. Bir ifade ağacı ziyaretçi var olan bir ifade ağacı geçirmek için kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: (Visual Basic) ifade ağaçlarını değiştirme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>İfade ağaçları derleme  
 <xref:System.Linq.Expressions.Expression%601> Sağlayan türü <xref:System.Linq.Expressions.Expression%601.Compile%2A> yürütülebilir bir temsilciye bir ifade ağacı tarafından temsil edilen kod derlenir yöntemi.  
  
 Aşağıdaki kod örneği, bir ifade ağacı derlemek ve sonuç kodu çalıştırmak gösterilmektedir.  
  
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
  
 Daha fazla bilgi için [nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Expressions>
- [Nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Nasıl yapılır: (Visual Basic) ifade ağaçlarını değiştirme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [Lambda İfadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Dinamik Dil Çalışma Zamanına Genel Bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Programlama Kavramları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
