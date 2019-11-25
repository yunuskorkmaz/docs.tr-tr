---
title: Eğitilen modelleri kaydetme ve yükleme
description: Eğitilen modelleri kaydetme ve yükleme hakkında bilgi edinin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3cebe979b5c279ce8cb90db5510f8758c24c2b4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977004"
---
# <a name="save-and-load-trained-models"></a><span data-ttu-id="22fee-103">Eğitilen modelleri kaydetme ve yükleme</span><span class="sxs-lookup"><span data-stu-id="22fee-103">Save and load trained models</span></span>

<span data-ttu-id="22fee-104">Uygulamanıza eğitilen modelleri kaydetmeyi ve yüklemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="22fee-104">Learn how to save and load trained models in your application.</span></span>

<span data-ttu-id="22fee-105">Model oluşturma işlemi boyunca, bir model bellekte bulunur ve uygulamanın yaşam döngüsü boyunca erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="22fee-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="22fee-106">Ancak, uygulama çalışmayı durdurduktan sonra, model yerel olarak veya uzaktan kaydedilmezse artık erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="22fee-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="22fee-107">Genellikle modeller, diğer uygulamalarda eğitim sonrasında, çıkarım veya yeniden eğitim için bir noktada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22fee-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="22fee-108">Bu nedenle, modelin depolanması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="22fee-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="22fee-109">Veri hazırlama ve model eğitimi işlem hatlarını kullanırken aşağıda açıklandığı gibi, bu belgenin sonraki bölümlerinde açıklanan adımları kullanarak modelleri kaydedin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="22fee-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="22fee-110">Bu örnek bir doğrusal regresyon modeli kullansa da, aynı işlem diğer ML.NET algoritmaları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="22fee-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f, 125000f, 122000f },
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
    }
};

// Create MLContext
MLContext mlContext = new MLContext();

// Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Define data preparation estimator
EstimatorChain<RegressionPredictionTransformer<LinearRegressionModelParameters>> pipelineEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .Append(mlContext.Regression.Trainers.Sdca());

// Train model
ITransformer trainedModel = pipelineEstimator.Fit(data);

// Save model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

<span data-ttu-id="22fee-111">Çoğu model ve veri hazırlama işlem hattı aynı sınıf kümesinden devraldığı için, bu bileşenlere yönelik Save ve Load Yöntem imzaları aynıdır.</span><span class="sxs-lookup"><span data-stu-id="22fee-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="22fee-112">Kullanım durumunuza bağlı olarak, veri hazırlama işlem hattını ve modelini tek bir [`ITransformer`](xref:Microsoft.ML.ITransformer) çıkarmak veya ayrı bir [`ITransformer`](xref:Microsoft.ML.ITransformer) oluşturmak için ayrı bir [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22fee-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span>

## <a name="save-a-model-locally"></a><span data-ttu-id="22fee-113">Modeli yerel olarak kaydetme</span><span class="sxs-lookup"><span data-stu-id="22fee-113">Save a model locally</span></span>

<span data-ttu-id="22fee-114">Bir modeli kaydederken iki şey olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="22fee-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="22fee-115">Modelin [`ITransformer`](xref:Microsoft.ML.ITransformer) .</span><span class="sxs-lookup"><span data-stu-id="22fee-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="22fee-116">[`ITransformer`](xref:Microsoft.ML.ITransformer)beklenen girdinin [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) .</span><span class="sxs-lookup"><span data-stu-id="22fee-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="22fee-117">Modeli eğitdikten sonra, eğitim modelini giriş verilerinin `DataViewSchema` kullanarak `model.zip` adlı bir dosyaya kaydetmek için [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="22fee-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span>

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="22fee-118">Yerel olarak depolanan bir modeli yükleme</span><span class="sxs-lookup"><span data-stu-id="22fee-118">Load a model stored locally</span></span>

<span data-ttu-id="22fee-119">Yerel olarak depolanan modeller, `ASP.NET Core` ve `Serverless Web Applications`gibi diğer işlemlerde veya uygulamalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="22fee-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="22fee-120">Daha fazla bilgi edinmek için bkz. [Web API 'de ml.NET kullanma](./serve-model-web-api-ml-net.md) ve [ml.net sunucusuz Web uygulaması](./serve-model-serverless-azure-functions-ml-net.md) nasıl yapılır makaleleri dağıtma.</span><span class="sxs-lookup"><span data-stu-id="22fee-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span>

<span data-ttu-id="22fee-121">Ayrı bir uygulama veya işlemde, eğitilen modeli uygulamanıza almak için [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) yöntemini dosya yoluyla birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="22fee-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="22fee-122">Uzaktan depolanan bir modeli yükleme</span><span class="sxs-lookup"><span data-stu-id="22fee-122">Load a model stored remotely</span></span>

<span data-ttu-id="22fee-123">Uygulamanıza uzak bir konumda depolanan veri hazırlama işlem hatlarını ve modellerini yüklemek için [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) yönteminde dosya yolu yerine bir [`Stream`](xref:System.IO.Stream) kullanın.</span><span class="sxs-lookup"><span data-stu-id="22fee-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema and ITransformers
DataViewSchema modelSchema;
ITransformer trainedModel;

// Load data prep pipeline and trained model
using (HttpClient client = new HttpClient())
{
    Stream modelFile = await client.GetStreamAsync("<YOUR-REMOTE-FILE-LOCATION>");

    trainedModel = mlContext.Model.Load(modelFile, out modelSchema);
}
```

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="22fee-124">Ayrı veri hazırlama ve model işlem hatları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="22fee-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="22fee-125">Ayrı veri hazırlama ve model eğitimi işlem hatları ile çalışma isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22fee-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="22fee-126">İşlem hatları ayrımı, öğrenilen model parametrelerini incelemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="22fee-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="22fee-127">Tahmin için, veri hazırlama ve model eğitimi işlemlerini içeren tek bir işlem hattını kaydetmek ve yüklemek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="22fee-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="22fee-128">Ayrı veri hazırlama işlem hatları ve modelleriyle çalışırken, tek işlem hatları ile aynı işlem geçerlidir; Artık her iki işlem hattı da aynı anda kaydedilip yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="22fee-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="22fee-129">Verilen ayrı veri hazırlama ve model eğitimi işlem hatları:</span><span class="sxs-lookup"><span data-stu-id="22fee-129">Given separate data preparation and model training pipelines:</span></span>

```csharp
// Define data preparation estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data preparation transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Pre-process data using data prep operations
IDataView transformedData = dataPrepTransformer.Transform(data);

// Train regression model
RegressionPredictionTransformer<LinearRegressionModelParameters> trainedModel = sdcaEstimator.Fit(transformedData);
```

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="22fee-130">Veri hazırlama işlem hattını ve eğitilen modeli kaydetme</span><span class="sxs-lookup"><span data-stu-id="22fee-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="22fee-131">Hem veri hazırlama işlem hattı hem de eğitilen modeli kaydetmek için aşağıdaki komutları kullanın:</span><span class="sxs-lookup"><span data-stu-id="22fee-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="22fee-132">Veri hazırlama işlem hattı ve eğitilen model yükleme</span><span class="sxs-lookup"><span data-stu-id="22fee-132">Load data preparation pipeline and trained model</span></span>

<span data-ttu-id="22fee-133">Ayrı bir süreç veya uygulamada, veri hazırlama işlem hattını ve eğitilen modeli şu anda aşağıdaki gibi yükleyin:</span><span class="sxs-lookup"><span data-stu-id="22fee-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
