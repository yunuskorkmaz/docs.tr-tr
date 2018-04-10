---
title: İfade ağaçları (C#)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5554b9e923b0cc1da4906cda1b7ca4e6aac75f11
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2018
---
# <a name="expression-trees-c"></a>İfade ağaçları (C#)
İfade ağaçları her düğüm olduğu bir ifade, örneğin bir ağaç benzeri veri yapısı, bir yöntem çağrısı veya bir ikili işlem kodu gibi temsil eden `x < y`.  
  
 Derleme ve ifade ağaçları tarafından temsil edilen kodu çalıştırın. Bu, dinamik yürütülebilir kodunun değiştirilmesini LINQ yürütülmesi çeşitli veritabanları ve dinamik sorgular oluşturulmasını sorgular sağlar. İfade ağaçları LINQ hakkında daha fazla bilgi için bkz: [nasıl yapılır: dinamik sorgular (C#) oluşturmak için ifade ağaçları kullanma](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 İfade ağaçları, aynı zamanda dinamik diller ve .NET Framework birlikte çalışabilirliği sağlamak için ve Microsoft Ara dili (MSIL) yerine ifade ağaçları yaymak üzere derleyici yazıcılarının etkinleştirmek için dinamik dil çalışma zamanı (DLR) kullanılır. DLR hakkında daha fazla bilgi için bkz: [dinamik dil çalışma zamanına genel bakış](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Bir ifade ağacına oluşturduğunuz bir anonim lambda ifadesi temelinde veya kullanarak ifade ağaçları el ile oluşturabilirsiniz için C# veya Visual Basic derleyici olabilir <xref:System.Linq.Expressions> ad alanı.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>İfade ağaçları gelen Lambda ifadeleri oluşturma  
 Lambda ifadesi türü değişkenine atanan zaman <xref:System.Linq.Expressions.Expression%601>, lambda ifadesi temsil eden bir ifade ağacına oluşturmak için kod derleyicisi yayar.  
  
 C# Derleyici ifade ağaçları yalnızca ifade Lambda'lar (veya tek satırlık Lambda'lar) oluşturabilirsiniz. Deyimi Lambda'lar (veya birden çok satırlı lambda) ayrıştırılamıyor. C# ' deki lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Aşağıdaki kod örneği temsil eden lambda ifadesi bir ifade ağacına oluşturmak C# Derleyici nasıl göstermek `num => num < 5`.  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>İfade ağaçları API'yi kullanarak oluşturma  
 İfade ağaçları API'yi kullanarak oluşturmak için kullanın <xref:System.Linq.Expressions.Expression> sınıfı. Bu sınıf belirli türlerinin ağaç düğümleri ifade oluşturun; Örneğin, statik Fabrika yöntemler içerir <xref:System.Linq.Expressions.ParameterExpression>, temsil eden bir değişken ya da parametre veya <xref:System.Linq.Expressions.MethodCallExpression>, yöntem çağrısı temsil eder. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, ve diğer ifade özgü türleri de tanımlanan <xref:System.Linq.Expressions> ad alanı. Bu tür soyut türden türetilmiş <xref:System.Linq.Expressions.Expression>.  
  
 Aşağıdaki kod örneğinde nasıl temsil eden lambda ifadesi bir ifade ağacına oluşturulduğunu gösteren `num => num < 5` API'yi kullanarak.  
  
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
  
 .NET Framework 4 veya sonraki sürümlerde, ifade ağaçları API de atamaları ve denetim akışı ifadeleri döngüler, koşullu blokları gibi destekler ve `try-catch` engeller. API'yi kullanarak gelen lambda ifadeleri C# Derleyici tarafından oluşturulabilen olandan daha karmaşık ifade ağaçları oluşturabilirsiniz. Aşağıdaki örnek, bir sayı çarpımını hesaplar bir ifade ağacına oluşturmak gösterilmiştir.  
  
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

Daha fazla bilgi için bkz: [oluşturma dinamik yöntemler ifade ağaçları Visual Studio 2010 ile](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), Visual Studio'nun daha yeni sürümleri da geçerli.
  
## <a name="parsing-expression-trees"></a>İfade ağaçları ayrıştırma  
 Aşağıdaki kod örneğinde nasıl ifade ağaç, gösterilmektedir temsil eden lambda ifadesi `num => num < 5` , bölümlere ayrılmış.  
  
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
  
## <a name="immutability-of-expression-trees"></a>İfade ağaçları girişi  
 İfade ağaçları sabit olmalı. Bu, bir ifade ağacına değiştirmek istiyorsanız, yeni bir ifade ağacına mevcut kopyalayarak ve bu düğümler değiştirme oluşturmalıdır, anlamına gelir. Bir ifade ağacına ziyaretçi varolan ifade ağacına gezme için kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: ifade ağaçlarını değiştirme (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>İfade ağaçları derleme  
 <xref:System.Linq.Expressions.Expression%601> Türü sağlar <xref:System.Linq.Expressions.Expression%601.Compile%2A> yürütülebilir bir temsilci bir ifade ağacına tarafından temsil edilen kodu derler yöntemi.  
  
 Aşağıdaki kod örneği, bir ifade ağacına derlemek ve ortaya çıkan kodu çalıştırmak gösterilmiştir.  
  
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
  
 Daha fazla bilgi için bkz: [nasıl yapılır: ifade ağaçlarını yürütme (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.Expressions>  
 [Nasıl yapılır: ifade ağaçlarını (C#) yürütme](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Nasıl yapılır: ifade ağaçlarını (C#) değiştirme](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [Lambda İfadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Dinamik Dil Çalışma Zamanına Genel Bakış](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
 [Programlama Kavramları (C#)](../../../../csharp/programming-guide/concepts/index.md)
