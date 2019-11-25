---
title: Modeli eğitme ve değerlendirme
description: Makine öğrenimi modelleri oluşturmayı, ölçümleri toplamayı ve ML.NET ile performansı ölçmeyi öğrenin. Bir Machine Learning modeli, yeni verileri kullanarak tahmine dayalı hale getirmek için eğitim verileri içindeki desenleri tanımlar.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 0e0f43225b9bf243c31b3095817bdcbdb3123012
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976767"
---
# <a name="train-and-evaluate-a-model"></a>Modeli eğitme ve değerlendirme

Makine öğrenimi modelleri oluşturmayı, ölçümleri toplamayı ve ML.NET ile performansı ölçmeyi öğrenin. Bu örnek bir regresyon modeli sunmakla birlikte, kavramlar diğer algoritmaların çoğunluğu genelinde uygulanabilir.

## <a name="split-data-for-training-and-testing"></a>Eğitim ve test için verileri bölme

Machine Learning modelinin amacı, eğitim verileri içindeki desenleri belirlemektir. Bu desenler, yeni verileri kullanarak tahmine dayalı hale getirmek için kullanılır.

Veriler `HousingData`gibi bir sınıfla modellenebilir.

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

Bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki veriler verilirler.

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

Verileri eğitme ve test kümelerine bölmek için [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) yöntemini kullanın. Sonuç, biri tren kümesi ve diğeri test kümesi için olmak üzere iki [`IDataView`](xref:Microsoft.ML.IDataView) üyesi içeren bir [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) nesnesi olur. Veri bölme yüzdesi `testFraction` parametresine göre belirlenir. Aşağıdaki kod parçacığı, test kümesi için özgün verilerin yüzde 20 ' sini tutuyor.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Verileri hazırlama

Bir makine öğrenimi modeli eğitimi öncesinde verilerin önceden işlenmesi gerekir. Veri hazırlama hakkında daha fazla bilgi için [veri hazırlığı hakkında nasıl yapılır makalesi](prepare-data-ml-net.md) ve [`transforms page`](../resources/transforms.md)bulunabilir.

ML.NET algoritmalarının giriş sütunu türlerinde kısıtlamalar vardır. Ayrıca, hiçbir değer belirtilmediğinde, giriş ve çıkış sütun adları için varsayılan değerler kullanılır.

### <a name="working-with-expected-column-types"></a>Beklenen sütun türleriyle çalışma

ML.NET ' deki makine öğrenimi algoritmaları, girdi olarak bilinen boyutun kayan bir vektörünü bekler. Tüm veriler zaten sayısal biçimde olduğunda ve birlikte işlenmek üzere tasarlanıyorsa (örn. resim piksel), [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliğini veri modelinize uygulayın.

Veriler tümüyle sayısal değilse ve her sütuna ayrı ayrı veri dönüştürmeleri uygulamak istiyorsanız, tüm sütunları yeni bir sütuna çıktı olan tek bir özellik vektöründe birleştirmek için tüm sütunlar işlendikten sonra [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) yöntemini kullanın.

Aşağıdaki kod parçacığı `Size` ve `HistoricalPrices` sütunlarını `Features`adlı yeni bir sütuna çıktı olan tek bir özellik vektörü halinde birleştirir. Ölçeklerde bir farklılık olduğundan, verileri normalleştirmek için `Features` sütununa [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) uygulanır.

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

ML.NET algoritmaları, hiçbiri belirtilmediğinde varsayılan sütun adlarını kullanır. Tüm traers, algoritmanın girdileri için `featureColumnName` adlı bir parametreye sahiptir ve geçerli olduğunda `labelColumnName`adlı beklenen değer için de bir parametreye sahip olurlar. Varsayılan olarak, bu değerler sırasıyla `Features` ve `Label`.

`Features`adlı yeni bir sütun oluşturmak için ön işleme sırasında [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) yöntemini kullanarak, önceden işlenmiş `IDataView`zaten mevcut olduğundan algoritmanın parametrelerinde özellik sütunu adını belirtmeye gerek yoktur. Etiket sütunu `CurrentPrice`, ancak [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği veri modelinde kullanıldığı için, ml.net `CurrentPrice` sütununu makine öğrenimi algoritması estimator öğesine `labelColumnName` parametresi sağlama ihtiyacını kaldıran `Label` olarak yeniden adlandırır.

Varsayılan sütun adlarını kullanmak istemiyorsanız, sonraki kod parçacığında gösterildiği gibi Machine Learning algoritması tahmin Aracı ' ı tanımlarken, özelliğin adlarını ve etiket sütunlarını parametre olarak etiketleyin:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Makine öğrenimi modelini eğitme

Veriler önceden işlendikten sonra, makine öğrenimi modelini [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regresyon algoritmasına eğerek [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) yöntemi kullanın.

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Model parametrelerini Ayıkla

Model eğitilirken, denetleme veya yeniden eğitim için öğrenilen [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) ayıklayın. [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) , eğitilen modelin sayısını ve öğrenilen katsayılarını veya ağırlıklarını sağlar.

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Diğer modellerin görevlerine özgü parametreleri vardır. Örneğin, [K-anlamı algoritması](xref:Microsoft.ML.Trainers.KMeansTrainer) , verileri centroıd 'ler temelinde kümeye koyar ve [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) , bu öğrenilen centroıd 'leri depolayan bir özellik içerir. Daha fazla bilgi edinmek için [`Microsoft.ML.Trainers` API belgelerini](xref:Microsoft.ML.Trainers) ziyaret edin ve adında `ModelParameters` içeren sınıfları arayın.

## <a name="evaluate-model-quality"></a>Model kalitesini değerlendir

En iyi performans sağlayan modeli seçmenize yardımcı olmak için test verilerinde performansını değerlendirmek gereklidir. Eğitilen modele yönelik çeşitli ölçümleri ölçmek için [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) yöntemini kullanın.

> [!NOTE]
> `Evaluate` yöntemi, hangi makine öğrenimi görevinin gerçekleştirildiğine bağlı olarak farklı ölçümler üretir. Daha fazla ayrıntı için [`Microsoft.ML.Data` API belgelerini](xref:Microsoft.ML.Data) ziyaret edin ve adında `Metrics` içeren sınıfları arayın.

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

1. Test veri kümesi önceden tanımlanmış veri hazırlama dönüştürmeleri kullanılarak önceden işlenir.
2. Eğitilen makine öğrenimi modeli, test verilerinde tahminleri yapmak için kullanılır.
3. `Evaluate` yönteminde, test veri kümesinin `CurrentPrice` sütunundaki değerler, regresyon modeli için ölçümleri hesaplamak üzere yeni çıkış tahminlerinin `Score` sütunuyla karşılaştırılır, bunlardan biri R-kare `rSquared` değişkeninde depolanır.

> [!NOTE]
> Bu küçük örnekte, R-kare, verilerin sınırlı büyüklüğü nedeniyle 0-1 aralığında olmayan bir sayıdır. Gerçek dünyada bir senaryoda, 0 ile 1 arasında bir değer görmeniz beklenir.
