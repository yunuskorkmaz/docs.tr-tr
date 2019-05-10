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
# <a name="save-and-load-trained-models"></a>Kaydet ve eğitilen modeller yüklenemiyor

Kaydetme ve uygulamanızı eğitilen modeller yükleme hakkında bilgi edinin. 

Modeli oluşturma işlemi boyunca bir model bellekte yer alan ve uygulama yaşam döngüsü boyunca erişilebilir. Model bir yerde yerel olarak veya uzaktan kaydedilmezse uygulama çalışıyorsa, durduktan sonra ancak artık erişilebilir değildir. Genellikle modelleri için çıkarım ya da diğer uygulamalarda eğitim ya da yeniden eğitim sonra belirli bir noktada kullanılır. Bu nedenle, model depolamak önemlidir. Kaydet ve veri hazırlama ve model eğitim işlem hatlarını aşağıda ayrıntılı bir gibi kullanırken bu belgenin sonraki bölümlerinde açıklanan adımları kullanarak modeller yüklenemiyor. Bu örnek bir doğrusal regresyon modeli kullansa da, diğer ML.NET algoritmalar için aynı işlem geçerlidir.

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

Çoğu modelleri ve veri hazırlık işlem hatları devralınacak çünkü aynı sınıflar, kayıt kümesi ve yöntem imzaları bu bileşenler için aynı yükleme. Kullanım Örneğinize bağlı olarak, ya da model ve veri hazırlık işlem hattı tek bir birleştirebilirsiniz [ `EstimatorChain` ](xref:Microsoft.ML.Data.TransformerChain%601) tek bir çıktı hangi [ `ITransformer` ](xref:Microsoft.ML.ITransformer) veya bunları eklenerek ayrı bir ayrı [ `ITransformer` ](xref:Microsoft.ML.ITransformer) her. 

## <a name="save-a-model-locally"></a>Modeli yerel olarak Kaydet

Bir modeli kaydederken iki şey gerekir:

1. [ `ITransformer` ](xref:Microsoft.ML.ITransformer) Modeli.
2. [ `DataViewSchema` ](xref:Microsoft.ML.DataViewSchema) , [ `ITransformer` ](xref:Microsoft.ML.ITransformer)Girişi beklenen.

Modeli eğitmek sonra kullanın [ `Save` ](xref:Microsoft.ML.ModelOperationsCatalog.Save*) eğitilen model bir dosyaya kaydetmek için yöntem `model.zip` kullanarak `DataViewSchema` giriş verisi. 

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>Yerel olarak depolanan bir modeli yüklenemiyor

Modeli yerel olarak depolanan diğer işlemlerde kullanılabilir veya gibi uygulamalar `ASP.NET Core` ve `Serverless Web Applications`. Bkz: [kullanım ML.NET Web API'sindeki](./serve-model-web-api-ml-net.md) ve [ML.NET sunucusuz Web uygulaması dağıtma](./serve-model-serverless-azure-functions-ml-net.md) daha fazla bilgi için nasıl yapılır makaleleri. 

Ayrı bir uygulama veya işlem [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) uygulamanıza eğitilen bir modelin alınacağı dosya yolu birlikte yöntemi.

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>Uzaktan depolanan bir modeli yüklenemiyor

Veri hazırlama işlem hatları ve uygulamanıza uzak bir konumda depolanan modelleri yüklemek için kullandığı bir [ `Stream` ](xref:System.IO.Stream) yerine bir dosya yolunda [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) yöntemi.

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
> Ayrı veri hazırlama ve model eğitim işlem hatlarını çalışmayı isteğe bağlıdır. İşlem hatları ayrımı öğrenilen model parametreleri incelemek kolaylaştırır. Tahminler elde etmek için kaydetme ve yükleme modeli eğitimi işlemleri ve veri hazırlama içeren tek bir işlem hattı daha kolay olur.

Ayrı veri hazırlama işlem hatları ve modelleri ile çalışırken, tek bir işlem hatları olarak aynı işlem geçerlidir; Her iki işlem hatları dışında şimdi kaydedilir ve aynı anda yüklenen gerekir.

Verilen ayrı veri hazırlama ve model eğitim işlem hatlarını:

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a>Veri hazırlama işlem hattı ve eğitilen Modeli Kaydet

Veri hazırlama işlem hattı ve eğitilen model kaydetmek için aşağıdaki komutları kullanın:

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>Veri hazırlama işlem hattı ve eğitilen model yükle 

Ayrı bir işlem veya uygulama, eğitilen modeli ve veri hazırlık işlem hattı aşağıdaki gibi aynı anda yükle:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
