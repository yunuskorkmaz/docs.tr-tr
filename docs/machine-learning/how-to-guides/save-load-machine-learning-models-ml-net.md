---
title: Kaydet ve eğitilen modeller yüklenemiyor
description: Kaydet ve eğitilen modelleri yükleme hakkında bilgi edinin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3d4a51ceaf707d30c5072b91d7baf7fe02ef433
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066171"
---
# <a name="save-and-load-trained-models"></a><span data-ttu-id="540c4-103">Kaydet ve eğitilen modeller yüklenemiyor</span><span class="sxs-lookup"><span data-stu-id="540c4-103">Save and load trained models</span></span>

<span data-ttu-id="540c4-104">Kaydetme ve uygulamanızı eğitilen modeller yükleme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="540c4-104">Learn how to save and load trained models in your application.</span></span> 

<span data-ttu-id="540c4-105">Modeli oluşturma işlemi boyunca bir model bellekte yer alan ve uygulama yaşam döngüsü boyunca erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="540c4-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="540c4-106">Model bir yerde yerel olarak veya uzaktan kaydedilmezse uygulama çalışıyorsa, durduktan sonra ancak artık erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="540c4-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="540c4-107">Genellikle modelleri için çıkarım ya da diğer uygulamalarda eğitim ya da yeniden eğitim sonra belirli bir noktada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="540c4-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="540c4-108">Bu nedenle, model depolamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="540c4-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="540c4-109">Kaydet ve veri hazırlama ve model eğitim işlem hatlarını aşağıda ayrıntılı bir gibi kullanırken bu belgenin sonraki bölümlerinde açıklanan adımları kullanarak modeller yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="540c4-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="540c4-110">Bu örnek bir doğrusal regresyon modeli kullansa da, diğer ML.NET algoritmalar için aynı işlem geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="540c4-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

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

<span data-ttu-id="540c4-111">Çoğu modelleri ve veri hazırlık işlem hatları devralınacak çünkü aynı sınıflar, kayıt kümesi ve yöntem imzaları bu bileşenler için aynı yükleme.</span><span class="sxs-lookup"><span data-stu-id="540c4-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="540c4-112">Kullanım Örneğinize bağlı olarak, ya da model ve veri hazırlık işlem hattı tek bir birleştirebilirsiniz [ `EstimatorChain` ](xref:Microsoft.ML.Data.TransformerChain%601) tek bir çıktı hangi [ `ITransformer` ](xref:Microsoft.ML.ITransformer) veya bunları eklenerek ayrı bir ayrı [ `ITransformer` ](xref:Microsoft.ML.ITransformer) her.</span><span class="sxs-lookup"><span data-stu-id="540c4-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span> 

## <a name="save-a-model-locally"></a><span data-ttu-id="540c4-113">Modeli yerel olarak Kaydet</span><span class="sxs-lookup"><span data-stu-id="540c4-113">Save a model locally</span></span>

<span data-ttu-id="540c4-114">Bir modeli kaydederken iki şey gerekir:</span><span class="sxs-lookup"><span data-stu-id="540c4-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="540c4-115">[ `ITransformer` ](xref:Microsoft.ML.ITransformer) Modeli.</span><span class="sxs-lookup"><span data-stu-id="540c4-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="540c4-116">[ `DataViewSchema` ](xref:Microsoft.ML.DataViewSchema) , [ `ITransformer` ](xref:Microsoft.ML.ITransformer)Girişi beklenen.</span><span class="sxs-lookup"><span data-stu-id="540c4-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="540c4-117">Modeli eğitmek sonra kullanın [ `Save` ](xref:Microsoft.ML.ModelOperationsCatalog.Save*) eğitilen model bir dosyaya kaydetmek için yöntem `model.zip` kullanarak `DataViewSchema` giriş verisi.</span><span class="sxs-lookup"><span data-stu-id="540c4-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span> 

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="540c4-118">Yerel olarak depolanan bir modeli yüklenemiyor</span><span class="sxs-lookup"><span data-stu-id="540c4-118">Load a model stored locally</span></span>

<span data-ttu-id="540c4-119">Modeli yerel olarak depolanan diğer işlemlerde kullanılabilir veya gibi uygulamalar `ASP.NET Core` ve `Serverless Web Applications`.</span><span class="sxs-lookup"><span data-stu-id="540c4-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="540c4-120">Bkz: [kullanım ML.NET Web API'sindeki](./serve-model-web-api-ml-net.md) ve [ML.NET sunucusuz Web uygulaması dağıtma](./serve-model-serverless-azure-functions-ml-net.md) daha fazla bilgi için nasıl yapılır makaleleri.</span><span class="sxs-lookup"><span data-stu-id="540c4-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span> 

<span data-ttu-id="540c4-121">Ayrı bir uygulama veya işlem [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) uygulamanıza eğitilen bir modelin alınacağı dosya yolu birlikte yöntemi.</span><span class="sxs-lookup"><span data-stu-id="540c4-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="540c4-122">Uzaktan depolanan bir modeli yüklenemiyor</span><span class="sxs-lookup"><span data-stu-id="540c4-122">Load a model stored remotely</span></span>

<span data-ttu-id="540c4-123">Veri hazırlama işlem hatları ve uygulamanıza uzak bir konumda depolanan modelleri yüklemek için kullandığı bir [ `Stream` ](xref:System.IO.Stream) yerine bir dosya yolunda [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="540c4-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="540c4-124">Ayrı veri hazırlama ve model işlem hatları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="540c4-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="540c4-125">Ayrı veri hazırlama ve model eğitim işlem hatlarını çalışmayı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="540c4-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="540c4-126">İşlem hatları ayrımı öğrenilen model parametreleri incelemek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="540c4-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="540c4-127">Tahminler elde etmek için kaydetme ve yükleme modeli eğitimi işlemleri ve veri hazırlama içeren tek bir işlem hattı daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="540c4-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="540c4-128">Ayrı veri hazırlama işlem hatları ve modelleri ile çalışırken, tek bir işlem hatları olarak aynı işlem geçerlidir; Her iki işlem hatları dışında şimdi kaydedilir ve aynı anda yüklenen gerekir.</span><span class="sxs-lookup"><span data-stu-id="540c4-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="540c4-129">Verilen ayrı veri hazırlama ve model eğitim işlem hatlarını:</span><span class="sxs-lookup"><span data-stu-id="540c4-129">Given separate data preparation and model training pipelines:</span></span>

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="540c4-130">Veri hazırlama işlem hattı ve eğitilen Modeli Kaydet</span><span class="sxs-lookup"><span data-stu-id="540c4-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="540c4-131">Veri hazırlama işlem hattı ve eğitilen model kaydetmek için aşağıdaki komutları kullanın:</span><span class="sxs-lookup"><span data-stu-id="540c4-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="540c4-132">Veri hazırlama işlem hattı ve eğitilen model yükle</span><span class="sxs-lookup"><span data-stu-id="540c4-132">Load data preparation pipeline and trained model</span></span> 

<span data-ttu-id="540c4-133">Ayrı bir işlem veya uygulama, eğitilen modeli ve veri hazırlık işlem hattı aşağıdaki gibi aynı anda yükle:</span><span class="sxs-lookup"><span data-stu-id="540c4-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
