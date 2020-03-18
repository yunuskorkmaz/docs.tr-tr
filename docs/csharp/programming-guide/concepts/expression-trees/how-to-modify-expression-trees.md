---
title: İfade ağaçları nasıl değiştirilir (C#)
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: e921c594497d02f5eb16cc60294e947e83636d7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73969897"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="fde9b-102">İfade ağaçları nasıl değiştirilir (C#)</span><span class="sxs-lookup"><span data-stu-id="fde9b-102">How to modify expression trees (C#)</span></span>
<span data-ttu-id="fde9b-103">Bu konu, bir ifade ağacını nasıl değiştirilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="fde9b-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="fde9b-104">İfade ağaçları değişmezdir, bu da doğrudan değiştirilemedikleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fde9b-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="fde9b-105">İfade ağacını değiştirmek için varolan bir ifade ağacının kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fde9b-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="fde9b-106"><xref:System.Linq.Expressions.ExpressionVisitor> Sınıfı, varolan bir ifade ağacında geçiş yapmak ve ziyaret ettiği her düğümü kopyalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fde9b-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="fde9b-107">İfade ağacını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="fde9b-107">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="fde9b-108">Yeni bir **Konsol Uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fde9b-108">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="fde9b-109">Ad `using` alanı için dosyaya `System.Linq.Expressions` bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fde9b-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="fde9b-110">`AndAlsoModifier` Sınıfı projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fde9b-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="fde9b-111">Bu sınıf <xref:System.Linq.Expressions.ExpressionVisitor> sınıfı devralır ve koşullu `AND` işlemleri temsil eden ifadeleri değiştirmek için özelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fde9b-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="fde9b-112">Bu işlemleri koşulludan `AND` koşulluya `OR`değiştirir.</span><span class="sxs-lookup"><span data-stu-id="fde9b-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="fde9b-113">Koşullu `AND` ifadeler ikili ifadeler <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> olarak temsil edilir, çünkü bunu yapmak için sınıf, temel türünün yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="fde9b-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="fde9b-114">`VisitBinary` Yöntemde, ona geçirilen ifade koşullu `AND` bir işlemi temsil ediyorsa, kod koşullu `OR` `AND` işleç yerine koşullu işleci içeren yeni bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="fde9b-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="fde9b-115">Geçirilen ifade koşullu `VisitBinary` `AND` bir işlemi temsil etmiyorsa, yöntem taban sınıf uygulamasına erteler.</span><span class="sxs-lookup"><span data-stu-id="fde9b-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="fde9b-116">Taban sınıf yöntemleri, ifade ağaçları gibi düğümler oluşturmak geçirilen, ancak düğümleri kendi alt ağaçları ziyaretçi tarafından özyinelemeli üretilen ifade ağaçları ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="fde9b-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="fde9b-117">Ad `using` alanı için dosyaya `System.Linq.Expressions` bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fde9b-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="fde9b-118">Bir ifade `Main` ağacı oluşturmak ve onu değiştirecek yönteme geçirmek için Program.cs dosyasındaki yönteme kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fde9b-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="fde9b-119">Kod koşullu `AND` bir işlem içeren bir ifade oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fde9b-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="fde9b-120">Daha sonra `AndAlsoModifier` sınıfın bir örneğini oluşturur ve `Modify` ifadeyi bu sınıfın yöntemine geçirir.</span><span class="sxs-lookup"><span data-stu-id="fde9b-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="fde9b-121">Değişikliği göstermek için hem özgün hem de değiştirilmiş ifade ağaçları çıktılanır.</span><span class="sxs-lookup"><span data-stu-id="fde9b-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="fde9b-122">Uygulamayı derle ve çalıştır.</span><span class="sxs-lookup"><span data-stu-id="fde9b-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde9b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fde9b-123">See also</span></span>

- [<span data-ttu-id="fde9b-124">İfade ağaçları nasıl yürütülür (C#)</span><span class="sxs-lookup"><span data-stu-id="fde9b-124">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="fde9b-125">İfade Ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="fde9b-125">Expression Trees (C#)</span></span>](./index.md)
