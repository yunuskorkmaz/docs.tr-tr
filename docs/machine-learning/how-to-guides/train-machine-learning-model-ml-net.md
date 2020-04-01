---
title: Modeli eğitme ve değerlendirme
description: Makine öğrenimi modelleri oluşturmayı, ölçümleri nasıl toplayıp ML.NET performansı nasıl ölçtüğünü öğrenin. Makine öğrenimi modeli, yeni veriler kullanarak öngörülerde bulunmak için eğitim verilerindeki desenleri tanımlar.
ms.date: 03/31/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 51499f2c0ece615a99740bd9b27f99d4b5ed1d01
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523855"
---
# <a name="train-and-evaluate-a-model"></a>Modeli eğitme ve değerlendirme

Makine öğrenimi modelleri oluşturmayı, ölçümleri nasıl toplayıp ML.NET performansı nasıl ölçtüğünü öğrenin. Bu örnek bir regresyon modeli eğitse de, kavramlar diğer algoritmaların çoğunda uygulanabilir.

## <a name="split-data-for-training-and-testing"></a>Eğitim ve test için verileri bölme

Makine öğrenimi modelinin amacı, eğitim verilerindeki desenleri belirlemektir. Bu desenler, yeni veriler kullanarak öngörülerde bulunmak için kullanılır.

Veriler gibi `HousingData`bir sınıf tarafından modellenebilir.

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

Bir ' ye yüklenen aşağıdaki [`IDataView`](xref:Microsoft.ML.IDataView)veriler göz önüne alındığında.

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

Verileri [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) tren ve test kümelerine bölmek için yöntemi kullanın. Sonuç, biri [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) tren seti, [`IDataView`](xref:Microsoft.ML.IDataView) diğeri test kümesi için olmak üzere iki üyeiçeren bir nesne olacaktır. Veri bölme yüzdesi `testFraction` parametre tarafından belirlenir. Aşağıdaki parçacık, test kümesi için orijinal verilerin yüzde 20'sini dışarıda tutuyor.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Verileri hazırlama

Bir makine öğrenme modeli nin eğitilmesinden önce verilerin önceden işlenmesi gerekir. Veri hazırlama hakkında daha fazla bilgi [veri hazırlık nasıl-nasıl](prepare-data-ml-net.md) [`transforms page`](../resources/transforms.md)makale yanı sıra bulunabilir .

ML.NET algoritmaların giriş sütunu türlerinde kısıtlamaları vardır. Ayrıca, hiçbir değer belirtilmediğinde giriş ve çıkış sütun adları için varsayılan değerler kullanılır.

### <a name="working-with-expected-column-types"></a>Beklenen sütun türleri ile çalışma

ML.NET makine öğrenme algoritmaları giriş olarak bilinen boyutta bir float vektör bekliyoruz. [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) Tüm veriler zaten sayısal biçimdeyken ve birlikte işlenmesi amaçlanan (yani görüntü pikselleri) veri modelinize özniteliği uygulayın.

Verilerin tümü sayısal değilse ve sütunların her birine ayrı ayrı farklı veri [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) dönüşümleri uygulamak istiyorsanız, tüm sütunlar işlendikten sonra tüm sütunları yeni bir sütuna çıktısı olan tek bir özellik vektöründe birleştirmek için yöntemi kullanın.

Aşağıdaki parçacık, sütunları `Size` ve `HistoricalPrices` sütunları, `Features`yeni bir sütuna çıktı olan tek bir özellik vektöründe birleştirir. Ölçeklerde bir fark olduğundan, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) verileri normalleştirmek için `Features` sütuna uygulanır.

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply transforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a>Varsayılan sütun adlarıyla çalışma

ML.NET algoritmaları hiçbiri belirtilmediğinde varsayılan sütun adlarını kullanır. Tüm eğitmenler algoritma nın `featureColumnName` girişleri için çağrılan bir parametreye sahiptir ve uygulanabilir olduğunda `labelColumnName`da beklenen değer için bir parametreye sahiptirler. Varsayılan olarak bu `Features` `Label` değerler sırasıyla ve sırasıyla.

Ön işleme [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) sırasında yöntemi kullanarak yeni bir `Features`sütun oluşturmak için , zaten önceden işlenmiş var olduğundan algoritmaparametrelerinde özellik sütun `IDataView`adını belirtmek için gerek yoktur. Etiket `CurrentPrice`sütunu, ancak [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) öznitelik veri modelinde kullanıldığından, ML.NET `CurrentPrice` makine `Label` öğrenme algoritması tahmincisi `labelColumnName` ne parametre sağlamak için gereksinimi kaldırır sütun yeniden adlandırır.

Varsayılan sütun adlarını kullanmak istemiyorsanız, makine öğrenme algoritması tahmincisi tanımlanırken özellik ve etiket sütunlarının adlarını sonraki parçacıkta gösterildiği gibi parametreler olarak geçirin:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="caching-data"></a>Verileri önbelleğe alma

Varsayılan olarak, veriler işlendiğinde, tembelce yüklenir veya akışlanır, bu da eğitmenlerin verileri diskten yükleyebileceği ve eğitim sırasında birden çok kez üzerinde yeniden işlem yapılabileceği anlamına gelir. Bu nedenle, verilerin diskten yüklenme sayısını azaltmak için belleğe sığan veri kümeleri için önbelleğe alma önerilir. Önbelleğe alma kullanılarak [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) bir [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A)parçası olarak yapılır.

Boru hattındaki herhangi [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) bir eğitmenden önce kullanılması önerilir.

Aşağıdakileri [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)kullanarak, [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) eğitmen önce ekleyen daha sonra eğitmen tarafından kullanılmak üzere önceki tahmin sonuçları önbelleğe

```csharp
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
// 3. Cache prepared data
// 4. Use Sdca trainer to train the model
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .AppendCacheCheckpoint(mlContext);
        .Append(mlContext.Regression.Trainers.Sdca());
```

## <a name="train-the-machine-learning-model"></a>Makine öğrenme modelini eğitin

Veriler önceden işlendikten sonra, [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) makine öğrenme modelini regresyon algoritmasıyla [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) eğitmek için yöntemi kullanın.

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Ayıklama modeli parametreleri

Model eğitildikten sonra, inceleme [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) veya yeniden eğitim için öğrenilenleri ayıklayın. Eğitimli [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) modelin önyargı ve öğrenilen katsayıları veya ağırlıkları sağlar.

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Diğer modeller, görevlerine özgü parametrelere sahiptir. Örneğin, [K-Means algoritması](xref:Microsoft.ML.Trainers.KMeansTrainer) verileri merkeze dayalı kümeye [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) koyar ve bu öğrenilen santriomları depolayan bir özellik içerir. Daha fazla bilgi edinmek için [ `Microsoft.ML.Trainers` API Dokümantasyon'u](xref:Microsoft.ML.Trainers) ziyaret edin ve kendi adlarında bulunan `ModelParameters` sınıfları arayın.

## <a name="evaluate-model-quality"></a>Model kalitesini değerlendirme

En iyi performans gösteren modeli seçmenize yardımcı olmak için, test verilerindeki performansını değerlendirmek önemlidir. Eğitilmiş [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) model için çeşitli ölçümleri ölçmek için yöntemi kullanın.

> [!NOTE]
> Yöntem, `Evaluate` makine öğrenimi görevinin gerçekleştirildiği yönteme bağlı olarak farklı ölçümler üretir. Daha fazla ayrıntı için [ `Microsoft.ML.Data` API Belgeleri'ni](xref:Microsoft.ML.Data) `Metrics` ziyaret edin ve adlarında bulunan sınıfları arayın.

```csharp
// Measure trained model performance
// Apply data prep transformer to test data
IDataView transformedTestData = dataPrepTransformer.Transform(testData);

// Use trained model to make inferences on test data
IDataView testDataPredictions = trainedModel.Transform(transformedTestData);

// Extract model metrics and get RSquared
RegressionMetrics trainedModelMetrics = mlContext.Regression.Evaluate(testDataPredictions);
double rSquared = trainedModelMetrics.RSquared;
```

Önceki kod örneğinde:

1. Test veri kümesi, daha önce tanımlanan veri hazırlama dönüşümleri kullanılarak önceden işlenir.
2. Eğitimli makine öğrenme modeli test verileri üzerinde tahminler yapmak için kullanılır.
3. Yöntemde, test veri `CurrentPrice` kümesisütunundaki değerler, regresyon modelinin ölçümlerini hesaplamak için yeni çıktı tahminlerinin `Score` sütununa karşılaştırılır ve bunlardan `rSquared` biri olan R-Squared değişkende depolanır. `Evaluate`

> [!NOTE]
> Bu küçük örnekte, R-Squared, verilerin sınırlı boyutu nedeniyle 0-1 aralığında olmayan bir sayıdır. Gerçek bir senaryoda, 0 ile 1 arasında bir değer görmeyi beklemelisiniz.
