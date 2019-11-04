---
title: 'Nasıl yapılır: dinamik sorgular oluşturmak için Ifade ağaçları kullanma (C#)'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 7f18539dba17f9fcb8769ca56d977908c58e6579
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418684"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="22105-102">Nasıl yapılır: dinamik sorgular oluşturmak için Ifade ağaçları kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="22105-102">How to: Use Expression Trees to Build Dynamic Queries (C#)</span></span>
<span data-ttu-id="22105-103">LINQ içinde, ifade ağaçları, <xref:System.Linq.IQueryable%601>uygulayan veri kaynaklarını hedefleyen yapısal sorguları temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22105-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="22105-104">Örneğin, LINQ sağlayıcısı ilişkisel veri depolarını sorgulamak için <xref:System.Linq.IQueryable%601> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="22105-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="22105-105">Derleyici C# , bu tür veri kaynaklarını hedefleyen sorguları, çalışma zamanında bir ifade ağacı oluşturan koda derler.</span><span class="sxs-lookup"><span data-stu-id="22105-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="22105-106">Sorgu sağlayıcısı daha sonra ifade ağacı veri yapısına çapraz geçiş yapabilir ve veri kaynağı için uygun bir sorgu diline çevirebilir.</span><span class="sxs-lookup"><span data-stu-id="22105-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="22105-107">İfade ağaçları Ayrıca LINQ içinde <xref:System.Linq.Expressions.Expression%601>tür değişkenlerine atanan Lambda ifadelerini temsil etmek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22105-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="22105-108">Bu konu başlığı altında, dinamik LINQ sorguları oluşturmak için ifade ağaçlarının nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22105-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="22105-109">Dinamik sorgular, bir sorgunun özelliklerinin derleme zamanında bilinmediği durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="22105-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="22105-110">Örneğin, bir uygulama, son kullanıcının verileri filtrelemek için bir veya daha fazla koşul belirtmesini sağlayan bir kullanıcı arabirimi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="22105-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="22105-111">Bu tür bir uygulamanın, sorgulama için LINQ kullanabilmesi amacıyla, çalışma zamanında LINQ sorgusu oluşturmak için ifade ağaçları kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="22105-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22105-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="22105-112">Example</span></span>  
 <span data-ttu-id="22105-113">Aşağıdaki örnek, `IQueryable` veri kaynağında bir sorgu oluşturmak ve sonra çalıştırmak için ifade ağaçlarının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="22105-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="22105-114">Kod, aşağıdaki sorguyu temsil etmek için bir ifade ağacı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="22105-114">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="22105-115"><xref:System.Linq.Expressions> ad alanındaki Fabrika yöntemleri, genel sorguyu oluşturan ifadeleri temsil eden ifade ağaçları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22105-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="22105-116">Standart sorgu operatörü yöntemlerine yapılan çağrıları temsil eden ifadeler, bu yöntemlerin <xref:System.Linq.Queryable> uygulamalarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="22105-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="22105-117">Son ifade ağacı, `IQueryable`türünde yürütülebilir bir sorgu oluşturmak için `IQueryable` veri kaynağı sağlayıcısının <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> uygulamasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="22105-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="22105-118">Sonuçlar, bu sorgu değişkeni numaralandırıldığı için alınır.</span><span class="sxs-lookup"><span data-stu-id="22105-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="22105-119">Bu kod, `Queryable.Where` metoduna geçirilen koşuldaki sabit sayıda ifadeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="22105-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="22105-120">Ancak, kullanıcı girişine bağlı bir değişken sayıda koşul ifadesini birleştiren bir uygulama yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22105-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="22105-121">Ayrıca, kullanıcının girişine bağlı olarak sorguda çağrılan standart sorgu işleçlerini da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22105-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="22105-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="22105-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="22105-123">System. Linq. Ifadeler ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="22105-123">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22105-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22105-124">See also</span></span>

- [<span data-ttu-id="22105-125">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="22105-125">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="22105-126">Nasıl yapılır: Ifade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="22105-126">How to: Execute Expression Trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="22105-127">Nasıl yapılır: çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="22105-127">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
