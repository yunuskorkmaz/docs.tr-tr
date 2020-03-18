---
title: Dinamik sorgular oluşturmak için ifade ağaçları nasıl kullanılır (C#)
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 6114ec13dd43a7df146b87dda00fba06d6eb870c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635905"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="0f9fc-102">Dinamik sorgular oluşturmak için ifade ağaçları nasıl kullanılır (C#)</span><span class="sxs-lookup"><span data-stu-id="0f9fc-102">How to use expression trees to build dynamic queries (C#)</span></span>
<span data-ttu-id="0f9fc-103">LINQ'da ifade ağaçları, uygulayan <xref:System.Linq.IQueryable%601>veri kaynaklarını hedefleyen yapılandırılmış sorguları temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="0f9fc-104">Örneğin, LINQ sağlayıcısı ilişkisel <xref:System.Linq.IQueryable%601> veri depolarını sorgulamak için arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="0f9fc-105">C# derleyicisi, bu tür veri kaynaklarını hedefleyen sorguları çalışma zamanında bir ifade ağacı oluşturan koda dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="0f9fc-106">Sorgu sağlayıcısı daha sonra ifade ağacı veri yapısını geçiş yapabilir ve veri kaynağına uygun bir sorgu diline çevirebilir.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="0f9fc-107">İfade ağaçları linq'te de türünün <xref:System.Linq.Expressions.Expression%601>değişkenlerine atanan lambda ifadelerini temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="0f9fc-108">Bu konu, dinamik LINQ sorguları oluşturmak için ifade ağaçlarının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="0f9fc-109">Bir sorgunun ayrıntıları derleme zamanında bilinmediğinde dinamik sorgular yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="0f9fc-110">Örneğin, bir uygulama, son kullanıcının verileri filtrelemek için bir veya daha fazla yüklem belirtmesini sağlayan bir kullanıcı arabirimi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="0f9fc-111">Sorgulama için LINQ'yi kullanabilmek için, bu tür bir uygulamanın çalışma zamanında LINQ sorgusunu oluşturmak için ifade ağaçlarını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f9fc-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f9fc-112">Example</span></span>  
 <span data-ttu-id="0f9fc-113">Aşağıdaki örnek, bir sorguyu bir `IQueryable` veri kaynağına karşı oluşturmak ve sonra yürütmek için ifade ağaçlarını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="0f9fc-114">Kod, aşağıdaki sorguyu temsil edecek bir ifade ağacı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0f9fc-114">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="0f9fc-115"><xref:System.Linq.Expressions> Ad alanındaki fabrika yöntemleri, genel sorguyu oluşturan ifadeleri temsil eden ifade ağaçları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="0f9fc-116">Standart sorgu işleci yöntemlerine yapılan çağrıları temsil <xref:System.Linq.Queryable> eden ifadeler, bu yöntemlerin uygulamalarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="0f9fc-117">Son ifade ağacı, tür <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> `IQueryable`yürütülebilir bir `IQueryable` sorgu oluşturmak için veri kaynağı sağlayıcısının uygulamasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="0f9fc-118">Sonuçlar, sorgu değişkeninin sayısala sıyrıkları ile elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-118">The results are obtained by enumerating that query variable.</span></span>  
  
```csharp  
// Add a using directive for System.Linq.Expressions.  
  
string[] companies = { "Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",  
                   "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",  
                   "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",  
                   "Blue Yonder Airlines", "Trey Research", "The Phone Company",  
                   "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee" };  
  
// The IQueryable data to query.  
IQueryable<String> queryableData = companies.AsQueryable<string>();  
  
// Compose the expression tree that represents the parameter to the predicate.  
ParameterExpression pe = Expression.Parameter(typeof(string), "company");  
  
// ***** Where(company => (company.ToLower() == "coho winery" || company.Length > 16)) *****  
// Create an expression tree that represents the expression 'company.ToLower() == "coho winery"'.  
Expression left = Expression.Call(pe, typeof(string).GetMethod("ToLower", System.Type.EmptyTypes));  
Expression right = Expression.Constant("coho winery");  
Expression e1 = Expression.Equal(left, right);  
  
// Create an expression tree that represents the expression 'company.Length > 16'.  
left = Expression.Property(pe, typeof(string).GetProperty("Length"));  
right = Expression.Constant(16, typeof(int));  
Expression e2 = Expression.GreaterThan(left, right);  
  
// Combine the expression trees to create an expression tree that represents the  
// expression '(company.ToLower() == "coho winery" || company.Length > 16)'.  
Expression predicateBody = Expression.OrElse(e1, e2);  
  
// Create an expression tree that represents the expression  
// 'queryableData.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))'  
MethodCallExpression whereCallExpression = Expression.Call(  
    typeof(Queryable),  
    "Where",  
    new Type[] { queryableData.ElementType },  
    queryableData.Expression,  
    Expression.Lambda<Func<string, bool>>(predicateBody, new ParameterExpression[] { pe }));  
// ***** End Where *****  
  
// ***** OrderBy(company => company) *****  
// Create an expression tree that represents the expression  
// 'whereCallExpression.OrderBy(company => company)'  
MethodCallExpression orderByCallExpression = Expression.Call(  
    typeof(Queryable),  
    "OrderBy",  
    new Type[] { queryableData.ElementType, queryableData.ElementType },  
    whereCallExpression,  
    Expression.Lambda<Func<string, string>>(pe, new ParameterExpression[] { pe }));  
// ***** End OrderBy *****  
  
// Create an executable query from the expression tree.  
IQueryable<string> results = queryableData.Provider.CreateQuery<string>(orderByCallExpression);  
  
// Enumerate the results.  
foreach (string company in results)  
    Console.WriteLine(company);  
  
/*  This code produces the following output:  
  
    Blue Yonder Airlines  
    City Power & Light  
    Coho Winery  
    Consolidated Messenger  
    Graphic Design Institute  
    Humongous Insurance  
    Lucerne Publishing  
    Northwind Traders  
    The Phone Company  
    Wide World Importers  
*/  
```  
  
 <span data-ttu-id="0f9fc-119">Bu kod, `Queryable.Where` yönteme geçirilen yüklemdeki sabit sayıda ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="0f9fc-120">Ancak, kullanıcı girişine bağlı değişken sayıda yüklem ifadesini birleştiren bir uygulama yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="0f9fc-121">Kullanıcıdan gelen girişe bağlı olarak, sorguda çağrılan standart sorgu işleçlerini de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f9fc-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0f9fc-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="0f9fc-123">System.Linq.Expressions ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-123">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9fc-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f9fc-124">See also</span></span>

- [<span data-ttu-id="0f9fc-125">İfade Ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="0f9fc-125">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="0f9fc-126">İfade ağaçları nasıl yürütülür (C#)</span><span class="sxs-lookup"><span data-stu-id="0f9fc-126">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="0f9fc-127">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="0f9fc-127">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
