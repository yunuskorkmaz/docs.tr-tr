---
title: "Boş Değer Atanabilir İşleçler (F#)"
description: "F # programlama dili kullanılabilir boş değer atanabilir işleçler hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3108c4ac-9e13-464d-a829-084a6eba038f
ms.openlocfilehash: b3c55dcbfd70c9bcddcc4a990b19a5b92620f822
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="nullable-operators"></a>Boş Değer Atanabilir İşleçler

Boş değer atanabilir işleçler aritmetik boş değer atanabilir türler ile bir veya iki tarafta iş ikili aritmetik veya karşılaştırma işleçler şunlardır. Sık yerine gerçek değerler null değerlere izin veritabanları gibi kaynaklardan veri ile çalışırken boş değer atanabilir türler kaynaklanır. Boş değer atanabilir işleçler sorgu ifadelerinde sık kullanılır. Dönüştürme işleçleri aritmetik ve karşılaştırma için boş değer atanabilir işleçler yanı sıra boş değer atanabilir türleri arasında dönüştürme için kullanılır. Boş değer atanabilir belirli sorgu işleçleri sürümleri de vardır.


## <a name="table-of-nullable-operators"></a>Boş değer atanabilir işleçler tablosu
Aşağıdaki tabloda F # dilinde desteklenen boş değer atanabilir işleçler listeler.

|Soldaki null|Sağdaki boş değer atanabilir|Her iki tarafında boş değer atanabilir|
|---|---|---|
|[?>=](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[>=?](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[?>=?](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[?>](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[>?](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[?>?](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[?<=](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[<=?](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[?<=?](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[?<](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<?](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[?<?](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[?<>](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[<>?](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[?<>?](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>Açıklamalar
Boş değer atanabilir işleçler içinde yer alan [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) ad modülünde [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d). Boş değer atanabilir veri türü `System.Nullable<'T>`.

Sorgu ifadelerinde boş değer atanabilir türler değerleri yerine null değerlere izin veren bir veri kaynağından verileri seçerken kaynaklanır. Bir SQL Server veritabanında bir tablodaki her veri sütunu null değerlere izin verilip verilmediğini gösteren bir özniteliği var. Null değerlere izin verilirse, veritabanı tarafından döndürülen veri temel veri türüne göre gibi gösterilemez null değerler içerebilir `int`, `float`ve benzeri. Bu nedenle, veriler olarak döndürülür bir `System.Nullable<int>` yerine `int`, ve `System.Nullable<float>` yerine `float`. Gerçek değer öğesinden elde edilebilir bir `System.Nullable<'T>` kullanarak nesne `Value` özelliği ve, varsa belirleyebilir bir `System.Nullable<'T>` nesne çağırarak değerine sahip `HasValue` yöntemi. Başka bir yararlı yöntem `System.Nullable<'T>.GetValueOrDefault` değer veya varsayılan değeri uygun türde almanıza yardımcı yöntemi. Varsayılan değer "sıfır" değerinin 0 gibi bazı formdur 0.0, veya `false`.

Boş değer atanabilir türler normal dönüşüm işleçleri kullanarak null ilkel türler için dönüştürülen `int` veya `float`. Boş değer atanabilir türler için dönüşüm işleçleri kullanarak bir boş değer atanabilir türünden başka bir boş değer atanabilir türüne dönüştürmek mümkündür. Uygun dönüşüm işleçleri olanları standart aynı ada sahip, ancak ayrı bir modül oldukları [null atanabilir](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) modülünde [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) ad alanı. Genellikle, bu ad sorgu ifadeleri ile çalışırken açın. Bu durumda, boş değer atanabilir dönüşüm işleçleri önek ekleyerek kullanabileceğiniz `Nullable.` aşağıdaki kodda gösterildiği gibi uygun dönüştürme işleci.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Çıktı `10.000000`.

Boş değer atanabilir veri alanları, işleçler gibi sorgu `sumByNullable`, sorgu ifadeleri kullanmak için de mevcut. Boş değer atanabilir veri değerleri ile çalışırken uygun sorgu işleci boş değer atanabilir sürümünü kullanmanız gerekir böylece sorgu işleçleri null türleri için boş değer atanabilir türler ile türü ile uyumlu değildir. Daha fazla bilgi için bkz: [sorgu ifadeleri](../query-expressions.md).

Aşağıdaki örnek, bir F # sorgu ifadesinde boş değer atanabilir işleçler kullanımını göstermektedir. İlk sorgunun bir boş değer atanabilir işleci olmadan bir sorgu nasıl yazacağınızı gösterir; ikinci sorguyu boş değer atanabilir işlecini kullanan bir eşdeğer sorgu gösterir. Bu örnek kod kullanmak üzere ayarlamak nasıl dahil olmak üzere tüm içerik için bkz: [izlenecek yol: tür sağlayıcılarını kullanarak tarafından SQL veritabanına erişme](../../tutorials/type-providers/accessing-a-sql-database.md).

```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq

[<Generate>]
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">

let db = dbSchema.GetDataContext()

query {
    for row in db.Table2 do
    where (row.TestData1.HasValue && row.TestData1.Value > 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
    for row in db.Table2 do
    // Use a nullable operator ?>
    where (row.TestData1 ?> 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="see-also"></a>Ayrıca Bkz.

[Tür sağlayıcıları](../../tutorials/type-providers/index.md)

[Sorgu ifadeleri](../query-expressions.md)
