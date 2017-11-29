---
title: "Nasıl yapılır: ifade ağaçlarını (Visual Basic) değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28a79a2dc8817a3fc6c7f3e2e01c1270d2981334
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Nasıl yapılır: ifade ağaçlarını (Visual Basic) değiştirme
Bu konu bir ifade ağacına değiştirme gösterir. İfade ağaçları değişmez, bunlar doğrudan değiştirilemiyor anlamına gelir. Bir ifade ağacına değiştirmek için varolan bir ifade ağacına bir kopyasını oluşturun ve bir kopya oluşturduğunuzda gerekli değişiklikleri yapın. Kullanabileceğiniz <xref:System.Linq.Expressions.ExpressionVisitor> sınıfı var olan bir ifade ağacına gezme ve onu ziyaret her bir düğüm kopyalamak için.  
  
### <a name="to-modify-an-expression-tree"></a>Bir ifade ağacına değiştirmek için  
  
1.  Yeni bir **konsol uygulaması** projesi.  
  
2.  Ekleme bir `Imports` deyimi dosya için `System.Linq.Expressions` ad alanı.  
  
3.  Ekleme `AndAlsoModifier` projenize sınıfı.  
  
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
  
     Bu sınıf devralır <xref:System.Linq.Expressions.ExpressionVisitor> sınıfı ve koşullu temsil eden ifadeleri değiştirmek için özelleştirilmiş `AND` işlemleri. Bu işlemler erişim ilkesinden değiştirir `AND` koşullu için `OR`. Bu sınıfı geçersiz kılma işlemleri yapmak için <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> temel türü yöntemi için koşullu `AND` ifadeleri ikili ifadeler olarak temsil. İçinde `VisitBinary` kendisine geçirilen ifade koşullu temsil ediyorsa yöntemi `AND` , işlem kodu oluşturan koşullu içeren yeni bir ifade `OR` işleci koşul yerine `AND` işleç. Varsa geçirilir ifade `VisitBinary` koşullu göstermiyor `AND` işlemi, yöntemi için temel sınıf uygulamasını erteler. İletilen ifade ağaçları gibi yapı düğümlerini ancak düğümleri olan ifade ağaçları yerine kendi alt ağaçları olan taban sınıf yöntemlerini yinelemeli olarak ziyaretçi tarafından üretilen.  
  
4.  Ekleme bir `Imports` deyimi dosya için `System.Linq.Expressions` ad alanı.  
  
5.  Kodu ekleyin `Main` yöntemi bir ifade ağacına oluşturup, yönteme geçirin Module1.vb dosyasında da değiştirir.  
  
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
  
     Koşullu içeren bir ifade kod oluşturur `AND` işlemi. Ardından bir örneğini oluşturur `AndAlsoModifier` sınıfı ve ifade geçirir `Modify` bu sınıfın yöntemi. Değişikliği göstermek için özgün ve değiştirilen ifade ağaçları yüzdelik.  
  
6.  Derleme ve uygulamayı çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ifade ağaçlarını (Visual Basic) yürütme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
