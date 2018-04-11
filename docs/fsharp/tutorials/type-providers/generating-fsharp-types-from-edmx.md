---
title: 'İzlenecek yol: EDMX Şema Dosyasından F# Türleri Oluşturma (F#)'
description: 'F # türleri F # 3.0 şemanın bir .edmx dosyasının nerede belirtildiğinden, varlık veri modeli (EDM) tarafından gösterilen veriler için oluşturmayı öğrenin.'
keywords: 'Visual f #, f # işlevsel programlama'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 901457dce358f768b4f4c980703e09f6c744918e
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a><span data-ttu-id="b2fd0-104">İzlenecek yol: EDMX Şema Dosyasından F# Türleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2fd0-104">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>

> [!NOTE]
<span data-ttu-id="b2fd0-105">Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="b2fd0-106">Bkz: [FSharp.Data](https://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="b2fd0-107">API başvuru bağlantılar için MSDN götürür.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="b2fd0-108">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="b2fd0-109">Bu F# 3.0 için izlenecek yol size bir .edmx dosyası içinde belirtilen şema olan Varlık Veri Modeli (EDM) tarafından temsil edilen veri için türler oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-109">This walkthrough for F# 3.0 shows you how to create types for data that is represented by the Entity Data Model (EDM), the schema for which is specified in an .edmx file.</span></span> <span data-ttu-id="b2fd0-110">Bu izlenecek yol aynı zamanda EdmxFile tür sağlayıcısının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-110">This walkthrough also shows how to use the EdmxFile type provider.</span></span> <span data-ttu-id="b2fd0-111">Başlamadan önce, bir SqlEntityConnection tür sağlayıcısının daha uygun bir tür sağlayıcısı seçeneği olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-111">Before you begin, consider whether a SqlEntityConnection type provider is a more appropriate type provider option.</span></span> <span data-ttu-id="b2fd0-112">SqlEntityConnection tür sağlayıcısı projenizin geliştirme aşamasında bağlanabildiğiniz canlı bir veritabanına sahip olduğunuz, ve bağlantı dizesini derleme zamanında belirlemenizin sorun olmadığı senaryolarda en iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-112">The SqlEntityConnection type provider works best for scenarios where you have a live database that you can connect to during the development phase of your project, and you do not mind specifying the connection string at compile time.</span></span> <span data-ttu-id="b2fd0-113">Ancak, bu tür sağlayıcısı EdmxFile tür sağlayıcı kadar çok veritabanı işlevselliğini açığa çıkarmadığı için sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-113">However, this type provider is also limited in that it doesn't expose as much database functionality as the EdmxFile type provider.</span></span> <span data-ttu-id="b2fd0-114">Ayrıca, eğer Varlık Veri Modeli kullanan bir veritabanı için canlı bir veritabanı bağlantısına sahip değilseniz, .edmx dosyasını veritabanıyla kodlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-114">Also, if you don't have a live database connection for a database project that uses the Entity Data Model, you can use the .edmx file to code against the database.</span></span> <span data-ttu-id="b2fd0-115">EdmxFile tür sağlayıcısını kullandığınızda, F# derleyicisi sağladığı türleri üretmek için EdmGen.exe'yi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-115">When you use the EdmxFile type provider, the F# compiler runs EdmGen.exe to generate the types that it provides.</span></span>

<span data-ttu-id="b2fd0-116">Bu izlenecek yol, başarılı olması için bu sırayla gerçekleştirmeniz gereken aşağıdaki görevleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="b2fd0-116">This walkthrough illustrates the following tasks, which you must perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="b2fd0-117">Bir EDMX dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2fd0-117">Creating an EDMX file</span></span>
<br />

- <span data-ttu-id="b2fd0-118">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2fd0-118">Creating the project</span></span>
<br />

- <span data-ttu-id="b2fd0-119">Bulma veya oluşturma varlık veri modeli bağlantı dizesi</span><span class="sxs-lookup"><span data-stu-id="b2fd0-119">Finding or creating the entity data model connection string</span></span>
<br />

- <span data-ttu-id="b2fd0-120">Tür sağlayıcısını yapılandırma </span><span class="sxs-lookup"><span data-stu-id="b2fd0-120">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="b2fd0-121">Veriyi sorgulama</span><span class="sxs-lookup"><span data-stu-id="b2fd0-121">Querying the data</span></span>
<br />

- <span data-ttu-id="b2fd0-122">Bir saklı yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="b2fd0-122">Calling a stored procedure</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="b2fd0-123">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b2fd0-123">Prerequisites</span></span>

## <a name="creating-an-edmx-file"></a><span data-ttu-id="b2fd0-124">Bir EDMX dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2fd0-124">Creating an EDMX file</span></span>
<span data-ttu-id="b2fd0-125">Eğer bir EDMX dosyasına zaten sahipseniz, bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-125">If you already have an EDMX file, you can skip this step.</span></span>


#### <a name="to-create-an-edmx-file"></a><span data-ttu-id="b2fd0-126">Bir EDMX dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b2fd0-126">To create an EDMX file</span></span>

- <span data-ttu-id="b2fd0-127">Sistemin EDMX dosyası yoksa adımda bu kılavuzun sonunda yönergeleri izleyerek [varlık veri modeli yapılandırma](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span><span class="sxs-lookup"><span data-stu-id="b2fd0-127">If you don't already have an EDMX file, you can follow the instructions at the end of this walkthrough in the step [Configuring the Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span></span>
<br />

## <a name="creating-the-project"></a><span data-ttu-id="b2fd0-128">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2fd0-128">Creating the project</span></span>
<span data-ttu-id="b2fd0-129">Bu adımda, bir proje oluşturup EDMX tür sağlayıcısı kullanmak için gerekli başvuruları eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-129">In this step, you create a project and add appropriate references to it to use the EDMX type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="b2fd0-130">Bir F# projesi oluşturmak ve ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b2fd0-130">To create and set up an F# project</span></span>

1. <span data-ttu-id="b2fd0-131">Önceki projeyi kapatın, başka bir proje oluşturun, ve onu SchoolEDM olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-131">Close the previous project, create another project, and name it SchoolEDM.</span></span>
<br />

2. <span data-ttu-id="b2fd0-132">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-132">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="b2fd0-133">İçinde **derlemeleri** alanı seçin **Framework** düğümü.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-133">In the **Assemblies** area, choose the **Framework** node.</span></span>
<br />

4. <span data-ttu-id="b2fd0-134">Kullanılabilir derlemeleri listesinden seçip **System.Data.Entity** ve **System.Data.Linq** derlemeler ve ardından **Ekle** düğmesi bu başvuruları ekleyin derlemeleri projenize.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-134">In the list of available assemblies, choose the **System.Data.Entity** and **System.Data.Linq** assemblies, and then choose the **Add** button to add references to these assemblies to your project.</span></span>
<br />

5. <span data-ttu-id="b2fd0-135">İçinde **derlemeleri** alanında **uzantıları** düğümü.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-135">In the **Assemblies** area, select the **Extensions** node.</span></span>
<br />

6. <span data-ttu-id="b2fd0-136">Kullanılabilir uzantılar listesinde, FSharp.Data.TypeProviders derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-136">In the  list of available extensions, add a reference to the FSharp.Data.TypeProviders assembly.</span></span>
<br />

7. <span data-ttu-id="b2fd0-137">Uygun ad alanlarını açmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-137">Add the following code to open the appropriate namespaces.</span></span>
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="b2fd0-138">Varlık Veri Modeli için bağlantı dizesi bulma ya da oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2fd0-138">Finding or creating the connection string for the Entity Data Model</span></span>
<span data-ttu-id="b2fd0-139">Varlık Veri Modeli için bağlantı dizesi (EDMX bağlantı dizesi) veritabanı için bağlantı dizesinin yanı sıra ayrıca ek bilgi de içerir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-139">The connection string for the Entity Data Model (EDMX connection string) includes not only the connection string for the database provider but also additional information.</span></span> <span data-ttu-id="b2fd0-140">Örneğin, basit bir SQL Server veritabanı için EDMX bağlantı dizesi aşağıdaki koda benzer.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-140">For example, EDMX connection string for a simple SQL Server database resembles the following code.</span></span>

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

<span data-ttu-id="b2fd0-141">EDMX bağlantı dizeleri hakkında daha fazla bilgi için bkz: [bağlantı dizeleri](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="b2fd0-141">For more information about EDMX connection strings, see [Connection Strings](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="b2fd0-142">Varlık Veri Modeli için bağlantı dizesi bulmak ya da oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b2fd0-142">To find or create the connection string for the Entity Data Model</span></span>

1. <span data-ttu-id="b2fd0-143">EDMX bağlantı dizelerini elle üretmek zor olabilir, bu nedenle onu programlı olarak üretmek size zaman kazandırabilir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-143">EDMX connection strings can be difficult to generate by hand, so you can save time by generating it programmatically.</span></span> <span data-ttu-id="b2fd0-144">Eğer EDMX bağlantı dizenizi biliyorsanız, bu adımı atlayarak bir sonraki adımda o dizeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-144">If you know your EDMX connection string, you can bypass this step and simply use that string in the next step.</span></span> <span data-ttu-id="b2fd0-145">Aksi takdirde, sağladığınız bir veritabanı bağlantı dizesinden EDMX bağlantı dizesi üretmek için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-145">If not, use the following code to generate the EDMX connection string from a database connection string that you provide.</span></span>
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a><span data-ttu-id="b2fd0-146">Tür sağlayıcısını yapılandırma </span><span class="sxs-lookup"><span data-stu-id="b2fd0-146">Configuring the type provider</span></span>
<span data-ttu-id="b2fd0-147">Bu adımda, tür sağlayıcısını EDMX bağlantı dizesi ile oluşturur ve yapılandırırsınız, ve .edmx dosyası içinde tanımlanan şema için türler üretirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-147">In this step, you create and configure the type provider with the EDMX connection string, and you generate types for the schema that's defined in the .edmx file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="b2fd0-148">Tür sağlayıcısını yapılandırmak ve türleri üretmek için</span><span class="sxs-lookup"><span data-stu-id="b2fd0-148">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="b2fd0-149">Bu izlenecek yolun ilk adımında ürettiğiniz .edmx dosyasını proje dosyanız içine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-149">Copy the .edmx file that you generated in the first step of this walkthrough to your project folder.</span></span>
<br />

2. <span data-ttu-id="b2fd0-150">Açık F # projenize, proje düğümünün kısayol menüsünden seçin **varolan öğeyi Ekle**ve ardından .edmx dosyasının projenize eklemek için seçin.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-150">Open the shortcut menu for the project node in your F# project, choose **Add Existing Item**, and then choose the .edmx file to add it to your project.</span></span>
<br />

3. <span data-ttu-id="b2fd0-151">.edmx dosyanız için tür sağlayıcısını etkinleştirmek için aşağıdaki kodu girin.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-151">Enter the following code to activate the type provider for your .edmx file.</span></span> <span data-ttu-id="b2fd0-152">Değiştir *Server*\*örneği * SQL Server ve örneğinizin adını çalıştırır ve ilk adım, .edmx dosyasının adı Bu anlatımda kullanmak sunucunuzun adı.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-152">Replace *Server*\*Instance* with the name of your server that's running SQL Server and the name of your instance, and use the name of your .edmx file from the first step in this walkthrough.</span></span>
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a><span data-ttu-id="b2fd0-153">Veriyi sorgulama</span><span class="sxs-lookup"><span data-stu-id="b2fd0-153">Querying the data</span></span>
<span data-ttu-id="b2fd0-154">Bu adımda, veritabanını sorgulamak için F# sorgu iadelerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-154">In this step, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="b2fd0-155">Verileri sorgulamak için</span><span class="sxs-lookup"><span data-stu-id="b2fd0-155">To query the data</span></span>

- <span data-ttu-id="b2fd0-156">Varlık veri modeli içindeki veriyi sorgulamak için aşağıdaki kodu girin.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-156">Enter the following code to query the data in the entity data model.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="b2fd0-157">Bir saklı yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="b2fd0-157">Calling a stored procedure</span></span>
<span data-ttu-id="b2fd0-158">EDMX tür sağlayıcısını kullanarak saklı yordamları çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-158">You can call stored procedures by using the EDMX type provider.</span></span> <span data-ttu-id="b2fd0-159">Aşağıdaki yordamda, bir saklı yordam Okul veritabanını içeren **UpdatePerson**, bir kayıt belirtilen yeni sütunların değerlerini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-159">In the following procedure, the School database contains a stored procedure, **UpdatePerson**, which updates a record, given new values for the columns.</span></span> <span data-ttu-id="b2fd0-160">Bu saklı yordamı DataContext türü üzerinde bir yöntem olarak açığa çıkarıldığı için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-160">You can use this stored procedure because it's exposed as a method on the DataContext type.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="b2fd0-161">Bir saklı yordamı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b2fd0-161">To call a stored procedure</span></span>

- <span data-ttu-id="b2fd0-162">Kayıtları güncelleştirmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-162">Add the following code to update records.</span></span>
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

<span data-ttu-id="b2fd0-163">Eğer başarılı olursanız sonuç 1'dir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-163">The result is 1 if you succeed.</span></span> <span data-ttu-id="b2fd0-164">Dikkat **exactlyOne** sorgu ifadesinde bir sonuç yalnızca döndürülen; tersi durumda, bir özel durum sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-164">Notice that **exactlyOne** is used in the query expression to ensure that only one result is returned; otherwise, an exception is thrown.</span></span> <span data-ttu-id="b2fd0-165">Ayrıca, boş değer atanabilir değerleri ile daha kolay çalışmak için basit kullanabilirsiniz **boş değer atanabilir** boş değer atanabilir değer normal bir değer dışında oluşturmak için bu kodda tanımlanan işlevi.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-165">Also, to work with nullable values more easily, you can use the simple **nullable** function that's defined in this code to create a nullable value out of an ordinary value.</span></span>

<br />

## <a name="configuring-the-entity-data-model"></a><span data-ttu-id="b2fd0-166">Varlık Veri Modeli'ni yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b2fd0-166">Configuring the Entity Data Model</span></span>
<span data-ttu-id="b2fd0-167">Bu yordamı yalnızca bir veritabanından tam bir Varlık Veri Modeli üretmeyi öğrenmek istiyorsanız ve sınayacağınız bir veritabanınız yok ise tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-167">You should complete this procedure only if you want to know how to generate a full Entity Data Model from a database and you don't have a database with which to test.</span></span>


#### <a name="to-configure-the-entity-data-model"></a><span data-ttu-id="b2fd0-168">Varlık Veri Modeli'ni yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="b2fd0-168">To configure the Entity Data Model</span></span>

1. <span data-ttu-id="b2fd0-169">Menü çubuğunda seçin **SQL**, **Transact-SQL Düzenleyicisi**, **yeni sorgu** bir veritabanı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-169">On the menu bar, choose **SQL**, **Transact-SQL Editor**, **New Query** to create a database.</span></span> <span data-ttu-id="b2fd0-170">Eğer istenirse, veritabanı sunucunuzu ve örneğinizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-170">If prompted, specify your database server and instance.</span></span>
<br />

2. <span data-ttu-id="b2fd0-171">Bölümünde açıklandığı gibi öğrenci veritabanı oluşturur veritabanı komut dosyasının içeriğini yapıştırın [Entity Framework belgelerine](https://msdn.microsoft.com/data/JJ614587.aspx) veri Geliştirici Merkezi'nde.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-171">Copy and paste the contents of the database script that creates the Student database, as described in the [Entity Framework documentation](https://msdn.microsoft.com/data/JJ614587.aspx) in the Data Developer Center.</span></span>
<br />

3. <span data-ttu-id="b2fd0-172">Üçgen simgesiyle araç çubuğu düğmesini seçerek veya Ctrl + Q anahtarları seçme SQL komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-172">Run the SQL script by choosing the toolbar button with the triangle symbol or choosing the Ctrl+Q keys.</span></span>
<br />

4. <span data-ttu-id="b2fd0-173">İçinde **Sunucu Gezgini**, kısayol menüsünü açın **veri bağlantıları**, seçin **Bağlantı Ekle**ve ardından örnek adını veritabanı sunucusunun adını girin ve Okul veritabanı.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-173">In **Server Explorer**, open the shortcut menu for **Data Connections**, choose **Add Connection**, and then enter the name of the database server, the name of the instance name, and the School database.</span></span>
<br />

5. <span data-ttu-id="b2fd0-174">Bir C# veya Visual Basic konsol uygulama projesi oluşturun, kendi kısayol menüsünü açın, seçin **Yeni Öğe Ekle**ve ardından **ADO.NET varlık veri modeli**.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-174">Create a C# or Visual Basic Console Application project, open its shortcut menu, choose **Add New Item**, and then choose **ADO.NET Entity Data Model**.</span></span>
<br />  <span data-ttu-id="b2fd0-175">Varlık Veri Modeli Sihirbazı açılır.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-175">The Entity Data Model Wizard opens.</span></span> <span data-ttu-id="b2fd0-176">Bu sihirbazı kullanarak, Varlık Veri Modeli'ni nasıl oluşturmak istediğinizi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-176">By using this wizard, you can choose how you want to create the Entity Data Model.</span></span>
<br />

6. <span data-ttu-id="b2fd0-177">Altında **Model içeriği seçin**seçin **veritabanından Oluştur** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-177">Under **Choose Model Contents**, select the **Generate from database** check box.</span></span>
<br />

7. <span data-ttu-id="b2fd0-178">Sonraki sayfada, veri bağlantısı olarak yeni oluşturulan School veritabanınızı seçin.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-178">On the next page, choose your newly created School database as the data connection.</span></span>
<br />  <span data-ttu-id="b2fd0-179">Bu bağlantı benzemelidir  **&lt;servername&gt;.&lt; InstanceName&gt;. School.dbo**.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-179">This connection should resemble **&lt;servername&gt;.&lt;instancename&gt;.School.dbo**.</span></span>
<br />

8. <span data-ttu-id="b2fd0-180">Varlık bağlantı dizenizi Panoya kopyalayın çünkü bu dize daha sonra önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-180">Copy your entity connection string to the Clipboard because that string might be important later.</span></span>
<br />

9. <span data-ttu-id="b2fd0-181">Varlık bağlantı dizesi kaydetmek için onay kutusunu emin olun **App.Config** dosya seçilir ve daha sonra bağlantı dizesini bulun gerekirse yardımcı olması metin kutusunda dize değerini not edin.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-181">Make sure the check box to save the entity connection string to the **App.Config** file is selected, and make note of the string value in the text box, which should help you locate the connection string later, if needed.</span></span>
<br />

10. <span data-ttu-id="b2fd0-182">Sonraki sayfada seçin **tabloları** ve **saklı yordamları ve işlevleri**.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-182">On the next page, choose **Tables** and **Stored Procedures and Functions**.</span></span>
<br />  <span data-ttu-id="b2fd0-183">En üst düzey düğümlerini seçerek, tüm tabloları, saklı yordamları ve işlevleri seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-183">By choosing these top-level nodes, you choose all tables, stored procedures, and functions.</span></span> <span data-ttu-id="b2fd0-184">Eğer isterseniz bunları tek tek de seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-184">You can also choose these individually, if you want.</span></span>
<br />

11. <span data-ttu-id="b2fd0-185">Diğer seçenekler için onay kutularının seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-185">Make sure that the check boxes for the other settings are selected.</span></span>
<br />  <span data-ttu-id="b2fd0-186">İlk **Pluralize veya oluşturulan nesne adlarını tekil hale getirin** onay kutusu yoksa, veritabanı tablolarını temsil eden nesneler adlandırma kurallarını eşleştirmek için çoğul tekil forms değiştirmek gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-186">The first **Pluralize or singularize generated object names** check box indicates whether to change singular forms to plural to match conventions in naming objects that represent database tables.</span></span> <span data-ttu-id="b2fd0-187">**Yabancı anahtar sütunlarını modele dahil** onay kutusu amacı olduğu veritabanı şeması için oluşturulan nesne türleri diğer alanlara birleştirmek için alanları dahil edilip edilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-187">The **Include foreign key columns in the model** check box determines whether to include fields for which the purpose is to join to other fields in the object types that are generated for the database schema.</span></span> <span data-ttu-id="b2fd0-188">Üçüncü onay kutusu model içinde saklı yordamların ve işlevlerin içerilip içerilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-188">The third check box indicates whether to include stored procedures and functions in the model.</span></span>
<br />

12. <span data-ttu-id="b2fd0-189">Seçin **son** Okul veritabanını temel alan bir varlık veri modeli içeren bir .edmx dosyası oluşturmak için düğmesini.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-189">Select the **Finish** button to generate an .edmx file that contains an Entity Data Model that's based on the School database.</span></span>
<br />  <span data-ttu-id="b2fd0-190">Bir dosya **Model1.edmx**, projenize, eklenen ve bir veritabanı diyagramı görünür.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-190">A file, **Model1.edmx**, is added to your project, and a database diagram appears.</span></span>
<br />

13. <span data-ttu-id="b2fd0-191">Menü çubuğunda seçin **Görünüm**, **diğer pencereler**, **varlık veri modeli tarayıcısı** model tüm ayrıntılarını görüntülemek için veya **varlık veri modeli eşleme ayrıntıları**  oluşturulan nesne modeli veritabanı tabloları ve sütunları nasıl eşlendiğini gösteren bir penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-191">On the menu bar, choose **View**, **Other Windows**, **Entity Data Model Browser** to view all the details of the model or **Entity Data Model Mapping Details** to open a window that shows how the generated object model maps onto database tables and columns.</span></span>
<br />


## <a name="next-steps"></a><span data-ttu-id="b2fd0-192">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b2fd0-192">Next Steps</span></span>
<span data-ttu-id="b2fd0-193">Diğer sorgular içinde listelenen kullanılabilir sorgu işleçleri bakarak keşfedin [sorgu ifadeleri](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b2fd0-193">Explore other queries by looking at the available query operators as listed in [Query Expressions](../../language-reference/query-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="b2fd0-194">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2fd0-194">See Also</span></span>
[<span data-ttu-id="b2fd0-195">Tür Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="b2fd0-195">Type Providers</span></span>](index.md)

[<span data-ttu-id="b2fd0-196">EdmxFile türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="b2fd0-196">EdmxFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="b2fd0-197">İzlenecek yol: tür sağlayıcılarını ve varlıkları kullanarak SQL veritabanına erişme</span><span class="sxs-lookup"><span data-stu-id="b2fd0-197">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>](accessing-a-sql-database-entities.md)

[<span data-ttu-id="b2fd0-198">Varlık Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="b2fd0-198">Entity Framework</span></span>](https://msdn.microsoft.com/data/ef)

[<span data-ttu-id="b2fd0-199">.edmx dosyasının genel bakış</span><span class="sxs-lookup"><span data-stu-id="b2fd0-199">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[<span data-ttu-id="b2fd0-200">EDM Generator &#40;EdmGen.exe&#41;</span><span class="sxs-lookup"><span data-stu-id="b2fd0-200">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)

