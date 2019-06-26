---
title: Dosyaları ve diğer kaynaklardan veri yükleme
description: Bu nasıl yapılır ML.NET içinde veri işleme ve eğitim için yükleme işlemini göstermektedir. Verileri özgün dosyalar veya veritabanları, JSON, XML veya bellek içi koleksiyonları gibi diğer veri kaynaklarında depolanır.
ms.date: 06/25/2019
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: fafbe3fed9e3f0b509eda4f9d8967965bde19767
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397741"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="47754-104">Dosyaları ve diğer kaynaklardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="47754-104">Load data from files and other sources</span></span>

<span data-ttu-id="47754-105">Bu nasıl yapılır ML.NET içinde veri işleme ve eğitim için yükleme işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="47754-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="47754-106">Verileri özgün dosyalar veya veritabanları, JSON, XML veya bellek içi koleksiyonları gibi diğer veri kaynaklarında depolanır.</span><span class="sxs-lookup"><span data-stu-id="47754-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="47754-107">Veri modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="47754-107">Create the data model</span></span>

<span data-ttu-id="47754-108">ML.NET sınıfları aracılığıyla veri modelleri tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="47754-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="47754-109">Örneğin, aşağıdaki giriş verileri verilen:</span><span class="sxs-lookup"><span data-stu-id="47754-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="47754-110">Aşağıdaki kod parçacığında temsil eden bir veri modeli oluşturun:</span><span class="sxs-lookup"><span data-stu-id="47754-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="47754-111">Veri modeli sütunu özniteliklerle ek açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="47754-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="47754-112">Öznitelikleri ML.NET veri modeli ve veri kaynağı hakkında daha fazla bilgi verin.</span><span class="sxs-lookup"><span data-stu-id="47754-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="47754-113">[ `LoadColumn` ](xref:Microsoft.ML.Data.LoadColumnAttribute) Öznitelik özellikleri sütun dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="47754-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47754-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) olan yalnızca bir dosyadan verileri yüklenirken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="47754-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="47754-115">Sütun olarak yükle:</span><span class="sxs-lookup"><span data-stu-id="47754-115">Load columns as:</span></span> 
- <span data-ttu-id="47754-116">Her bir sütun ister `Size` ve `CurrentPrices` içinde `HousingData` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="47754-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="47754-117">Bir vektör biçiminde bir zaman birden çok sütun ister `HistoricalPrices` içinde `HousingData` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="47754-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="47754-118">Bir vektör özelliği varsa, uygulama [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) veri modelinizde özellik özniteliği.</span><span class="sxs-lookup"><span data-stu-id="47754-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="47754-119">Vektördeki tüm öğeleri aynı türde olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47754-119">It's important to note that all of the elements in the vector need to be the same type.</span></span>

<span data-ttu-id="47754-120">ML.NET Operates aracılığıyla sütun adları.</span><span class="sxs-lookup"><span data-stu-id="47754-120">ML.NET Operates through column names.</span></span> <span data-ttu-id="47754-121">Özellik adı dışında bir şey bir sütunun adını değiştirmek istiyorsanız, kullanın [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="47754-121">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="47754-122">Bellek içi nesneleri oluştururken, yine de özellik adı'nı kullanarak nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47754-122">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="47754-123">Ancak, veri işleme ve yapı makine öğrenimi modellerini, ML.NET geçersiz kılar ve sağlanan değerle özelliğine başvuruyor [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="47754-123">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="47754-124">Tek bir dosyadan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="47754-124">Load data from a single file</span></span>

<span data-ttu-id="47754-125">Bir dosya kullanımdan verileri yüklemek için [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) veri modeline yüklenen verilerin yanı sıra yöntemi.</span><span class="sxs-lookup"><span data-stu-id="47754-125">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="47754-126">Bu yana `separatorChar` parametre varsayılan olarak sekmeyle, veri dosyanızın gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="47754-126">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="47754-127">Üstbilgi dosyanız varsa Ayarla `hasHeader` parametresi `true` dosyanın ilk satırı yoksay ve ikinci satırında veri yüklemeye başlamak için.</span><span class="sxs-lookup"><span data-stu-id="47754-127">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="47754-128">Birden çok dosyadan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="47754-128">Load data from multiple files</span></span>

<span data-ttu-id="47754-129">Aynı veri şemasını olduğu sürece, verilerinizi birden çok dosyasında depolanır, olay, ML.NET, veri ya da aynı dizinde olan birden çok dosya ya da birden çok dizini sağlar.</span><span class="sxs-lookup"><span data-stu-id="47754-129">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="47754-130">Tek bir dizindeki dosyaları yükleme</span><span class="sxs-lookup"><span data-stu-id="47754-130">Load from files in a single directory</span></span>

<span data-ttu-id="47754-131">Tüm veri dosyaları aynı dizinde olduğunda, joker [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="47754-131">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="47754-132">Birden çok dizinlerde dosyaları yükleme</span><span class="sxs-lookup"><span data-stu-id="47754-132">Load from files in multiple directories</span></span>

<span data-ttu-id="47754-133">Birden çok dizinlerden verileri yüklemek için kullanmak [ `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) yöntemi oluşturmak için bir [ `TextLoader` ](xref:Microsoft.ML.Data.TextLoader).</span><span class="sxs-lookup"><span data-stu-id="47754-133">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="47754-134">Ardından, [ `TextLoader.Load` ](xref:Microsoft.ML.DataLoaderExtensions.Load*) yöntemi ve (joker karakterler kullanılamaz) tek tek dosya yollarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="47754-134">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="47754-135">Diğer kaynaklardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="47754-135">Load data from other sources</span></span>

<span data-ttu-id="47754-136">ML.NET dosyalarında depolanan verileri yüklenirken yanı sıra dahil ancak bunlarla sınırlı olmayan kaynaklardan veri yükleme destekler:</span><span class="sxs-lookup"><span data-stu-id="47754-136">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="47754-137">Bellek içi koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="47754-137">In-memory collections</span></span>
- <span data-ttu-id="47754-138">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="47754-138">JSON/XML</span></span>
- <span data-ttu-id="47754-139">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="47754-139">Databases</span></span>

<span data-ttu-id="47754-140">ML.NET kaynakları akış ile çalışırken, bir bellek içi koleksiyonun biçiminde olması için giriş girmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47754-140">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="47754-141">Bu nedenle, JSON/XML gibi kaynaklar ile çalışırken, bir bellek içi koleksiyona verilerin biçimlendirilmesi emin olun.</span><span class="sxs-lookup"><span data-stu-id="47754-141">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="47754-142">Şu bellek içi koleksiyonu verilen:</span><span class="sxs-lookup"><span data-stu-id="47754-142">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="47754-143">Bellek içi koleksiyona bir [ `IDataView` ](xref:Microsoft.ML.IDataView) ile [ `LoadFromEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yöntemi:</span><span class="sxs-lookup"><span data-stu-id="47754-143">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
