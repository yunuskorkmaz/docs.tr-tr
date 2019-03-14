---
title: Azure işlevleri için ML.NET Model dağıtma
description: ML.NET yaklaşım analizi makine öğrenme modelinin tahmin için Azure işlevleri'ni kullanarak internet üzerinden hizmet
ms.date: 03/08/2019
ms.custom: mvc,how-to
ms.openlocfilehash: db29e37660665b02ab93a07b37418f0c4c20a608
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788656"
---
# <a name="how-to-use-mlnet-model-in-azure-functions"></a>Nasıl yapılır: Azure işlevleri ML.NET modelini kullanın

Bu nasıl yapılır tek tek nasıl Öngörüler gösteren Azure işlevleri gibi sunucusuz bir ortamda Internet üzerinden önceden oluşturulmuş ML.NET makine öğrenme modeli kullanılarak yapılabilir.

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**. Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) "Azure geliştirme yüklü" ve ".NET Core çoklu platform geliştirme" iş yükü. 
- [Azure işlevleri araçları](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- Önceden eğitilmiş model. 
    - Kullanım [ML.NET yaklaşım analizi Öğreticisi](../tutorials/sentiment-analysis.md) kendi modeli derler.
    - Bu indirme [önceden eğitilmiş yaklaşım analizi, machine learning modeli](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-azure-functions-project"></a>Azure işlevleri projesi oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#**  düğümünü ve ardından **bulut** düğümü. Ardından **Azure işlevleri** proje şablonu. İçinde **adı** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve ardından **Tamam** düğmesi.
1. İçinde **yeni proje** iletişim kutusunda, proje seçeneklerinde Yukarıdaki açılan listeyi açın ve seçin **Azure işlevler v2 (.NET Core)**. Ardından, **Http tetikleyicisi** proje ve ardından **Tamam** düğmesi.
1. Adlı bir dizin oluşturmak *MLModels* modelinizi kaydetmek için projenizde:

    İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**. "MLModels" yazın ve Enter tuşuna basın.

1. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

## <a name="add-pre-built-model-to-project"></a>Önceden oluşturulmuş Model projeye Ekle

1. Önceden oluşturulmuş modelinizi kopyalama *MLModels* klasör.
1. Çözüm Gezgini'nde, önceden oluşturulmuş model dosyasını sağ tıklatın ve seçin **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

## <a name="create-function-to-analyze-sentiment"></a>Yaklaşımı analiz etmek için işlev oluşturma

Yaklaşım tahmin etmek için bir sınıf oluşturun. Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **Azure işlevi** değiştirip **adı** alanı *AnalyzeSentiment.cs*. Ardından, **Ekle** düğmesi.

1. İçinde **yeni Azure işlevi** iletişim kutusunda **Http tetikleyicisi**. Ardından, **Tamam** düğmesi.

    *AnalyzeSentiment.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *GitHubIssueData.cs*:

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
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using Microsoft.ML.Data;
using MLNETServerless.DataModels;
```

### <a name="create-data-models"></a>Veri modelleri oluşturma

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir. Yeni bir sınıf, projenize ekleyin:

1. Adlı bir dizin oluşturmak *DataModels* projenizde veri Modellerinizi kaydetmek için: Çözüm Gezgini'nde seçin ve proje üzerinde sağ **Ekle > Yeni klasör**. "DataModels" yazın ve Enter tuşuna basın.
2. Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.
3. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*. Ardından, **Ekle** düğmesi. *SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *SentimentData.cs*:

```csharp
using Microsoft.ML.Data;
```

Varolan sınıf tanımına kaldırın ve SentimentData.cs dosyaya aşağıdaki kodu ekleyin:

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }
}
```

4. Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.
5. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentPrediction.cs*. Ardından, **Ekle** düğmesi. *SentimentPrediction.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *SentimentPrediction.cs*:

```csharp
using Microsoft.ML.Data;
```

Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *SentimentPrediction.cs* dosyası:

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

### <a name="add-prediction-logic"></a>Tahmin mantığı ekleyin

Mevcut uygulanması yerine *çalıştırmak* yönteminde *AnalyzeSentiment* sınıfı aşağıdaki kod ile:

```csharp
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function,"post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        //Create Context
        MLContext mlContext = new MLContext();

        //Load Model
        using (var fs = File.OpenRead("MLModels/sentiment_model.zip"))
        {
            model = mlContext.Model.Load(fs);
        }

        //Parse HTTP Request Body
        string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

        //Create Prediction Engine
        PredictionEngine<SentimentData, SentimentPrediction> predictionEngine = model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);

        //Make Prediction
        SentimentPrediction prediction = predictionEngine.Predict(data);

        //Convert prediction to string
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        //Return Prediction
        return (ActionResult)new OkObjectResult(isToxic);
    }
}
```

## <a name="test-locally"></a>Yerel olarak test etme

Her şeyi ayarlanır, bu uygulamayı test etmek için zaman değil:

1. Uygulamayı çalıştırma
1. PowerShell'i açın ve kodu girin bağlantı noktası, bağlantı noktası olduğu istemine uygulamanız çalışıyor. Genellikle 7071 bağlantı noktasıdır. 

```powershell
Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

Başarılı olursa çıktı aşağıdaki metne benzer görünmelidir:

```powershell
Toxic
```

Tebrikler! Ayrıca, bir Azure işlevi kullanarak internet üzerinden tahminlerde bulunmak üzere modelinizi başarıyla hizmet vermektedir.

## <a name="next-steps"></a>Sonraki Adımlar

- [Azure’a dağıtma](/azure/azure-functions/functions-develop-vs#publish-to-azure)