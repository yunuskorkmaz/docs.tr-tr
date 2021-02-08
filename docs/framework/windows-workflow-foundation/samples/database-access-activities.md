---
description: 'Daha fazla bilgi edinin: veritabanı erişim etkinlikleri'
title: Veritabanı Erişimi Etkinlikleri
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 421da4a55997dac62ccc5c598bc401a20711ec61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792550"
---
# <a name="database-access-activities"></a><span data-ttu-id="d6b09-103">Veritabanı Erişimi Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="d6b09-103">Database Access Activities</span></span>

<span data-ttu-id="d6b09-104">Veritabanı erişim etkinlikleri, bir iş akışı içindeki bir veritabanına erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6b09-104">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="d6b09-105">Bu etkinlikler, veritabanlarına erişim sağlamak veya bilgileri değiştirmek ve veritabanına erişmek için [ADO.net](../../data/adonet/index.md) kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6b09-105">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6b09-106">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6b09-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d6b09-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d6b09-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d6b09-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için (indirme sayfası) bölümüne gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d6b09-108">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d6b09-109">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d6b09-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="d6b09-110">Veritabanı etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="d6b09-110">Database Activities</span></span>

<span data-ttu-id="d6b09-111">Aşağıdaki bölümler, bu örneğe dahil edilen etkinliklerin listesini ayrıntılandırır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-111">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="d6b09-112">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="d6b09-112">DbUpdate</span></span>

<span data-ttu-id="d6b09-113">Veritabanında değişiklik üreten bir SQL sorgusu yürütür (ekleme, güncelleştirme, silme ve diğer değişiklikler).</span><span class="sxs-lookup"><span data-stu-id="d6b09-113">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

<span data-ttu-id="d6b09-114">Bu sınıf, işini zaman uyumsuz olarak gerçekleştirir (öğesinden türetilir <xref:System.Activities.AsyncCodeActivity> ve zaman uyumsuz yeteneklerini kullanır).</span><span class="sxs-lookup"><span data-stu-id="d6b09-114">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="d6b09-115">Bağlantı bilgileri, bir sağlayıcı sabit adı ( `ProviderName` ) ve bağlantı dizesi ( `ConnectionString` ) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı () kullanılarak yapılandırılabilir `ConfigFileSectionName` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-115">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="d6b09-116">Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d6b09-116">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="d6b09-117">`DbUpdate`Yürütüldükten sonra, etkilenen kayıtların sayısı, `AffectedRecords` özelliğinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d6b09-117">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

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

|<span data-ttu-id="d6b09-118">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="d6b09-118">Argument</span></span>|<span data-ttu-id="d6b09-119">Description</span><span class="sxs-lookup"><span data-stu-id="d6b09-119">Description</span></span>|
|-|-|
|<span data-ttu-id="d6b09-120">Adı</span><span class="sxs-lookup"><span data-stu-id="d6b09-120">ProviderName</span></span>|<span data-ttu-id="d6b09-121">ADO.NET sağlayıcısı sabit adı.</span><span class="sxs-lookup"><span data-stu-id="d6b09-121">ADO.NET provider invariant name.</span></span> <span data-ttu-id="d6b09-122">Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-122">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="d6b09-123">Dizisi</span><span class="sxs-lookup"><span data-stu-id="d6b09-123">ConnectionString</span></span>|<span data-ttu-id="d6b09-124">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="d6b09-124">Connection string to connect to the database.</span></span> <span data-ttu-id="d6b09-125">Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-125">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="d6b09-126">ConfigName</span><span class="sxs-lookup"><span data-stu-id="d6b09-126">ConfigName</span></span>|<span data-ttu-id="d6b09-127">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı.</span><span class="sxs-lookup"><span data-stu-id="d6b09-127">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="d6b09-128">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.</span><span class="sxs-lookup"><span data-stu-id="d6b09-128">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="d6b09-129">CommandType</span><span class="sxs-lookup"><span data-stu-id="d6b09-129">CommandType</span></span>|<span data-ttu-id="d6b09-130">Yürütülecek öğesinin türü <xref:System.Data.Common.DbCommand> .</span><span class="sxs-lookup"><span data-stu-id="d6b09-130">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="d6b09-131">Sql</span><span class="sxs-lookup"><span data-stu-id="d6b09-131">Sql</span></span>|<span data-ttu-id="d6b09-132">Yürütülecek SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="d6b09-132">The SQL command to be executed.</span></span>|
|<span data-ttu-id="d6b09-133">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6b09-133">Parameters</span></span>|<span data-ttu-id="d6b09-134">SQL sorgusunun parametrelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d6b09-134">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="d6b09-135">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="d6b09-135">AffectedRecords</span></span>|<span data-ttu-id="d6b09-136">Son işlemden etkilenen kayıt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d6b09-136">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="d6b09-137">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="d6b09-137">DbQueryScalar</span></span>

<span data-ttu-id="d6b09-138">Veritabanından tek bir değer alan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="d6b09-138">Executes a query that retrieves a single value from the database.</span></span>

<span data-ttu-id="d6b09-139">Bu sınıf, işini zaman uyumsuz olarak gerçekleştirir (öğesinden türetilir <xref:System.Activities.AsyncCodeActivity%601> ve zaman uyumsuz yeteneklerini kullanır).</span><span class="sxs-lookup"><span data-stu-id="d6b09-139">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="d6b09-140">Bağlantı bilgileri, bir sağlayıcı sabit adı ( `ProviderName` ) ve bağlantı dizesi ( `ConnectionString` ) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı () kullanılarak yapılandırılabilir `ConfigFileSectionName` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-140">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="d6b09-141">Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d6b09-141">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="d6b09-142">`DbQueryScalar`Yürütüldükten sonra skaler, `Result out` bağımsız değişkende ( `TResult` temel sınıfta tanımlanan türünde <xref:System.Activities.AsyncCodeActivity%601> ) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d6b09-142">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

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

|<span data-ttu-id="d6b09-143">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="d6b09-143">Argument</span></span>|<span data-ttu-id="d6b09-144">Description</span><span class="sxs-lookup"><span data-stu-id="d6b09-144">Description</span></span>|
|-|-|
|<span data-ttu-id="d6b09-145">Adı</span><span class="sxs-lookup"><span data-stu-id="d6b09-145">ProviderName</span></span>|<span data-ttu-id="d6b09-146">ADO.NET sağlayıcısı sabit adı.</span><span class="sxs-lookup"><span data-stu-id="d6b09-146">ADO.NET provider invariant name.</span></span> <span data-ttu-id="d6b09-147">Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-147">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="d6b09-148">Dizisi</span><span class="sxs-lookup"><span data-stu-id="d6b09-148">ConnectionString</span></span>|<span data-ttu-id="d6b09-149">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="d6b09-149">Connection string to connect to the database.</span></span> <span data-ttu-id="d6b09-150">Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-150">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="d6b09-151">ConfigName</span><span class="sxs-lookup"><span data-stu-id="d6b09-151">ConfigName</span></span>|<span data-ttu-id="d6b09-152">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı.</span><span class="sxs-lookup"><span data-stu-id="d6b09-152">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="d6b09-153">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.</span><span class="sxs-lookup"><span data-stu-id="d6b09-153">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="d6b09-154">CommandType</span><span class="sxs-lookup"><span data-stu-id="d6b09-154">CommandType</span></span>|<span data-ttu-id="d6b09-155">Yürütülecek öğesinin türü <xref:System.Data.Common.DbCommand> .</span><span class="sxs-lookup"><span data-stu-id="d6b09-155">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="d6b09-156">Sql</span><span class="sxs-lookup"><span data-stu-id="d6b09-156">Sql</span></span>|<span data-ttu-id="d6b09-157">Yürütülecek SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="d6b09-157">The SQL command to be executed.</span></span>|
|<span data-ttu-id="d6b09-158">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6b09-158">Parameters</span></span>|<span data-ttu-id="d6b09-159">SQL sorgusunun parametrelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d6b09-159">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="d6b09-160">Sonuç</span><span class="sxs-lookup"><span data-stu-id="d6b09-160">Result</span></span>|<span data-ttu-id="d6b09-161">Sorgu yürütüldükten sonra elde edilen skaler.</span><span class="sxs-lookup"><span data-stu-id="d6b09-161">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="d6b09-162">Bu bağımsız değişken türündedir `TResult` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-162">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="d6b09-163">DbQuery</span><span class="sxs-lookup"><span data-stu-id="d6b09-163">DbQuery</span></span>

<span data-ttu-id="d6b09-164">Bir nesne listesini alan bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="d6b09-164">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="d6b09-165">Sorgu yürütüldükten sonra bir eşleme işlevi yürütülür (Bu <xref:System.Func%601> < `DbDataReader` , `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult`> olabilir).</span><span class="sxs-lookup"><span data-stu-id="d6b09-165">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="d6b09-166">Bu eşleme işlevi, içindeki bir kaydı alır `DbDataReader` ve döndürülecek nesne ile eşler.</span><span class="sxs-lookup"><span data-stu-id="d6b09-166">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

<span data-ttu-id="d6b09-167">Bağlantı bilgileri, bir sağlayıcı sabit adı ( `ProviderName` ) ve bağlantı dizesi ( `ConnectionString` ) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı () kullanılarak yapılandırılabilir `ConfigFileSectionName` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-167">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="d6b09-168">Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d6b09-168">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="d6b09-169">SQL sorgusunun sonuçları bir kullanılarak alınır `DbDataReader` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-169">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="d6b09-170">Etkinlik `DbDataReader` öğesinde yinelenir ve içindeki satırları `DbDataReader` bir örneğine eşler `TResult` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-170">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="d6b09-171">Kullanıcısının `DbQuery` eşleme kodunu sağlaması gerekir ve bu iki şekilde yapılabilir: bir <xref:System.Func%601> < `DbDataReader` , `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult`> kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d6b09-171">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="d6b09-172">İlk durumda, eşleme tek bir yürütme darbeli yapılır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-172">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="d6b09-173">Bu nedenle daha hızlıdır, ancak bu XAML 'e serileştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="d6b09-173">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="d6b09-174">Son durumda, eşleme birden çok pulda gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d6b09-174">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="d6b09-175">Bu nedenle, daha yavaş olabilir ancak XAML 'ye serileştirilebilir ve bildirimli olarak yazılabilir (varolan herhangi bir etkinlik eşlemeye katılabilir).</span><span class="sxs-lookup"><span data-stu-id="d6b09-175">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

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

|<span data-ttu-id="d6b09-176">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="d6b09-176">Argument</span></span>|<span data-ttu-id="d6b09-177">Description</span><span class="sxs-lookup"><span data-stu-id="d6b09-177">Description</span></span>|
|-|-|
|<span data-ttu-id="d6b09-178">Adı</span><span class="sxs-lookup"><span data-stu-id="d6b09-178">ProviderName</span></span>|<span data-ttu-id="d6b09-179">ADO.NET sağlayıcısı sabit adı.</span><span class="sxs-lookup"><span data-stu-id="d6b09-179">ADO.NET provider invariant name.</span></span> <span data-ttu-id="d6b09-180">Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-180">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="d6b09-181">Dizisi</span><span class="sxs-lookup"><span data-stu-id="d6b09-181">ConnectionString</span></span>|<span data-ttu-id="d6b09-182">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="d6b09-182">Connection string to connect to the database.</span></span> <span data-ttu-id="d6b09-183">Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-183">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="d6b09-184">ConfigName</span><span class="sxs-lookup"><span data-stu-id="d6b09-184">ConfigName</span></span>|<span data-ttu-id="d6b09-185">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı.</span><span class="sxs-lookup"><span data-stu-id="d6b09-185">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="d6b09-186">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.</span><span class="sxs-lookup"><span data-stu-id="d6b09-186">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="d6b09-187">CommandType</span><span class="sxs-lookup"><span data-stu-id="d6b09-187">CommandType</span></span>|<span data-ttu-id="d6b09-188">Yürütülecek öğesinin türü <xref:System.Data.Common.DbCommand> .</span><span class="sxs-lookup"><span data-stu-id="d6b09-188">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="d6b09-189">Sql</span><span class="sxs-lookup"><span data-stu-id="d6b09-189">Sql</span></span>|<span data-ttu-id="d6b09-190">Yürütülecek SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="d6b09-190">The SQL command to be executed.</span></span>|
|<span data-ttu-id="d6b09-191">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6b09-191">Parameters</span></span>|<span data-ttu-id="d6b09-192">SQL sorgusunun parametrelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d6b09-192">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="d6b09-193">Eşleyici</span><span class="sxs-lookup"><span data-stu-id="d6b09-193">Mapper</span></span>|<span data-ttu-id="d6b09-194"><xref:System.Func%601> < `DbDataReader` `TResult` Sorgu yürütmenin sonucu olarak elde edilen bir kaydı alan eşleme işlevi (,>) `DataReader` ve `TResult` koleksiyona eklenmek üzere türünde bir nesnenin örneğini döndürür `Result` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-194">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="d6b09-195">Bu durumda, eşleme tek bir yürütmede yürütme yapılır, ancak tasarımcı kullanılarak bildirimli olarak yazılamıyor.</span><span class="sxs-lookup"><span data-stu-id="d6b09-195">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="d6b09-196">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="d6b09-196">MapperFunc</span></span>|<span data-ttu-id="d6b09-197"><xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult` Sorgu yürütmenin sonucu olarak elde edilen bir kaydı alan eşleme işlevi (,>) `DataReader` ve `TResult` koleksiyona eklenmek üzere türünde bir nesnenin örneğini döndürür `Result` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-197">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="d6b09-198">Bu durumda, eşleme birden çok sayıda yürütmede yapılır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-198">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="d6b09-199">Bu işlev XAML 'ye serileştirilebilir ve bildirimli olarak yazılabilir (var olan herhangi bir etkinlik eşlemede yer alabilir).</span><span class="sxs-lookup"><span data-stu-id="d6b09-199">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="d6b09-200">Sonuç</span><span class="sxs-lookup"><span data-stu-id="d6b09-200">Result</span></span>|<span data-ttu-id="d6b09-201">Sorguyu yürütmenin ve içindeki her kayıt için eşleme işlevinin yürütüldüğü sonuç olarak elde edilen nesnelerin listesi `DataReader` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-201">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="d6b09-202">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="d6b09-202">DbQueryDataSet</span></span>

<span data-ttu-id="d6b09-203">Döndüren bir sorgu yürütür <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d6b09-203">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d6b09-204">Bu sınıf, zaman uyumsuz olarak işini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d6b09-204">This class performs its work asynchronously.</span></span> <span data-ttu-id="d6b09-205"><xref:System.Activities.AsyncCodeActivity> < `TResult`> türetilir ve zaman uyumsuz yeteneklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-205">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

<span data-ttu-id="d6b09-206">Bağlantı bilgileri, bir sağlayıcı sabit adı ( `ProviderName` ) ve bağlantı dizesi ( `ConnectionString` ) ayarlanarak veya yalnızca uygulama yapılandırma dosyasından bir bağlantı dizesi yapılandırma adı () kullanılarak yapılandırılabilir `ConfigFileSectionName` .</span><span class="sxs-lookup"><span data-stu-id="d6b09-206">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="d6b09-207">Yürütülecek sorgu, `Sql` özelliğinde yapılandırılır ve parametreler `Parameters` koleksiyondan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d6b09-207">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="d6b09-208">Yürütüldükten sonra, `DbQueryDataSet` `DataSet` `Result out` bağımsız değişkende ( `TResult` temel sınıfta tanımlanan türünde <xref:System.Activities.AsyncCodeActivity%601> ) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d6b09-208">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

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

|<span data-ttu-id="d6b09-209">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="d6b09-209">Argument</span></span>|<span data-ttu-id="d6b09-210">Description</span><span class="sxs-lookup"><span data-stu-id="d6b09-210">Description</span></span>|
|-|-|
|<span data-ttu-id="d6b09-211">Adı</span><span class="sxs-lookup"><span data-stu-id="d6b09-211">ProviderName</span></span>|<span data-ttu-id="d6b09-212">ADO.NET sağlayıcısı sabit adı.</span><span class="sxs-lookup"><span data-stu-id="d6b09-212">ADO.NET provider invariant name.</span></span> <span data-ttu-id="d6b09-213">Bu bağımsız değişken ayarlandıysa `ConnectionString` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-213">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="d6b09-214">Dizisi</span><span class="sxs-lookup"><span data-stu-id="d6b09-214">ConnectionString</span></span>|<span data-ttu-id="d6b09-215">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="d6b09-215">Connection string to connect to the database.</span></span> <span data-ttu-id="d6b09-216">Bu bağımsız değişken ayarlandıysa `ProviderName` de ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-216">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="d6b09-217">ConfigName</span><span class="sxs-lookup"><span data-stu-id="d6b09-217">ConfigName</span></span>|<span data-ttu-id="d6b09-218">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümünün adı.</span><span class="sxs-lookup"><span data-stu-id="d6b09-218">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="d6b09-219">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli olmadığında.</span><span class="sxs-lookup"><span data-stu-id="d6b09-219">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="d6b09-220">CommandType</span><span class="sxs-lookup"><span data-stu-id="d6b09-220">CommandType</span></span>|<span data-ttu-id="d6b09-221">Yürütülecek öğesinin türü <xref:System.Data.Common.DbCommand> .</span><span class="sxs-lookup"><span data-stu-id="d6b09-221">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="d6b09-222">Sql</span><span class="sxs-lookup"><span data-stu-id="d6b09-222">Sql</span></span>|<span data-ttu-id="d6b09-223">Yürütülecek SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="d6b09-223">The SQL command to be executed.</span></span>|
|<span data-ttu-id="d6b09-224">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6b09-224">Parameters</span></span>|<span data-ttu-id="d6b09-225">SQL sorgusunun parametrelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d6b09-225">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="d6b09-226">Sonuç</span><span class="sxs-lookup"><span data-stu-id="d6b09-226">Result</span></span>|<span data-ttu-id="d6b09-227"><xref:System.Data.DataSet> Sorgu yürütüldükten sonra elde edilen.</span><span class="sxs-lookup"><span data-stu-id="d6b09-227"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="d6b09-228">Bağlantı bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d6b09-228">Configuring Connection Information</span></span>

<span data-ttu-id="d6b09-229">Tüm Dbacmize aynı yapılandırma parametrelerini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-229">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="d6b09-230">İki şekilde yapılandırılabilirler:</span><span class="sxs-lookup"><span data-stu-id="d6b09-230">They can be configured in two ways:</span></span>

- <span data-ttu-id="d6b09-231">`ConnectionString + InvariantName`: ADO.NET sağlayıcısı sabit adını ve bağlantı dizesini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d6b09-231">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

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

- <span data-ttu-id="d6b09-232">`ConfigName`: Bağlantı bilgilerini içeren yapılandırma bölümünün adını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d6b09-232">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- <span data-ttu-id="d6b09-233">Etkinlikte:</span><span class="sxs-lookup"><span data-stu-id="d6b09-233">In the activity:</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a><span data-ttu-id="d6b09-234">Bu örnek çalıştırılıyor</span><span class="sxs-lookup"><span data-stu-id="d6b09-234">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="d6b09-235">Kurulum yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d6b09-235">Setup instructions</span></span>

<span data-ttu-id="d6b09-236">Bu örnek bir veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-236">This sample uses a database.</span></span> <span data-ttu-id="d6b09-237">Örnekle birlikte bir kurulum ve yükleme betiği (Setup. cmd) sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-237">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="d6b09-238">Komut istemi 'ni kullanarak bu dosyayı yürütmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6b09-238">You must execute that file using the command prompt.</span></span>

<span data-ttu-id="d6b09-239">Setup. cmd betiği, aşağıdakileri yapan SQL komutlarını içeren CreateDb. SQL komut dosyasını çağırır:</span><span class="sxs-lookup"><span data-stu-id="d6b09-239">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="d6b09-240">DbActivitiesSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6b09-240">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="d6b09-241">Roller tablosu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6b09-241">Creates the Roles table.</span></span>

- <span data-ttu-id="d6b09-242">Çalışanlar tablosu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6b09-242">Creates Employees table.</span></span>

- <span data-ttu-id="d6b09-243">Roller tablosuna üç kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="d6b09-243">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="d6b09-244">Çalışanlar tablosuna on iki kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="d6b09-244">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="d6b09-245">Setup. cmd dosyasını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d6b09-245">To run Setup.cmd</span></span>

1. <span data-ttu-id="d6b09-246">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="d6b09-246">Open a command prompt.</span></span>

2. <span data-ttu-id="d6b09-247">Dbacmize Sample klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="d6b09-247">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="d6b09-248">"Setup. cmd" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d6b09-248">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d6b09-249">Setup. cmd, örneği yerel makinenizde SqlExpress örneğine yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="d6b09-249">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="d6b09-250">Bunu başka bir SQL Server örneğine yüklemek istiyorsanız, Setup. cmd dosyasını yeni örnek adıyla düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="d6b09-250">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="d6b09-251">Örnek veritabanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="d6b09-251">To uninstall the sample database</span></span>

1. <span data-ttu-id="d6b09-252">Komut isteminde Sample klasöründen Cleanup. cmd ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d6b09-252">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="d6b09-253">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d6b09-253">To run the sample</span></span>

1. <span data-ttu-id="d6b09-254">Çözümü Visual Studio 2010 ' de açın</span><span class="sxs-lookup"><span data-stu-id="d6b09-254">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="d6b09-255">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d6b09-255">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="d6b09-256">Örneği hata ayıklama olmadan çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d6b09-256">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6b09-257">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6b09-257">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d6b09-258">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d6b09-258">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d6b09-259">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d6b09-259">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d6b09-260">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d6b09-260">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
