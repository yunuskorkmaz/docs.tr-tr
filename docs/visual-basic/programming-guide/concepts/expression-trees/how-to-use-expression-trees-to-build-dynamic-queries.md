---
title: 'Nasıl yapılır: Dinamik Sorgular Derlemek için İfade Ağaçları Kullanma'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 1f686c37b5d04263ac5ae0dd6883aa8a519ed19e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410985"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="eeea8-102">Nasıl yapılır: dinamik sorgular oluşturmak için Ifade ağaçları kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eeea8-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>

<span data-ttu-id="eeea8-103">LINQ içinde, ifade ağaçları, uygulayan veri kaynaklarını hedefleyen yapılandırılmış sorguları temsil etmek için kullanılır <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="eeea8-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="eeea8-104">Örneğin, LINQ sağlayıcısı <xref:System.Linq.IQueryable%601> ilişkisel veri depolarını sorgulamak için arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="eeea8-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="eeea8-105">Visual Basic Derleyicisi, bu tür veri kaynaklarını hedefleyen sorguları, çalışma zamanında bir ifade ağacı oluşturan koda derler.</span><span class="sxs-lookup"><span data-stu-id="eeea8-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="eeea8-106">Sorgu sağlayıcısı daha sonra ifade ağacı veri yapısına çapraz geçiş yapabilir ve veri kaynağı için uygun bir sorgu diline çevirebilir.</span><span class="sxs-lookup"><span data-stu-id="eeea8-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>

<span data-ttu-id="eeea8-107">İfade ağaçları Ayrıca LINQ 'te tür değişkenlerine atanan Lambda ifadelerini temsil etmek için de kullanılır <xref:System.Linq.Expressions.Expression%601> .</span><span class="sxs-lookup"><span data-stu-id="eeea8-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>

<span data-ttu-id="eeea8-108">Bu konu başlığı altında, dinamik LINQ sorguları oluşturmak için ifade ağaçlarının nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eeea8-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="eeea8-109">Dinamik sorgular, bir sorgunun özelliklerinin derleme zamanında bilinmediği durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="eeea8-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="eeea8-110">Örneğin, bir uygulama, son kullanıcının verileri filtrelemek için bir veya daha fazla koşul belirtmesini sağlayan bir kullanıcı arabirimi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="eeea8-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="eeea8-111">Bu tür bir uygulamanın, sorgulama için LINQ kullanabilmesi amacıyla, çalışma zamanında LINQ sorgusu oluşturmak için ifade ağaçları kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eeea8-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>

## <a name="example"></a><span data-ttu-id="eeea8-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="eeea8-112">Example</span></span>

<span data-ttu-id="eeea8-113">Aşağıdaki örnek, bir veri kaynağına yönelik sorgu oluşturmak ve ardından yürütmek için ifade ağaçlarının nasıl kullanılacağını gösterir `IQueryable` .</span><span class="sxs-lookup"><span data-stu-id="eeea8-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="eeea8-114">Kod, aşağıdaki sorguyu temsil etmek için bir ifade ağacı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="eeea8-114">The code builds an expression tree to represent the following query:</span></span>

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

<span data-ttu-id="eeea8-115">Ad alanındaki Fabrika yöntemleri, <xref:System.Linq.Expressions> genel sorguyu oluşturan ifadeleri temsil eden ifade ağaçları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eeea8-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="eeea8-116">Standart sorgu operatörü yöntemlerine yapılan çağrıları temsil eden ifadeler, <xref:System.Linq.Queryable> Bu yöntemlerin uygulamalarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="eeea8-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="eeea8-117">Son ifade ağacı, <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> `IQueryable` türünde çalıştırılabilir bir sorgu oluşturmak için veri kaynağının sağlayıcısı uygulamasına geçirilir `IQueryable` .</span><span class="sxs-lookup"><span data-stu-id="eeea8-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="eeea8-118">Sonuçlar, bu sorgu değişkeni numaralandırıldığı için alınır.</span><span class="sxs-lookup"><span data-stu-id="eeea8-118">The results are obtained by enumerating that query variable.</span></span>

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

<span data-ttu-id="eeea8-119">Bu kod, metoduna geçirilen koşuldaki sabit sayıda ifadeyi kullanır `Queryable.Where` .</span><span class="sxs-lookup"><span data-stu-id="eeea8-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="eeea8-120">Ancak, kullanıcı girişine bağlı bir değişken sayıda koşul ifadesini birleştiren bir uygulama yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eeea8-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="eeea8-121">Ayrıca, kullanıcının girişine bağlı olarak sorguda çağrılan standart sorgu işleçlerini da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eeea8-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="eeea8-122">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="eeea8-122">Compile the code</span></span>

- <span data-ttu-id="eeea8-123">Yeni bir **konsol uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eeea8-123">Create a new **Console Application** project.</span></span>

- <span data-ttu-id="eeea8-124">System. Linq. Ifadeler ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eeea8-124">Include the System.Linq.Expressions namespace.</span></span>

- <span data-ttu-id="eeea8-125">Örnekteki kodu kopyalayın ve `Main` `Sub` yordama yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="eeea8-125">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="eeea8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eeea8-126">See also</span></span>

- [<span data-ttu-id="eeea8-127">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eeea8-127">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="eeea8-128">Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eeea8-128">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
