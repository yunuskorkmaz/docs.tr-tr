---
title: 'Nasıl yapılır: (Visual Basic) ifade ağaçlarını değiştirme'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: a9b94cbd7bf24b0cc8efcfc66d8c5e7df4e27307
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305331"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Nasıl yapılır: (Visual Basic) ifade ağaçlarını değiştirme
Bu konu nasıl bir ifade ağacı değiştirileceğini gösterir. İfade ağaçları değişmezse, yani bunlar doğrudan değiştirilemez. İfade ağacı değiştirmek için var olan bir ifade ağacı bir kopyasını oluşturun ve bir kopya oluşturduğunuzda gerekli değişiklikleri yapın. Kullanabileceğiniz <xref:System.Linq.Expressions.ExpressionVisitor> var olan bir ifade ağacı gezme ve onu ziyaret her düğüm kopyalamak için bir sınıf.  
  
### <a name="to-modify-an-expression-tree"></a>İfade ağacı değiştirmek için  
  
1. Yeni bir **konsol uygulaması** proje.  
  
2. Ekleme bir `Imports` deyimi için dosyaya `System.Linq.Expressions` ad alanı.  
  
3. Ekleme `AndAlsoModifier` projenize sınıfı.  
  
    ```vb  
    Public Class AndAlsoModifier  
        Inherits ExpressionVisitor  
  
        Public Function Modify(ByVal expr As Expression) As Expression  
            Return Visit(expr)  
        End Function  
  
        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression  
            If b.NodeType = ExpressionType.AndAlso Then  
                Dim left = Me.Visit(b.Left)  
                Dim right = Me.Visit(b.Right)  
  
                ' Make this binary expression an OrElse operation instead   
                ' of an AndAlso operation.  
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _  
                                             b.IsLiftedToNull, b.Method)  
            End If  
  
            Return MyBase.VisitBinary(b)  
        End Function  
    End Class  
    ```  
  
     Bu sınıf devralır <xref:System.Linq.Expressions.ExpressionVisitor> temsil eden koşullu ifadeleri değiştirmek için özelleştirilmiş ve sınıf `AND` operations. Erişim ilkesinden işlemlerini değişiklikleri `AND` koşullu için `OR`. Bu sınıf geçersiz kılmalarını yapmak için <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> temel türün yöntemi olduğundan koşullu `AND` ifadeleri, ikili ifadelere temsil edilir. İçinde `VisitBinary` koşullu kendisine geçirilen ifade temsil ediyorsa yöntemi `AND` işlemi, kod yapıları koşullu içeren yeni bir ifade `OR` koşul yerine işleci `AND` işleci. Geçirilen ifade `VisitBinary` koşullu göstermiyor `AND` işlem, yöntem, temel sınıf uygulamasına erteler. İletilen ifade ağaçları gibi yapı düğümleri ancak düğümleri olan ifade ağaçları yerine kendi alt ağaçları sahip taban sınıf yöntemlerini yinelemeli olarak ziyaretçi tarafından üretilen.  
  
4. Ekleme bir `Imports` deyimi için dosyaya `System.Linq.Expressions` ad alanı.  
  
5. Kodu `Main` yöntemi Module1.vb dosyasındaki bir ifade ağacı oluşturmak ve bu yönteme geçirmek için onu değiştirir.  
  
    ```vb  
    Dim expr As Expression(Of Func(Of String, Boolean)) = _  
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")  
  
    Console.WriteLine(expr)  
  
    Dim modifier As New AndAlsoModifier()  
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))  
  
    Console.WriteLine(modifiedExpr)  
  
    ' This code produces the following output:  
    ' name => ((name.Length > 10) && name.StartsWith("G"))  
    ' name => ((name.Length > 10) || name.StartsWith("G"))  
    ```  
  
     Kod içeren bir koşullu ifade oluşturur `AND` işlemi. Ardından bir örneğini oluşturur `AndAlsoModifier` sınıfı ve ifade geçirir `Modify` bu sınıfın yöntemi. Hem özgün hem de değiştirilmiş ifade ağaçlarını değiştirme gösterilecek yüzdelik.  
  
6. Derleme ve uygulamayı çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
