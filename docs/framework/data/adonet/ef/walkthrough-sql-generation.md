---
title: 'İzlenecek yol: SQL Üretimi'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 09b5a3c2dea5cd0483d617ee8064b41dc19c3374
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248283"
---
# <a name="walkthrough-sql-generation"></a><span data-ttu-id="2ca35-102">İzlenecek yol: SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="2ca35-102">Walkthrough: SQL Generation</span></span>

<span data-ttu-id="2ca35-103">Bu konuda, [örnek SAĞLAYıCıDA](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)SQL oluşturma işleminin nasıl gerçekleştiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-103">This topic illustrates how SQL generation occurs in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0).</span></span> <span data-ttu-id="2ca35-104">Aşağıdaki Entity SQL sorgusu, örnek sağlayıcıda bulunan modeli kullanır:</span><span class="sxs-lookup"><span data-stu-id="2ca35-104">The following Entity SQL query uses the model that is included with the sample provider:</span></span>

```sql
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName
        FROM NorthwindEntities.Products AS P) as j1
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry
            FROM NorthwindEntities.OrderDetails AS OD) as j2
            ON j1.ProductId == j2.ProductId
```

<span data-ttu-id="2ca35-105">Sorgu, sağlayıcıya geçirilen aşağıdaki çıkış komut ağacını üretir:</span><span class="sxs-lookup"><span data-stu-id="2ca35-105">The query produces the following output command tree that is passed to the provider:</span></span>

```
DbQueryCommandTree
|_Parameters
|_Query : Collection{Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]}
  |_Project
    |_Input : 'Join4'
    | |_InnerJoin
    |   |_Left : 'Join1'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent1'
    |   |   | |_Scan : dbo.Products
    |   |   |_Right : 'Extent2'
    |   |   | |_Scan : dbo.Categories
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent1).CategoryID
    |   |       |_=
    |   |       |_Var(Extent2).CategoryID
    |   |_Right : 'Join3'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent3'
    |   |   | |_Scan : dbo.OrderDetails
    |   |   |_Right : 'Join2'
    |   |   | |_LeftOuterJoin
    |   |   |   |_Left : 'Extent4'
    |   |   |   | |_Scan : dbo.Orders
    |   |   |   |_Right : 'Extent5'
    |   |   |   | |_Scan : dbo.InternationalOrders
    |   |   |   |_JoinCondition
    |   |   |     |_
    |   |   |       |_Var(Extent4).OrderID
    |   |   |       |_=
    |   |   |       |_Var(Extent5).OrderID
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent3).OrderID
    |   |       |_=
    |   |       |_Var(Join2).Extent4.OrderID
    |   |_JoinCondition
    |     |_
    |       |_Var(Join1).Extent1.ProductID
    |       |_=
    |       |_Var(Join3).Extent3.ProductID
    |_Projection
      |_NewInstance : Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]
        |_Column : 'C1'
        | |_1
        |_Column : 'ProductID'
        | |_Var(Join4).Join1.Extent1.ProductID
        |_Column : 'ProductName'
        | |_Var(Join4).Join1.Extent1.ProductName
        |_Column : 'CategoryName'
        | |_Var(Join4).Join1.Extent2.CategoryName
        |_Column : 'ShipCountry'
        | |_Var(Join4).Join3.Join2.Extent4.ShipCountry
        |_Column : 'ProductID1'
          |_Var(Join4).Join3.Extent3.ProductID
```

 <span data-ttu-id="2ca35-106">Bu konuda, bu çıktı komut ağacının aşağıdaki SQL deyimlerine nasıl çevrilebileceğini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ca35-106">This topic describes how to translate this output command tree into the following SQL statements.</span></span>

```sql
SELECT
1 AS [C1],
[Extent1].[ProductID] AS [ProductID],
[Extent1].[ProductName] AS [ProductName],
[Extent2].[CategoryName] AS [CategoryName],
[Join3].[ShipCountry] AS [ShipCountry],
[Join3].[ProductID] AS [ProductID1]
FROM   [dbo].[Products] AS [Extent1]
LEFT OUTER JOIN [dbo].[Categories] AS [Extent2] ON [Extent1].[CategoryID] = [Extent2].[CategoryID]
INNER JOIN
(SELECT [Extent3].[OrderID] AS [OrderID1], [Extent3].[ProductID] AS [ProductID], [Extent3].[UnitPrice] AS [UnitPrice], [Extent3].[Quantity] AS [Quantity], [Extent3].[Discount] AS [Discount], [Join2].[OrderID2], [Join2].[CustomerID], [Join2].[EmployeeID], [Join2].[OrderDate], [Join2].[RequiredDate], [Join2].[ShippedDate], [Join2].[Freight], [Join2].[ShipName], [Join2].[ShipAddress], [Join2].[ShipCity], [Join2].[ShipRegion], [Join2].[ShipPostalCode], [Join2].[ShipCountry], [Join2].[OrderID3], [Join2].[CustomsDescription], [Join2].[ExciseTax]
FROM  [dbo].[OrderDetails] AS [Extent3]
LEFT OUTER JOIN
      (SELECT [Extent4].[OrderID] AS [OrderID2], [Extent4].[CustomerID] AS [CustomerID], [Extent4].[EmployeeID] AS [EmployeeID], [Extent4].[OrderDate] AS [OrderDate], [Extent4].[RequiredDate] AS [RequiredDate], [Extent4].[ShippedDate] AS [ShippedDate], [Extent4].[Freight] AS [Freight], [Extent4].[ShipName] AS [ShipName], [Extent4].[ShipAddress] AS [ShipAddress], [Extent4].[ShipCity] AS [ShipCity], [Extent4].[ShipRegion] AS [ShipRegion], [Extent4].[ShipPostalCode] AS [ShipPostalCode], [Extent4].[ShipCountry] AS [ShipCountry], [Extent5].[OrderID] AS [OrderID3], [Extent5].[CustomsDescription] AS [CustomsDescription], [Extent5].[ExciseTax] AS [ExciseTax]
FROM  [dbo].[Orders] AS [Extent4]
LEFT OUTER JOIN [dbo].[InternationalOrders] AS [Extent5] ON [Extent4].[OrderID] = [Extent5].[OrderID]
      ) AS [Join2] ON [Extent3].[OrderID] = [Join2].[OrderID2]
   ) AS [Join3] ON [Extent1].[ProductID] = [Join3].[ProductID]
```

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="2ca35-107">SQL oluşturma 'nın ilk aşaması: Ifade ağacını ziyaret etme</span><span class="sxs-lookup"><span data-stu-id="2ca35-107">First Phase of SQL Generation: Visiting the Expression Tree</span></span>

<span data-ttu-id="2ca35-108">Aşağıdaki şekilde, ziyaretçinin başlangıçtaki boş durumu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-108">The following figure illustrates the initial empty state of the visitor.</span></span>  <span data-ttu-id="2ca35-109">Bu konuda, yalnızca izlenecek yol açıklamasında ilgili özellikler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-109">Throughout this topic, only the properties relevant to the walkthrough explanation are shown.</span></span>

<span data-ttu-id="2ca35-110">![Diyagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span><span class="sxs-lookup"><span data-stu-id="2ca35-110">![Diagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span></span>

<span data-ttu-id="2ca35-111">Proje düğümü ziyaret edildiğinde, VisitInputExpression kendi girdisi üzerinden çağrılır (Join4), bu, Join4 'ın VisitJoinExpression yöntemi tarafından nasıl ziyaret edildiğini tetikler.</span><span class="sxs-lookup"><span data-stu-id="2ca35-111">When the Project  node is visited, VisitInputExpression is called over its input (Join4), which triggers the visit of Join4 by the method VisitJoinExpression.</span></span> <span data-ttu-id="2ca35-112">Bu en üstteki bir JOIN olduğundan, ıparentajoın yanlış döndürür ve SELECT deyimin yığınına yeni bir Sqlselectdeyimin (SelectStatement0) oluşturulup gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-112">Because this is a topmost join, IsParentAJoin returns false and a new SqlSelectStatement (SelectStatement0) is created and pushed on the SELECT statement stack.</span></span> <span data-ttu-id="2ca35-113">Ayrıca, sembol tablosuna yeni bir kapsam (scope0) girilir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-113">Also, a new scope (scope0) is entered in the symbol table.</span></span> <span data-ttu-id="2ca35-114">Birleşimin ilk (sol) girişi ziyaret edildiğinde, ıparentajoın yığınına ' true ' gönderildi.</span><span class="sxs-lookup"><span data-stu-id="2ca35-114">Before the first (left) input of the join is visited, 'true' is pushed on the IsParentAJoin stack.</span></span> <span data-ttu-id="2ca35-115">Join4 'in sol girişi olan Join1 'den önce, ziyaretçi durumu, sonraki şekilde gösterildiği gibidir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-115">Right before Join1, which is the left input of Join4, is visited, the state of the visitor is as shown in the next figure.</span></span>

<span data-ttu-id="2ca35-116">![Diyagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44EA-8e74-c5001d5d5d79")</span><span class="sxs-lookup"><span data-stu-id="2ca35-116">![Diagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span></span>

<span data-ttu-id="2ca35-117">Join4 üzerinden bir JOIN yöntemi çağrıldığında, ısparentajoın değeri true 'dur, bu nedenle geçerli SELECT ifadesini yeniden kullanır SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="2ca35-117">When the join visit method is invoked over Join4, IsParentAJoin is true, thus it reuses the current select statement SelectStatement0.</span></span> <span data-ttu-id="2ca35-118">Yeni bir kapsam girilmiştir (kapsam1).</span><span class="sxs-lookup"><span data-stu-id="2ca35-118">A new scope is entered (scope1).</span></span> <span data-ttu-id="2ca35-119">Sol alt öğesini ziyaret etmeden önce, Extent1, Isparentajoın yığınına başka bir doğru gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-119">Before visiting its left child, Extent1, another true is pushed on the IsParentAJoin stack.</span></span>

<span data-ttu-id="2ca35-120">Extent1 ziyaret edildiğinde, ısparentajoın doğru döndürdüğünden, "[dbo]" içeren bir SqlBuilder döndürür. [Ürünler] ".</span><span class="sxs-lookup"><span data-stu-id="2ca35-120">When Extent1 is visited, because IsParentAJoin returns true, it returns a SqlBuilder containing "[dbo].[Products]".</span></span> <span data-ttu-id="2ca35-121">Denetim, Join4 ziyaret eden yönteme geri döner.</span><span class="sxs-lookup"><span data-stu-id="2ca35-121">The control returns to the method visiting Join4.</span></span> <span data-ttu-id="2ca35-122">Bir giriş Isparentajoın 'ten alınır ve ProcessJoinInputResult çağrılır ve bu, ziyaret Extent1 sonucunu SelectStatement0 From yan tümcesine ekler.</span><span class="sxs-lookup"><span data-stu-id="2ca35-122">An entry is popped from IsParentAJoin, and ProcessJoinInputResult is called, which appends the result of visiting Extent1 to the From clause of SelectStatement0.</span></span> <span data-ttu-id="2ca35-123">"Extent1" giriş bağlama adı için symbol_Extent1, "" adlı yeni bir sembol oluşturulur, SelectStatement0 'in FromExtents öğesine eklenir ve ayrıca "as" ve symbol_Extent1 from yan tümcesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-123">A new from symbol, symbol_Extent1, for the input binding name "Extent1" is created, added to the FromExtents of SelectStatement0, and also "As" and  symbol_Extent1 are appended to the from clause.</span></span> <span data-ttu-id="2ca35-124">"Extent1" için AllExtentNames öğesine 0 değeri ile yeni bir giriş eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-124">A new entry is added to AllExtentNames for "Extent1" with the value of 0.</span></span> <span data-ttu-id="2ca35-125">"Extent1" öğesini symbol symbol_Extent1 ile ilişkilendirmek için sembol tablosundaki geçerli kapsama yeni bir giriş eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-125">A new entry is added to the current scope in the symbol table to associate "Extent1" with its symbol symbol_Extent1.</span></span> <span data-ttu-id="2ca35-126">Symbol_Extent1, Sqlselectdeyimin Alljoinpackages öğesine de eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-126">Symbol_Extent1 is also added to the AllJoinExtents of the SqlSelectStatement.</span></span>

<span data-ttu-id="2ca35-127">Join1 öğesinin doğru girişinden önce, SelectStatement0 From yan tümcesine "LEFT OUTER JOIN" eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-127">Before the right input of Join1 is visited, "LEFT OUTER JOIN" is added to the From clause of SelectStatement0.</span></span> <span data-ttu-id="2ca35-128">Doğru giriş bir tarama ifadesi olduğundan, ısparentajoın yığınına doğru yeniden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-128">Because the right input is a Scan expression, true is again pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="2ca35-129">Sonraki şekilde gösterildiği gibi doğru girişi ziyaret etmeden önce durum.</span><span class="sxs-lookup"><span data-stu-id="2ca35-129">The state before visiting the right input as shown in the next figure.</span></span>

<span data-ttu-id="2ca35-130">![Diyagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-B209-e16166304fdc")</span><span class="sxs-lookup"><span data-stu-id="2ca35-130">![Diagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span></span>

<span data-ttu-id="2ca35-131">Doğru giriş, sol girişle aynı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-131">The right input is processed in the same way as the left input.</span></span> <span data-ttu-id="2ca35-132">Doğru girişi ziyaret ettikten sonra durum, sonraki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-132">The state after visiting the right input is shown in the next figure.</span></span>

<span data-ttu-id="2ca35-133">![Diyagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span><span class="sxs-lookup"><span data-stu-id="2ca35-133">![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span></span>

<span data-ttu-id="2ca35-134">Next "false", ıparentajoın yığınına ve JOIN koşulu var (Extent1) üzerinden gönderilir. CategoryID = = var (Extent2). CategoryID işlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-134">Next "false" is pushed on the IsParentAJoin stack and the join condition Var(Extent1).CategoryID == Var(Extent2).CategoryID is processed.</span></span> <span data-ttu-id="2ca35-135">Sembol tablosunda bir arama yapıldıktan sonra var \<(Extent1), symbol_Extent1 > olarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-135">Var(Extent1) is resolved to \<symbol_Extent1> after a look up in the symbol table.</span></span> <span data-ttu-id="2ca35-136">Örnek, var olan (Extent1) işleminin bir sonucu olarak basit bir simgeye çözümlendiğini. CategoryID, symbol1 > olan \<bir SqlBuilder. " CategoryID "döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2ca35-136">Because the instance is resolved to a simple Symbol, as a result of processing Var(Extent1).CategoryID, a SqlBuilder with \<symbol1>."CategoryID" is returned.</span></span> <span data-ttu-id="2ca35-137">Benzer şekilde, karşılaştırmanın diğer tarafı işlenir ve JOIN koşulunu ziyaret eden sonuç SelectStatement1 FROM yan tümcesine eklenir ve "false" değeri Isparentajoın yığınından alınır.</span><span class="sxs-lookup"><span data-stu-id="2ca35-137">Similarly the other side of the comparison is processed, and the result of visiting the join condition is appended to the FROM clause of SelectStatement1 and the value "false" is popped from the IsParentAJoin stack.</span></span>

<span data-ttu-id="2ca35-138">Bununla birlikte, Join1 tamamen işlenir ve bir kapsam sembol tablosundan alınır.</span><span class="sxs-lookup"><span data-stu-id="2ca35-138">With this, Join1 has completely been processed, and a scope is popped from the symbol table.</span></span>

<span data-ttu-id="2ca35-139">Denetim, Join1 'in üst öğesi olan Join4 işleme döner.</span><span class="sxs-lookup"><span data-stu-id="2ca35-139">Control returns to processing Join4, the parent of Join1.</span></span> <span data-ttu-id="2ca35-140">Alt öğe SELECT ifadesini yeniden kullandığından, Join1 kapsamları tek bir JOIN simgesiyle \<joinSymbol_Join1 > ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-140">Because the child reused the Select statement, the Join1 extents are replaced with a single Join symbol \<joinSymbol_Join1>.</span></span> <span data-ttu-id="2ca35-141">Ayrıca, Join1 ile \<joinSymbol_Join1 > ilişkilendirmek için sembol tablosuna yeni bir giriş eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-141">Also a new entry is added to the symbol table to associate Join1 with \<joinSymbol_Join1>.</span></span>

<span data-ttu-id="2ca35-142">İşlenecek sonraki düğüm, Join3 'in ikinci alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-142">The next node to be processed is Join3, the second child of Join4.</span></span> <span data-ttu-id="2ca35-143">Doğru bir alt öğe olduğundan, ısparentajoın yığınına "false" gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-143">As it is a right child, "false" is pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="2ca35-144">Bu noktadaki ziyaretçi durumu bir sonraki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-144">The state of the visitor at this point is illustrated in the next figure.</span></span>

<span data-ttu-id="2ca35-145">![Diyagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span><span class="sxs-lookup"><span data-stu-id="2ca35-145">![Diagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span></span>

<span data-ttu-id="2ca35-146">Join3 için Isparentajoın yanlış döndürür ve yeni bir Sqlselectdeyimin (SelectStatement1) başlaması ve yığın üzerine itilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-146">For Join3, IsParentAJoin returns false and needs to start a new SqlSelectStatement (SelectStatement1) and push it on the stack.</span></span> <span data-ttu-id="2ca35-147">İşleme önceki birleşimlerle yaptığı için devam eder, yığına yeni bir kapsam gönderilir ve alt öğeler işlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-147">Processing continues as it did with the previous the previous joins, a new scope is pushed on the stack and the children are processed.</span></span> <span data-ttu-id="2ca35-148">Sol alt öğe bir kapsam (Extent3) ve sağ alt öğe de yeni bir Sqlselectdeyimin başlaması gereken bir birleşimdir (Join2): SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="2ca35-148">The left child is an Extent (Extent3) and the right child is a join (Join2) which also needs to start a new SqlSelectStatement: SelectStatement2.</span></span> <span data-ttu-id="2ca35-149">Join2 üzerindeki alt öğeler de modellerdir ve SelectStatement2 içinde toplanır.</span><span class="sxs-lookup"><span data-stu-id="2ca35-149">The children on Join2 are Extents as well and are aggregated into SelectStatement2.</span></span>

<span data-ttu-id="2ca35-150">Join2 sonrasında ziyaretçi durumu, ancak işlem sonrası (ProcessJoinInputResult) yapıldıktan sonra bir sonraki şekilde gösterilir:</span><span class="sxs-lookup"><span data-stu-id="2ca35-150">The state of the visitor right after Join2 is visited, but before its post-processing (ProcessJoinInputResult) is done is shown in the next figure:</span></span>

<span data-ttu-id="2ca35-151">![Diyagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8B09-4c99-b411-40af239c3c4d")</span><span class="sxs-lookup"><span data-stu-id="2ca35-151">![Diagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span></span>

<span data-ttu-id="2ca35-152">Önceki şekilde SelectStatement2, yığın dışına ayrıldığından, ancak henüz üst öğe tarafından işlenmediği için serbest bir kayan olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-152">In the previous figure, SelectStatement2 is shown as free floating because it was popped out of the stack, but not yet post processed by the parent.</span></span> <span data-ttu-id="2ca35-153">Bunun üst öğenin bölümüne eklenmesi gerekir, ancak SELECT yan tümcesi olmadan tam bir SQL deyimi değildir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-153">It needs to be added to the FROM part of the parent, but it is not a complete SQL statement without a SELECT clause.</span></span> <span data-ttu-id="2ca35-154">Bu nedenle, bu noktada varsayılan sütunlar (girişleri tarafından üretilen tüm sütunlar), select listesine AddDefaultColumns yöntemine göre eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-154">So, at this point, the default columns (all the columns produced by its inputs) are added to the select list by the method AddDefaultColumns.</span></span> <span data-ttu-id="2ca35-155">AddDefaultColumns, FromExtents içindeki sembolleri yineler ve her sembol için kapsamda getirilen tüm sütunları ekler.</span><span class="sxs-lookup"><span data-stu-id="2ca35-155">AddDefaultColumns iterates over the symbols in FromExtents and for each symbol adds all the columns brought in scope.</span></span> <span data-ttu-id="2ca35-156">Basit bir sembol için, eklenecek tüm özellikleri almak için sembol türüne bakar.</span><span class="sxs-lookup"><span data-stu-id="2ca35-156">For a simple symbol, it looks at the symbol type to retrieve all its properties to be added.</span></span> <span data-ttu-id="2ca35-157">Ayrıca, AllColumnNames sözlüğünü sütun adlarıyla doldurur.</span><span class="sxs-lookup"><span data-stu-id="2ca35-157">It also populates the AllColumnNames dictionary with the column names.</span></span> <span data-ttu-id="2ca35-158">Tamamlanan SelectStatement2, SelectStatement1 FROM yan tümcesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-158">The completed SelectStatement2 is appended to the FROM clause of SelectStatement1.</span></span>

<span data-ttu-id="2ca35-159">Daha sonra, Join2 temsil etmek için yeni bir JOIN simgesi oluşturulur, iç içe bir JOIN olarak işaretlenir ve SelectStatement1 'in Alljoinpackages öğesine eklenir ve sembol tablosuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-159">Next, a new join symbol is created to represent Join2, it is marked as a nested join and added to the AllJoinExtents of SelectStatement1 and added to the symbol table.</span></span>  <span data-ttu-id="2ca35-160">Şimdi Join3, var (Extent3) öğesinin JOIN koşulu. OrderID = var (Join2). Extent4. OrderID, işlenmeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-160">Now the join condition of Join3, Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID, needs to be processed.</span></span> <span data-ttu-id="2ca35-161">Sol taraftaki işlemin işlenmesi Join1 JOIN koşuluna benzerdir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-161">Processing of the left hand side is similar to the join condition of Join1.</span></span> <span data-ttu-id="2ca35-162">Bununla birlikte, sağ ve yan "var (Join2) işlemi. Extent4. OrderID, JOIN düzleştirme gerektirdiğinden farklı.</span><span class="sxs-lookup"><span data-stu-id="2ca35-162">However, the processing of the right and side "Var(Join2).Extent4.OrderID" is different because join flattening is required.</span></span>

<span data-ttu-id="2ca35-163">Sonraki şekilde DbPropertyExpression "var (Join2) öncesindeki ziyaretçinin durumu gösterilmektedir. Extent4. OrderID "işlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-163">The next figure shows the state of the visitor right before the DbPropertyExpression "Var(Join2).Extent4.OrderID" is processed.</span></span>

<span data-ttu-id="2ca35-164">"Var (Join2) öğesini düşünün. Extent4. OrderID "ziyaret edilir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-164">Consider how "Var(Join2).Extent4.OrderID" is visited.</span></span> <span data-ttu-id="2ca35-165">Birincisi, örnek özelliği "var (Join2). Extent4 ", başka bir DbPropertyExpression olan ve önce" var (Join2) "örneğini ziyaret eden bir kez ziyaret edildi.</span><span class="sxs-lookup"><span data-stu-id="2ca35-165">First, the instance property "Var(Join2).Extent4" is visited, which is another DbPropertyExpression and first visits its instance "Var(Join2)".</span></span> <span data-ttu-id="2ca35-166">Sembol tablosundaki en üstteki kapsamda, "Join2", joinSymbol_join2 > olarak \<çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-166">In the top most scope in the symbol table, "Join2" resolves to \<joinSymbol_join2>.</span></span> <span data-ttu-id="2ca35-167">DbPropertyExpression işleme "var (Join2) için ziyaret yöntemi içinde. Extent4 "örnek ziyaret edildiğinde ve düzleştirme gerektiğinde bir JOIN sembolünün döndürülmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2ca35-167">In the visit method for DbPropertyExpression processing "Var(Join2).Extent4" notice that a join symbol was returned when visiting the instance and flattening is required.</span></span>

<span data-ttu-id="2ca35-168">İç içe bir JOIN olduğundan, JOIN sembolünün NameToExtent sözlüğünde "Extent4" özelliğini arar, bunu \<symbol_Extent4 > çözün ve yeni bir SymbolPair döndürür (\<joinSymbol_join2 >, \<symbol_Extent4 >).</span><span class="sxs-lookup"><span data-stu-id="2ca35-168">Since it is a nested join, we look up the property "Extent4" in the NameToExtent dictionary of the join symbol, resolve it to \<symbol_Extent4> and return a new SymbolPair(\<joinSymbol_join2>, \<symbol_Extent4>).</span></span> <span data-ttu-id="2ca35-169">"Var (Join2) örneğinin işlenmesinden bir sembol çifti döndürüldüğünden. Extent4. OrderID "," OrderID "özelliği, temsil ettiği kapsamın sütunlarının bir listesini içeren, bu\<sembol çiftinin (symbol_Extent4 >) ColumnPart öğesinden çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-169">Since a symbol pair is returned from the processing of the instance of "Var(Join2).Extent4.OrderID",  the property "OrderID" is resolved from the ColumnPart of that symbol pair (\<symbol_Extent4>), which has a list of the columns of the extent it represents.</span></span> <span data-ttu-id="2ca35-170">So, "var (Join2). Extent4. OrderID, { \<joinSymbol_Join2 >, ".", \<symbol_OrderID >} olarak çözümlendi.</span><span class="sxs-lookup"><span data-stu-id="2ca35-170">So, "Var(Join2).Extent4.OrderID" is resolved to { \<joinSymbol_Join2>, ".", \<symbol_OrderID>}.</span></span>

<span data-ttu-id="2ca35-171">Join4 'in JOIN koşulu benzer şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-171">The join condition of Join4 is similarly processed.</span></span> <span data-ttu-id="2ca35-172">Denetim, en üstteki proje işlenen VisitInputExpression yöntemine döner.</span><span class="sxs-lookup"><span data-stu-id="2ca35-172">The control returns to the VisitInputExpression method that processed the top most project.</span></span> <span data-ttu-id="2ca35-173">Döndürülen SelectStatement0 'in FromExtents ' ye bakarak, giriş bir JOIN olarak tanımlanır ve özgün uzantıları kaldırır ve yalnızca JOIN simgesiyle yeni bir uzantı ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-173">Looking at the FromExtents of the returned SelectStatement0, the input is identified as a join, and removes the original extents and replaces them with a new extent with just the Join symbol.</span></span> <span data-ttu-id="2ca35-174">Sembol tablosu da güncellenir ve projenin projeksiyon bölümü işlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-174">The symbol table is also updated and next the projection part of the Project is processed.</span></span> <span data-ttu-id="2ca35-175">Özelliklerin çözümlenmesi ve JOIN kapsamlarının düzleştirilmesi daha önce açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2ca35-175">The resolving of the properties and the flattening of the join extents is as described earlier.</span></span>

<span data-ttu-id="2ca35-176">![Diyagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40AE-ACCC-a10e18e28b81")</span><span class="sxs-lookup"><span data-stu-id="2ca35-176">![Diagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span></span>

<span data-ttu-id="2ca35-177">Son olarak, aşağıdaki Sqlselectdeyimin oluşturulması gerekir:</span><span class="sxs-lookup"><span data-stu-id="2ca35-177">Finally, the following SqlSelectStatement is produced:</span></span>

```
SELECT:
  "1", " AS ", "[C1]",
  <symbol_Extent1>, ".", "[ProductID]", " AS ", "[ProductID]",
  <symbol_Extent1>, ".", "[ProductName]", " AS ", "[ProductName]",
  <symbol_Extent2>, ".", "[CategoryName]", " AS ", "[CategoryName]",
  <joinSymbol_Join3>, ".", <symbol_ShipCountry>, " AS ", "[ShipCountry]",
  <joinSymbol_Join3>, ".", <symbol_ProductID>, " AS ", "[ProductID1]"
FROM: "[dbo].[Products]", " AS ", <symbol_Extent1>,
        "LEFT OUTER JOIN ""[dbo].[Categories]", " AS ", <symbol_Extent2>, " ON ", <symbol_Extent1>, ".", "[CategoryID]", " = ", <symbol_Extent2>, ".", "[CategoryID]",
        "INNER JOIN ",
        " (", SELECT:
           <symbol_Extent3>, ".", "[OrderID]", " AS ", <symbol_OrderID>, ",
              <symbol_Extent3>, ".", "[ProductID]", " AS ", <symbol_ProductID>, ...,
         <joinSymbol_Join2>, ".", <symbol_OrderID_2>, ", ",
           <joinSymbol_Join2>, ".", <symbol_CustomerID>, ....,
        <joinSymbol_Join2>, ".", <symbol_OrderID_3>,
<joinSymbol_Join2>, ".", <symbol_CustomsDescription>,
<joinSymbol_Join2>, ".", <symbol_ExciseTax>
FROM: "[dbo].[OrderDetails]", " AS ", <symbol_Extent3>,
"LEFT OUTER JOIN ",
" (", SELECT:
<symbol_Extent4>, ".", "[OrderID]", " AS ", <symbol_OrderID_2>,
<symbol_Extent4>, ".", "[CustomerID]", " AS ", <symbol_CustomerID>, ...
<symbol_Extent5>, ".", "[OrderID]", " AS ", <symbol_OrderID_3>,
<symbol_Extent5>, ".", "[CustomsDescription]", " AS ", <symbol_CustomsDescription>,
<symbol_Extent5>, ".", "[ExciseTax]", " AS ", <symbol_ExciseTax>
FROM: "[dbo].[Orders]", " AS ", <symbol_Extent4>,
"LEFT OUTER JOIN ", , "[dbo].[InternationalOrders]", " AS ", <symbol_Extent5>,
" ON ", <symbol_Extent4>, ".", "[OrderID]", " = ", , <symbol_Extent5>, ".", "[OrderID]"
" )", " AS ", <joinSymbol_Join2>, " ON ", , , <symbol_Extent3>, ".", "[OrderID]", " = ", , <joinSymbol_Join2>, ".", <symbol_OrderID_2>
" )", " AS ", <joinSymbol_Join3>, " ON ", , , <symbol_Extent1>, ".", "[ProductID]", " = ", , <joinSymbol_Join3>, ".", <symbol_ProductID>
```

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="2ca35-178">SQL üretimi ikinci aşaması: String komutunu oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ca35-178">Second Phase of SQL Generation: Generating the String Command</span></span>

<span data-ttu-id="2ca35-179">İkinci aşama semboller için gerçek adlar üretir ve yalnızca "OrderID" adlı sütunları temsil eden simgelere odaklanıyoruz, bu durumda bir çakışma çözümlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-179">The second phase produces actual names for the symbols, and we only focus on the symbols representing columns named "OrderID", as in this case a conflict needs to be resolved.</span></span> <span data-ttu-id="2ca35-180">Bunlar Sqlselectdeyimde vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="2ca35-180">These are highlighted in the SqlSelectStatement.</span></span> <span data-ttu-id="2ca35-181">Şekilde kullanılan son eklerin yalnızca bunların farklı örnekler olduğunu vurgulayıp, bu aşamada son adlarının (yani özgün adların farklı biçimde) henüz atanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2ca35-181">Note that the suffixes used in the figure are only to emphasize that these are different instances, not to represent any new names, as at this stage their final names (possibly different form the original names) have not been assigned yet.</span></span>

<span data-ttu-id="2ca35-182">Yeniden adlandırılması \<gereken ilk sembol symbol_OrderID >.</span><span class="sxs-lookup"><span data-stu-id="2ca35-182">The first symbol found that needs to be renamed is \<symbol_OrderID>.</span></span> <span data-ttu-id="2ca35-183">Yeni adı "OrderID1" olarak atanır, 1 "OrderID" için son kullanılan sonek olarak işaretlenir ve sembol yeniden adlandırmadan önce işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-183">Its new name is assigned as "OrderID1", 1 is marked as the last used suffix for "OrderID" and the symbol is marked as not needing renaming.</span></span> <span data-ttu-id="2ca35-184">Sonra, \<symbol_OrderID_2 > ilk kullanımı bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ca35-184">Next, the first usage of \<symbol_OrderID_2> is found.</span></span> <span data-ttu-id="2ca35-185">Bu, bir sonraki kullanılabilir son eki ("OrderID2") kullanacak şekilde yeniden adlandırılamayan olarak işaretlenir ve daha sonra bir dahaki sefer kullanıldığında yeniden adlandırılamayan olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="2ca35-185">It is renamed to use the next available suffix ("OrderID2") and again marked as not needing renaming, so that next time it is used it does not get renamed.</span></span> <span data-ttu-id="2ca35-186">Bu, symbol_OrderID_3 > \<için yapılır.</span><span class="sxs-lookup"><span data-stu-id="2ca35-186">This is done for \<symbol_OrderID_3> too.</span></span>

<span data-ttu-id="2ca35-187">İkinci aşamanın sonunda, son SQL açıklaması oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2ca35-187">At the end of the second phase, the final SQL statement is generated.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ca35-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ca35-188">See also</span></span>

- [<span data-ttu-id="2ca35-189">Örnek Sağlayıcısında SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ca35-189">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)
