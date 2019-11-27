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
# <a name="expression-trees-visual-basic"></a>İfade ağaçları (Visual Basic)
İfade ağaçları, her düğümün bir ifade olduğu, örneğin bir yöntem çağrısı veya `x < y`gibi bir ikili işlem olduğu ağaç benzeri bir veri yapısında kodu temsil eder.  
  
 İfade ağaçları ile temsil edilen kodu derleyebilir ve çalıştırabilirsiniz. Bu, yürütülebilir kodun dinamik olarak değiştirilmesini, çeşitli veritabanlarındaki LINQ sorgularının yürütülmesini ve dinamik sorguların oluşturulmasını mümkün bir şekilde sunar. LINQ içindeki ifade ağaçları hakkında daha fazla bilgi için bkz. [nasıl yapılır: dinamik sorgular oluşturmak Için Ifade ağaçları kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 İfade ağaçları ayrıca dinamik diller ve .NET Framework arasında birlikte çalışabilirlik sağlamak ve derleyici yazıcılarının Microsoft ara dili (MSIL) yerine ifade ağaçları sunmak için dinamik dil çalışma zamanı (DLR) içinde de kullanılır. DLR hakkında daha fazla bilgi için bkz. [dinamik dil çalışma zamanına genel bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 C# Veya Visual Basic derleyicisinin anonim lambda ifadesine göre sizin için bir ifade ağacı oluşturmasını sağlayabilir veya <xref:System.Linq.Expressions> ad alanını kullanarak el ile ifade ağaçları oluşturabilirsiniz.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Lambda Ifadelerinden Ifade ağaçları oluşturma  
 Lambda ifadesi <xref:System.Linq.Expressions.Expression%601>türünde bir değişkene atandığında, derleyici lambda ifadesini temsil eden bir ifade ağacı oluşturmak için kodu yayar.  
  
 Visual Basic Derleyicisi yalnızca ifade lambdaları (veya tek satırlık Lambdalar) için ifade ağaçları oluşturabilir. İfade lambdaları (veya çok satırlı Lambdalar) ayrıştırılamaz. Visual Basic lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Aşağıdaki kod örnekleri, Visual Basic derleyicisinin `Function(num) num < 5`lambda ifadesini temsil eden bir ifade ağacının nasıl oluşturulduğunu gösterir.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>API kullanarak Ifade ağaçları oluşturma  
 API kullanarak ifade ağaçları oluşturmak için <xref:System.Linq.Expressions.Expression> sınıfını kullanın. Bu sınıf, bir değişken veya parametre temsil eden <xref:System.Linq.Expressions.ParameterExpression>, ya da bir yöntem çağrısını temsil eden <xref:System.Linq.Expressions.MethodCallExpression>gibi belirli türlerin ifade ağacı düğümlerini oluşturan statik fabrika yöntemleri içerir. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>ve diğer ifadeye özgü türler <xref:System.Linq.Expressions> ad alanında da tanımlanmıştır. Bu türler <xref:System.Linq.Expressions.Expression>soyut türünden türetilir.  
  
 Aşağıdaki kod örneği, API kullanarak `Function(num) num < 5` lambda ifadesini temsil eden bir ifade ağacının nasıl oluşturulacağını göstermektedir.  
  
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
  
 .NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API 'SI, döngüleri, koşullu blokları ve `try-catch` blokları gibi atamaları ve denetim akışı ifadelerini de destekler. API 'yi kullanarak, Visual Basic Derleyicisi tarafından lambda ifadelerinden oluşturulanlardan daha karmaşık ifade ağaçları oluşturabilirsiniz. Aşağıdaki örnek, bir sayının faktöriyelini hesaplayan bir ifade ağacının nasıl oluşturulacağını göstermektedir.  
  
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

Daha fazla bilgi için bkz. Visual Studio 'nun sonraki sürümleri için de geçerli olan [Visual studio 2010 ' de Ifade ağaçları Ile dinamik yöntemler üretme](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/).
  
## <a name="parsing-expression-trees"></a>Ifade ağaçlarını ayrıştırma  
 Aşağıdaki kod örneği, `Function(num) num < 5` lambda ifadesini temsil eden ifade ağacının bölümlerine nasıl parçalanacağını göstermektedir.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Ifade ağaçlarının dengeszlik düzeyini bilme  
 İfade ağaçları sabit olmalıdır. Yani, bir ifade ağacını değiştirmek istiyorsanız, var olan birini kopyalayarak ve içindeki düğümleri değiştirerek yeni bir ifade ağacı oluşturmanız gerekir. Varolan ifade ağacında çapraz geçiş yapmak için bir ifade ağacı Visitor kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Ifade ağaçlarını derleme  
 <xref:System.Linq.Expressions.Expression%601> türü, bir ifade ağacının temsil ettiği kodu yürütülebilir bir temsilciye derleyen <xref:System.Linq.Expressions.Expression%601.Compile%2A> yöntemini sağlar.  
  
 Aşağıdaki kod örneği, bir ifade ağacının nasıl derlendiğini ve sonuçta elde edilen kodu nasıl çalıştıracağınızı gösterir.  
  
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
  
 Daha fazla bilgi için bkz. [nasıl yapılır: yürütme Ifade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Expressions>
- [Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [Lambda İfadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Dinamik Dil Çalışma Zamanına Genel Bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Programlama kavramları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
