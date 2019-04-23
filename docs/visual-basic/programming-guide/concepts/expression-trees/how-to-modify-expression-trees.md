---
title: 'Nasıl yapılır: (Visual Basic) ifade ağaçlarını değiştirme'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: a9b94cbd7bf24b0cc8efcfc66d8c5e7df4e27307
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305331"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="e395a-102">Nasıl yapılır: (Visual Basic) ifade ağaçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="e395a-102">How to: Modify Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="e395a-103">Bu konu nasıl bir ifade ağacı değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e395a-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="e395a-104">İfade ağaçları değişmezse, yani bunlar doğrudan değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e395a-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="e395a-105">İfade ağacı değiştirmek için var olan bir ifade ağacı bir kopyasını oluşturun ve bir kopya oluşturduğunuzda gerekli değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="e395a-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="e395a-106">Kullanabileceğiniz <xref:System.Linq.Expressions.ExpressionVisitor> var olan bir ifade ağacı gezme ve onu ziyaret her düğüm kopyalamak için bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="e395a-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="e395a-107">İfade ağacı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="e395a-107">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="e395a-108">Yeni bir **konsol uygulaması** proje.</span><span class="sxs-lookup"><span data-stu-id="e395a-108">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="e395a-109">Ekleme bir `Imports` deyimi için dosyaya `System.Linq.Expressions` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e395a-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="e395a-110">Ekleme `AndAlsoModifier` projenize sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e395a-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="e395a-111">Bu sınıf devralır <xref:System.Linq.Expressions.ExpressionVisitor> temsil eden koşullu ifadeleri değiştirmek için özelleştirilmiş ve sınıf `AND` operations.</span><span class="sxs-lookup"><span data-stu-id="e395a-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="e395a-112">Erişim ilkesinden işlemlerini değişiklikleri `AND` koşullu için `OR`.</span><span class="sxs-lookup"><span data-stu-id="e395a-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="e395a-113">Bu sınıf geçersiz kılmalarını yapmak için <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> temel türün yöntemi olduğundan koşullu `AND` ifadeleri, ikili ifadelere temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="e395a-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="e395a-114">İçinde `VisitBinary` koşullu kendisine geçirilen ifade temsil ediyorsa yöntemi `AND` işlemi, kod yapıları koşullu içeren yeni bir ifade `OR` koşul yerine işleci `AND` işleci.</span><span class="sxs-lookup"><span data-stu-id="e395a-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="e395a-115">Geçirilen ifade `VisitBinary` koşullu göstermiyor `AND` işlem, yöntem, temel sınıf uygulamasına erteler.</span><span class="sxs-lookup"><span data-stu-id="e395a-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="e395a-116">İletilen ifade ağaçları gibi yapı düğümleri ancak düğümleri olan ifade ağaçları yerine kendi alt ağaçları sahip taban sınıf yöntemlerini yinelemeli olarak ziyaretçi tarafından üretilen.</span><span class="sxs-lookup"><span data-stu-id="e395a-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="e395a-117">Ekleme bir `Imports` deyimi için dosyaya `System.Linq.Expressions` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e395a-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="e395a-118">Kodu `Main` yöntemi Module1.vb dosyasındaki bir ifade ağacı oluşturmak ve bu yönteme geçirmek için onu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e395a-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="e395a-119">Kod içeren bir koşullu ifade oluşturur `AND` işlemi.</span><span class="sxs-lookup"><span data-stu-id="e395a-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="e395a-120">Ardından bir örneğini oluşturur `AndAlsoModifier` sınıfı ve ifade geçirir `Modify` bu sınıfın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e395a-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="e395a-121">Hem özgün hem de değiştirilmiş ifade ağaçlarını değiştirme gösterilecek yüzdelik.</span><span class="sxs-lookup"><span data-stu-id="e395a-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="e395a-122">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e395a-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e395a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e395a-123">See also</span></span>

- [<span data-ttu-id="e395a-124">Nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme</span><span class="sxs-lookup"><span data-stu-id="e395a-124">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="e395a-125">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e395a-125">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
