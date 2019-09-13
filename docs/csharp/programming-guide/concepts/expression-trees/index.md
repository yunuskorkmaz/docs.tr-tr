---
title: İfade ağaçları (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 7e63bf28f10070daa9624daa67bd5118fa67874d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926723"
---
# <a name="expression-trees-c"></a>İfade ağaçları (C#)
İfade ağaçları, her düğümün bir ifade olduğu, örneğin bir yöntem çağrısı veya gibi `x < y`bir ikili işlem olduğu ağaç benzeri bir veri yapısında kodu temsil eder.  
  
 İfade ağaçları ile temsil edilen kodu derleyebilir ve çalıştırabilirsiniz. Bu, yürütülebilir kodun dinamik olarak değiştirilmesini, çeşitli veritabanlarındaki LINQ sorgularının yürütülmesini ve dinamik sorguların oluşturulmasını mümkün bir şekilde sunar. LINQ 'teki ifade ağaçları hakkında daha fazla bilgi için bkz [. nasıl yapılır: Dinamik sorgular oluşturmak için Ifade ağaçları kullanın (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 İfade ağaçları ayrıca dinamik diller ve .NET Framework arasında birlikte çalışabilirlik sağlamak ve derleyici yazıcılarının Microsoft ara dili (MSIL) yerine ifade ağaçları sunmak için dinamik dil çalışma zamanı (DLR) içinde de kullanılır. DLR hakkında daha fazla bilgi için bkz. [dinamik dil çalışma zamanına genel bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 C# Veya Visual Basic derleyicisinin anonim lambda ifadesine göre sizin için bir ifade ağacı oluşturmasını sağlayabilir veya <xref:System.Linq.Expressions> ad alanını kullanarak el ile ifade ağaçları oluşturabilirsiniz.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Lambda Ifadelerinden Ifade ağaçları oluşturma  
 Lambda ifadesi türünde <xref:System.Linq.Expressions.Expression%601>bir değişkene atandığında, derleyici lambda ifadesini temsil eden bir ifade ağacı oluşturmak için kodu yayar.  
  
 C# Derleyici yalnızca ifade lambdaları (veya tek satırlık Lambdalar) için ifade ağaçları oluşturabilir. İfade lambdaları (veya çok satırlı Lambdalar) ayrıştırılamaz. İçindeki C#lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../statements-expressions-operators/lambda-expressions.md).  
  
 Aşağıdaki kod örnekleri, C# derleyicinin lambda ifadesini `num => num < 5`temsil eden bir ifade ağacının nasıl oluşturulduğunu gösterir.  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>API kullanarak Ifade ağaçları oluşturma  
 API kullanarak ifade ağaçları oluşturmak için <xref:System.Linq.Expressions.Expression> sınıfını kullanın. Bu sınıf, bir değişken veya parametre temsil eden veya <xref:System.Linq.Expressions.ParameterExpression> <xref:System.Linq.Expressions.MethodCallExpression>bir yöntem çağrısını temsil eden belirli türlerin ifade ağacı düğümlerini oluşturan statik fabrika yöntemleri içerir. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>ve diğer ifadeye özgü türler de <xref:System.Linq.Expressions> ad alanında tanımlanmıştır. Bu türler soyut türden <xref:System.Linq.Expressions.Expression>türetilir.  
  
 Aşağıdaki kod örneğinde, API kullanarak lambda ifadesini `num => num < 5` temsil eden bir ifade ağacının nasıl oluşturulacağı gösterilmektedir.  
  
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
  
 .NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API 'si, döngüleri, koşullu blokları ve `try-catch` blokları gibi atamaları ve denetim akışı ifadelerini de destekler. API 'yi kullanarak, C# derleyici tarafından lambda ifadelerinden oluşturulanlardan daha karmaşık ifade ağaçları oluşturabilirsiniz. Aşağıdaki örnek, bir sayının faktöriyelini hesaplayan bir ifade ağacının nasıl oluşturulacağını göstermektedir.  
  
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

Daha fazla bilgi için bkz. Visual Studio 'nun sonraki sürümleri için de geçerli olan [Visual studio 2010 ' de Ifade ağaçları Ile dinamik yöntemler üretme](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/).
  
## <a name="parsing-expression-trees"></a>Ifade ağaçlarını ayrıştırma  
 Aşağıdaki kod örneği, lambda ifadesini `num => num < 5` temsil eden ifade ağacının parçalar halinde nasıl birleştirilebileceğini gösterir.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Ifade ağaçlarının dengeszlik düzeyini bilme  
 İfade ağaçları sabit olmalıdır. Yani, bir ifade ağacını değiştirmek istiyorsanız, var olan birini kopyalayarak ve içindeki düğümleri değiştirerek yeni bir ifade ağacı oluşturmanız gerekir. Varolan ifade ağacında çapraz geçiş yapmak için bir ifade ağacı Visitor kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Ifade ağaçlarını (C#)](./how-to-modify-expression-trees.md)değiştirin.  
  
## <a name="compiling-expression-trees"></a>Ifade ağaçlarını derleme  
 Türü, bir ifade <xref:System.Linq.Expressions.Expression%601.Compile%2A> ağacı tarafından temsil edilen kodu bir çalıştırılabilir temsilciye derlenen yöntemi sağlar. <xref:System.Linq.Expressions.Expression%601>  
  
 Aşağıdaki kod örneği, bir ifade ağacının nasıl derlendiğini ve sonuçta elde edilen kodu nasıl çalıştıracağınızı gösterir.  
  
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
  
 Daha fazla bilgi için [nasıl yapılır: Ifade ağaçları (C#)](./how-to-execute-expression-trees.md)yürütün.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Expressions>
- [Nasıl yapılır: Ifade ağaçlarını yürütme (C#)](./how-to-execute-expression-trees.md)
- [Nasıl yapılır: Ifade ağaçlarını değiştirme (C#)](./how-to-modify-expression-trees.md)
- [Lambda İfadeleri](../../statements-expressions-operators/lambda-expressions.md)
- [Dinamik Dil Çalışma Zamanına Genel Bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Programlama kavramları (C#)](../index.md)
