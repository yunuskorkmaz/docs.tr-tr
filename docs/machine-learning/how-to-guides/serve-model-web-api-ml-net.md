---
title: ASP.NET Core Web API 'sinde model dağıtma
description: ASP.NET Core Web API 'sini kullanarak Internet üzerinden ML.NET yaklaşım analizi makine öğrenimi modelini sunar
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: e1dcc719738a2beb3e63463245d4721c5298cf85
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666656"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>ASP.NET Core Web API 'sinde model dağıtma

Bir ASP.NET Core Web API 'SI kullanarak Web 'de önceden eğitilen ML.NET makine öğrenimi modelini nasıl kullanacağınızı öğrenin. Bir Web API 'SI üzerinde bir modele hizmet sunmak, standart HTTP yöntemleri aracılığıyla tahmine dayalı hale getirilmiş.

> [!NOTE]
> `PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.
- PowerShell.
- Önceden eğitilen model. Kendi modelinizi derlemek için [ML.NET yaklaşım Analizi öğreticisini](../tutorials/sentiment-analysis.md) kullanın veya bu [önceden eğitilen yaklaşım Analizi Machine Learning modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirin

## <a name="create-aspnet-core-web-api-project"></a>ASP.NET Core Web API projesi oluştur

1. Visual Studio 2017'yi açın. Menü çubuğundan **dosya > yeni > projesi** öğesini seçin. Yeni proje iletişim kutusunda, **Visual C#**  düğümünü ve ardından **Web** düğümünü seçin. **ASP.NET Core Web uygulaması** proje şablonunu seçin. **Ad** metin kutusuna "SentimentAnalysisWebAPI" yazın ve **Tamam** düğmesini seçin.

1. Farklı türlerde ASP.NET Core projeler görüntüleyen pencerede, **API** ' yi seçin ve **Tamam** düğmesini seçin.

1. Önceden oluşturulmuş makine öğrenimi modeli dosyalarınızı kaydetmek için projenizde *Mlmodeller* adlı bir dizin oluşturun:

    Çözüm Gezgini, projenize sağ tıklayın ve > Yeni klasör Ekle ' yi seçin. "Mlmodeller" yazın ve ENTER tuşuna basın.

1. **Microsoft.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden bu paketi seçin ve sonra da Install düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız Lisans Kabulü iletişim kutusunda **kabul ediyorum** düğmesini seçin.

1. **Microsoft.Extensions.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.Extensions.ml**için arama yapın, listeden bu paketi seçin ve sonra da Install düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız Lisans Kabulü iletişim kutusunda **kabul ediyorum** düğmesini seçin.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Modeli ASP.NET Core Web API projesine ekle

1. Önceden oluşturulmuş modelinizi *Mlmodeller* dizinine kopyalayın
1. Çözüm Gezgini, model ZIP dosyasına sağ tıklayın ve Özellikler ' i seçin. Gelişmiş ' in altında, çıkış dizinine Kopyala değerini daha yeniyse kopyala olarak değiştirin.

## <a name="create-data-models"></a>Veri modelleri oluşturma

Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturmanız gerekir. Projenize yeni bir sınıf ekleyin:

1. Veri modellerinizi kaydetmek için projenizde *Datamodeller* adlı bir dizin oluşturun:

    Çözüm Gezgini, projenize sağ tıklayın ve > Yeni klasör Ekle ' yi seçin. "Datamodeller" yazın ve **ENTER**tuşuna basın.

2. Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra > yeni öğe Ekle ' yi seçin.
3. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin. *SentimentData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki using ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu **SentimentData.cs** dosyasına ekleyin:
    
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
5. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentPrediction.cs*olarak değiştirin. Sonra Ekle düğmesini seçin. *SentimentPrediction.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki using ifadesini *SentimentPrediction.cs*öğesinin en üstüne ekleyin:

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

    `SentimentPrediction`öğesinden `SentimentData`devralır. Bu, `SentimentText` özellikte orijinal verileri, model tarafından oluşturulan çıktıyı birlikte görmenizi kolaylaştırır. 

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Uygulamada kullanmak için PredictionEnginePool Kaydet

Tek bir tahmin yapmak için kullanın [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). Uygulamanızda kullanabilmeniz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, gerektiğinde oluşturmanız gerekir. Bu durumda, dikkate alınması gereken en iyi yöntem bağımlılık ekleme yöntemidir.

[ASP.NET Core ' de bağımlılık ekleme](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)hakkında bilgi edinmek istiyorsanız aşağıdaki bağlantıda daha fazla bilgi sağlanmaktadır.

1. *Startup.cs* sınıfını açın ve aşağıdaki using ifadesini dosyanın en üstüne ekleyin:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. *ConfigureServices* yöntemine aşağıdaki kodu ekleyin:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

Yüksek düzeyde bu kod, uygulama tarafından el ile yapmak yerine nesneleri ve hizmetleri otomatik olarak başlatır.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir. Gelişmiş performans ve iş parçacığı güvenliği için, uygulama `PredictionEnginePool` kullanımı için `PredictionEngine` bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) nesne oluşturan hizmetini kullanın. [ASP.NET Core içinde nesne havuzları `PredictionEngine` oluşturma ve kullanma](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)hakkında daha fazla bilgi edinmek için aşağıdaki blog gönderisini okuyun.  

## <a name="create-predict-controller"></a>Tahmin denetleyicisi oluştur

Gelen HTTP isteklerinizi işlemek için bir denetleyici oluşturun.

1. Çözüm Gezgini, *denetleyiciler* dizinine sağ tıklayın ve sonra **> denetleyicisi Ekle**' yi seçin.
1. **Yeni öğe Ekle** iletişim kutusunda, **API denetleyicisi boş** ' ı seçin ve **Ekle**' yi seçin.
1. İstemde, **Denetleyici adı** alanını *PredictController.cs*olarak değiştirin. Sonra Ekle düğmesini seçin. *PredictController.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki using ifadesini *PredictController.cs*öğesinin en üstüne ekleyin:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *PredictController.cs* dosyasına ekleyin:
    
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

Bu kod, `PredictionEnginePool` bağımlılığı ekleme yoluyla aldığınız denetleyicinin oluşturucusuna geçirerek öğesine atar. Ardından, `Predict` `Post` denetleyicinin yöntemi tahmin yapmak `PredictionEnginePool` için öğesini kullanır ve başarılı olursa sonuçları kullanıcıya geri döndürür.

## <a name="test-web-api-locally"></a>Web API 'sini yerel olarak test etme

Her şey ayarlandıktan sonra, uygulamayı test etmek zaman alabilir.

1. Uygulamayı çalıştırın.
1. PowerShell 'i açın ve aşağıdaki kodu girerek bağlantı noktasının, uygulamanızın dinlediği bağlantı noktasıdır.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Başarılı olursa, çıkış aşağıdaki metne benzer görünmelidir:
    
    ```powershell
    Negative
    ```

Tebrikler! ASP.NET Core bir Web API 'SI kullanarak internet üzerinden tahmin etmek için modelinize başarıyla hizmet sundu.

## <a name="next-steps"></a>Sonraki Adımlar

- [Azure’a dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)
