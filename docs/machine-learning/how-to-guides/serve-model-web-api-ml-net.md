---
title: Bir ASP.NET Core Web API'si, model dağıtma
description: ML.NET yaklaşım analizi, makine öğrenme modelinin ASP.NET Core Web API'si kullanarak internet üzerinden hizmet
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: f8b8f74f752aeb243d4a2987929bd28ddc5f7d5a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641091"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Bir ASP.NET Core Web API'si, model dağıtma

Bir ASP.NET Core Web API'si kullanarak web üzerinde önceden eğitilen ML.NET makine öğrenme modeli hizmet öğrenin. Bir modeli bir web API'si sunan standart HTTP yöntemleri aracılığıyla Öngörüler sağlar.

> [!NOTE]
> `PredictionEnginePool` Hizmet uzantısı, şu anda Önizleme aşamasındadır.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.
- PowerShell.
- Önceden eğitilmiş model. Kullanım [ML.NET yaklaşım analizi Öğreticisi](../tutorials/sentiment-analysis.md) kendi modelinizi oluşturun veya bunu indirmek üzere [önceden eğitilmiş yaklaşım analizi, machine learning modeli](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>ASP.NET Core Web API projesi oluşturma

1. Visual Studio 2017'yi açın. Seçin **Dosya > Yeni > Proje** menü çubuğundan. Yeni Proje iletişim kutusunda, seçmek **Visual C#**  düğümünü ve ardından **Web** düğümü. Ardından **ASP.NET Core Web uygulaması** proje şablonu. İçinde **adı** metin kutusuna "SentimentAnalysisWebAPI" yazın ve ardından **Tamam** düğmesi.

1. ASP.NET Core projeleri farklı türde görüntüler penceresinde seçin **API** ve select **Tamam** düğmesi.

1. Adlı bir dizin oluşturmak *MLModels* projenizde, önceden oluşturulmuş makine öğrenimi modeli dosyaları kaydetmek için:

    Çözüm Gezgini'nde projenize sağ tıklayın ve Ekle > Yeni bir klasör. "MLModels" yazın ve Enter tuşuna basın.

1. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, listesinde o paketi seçin ve Yükle düğmesini seçin. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** için lisans şartlarını kabul ediyorsanız lisans kabulü iletişim kutusunda düğmesi listelenen paketler.

1. Yükleme **Microsoft.Extensions.ML Nuget paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.Extensions.ML**, listesinde o paketi seçin ve Yükle düğmesini seçin. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** için lisans şartlarını kabul ediyorsanız lisans kabulü iletişim kutusunda düğmesi listelenen paketler.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Model için ASP.NET Core Web API projesi Ekle

1. Önceden oluşturulmuş modelinizi kopyalama *MLModels* dizini
1. Çözüm Gezgini'nde, model zip dosyasını sağ tıklayın ve Özellikler'i seçin. Gelişmiş altında kopyalama çıkış dizinine kopyalanacak yeniyse değiştirin.

## <a name="create-data-models"></a>Veri modelleri oluşturma

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir. Yeni bir sınıf, projenize ekleyin:

1. Adlı bir dizin oluşturmak *DataModels* projenizde veri Modellerinizi kaydetmek için:

    Çözüm Gezgini'nde projenize sağ tıklayın ve Ekle > Yeni bir klasör. "DataModels" yazın ve isabet **Enter**.

2. Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından Ekle > Yeni öğe.
3. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*. Ardından, **Ekle** düğmesi. *SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *SentimentData.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin **SentimentData.cs** dosyası:
    
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
5. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentPrediction.cs*. Ardından Ekle düğmesini seçin. *SentimentPrediction.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *SentimentPrediction.cs*:

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

    `SentimentPrediction` devralınan `SentimentData`. Bu, özgün veri görmeyi kolaylaştırır `SentimentText` modeli tarafından oluşturulan çıktı birlikte özelliği. 

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Uygulama kullanım PredictionEnginePool kaydolun

Tek bir tahminde bulunmak için kullanmak [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602). Kullanmak için [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) gerektiğinde uygulamanızı oluşturmanız gerekir. Bu durumda, dikkate alınması gereken bir en iyi bağımlılık ekleme yöntemidir.

Hakkında bilgi edinmek istiyorsanız aşağıdaki bağlantıda daha fazla bilgi sağlar. [ASP.NET Core bağımlılık ekleme](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Açık *Startup.cs* sınıfı ve aşağıdaki using deyimini dosyanın en üstüne:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. Aşağıdaki kodu ekleyin *Createservicereplicalisteners()* yöntemi:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

Yüksek düzeyde, bu kod nesneleri ve otomatik yerine el ile yapmanıza gerek kalmadan uygulama tarafından istendiğinde hizmetlerini başlatır.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) iş parçacığı açısından güvenli değildir. Performansı artırmak ve iş parçacığı güvenliği için kullanmak `PredictionEnginePool` oluşturan hizmeti bir [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) , `PredictionEngine` nesneleri uygulama kullanımı. Hakkında daha fazla bilgi edinmek için şu blog gönderisini okuyun [oluşturma ve kullanma `PredictionEngine` nesne ASP.NET Core havuzlarında](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).  

## <a name="create-predict-controller"></a>Predıct denetleyicisi oluşturma

Gelen HTTP isteklerini işlemek için bir denetleyici oluşturun.

1. Çözüm Gezgini'nde sağ *denetleyicileri* dizin ve ardından **Ekle > denetleyicisi**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **boş API denetleyicisi** seçip **Ekle**.
1. Komut istemi değişim **Denetleyici adı** alanı *PredictController.cs*. Ardından Ekle düğmesini seçin. *PredictController.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *PredictController.cs*:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *PredictController.cs* dosyası:
    
    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

Bu kod atar `PredictionEnginePool` bağımlılık ekleme erişmenizi denetleyicinin oluşturucusuna geçirerek. Ardından, `Predict` denetleyicinin `Post` yöntemi kullanan `PredictionEnginePool` tahminlerde bulunabilir ve başarılı olursa sonuçları kullanıcıya geri döndürmek için.

## <a name="test-web-api-locally"></a>Yerel olarak test web API'si

Her şeyi ayarlandıktan sonra uygulama test etme vakti.

1. Uygulamayı çalıştırın.
1. PowerShell'i açın ve bağlantı noktası, bağlantı noktası olduğu aşağıdaki kodu girin. uygulamanızı dinlediği.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Başarılı olursa çıktı aşağıdaki metne benzer görünmelidir:
    
    ```powershell
    Negative
    ```

Tebrikler! Ayrıca, bir ASP.NET Core Web API'si kullanarak internet üzerinden tahminlerde bulunmak üzere modelinizi başarıyla hizmet vermektedir.

## <a name="next-steps"></a>Sonraki Adımlar

- [Azure’a dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)
