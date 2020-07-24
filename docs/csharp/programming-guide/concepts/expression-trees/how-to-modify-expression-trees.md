---
title: İfade ağaçlarını değiştirme (C#)
description: Varolan bir ifade ağacının kopyasını oluşturarak ve gerekli değişiklikleri yaparak bir ifade ağacını değiştirme hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 45aea18e253811d4e5c60f23f7f8496d4358f64c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105601"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="47e2f-103">İfade ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="47e2f-103">How to modify expression trees (C#)</span></span>
<span data-ttu-id="47e2f-104">Bu konu başlığı altında, bir ifade ağacının nasıl değiştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47e2f-104">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="47e2f-105">İfade ağaçları sabittir ve bu, doğrudan değiştirilemediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="47e2f-105">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="47e2f-106">Bir ifade ağacını değiştirmek için, var olan bir ifade ağacının bir kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47e2f-106">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="47e2f-107"><xref:System.Linq.Expressions.ExpressionVisitor>Sınıfını, var olan bir ifade ağacında çapraz geçiş yapmak ve bulduğu her düğümü kopyalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47e2f-107">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="47e2f-108">Bir ifade ağacını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="47e2f-108">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="47e2f-109">Yeni bir **konsol uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47e2f-109">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="47e2f-110">`using`Ad alanı için dosyasına bir yönerge ekleyin `System.Linq.Expressions` .</span><span class="sxs-lookup"><span data-stu-id="47e2f-110">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="47e2f-111">`AndAlsoModifier`Sınıfını projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="47e2f-111">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="47e2f-112">Bu sınıf sınıfını devralır <xref:System.Linq.Expressions.ExpressionVisitor> ve koşullu işlemleri temsil eden ifadeleri değiştirmek için özelleştirilmiştir `AND` .</span><span class="sxs-lookup"><span data-stu-id="47e2f-112">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="47e2f-113">Bu işlemleri koşullu sunucudan `AND` koşullu olarak değiştirir `OR` .</span><span class="sxs-lookup"><span data-stu-id="47e2f-113">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="47e2f-114">Bunu yapmak için, <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> koşullu `AND` ifadeler ikili ifadeler olarak temsil edildiği için sınıf temel tür yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="47e2f-114">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="47e2f-115">`VisitBinary`Yönteminde, kendisine geçirilen ifade koşullu bir işlemi temsil ediyorsa `AND` , kod koşullu işleç yerine koşullu işleci içeren yeni bir ifade oluşturur `OR` `AND` .</span><span class="sxs-lookup"><span data-stu-id="47e2f-115">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="47e2f-116">Geçirilen ifade `VisitBinary` koşullu bir işlemi temsil ediyorsa `AND` , yöntemi temel sınıf uygulamasına erteler.</span><span class="sxs-lookup"><span data-stu-id="47e2f-116">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="47e2f-117">Temel sınıf yöntemleri, geçirilen ifade ağaçları gibi düğümleri oluşturur, ancak düğümlerin alt ağaçları, ziyaretçi tarafından yinelemeli olarak üretilen ifade ağaçları ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="47e2f-117">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="47e2f-118">`using`Ad alanı için dosyasına bir yönerge ekleyin `System.Linq.Expressions` .</span><span class="sxs-lookup"><span data-stu-id="47e2f-118">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="47e2f-119">`Main`Program.cs dosyasındaki yöntemine kod ekleyerek bir ifade ağacı oluşturun ve bunu değiştirecek yönteme geçirin.</span><span class="sxs-lookup"><span data-stu-id="47e2f-119">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="47e2f-120">Kod, koşullu bir işlem içeren bir ifade oluşturur `AND` .</span><span class="sxs-lookup"><span data-stu-id="47e2f-120">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="47e2f-121">Daha sonra sınıfın bir örneğini oluşturur `AndAlsoModifier` ve `Modify` Bu sınıfın yöntemine ifadeyi geçirir.</span><span class="sxs-lookup"><span data-stu-id="47e2f-121">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="47e2f-122">Hem özgün hem de değiştirilen ifade ağaçları değişikliği göstermek için çıktılardır.</span><span class="sxs-lookup"><span data-stu-id="47e2f-122">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="47e2f-123">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="47e2f-123">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e2f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47e2f-124">See also</span></span>

- [<span data-ttu-id="47e2f-125">İfade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="47e2f-125">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="47e2f-126">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="47e2f-126">Expression Trees (C#)</span></span>](./index.md)
