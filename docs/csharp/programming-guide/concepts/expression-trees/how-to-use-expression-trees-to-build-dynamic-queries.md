---
title: 'Nasıl yapılır: dinamik sorgular (C#) derlemek için ifade ağaçları kullanma'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 3ae21422576abccde51d7708007132a87bedbad6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Nasıl yapılır: dinamik sorgular (C#) derlemek için ifade ağaçları kullanma
LINQ, uygulama veri kaynaklarını hedef yapılandırılmış sorguların temsil etmek için ifade ağaçları kullanılan <xref:System.Linq.IQueryable%601>. Örneğin, LINQ sağlayıcısını uygular <xref:System.Linq.IQueryable%601> ilişkisel veri depoları sorgulamak için arabirim. C# Derleyici çalışma zamanında bir ifade ağacına derlemeler koda gibi veri kaynakları hedef sorguları derler. Sorgu sağlayıcısı ifade ağaç veri yapısı çapraz geçiş ve veri kaynağı için uygun bir sorgu dili içine çevir.  
  
 İfade ağaçları için de kullanılır LINQ türü değişkenlere atanan lambda ifadeleri temsil <xref:System.Linq.Expressions.Expression%601>.  
  
 Bu konu, dinamik LINQ sorguları oluşturmak için ifade ağaçları kullanmayı açıklar. Dinamik sorgular derleme zamanında bir sorgu ayrıntılarını bilinmiyor olduğunda yararlıdır. Örneğin, bir uygulama verilerini filtrelemek için bir veya daha fazla koşulları belirtmek son kullanıcının sağlayan bir kullanıcı arabirimi sağlayabilir. LINQ sorgulaması için kullanmak için bu tür bir uygulama ifade ağaçları çalışma zamanında LINQ sorgusu oluşturmak için kullanmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorgu oluşturmak için ifade ağaçları kullanma gösterilmektedir bir `IQueryable` veri kaynağı ve sonra yürütün. Kod aşağıdaki sorguyu temsil etmek için bir ifade ağacına oluşturur:  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 Fabrika yöntemlere <xref:System.Linq.Expressions> ad alanı, genel sorgulamasını olun ifadeleri temsil ifade ağaçları oluşturmak için kullanılır. Standart sorgu işleci yöntem çağrıları temsil eden ifadeleri başvurmak <xref:System.Linq.Queryable> bu yöntemlerin uygulamaları. Son ifade ağacına geçirilir <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> sağlayıcısı uyarlamasını `IQueryable` türü yürütülebilir bir sorgu oluşturmak için veri kaynağı `IQueryable`. Bu sorgu değişkeni numaralandırarak sonuçları elde edilir.  
  
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
  
 Bu kodu geçirilir karşılaştırma ifadeleri sabit sayıda kullanır `Queryable.Where` yöntemi. Ancak, kullanıcı girişi bağlıdır değişken karşılaştırma ifadeleri sayıda birleştiren bir uygulama yazabilirsiniz. Kullanıcı girişi bağlı olarak sorguyu adlı standart sorgu işleçleri de değişebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Yeni bir **konsol uygulaması** projesi.  
  
-   Zaten başvurulmayan System.Core.dll bir başvuru ekleyin.  
  
-   System.Linq.Expressions ad alanı içerir.  
  
-   Örnekten kodu kopyalayın ve yapıştırın `Main` yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Nasıl yapılır: ifade ağaçlarını (C#) yürütme](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Nasıl yapılır: çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
