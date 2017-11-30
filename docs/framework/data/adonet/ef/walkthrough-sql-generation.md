---
title: "İzlenecek yol: SQL oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c19c459bf3b62b7e1d7e2917e09717c246e728c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-sql-generation"></a><span data-ttu-id="9dac8-102">İzlenecek yol: SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dac8-102">Walkthrough: SQL Generation</span></span>
<span data-ttu-id="9dac8-103">Bu konuda SQL üretimi oluşuyor nasıl gösterilmektedir [örnek sağlayıcı](http://go.microsoft.com/fwlink/?LinkId=180616).</span><span class="sxs-lookup"><span data-stu-id="9dac8-103">This topic illustrates how SQL generation occurs in the [Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616).</span></span> <span data-ttu-id="9dac8-104">Aşağıdaki varlık SQL sorgusunu örnek sağlayıcı ile birlikte modeli kullanır:</span><span class="sxs-lookup"><span data-stu-id="9dac8-104">The following Entity SQL query uses the model that is included with the sample provider:</span></span>  
  
```  
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId  
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName  
        FROM NorthwindEntities.Products AS P) as j1  
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry  
            FROM NorthwindEntities.OrderDetails AS OD) as j2  
            ON j1.ProductId == j2.ProductId   
```  
  
 <span data-ttu-id="9dac8-105">Sorgu sağlayıcısına geçirilen aşağıdaki çıkış komut ağacı üretir:</span><span class="sxs-lookup"><span data-stu-id="9dac8-105">The query produces the following output command tree that is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="9dac8-106">Bu konu, aşağıdaki SQL deyimleri bu çıkış komut ağacı Çevir açıklar.</span><span class="sxs-lookup"><span data-stu-id="9dac8-106">This topic describes how to translate this output command tree into the following SQL statements.</span></span>  
  
```  
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
  
## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="9dac8-107">Birinci aşama SQL nesil: ifade ağacına ziyaret edin</span><span class="sxs-lookup"><span data-stu-id="9dac8-107">First Phase of SQL Generation: Visiting the Expression Tree</span></span>  
 <span data-ttu-id="9dac8-108">Aşağıdaki şekilde ziyaretçi ilk boş durumunda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-108">The following figure illustrates the initial empty state of the visitor.</span></span>  <span data-ttu-id="9dac8-109">Bu konu boyunca yalnızca izlenecek açıklama ilgili özellikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-109">Throughout this topic, only the properties relevant to the walkthrough explanation are shown.</span></span>  
  
 <span data-ttu-id="9dac8-110">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span><span class="sxs-lookup"><span data-stu-id="9dac8-110">![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span></span>  
  
 <span data-ttu-id="9dac8-111">Proje düğümüne sitesini ziyaret ettiğinizde VisitInputExpression hangi Join4 ziyaret VisitJoinExpression yöntemi tarafından tetikler kendi giriş (Join4) üzerinden adı verilir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-111">When the Project  node is visited, VisitInputExpression is called over its input (Join4), which triggers the visit of Join4 by the method VisitJoinExpression.</span></span> <span data-ttu-id="9dac8-112">En üstteki birleştirme çünkü IsParentAJoin false değerini döndürür ve yeni SqlSelectStatement (SelectStatement0) oluşturulur ve SELECT deyimi yığına.</span><span class="sxs-lookup"><span data-stu-id="9dac8-112">Because this is a topmost join, IsParentAJoin returns false and a new SqlSelectStatement (SelectStatement0) is created and pushed on the SELECT statement stack.</span></span> <span data-ttu-id="9dac8-113">Ayrıca, yeni bir kapsam (scope0) sembol tablosuna girilir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-113">Also, a new scope (scope0) is entered in the symbol table.</span></span> <span data-ttu-id="9dac8-114">İlk (soldaki) giriş katılma ziyaret edilen önce 'true' IsParentAJoin yığında gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-114">Before the first (left) input of the join is visited, 'true' is pushed on the IsParentAJoin stack.</span></span> <span data-ttu-id="9dac8-115">Sağ Join4 sol girişi olan Join1 ziyaret edilen önce ziyaretçi sonraki gösterildiği gibi bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9dac8-115">Right before Join1, which is the left input of Join4, is visited, the state of the visitor is as shown in the next figure.</span></span>  
  
 <span data-ttu-id="9dac8-116">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span><span class="sxs-lookup"><span data-stu-id="9dac8-116">![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span></span>  
  
 <span data-ttu-id="9dac8-117">Birleşim ziyaret ettiğinizde yöntemi Join4 çağrılır IsParentAJoin true, böylece geçerli select deyimi SelectStatement0 yeniden kullanır.</span><span class="sxs-lookup"><span data-stu-id="9dac8-117">When the join visit method is invoked over Join4, IsParentAJoin is true, thus it reuses the current select statement SelectStatement0.</span></span> <span data-ttu-id="9dac8-118">Yeni bir kapsam girilen (kapsam1) olur.</span><span class="sxs-lookup"><span data-stu-id="9dac8-118">A new scope is entered (scope1).</span></span> <span data-ttu-id="9dac8-119">Sol alt, Extent1, ziyaret önce başka bir true IsParentAJoin yığında gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-119">Before visiting its left child, Extent1, another true is pushed on the IsParentAJoin stack.</span></span>  
  
 <span data-ttu-id="9dac8-120">IsParentAJoin true döndürdüğünden Extent1 ziyaret edildiğinde "[dbo]. içeren bir SqlBuilder döndürür [Ürünler] ".</span><span class="sxs-lookup"><span data-stu-id="9dac8-120">When Extent1 is visited, because IsParentAJoin returns true, it returns a SqlBuilder containing "[dbo].[Products]".</span></span> <span data-ttu-id="9dac8-121">Denetim Join4 ziyaret yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dac8-121">The control returns to the method visiting Join4.</span></span> <span data-ttu-id="9dac8-122">Bir giriş IsParentAJoin Sil'i ve hangi Extent1 SelectStatement0 From yan tümcesi ziyaret sonucunu ekler ProcessJoinInputResult çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9dac8-122">An entry is popped from IsParentAJoin, and ProcessJoinInputResult is called, which appends the result of visiting Extent1 to the From clause of SelectStatement0.</span></span> <span data-ttu-id="9dac8-123">Giriş bağlaması adı "Extent1" oluşturulan için yeni bir sembol, symbol_Extent1, gelen SelectStatement0 ve "As" FromExtents eklenir ve symbol_Extent1 için eklenen from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="9dac8-123">A new from symbol, symbol_Extent1, for the input binding name "Extent1" is created, added to the FromExtents of SelectStatement0, and also "As" and  symbol_Extent1 are appended to the from clause.</span></span> <span data-ttu-id="9dac8-124">Yeni bir giriş AllExtentNames için 0 değerini "Extent1 için" eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-124">A new entry is added to AllExtentNames for "Extent1" with the value of 0.</span></span> <span data-ttu-id="9dac8-125">Yeni bir giriş "Extent1" kendi simge symbol_Extent1 ile ilişkilendirmek için Sembol tablosunu geçerli kapsamda eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-125">A new entry is added to the current scope in the symbol table to associate "Extent1" with its symbol symbol_Extent1.</span></span> <span data-ttu-id="9dac8-126">Symbol_Extent1 SqlSelectStatement AllJoinExtents için de eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-126">Symbol_Extent1 is also added to the AllJoinExtents of the SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="9dac8-127">Join1 sağ girişi ziyaret edilen önce "LEFT OUTER JOIN" SelectStatement0 From yan tümcesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-127">Before the right input of Join1 is visited, "LEFT OUTER JOIN" is added to the From clause of SelectStatement0.</span></span> <span data-ttu-id="9dac8-128">Sağ giriş tarama ifade olduğundan true yeniden IsParentAJoin yığına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-128">Because the right input is a Scan expression, true is again pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="9dac8-129">Sonraki şekilde gösterildiği gibi sağ giriş ziyaret önce durumu.</span><span class="sxs-lookup"><span data-stu-id="9dac8-129">The state before visiting the right input as shown in the next figure.</span></span>  
  
 <span data-ttu-id="9dac8-130">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span><span class="sxs-lookup"><span data-stu-id="9dac8-130">![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span></span>  
  
 <span data-ttu-id="9dac8-131">Sağ giriş sol giriş olarak aynı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-131">The right input is processed in the same way as the left input.</span></span> <span data-ttu-id="9dac8-132">Sağ giriş ziyaret sonra durumu sonraki gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-132">The state after visiting the right input is shown in the next figure.</span></span>  
  
 <span data-ttu-id="9dac8-133">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span><span class="sxs-lookup"><span data-stu-id="9dac8-133">![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span></span>  
  
 <span data-ttu-id="9dac8-134">Sonraki "false" IsParentAJoin yığını ve birleşim koşuluna Var(Extent1) gönderilir. Adlı kullanıcı, Categoryıd'si Var(Extent2) ==. Adlı kullanıcı, Categoryıd'si işlenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-134">Next "false" is pushed on the IsParentAJoin stack and the join condition Var(Extent1).CategoryID == Var(Extent2).CategoryID is processed.</span></span> <span data-ttu-id="9dac8-135">Var(Extenent1) < symbol_Extent1 > sonra bir görünüm yukarı simgesi tabloda çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-135">Var(Extenent1) is resolved to <symbol_Extent1> after a look up in the symbol table.</span></span> <span data-ttu-id="9dac8-136">Örnek Var(Extent1) işleme sonucunda basit bir simge için çözümlenmiş olmasından dolayı. Adlı kullanıcı, Categoryıd'si, SqlBuilder ile \<symbol1 >. " Adlı kullanıcı, Categoryıd'si"döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9dac8-136">Because the instance is resolved to a simple Symbol, as a result of processing Var(Extent1).CategoryID, a SqlBuilder with \<symbol1>."CategoryID" is returned.</span></span> <span data-ttu-id="9dac8-137">Karşılaştırma diğer tarafını benzer şekilde işlenir ve birleştirme koşulunun ziyaret sonucunu FROM yan tümcesi SelectStatement1 ve "false" Sil'i IsParentAJoin yığınından değeri eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-137">Similarly the other side of the comparison is processed, and the result of visiting the join condition is appended to the FROM clause of SelectStatement1 and the value "false" is popped from the IsParentAJoin stack.</span></span>  
  
 <span data-ttu-id="9dac8-138">Bu, Join1 tamamen işlendikten ve kapsam simgesi tablosundan Sil'i.</span><span class="sxs-lookup"><span data-stu-id="9dac8-138">With this, Join1 has completely been processed, and a scope is popped from the symbol table.</span></span>  
  
 <span data-ttu-id="9dac8-139">Join4, Join1 üst işlemeyi denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dac8-139">Control returns to processing Join4, the parent of Join1.</span></span> <span data-ttu-id="9dac8-140">Alt seçme deyimi yeniden çünkü Join1 kapsam tek birleştirme simgesiyle < joinSymbol_Join1 > değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-140">Because the child reused the Select statement, the Join1 extents are replaced with a single Join symbol <joinSymbol_Join1>.</span></span> <span data-ttu-id="9dac8-141">Ayrıca yeni bir giriş Join1 < joinSymbol_Join1 > ile ilişkilendirmek için Sembol tablosuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-141">Also a new entry is added to the symbol table to associate Join1 with <joinSymbol_Join1>.</span></span>  
  
 <span data-ttu-id="9dac8-142">İşlenecek sonraki Join3, Join4 ikinci alt düğümdür.</span><span class="sxs-lookup"><span data-stu-id="9dac8-142">The next node to be processed is Join3, the second child of Join4.</span></span> <span data-ttu-id="9dac8-143">Sağ alt olduğu gibi "false" IsParentAJoin yığına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-143">As it is a right child, "false" is pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="9dac8-144">Bu noktada ziyaretçi durumunu sonraki çizimde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-144">The state of the visitor at this point is illustrated in the next figure.</span></span>  
  
 <span data-ttu-id="9dac8-145">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span><span class="sxs-lookup"><span data-stu-id="9dac8-145">![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span></span>  
  
 <span data-ttu-id="9dac8-146">Join3, IsParentAJoin false değerini döndürür ve yeni SqlSelectStatement (SelectStatement1) başlatın ve yığında itme gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="9dac8-146">For Join3, IsParentAJoin returns false and needs to start a new SqlSelectStatement (SelectStatement1) and push it on the stack.</span></span> <span data-ttu-id="9dac8-147">Önceki birleştirmeler önceki ile mi, yeni bir kapsam yığına ve alt işlenen olarak devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-147">Processing continues as it did with the previous the previous joins, a new scope is pushed on the stack and the children are processed.</span></span> <span data-ttu-id="9dac8-148">Sol alt bir uzantı (Extent3) ve sağ alt ayrıca yeni SqlSelectStatement başlatmak için gereken bir birleştirme (Join2): SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="9dac8-148">The left child is an Extent (Extent3) and the right child is a join (Join2) which also needs to start a new SqlSelectStatement: SelectStatement2.</span></span> <span data-ttu-id="9dac8-149">Alt Join2 üzerinde kapsam da olan ve SelectStatement2 toplanır.</span><span class="sxs-lookup"><span data-stu-id="9dac8-149">The children on Join2 are Extents as well and are aggregated into SelectStatement2.</span></span>  
  
 <span data-ttu-id="9dac8-150">Ziyaretçi sağ durumunu Join2 ziyaret sonra ancak sonrası işlemesi (ProcessJoinInputResult) yapılır önce sonraki gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9dac8-150">The state of the visitor right after Join2 is visited, but before its post-processing (ProcessJoinInputResult) is done is shown in the next figure:</span></span>  
  
 <span data-ttu-id="9dac8-151">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span><span class="sxs-lookup"><span data-stu-id="9dac8-151">![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span></span>  
  
 <span data-ttu-id="9dac8-152">Yığın dışında Sil'i ancak henüz post için ücretsiz kayan üst tarafından işlenen gibi önceki çizimde SelectStatement2 gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-152">In the previous figure, SelectStatement2 is shown as free floating because it was popped out of the stack, but not yet post processed by the parent.</span></span> <span data-ttu-id="9dac8-153">Üst FROM bölümüne eklenmesi gerekir, ancak bir SELECT yan tümcesi olmadan tam bir SQL deyimi değil.</span><span class="sxs-lookup"><span data-stu-id="9dac8-153">It needs to be added to the FROM part of the parent, but it is not a complete SQL statement without a SELECT clause.</span></span> <span data-ttu-id="9dac8-154">Bu nedenle, bu noktada, (girdilerinden tarafından üretilen tüm sütunlar) varsayılan sütunları seçim listesine AddDefaultColumns yöntemi tarafından eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-154">So, at this point, the default columns (all the columns produced by its inputs) are added to the select list by the method AddDefaultColumns.</span></span> <span data-ttu-id="9dac8-155">AddDefaultColumns FromExtents sembolleri üzerinden tekrarlanan ve kapsamda duruma tüm sütunları her simgesi ekler.</span><span class="sxs-lookup"><span data-stu-id="9dac8-155">AddDefaultColumns iterates over the symbols in FromExtents and for each symbol adds all the columns brought in scope.</span></span> <span data-ttu-id="9dac8-156">Basit bir simge için eklenecek tüm özelliklerini alınacak simge türü görünüyor.</span><span class="sxs-lookup"><span data-stu-id="9dac8-156">For a simple symbol, it looks at the symbol type to retrieve all its properties to be added.</span></span> <span data-ttu-id="9dac8-157">Ayrıca, AllColumnNames sözlüğü sütun adları ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="9dac8-157">It also populates the AllColumnNames dictionary with the column names.</span></span> <span data-ttu-id="9dac8-158">Tamamlanan SelectStatement2 SelectStatement1 FROM yan tümcesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-158">The completed SelectStatement2 is appended to the FROM clause of SelectStatement1.</span></span>  
  
 <span data-ttu-id="9dac8-159">Ardından, yeni bir birleşim sembol Join2 temsil etmek üzere oluşturulur, bu bir iç içe geçmiş birleştirme işaretlenmiş ve, AllJoinExtents SelectStatement1 eklenir ve sembol tablosuna eklendi.</span><span class="sxs-lookup"><span data-stu-id="9dac8-159">Next, a new join symbol is created to represent Join2, it is marked as a nested join and added to the AllJoinExtents of SelectStatement1 and added to the symbol table.</span></span>  <span data-ttu-id="9dac8-160">Şimdi birleşim koşulu Join3, Var(Extent3). OrderID Var(Join2) =. Extent4.OrderID, işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-160">Now the join condition of Join3, Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID, needs to be processed.</span></span> <span data-ttu-id="9dac8-161">Sol taraftaki işlenmesini Join1 birleşim koşulu benzer.</span><span class="sxs-lookup"><span data-stu-id="9dac8-161">Processing of the left hand side is similar to the join condition of Join1.</span></span> <span data-ttu-id="9dac8-162">Ancak, sağa ve yan "Var(Join2) işlenmesini. Birleşim düzleştirme gerekli olduğundan Extent4.OrderID"farklıdır.</span><span class="sxs-lookup"><span data-stu-id="9dac8-162">However, the processing of the right and side "Var(Join2).Extent4.OrderID" is different because join flattening is required.</span></span>  
  
 <span data-ttu-id="9dac8-163">Sonraki şekilde ziyaretçi hemen önce "Var(Join2). DbPropertyExpression durumunu gösterir. Extent4.OrderID"işlenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-163">The next figure shows the state of the visitor right before the DbPropertyExpression "Var(Join2).Extent4.OrderID" is processed.</span></span>  
  
 <span data-ttu-id="9dac8-164">Göz önünde bulundurun nasıl "Var(Join2). Extent4.OrderID"ziyaret edilen.</span><span class="sxs-lookup"><span data-stu-id="9dac8-164">Consider how "Var(Join2).Extent4.OrderID" is visited.</span></span> <span data-ttu-id="9dac8-165">İlk olarak, örnek özelliği "Var(Join2). Extent4 "ziyaret edilen başka bir DbPropertyExpression olduğu ve ilk örneğinin"Var(Join2)"ziyaret eder.</span><span class="sxs-lookup"><span data-stu-id="9dac8-165">First, the instance property "Var(Join2).Extent4" is visited, which is another DbPropertyExpression and first visits its instance "Var(Join2)".</span></span> <span data-ttu-id="9dac8-166">Üst çoğu kapsamda simgesi tablosundaki "Join2" < joinSymbol_join2 > çözümler.</span><span class="sxs-lookup"><span data-stu-id="9dac8-166">In the top most scope in the symbol table, "Join2" resolves to <joinSymbol_join2>.</span></span> <span data-ttu-id="9dac8-167">"Var(Join2). işleme DbPropertyExpression için ziyaret yöntemi Extent4 "örnek ziyaret edip düzleştirme gerekli olduğunda bir birleşim simge döndürüldü dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9dac8-167">In the visit method for DbPropertyExpression processing "Var(Join2).Extent4" notice that a join symbol was returned when visiting the instance and flattening is required.</span></span>  
  
 <span data-ttu-id="9dac8-168">İç içe geçmiş bir birleştirme olduğuna göre biz birleştirme simgenin NameToExtent sözlükte "Extent4" özelliği aramak, < symbol_Extent4 > çözümlemek ve yeni SymbolPair dönün (< joinSymbol_join2 >, < symbol_Extent4 >).</span><span class="sxs-lookup"><span data-stu-id="9dac8-168">Since it is a nested join, we look up the property "Extent4" in the NameToExtent dictionary of the join symbol, resolve it to <symbol_Extent4> and return a new SymbolPair(<joinSymbol_join2>, <symbol_Extent4>).</span></span> <span data-ttu-id="9dac8-169">Bu yana bir simge çifti "Var(Join2). örneğinin işlenmesini döndürülür Extent4.OrderID","OrderID"özelliğini temsil ettiği ölçüde sütunlarının listesini içeren bu simge çifti (< symbol_Extent4 >), ColumnPart çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-169">Since a symbol pair is returned from the processing of the instance of "Var(Join2).Extent4.OrderID",  the property "OrderID" is resolved from the ColumnPart of that symbol pair (<symbol_Extent4>), which has a list of the columns of the extent it represents.</span></span> <span data-ttu-id="9dac8-170">Bunu, "Var(Join2). Extent4.OrderID"Çözüldü {< joinSymbol_Join2 >". ", < symbol_OrderID >}.</span><span class="sxs-lookup"><span data-stu-id="9dac8-170">So, "Var(Join2).Extent4.OrderID" is resolved to { <joinSymbol_Join2>, ".", <symbol_OrderID>}.</span></span>  
  
 <span data-ttu-id="9dac8-171">Birleşim koşulu Join4 benzer şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-171">The join condition of Join4 is similarly processed.</span></span> <span data-ttu-id="9dac8-172">Denetim çoğu proje üst işlenen VisitInputExpression yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dac8-172">The control returns to the VisitInputExpression method that processed the top most project.</span></span> <span data-ttu-id="9dac8-173">Döndürülen SelectStatement0 FromExtents baktığınızda, Giriş bir birleşim tanımlanır ve özgün kapsam kaldırır ve bunları yalnızca birleştirme simgesi ile yeni bir kapsam ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-173">Looking at the FromExtents of the returned SelectStatement0, the input is identified as a join, and removes the original extents and replaces them with a new extent with just the Join symbol.</span></span> <span data-ttu-id="9dac8-174">Sembol tablosuna de güncelleştirilir ve projeksiyon projenin bir parçası sonraki işlenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-174">The symbol table is also updated and next the projection part of the Project is processed.</span></span> <span data-ttu-id="9dac8-175">Özellikleri ve birleştirme işlenmekte olan sınırlarını düzleştirme çözme, daha önce açıklandığı gibi özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-175">The resolving of the properties and the flattening of the join extents is as described earlier.</span></span>  
  
 <span data-ttu-id="9dac8-176">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span><span class="sxs-lookup"><span data-stu-id="9dac8-176">![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span></span>  
  
 <span data-ttu-id="9dac8-177">Son olarak, aşağıdaki SqlSelectStatement oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="9dac8-177">Finally, the following SqlSelectStatement is produced:</span></span>  
  
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
  
### <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="9dac8-178">SQL üretimi ikinci aşaması: dize komutu oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="9dac8-178">Second Phase of SQL Generation: Generating the String Command</span></span>  
 <span data-ttu-id="9dac8-179">İkinci aşama sembolleri gerçek adlarını oluşturur ve biz yalnızca bir çakışma çözülmesi gereken bu durumda olduğu gibi "OrderID" adlı sütun temsil eden simgeleri odaklanır.</span><span class="sxs-lookup"><span data-stu-id="9dac8-179">The second phase produces actual names for the symbols, and we only focus on the symbols representing columns named "OrderID", as in this case a conflict needs to be resolved.</span></span> <span data-ttu-id="9dac8-180">Bunlar SqlSelectStatement vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="9dac8-180">These are highlighted in the SqlSelectStatement.</span></span> <span data-ttu-id="9dac8-181">Tüm yeni adları bu gibi temsil etmiyor için farklı örnekler, bunlar yalnızca vurgulamak için şekilde kullanılan sonekleri olduğunu unutmayın. son adlarını aşama (muhtemelen farklı özgün adlarını oluşturmak) henüz atanmış değil.</span><span class="sxs-lookup"><span data-stu-id="9dac8-181">Note that the suffixes used in the figure are only to emphasize that these are different instances, not to represent any new names, as at this stage their final names (possibly different form the original names) have not been assigned yet.</span></span>  
  
 <span data-ttu-id="9dac8-182">Yeniden adlandırılacak gereken ilk simgenin bulunduğu < symbol_OrderID > değil.</span><span class="sxs-lookup"><span data-stu-id="9dac8-182">The first symbol found that needs to be renamed is <symbol_OrderID>.</span></span> <span data-ttu-id="9dac8-183">Yeni adıyla "OrderID1" atanmış, 1 son soneki "OrderID" için kullanılan ve simgenin yeniden adlandırma kalmamanız olarak işaretlenmiş olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-183">Its new name is assigned as "OrderID1", 1 is marked as the last used suffix for "OrderID" and the symbol is marked as not needing renaming.</span></span> <span data-ttu-id="9dac8-184">Ardından, < symbol_OrderID_2 > ilk kullanımını bulunur.</span><span class="sxs-lookup"><span data-stu-id="9dac8-184">Next, the first usage of <symbol_OrderID_2> is found.</span></span> <span data-ttu-id="9dac8-185">Sonraki kullanılabilir sonek ("OrderID2") kullanmak üzere yeniden adlandırılmış ve böylece kullanıldığı sonraki zaman onu yeniden adlandırılmaz yeniden yeniden adlandırma kalmamanız olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="9dac8-185">It is renamed to use the next available suffix ("OrderID2") and again marked as not needing renaming, so that next time it is used it does not get renamed.</span></span> <span data-ttu-id="9dac8-186">Bu < symbol_OrderID_3 > için çok gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9dac8-186">This is done for <symbol_OrderID_3> too.</span></span>  
  
 <span data-ttu-id="9dac8-187">İkinci aşamasının sonunda, nihai SQL deyimini oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9dac8-187">At the end of the second phase, the final SQL statement is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dac8-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9dac8-188">See Also</span></span>  
 [<span data-ttu-id="9dac8-189">Örnek Sağlayıcısı'nda SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dac8-189">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
