---
title: Boş Değer Atanabilir İşleçler
description: 'F # programlama dilinde kullanılabilen null yapılabilir işleçler hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 951692ba22781f7f9e759c55bc708fc24f7a5014
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559147"
---
# <a name="nullable-operators"></a>Boş Değer Atanabilir İşleçler

Null yapılabilir işleçler, tek veya her iki tarafta null yapılabilir aritmetik türler ile çalışan ikili aritmetik veya karşılaştırma işleçleridir. Null yapılabilir türler, gerçek değerlerin yerinde null değerlere izin veren veritabanları gibi kaynaklardaki verilerle çalışırken sık sık meydana gelen bir tür. Null yapılabilir işleçler genellikle sorgu ifadelerinde kullanılır. Aritmetik ve karşılaştırma için null yapılabilir işleçlere ek olarak, dönüştürme işleçleri null yapılabilir türler arasında dönüştürme yapmak için kullanılabilir. Ayrıca belirli sorgu işleçlerinin null yapılabilir sürümleri de vardır.

## <a name="table-of-nullable-operators"></a>Null yapılabilir Işleçler tablosu

Aşağıdaki tabloda, F # dilinde desteklenen null yapılabilir işleçler listelenmektedir.

|Sol tarafta null yapılabilir|Sağ tarafta null yapılabilir|Her iki taraf null yapılabilir|
|---|---|---|
|[? >=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=%20))|[>=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E=?%20))|[? >=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=?%20))|
|[? >](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E%20))|[>?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E?%20))|[? >?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E?%20))|
|[? <=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=%20))|[<=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C=?%20))|[? <=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=?%20))|
|[? <](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%20))|[<?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C?%20))|[? <?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C?%20))|
|[?=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=%20))|[=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20=?%20))|[?=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=?%20))|
|[? <>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E%20))|[<>?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C%3E?%20))|[? <>?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E?%20))|
|[?+](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+%20))|[+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20+?%20))|[?+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+?%20))|
|[?-](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-%20))|[-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20-?%20))|[?-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-?%20))|
|[?*](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*%20))|[*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20*?%20))|[?*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*?%20))|
|[?/](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/%20))|[/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20/?%20))|[?/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/?%20))|
|[?%](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%%20))|[%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%?%20))|[?%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%?%20))|

## <a name="remarks"></a>Açıklamalar

Null yapılabilir işleçler, [FSharp. Linq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html)ad alanındaki [NullableOperators](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html) modülüne dahil edilir. Null yapılabilir veri türü `System.Nullable<'T>` .

Sorgu ifadelerinde, değerler yerine null değerlere izin veren bir veri kaynağından veri seçerken null yapılabilir türler oluşur. Bir SQL Server veritabanında, bir tablodaki her veri sütununun, null değerlere izin verilip verilmediğini gösteren bir özniteliği vardır. Null değerlere izin veriliyorsa, veritabanından döndürülen veriler,, vb. temel bir veri türüyle temsil edilemeyecek null değerler içerebilir `int` `float` . Bu nedenle, veriler yerine ve yerine olarak döndürülür `System.Nullable<int>` `int` `System.Nullable<float>` `float` . Gerçek değer, `System.Nullable<'T>` özelliğini kullanarak nesnesinden elde edilebilir `Value` ve `System.Nullable<'T>` yöntemi çağırarak bir nesnenin bir değere sahip olup olmadığını belirleyebilirsiniz `HasValue` . Diğer bir yararlı yöntem, `System.Nullable<'T>.GetValueOrDefault` değeri veya uygun türde varsayılan bir değer almanızı sağlayan yöntemidir. Varsayılan değer, 0, 0,0 veya gibi bir "sıfır" değeri biçimidir `false` .

Null yapılabilir türler, veya gibi olağan dönüştürme işleçleri kullanılarak null yapılamayan ilkel türlere dönüştürülebilir `int` `float` . Null yapılabilir türler için dönüştürme işleçleri kullanılarak, null yapılabilir bir türden başka bir null yapılabilir türe dönüştürmek de mümkündür. Uygun dönüştürme işleçleri standart olanlarla aynı ada sahiptir, ancak bunlar ayrı bir modülde ve [FSharp. Linq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html) ad alanındaki [null yapılabilir](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullablemodule.html) modüldür. Genellikle, sorgu ifadeleriyle çalışırken bu ad alanını açarsınız. Bu durumda, `Nullable.` aşağıdaki kodda gösterildiği gibi, öneki uygun dönüştürme işlecine ekleyerek Nullable dönüştürme işleçlerini kullanabilirsiniz.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Çıktı `10.000000` .

Sorgu ifadelerinde kullanılmak üzere null olabilen veri alanları üzerinde sorgu işleçleri `sumByNullable` de vardır. Null olamayan türler için sorgu işleçleri, null yapılabilir türler ile tür uyumlu değildir, bu nedenle null yapılabilir veri değerleriyle çalışırken uygun sorgu işlecinin Nullable sürümünü kullanmanız gerekir. Daha fazla bilgi için bkz. [sorgu ifadeleri](../query-expressions.md).

Aşağıdaki örnek, bir F # sorgu ifadesinde null yapılabilir işleçlerin kullanımını gösterir. İlk sorgu, null yapılabilir işleç olmadan bir sorguyu nasıl yazacağınızı gösterir. İkinci sorgu, null olabilen bir işleç kullanan eşdeğer bir sorgu gösterir. Bu örnek kodu kullanmak için veritabanını ayarlama da dahil olmak üzere tam bağlam için bkz. [Izlenecek yol: tür sağlayıcılarını kullanarak SQL veritabanına erişme](../../tutorials/type-providers/index.md).

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

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Sağlayıcıları](../../tutorials/type-providers/index.md)
- [Sorgu İfadeleri](../query-expressions.md)
