---
title: İfade ağaçları (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: f17b4fba92c502ca6d53fef7ac6d01f2fdefc02e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526871"
---
# <a name="expression-trees-c"></a>İfade ağaçları (C#)
İfade ağaçları her bir düğümü olduğu bir ifade, örneğin bir ağaç benzeri veri yapısı, bir yöntem çağrısı veya bir ikili işlem kodu gibi temsil eden `x < y`.  
  
 Derleme ve ifade ağaçları tarafından temsil edilen kodu çalıştırın. Bu, çeşitli veritabanları ve dinamik sorgular oluşturulmasını yürütme LINQ sorguları yürütülebilir kodun dinamik değişikliğini sağlar. LINQ ifade ağaçları hakkında daha fazla bilgi için bkz: [nasıl yapılır: dinamik sorgular (C#) derleme kullan ifade ağaçlarına](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 İfade ağaçları ayrıca dinamik dil çalışma zamanı (DLR) dinamik dilleri ve .NET Framework arasında birlikte çalışabilirliği sağlamak ve Microsoft Ara dilini (MSIL) yerine ifade ağaçları yaymak derleyici yazıcıları etkinleştirmek için kullanılır. DLR hakkında daha fazla bilgi için bkz: [dinamik dil çalışma zamanına genel bakış](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Bir lambda anonim ifadeye dayalı veya kullanarak, el ile bir ifade ağaçları oluşturabilirsiniz bir ifade ağacı oluşturma C# veya Visual Basic derleyici olabilir <xref:System.Linq.Expressions> ad alanı.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Gelen Lambda ifadeleri ifade ağaçları oluşturma  
 Bir lambda ifadesi türden bir değişkene atanmış zaman <xref:System.Linq.Expressions.Expression%601>, derleyici lambda ifadeyi temsil eden bir ifade ağacı oluşturmak için kod gösterir.  
  
 C# derleyicisi, ifade ağaçları yalnızca ifade lambdaları (veya tek satırlı lambdalar) oluşturabilirsiniz. Deyim lambdaları (veya çok satırlı lambdalar) ayrıştırılamıyor. C# ' deki lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Aşağıdaki kod örnekleri, C# Derleyici lambda ifadeyi temsil eden bir ifade ağacı oluşturmak göstermektedir `num => num < 5`.  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>İfade ağaçları API'sini kullanarak oluşturma  
 İfade ağaçları API'sini kullanarak oluşturmak için kullanın <xref:System.Linq.Expressions.Expression> sınıfı. Bu sınıf, ağaç düğümleri belirli türlerin ifade oluşturun, örneğin, statik Fabrika yöntemleri içerir. <xref:System.Linq.Expressions.ParameterExpression>, temsil eden bir değişken veya parametre, veya <xref:System.Linq.Expressions.MethodCallExpression>, bir yöntem çağrısını temsil eder. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer özel ifade türleri ayrıca tanımlanan <xref:System.Linq.Expressions> ad alanı. Bu tür soyut türünden türetilmesi <xref:System.Linq.Expressions.Expression>.  
  
 Aşağıdaki kod örneği temsil eden lambda ifadesi ifade ağacı oluşturma işlemini gösterir `num => num < 5` API'yi kullanarak.  
  
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
  
 .NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API aynı zamanda atamaları ve Döngüler, koşullu blokları gibi denetim akışı ifadeler destekler ve `try-catch` engeller. API'yi kullanarak gelen lambda ifadeleri için C# Derleyici tarafından oluşturulan olandan daha karmaşık bir ifade ağaçları oluşturabilirsiniz. Aşağıdaki örnek, bir sayının faktöriyelini hesaplar bir ifade ağacı oluşturma işlemini gösterir.  
  
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

Daha fazla bilgi için [oluşturma dinamik yöntemler ifade ağaçlarında Visual Studio 2010 ile](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), Visual Studio'nun daha sonraki sürümlere da geçerli.
  
## <a name="parsing-expression-trees"></a>İfade ağaçları ayrıştırma  
 Aşağıdaki kod örneğinde nasıl ifade ağacı, gösterir temsil eden lambda ifadesi `num => num < 5` parçasına ayrıştırıldı.  
  
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
  
## <a name="immutability-of-expression-trees"></a>İfade ağaçları değiştirilemezlik  
 İfade ağaçları sabit olmalıdır. Bu, bir ifade ağacı değiştirmek istiyorsanız, size yeni bir ifade ağacı var olan bir kopyalama ve bu düğümler değiştirerek oluşturmalıdır, anlamına gelir. Bir ifade ağacı ziyaretçi var olan bir ifade ağacı geçirmek için kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: ifade ağaçlarını değiştirme (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>İfade ağaçları derleme  
 <xref:System.Linq.Expressions.Expression%601> Sağlayan türü <xref:System.Linq.Expressions.Expression%601.Compile%2A> yürütülebilir bir temsilciye bir ifade ağacı tarafından temsil edilen kod derlenir yöntemi.  
  
 Aşağıdaki kod örneği, bir ifade ağacı derlemek ve sonuç kodu çalıştırmak gösterilmektedir.  
  
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
  
 Daha fazla bilgi için [nasıl yapılır: ifade ağaçlarını yürütme (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Linq.Expressions>  
- [Nasıl yapılır: ifade ağaçlarını (C#) yürütme](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
- [Nasıl yapılır: ifade ağaçlarını (C#) değiştirme](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
- [Lambda İfadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Dinamik Dil Çalışma Zamanına Genel Bakış](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
- [Programlama Kavramları (C#)](../../../../csharp/programming-guide/concepts/index.md)
