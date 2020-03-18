---
title: Modeli eğitme ve değerlendirme
description: Makine öğrenimi modelleri oluşturmayı, ölçümleri nasıl toplayıp ML.NET performansı nasıl ölçtüğünü öğrenin. Makine öğrenimi modeli, yeni veriler kullanarak öngörülerde bulunmak için eğitim verilerindeki desenleri tanımlar.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 0e0f43225b9bf243c31b3095817bdcbdb3123012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976767"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="1b591-104">Modeli eğitme ve değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1b591-104">Train and evaluate a model</span></span>

<span data-ttu-id="1b591-105">Makine öğrenimi modelleri oluşturmayı, ölçümleri nasıl toplayıp ML.NET performansı nasıl ölçtüğünü öğrenin.</span><span class="sxs-lookup"><span data-stu-id="1b591-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="1b591-106">Bu örnek bir regresyon modeli eğitse de, kavramlar diğer algoritmaların çoğunda uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1b591-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="1b591-107">Eğitim ve test için verileri bölme</span><span class="sxs-lookup"><span data-stu-id="1b591-107">Split data for training and testing</span></span>

<span data-ttu-id="1b591-108">Makine öğrenimi modelinin amacı, eğitim verilerindeki desenleri belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="1b591-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="1b591-109">Bu desenler, yeni veriler kullanarak öngörülerde bulunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b591-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="1b591-110">Veriler gibi `HousingData`bir sınıf tarafından modellenebilir.</span><span class="sxs-lookup"><span data-stu-id="1b591-110">The data can be modeled by a class like `HousingData`.</span></span>

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

<span data-ttu-id="1b591-111">Bir ' ye yüklenen aşağıdaki [`IDataView`](xref:Microsoft.ML.IDataView)veriler göz önüne alındığında.</span><span class="sxs-lookup"><span data-stu-id="1b591-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

<span data-ttu-id="1b591-112">Verileri [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) tren ve test kümelerine bölmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b591-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="1b591-113">Sonuç, biri [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) tren seti, [`IDataView`](xref:Microsoft.ML.IDataView) diğeri test kümesi için olmak üzere iki üyeiçeren bir nesne olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1b591-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="1b591-114">Veri bölme yüzdesi `testFraction` parametre tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1b591-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="1b591-115">Aşağıdaki parçacık, test kümesi için orijinal verilerin yüzde 20'sini dışarıda tutuyor.</span><span class="sxs-lookup"><span data-stu-id="1b591-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="1b591-116">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="1b591-116">Prepare the data</span></span>

<span data-ttu-id="1b591-117">Bir makine öğrenme modeli nin eğitilmesinden önce verilerin önceden işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b591-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="1b591-118">Veri hazırlama hakkında daha fazla bilgi [veri hazırlık nasıl-nasıl](prepare-data-ml-net.md) [`transforms page`](../resources/transforms.md)makale yanı sıra bulunabilir .</span><span class="sxs-lookup"><span data-stu-id="1b591-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="1b591-119">ML.NET algoritmaların giriş sütunu türlerinde kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="1b591-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="1b591-120">Ayrıca, hiçbir değer belirtilmediğinde giriş ve çıkış sütun adları için varsayılan değerler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b591-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="1b591-121">Beklenen sütun türleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="1b591-121">Working with expected column types</span></span>

<span data-ttu-id="1b591-122">ML.NET makine öğrenme algoritmaları giriş olarak bilinen boyutta bir float vektör bekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="1b591-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="1b591-123">[`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) Tüm veriler zaten sayısal biçimdeyken ve birlikte işlenmesi amaçlanan (yani görüntü pikselleri) veri modelinize özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1b591-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span>

<span data-ttu-id="1b591-124">Verilerin tümü sayısal değilse ve sütunların her birine ayrı ayrı farklı veri [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) dönüşümleri uygulamak istiyorsanız, tüm sütunlar işlendikten sonra tüm sütunları yeni bir sütuna çıktısı olan tek bir özellik vektöründe birleştirmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b591-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span>

<span data-ttu-id="1b591-125">Aşağıdaki parçacık, sütunları `Size` ve `HistoricalPrices` sütunları, `Features`yeni bir sütuna çıktı olan tek bir özellik vektöründe birleştirir.</span><span class="sxs-lookup"><span data-stu-id="1b591-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="1b591-126">Ölçeklerde bir fark olduğundan, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) verileri normalleştirmek için `Features` sütuna uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1b591-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

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

### <a name="working-with-default-column-names"></a><span data-ttu-id="1b591-127">Varsayılan sütun adlarıyla çalışma</span><span class="sxs-lookup"><span data-stu-id="1b591-127">Working with default column names</span></span>

<span data-ttu-id="1b591-128">ML.NET algoritmaları hiçbiri belirtilmediğinde varsayılan sütun adlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b591-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="1b591-129">Tüm eğitmenler algoritma nın `featureColumnName` girişleri için çağrılan bir parametreye sahiptir ve uygulanabilir olduğunda `labelColumnName`da beklenen değer için bir parametreye sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="1b591-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="1b591-130">Varsayılan olarak bu `Features` `Label` değerler sırasıyla ve sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="1b591-130">By default those values are `Features` and `Label` respectively.</span></span>

<span data-ttu-id="1b591-131">Ön işleme [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) sırasında yöntemi kullanarak yeni bir `Features`sütun oluşturmak için , zaten önceden işlenmiş var olduğundan algoritmaparametrelerinde özellik sütun `IDataView`adını belirtmek için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="1b591-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="1b591-132">Etiket `CurrentPrice`sütunu, ancak [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) öznitelik veri modelinde kullanıldığından, ML.NET `CurrentPrice` makine `Label` öğrenme algoritması tahmincisi `labelColumnName` ne parametre sağlamak için gereksinimi kaldırır sütun yeniden adlandırır.</span><span class="sxs-lookup"><span data-stu-id="1b591-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span>

<span data-ttu-id="1b591-133">Varsayılan sütun adlarını kullanmak istemiyorsanız, makine öğrenme algoritması tahmincisi tanımlanırken özellik ve etiket sütunlarının adlarını sonraki parçacıkta gösterildiği gibi parametreler olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="1b591-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="1b591-134">Makine öğrenme modelini eğitin</span><span class="sxs-lookup"><span data-stu-id="1b591-134">Train the machine learning model</span></span>

<span data-ttu-id="1b591-135">Veriler önceden işlendikten sonra, [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) makine öğrenme modelini regresyon algoritmasıyla [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) eğitmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b591-135">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="1b591-136">Ayıklama modeli parametreleri</span><span class="sxs-lookup"><span data-stu-id="1b591-136">Extract model parameters</span></span>

<span data-ttu-id="1b591-137">Model eğitildikten sonra, inceleme [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) veya yeniden eğitim için öğrenilen ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="1b591-137">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or re-training.</span></span> <span data-ttu-id="1b591-138">Eğitimli [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) modelin önyargı ve öğrenilen katsayıları veya ağırlıkları sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b591-138">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span>

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="1b591-139">Diğer modeller, görevlerine özgü parametrelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1b591-139">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="1b591-140">Örneğin, [K-Means algoritması](xref:Microsoft.ML.Trainers.KMeansTrainer) verileri merkeze dayalı kümeye [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) koyar ve bu öğrenilen santriomları depolayan bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="1b591-140">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="1b591-141">Daha fazla bilgi edinmek için [ `Microsoft.ML.Trainers` API Dokümantasyon'u](xref:Microsoft.ML.Trainers) ziyaret edin ve kendi adlarında bulunan `ModelParameters` sınıfları arayın.</span><span class="sxs-lookup"><span data-stu-id="1b591-141">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span>

## <a name="evaluate-model-quality"></a><span data-ttu-id="1b591-142">Model kalitesini değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1b591-142">Evaluate model quality</span></span>

<span data-ttu-id="1b591-143">En iyi performans gösteren modeli seçmenize yardımcı olmak için, test verilerindeki performansını değerlendirmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1b591-143">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="1b591-144">Eğitilmiş [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) model için çeşitli ölçümleri ölçmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b591-144">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="1b591-145">Yöntem, `Evaluate` makine öğrenimi görevinin gerçekleştirildiği yönteme bağlı olarak farklı ölçümler üretir.</span><span class="sxs-lookup"><span data-stu-id="1b591-145">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="1b591-146">Daha fazla ayrıntı için [ `Microsoft.ML.Data` API Belgeleri'ni](xref:Microsoft.ML.Data) `Metrics` ziyaret edin ve adlarında bulunan sınıfları arayın.</span><span class="sxs-lookup"><span data-stu-id="1b591-146">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span>

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

<span data-ttu-id="1b591-147">Önceki kod örneğinde:</span><span class="sxs-lookup"><span data-stu-id="1b591-147">In the previous code sample:</span></span>

1. <span data-ttu-id="1b591-148">Test veri kümesi, daha önce tanımlanan veri hazırlama dönüşümleri kullanılarak önceden işlenir.</span><span class="sxs-lookup"><span data-stu-id="1b591-148">Test data set is pre-processed using the data preparation transforms previously defined.</span></span>
2. <span data-ttu-id="1b591-149">Eğitimli makine öğrenme modeli test verileri üzerinde tahminler yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b591-149">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="1b591-150">Yöntemde, test veri `CurrentPrice` kümesisütunundaki değerler, regresyon modelinin ölçümlerini hesaplamak için yeni çıktı tahminlerinin `Score` sütununa karşılaştırılır ve bunlardan `rSquared` biri olan R-Squared değişkende depolanır. `Evaluate`</span><span class="sxs-lookup"><span data-stu-id="1b591-150">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="1b591-151">Bu küçük örnekte, R-Squared, verilerin sınırlı boyutu nedeniyle 0-1 aralığında olmayan bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="1b591-151">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="1b591-152">Gerçek bir senaryoda, 0 ile 1 arasında bir değer görmeyi beklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1b591-152">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
