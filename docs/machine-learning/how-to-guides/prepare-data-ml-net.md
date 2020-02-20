---
title: Model oluşturmaya yönelik verileri hazırlama
description: Ek işleme veya model oluşturmaya yönelik verileri işlemek ve hazırlamak için ML.NET içindeki dönüştürmeleri nasıl kullanacağınızı öğrenin.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452993"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="e5ea0-103">Model oluşturmaya yönelik verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="e5ea0-103">Prepare data for building a model</span></span>

<span data-ttu-id="e5ea0-104">ML.NET kullanarak ek işleme veya bir model oluşturmaya yönelik verileri hazırlama hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="e5ea0-105">Veriler genellikle temiz ve seyrek yapılır.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="e5ea0-106">ML.NET Machine Learning algoritmaları, giriş veya özelliklerin tek bir sayısal vektörde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="e5ea0-107">Benzer şekilde, tahmin edilecek değer (etiket), özellikle de kategorik veriler, kodlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="e5ea0-108">Bu nedenle, veri hazırlama amaçlarından biri, verileri ML.NET algoritmaları tarafından beklenen biçimde almak.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="e5ea0-109">Verileri Filtrele</span><span class="sxs-lookup"><span data-stu-id="e5ea0-109">Filter data</span></span>

<span data-ttu-id="e5ea0-110">Bazen, bir veri kümesindeki tüm veriler Analize uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="e5ea0-111">İlgisiz verileri kaldırma yaklaşımı filtreleniyor.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="e5ea0-112">[`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) , tüm verileri içeren bir [`IDataView`](xref:Microsoft.ML.IDataView) alıp yalnızca ilgilendiğiniz veri noktalarını içeren bir [ıdataview](xref:Microsoft.ML.IDataView) döndüren bir filtre işlemleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="e5ea0-113">Filtre işlemleri [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)gibi bir [`IEstimator`](xref:Microsoft.ML.IEstimator%601) veya [`ITransformer`](xref:Microsoft.ML.ITransformer) olmadığından, [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) veya [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) veri hazırlama işlem hattının parçası olarak dahil edilemez olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="e5ea0-114">Aşağıdaki giriş verilerini alın ve `data`adlı bir [`IDataView`](xref:Microsoft.ML.IDataView) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="e5ea0-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="e5ea0-115">Bir sütunun değerine göre verileri filtrelemek için [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="e5ea0-116">Yukarıdaki örnek, 200000 ile 1000000 arasında bir fiyata sahip veri kümesindeki satırları alır.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="e5ea0-117">Bu filtreyi uygulamanın sonucu yalnızca verilerdeki son iki satırı döndürür ve fiyatı 100000 olduğundan ve belirtilen Aralık arasında olmadığından ilk satırı dışlayacak.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="e5ea0-118">Eksik değerleri Değiştir</span><span class="sxs-lookup"><span data-stu-id="e5ea0-118">Replace missing values</span></span>

<span data-ttu-id="e5ea0-119">Eksik değerler veri kümelerinde yaygın bir oluşumlardır.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="e5ea0-120">Eksik değerlerle ilgilenmeye yönelik bir yaklaşım, veri içindeki ortalama değer gibi herhangi bir veya başka bir anlamlı değer varsa, bunları verilen türün varsayılan değeriyle değiştirecektir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="e5ea0-121">Aşağıdaki giriş verilerini alın ve `data`adlı bir [`IDataView`](xref:Microsoft.ML.IDataView) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="e5ea0-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="e5ea0-122">Listemizdeki son öğenin `Price`için eksik bir değere sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="e5ea0-123">`Price` sütununda eksik değerleri değiştirmek için [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) metodunu kullanarak eksik değeri girin.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5ea0-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) yalnızca sayısal verilerle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="e5ea0-125">ML.NET çeşitli [değiştirme modlarını](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)destekler.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="e5ea0-126">Yukarıdaki örnek, eksik değeri bu sütunun ortalama değeriyle dolduran `Mean` değiştirme modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="e5ea0-127">Değiştirme işleminin sonucu, 100.000 ve 300.000 ortalaması olduğundan, 200.000 ile verilerdeki son öğenin `Price` özelliğini doldurur.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="e5ea0-128">Normalleyiciler kullanma</span><span class="sxs-lookup"><span data-stu-id="e5ea0-128">Use normalizers</span></span>

<span data-ttu-id="e5ea0-129">[Normalleştirme](https://en.wikipedia.org/wiki/Feature_scaling) , bir makine öğrenimi algoritması tarafından daha doğru işlenebilmeleri için, özellikleri genellikle 0 ile 1 arasında olacak şekilde ölçeklendirmek için kullanılan bir veri ön işleme tekniğidir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="e5ea0-130">Örneğin, yaş ve gelir aralıkları genellikle, 0-100 ve gelirin genellikle sıfır-binlerce aralığında olması bakımından yaş açısından önemli ölçüde farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="e5ea0-131">Daha ayrıntılı bir liste ve normalleştirme dönüştürmelerini açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="e5ea0-132">Minimum-en fazla normalleştirme</span><span class="sxs-lookup"><span data-stu-id="e5ea0-132">Min-Max normalization</span></span>

<span data-ttu-id="e5ea0-133">Aşağıdaki giriş verilerini alın ve `data`adlı bir [`IDataView`](xref:Microsoft.ML.IDataView) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="e5ea0-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="e5ea0-134">Normalleştirme, tek bir sayısal değere ve vektörlerine sahip sütunlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="e5ea0-135">`Price` sütunundaki verileri, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) yöntemiyle Min-Max normalleştirmesini kullanarak normalleştirin.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="e5ea0-136">`[200000,100000]` orijinal fiyat değerleri, 0-1 aralığında çıkış değerleri üreten `MinMax` normalleştirme formülü kullanılarak `[ 1, 0.5 ]` dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="e5ea0-137">Gruplama</span><span class="sxs-lookup"><span data-stu-id="e5ea0-137">Binning</span></span>

<span data-ttu-id="e5ea0-138">[Binme](https://en.wikipedia.org/wiki/Data_binning) , sürekli değerleri girişin ayrı bir gösterimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="e5ea0-139">Örneğin, özelliklerden birinin yaş olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="e5ea0-140">Bini gerçek yaş değerini kullanmak yerine, bu değer için aralıklar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="e5ea0-141">0-18 bir bin olabilir, diğeri 19-35 olabilir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="e5ea0-142">Aşağıdaki giriş verilerini alın ve `data`adlı bir [`IDataView`](xref:Microsoft.ML.IDataView) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="e5ea0-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="e5ea0-143">[`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) yöntemi kullanarak verileri depo gözleri halinde normalleştirin.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="e5ea0-144">`maximumBinCount` parametresi, verilerinizi sınıflandırmak için gereken bölme sayısını belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="e5ea0-145">Bu örnekte, veriler iki bölme içine alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="e5ea0-146">Binme sonucu `[0,200000,Infinity]`bin sınırlarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="e5ea0-147">Bu nedenle, ilk gözlem 0-200000 arasında ve diğerleri 200000 ' den büyük ancak sonsuz ' dan az olduğu için ortaya çıkan depo gözleri `[0,1,1]`.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="e5ea0-148">Kategorik verilerle çalışma</span><span class="sxs-lookup"><span data-stu-id="e5ea0-148">Work with categorical data</span></span>

<span data-ttu-id="e5ea0-149">En yaygın veri türlerinden biri kategorik verilerden biridir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="e5ea0-150">Kategorik verilerin sınırlı sayıda kategorisi vardır.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="e5ea0-151">Örneğin, ABD 'nin durumları veya bir resim kümesinde bulunan hayvanlar türlerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="e5ea0-152">Kategorik verilerin özellikler ya da Etiketler olup olmadığı, bir makine öğrenimi modeli oluşturmak için kullanılabilmesi için bunların sayısal bir değerle eşlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="e5ea0-153">ML.NET ' de kategorik verilerle çalışmanın çeşitli yolları, çözmenize çalıştığınız soruna bağlı olarak vardır.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="e5ea0-154">Anahtar değer eşleme</span><span class="sxs-lookup"><span data-stu-id="e5ea0-154">Key value mapping</span></span>

<span data-ttu-id="e5ea0-155">ML.NET ' de, anahtar bir kategoriyi temsil eden bir tamsayı değeridir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="e5ea0-156">Anahtar değeri eşleme, genellikle dize etiketlerini eğitimin benzersiz tamsayı değerleriyle eşlemek için kullanılır, ardından model bir tahmin yapmak için kullanıldığında dize değerlerine geri dönün.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="e5ea0-157">Anahtar değer eşlemesini gerçekleştirmek için kullanılan dönüşümler [Mapvaluetokey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) ve [Mapkeytovalue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A)' lardır.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="e5ea0-158">`MapValueToKey`, bir tahmin yaparken `MapKeyToValue` ters dönüştürmeyi gerçekleştirebilmesi için modeldeki eşlemelerin bir sözlüğünü ekler.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="e5ea0-159">Tek bir etkin kodlama</span><span class="sxs-lookup"><span data-stu-id="e5ea0-159">One hot encoding</span></span>

<span data-ttu-id="e5ea0-160">Bir sıcak kodlama, sınırlı bir değer kümesi alır ve bunları ikili temsilinin dizedeki benzersiz konumlarda tek bir `1` değerine sahip olan tamsayılara eşler.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="e5ea0-161">Kategorik verilerin örtük bir sıralaması yoksa, tek bir sık kullanılan kodlama en iyi seçim olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="e5ea0-162">Aşağıdaki tabloda, ham değerler olarak ZIP kodlarına sahip bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="e5ea0-163">Ham değer</span><span class="sxs-lookup"><span data-stu-id="e5ea0-163">Raw value</span></span>|<span data-ttu-id="e5ea0-164">Sık kodlanmış bir değer</span><span class="sxs-lookup"><span data-stu-id="e5ea0-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="e5ea0-165">98052</span><span class="sxs-lookup"><span data-stu-id="e5ea0-165">98052</span></span>|<span data-ttu-id="e5ea0-166">00... 01</span><span class="sxs-lookup"><span data-stu-id="e5ea0-166">00...01</span></span>|
|<span data-ttu-id="e5ea0-167">98100</span><span class="sxs-lookup"><span data-stu-id="e5ea0-167">98100</span></span>|<span data-ttu-id="e5ea0-168">00... 10</span><span class="sxs-lookup"><span data-stu-id="e5ea0-168">00...10</span></span>|
|<span data-ttu-id="e5ea0-169">...</span><span class="sxs-lookup"><span data-stu-id="e5ea0-169">...</span></span>|<span data-ttu-id="e5ea0-170">...</span><span class="sxs-lookup"><span data-stu-id="e5ea0-170">...</span></span>|
|<span data-ttu-id="e5ea0-171">98109</span><span class="sxs-lookup"><span data-stu-id="e5ea0-171">98109</span></span>|<span data-ttu-id="e5ea0-172">10... 00</span><span class="sxs-lookup"><span data-stu-id="e5ea0-172">10...00</span></span>|

<span data-ttu-id="e5ea0-173">Kategorik verileri tek başına kodlanmış sayılara dönüştürecek dönüşüm [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span><span class="sxs-lookup"><span data-stu-id="e5ea0-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="e5ea0-174">Karma</span><span class="sxs-lookup"><span data-stu-id="e5ea0-174">Hashing</span></span>

<span data-ttu-id="e5ea0-175">Karma oluşturma, kategorik verileri sayılara dönüştürmek için başka bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="e5ea0-176">Karma işlevi rastgele boyuttaki verileri (örneğin, metin dizesi) sabit bir aralığa göre bir sayıya eşler.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="e5ea0-177">Karma özellikleri, özelliklerin vektörleştirilmesi için hızlı ve verimli bir yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="e5ea0-178">Machine Learning 'de karma hale getirilmiş bir önemli örneği, bilinen sözcüklerin bir sözlüğünü tutmak yerine, e-postadaki her sözcüğün karma hale getirilmiş ve büyük bir özellik vektörüne eklendiği e-posta istenmeyen posta filtrelemedir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="e5ea0-179">Bu şekilde karma kullanılması, sözlükte olmayan sözcüklerin kullanımı ile ilgili kötü amaçlı posta filtreleme sorunu yaşamasını önler.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="e5ea0-180">ML.NET metin, tarih ve sayısal veriler üzerinde karma hale getirmek için [karma](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) dönüşüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="e5ea0-181">Değer anahtarı eşleme gibi, karma dönüştürmenin çıkışları anahtar türlerdir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="e5ea0-182">Metin verileriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="e5ea0-182">Work with text data</span></span>

<span data-ttu-id="e5ea0-183">Kategorik veriler gibi, metin verilerinin bir makine öğrenimi modeli oluşturmak için kullanılmadan önce sayısal özelliklere dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="e5ea0-184">Daha ayrıntılı bir liste ve metin dönüştürmelerini açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="e5ea0-185">Bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenmiş olan veriler gibi verileri kullanma:</span><span class="sxs-lookup"><span data-stu-id="e5ea0-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="e5ea0-186">ML.NET, bir metnin dize değerini alan ve bir dizi tekil dönüştürme uygulayarak metinden bir özellikler kümesi oluşturan [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) dönüşümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="e5ea0-187">Elde edilen dönüşüm, `Description` sütunundaki metin değerlerini aşağıdaki çıkışa benzer bir sayısal vector öğesine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="e5ea0-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="e5ea0-188">`FeaturizeText` oluşturan dönüşümler, özellik üretimi üzerinde daha ince denetim için ayrı ayrı de uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="e5ea0-189">`textEstimator`, [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) yöntemi tarafından gerçekleştirilen işlemlerin bir alt kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="e5ea0-190">Daha karmaşık bir işlem hattının avantajı, verilere uygulanan dönüşümlere göre denetim ve görünürlük sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5ea0-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="e5ea0-191">Örnek olarak ilk girdiyi kullanarak aşağıda, `textEstimator`tarafından tanımlanan dönüştürme adımları tarafından oluşturulan sonuçların ayrıntılı bir açıklaması verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e5ea0-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="e5ea0-192">**Özgün metin: Bu iyi bir üründür**</span><span class="sxs-lookup"><span data-stu-id="e5ea0-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="e5ea0-193">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e5ea0-193">Transform</span></span> | <span data-ttu-id="e5ea0-194">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5ea0-194">Description</span></span> | <span data-ttu-id="e5ea0-195">Sonuç</span><span class="sxs-lookup"><span data-stu-id="e5ea0-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="e5ea0-196">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="e5ea0-196">1. NormalizeText</span></span> | <span data-ttu-id="e5ea0-197">Varsayılan olarak tüm harfleri küçük harfe dönüştürür</span><span class="sxs-lookup"><span data-stu-id="e5ea0-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="e5ea0-198">Bu iyi bir üründür</span><span class="sxs-lookup"><span data-stu-id="e5ea0-198">this is a good product</span></span>
|<span data-ttu-id="e5ea0-199">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="e5ea0-199">2. TokenizeWords</span></span> | <span data-ttu-id="e5ea0-200">Dizeyi tek tek sözcüklere böler</span><span class="sxs-lookup"><span data-stu-id="e5ea0-200">Splits string into individual words</span></span> | <span data-ttu-id="e5ea0-201">["This", "dir", "a", "iyidir", "Product"]</span><span class="sxs-lookup"><span data-stu-id="e5ea0-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="e5ea0-202">3. Removedefaultstopkelimeleri</span><span class="sxs-lookup"><span data-stu-id="e5ea0-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="e5ea0-203">*Ve gibi* stopsözcüklerini *kaldırır.*</span><span class="sxs-lookup"><span data-stu-id="e5ea0-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="e5ea0-204">["iyi", "ürün"]</span><span class="sxs-lookup"><span data-stu-id="e5ea0-204">["good","product"]</span></span>
|<span data-ttu-id="e5ea0-205">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="e5ea0-205">4. MapValueToKey</span></span> | <span data-ttu-id="e5ea0-206">Değerleri, giriş verilerine göre anahtarlar (kategoriler) ile eşler</span><span class="sxs-lookup"><span data-stu-id="e5ea0-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="e5ea0-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="e5ea0-207">[1,2]</span></span>
|<span data-ttu-id="e5ea0-208">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="e5ea0-208">5. ProduceNGrams</span></span> | <span data-ttu-id="e5ea0-209">Metni birbirini izleyen sözcüklerin sıralamasına dönüştürür</span><span class="sxs-lookup"><span data-stu-id="e5ea0-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="e5ea0-210">[1, 1, 1, 0, 0]</span><span class="sxs-lookup"><span data-stu-id="e5ea0-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="e5ea0-211">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="e5ea0-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="e5ea0-212">Girdileri LP-norm olarak ölçeklendirin</span><span class="sxs-lookup"><span data-stu-id="e5ea0-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="e5ea0-213">[0,577350529, 0,577350529, 0,577350529, 0, 0]</span><span class="sxs-lookup"><span data-stu-id="e5ea0-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
