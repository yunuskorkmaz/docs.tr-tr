---
title: Veritabanı Erişimi Etkinlikleri
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 31794a583e87b5948457fac754cb5bf66fafa09c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016033"
---
# <a name="database-access-activities"></a><span data-ttu-id="7e341-102">Veritabanı Erişimi Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="7e341-102">Database Access Activities</span></span>

<span data-ttu-id="7e341-103">Veritabanı erişim etkinlikleri, bir iş akışı içindeki bir veritabanına erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e341-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="7e341-104">Bu etkinlikler, veritabanlarına erişim sağlamak veya bilgileri değiştirmek ve veritabanına erişmek için [ADO.net](https://go.microsoft.com/fwlink/?LinkId=166081) kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e341-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e341-105">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7e341-106">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7e341-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7e341-107">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için (indirme sayfası) bölümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="7e341-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7e341-108">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7e341-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="7e341-109">Veritabanı etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="7e341-109">Database Activities</span></span>

<span data-ttu-id="7e341-110">Aşağıdaki bölümler, bu örneğe dahil edilen etkinliklerin listesini ayrıntılandırır.</span><span class="sxs-lookup"><span data-stu-id="7e341-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="7e341-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="7e341-111">DbUpdate</span></span>

<span data-ttu-id="7e341-112">Veritabanında değişiklik üreten bir SQL sorgusu yürütür (ekleme, güncelleştirme, silme ve diğer değişiklikler).</span><span class="sxs-lookup"><span data-stu-id="7e341-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

<span data-ttu-id="7e341-113">Bu sınıf, işini zaman uyumsuz olarak gerçekleştirir (öğesinden <xref:System.Activities.AsyncCodeActivity> türetilir ve zaman uyumsuz yeteneklerini kullanır).</span><span class="sxs-lookup"><span data-stu-id="7e341-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="7e341-114">Bağlantı bilgileri, bir sağlayıcı sabit adı (`ProviderName`) ve bağlantı dizesi (`ConnectionString`) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı (`ConfigFileSectionName`) kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="7e341-115">Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="7e341-116">Yürütüldükten `DbUpdate` sonra, etkilenen kayıtların sayısı, `AffectedRecords` özelliğinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7e341-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```csharp
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|<span data-ttu-id="7e341-117">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="7e341-117">Argument</span></span>|<span data-ttu-id="7e341-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e341-118">Description</span></span>|
|-|-|
|<span data-ttu-id="7e341-119">Adı</span><span class="sxs-lookup"><span data-stu-id="7e341-119">ProviderName</span></span>|<span data-ttu-id="7e341-120">ADO.NET sağlayıcısı sabit adı.</span><span class="sxs-lookup"><span data-stu-id="7e341-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="7e341-121">Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e341-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="7e341-122">Dizisi</span><span class="sxs-lookup"><span data-stu-id="7e341-122">ConnectionString</span></span>|<span data-ttu-id="7e341-123">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="7e341-123">Connection string to connect to the database.</span></span> <span data-ttu-id="7e341-124">Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e341-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="7e341-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="7e341-125">ConfigName</span></span>|<span data-ttu-id="7e341-126">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı.</span><span class="sxs-lookup"><span data-stu-id="7e341-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="7e341-127">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.</span><span class="sxs-lookup"><span data-stu-id="7e341-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="7e341-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="7e341-128">CommandType</span></span>|<span data-ttu-id="7e341-129">Yürütülecek öğesinin <xref:System.Data.Common.DbCommand> türü.</span><span class="sxs-lookup"><span data-stu-id="7e341-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="7e341-130">SQL</span><span class="sxs-lookup"><span data-stu-id="7e341-130">Sql</span></span>|<span data-ttu-id="7e341-131">Yürütülecek SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="7e341-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="7e341-132">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e341-132">Parameters</span></span>|<span data-ttu-id="7e341-133">SQL sorgusunun parametrelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7e341-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="7e341-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="7e341-134">AffectedRecords</span></span>|<span data-ttu-id="7e341-135">Son işlemden etkilenen kayıt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7e341-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="7e341-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="7e341-136">DbQueryScalar</span></span>

<span data-ttu-id="7e341-137">Veritabanından tek bir değer alan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="7e341-137">Executes a query that retrieves a single value from the database.</span></span>

<span data-ttu-id="7e341-138">Bu sınıf, işini zaman uyumsuz olarak gerçekleştirir (öğesinden <xref:System.Activities.AsyncCodeActivity%601> türetilir ve zaman uyumsuz yeteneklerini kullanır).</span><span class="sxs-lookup"><span data-stu-id="7e341-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="7e341-139">Bağlantı bilgileri, bir sağlayıcı sabit adı (`ProviderName`) ve bağlantı dizesi (`ConnectionString`) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı (`ConfigFileSectionName`) kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="7e341-140">Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="7e341-141">Yürütüldükten `DbQueryScalar` sonra skaler, `Result out` bağımsız değişkende (temel sınıfta <xref:System.Activities.AsyncCodeActivity%601>tanımlanan türünde `TResult`) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7e341-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="7e341-142">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="7e341-142">Argument</span></span>|<span data-ttu-id="7e341-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e341-143">Description</span></span>|
|-|-|
|<span data-ttu-id="7e341-144">Adı</span><span class="sxs-lookup"><span data-stu-id="7e341-144">ProviderName</span></span>|<span data-ttu-id="7e341-145">ADO.NET sağlayıcısı sabit adı.</span><span class="sxs-lookup"><span data-stu-id="7e341-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="7e341-146">Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e341-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="7e341-147">Dizisi</span><span class="sxs-lookup"><span data-stu-id="7e341-147">ConnectionString</span></span>|<span data-ttu-id="7e341-148">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="7e341-148">Connection string to connect to the database.</span></span> <span data-ttu-id="7e341-149">Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e341-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="7e341-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="7e341-150">ConfigName</span></span>|<span data-ttu-id="7e341-151">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı.</span><span class="sxs-lookup"><span data-stu-id="7e341-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="7e341-152">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.</span><span class="sxs-lookup"><span data-stu-id="7e341-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="7e341-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="7e341-153">CommandType</span></span>|<span data-ttu-id="7e341-154">Yürütülecek öğesinin <xref:System.Data.Common.DbCommand> türü.</span><span class="sxs-lookup"><span data-stu-id="7e341-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="7e341-155">SQL</span><span class="sxs-lookup"><span data-stu-id="7e341-155">Sql</span></span>|<span data-ttu-id="7e341-156">Yürütülecek SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="7e341-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="7e341-157">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e341-157">Parameters</span></span>|<span data-ttu-id="7e341-158">SQL sorgusunun parametrelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7e341-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="7e341-159">Sonuç</span><span class="sxs-lookup"><span data-stu-id="7e341-159">Result</span></span>|<span data-ttu-id="7e341-160">Sorgu yürütüldükten sonra elde edilen skaler.</span><span class="sxs-lookup"><span data-stu-id="7e341-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="7e341-161">Bu bağımsız değişken türündedir `TResult`.</span><span class="sxs-lookup"><span data-stu-id="7e341-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="7e341-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="7e341-162">DbQuery</span></span>

<span data-ttu-id="7e341-163">Bir nesne listesini alan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="7e341-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="7e341-164"><xref:System.Func%601>Sorgu yürütüldükten sonra bir eşleme işlevi yürütülür (Bu `DbDataReader` <xref:System.Activities.ActivityFunc%601> `DbDataReader` <, `TResult`> veya < bir`TResult`> olabilir).</span><span class="sxs-lookup"><span data-stu-id="7e341-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="7e341-165">Bu eşleme işlevi, içindeki `DbDataReader` bir kaydı alır ve döndürülecek nesne ile eşler.</span><span class="sxs-lookup"><span data-stu-id="7e341-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

<span data-ttu-id="7e341-166">Bağlantı bilgileri, bir sağlayıcı sabit adı (`ProviderName`) ve bağlantı dizesi (`ConnectionString`) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı (`ConfigFileSectionName`) kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="7e341-167">Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="7e341-168">SQL sorgusunun sonuçları bir `DbDataReader`kullanılarak alınır.</span><span class="sxs-lookup"><span data-stu-id="7e341-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="7e341-169">Etkinlik `DbDataReader` öğesindeyinelenir`TResult`ve içindeki satırlarıbirörneğineeşler.`DbDataReader`</span><span class="sxs-lookup"><span data-stu-id="7e341-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="7e341-170">`DbQuery` Kullanıcısının eşleme kodunu sağlaması gerekir ve bu iki şekilde yapılabilir: bir `DbDataReader` < <xref:System.Activities.ActivityFunc%601> < `DbDataReader` <xref:System.Func%601>, `TResult`> veya bir `TResult`> kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7e341-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="7e341-171">İlk durumda, eşleme tek bir yürütme darbeli yapılır.</span><span class="sxs-lookup"><span data-stu-id="7e341-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="7e341-172">Bu nedenle daha hızlıdır, ancak bu XAML 'e serileştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="7e341-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="7e341-173">Son durumda, eşleme birden çok pulda gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="7e341-174">Bu nedenle, daha yavaş olabilir ancak XAML 'ye serileştirilebilir ve bildirimli olarak yazılabilir (varolan herhangi bir etkinlik eşlemeye katılabilir).</span><span class="sxs-lookup"><span data-stu-id="7e341-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```csharp
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|<span data-ttu-id="7e341-175">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="7e341-175">Argument</span></span>|<span data-ttu-id="7e341-176">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e341-176">Description</span></span>|
|-|-|
|<span data-ttu-id="7e341-177">Adı</span><span class="sxs-lookup"><span data-stu-id="7e341-177">ProviderName</span></span>|<span data-ttu-id="7e341-178">ADO.NET sağlayıcısı sabit adı.</span><span class="sxs-lookup"><span data-stu-id="7e341-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="7e341-179">Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e341-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="7e341-180">Dizisi</span><span class="sxs-lookup"><span data-stu-id="7e341-180">ConnectionString</span></span>|<span data-ttu-id="7e341-181">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="7e341-181">Connection string to connect to the database.</span></span> <span data-ttu-id="7e341-182">Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e341-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="7e341-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="7e341-183">ConfigName</span></span>|<span data-ttu-id="7e341-184">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı.</span><span class="sxs-lookup"><span data-stu-id="7e341-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="7e341-185">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.</span><span class="sxs-lookup"><span data-stu-id="7e341-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="7e341-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="7e341-186">CommandType</span></span>|<span data-ttu-id="7e341-187">Yürütülecek öğesinin <xref:System.Data.Common.DbCommand> türü.</span><span class="sxs-lookup"><span data-stu-id="7e341-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="7e341-188">SQL</span><span class="sxs-lookup"><span data-stu-id="7e341-188">Sql</span></span>|<span data-ttu-id="7e341-189">Yürütülecek SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="7e341-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="7e341-190">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e341-190">Parameters</span></span>|<span data-ttu-id="7e341-191">SQL sorgusunun parametrelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7e341-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="7e341-192">Eşleyici</span><span class="sxs-lookup"><span data-stu-id="7e341-192">Mapper</span></span>|<span data-ttu-id="7e341-193">Sorgu<xref:System.Func%601>yürütmenin`DbDataReader`< `DataReader` sonucuolarak`TResult`elde edilen bir kaydı alan eşleme işlevi (, >) ve bir nesnenin bir örneğini içine eklenmek üzere `TResult` `Result` koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="7e341-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="7e341-194">Bu durumda, eşleme tek bir yürütmede yürütme yapılır, ancak tasarımcı kullanılarak bildirimli olarak yazılamıyor.</span><span class="sxs-lookup"><span data-stu-id="7e341-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="7e341-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="7e341-195">MapperFunc</span></span>|<span data-ttu-id="7e341-196">Sorgu<xref:System.Activities.ActivityFunc%601>yürütmenin`DbDataReader`< `DataReader` sonucuolarak`TResult`elde edilen bir kaydı alan eşleme işlevi (, >) ve bir nesnenin bir örneğini içine eklenmek üzere `TResult` `Result` koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="7e341-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="7e341-197">Bu durumda, eşleme birden çok sayıda yürütmede yapılır.</span><span class="sxs-lookup"><span data-stu-id="7e341-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="7e341-198">Bu işlev XAML 'ye serileştirilebilir ve bildirimli olarak yazılabilir (var olan herhangi bir etkinlik eşlemede yer alabilir).</span><span class="sxs-lookup"><span data-stu-id="7e341-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="7e341-199">Sonuç</span><span class="sxs-lookup"><span data-stu-id="7e341-199">Result</span></span>|<span data-ttu-id="7e341-200">Sorguyu yürütmenin ve içindeki `DataReader`her kayıt için eşleme işlevinin yürütüldüğü sonuç olarak elde edilen nesnelerin listesi.</span><span class="sxs-lookup"><span data-stu-id="7e341-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="7e341-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="7e341-201">DbQueryDataSet</span></span>

<span data-ttu-id="7e341-202">Döndüren bir sorgu yürütür <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="7e341-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7e341-203">Bu sınıf, zaman uyumsuz olarak işini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="7e341-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="7e341-204">> Türetilir <xref:System.Activities.AsyncCodeActivity> <ve zaman uyumsuz yeteneklerini kullanır. `TResult`</span><span class="sxs-lookup"><span data-stu-id="7e341-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

<span data-ttu-id="7e341-205">Bağlantı bilgileri, bir sağlayıcı sabit adı (`ProviderName`) ve bağlantı dizesi (`ConnectionString`) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı (`ConfigFileSectionName`) kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="7e341-206">Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="7e341-207">`DbQueryDataSet` `TResult`Yürütüldükten sonra, `Result out` bağımsız değişkende (temel sınıfta<xref:System.Activities.AsyncCodeActivity%601>tanımlanan türünde) döndürülür. `DataSet`</span><span class="sxs-lookup"><span data-stu-id="7e341-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="7e341-208">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="7e341-208">Argument</span></span>|<span data-ttu-id="7e341-209">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e341-209">Description</span></span>|
|-|-|
|<span data-ttu-id="7e341-210">Adı</span><span class="sxs-lookup"><span data-stu-id="7e341-210">ProviderName</span></span>|<span data-ttu-id="7e341-211">ADO.NET sağlayıcısı sabit adı.</span><span class="sxs-lookup"><span data-stu-id="7e341-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="7e341-212">Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e341-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="7e341-213">Dizisi</span><span class="sxs-lookup"><span data-stu-id="7e341-213">ConnectionString</span></span>|<span data-ttu-id="7e341-214">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="7e341-214">Connection string to connect to the database.</span></span> <span data-ttu-id="7e341-215">Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e341-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="7e341-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="7e341-216">ConfigName</span></span>|<span data-ttu-id="7e341-217">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı.</span><span class="sxs-lookup"><span data-stu-id="7e341-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="7e341-218">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.</span><span class="sxs-lookup"><span data-stu-id="7e341-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="7e341-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="7e341-219">CommandType</span></span>|<span data-ttu-id="7e341-220">Yürütülecek öğesinin <xref:System.Data.Common.DbCommand> türü.</span><span class="sxs-lookup"><span data-stu-id="7e341-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="7e341-221">SQL</span><span class="sxs-lookup"><span data-stu-id="7e341-221">Sql</span></span>|<span data-ttu-id="7e341-222">Yürütülecek SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="7e341-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="7e341-223">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e341-223">Parameters</span></span>|<span data-ttu-id="7e341-224">SQL sorgusunun parametrelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7e341-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="7e341-225">Sonuç</span><span class="sxs-lookup"><span data-stu-id="7e341-225">Result</span></span>|<span data-ttu-id="7e341-226"><xref:System.Data.DataSet>Sorgu yürütüldükten sonra elde edilen.</span><span class="sxs-lookup"><span data-stu-id="7e341-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="7e341-227">Bağlantı bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7e341-227">Configuring Connection Information</span></span>

<span data-ttu-id="7e341-228">Tüm Dbacmize aynı yapılandırma parametrelerini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="7e341-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="7e341-229">İki şekilde yapılandırılabilirler:</span><span class="sxs-lookup"><span data-stu-id="7e341-229">They can be configured in two ways:</span></span>

- <span data-ttu-id="7e341-230">`ConnectionString + InvariantName`: ADO.NET sağlayıcısı sabit adını ve bağlantı dizesini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7e341-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<DateTime>()
  {
      ProviderName = "System.Data.SqlClient",
      ConnectionString = @"Data Source=.\SQLExpress;
                            Initial Catalog=DbActivitiesSample;
                            Integrated Security=True",
      Sql = "SELECT GetDate()"
  };
  ```

- <span data-ttu-id="7e341-231">`ConfigName`: Bağlantı bilgilerini içeren yapılandırma bölümünün adını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7e341-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- <span data-ttu-id="7e341-232">Etkinlikte:</span><span class="sxs-lookup"><span data-stu-id="7e341-232">In the activity:</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a><span data-ttu-id="7e341-233">Bu örnek çalıştırılıyor</span><span class="sxs-lookup"><span data-stu-id="7e341-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="7e341-234">Kurulum yönergeleri</span><span class="sxs-lookup"><span data-stu-id="7e341-234">Setup instructions</span></span>

<span data-ttu-id="7e341-235">Bu örnek bir veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7e341-235">This sample uses a database.</span></span> <span data-ttu-id="7e341-236">Örnekle birlikte bir kurulum ve yükleme betiği (Setup. cmd) sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7e341-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="7e341-237">Komut istemi 'ni kullanarak bu dosyayı yürütmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e341-237">You must execute that file using the command prompt.</span></span>

<span data-ttu-id="7e341-238">Setup. cmd betiği, aşağıdakileri yapan SQL komutlarını içeren CreateDb. SQL komut dosyasını çağırır:</span><span class="sxs-lookup"><span data-stu-id="7e341-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="7e341-239">DbActivitiesSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e341-239">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="7e341-240">Roller tablosu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e341-240">Creates the Roles table.</span></span>

- <span data-ttu-id="7e341-241">Çalışanlar tablosu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e341-241">Creates Employees table.</span></span>

- <span data-ttu-id="7e341-242">Roller tablosuna üç kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="7e341-242">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="7e341-243">Çalışanlar tablosuna on iki kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="7e341-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="7e341-244">Setup. cmd dosyasını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7e341-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="7e341-245">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="7e341-245">Open a command prompt.</span></span>

2. <span data-ttu-id="7e341-246">Dbacmize Sample klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="7e341-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="7e341-247">"Setup. cmd" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7e341-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7e341-248">Setup. cmd, örneği yerel makinenizde SqlExpress örneğine yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="7e341-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="7e341-249">Bunu başka bir SQL Server örneğine yüklemek istiyorsanız, Setup. cmd dosyasını yeni örnek adıyla düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="7e341-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="7e341-250">Örnek veritabanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="7e341-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="7e341-251">Komut isteminde Sample klasöründen Cleanup. cmd ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7e341-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="7e341-252">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7e341-252">To run the sample</span></span>

1. <span data-ttu-id="7e341-253">Çözümü Visual Studio 2010 ' de açın</span><span class="sxs-lookup"><span data-stu-id="7e341-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="7e341-254">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="7e341-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="7e341-255">Örneği hata ayıklama olmadan çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="7e341-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e341-256">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e341-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7e341-257">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7e341-257">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7e341-258">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="7e341-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7e341-259">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7e341-259">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
