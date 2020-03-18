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
# <a name="prepare-data-for-building-a-model"></a>Model oluşturmak için veri hazırlama

Ek işleme veya model oluşturmak için veri hazırlamak için ML.NET nasıl kullanacağınızı öğrenin.

Veriler genellikle kirli ve seyrektir. ML.NET makine öğrenimi algoritmaları girdi veya özelliklerin tek bir sayısal vektörde olmasını bekler. Benzer şekilde, tahmin edilecek değer (etiket), özellikle kategorik veriler olduğunda, kodlanmalıdır. Bu nedenle veri hazırlamanın amaçlarından biri, verileri ML.NET algoritmaları tarafından beklenen biçime getirmektir.

## <a name="filter-data"></a>Verileri filtreleme

Bazen, bir veri kümesindeki tüm veriler çözümleme için geçerli değildir. Alakasız verileri kaldırmak için bir yaklaşım filtreleme olduğunu. Tüm [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) verileri içeren ve [`IDataView`](xref:Microsoft.ML.IDataView) yalnızca ilgi çekici veri noktalarını içeren bir [IDataView](xref:Microsoft.ML.IDataView) döndüren bir filtre işlemleri kümesi içerir. Filtre [`IEstimator`](xref:Microsoft.ML.IEstimator%601) işlemleri bir veya [`ITransformer`](xref:Microsoft.ML.ITransformer) benzeri olmadığı [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)için, bir [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) veya [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) veri hazırlama ardışık hattının bir parçası olarak dahil edilemeyeceğini unutmayın.

Aşağıdaki giriş verilerini alın ve [`IDataView`](xref:Microsoft.ML.IDataView) aşağıdaki `data`bir çağrıya yükleyin:

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

Verileri sütunun değerine göre filtrelemek [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) için yöntemi kullanın.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

Yukarıdaki örnek, 200000 ile 100000 arasında bir fiyatla veri kümesindeki satırları alır. Bu filtreyi uygulamanın sonucu, verilerdeki yalnızca son iki satırı döndürür ve fiyatı 100.000 olduğundan ve belirtilen aralık arasında olmadığından ilk satırı hariç tutar.

## <a name="replace-missing-values"></a>Eksik değerleri değiştirme

Eksik değerler veri kümelerinde sık karşılaşılan bir durumdur. Eksik değerlerle başa çıkmak için bir yaklaşım, verilerdeki ortalama değer gibi herhangi biri veya başka bir anlamlı değer varsa, verilen tür için varsayılan değer ile bunları değiştirmektir.

Aşağıdaki giriş verilerini alın ve [`IDataView`](xref:Microsoft.ML.IDataView) aşağıdaki `data`bir çağrıya yükleyin:

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

Listemizdeki son öğenin eksik bir `Price`değeri olduğuna dikkat edin. `Price` Sütundaki eksik değerleri değiştirmek için, [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) eksik değeri doldurmak için yöntemi kullanın.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)yalnızca sayısal verilerle çalışır.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET çeşitli [değiştirme modlarını](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)destekler. Yukarıdaki örnekte, `Mean` eksik değeri bu sütunun ortalama değeriyle dolduran değiştirme modu kullanılır. 100.000 ve `Price` 300.000 ortalama beri 200.000 ile verilerimizde son öğe için mülkiyet 'nin sonucu's özelliği doldurur.

## <a name="use-normalizers"></a>Normalleştiriciler kullanın

[Normalleştirme,](https://en.wikipedia.org/wiki/Feature_scaling) genellikle 0 ile 1 arasında olan özellikleri aynı aralıkta ölçeklendirmek için kullanılan bir veri ön işleme tekniğidir, böylece bir makine öğrenme algoritması tarafından daha doğru bir şekilde işlenebilirler. Örneğin, yaş ve gelir aralıkları genellikle 0-100 aralığında olmak yaş ve gelir genellikle sıfır ile binlerce aralığında olmak ile önemli ölçüde değişir. Daha ayrıntılı bir liste ve normalleştirme dönüşümlerinin açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.

### <a name="min-max-normalization"></a>Min-Max normalleştirme

Aşağıdaki giriş verilerini alın ve [`IDataView`](xref:Microsoft.ML.IDataView) aşağıdaki `data`bir çağrıya yükleyin:

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

Normalleştirme, tek sayısal değerlere ve vektörlere sahip sütunlara uygulanabilir. Yöntemle min-max normalleştirme kullanarak sütundaki `Price` [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) verileri normalleştirin.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Özgün fiyat `[200000,100000]` değerleri, 0-1 `MinMax` aralığında çıkış değerleri üreten normalleştirme formülü `[ 1, 0.5 ]` kullanılarak dönüştürülür.

### <a name="binning"></a>Binn

[Binning,](https://en.wikipedia.org/wiki/Data_binning) sürekli değerleri girdinin ayrı bir temsiline dönüştürür. Örneğin, özelliklerinizden birinin yaş olduğunu varsayalım. Binning, gerçek yaş değerini kullanmak yerine, bu değer için aralıklar oluşturur. 0-18 bir çöp kutusu olabilir, başka bir 19-35 ve benzeri olabilir.

Aşağıdaki giriş verilerini alın ve [`IDataView`](xref:Microsoft.ML.IDataView) aşağıdaki `data`bir çağrıya yükleyin:

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

Yöntemi kullanarak verileri kutulara [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) normalleştirin. Parametre, `maximumBinCount` verilerinizi sınıflandırmak için gereken kutu sayısının belirtilmesini sağlar. Bu örnekte, veriler iki kutuya konur.

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

Binning sonucu bin sınırları `[0,200000,Infinity]`oluşturur. Bu nedenle ortaya çıkan `[0,1,1]` kutular ilk gözlem 0-200000 arasında ve diğerleri 200000 daha büyük ama sonsuzdaha az olmasıdır.

## <a name="work-with-categorical-data"></a>Kategorik verilerle çalışma

En yaygın veri türlerinden biri kategorik verilerdir. Kategorik verilerin sınırlı sayıda kategorisi vardır. Örneğin, ABD'nin durumları veya bir dizi resimde bulunan hayvan türlerinin listesi. Kategorik veriler özellik veya etiket olsun, bir makine öğrenme modeli oluşturmak için kullanılabilen sayısal bir değerüzerine eşlenmelidir. ML.NET'da, çözdüğünen soruna bağlı olarak kategorik verilerle çalışmanın çeşitli yolları vardır.

### <a name="key-value-mapping"></a>Anahtar değeri eşleme

ML.NET' de anahtar, bir kategoriyi temsil eden bir tamsayı değeridir. Anahtar değeri eşleme, dize etiketlerini eğitim için benzersiz tamsayı değerlerine eşlemek için en sık kullanılır, ardından model tahmin yapmak için kullanıldığında dize değerlerine geri döner.

Anahtar değer eşleme gerçekleştirmek için kullanılan dönüşümler [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) ve [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A)vardır.

`MapValueToKey`modele bir eşleme sözlüğü ekler, `MapKeyToValue` böylece bir tahmin yaparken ters dönüşümü gerçekleştirebilir.

### <a name="one-hot-encoding"></a>Bir sıcak kodlama

Bir sıcak kodlama sonlu bir değer kümesialır ve bunları ikili gösterimi dizedeki benzersiz konumlarda tek `1` bir değere sahip tamsayılarla eşler. Kategorik verilerin örtük olarak sıralanması yoksa, bir sıcak kodlama en iyi seçim olabilir. Aşağıdaki tabloda posta kodları ham değerler olarak bir örnek gösterilmektedir.

|Ham değer|Bir sıcak kodlanmış değer|
|---------|---------------------|
|98052|00...01|
|98100|00...10|
|...|...|
|98109|10...00|

Kategorik verileri tek sıcak kodlanmış sayılara dönüştürme [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A)dönüştürme.

### <a name="hashing"></a>Karma

Karma, kategorik verileri sayılara dönüştürmenin başka bir yoludur. Karma işlev, rasgele bir boyutun (örneğin bir metin dizisi) verilerini sabit aralıklı bir sayıya eşler. Karma, özellikleri vektörelleştirmenin hızlı ve uzayda etkili bir yolu olabilir. Makine öğreniminde karma bir örnek, bilinen sözcüklerin bir sözlüğünü korumak yerine, e-postadaki her kelimenin karma ve büyük bir özellik vektörüne eklendiği e-posta spam filtrelemedir. Karma kullanımı bu şekilde sözlükte olmayan sözcüklerin kullanımı ile kötü amaçlı spam filtreleme sorunu önler.

ML.NET, metin, tarih ve sayısal veriler üzerinde karma gerçekleştirmek için [Karma](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) dönüştürme sağlar. Değer anahtarı eşleme gibi, karma dönüşümün çıktıları da anahtar türleridir.

## <a name="work-with-text-data"></a>Metin verileriyle çalışma

Kategorik veriler gibi, metin verilerinin de bir makine öğrenme modeli oluşturmak için kullanmadan önce sayısal özelliklere dönüştürülmesi gerekir. Daha ayrıntılı bir liste ve metin dönüşümlerinin açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.

Aşağıdaki veriler gibi verileri kullanarak aşağıdaki [`IDataView`](xref:Microsoft.ML.IDataView)verilere yüklenmiş:

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

ML.NET, [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) bir metnin dize değerini alan ve bir dizi bireysel dönüşüm uygulayarak metinden bir dizi özellik oluşturan dönüşümü sağlar.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

Elde edilen dönüştürme, `Description` sütundaki metin değerlerini aşağıdaki çıktıya benzeyen sayısal bir vektöre dönüştürür:

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Makyaj `FeaturizeText` dönüşümleri, özellik üretimi üzerinde daha ince tane kontrolü için ayrı ayrı da uygulanabilir.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator`yöntem tarafından gerçekleştirilen işlemlerin [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) bir alt kümesini içerir. Daha karmaşık bir boru hattının yararı, verilere uygulanan dönüşümler üzerinde kontrol ve görünürlüktür.

Örnek olarak ilk girişi kullanarak, aşağıdaki tarafından `textEstimator`tanımlanan dönüşüm adımları tarafından üretilen sonuçların ayrıntılı bir açıklamasıdır:

**Orijinal Metin: Bu iyi bir üründür**

|Dönüşüm | Açıklama | Sonuç
|--|--|--|
|1. Metni Normalleştirme | Varsayılan olarak tüm harfleri küçük harfe dönüştürür | Bu iyi bir üründür
|2. TokenizeWords | Dizeyi tek tek sözcüklere böler | ["this","is","a","iyi"," ürün"]
|3. Varsayılan StopKelimeleri Kaldırma | *Gibi* stopwords kaldırır ve *bir*. | ["iyi"," ürün"]
|4. MapValueToKey | Giriş verilerine göre anahtarların (kategorilerin) değerlerini eşler |  [1,2]
|5. Üretmis Gramlar | Metni ardışık sözcükler dizisine dönüştürür | [1,1,1,0,0]
|6. NormalizeLpNorm | Girişleri lp normlarına göre ölçeklendirin | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
