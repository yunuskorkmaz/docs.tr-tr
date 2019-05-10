---
title: Azure işlevleri için model dağıtma
description: ML.NET yaklaşım analizi makine öğrenme modelinin tahmin için Azure işlevleri'ni kullanarak internet üzerinden hizmet
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: c30c1c2e6f00020d22fe32fb3f53cefe88d8bb09
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063506"
---
# <a name="deploy-a-model-to-azure-functions"></a>Azure işlevleri için model dağıtma

HTTP üzerinden Azure işlevleri ile sunucusuz ortam öğrenme modeli tahminler elde etmek için önceden eğitilmiş bir ML.NET makine dağıtmayı öğrenin.

> [!NOTE]
> `PredictionEnginePool` Hizmet uzantısı, şu anda Önizleme aşamasındadır.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) "Azure geliştirme yüklü" ve ".NET Core çoklu platform geliştirme" iş yükü.
- [Azure işlevleri araçları](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- Önceden eğitilmiş model. Kullanım [ML.NET yaklaşım analizi Öğreticisi](../tutorials/sentiment-analysis.md) kendi modelinizi oluşturun veya bunu indirmek üzere [önceden eğitilmiş yaklaşım analizi, machine learning modeli](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-azure-functions-project"></a>Azure işlevleri projesi oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#**  düğümünü ve ardından **bulut** düğümü. Ardından **Azure işlevleri** proje şablonu. İçinde **adı** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve ardından **Tamam** düğmesi.
1. İçinde **yeni proje** iletişim kutusunda, proje seçeneklerinde Yukarıdaki açılan listeyi açın ve seçin **Azure işlevler v2 (.NET Core)**. Ardından, **Http tetikleyicisi** proje ve ardından **Tamam** düğmesi.
1. Adlı bir dizin oluşturmak *MLModels* modelinizi kaydetmek için projenizde:

    İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**. "MLModels" yazın ve Enter tuşuna basın.

1. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

1. Yükleme **Microsoft.Extensions.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.Extensions.ML**, bu paket listesinde seçip **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

## <a name="add-pre-trained-model-to-project"></a>Önceden eğitilmiş model projeye Ekle

1. Önceden oluşturulmuş modelinizi kopyalama *MLModels* klasör.
1. Çözüm Gezgini'nde, önceden oluşturulmuş model dosyasını sağ tıklatın ve seçin **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Yaklaşımı analiz etmek için Azure işlevi oluşturma

Yaklaşım tahmin etmek için bir sınıf oluşturun. Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **Azure işlevi** değiştirip **adı** alanı *AnalyzeSentiment.cs*. Ardından, **Ekle** düğmesi.

1. İçinde **yeni Azure işlevi** iletişim kutusunda **Http tetikleyicisi**. Ardından, **Tamam** düğmesi.

    *AnalyzeSentiment.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *AnalyzeSentiment.cs*:

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

    Varsayılan olarak, `AnalyzeSentiment` sınıfı `static`. Kaldırdığınızdan emin olun `static` sınıf tanımından anahtar sözcüğü.

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a>Veri modelleri oluşturma

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir. Yeni bir sınıf, projenize ekleyin:

1. Adlı bir dizin oluşturmak *DataModels* projenizde veri Modellerinizi kaydetmek için: Çözüm Gezgini'nde seçin ve proje üzerinde sağ **Ekle > Yeni klasör**. "DataModels" yazın ve Enter tuşuna basın.
2. Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.
3. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*. Ardından, **Ekle** düğmesi. 

    *SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *SentimentData.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *SentimentData.cs* dosyası:
    
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

4. Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.
5. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentPrediction.cs*. Ardından, **Ekle** düğmesi. *SentimentPrediction.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *SentimentPrediction.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *SentimentPrediction.cs* dosyası:

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction` devralınan `SentimentData` özgün verilere erişim sağlayan `SentimentText` özelliğinin yanı sıra model tarafından oluşturulan çıktı.

## <a name="register-predictionenginepool-service"></a>PredictionEnginePool hizmeti kaydedin

Tek bir tahminde bulunmak için kullanmak [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602). Kullanmak için [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) gerektiğinde uygulamanızı oluşturmanız gerekir. Bu durumda, dikkate alınması gereken bir en iyi bağımlılık ekleme yöntemidir.

Hakkında bilgi edinmek istiyorsanız aşağıdaki bağlantıda daha fazla bilgi sağlar. [bağımlılık ekleme](https://en.wikipedia.org/wiki/Dependency_injection).

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *Startup.cs*. Ardından, **Ekle** düğmesi. 

    *Startup.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *Startup.cs*:

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Kullanarak aşağıdaki var olan kod kaldırma deyimleri ve aşağıdaki kodu ekleyin *Startup.cs* dosyası:

    ```csharp
    [assembly: WebJobsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        class Startup : IWebJobsStartup
        {
            public void Configure(IWebJobsBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

Yüksek düzeyde, bu kod nesneleri ve otomatik yerine el ile yapmanıza gerek kalmadan uygulama tarafından istendiğinde hizmetlerini başlatır.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) iş parçacığı açısından güvenli değildir. Performansı artırmak ve iş parçacığı güvenliği için kullanmak `PredictionEnginePool` oluşturan hizmeti bir [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) , `PredictionEngine` nesneleri uygulama kullanımı. 

## <a name="register-startup-as-an-azure-functions-extension"></a>Azure işlevleri uzantı olarak başlangıç kaydetme

Kullanmak için `Startup` uygulamanızda, Azure işlevleri uzantı olarak kaydetmeniz gerekir. Adlı yeni bir dosya oluşturun *extensions.json* projenizdeki bir zaten mevcut değilse.

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **yeni öğe** iletişim kutusunda **Visual C#**  düğümünü ve ardından **Web** düğümü. Ardından **Json dosyası** seçeneği. İçinde **adı** metin kutusuna "extensions.json" yazın ve ardından **Tamam** düğmesi.

    *Extensions.json* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki içeriği ekleyin *extensions.json*:
    
    ```json
    {
      "extensions": [
        {
          "name": "Startup",
          "typename": "SentimentAnalysisFunctionsApp.Startup, SentimentAnalysisFunctionsApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"
        }
      ]
    }
    ```

1. Çözüm Gezgini'nde sağ tıklayın, *extensions.json* seçin ve dosya **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

## <a name="load-the-model-into-the-function"></a>İşleve model yüklenemiyor

Aşağıdaki kodu ekleyin *AnalyzeSentiment* sınıfı:

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

Bu kod atar `PredictionEnginePool` bağımlılık ekleme erişmenizi işlevin oluşturucusuna geçirerek.

## <a name="use-the-model-to-make-predictions"></a>Tahminler elde etmeye modelini kullanın

Mevcut uygulanması yerine *çalıştırmak* yönteminde *AnalyzeSentiment* sınıfı aşağıdaki kod ile:

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

Zaman `Run` yöntemini yürütür, HTTP isteği gelen verileri seri durumdan ve için girdi olarak kullanılan `PredictionEnginePool`. `Predict` Yöntemi tahmin oluşturmak ve bir sonuç kullanıcıya sonra çağrılır. 

## <a name="test-locally"></a>Yerel olarak test etme

Her şeyi ayarlanır, bu uygulamayı test etmek için zaman değil:

1. Uygulamayı çalıştırma
1. PowerShell'i açın ve kodu girin bağlantı noktası, bağlantı noktası olduğu istemine uygulamanız çalışıyor. Genellikle 7071 bağlantı noktasıdır.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Başarılı olursa çıktı aşağıdaki metne benzer görünmelidir:
    
    ```powershell
    Negative
    ```

Tebrikler! Ayrıca, bir Azure işlevi kullanarak internet üzerinden tahminlerde bulunmak üzere modelinizi başarıyla hizmet vermektedir.

## <a name="next-steps"></a>Sonraki Adımlar

- [Azure’a dağıtma](/azure/azure-functions/functions-develop-vs#publish-to-azure)