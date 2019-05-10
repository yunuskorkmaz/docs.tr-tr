---
title: Eğitme ve modeli değerlendirme
description: Eğitme ve değerlendirme ML.NET, makine öğrenimi modelleri hakkında bilgi edinin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2abb17aad6091cd6a5f0b6f82835011d01b40153
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063632"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="39c74-103">Eğitme ve modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="39c74-103">Train and evaluate a model</span></span>

<span data-ttu-id="39c74-104">Makine öğrenimi modellerini Derleme ve öğrenilen parametreleri Ayıkla ML.NET performansı ölçmek öğrenin.</span><span class="sxs-lookup"><span data-stu-id="39c74-104">Learn how to build machine learning models, extract learned parameters and measure performance with ML.NET.</span></span> <span data-ttu-id="39c74-105">Bu örnek bir regresyon modeli eğitir olsa da, diğer algoritmalar çoğunu kavramları uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="39c74-105">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="39c74-106">Verileri eğitim ve test için bölme</span><span class="sxs-lookup"><span data-stu-id="39c74-106">Split data for training and testing</span></span>

<span data-ttu-id="39c74-107">Makine öğrenme modelinin amacı, eğitim verilerini içinde desen belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="39c74-107">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="39c74-108">Bu düzenleri, yeni verileri kullanarak tahmin yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39c74-108">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="39c74-109">Aşağıdaki veri modeli verilen:</span><span class="sxs-lookup"><span data-stu-id="39c74-109">Given the following data model:</span></span>

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

<span data-ttu-id="39c74-110">Verilerin bir [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="39c74-110">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="39c74-111">Kullanım [ `TrainTestSplit` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) train verileri bölme ve test kümeleri için yöntem.</span><span class="sxs-lookup"><span data-stu-id="39c74-111">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="39c74-112">Sonuç olacaktır bir [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) iki içeren bir nesne [ `IDataView` ](xref:Microsoft.ML.IDataView) üyeleri, biri train kümesi ve diğer test kümesi için.</span><span class="sxs-lookup"><span data-stu-id="39c74-112">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="39c74-113">Verileri bölme yüzdesi belirlenir `testFraction` parametresi.</span><span class="sxs-lookup"><span data-stu-id="39c74-113">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="39c74-114">Aşağıdaki kod parçacığında, özgün verilerin test kümesi için yüzde 20 kullanıma tutuyor.</span><span class="sxs-lookup"><span data-stu-id="39c74-114">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="39c74-115">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="39c74-115">Prepare the data</span></span>

<span data-ttu-id="39c74-116">Verilerin machine learning modeli eğitimi önce önceden işlenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="39c74-116">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="39c74-117">Veri hazırlama hakkında daha fazla bilgi bulunabilir [veri hazırlama ile ilgili nasıl yapılır makalesi](prepare-data-ml-net.md) yanı sıra [ `transforms page` ](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="39c74-117">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="39c74-118">ML.NET algoritmaları giriş sütun türleri kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="39c74-118">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="39c74-119">Ayrıca, herhangi bir değer belirtildiğinde giriş ve çıkış sütun adları için varsayılan değerler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39c74-119">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="39c74-120">Beklenen sütun türleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="39c74-120">Working with expected column types</span></span>

<span data-ttu-id="39c74-121">ML.NET, makine öğrenimi algoritmaları, giriş olarak bilinen boyutunun bir kayan nokta vektör bekler.</span><span class="sxs-lookup"><span data-stu-id="39c74-121">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="39c74-122">Uygulama [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliğini tüm verileri sayısal biçimde zaten ve olmaya yönelik veri modelinizi birlikte (yani, görüntü piksel) işlenir.</span><span class="sxs-lookup"><span data-stu-id="39c74-122">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span> 

<span data-ttu-id="39c74-123">Veriler, tüm sayısal değil ve tek tek her sütun farklı veri dönüşümleri uygulamak kullanmak istiyorsanız [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) yöntemi tüm sütunları işlenmemiş tüm sütunları tek tek birleştirmek için Yeni bir sütun çıkışları tek bir özellik vektörü.</span><span class="sxs-lookup"><span data-stu-id="39c74-123">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span> 

<span data-ttu-id="39c74-124">Aşağıdaki kod parçacığı birleştirir `Size` ve `HistoricalPrices` adlı yeni bir sütun çıktı bir tek özellik vektör sütunlara `Features`.</span><span class="sxs-lookup"><span data-stu-id="39c74-124">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="39c74-125">Ölçekler, fark olduğundan [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) uygulanan `Features` veri'leri normalleştirmek için sütun.</span><span class="sxs-lookup"><span data-stu-id="39c74-125">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply tranforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a><span data-ttu-id="39c74-126">Varsayılan sütun adları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="39c74-126">Working with default column names</span></span>

<span data-ttu-id="39c74-127">ML.NET algoritmalarını hiçbiri belirtilen varsayılan sütun adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="39c74-127">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="39c74-128">Tüm Eğitmenler adlı bir parametreye sahip `featureColumnName` algoritması ve geçerli de sahip oldukları bir parametre için beklenen değer çağrıldığında girişleri için `labelColumnName`.</span><span class="sxs-lookup"><span data-stu-id="39c74-128">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="39c74-129">Varsayılan olarak, bu değerler `Features` ve `Label` sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="39c74-129">By default those values are `Features` and `Label` respectively.</span></span> 

<span data-ttu-id="39c74-130">Kullanarak [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) yöntemi yeni bir sütun oluşturmak için ön işleme sırasında `Features`, içinde zaten mevcut olduğundan, algoritma parametrelerinde özelliği sütun adını belirtmek için gerek yoktur Ön işlemden `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="39c74-130">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="39c74-131">Etiket sütunu `CurrentPrice`, ancak [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği, veri modelinde kullanılır, ML.NET yeniden adlandırır `CurrentPrice` sütuna `Label` sağlama gereksinimini kaldırır `labelColumnName` Makine öğrenimi algoritması estimator parametresi.</span><span class="sxs-lookup"><span data-stu-id="39c74-131">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span> 

<span data-ttu-id="39c74-132">Varsayılan sütun adlarını kullanmak istemiyorsanız, özellik ve etiket sütunlarının adlarını makine öğrenimi algoritması estimator tarafından sonraki kod parçacığında gösterildiği gibi tanımlarken parametreler olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="39c74-132">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="39c74-133">Machine learning modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="39c74-133">Train the machine learning model</span></span>

<span data-ttu-id="39c74-134">Verileri önceden işlenmiş olduğunda kullanın [ `Fit` ](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) yöntemi ile machine learning modelini eğitmek için [ `StochasticDualCoordinateAscent` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regresyon algoritması.</span><span class="sxs-lookup"><span data-stu-id="39c74-134">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoodrinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="39c74-135">Model parametreleri Ayıkla</span><span class="sxs-lookup"><span data-stu-id="39c74-135">Extract model parameters</span></span>

<span data-ttu-id="39c74-136">Eğitilen modelin sonra öğrenilen ayıklamak [ `ModelParameters` ](xref:Microsoft.ML.Trainers.ModelParametersBase`1) İnceleme ya da yeniden eğitim için.</span><span class="sxs-lookup"><span data-stu-id="39c74-136">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase`1) for inspection or re-training.</span></span> <span data-ttu-id="39c74-137">[ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) Eğilim ve öğrenilen katsayıları veya eğitim modeli ağırlıkları sağlayın.</span><span class="sxs-lookup"><span data-stu-id="39c74-137">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span> 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="39c74-138">Diğer modelleri, kendi görevlere özgü parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="39c74-138">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="39c74-139">Örneğin, [K-ortalamaları algoritması](xref:Microsoft.ML.Trainers.KMeansTrainer) veri kümesine üzerinde centroids koyar ve [ `KMeansModelParameters` ](xref:Microsoft.ML.Trainers.KMeansModelParameters) bu öğrenilen centroids depolayan bir özellik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="39c74-139">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="39c74-140">Daha fazla bilgi için ziyaret [ `Microsoft.ML.Trainers` API belgeleri](xref:Microsoft.ML.Trainers) ve içeren sınıflar için konum `ModelParameters` adında.</span><span class="sxs-lookup"><span data-stu-id="39c74-140">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span> 

## <a name="evaluate-model-quality"></a><span data-ttu-id="39c74-141">Model kalitesi değerlendir</span><span class="sxs-lookup"><span data-stu-id="39c74-141">Evaluate model quality</span></span>

<span data-ttu-id="39c74-142">En iyi performansa sahip model seçmenize yardımcı olması için test verilerini performansını değerlendirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="39c74-142">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="39c74-143">Kullanım [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) eğitim modeli için çeşitli ölçümleri ölçme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="39c74-143">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="39c74-144">`Evaluate` Farklı ölçümlere bağlı olarak hangi machine learning görev olmuştur gerçekleştirildi yöntemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39c74-144">The `Evaluate` method produces different metrics depending on which machine learning task was was performed.</span></span> <span data-ttu-id="39c74-145">Daha fazla bilgi için ziyaret [ `Microsoft.ML.Data` API belgeleri](xref:Microsoft.ML.Data) ve içeren sınıflar için konum `Metrics` adında.</span><span class="sxs-lookup"><span data-stu-id="39c74-145">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span> 

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

<span data-ttu-id="39c74-146">Önceki kod örneğinde:</span><span class="sxs-lookup"><span data-stu-id="39c74-146">In the previous code sample:</span></span>  
1. <span data-ttu-id="39c74-147">Test veri kümesini kullanarak önceden tanımlanmış veri hazırlama dönüşümleri önceden işlenir.</span><span class="sxs-lookup"><span data-stu-id="39c74-147">Test data set is pre-processed using the data preparation transforms previously defined.</span></span> 
2. <span data-ttu-id="39c74-148">Eğitilen makine öğrenimi modeli, test verileri üzerindeki tahminlerde bulunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39c74-148">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="39c74-149">İçinde `Evaluate` yöntemi, değerleri `CurrentPrice` sınama veri kümesi sütunu karşı karşılaştırılır `Score` yeni çıkış sütununun tahminler elde etmek için regresyon ölçümler hesaplamak için model, bunlardan biri, R karesi alınmış depolanır`rSquared` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="39c74-149">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="39c74-150">Küçük Bu örnekte, bir sayı olan R kare 0-1 sınırlı veri boyutu nedeniyle aralıkta değil.</span><span class="sxs-lookup"><span data-stu-id="39c74-150">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="39c74-151">Gerçek hayattaki bir senaryoda, 0 ile 1 arasında bir değer görmeyi beklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="39c74-151">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
