---
title: "İzlenecek yol: DBML Dosyasından F# Türleri Oluşturma (F#)"
description: "Şema bilgileri .dbml dosyasında kodlanmış olduğunda F # 3.0 bir veritabanından veri için F # türleri oluşturmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: a919c2acb2b5b8c2ce93124f2f541bd092d15c35
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a><span data-ttu-id="8bec0-104">İzlenecek yol: DBML Dosyasından F# Türleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bec0-104">Walkthrough: Generating F# Types from a DBML File</span></span>

> [!NOTE]
<span data-ttu-id="8bec0-105">Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8bec0-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="8bec0-106">Bkz: [FSharp.Data](http://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.</span><span class="sxs-lookup"><span data-stu-id="8bec0-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="8bec0-107">API başvuru bağlantılar için MSDN götürür.</span><span class="sxs-lookup"><span data-stu-id="8bec0-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="8bec0-108">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="8bec0-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="8bec0-109">Bu kılavuz F # 3.0 için şema bilgileri .dbml dosyasında kodlanmış varsa, bir veritabanından veri türlerinde oluşturun açıklar.</span><span class="sxs-lookup"><span data-stu-id="8bec0-109">This walkthrough for F# 3.0 describes how to create types for data from a database when you have schema information encoded in a .dbml file.</span></span> <span data-ttu-id="8bec0-110">LINQ-SQL veritabanı şemasını temsil etmek için bu dosya biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8bec0-110">LINQ to SQL uses this file format to represent database schema.</span></span> <span data-ttu-id="8bec0-111">Visual Studio'da (O/R) Nesne İlişkisel Tasarımcısı'nı kullanarak, bir LINQ to SQL şema dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bec0-111">You can generate a LINQ to SQL schema file in Visual Studio by using the Object Relational (O/R) Designer.</span></span> <span data-ttu-id="8bec0-112">Daha fazla bilgi için bkz: [O/R Tasarımcısı genel bakış](https://msdn.microsoft.com/library/bb384511.aspx) ve [LINQ-SQL kod oluşturma](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="8bec0-112">For more information, see [O/R Designer Overview](https://msdn.microsoft.com/library/bb384511.aspx) and [Code Generation in LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>

<span data-ttu-id="8bec0-113">Veritabanı işaretleme dili (DBML) türü sağlayıcısı, derleme zamanında statik bağlantı dizesini belirtmek gerek kalmadan veritabanı şemasını temel alan türlerini kullanan kod yazmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bec0-113">The Database Markup Language (DBML) type provider allows you to write code that uses types based on a database schema without requiring you to specify a static connection string at compile time.</span></span> <span data-ttu-id="8bec0-114">Son uygulama farklı bir veritabanı, farklı kimlik bilgileri veya farklı bağlantı dizesi birden uygulama geliştirmek için kullandığınız kullanacağını olasılığı için izin vermeniz gerekiyorsa, yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8bec0-114">That can be useful if you need to allow for the possibility that the final application will use a different database, different credentials, or a different connection string than the one you use to develop the application.</span></span> <span data-ttu-id="8bec0-115">Derleme zamanında kullanabileceğiniz doğrudan veritabanı bağlantısı varsa ve aynı veritabanı ve yerleşik uygulamanızda sonunda kullanacağı kimlik bilgilerini budur SQLDataConnection türü sağlayıcısı de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bec0-115">If you have a direct database connection that you can use at compile time and this is the same database and credentials that you will eventually use in your built application, you can also use the SQLDataConnection type provider.</span></span> <span data-ttu-id="8bec0-116">Daha fazla bilgi için bkz: [izlenecek yol: tür sağlayıcılarını kullanarak tarafından SQL veritabanına erişme](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="8bec0-116">For more information, see [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>

<span data-ttu-id="8bec0-117">Bu kılavuz aşağıdaki görevler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8bec0-117">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="8bec0-118">Bu sırada başarılı olması gözden geçirme tamamlanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8bec0-118">They should be completed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="8bec0-119">.Dbml dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bec0-119">Creating a .dbml file</span></span>
<br />

- <span data-ttu-id="8bec0-120">Oluşturma ve F # projesinde ayarlama</span><span class="sxs-lookup"><span data-stu-id="8bec0-120">Creating and setting up an F# project</span></span>
<br />

- <span data-ttu-id="8bec0-121">Tür sağlayıcısı yapılandırma ve türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bec0-121">Configuring the type provider and generating the types</span></span>
<br />

- <span data-ttu-id="8bec0-122">Veritabanını sorgulama</span><span class="sxs-lookup"><span data-stu-id="8bec0-122">Querying the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="8bec0-123">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8bec0-123">Prerequisites</span></span>

## <a name="creating-a-dbml-file"></a><span data-ttu-id="8bec0-124">.Dbml dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bec0-124">Creating a .dbml file</span></span>
<span data-ttu-id="8bec0-125">Üzerinde test etmek için bir veritabanı yoksa, ekranın alt kısmındaki yönergeleri izleyerek oluşturun [izlenecek yol: tür sağlayıcılarını kullanarak tarafından SQL veritabanına erişme](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="8bec0-125">If you do not have a database to test on, create one by following the instructions at the bottom of [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span> <span data-ttu-id="8bec0-126">Bu yönergeleri izleyin, birkaç basit tabloları ve saklı yordamlar SQL Server'ınızdaki içeren Veritabanım adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bec0-126">If you follow these instructions, you will create a database called MyDatabase that contains a few simple tables and stored procedures on your SQL Server.</span></span>

<span data-ttu-id="8bec0-127">Bir .dbml dosyası zaten varsa bölümüne atlayabilirsiniz **oluşturma ve ayarlama bir F # projeyi**.</span><span class="sxs-lookup"><span data-stu-id="8bec0-127">If you already have a .dbml file, you can skip to the section, **Create and Set Up an F# Project**.</span></span> <span data-ttu-id="8bec0-128">Aksi takdirde, var olan bir SQL veritabanını belirtilen bir .dbml dosyası oluşturun ve komut satırı kullanarak SqlMetal.exe aracı.</span><span class="sxs-lookup"><span data-stu-id="8bec0-128">Otherwise, you can create a .dbml file given an existing SQL database and by using the command-line tool SqlMetal.exe.</span></span>


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a><span data-ttu-id="8bec0-129">SqlMetal.exe kullanarak bir .dbml dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8bec0-129">To create a .dbml file by using SqlMetal.exe</span></span>

1. <span data-ttu-id="8bec0-130">Açık bir **Geliştirici komut istemi**.</span><span class="sxs-lookup"><span data-stu-id="8bec0-130">Open a **Developer Command Prompt**.</span></span>
<br />

2. <span data-ttu-id="8bec0-131">Girerek SqlMetal.exe erişimi olduğundan emin olun `SqlMetal.exe /?` komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="8bec0-131">Ensure that you have access to SqlMetal.exe by entering `SqlMetal.exe /?` at the command prompt.</span></span> <span data-ttu-id="8bec0-132">SqlMetal.exe altında yüklü genellikle **Microsoft SDKs** klasöründe **Program Files** veya **Program Files (x86)**.</span><span class="sxs-lookup"><span data-stu-id="8bec0-132">SqlMetal.exe is typically installed under the **Microsoft SDKs** folder in **Program Files** or **Program Files (x86)**.</span></span>
<br />

3. <span data-ttu-id="8bec0-133">SqlMetal.exe aşağıdaki komut satırı seçenekleriyle çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8bec0-133">Run SqlMetal.exe with the following command-line options.</span></span> <span data-ttu-id="8bec0-134">Uygun bir yol yerine alternatif `c:\destpath` .dbml dosyası oluşturun ve veritabanı sunucusu için uygun değerleri eklemek için adını ve veritabanı adını örneği.</span><span class="sxs-lookup"><span data-stu-id="8bec0-134">Substitute an appropriate path in place of `c:\destpath` to create the .dbml file, and insert appropriate values for the database server, instance name, and database name.</span></span>
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
<span data-ttu-id="8bec0-135">SqlMetal.exe izin sorunları nedeniyle dosya oluştururken sorun varsa, yazma erişimine sahip bir klasör için geçerli dizini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8bec0-135">If SqlMetal.exe has trouble creating the file due to permissions issues, change the current directory to a folder that you have write access to.</span></span>


4. <span data-ttu-id="8bec0-136">Ayrıca, diğer kullanılabilir komut satırı seçenekleri da bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bec0-136">You can also look at the other available command-line options.</span></span> <span data-ttu-id="8bec0-137">Örneğin, görünümler ve oluşturulan türler dahil SQL işlevleri istiyorsanız kullanabileceğiniz seçenekleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8bec0-137">For example, there are options you can use if you want views and SQL functions included in the generated types.</span></span> <span data-ttu-id="8bec0-138">Daha fazla bilgi için bkz: [SqlMetal.exe &#40; Kod oluşturma Aracı &#41; ](https://msdn.microsoft.com/library/bb386987).</span><span class="sxs-lookup"><span data-stu-id="8bec0-138">For more information, see [SqlMetal.exe &#40;Code Generation Tool&#41;](https://msdn.microsoft.com/library/bb386987).</span></span>
<br />


## <a name="creating-and-setting-up-an-f-project"></a><span data-ttu-id="8bec0-139">Oluşturma ve F # projesinde ayarlama</span><span class="sxs-lookup"><span data-stu-id="8bec0-139">Creating and setting up an F# project</span></span>
<span data-ttu-id="8bec0-140">Bu adımda, bir proje oluşturun ve DBML türü sağlayıcısı kullanmak için uygun başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bec0-140">In this step, you create a project and add appropriate references to use the DBML type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="8bec0-141">Bir F# projesi oluşturmak ve ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8bec0-141">To create and set up an F# project</span></span>

1. <span data-ttu-id="8bec0-142">Yeni bir F # konsol uygulaması projesi çözümünüze ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bec0-142">Add a new F# Console Application project to your solution.</span></span>
<br />

2. <span data-ttu-id="8bec0-143">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8bec0-143">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="8bec0-144">İçinde **derlemeleri** alanı seçin **Framework** düğümü ve ardından kullanılabilir derlemeleri listesinden seçip **System.Data** ve **System.Data.Linq**  derlemeler.</span><span class="sxs-lookup"><span data-stu-id="8bec0-144">In the **Assemblies** area, choose the **Framework** node, and then, in the list of available assemblies, choose the **System.Data** and **System.Data.Linq** assemblies.</span></span>
<br />

4. <span data-ttu-id="8bec0-145">İçinde **derlemeleri** alanı seçin **uzantıları**ve ardından kullanılabilir derlemeleri listesinden seçip **FSharp.Data.TypeProviders**.</span><span class="sxs-lookup"><span data-stu-id="8bec0-145">In the **Assemblies** area, choose **Extensions**, and then, in the list of available assemblies, choose **FSharp.Data.TypeProviders**.</span></span>
<br />

5. <span data-ttu-id="8bec0-146">Seçin **Tamam** düğmesi bu derlemeler başvuruları projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bec0-146">Choose the **OK** button to add references to these assemblies to your project.</span></span>
<br />

6. <span data-ttu-id="8bec0-147">(İsteğe bağlı).</span><span class="sxs-lookup"><span data-stu-id="8bec0-147">(Optional).</span></span> <span data-ttu-id="8bec0-148">Önceki adımda oluşturduğunuz .dbml dosyasını kopyalayın ve dosyayı projeniz için ana klasörü yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="8bec0-148">Copy the .dbml file that you created in the previous step, and paste the file in the main folder for your project.</span></span> <span data-ttu-id="8bec0-149">Bu klasör, proje dosyası (.fsproj) ve kod dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="8bec0-149">This folder contains the project file (.fsproj) and code files.</span></span> <span data-ttu-id="8bec0-150">Menü çubuğunda seçin **proje**, **varolan öğeyi Ekle**ve ardından projenize eklemek için .dbml dosyasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="8bec0-150">On the menu bar, choose **Project**, **Add Existing Item**, and then specify the .dbml file to add it to your project.</span></span> <span data-ttu-id="8bec0-151">Bu adımları tamamladıktan sonraki adımda ResolutionFolder statik parametresinin kullanmayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bec0-151">If you complete these steps, you can omit the ResolutionFolder static parameter in the next step.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="8bec0-152">Tür sağlayıcısını yapılandırma </span><span class="sxs-lookup"><span data-stu-id="8bec0-152">Configuring the type provider</span></span>
<span data-ttu-id="8bec0-153">Bu bölümde, tür sağlayıcısı oluşturun ve .dbml dosyasında tanımlanan şemasından türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bec0-153">In this section, you create a type provider and generate types from the schema that’s described in the .dbml file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a><span data-ttu-id="8bec0-154">Tür sağlayıcısı yapılandırmak ve türleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8bec0-154">To configure the type provider and generate the types</span></span>

- <span data-ttu-id="8bec0-155">Açılır kodu ekleyin **TypeProviders** ad alanı ve kullanmak istediğiniz .dbml dosyası için tür sağlayıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="8bec0-155">Add code that opens the **TypeProviders** namespace and instantiates the type provider for the .dbml file that you want to use.</span></span> <span data-ttu-id="8bec0-156">Projenize .dbml dosyası eklediyseniz, ResolutionFolder statik parametreyi atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bec0-156">If you added the .dbml file to your project, you can omit the ResolutionFolder static parameter.</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

<span data-ttu-id="8bec0-157">DataContext türü oluşturulan tüm türleri için erişim sağlar ve devraldığı `System.Data.Linq.DataContext`.</span><span class="sxs-lookup"><span data-stu-id="8bec0-157">The DataContext type provides access to all the generated types and inherits from `System.Data.Linq.DataContext`.</span></span> <span data-ttu-id="8bec0-158">DbmlFile türü sağlayıcısı ayarlayabileceğiniz çeşitli statik parametre yok.</span><span class="sxs-lookup"><span data-stu-id="8bec0-158">The DbmlFile type provider has various static parameters that you can set.</span></span> <span data-ttu-id="8bec0-159">Örneğin, DataContext türü için farklı bir ad belirterek kullanabileceğiniz `DataContext=MyDataContext`.</span><span class="sxs-lookup"><span data-stu-id="8bec0-159">For example, you can use a different name for the DataContext type by specifying `DataContext=MyDataContext`.</span></span> <span data-ttu-id="8bec0-160">Bu durumda, kodunuzu aşağıdaki örneğe benzer:</span><span class="sxs-lookup"><span data-stu-id="8bec0-160">In that case, your code resembles the following example:</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a><span data-ttu-id="8bec0-161">Veritabanını sorgulama</span><span class="sxs-lookup"><span data-stu-id="8bec0-161">Querying the database</span></span>
<span data-ttu-id="8bec0-162">Bu bölümde, veritabanını sorgulamak için F # sorgu ifadeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="8bec0-162">In this section, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="8bec0-163">Verileri sorgulamak için</span><span class="sxs-lookup"><span data-stu-id="8bec0-163">To query the data</span></span>

- <span data-ttu-id="8bec0-164">Veritabanını sorgulamak için kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bec0-164">Add code to query the database.</span></span>
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a><span data-ttu-id="8bec0-165">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="8bec0-165">Next Steps</span></span>
<span data-ttu-id="8bec0-166">Diğer sorgu ifadeleri kullanın veya bir veritabanı bağlantısı veri bağlamından almak ve normal ADO.NET veri işlemleri gerçekleştirmek için devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bec0-166">You can proceed to use other query expressions, or get a database connection from the data context and perform normal ADO.NET data operations.</span></span> <span data-ttu-id="8bec0-167">İçindeki "Sorgu veri sonra" için ek adımlar, bölümlere bakın [izlenecek yol: tür sağlayıcılarını kullanarak tarafından SQL veritabanına erişme](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="8bec0-167">For additional steps, see the sections after "Query the Data" in [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="8bec0-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bec0-168">See Also</span></span>
[<span data-ttu-id="8bec0-169">DbmlFile türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8bec0-169">DbmlFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="8bec0-170">Tür sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="8bec0-170">Type Providers</span></span>](index.md)

[<span data-ttu-id="8bec0-171">İzlenecek yol: tür sağlayıcılarını kullanarak SQL veritabanına erişme</span><span class="sxs-lookup"><span data-stu-id="8bec0-171">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>](accessing-a-sql-database.md)

[<span data-ttu-id="8bec0-172">SqlMetal.exe &#40; Kod oluşturma Aracı &#41;</span><span class="sxs-lookup"><span data-stu-id="8bec0-172">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)

[<span data-ttu-id="8bec0-173">Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="8bec0-173">Query Expressions</span></span>](../../language-reference/query-expressions.md)
