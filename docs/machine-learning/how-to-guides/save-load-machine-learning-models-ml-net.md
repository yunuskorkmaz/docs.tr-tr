---
title: Eğitimli modelleri kaydetme ve yükleme
description: Eğitimli modelleri nasıl kaydedin ve yükleyin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3cebe979b5c279ce8cb90db5510f8758c24c2b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977004"
---
# <a name="save-and-load-trained-models"></a><span data-ttu-id="e8679-103">Eğitimli modelleri kaydetme ve yükleme</span><span class="sxs-lookup"><span data-stu-id="e8679-103">Save and load trained models</span></span>

<span data-ttu-id="e8679-104">Uygulamanızda eğitimli modelleri nasıl kaydedin ve yükleyin öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e8679-104">Learn how to save and load trained models in your application.</span></span>

<span data-ttu-id="e8679-105">Model oluşturma işlemi boyunca, bir model bellekte yaşar ve uygulamanın yaşam döngüsü boyunca erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e8679-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="e8679-106">Ancak, uygulama çalışmayı durdurduktan sonra, model yerel veya uzaktan bir yere kaydedilmezse, artık erişilemez.</span><span class="sxs-lookup"><span data-stu-id="e8679-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="e8679-107">Genellikle modeller çıkarım veya yeniden eğitim için diğer uygulamalarda eğitimden sonra bir noktada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8679-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="e8679-108">Bu nedenle, modeli depolamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e8679-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="e8679-109">Aşağıda ayrıntılı olarak açıklanan veri hazırlama ve model eğitim boru hatlarını kullanırken bu belgenin sonraki bölümlerinde açıklanan adımları kullanarak modelleri kaydedin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e8679-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="e8679-110">Bu örnek doğrusal bir regresyon modeli kullansa da, aynı işlem diğer ML.NET algoritmaları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e8679-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

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

<span data-ttu-id="e8679-111">Çoğu model ve veri hazırlama ardışık lığı aynı sınıf kümesinden devraldığından, bu bileşenler için kaydetme ve yükleme yöntemi imzaları aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e8679-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="e8679-112">Kullanım durumunuza bağlı olarak, veri hazırlama ardışık lığını ve [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) modelini [`ITransformer`](xref:Microsoft.ML.ITransformer) tek bir çıktı da [`ITransformer`](xref:Microsoft.ML.ITransformer) elde edecek veya bunları birbirinden ayıran tek bir şekilde birleştirerek her biri için ayrı bir ayrı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8679-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span>

## <a name="save-a-model-locally"></a><span data-ttu-id="e8679-113">Bir modeli yerel olarak kaydetme</span><span class="sxs-lookup"><span data-stu-id="e8679-113">Save a model locally</span></span>

<span data-ttu-id="e8679-114">Bir modeli kaydederken iki şeye ihtiyacınız var:</span><span class="sxs-lookup"><span data-stu-id="e8679-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="e8679-115">Modelin. [`ITransformer`](xref:Microsoft.ML.ITransformer)</span><span class="sxs-lookup"><span data-stu-id="e8679-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="e8679-116">[`ITransformer`](xref:Microsoft.ML.ITransformer)'beklenen [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) giriş.</span><span class="sxs-lookup"><span data-stu-id="e8679-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="e8679-117">Modeli eğittikten sonra, eğitilen [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) modeli giriş `model.zip` verilerini `DataViewSchema` kullanarak adlandırılan bir dosyaya kaydetmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8679-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span>

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="e8679-118">Yerel olarak depolanan bir modeli yükleme</span><span class="sxs-lookup"><span data-stu-id="e8679-118">Load a model stored locally</span></span>

<span data-ttu-id="e8679-119">Yerel olarak depolanan modeller, diğer işlemlerde `ASP.NET Core` veya `Serverless Web Applications`uygulamalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8679-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="e8679-120">Bkz. [Web API'sında ML.NET kullanın](./serve-model-web-api-ml-net.md) ve daha fazla bilgi edinmek için sunucusuz web uygulaması ML.NET nasıl kullanılır makalelerini [dağıtın.](./serve-model-serverless-azure-functions-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="e8679-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span>

<span data-ttu-id="e8679-121">Ayrı bir uygulama veya işlemde, eğitilmiş modeli uygulamanıza sokmak için dosya yolu ile birlikte [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8679-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="e8679-122">Uzaktan depolanan bir modeli yükleme</span><span class="sxs-lookup"><span data-stu-id="e8679-122">Load a model stored remotely</span></span>

<span data-ttu-id="e8679-123">Uzak bir konumda depolanan veri hazırlama ardışık lıklarını ve [`Stream`](xref:System.IO.Stream) modelleri uygulamanıza yüklemek [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) için yöntemde dosya yolu yerine bir dosya yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8679-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="e8679-124">Ayrı veri hazırlama ve model boru hatları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="e8679-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="e8679-125">Ayrı veri hazırlama ve model eğitim boru hatları ile çalışma isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e8679-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="e8679-126">Boru hatlarının ayrılması, öğrenilen model parametrelerinin incelenmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e8679-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="e8679-127">Öngörüler için, veri hazırlama ve model eğitim işlemlerini içeren tek bir ardışık işlemi kaydetmek ve yüklemek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="e8679-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="e8679-128">Ayrı veri hazırlama boru hatları ve modelleri ile çalışırken, tek boru hatları ile aynı süreç geçerlidir; şimdi her iki boru hattı nın da aynı anda kaydedilmesi ve yüklenmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="e8679-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="e8679-129">Ayrı veri hazırlama ve model eğitim boru hatları verilir:</span><span class="sxs-lookup"><span data-stu-id="e8679-129">Given separate data preparation and model training pipelines:</span></span>

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="e8679-130">Veri hazırlama boru hattını ve eğitimli modeli kaydetme</span><span class="sxs-lookup"><span data-stu-id="e8679-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="e8679-131">Hem veri hazırlama ardışıklığını hem de eğitilmiş modeli kaydetmek için aşağıdaki komutları kullanın:</span><span class="sxs-lookup"><span data-stu-id="e8679-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="e8679-132">Yük veri hazırlama boru hattı ve eğitimli model</span><span class="sxs-lookup"><span data-stu-id="e8679-132">Load data preparation pipeline and trained model</span></span>

<span data-ttu-id="e8679-133">Ayrı bir işlem veya uygulamada, veri hazırlama ardışık hattını ve eğitilmiş modeli aynı anda aşağıdaki gibi yükleyin:</span><span class="sxs-lookup"><span data-stu-id="e8679-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
