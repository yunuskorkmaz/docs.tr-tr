---
title: Dosyalardan ve diğer kaynaklardan veri yükleme
description: API'yi kullanarak ML.NET işlemek ve işlemek için verileri nasıl yükleyeceğimiz öğrenin. Veriler dosyalarda, veritabanlarında, JSON'da, XML'de veya bellek içi koleksiyonlarda depolanır.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74344749"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="9d0eb-104">Dosyalardan ve diğer kaynaklardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="9d0eb-104">Load data from files and other sources</span></span>

<span data-ttu-id="9d0eb-105">API'yi kullanarak ML.NET işlemek ve işlemek için verileri nasıl yükleyeceğimiz öğrenin.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-105">Learn how to load data for processing and training into ML.NET using the API.</span></span> <span data-ttu-id="9d0eb-106">Veriler başlangıçta dosyalarda veya veritabanları, JSON, XML veya bellek içi koleksiyonlar gibi diğer veri kaynaklarında depolanır.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

<span data-ttu-id="9d0eb-107">Model Oluşturucu kullanıyorsanız, [Model Oluşturucu'ya Yük eğitim verilerine](load-data-model-builder.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-107">If you're using Model Builder, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="9d0eb-108">Veri modelini oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d0eb-108">Create the data model</span></span>

<span data-ttu-id="9d0eb-109">ML.NET, sınıflar aracılığıyla veri modellerini tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-109">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="9d0eb-110">Örneğin, aşağıdaki giriş verileri göz önüne alındığında:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-110">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="9d0eb-111">Aşağıdaki parçacığı temsil eden bir veri modeli oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-111">Create a data model that represents the snippet below:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="9d0eb-112">Veri modelini sütun öznitelikleriyle açıklama</span><span class="sxs-lookup"><span data-stu-id="9d0eb-112">Annotating the data model with column attributes</span></span>

<span data-ttu-id="9d0eb-113">Öznitelikler ML.NET veri modeli ve veri kaynağı hakkında daha fazla bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-113">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="9d0eb-114">Öznitelik, [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) özelliklerinizin sütun dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-114">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d0eb-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)yalnızca bir dosyadan veri yüklerken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="9d0eb-116">Sütunları şu şekilde yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-116">Load columns as:</span></span>

- <span data-ttu-id="9d0eb-117">Sınıf gibi `Size` `CurrentPrices` ve sınıfta ki tek tek sütunlar. `HousingData`</span><span class="sxs-lookup"><span data-stu-id="9d0eb-117">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="9d0eb-118">`HousingData` Sınıftaki gibi `HistoricalPrices` bir vektör şeklinde bir seferde birden çok sütun.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-118">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="9d0eb-119">Bir vektör özelliğiniz varsa, [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliği veri modelinizdeki özelliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-119">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="9d0eb-120">Vektördeki tüm elementlerin aynı türde olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-120">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="9d0eb-121">Sütunları ayrı tutmak özellik mühendisliğinin kolaylığı ve esnekliğini sağlar, ancak çok sayıda sütun için, tek tek sütunlar üzerinde çalışma eğitim hızı üzerinde bir etkiye neden olur.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-121">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="9d0eb-122">ML.NET Sütun adları aracılığıyla çalışır.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-122">ML.NET Operates through column names.</span></span> <span data-ttu-id="9d0eb-123">Bir sütunun adını özellik adından başka bir şeyle değiştirmek [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) istiyorsanız, özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-123">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="9d0eb-124">Bellek içi nesneler oluştururken, özellik adını kullanarak nesneler oluşturmaya devam edebebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-124">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="9d0eb-125">Ancak, veri işleme ve makine öğrenme modelleri oluşturmak için, ML.NET geçersiz [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) kılar ve öznitelik sağlanan değeri ile özelliği başvurur.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-125">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="9d0eb-126">Tek bir dosyadan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="9d0eb-126">Load data from a single file</span></span>

<span data-ttu-id="9d0eb-127">Bir dosyadan veri yüklemek [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) için yüklenecek veriler için veri modeli ile birlikte yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-127">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="9d0eb-128">`separatorChar` Parametre varsayılan olarak sekme delimited olduğundan, gerektiğinde veri dosyanız için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-128">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="9d0eb-129">Dosyanızın üstbilgisi varsa, parametreyi `hasHeader` `true` dosyadaki ilk satırı yoksayacak şekilde ayarlayın ve ikinci satırdan veri yüklemeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-129">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="9d0eb-130">Birden çok dosyadan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="9d0eb-130">Load data from multiple files</span></span>

<span data-ttu-id="9d0eb-131">Verilerinizin birden çok dosyada depolandığı durumlarda, veri şeması aynı olduğu sürece, ML.NET aynı dizinde veya birden çok dizindeki birden çok dosyadan veri yüklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-131">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="9d0eb-132">Dosyalardan tek bir dizindeki yükleme</span><span class="sxs-lookup"><span data-stu-id="9d0eb-132">Load from files in a single directory</span></span>

<span data-ttu-id="9d0eb-133">Tüm veri dosyalarınız aynı dizinde olduğunda, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yöntemde joker karakterleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-133">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="9d0eb-134">Birden çok dizindeki dosyalardan yükleme</span><span class="sxs-lookup"><span data-stu-id="9d0eb-134">Load from files in multiple directories</span></span>

<span data-ttu-id="9d0eb-135">Birden çok dizinden veri [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) yüklemek için, [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)bir .</span><span class="sxs-lookup"><span data-stu-id="9d0eb-135">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="9d0eb-136">Ardından, [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) yöntemi kullanın ve tek tek dosya yollarını belirtin (joker karakterler kullanılamaz).</span><span class="sxs-lookup"><span data-stu-id="9d0eb-136">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="9d0eb-137">İlişkisel bir veritabanından veri yükleme</span><span class="sxs-lookup"><span data-stu-id="9d0eb-137">Load data from a relational database</span></span>

<span data-ttu-id="9d0eb-138">ML.NET, SQL Server, Azure SQL Database, [`System.Data`](xref:System.Data) Oracle, SQLite, PostgreSQL, Progress, IBM DB2 ve daha birçok kişi tarafından desteklenen çeşitli ilişkisel veritabanlarından veri yüklemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-138">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

> [!NOTE]
> <span data-ttu-id="9d0eb-139">`DatabaseLoader` [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet paketini kullanmak için başvuru.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-139">To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.</span></span>

<span data-ttu-id="9d0eb-140">Adlı `House` bir tablo ve aşağıdaki şema ile bir veritabanı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-140">Given a database with a table named `House` and the following schema:</span></span>

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="9d0eb-141">Veriler gibi `HouseData`bir sınıf tarafından modellenebilir.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="9d0eb-142">Daha sonra, uygulamanızın içinde, bir `DatabaseLoader`.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="9d0eb-143">Bağlantı dizenizi ve veritabanında yürütülecek SQL komutunu `DatabaseSource` tanımlayın ve bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="9d0eb-144">Bu örnek, dosya yolu olan bir LocalDB SQL Server veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="9d0eb-145">Ancak, DatabaseLoader veritabanları için şirket içinde ve bulutta başka geçerli bağlantı dizesini destekler.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="9d0eb-146">Türü [`Real`](xref:System.Data.SqlDbType) olmayan sayısal verilerin [`Real`](xref:System.Data.SqlDbType).</span><span class="sxs-lookup"><span data-stu-id="9d0eb-146">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="9d0eb-147">Tür, [`Real`](xref:System.Data.SqlDbType) tek duyarlıklı kayan nokta değeri [`Single`](xref:System.Single)veya ML.NET algoritmaları tarafından beklenen giriş türü olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-147">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="9d0eb-148">Bu örnekte, `NumBed` sütun veritabanında bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-148">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="9d0eb-149">`CAST` Yerleşik işlevi kullanılarak, [`Real`](xref:System.Data.SqlDbType)'ye dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-149">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="9d0eb-150">`Price` Özellik zaten tür [`Real`](xref:System.Data.SqlDbType) olduğundan olduğu gibi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-150">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="9d0eb-151">Verileri `Load` bir [`IDataView`](xref:Microsoft.ML.IDataView)'e yüklemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-151">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="9d0eb-152">Diğer kaynaklardan gelen verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="9d0eb-152">Load data from other sources</span></span>

<span data-ttu-id="9d0eb-153">Dosyalarda depolanan verileri yüklemenin yanı sıra, ML.NET aşağıdakileri içeren ancak bunlarla sınırlı olmayan kaynaklardan veri yüklemeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-153">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="9d0eb-154">Bellek içi koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="9d0eb-154">In-memory collections</span></span>
- <span data-ttu-id="9d0eb-155">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="9d0eb-155">JSON/XML</span></span>

<span data-ttu-id="9d0eb-156">Akış kaynaklarıyla çalışırken, ML.NET girişin bellek içi bir koleksiyon biçiminde olmasını beklediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-156">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="9d0eb-157">Bu nedenle, JSON/XML gibi kaynaklarla çalışırken, verileri bellek içi bir koleksiyona biçimlendirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-157">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="9d0eb-158">Aşağıdaki bellek içi koleksiyon göz önüne alındığında:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-158">Given the following in-memory collection:</span></span>

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

<span data-ttu-id="9d0eb-159">Bellek içi koleksiyonu yöntemle [`IDataView`](xref:Microsoft.ML.IDataView) bir [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yönteme yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9d0eb-159">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d0eb-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)yüklerinin [`IEnumerable`](xref:System.Collections.IEnumerable) iş parçacığı için güvenli olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="9d0eb-161">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9d0eb-161">Next steps</span></span>

- <span data-ttu-id="9d0eb-162">Verileri temizlemek veya başka bir şekilde işlemek [için](prepare-data-ml-net.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="9d0eb-162">To clean or otherwise process data, see [Prepare data for building a model](prepare-data-ml-net.md).</span></span>
- <span data-ttu-id="9d0eb-163">Bir model oluşturmaya hazır olduğunuzda, [Train'e bakın ve bir modeli değerlendirin.](train-machine-learning-model-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="9d0eb-163">When you're ready to build a model, see [Train and evaluate a model](train-machine-learning-model-ml-net.md).</span></span>
