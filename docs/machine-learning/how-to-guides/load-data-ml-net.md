---
title: Dosyalardan ve diğer kaynaklardan veri yükleme
description: Bu nasıl yapılır, ML.NET ' ye işleme ve eğitim için nasıl veri yükleneceğini gösterir. Veriler başlangıçta dosyalar veya veritabanları, JSON, XML veya bellek içi Koleksiyonlar gibi diğer veri kaynaklarında depolanır.
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 82a4d19a6296faa6d195e301016b1bf97d483a2c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040797"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="b8b43-104">Dosyalardan ve diğer kaynaklardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="b8b43-104">Load data from files and other sources</span></span>

<span data-ttu-id="b8b43-105">Bu nasıl yapılır, ML.NET ' ye işleme ve eğitim için nasıl veri yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8b43-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="b8b43-106">Veriler başlangıçta dosyalar veya veritabanları, JSON, XML veya bellek içi Koleksiyonlar gibi diğer veri kaynaklarında depolanır.</span><span class="sxs-lookup"><span data-stu-id="b8b43-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="b8b43-107">Veri modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8b43-107">Create the data model</span></span>

<span data-ttu-id="b8b43-108">ML.NET, sınıflar aracılığıyla veri modelleri tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8b43-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="b8b43-109">Örneğin, aşağıdaki giriş verileri verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="b8b43-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="b8b43-110">Aşağıdaki kod parçacığını temsil eden bir veri modeli oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b8b43-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="b8b43-111">Sütun öznitelikleriyle veri modeline açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="b8b43-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="b8b43-112">Öznitelikler, veri modeli ve veri kaynağı hakkında ML.NET daha fazla bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="b8b43-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="b8b43-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) özniteliği, özelliklerinin sütun dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8b43-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8b43-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) yalnızca bir dosyadan veri yüklenirken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8b43-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="b8b43-115">Sütunları şu şekilde yükle:</span><span class="sxs-lookup"><span data-stu-id="b8b43-115">Load columns as:</span></span>

- <span data-ttu-id="b8b43-116">`HousingData` sınıfında `Size` ve `CurrentPrices` gibi bireysel sütunlar.</span><span class="sxs-lookup"><span data-stu-id="b8b43-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="b8b43-117">`HousingData` sınıfında `HistoricalPrices` benzer bir vektör biçiminde tek seferde birden çok sütun.</span><span class="sxs-lookup"><span data-stu-id="b8b43-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="b8b43-118">Vektör özelliği varsa, [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliğini veri modelinizdeki özelliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b8b43-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="b8b43-119">Vektördeki tüm öğelerin aynı türde olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b8b43-119">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="b8b43-120">Sütunların ayrılmış tutulması, özellik mühendisliğinin kolaylığını ve esnekliğini sağlar, ancak çok fazla sayıda sütun için, bireysel sütunlarda çalışan eğitim hızında bir etkiye neden olur.</span><span class="sxs-lookup"><span data-stu-id="b8b43-120">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="b8b43-121">ML.NET, sütun adlarıyla çalışır.</span><span class="sxs-lookup"><span data-stu-id="b8b43-121">ML.NET Operates through column names.</span></span> <span data-ttu-id="b8b43-122">Bir sütunun adını özellik adı dışında bir şekilde değiştirmek istiyorsanız, [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8b43-122">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="b8b43-123">Bellek içi nesneler oluştururken, hala özellik adını kullanarak nesneler oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="b8b43-123">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="b8b43-124">Ancak, veri işleme ve makine öğrenimi modelleri oluşturma için ML.NET, [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğinde belirtilen değeri geçersiz kılar ve özelliğe başvurur.</span><span class="sxs-lookup"><span data-stu-id="b8b43-124">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="b8b43-125">Tek bir dosyadaki verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="b8b43-125">Load data from a single file</span></span>

<span data-ttu-id="b8b43-126">Bir dosyadan veri yüklemek için, yüklenecek verilerin veri modeliyle birlikte [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8b43-126">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="b8b43-127">`separatorChar` parametre varsayılan olarak sekmeyle ayrılmış olduğundan, bunu veri dosyanız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b8b43-127">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="b8b43-128">Dosyanızın bir üstbilgisi varsa, dosyadaki ilk satırı yoksaymak ve ikinci satırdan verileri yüklemeye başlamak için `hasHeader` parametresini `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b8b43-128">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="b8b43-129">Birden çok dosyadan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="b8b43-129">Load data from multiple files</span></span>

<span data-ttu-id="b8b43-130">Verilerinizin birden çok dosyada depolandığından, veri şeması aynı olduğu sürece, ML.NET aynı dizinde veya birden çok dizinde bulunan birden çok dosyadan veri yüklemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="b8b43-130">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="b8b43-131">Tek bir dizindeki dosyalardan yükleme</span><span class="sxs-lookup"><span data-stu-id="b8b43-131">Load from files in a single directory</span></span>

<span data-ttu-id="b8b43-132">Tüm veri dosyalarınız aynı dizinde olduğunda, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yönteminde joker karakterler kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8b43-132">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="b8b43-133">Birden çok dizindeki dosyalardan yükleme</span><span class="sxs-lookup"><span data-stu-id="b8b43-133">Load from files in multiple directories</span></span>

<span data-ttu-id="b8b43-134">Birden çok dizindeki verileri yüklemek için [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) yöntemi kullanarak bir [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b8b43-134">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="b8b43-135">Sonra, [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) yöntemini kullanın ve tek dosya yollarını belirtin (joker karakterler kullanılamaz).</span><span class="sxs-lookup"><span data-stu-id="b8b43-135">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="b8b43-136">İlişkisel veritabanından veri yükleme</span><span class="sxs-lookup"><span data-stu-id="b8b43-136">Load data from a relational database</span></span>

> [!NOTE]
> <span data-ttu-id="b8b43-137">DatabaseLoader Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="b8b43-137">DatabaseLoader is currently in preview.</span></span> <span data-ttu-id="b8b43-138">[Microsoft. ml. deneysel](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview) ve [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) NuGet paketlerine başvurarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8b43-138">It can be used by referencing the [Microsoft.ML.Experimental](https://www.nuget.org/packages/Microsoft.ML.Experimental/0.16.0-preview) and [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient/4.6.1) NuGet packages.</span></span>

<span data-ttu-id="b8b43-139">ML.NET, SQL Server, Azure SQL veritabanı, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 ve çok daha fazlasını içeren [`System.Data`](xref:System.Data) tarafından desteklenen çeşitli ilişkisel veritabanlarından veri yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="b8b43-139">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

<span data-ttu-id="b8b43-140">`House` adlı bir tabloya ve aşağıdaki şemaya sahip bir veritabanı verilirler:</span><span class="sxs-lookup"><span data-stu-id="b8b43-140">Given a database with a table named `House` and the following schema:</span></span>

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="b8b43-141">Veriler `HouseData`gibi bir sınıfla modellenebilir.</span><span class="sxs-lookup"><span data-stu-id="b8b43-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }
    
    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="b8b43-142">Ardından, uygulamanızın içinde bir `DatabaseLoader`oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b8b43-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="b8b43-143">Bağlantı dizenizi ve veritabanında yürütülecek SQL komutunu ve bir `DatabaseSource` örneği oluşturmayı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b8b43-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="b8b43-144">Bu örnek, bir LocalDB SQL Server veritabanını bir dosya yolu ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8b43-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="b8b43-145">Ancak DatabaseLoader, şirket içi ve buluttaki veritabanları için geçerli olan diğer bağlantı dizelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="b8b43-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="b8b43-146">[`Real`](xref:System.Data.SqlDbType) türünde olmayan sayısal verilerin [`Real`](xref:System.Data.SqlDbType)dönüştürülecek olması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="b8b43-146">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="b8b43-147">[`Real`](xref:System.Data.SqlDbType) türü tek duyarlıklı kayan nokta değeri veya [`Single`](xref:System.Single), ml.net algoritmaları tarafından beklenen giriş türü olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="b8b43-147">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="b8b43-148">Bu örnekte, `NumBed` sütunu veritabanındaki bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="b8b43-148">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="b8b43-149">`CAST` yerleşik işlevini kullanarak [`Real`](xref:System.Data.SqlDbType)dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="b8b43-149">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="b8b43-150">`Price` özelliği zaten tür olduğundan [`Real`](xref:System.Data.SqlDbType) olduğu gibi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b8b43-150">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="b8b43-151">Verileri bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklemek için `Load` yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8b43-151">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="b8b43-152">Diğer kaynaklardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="b8b43-152">Load data from other sources</span></span>

<span data-ttu-id="b8b43-153">ML.NET, dosyalarda depolanan verileri yüklemeye ek olarak, dahil edilen ancak bunlarla sınırlı olmayan kaynaklardan veri yüklemeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="b8b43-153">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="b8b43-154">Bellek içi Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="b8b43-154">In-memory collections</span></span>
- <span data-ttu-id="b8b43-155">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="b8b43-155">JSON/XML</span></span>

<span data-ttu-id="b8b43-156">Akış kaynaklarıyla çalışırken ML.NET, girişin bellek içi koleksiyon biçiminde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="b8b43-156">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="b8b43-157">Bu nedenle, JSON/XML gibi kaynaklarla çalışırken, verileri bellek içi bir koleksiyonda biçimlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b8b43-157">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="b8b43-158">Aşağıdaki bellek içi koleksiyon verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="b8b43-158">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="b8b43-159">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yöntemi ile bir [`IDataView`](xref:Microsoft.ML.IDataView) bellek içi toplamayı yükleyin:</span><span class="sxs-lookup"><span data-stu-id="b8b43-159">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8b43-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) , tarafından yüklendiği [`IEnumerable`](xref:System.Collections.IEnumerable) iş parçacığı açısından güvenli olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="b8b43-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="b8b43-161">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="b8b43-161">Next steps</span></span>

<span data-ttu-id="b8b43-162">Makine öğrenimi modelini eğiteiçin model Oluşturucu kullanıyorsanız bkz. [model Oluşturucu 'da eğitim verilerini yükleme](load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="b8b43-162">If you're using Model Builder to train the machine learning model, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>
