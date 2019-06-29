---
title: 'İzlenecek yol: SQL Üretimi'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 5d8723c6a6d1ab12a2ba1f0f2f7cd5e09e82bfad
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422768"
---
# <a name="walkthrough-sql-generation"></a>İzlenecek yol: SQL Üretimi

Bu konu başlığı altında SQL oluşturma nasıl meydana gösterir [örnek sağlayıcısı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0). Aşağıdaki varlık SQL sorgusunu örnek sağlayıcısında modeli kullanır:

```sql
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

 Bu konu, bu çıkış komut ağacı ile aşağıdaki SQL deyimlerini Çevir açıklar.

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

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>Birinci aşama SQL oluşturma: İfade ağacı ziyaret edin

Aşağıdaki şekil, ziyaretçi ilk boş durumunu gösterir.  Bu konu başlığı altında yaptığımız, yalnızca ilgili izlenecek yol açıklama özellikleri gösterilmektedir.

![Diyagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")

Proje düğümünü ziyaret edildiğinde VisitInputExpression Join4 ziyaret edin VisitJoinExpression yöntemi tetikler (Join4), kendi girişi üzerinde çağrılır. Bu, en üstteki birleştirme olduğu için IsParentAJoin false değerini döndürür ve yeni bir SqlSelectStatement (SelectStatement0) oluşturulur ve SELECT deyimi yığına itildi. Ayrıca, yeni bir kapsam (scope0) sembolü tabloda girilir. JOIN (sol) ilk giriş ziyaret edilen önce 'true' IsParentAJoin yığın üzerine itilir. Sağa Join4 sol giriş olan Join1 ziyaret edilen önce ziyaretçi sonraki çizimde gösterildiği gibi durumudur.

![Diyagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")

Birleştirme ziyaret ettiğinizde Join4 yöntemi çağrılır, IsParentAJoin geçerlidir, bu nedenle geçerli select deyimi SelectStatement0 yeniden kullanır. Yeni bir kapsam girilen (kapsam1) ' dir. Sol alt, Extent1, ziyaret önce başka bir true IsParentAJoin yığın üzerine itilir.

Çünkü IsParentAJoin true döndürür Extent1 ziyaret edildiğinde "[dbo]. içeren bir SqlBuilder döndürür. [Products] ". Denetim Join4 ziyaret yöntemi döndürür. Bir giriş IsParentAJoin kaldırılır ve hangi Extent1 SelectStatement0 From yan tümcesi ziyaret sonucunu ekler ProcessJoinInputResult çağrılır. Oluşturulan bir giriş bağlaması adı "Extent1" için yeni bir sembol, symbol_Extent1, gelen SelectStatement0 ve ayrıca "Olarak" FromExtents eklenen ve symbol_Extent1 eklenir from yan tümcesi. Yeni bir giriş AllExtentNames için 0 değerini "Extent1 için" eklenir. Yeni bir giriş, geçerli kapsamda "Extent1", sembol symbol_Extent1 ile ilişkilendirmek için Sembol tablosuna eklenir. Symbol_Extent1 SqlSelectStatement ' AllJoinExtents için de eklenir.

Join1 sağ girişine ziyaret edilen önce "LEFT OUTER JOIN" SelectStatement0 From yan tümcesi eklenir. Sağ giriş tarama ifade olduğundan, true yeniden IsParentAJoin yığına itilir. Sonraki şekilde gösterildiği gibi sağ girişine ziyaret önce durumu.

![Diyagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")

Sağ giriş sol giriş olarak aynı şekilde işlenir. Sonraki şekilde gösterildiği sağ girişine ziyaret sonra durumu.

![Diyagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")

Sonraki "false" IsParentAJoin yığını ve birleştirme koşulunun Var(Extent1) gönderilir. CategoryID Var(Extent2) ==. CategoryID işlenir. Var(Extent1) Çözüldü \<symbol_Extent1 > Sembol tablosuna Ara sonra. Örneği basit bir sembole Var(Extent1) işleme sonucunda, çözümlenmiş olmasından dolayı. CategoryID, bir SqlBuilder ile \<symbol1 >. " CategoryID"döndürülür. Karşılaştırma diğer tarafında benzer şekilde işlenir ve birleştirme koşulunun ziyaret sonucunu FROM yan tümcesi SelectStatement1 ve "false" POP IsParentAJoin yığından değer eklenir.

Bu, Join1 tamamen işlenmesi ve sembol tablodan bir kapsam kaldırılır.

Join4, Join1 üst işlemesine denetimini döndürür. Alt seçme deyimi yeniden çünkü Join1 alanları tek bir birleşim simgesi ile değiştirilir \<joinSymbol_Join1 >. Ayrıca yeni bir giriş Join1 ile ilişkilendirmek için Sembol tablosuna eklenir \<joinSymbol_Join1 >.

İşlenecek sonraki Join3, ikinci alt öğesinin Join4 düğümüdür. Sağ alt olduğu gibi "false" IsParentAJoin yığına itilir. Bu noktada ziyaretçi durumunu, sonraki çizimde gösterilmiştir.

![Diyagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")

Join3 için IsParentAJoin false değerini döndürür ve yeni bir SqlSelectStatement (SelectStatement1) başlatın ve yığında göndermek gerekir. İşlem, önceki birleştirmeler önceki mı, yeni bir kapsam yığın üzerine itilir ve alt işlenebilir gibi devam eder. Sol alt bir uzantı (Extent3) ve sağ alt ayrıca yeni SqlSelectStatement başlatmak için gereken bir birleştirme (Join2): SelectStatement2. Alt Join2 üzerinde de kapsamları misiniz ve SelectStatement2 toplanır.

Ziyaretçi sağ durumunu Join2 ziyaret edilen sonra ancak (ProcessJoinInputResult) sonrası işleme yapılmadan önce bir sonraki çizimde gösterilmektedir:

![Diyagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")

Önceki resimde, çünkü yığın dışında POP ancak henüz sonrası ücretsiz kayan üst öğe tarafından işlenen olarak SelectStatement2 gösterilir. Bu üst FROM bölümüne eklenmesi gerekir, ancak bir SELECT yan tümcesi olmadan tam bir SQL deyimi değil. Bu nedenle, bu noktada, (girdilerinden tarafından üretilen tüm sütunlar) varsayılan sütunları seçim listesine AddDefaultColumns yöntemi tarafından eklenir. AddDefaultColumns FromExtents sembolleri üzerinden yinelenir ve her bir sembol için kapsam olarak öne sürülen tüm sütunları ekler. Basit bir sembol için eklenmesi için tüm özelliklerini almak için simge türü görünüyor. Ayrıca, AllColumnNames sözlük sütun adları ile doldurur. Tamamlanan SelectStatement2 SelectStatement1 FROM yan tümcesi eklenir.

Ardından, yeni bir birleştirme sembol Join2 temsil etmek için oluşturulmuş, iç içe birleşim işaretlenmiş ve, AllJoinExtents SelectStatement1 eklenir ve sembol tablosuna eklenir.  Artık birleştirme koşulunun Join3, Var(Extent3). OrderID Var(Join2) =. Extent4.OrderID, işlenmesi gerekir. Sol taraftaki işlenmesini Join1 birleştirme durumuna benzer. Ancak, işleme ve sağ tarafında "Var(Join2). Birleştirme düzleştirme gerekli olduğundan Extent4.OrderID"farklıdır.

Sonraki şekilde, ziyaretçi hemen önce "Var(Join2). DbPropertyExpression durumunu gösterir. Extent4.OrderID"işlenir.

Göz önünde bulundurun nasıl "Var(Join2). Extent4.OrderID"ziyaret edilmedi. İlk olarak, örnek özelliğini "Var(Join2). Extent4 "ziyaret edildiğinde, başka bir DbPropertyExpression olduğundan ve önce kendi örneğini"Var(Join2)"ziyaret eder. Sembol tablosuna üst çoğu kapsam içinde "Join2" çözümler \<joinSymbol_join2 >. "Var(Join2). işleme DbPropertyExpression için ziyaret yöntemi Extent4 "örnek ziyaret edip düzleştirme gerektiğinde bir birleşim sembol döndürülen dikkat edin.

İç içe birleşim olduğundan, biz özelliği "Extent4" birleştirme sembol NameToExtent sözlüğünde baktığınızda, kendisine çözmek \<symbol_Extent4 > ve yeni SymbolPair döndürür (\<joinSymbol_join2 >, \<symbol_Extent4 ">). Bir simge çifti "Var(Join2). örneğinin işlenmesini döndürüldüğünden Extent4.OrderID","OrderID"özelliği bu simge çifti ColumnPart çözümlenen (\<symbol_Extent4 >), temsil ettiği kapsamın sütunlar listesine sahiptir. Bunu, "Var(Join2). Extent4.OrderID"Çözüldü { \<joinSymbol_Join2 >,". ", \<symbol_OrderID >}.

Birleşim koşulu Join4 benzer şekilde işlenir. Denetimi üst işleme VisitInputExpression yöntemi çoğu proje döndürür. Döndürülen SelectStatement0 ' FromExtents bakarak, Giriş bir birleştirme tanımlanır ve özgün kapsamlarını kaldırır ve bunları yeni bir uzantı yalnızca birleştirme sembolü ile değiştirir. Sembol tablosuna de güncelleştirilir ve projeksiyon projenin bir parçası sonraki işlenir. Özellikleri ve düzleştirme birleştirme kapsam çözümleme, daha önce açıklandığı gibi özelliğidir.

![Diyagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")

Son olarak, aşağıdaki SqlSelectStatement üretilir:

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

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>İkinci aşama SQL oluşturma: STRING komutu oluşturma

İkinci aşama simgelerinin gerçek adlarını oluşturur ve yalnızca bir çakışma çözülmesi gerekir, bu durumda olduğu gibi "OrderID" adlı sütunlar temsil eden simgeler odaklanıyoruz. Bunlar SqlSelectStatement vurgulanır. Yalnızca yeni adlara bu şekilde temsil eden değil farklı örnekleri, bunlar vurgulamak için şekilde kullanılan sonekleri olduğunu unutmayın. Aşama son adlarıyla (büyük olasılıkla farklı özgün adlarını form) henüz atanmadı.

Yeniden adlandırılacak gereken ilk simge bulunamadı olan \<symbol_OrderID >. Yeni adıyla "OrderID1" atanmış, 1, sembol yeniden adlandırma gerek değil olarak işaretlenir ve son soneki "OrderID" için kullanılan olarak işaretlenmiş. Ardından, ilk kullanımını \<symbol_OrderID_2 > bulunur. Sonraki kullanılabilir soneki ("OrderID2") kullanan olarak yeniden adlandırıldı ve böylece kullanıldığı bir sonraki açışınızda, yeniden adlandırılmaz yeniden yeniden adlandırma, kalmamanız olarak işaretlenmiş. Bunu yapmanız \<symbol_OrderID_3 > çok.

İkinci aşama sonunda, son SQL deyimi oluşturuldu.

## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Sağlayıcısında SQL Oluşturma](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
