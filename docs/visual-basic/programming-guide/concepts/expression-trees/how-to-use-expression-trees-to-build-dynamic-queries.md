---
title: "Nasıl yapılır: dinamik sorgular (Visual Basic) derlemek için ifade ağaçları kullanma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d09f89b0b49118d575690f577c77c5c3d2a76e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="b1925-102">Nasıl yapılır: dinamik sorgular (Visual Basic) derlemek için ifade ağaçları kullanma</span><span class="sxs-lookup"><span data-stu-id="b1925-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="b1925-103">LINQ, uygulama veri kaynaklarını hedef yapılandırılmış sorguların temsil etmek için ifade ağaçları kullanılan <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="b1925-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="b1925-104">Örneğin, LINQ sağlayıcısını uygular <xref:System.Linq.IQueryable%601> ilişkisel veri depoları sorgulamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="b1925-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="b1925-105">Visual Basic derleyici çalışma zamanında bir ifade ağacına derlemeler koda gibi veri kaynakları hedef sorguları derler.</span><span class="sxs-lookup"><span data-stu-id="b1925-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="b1925-106">Sorgu sağlayıcısı ifade ağaç veri yapısı çapraz geçiş ve veri kaynağı için uygun bir sorgu dili içine çevir.</span><span class="sxs-lookup"><span data-stu-id="b1925-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="b1925-107">İfade ağaçları için de kullanılır LINQ türü değişkenlere atanan lambda ifadeleri temsil <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="b1925-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="b1925-108">Bu konu, dinamik LINQ sorguları oluşturmak için ifade ağaçları kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b1925-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="b1925-109">Dinamik sorgular derleme zamanında bir sorgu ayrıntılarını bilinmiyor olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b1925-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="b1925-110">Örneğin, bir uygulama verilerini filtrelemek için bir veya daha fazla koşulları belirtmek son kullanıcının sağlayan bir kullanıcı arabirimi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b1925-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="b1925-111">LINQ sorgulaması için kullanmak için bu tür bir uygulama ifade ağaçları çalışma zamanında LINQ sorgusu oluşturmak için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1925-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1925-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1925-112">Example</span></span>  
 <span data-ttu-id="b1925-113">Aşağıdaki örnek, bir sorgu oluşturmak için ifade ağaçları kullanma gösterilmektedir bir `IQueryable` veri kaynağı ve sonra yürütün.</span><span class="sxs-lookup"><span data-stu-id="b1925-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="b1925-114">Kod aşağıdaki sorguyu temsil etmek için bir ifade ağacına oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b1925-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="b1925-115">Fabrika yöntemlere <xref:System.Linq.Expressions> ad alanı, genel sorgulamasını olun ifadeleri temsil ifade ağaçları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1925-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="b1925-116">Standart sorgu işleci yöntem çağrıları temsil eden ifadeleri başvurmak <xref:System.Linq.Queryable> bu yöntemlerin uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="b1925-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="b1925-117">Son ifade ağacına geçirilir <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> sağlayıcısı uyarlamasını `IQueryable` türü yürütülebilir bir sorgu oluşturmak için veri kaynağı `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="b1925-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="b1925-118">Bu sorgu değişkeni numaralandırarak sonuçları elde edilir.</span><span class="sxs-lookup"><span data-stu-id="b1925-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="b1925-119">Bu kodu geçirilir karşılaştırma ifadeleri sabit sayıda kullanır `Queryable.Where` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b1925-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="b1925-120">Ancak, kullanıcı girişi bağlıdır değişken karşılaştırma ifadeleri sayıda birleştiren bir uygulama yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1925-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="b1925-121">Kullanıcı girişi bağlı olarak sorguyu adlı standart sorgu işleçleri de değişebilir.</span><span class="sxs-lookup"><span data-stu-id="b1925-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1925-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b1925-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b1925-123">Yeni bir **konsol uygulaması** projesi.</span><span class="sxs-lookup"><span data-stu-id="b1925-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="b1925-124">Zaten başvurulmayan System.Core.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1925-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="b1925-125">System.Linq.Expressions ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="b1925-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="b1925-126">Örnekten kodu kopyalayın ve yapıştırın `Main` `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="b1925-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1925-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1925-127">See Also</span></span>  
 [<span data-ttu-id="b1925-128">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1925-128">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="b1925-129">Nasıl yapılır: ifade ağaçlarını (Visual Basic) yürütme</span><span class="sxs-lookup"><span data-stu-id="b1925-129">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
