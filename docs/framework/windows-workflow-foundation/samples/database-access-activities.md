---
title: Veritabanı Erişimi Etkinlikleri
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 2463c3a87be7f7e248572d45e018b72661f4f8c7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322608"
---
# <a name="database-access-activities"></a><span data-ttu-id="18a22-102">Veritabanı Erişimi Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="18a22-102">Database Access Activities</span></span>
<span data-ttu-id="18a22-103">Veritabanı erişimi etkinlikleri iş akışı içindeki bir veritabanına erişmek izin verin.</span><span class="sxs-lookup"><span data-stu-id="18a22-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="18a22-104">Bu etkinliklerin alma veya bilgileri değiştirin ve veritabanlarına erişim ver [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) veritabanına erişmek için.</span><span class="sxs-lookup"><span data-stu-id="18a22-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18a22-105">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="18a22-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="18a22-106">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="18a22-106">Check for the following (default) directory before continuing.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  <span data-ttu-id="18a22-107">Bu dizin mevcut değilse (indirme sayfası) Git tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="18a22-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18a22-108">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="18a22-108">This sample is located in the following directory.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="18a22-109">Veritabanı etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="18a22-109">Database Activities</span></span>
 <span data-ttu-id="18a22-110">Bu örnekte bulunan etkinliklerinin listesini aşağıdaki bölümlerde ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18a22-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="18a22-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="18a22-111">DbUpdate</span></span>
 <span data-ttu-id="18a22-112">(Ekleme, güncelleştirme, silme ve diğer değişikliklerin) veritabanında değişiklik üreten bir SQL sorgusunu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="18a22-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

 <span data-ttu-id="18a22-113">Bu sınıf, zaman uyumsuz olarak kendi işini gerçekleştirir (türetildiği <xref:System.Activities.AsyncCodeActivity> ve zaman uyumsuz özelliklerini kullanır).</span><span class="sxs-lookup"><span data-stu-id="18a22-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="18a22-114">Bağlantı bilgilerini sağlayıcının değişmez adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasına ait.</span><span class="sxs-lookup"><span data-stu-id="18a22-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="18a22-115">Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreler aracılığıyla geçirilir `Parameters` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="18a22-116">Sonra `DbUpdate` olan yürütüldü, etkilenen kayıtların sayısı döndürülür `AffectedRecords` özelliği.</span><span class="sxs-lookup"><span data-stu-id="18a22-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```
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

|<span data-ttu-id="18a22-117">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="18a22-117">Argument</span></span>|<span data-ttu-id="18a22-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18a22-118">Description</span></span>|
|-|-|
|<span data-ttu-id="18a22-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="18a22-119">ProviderName</span></span>|<span data-ttu-id="18a22-120">ADO.NET sağlayıcısı değişmez adı.</span><span class="sxs-lookup"><span data-stu-id="18a22-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="18a22-121">Bu bağımsız değişken ayarlarsanız, ardından `ConnectionString` de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a22-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="18a22-122">bağlantı dizesi</span><span class="sxs-lookup"><span data-stu-id="18a22-122">ConnectionString</span></span>|<span data-ttu-id="18a22-123">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="18a22-123">Connection string to connect to the database.</span></span> <span data-ttu-id="18a22-124">Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a22-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="18a22-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="18a22-125">ConfigName</span></span>|<span data-ttu-id="18a22-126">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı.</span><span class="sxs-lookup"><span data-stu-id="18a22-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="18a22-127">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="18a22-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="18a22-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="18a22-128">CommandType</span></span>|<span data-ttu-id="18a22-129">Tür <xref:System.Data.Common.DbCommand> yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="18a22-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="18a22-130">Sql</span><span class="sxs-lookup"><span data-stu-id="18a22-130">Sql</span></span>|<span data-ttu-id="18a22-131">Çalıştırılacak SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="18a22-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="18a22-132">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18a22-132">Parameters</span></span>|<span data-ttu-id="18a22-133">SQL sorgu parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="18a22-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="18a22-134">AffectedRecords</span></span>|<span data-ttu-id="18a22-135">Son işlem tarafından etkilenen kayıtların sayısı.</span><span class="sxs-lookup"><span data-stu-id="18a22-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="18a22-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="18a22-136">DbQueryScalar</span></span>
 <span data-ttu-id="18a22-137">Veritabanından tek bir değer alır. bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="18a22-137">Executes a query that retrieves a single value from the database.</span></span>

 <span data-ttu-id="18a22-138">Bu sınıf, zaman uyumsuz olarak kendi işini gerçekleştirir (türetildiği <xref:System.Activities.AsyncCodeActivity%601> ve zaman uyumsuz özelliklerini kullanır).</span><span class="sxs-lookup"><span data-stu-id="18a22-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="18a22-139">Bağlantı bilgilerini sağlayıcının değişmez adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasına ait.</span><span class="sxs-lookup"><span data-stu-id="18a22-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="18a22-140">Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreler aracılığıyla geçirilir `Parameters` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="18a22-141">Sonra `DbQueryScalar` olan yürütüldü, skaler döndürülür `Result out` bağımsız değişken (tür `TResult`, yani temel sınıfta tanımlanan <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="18a22-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
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

|<span data-ttu-id="18a22-142">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="18a22-142">Argument</span></span>|<span data-ttu-id="18a22-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18a22-143">Description</span></span>|
|-|-|
|<span data-ttu-id="18a22-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="18a22-144">ProviderName</span></span>|<span data-ttu-id="18a22-145">ADO.NET sağlayıcısı değişmez adı.</span><span class="sxs-lookup"><span data-stu-id="18a22-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="18a22-146">Bu bağımsız değişken ayarlarsanız, ardından `ConnectionString` de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a22-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="18a22-147">bağlantı dizesi</span><span class="sxs-lookup"><span data-stu-id="18a22-147">ConnectionString</span></span>|<span data-ttu-id="18a22-148">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="18a22-148">Connection string to connect to the database.</span></span> <span data-ttu-id="18a22-149">Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a22-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="18a22-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="18a22-150">ConfigName</span></span>|<span data-ttu-id="18a22-151">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı.</span><span class="sxs-lookup"><span data-stu-id="18a22-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="18a22-152">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="18a22-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="18a22-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="18a22-153">CommandType</span></span>|<span data-ttu-id="18a22-154">Tür <xref:System.Data.Common.DbCommand> yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="18a22-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="18a22-155">Sql</span><span class="sxs-lookup"><span data-stu-id="18a22-155">Sql</span></span>|<span data-ttu-id="18a22-156">Çalıştırılacak SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="18a22-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="18a22-157">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18a22-157">Parameters</span></span>|<span data-ttu-id="18a22-158">SQL sorgu parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="18a22-159">Sonuç</span><span class="sxs-lookup"><span data-stu-id="18a22-159">Result</span></span>|<span data-ttu-id="18a22-160">Sorgu yürütüldükten sonra elde edilen skaler.</span><span class="sxs-lookup"><span data-stu-id="18a22-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="18a22-161">Bu bağımsız değişken türünde `TResult`.</span><span class="sxs-lookup"><span data-stu-id="18a22-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="18a22-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="18a22-162">DbQuery</span></span>
 <span data-ttu-id="18a22-163">Nesnelerin bir listesini alır. bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="18a22-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="18a22-164">Sorgu yürütüldükten sonra bir eşleme işlev yürütülür (olabilir <xref:System.Func%601> < `DbDataReader`, `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="18a22-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="18a22-165">Bu eşleme işlevi bir kaydı alır bir `DbDataReader` ve döndürülecek nesnesine eşler.</span><span class="sxs-lookup"><span data-stu-id="18a22-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

 <span data-ttu-id="18a22-166">Bağlantı bilgilerini sağlayıcının değişmez adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasına ait.</span><span class="sxs-lookup"><span data-stu-id="18a22-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="18a22-167">Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreler aracılığıyla geçirilir `Parameters` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="18a22-168">Kullanarak SQL sorgusunun sonuçları alınırken bir `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="18a22-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="18a22-169">Etkinlik gezinir `DbDataReader` ve satırlarda eşler `DbDataReader` örneğine `TResult`.</span><span class="sxs-lookup"><span data-stu-id="18a22-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="18a22-170">Kullanıcıyı `DbQuery` eşleme kod ve bu iki şekilde yapılır sağlamalıdır: kullanarak bir <xref:System.Func%601> < `DbDataReader`, `TResult`> veya bir <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="18a22-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="18a22-171">Bu durumda, tek bir yürütme nabzını içinde Haritası gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="18a22-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="18a22-172">Bu nedenle, daha hızlı, ancak bu XAML için seri hale getirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="18a22-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="18a22-173">En son durumda birden çok darbelerin Haritası gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="18a22-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="18a22-174">Bu nedenle, bunu daha yavaş olabilir, ancak XAML için sıralanabilir ve bildirimli olarak yazılmış (herhangi bir mevcut etkinlik eşlemede katılabilir).</span><span class="sxs-lookup"><span data-stu-id="18a22-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```
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

|<span data-ttu-id="18a22-175">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="18a22-175">Argument</span></span>|<span data-ttu-id="18a22-176">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18a22-176">Description</span></span>|
|-|-|
|<span data-ttu-id="18a22-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="18a22-177">ProviderName</span></span>|<span data-ttu-id="18a22-178">ADO.NET sağlayıcısı değişmez adı.</span><span class="sxs-lookup"><span data-stu-id="18a22-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="18a22-179">Bu bağımsız değişken ayarlarsanız, ardından `ConnectionString` de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a22-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="18a22-180">bağlantı dizesi</span><span class="sxs-lookup"><span data-stu-id="18a22-180">ConnectionString</span></span>|<span data-ttu-id="18a22-181">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="18a22-181">Connection string to connect to the database.</span></span> <span data-ttu-id="18a22-182">Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a22-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="18a22-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="18a22-183">ConfigName</span></span>|<span data-ttu-id="18a22-184">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı.</span><span class="sxs-lookup"><span data-stu-id="18a22-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="18a22-185">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="18a22-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="18a22-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="18a22-186">CommandType</span></span>|<span data-ttu-id="18a22-187">Tür <xref:System.Data.Common.DbCommand> yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="18a22-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="18a22-188">Sql</span><span class="sxs-lookup"><span data-stu-id="18a22-188">Sql</span></span>|<span data-ttu-id="18a22-189">Çalıştırılacak SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="18a22-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="18a22-190">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18a22-190">Parameters</span></span>|<span data-ttu-id="18a22-191">SQL sorgu parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="18a22-192">Eşleyici</span><span class="sxs-lookup"><span data-stu-id="18a22-192">Mapper</span></span>|<span data-ttu-id="18a22-193">İşlev eşleme mapping (<xref:System.Func%601><`DbDataReader`, `TResult`>) bir kayda alan `DataReader` sorgu yürütülürken zaman almış ve türünde bir nesne örneğini döndürür `TResult` içineklenecek`Result` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="18a22-194">Bu durumda, tek bir yürütme nabzını içinde eşleme gerçekleştirilir, ancak bildirimli olarak Tasarımcısı'nı kullanarak yazılması olamaz.</span><span class="sxs-lookup"><span data-stu-id="18a22-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="18a22-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="18a22-195">MapperFunc</span></span>|<span data-ttu-id="18a22-196">İşlev eşleme mapping (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) bir kayda alan `DataReader` sorgu yürütülürken zaman almış ve türünde bir nesne örneğini döndürür `TResult` içineklenecek`Result` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="18a22-197">Bu durumda, eşleme, birden çok yürütme darbelerin gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="18a22-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="18a22-198">Bu işlev için XAML sıralanabilir ve bildirimli olarak yazılmış (herhangi bir mevcut etkinlik eşlemede katılabilir).</span><span class="sxs-lookup"><span data-stu-id="18a22-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="18a22-199">Sonuç</span><span class="sxs-lookup"><span data-stu-id="18a22-199">Result</span></span>|<span data-ttu-id="18a22-200">Nesnelerinin listesi elde sorgusunun yürütülmesi ve her kayıt için eşleme işlev yürütme doğrulanamadığı `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="18a22-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="18a22-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="18a22-201">DbQueryDataSet</span></span>
 <span data-ttu-id="18a22-202">Döndüren bir sorgu yürütür bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="18a22-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="18a22-203">Bu sınıf, zaman uyumsuz olarak kendi işini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="18a22-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="18a22-204">Öğesinden türetilen <xref:System.Activities.AsyncCodeActivity> < `TResult`> ve zaman uyumsuz özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="18a22-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

 <span data-ttu-id="18a22-205">Bağlantı bilgilerini sağlayıcının değişmez adı ayarlanarak yapılandırılabilir (`ProviderName`) ve bağlantı dizesini (`ConnectionString`) veya yalnızca bir bağlantı dizesi yapılandırma adı kullanarak (`ConfigFileSectionName`) uygulama yapılandırma dosyasına ait.</span><span class="sxs-lookup"><span data-stu-id="18a22-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="18a22-206">Yürütülecek sorgu yapılandırılan kendi `Sql` özelliği ve parametreler aracılığıyla geçirilir `Parameters` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="18a22-207">Sonra `DbQueryDataSet` yürütülür `DataSet` döndürülür `Result out` bağımsız değişken (tür `TResult`, diğer bir deyişle temel sınıfta tanımlanan <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="18a22-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
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

|<span data-ttu-id="18a22-208">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="18a22-208">Argument</span></span>|<span data-ttu-id="18a22-209">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18a22-209">Description</span></span>|
|-|-|
|<span data-ttu-id="18a22-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="18a22-210">ProviderName</span></span>|<span data-ttu-id="18a22-211">ADO.NET sağlayıcısı değişmez adı.</span><span class="sxs-lookup"><span data-stu-id="18a22-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="18a22-212">Bu bağımsız değişken ayarlarsanız, ardından `ConnectionString` de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a22-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="18a22-213">bağlantı dizesi</span><span class="sxs-lookup"><span data-stu-id="18a22-213">ConnectionString</span></span>|<span data-ttu-id="18a22-214">Veritabanına bağlanmak için bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="18a22-214">Connection string to connect to the database.</span></span> <span data-ttu-id="18a22-215">Bu bağımsız değişken, ayarlanırsa `ProviderName` de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a22-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="18a22-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="18a22-216">ConfigName</span></span>|<span data-ttu-id="18a22-217">Bağlantı bilgilerinin depolandığı yapılandırma dosyası bölümün adı.</span><span class="sxs-lookup"><span data-stu-id="18a22-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="18a22-218">Bu bağımsız değişken ayarlandığında `ProviderName` ve `ConnectionString` gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="18a22-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="18a22-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="18a22-219">CommandType</span></span>|<span data-ttu-id="18a22-220">Tür <xref:System.Data.Common.DbCommand> yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="18a22-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="18a22-221">Sql</span><span class="sxs-lookup"><span data-stu-id="18a22-221">Sql</span></span>|<span data-ttu-id="18a22-222">Çalıştırılacak SQL komutu.</span><span class="sxs-lookup"><span data-stu-id="18a22-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="18a22-223">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18a22-223">Parameters</span></span>|<span data-ttu-id="18a22-224">SQL sorgu parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="18a22-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="18a22-225">Sonuç</span><span class="sxs-lookup"><span data-stu-id="18a22-225">Result</span></span>|<xref:System.Data.DataSet> <span data-ttu-id="18a22-226">Sorgu yürütüldükten sonra elde edilir.</span><span class="sxs-lookup"><span data-stu-id="18a22-226">that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="18a22-227">Bağlantı bilgilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="18a22-227">Configuring Connection Information</span></span>
 <span data-ttu-id="18a22-228">Tüm DbActivities aynı yapılandırma parametrelerini paylaşın.</span><span class="sxs-lookup"><span data-stu-id="18a22-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="18a22-229">İki şekilde yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="18a22-229">They can be configured in two ways:</span></span>

-   `ConnectionString + InvariantName`<span data-ttu-id="18a22-230">: ADO.NET sağlayıcısı sabit adı ve bağlantı dizesini ayarlayalım.</span><span class="sxs-lookup"><span data-stu-id="18a22-230">: Set the ADO.NET provider invariant name and connection string.</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<DateTime>()
    {
        ProviderName = "System.Data.SqlClient",
        ConnectionString = @"Data Source=.\SQLExpress;
                             Initial Catalog=DbActivitiesSample;
                             Integrated Security=True",
        Sql = "SELECT GetDate()"
    };
    ```

-   `ConfigName`<span data-ttu-id="18a22-231">: Bağlantı bilgilerini içeren yapılandırma bölümünün adını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="18a22-231">: Set the name of the configuration section that contains the connection information.</span></span>

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

-   <span data-ttu-id="18a22-232">Etkinlik:</span><span class="sxs-lookup"><span data-stu-id="18a22-232">In the activity:</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a><span data-ttu-id="18a22-233">Bu örneği çalıştırmadan</span><span class="sxs-lookup"><span data-stu-id="18a22-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="18a22-234">Kurulum yönergeleri</span><span class="sxs-lookup"><span data-stu-id="18a22-234">Setup instructions</span></span>
 <span data-ttu-id="18a22-235">Bu örnek, bir veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="18a22-235">This sample uses a database.</span></span> <span data-ttu-id="18a22-236">Kurulum ve yükleme komut dosyası (Setup.cmd) örnek ile sağlanır.</span><span class="sxs-lookup"><span data-stu-id="18a22-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="18a22-237">Komut istemi kullanarak bu dosyayı yürütmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a22-237">You must execute that file using the command prompt.</span></span>

 <span data-ttu-id="18a22-238">Setup.cmd betiği aşağıdakileri SQL komutlarını içeren CreateDb.sql komut dosyasını çağırır:</span><span class="sxs-lookup"><span data-stu-id="18a22-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

-   <span data-ttu-id="18a22-239">DbActivitiesSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18a22-239">Creates a database called DbActivitiesSample.</span></span>

-   <span data-ttu-id="18a22-240">Rolleri tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18a22-240">Creates the Roles table.</span></span>

-   <span data-ttu-id="18a22-241">Çalışanlar bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18a22-241">Creates Employees table.</span></span>

-   <span data-ttu-id="18a22-242">Üç kayıt rolleri tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="18a22-242">Inserts three records into the Roles table.</span></span>

-   <span data-ttu-id="18a22-243">On iki kayıtları çalışanlar tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="18a22-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="18a22-244">Setup.cmd çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="18a22-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="18a22-245">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="18a22-245">Open a command prompt.</span></span>

2. <span data-ttu-id="18a22-246">DbActivities örnek klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="18a22-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="18a22-247">"Setup.cmd" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="18a22-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="18a22-248">Setup.cmd yerel makine SqlExpress Örneğinizde örneği yüklemek çalışır.</span><span class="sxs-lookup"><span data-stu-id="18a22-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="18a22-249">Diğer SQL server örneği'nde yüklemek istiyorsanız, Setup.cmd ile yeni örnek adını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="18a22-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="18a22-250">Örnek veritabanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="18a22-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="18a22-251">Örnek klasöründeki bir komut isteminde CleanUp.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="18a22-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="18a22-252">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="18a22-252">To run the sample</span></span>

1. <span data-ttu-id="18a22-253">Visual Studio 2010'da çözümü açın</span><span class="sxs-lookup"><span data-stu-id="18a22-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="18a22-254">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="18a22-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="18a22-255">Hata ayıklama olmadan örneği çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="18a22-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="18a22-256">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="18a22-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="18a22-257">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="18a22-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="18a22-258">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="18a22-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18a22-259">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="18a22-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
