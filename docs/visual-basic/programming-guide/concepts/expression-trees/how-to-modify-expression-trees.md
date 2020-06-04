---
title: 'Nasıl Yapılır: İfade Ağaçlarını Değiştirme'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 1f052120a2e7e12f5a985adce3ae193afec0e9af
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410998"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)

Bu konu başlığı altında, bir ifade ağacının nasıl değiştirileceği gösterilmektedir. İfade ağaçları sabittir ve bu, doğrudan değiştirilemediği anlamına gelir. Bir ifade ağacını değiştirmek için, var olan bir ifade ağacının bir kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir. <xref:System.Linq.Expressions.ExpressionVisitor>Sınıfını, var olan bir ifade ağacında çapraz geçiş yapmak ve bulduğu her düğümü kopyalamak için kullanabilirsiniz.

## <a name="to-modify-an-expression-tree"></a>Bir ifade ağacını değiştirmek için

1. Yeni bir **konsol uygulaması** projesi oluşturun.

2. `Imports`Ad alanı için dosyasına bir ifade ekleyin `System.Linq.Expressions` .

3. `AndAlsoModifier`Sınıfını projenize ekleyin.

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

    Bu sınıf sınıfını devralır <xref:System.Linq.Expressions.ExpressionVisitor> ve koşullu işlemleri temsil eden ifadeleri değiştirmek için özelleştirilmiştir `AND` . Bu işlemleri koşullu sunucudan `AND` koşullu olarak değiştirir `OR` . Bunu yapmak için, <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> koşullu `AND` ifadeler ikili ifadeler olarak temsil edildiği için sınıf temel tür yöntemini geçersiz kılar. `VisitBinary`Yönteminde, kendisine geçirilen ifade koşullu bir işlemi temsil ediyorsa `AND` , kod koşullu işleç yerine koşullu işleci içeren yeni bir ifade oluşturur `OR` `AND` . Geçirilen ifade `VisitBinary` koşullu bir işlemi temsil ediyorsa `AND` , yöntemi temel sınıf uygulamasına erteler. Temel sınıf yöntemleri, geçirilen ifade ağaçları gibi düğümleri oluşturur, ancak düğümlerin alt ağaçları, ziyaretçi tarafından yinelemeli olarak üretilen ifade ağaçları ile değiştirilmiştir.

4. `Imports`Ad alanı için dosyasına bir ifade ekleyin `System.Linq.Expressions` .

5. `Main`Bir ifade ağacı oluşturmak ve bunu değiştirecek yönteme geçirmek Için Module1. vb dosyasındaki yöntemine kod ekleyin.

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

    Kod, koşullu bir işlem içeren bir ifade oluşturur `AND` . Daha sonra sınıfın bir örneğini oluşturur `AndAlsoModifier` ve `Modify` Bu sınıfın yöntemine ifadeyi geçirir. Hem özgün hem de değiştirilen ifade ağaçları değişikliği göstermek için çıktılardır.

6. Uygulamayı derleyin ve çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)](how-to-execute-expression-trees.md)
- [İfade ağaçları (Visual Basic)](index.md)
