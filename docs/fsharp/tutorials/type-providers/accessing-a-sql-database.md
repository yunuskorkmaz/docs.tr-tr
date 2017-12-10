---
title: "İzlenecek yol: Tür Sağlayıcılarını Kullanarak SQL Veritabanına Erişme (F#)"
description: "(LINQ-SQL) SqlDataConnection türü sağlayıcısı F # 3. 0'Canlı veritabanı bağlantısı varsa, bir SQL veritabanı için türleri oluşturmak için nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: 7177eca33ded712308bbc6198040d833b7364d55
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a>İzlenecek yol: Tür Sağlayıcılarını Kullanarak SQL Veritabanına Erişme

> [!NOTE]
Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.  Bkz: [FSharp.Data](http://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.

> [!NOTE]
API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Bu kılavuz, F # bir veritabanı için dinamik bir bağlantı varsa, bir SQL veritabanında veri türlerinde oluşturmak 3.0 kullanılabilir (LINQ-SQL) SqlDataConnection türü sağlayıcısı kullanımı açıklanmaktadır. Bir veritabanı için dinamik bir bağlantı sahip değildir, ancak SQL şema dosyası (DBML dosyası) için bir LINQ sahip değilse, bkz: [izlenecek yol: DBML dosyasından oluşturma F # türleri](generating-fsharp-types-from-dbml.md).

Bu kılavuz aşağıdaki görevler gösterilir. Bu görevler başarılı olması gözden geçirme bu sırayla gerçekleştirilmesi gerekir:


- Bir test veritabanı hazırlanıyor

- Projeyi oluşturma

- Tür sağlayıcısı ayarlama

- Veriyi sorgulama

- Boş değer atanabilir alanları ile çalışma

- Bir saklı yordamı çağırma

- Veritabanını güncelleme

- Transact-SQL kodu çalıştırma

- Tam veri bağlamı kullanarak

- Verileri silme

- Bir test veritabanı (gerektiğinde) oluşturun

## <a name="preparing-a-test-database"></a>Bir Test veritabanı hazırlanıyor
SQL Server çalıştıran bir sunucuda test amacıyla bir veritabanı oluşturun. Veritabanı kullanabilir bölümünde bu sayfanın altındaki komut dosyası oluşturma [test veritabanı oluşturma](#creating-a-test-database) Bunu yapmak için.


#### <a name="to-prepare-a-test-database"></a>Bir test veritabanı hazırlamak için

Veritabanım oluşturma komut dosyasını çalıştırmak için **Görünüm** menüsünde ve ardından **SQL Server Nesne Gezgini** veya Ctrl + seçin\, Ctrl + S anahtarları. İçinde **SQL Server Nesne Gezgini** penceresinde, uygun örneğini için kısayol menüsünü açın, seçin **yeni sorgu**, bu sayfanın altındaki komut dosyasını kopyalayın ve komut dosyası düzenleyiciye yapıştırın. SQL komut dosyasını çalıştırmak için üçgen simgesiyle Araç simgesini seçin veya Ctrl + Q anahtarları seçin. Hakkında daha fazla bilgi için **SQL Server Nesne Gezgini**, bkz: [bağlı veritabanı geliştirme](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).


## <a name="creating-the-project"></a>Projeyi oluşturma
Ardından, bir F # uygulama projesi oluşturun.


#### <a name="to-create-and-set-up-the-project"></a>Oluşturun ve projeyi ayarlamak için

1. Yeni bir F # uygulama projesi oluşturun.

2. Başvurular ekleyin [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), yanı `System.Data`, ve `System.Data.Linq`.

3. Uygun ad alanları Program.fs F # kod dosyanın üst kısmına aşağıdaki kod satırlarını ekleyerek açın.

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. Çoğu F # programları ile olarak derlenmiş bir program olarak bu kılavuzda kod yürütebilir veya bir komut dosyası olarak etkileşimli olarak çalıştırabilirsiniz. Komut dosyaları kullanmayı tercih ederseniz, select proje düğümünün kısayol menüsünü açın **Yeni Öğe Ekle**bir F # komut dosyası eklemek ve kodu her adımda komut dosyasına ekleyin. Derleme başvurularını yüklemek için dosyanın üst kısmında aşağıdaki satırları eklemeniz gerekir.

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  Ekleyin ve çalıştırmak için F # Etkileşimli'de Alt + Enter tuşlarına basın, sonra her kod bloğunu seçebilirsiniz.

## <a name="setting-up-a-type-provider"></a>Tür sağlayıcısı ayarlama
Bu adımda, veritabanı şemanızı tür sağlayıcısı oluşturun.


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a>Doğrudan veritabanı bağlantısı türü sağlayıcıdan ayarlamak için

Kritik iki tür sağlayıcısı kullanarak bir SQL veritabanını sorgulamak için kullanabileceğiniz türleri oluşturmak için gereken kod satırı vardır. İlk olarak, tür sağlayıcısı örneği oluşturur. Bunu yapmak için oluşturmak için bir tür kısaltması nasıl göründüğünü bir `SqlDataConnection` bir statik genel parametresiyle. `SqlDataConnection`bir SQL türü sağlayıcısı ve ile karıştırılmamalıdır `SqlConnection` yazın ADO.NET programlamada kullanılır. Bağlanmak istediğiniz veritabanına sahip ve bir bağlantı dizesi varsa, tür sağlayıcısı çağırmak için aşağıdaki kodu kullanın. Verilen örnek dize için kendi bağlantı dizesini değiştirin. Örneğin, sunucunuz MYSERVER ve veritabanı örneği olan örneği, Veritabanım veritabanı adıdır ve veritabanını, sonra bağlantı dizesini erişmek için Windows kimlik doğrulaması kullanmak istediğiniz olarak olacaksa aşağıdaki örnek kodda verilir.

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

Bir türe sahip artık `dbSchema`, veritabanı tablolarını temsil eden tüm oluşturulan türlerin içeren bir üst türü değil. Bir nesne de `db`, veritabanındaki tüm tabloların üyeleri sahiptir. Tablo adlarının özelliklerdir ve bu özellikleri türünü F # derleyici tarafından oluşturulur. Türleri iç içe geçmiş türler altında görünür `dbSchema.ServiceTypes`. Bu nedenle, bu tablolar satır için alınan herhangi bir veriyi bu tablo için oluşturulan uygun türde bir örneğidir. Türünün adı `ServiceTypes.Table1`.

F # dili sorguları SQL sorguları yorumlaması ile tanımak için ayarlar satır gözden `Log` veri bağlamı özelliği.

Daha fazla tür sağlayıcısı tarafından oluşturulan türleri keşfetmek için aşağıdaki kodu ekleyin.

```fsharp
let table1 = db.Table1
```

Üzerine gelerek `table1` türünü görmek için. Kendi türü `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` ve her satırın türü oluşturulan türü olduğunu genel bağımsız değişken gelir `dbSchema.ServiceTypes.Table1`. Derleyici veritabanında her tablo için benzer bir türü oluşturur.

## <a name="querying-the-data"></a>Veriyi sorgulama
Bu adımda, F # sorgu ifadeleri kullanarak bir sorgu yazın.


#### <a name="to-query-the-data"></a>Verileri sorgulamak için

1. Şimdi veritabanında bu tablo için bir sorgu oluşturun. Aşağıdaki kodu ekleyin.

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  Word görünümünü `query` Bunun tipik veritabanı sorgusunun benzer sonuçlar koleksiyonu oluşturur hesaplama ifadesi türü bir sorgu ifadesi olduğunu gösterir. Sorgu getirirseniz örneği olduğunu göreceksiniz [Linq.QueryBuilder sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), sorgu hesaplama ifadesi tanımlayan bir tür. Üzerine getirirseniz `query1`, örneği olduğunu göreceksiniz `System.Linq.IQueryable`. Adı da anlaşılacağı gibi `System.Linq.IQueryable` sorgulanan, verileri değil bir sorgu sonucunu temsil eder. Sorgu zaman değerlendirilen yalnızca veritabanıdır anlamına sorgulanan geç değerlendirme tabi sorgudur. Son satırı sorgusu geçirir `Seq.iter`. Sorguları numaralandırılabilir ve dizileri gibi yinelendiğinde. Daha fazla bilgi için bkz: [sorgu ifadeleri](../../language-reference/query-expressions.md).

2. Şimdi bir sorgu işleci sorguya ekleyin. Sorgu işleçleri daha karmaşık sorgular oluşturmak için kullanabileceğiniz bir dizi vardır. Bu örnek ayrıca sorgu değişkeni ortadan kaldırmak ve ardışık düzen işleci kullanın gösterir.

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. Daha karmaşık bir sorgu iki tablonun JOIN ile birlikte ekleyin.

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. Gerçek kodda Sorgunuzdaki genellikle parametreleridir değerleri veya değişkenleri, derleme zamanında sabitleri. Bir parametre alır ve ardından 10 değeri ile bu işlev çağrıları bir işlevdeki bir sorgu sarmalar aşağıdaki kodu ekleyin.

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a>Boş değer atanabilir alanları ile çalışma
Veritabanlarında, alanları genellikle null değerlere izin verir. .NET türü sistemde, bu türlerde bulunmayan olduğundan, boş bir olası değer olarak null değerlere izin veri sıradan sayısal veri türleri kullanamaz. Bu nedenle, bu değerleri örneği tarafından temsil edilen `System.Nullable` türü. Bu tür alanları değer alanın adı ile doğrudan erişim yerine, bazı ek adımlar eklemeniz gerekir. Kullanabileceğiniz `System.Nullable.Value` null atanabilir bir tür temel alınan değeri erişmek için özellik. `System.Nullable.Value` Özelliği nesne bir değere sahip yerine null ise bir özel durum oluşturur. Kullanabileceğiniz `System.Nullable.HasValue` kullanın veya bir değer olup olmadığını belirlemek için Boolean yöntemi `System.Nullable.GetValueOrDefault()` tüm durumlarda gerçek bir değere sahip olduğundan emin olmak için. Kullanırsanız `System.Nullable.GetValueOrDefault()` ve veritabanında, bir null sonra onu değiştirilir dize türleri için boş bir dize gibi bir değerle tam sayı türleri için 0 veya kayan 0,0 türleri gelin.

Null değerler üzerinde eşitlik testler veya karşılaştırmaları gerçekleştirmek gerektiğinde bir `where` yan tümcesinin sorgudaki bulunan boş değer atanabilir işleçler kullanabileceğiniz [Linq.NullableOperators Modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d). Normal Karşılaştırma işleçleri gibi bunlar `=`, `>`, `<=`ve benzeri dışında boş değer atanabilir değerlerinin olduğu sol veya sağ işlecinin bir soru işaretiyle görünür. Örneğin, işleci `>?` bir büyük-daha sağdaki boş değer atanabilir bir değerle işleci. Bu işleçlere iş taraflardan ifadesinin null ise, ifade için değerlendirme yoludur `false`. İçinde bir `where` yan tümcesi, bu genellikle anlamına gelir null alanlar içeren satırları seçili ve sorgu sonuçlarında döndürülmedi.


#### <a name="to-work-with-nullable-fields"></a>Boş değer atanabilir alanları ile çalışmak için

Aşağıdaki kod null değerleri ile çalışma gösterir; varsayımında **TestData1** null değerlere izin veren bir tamsayı alanıdır.

```fsharp
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

## <a name="calling-a-stored-procedure"></a>Bir saklı yordamı çağırma
Veritabanı üzerinde saklı yordamlarda F # çağrılabilir. Statik parametresinin ayarlamalısınız `StoredProcedures` için `true` türü sağlayıcısı oluşturmada içinde. Tür sağlayıcısı `SqlDataConnection` oluşturulan türlerini yapılandırmak için kullanabileceğiniz çeşitli statik yöntemler içerir. Bu kapsamlı bir açıklama için bkz: [SqlDataConnection türü sağlayıcısı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d). Veri bağlamı türünün bir yöntemi, her bir saklı yordam için oluşturulur.


#### <a name="to-call-a-stored-procedure"></a>Bir saklı yordamı çağırmak için

Saklı yordamlar boş değer atanabilir parametreleri alırsa, uygun bir geçirmeniz gereken `System.Nullable` değeri. Skaler veya bir tablo döndüren bir saklı yordam yöntem dönüş değeri `System.Data.Linq.ISingleResult`, döndürülen veri erişim sağlayan özellikler içerir. Tür bağımsız değişkeni için `System.Data.Linq.ISingleResult` belirli yordam bağlıdır ve ayrıca, tür sağlayıcısı oluşturan türlerinden biridir. Adlı bir saklı yordam için `Procedure1`, türü `Procedure1Result`. Türü `Procedure1Result` adlarını içeren sütunları döndürülen bir tablo veya, skaler değer döndüren bir saklı yordam için dönüş değerini temsil eder.

Aşağıdaki kod bir yordam olduğunu varsayar `Procedure1` adlı bir sütun döndüren bir sorgu parametresi olarak iki boş değer atanabilir tamsayı alan veritabanında çalıştıran `TestData1`ve bir tamsayı döndürür.

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a>Veritabanını güncelleme
LINQ DataContext türü daha kolay bir tam olarak yazılmış şekilde oluşturulan türleriyle hizmetteki veritabanı güncelleştirmeleri gerçekleştirmek için yöntemler içerir.


#### <a name="to-update-the-database"></a>Veritabanını güncellemek için

1. Aşağıdaki kodda birkaç satır veritabanına eklenir. Yalnızca bir satır ekliyorsanız, kullanabileceğiniz `System.Data.Linq.Table.InsertOnSubmit()` eklemek için yeni satır belirtmek için. Birden çok satır ekliyorsanız, bunları bir toplama ve arama yerleştirdiğiniz `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`. Bu yöntemlerin her ikisi çağırdığınızda, veritabanı hemen değiştirilmez. Çağırmalısınız `System.Data.Linq.DataContext.SubmitChanges` gerçekten değişiklikleri uygulamak için. Varsayılan olarak, önce yaptığınız her şey çağrı `System.Data.Linq.DataContext.SubmitChanges` dolaylı olarak aynı işlem bir parçasıdır.

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. Şimdi satırları silme işlemi çağırarak temizleyin.

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a>Transact-SQL kodu çalıştırma
Ayrıca, doğrudan kullanarak Transact-SQL belirtebilirsiniz `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` yöntemi `DataContext` sınıfı.


#### <a name="to-execute-custom-sql-commands"></a>Özel SQL komutlarını çalıştırmak için

Aşağıdaki kod bir kaydı bir tabloya ekleme ve bir tablodan bir kaydı silmek için SQL komutlarının nasıl gönderileceğini gösterir.

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a>Tam veri bağlamı kullanarak
Önceki örneklerde, `GetDataContext` yöntemi ne adlı almak için kullanılan *Basitleştirilmiş veri bağlamı* veritabanı şeması için. Basitleştirilmiş veri bağlamı kullanılabilir olarak çok sayıda üye olmadığından sorgu oluşturma sırasında kullanmak daha kolay olur. Bu nedenle, IntelliSense özelliklerinde göz attığınızda, tabloları ve saklı yordamlar gibi veritabanı yapısına odaklanabilirsiniz. Ancak, Basitleştirilmiş veri bağlamı ile neler yapabileceğiniz bir sınır yoktur. Diğer eylemleri gerçekleştirmenize olanak sağlayan bir tam veri bağlamı. aynı zamanda kullanılabilir bu bulunan `ServiceTypes` ve adına sahip *DataContext* , sağladığınız, statik parametre. Bunu sağlamadı ise veri içerik türünün adı diğer girişinize göre SqlMetal.exe tarafından sizin için oluşturulur. Tam veri bağlamı devraldığı `System.Data.Linq.DataContext` ve ADO.NET veri türlerine başvuruları gibi dahil olduğu temel sınıfın üyeleri ortaya koyar `Connection` nesnesi, gibi yöntemler `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` ve `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` SQL'de sorgular yazmak için kullanabilirsiniz ve işlemleri açıkça çalışmak için de anlamına gelir.


#### <a name="to-use-the-full-data-context"></a>Tam veri içeriği kullanmak için

Aşağıdaki kodda, tam veri bağlamı nesneyi alıp doğrudan veritabanına karşı komutları yürütmek için kullanma gösterilmektedir. Bu durumda, iki komut aynı işlemin bir parçası olarak yürütülür.

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a>Verileri silme
Bu adım veri tablodan satırları silmek nasıl gösterir.


#### <a name="to-delete-rows-from-the-database"></a>Satırları veritabanından silmek için

Şimdi, temiz satırları belirtilen tablodan, örneği satırları siler işlevi yazarak eklenen tüm `System.Data.Linq.Table` sınıfı. Ardından, silmek istediğiniz tüm satırları bulmak için bir sorgu yazın ve sorgu sonuçlarını kanal `deleteRows` işlevi. Bu kod işlev bağımsız değişkenleri, kısmi uygulama sağlama yeteneği yararlanır.

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a>Test veritabanı oluşturma
Bu bölümde Bu anlatımda kullanmak için test veritabanını ayarlamak nasıl gösterir.

Veritabanı şekilde değiştirirseniz, tür sağlayıcısı sıfırlamak sahip unutmayın. Tür sağlayıcısı sıfırlamak için yeniden oluşturmanız veya tür sağlayıcısı içeren projeyi temizleyin.


#### <a name="to-create-the-test-database"></a>Test veritabanı oluşturmak için

1. İçinde **Sunucu Gezgini**, kısayol menüsünü açın **veri bağlantıları** düğümünü ve **Bağlantı Ekle**. **Bağlantı Ekle** iletişim kutusu görüntülenir.

2. İçinde **sunucu adı** kutusunda, bir yönetim erişimine sahip SQL Server örneğinin adını belirtin veya bir sunucuya erişimi yoksa (localdb\v11.0) belirtin. SQL Express LocalDB geliştirme ve test makinenizde basit bir veritabanı sunucusu sağlar. Yeni bir düğüm oluşturulur **Sunucu Gezgini** altında **veri bağlantıları**. Yerel veritabanı hakkında daha fazla bilgi için bkz: [izlenecek yol: Visual Studio'da yerel veritabanı dosyası oluşturma](https://msdn.microsoft.com/library/ms233763.aspx).

3. Yeni bağlantı düğümü için kısayol menüsünü açın ve seçin **yeni sorgu**.

4. Aşağıdaki SQL betiğini kopyalayın, sorgu düzenleyicisine yapıştırın ve ardından **yürütme** araç çubuğunda düğmesini veya Ctrl + Shift + E anahtarları seçin.

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a>Ayrıca Bkz.
[Tür sağlayıcıları](index.md)

[SqlDataConnection türü sağlayıcısı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[İzlenecek yol: DBML dosyasından F # türleri oluşturma](generating-fsharp-types-from-dbml.md)

[Sorgu ifadeleri](../../language-reference/query-expressions.md)

[LINQ-SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)

[SqlMetal.exe &#40; Kod oluşturma Aracı &#41;](https://msdn.microsoft.com/library/bb386987)
