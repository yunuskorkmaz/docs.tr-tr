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
# <a name="save-and-load-trained-models"></a>Eğitimli modelleri kaydetme ve yükleme

Uygulamanızda eğitimli modelleri nasıl kaydedin ve yükleyin öğrenin.

Model oluşturma işlemi boyunca, bir model bellekte yaşar ve uygulamanın yaşam döngüsü boyunca erişilebilir. Ancak, uygulama çalışmayı durdurduktan sonra, model yerel veya uzaktan bir yere kaydedilmezse, artık erişilemez. Genellikle modeller çıkarım veya yeniden eğitim için diğer uygulamalarda eğitimden sonra bir noktada kullanılır. Bu nedenle, modeli depolamak önemlidir. Aşağıda ayrıntılı olarak açıklanan veri hazırlama ve model eğitim boru hatlarını kullanırken bu belgenin sonraki bölümlerinde açıklanan adımları kullanarak modelleri kaydedin ve yükleyin. Bu örnek doğrusal bir regresyon modeli kullansa da, aynı işlem diğer ML.NET algoritmaları için de geçerlidir.

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

Çoğu model ve veri hazırlama ardışık lığı aynı sınıf kümesinden devraldığından, bu bileşenler için kaydetme ve yükleme yöntemi imzaları aynıdır. Kullanım durumunuza bağlı olarak, veri hazırlama ardışık lığını ve [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) modelini [`ITransformer`](xref:Microsoft.ML.ITransformer) tek bir çıktı da [`ITransformer`](xref:Microsoft.ML.ITransformer) elde edecek veya bunları birbirinden ayıran tek bir şekilde birleştirerek her biri için ayrı bir ayrı oluşturabilirsiniz.

## <a name="save-a-model-locally"></a>Bir modeli yerel olarak kaydetme

Bir modeli kaydederken iki şeye ihtiyacınız var:

1. Modelin. [`ITransformer`](xref:Microsoft.ML.ITransformer)
2. [`ITransformer`](xref:Microsoft.ML.ITransformer)'beklenen [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) giriş.

Modeli eğittikten sonra, eğitilen [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) modeli giriş `model.zip` verilerini `DataViewSchema` kullanarak adlandırılan bir dosyaya kaydetmek için yöntemi kullanın.

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>Yerel olarak depolanan bir modeli yükleme

Yerel olarak depolanan modeller, diğer işlemlerde `ASP.NET Core` veya `Serverless Web Applications`uygulamalarda kullanılabilir. Bkz. [Web API'sında ML.NET kullanın](./serve-model-web-api-ml-net.md) ve daha fazla bilgi edinmek için sunucusuz web uygulaması ML.NET nasıl kullanılır makalelerini [dağıtın.](./serve-model-serverless-azure-functions-ml-net.md)

Ayrı bir uygulama veya işlemde, eğitilmiş modeli uygulamanıza sokmak için dosya yolu ile birlikte [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) yöntemi kullanın.

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>Uzaktan depolanan bir modeli yükleme

Uzak bir konumda depolanan veri hazırlama ardışık lıklarını ve [`Stream`](xref:System.IO.Stream) modelleri uygulamanıza yüklemek [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) için yöntemde dosya yolu yerine bir dosya yolu kullanın.

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a>Ayrı veri hazırlama ve model boru hatları ile çalışma

> [!NOTE]
> Ayrı veri hazırlama ve model eğitim boru hatları ile çalışma isteğe bağlıdır. Boru hatlarının ayrılması, öğrenilen model parametrelerinin incelenmesini kolaylaştırır. Öngörüler için, veri hazırlama ve model eğitim işlemlerini içeren tek bir ardışık işlemi kaydetmek ve yüklemek daha kolaydır.

Ayrı veri hazırlama boru hatları ve modelleri ile çalışırken, tek boru hatları ile aynı süreç geçerlidir; şimdi her iki boru hattı nın da aynı anda kaydedilmesi ve yüklenmesi gerekiyor.

Ayrı veri hazırlama ve model eğitim boru hatları verilir:

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a>Veri hazırlama boru hattını ve eğitimli modeli kaydetme

Hem veri hazırlama ardışıklığını hem de eğitilmiş modeli kaydetmek için aşağıdaki komutları kullanın:

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>Yük veri hazırlama boru hattı ve eğitimli model

Ayrı bir işlem veya uygulamada, veri hazırlama ardışık hattını ve eğitilmiş modeli aynı anda aşağıdaki gibi yükleyin:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
