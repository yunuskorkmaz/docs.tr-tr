---
title: Modeli Azure İşlevleri’ne dağıtma
description: Azure Işlevleri 'ni kullanarak Internet üzerinden tahmin için ML.NET yaklaşım analizi makine öğrenimi modelini sunar
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 96b62017994da5b7b209c441b3e7fb760cad5201
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666677"
---
# <a name="deploy-a-model-to-azure-functions"></a>Modeli Azure İşlevleri’ne dağıtma

Azure Işlevleri sunucusuz bir ortam aracılığıyla HTTP üzerinden tahmin için önceden eğitilen ML.NET makine öğrenimi modelini dağıtmayı öğrenin.

> [!NOTE]
> `PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.

## <a name="prerequisites"></a>Önkoşullar

- ".NET Core platformlar arası geliştirme" iş yükü ve "Azure geliştirme" yüklü olan [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) .
- Microsoft. NET. SDK. Functions NuGet paketi sürüm 1.0.28 +.
- [Azure Işlevleri araçları](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- Önceden eğitilen model. Kendi modelinizi derlemek için [ML.NET yaklaşım Analizi öğreticisini](../tutorials/sentiment-analysis.md) kullanın veya bu [önceden eğitilen yaklaşım Analizi Machine Learning modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirin

## <a name="create-azure-functions-project"></a>Azure Işlevleri projesi oluştur

1. Visual Studio 2017'yi açın. Menü çubuğundan **Dosya** > **Yeni** > **Proje** ' yi seçin. **Yeni proje** iletişim kutusunda, **Visual C#**  düğümünü ve ardından **bulut** düğümünü seçin. Ardından **Azure işlevleri** proje şablonunu seçin. **Ad** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve **Tamam** düğmesini seçin.
1. **Yeni proje** iletişim kutusunda, proje seçeneklerinin üzerindeki açılan menüyü açın ve **Azure işlevleri v2 (.NET Core)** seçeneğini belirleyin. Ardından, **http tetikleyicisi** projesini seçin ve **Tamam** düğmesini seçin.
1. Modelinize kaydetmek için projenizde *Mlmodeller* adlı bir dizin oluşturun:

    **Çözüm Gezgini**, projenize sağ tıklayın ve**Yeni klasör** **Ekle** > ' yi seçin. "Mlmodeller" yazın ve ENTER tuşuna basın.

1. **Microsoft.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.

1. **Microsoft. Azure. Functions. Extensions NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft. Azure. Functions. Extensions**araması yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.

1. **Microsoft.Extensions.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.Extensions.ml**için arama yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.

1. **Microsoft. net. SDK. Functions NuGet paketini** 1.0.28 + sürümüne güncelleştirin:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, yüklü sekmesini seçin, **Microsoft. net. SDK. Functions**araması yapın, listeden bu paketi seçin, sürüm açılan menüsünde 1.0.28 veya üzeri ' i seçin ve **Güncelleştir** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.

## <a name="add-pre-trained-model-to-project"></a>Projeye önceden eğitilen Model Ekle

1. Önceden oluşturulmuş modelinizi *Mlmodeller* klasörüne kopyalayın.
1. Çözüm Gezgini, önceden oluşturulmuş model dosyanıza sağ tıklayıp **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

## <a name="create-azure-function-to-analyze-sentiment"></a>Yaklaşımı çözümlemek için Azure Işlevi oluşturma

Yaklaşımı tahmin etmek için bir sınıf oluşturun. Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.

1. **Yeni öğe Ekle** Iletişim kutusunda **Azure işlevi** ' ni seçin ve **ad** alanını *AnalyzeSentiment.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

1. **Yeni Azure işlevi** Iletişim kutusunda **http tetikleyicisi**' ni seçin. Ardından **Tamam** düğmesini seçin.

    *AnalyzeSentiment.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *AnalyzeSentiment.cs*öğesinin en üstüne ekleyin:

    ```csharp
    using System;
    using System.IO;
    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using Microsoft.AspNetCore.Http;
    using Microsoft.Extensions.Logging;
    using Newtonsoft.Json;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Varsayılan olarak, `AnalyzeSentiment` `static`sınıfı. `static` Anahtar sözcüğünü sınıf tanımından kaldırdığınızdan emin olun.

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a>Veri modelleri oluşturma

Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturmanız gerekir. Projenize yeni bir sınıf ekleyin:

1. Veri modellerinizi kaydetmek için projenizde *Datamodeller* adlı bir dizin oluşturun: Çözüm Gezgini, projenize sağ tıklayın ve **> yeni klasör ekle**' yi seçin. "Datamodeller" yazın ve ENTER tuşuna basın.
2. Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.
3. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin. 

    *SentimentData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki using ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentData.cs* dosyasına ekleyin:
    
    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.
5. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentPrediction.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin. *SentimentPrediction.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki using ifadesini *SentimentPrediction.cs*öğesinin en üstüne ekleyin:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentPrediction.cs* dosyasına ekleyin:

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction``SentimentData` ,`SentimentText` özelliğindeki özgün verilere ve model tarafından oluşturulan çıktıya erişim sağlayan öğesinden devralır.

## <a name="register-predictionenginepool-service"></a>PredictionEnginePool hizmetini Kaydet

Tek bir tahmin yapmak için kullanın [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). Uygulamanızda kullanabilmeniz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, gerektiğinde oluşturmanız gerekir. Bu durumda, dikkate alınması gereken en iyi yöntem bağımlılık ekleme yöntemidir.

Aşağıdaki bağlantı, [bağımlılık ekleme](https://en.wikipedia.org/wiki/Dependency_injection)hakkında bilgi edinmek istiyorsanız daha fazla bilgi sağlar.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *Startup.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin. 

    *Startup.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki using ifadesini *Startup.cs*öğesinin en üstüne ekleyin:

    ```csharp
    using Microsoft.Azure.Functions.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Using deyimlerinin altındaki mevcut kodu kaldırın ve *Startup.cs* dosyasına aşağıdaki kodu ekleyin:

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {
            public override void Configure(IFunctionsHostBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

Yüksek düzeyde bu kod, uygulama tarafından el ile yapmak yerine nesneleri ve hizmetleri otomatik olarak başlatır.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir. Gelişmiş performans ve iş parçacığı güvenliği için, uygulama `PredictionEnginePool` kullanımı için `PredictionEngine` bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) nesne oluşturan hizmetini kullanın. 

## <a name="load-the-model-into-the-function"></a>Modeli işleve yükleme

Aşağıdaki kodu, *çözümleyiciler* sınıfının içine ekleyin:

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

Bu kod, `PredictionEnginePool` bağımlılığı ekleme yoluyla aldığınız işlevin oluşturucusuna geçirerek öğesine atar.

## <a name="use-the-model-to-make-predictions"></a>Tahminleri yapmak için modeli kullanın

*Çözümleyiciler* sınıfında bulunan *Run* yönteminin mevcut uygulamasını aşağıdaki kodla değiştirin:

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);
    
    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

Yöntem yürütüldüğünde, http isteğinden gelen veriler seri durumdan çıkarılmış olur ve `PredictionEnginePool`için giriş olarak kullanılır. `Run` Daha `Predict` sonra yöntemi bir tahmin oluşturmak ve sonucu kullanıcıya döndürmek için çağrılır. 

## <a name="test-locally"></a>Yerel olarak test etme

Her şey ayarlandığına göre, uygulamayı test etmek zaman alabilir:

1. Uygulamayı çalıştırma
1. PowerShell 'i açın ve kodu, uygulamanızın üzerinde çalıştığı bağlantı noktası olan bağlantı noktasının bulunduğu istemine girin. Genellikle bağlantı noktası 7071 ' dir.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Başarılı olursa, çıkış aşağıdaki metne benzer görünmelidir:
    
    ```powershell
    Negative
    ```

Tebrikler! Azure Işlevi kullanarak, internet üzerinden tahmine dayalı hale getirmek için modelinizi başarıyla sundu.

## <a name="next-steps"></a>Sonraki Adımlar

- [Azure’a dağıtma](/azure/azure-functions/functions-develop-vs#publish-to-azure)
