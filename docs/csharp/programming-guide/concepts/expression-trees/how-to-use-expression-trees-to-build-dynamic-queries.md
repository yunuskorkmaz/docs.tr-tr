---
title: 'Nasıl yapılır: Dinamik sorgular derlemek için ifade ağaçları kullanma (C#)'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: dec9d84f7fa37f859e307f2a653464608684bc88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668529"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Nasıl yapılır: Dinamik sorgular derlemek için ifade ağaçları kullanma (C#)
LINQ içinde uygulama veri kaynaklarını hedefleyen yapılandırılmış sorguların temsil etmek için ifade ağaçları kullanılan <xref:System.Linq.IQueryable%601>. Örneğin, LINQ sağlayıcı uygulayan <xref:System.Linq.IQueryable%601> ilişkisel veri deposu sorgulamak için arabirim. C# derleyicisi gibi veri kaynakları, çalışma zamanında bir ifade ağacı oluşturan koda hedef sorguları derler. Sorgu sağlayıcısına geçiş ifadesi ağaç veri yapısı ve veri kaynağı için uygun bir sorgu dili küçültmesini.  
  
 İfade ağaçları için de kullanılır LINQ türündeki değişkenler için atanmış olan lambda ifadeleri temsil <xref:System.Linq.Expressions.Expression%601>.  
  
 Bu konuda, dinamik LINQ sorguları oluşturmak için ifade ağaçları kullanmayı açıklar. Dinamik sorgular, bir sorgu ayrıntılarını derleme zamanında bilinen olduğunda yararlıdır. Örneğin, bir uygulama verilerini filtrelemek için bir veya daha fazla koşulları belirtmek son kullanıcının sağlayan bir kullanıcı arabirimi sağlayabilir. Sorgulamak için LINQ kullanmak için bu tür bir uygulama ifade ağaçları çalışma zamanında LINQ sorgusu oluşturmak için kullanmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir sorgu oluşturmak için ifade ağaçları kullanma işlemi gösterilmektedir bir `IQueryable` veri kaynağını seçin ve sonra yürütün. Kod, aşağıdaki sorguyu temsil etmek için bir ifade ağacı oluşturur:  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 Fabrika yöntemleri <xref:System.Linq.Expressions> ad alanı, genel sorgu yapmak ifadeleri temsil eden bir ifade ağacı oluşturmak için kullanılır. Standart sorgu işleci yöntemlerinin çağrıları temsil eden ifadeleri başvurmak <xref:System.Linq.Queryable> bu yöntemlerin uygulamaları. Son bir ifade ağacı geçirilir <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> sağlayıcısı uygulaması `IQueryable` yürütülebilir bir sorgu türü oluşturmak için veri kaynağı `IQueryable`. Bu sorgu değişkeni numaralandırarak sonuçlar elde edilir.  
  
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
  
 Bu kodu ifadeler sabit sayıda geçirilir koşulu kullanır `Queryable.Where` yöntemi. Ancak, kullanıcı girişi bağlıdır değişken koşul ifadeleri sayısı birleştiren bir uygulama yazabilirsiniz. Kullanıcı girişini bağlı olarak sorguyu adlı standart sorgu işleçleri de değişebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Yeni bir **konsol uygulaması** proje.  
  
- Zaten başvurulmayan System.Core.dll öğesine başvuru ekleyin.  
  
- System.Linq.Expressions ad alanı içerir.  
  
- Örnek kodu kopyalayın ve yapıştırın `Main` yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Nasıl yapılır: İfade ağaçlarını yürütme (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Nasıl yapılır: Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
