---
title: 'Nasıl yapılır: ifade ağaçlarını (C#) değiştirme'
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 3a43e2365475644d5081ced7bfec11e1a2b5121e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329848"
---
# <a name="how-to-modify-expression-trees-c"></a>Nasıl yapılır: ifade ağaçlarını (C#) değiştirme
Bu konu bir ifade ağacına değiştirme gösterir. İfade ağaçları değişmez, bunlar doğrudan değiştirilemiyor anlamına gelir. Bir ifade ağacına değiştirmek için varolan bir ifade ağacına bir kopyasını oluşturun ve bir kopya oluşturduğunuzda gerekli değişiklikleri yapın. Kullanabileceğiniz <xref:System.Linq.Expressions.ExpressionVisitor> sınıfı var olan bir ifade ağacına gezme ve onu ziyaret her bir düğüm kopyalamak için.  
  
### <a name="to-modify-an-expression-tree"></a>Bir ifade ağacına değiştirmek için  
  
1.  Yeni bir **konsol uygulaması** projesi.  
  
2.  Ekleme bir `using` dosya için yönerge `System.Linq.Expressions` ad alanı.  
  
3.  Ekleme `AndAlsoModifier` projenize sınıfı.  
  
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
  
     Bu sınıf devralır <xref:System.Linq.Expressions.ExpressionVisitor> sınıfı ve koşullu temsil eden ifadeleri değiştirmek için özelleştirilmiş `AND` işlemleri. Bu işlemler erişim ilkesinden değiştirir `AND` koşullu için `OR`. Bu sınıfı geçersiz kılma işlemleri yapmak için <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> temel türü yöntemi için koşullu `AND` ifadeleri ikili ifadeler olarak temsil. İçinde `VisitBinary` kendisine geçirilen ifade koşullu temsil ediyorsa yöntemi `AND` , işlem kodu oluşturan koşullu içeren yeni bir ifade `OR` işleci koşul yerine `AND` işleç. Varsa geçirilir ifade `VisitBinary` koşullu göstermiyor `AND` işlemi, yöntemi için temel sınıf uygulamasını erteler. İletilen ifade ağaçları gibi yapı düğümlerini ancak düğümleri olan ifade ağaçları yerine kendi alt ağaçları olan taban sınıf yöntemlerini yinelemeli olarak ziyaretçi tarafından üretilen.  
  
4.  Ekleme bir `using` dosya için yönerge `System.Linq.Expressions` ad alanı.  
  
5.  Kodu ekleyin `Main` yöntemi Program.cs dosyasında bir ifade ağacına oluşturun ve bu yönteme geçirin onu değiştirir.  
  
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
  
     Koşullu içeren bir ifade kod oluşturur `AND` işlemi. Ardından bir örneğini oluşturur `AndAlsoModifier` sınıfı ve ifade geçirir `Modify` bu sınıfın yöntemi. Değişikliği göstermek için özgün ve değiştirilen ifade ağaçları yüzdelik.  
  
6.  Derleme ve uygulamayı çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ifade ağaçlarını (C#) yürütme](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
