---
title: Modeli eğitme ve değerlendirme
description: Makine öğrenimi modellerini oluşturun, Ölçümler ve Ölçüm performans ML.NET ile toplama öğrenin. Makine öğrenme modeli yeni verileri kullanarak tahmin yapmayı sağlayan eğitim verilerini içinde desen tanımlar.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 61cdaf693c417d02da95d1d79ab30eb2d30a057b
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397636"
---
# <a name="train-and-evaluate-a-model"></a>Modeli eğitme ve değerlendirme

Makine öğrenimi modellerini oluşturun, Ölçümler ve Ölçüm performans ML.NET ile toplama öğrenin. Bu örnek bir regresyon modeli eğitir olsa da, diğer algoritmalar çoğunu kavramları uygulanabilir.

## <a name="split-data-for-training-and-testing"></a>Verileri eğitim ve test için bölme

Makine öğrenme modelinin amacı, eğitim verilerini içinde desen belirlemektir. Bu düzenleri, yeni verileri kullanarak tahmin yapmak için kullanılır.

Aşağıdaki veri modeli verilen:

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

Verilerin bir [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Kullanım [ `TrainTestSplit` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) train verileri bölme ve test kümeleri için yöntem. Sonuç olacaktır bir [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) iki içeren bir nesne [ `IDataView` ](xref:Microsoft.ML.IDataView) üyeleri, biri train kümesi ve diğer test kümesi için. Verileri bölme yüzdesi belirlenir `testFraction` parametresi. Aşağıdaki kod parçacığında, özgün verilerin test kümesi için yüzde 20 kullanıma tutuyor.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Verileri hazırlama

Verilerin machine learning modeli eğitimi önce önceden işlenmiş olması gerekir. Veri hazırlama hakkında daha fazla bilgi bulunabilir [veri hazırlama ile ilgili nasıl yapılır makalesi](prepare-data-ml-net.md) yanı sıra [ `transforms page` ](../resources/transforms.md).

ML.NET algoritmaları giriş sütun türleri kısıtlamalar vardır. Ayrıca, herhangi bir değer belirtildiğinde giriş ve çıkış sütun adları için varsayılan değerler kullanılır.

### <a name="working-with-expected-column-types"></a>Beklenen sütun türleri ile çalışma

ML.NET, makine öğrenimi algoritmaları, giriş olarak bilinen boyutunun bir kayan nokta vektör bekler. Uygulama [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliğini tüm verileri sayısal biçimde zaten ve olmaya yönelik veri modelinizi birlikte (yani, görüntü piksel) işlenir. 

Veriler, tüm sayısal değil ve tek tek her sütun farklı veri dönüşümleri uygulamak kullanmak istiyorsanız [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) yöntemi tüm sütunları işlenmemiş tüm sütunları tek tek birleştirmek için Yeni bir sütun çıkışları tek bir özellik vektörü. 

Aşağıdaki kod parçacığı birleştirir `Size` ve `HistoricalPrices` adlı yeni bir sütun çıktı bir tek özellik vektör sütunlara `Features`. Ölçekler, fark olduğundan [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) uygulanan `Features` veri'leri normalleştirmek için sütun.

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

### <a name="working-with-default-column-names"></a>Varsayılan sütun adları ile çalışma

ML.NET algoritmalarını hiçbiri belirtilen varsayılan sütun adları kullanın. Tüm Eğitmenler adlı bir parametreye sahip `featureColumnName` algoritması ve geçerli de sahip oldukları bir parametre için beklenen değer çağrıldığında girişleri için `labelColumnName`. Varsayılan olarak, bu değerler `Features` ve `Label` sırasıyla. 

Kullanarak [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) yöntemi yeni bir sütun oluşturmak için ön işleme sırasında `Features`, içinde zaten mevcut olduğundan, algoritma parametrelerinde özelliği sütun adını belirtmek için gerek yoktur Ön işlemden `IDataView`. Etiket sütunu `CurrentPrice`, ancak [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği, veri modelinde kullanılır, ML.NET yeniden adlandırır `CurrentPrice` sütuna `Label` sağlama gereksinimini kaldırır `labelColumnName` Makine öğrenimi algoritması estimator parametresi. 

Varsayılan sütun adlarını kullanmak istemiyorsanız, özellik ve etiket sütunlarının adlarını makine öğrenimi algoritması estimator tarafından sonraki kod parçacığında gösterildiği gibi tanımlarken parametreler olarak geçirin:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Machine learning modeli eğitme

Verileri önceden işlenmiş olduğunda kullanın [ `Fit` ](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) yöntemi ile machine learning modelini eğitmek için [ `StochasticDualCoordinateAscent` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regresyon algoritması.

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Model parametreleri Ayıkla

Eğitilen modelin sonra öğrenilen ayıklamak [ `ModelParameters` ](xref:Microsoft.ML.Trainers.ModelParametersBase%601) İnceleme ya da yeniden eğitim için. [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) Eğilim ve öğrenilen katsayıları veya eğitim modeli ağırlıkları sağlayın. 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Diğer modelleri, kendi görevlere özgü parametrelere sahip. Örneğin, [K-ortalamaları algoritması](xref:Microsoft.ML.Trainers.KMeansTrainer) veri kümesine üzerinde centroids koyar ve [ `KMeansModelParameters` ](xref:Microsoft.ML.Trainers.KMeansModelParameters) bu öğrenilen centroids depolayan bir özellik içeriyor. Daha fazla bilgi için ziyaret [ `Microsoft.ML.Trainers` API belgeleri](xref:Microsoft.ML.Trainers) ve içeren sınıflar için konum `ModelParameters` adında. 

## <a name="evaluate-model-quality"></a>Model kalitesi değerlendir

En iyi performansa sahip model seçmenize yardımcı olması için test verilerini performansını değerlendirmek için gereklidir. Kullanım [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) eğitim modeli için çeşitli ölçümleri ölçme yöntemi.

> [!NOTE]
> `Evaluate` Yöntemi üreten farklı ölçümlere bağlı olarak hangi machine learning görev gerçekleştirildi. Daha fazla bilgi için ziyaret [ `Microsoft.ML.Data` API belgeleri](xref:Microsoft.ML.Data) ve içeren sınıflar için konum `Metrics` adında. 

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
1. Test veri kümesini kullanarak önceden tanımlanmış veri hazırlama dönüşümleri önceden işlenir. 
2. Eğitilen makine öğrenimi modeli, test verileri üzerindeki tahminlerde bulunmak için kullanılır.
3. İçinde `Evaluate` yöntemi, değerleri `CurrentPrice` sınama veri kümesi sütunu karşı karşılaştırılır `Score` yeni çıkış sütununun tahminler elde etmek için regresyon ölçümler hesaplamak için model, bunlardan biri, R karesi alınmış depolanır`rSquared` değişkeni.

> [!NOTE]
> Küçük Bu örnekte, bir sayı olan R kare 0-1 sınırlı veri boyutu nedeniyle aralıkta değil. Gerçek hayattaki bir senaryoda, 0 ile 1 arasında bir değer görmeyi beklemelisiniz.
