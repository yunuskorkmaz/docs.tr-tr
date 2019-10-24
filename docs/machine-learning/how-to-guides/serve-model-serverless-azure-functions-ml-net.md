---
title: Modeli Azure İşlevleri’ne dağıtma
description: Azure Işlevleri 'ni kullanarak Internet üzerinden tahmin için ML.NET yaklaşım analizi makine öğrenimi modelini sunar
ms.date: 09/12/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 4f805c638df9e60160c27fa08995ce393e59d007
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774524"
---
# <a name="deploy-a-model-to-azure-functions"></a>Modeli Azure İşlevleri’ne dağıtma

Azure Işlevleri sunucusuz bir ortam aracılığıyla HTTP üzerinden tahmin için önceden eğitilen ML.NET makine öğrenimi modelini dağıtmayı öğrenin.

> [!NOTE]
> `PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.

## <a name="prerequisites"></a>Prerequisites

- ".NET Core platformlar arası geliştirme" iş yükü ve "Azure geliştirme" yüklü [Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) .
- Microsoft. NET. SDK. Functions NuGet paketi sürüm 1.0.28 +.
- [Azure Işlevleri araçları](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- Önceden eğitilen model. Kendi modelinizi derlemek için [ML.NET yaklaşım Analizi öğreticisini](../tutorials/sentiment-analysis.md) kullanın veya bu [önceden eğitilen yaklaşım Analizi Machine Learning modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirin

## <a name="create-azure-functions-project"></a>Azure Işlevleri projesi oluştur

1. Visual Studio 2017 ' i açın. Menü çubuğundan **dosya** > **Yeni** > **Proje** ' yi seçin. **Yeni proje** iletişim kutusunda, **Visual C#**  düğümünü ve ardından **bulut** düğümünü seçin. Ardından **Azure işlevleri** proje şablonunu seçin. **Ad** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve **Tamam** düğmesini seçin.
1. **Yeni proje** iletişim kutusunda, proje seçeneklerinin üzerindeki açılan menüyü açın ve **Azure işlevleri v2 (.NET Core)** seçeneğini belirleyin. Ardından, **http tetikleyicisi** projesini seçin ve **Tamam** düğmesini seçin.
1. Modelinize kaydetmek için projenizde *Mlmodeller* adlı bir dizin oluşturun:

    **Çözüm Gezgini**, projenize sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin. "Mlmodeller" yazın ve ENTER tuşuna basın.

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

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.

1. **Yeni öğe Ekle** Iletişim kutusunda **Azure işlevi** ' ni seçin ve **ad** alanını *AnalyzeSentiment.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

1. **Yeni Azure işlevi** Iletişim kutusunda **http tetikleyicisi**' ni seçin. Ardından **Tamam** düğmesini seçin.

    *AnalyzeSentiment.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadesini *AnalyzeSentiment.cs*öğesinin en üstüne ekleyin:

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    Varsayılan olarak, `AnalyzeSentiment` sınıfı `static` ' dir. Sınıf tanımından `static` anahtar sözcüğünü kaldırdığınızdan emin olun.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Veri modelleri oluşturma

Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturmanız gerekir. Projenize yeni bir sınıf ekleyin:

1. Projenizde veri modellerinizi kaydetmek için *datamodeller* adlı bir dizin oluşturun: Çözüm Gezgini, projenize sağ tıklayın ve **> yeni klasör ekle**' yi seçin. "Datamodeller" yazın ve ENTER tuşuna basın.
2. Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.
3. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *SentimentData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki using ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentData.cs* dosyasına ekleyin:

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.
5. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentPrediction.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin. *SentimentPrediction.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki using ifadesini *SentimentPrediction.cs*öğesinin en üstüne ekleyin:

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentPrediction.cs* dosyasına ekleyin:

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction`, `SentimentText` özelliğindeki özgün verilere ve model tarafından oluşturulan çıktıya erişim sağlayan `SentimentData` ' den devralır.

## <a name="register-predictionenginepool-service"></a>PredictionEnginePool hizmetini Kaydet

Tek bir tahmin yapmak için bir [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)oluşturmanız gerekir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir. Ayrıca, uygulamanızın içinde gerek duyduğu her yerde bir örneği oluşturmanız gerekir. Uygulamanız büyüdükçe, bu işlem yönetilebilir hale gelebilir. Daha iyi performans ve iş parçacığı güvenliği için, uygulamanız genelinde kullanılmak üzere bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan bağımlılık ekleme ve `PredictionEnginePool` hizmeti birleşimini kullanın.

Aşağıdaki bağlantı, [bağımlılık ekleme](https://en.wikipedia.org/wiki/Dependency_injection)hakkında daha fazla bilgi edinmek istiyorsanız daha fazla bilgi sağlar.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.
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
                    .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
            }
        }
    }
    ```

Yüksek düzeyde, bu kod, uygulama tarafından el ile yapmak yerine, daha sonra kullanmak üzere nesne ve hizmetleri otomatik olarak başlatır.

Makine öğrenimi modelleri statik değildir. Yeni eğitim verileri kullanılabilir hale geldiğinde, model geri çekme ve yeniden dağıtılır. Bir modelin en son sürümünü uygulamanıza almanın bir yolu, uygulamanın tamamını yeniden dağıtmaktan biridir. Ancak bu, uygulama kapalı kalma süresini tanıtır. @No__t_0 hizmeti, uygulamanızı kapatmak zorunda kalmadan güncelleştirilmiş bir modeli yeniden yükleme mekanizması sağlar.

@No__t_0 parametresini `true` olarak ayarlayın ve `PredictionEnginePool` dosya sistemi değişiklik bildirimlerini dinleyen ve dosyada değişiklik olduğunda olay başlatan bir [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) başlatır. Bu, modeli otomatik olarak yeniden yüklemek için `PredictionEnginePool` ' a sorar.

Model `modelName` parametresiyle tanımlanır, böylece değişiklik yapıldığında uygulama başına birden fazla model yeniden yüklenebilir.

> [!TIP]
> Alternatif olarak, uzaktan depolanan modellerle çalışırken `FromUri` yöntemini kullanabilirsiniz. Dosya değiştirilen olayları izlemek yerine `FromUri`, uzak konumu değişiklikler için yoklar. Yoklama aralığı varsayılan olarak 5 dakikadır. Uygulama gereksinimlerine bağlı olarak yoklama aralığını artırabilir veya azaltabilirsiniz. Aşağıdaki kod örneğinde, `PredictionEnginePool` her dakikada belirtilen URI 'de depolanan modeli yoklar.
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>Modeli işleve yükleme

Aşağıdaki kodu, *çözümleyiciler* sınıfının içine ekleyin:

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

Bu kod, bağımlılığı ekleme yoluyla aldığınız işlevin oluşturucusuna geçirerek `PredictionEnginePool` ' a atar.

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
    SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

@No__t_0 yöntemi yürütüldüğünde, HTTP isteğinden gelen veriler seri durumdan çıkarılacak ve `PredictionEnginePool` giriş olarak kullanılır. @No__t_0 yöntemi daha sonra, `Startup` sınıfına kayıtlı `SentimentAnalysisModel` kullanarak tahmine dayalı hale getirmek için çağrılır ve başarılı olursa sonuçları kullanıcıya geri döndürür.

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

Mühendisi! Azure Işlevi kullanarak, internet üzerinden tahmine dayalı hale getirmek için modelinizi başarıyla sundu.

## <a name="next-steps"></a>Sonraki Adımlar

- [Azure’a dağıtma](/azure/azure-functions/functions-develop-vs#publish-to-azure)
