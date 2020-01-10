---
title: Dinamik sorgular oluşturmak için ifade ağaçları kullanma (C#)
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 6114ec13dd43a7df146b87dda00fba06d6eb870c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635905"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Dinamik sorgular oluşturmak için ifade ağaçları kullanma (C#)
LINQ içinde, ifade ağaçları, <xref:System.Linq.IQueryable%601>uygulayan veri kaynaklarını hedefleyen yapısal sorguları temsil etmek için kullanılır. Örneğin, LINQ sağlayıcısı ilişkisel veri depolarını sorgulamak için <xref:System.Linq.IQueryable%601> arabirimini uygular. Derleyici C# , bu tür veri kaynaklarını hedefleyen sorguları, çalışma zamanında bir ifade ağacı oluşturan koda derler. Sorgu sağlayıcısı daha sonra ifade ağacı veri yapısına çapraz geçiş yapabilir ve veri kaynağı için uygun bir sorgu diline çevirebilir.  
  
 İfade ağaçları Ayrıca LINQ içinde <xref:System.Linq.Expressions.Expression%601>tür değişkenlerine atanan Lambda ifadelerini temsil etmek için de kullanılır.  
  
 Bu konu başlığı altında, dinamik LINQ sorguları oluşturmak için ifade ağaçlarının nasıl kullanılacağı açıklanmaktadır. Dinamik sorgular, bir sorgunun özelliklerinin derleme zamanında bilinmediği durumlarda faydalıdır. Örneğin, bir uygulama, son kullanıcının verileri filtrelemek için bir veya daha fazla koşul belirtmesini sağlayan bir kullanıcı arabirimi sağlayabilir. Bu tür bir uygulamanın, sorgulama için LINQ kullanabilmesi amacıyla, çalışma zamanında LINQ sorgusu oluşturmak için ifade ağaçları kullanması gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `IQueryable` veri kaynağında bir sorgu oluşturmak ve sonra çalıştırmak için ifade ağaçlarının nasıl kullanılacağını gösterir. Kod, aşağıdaki sorguyu temsil etmek için bir ifade ağacı oluşturur:  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <xref:System.Linq.Expressions> ad alanındaki Fabrika yöntemleri, genel sorguyu oluşturan ifadeleri temsil eden ifade ağaçları oluşturmak için kullanılır. Standart sorgu operatörü yöntemlerine yapılan çağrıları temsil eden ifadeler, bu yöntemlerin <xref:System.Linq.Queryable> uygulamalarına başvurur. Son ifade ağacı, `IQueryable`türünde yürütülebilir bir sorgu oluşturmak için `IQueryable` veri kaynağı sağlayıcısının <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> uygulamasına geçirilir. Sonuçlar, bu sorgu değişkeni numaralandırıldığı için alınır.  
  
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
  
 Bu kod, `Queryable.Where` metoduna geçirilen koşuldaki sabit sayıda ifadeyi kullanır. Ancak, kullanıcı girişine bağlı bir değişken sayıda koşul ifadesini birleştiren bir uygulama yazabilirsiniz. Ayrıca, kullanıcının girişine bağlı olarak sorguda çağrılan standart sorgu işleçlerini da değiştirebilirsiniz.  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- System. Linq. Ifadeler ad alanını ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (C#)](./index.md)
- [İfade ağaçlarını yürütme (C#)](./how-to-execute-expression-trees.md)
- [Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
