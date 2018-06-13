---
title: 'Nasıl yapılır: dinamik sorgular (C#) derlemek için ifade ağaçları kullanma'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 3ae21422576abccde51d7708007132a87bedbad6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327714"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="de417-102">Nasıl yapılır: dinamik sorgular (C#) derlemek için ifade ağaçları kullanma</span><span class="sxs-lookup"><span data-stu-id="de417-102">How to: Use Expression Trees to Build Dynamic Queries (C#)</span></span>
<span data-ttu-id="de417-103">LINQ, uygulama veri kaynaklarını hedef yapılandırılmış sorguların temsil etmek için ifade ağaçları kullanılan <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="de417-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="de417-104">Örneğin, LINQ sağlayıcısını uygular <xref:System.Linq.IQueryable%601> ilişkisel veri depoları sorgulamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="de417-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="de417-105">C# Derleyici çalışma zamanında bir ifade ağacına derlemeler koda gibi veri kaynakları hedef sorguları derler.</span><span class="sxs-lookup"><span data-stu-id="de417-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="de417-106">Sorgu sağlayıcısı ifade ağaç veri yapısı çapraz geçiş ve veri kaynağı için uygun bir sorgu dili içine çevir.</span><span class="sxs-lookup"><span data-stu-id="de417-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="de417-107">İfade ağaçları için de kullanılır LINQ türü değişkenlere atanan lambda ifadeleri temsil <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="de417-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="de417-108">Bu konu, dinamik LINQ sorguları oluşturmak için ifade ağaçları kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="de417-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="de417-109">Dinamik sorgular derleme zamanında bir sorgu ayrıntılarını bilinmiyor olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="de417-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="de417-110">Örneğin, bir uygulama verilerini filtrelemek için bir veya daha fazla koşulları belirtmek son kullanıcının sağlayan bir kullanıcı arabirimi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="de417-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="de417-111">LINQ sorgulaması için kullanmak için bu tür bir uygulama ifade ağaçları çalışma zamanında LINQ sorgusu oluşturmak için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de417-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de417-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="de417-112">Example</span></span>  
 <span data-ttu-id="de417-113">Aşağıdaki örnek, bir sorgu oluşturmak için ifade ağaçları kullanma gösterilmektedir bir `IQueryable` veri kaynağı ve sonra yürütün.</span><span class="sxs-lookup"><span data-stu-id="de417-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="de417-114">Kod aşağıdaki sorguyu temsil etmek için bir ifade ağacına oluşturur:</span><span class="sxs-lookup"><span data-stu-id="de417-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 <span data-ttu-id="de417-115">Fabrika yöntemlere <xref:System.Linq.Expressions> ad alanı, genel sorgulamasını olun ifadeleri temsil ifade ağaçları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de417-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="de417-116">Standart sorgu işleci yöntem çağrıları temsil eden ifadeleri başvurmak <xref:System.Linq.Queryable> bu yöntemlerin uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="de417-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="de417-117">Son ifade ağacına geçirilir <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> sağlayıcısı uyarlamasını `IQueryable` türü yürütülebilir bir sorgu oluşturmak için veri kaynağı `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="de417-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="de417-118">Bu sorgu değişkeni numaralandırarak sonuçları elde edilir.</span><span class="sxs-lookup"><span data-stu-id="de417-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="de417-119">Bu kodu geçirilir karşılaştırma ifadeleri sabit sayıda kullanır `Queryable.Where` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de417-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="de417-120">Ancak, kullanıcı girişi bağlıdır değişken karşılaştırma ifadeleri sayıda birleştiren bir uygulama yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de417-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="de417-121">Kullanıcı girişi bağlı olarak sorguyu adlı standart sorgu işleçleri de değişebilir.</span><span class="sxs-lookup"><span data-stu-id="de417-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de417-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="de417-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="de417-123">Yeni bir **konsol uygulaması** projesi.</span><span class="sxs-lookup"><span data-stu-id="de417-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="de417-124">Zaten başvurulmayan System.Core.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="de417-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="de417-125">System.Linq.Expressions ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="de417-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="de417-126">Örnekten kodu kopyalayın ve yapıştırın `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de417-126">Copy the code from the example and paste it into the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de417-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de417-127">See Also</span></span>  
 [<span data-ttu-id="de417-128">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="de417-128">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="de417-129">Nasıl yapılır: ifade ağaçlarını (C#) yürütme</span><span class="sxs-lookup"><span data-stu-id="de417-129">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="de417-130">Nasıl yapılır: çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="de417-130">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
