---
title: 'İzlenecek yol: SQL oluşturma'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: ab08b404dc60483a39e5c6ae56d82b63932c3f3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766328"
---
# <a name="walkthrough-sql-generation"></a>İzlenecek yol: SQL oluşturma
Bu konuda SQL üretimi oluşuyor nasıl gösterilmektedir [örnek sağlayıcı](http://go.microsoft.com/fwlink/?LinkId=180616). Aşağıdaki varlık SQL sorgusunu örnek sağlayıcı ile birlikte modeli kullanır:  
  
```  
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId  
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName  
        FROM NorthwindEntities.Products AS P) as j1  
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry  
            FROM NorthwindEntities.OrderDetails AS OD) as j2  
            ON j1.ProductId == j2.ProductId   
```  
  
 Sorgu sağlayıcısına geçirilen aşağıdaki çıkış komut ağacı üretir:  
  
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
  
 Bu konu, aşağıdaki SQL deyimleri bu çıkış komut ağacı Çevir açıklar.  
  
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
  
## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>Birinci aşama SQL nesil: ifade ağacına ziyaret edin  
 Aşağıdaki şekilde ziyaretçi ilk boş durumunda gösterilmektedir.  Bu konu boyunca yalnızca izlenecek açıklama ilgili özellikleri gösterilmektedir.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")  
  
 Proje düğümüne sitesini ziyaret ettiğinizde VisitInputExpression hangi Join4 ziyaret VisitJoinExpression yöntemi tarafından tetikler kendi giriş (Join4) üzerinden adı verilir. En üstteki birleştirme çünkü IsParentAJoin false değerini döndürür ve yeni SqlSelectStatement (SelectStatement0) oluşturulur ve SELECT deyimi yığına. Ayrıca, yeni bir kapsam (scope0) sembol tablosuna girilir. İlk (soldaki) giriş katılma ziyaret edilen önce 'true' IsParentAJoin yığında gönderilir. Sağ Join4 sol girişi olan Join1 ziyaret edilen önce ziyaretçi sonraki gösterildiği gibi bir durumda.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")  
  
 Birleşim ziyaret ettiğinizde yöntemi Join4 çağrılır IsParentAJoin true, böylece geçerli select deyimi SelectStatement0 yeniden kullanır. Yeni bir kapsam girilen (kapsam1) olur. Sol alt, Extent1, ziyaret önce başka bir true IsParentAJoin yığında gönderilir.  
  
 IsParentAJoin true döndürdüğünden Extent1 ziyaret edildiğinde "[dbo]. içeren bir SqlBuilder döndürür [Ürünler] ". Denetim Join4 ziyaret yöntemi döndürür. Bir giriş IsParentAJoin Sil'i ve hangi Extent1 SelectStatement0 From yan tümcesi ziyaret sonucunu ekler ProcessJoinInputResult çağrılır. Giriş bağlaması adı "Extent1" oluşturulan için yeni bir sembol, symbol_Extent1, gelen SelectStatement0 ve "As" FromExtents eklenir ve symbol_Extent1 için eklenen from yan tümcesi. Yeni bir giriş AllExtentNames için 0 değerini "Extent1 için" eklenir. Yeni bir giriş "Extent1" kendi simge symbol_Extent1 ile ilişkilendirmek için Sembol tablosunu geçerli kapsamda eklenir. Symbol_Extent1 SqlSelectStatement AllJoinExtents için de eklenir.  
  
 Join1 sağ girişi ziyaret edilen önce "LEFT OUTER JOIN" SelectStatement0 From yan tümcesi eklenir. Sağ giriş tarama ifade olduğundan true yeniden IsParentAJoin yığına gönderilir. Sonraki şekilde gösterildiği gibi sağ giriş ziyaret önce durumu.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")  
  
 Sağ giriş sol giriş olarak aynı şekilde işlenir. Sağ giriş ziyaret sonra durumu sonraki gösterilmiştir.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")  
  
 Sonraki "false" IsParentAJoin yığını ve birleşim koşuluna Var(Extent1) gönderilir. Adlı kullanıcı, Categoryıd'si Var(Extent2) ==. Adlı kullanıcı, Categoryıd'si işlenir. Var(Extenent1) < symbol_Extent1 > sonra bir görünüm yukarı simgesi tabloda çözümlenir. Örnek Var(Extent1) işleme sonucunda basit bir simge için çözümlenmiş olmasından dolayı. Adlı kullanıcı, Categoryıd'si, SqlBuilder ile \<symbol1 >. " Adlı kullanıcı, Categoryıd'si"döndürülür. Karşılaştırma diğer tarafını benzer şekilde işlenir ve birleştirme koşulunun ziyaret sonucunu FROM yan tümcesi SelectStatement1 ve "false" Sil'i IsParentAJoin yığınından değeri eklenir.  
  
 Bu, Join1 tamamen işlendikten ve kapsam simgesi tablosundan Sil'i.  
  
 Join4, Join1 üst işlemeyi denetimini döndürür. Alt seçme deyimi yeniden çünkü Join1 kapsam tek birleştirme simgesiyle < joinSymbol_Join1 > değiştirilir. Ayrıca yeni bir giriş Join1 < joinSymbol_Join1 > ile ilişkilendirmek için Sembol tablosuna eklenir.  
  
 İşlenecek sonraki Join3, Join4 ikinci alt düğümdür. Sağ alt olduğu gibi "false" IsParentAJoin yığına gönderilir. Bu noktada ziyaretçi durumunu sonraki çizimde gösterilmiştir.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")  
  
 Join3, IsParentAJoin false değerini döndürür ve yeni SqlSelectStatement (SelectStatement1) başlatın ve yığında itme gerekiyor. Önceki birleştirmeler önceki ile mi, yeni bir kapsam yığına ve alt işlenen olarak devam ettirir. Sol alt bir uzantı (Extent3) ve sağ alt ayrıca yeni SqlSelectStatement başlatmak için gereken bir birleştirme (Join2): SelectStatement2. Alt Join2 üzerinde kapsam da olan ve SelectStatement2 toplanır.  
  
 Ziyaretçi sağ durumunu Join2 ziyaret sonra ancak sonrası işlemesi (ProcessJoinInputResult) yapılır önce sonraki gösterilmiştir:  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")  
  
 Yığın dışında Sil'i ancak henüz post için ücretsiz kayan üst tarafından işlenen gibi önceki çizimde SelectStatement2 gösterilir. Üst FROM bölümüne eklenmesi gerekir, ancak bir SELECT yan tümcesi olmadan tam bir SQL deyimi değil. Bu nedenle, bu noktada, (girdilerinden tarafından üretilen tüm sütunlar) varsayılan sütunları seçim listesine AddDefaultColumns yöntemi tarafından eklenir. AddDefaultColumns FromExtents sembolleri üzerinden tekrarlanan ve kapsamda duruma tüm sütunları her simgesi ekler. Basit bir simge için eklenecek tüm özelliklerini alınacak simge türü görünüyor. Ayrıca, AllColumnNames sözlüğü sütun adları ile doldurur. Tamamlanan SelectStatement2 SelectStatement1 FROM yan tümcesi eklenir.  
  
 Ardından, yeni bir birleşim sembol Join2 temsil etmek üzere oluşturulur, bu bir iç içe geçmiş birleştirme işaretlenmiş ve, AllJoinExtents SelectStatement1 eklenir ve sembol tablosuna eklendi.  Şimdi birleşim koşulu Join3, Var(Extent3). OrderID Var(Join2) =. Extent4.OrderID, işlenmesi gerekir. Sol taraftaki işlenmesini Join1 birleşim koşulu benzer. Ancak, sağa ve yan "Var(Join2) işlenmesini. Birleşim düzleştirme gerekli olduğundan Extent4.OrderID"farklıdır.  
  
 Sonraki şekilde ziyaretçi hemen önce "Var(Join2). DbPropertyExpression durumunu gösterir. Extent4.OrderID"işlenir.  
  
 Göz önünde bulundurun nasıl "Var(Join2). Extent4.OrderID"ziyaret edilen. İlk olarak, örnek özelliği "Var(Join2). Extent4 "ziyaret edilen başka bir DbPropertyExpression olduğu ve ilk örneğinin"Var(Join2)"ziyaret eder. Üst çoğu kapsamda simgesi tablosundaki "Join2" < joinSymbol_join2 > çözümler. "Var(Join2). işleme DbPropertyExpression için ziyaret yöntemi Extent4 "örnek ziyaret edip düzleştirme gerekli olduğunda bir birleşim simge döndürüldü dikkat edin.  
  
 İç içe geçmiş bir birleştirme olduğuna göre biz birleştirme simgenin NameToExtent sözlükte "Extent4" özelliği aramak, < symbol_Extent4 > çözümlemek ve yeni SymbolPair dönün (< joinSymbol_join2 >, < symbol_Extent4 >). Bu yana bir simge çifti "Var(Join2). örneğinin işlenmesini döndürülür Extent4.OrderID","OrderID"özelliğini temsil ettiği ölçüde sütunlarının listesini içeren bu simge çifti (< symbol_Extent4 >), ColumnPart çözümlenir. Bunu, "Var(Join2). Extent4.OrderID"Çözüldü {< joinSymbol_Join2 >". ", < symbol_OrderID >}.  
  
 Birleşim koşulu Join4 benzer şekilde işlenir. Denetim çoğu proje üst işlenen VisitInputExpression yöntemi döndürür. Döndürülen SelectStatement0 FromExtents baktığınızda, Giriş bir birleşim tanımlanır ve özgün kapsam kaldırır ve bunları yalnızca birleştirme simgesi ile yeni bir kapsam ile değiştirir. Sembol tablosuna de güncelleştirilir ve projeksiyon projenin bir parçası sonraki işlenir. Özellikleri ve birleştirme işlenmekte olan sınırlarını düzleştirme çözme, daha önce açıklandığı gibi özelliğidir.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")  
  
 Son olarak, aşağıdaki SqlSelectStatement oluşturulur:  
  
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
  
### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>SQL üretimi ikinci aşaması: dize komutu oluşturuluyor  
 İkinci aşama sembolleri gerçek adlarını oluşturur ve biz yalnızca bir çakışma çözülmesi gereken bu durumda olduğu gibi "OrderID" adlı sütun temsil eden simgeleri odaklanır. Bunlar SqlSelectStatement vurgulanır. Tüm yeni adları bu gibi temsil etmiyor için farklı örnekler, bunlar yalnızca vurgulamak için şekilde kullanılan sonekleri olduğunu unutmayın. son adlarını aşama (muhtemelen farklı özgün adlarını oluşturmak) henüz atanmış değil.  
  
 Yeniden adlandırılacak gereken ilk simgenin bulunduğu < symbol_OrderID > değil. Yeni adıyla "OrderID1" atanmış, 1 son soneki "OrderID" için kullanılan ve simgenin yeniden adlandırma kalmamanız olarak işaretlenmiş olarak işaretlenir. Ardından, < symbol_OrderID_2 > ilk kullanımını bulunur. Sonraki kullanılabilir sonek ("OrderID2") kullanmak üzere yeniden adlandırılmış ve böylece kullanıldığı sonraki zaman onu yeniden adlandırılmaz yeniden yeniden adlandırma kalmamanız olarak işaretlenmiş. Bu < symbol_OrderID_3 > için çok gerçekleştirilir.  
  
 İkinci aşamasının sonunda, nihai SQL deyimini oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Örnek Sağlayıcısında SQL Oluşturma](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
