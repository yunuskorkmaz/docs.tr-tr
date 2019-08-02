---
title: Dosyalardan ve diğer kaynaklardan veri yükleme
description: Bu nasıl yapılır, ML.NET ' ye işleme ve eğitim için nasıl veri yükleneceğini gösterir. Veriler başlangıçta dosyalar veya veritabanları, JSON, XML veya bellek içi Koleksiyonlar gibi diğer veri kaynaklarında depolanır.
ms.date: 08/01/2019
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: d5f3aab14a60a8c9860dc67f1cc98f3b1b3188ed
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733361"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="0180f-104">Dosyalardan ve diğer kaynaklardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="0180f-104">Load data from files and other sources</span></span>

<span data-ttu-id="0180f-105">Bu nasıl yapılır, ML.NET ' ye işleme ve eğitim için nasıl veri yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0180f-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="0180f-106">Veriler başlangıçta dosyalar veya veritabanları, JSON, XML veya bellek içi Koleksiyonlar gibi diğer veri kaynaklarında depolanır.</span><span class="sxs-lookup"><span data-stu-id="0180f-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="0180f-107">Veri modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="0180f-107">Create the data model</span></span>

<span data-ttu-id="0180f-108">ML.NET, sınıflar aracılığıyla veri modelleri tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0180f-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="0180f-109">Örneğin, aşağıdaki giriş verileri verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="0180f-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="0180f-110">Aşağıdaki kod parçacığını temsil eden bir veri modeli oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0180f-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="0180f-111">Sütun öznitelikleriyle veri modeline açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="0180f-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="0180f-112">Öznitelikler, veri modeli ve veri kaynağı hakkında ML.NET daha fazla bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="0180f-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="0180f-113">Öznitelik [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) , özelliklerinin sütun dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0180f-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0180f-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)yalnızca bir dosyadan veri yüklenirken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0180f-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="0180f-115">Sütunları şu şekilde yükle:</span><span class="sxs-lookup"><span data-stu-id="0180f-115">Load columns as:</span></span> 
- <span data-ttu-id="0180f-116">Sınıfında ve `Size` `CurrentPrices` gibi ayrı sütunlar. `HousingData`</span><span class="sxs-lookup"><span data-stu-id="0180f-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="0180f-117">Sınıf`HousingData` gibi `HistoricalPrices` bir vektör biçiminde tek seferde birden çok sütun.</span><span class="sxs-lookup"><span data-stu-id="0180f-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="0180f-118">Vektör özelliği varsa, [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliğini veri modelinizdeki özelliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="0180f-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="0180f-119">Vektördeki tüm öğelerin aynı türde olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0180f-119">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="0180f-120">Sütunların ayrılmış tutulması, özellik mühendisliğinin kolaylığını ve esnekliğini sağlar, ancak çok fazla sayıda sütun için, bireysel sütunlarda çalışan eğitim hızında bir etkiye neden olur.</span><span class="sxs-lookup"><span data-stu-id="0180f-120">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="0180f-121">ML.NET, sütun adlarıyla çalışır.</span><span class="sxs-lookup"><span data-stu-id="0180f-121">ML.NET Operates through column names.</span></span> <span data-ttu-id="0180f-122">Bir sütunun adını özellik adı dışında bir şekilde değiştirmek istiyorsanız, [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0180f-122">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="0180f-123">Bellek içi nesneler oluştururken, hala özellik adını kullanarak nesneler oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="0180f-123">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="0180f-124">Ancak, veri işleme ve makine öğrenimi modelleri oluşturma için, ml.net geçersiz kılar ve özelliği [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğinde belirtilen değerle başvurur.</span><span class="sxs-lookup"><span data-stu-id="0180f-124">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="0180f-125">Tek bir dosyadaki verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="0180f-125">Load data from a single file</span></span>

<span data-ttu-id="0180f-126">Bir dosyadan veri yüklemek için yöntemini, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yüklenecek verilerin veri modeliyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="0180f-126">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="0180f-127">`separatorChar` Parametre varsayılan olarak sekmeyle ayrılmış olduğundan, bunu veri dosyanız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0180f-127">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="0180f-128">Dosyanızın bir üstbilgisi varsa, `hasHeader` `true` parametresini dosyadaki ilk satırı yoksayacak şekilde ayarlayın ve ikinci satırdan verileri yüklemeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="0180f-128">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="0180f-129">Birden çok dosyadan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="0180f-129">Load data from multiple files</span></span>

<span data-ttu-id="0180f-130">Verilerinizin birden çok dosyada depolandığından, veri şeması aynı olduğu sürece, ML.NET aynı dizinde veya birden çok dizinde bulunan birden çok dosyadan veri yüklemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="0180f-130">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="0180f-131">Tek bir dizindeki dosyalardan yükleme</span><span class="sxs-lookup"><span data-stu-id="0180f-131">Load from files in a single directory</span></span>

<span data-ttu-id="0180f-132">Tüm veri dosyalarınız aynı dizinde olduğunda, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yönteminde joker karakterler kullanın.</span><span class="sxs-lookup"><span data-stu-id="0180f-132">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="0180f-133">Birden çok dizindeki dosyalardan yükleme</span><span class="sxs-lookup"><span data-stu-id="0180f-133">Load from files in multiple directories</span></span>

<span data-ttu-id="0180f-134">Birden çok dizindeki verileri yüklemek için [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) yöntemini kullanarak bir [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0180f-134">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="0180f-135">Ardından, [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) yöntemini kullanın ve tek dosya yollarını belirtin (joker karakterler kullanılamaz).</span><span class="sxs-lookup"><span data-stu-id="0180f-135">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="0180f-136">Diğer kaynaklardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="0180f-136">Load data from other sources</span></span>

<span data-ttu-id="0180f-137">ML.NET, dosyalarda depolanan verileri yüklemeye ek olarak, dahil edilen ancak bunlarla sınırlı olmayan kaynaklardan veri yüklemeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="0180f-137">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="0180f-138">Bellek içi Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="0180f-138">In-memory collections</span></span>
- <span data-ttu-id="0180f-139">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="0180f-139">JSON/XML</span></span>
- <span data-ttu-id="0180f-140">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="0180f-140">Databases</span></span>

<span data-ttu-id="0180f-141">Akış kaynaklarıyla çalışırken ML.NET, girişin bellek içi koleksiyon biçiminde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="0180f-141">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="0180f-142">Bu nedenle, JSON/XML gibi kaynaklarla çalışırken, verileri bellek içi bir koleksiyonda biçimlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0180f-142">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="0180f-143">Aşağıdaki bellek içi koleksiyon verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="0180f-143">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="0180f-144">Bellek içi toplamayı, [`IDataView`](xref:Microsoft.ML.IDataView) [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yöntemiyle bir öğesine yükleyin:</span><span class="sxs-lookup"><span data-stu-id="0180f-144">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0180f-145">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*), [`IEnumerable`](xref:System.Collections.IEnumerable) ' den yüklendiği varsayılmaktadır, iş parçacığı güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="0180f-145">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span> 

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
