---
title: Model oluşturmak için veri hazırlama
description: Ek işleme veya model oluşturma için verileri işlemek ve hazırlamak için ML.NET dönüşümleri nasıl kullanacağınızı öğrenin.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77452993"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="62183-103">Model oluşturmak için veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="62183-103">Prepare data for building a model</span></span>

<span data-ttu-id="62183-104">Ek işleme veya model oluşturmak için veri hazırlamak için ML.NET nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="62183-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="62183-105">Veriler genellikle kirli ve seyrektir.</span><span class="sxs-lookup"><span data-stu-id="62183-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="62183-106">ML.NET makine öğrenimi algoritmaları girdi veya özelliklerin tek bir sayısal vektörde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="62183-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="62183-107">Benzer şekilde, tahmin edilecek değer (etiket), özellikle kategorik veriler olduğunda, kodlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62183-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="62183-108">Bu nedenle veri hazırlamanın amaçlarından biri, verileri ML.NET algoritmaları tarafından beklenen biçime getirmektir.</span><span class="sxs-lookup"><span data-stu-id="62183-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="62183-109">Verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="62183-109">Filter data</span></span>

<span data-ttu-id="62183-110">Bazen, bir veri kümesindeki tüm veriler çözümleme için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="62183-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="62183-111">Alakasız verileri kaldırmak için bir yaklaşım filtreleme olduğunu.</span><span class="sxs-lookup"><span data-stu-id="62183-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="62183-112">Tüm [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) verileri içeren ve [`IDataView`](xref:Microsoft.ML.IDataView) yalnızca ilgi çekici veri noktalarını içeren bir [IDataView](xref:Microsoft.ML.IDataView) döndüren bir filtre işlemleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="62183-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="62183-113">Filtre [`IEstimator`](xref:Microsoft.ML.IEstimator%601) işlemleri bir veya [`ITransformer`](xref:Microsoft.ML.ITransformer) benzeri olmadığı [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)için, bir [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) veya [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) veri hazırlama ardışık hattının bir parçası olarak dahil edilemeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="62183-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="62183-114">Aşağıdaki giriş verilerini alın ve [`IDataView`](xref:Microsoft.ML.IDataView) aşağıdaki `data`bir çağrıya yükleyin:</span><span class="sxs-lookup"><span data-stu-id="62183-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="62183-115">Verileri sütunun değerine göre filtrelemek [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="62183-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="62183-116">Yukarıdaki örnek, 200000 ile 100000 arasında bir fiyatla veri kümesindeki satırları alır.</span><span class="sxs-lookup"><span data-stu-id="62183-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="62183-117">Bu filtreyi uygulamanın sonucu, verilerdeki yalnızca son iki satırı döndürür ve fiyatı 100.000 olduğundan ve belirtilen aralık arasında olmadığından ilk satırı hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="62183-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="62183-118">Eksik değerleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="62183-118">Replace missing values</span></span>

<span data-ttu-id="62183-119">Eksik değerler veri kümelerinde sık karşılaşılan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="62183-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="62183-120">Eksik değerlerle başa çıkmak için bir yaklaşım, verilerdeki ortalama değer gibi herhangi biri veya başka bir anlamlı değer varsa, verilen tür için varsayılan değer ile bunları değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="62183-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="62183-121">Aşağıdaki giriş verilerini alın ve [`IDataView`](xref:Microsoft.ML.IDataView) aşağıdaki `data`bir çağrıya yükleyin:</span><span class="sxs-lookup"><span data-stu-id="62183-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="62183-122">Listemizdeki son öğenin eksik bir `Price`değeri olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="62183-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="62183-123">`Price` Sütundaki eksik değerleri değiştirmek için, [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) eksik değeri doldurmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="62183-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62183-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)yalnızca sayısal verilerle çalışır.</span><span class="sxs-lookup"><span data-stu-id="62183-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="62183-125">ML.NET çeşitli [değiştirme modlarını](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)destekler.</span><span class="sxs-lookup"><span data-stu-id="62183-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="62183-126">Yukarıdaki örnekte, `Mean` eksik değeri bu sütunun ortalama değeriyle dolduran değiştirme modu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62183-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="62183-127">100.000 ve `Price` 300.000 ortalama beri 200.000 ile verilerimizde son öğe için mülkiyet 'nin sonucu's özelliği doldurur.</span><span class="sxs-lookup"><span data-stu-id="62183-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="62183-128">Normalleştiriciler kullanın</span><span class="sxs-lookup"><span data-stu-id="62183-128">Use normalizers</span></span>

<span data-ttu-id="62183-129">[Normalleştirme,](https://en.wikipedia.org/wiki/Feature_scaling) genellikle 0 ile 1 arasında olan özellikleri aynı aralıkta ölçeklendirmek için kullanılan bir veri ön işleme tekniğidir, böylece bir makine öğrenme algoritması tarafından daha doğru bir şekilde işlenebilirler.</span><span class="sxs-lookup"><span data-stu-id="62183-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="62183-130">Örneğin, yaş ve gelir aralıkları genellikle 0-100 aralığında olmak yaş ve gelir genellikle sıfır ile binlerce aralığında olmak ile önemli ölçüde değişir.</span><span class="sxs-lookup"><span data-stu-id="62183-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="62183-131">Daha ayrıntılı bir liste ve normalleştirme dönüşümlerinin açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="62183-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="62183-132">Min-Max normalleştirme</span><span class="sxs-lookup"><span data-stu-id="62183-132">Min-Max normalization</span></span>

<span data-ttu-id="62183-133">Aşağıdaki giriş verilerini alın ve [`IDataView`](xref:Microsoft.ML.IDataView) aşağıdaki `data`bir çağrıya yükleyin:</span><span class="sxs-lookup"><span data-stu-id="62183-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="62183-134">Normalleştirme, tek sayısal değerlere ve vektörlere sahip sütunlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="62183-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="62183-135">Yöntemle min-max normalleştirme kullanarak sütundaki `Price` [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) verileri normalleştirin.</span><span class="sxs-lookup"><span data-stu-id="62183-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="62183-136">Özgün fiyat `[200000,100000]` değerleri, 0-1 `MinMax` aralığında çıkış değerleri üreten normalleştirme formülü `[ 1, 0.5 ]` kullanılarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="62183-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="62183-137">Binn</span><span class="sxs-lookup"><span data-stu-id="62183-137">Binning</span></span>

<span data-ttu-id="62183-138">[Binning,](https://en.wikipedia.org/wiki/Data_binning) sürekli değerleri girdinin ayrı bir temsiline dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="62183-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="62183-139">Örneğin, özelliklerinizden birinin yaş olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="62183-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="62183-140">Binning, gerçek yaş değerini kullanmak yerine, bu değer için aralıklar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62183-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="62183-141">0-18 bir çöp kutusu olabilir, başka bir 19-35 ve benzeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="62183-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="62183-142">Aşağıdaki giriş verilerini alın ve [`IDataView`](xref:Microsoft.ML.IDataView) aşağıdaki `data`bir çağrıya yükleyin:</span><span class="sxs-lookup"><span data-stu-id="62183-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="62183-143">Yöntemi kullanarak verileri kutulara [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) normalleştirin.</span><span class="sxs-lookup"><span data-stu-id="62183-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="62183-144">Parametre, `maximumBinCount` verilerinizi sınıflandırmak için gereken kutu sayısının belirtilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="62183-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="62183-145">Bu örnekte, veriler iki kutuya konur.</span><span class="sxs-lookup"><span data-stu-id="62183-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="62183-146">Binning sonucu bin sınırları `[0,200000,Infinity]`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62183-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="62183-147">Bu nedenle ortaya çıkan `[0,1,1]` kutular ilk gözlem 0-200000 arasında ve diğerleri 200000 daha büyük ama sonsuzdaha az olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="62183-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="62183-148">Kategorik verilerle çalışma</span><span class="sxs-lookup"><span data-stu-id="62183-148">Work with categorical data</span></span>

<span data-ttu-id="62183-149">En yaygın veri türlerinden biri kategorik verilerdir.</span><span class="sxs-lookup"><span data-stu-id="62183-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="62183-150">Kategorik verilerin sınırlı sayıda kategorisi vardır.</span><span class="sxs-lookup"><span data-stu-id="62183-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="62183-151">Örneğin, ABD'nin durumları veya bir dizi resimde bulunan hayvan türlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="62183-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="62183-152">Kategorik veriler özellik veya etiket olsun, bir makine öğrenme modeli oluşturmak için kullanılabilen sayısal bir değerüzerine eşlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="62183-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="62183-153">ML.NET'da, çözdüğünen soruna bağlı olarak kategorik verilerle çalışmanın çeşitli yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="62183-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="62183-154">Anahtar değeri eşleme</span><span class="sxs-lookup"><span data-stu-id="62183-154">Key value mapping</span></span>

<span data-ttu-id="62183-155">ML.NET' de anahtar, bir kategoriyi temsil eden bir tamsayı değeridir.</span><span class="sxs-lookup"><span data-stu-id="62183-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="62183-156">Anahtar değeri eşleme, dize etiketlerini eğitim için benzersiz tamsayı değerlerine eşlemek için en sık kullanılır, ardından model tahmin yapmak için kullanıldığında dize değerlerine geri döner.</span><span class="sxs-lookup"><span data-stu-id="62183-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="62183-157">Anahtar değer eşleme gerçekleştirmek için kullanılan dönüşümler [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) ve [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A)vardır.</span><span class="sxs-lookup"><span data-stu-id="62183-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="62183-158">`MapValueToKey`modele bir eşleme sözlüğü ekler, `MapKeyToValue` böylece bir tahmin yaparken ters dönüşümü gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="62183-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="62183-159">Bir sıcak kodlama</span><span class="sxs-lookup"><span data-stu-id="62183-159">One hot encoding</span></span>

<span data-ttu-id="62183-160">Bir sıcak kodlama sonlu bir değer kümesialır ve bunları ikili gösterimi dizedeki benzersiz konumlarda tek `1` bir değere sahip tamsayılarla eşler.</span><span class="sxs-lookup"><span data-stu-id="62183-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="62183-161">Kategorik verilerin örtük olarak sıralanması yoksa, bir sıcak kodlama en iyi seçim olabilir.</span><span class="sxs-lookup"><span data-stu-id="62183-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="62183-162">Aşağıdaki tabloda posta kodları ham değerler olarak bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="62183-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="62183-163">Ham değer</span><span class="sxs-lookup"><span data-stu-id="62183-163">Raw value</span></span>|<span data-ttu-id="62183-164">Bir sıcak kodlanmış değer</span><span class="sxs-lookup"><span data-stu-id="62183-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="62183-165">98052</span><span class="sxs-lookup"><span data-stu-id="62183-165">98052</span></span>|<span data-ttu-id="62183-166">00...01</span><span class="sxs-lookup"><span data-stu-id="62183-166">00...01</span></span>|
|<span data-ttu-id="62183-167">98100</span><span class="sxs-lookup"><span data-stu-id="62183-167">98100</span></span>|<span data-ttu-id="62183-168">00...10</span><span class="sxs-lookup"><span data-stu-id="62183-168">00...10</span></span>|
|<span data-ttu-id="62183-169">...</span><span class="sxs-lookup"><span data-stu-id="62183-169">...</span></span>|<span data-ttu-id="62183-170">...</span><span class="sxs-lookup"><span data-stu-id="62183-170">...</span></span>|
|<span data-ttu-id="62183-171">98109</span><span class="sxs-lookup"><span data-stu-id="62183-171">98109</span></span>|<span data-ttu-id="62183-172">10...00</span><span class="sxs-lookup"><span data-stu-id="62183-172">10...00</span></span>|

<span data-ttu-id="62183-173">Kategorik verileri tek sıcak kodlanmış sayılara dönüştürme [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A)dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="62183-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="62183-174">Karma</span><span class="sxs-lookup"><span data-stu-id="62183-174">Hashing</span></span>

<span data-ttu-id="62183-175">Karma, kategorik verileri sayılara dönüştürmenin başka bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="62183-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="62183-176">Karma işlev, rasgele bir boyutun (örneğin bir metin dizisi) verilerini sabit aralıklı bir sayıya eşler.</span><span class="sxs-lookup"><span data-stu-id="62183-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="62183-177">Karma, özellikleri vektörelleştirmenin hızlı ve uzayda etkili bir yolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="62183-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="62183-178">Makine öğreniminde karma bir örnek, bilinen sözcüklerin bir sözlüğünü korumak yerine, e-postadaki her kelimenin karma ve büyük bir özellik vektörüne eklendiği e-posta spam filtrelemedir.</span><span class="sxs-lookup"><span data-stu-id="62183-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="62183-179">Karma kullanımı bu şekilde sözlükte olmayan sözcüklerin kullanımı ile kötü amaçlı spam filtreleme sorunu önler.</span><span class="sxs-lookup"><span data-stu-id="62183-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="62183-180">ML.NET, metin, tarih ve sayısal veriler üzerinde karma gerçekleştirmek için [Karma](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) dönüştürme sağlar.</span><span class="sxs-lookup"><span data-stu-id="62183-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="62183-181">Değer anahtarı eşleme gibi, karma dönüşümün çıktıları da anahtar türleridir.</span><span class="sxs-lookup"><span data-stu-id="62183-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="62183-182">Metin verileriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="62183-182">Work with text data</span></span>

<span data-ttu-id="62183-183">Kategorik veriler gibi, metin verilerinin de bir makine öğrenme modeli oluşturmak için kullanmadan önce sayısal özelliklere dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="62183-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="62183-184">Daha ayrıntılı bir liste ve metin dönüşümlerinin açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="62183-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="62183-185">Aşağıdaki veriler gibi verileri kullanarak aşağıdaki [`IDataView`](xref:Microsoft.ML.IDataView)verilere yüklenmiş:</span><span class="sxs-lookup"><span data-stu-id="62183-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="62183-186">ML.NET, [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) bir metnin dize değerini alan ve bir dizi bireysel dönüşüm uygulayarak metinden bir dizi özellik oluşturan dönüşümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="62183-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="62183-187">Elde edilen dönüştürme, `Description` sütundaki metin değerlerini aşağıdaki çıktıya benzeyen sayısal bir vektöre dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="62183-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="62183-188">Makyaj `FeaturizeText` dönüşümleri, özellik üretimi üzerinde daha ince tane kontrolü için ayrı ayrı da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="62183-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="62183-189">`textEstimator`yöntem tarafından gerçekleştirilen işlemlerin [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) bir alt kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="62183-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="62183-190">Daha karmaşık bir boru hattının yararı, verilere uygulanan dönüşümler üzerinde kontrol ve görünürlüktür.</span><span class="sxs-lookup"><span data-stu-id="62183-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="62183-191">Örnek olarak ilk girişi kullanarak, aşağıdaki tarafından `textEstimator`tanımlanan dönüşüm adımları tarafından üretilen sonuçların ayrıntılı bir açıklamasıdır:</span><span class="sxs-lookup"><span data-stu-id="62183-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="62183-192">**Orijinal Metin: Bu iyi bir üründür**</span><span class="sxs-lookup"><span data-stu-id="62183-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="62183-193">Dönüşüm</span><span class="sxs-lookup"><span data-stu-id="62183-193">Transform</span></span> | <span data-ttu-id="62183-194">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62183-194">Description</span></span> | <span data-ttu-id="62183-195">Sonuç</span><span class="sxs-lookup"><span data-stu-id="62183-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="62183-196">1. Metni Normalleştirme</span><span class="sxs-lookup"><span data-stu-id="62183-196">1. NormalizeText</span></span> | <span data-ttu-id="62183-197">Varsayılan olarak tüm harfleri küçük harfe dönüştürür</span><span class="sxs-lookup"><span data-stu-id="62183-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="62183-198">Bu iyi bir üründür</span><span class="sxs-lookup"><span data-stu-id="62183-198">this is a good product</span></span>
|<span data-ttu-id="62183-199">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="62183-199">2. TokenizeWords</span></span> | <span data-ttu-id="62183-200">Dizeyi tek tek sözcüklere böler</span><span class="sxs-lookup"><span data-stu-id="62183-200">Splits string into individual words</span></span> | <span data-ttu-id="62183-201">["this","is","a","iyi"," ürün"]</span><span class="sxs-lookup"><span data-stu-id="62183-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="62183-202">3. Varsayılan StopKelimeleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="62183-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="62183-203">*Gibi* stopwords kaldırır ve *bir*.</span><span class="sxs-lookup"><span data-stu-id="62183-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="62183-204">["iyi"," ürün"]</span><span class="sxs-lookup"><span data-stu-id="62183-204">["good","product"]</span></span>
|<span data-ttu-id="62183-205">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="62183-205">4. MapValueToKey</span></span> | <span data-ttu-id="62183-206">Giriş verilerine göre anahtarların (kategorilerin) değerlerini eşler</span><span class="sxs-lookup"><span data-stu-id="62183-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="62183-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="62183-207">[1,2]</span></span>
|<span data-ttu-id="62183-208">5. Üretmis Gramlar</span><span class="sxs-lookup"><span data-stu-id="62183-208">5. ProduceNGrams</span></span> | <span data-ttu-id="62183-209">Metni ardışık sözcükler dizisine dönüştürür</span><span class="sxs-lookup"><span data-stu-id="62183-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="62183-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="62183-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="62183-211">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="62183-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="62183-212">Girişleri lp normlarına göre ölçeklendirin</span><span class="sxs-lookup"><span data-stu-id="62183-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="62183-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="62183-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
