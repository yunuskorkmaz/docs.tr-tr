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
ms.openlocfilehash: dbc5d889fb7883b4327180fdf34accf45bf519e7
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a><span data-ttu-id="24dd1-104">İzlenecek yol: Tür Sağlayıcılarını Kullanarak SQL Veritabanına Erişme</span><span class="sxs-lookup"><span data-stu-id="24dd1-104">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="24dd1-105">Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="24dd1-106">Bkz: [FSharp.Data](https://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.</span><span class="sxs-lookup"><span data-stu-id="24dd1-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="24dd1-107">API başvuru bağlantılar için MSDN götürür.</span><span class="sxs-lookup"><span data-stu-id="24dd1-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="24dd1-108">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="24dd1-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="24dd1-109">Bu kılavuz, F # bir veritabanı için dinamik bir bağlantı varsa, bir SQL veritabanında veri türlerinde oluşturmak 3.0 kullanılabilir (LINQ-SQL) SqlDataConnection türü sağlayıcısı kullanımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24dd1-109">This walkthrough explains how to use the SqlDataConnection (LINQ to SQL) type provider that is available in F# 3.0 to generate types for data in a SQL database when you have a live connection to a database.</span></span> <span data-ttu-id="24dd1-110">Bir veritabanı için dinamik bir bağlantı sahip değildir, ancak SQL şema dosyası (DBML dosyası) için bir LINQ sahip değilse, bkz: [izlenecek yol: DBML dosyasından oluşturma F # türleri](generating-fsharp-types-from-dbml.md).</span><span class="sxs-lookup"><span data-stu-id="24dd1-110">If you do not have a live connection to a database, but you do have a LINQ to SQL schema file (DBML file), see [Walkthrough: Generating F# Types from a DBML File](generating-fsharp-types-from-dbml.md).</span></span>

<span data-ttu-id="24dd1-111">Bu kılavuz aşağıdaki görevler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-111">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="24dd1-112">Bu görevler başarılı olması gözden geçirme bu sırayla gerçekleştirilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="24dd1-112">These tasks must be performed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="24dd1-113">Bir test veritabanı hazırlanıyor</span><span class="sxs-lookup"><span data-stu-id="24dd1-113">Preparing a test database</span></span>

- <span data-ttu-id="24dd1-114">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="24dd1-114">Creating the project</span></span>

- <span data-ttu-id="24dd1-115">Tür sağlayıcısı ayarlama</span><span class="sxs-lookup"><span data-stu-id="24dd1-115">Setting up a type provider</span></span>

- <span data-ttu-id="24dd1-116">Veriyi sorgulama</span><span class="sxs-lookup"><span data-stu-id="24dd1-116">Querying the data</span></span>

- <span data-ttu-id="24dd1-117">Boş değer atanabilir alanları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="24dd1-117">Working with nullable fields</span></span>

- <span data-ttu-id="24dd1-118">Bir saklı yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="24dd1-118">Calling a stored procedure</span></span>

- <span data-ttu-id="24dd1-119">Veritabanını güncelleme</span><span class="sxs-lookup"><span data-stu-id="24dd1-119">Updating the database</span></span>

- <span data-ttu-id="24dd1-120">Transact-SQL kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="24dd1-120">Executing Transact-SQL code</span></span>

- <span data-ttu-id="24dd1-121">Tam veri bağlamı kullanarak</span><span class="sxs-lookup"><span data-stu-id="24dd1-121">Using the full data context</span></span>

- <span data-ttu-id="24dd1-122">Verileri silme</span><span class="sxs-lookup"><span data-stu-id="24dd1-122">Deleting data</span></span>

- <span data-ttu-id="24dd1-123">Bir test veritabanı (gerektiğinde) oluşturun</span><span class="sxs-lookup"><span data-stu-id="24dd1-123">Create a test database (as needed)</span></span>

## <a name="preparing-a-test-database"></a><span data-ttu-id="24dd1-124">Bir Test veritabanı hazırlanıyor</span><span class="sxs-lookup"><span data-stu-id="24dd1-124">Preparing a Test Database</span></span>
<span data-ttu-id="24dd1-125">SQL Server çalıştıran bir sunucuda test amacıyla bir veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24dd1-125">On a server that's running SQL Server, create a database for testing purposes.</span></span> <span data-ttu-id="24dd1-126">Veritabanı kullanabilir bölümünde bu sayfanın altındaki komut dosyası oluşturma [test veritabanı oluşturma](#creating-a-test-database) Bunu yapmak için.</span><span class="sxs-lookup"><span data-stu-id="24dd1-126">You can use the database create script at the bottom of this page in the section [Creating a test database](#creating-a-test-database) to do this.</span></span>


#### <a name="to-prepare-a-test-database"></a><span data-ttu-id="24dd1-127">Bir test veritabanı hazırlamak için</span><span class="sxs-lookup"><span data-stu-id="24dd1-127">To prepare a test database</span></span>

<span data-ttu-id="24dd1-128">Veritabanım oluşturma komut dosyasını çalıştırmak için **Görünüm** menüsünde ve ardından **SQL Server Nesne Gezgini** veya Ctrl + seçin\, Ctrl + S anahtarları.</span><span class="sxs-lookup"><span data-stu-id="24dd1-128">To run the MyDatabase Create Script, open the **View** menu, and then choose **SQL Server Object Explorer** or choose the Ctrl+\, Ctrl+S keys.</span></span> <span data-ttu-id="24dd1-129">İçinde **SQL Server Nesne Gezgini** penceresinde, uygun örneğini için kısayol menüsünü açın, seçin **yeni sorgu**, bu sayfanın altındaki komut dosyasını kopyalayın ve komut dosyası düzenleyiciye yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="24dd1-129">In **SQL Server Object Explorer** window, open the shortcut menu for the appropriate instance, choose **New Query**, copy the script at the bottom of this page, and then paste the script into the editor.</span></span> <span data-ttu-id="24dd1-130">SQL komut dosyasını çalıştırmak için üçgen simgesiyle Araç simgesini seçin veya Ctrl + Q anahtarları seçin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-130">To run the SQL script, choose the toolbar icon with the triangular symbol, or choose the Ctrl+Q keys.</span></span> <span data-ttu-id="24dd1-131">Hakkında daha fazla bilgi için **SQL Server Nesne Gezgini**, bkz: [bağlı veritabanı geliştirme](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span><span class="sxs-lookup"><span data-stu-id="24dd1-131">For more information about **SQL Server Object Explorer**, see [Connected Database Development](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span></span>


## <a name="creating-the-project"></a><span data-ttu-id="24dd1-132">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="24dd1-132">Creating the project</span></span>
<span data-ttu-id="24dd1-133">Ardından, bir F # uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24dd1-133">Next, you create an F# application project.</span></span>


#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="24dd1-134">Oluşturun ve projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="24dd1-134">To create and set up the project</span></span>

1. <span data-ttu-id="24dd1-135">Yeni bir F # uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24dd1-135">Create a new F# Application project.</span></span>

2. <span data-ttu-id="24dd1-136">Başvurular ekleyin [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), yanı `System.Data`, ve `System.Data.Linq`.</span><span class="sxs-lookup"><span data-stu-id="24dd1-136">Add references to [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), as well as `System.Data`, and `System.Data.Linq`.</span></span>

3. <span data-ttu-id="24dd1-137">Uygun ad alanları Program.fs F # kod dosyanın üst kısmına aşağıdaki kod satırlarını ekleyerek açın.</span><span class="sxs-lookup"><span data-stu-id="24dd1-137">Open the appropriate namespaces by adding the following lines of code to the top of your F# code file Program.fs.</span></span>

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. <span data-ttu-id="24dd1-138">Çoğu F # programları ile olarak derlenmiş bir program olarak bu kılavuzda kod yürütebilir veya bir komut dosyası olarak etkileşimli olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dd1-138">As with most F# programs, you can execute the code in this walkthrough as a compiled program, or you can run it interactively as a script.</span></span> <span data-ttu-id="24dd1-139">Komut dosyaları kullanmayı tercih ederseniz, select proje düğümünün kısayol menüsünü açın **Yeni Öğe Ekle**bir F # komut dosyası eklemek ve kodu her adımda komut dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-139">If you prefer to use scripts, open the shortcut menu for the project node, select **Add New Item**, add an F# script file, and add the code in each step to the script.</span></span> <span data-ttu-id="24dd1-140">Derleme başvurularını yüklemek için dosyanın üst kısmında aşağıdaki satırları eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-140">You will need to add the following lines at the top of the file to load the assembly references.</span></span>

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  <span data-ttu-id="24dd1-141">Ekleyin ve çalıştırmak için F # Etkileşimli'de Alt + Enter tuşlarına basın, sonra her kod bloğunu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dd1-141">You can then select each block of code as you add it and press Alt+Enter to run it in F# Interactive.</span></span>

## <a name="setting-up-a-type-provider"></a><span data-ttu-id="24dd1-142">Tür sağlayıcısı ayarlama</span><span class="sxs-lookup"><span data-stu-id="24dd1-142">Setting up a type provider</span></span>
<span data-ttu-id="24dd1-143">Bu adımda, veritabanı şemanızı tür sağlayıcısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24dd1-143">In this step, you create a type provider for your database schema.</span></span>


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a><span data-ttu-id="24dd1-144">Doğrudan veritabanı bağlantısı türü sağlayıcıdan ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="24dd1-144">To set up the type provider from a direct database connection</span></span>

<span data-ttu-id="24dd1-145">Kritik iki tür sağlayıcısı kullanarak bir SQL veritabanını sorgulamak için kullanabileceğiniz türleri oluşturmak için gereken kod satırı vardır.</span><span class="sxs-lookup"><span data-stu-id="24dd1-145">There are two critical lines of code that you need in order to create the types that you can use to query a SQL database using the type provider.</span></span> <span data-ttu-id="24dd1-146">İlk olarak, tür sağlayıcısı örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24dd1-146">First, you instantiate the type provider.</span></span> <span data-ttu-id="24dd1-147">Bunu yapmak için oluşturmak için bir tür kısaltması nasıl göründüğünü bir `SqlDataConnection` bir statik genel parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="24dd1-147">To do this, create what looks like a type abbreviation for a `SqlDataConnection` with a static generic parameter.</span></span> <span data-ttu-id="24dd1-148">`SqlDataConnection` bir SQL türü sağlayıcısı ve ile karıştırılmamalıdır `SqlConnection` yazın ADO.NET programlamada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24dd1-148">`SqlDataConnection` is a SQL type provider, and should not be confused with `SqlConnection` type that is used in ADO.NET programming.</span></span> <span data-ttu-id="24dd1-149">Bağlanmak istediğiniz veritabanına sahip ve bir bağlantı dizesi varsa, tür sağlayıcısı çağırmak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="24dd1-149">If you have a database that you want to connect to, and have a connection string, use the following code to invoke the type provider.</span></span> <span data-ttu-id="24dd1-150">Verilen örnek dize için kendi bağlantı dizesini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-150">Substitute your own connection string for the example string given.</span></span> <span data-ttu-id="24dd1-151">Örneğin, sunucunuz MYSERVER ve veritabanı örneği olan örneği, Veritabanım veritabanı adıdır ve veritabanını, sonra bağlantı dizesini erişmek için Windows kimlik doğrulaması kullanmak istediğiniz olarak olacaksa aşağıdaki örnek kodda verilir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-151">For example, if your server is MYSERVER and the database instance is INSTANCE, the database name is MyDatabase, and you want to use Windows Authentication to access the database, then the connection string would be as given in the following example code.</span></span>

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

<span data-ttu-id="24dd1-152">Bir türe sahip artık `dbSchema`, veritabanı tablolarını temsil eden tüm oluşturulan türlerin içeren bir üst türü değil.</span><span class="sxs-lookup"><span data-stu-id="24dd1-152">Now you have a type, `dbSchema`, which is a parent type that contains all the generated types that represent database tables.</span></span> <span data-ttu-id="24dd1-153">Bir nesne de `db`, veritabanındaki tüm tabloların üyeleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-153">You also have an object, `db`, which has as its members all the tables in the database.</span></span> <span data-ttu-id="24dd1-154">Tablo adlarının özelliklerdir ve bu özellikleri türünü F # derleyici tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24dd1-154">The table names are properties, and the type of these properties is generated by the F# compiler.</span></span> <span data-ttu-id="24dd1-155">Türleri iç içe geçmiş türler altında görünür `dbSchema.ServiceTypes`.</span><span class="sxs-lookup"><span data-stu-id="24dd1-155">The types themselves appear as nested types under `dbSchema.ServiceTypes`.</span></span> <span data-ttu-id="24dd1-156">Bu nedenle, bu tablolar satır için alınan herhangi bir veriyi bu tablo için oluşturulan uygun türde bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-156">Therefore, any data retrieved for rows of these tables is an instance of the appropriate type that was generated for that table.</span></span> <span data-ttu-id="24dd1-157">Türünün adı `ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="24dd1-157">The name of the type is `ServiceTypes.Table1`.</span></span>

<span data-ttu-id="24dd1-158">F # dili sorguları SQL sorguları yorumlaması ile tanımak için ayarlar satır gözden `Log` veri bağlamı özelliği.</span><span class="sxs-lookup"><span data-stu-id="24dd1-158">To familiarize yourself with how the F# language interprets queries into SQL queries, review the line that sets the `Log` property on the data context.</span></span>

<span data-ttu-id="24dd1-159">Daha fazla tür sağlayıcısı tarafından oluşturulan türleri keşfetmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-159">To further explore the types created by the type provider, add the following code.</span></span>

```fsharp
let table1 = db.Table1
```

<span data-ttu-id="24dd1-160">Üzerine gelerek `table1` türünü görmek için.</span><span class="sxs-lookup"><span data-stu-id="24dd1-160">Hover over `table1` to see its type.</span></span> <span data-ttu-id="24dd1-161">Kendi türü `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` ve her satırın türü oluşturulan türü olduğunu genel bağımsız değişken gelir `dbSchema.ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="24dd1-161">Its type is `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` and the generic argument implies that the type of each row is the generated type, `dbSchema.ServiceTypes.Table1`.</span></span> <span data-ttu-id="24dd1-162">Derleyici veritabanında her tablo için benzer bir türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24dd1-162">The compiler creates a similar type for each table in the database.</span></span>

## <a name="querying-the-data"></a><span data-ttu-id="24dd1-163">Veriyi sorgulama</span><span class="sxs-lookup"><span data-stu-id="24dd1-163">Querying the data</span></span>
<span data-ttu-id="24dd1-164">Bu adımda, F # sorgu ifadeleri kullanarak bir sorgu yazın.</span><span class="sxs-lookup"><span data-stu-id="24dd1-164">In this step, you write a query using F# query expressions.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="24dd1-165">Verileri sorgulamak için</span><span class="sxs-lookup"><span data-stu-id="24dd1-165">To query the data</span></span>

1. <span data-ttu-id="24dd1-166">Şimdi veritabanında bu tablo için bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24dd1-166">Now create a query for that table in the database.</span></span> <span data-ttu-id="24dd1-167">Aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-167">Add the following code.</span></span>

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  <span data-ttu-id="24dd1-168">Word görünümünü `query` Bunun tipik veritabanı sorgusunun benzer sonuçlar koleksiyonu oluşturur hesaplama ifadesi türü bir sorgu ifadesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-168">The appearance of the word `query` indicates that this is a query expression, a type of computation expression that generates a collection of results similar of a typical database query.</span></span> <span data-ttu-id="24dd1-169">Sorgu getirirseniz örneği olduğunu göreceksiniz [Linq.QueryBuilder sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), sorgu hesaplama ifadesi tanımlayan bir tür.</span><span class="sxs-lookup"><span data-stu-id="24dd1-169">If you hover over query, you will see that it is an instance of [Linq.QueryBuilder Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), a type that defines the query computation expression.</span></span> <span data-ttu-id="24dd1-170">Üzerine getirirseniz `query1`, örneği olduğunu göreceksiniz `System.Linq.IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="24dd1-170">If you hover over `query1`, you will see that it is an instance of `System.Linq.IQueryable`.</span></span> <span data-ttu-id="24dd1-171">Adı da anlaşılacağı gibi `System.Linq.IQueryable` sorgulanan, verileri değil bir sorgu sonucunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="24dd1-171">As the name suggests, `System.Linq.IQueryable` represents data that may be queried, not the result of a query.</span></span> <span data-ttu-id="24dd1-172">Sorgu zaman değerlendirilen yalnızca veritabanıdır anlamına sorgulanan geç değerlendirme tabi sorgudur.</span><span class="sxs-lookup"><span data-stu-id="24dd1-172">A query is subject to lazy evaluation, which means that the database is only queried when the query is evaluated.</span></span> <span data-ttu-id="24dd1-173">Son satırı sorgusu geçirir `Seq.iter`.</span><span class="sxs-lookup"><span data-stu-id="24dd1-173">The final line passes the query through `Seq.iter`.</span></span> <span data-ttu-id="24dd1-174">Sorguları numaralandırılabilir ve dizileri gibi yinelendiğinde.</span><span class="sxs-lookup"><span data-stu-id="24dd1-174">Queries are enumerable and may be iterated like sequences.</span></span> <span data-ttu-id="24dd1-175">Daha fazla bilgi için bkz: [sorgu ifadeleri](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="24dd1-175">For more information, see [Query Expressions](../../language-reference/query-expressions.md).</span></span>

2. <span data-ttu-id="24dd1-176">Şimdi bir sorgu işleci sorguya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-176">Now add a query operator to the query.</span></span> <span data-ttu-id="24dd1-177">Sorgu işleçleri daha karmaşık sorgular oluşturmak için kullanabileceğiniz bir dizi vardır.</span><span class="sxs-lookup"><span data-stu-id="24dd1-177">There are a number of query operators available that you can use to construct more complex queries.</span></span> <span data-ttu-id="24dd1-178">Bu örnek ayrıca sorgu değişkeni ortadan kaldırmak ve ardışık düzen işleci kullanın gösterir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-178">This example also shows that you can eliminate the query variable and use a pipeline operator instead.</span></span>

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. <span data-ttu-id="24dd1-179">Daha karmaşık bir sorgu iki tablonun JOIN ile birlikte ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-179">Add a more complex query with a join of two tables.</span></span>

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

4. <span data-ttu-id="24dd1-180">Gerçek kodda Sorgunuzdaki genellikle parametreleridir değerleri veya değişkenleri, derleme zamanında sabitleri.</span><span class="sxs-lookup"><span data-stu-id="24dd1-180">In real-world code, the parameters in your query are usually values or variables, not compile-time constants.</span></span> <span data-ttu-id="24dd1-181">Bir parametre alır ve ardından 10 değeri ile bu işlev çağrıları bir işlevdeki bir sorgu sarmalar aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-181">Add the following code that wraps a query in a function that takes a parameter, and then calls that function with the value 10.</span></span>

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a><span data-ttu-id="24dd1-182">Boş değer atanabilir alanları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="24dd1-182">Working with nullable fields</span></span>
<span data-ttu-id="24dd1-183">Veritabanlarında, alanları genellikle null değerlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-183">In databases, fields often allow null values.</span></span> <span data-ttu-id="24dd1-184">.NET türü sistemde, bu türlerde bulunmayan olduğundan, boş bir olası değer olarak null değerlere izin veri sıradan sayısal veri türleri kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="24dd1-184">In the .NET type system, you cannot use the ordinary numerical data types for data that allows nulls because those types do not have null as a possible value.</span></span> <span data-ttu-id="24dd1-185">Bu nedenle, bu değerleri örneği tarafından temsil edilen `System.Nullable` türü.</span><span class="sxs-lookup"><span data-stu-id="24dd1-185">Therefore, these values are represented by instances of `System.Nullable` type.</span></span> <span data-ttu-id="24dd1-186">Bu tür alanları değer alanın adı ile doğrudan erişim yerine, bazı ek adımlar eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-186">Instead of accessing the value of such fields directly with the name of the field, you need to add some extra steps.</span></span> <span data-ttu-id="24dd1-187">Kullanabileceğiniz `System.Nullable.Value` null atanabilir bir tür temel alınan değeri erişmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="24dd1-187">You can use the `System.Nullable.Value` property to access the underlying value of a nullable type.</span></span> <span data-ttu-id="24dd1-188">`System.Nullable.Value` Özelliği nesne bir değere sahip yerine null ise bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24dd1-188">The `System.Nullable.Value` property throws an exception if the object is null rather than having a value.</span></span> <span data-ttu-id="24dd1-189">Kullanabileceğiniz `System.Nullable.HasValue` kullanın veya bir değer olup olmadığını belirlemek için Boolean yöntemi `System.Nullable.GetValueOrDefault()` tüm durumlarda gerçek bir değere sahip olduğundan emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="24dd1-189">You can use the `System.Nullable.HasValue` Boolean method to determine if a value exists, or use `System.Nullable.GetValueOrDefault()` to ensure that you have an actual value in all cases.</span></span> <span data-ttu-id="24dd1-190">Kullanırsanız `System.Nullable.GetValueOrDefault()` ve veritabanında, bir null sonra onu değiştirilir dize türleri için boş bir dize gibi bir değerle tam sayı türleri için 0 veya kayan 0,0 türleri gelin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-190">If you use `System.Nullable.GetValueOrDefault()` and there is a null in the database, then it is replaced with a value such as an empty string for string types, 0 for integral types or 0.0 for floating point types.</span></span>

<span data-ttu-id="24dd1-191">Null değerler üzerinde eşitlik testler veya karşılaştırmaları gerçekleştirmek gerektiğinde bir `where` yan tümcesinin sorgudaki bulunan boş değer atanabilir işleçler kullanabileceğiniz [Linq.NullableOperators Modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="24dd1-191">When you need to perform equality tests or comparisons on nullable values in a `where` clause in a query, you can use the nullable operators found in the [Linq.NullableOperators Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span></span> <span data-ttu-id="24dd1-192">Normal Karşılaştırma işleçleri gibi bunlar `=`, `>`, `<=`ve benzeri dışında boş değer atanabilir değerlerinin olduğu sol veya sağ işlecinin bir soru işaretiyle görünür.</span><span class="sxs-lookup"><span data-stu-id="24dd1-192">These are like the regular comparison operators `=`, `>`, `<=`, and so on, except that a question mark appears on the left or right of the operator where the nullable values are.</span></span> <span data-ttu-id="24dd1-193">Örneğin, işleci `>?` bir büyük-daha sağdaki boş değer atanabilir bir değerle işleci.</span><span class="sxs-lookup"><span data-stu-id="24dd1-193">For example, the operator `>?` is a greater-than operator with a nullable value on the right.</span></span> <span data-ttu-id="24dd1-194">Bu işleçlere iş taraflardan ifadesinin null ise, ifade için değerlendirme yoludur `false`.</span><span class="sxs-lookup"><span data-stu-id="24dd1-194">The way these operators work is that if either side of the expression is null, the expression evaluates to `false`.</span></span> <span data-ttu-id="24dd1-195">İçinde bir `where` yan tümcesi, bu genellikle anlamına gelir null alanlar içeren satırları seçili ve sorgu sonuçlarında döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="24dd1-195">In a `where` clause, this generally means that the rows that contain null fields are not selected and not returned in the query results.</span></span>


#### <a name="to-work-with-nullable-fields"></a><span data-ttu-id="24dd1-196">Boş değer atanabilir alanları ile çalışmak için</span><span class="sxs-lookup"><span data-stu-id="24dd1-196">To work with nullable fields</span></span>

<span data-ttu-id="24dd1-197">Aşağıdaki kod null değerleri ile çalışma gösterir; varsayımında **TestData1** null değerlere izin veren bir tamsayı alanıdır.</span><span class="sxs-lookup"><span data-stu-id="24dd1-197">The following code shows working with nullable values; assume that **TestData1** is an integer field that allows nulls.</span></span>

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

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="24dd1-198">Bir saklı yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="24dd1-198">Calling a stored procedure</span></span>
<span data-ttu-id="24dd1-199">Veritabanı üzerinde saklı yordamlarda F # çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-199">Any stored procedures on the database can be called from F#.</span></span> <span data-ttu-id="24dd1-200">Statik parametresinin ayarlamalısınız `StoredProcedures` için `true` türü sağlayıcısı oluşturmada içinde.</span><span class="sxs-lookup"><span data-stu-id="24dd1-200">You must set the static parameter `StoredProcedures` to `true` in the type provider instantiation.</span></span> <span data-ttu-id="24dd1-201">Tür sağlayıcısı `SqlDataConnection` oluşturulan türlerini yapılandırmak için kullanabileceğiniz çeşitli statik yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-201">The type provider `SqlDataConnection` contains several static methods that you can use to configure the types that are generated.</span></span> <span data-ttu-id="24dd1-202">Bu kapsamlı bir açıklama için bkz: [SqlDataConnection türü sağlayıcısı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="24dd1-202">For a complete description of these, see [SqlDataConnection Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span></span> <span data-ttu-id="24dd1-203">Veri bağlamı türünün bir yöntemi, her bir saklı yordam için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24dd1-203">A method on the data context type is generated for each stored procedure.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="24dd1-204">Bir saklı yordamı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="24dd1-204">To call a stored procedure</span></span>

<span data-ttu-id="24dd1-205">Saklı yordamlar boş değer atanabilir parametreleri alırsa, uygun bir geçirmeniz gereken `System.Nullable` değeri.</span><span class="sxs-lookup"><span data-stu-id="24dd1-205">If the stored procedures takes parameters that are nullable, you need to pass an appropriate `System.Nullable` value.</span></span> <span data-ttu-id="24dd1-206">Skaler veya bir tablo döndüren bir saklı yordam yöntem dönüş değeri `System.Data.Linq.ISingleResult`, döndürülen veri erişim sağlayan özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-206">The return value of a stored procedure method that returns a scalar or a table is `System.Data.Linq.ISingleResult`, which contains properties that enable you to access the returned data.</span></span> <span data-ttu-id="24dd1-207">Tür bağımsız değişkeni için `System.Data.Linq.ISingleResult` belirli yordam bağlıdır ve ayrıca, tür sağlayıcısı oluşturan türlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-207">The type argument for `System.Data.Linq.ISingleResult` depends on the specific procedure and is also one of the types that the type provider generates.</span></span> <span data-ttu-id="24dd1-208">Adlı bir saklı yordam için `Procedure1`, türü `Procedure1Result`.</span><span class="sxs-lookup"><span data-stu-id="24dd1-208">For a stored procedure named `Procedure1`, the type is `Procedure1Result`.</span></span> <span data-ttu-id="24dd1-209">Türü `Procedure1Result` adlarını içeren sütunları döndürülen bir tablo veya, skaler değer döndüren bir saklı yordam için dönüş değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="24dd1-209">The type `Procedure1Result` contains the names of the columns in a returned table, or, for a stored procedure that returns a scalar value, it represents the return value.</span></span>

<span data-ttu-id="24dd1-210">Aşağıdaki kod bir yordam olduğunu varsayar `Procedure1` adlı bir sütun döndüren bir sorgu parametresi olarak iki boş değer atanabilir tamsayı alan veritabanında çalıştıran `TestData1`ve bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="24dd1-210">The following code assumes that there is a procedure `Procedure1` on the database that takes two nullable integers as parameters, runs a query that returns a column named `TestData1`, and returns an integer.</span></span>

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

## <a name="updating-the-database"></a><span data-ttu-id="24dd1-211">Veritabanını güncelleme</span><span class="sxs-lookup"><span data-stu-id="24dd1-211">Updating the database</span></span>
<span data-ttu-id="24dd1-212">LINQ DataContext türü daha kolay bir tam olarak yazılmış şekilde oluşturulan türleriyle hizmetteki veritabanı güncelleştirmeleri gerçekleştirmek için yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-212">The LINQ DataContext type contains methods that make it easier to perform transacted database updates in a fully typed fashion with the generated types.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="24dd1-213">Veritabanını güncellemek için</span><span class="sxs-lookup"><span data-stu-id="24dd1-213">To update the database</span></span>

1. <span data-ttu-id="24dd1-214">Aşağıdaki kodda birkaç satır veritabanına eklenir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-214">In the following code, several rows are added to the database.</span></span> <span data-ttu-id="24dd1-215">Yalnızca bir satır ekliyorsanız, kullanabileceğiniz `System.Data.Linq.Table.InsertOnSubmit()` eklemek için yeni satır belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="24dd1-215">If you are only adding a row, you can use `System.Data.Linq.Table.InsertOnSubmit()` to specify the new row to add.</span></span> <span data-ttu-id="24dd1-216">Birden çok satır ekliyorsanız, bunları bir toplama ve arama yerleştirdiğiniz `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span><span class="sxs-lookup"><span data-stu-id="24dd1-216">If you are inserting multiple rows, you should put them into a collection and call `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span></span> <span data-ttu-id="24dd1-217">Bu yöntemlerin her ikisi çağırdığınızda, veritabanı hemen değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="24dd1-217">When you call either of these methods, the database is not immediately changed.</span></span> <span data-ttu-id="24dd1-218">Çağırmalısınız `System.Data.Linq.DataContext.SubmitChanges` gerçekten değişiklikleri uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="24dd1-218">You must call `System.Data.Linq.DataContext.SubmitChanges` to actually commit the changes.</span></span> <span data-ttu-id="24dd1-219">Varsayılan olarak, önce yaptığınız her şey çağrı `System.Data.Linq.DataContext.SubmitChanges` dolaylı olarak aynı işlem bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="24dd1-219">By default, everything that you do before you call `System.Data.Linq.DataContext.SubmitChanges` is implicitly part of the same transaction.</span></span>

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

2. <span data-ttu-id="24dd1-220">Şimdi satırları silme işlemi çağırarak temizleyin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-220">Now clean up the rows by calling a delete operation.</span></span>

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

## <a name="executing-transact-sql-code"></a><span data-ttu-id="24dd1-221">Transact-SQL kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="24dd1-221">Executing Transact-SQL code</span></span>
<span data-ttu-id="24dd1-222">Ayrıca, doğrudan kullanarak Transact-SQL belirtebilirsiniz `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` yöntemi `DataContext` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="24dd1-222">You can also specify Transact-SQL directly by using the `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` method on the `DataContext` class.</span></span>


#### <a name="to-execute-custom-sql-commands"></a><span data-ttu-id="24dd1-223">Özel SQL komutlarını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="24dd1-223">To execute custom SQL commands</span></span>

<span data-ttu-id="24dd1-224">Aşağıdaki kod bir kaydı bir tabloya ekleme ve bir tablodan bir kaydı silmek için SQL komutlarının nasıl gönderileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-224">The following code shows how to send SQL commands to insert a record into a table and also to delete a record from a table.</span></span>

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

## <a name="using-the-full-data-context"></a><span data-ttu-id="24dd1-225">Tam veri bağlamı kullanarak</span><span class="sxs-lookup"><span data-stu-id="24dd1-225">Using the full data context</span></span>
<span data-ttu-id="24dd1-226">Önceki örneklerde, `GetDataContext` yöntemi ne adlı almak için kullanılan *Basitleştirilmiş veri bağlamı* veritabanı şeması için.</span><span class="sxs-lookup"><span data-stu-id="24dd1-226">In the previous examples, the `GetDataContext` method was used to get what is called the *simplified data context* for the database schema.</span></span> <span data-ttu-id="24dd1-227">Basitleştirilmiş veri bağlamı kullanılabilir olarak çok sayıda üye olmadığından sorgu oluşturma sırasında kullanmak daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="24dd1-227">The simplified data context is easier to use when you are constructing queries because there are not as many members available.</span></span> <span data-ttu-id="24dd1-228">Bu nedenle, IntelliSense özelliklerinde göz attığınızda, tabloları ve saklı yordamlar gibi veritabanı yapısına odaklanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dd1-228">Therefore, when you browse the properties in IntelliSense, you can focus on the database structure, such as the tables and stored procedures.</span></span> <span data-ttu-id="24dd1-229">Ancak, Basitleştirilmiş veri bağlamı ile neler yapabileceğiniz bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="24dd1-229">However, there is a limit to what you can do with the simplified data context.</span></span> <span data-ttu-id="24dd1-230">Diğer eylemleri gerçekleştirmenize olanak sağlayan bir tam veri bağlamı.</span><span class="sxs-lookup"><span data-stu-id="24dd1-230">A full data context that provides the ability to perform other actions.</span></span> <span data-ttu-id="24dd1-231">aynı zamanda kullanılabilir bu bulunan `ServiceTypes` ve adına sahip *DataContext* , sağladığınız, statik parametre.</span><span class="sxs-lookup"><span data-stu-id="24dd1-231">is also available This is located in the `ServiceTypes` and has the name of the *DataContext* static parameter if you provided it.</span></span> <span data-ttu-id="24dd1-232">Bunu sağlamadı ise veri içerik türünün adı diğer girişinize göre SqlMetal.exe tarafından sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24dd1-232">If you did not provide it, the name of the data context type is generated for you by SqlMetal.exe based on the other input.</span></span> <span data-ttu-id="24dd1-233">Tam veri bağlamı devraldığı `System.Data.Linq.DataContext` ve ADO.NET veri türlerine başvuruları gibi dahil olduğu temel sınıfın üyeleri ortaya koyar `Connection` nesnesi, gibi yöntemler `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` ve `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` SQL'de sorgular yazmak için kullanabilirsiniz ve işlemleri açıkça çalışmak için de anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-233">The full data context inherits from `System.Data.Linq.DataContext` and exposes the members of its base class, including references to ADO.NET data types such as the `Connection` object, methods such as `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` and `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` that you can use to write queries in SQL, and also a means to work with transactions explicitly.</span></span>


#### <a name="to-use-the-full-data-context"></a><span data-ttu-id="24dd1-234">Tam veri içeriği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="24dd1-234">To use the full data context</span></span>

<span data-ttu-id="24dd1-235">Aşağıdaki kodda, tam veri bağlamı nesneyi alıp doğrudan veritabanına karşı komutları yürütmek için kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-235">The following code demonstrates getting a full data context object and using it to execute commands directly against the database.</span></span> <span data-ttu-id="24dd1-236">Bu durumda, iki komut aynı işlemin bir parçası olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="24dd1-236">In this case, two commands are executed as part of the same transaction.</span></span>

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

## <a name="deleting-data"></a><span data-ttu-id="24dd1-237">Verileri silme</span><span class="sxs-lookup"><span data-stu-id="24dd1-237">Deleting data</span></span>
<span data-ttu-id="24dd1-238">Bu adım veri tablodan satırları silmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-238">This step shows you how to delete rows from a data table.</span></span>


#### <a name="to-delete-rows-from-the-database"></a><span data-ttu-id="24dd1-239">Satırları veritabanından silmek için</span><span class="sxs-lookup"><span data-stu-id="24dd1-239">To delete rows from the database</span></span>

<span data-ttu-id="24dd1-240">Şimdi, temiz satırları belirtilen tablodan, örneği satırları siler işlevi yazarak eklenen tüm `System.Data.Linq.Table` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="24dd1-240">Now, clean up any added rows by writing a function that deletes rows from a specified table, an instance of the `System.Data.Linq.Table` class.</span></span> <span data-ttu-id="24dd1-241">Ardından, silmek istediğiniz tüm satırları bulmak için bir sorgu yazın ve sorgu sonuçlarını kanal `deleteRows` işlevi.</span><span class="sxs-lookup"><span data-stu-id="24dd1-241">Then write a query to find all the rows that you want to delete, and pipe the results of the query into the `deleteRows` function.</span></span> <span data-ttu-id="24dd1-242">Bu kod işlev bağımsız değişkenleri, kısmi uygulama sağlama yeteneği yararlanır.</span><span class="sxs-lookup"><span data-stu-id="24dd1-242">This code takes advantage of the ability to provide partial application of function arguments.</span></span>

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

## <a name="creating-a-test-database"></a><span data-ttu-id="24dd1-243">Test veritabanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="24dd1-243">Creating a test database</span></span>
<span data-ttu-id="24dd1-244">Bu bölümde Bu anlatımda kullanmak için test veritabanını ayarlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-244">This section shows you how to set up the test database to use in this walkthrough.</span></span>

<span data-ttu-id="24dd1-245">Veritabanı şekilde değiştirirseniz, tür sağlayıcısı sıfırlamak sahip unutmayın.</span><span class="sxs-lookup"><span data-stu-id="24dd1-245">Note that if you alter the database in some way, you will have to reset the type provider.</span></span> <span data-ttu-id="24dd1-246">Tür sağlayıcısı sıfırlamak için yeniden oluşturmanız veya tür sağlayıcısı içeren projeyi temizleyin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-246">To reset the type provider, rebuild or clean the project that contains the type provider.</span></span>


#### <a name="to-create-the-test-database"></a><span data-ttu-id="24dd1-247">Test veritabanı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="24dd1-247">To create the test database</span></span>

1. <span data-ttu-id="24dd1-248">İçinde **Sunucu Gezgini**, kısayol menüsünü açın **veri bağlantıları** düğümünü ve **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="24dd1-248">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and choose **Add Connection**.</span></span> <span data-ttu-id="24dd1-249">**Bağlantı Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="24dd1-249">The **Add Connection** dialog box appears.</span></span>

2. <span data-ttu-id="24dd1-250">İçinde **sunucu adı** kutusunda, bir yönetim erişimine sahip SQL Server örneğinin adını belirtin veya bir sunucuya erişimi yoksa (localdb\v11.0) belirtin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-250">In the **Server name** box, specify the name of an instance of SQL Server that you have administrative access to, or if you do not have access to a server, specify (localdb\v11.0).</span></span> <span data-ttu-id="24dd1-251">SQL Express LocalDB geliştirme ve test makinenizde basit bir veritabanı sunucusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="24dd1-251">SQL Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="24dd1-252">Yeni bir düğüm oluşturulur **Sunucu Gezgini** altında **veri bağlantıları**.</span><span class="sxs-lookup"><span data-stu-id="24dd1-252">A new node is created in **Server Explorer** under **Data Connections**.</span></span> <span data-ttu-id="24dd1-253">Yerel veritabanı hakkında daha fazla bilgi için bkz: [izlenecek yol: Visual Studio'da yerel veritabanı dosyası oluşturma](https://msdn.microsoft.com/library/ms233763.aspx).</span><span class="sxs-lookup"><span data-stu-id="24dd1-253">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>

3. <span data-ttu-id="24dd1-254">Yeni bağlantı düğümü için kısayol menüsünü açın ve seçin **yeni sorgu**.</span><span class="sxs-lookup"><span data-stu-id="24dd1-254">Open the shortcut menu for the new connection node, and select **New Query**.</span></span>

4. <span data-ttu-id="24dd1-255">Aşağıdaki SQL betiğini kopyalayın, sorgu düzenleyicisine yapıştırın ve ardından **yürütme** araç çubuğunda düğmesini veya Ctrl + Shift + E anahtarları seçin.</span><span class="sxs-lookup"><span data-stu-id="24dd1-255">Copy the following SQL script, paste it into the query editor, and then choose the **Execute** button on the toolbar or choose the Ctrl+Shift+E keys.</span></span>

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


## <a name="see-also"></a><span data-ttu-id="24dd1-256">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24dd1-256">See Also</span></span>
[<span data-ttu-id="24dd1-257">Tür Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="24dd1-257">Type Providers</span></span>](index.md)

[<span data-ttu-id="24dd1-258">SqlDataConnection türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="24dd1-258">SqlDataConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[<span data-ttu-id="24dd1-259">İzlenecek yol: DBML dosyasından F # türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="24dd1-259">Walkthrough: Generating F# Types from a DBML File</span></span>](generating-fsharp-types-from-dbml.md)

[<span data-ttu-id="24dd1-260">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="24dd1-260">Query Expressions</span></span>](../../language-reference/query-expressions.md)

[<span data-ttu-id="24dd1-261">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="24dd1-261">LINQ to SQL</span></span>](../../../../docs/framework/data/adonet/sql/linq/index.md)

[<span data-ttu-id="24dd1-262">SqlMetal.exe &#40; Kod oluşturma Aracı &#41;</span><span class="sxs-lookup"><span data-stu-id="24dd1-262">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)
