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
# <a name="prepare-data-for-building-a-model"></a>Model oluşturmaya yönelik verileri hazırlama

ML.NET kullanarak ek işleme veya bir model oluşturmaya yönelik verileri hazırlama hakkında bilgi edinin.

Veriler genellikle temiz ve seyrek yapılır. ML.NET Machine Learning algoritmaları, giriş veya özelliklerin tek bir sayısal vektörde olmasını bekler. Benzer şekilde, tahmin edilecek değer (etiket), özellikle de kategorik veriler, kodlanmalıdır. Bu nedenle, veri hazırlama amaçlarından biri, verileri ML.NET algoritmaları tarafından beklenen biçimde almak.

## <a name="filter-data"></a>Verileri Filtrele

Bazen, bir veri kümesindeki tüm veriler Analize uygun değildir. İlgisiz verileri kaldırma yaklaşımı filtreleniyor. [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) , tüm verileri içeren bir [`IDataView`](xref:Microsoft.ML.IDataView) alıp yalnızca ilgilendiğiniz veri noktalarını içeren bir [ıdataview](xref:Microsoft.ML.IDataView) döndüren bir filtre işlemleri kümesi içerir. Filtre işlemleri [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)gibi bir [`IEstimator`](xref:Microsoft.ML.IEstimator%601) veya [`ITransformer`](xref:Microsoft.ML.ITransformer) olmadığından, [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) veya [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) veri hazırlama işlem hattının parçası olarak dahil edilemez olduğunu unutmayın.

Aşağıdaki giriş verilerini alın ve `data`adlı bir [`IDataView`](xref:Microsoft.ML.IDataView) yükleyin:

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

Bir sütunun değerine göre verileri filtrelemek için [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) yöntemini kullanın.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Yukarıdaki örnek, 200000 ile 1000000 arasında bir fiyata sahip veri kümesindeki satırları alır. Bu filtreyi uygulamanın sonucu yalnızca verilerdeki son iki satırı döndürür ve fiyatı 100000 olduğundan ve belirtilen Aralık arasında olmadığından ilk satırı dışlayacak.

## <a name="replace-missing-values"></a>Eksik değerleri Değiştir

Eksik değerler veri kümelerinde yaygın bir oluşumlardır. Eksik değerlerle ilgilenmeye yönelik bir yaklaşım, veri içindeki ortalama değer gibi herhangi bir veya başka bir anlamlı değer varsa, bunları verilen türün varsayılan değeriyle değiştirecektir.

Aşağıdaki giriş verilerini alın ve `data`adlı bir [`IDataView`](xref:Microsoft.ML.IDataView) yükleyin:

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

Listemizdeki son öğenin `Price`için eksik bir değere sahip olduğuna dikkat edin. `Price` sütununda eksik değerleri değiştirmek için [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) metodunu kullanarak eksik değeri girin.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) yalnızca sayısal verilerle birlikte kullanılabilir.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET çeşitli [değiştirme modlarını](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)destekler. Yukarıdaki örnek, eksik değeri bu sütunun ortalama değeriyle dolduran `Mean` değiştirme modunu kullanır. Değiştirme işleminin sonucu, 100.000 ve 300.000 ortalaması olduğundan, 200.000 ile verilerdeki son öğenin `Price` özelliğini doldurur.

## <a name="use-normalizers"></a>Normalleyiciler kullanma

[Normalleştirme](https://en.wikipedia.org/wiki/Feature_scaling) , bir makine öğrenimi algoritması tarafından daha doğru işlenebilmeleri için, özellikleri genellikle 0 ile 1 arasında olacak şekilde ölçeklendirmek için kullanılan bir veri ön işleme tekniğidir. Örneğin, yaş ve gelir aralıkları genellikle, 0-100 ve gelirin genellikle sıfır-binlerce aralığında olması bakımından yaş açısından önemli ölçüde farklılık gösterir. Daha ayrıntılı bir liste ve normalleştirme dönüştürmelerini açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.

### <a name="min-max-normalization"></a>Minimum-en fazla normalleştirme

Aşağıdaki giriş verilerini alın ve `data`adlı bir [`IDataView`](xref:Microsoft.ML.IDataView) yükleyin:

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

Normalleştirme, tek bir sayısal değere ve vektörlerine sahip sütunlara uygulanabilir. `Price` sütunundaki verileri, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) yöntemiyle Min-Max normalleştirmesini kullanarak normalleştirin.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

`[200000,100000]` orijinal fiyat değerleri, 0-1 aralığında çıkış değerleri üreten `MinMax` normalleştirme formülü kullanılarak `[ 1, 0.5 ]` dönüştürülür.

### <a name="binning"></a>Gruplama

[Binme](https://en.wikipedia.org/wiki/Data_binning) , sürekli değerleri girişin ayrı bir gösterimine dönüştürür. Örneğin, özelliklerden birinin yaş olduğunu varsayalım. Bini gerçek yaş değerini kullanmak yerine, bu değer için aralıklar oluşturur. 0-18 bir bin olabilir, diğeri 19-35 olabilir ve bu şekilde devam eder.

Aşağıdaki giriş verilerini alın ve `data`adlı bir [`IDataView`](xref:Microsoft.ML.IDataView) yükleyin:

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

[`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) yöntemi kullanarak verileri depo gözleri halinde normalleştirin. `maximumBinCount` parametresi, verilerinizi sınıflandırmak için gereken bölme sayısını belirtmenize olanak sağlar. Bu örnekte, veriler iki bölme içine alınacaktır.

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Binme sonucu `[0,200000,Infinity]`bin sınırlarını oluşturur. Bu nedenle, ilk gözlem 0-200000 arasında ve diğerleri 200000 ' den büyük ancak sonsuz ' dan az olduğu için ortaya çıkan depo gözleri `[0,1,1]`.

## <a name="work-with-categorical-data"></a>Kategorik verilerle çalışma

En yaygın veri türlerinden biri kategorik verilerden biridir. Kategorik verilerin sınırlı sayıda kategorisi vardır. Örneğin, ABD 'nin durumları veya bir resim kümesinde bulunan hayvanlar türlerinin bir listesi. Kategorik verilerin özellikler ya da Etiketler olup olmadığı, bir makine öğrenimi modeli oluşturmak için kullanılabilmesi için bunların sayısal bir değerle eşlenmesi gerekir. ML.NET ' de kategorik verilerle çalışmanın çeşitli yolları, çözmenize çalıştığınız soruna bağlı olarak vardır.

### <a name="key-value-mapping"></a>Anahtar değer eşleme

ML.NET ' de, anahtar bir kategoriyi temsil eden bir tamsayı değeridir. Anahtar değeri eşleme, genellikle dize etiketlerini eğitimin benzersiz tamsayı değerleriyle eşlemek için kullanılır, ardından model bir tahmin yapmak için kullanıldığında dize değerlerine geri dönün.

Anahtar değer eşlemesini gerçekleştirmek için kullanılan dönüşümler [Mapvaluetokey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) ve [Mapkeytovalue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A)' lardır.

`MapValueToKey`, bir tahmin yaparken `MapKeyToValue` ters dönüştürmeyi gerçekleştirebilmesi için modeldeki eşlemelerin bir sözlüğünü ekler.

### <a name="one-hot-encoding"></a>Tek bir etkin kodlama

Bir sıcak kodlama, sınırlı bir değer kümesi alır ve bunları ikili temsilinin dizedeki benzersiz konumlarda tek bir `1` değerine sahip olan tamsayılara eşler. Kategorik verilerin örtük bir sıralaması yoksa, tek bir sık kullanılan kodlama en iyi seçim olabilir. Aşağıdaki tabloda, ham değerler olarak ZIP kodlarına sahip bir örnek gösterilmektedir.

|Ham değer|Sık kodlanmış bir değer|
|---------|---------------------|
|98052|00... 01|
|98100|00... 10|
|...|...|
|98109|10... 00|

Kategorik verileri tek başına kodlanmış sayılara dönüştürecek dönüşüm [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).

### <a name="hashing"></a>Karma

Karma oluşturma, kategorik verileri sayılara dönüştürmek için başka bir yoldur. Karma işlevi rastgele boyuttaki verileri (örneğin, metin dizesi) sabit bir aralığa göre bir sayıya eşler. Karma özellikleri, özelliklerin vektörleştirilmesi için hızlı ve verimli bir yol olabilir. Machine Learning 'de karma hale getirilmiş bir önemli örneği, bilinen sözcüklerin bir sözlüğünü tutmak yerine, e-postadaki her sözcüğün karma hale getirilmiş ve büyük bir özellik vektörüne eklendiği e-posta istenmeyen posta filtrelemedir. Bu şekilde karma kullanılması, sözlükte olmayan sözcüklerin kullanımı ile ilgili kötü amaçlı posta filtreleme sorunu yaşamasını önler.

ML.NET metin, tarih ve sayısal veriler üzerinde karma hale getirmek için [karma](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) dönüşüm sağlar. Değer anahtarı eşleme gibi, karma dönüştürmenin çıkışları anahtar türlerdir.

## <a name="work-with-text-data"></a>Metin verileriyle çalışma

Kategorik veriler gibi, metin verilerinin bir makine öğrenimi modeli oluşturmak için kullanılmadan önce sayısal özelliklere dönüştürülmesi gerekir. Daha ayrıntılı bir liste ve metin dönüştürmelerini açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.

Bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenmiş olan veriler gibi verileri kullanma:

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

ML.NET, bir metnin dize değerini alan ve bir dizi tekil dönüştürme uygulayarak metinden bir özellikler kümesi oluşturan [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) dönüşümünü sağlar.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Elde edilen dönüşüm, `Description` sütunundaki metin değerlerini aşağıdaki çıkışa benzer bir sayısal vector öğesine dönüştürür:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

`FeaturizeText` oluşturan dönüşümler, özellik üretimi üzerinde daha ince denetim için ayrı ayrı de uygulanabilir.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator`, [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) yöntemi tarafından gerçekleştirilen işlemlerin bir alt kümesini içerir. Daha karmaşık bir işlem hattının avantajı, verilere uygulanan dönüşümlere göre denetim ve görünürlük sağlar.

Örnek olarak ilk girdiyi kullanarak aşağıda, `textEstimator`tarafından tanımlanan dönüştürme adımları tarafından oluşturulan sonuçların ayrıntılı bir açıklaması verilmiştir:

**Özgün metin: Bu iyi bir üründür**

|Dönüştürme | Açıklama | Sonuç
|--|--|--|
|1. NormalizeText | Varsayılan olarak tüm harfleri küçük harfe dönüştürür | Bu iyi bir üründür
|2. TokenizeWords | Dizeyi tek tek sözcüklere böler | ["This", "dir", "a", "iyidir", "Product"]
|3. Removedefaultstopkelimeleri | *Ve gibi* stopsözcüklerini *kaldırır.* | ["iyi", "ürün"]
|4. MapValueToKey | Değerleri, giriş verilerine göre anahtarlar (kategoriler) ile eşler |  [1,2]
|5. ProduceNGrams | Metni birbirini izleyen sözcüklerin sıralamasına dönüştürür | [1, 1, 1, 0, 0]
|6. NormalizeLpNorm | Girdileri LP-norm olarak ölçeklendirin | [0,577350529, 0,577350529, 0,577350529, 0, 0]
