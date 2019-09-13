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
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="305ab-104">Modeli eğitme ve değerlendirme</span><span class="sxs-lookup"><span data-stu-id="305ab-104">Train and evaluate a model</span></span>

<span data-ttu-id="305ab-105">Makine öğrenimi modelleri oluşturmayı, ölçümleri toplamayı ve ML.NET ile performansı ölçmeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="305ab-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="305ab-106">Bu örnek bir regresyon modeli sunmakla birlikte, kavramlar diğer algoritmaların çoğunluğu genelinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="305ab-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="305ab-107">Eğitim ve test için verileri bölme</span><span class="sxs-lookup"><span data-stu-id="305ab-107">Split data for training and testing</span></span>

<span data-ttu-id="305ab-108">Machine Learning modelinin amacı, eğitim verileri içindeki desenleri belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="305ab-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="305ab-109">Bu desenler, yeni verileri kullanarak tahmine dayalı hale getirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="305ab-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="305ab-110">Veriler, gibi `HousingData`bir sınıfa göre modellenebilir.</span><span class="sxs-lookup"><span data-stu-id="305ab-110">The data can be modeled by a class like `HousingData`.</span></span>

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

<span data-ttu-id="305ab-111">' A yüklenen aşağıdaki veriler verilirler [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="305ab-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

<span data-ttu-id="305ab-112">Verileri tren ve test kümelerine bölmek için [yönteminikullanın.`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*)</span><span class="sxs-lookup"><span data-stu-id="305ab-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="305ab-113">Sonuç, biri tren kümesi [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) ve diğeri test kümesi [`IDataView`](xref:Microsoft.ML.IDataView) için olmak üzere iki üye içeren bir nesne olacaktır.</span><span class="sxs-lookup"><span data-stu-id="305ab-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="305ab-114">Veri bölme yüzdesi `testFraction` parametreye göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="305ab-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="305ab-115">Aşağıdaki kod parçacığı, test kümesi için özgün verilerin yüzde 20 ' sini tutuyor.</span><span class="sxs-lookup"><span data-stu-id="305ab-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="305ab-116">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="305ab-116">Prepare the data</span></span>

<span data-ttu-id="305ab-117">Bir makine öğrenimi modeli eğitimi öncesinde verilerin önceden işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="305ab-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="305ab-118">Veri hazırlama hakkında daha fazla bilgi için [veri hazırlığı nasıl yapılır makalesi](prepare-data-ml-net.md) ve [`transforms page`](../resources/transforms.md)' de bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="305ab-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="305ab-119">ML.NET algoritmalarının giriş sütunu türlerinde kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="305ab-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="305ab-120">Ayrıca, hiçbir değer belirtilmediğinde, giriş ve çıkış sütun adları için varsayılan değerler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="305ab-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="305ab-121">Beklenen sütun türleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="305ab-121">Working with expected column types</span></span>

<span data-ttu-id="305ab-122">ML.NET ' deki makine öğrenimi algoritmaları, girdi olarak bilinen boyutun kayan bir vektörünü bekler.</span><span class="sxs-lookup"><span data-stu-id="305ab-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="305ab-123">Tüm veriler zaten sayısal biçimde olduğunda ve birlikte işlenmek üzere tasarlanıyorsa (örn. resim piksel), [özniteliğiverimodelinizeuygulayın.`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute)</span><span class="sxs-lookup"><span data-stu-id="305ab-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span> 

<span data-ttu-id="305ab-124">Veriler tümüyle sayısal değilse ve her sütuna ayrı ayrı veri dönüştürmeleri uygulamak istiyorsanız, tüm sütunları tek bir özellik vektöründe birleştirmek için [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) tüm sütunlar işlendikten sonra yöntemi kullanın. Yeni bir sütuna çıktı.</span><span class="sxs-lookup"><span data-stu-id="305ab-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span> 

<span data-ttu-id="305ab-125">Aşağıdaki kod parçacığı, ve `Size` `HistoricalPrices` sütunlarını, adlı `Features`yeni bir sütuna çıktı olan tek bir özellik vektörü halinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="305ab-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="305ab-126">Ölçeklerde bir farklılık olduğundan, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) verileri normalleştirmek için `Features` sütuna uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="305ab-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

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

### <a name="working-with-default-column-names"></a><span data-ttu-id="305ab-127">Varsayılan sütun adlarıyla çalışma</span><span class="sxs-lookup"><span data-stu-id="305ab-127">Working with default column names</span></span>

<span data-ttu-id="305ab-128">ML.NET algoritmaları, hiçbiri belirtilmediğinde varsayılan sütun adlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="305ab-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="305ab-129">Tüm traers, algoritmanın girdileri için çağrılan `featureColumnName` bir parametreye sahiptir ve geçerli olduğunda, beklenen `labelColumnName`değer için bir parametre de vardır.</span><span class="sxs-lookup"><span data-stu-id="305ab-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="305ab-130">Varsayılan olarak bu değerler `Features` ve `Label` sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="305ab-130">By default those values are `Features` and `Label` respectively.</span></span> 

<span data-ttu-id="305ab-131">Adlı [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) `IDataView`yeni bir sütun oluşturmak için ön işleme sırasında yöntemini kullanarak, önceden işlenmiş durumda olduğundan, algoritmanın parametrelerinde özellik sütunu adını belirtmeniz gerekmez. `Features`</span><span class="sxs-lookup"><span data-stu-id="305ab-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="305ab-132">Etiket sütunu, ancak `CurrentPrice` [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) öznitelik veri modelinde kullanıldığı `CurrentPrice` `Label` için ml.net, Machine Learning algoritmasına parametresağlamagereksiniminikaldıransütunuyenidenadlandırır.`labelColumnName` Tahmin Aracı.</span><span class="sxs-lookup"><span data-stu-id="305ab-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span> 

<span data-ttu-id="305ab-133">Varsayılan sütun adlarını kullanmak istemiyorsanız, sonraki kod parçacığında gösterildiği gibi Machine Learning algoritması tahmin Aracı ' ı tanımlarken, özelliğin adlarını ve etiket sütunlarını parametre olarak etiketleyin:</span><span class="sxs-lookup"><span data-stu-id="305ab-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="305ab-134">Makine öğrenimi modelini eğitme</span><span class="sxs-lookup"><span data-stu-id="305ab-134">Train the machine learning model</span></span>

<span data-ttu-id="305ab-135">Veriler önceden işlendikten sonra, makine öğrenimi modelini [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) gerileme algoritmayla eğitme yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="305ab-135">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="305ab-136">Model parametrelerini Ayıkla</span><span class="sxs-lookup"><span data-stu-id="305ab-136">Extract model parameters</span></span>

<span data-ttu-id="305ab-137">Model eğitilirken İnceleme veya yeniden eğitim için öğrenilen [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) ' ı ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="305ab-137">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or re-training.</span></span> <span data-ttu-id="305ab-138">Eğitilen modelin sapve öğrenilen katsayılarını veya ağırlıklarını [sağlar.`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters)</span><span class="sxs-lookup"><span data-stu-id="305ab-138">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span> 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="305ab-139">Diğer modellerin görevlerine özgü parametreleri vardır.</span><span class="sxs-lookup"><span data-stu-id="305ab-139">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="305ab-140">Örneğin, [K-anlamı algoritması](xref:Microsoft.ML.Trainers.KMeansTrainer) , verileri centroıd 'ler temelinde kümeye koyar ve [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) Bu öğrenilen centroıd 'leri depolayan bir özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="305ab-140">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="305ab-141">Daha fazla bilgi edinmek için [ `Microsoft.ML.Trainers` API belgelerini](xref:Microsoft.ML.Trainers) ziyaret edin ve adlarını içeren `ModelParameters` sınıfları arayın.</span><span class="sxs-lookup"><span data-stu-id="305ab-141">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span> 

## <a name="evaluate-model-quality"></a><span data-ttu-id="305ab-142">Model kalitesini değerlendir</span><span class="sxs-lookup"><span data-stu-id="305ab-142">Evaluate model quality</span></span>

<span data-ttu-id="305ab-143">En iyi performans sağlayan modeli seçmenize yardımcı olmak için test verilerinde performansını değerlendirmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="305ab-143">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="305ab-144">Eğitilen modele yönelik çeşitli ölçümleri ölçmek için [yönteminikullanın.`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*)</span><span class="sxs-lookup"><span data-stu-id="305ab-144">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="305ab-145">Yöntemi `Evaluate` , hangi makine öğrenimi görevinin gerçekleştirildiğine bağlı olarak farklı ölçümler üretir.</span><span class="sxs-lookup"><span data-stu-id="305ab-145">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="305ab-146">Daha fazla ayrıntı için [ `Microsoft.ML.Data` API belgelerini](xref:Microsoft.ML.Data) ziyaret edin ve adlarını içeren `Metrics` sınıfları arayın.</span><span class="sxs-lookup"><span data-stu-id="305ab-146">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span> 

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

<span data-ttu-id="305ab-147">Önceki kod örneğinde:</span><span class="sxs-lookup"><span data-stu-id="305ab-147">In the previous code sample:</span></span>  

1. <span data-ttu-id="305ab-148">Test veri kümesi önceden tanımlanmış veri hazırlama dönüştürmeleri kullanılarak önceden işlenir.</span><span class="sxs-lookup"><span data-stu-id="305ab-148">Test data set is pre-processed using the data preparation transforms previously defined.</span></span> 
2. <span data-ttu-id="305ab-149">Eğitilen makine öğrenimi modeli, test verilerinde tahminleri yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="305ab-149">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="305ab-150">Yönteminde, test veri `CurrentPrice` `Score` kümesi sütunundaki değerler, regresyon modeli için ölçümleri hesaplamak üzere yeni çıkış tahminlerinin sütunuyla karşılaştırılır, bunlardan biri R-kare `Evaluate` `rSquared` değişken.</span><span class="sxs-lookup"><span data-stu-id="305ab-150">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="305ab-151">Bu küçük örnekte, R-kare, verilerin sınırlı büyüklüğü nedeniyle 0-1 aralığında olmayan bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="305ab-151">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="305ab-152">Gerçek dünyada bir senaryoda, 0 ile 1 arasında bir değer görmeniz beklenir.</span><span class="sxs-lookup"><span data-stu-id="305ab-152">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
