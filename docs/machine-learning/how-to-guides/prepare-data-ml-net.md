---
title: Verileri hazırlama
description: Dönüşümler ML.NET yönetmek ve ek işlem için verileri hazırlama veya yapı modeli için kullanmayı öğrenin.
author: luisquintanilla
ms.author: luquinta
ms.date: 05/03/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 461a00c6ecc1d9a8b9caaca79f9d7905d2bb7528
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063469"
---
# <a name="prepare-data"></a><span data-ttu-id="0b723-103">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="0b723-103">Prepare Data</span></span>

<span data-ttu-id="0b723-104">ML.NET ek işleme veya bir model oluşturmak için veri hazırlamak için kullanmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="0b723-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="0b723-105">Genellikle şekilde çoğaltamaması ve aralıklı verilerdir.</span><span class="sxs-lookup"><span data-stu-id="0b723-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="0b723-106">Ayrıca, giriş veya tek bir sayısal vektörü olarak özellikleri ML.NET makine öğrenimi algoritmaları bekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="0b723-106">Additionally, ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="0b723-107">Bu nedenle veri hazırlama hedeflerinden ML.NET algoritmalarda beklenen biçime verilerinin elde edilmesidir.</span><span class="sxs-lookup"><span data-stu-id="0b723-107">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span> 

## <a name="filter-data"></a><span data-ttu-id="0b723-108">Verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="0b723-108">Filter data</span></span>

<span data-ttu-id="0b723-109">Bazı durumlarda, veri kümesindeki tüm verileri analiz için ilgili.</span><span class="sxs-lookup"><span data-stu-id="0b723-109">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="0b723-110">İlgisiz verilerin kaldırmak için bir yaklaşım filtreleme.</span><span class="sxs-lookup"><span data-stu-id="0b723-110">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="0b723-111">[ `DataOperationsCatalog` ](xref:Microsoft.ML.DataOperationsCatalog) Olur filtresi işlemlerini kümesini içeren bir [ `IDataView` ](xref:Microsoft.ML.IDataView) tüm dönüş ve veri içeren bir [IDataView](xref:Microsoft.ML.IDataView) yalnızca içeren ilgi çekici veri noktaları.</span><span class="sxs-lookup"><span data-stu-id="0b723-111">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="0b723-112">Filtre işlemler atomik değildir çünkü dikkat etmeniz önemlidir bir [ `IEstimator` ](xref:Microsoft.ML.IEstimator%601) veya [ `ITransformer` ](xref:Microsoft.ML.ITransformer) ister de [ `TransformsCatalog` ](xref:Microsoft.ML.TransformsCatalog), bunlar olamaz parçası olarak dahil edilen bir [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) veya [ `TransformerChain` ](xref:Microsoft.ML.Data.TransformerChain%601) veri hazırlama işlem hattı.</span><span class="sxs-lookup"><span data-stu-id="0b723-112">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span> 

<span data-ttu-id="0b723-113">Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="0b723-113">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="0b723-114">Verilere bir sütun değerine göre filtre uygulamak için kullanma [ `FilterRowsByColumn` ](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b723-114">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="0b723-115">Yukarıdaki örnek veri kümesiyle birlikte bir fiyat 200000 ile 1000000 arasında satırları alır.</span><span class="sxs-lookup"><span data-stu-id="0b723-115">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="0b723-116">Bu filtre sonucu verileri yalnızca son iki satırını döndürür ve ancak ilk satırın tutma olduğundan bunun ücreti 100000 ve belirtilen aralık arasında değil.</span><span class="sxs-lookup"><span data-stu-id="0b723-116">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="0b723-117">Eksik değerleri Değiştir</span><span class="sxs-lookup"><span data-stu-id="0b723-117">Replace missing values</span></span>

<span data-ttu-id="0b723-118">Veri kümelerinde sık karşılaştıkları eksik değerler.</span><span class="sxs-lookup"><span data-stu-id="0b723-118">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="0b723-119">Eksik değerleri ilgilenmek için bir yaklaşım ise bunları verilen tür için varsayılan değer ya da başka bir değiştirmek için ortalama değer gibi anlamlı bir değer.</span><span class="sxs-lookup"><span data-stu-id="0b723-119">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span> 

<span data-ttu-id="0b723-120">Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="0b723-120">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=float.NaN
    }
};
```

<span data-ttu-id="0b723-121">Listemize içerisindeki son öğe için eksik değer olduğunu fark `Price`.</span><span class="sxs-lookup"><span data-stu-id="0b723-121">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="0b723-122">Eksik değerleri değiştirmek için `Price` sütun kullanımı [ `ReplaceMissingValues` ](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) eksik değeri doldurmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b723-122">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b723-123">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) yalnızca sayısal verilerle çalışır.</span><span class="sxs-lookup"><span data-stu-id="0b723-123">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="0b723-124">ML.NET destekleyen çeşitli [değiştirme modları](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="0b723-124">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="0b723-125">Örnek kullanımlar yukarıda `Mean` değiştirme modu, bir eksik değeri söz konusu sütunun ortalama değer ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="0b723-125">The sample above uses the `Mean` replacement mode which will fill in the missing value with that column's average value.</span></span> <span data-ttu-id="0b723-126">Değiştirme'nin sonucu doldurur `Price` verilerimizi 100.000 ve 300000 ortalamasını olduğundan 200.000 ile içerisindeki son öğe özelliği.</span><span class="sxs-lookup"><span data-stu-id="0b723-126">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span> 

## <a name="use-normalizers"></a><span data-ttu-id="0b723-127">Normalizers kullanın</span><span class="sxs-lookup"><span data-stu-id="0b723-127">Use normalizers</span></span>

<span data-ttu-id="0b723-128">[Normalleştirme](https://en.wikipedia.org/wiki/Feature_scaling) aynı ölçekte daha hızlı yakınsama algoritmaları yardımcı olan özellikleri standart hale getirmek için kullanılan bir teknik ön işleme bir veri.</span><span class="sxs-lookup"><span data-stu-id="0b723-128">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to standardize features that are not on the same scale which helps algorithms converge faster.</span></span> <span data-ttu-id="0b723-129">Örneğin, yaş ve gelir gibi değerler için aralıklar, genellikle genellikle sıfır binlerce aralığında olan gelir ve 0-100 aralığında olması geçerlilik süresi ile önemli ölçüde farklılık.</span><span class="sxs-lookup"><span data-stu-id="0b723-129">For example, the ranges for values like age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="0b723-130">Ziyaret [dönüşümler sayfa](../resources/transforms.md) daha ayrıntılı bir listesi ve normalleştirme dönüşümler açıklaması.</span><span class="sxs-lookup"><span data-stu-id="0b723-130">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span> 

### <a name="min-max-normalization"></a><span data-ttu-id="0b723-131">Min-Maks normalleştirme</span><span class="sxs-lookup"><span data-stu-id="0b723-131">Min-Max normalization</span></span>

<span data-ttu-id="0b723-132">Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="0b723-132">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms = 2f,
        Price = 200000f
    },
    new HomeData
    {
        NumberOfBedrooms = 1f,
        Price = 100000f
    }
};
```

<span data-ttu-id="0b723-133">Min-Maks normalleştirme kullanarak veri Normalleştir [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b723-133">Normalize the data using min-max normalization using the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="0b723-134">Özgün fiyat değerlerini `[200000,100000]` dönüştürülür `[ 1, 0.5 ]` kullanarak `MinMax` normalleştirme formül, bir çıkış değerleri 0-1 aralığında oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b723-134">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula which generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="0b723-135">Gruplama</span><span class="sxs-lookup"><span data-stu-id="0b723-135">Binning</span></span>

<span data-ttu-id="0b723-136">[Gruplama](https://en.wikipedia.org/wiki/Data_binning) sürekli değerleri ayrık bir giriş gösterimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0b723-136">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="0b723-137">Örneğin, yaş, özelliklerden biri olduğunu varsayın.</span><span class="sxs-lookup"><span data-stu-id="0b723-137">For example, suppose one of your features is age.</span></span> <span data-ttu-id="0b723-138">Gruplama gerçek yaş değeri kullanmak yerine, bu değer aralıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b723-138">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="0b723-139">0-18 bir depo olabilir, başka bir 19-35 vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b723-139">0-18 could be one bin, another could be 19-35 and so on.</span></span> 

<span data-ttu-id="0b723-140">Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="0b723-140">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="0b723-141">Verileri kullanarak bölmeler Normalleştir [ `NormalizeBinning` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b723-141">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) method.</span></span> <span data-ttu-id="0b723-142">`maximumBinCount` Parametresi verilerinizi sınıflandırmak için gereken depo sayısını belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b723-142">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="0b723-143">Bu örnekte, verileri iki depo yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0b723-143">In this example, data will be put into two bins.</span></span>  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="0b723-144">Depo sınırları gruplama sonucunu oluşturur `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="0b723-144">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="0b723-145">Bu nedenle sonuç depo olan `[0,1,1]` ilk gözlem 0 200000 ve diğerleri arasında olduğundan 200000 büyüktür, ancak sonsuza küçüktür.</span><span class="sxs-lookup"><span data-stu-id="0b723-145">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="0b723-146">Kategorik verileri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="0b723-146">Work with categorical data</span></span>

<span data-ttu-id="0b723-147">Bir machine learning modeli oluşturmak için kullanılmadan önce bir sayıya dönüştürülecek sayısal olmayan sütunları ise kategorik veriler gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b723-147">Non-numeric categorical data needs to be converted to a number before being used to build a machine learning model.</span></span> 

<span data-ttu-id="0b723-148">Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="0b723-148">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
CarData[] cars = new CarData[] 
{
    new CarData
    {
        Color="Red",
        VehicleType="SUV"
    },
    new CarData
    {
        Color="Blue",
        VehicleType="Sedan"
    },
    new CarData
    {
        Color="Black",
        VehicleType="SUV"
    }
};
```

<span data-ttu-id="0b723-149">Kategorik `VehicleType` özelliği, bir sayı kullanarak dönüştürülebilir [ `OneHotEncoding` ](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b723-149">The categorical `VehicleType` property can be converted into a number using the [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) method.</span></span> 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

<span data-ttu-id="0b723-150">Metin değerini elde edilen dönüştürme dönüştürür `VehicleType` bir sayı.</span><span class="sxs-lookup"><span data-stu-id="0b723-150">The resulting transform converts the text value of `VehicleType` to a number.</span></span> <span data-ttu-id="0b723-151">Girdileri `VehicleType` sütun dönüştürme uygulandığında şu olur:</span><span class="sxs-lookup"><span data-stu-id="0b723-151">The entries in the `VehicleType` column become the following when the transform is applied:</span></span> 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a><span data-ttu-id="0b723-152">Metin verileri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="0b723-152">Work with text data</span></span>

<span data-ttu-id="0b723-153">Bir machine learning modeli oluşturmak üzere kullanmadan önce sayıya Dönüştürülecek metin verileri gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b723-153">Text data needs to be transformed into numbers before using it to build a machine learning model.</span></span> <span data-ttu-id="0b723-154">Ziyaret [dönüşümler sayfa](../resources/transforms.md) daha ayrıntılı bir listesi ve metin dönüştürmeleri açıklaması.</span><span class="sxs-lookup"><span data-stu-id="0b723-154">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="0b723-155">Aşağıdaki verileri içine yüklenmiş gibi verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="0b723-155">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
ReviewData[] reviews = new ReviewData[]
{
    new ReviewData
    {
        Description="This is a good product",
        Rating=4.7f
    },
    new ReviewData
    {
        Description="This is a bad product",
        Rating=2.3f
    }
};
```

<span data-ttu-id="0b723-156">Metni bir sayısal vektör gösterimine dönüştürmek için en az bir adımda [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b723-156">The minimum step to convert text to a numerical vector representation is to use the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="0b723-157">Kullanarak [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) dönüştürme, bir dizi dönüşümleri lp normalleştirilmiş word ve karakter ngrams temsil eden sayısal bir vektör içinde elde edilen giriş metin sütununu uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0b723-157">By using the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transform, a series of transformations is applied to the input text column resulting in a numerical vector representing the lp-normalized word and character ngrams.</span></span> 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="0b723-158">Sonuçta elde edilen dönüştürme metin değerleri dönüştürecektir `Description` aşağıdaki çıktıya benzer bir sayısal vektör sütunu:</span><span class="sxs-lookup"><span data-stu-id="0b723-158">The resulting transform would convert the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="0b723-159">Birleştirme karmaşık metin işleme adımları içine bir [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) gürültü kaldırın ve potansiyel olarak gerektiğinde, gerekli işlem kaynaklarının miktarını azaltmak için.</span><span class="sxs-lookup"><span data-stu-id="0b723-159">Combine complex text processing steps into an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) to remove noise and potentially reduce the amount of required processing resources as needed.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="0b723-160">`textEstimator` bir alt kümesini tarafından gerçekleştirilen işlemleri içeren [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b723-160">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="0b723-161">Daha karmaşık bir işlem hattının avantajı denetim ve görünürlüğü verilere uygulanan dönüştürmeler biter.</span><span class="sxs-lookup"><span data-stu-id="0b723-161">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span> 

<span data-ttu-id="0b723-162">Örnek kullanıldığında ilk giriş tarafından tanımlanan dönüştürme adımı tarafından üretilen sonuçlar ayrıntılı bir açıklaması verilmiştir `textEstimator`:</span><span class="sxs-lookup"><span data-stu-id="0b723-162">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="0b723-163">**Orijinal metni: Bu iyi bir üründür**</span><span class="sxs-lookup"><span data-stu-id="0b723-163">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="0b723-164">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0b723-164">Transform</span></span> | <span data-ttu-id="0b723-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b723-165">Description</span></span> | <span data-ttu-id="0b723-166">Sonuç</span><span class="sxs-lookup"><span data-stu-id="0b723-166">Result</span></span>
|--|--|--|
|<span data-ttu-id="0b723-167">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="0b723-167">1. NormalizeText</span></span> | <span data-ttu-id="0b723-168">Tüm harfleri küçük harfe varsayılan olarak dönüştürür</span><span class="sxs-lookup"><span data-stu-id="0b723-168">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="0b723-169">Bu iyi bir üründür</span><span class="sxs-lookup"><span data-stu-id="0b723-169">this is a good product</span></span>
|<span data-ttu-id="0b723-170">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="0b723-170">2. TokenizeWords</span></span> | <span data-ttu-id="0b723-171">Bölmelerini kelimeler dizeye</span><span class="sxs-lookup"><span data-stu-id="0b723-171">Splits string into individual words</span></span> | <span data-ttu-id="0b723-172">["Bu", "is", "bir","iyi","product"]</span><span class="sxs-lookup"><span data-stu-id="0b723-172">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="0b723-173">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="0b723-173">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="0b723-174">Durdurma sözcükleri gibi kaldırır *olduğu* ve *bir*.</span><span class="sxs-lookup"><span data-stu-id="0b723-174">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="0b723-175">["good", "product"]</span><span class="sxs-lookup"><span data-stu-id="0b723-175">["good","product"]</span></span>
|<span data-ttu-id="0b723-176">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="0b723-176">4. MapValueToKey</span></span> | <span data-ttu-id="0b723-177">Anahtarları (Kategoriler) giriş verileri temel alan değerleri eşleyen</span><span class="sxs-lookup"><span data-stu-id="0b723-177">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="0b723-178">[1,2]</span><span class="sxs-lookup"><span data-stu-id="0b723-178">[1,2]</span></span>
|<span data-ttu-id="0b723-179">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="0b723-179">5. ProduceNGrams</span></span> | <span data-ttu-id="0b723-180">Metin ardışık sözcükleri dizisine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0b723-180">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="0b723-181">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="0b723-181">[1,1,1,0,0]</span></span>
|<span data-ttu-id="0b723-182">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="0b723-182">6. NormalizeLpNorm</span></span> | <span data-ttu-id="0b723-183">Kendi lp norm tarafından ölçek girişleri</span><span class="sxs-lookup"><span data-stu-id="0b723-183">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="0b723-184">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="0b723-184">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
