---
title: İfade ağaçlarını değiştirme (C#)
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: e921c594497d02f5eb16cc60294e947e83636d7a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969897"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="b6664-102">İfade ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="b6664-102">How to modify expression trees (C#)</span></span>
<span data-ttu-id="b6664-103">Bu konu başlığı altında, bir ifade ağacının nasıl değiştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b6664-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="b6664-104">İfade ağaçları sabittir ve bu, doğrudan değiştirilemediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b6664-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="b6664-105">Bir ifade ağacını değiştirmek için, var olan bir ifade ağacının bir kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6664-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="b6664-106"><xref:System.Linq.Expressions.ExpressionVisitor> sınıfını, var olan bir ifade ağacında çapraz geçiş yapmak ve bulduğu her düğümü kopyalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6664-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="b6664-107">Bir ifade ağacını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="b6664-107">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="b6664-108">Yeni bir **konsol uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6664-108">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="b6664-109">`System.Linq.Expressions` ad alanı için dosyaya bir `using` yönergesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6664-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="b6664-110">`AndAlsoModifier` sınıfını projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6664-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
    ```csharp  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     <span data-ttu-id="b6664-111">Bu sınıf <xref:System.Linq.Expressions.ExpressionVisitor> sınıfını devralır ve koşullu `AND` işlemlerini temsil eden ifadeleri değiştirmek için özelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b6664-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="b6664-112">Bu işlemleri koşullu bir `AND` koşullu `OR`olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b6664-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="b6664-113">Bunu yapmak için, koşullu `AND` ifadeler ikili ifadeler olarak temsil edildiği için sınıf temel türün <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b6664-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="b6664-114">`VisitBinary` yönteminde, kendisine geçirilen ifade koşullu bir `AND` işlemini gösteriyorsa, kod koşullu `AND` işleci yerine koşullu `OR` işlecini içeren yeni bir ifade oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b6664-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="b6664-115">`VisitBinary` geçirilen ifade koşullu `AND` işlemini temsil ediyorsa, yöntemi temel sınıf uygulamasına erteler.</span><span class="sxs-lookup"><span data-stu-id="b6664-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="b6664-116">Temel sınıf yöntemleri, geçirilen ifade ağaçları gibi düğümleri oluşturur, ancak düğümlerin alt ağaçları, ziyaretçi tarafından yinelemeli olarak üretilen ifade ağaçları ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b6664-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="b6664-117">`System.Linq.Expressions` ad alanı için dosyaya bir `using` yönergesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6664-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="b6664-118">Bir ifade ağacı oluşturmak ve bunu değiştirecek yönteme geçirmek için Program.cs dosyasındaki `Main` yöntemine kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6664-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
    ```csharp  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     <span data-ttu-id="b6664-119">Kod, koşullu `AND` işlemi içeren bir ifade oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b6664-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="b6664-120">Daha sonra, `AndAlsoModifier` sınıfının bir örneğini oluşturur ve bu sınıfın `Modify` yöntemine ifadeyi geçirir.</span><span class="sxs-lookup"><span data-stu-id="b6664-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="b6664-121">Hem özgün hem de değiştirilen ifade ağaçları değişikliği göstermek için çıktılardır.</span><span class="sxs-lookup"><span data-stu-id="b6664-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="b6664-122">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b6664-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6664-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6664-123">See also</span></span>

- [<span data-ttu-id="b6664-124">İfade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="b6664-124">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="b6664-125">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="b6664-125">Expression Trees (C#)</span></span>](./index.md)
