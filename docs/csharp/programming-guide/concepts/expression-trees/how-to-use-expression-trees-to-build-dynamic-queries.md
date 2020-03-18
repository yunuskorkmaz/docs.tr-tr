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
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Dinamik sorgular oluşturmak için ifade ağaçları nasıl kullanılır (C#)
LINQ'da ifade ağaçları, uygulayan <xref:System.Linq.IQueryable%601>veri kaynaklarını hedefleyen yapılandırılmış sorguları temsil etmek için kullanılır. Örneğin, LINQ sağlayıcısı ilişkisel <xref:System.Linq.IQueryable%601> veri depolarını sorgulamak için arabirimi uygular. C# derleyicisi, bu tür veri kaynaklarını hedefleyen sorguları çalışma zamanında bir ifade ağacı oluşturan koda dönüştürür. Sorgu sağlayıcısı daha sonra ifade ağacı veri yapısını geçiş yapabilir ve veri kaynağına uygun bir sorgu diline çevirebilir.  
  
 İfade ağaçları linq'te de türünün <xref:System.Linq.Expressions.Expression%601>değişkenlerine atanan lambda ifadelerini temsil etmek için kullanılır.  
  
 Bu konu, dinamik LINQ sorguları oluşturmak için ifade ağaçlarının nasıl kullanılacağını açıklar. Bir sorgunun ayrıntıları derleme zamanında bilinmediğinde dinamik sorgular yararlıdır. Örneğin, bir uygulama, son kullanıcının verileri filtrelemek için bir veya daha fazla yüklem belirtmesini sağlayan bir kullanıcı arabirimi sağlayabilir. Sorgulama için LINQ'yi kullanabilmek için, bu tür bir uygulamanın çalışma zamanında LINQ sorgusunu oluşturmak için ifade ağaçlarını kullanması gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorguyu bir `IQueryable` veri kaynağına karşı oluşturmak ve sonra yürütmek için ifade ağaçlarını nasıl kullanacağınızı gösterir. Kod, aşağıdaki sorguyu temsil edecek bir ifade ağacı oluşturur:  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <xref:System.Linq.Expressions> Ad alanındaki fabrika yöntemleri, genel sorguyu oluşturan ifadeleri temsil eden ifade ağaçları oluşturmak için kullanılır. Standart sorgu işleci yöntemlerine yapılan çağrıları temsil <xref:System.Linq.Queryable> eden ifadeler, bu yöntemlerin uygulamalarına başvurur. Son ifade ağacı, tür <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> `IQueryable`yürütülebilir bir `IQueryable` sorgu oluşturmak için veri kaynağı sağlayıcısının uygulamasına geçirilir. Sonuçlar, sorgu değişkeninin sayısala sıyrıkları ile elde edilir.  
  
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
  
 Bu kod, `Queryable.Where` yönteme geçirilen yüklemdeki sabit sayıda ifade kullanır. Ancak, kullanıcı girişine bağlı değişken sayıda yüklem ifadesini birleştiren bir uygulama yazabilirsiniz. Kullanıcıdan gelen girişe bağlı olarak, sorguda çağrılan standart sorgu işleçlerini de değiştirebilirsiniz.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- System.Linq.Expressions ad alanını ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade Ağaçları (C#)](./index.md)
- [İfade ağaçları nasıl yürütülür (C#)](./how-to-execute-expression-trees.md)
- [Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
