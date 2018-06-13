---
title: 'Nasıl yapılır: dinamik sorgular (Visual Basic) derlemek için ifade ağaçları kullanma'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: a2101598a083f8d0738cb531ebbaea0f7a87a577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643427"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Nasıl yapılır: dinamik sorgular (Visual Basic) derlemek için ifade ağaçları kullanma
LINQ, uygulama veri kaynaklarını hedef yapılandırılmış sorguların temsil etmek için ifade ağaçları kullanılan <xref:System.Linq.IQueryable%601>. Örneğin, LINQ sağlayıcısını uygular <xref:System.Linq.IQueryable%601> ilişkisel veri depoları sorgulamak için arabirim. Visual Basic derleyici çalışma zamanında bir ifade ağacına derlemeler koda gibi veri kaynakları hedef sorguları derler. Sorgu sağlayıcısı ifade ağaç veri yapısı çapraz geçiş ve veri kaynağı için uygun bir sorgu dili içine çevir.  
  
 İfade ağaçları için de kullanılır LINQ türü değişkenlere atanan lambda ifadeleri temsil <xref:System.Linq.Expressions.Expression%601>.  
  
 Bu konu, dinamik LINQ sorguları oluşturmak için ifade ağaçları kullanmayı açıklar. Dinamik sorgular derleme zamanında bir sorgu ayrıntılarını bilinmiyor olduğunda yararlıdır. Örneğin, bir uygulama verilerini filtrelemek için bir veya daha fazla koşulları belirtmek son kullanıcının sağlayan bir kullanıcı arabirimi sağlayabilir. LINQ sorgulaması için kullanmak için bu tür bir uygulama ifade ağaçları çalışma zamanında LINQ sorgusu oluşturmak için kullanmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorgu oluşturmak için ifade ağaçları kullanma gösterilmektedir bir `IQueryable` veri kaynağı ve sonra yürütün. Kod aşağıdaki sorguyu temsil etmek için bir ifade ağacına oluşturur:  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 Fabrika yöntemlere <xref:System.Linq.Expressions> ad alanı, genel sorgulamasını olun ifadeleri temsil ifade ağaçları oluşturmak için kullanılır. Standart sorgu işleci yöntem çağrıları temsil eden ifadeleri başvurmak <xref:System.Linq.Queryable> bu yöntemlerin uygulamaları. Son ifade ağacına geçirilir <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> sağlayıcısı uyarlamasını `IQueryable` türü yürütülebilir bir sorgu oluşturmak için veri kaynağı `IQueryable`. Bu sorgu değişkeni numaralandırarak sonuçları elde edilir.  
  
```vb  
' Add an Imports statement for System.Linq.Expressions.  
  
Dim companies =   
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",   
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",   
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",   
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",   
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}  
  
' The IQueryable data to query.  
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()  
  
' Compose the expression tree that represents the parameter to the predicate.  
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")  
  
' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****  
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".  
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))  
Dim right As Expression = Expression.Constant("coho winery")  
Dim e1 As Expression = Expression.Equal(left, right)  
  
' Create an expression tree that represents the expression: company.Length > 16.  
left = Expression.Property(pe, GetType(String).GetProperty("Length"))  
right = Expression.Constant(16, GetType(Integer))  
Dim e2 As Expression = Expression.GreaterThan(left, right)  
  
' Combine the expressions to create an expression tree that represents the  
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).  
Dim predicateBody As Expression = Expression.OrElse(e1, e2)  
  
' Create an expression tree that represents the expression:  
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)  
Dim whereCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "Where",   
        New Type() {queryableData.ElementType},   
        queryableData.Expression,   
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))  
' ***** End Where *****  
  
' ***** OrderBy(Function(company) company) *****  
' Create an expression tree that represents the expression:  
' whereCallExpression.OrderBy(Function(company) company)  
Dim orderByCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "OrderBy",   
        New Type() {queryableData.ElementType, queryableData.ElementType},   
        whereCallExpression,   
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))  
' ***** End OrderBy *****  
  
' Create an executable query from the expression tree.  
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)  
  
' Enumerate the results.  
For Each company As String In results  
    Console.WriteLine(company)  
Next  
  
' This code produces the following output:  
'  
' Blue Yonder Airlines  
' City Power & Light  
' Coho Winery  
' Consolidated Messenger  
' Graphic Design Institute  
' Humongous Insurance  
' Lucerne Publishing  
' Northwind Traders  
' The Phone Company  
' Wide World Importers  
```  
  
 Bu kodu geçirilir karşılaştırma ifadeleri sabit sayıda kullanır `Queryable.Where` yöntemi. Ancak, kullanıcı girişi bağlıdır değişken karşılaştırma ifadeleri sayıda birleştiren bir uygulama yazabilirsiniz. Kullanıcı girişi bağlı olarak sorguyu adlı standart sorgu işleçleri de değişebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Yeni bir **konsol uygulaması** projesi.  
  
-   Zaten başvurulmayan System.Core.dll bir başvuru ekleyin.  
  
-   System.Linq.Expressions ad alanı içerir.  
  
-   Örnekten kodu kopyalayın ve yapıştırın `Main` `Sub` yordamı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [Nasıl yapılır: ifade ağaçlarını (Visual Basic) yürütme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
