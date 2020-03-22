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
# <a name="expression-trees-visual-basic"></a>İfade Ağaçları (Visual Basic)
İfade ağaçları, her düğümün bir ifade olduğu ağaç benzeri bir veri yapısındaki kodu temsil ediyor, örneğin bir yöntem çağrısı veya . gibi `x < y`ikili bir işlem.  
  
 İfade ağaçları tarafından temsil edilen kodu derleyebilir ve çalıştırabilirsiniz. Bu, yürütülebilir kodun dinamik olarak değiştirilmesini, çeşitli veritabanlarında LINQ sorgularının yürütülmesini ve dinamik sorguların oluşturulmasını sağlar. LINQ'daki ifade ağaçları hakkında daha fazla bilgi için [bkz: Dinamik Sorgular Oluşturmak için İfade Ağaçlarını Kullanın (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 İfade ağaçları, dinamik diller ve .NET Framework arasında birlikte çalışabilirlik sağlamak ve derleyici yazarların Microsoft ara dili (MSIL) yerine ifade ağaçları yayatmasını sağlamak için dinamik dil çalışma süresinde (DLR) de kullanılır. DLR hakkında daha fazla bilgi için [Dinamik Dil Çalışma Süresine Genel Bakış'a](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)bakın.  
  
 C# veya Visual Basic derleyicisinin anonim bir lambda ifadesine dayalı olarak sizin için bir ifade ağacı <xref:System.Linq.Expressions> oluşturmasını sağlayabilir veya ad alanını kullanarak ifade ağaçları el ile oluşturabilirsiniz.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Lambda İfadelerinden İfade Ağaçları Oluşturma  
 Bir lambda ifadesi bir tür <xref:System.Linq.Expressions.Expression%601>değişkenine atandığında, derleyici lambda ifadesini temsil eden bir ifade ağacı oluşturmak için kod yakar.  
  
 Visual Basic derleyicisi ifade ağaçları sadece ifade lambdas (veya tek satırlambdas) oluşturabilirsiniz. İfade lambdas (veya çok çizgili lambdas) ayrıştırılamaz. Visual Basic'teki lambda ifadeleri hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
  
 Aşağıdaki kod örnekleri, Visual Basic derleyicisinin lambda ifadesini `Function(num) num < 5`temsil eden bir ifade ağacı oluşturmasını gösterir.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>API'yi Kullanarak İfade Ağaçları Oluşturma  
 API'yi kullanarak ifade ağaçları oluşturmak <xref:System.Linq.Expressions.Expression> için sınıfı kullanın. Bu sınıf, örneğin, <xref:System.Linq.Expressions.ParameterExpression>bir değişken veya parametreyi temsil eden veya <xref:System.Linq.Expressions.MethodCallExpression>bir yöntem çağrısını temsil eden, belirli türlerdeki ifade ağacı düğümlerini oluşturan statik fabrika yöntemleri içerir. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer ifadeye özgü türleri <xref:System.Linq.Expressions> de ad alanında tanımlanır. Bu tür soyut türünden <xref:System.Linq.Expressions.Expression>türetilmiştir.  
  
 Aşağıdaki kod örneği, API'yi kullanarak lambda ifadesini `Function(num) num < 5` temsil eden bir ifade ağacının nasıl oluşturulabildiğini gösterir.  
  
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
  
 .NET Framework 4 veya sonraki durumlarda, ifade ağaçları API ayrıca döngüler, koşullu bloklar `try-catch` ve bloklar gibi atamaları ve denetim akış ifadelerini destekler. API'yi kullanarak, Visual Basic derleyicisi tarafından lambda ifadelerinden oluşturulabilen ifadelerden daha karmaşık ifade ağaçları oluşturabilirsiniz. Aşağıdaki örnek, bir sayının faktöriyelini hesaplayan bir ifade ağacının nasıl oluşturulabildiğini gösterir.  
  
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

Daha fazla bilgi için Visual [Studio 2010'da İfade Ağaçlarıyla Dinamik Yöntemler Oluşturma](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/)bölümüne bakın ve bu yöntemler Visual Studio'nun sonraki sürümleri için de geçerlidir.
  
## <a name="parsing-expression-trees"></a>Ayrışma İfade Ağaçları  
 Aşağıdaki kod örneği, lambda ifadesini `Function(num) num < 5` temsil eden ifade ağacının parçalarına nasıl ayrıştırılabildiğini gösterir.  
  
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
  
## <a name="immutability-of-expression-trees"></a>İfade Ağaçlarının Değişmezliği  
 İfade ağaçları değişmez olmalıdır. Bu, bir ifade ağacını değiştirmek istiyorsanız, varolan bir ifadeyi kopyalayarak ve düğümleri değiştirerek yeni bir ifade ağacı oluşturmanız gerektiği anlamına gelir. Varolan ifade ağacını geçmek için bir ifade ağacı ziyaretçisi kullanabilirsiniz. Daha fazla bilgi için [bkz: İfade Ağaçlarını Değiştir (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>İfade Ağaçlarını Derleme  
 Tür, <xref:System.Linq.Expressions.Expression%601> bir <xref:System.Linq.Expressions.Expression%601.Compile%2A> ifade ağacı tarafından temsil edilen kodu yürütülebilir bir temsilciye derleyen yöntemi sağlar.  
  
 Aşağıdaki kod örneği, bir ifade ağacının nasıl derlenebildiğini ve ortaya çıkan kodunasıl çalıştırılabildiğini gösterir.  
  
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
  
 Daha fazla bilgi için [bkz: İfade Ağaçlarını Yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Expressions>
- [Nasıl Yapılır: İfade Ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Nasıl Yapılır: İfade Ağaçlarını Değiştir (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [Lambda İfadeler](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Dinamik Dil Çalışma Süresine Genel Bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Programlama Kavramları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
