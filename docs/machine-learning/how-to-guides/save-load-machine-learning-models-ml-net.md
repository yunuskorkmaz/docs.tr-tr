---
title: Eğitilen modelleri kaydetme ve yükleme
description: Eğitilen modelleri kaydetme ve yükleme hakkında bilgi edinin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 681a35956a8959e2f1cbb5a7023e0ef29b67097e
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679540"
---
# <a name="save-and-load-trained-models"></a>Eğitilen modelleri kaydetme ve yükleme

Uygulamanıza eğitilen modelleri kaydetmeyi ve yüklemeyi öğrenin.

Model oluşturma işlemi boyunca, bir model bellekte bulunur ve uygulamanın yaşam döngüsü boyunca erişilebilir. Ancak, uygulama çalışmayı durdurduktan sonra, model yerel olarak veya uzaktan kaydedilmezse artık erişilebilir değildir. Genellikle modeller, diğer uygulamalarda eğitim sonrasında, çıkarım veya yeniden eğitim için bir noktada kullanılır. Bu nedenle, modelin depolanması önemlidir. Veri hazırlama ve model eğitimi işlem hatlarını kullanırken aşağıda açıklandığı gibi, bu belgenin sonraki bölümlerinde açıklanan adımları kullanarak modelleri kaydedin ve yükleyin. Bu örnek bir doğrusal regresyon modeli kullansa da, aynı işlem diğer ML.NET algoritmaları için de geçerlidir.

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

Çoğu model ve veri hazırlama işlem hattı aynı sınıf kümesinden devraldığı için, bu bileşenlere yönelik Save ve Load Yöntem imzaları aynıdır. Kullanım durumunuza bağlı olarak, veri hazırlama işlem hattını ve modelini tek [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) tek veya ayrı bir şekilde bir araya getirerek [`ITransformer`](xref:Microsoft.ML.ITransformer) her biri için ayrı bir oluşturalım [`ITransformer`](xref:Microsoft.ML.ITransformer) .

## <a name="save-a-model-locally"></a>Modeli yerel olarak kaydetme

Bir modeli kaydederken iki şey olması gerekir:

1. [`ITransformer`](xref:Microsoft.ML.ITransformer)Model.
2. [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) [`ITransformer`](xref:Microsoft.ML.ITransformer) Beklenen girişin.

Modeli eğitdikten sonra, [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save%2A) eğitilen modeli `model.zip` giriş verilerinin kullanılarak adlandırılan bir dosyaya kaydetmek için yöntemini kullanın `DataViewSchema` .

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>Yerel olarak depolanan bir modeli yükleme

Yerel olarak depolanan modeller, ve gibi diğer işlemlerde veya uygulamalarda kullanılabilir `ASP.NET Core` `Serverless Web Applications` . Daha fazla bilgi edinmek için bkz. [Web API 'de ml.NET kullanma](./serve-model-web-api-ml-net.md) ve [ml.net sunucusuz Web uygulaması](./serve-model-serverless-azure-functions-ml-net.md) nasıl yapılır makaleleri dağıtma.

Ayrı bir uygulama veya işlemde, [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load%2A) eğitilen modeli uygulamanıza almak için yöntemi dosya yoluyla birlikte kullanın.

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>Uzaktan depolanan bir modeli yükleme

Uygulamanıza uzak bir konumda depolanan veri hazırlama işlem hatlarını ve modellerini yüklemek için, [`Stream`](xref:System.IO.Stream) yöntemde dosya yolu yerine bir kullanın [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load%2A) .

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a>Ayrı veri hazırlama ve model işlem hatları ile çalışma

> [!NOTE]
> Ayrı veri hazırlama ve model eğitimi işlem hatları ile çalışma isteğe bağlıdır. İşlem hatları ayrımı, öğrenilen model parametrelerini incelemeyi kolaylaştırır. Tahmin için, veri hazırlama ve model eğitimi işlemlerini içeren tek bir işlem hattını kaydetmek ve yüklemek daha kolay.

Ayrı veri hazırlama işlem hatları ve modelleriyle çalışırken, tek işlem hatları ile aynı işlem geçerlidir; Artık her iki işlem hattı da aynı anda kaydedilip yüklenmelidir.

Verilen ayrı veri hazırlama ve model eğitimi işlem hatları:

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a>Veri hazırlama işlem hattını ve eğitilen modeli kaydetme

Hem veri hazırlama işlem hattı hem de eğitilen modeli kaydetmek için aşağıdaki komutları kullanın:

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>Veri hazırlama işlem hattı ve eğitilen model yükleme

Ayrı bir süreç veya uygulamada, veri hazırlama işlem hattını ve eğitilen modeli şu anda aşağıdaki gibi yükleyin:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
