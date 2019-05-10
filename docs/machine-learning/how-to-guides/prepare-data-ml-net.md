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
# <a name="prepare-data"></a>Verileri hazırlama

ML.NET ek işleme veya bir model oluşturmak için veri hazırlamak için kullanmayı öğrenin.

Genellikle şekilde çoğaltamaması ve aralıklı verilerdir. Ayrıca, giriş veya tek bir sayısal vektörü olarak özellikleri ML.NET makine öğrenimi algoritmaları bekliyoruz. Bu nedenle veri hazırlama hedeflerinden ML.NET algoritmalarda beklenen biçime verilerinin elde edilmesidir. 

## <a name="filter-data"></a>Verileri filtreleme

Bazı durumlarda, veri kümesindeki tüm verileri analiz için ilgili. İlgisiz verilerin kaldırmak için bir yaklaşım filtreleme. [ `DataOperationsCatalog` ](xref:Microsoft.ML.DataOperationsCatalog) Olur filtresi işlemlerini kümesini içeren bir [ `IDataView` ](xref:Microsoft.ML.IDataView) tüm dönüş ve veri içeren bir [IDataView](xref:Microsoft.ML.IDataView) yalnızca içeren ilgi çekici veri noktaları. Filtre işlemler atomik değildir çünkü dikkat etmeniz önemlidir bir [ `IEstimator` ](xref:Microsoft.ML.IEstimator%601) veya [ `ITransformer` ](xref:Microsoft.ML.ITransformer) ister de [ `TransformsCatalog` ](xref:Microsoft.ML.TransformsCatalog), bunlar olamaz parçası olarak dahil edilen bir [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) veya [ `TransformerChain` ](xref:Microsoft.ML.Data.TransformerChain%601) veri hazırlama işlem hattı. 

Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Verilere bir sütun değerine göre filtre uygulamak için kullanma [ `FilterRowsByColumn` ](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) yöntemi.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Yukarıdaki örnek veri kümesiyle birlikte bir fiyat 200000 ile 1000000 arasında satırları alır. Bu filtre sonucu verileri yalnızca son iki satırını döndürür ve ancak ilk satırın tutma olduğundan bunun ücreti 100000 ve belirtilen aralık arasında değil.

## <a name="replace-missing-values"></a>Eksik değerleri Değiştir

Veri kümelerinde sık karşılaştıkları eksik değerler. Eksik değerleri ilgilenmek için bir yaklaşım ise bunları verilen tür için varsayılan değer ya da başka bir değiştirmek için ortalama değer gibi anlamlı bir değer. 

Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Listemize içerisindeki son öğe için eksik değer olduğunu fark `Price`. Eksik değerleri değiştirmek için `Price` sütun kullanımı [ `ReplaceMissingValues` ](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) eksik değeri doldurmak için yöntemi.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) yalnızca sayısal verilerle çalışır.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET destekleyen çeşitli [değiştirme modları](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). Örnek kullanımlar yukarıda `Mean` değiştirme modu, bir eksik değeri söz konusu sütunun ortalama değer ile doldurur. Değiştirme'nin sonucu doldurur `Price` verilerimizi 100.000 ve 300000 ortalamasını olduğundan 200.000 ile içerisindeki son öğe özelliği. 

## <a name="use-normalizers"></a>Normalizers kullanın

[Normalleştirme](https://en.wikipedia.org/wiki/Feature_scaling) aynı ölçekte daha hızlı yakınsama algoritmaları yardımcı olan özellikleri standart hale getirmek için kullanılan bir teknik ön işleme bir veri. Örneğin, yaş ve gelir gibi değerler için aralıklar, genellikle genellikle sıfır binlerce aralığında olan gelir ve 0-100 aralığında olması geçerlilik süresi ile önemli ölçüde farklılık. Ziyaret [dönüşümler sayfa](../resources/transforms.md) daha ayrıntılı bir listesi ve normalleştirme dönüşümler açıklaması. 

### <a name="min-max-normalization"></a>Min-Maks normalleştirme

Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Min-Maks normalleştirme kullanarak veri Normalleştir [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) yöntemi.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Özgün fiyat değerlerini `[200000,100000]` dönüştürülür `[ 1, 0.5 ]` kullanarak `MinMax` normalleştirme formül, bir çıkış değerleri 0-1 aralığında oluşturur.

### <a name="binning"></a>Gruplama

[Gruplama](https://en.wikipedia.org/wiki/Data_binning) sürekli değerleri ayrık bir giriş gösterimine dönüştürür. Örneğin, yaş, özelliklerden biri olduğunu varsayın. Gruplama gerçek yaş değeri kullanmak yerine, bu değer aralıkları oluşturur. 0-18 bir depo olabilir, başka bir 19-35 vb. olabilir. 

Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Verileri kullanarak bölmeler Normalleştir [ `NormalizeBinning` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) yöntemi. `maximumBinCount` Parametresi verilerinizi sınıflandırmak için gereken depo sayısını belirtmenizi sağlar. Bu örnekte, verileri iki depo yerleştirilir.  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Depo sınırları gruplama sonucunu oluşturur `[0,200000,Infinity]`. Bu nedenle sonuç depo olan `[0,1,1]` ilk gözlem 0 200000 ve diğerleri arasında olduğundan 200000 büyüktür, ancak sonsuza küçüktür.

## <a name="work-with-categorical-data"></a>Kategorik verileri ile çalışma

Bir machine learning modeli oluşturmak için kullanılmadan önce bir sayıya dönüştürülecek sayısal olmayan sütunları ise kategorik veriler gerekir. 

Yüklenen aşağıdaki giriş verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Kategorik `VehicleType` özelliği, bir sayı kullanarak dönüştürülebilir [ `OneHotEncoding` ](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) yöntemi. 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

Metin değerini elde edilen dönüştürme dönüştürür `VehicleType` bir sayı. Girdileri `VehicleType` sütun dönüştürme uygulandığında şu olur: 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a>Metin verileri ile çalışma

Bir machine learning modeli oluşturmak üzere kullanmadan önce sayıya Dönüştürülecek metin verileri gerekir. Ziyaret [dönüşümler sayfa](../resources/transforms.md) daha ayrıntılı bir listesi ve metin dönüştürmeleri açıklaması.

Aşağıdaki verileri içine yüklenmiş gibi verileri kullanarak bir [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Metni bir sayısal vektör gösterimine dönüştürmek için en az bir adımda [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) yöntemi. Kullanarak [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) dönüştürme, bir dizi dönüşümleri lp normalleştirilmiş word ve karakter ngrams temsil eden sayısal bir vektör içinde elde edilen giriş metin sütununu uygulanır. 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Sonuçta elde edilen dönüştürme metin değerleri dönüştürecektir `Description` aşağıdaki çıktıya benzer bir sayısal vektör sütunu:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Birleştirme karmaşık metin işleme adımları içine bir [ `EstimatorChain` ](xref:Microsoft.ML.Data.EstimatorChain%601) gürültü kaldırın ve potansiyel olarak gerektiğinde, gerekli işlem kaynaklarının miktarını azaltmak için.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` bir alt kümesini tarafından gerçekleştirilen işlemleri içeren [ `FeaturizeText` ](xref:Microsoft.ML.TextCatalog.FeaturizeText*) yöntemi. Daha karmaşık bir işlem hattının avantajı denetim ve görünürlüğü verilere uygulanan dönüştürmeler biter. 

Örnek kullanıldığında ilk giriş tarafından tanımlanan dönüştürme adımı tarafından üretilen sonuçlar ayrıntılı bir açıklaması verilmiştir `textEstimator`:

**Orijinal metni: Bu iyi bir üründür**

|Dönüştürme | Açıklama | Sonuç
|--|--|--|
|1. NormalizeText | Tüm harfleri küçük harfe varsayılan olarak dönüştürür | Bu iyi bir üründür
|2. TokenizeWords | Bölmelerini kelimeler dizeye | ["Bu", "is", "bir","iyi","product"]
|3. RemoveDefaultStopWords | Durdurma sözcükleri gibi kaldırır *olduğu* ve *bir*. | ["good", "product"]
|4. MapValueToKey | Anahtarları (Kategoriler) giriş verileri temel alan değerleri eşleyen |  [1,2]
|5. ProduceNGrams | Metin ardışık sözcükleri dizisine dönüştürür. | [1,1,1,0,0]
|6. NormalizeLpNorm | Kendi lp norm tarafından ölçek girişleri | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
