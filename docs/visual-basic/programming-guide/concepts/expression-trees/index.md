---
title: İfade ağaçları (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: babee41f7df48f270d0c56cb2af91e463407d5c1
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696955"
---
# <a name="expression-trees-visual-basic"></a>İfade ağaçları (Visual Basic)
İfade ağaçları her düğüm olduğu bir ifade, örneğin bir ağaç benzeri veri yapısı, bir yöntem çağrısı veya bir ikili işlem kodu gibi temsil eden `x < y`.  
  
 Derleme ve ifade ağaçları tarafından temsil edilen kodu çalıştırın. Bu, dinamik yürütülebilir kodunun değiştirilmesini LINQ yürütülmesi çeşitli veritabanları ve dinamik sorgular oluşturulmasını sorgular sağlar. İfade ağaçları LINQ hakkında daha fazla bilgi için bkz: [nasıl yapılır: dinamik sorgular derleme (Visual Basic) için kullanımı ifade ağaçları](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 İfade ağaçları, aynı zamanda dinamik diller ve .NET Framework birlikte çalışabilirliği sağlamak için ve Microsoft Ara dili (MSIL) yerine ifade ağaçları yaymak üzere derleyici yazıcılarının etkinleştirmek için dinamik dil çalışma zamanı (DLR) kullanılır. DLR hakkında daha fazla bilgi için bkz: [dinamik dil çalışma zamanına genel bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Bir ifade ağacına oluşturduğunuz bir anonim lambda ifadesi temelinde veya kullanarak ifade ağaçları el ile oluşturabilirsiniz için C# veya Visual Basic derleyici olabilir <xref:System.Linq.Expressions> ad alanı.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>İfade ağaçları gelen Lambda ifadeleri oluşturma  
 Lambda ifadesi türü değişkenine atanan zaman <xref:System.Linq.Expressions.Expression%601>, lambda ifadesi temsil eden bir ifade ağacına oluşturmak için kod derleyicisi yayar.  
  
 Visual Basic derleyici ifade ağaçları yalnızca ifade Lambda'lar (veya tek satırlık Lambda'lar) oluşturabilirsiniz. Deyimi Lambda'lar (veya birden çok satırlı lambda) ayrıştırılamıyor. Visual Basic'te lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Aşağıdaki kod örneği temsil eden lambda ifadesi bir ifade ağacına oluşturma Visual Basic derleyici nasıl göstermek `Function(num) num < 5`.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>İfade ağaçları API'yi kullanarak oluşturma  
 İfade ağaçları API'yi kullanarak oluşturmak için kullanın <xref:System.Linq.Expressions.Expression> sınıfı. Bu sınıf belirli türlerinin ağaç düğümleri ifade oluşturun; Örneğin, statik Fabrika yöntemler içerir <xref:System.Linq.Expressions.ParameterExpression>, temsil eden bir değişken ya da parametre veya <xref:System.Linq.Expressions.MethodCallExpression>, yöntem çağrısı temsil eder. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer ifade özgü türleri de tanımlanan <xref:System.Linq.Expressions> ad alanı. Bu tür soyut türden türetilmiş <xref:System.Linq.Expressions.Expression>.  
  
 Aşağıdaki kod örneğinde nasıl temsil eden lambda ifadesi bir ifade ağacına oluşturulduğunu gösteren `Function(num) num < 5` API'yi kullanarak.  
  
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
  
 .NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API de atamaları ve denetim akışı ifadeleri döngüler, koşullu blokları gibi destekler ve `try-catch` engeller. API'yi kullanarak gelen lambda ifadeleri Visual Basic derleyici tarafından oluşturulabilen olandan daha karmaşık ifade ağaçları oluşturabilirsiniz. Aşağıdaki örnek, bir sayı çarpımını hesaplar bir ifade ağacına oluşturmak gösterilmiştir.  
  
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

Daha fazla bilgi için bkz: [oluşturma dinamik yöntemler ifade ağaçları Visual Studio 2010 ile](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010), Visual Studio'nun daha yeni sürümleri da geçerli.
  
## <a name="parsing-expression-trees"></a>İfade ağaçları ayrıştırma  
 Aşağıdaki kod örneğinde nasıl ifade ağaç, gösterilmektedir temsil eden lambda ifadesi `Function(num) num < 5` , bölümlere ayrılmış.  
  
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
  
## <a name="immutability-of-expression-trees"></a>İfade ağaçları girişi  
 İfade ağaçları sabit olmalı. Bu, bir ifade ağacına değiştirmek istiyorsanız, yeni bir ifade ağacına mevcut kopyalayarak ve bu düğümler değiştirme oluşturmalıdır, anlamına gelir. Bir ifade ağacına ziyaretçi varolan ifade ağacına gezme için kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: ifade ağaçlarını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>İfade ağaçları derleme  
 <xref:System.Linq.Expressions.Expression%601> Türü sağlar <xref:System.Linq.Expressions.Expression%601.Compile%2A> yürütülebilir bir temsilci bir ifade ağacına tarafından temsil edilen kodu derler yöntemi.  
  
 Aşağıdaki kod örneği, bir ifade ağacına derlemek ve ortaya çıkan kodu çalıştırmak gösterilmiştir.  
  
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
  
 Daha fazla bilgi için bkz: [nasıl yapılır: ifade ağaçlarını yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.Expressions>  
 [Nasıl yapılır: ifade ağaçlarını (Visual Basic) yürütme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Nasıl yapılır: ifade ağaçlarını (Visual Basic) değiştirme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [Lambda İfadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Dinamik Dil Çalışma Zamanına Genel Bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
 [Programlama Kavramları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
