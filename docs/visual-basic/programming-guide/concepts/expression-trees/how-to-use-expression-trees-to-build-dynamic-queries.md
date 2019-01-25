---
title: 'Nasıl yapılır: (Visual Basic) dinamik sorgular derlemek için ifade ağaçları kullanma'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: dd1e5fff21ef68683d0b721e84c4690d8e440d60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645472"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="377e7-102">Nasıl yapılır: (Visual Basic) dinamik sorgular derlemek için ifade ağaçları kullanma</span><span class="sxs-lookup"><span data-stu-id="377e7-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="377e7-103">LINQ içinde uygulama veri kaynaklarını hedefleyen yapılandırılmış sorguların temsil etmek için ifade ağaçları kullanılan <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="377e7-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="377e7-104">Örneğin, LINQ sağlayıcı uygulayan <xref:System.Linq.IQueryable%601> ilişkisel veri deposu sorgulamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="377e7-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="377e7-105">Visual Basic Derleyicisi, çalışma zamanında bir ifade ağacı oluşturan koda gibi veri kaynakları hedef sorguları derler.</span><span class="sxs-lookup"><span data-stu-id="377e7-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="377e7-106">Sorgu sağlayıcısına geçiş ifadesi ağaç veri yapısı ve veri kaynağı için uygun bir sorgu dili küçültmesini.</span><span class="sxs-lookup"><span data-stu-id="377e7-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="377e7-107">İfade ağaçları için de kullanılır LINQ türündeki değişkenler için atanmış olan lambda ifadeleri temsil <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="377e7-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="377e7-108">Bu konuda, dinamik LINQ sorguları oluşturmak için ifade ağaçları kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="377e7-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="377e7-109">Dinamik sorgular, bir sorgu ayrıntılarını derleme zamanında bilinen olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="377e7-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="377e7-110">Örneğin, bir uygulama verilerini filtrelemek için bir veya daha fazla koşulları belirtmek son kullanıcının sağlayan bir kullanıcı arabirimi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="377e7-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="377e7-111">Sorgulamak için LINQ kullanmak için bu tür bir uygulama ifade ağaçları çalışma zamanında LINQ sorgusu oluşturmak için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="377e7-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="377e7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="377e7-112">Example</span></span>  
 <span data-ttu-id="377e7-113">Aşağıdaki örnek bir sorgu oluşturmak için ifade ağaçları kullanma işlemi gösterilmektedir bir `IQueryable` veri kaynağını seçin ve sonra yürütün.</span><span class="sxs-lookup"><span data-stu-id="377e7-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="377e7-114">Kod, aşağıdaki sorguyu temsil etmek için bir ifade ağacı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="377e7-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="377e7-115">Fabrika yöntemleri <xref:System.Linq.Expressions> ad alanı, genel sorgu yapmak ifadeleri temsil eden bir ifade ağacı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="377e7-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="377e7-116">Standart sorgu işleci yöntemlerinin çağrıları temsil eden ifadeleri başvurmak <xref:System.Linq.Queryable> bu yöntemlerin uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="377e7-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="377e7-117">Son bir ifade ağacı geçirilir <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> sağlayıcısı uygulaması `IQueryable` yürütülebilir bir sorgu türü oluşturmak için veri kaynağı `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="377e7-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="377e7-118">Bu sorgu değişkeni numaralandırarak sonuçlar elde edilir.</span><span class="sxs-lookup"><span data-stu-id="377e7-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="377e7-119">Bu kodu ifadeler sabit sayıda geçirilir koşulu kullanır `Queryable.Where` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="377e7-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="377e7-120">Ancak, kullanıcı girişi bağlıdır değişken koşul ifadeleri sayısı birleştiren bir uygulama yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="377e7-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="377e7-121">Kullanıcı girişini bağlı olarak sorguyu adlı standart sorgu işleçleri de değişebilir.</span><span class="sxs-lookup"><span data-stu-id="377e7-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="377e7-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="377e7-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="377e7-123">Yeni bir **konsol uygulaması** proje.</span><span class="sxs-lookup"><span data-stu-id="377e7-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="377e7-124">Zaten başvurulmayan System.Core.dll öğesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="377e7-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="377e7-125">System.Linq.Expressions ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="377e7-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="377e7-126">Örnek kodu kopyalayın ve yapıştırın `Main` `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="377e7-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="377e7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="377e7-127">See also</span></span>
- [<span data-ttu-id="377e7-128">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="377e7-128">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="377e7-129">Nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme</span><span class="sxs-lookup"><span data-stu-id="377e7-129">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
