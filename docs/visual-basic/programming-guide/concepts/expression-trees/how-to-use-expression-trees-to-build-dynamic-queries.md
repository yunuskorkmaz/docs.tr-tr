---
title: 'Nasıl yapılır: (Visual Basic) dinamik sorgular derlemek için ifade ağaçları kullanma'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: d9b1f97fd8bf3dfb15f3e1ab65b02a81b5607792
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642318"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Nasıl yapılır: (Visual Basic) dinamik sorgular derlemek için ifade ağaçları kullanma
LINQ içinde uygulama veri kaynaklarını hedefleyen yapılandırılmış sorguların temsil etmek için ifade ağaçları kullanılan <xref:System.Linq.IQueryable%601>. Örneğin, LINQ sağlayıcı uygulayan <xref:System.Linq.IQueryable%601> ilişkisel veri deposu sorgulamak için arabirim. Visual Basic Derleyicisi, çalışma zamanında bir ifade ağacı oluşturan koda gibi veri kaynakları hedef sorguları derler. Sorgu sağlayıcısına geçiş ifadesi ağaç veri yapısı ve veri kaynağı için uygun bir sorgu dili küçültmesini.  
  
 İfade ağaçları için de kullanılır LINQ türündeki değişkenler için atanmış olan lambda ifadeleri temsil <xref:System.Linq.Expressions.Expression%601>.  
  
 Bu konuda, dinamik LINQ sorguları oluşturmak için ifade ağaçları kullanmayı açıklar. Dinamik sorgular, bir sorgu ayrıntılarını derleme zamanında bilinen olduğunda yararlıdır. Örneğin, bir uygulama verilerini filtrelemek için bir veya daha fazla koşulları belirtmek son kullanıcının sağlayan bir kullanıcı arabirimi sağlayabilir. Sorgulamak için LINQ kullanmak için bu tür bir uygulama ifade ağaçları çalışma zamanında LINQ sorgusu oluşturmak için kullanmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir sorgu oluşturmak için ifade ağaçları kullanma işlemi gösterilmektedir bir `IQueryable` veri kaynağını seçin ve sonra yürütün. Kod, aşağıdaki sorguyu temsil etmek için bir ifade ağacı oluşturur:  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 Fabrika yöntemleri <xref:System.Linq.Expressions> ad alanı, genel sorgu yapmak ifadeleri temsil eden bir ifade ağacı oluşturmak için kullanılır. Standart sorgu işleci yöntemlerinin çağrıları temsil eden ifadeleri başvurmak <xref:System.Linq.Queryable> bu yöntemlerin uygulamaları. Son bir ifade ağacı geçirilir <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> sağlayıcısı uygulaması `IQueryable` yürütülebilir bir sorgu türü oluşturmak için veri kaynağı `IQueryable`. Bu sorgu değişkeni numaralandırarak sonuçlar elde edilir.  
  
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
  
 Bu kodu ifadeler sabit sayıda geçirilir koşulu kullanır `Queryable.Where` yöntemi. Ancak, kullanıcı girişi bağlıdır değişken koşul ifadeleri sayısı birleştiren bir uygulama yazabilirsiniz. Kullanıcı girişini bağlı olarak sorguyu adlı standart sorgu işleçleri de değişebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Yeni bir **konsol uygulaması** proje.  
  
- Zaten başvurulmayan System.Core.dll öğesine başvuru ekleyin.  
  
- System.Linq.Expressions ad alanı içerir.  
  
- Örnek kodu kopyalayın ve yapıştırın `Main` `Sub` yordamı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
