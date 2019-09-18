---
title: 'Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: ac196b56f178659765437a97a25f46c04f8040fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054208"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="4dd0c-102">Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dd0c-102">How to: Modify Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="4dd0c-103">Bu konu başlığı altında, bir ifade ağacının nasıl değiştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="4dd0c-104">İfade ağaçları sabittir ve bu, doğrudan değiştirilemediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="4dd0c-105">Bir ifade ağacını değiştirmek için, var olan bir ifade ağacının bir kopyasını oluşturmanız ve kopyayı oluşturduğunuzda gerekli değişiklikleri yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="4dd0c-106">Sınıfını, <xref:System.Linq.Expressions.ExpressionVisitor> var olan bir ifade ağacında çapraz geçiş yapmak ve bulduğu her düğümü kopyalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>

## <a name="to-modify-an-expression-tree"></a><span data-ttu-id="4dd0c-107">Bir ifade ağacını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="4dd0c-107">To modify an expression tree</span></span>

1. <span data-ttu-id="4dd0c-108">Yeni bir **konsol uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-108">Create a new **Console Application** project.</span></span>

2. <span data-ttu-id="4dd0c-109">Ad`System.Linq.Expressions` alanı `Imports` için dosyasına bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

3. <span data-ttu-id="4dd0c-110">`AndAlsoModifier` Sınıfını projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-110">Add the `AndAlsoModifier` class to your project.</span></span>

    ```vb
    Public Class AndAlsoModifier
        Inherits ExpressionVisitor

        Public Function Modify(ByVal expr As Expression) As Expression
            Return Visit(expr)
        End Function

        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression
            If b.NodeType = ExpressionType.AndAlso Then
                Dim left = Me.Visit(b.Left)
                Dim right = Me.Visit(b.Right)

                ' Make this binary expression an OrElse operation instead
                ' of an AndAlso operation.
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _
                                             b.IsLiftedToNull, b.Method)
            End If

            Return MyBase.VisitBinary(b)
        End Function
    End Class
    ```

    <span data-ttu-id="4dd0c-111">Bu sınıf <xref:System.Linq.Expressions.ExpressionVisitor> sınıfını devralır ve koşullu `AND` işlemleri temsil eden ifadeleri değiştirmek için özelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="4dd0c-112">Bu işlemleri koşullu `AND` sunucudan koşullu `OR`olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="4dd0c-113">Bunu yapmak için, koşullu <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> `AND` ifadeler ikili ifadeler olarak temsil edildiği için sınıf temel tür yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="4dd0c-114">Yönteminde, kendisine geçirilen ifade koşullu `AND` bir işlemi temsil ediyorsa, kod koşullu `OR` işleci `AND` içeren yeni bir ifade oluşturur `VisitBinary` işlecinde.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="4dd0c-115">Geçirilen `VisitBinary` ifade koşullu `AND` bir işlemi temsil ediyorsa, yöntemi temel sınıf uygulamasına erteler.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="4dd0c-116">Temel sınıf yöntemleri, geçirilen ifade ağaçları gibi düğümleri oluşturur, ancak düğümlerin alt ağaçları, ziyaretçi tarafından yinelemeli olarak üretilen ifade ağaçları ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>

4. <span data-ttu-id="4dd0c-117">Ad`System.Linq.Expressions` alanı `Imports` için dosyasına bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

5. <span data-ttu-id="4dd0c-118">Bir ifade ağacı oluşturmak `Main` ve bunu değiştirecek yönteme geçirmek için Module1. vb dosyasındaki yöntemine kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>

    ```vb
    Dim expr As Expression(Of Func(Of String, Boolean)) = _
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")

    Console.WriteLine(expr)

    Dim modifier As New AndAlsoModifier()
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))

    Console.WriteLine(modifiedExpr)

    ' This code produces the following output:
    ' name => ((name.Length > 10) && name.StartsWith("G"))
    ' name => ((name.Length > 10) || name.StartsWith("G"))
    ```

    <span data-ttu-id="4dd0c-119">Kod, koşullu `AND` bir işlem içeren bir ifade oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="4dd0c-120">Daha sonra `AndAlsoModifier` sınıfın bir örneğini oluşturur ve bu sınıfın `Modify` yöntemine ifadeyi geçirir.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="4dd0c-121">Hem özgün hem de değiştirilen ifade ağaçları değişikliği göstermek için çıktılardır.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-121">Both the original and the modified expression trees are outputted to show the change.</span></span>

6. <span data-ttu-id="4dd0c-122">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-122">Compile and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dd0c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dd0c-123">See also</span></span>

- [<span data-ttu-id="4dd0c-124">Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dd0c-124">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="4dd0c-125">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dd0c-125">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
