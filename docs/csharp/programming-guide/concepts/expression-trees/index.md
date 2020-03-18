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
# <a name="expression-trees-c"></a>İfade Ağaçları (C#)
İfade ağaçları, her düğümün bir ifade olduğu ağaç benzeri bir veri yapısındaki kodu temsil ediyor, örneğin bir yöntem çağrısı veya . gibi `x < y`ikili bir işlem.  
  
 İfade ağaçları tarafından temsil edilen kodu derleyebilir ve çalıştırabilirsiniz. Bu, yürütülebilir kodun dinamik olarak değiştirilmesini, çeşitli veritabanlarında LINQ sorgularının yürütülmesini ve dinamik sorguların oluşturulmasını sağlar. LINQ'daki ifade ağaçları hakkında daha fazla bilgi [için, dinamik sorgular (C#) oluşturmak için ifade ağaçlarının nasıl kullanılacağına](./how-to-use-expression-trees-to-build-dynamic-queries.md)bakın.
  
 İfade ağaçları, dinamik diller ve .NET Framework arasında birlikte çalışabilirlik sağlamak ve derleyici yazarların Microsoft ara dili (MSIL) yerine ifade ağaçları yayatmasını sağlamak için dinamik dil çalışma süresinde (DLR) de kullanılır. DLR hakkında daha fazla bilgi için [Dinamik Dil Çalışma Süresine Genel Bakış'a](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)bakın.  
  
 C# veya Visual Basic derleyicisinin anonim bir lambda ifadesine dayalı olarak sizin için bir ifade ağacı <xref:System.Linq.Expressions> oluşturmasını sağlayabilir veya ad alanını kullanarak ifade ağaçları el ile oluşturabilirsiniz.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Lambda İfadelerinden İfade Ağaçları Oluşturma  
 Bir lambda ifadesi bir tür <xref:System.Linq.Expressions.Expression%601>değişkenine atandığında, derleyici lambda ifadesini temsil eden bir ifade ağacı oluşturmak için kod yakar.  
  
 C# derleyicisi ifade ağaçları sadece ifade lambdas (veya tek satırlambdas) üretebilir. İfade lambdas (veya çok çizgili lambdas) ayrıştırılamaz. C#'daki lambda ifadeleri hakkında daha fazla bilgi için [Lambda İfadeleri'ne](../../statements-expressions-operators/lambda-expressions.md)bakın.  
  
 Aşağıdaki kod örnekleri, C# derleyicisinin lambda ifadesini `num => num < 5`temsil eden bir ifade ağacı oluşturmasını gösterir.  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>API'yi Kullanarak İfade Ağaçları Oluşturma  
 API'yi kullanarak ifade ağaçları oluşturmak <xref:System.Linq.Expressions.Expression> için sınıfı kullanın. Bu sınıf, örneğin, <xref:System.Linq.Expressions.ParameterExpression>bir değişken veya parametreyi temsil eden veya <xref:System.Linq.Expressions.MethodCallExpression>bir yöntem çağrısını temsil eden, belirli türlerdeki ifade ağacı düğümlerini oluşturan statik fabrika yöntemleri içerir. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer ifadeye özgü türleri <xref:System.Linq.Expressions> de ad alanında tanımlanır. Bu tür soyut türünden <xref:System.Linq.Expressions.Expression>türetilmiştir.  
  
 Aşağıdaki kod örneği, API'yi kullanarak lambda ifadesini `num => num < 5` temsil eden bir ifade ağacının nasıl oluşturulabildiğini gösterir.  
  
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
  
 .NET Framework 4 veya sonraki durumlarda, ifade ağaçları API ayrıca döngüler, koşullu bloklar `try-catch` ve bloklar gibi atamaları ve denetim akış ifadelerini destekler. API'yi kullanarak, C# derleyicisi tarafından lambda ifadelerinden oluşturulabilenifadelerden daha karmaşık ifade ağaçları oluşturabilirsiniz. Aşağıdaki örnek, bir sayının faktöriyelini hesaplayan bir ifade ağacının nasıl oluşturulabildiğini gösterir.  
  
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

Daha fazla bilgi için Visual [Studio 2010'da İfade Ağaçlarıyla Dinamik Yöntemler Oluşturma](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/)bölümüne bakın ve bu yöntemler Visual Studio'nun sonraki sürümleri için de geçerlidir.
  
## <a name="parsing-expression-trees"></a>Ayrışma İfade Ağaçları  
 Aşağıdaki kod örneği, lambda ifadesini `num => num < 5` temsil eden ifade ağacının parçalarına nasıl ayrıştırılabildiğini gösterir.  
  
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
  
## <a name="immutability-of-expression-trees"></a>İfade Ağaçlarının Değişmezliği  
 İfade ağaçları değişmez olmalıdır. Bu, bir ifade ağacını değiştirmek istiyorsanız, varolan bir ifadeyi kopyalayarak ve düğümleri değiştirerek yeni bir ifade ağacı oluşturmanız gerektiği anlamına gelir. Varolan ifade ağacını geçmek için bir ifade ağacı ziyaretçisi kullanabilirsiniz. Daha fazla bilgi için [ifade ağaçlarını (C#) nasıl değiştirebilirsiniz'](./how-to-modify-expression-trees.md)e bakın.
  
## <a name="compiling-expression-trees"></a>İfade Ağaçlarını Derleme  
 Tür, <xref:System.Linq.Expressions.Expression%601> bir <xref:System.Linq.Expressions.Expression%601.Compile%2A> ifade ağacı tarafından temsil edilen kodu yürütülebilir bir temsilciye derleyen yöntemi sağlar.  
  
 Aşağıdaki kod örneği, bir ifade ağacının nasıl derlenebildiğini ve ortaya çıkan kodunasıl çalıştırılabildiğini gösterir.  
  
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
  
 Daha fazla bilgi için [ifade ağaçlarının (C#) nasıl yürütüldürüne](./how-to-execute-expression-trees.md)bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Expressions>
- [İfade ağaçları nasıl yürütülür (C#)](./how-to-execute-expression-trees.md)
- [İfade ağaçları nasıl değiştirilir (C#)](./how-to-modify-expression-trees.md)
- [Lambda İfadeler](../../statements-expressions-operators/lambda-expressions.md)
- [Dinamik Dil Çalışma Süresine Genel Bakış](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Programlama Kavramları (C#)](../index.md)
