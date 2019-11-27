---
title: 'Nasıl Yapılır: İfade Ağaçlarını Değiştirme'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 12ccad6df7d6c7d91ebc290163db362eae173209
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353755"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)

Bu konu başlığı altında, bir ifade ağacının nasıl değiştirileceği gösterilmektedir. İfade ağaçları sabittir ve bu, doğrudan değiştirilemediği anlamına gelir. Bir ifade ağacını değiştirmek için, var olan bir ifade ağacının bir kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir. <xref:System.Linq.Expressions.ExpressionVisitor> sınıfını, var olan bir ifade ağacında çapraz geçiş yapmak ve bulduğu her düğümü kopyalamak için kullanabilirsiniz.

## <a name="to-modify-an-expression-tree"></a>Bir ifade ağacını değiştirmek için

1. Yeni bir **konsol uygulaması** projesi oluşturun.

2. `System.Linq.Expressions` ad alanı için dosyaya `Imports` bir ifade ekleyin.

3. `AndAlsoModifier` sınıfını projenize ekleyin.

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

    Bu sınıf <xref:System.Linq.Expressions.ExpressionVisitor> sınıfını devralır ve koşullu `AND` işlemlerini temsil eden ifadeleri değiştirmek için özelleştirilmiştir. Bu işlemleri koşullu bir `AND` koşullu `OR`olarak değiştirir. Bunu yapmak için, koşullu `AND` ifadeler ikili ifadeler olarak temsil edildiği için sınıf temel türün <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> yöntemini geçersiz kılar. `VisitBinary` yönteminde, kendisine geçirilen ifade koşullu bir `AND` işlemini gösteriyorsa, kod koşullu `AND` işleci yerine koşullu `OR` işlecini içeren yeni bir ifade oluşturur. `VisitBinary` geçirilen ifade koşullu `AND` işlemini temsil ediyorsa, yöntemi temel sınıf uygulamasına erteler. Temel sınıf yöntemleri, geçirilen ifade ağaçları gibi düğümleri oluşturur, ancak düğümlerin alt ağaçları, ziyaretçi tarafından yinelemeli olarak üretilen ifade ağaçları ile değiştirilmiştir.

4. `System.Linq.Expressions` ad alanı için dosyaya `Imports` bir ifade ekleyin.

5. Bir ifade ağacı oluşturmak ve bunu değiştirecek yönteme geçirmek için Module1. vb dosyasındaki `Main` yöntemine kod ekleyin.

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

    Kod, koşullu `AND` işlemi içeren bir ifade oluşturur. Daha sonra, `AndAlsoModifier` sınıfının bir örneğini oluşturur ve bu sınıfın `Modify` yöntemine ifadeyi geçirir. Hem özgün hem de değiştirilen ifade ağaçları değişikliği göstermek için çıktılardır.

6. Uygulamayı derleyin ve çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
