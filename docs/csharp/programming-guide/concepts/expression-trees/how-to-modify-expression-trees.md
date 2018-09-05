---
title: 'Nasıl yapılır: ifade ağaçlarını (C#) değiştirme'
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 97a8ea0d66edf5d084c442deae32e04bdeb63c32
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528757"
---
# <a name="how-to-modify-expression-trees-c"></a>Nasıl yapılır: ifade ağaçlarını (C#) değiştirme
Bu konu nasıl bir ifade ağacı değiştirileceğini gösterir. İfade ağaçları değişmezse, yani bunlar doğrudan değiştirilemez. İfade ağacı değiştirmek için var olan bir ifade ağacı bir kopyasını oluşturun ve bir kopya oluşturduğunuzda gerekli değişiklikleri yapın. Kullanabileceğiniz <xref:System.Linq.Expressions.ExpressionVisitor> var olan bir ifade ağacı gezme ve onu ziyaret her düğüm kopyalamak için bir sınıf.  
  
### <a name="to-modify-an-expression-tree"></a>İfade ağacı değiştirmek için  
  
1.  Yeni bir **konsol uygulaması** proje.  
  
2.  Ekleme bir `using` dosyası yönerge `System.Linq.Expressions` ad alanı.  
  
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
  
     Bu sınıf devralır <xref:System.Linq.Expressions.ExpressionVisitor> temsil eden koşullu ifadeleri değiştirmek için özelleştirilmiş ve sınıf `AND` operations. Erişim ilkesinden işlemlerini değişiklikleri `AND` koşullu için `OR`. Bu sınıf geçersiz kılmalarını yapmak için <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> temel türün yöntemi olduğundan koşullu `AND` ifadeleri, ikili ifadelere temsil edilir. İçinde `VisitBinary` koşullu kendisine geçirilen ifade temsil ediyorsa yöntemi `AND` işlemi, kod yapıları koşullu içeren yeni bir ifade `OR` koşul yerine işleci `AND` işleci. Geçirilen ifade `VisitBinary` koşullu göstermiyor `AND` işlem, yöntem, temel sınıf uygulamasına erteler. İletilen ifade ağaçları gibi yapı düğümleri ancak düğümleri olan ifade ağaçları yerine kendi alt ağaçları sahip taban sınıf yöntemlerini yinelemeli olarak ziyaretçi tarafından üretilen.  
  
4.  Ekleme bir `using` dosyası yönerge `System.Linq.Expressions` ad alanı.  
  
5.  Kodu `Main` yöntemi Program.cs dosyasındaki bir ifade ağacı oluşturmak ve bu yönteme geçirmek için onu değiştirir.  
  
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
  
     Kod içeren bir koşullu ifade oluşturur `AND` işlemi. Ardından bir örneğini oluşturur `AndAlsoModifier` sınıfı ve ifade geçirir `Modify` bu sınıfın yöntemi. Hem özgün hem de değiştirilmiş ifade ağaçlarını değiştirme gösterilecek yüzdelik.  
  
6.  Derleme ve uygulamayı çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Nasıl yapılır: ifade ağaçlarını (C#) yürütme](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
- [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
