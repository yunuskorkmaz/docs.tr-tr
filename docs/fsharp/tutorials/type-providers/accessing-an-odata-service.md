---
title: "İzlenecek yol: Tür Sağlayıcılarını Kullanarak OData Hizmetine Erişim (F#)"
description: "Bir OData hizmeti için istemci türleri oluşturmak için F # 3. 0'f # ODataService türü sağlayıcısı kullanmayı öğrenin ve hizmet, veri akışlarını sorgu sağlar."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0adae84c-b0fa-455f-994b-274ecdc6df30
ms.openlocfilehash: 750407c36a989cece30c0c0654ff905c8eee3b33
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-an-odata-service-by-using-type-providers"></a>İzlenecek yol: Tür Sağlayıcılarını Kullanarak OData Hizmetine Erişim

> [!NOTE]
Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.  Bkz: [FSharp.Data](https://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.

> [!NOTE]
API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Açık Veri Protokolü, yani OData Internet üzerinden veri aktarımı için bir protokoldür. Birçok veri sağlayıcısı, bir OData web hizmetini yayımlayarak verilerine erişimi kullanıma sunar. F # veri türleri kullanılarak otomatik olarak oluşturulan 3.0 içinde herhangi bir OData kaynaktan veri erişim `ODataService` türü sağlayıcısı. Https://msdn.microsoft.com/library/da3380cc-f6da-4c6c-bdb2-bb86afa59d62 OData hakkında daha fazla bilgi için bkz.

Bu kılavuzda F # ODataService türü sağlayıcısı bir OData hizmeti için istemci türleri oluşturmak için nasıl kullanılacağını gösterir ve hizmet, veri akışlarını sorgu sağlar.

Bu izlenecek yol, başarılı olması için bu sırayla gerçekleştirmeniz gereken aşağıdaki görevleri gösterir:


- İstemci projesi bir OData hizmeti için yapılandırma
<br />

- OData türlerini erişme
<br />

- Bir OData hizmet sorgulama
<br />

- OData istekleri doğrulanıyor
<br />


## <a name="configuring-a-client-project-for-an-odata-service"></a>İstemci projesi bir OData hizmeti için yapılandırma
Bu adımda, bir OData türü sağlayıcısı kullanmak için bir projesi ayarlayın.


#### <a name="to-configure-a-client-project-for-an-odata-service"></a>Bir OData hizmeti için bir istemci projesi yapılandırmak için

- F # konsol uygulaması projesini açın ve ardından bir başvuru ekleyin `System.Data.Services.Client` Framework derleme.
<br />

- Altında `Extensions`, bir başvuru ekleyin `FSharp.Data.TypeProviders` derleme.
<br />

## <a name="accessing-odata-types"></a>OData türlerini erişme
Bu adımda, erişim sağlayan türleri ve verileri bir OData hizmeti için tür sağlayıcısı oluşturun.


#### <a name="to-access-odata-types"></a>OData türlerini erişmek için

- Kod Düzenleyicisi'nde, bir F # kaynak dosyasını açın ve aşağıdaki kodu girin.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type Northwind = ODataService<"https://services.odata.org/Northwind/Northwind.svc/">

let db = Northwind.GetDataContext()
let fullContext = Northwind.ServiceTypes.NorthwindEntities()
```

Bu örnekte, F # tür sağlayıcısı çağrılır ve belirttiğiniz OData URI'SİNİN temel türleri kümesi oluşturmak üzere talimat. İki nesne kullanılabilir; verileri hakkında bilgiler içerir Basitleştirilmiş veri bağlamı biridir `db` örnekte. Bu nesne türleri tablolar veya akışları için içeren veritabanı ile ilişkili yalnızca veri türlerini içerir. Başka bir nesneyle `fullContext` Bu örnekte, bir örneğidir `System.Data.Linq.DataContext` ve birçok ek özellikler, yöntemleri ve olayları içerir.
<br />


## <a name="querying-an-odata-service"></a>Bir OData hizmet sorgulama
Bu adımda, OData hizmeti sorgulamak için F # sorgu ifadeleri kullanın.


#### <a name="to-query-an-odata-service"></a>Bir OData hizmeti sorgulamak için

1. Türü Sağlayıcısı'nı ayarladığımıza göre OData hizmetine sorgulayabilirsiniz.
<br />  OData yalnızca bir alt kümesini kullanılabilir sorgu işlemleri destekler. Aşağıdaki işlemleri ve bunların karşılık gelen anahtar sözcükleri desteklenir:
<br />
  - projeksiyon (`select`)
<br />

  - Filtreleme (`where`, göre dizesi kullanılarak tarih ve işlemler)
<br />

  - disk belleği (`skip`, `take`)
<br />

  - Sıralama (`orderBy`, `thenBy`)
<br />

  - `AddQueryOption` ve `Expand`, OData özel işlemler olduğu
<br />

  Daha fazla bilgi için bkz: [LINQ konuları &#40; WCF Veri Hizmetleri &#41; ](https://msdn.microsoft.com/library/ee622463.aspx).
<br />  Tüm girişleri akış veya tablosunda istiyorsanız, aşağıdaki kod olduğu gibi sorgu ifadesi en basit biçimi kullanın:
<br />

```fsharp
query {
  for customer in db.Customers do
  select customer
} |> Seq.iter (fun customer ->
                  printfn "ID: %s\nCompany: %s" customer.CustomerID customer.CompanyName
                  printfn "Contact: %s\nAddress: %s" customer.ContactName customer.Address
                  printfn "         %s, %s %s" customer.City customer.Region customer.PostalCode
                  printfn "%s\n" customer.Phone)
```

2. Alanları veya select anahtar sözcüğünden sonra bir tanımlama grubu kullanarak istediğiniz sütunları belirtin.
<br />

```fsharp
  query { 
    for cat in db.Categories do
    select (cat.CategoryID, cat.CategoryName, cat.Description)
  } |> Seq.iter (fun (id, name, description) ->
                    printfn "ID: %d\nCategory: %s\nDescription: %s\n" id name description)
```

3. Koşullar kullanarak belirttiğiniz bir `where` yan tümcesi.
<br />

```fsharp
query {
  for employee in db.Employees do
  where (employee.EmployeeID = 9)
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

4. Sorgu için bir alt dize koşulu kullanarak belirtin `System.String.Contains(System.String)` yöntemi. Aşağıdaki sorgu adlarında "Chef" olan tüm ürünleri verir. Ayrıca kullanımını fark `System.Nullable<'T>.GetValueOrDefault()`. `UnitPrice` Kullanarak ya da değeri almalısınız bir boş değer atanabilir değer olduğundan `Value` özelliği veya çağırmalıdır `System.Nullable<'T>.GetValueOrDefault()`.
<br />

```fsharp
query { 
  for product in db.Products do
  where (product.ProductName.Contains("Chef"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

5. Kullanım `System.String.EndsWith(System.String)` bir dizeyi belirli bir dizeyle sona ereceğini belirtmek için yöntem.
<br />

```fsharp
query {
  for product in db.Products do
  where (product.ProductName.EndsWith("u"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

6. Koşulları birleştirmek bir where yan tümcesini kullanarak `&&` işleci.
<br />

```fsharp
// Open this module to use the nullable operators ?> and ?<.
open Microsoft.FSharp.Linq.NullableOperators

let salesIn1997 = query { 
  for sales in db.Category_Sales_for_1997 do
  where (sales.CategorySales ?> 50000.00M && sales.CategorySales ?< 60000.0M)
  select sales }

salesIn1997
|> Seq.iter (fun sales ->
                printfn "Category: %s Sales: %M" sales.CategoryName (sales.CategorySales.GetValueOrDefault()))
```

İşleçler `?>` ve `?<` boş değer atanabilir işleçler. Boş değer atanabilir eşitlik ve Karşılaştırma işleçleri tam kümesini kullanabilirsiniz. Daha fazla bilgi için bkz: [Linq.NullableOperators Modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).
<br />

7. Kullanmak `sortBy` sorgu işleci sıralamasını belirtmek ve kullanmak `thenBy` sıralama başka bir düzeyini belirtmek için. Ayrıca bir tanımlama grubu sorgu select bölümünde kullanımına dikkat edin. Bu nedenle, sorgu bir tanımlama grubu bir öğe türüne sahip.
<br />

```fsharp
printfn "Freight for some orders: "

query { 
  for order in db.Orders do
  sortBy (order.OrderDate.Value)
  thenBy (order.OrderID)
  select (order.OrderDate, order.OrderID, order.Customer.CompanyName)
} |> Seq.iter (fun (orderDate, orderID, company) ->
                  printfn "OrderDate: %s" (orderDate.GetValueOrDefault().ToString())
                  printfn "OrderID: %d Company: %s\n" orderID company)
```

8. Atla işlecini kullanarak belirli bir kayıt sayısı yoksay ve döndürmek için kayıt sayısını belirtmek için Al işlecini kullanın. Bu şekilde, disk belleği veri akışları uygulayabilirsiniz.
<br />

```fsharp
printfn "Get the first page of 2 employees."

query { 
  for employee in db.Employees do
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID)) 

printfn "Get the next 2 employees."

query { 
  for employee in db.Employees do
  skip 2
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

## <a name="verifying-the-odata-request"></a>OData isteği doğrulama
Tüm OData sorgu belirli bir OData isteği URI çevrilir. URI, belki de hata ayıklama için bir olay işleyicisi ekleyerek amacıyla olduğunu doğrulayabilirsiniz `SendingRequest` tam veri context nesnesinde olay.


#### <a name="to-verify-the-odata-request"></a>OData isteği doğrulamak için

- OData isteği URI doğrulamak için aşağıdaki kodu kullanın:
<br />

```fsharp
// The DataContext property returns the full data context.
db.DataContext.SendingRequest.Add (fun eventArgs -> printfn "Requesting %A" eventArgs.Request.RequestUri)
```

Önceki kod çıktısı şöyledir:
<br />`requesting https://services.odata.org/Northwind/Northwind.svc/Orders()?$orderby=ShippedDate&amp;$select=OrderID,ShippedDate`


## <a name="see-also"></a>Ayrıca Bkz.
[Sorgu İfadeleri](../../language-reference/query-expressions.md)

[LINQ konuları (WCF Veri Hizmetleri)](https://msdn.microsoft.com/library/ee622463.aspx)

[ODataService türü sağlayıcısı (F #)](https://msdn.microsoft.com/visualfsharpdocs/conceptual/odataservice-type-provider-%5bfsharp%5d)
