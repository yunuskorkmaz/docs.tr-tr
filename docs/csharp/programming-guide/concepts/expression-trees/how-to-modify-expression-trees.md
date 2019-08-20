---
title: 'Nasıl yapılır: Ifade ağaçlarını değiştirme (C#)'
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 7875cf1ccca8866cc87ebec80701ad77ad2bea2d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595063"
---
# <a name="how-to-modify-expression-trees-c"></a>Nasıl yapılır: Ifade ağaçlarını değiştirme (C#)
Bu konu başlığı altında, bir ifade ağacının nasıl değiştirileceği gösterilmektedir. İfade ağaçları sabittir ve bu, doğrudan değiştirilemediği anlamına gelir. Bir ifade ağacını değiştirmek için, var olan bir ifade ağacının bir kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir. Sınıfını, <xref:System.Linq.Expressions.ExpressionVisitor> var olan bir ifade ağacında çapraz geçiş yapmak ve bulduğu her düğümü kopyalamak için kullanabilirsiniz.  
  
### <a name="to-modify-an-expression-tree"></a>Bir ifade ağacını değiştirmek için  
  
1. Yeni bir **konsol uygulaması** projesi oluşturun.  
  
2. Ad`System.Linq.Expressions` alanı `using` için dosyasına bir yönerge ekleyin.  
  
3. `AndAlsoModifier` Sınıfını projenize ekleyin.  
  
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
  
     Bu sınıf <xref:System.Linq.Expressions.ExpressionVisitor> sınıfını devralır ve koşullu `AND` işlemleri temsil eden ifadeleri değiştirmek için özelleştirilmiştir. Bu işlemleri koşullu `AND` sunucudan koşullu `OR`olarak değiştirir. Bunu yapmak için, koşullu <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> `AND` ifadeler ikili ifadeler olarak temsil edildiği için sınıf temel tür yöntemini geçersiz kılar. Yönteminde, kendisine geçirilen ifade koşullu `AND` bir işlemi temsil ediyorsa, kod koşullu `OR` işleci `AND` içeren yeni bir ifade oluşturur `VisitBinary` işlecinde. Geçirilen `VisitBinary` ifade koşullu `AND` bir işlemi temsil ediyorsa, yöntemi temel sınıf uygulamasına erteler. Temel sınıf yöntemleri, geçirilen ifade ağaçları gibi düğümleri oluşturur, ancak düğümlerin alt ağaçları, ziyaretçi tarafından yinelemeli olarak üretilen ifade ağaçları ile değiştirilmiştir.  
  
4. Ad`System.Linq.Expressions` alanı `using` için dosyasına bir yönerge ekleyin.  
  
5. Program.cs dosyasındaki `Main` yöntemine kod ekleyerek bir ifade ağacı oluşturun ve bunu değiştirecek yönteme geçirin.  
  
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
  
     Kod, koşullu `AND` bir işlem içeren bir ifade oluşturur. Daha sonra `AndAlsoModifier` sınıfın bir örneğini oluşturur ve bu sınıfın `Modify` yöntemine ifadeyi geçirir. Hem özgün hem de değiştirilen ifade ağaçları değişikliği göstermek için çıktılardır.  
  
6. Uygulamayı derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Ifade ağaçlarını yürütme (C#)](./how-to-execute-expression-trees.md)
- [İfade ağaçları (C#)](./index.md)
