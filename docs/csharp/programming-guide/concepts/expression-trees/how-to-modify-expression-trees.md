---
title: İfade ağaçlarını değiştirme (C#)
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: e921c594497d02f5eb16cc60294e947e83636d7a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969897"
---
# <a name="how-to-modify-expression-trees-c"></a>İfade ağaçlarını değiştirme (C#)
Bu konu başlığı altında, bir ifade ağacının nasıl değiştirileceği gösterilmektedir. İfade ağaçları sabittir ve bu, doğrudan değiştirilemediği anlamına gelir. Bir ifade ağacını değiştirmek için, var olan bir ifade ağacının bir kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir. <xref:System.Linq.Expressions.ExpressionVisitor> sınıfını, var olan bir ifade ağacında çapraz geçiş yapmak ve bulduğu her düğümü kopyalamak için kullanabilirsiniz.  
  
### <a name="to-modify-an-expression-tree"></a>Bir ifade ağacını değiştirmek için  
  
1. Yeni bir **konsol uygulaması** projesi oluşturun.  
  
2. `System.Linq.Expressions` ad alanı için dosyaya bir `using` yönergesi ekleyin.  
  
3. `AndAlsoModifier` sınıfını projenize ekleyin.  
  
    ```csharp  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     Bu sınıf <xref:System.Linq.Expressions.ExpressionVisitor> sınıfını devralır ve koşullu `AND` işlemlerini temsil eden ifadeleri değiştirmek için özelleştirilmiştir. Bu işlemleri koşullu bir `AND` koşullu `OR`olarak değiştirir. Bunu yapmak için, koşullu `AND` ifadeler ikili ifadeler olarak temsil edildiği için sınıf temel türün <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> yöntemini geçersiz kılar. `VisitBinary` yönteminde, kendisine geçirilen ifade koşullu bir `AND` işlemini gösteriyorsa, kod koşullu `AND` işleci yerine koşullu `OR` işlecini içeren yeni bir ifade oluşturur. `VisitBinary` geçirilen ifade koşullu `AND` işlemini temsil ediyorsa, yöntemi temel sınıf uygulamasına erteler. Temel sınıf yöntemleri, geçirilen ifade ağaçları gibi düğümleri oluşturur, ancak düğümlerin alt ağaçları, ziyaretçi tarafından yinelemeli olarak üretilen ifade ağaçları ile değiştirilmiştir.  
  
4. `System.Linq.Expressions` ad alanı için dosyaya bir `using` yönergesi ekleyin.  
  
5. Bir ifade ağacı oluşturmak ve bunu değiştirecek yönteme geçirmek için Program.cs dosyasındaki `Main` yöntemine kod ekleyin.  
  
    ```csharp  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     Kod, koşullu `AND` işlemi içeren bir ifade oluşturur. Daha sonra, `AndAlsoModifier` sınıfının bir örneğini oluşturur ve bu sınıfın `Modify` yöntemine ifadeyi geçirir. Hem özgün hem de değiştirilen ifade ağaçları değişikliği göstermek için çıktılardır.  
  
6. Uygulamayı derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçlarını yürütme (C#)](./how-to-execute-expression-trees.md)
- [İfade ağaçları (C#)](./index.md)
