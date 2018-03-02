---
title: "İzlenecek yol: Tür Sağlayıcılarını ve Varlıkları Kullanarak SQL Veritabanına Erişim (F#)"
description: "ADO.NET varlık veri modeli F # 3.0 dayalı bir SQL veritabanı için yazılan veri erişim öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: 153050f27ade0152741bdc2d77ab85eefa8418e9
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a><span data-ttu-id="2aaa8-104">İzlenecek yol: Tür Sağlayıcılarını ve Varlıkları Kullanarak SQL Veritabanına Erişim</span><span class="sxs-lookup"><span data-stu-id="2aaa8-104">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>

> [!NOTE]
<span data-ttu-id="2aaa8-105">Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="2aaa8-106">Bkz: [FSharp.Data](https://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="2aaa8-107">API başvuru bağlantılar için MSDN götürür.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="2aaa8-108">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="2aaa8-109">Bu F# 3.0 için izlenecek yol size ADO.NET Varlık Veri Modeli'ni temel alan bir SQL veritabanı için türlü veriye nasıl erişeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-109">This walkthrough for F# 3.0 shows you how to access typed data for a SQL database based on the ADO.NET Entity Data Model.</span></span> <span data-ttu-id="2aaa8-110">Bu kılavuzda F # ayarlanacağı gösterilmiştir `SqlEntityConnection` bir SQL veritabanı, veri sorguları yazma, veritabanı üzerinde saklı yordamları çağırmak nasıl yanı sıra bazı ADO.NET Entity Framework türleri ve yöntemleri upd için nasıl kullanıldığını ile kullanmak için tür sağlayıcısı Veritabanı tarih.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-110">This walkthrough shows you how to set up the F# `SqlEntityConnection` type provider for use with a SQL database, how to write queries against the data, how to call stored procedures on the database, as well as how to use some of the ADO.NET Entity Framework types and methods to update the database.</span></span>

<span data-ttu-id="2aaa8-111">Bu izlenecek yol, başarılı olması için bu sırayla gerçekleştirmeniz gereken aşağıdaki görevleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="2aaa8-111">This walkthrough illustrates the following tasks, which you should perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="2aaa8-112">School veritabanını oluşturma</span><span class="sxs-lookup"><span data-stu-id="2aaa8-112">Create the School database</span></span>
<br />

- <span data-ttu-id="2aaa8-113">Bir F# projesi oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2aaa8-113">Create and configure an F# project</span></span>
<br />

- <span data-ttu-id="2aaa8-114">Tür sağlayıcısı yapılandırmak ve varlık veri modeli bağlanmak</span><span class="sxs-lookup"><span data-stu-id="2aaa8-114">Configure the type provider and connect to the Entity Data Model</span></span>
<br />

- <span data-ttu-id="2aaa8-115">Veritabanı sorgulama</span><span class="sxs-lookup"><span data-stu-id="2aaa8-115">Query the database</span></span>
<br />

- <span data-ttu-id="2aaa8-116">Veritabanını güncelleme</span><span class="sxs-lookup"><span data-stu-id="2aaa8-116">Updating the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="2aaa8-117">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2aaa8-117">Prerequisites</span></span>
<span data-ttu-id="2aaa8-118">Bu adımları tamamlamak için üzerinde bir veritabanı oluşturabileceğiniz SQL Server çalıştıran bir sunucuya erişiminiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-118">You must have access to a server that's running SQL Server where you can create a database to complete these steps.</span></span>

## <a name="create-the-school-database"></a><span data-ttu-id="2aaa8-119">School veritabanını oluşturma</span><span class="sxs-lookup"><span data-stu-id="2aaa8-119">Create the School database</span></span>
<span data-ttu-id="2aaa8-120">School veritabanını SQL Server çalıştıran ve yönetimsel erişiminiz olan herhangi bir sunucu üzerinde oluşturabilir ya da LocalDB kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-120">You can create the School database on any server that's running SQL Server to which you have administrative access, or you can use LocalDB.</span></span>


#### <a name="to-create-the-school-database"></a><span data-ttu-id="2aaa8-121">School veritabanını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2aaa8-121">To create the School database</span></span>

1. <span data-ttu-id="2aaa8-122">İçinde **Sunucu Gezgini**, kısayol menüsünü açın **veri bağlantıları** düğümünü ve ardından **Bağlantı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-122">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and then choose **Add Connection**.</span></span>
<br />  <span data-ttu-id="2aaa8-123">**Bağlantı Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-123">The **Add Connection** dialog box appears.</span></span>
<br />

2. <span data-ttu-id="2aaa8-124">İçinde **sunucu adı** kutusuna olan yönetim erişimi SQL Server örneği adı belirtin veya bir sunucuya erişimi yoksa (localdb\v11.0) belirtin.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-124">In the **Server name** box, specify the name of an instance of SQL Server to which you have administrative access, or specify (localdb\v11.0) if you don't have access to a server.</span></span>
<br />  <span data-ttu-id="2aaa8-125">SQL Server Express LocalDB makineniz üzerinde geliştirme ve sınama için bir hafif veritabanı sunucusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-125">SQL Server Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="2aaa8-126">Yerel veritabanı hakkında daha fazla bilgi için bkz: [izlenecek yol: Visual Studio'da yerel veritabanı dosyası oluşturma](https://msdn.microsoft.com/library/ms233763.aspx).</span><span class="sxs-lookup"><span data-stu-id="2aaa8-126">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>
<br />  <span data-ttu-id="2aaa8-127">Yeni bir düğüm oluşturulur **Sunucu Gezgini** altında **veri bağlantıları**.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-127">A new node is created in **Server Explorer** under **Data Connections**.</span></span>
<br />

3. <span data-ttu-id="2aaa8-128">Yeni bağlantı düğümü için kısayol menüsünü açın ve ardından **yeni sorgu**.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-128">Open the shortcut menu for the new connection node, and then choose **New Query**.</span></span>
<br />

4. <span data-ttu-id="2aaa8-129">Açık [Okul örnek veritabanı oluşturma](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx) Microsoft Web sitesine gidin ve ardından Kopyala ve Yapıştır üzerinde veritabanı betiği Okul Veritabanı Düzenleyicisi penceresine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-129">Open [Creating the School Sample Database](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx) on the Microsoft website, and then copy and paste the database script that creates the School database into the editor window.</span></span>
<br />


## <span data-ttu-id="2aaa8-130"><a name="BKMK_CreateConfigFSProj"></a></span><span class="sxs-lookup"><span data-stu-id="2aaa8-130"><a name="BKMK_CreateConfigFSProj"> </a></span></span>

## <a name="create-and-configure-an-f-project"></a><span data-ttu-id="2aaa8-131">Bir F# projesi oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2aaa8-131">Create and configure an F# project</span></span>
<span data-ttu-id="2aaa8-132">Bu adımda, bir proje oluşturursunuz ve onu bir tür sağlayıcısı kullanması için ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-132">In this step, you create a project and set it up to use a type provider.</span></span>


#### <a name="to-create-and-configure-an-f-project"></a><span data-ttu-id="2aaa8-133">Bir F# projesi oluşturmak ve yapılandırmak için:</span><span class="sxs-lookup"><span data-stu-id="2aaa8-133">To create and configure an F# project</span></span>

1. <span data-ttu-id="2aaa8-134">Önceki projeyi kapatın, başka bir proje oluşturun ve adlandırın **SchoolEDM**.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-134">Close the previous project, create another project, and name it **SchoolEDM**.</span></span>
<br />

2. <span data-ttu-id="2aaa8-135">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-135">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="2aaa8-136">Seçin **Framework** düğümünü ve ardından **Framework** listesinde, seçin **System.Data**, **System.Data.Entity**ve **System.Data.Linq**.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-136">Choose the **Framework** node, and then, in the **Framework** list, choose **System.Data**, **System.Data.Entity**,  and **System.Data.Linq**.</span></span>
<br />

4. <span data-ttu-id="2aaa8-137">Seçin **uzantıları** düğümü, bir başvuru ekleyin [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) derleme ve ardından **Tamam** düğmesi iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-137">Choose the **Extensions** node, add a reference to the [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) assembly, and then choose the **OK** button to dismiss the dialog box.</span></span>
<br />

5. <span data-ttu-id="2aaa8-138">Bir iç modül tanımlamak ve uygun ad alanlarını açmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2aaa8-138">Add the following code to define an internal module and open appropriate namespaces.</span></span> <span data-ttu-id="2aaa8-139">Tür sağlayıcısı türleri yalnızca bir özel ya da iç ad alanına ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-139">The type provider can inject types only into a private or internal namespace.</span></span>
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. <span data-ttu-id="2aaa8-140">Bu izlenecek adımları yerine komut dosyası olarak derlenmiş bir program olarak etkileşimli olarak kodu çalıştırmak için proje düğümünün kısayol menüsünü açın, seçin **Yeni Öğe Ekle**bir F # komut dosyası ekleyin ve sonra kodu her adımda komut dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-140">To run the code in this walkthrough interactively as a script instead of as a compiled program, open the shortcut menu for the project node, choose **Add New Item**, add an F# script file, and then add the code in each step to the script.</span></span> <span data-ttu-id="2aaa8-141">Derleme başvurularını yüklemek için, aşağıdaki satırları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-141">To load the assembly references, add the following lines.</span></span>
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. <span data-ttu-id="2aaa8-142">Her kod bloğunu ekledikçe vurgulayın, ve Alt + Enter tuşlarını seçerek F# Interactive içinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-142">Highlight each block of code as you add it, and choose the Alt + Enter keys to run it in F# Interactive.</span></span>
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="2aaa8-143">Tür sağlayıcısını yapılandırma ve Varlık Veri Modeli'ne bağlanma</span><span class="sxs-lookup"><span data-stu-id="2aaa8-143">Configure the type provider, and connect to the Entity Data Model</span></span>
<span data-ttu-id="2aaa8-144">Bu adımda, bir veri bağlantısı ile bir tür sağlayıcısı ayarlarsınız ve veriyle çalışmanıza olanak veren bir veri bağlamı elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-144">In this step, you set up a type provider with a data connection and obtain a data context that allows you to work with data.</span></span>


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="2aaa8-145">Tür sağlayıcısını yapılandırmak ve Varlık Veri Modeli'ne bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="2aaa8-145">To configure the type provider, and connect to the Entity Data Model</span></span>

1. <span data-ttu-id="2aaa8-146">Yapılandırmak için aşağıdaki kodu girin `SqlEntityConnection` F # türleri oluşturur türü sağlayıcısı temel varlık veri modeli üzerinde önceden oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-146">Enter the following code to configure the `SqlEntityConnection` type provider that generates F# types based on the Entity Data Model that you created previously.</span></span> <span data-ttu-id="2aaa8-147">Tam EDMX bağlantı dizesi yerine, yalnızca SQL bağlantı dizesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-147">Instead of the full EDMX connection string, use only the SQL connection string.</span></span>
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  <span data-ttu-id="2aaa8-148">Bu eylem daha önce oluşturduğunuz veritabanı bağlantısı ile bir tür sağlayıcısı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-148">This action sets up a type provider with the database connection that you created earlier.</span></span> <span data-ttu-id="2aaa8-149">Özellik `MultipleActiveResultSets` bu özellik veritabanında bir ADO.NET Entity Framework kod içinde sık oluşabilir bir bağlantı zaman uyumsuz olarak yürütmek birden çok komut verdiğinden ADO.NET Entity Framework kullandığınızda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-149">The property `MultipleActiveResultSets` is needed when you use the ADO.NET Entity Framework because this property allows multiple commands to execute asynchronously on the database in one connection, which can occur frequently in ADO.NET Entity Framework code.</span></span> <span data-ttu-id="2aaa8-150">Daha fazla bilgi için bkz: [birden fazla etkin sonuç kümeleri (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span><span class="sxs-lookup"><span data-stu-id="2aaa8-150">For more information, see [Multiple Active Result Sets (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span></span>
<br />

2. <span data-ttu-id="2aaa8-151">Veritabanı tablolarını özellikler olarak ve veritabanı saklı yordamlarını ve işlevlerini yöntemler olarak içeren bir nesne olan veri bağlamını alın.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-151">Get the data context, which is an object that contains the database tables as properties and the database stored procedures and functions as methods.</span></span>
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a><span data-ttu-id="2aaa8-152">Veritabanını sorgulama</span><span class="sxs-lookup"><span data-stu-id="2aaa8-152">Querying the database</span></span>
<span data-ttu-id="2aaa8-153">Bu adımda, veritabanı üzerinde çeşitli sorguları yürütmek için F# sorgu ifadelerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-153">In this step, you use F# query expressions to execute various queries on the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="2aaa8-154">Verileri sorgulamak için</span><span class="sxs-lookup"><span data-stu-id="2aaa8-154">To query the data</span></span>

- <span data-ttu-id="2aaa8-155">Varlık veri modelinden veriyi sorgulamak için aşağıdaki kodu girin.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-155">Enter the following code to query the data from the entity data model.</span></span> <span data-ttu-id="2aaa8-156">Veri tabanı tablosu Course'u Courses olarak ve Person'ı People olarak çeviren Pluralize = true etkisine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-156">Note the effect of Pluralize = true, which changes the database table Course to Courses and Person to People.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a><span data-ttu-id="2aaa8-157">Veritabanını güncelleme</span><span class="sxs-lookup"><span data-stu-id="2aaa8-157">Updating the database</span></span>
<span data-ttu-id="2aaa8-158">Veritabanını güncellemek için, Varlık Çerçevesi sınıflarını ve yöntemlerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-158">To update the database, you use the Entity Framework classes and methods.</span></span> <span data-ttu-id="2aaa8-159">SQLEntityConnection tür sağlayıcısı ile iki tür veri bağlamı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-159">You can use two types of data context with the SQLEntityConnection type provider.</span></span> <span data-ttu-id="2aaa8-160">İlk olarak, `ServiceTypes.SimpleDataContextTypes.EntityContainer` veritabanı tabloları ve sütunları temsil eden sağlanan özellikler içeren Basitleştirilmiş veri bağlamı.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-160">First, `ServiceTypes.SimpleDataContextTypes.EntityContainer` is the simplified data context, which includes only the provided properties that represent database tables and columns.</span></span> <span data-ttu-id="2aaa8-161">İkinci olarak, tam veri bağlamı Entity Framework sınıfının bir örneği olan `System.Data.Objects.ObjectContext`, yöntemi içeren `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` veritabanına satırları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-161">Second, the full data context is an instance of the Entity Framework class `System.Data.Objects.ObjectContext`, which contains the method `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` to add rows to the database.</span></span> <span data-ttu-id="2aaa8-162">Varlık Çerçevesi tabloları ve aralarındaki ilişkiyi tanır, ve böylece veritabanı tutarlılığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-162">The Entity Framework recognizes the tables and the relationships between them, so it enforces database consistency.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="2aaa8-163">Veritabanını güncellemek için</span><span class="sxs-lookup"><span data-stu-id="2aaa8-163">To update the database</span></span>

1. <span data-ttu-id="2aaa8-164">Aşağıdaki kodu programınıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-164">Add the following code to your program.</span></span> <span data-ttu-id="2aaa8-165">Bu örnekte, aralarında bir ilişki olan iki nesne eklersiniz, ve bir eğitmen ve bir ofis ataması eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-165">In this example, you add two objects with a relationship between them, and you add an instructor and an office assignment.</span></span> <span data-ttu-id="2aaa8-166">Tablo `OfficeAssignments` içeren `InstructorID` başvuruda bulunan sütun `PersonID` sütununda `Person` tablo.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-166">The table `OfficeAssignments` contains the `InstructorID` column, which references the `PersonID` column in the `Person` table.</span></span>
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

<span data-ttu-id="2aaa8-167">Çağrısı tamamlanana kadar hiçbir şey veritabanında değiştirildiğinde `System.Data.Objects.ObjectContext.SaveChanges`.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-167">Nothing is changed in the database until you call `System.Data.Objects.ObjectContext.SaveChanges`.</span></span>
<br />

2. <span data-ttu-id="2aaa8-168">Şimdi eklediğiniz nesneleri silerek veritabanını önceki durumuna geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-168">Now restore the database to its earlier state by deleting the objects that you added.</span></span>
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
<span data-ttu-id="2aaa8-169">Bir sorgu ifadesi kullandığınızda, sorgunun tembel değerlendirmeye bağlı olduğunu hatırlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-169">When you use a query expression, you must remember that the query is subject to lazy evaluation.</span></span> <span data-ttu-id="2aaa8-170">Bu nedenle, veritabanı herhangi bir zincirleme değerlendirme sırasında hala okumaya açıktır, her sorgu ifadesi sonrasındaki lambda ifadesi blokları gibi.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-170">Therefore, the database is still open for reading during any chained evaluations, such as in the lambda expression blocks after each query expression.</span></span> <span data-ttu-id="2aaa8-171">Açıkça ya da örtülü olarak bir işlem kullanan herhangi bir veritabanı işlemi okuma işlemleri tamamlandıktan sonra gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-171">Any database operation that explicitly or implicitly uses a transaction must occur after the read operations have completed.</span></span>


## <a name="next-steps"></a><span data-ttu-id="2aaa8-172">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="2aaa8-172">Next Steps</span></span>
<span data-ttu-id="2aaa8-173">Kullanılabilir sorgu işleçleri gözden geçirerek diğer sorgu seçeneklerini keşfetmek [sorgu ifadeleri](../../language-reference/query-expressions.md)ve da gözden [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) hangi işlevleri için kullanılabilir olduğunda anlamak için Bu tür sağlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-173">Explore other query options by reviewing the query operators available in [Query Expressions](../../language-reference/query-expressions.md), and also review the [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) to understand what functionality is available to you when you use this type provider.</span></span>


## <a name="see-also"></a><span data-ttu-id="2aaa8-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2aaa8-174">See Also</span></span>
[<span data-ttu-id="2aaa8-175">Tür Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="2aaa8-175">Type Providers</span></span>](index.md)  
[<span data-ttu-id="2aaa8-176">SqlEntityConnection Type Provider</span><span class="sxs-lookup"><span data-stu-id="2aaa8-176">SqlEntityConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)  
[<span data-ttu-id="2aaa8-177">İzlenecek yol: EDMX şema dosyasından F # türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="2aaa8-177">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>](generating-fsharp-types-from-edmx.md)  
[<span data-ttu-id="2aaa8-178">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2aaa8-178">ADO.NET Entity Framework</span></span>](https://msdn.microsoft.com/library/bb399572)  
[<span data-ttu-id="2aaa8-179">.edmx dosyasının genel bakış</span><span class="sxs-lookup"><span data-stu-id="2aaa8-179">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
[<span data-ttu-id="2aaa8-180">EDM Oluşturucu &#40; EdmGen.exe &#41;</span><span class="sxs-lookup"><span data-stu-id="2aaa8-180">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)  
