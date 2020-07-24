---
title: İfade ağaçlarını değiştirme (C#)
description: Varolan bir ifade ağacının kopyasını oluşturarak ve gerekli değişiklikleri yaparak bir ifade ağacını değiştirme hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 45aea18e253811d4e5c60f23f7f8496d4358f64c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105601"
---
# <a name="how-to-modify-expression-trees-c"></a>İfade ağaçlarını değiştirme (C#)
Bu konu başlığı altında, bir ifade ağacının nasıl değiştirileceği gösterilmektedir. İfade ağaçları sabittir ve bu, doğrudan değiştirilemediği anlamına gelir. Bir ifade ağacını değiştirmek için, var olan bir ifade ağacının bir kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir. <xref:System.Linq.Expressions.ExpressionVisitor>Sınıfını, var olan bir ifade ağacında çapraz geçiş yapmak ve bulduğu her düğümü kopyalamak için kullanabilirsiniz.  
  
### <a name="to-modify-an-expression-tree"></a>Bir ifade ağacını değiştirmek için  
  
1. Yeni bir **konsol uygulaması** projesi oluşturun.  
  
2. `using`Ad alanı için dosyasına bir yönerge ekleyin `System.Linq.Expressions` .  
  
3. `AndAlsoModifier`Sınıfını projenize ekleyin.  
  
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
  
     Bu sınıf sınıfını devralır <xref:System.Linq.Expressions.ExpressionVisitor> ve koşullu işlemleri temsil eden ifadeleri değiştirmek için özelleştirilmiştir `AND` . Bu işlemleri koşullu sunucudan `AND` koşullu olarak değiştirir `OR` . Bunu yapmak için, <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> koşullu `AND` ifadeler ikili ifadeler olarak temsil edildiği için sınıf temel tür yöntemini geçersiz kılar. `VisitBinary`Yönteminde, kendisine geçirilen ifade koşullu bir işlemi temsil ediyorsa `AND` , kod koşullu işleç yerine koşullu işleci içeren yeni bir ifade oluşturur `OR` `AND` . Geçirilen ifade `VisitBinary` koşullu bir işlemi temsil ediyorsa `AND` , yöntemi temel sınıf uygulamasına erteler. Temel sınıf yöntemleri, geçirilen ifade ağaçları gibi düğümleri oluşturur, ancak düğümlerin alt ağaçları, ziyaretçi tarafından yinelemeli olarak üretilen ifade ağaçları ile değiştirilmiştir.  
  
4. `using`Ad alanı için dosyasına bir yönerge ekleyin `System.Linq.Expressions` .  
  
5. `Main`Program.cs dosyasındaki yöntemine kod ekleyerek bir ifade ağacı oluşturun ve bunu değiştirecek yönteme geçirin.  
  
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
  
     Kod, koşullu bir işlem içeren bir ifade oluşturur `AND` . Daha sonra sınıfın bir örneğini oluşturur `AndAlsoModifier` ve `Modify` Bu sınıfın yöntemine ifadeyi geçirir. Hem özgün hem de değiştirilen ifade ağaçları değişikliği göstermek için çıktılardır.  
  
6. Uygulamayı derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçlarını yürütme (C#)](./how-to-execute-expression-trees.md)
- [İfade ağaçları (C#)](./index.md)
