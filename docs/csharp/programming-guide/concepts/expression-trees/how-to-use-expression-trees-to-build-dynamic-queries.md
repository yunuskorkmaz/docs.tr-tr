---
title: Dinamik sorgular oluşturmak için ifade ağaçları kullanma (C#)
description: Dinamik LINQ sorguları oluşturmak için ifade ağaçlarını nasıl kullanacağınızı öğrenin. Bu sorgular, derleme zamanında bir sorgunun özellikleri bilinmiyorsa yararlıdır.
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: edcef4068c19ba8e789683cf6ba4d5ef2477e0d8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105591"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="97cab-104">Dinamik sorgular oluşturmak için ifade ağaçları kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="97cab-104">How to use expression trees to build dynamic queries (C#)</span></span>
<span data-ttu-id="97cab-105">LINQ içinde, ifade ağaçları, uygulayan veri kaynaklarını hedefleyen yapılandırılmış sorguları temsil etmek için kullanılır <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="97cab-105">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="97cab-106">Örneğin, LINQ sağlayıcısı <xref:System.Linq.IQueryable%601> ilişkisel veri depolarını sorgulamak için arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="97cab-106">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="97cab-107">C# derleyicisi, bu tür veri kaynaklarını hedefleyen sorguları, çalışma zamanında bir ifade ağacı oluşturan koda derler.</span><span class="sxs-lookup"><span data-stu-id="97cab-107">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="97cab-108">Sorgu sağlayıcısı daha sonra ifade ağacı veri yapısına çapraz geçiş yapabilir ve veri kaynağı için uygun bir sorgu diline çevirebilir.</span><span class="sxs-lookup"><span data-stu-id="97cab-108">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="97cab-109">İfade ağaçları Ayrıca LINQ 'te tür değişkenlerine atanan Lambda ifadelerini temsil etmek için de kullanılır <xref:System.Linq.Expressions.Expression%601> .</span><span class="sxs-lookup"><span data-stu-id="97cab-109">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="97cab-110">Bu konu başlığı altında, dinamik LINQ sorguları oluşturmak için ifade ağaçlarının nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97cab-110">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="97cab-111">Dinamik sorgular, bir sorgunun özelliklerinin derleme zamanında bilinmediği durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="97cab-111">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="97cab-112">Örneğin, bir uygulama, son kullanıcının verileri filtrelemek için bir veya daha fazla koşul belirtmesini sağlayan bir kullanıcı arabirimi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="97cab-112">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="97cab-113">Bu tür bir uygulamanın, sorgulama için LINQ kullanabilmesi amacıyla, çalışma zamanında LINQ sorgusu oluşturmak için ifade ağaçları kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="97cab-113">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97cab-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="97cab-114">Example</span></span>  
 <span data-ttu-id="97cab-115">Aşağıdaki örnek, bir veri kaynağına yönelik sorgu oluşturmak ve ardından yürütmek için ifade ağaçlarının nasıl kullanılacağını gösterir `IQueryable` .</span><span class="sxs-lookup"><span data-stu-id="97cab-115">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="97cab-116">Kod, aşağıdaki sorguyu temsil etmek için bir ifade ağacı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="97cab-116">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="97cab-117">Ad alanındaki Fabrika yöntemleri, <xref:System.Linq.Expressions> genel sorguyu oluşturan ifadeleri temsil eden ifade ağaçları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97cab-117">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="97cab-118">Standart sorgu operatörü yöntemlerine yapılan çağrıları temsil eden ifadeler, <xref:System.Linq.Queryable> Bu yöntemlerin uygulamalarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="97cab-118">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="97cab-119">Son ifade ağacı, <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> `IQueryable` türünde çalıştırılabilir bir sorgu oluşturmak için veri kaynağının sağlayıcısı uygulamasına geçirilir `IQueryable` .</span><span class="sxs-lookup"><span data-stu-id="97cab-119">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="97cab-120">Sonuçlar, bu sorgu değişkeni numaralandırıldığı için alınır.</span><span class="sxs-lookup"><span data-stu-id="97cab-120">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="97cab-121">Bu kod, metoduna geçirilen koşuldaki sabit sayıda ifadeyi kullanır `Queryable.Where` .</span><span class="sxs-lookup"><span data-stu-id="97cab-121">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="97cab-122">Ancak, kullanıcı girişine bağlı bir değişken sayıda koşul ifadesini birleştiren bir uygulama yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97cab-122">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="97cab-123">Ayrıca, kullanıcının girişine bağlı olarak sorguda çağrılan standart sorgu işleçlerini da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97cab-123">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="97cab-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="97cab-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="97cab-125">System. Linq. Ifadeler ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="97cab-125">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97cab-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97cab-126">See also</span></span>

- [<span data-ttu-id="97cab-127">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="97cab-127">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="97cab-128">İfade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="97cab-128">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="97cab-129">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="97cab-129">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
