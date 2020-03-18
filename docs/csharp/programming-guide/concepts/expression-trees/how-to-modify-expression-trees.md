---
title: İfade ağaçları nasıl değiştirilir (C#)
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: e921c594497d02f5eb16cc60294e947e83636d7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73969897"
---
# <a name="how-to-modify-expression-trees-c"></a>İfade ağaçları nasıl değiştirilir (C#)
Bu konu, bir ifade ağacını nasıl değiştirilen gösterir. İfade ağaçları değişmezdir, bu da doğrudan değiştirilemedikleri anlamına gelir. İfade ağacını değiştirmek için varolan bir ifade ağacının kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir. <xref:System.Linq.Expressions.ExpressionVisitor> Sınıfı, varolan bir ifade ağacında geçiş yapmak ve ziyaret ettiği her düğümü kopyalamak için kullanabilirsiniz.  
  
### <a name="to-modify-an-expression-tree"></a>İfade ağacını değiştirmek için  
  
1. Yeni bir **Konsol Uygulaması** projesi oluşturun.  
  
2. Ad `using` alanı için dosyaya `System.Linq.Expressions` bir yönerge ekleyin.  
  
3. `AndAlsoModifier` Sınıfı projenize ekleyin.  
  
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
  
     Bu sınıf <xref:System.Linq.Expressions.ExpressionVisitor> sınıfı devralır ve koşullu `AND` işlemleri temsil eden ifadeleri değiştirmek için özelleştirilmiştir. Bu işlemleri koşulludan `AND` koşulluya `OR`değiştirir. Koşullu `AND` ifadeler ikili ifadeler <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> olarak temsil edilir, çünkü bunu yapmak için sınıf, temel türünün yöntemini geçersiz kılar. `VisitBinary` Yöntemde, ona geçirilen ifade koşullu `AND` bir işlemi temsil ediyorsa, kod koşullu `OR` `AND` işleç yerine koşullu işleci içeren yeni bir ifade içerir. Geçirilen ifade koşullu `VisitBinary` `AND` bir işlemi temsil etmiyorsa, yöntem taban sınıf uygulamasına erteler. Taban sınıf yöntemleri, ifade ağaçları gibi düğümler oluşturmak geçirilen, ancak düğümleri kendi alt ağaçları ziyaretçi tarafından özyinelemeli üretilen ifade ağaçları ile değiştirilir.  
  
4. Ad `using` alanı için dosyaya `System.Linq.Expressions` bir yönerge ekleyin.  
  
5. Bir ifade `Main` ağacı oluşturmak ve onu değiştirecek yönteme geçirmek için Program.cs dosyasındaki yönteme kod ekleyin.  
  
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
  
     Kod koşullu `AND` bir işlem içeren bir ifade oluşturur. Daha sonra `AndAlsoModifier` sınıfın bir örneğini oluşturur ve `Modify` ifadeyi bu sınıfın yöntemine geçirir. Değişikliği göstermek için hem özgün hem de değiştirilmiş ifade ağaçları çıktılanır.  
  
6. Uygulamayı derle ve çalıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları nasıl yürütülür (C#)](./how-to-execute-expression-trees.md)
- [İfade Ağaçları (C#)](./index.md)
