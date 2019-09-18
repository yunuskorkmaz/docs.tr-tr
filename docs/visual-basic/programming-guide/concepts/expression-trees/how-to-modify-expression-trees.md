---
title: 'Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: ac196b56f178659765437a97a25f46c04f8040fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054208"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)

Bu konu başlığı altında, bir ifade ağacının nasıl değiştirileceği gösterilmektedir. İfade ağaçları sabittir ve bu, doğrudan değiştirilemediği anlamına gelir. Bir ifade ağacını değiştirmek için, var olan bir ifade ağacının bir kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir. Sınıfını, <xref:System.Linq.Expressions.ExpressionVisitor> var olan bir ifade ağacında çapraz geçiş yapmak ve bulduğu her düğümü kopyalamak için kullanabilirsiniz.

## <a name="to-modify-an-expression-tree"></a>Bir ifade ağacını değiştirmek için

1. Yeni bir **konsol uygulaması** projesi oluşturun.

2. Ad`System.Linq.Expressions` alanı `Imports` için dosyasına bir ifade ekleyin.

3. `AndAlsoModifier` Sınıfını projenize ekleyin.

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

    Bu sınıf <xref:System.Linq.Expressions.ExpressionVisitor> sınıfını devralır ve koşullu `AND` işlemleri temsil eden ifadeleri değiştirmek için özelleştirilmiştir. Bu işlemleri koşullu `AND` sunucudan koşullu `OR`olarak değiştirir. Bunu yapmak için, koşullu <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> `AND` ifadeler ikili ifadeler olarak temsil edildiği için sınıf temel tür yöntemini geçersiz kılar. Yönteminde, kendisine geçirilen ifade koşullu `AND` bir işlemi temsil ediyorsa, kod koşullu `OR` işleci `AND` içeren yeni bir ifade oluşturur `VisitBinary` işlecinde. Geçirilen `VisitBinary` ifade koşullu `AND` bir işlemi temsil ediyorsa, yöntemi temel sınıf uygulamasına erteler. Temel sınıf yöntemleri, geçirilen ifade ağaçları gibi düğümleri oluşturur, ancak düğümlerin alt ağaçları, ziyaretçi tarafından yinelemeli olarak üretilen ifade ağaçları ile değiştirilmiştir.

4. Ad`System.Linq.Expressions` alanı `Imports` için dosyasına bir ifade ekleyin.

5. Bir ifade ağacı oluşturmak `Main` ve bunu değiştirecek yönteme geçirmek için Module1. vb dosyasındaki yöntemine kod ekleyin.

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

    Kod, koşullu `AND` bir işlem içeren bir ifade oluşturur. Daha sonra `AndAlsoModifier` sınıfın bir örneğini oluşturur ve bu sınıfın `Modify` yöntemine ifadeyi geçirir. Hem özgün hem de değiştirilen ifade ağaçları değişikliği göstermek için çıktılardır.

6. Uygulamayı derleyin ve çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
