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
# <a name="walkthrough-sql-generation"></a>İzlenecek yol: SQL Üretimi

Bu konuda, [örnek SAĞLAYıCıDA](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)SQL oluşturma işleminin nasıl gerçekleştiği gösterilmektedir. Aşağıdaki Entity SQL sorgusu, örnek sağlayıcıda bulunan modeli kullanır:

```sql
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName
        FROM NorthwindEntities.Products AS P) as j1
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry
            FROM NorthwindEntities.OrderDetails AS OD) as j2
            ON j1.ProductId == j2.ProductId
```

Sorgu, sağlayıcıya geçirilen aşağıdaki çıkış komut ağacını üretir:

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

 Bu konuda, bu çıktı komut ağacının aşağıdaki SQL deyimlerine nasıl çevrilebileceğini açıklanmaktadır.

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

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>SQL oluşturma 'nın ilk aşaması: Ifade ağacını ziyaret etme

Aşağıdaki şekilde, ziyaretçinin başlangıçtaki boş durumu gösterilmektedir.  Bu konuda, yalnızca izlenecek yol açıklamasında ilgili özellikler gösterilir.

![Diyagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")

Proje düğümü ziyaret edildiğinde, VisitInputExpression kendi girdisi üzerinden çağrılır (Join4), bu, Join4 'ın VisitJoinExpression yöntemi tarafından nasıl ziyaret edildiğini tetikler. Bu en üstteki bir JOIN olduğundan, ıparentajoın yanlış döndürür ve SELECT deyimin yığınına yeni bir Sqlselectdeyimin (SelectStatement0) oluşturulup gönderilir. Ayrıca, sembol tablosuna yeni bir kapsam (scope0) girilir. Birleşimin ilk (sol) girişi ziyaret edildiğinde, ıparentajoın yığınına ' true ' gönderildi. Join4 'in sol girişi olan Join1 'den önce, ziyaretçi durumu, sonraki şekilde gösterildiği gibidir.

![Diyagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44EA-8e74-c5001d5d5d79")

Join4 üzerinden bir JOIN yöntemi çağrıldığında, ısparentajoın değeri true 'dur, bu nedenle geçerli SELECT ifadesini yeniden kullanır SelectStatement0. Yeni bir kapsam girilmiştir (kapsam1). Sol alt öğesini ziyaret etmeden önce, Extent1, Isparentajoın yığınına başka bir doğru gönderilir.

Extent1 ziyaret edildiğinde, ısparentajoın doğru döndürdüğünden, "[dbo]" içeren bir SqlBuilder döndürür. [Ürünler] ". Denetim, Join4 ziyaret eden yönteme geri döner. Bir giriş Isparentajoın 'ten alınır ve ProcessJoinInputResult çağrılır ve bu, ziyaret Extent1 sonucunu SelectStatement0 From yan tümcesine ekler. "Extent1" giriş bağlama adı için symbol_Extent1, "" adlı yeni bir sembol oluşturulur, SelectStatement0 'in FromExtents öğesine eklenir ve ayrıca "as" ve symbol_Extent1 from yan tümcesine eklenir. "Extent1" için AllExtentNames öğesine 0 değeri ile yeni bir giriş eklenir. "Extent1" öğesini symbol symbol_Extent1 ile ilişkilendirmek için sembol tablosundaki geçerli kapsama yeni bir giriş eklenir. Symbol_Extent1, Sqlselectdeyimin Alljoinpackages öğesine de eklenir.

Join1 öğesinin doğru girişinden önce, SelectStatement0 From yan tümcesine "LEFT OUTER JOIN" eklenir. Doğru giriş bir tarama ifadesi olduğundan, ısparentajoın yığınına doğru yeniden gönderilir. Sonraki şekilde gösterildiği gibi doğru girişi ziyaret etmeden önce durum.

![Diyagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-B209-e16166304fdc")

Doğru giriş, sol girişle aynı şekilde işlenir. Doğru girişi ziyaret ettikten sonra durum, sonraki şekilde gösterilmiştir.

![Diyagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")

Next "false", ıparentajoın yığınına ve JOIN koşulu var (Extent1) üzerinden gönderilir. CategoryID = = var (Extent2). CategoryID işlenir. Sembol tablosunda bir arama yapıldıktan sonra var \<(Extent1), symbol_Extent1 > olarak çözümlenir. Örnek, var olan (Extent1) işleminin bir sonucu olarak basit bir simgeye çözümlendiğini. CategoryID, symbol1 > olan \<bir SqlBuilder. " CategoryID "döndürülür. Benzer şekilde, karşılaştırmanın diğer tarafı işlenir ve JOIN koşulunu ziyaret eden sonuç SelectStatement1 FROM yan tümcesine eklenir ve "false" değeri Isparentajoın yığınından alınır.

Bununla birlikte, Join1 tamamen işlenir ve bir kapsam sembol tablosundan alınır.

Denetim, Join1 'in üst öğesi olan Join4 işleme döner. Alt öğe SELECT ifadesini yeniden kullandığından, Join1 kapsamları tek bir JOIN simgesiyle \<joinSymbol_Join1 > ile değiştirilmiştir. Ayrıca, Join1 ile \<joinSymbol_Join1 > ilişkilendirmek için sembol tablosuna yeni bir giriş eklenir.

İşlenecek sonraki düğüm, Join3 'in ikinci alt öğesidir. Doğru bir alt öğe olduğundan, ısparentajoın yığınına "false" gönderilir. Bu noktadaki ziyaretçi durumu bir sonraki şekilde gösterilmiştir.

![Diyagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")

Join3 için Isparentajoın yanlış döndürür ve yeni bir Sqlselectdeyimin (SelectStatement1) başlaması ve yığın üzerine itilmesi gerekir. İşleme önceki birleşimlerle yaptığı için devam eder, yığına yeni bir kapsam gönderilir ve alt öğeler işlenir. Sol alt öğe bir kapsam (Extent3) ve sağ alt öğe de yeni bir Sqlselectdeyimin başlaması gereken bir birleşimdir (Join2): SelectStatement2. Join2 üzerindeki alt öğeler de modellerdir ve SelectStatement2 içinde toplanır.

Join2 sonrasında ziyaretçi durumu, ancak işlem sonrası (ProcessJoinInputResult) yapıldıktan sonra bir sonraki şekilde gösterilir:

![Diyagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8B09-4c99-b411-40af239c3c4d")

Önceki şekilde SelectStatement2, yığın dışına ayrıldığından, ancak henüz üst öğe tarafından işlenmediği için serbest bir kayan olarak gösterilir. Bunun üst öğenin bölümüne eklenmesi gerekir, ancak SELECT yan tümcesi olmadan tam bir SQL deyimi değildir. Bu nedenle, bu noktada varsayılan sütunlar (girişleri tarafından üretilen tüm sütunlar), select listesine AddDefaultColumns yöntemine göre eklenir. AddDefaultColumns, FromExtents içindeki sembolleri yineler ve her sembol için kapsamda getirilen tüm sütunları ekler. Basit bir sembol için, eklenecek tüm özellikleri almak için sembol türüne bakar. Ayrıca, AllColumnNames sözlüğünü sütun adlarıyla doldurur. Tamamlanan SelectStatement2, SelectStatement1 FROM yan tümcesine eklenir.

Daha sonra, Join2 temsil etmek için yeni bir JOIN simgesi oluşturulur, iç içe bir JOIN olarak işaretlenir ve SelectStatement1 'in Alljoinpackages öğesine eklenir ve sembol tablosuna eklenir.  Şimdi Join3, var (Extent3) öğesinin JOIN koşulu. OrderID = var (Join2). Extent4. OrderID, işlenmeyi gerektirir. Sol taraftaki işlemin işlenmesi Join1 JOIN koşuluna benzerdir. Bununla birlikte, sağ ve yan "var (Join2) işlemi. Extent4. OrderID, JOIN düzleştirme gerektirdiğinden farklı.

Sonraki şekilde DbPropertyExpression "var (Join2) öncesindeki ziyaretçinin durumu gösterilmektedir. Extent4. OrderID "işlenir.

"Var (Join2) öğesini düşünün. Extent4. OrderID "ziyaret edilir. Birincisi, örnek özelliği "var (Join2). Extent4 ", başka bir DbPropertyExpression olan ve önce" var (Join2) "örneğini ziyaret eden bir kez ziyaret edildi. Sembol tablosundaki en üstteki kapsamda, "Join2", joinSymbol_join2 > olarak \<çözümlenir. DbPropertyExpression işleme "var (Join2) için ziyaret yöntemi içinde. Extent4 "örnek ziyaret edildiğinde ve düzleştirme gerektiğinde bir JOIN sembolünün döndürülmediğine dikkat edin.

İç içe bir JOIN olduğundan, JOIN sembolünün NameToExtent sözlüğünde "Extent4" özelliğini arar, bunu \<symbol_Extent4 > çözün ve yeni bir SymbolPair döndürür (\<joinSymbol_join2 >, \<symbol_Extent4 >). "Var (Join2) örneğinin işlenmesinden bir sembol çifti döndürüldüğünden. Extent4. OrderID "," OrderID "özelliği, temsil ettiği kapsamın sütunlarının bir listesini içeren, bu\<sembol çiftinin (symbol_Extent4 >) ColumnPart öğesinden çözümlenir. So, "var (Join2). Extent4. OrderID, { \<joinSymbol_Join2 >, ".", \<symbol_OrderID >} olarak çözümlendi.

Join4 'in JOIN koşulu benzer şekilde işlenir. Denetim, en üstteki proje işlenen VisitInputExpression yöntemine döner. Döndürülen SelectStatement0 'in FromExtents ' ye bakarak, giriş bir JOIN olarak tanımlanır ve özgün uzantıları kaldırır ve yalnızca JOIN simgesiyle yeni bir uzantı ile değiştirir. Sembol tablosu da güncellenir ve projenin projeksiyon bölümü işlenir. Özelliklerin çözümlenmesi ve JOIN kapsamlarının düzleştirilmesi daha önce açıklanmıştır.

![Diyagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40AE-ACCC-a10e18e28b81")

Son olarak, aşağıdaki Sqlselectdeyimin oluşturulması gerekir:

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

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>SQL üretimi ikinci aşaması: String komutunu oluşturma

İkinci aşama semboller için gerçek adlar üretir ve yalnızca "OrderID" adlı sütunları temsil eden simgelere odaklanıyoruz, bu durumda bir çakışma çözümlenmesi gerekir. Bunlar Sqlselectdeyimde vurgulanır. Şekilde kullanılan son eklerin yalnızca bunların farklı örnekler olduğunu vurgulayıp, bu aşamada son adlarının (yani özgün adların farklı biçimde) henüz atanmadığını unutmayın.

Yeniden adlandırılması \<gereken ilk sembol symbol_OrderID >. Yeni adı "OrderID1" olarak atanır, 1 "OrderID" için son kullanılan sonek olarak işaretlenir ve sembol yeniden adlandırmadan önce işaretlenir. Sonra, \<symbol_OrderID_2 > ilk kullanımı bulunur. Bu, bir sonraki kullanılabilir son eki ("OrderID2") kullanacak şekilde yeniden adlandırılamayan olarak işaretlenir ve daha sonra bir dahaki sefer kullanıldığında yeniden adlandırılamayan olarak işaretlenir. Bu, symbol_OrderID_3 > \<için yapılır.

İkinci aşamanın sonunda, son SQL açıklaması oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Sağlayıcısında SQL Oluşturma](sql-generation-in-the-sample-provider.md)
