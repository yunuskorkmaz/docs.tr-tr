---
title: Model oluşturmaya yönelik verileri hazırlama
description: Ek işleme veya model oluşturmaya yönelik verileri işlemek ve hazırlamak için ML.NET içindeki dönüştürmeleri nasıl kullanacağınızı öğrenin.
author: luisquintanilla
ms.author: luquinta
ms.date: 09/11/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 4452aef351f33df532f3c673307dedbbf71631b8
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929365"
---
# <a name="prepare-data-for-building-a-model"></a>Model oluşturmaya yönelik verileri hazırlama

ML.NET kullanarak ek işleme veya bir model oluşturmaya yönelik verileri hazırlama hakkında bilgi edinin.

Veriler genellikle temiz ve seyrek yapılır. ML.NET Machine Learning algoritmaları, giriş veya özelliklerin tek bir sayısal vektörde olmasını bekler. Benzer şekilde, tahmin edilecek değer (etiket), özellikle de kategorik veriler, kodlanmalıdır. Bu nedenle, veri hazırlama amaçlarından biri, verileri ML.NET algoritmaları tarafından beklenen biçimde almak. 

## <a name="filter-data"></a>Verileri Filtrele

Bazen, bir veri kümesindeki tüm veriler Analize uygun değildir. İlgisiz verileri kaldırma yaklaşımı filtreleniyor. , [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) Tüm verileri [`IDataView`](xref:Microsoft.ML.IDataView) içeren ve yalnızca ilgilendiğiniz veri noktalarını içeren bir [ıdataview](xref:Microsoft.ML.IDataView) döndüren bir filtre işlemleri kümesi içerir. Filtre [`IEstimator`](xref:Microsoft.ML.IEstimator%601) işlemleri bir [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) veya [`ITransformer`](xref:Microsoft.ML.ITransformer) gibi [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)olmadığından, bir [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) veya veri hazırlama işlem hattının parçası olarak eklenemediğinden emin olmak önemlidir. 

' A [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:

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

Bir sütunun değerine göre verileri filtrelemek için [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) yöntemini kullanın.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Yukarıdaki örnek, 200000 ile 1000000 arasında bir fiyata sahip veri kümesindeki satırları alır. Bu filtreyi uygulamanın sonucu yalnızca verilerdeki son iki satırı döndürür ve fiyatı 100000 olduğundan ve belirtilen Aralık arasında olmadığından ilk satırı dışlayacak.

## <a name="replace-missing-values"></a>Eksik değerleri Değiştir

Eksik değerler veri kümelerinde yaygın bir oluşumlardır. Eksik değerlerle ilgilenmeye yönelik bir yaklaşım, veri içindeki ortalama değer gibi herhangi bir veya başka bir anlamlı değer varsa, bunları verilen türün varsayılan değeriyle değiştirecektir. 

' A [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:

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

Listemizdeki son öğenin için `Price`değeri eksik olduğuna dikkat edin. `Price` Sütundaki eksik değerleri değiştirmek için, bu eksik değeri dolduracak [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) yöntemi kullanın.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*)yalnızca sayısal verilerle birlikte kullanılabilir.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET çeşitli [değiştirme modlarını](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)destekler. Yukarıdaki örnek, bu sütunun `Mean` ortalama değerine sahip eksik değeri dolduracak değiştirme modunu kullanır. Değiştirme işleminin sonucu, 100.000 ve 300.000 `Price` ortalaması olduğundan, 200.000 ile verilerimizin son öğesi için özelliği doldurur. 

## <a name="use-normalizers"></a>Normalleyiciler kullanma

[Normalleştirme](https://en.wikipedia.org/wiki/Feature_scaling) , algoritmaların daha hızlı yakınsamasını sağlayan, aynı ölçekte olmayan özellikleri standartlaştırmak için kullanılan bir veri ön işleme tekniğidir. Örneğin, yaş ve gelir gibi değerlerin aralıkları genellikle, 0-100 ve gelirin genellikle sıfır-binlerce aralığında olması bakımından yaş açısından önemli ölçüde farklılık gösterir. Daha ayrıntılı bir liste ve normalleştirme dönüştürmelerini açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin. 

### <a name="min-max-normalization"></a>Minimum-en fazla normalleştirme

' A [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:

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

Normalleştirme, tek bir sayısal değere ve vektörlerine sahip sütunlara uygulanabilir. Yöntemi ile Min-Max `Price` normalleştirmesini kullanarak sütundaki verileri normalleştirin. [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*)

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Özgün fiyat değerleri `[200000,100000]` , 0-1 aralığında çıkış `[ 1, 0.5 ]` değerleri üreten `MinMax` normalleştirme formülü kullanılarak öğesine dönüştürülür.

### <a name="binning"></a>Gruplama

[Binme](https://en.wikipedia.org/wiki/Data_binning) , sürekli değerleri girişin ayrı bir gösterimine dönüştürür. Örneğin, özelliklerden birinin yaş olduğunu varsayalım. Bini gerçek yaş değerini kullanmak yerine, bu değer için aralıklar oluşturur. 0-18 bir bin olabilir, diğeri 19-35 olabilir ve bu şekilde devam eder. 

' A [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:

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

[`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) Yöntemini kullanarak verileri depo gözlerine normalleştirin. `maximumBinCount` Parametresi, verilerinizi sınıflandırmak için gereken bölme sayısını belirtmenize olanak sağlar. Bu örnekte, veriler iki bölme içine alınacaktır.  

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Binüş 'in sonucu, öğesinin `[0,200000,Infinity]`bölme sınırlarını oluşturur. Bu nedenle, ilk gözlemin 0-200000 arasında ve diğerleri 200000 ' den daha büyük ancak sonsuz ' dan az olduğu için ortaya çıkan depo gözleri vardır `[0,1,1]` .

## <a name="work-with-categorical-data"></a>Kategorik verilerle çalışma

Sayısal olmayan kategorik verilerin bir makine öğrenimi modeli oluşturmak için kullanılmadan önce bir sayıya dönüştürülmesi gerekir. 

' A [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:

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

Kategorik `VehicleType` özelliği [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) yöntemi kullanılarak bir sayıya dönüştürülebilir. 

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

Elde edilen dönüşüm metin değerini `VehicleType` bir sayıya dönüştürür. Dönüştürme uygulandığında `VehicleType` sütunundaki girişler aşağıdaki gibi olur: 

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a>Metin verileriyle çalışma

Bir makine öğrenimi modeli oluşturmak için, metin verilerinin kullanılmadan önce sayılara dönüştürülmesi gerekir. Daha ayrıntılı bir liste ve metin dönüştürmelerini açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.

Aşağıdaki verilere yüklenmiş [`IDataView`](xref:Microsoft.ML.IDataView)veriler gibi verileri kullanarak:

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

Metni sayısal bir vektör gösterimine dönüştürmek için gereken en düşük adım [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) yöntemi kullanmaktır. [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) Dönüşümü kullanarak, giriş metin sütununa bir dizi dönüştürme uygulanır ve bu, LP normalleştirilmiş sözcük ve karakter Ngram sayısını temsil eden sayısal bir Vector öğesine neden olur. 

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Elde edilen dönüşüm, `Description` sütundaki metin değerlerini aşağıdaki çıkışa benzer bir sayısal vector öğesine dönüştürür:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Paraziti kaldırmak için karmaşık metin işleme adımlarını [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) bir ile birleştirin ve gereken işlem kaynakları miktarını gerektiği gibi azaltabilirsiniz.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator`[`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) yöntemi tarafından gerçekleştirilen işlemlerin bir alt kümesini içerir. Daha karmaşık bir işlem hattının avantajı, verilere uygulanan dönüşümlere göre denetim ve görünürlük sağlar. 

Örnek olarak ilk girdiyi kullanarak aşağıda, tarafından `textEstimator`tanımlanan dönüştürme adımları tarafından oluşturulan sonuçların ayrıntılı bir açıklaması verilmiştir:

**Özgün metin: Bu iyi bir üründür**

|Dönüştürme | Açıklama | Sonuç
|--|--|--|
|1. NormalizeText | Varsayılan olarak tüm harfleri küçük harfe dönüştürür | Bu iyi bir üründür
|2. TokenizeWords | Dizeyi tek tek sözcüklere böler | ["This", "dir", "a", "iyidir", "Product"]
|3. Removedefaultstopkelimeleri | *Ve gibi* stopsözcüklerini *kaldırır.* | ["iyi", "ürün"]
|4. MapValueToKey | Değerleri, giriş verilerine göre anahtarlar (kategoriler) ile eşler |  [1,2]
|5. ProduceNGrams | Metni birbirini izleyen sözcüklerin sıralamasına dönüştürür | [1, 1, 1, 0, 0]
|6. NormalizeLpNorm | Girdileri LP-norm olarak ölçeklendirin | [0,577350529, 0,577350529, 0,577350529, 0, 0]
