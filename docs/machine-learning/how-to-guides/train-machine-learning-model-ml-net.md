---
title: Modeli eğitme ve değerlendirme
description: Makine öğrenimi modelleri oluşturmayı, ölçümleri toplamayı ve ML.NET ile performansı ölçmeyi öğrenin. Bir Machine Learning modeli, yeni verileri kullanarak tahmine dayalı hale getirmek için eğitim verileri içindeki desenleri tanımlar.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: fc735f28bad91b9714d7e6bf2a9c7c620acacc4d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929341"
---
# <a name="train-and-evaluate-a-model"></a>Modeli eğitme ve değerlendirme

Makine öğrenimi modelleri oluşturmayı, ölçümleri toplamayı ve ML.NET ile performansı ölçmeyi öğrenin. Bu örnek bir regresyon modeli sunmakla birlikte, kavramlar diğer algoritmaların çoğunluğu genelinde uygulanabilir.

## <a name="split-data-for-training-and-testing"></a>Eğitim ve test için verileri bölme

Machine Learning modelinin amacı, eğitim verileri içindeki desenleri belirlemektir. Bu desenler, yeni verileri kullanarak tahmine dayalı hale getirmek için kullanılır.

Veriler, gibi `HousingData`bir sınıfa göre modellenebilir.

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

' A yüklenen aşağıdaki veriler verilirler [`IDataView`](xref:Microsoft.ML.IDataView).

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

Verileri tren ve test kümelerine bölmek için [yönteminikullanın.`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) Sonuç, biri tren kümesi [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) ve diğeri test kümesi [`IDataView`](xref:Microsoft.ML.IDataView) için olmak üzere iki üye içeren bir nesne olacaktır. Veri bölme yüzdesi `testFraction` parametreye göre belirlenir. Aşağıdaki kod parçacığı, test kümesi için özgün verilerin yüzde 20 ' sini tutuyor.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Verileri hazırlama

Bir makine öğrenimi modeli eğitimi öncesinde verilerin önceden işlenmesi gerekir. Veri hazırlama hakkında daha fazla bilgi için [veri hazırlığı nasıl yapılır makalesi](prepare-data-ml-net.md) ve [`transforms page`](../resources/transforms.md)' de bulunabilir.

ML.NET algoritmalarının giriş sütunu türlerinde kısıtlamalar vardır. Ayrıca, hiçbir değer belirtilmediğinde, giriş ve çıkış sütun adları için varsayılan değerler kullanılır.

### <a name="working-with-expected-column-types"></a>Beklenen sütun türleriyle çalışma

ML.NET ' deki makine öğrenimi algoritmaları, girdi olarak bilinen boyutun kayan bir vektörünü bekler. Tüm veriler zaten sayısal biçimde olduğunda ve birlikte işlenmek üzere tasarlanıyorsa (örn. resim piksel), [özniteliğiverimodelinizeuygulayın.`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 

Veriler tümüyle sayısal değilse ve her sütuna ayrı ayrı veri dönüştürmeleri uygulamak istiyorsanız, tüm sütunları tek bir özellik vektöründe birleştirmek için [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) tüm sütunlar işlendikten sonra yöntemi kullanın. Yeni bir sütuna çıktı. 

Aşağıdaki kod parçacığı, ve `Size` `HistoricalPrices` sütunlarını, adlı `Features`yeni bir sütuna çıktı olan tek bir özellik vektörü halinde birleştirir. Ölçeklerde bir farklılık olduğundan, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) verileri normalleştirmek için `Features` sütuna uygulanmış olması gerekir.

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

ML.NET algoritmaları, hiçbiri belirtilmediğinde varsayılan sütun adlarını kullanır. Tüm traers, algoritmanın girdileri için çağrılan `featureColumnName` bir parametreye sahiptir ve geçerli olduğunda, beklenen `labelColumnName`değer için bir parametre de vardır. Varsayılan olarak bu değerler `Features` ve `Label` sırasıyla. 

Adlı [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) `IDataView`yeni bir sütun oluşturmak için ön işleme sırasında yöntemini kullanarak, önceden işlenmiş durumda olduğundan, algoritmanın parametrelerinde özellik sütunu adını belirtmeniz gerekmez. `Features` Etiket sütunu, ancak `CurrentPrice` [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) öznitelik veri modelinde kullanıldığı `CurrentPrice` `Label` için ml.net, Machine Learning algoritmasına parametresağlamagereksiniminikaldıransütunuyenidenadlandırır.`labelColumnName` Tahmin Aracı. 

Varsayılan sütun adlarını kullanmak istemiyorsanız, sonraki kod parçacığında gösterildiği gibi Machine Learning algoritması tahmin Aracı ' ı tanımlarken, özelliğin adlarını ve etiket sütunlarını parametre olarak etiketleyin:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Makine öğrenimi modelini eğitme

Veriler önceden işlendikten sonra, makine öğrenimi modelini [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) gerileme algoritmayla eğitme yöntemini kullanın.

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Model parametrelerini Ayıkla

Model eğitilirken İnceleme veya yeniden eğitim için öğrenilen [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) ' ı ayıklayın. Eğitilen modelin sapve öğrenilen katsayılarını veya ağırlıklarını [sağlar.`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Diğer modellerin görevlerine özgü parametreleri vardır. Örneğin, [K-anlamı algoritması](xref:Microsoft.ML.Trainers.KMeansTrainer) , verileri centroıd 'ler temelinde kümeye koyar ve [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) Bu öğrenilen centroıd 'leri depolayan bir özelliği içerir. Daha fazla bilgi edinmek için [ `Microsoft.ML.Trainers` API belgelerini](xref:Microsoft.ML.Trainers) ziyaret edin ve adlarını içeren `ModelParameters` sınıfları arayın. 

## <a name="evaluate-model-quality"></a>Model kalitesini değerlendir

En iyi performans sağlayan modeli seçmenize yardımcı olmak için test verilerinde performansını değerlendirmek gereklidir. Eğitilen modele yönelik çeşitli ölçümleri ölçmek için [yönteminikullanın.`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*)

> [!NOTE]
> Yöntemi `Evaluate` , hangi makine öğrenimi görevinin gerçekleştirildiğine bağlı olarak farklı ölçümler üretir. Daha fazla ayrıntı için [ `Microsoft.ML.Data` API belgelerini](xref:Microsoft.ML.Data) ziyaret edin ve adlarını içeren `Metrics` sınıfları arayın. 

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
3. Yönteminde, test veri `CurrentPrice` `Score` kümesi sütunundaki değerler, regresyon modeli için ölçümleri hesaplamak üzere yeni çıkış tahminlerinin sütunuyla karşılaştırılır, bunlardan biri R-kare `Evaluate` `rSquared` değişken.

> [!NOTE]
> Bu küçük örnekte, R-kare, verilerin sınırlı büyüklüğü nedeniyle 0-1 aralığında olmayan bir sayıdır. Gerçek dünyada bir senaryoda, 0 ile 1 arasında bir değer görmeniz beklenir.
