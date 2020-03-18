---
title: ASP.NET Core Web API'sinde bir model dağıtma
description: ASP.NET Core Web API kullanarak internet üzerinden ML.NET duygu analizi makine öğrenme modeli hizmet
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398932"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>ASP.NET Core Web API'sinde bir model dağıtma

ASP.NET Core Web API kullanarak web üzerinde önceden eğitilmiş ML.NET makine öğrenimi modelinin nasıl hizmet verilebildiğini öğrenin. Bir web API üzerinden bir model hizmet standart HTTP yöntemleri ile tahminler sağlar.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.
- Powershell.
- Önceden eğitilmiş bir model. Kendi modelinizi oluşturmak veya bu [önceden eğitilmiş duygu analizi makine öğrenme modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirmek için ML.NET Sentiment Analysis [öğreticisini](../tutorials/sentiment-analysis.md) kullanın

## <a name="create-aspnet-core-web-api-project"></a>Çekirdek Web API ASP.NET oluşturma

1. Visual Studio 2017'yi açın. Menü çubuğundan **Dosya > Yeni > Projesi'ni** seçin. Yeni Proje iletişim kutusunda, **Web** düğümü tarafından izlenen **Visual C#** düğümünü seçin. Ardından **ASP.NET Çekirdek Web Uygulaması** proje şablonuna gidin. **Ad** metin kutusunda "SentimentAnalysisWebAPI" yazın ve ardından **Tamam** düğmesini seçin.

1. Farklı ASP.NET Çekirdek Projeleri türlerini görüntüleyen **pencerede, API'yi** ve **Tamam** düğmesini seçin' i seçin.

1. Önceden oluşturulmuş makine öğrenme modeli dosyalarınızı kaydetmek için projenizde *MLModels* adlı bir dizin oluşturun:

    Çözüm Gezgini'nde projenize sağ tıklayın ve Yeni Klasör > Ekle'yi seçin. "MLModels" yazın ve Enter tuşuna basın.

1. Microsoft.ML **NuGet Paketini**Yükleyin:

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML**arayın, listedeki paketi seçin ve Yükle düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul Et** düğmesini seçin.

1. Microsoft.Extensions.ML **Nuget Paketini**Yükleyin:

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.Extensions.ML**arayın, listedeki paketi seçin ve Yükle düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul Et** düğmesini seçin.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Core Web API projesine model ekleme ASP.NET

1. Önceden oluşturulmuş modelinizi *MLModels* dizinine kopyalayın
1. Çözüm Gezgini'nde, model zip dosyasına sağ tıklayın ve Özellikler'i seçin. Gelişmiş altında, daha yeniyse, Kopya'nın değerini Çıktı Dizini'ne kopyaolarak değiştirin.

## <a name="create-data-models"></a>Veri modelleri oluşturma

Giriş verileriniz ve öngörüleriniz için bazı sınıflar oluşturmanız gerekir. Projenize yeni bir sınıf ekleyin:

1. Veri modellerinizi kaydetmek için projenizde *Veri Modelleri* adında bir dizin oluşturun:

    Çözüm Gezgini'nde projenize sağ tıklayın ve Yeni Klasör > Ekle'yi seçin. "DataModels" yazın ve **Enter**tuşuna basın.

2. Çözüm Gezgini'nde, *DataModels* dizinini sağ tıklatın ve ardından Yeni Öğe > ekle'yi seçin.
3. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentData.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin. *SentimentData.cs* dosyası kod düzenleyicisinde açılır. *SentimentData.cs*üst kısmında aşağıdaki ifadesini kullanarak ekleyin:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Varolan sınıf tanımını kaldırın ve **SentimentData.cs** dosyasına aşağıdaki kodu ekleyin:

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

4. Çözüm Gezgini'nde, *DataModels* dizinini sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.
5. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentPrediction.cs*olarak değiştirin. Ardından Ekle düğmesini seçin. kod düzenleyicisinde *SentimentPrediction.cs* dosyası açılır. *SentimentPrediction.cs*üstüne aşağıdaki ifadesini kullanarak ekleyin:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Varolan sınıf tanımını kaldırın ve *SentimentPrediction.cs* dosyasına aşağıdaki kodu ekleyin:

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction`'den `SentimentData`devralır. Bu, model tarafından oluşturulan çıktıyla `SentimentText` birlikte özellikteki özgün verileri görmeyi kolaylaştırır.

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Register PredictionEnginePool uygulamada kullanılmak üzere

Tek bir tahmin yapmak için, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)bir . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Ayrıca, uygulamanız içinde gerekli olan her yerde bunun bir örneğini oluşturmanız gerekir. Uygulamanız büyüdükçe, bu işlem yönetilemez hale gelebilir. Daha iyi performans ve iş parçacığı güvenliği için, `PredictionEnginePool` uygulamanız boyunca [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) kullanılmak [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) üzere bir nesne oluşturan bağımlılık enjeksiyonu ve hizmetin bir birleşimini kullanın.

Eğer [ASP.NET Core bağımlılık enjeksiyon](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)hakkında daha fazla bilgi edinmek istiyorsanız aşağıdaki bağlantı daha fazla bilgi sağlar.

1. *Startup.cs* sınıfını açın ve dosyanın üst bölümüne aşağıdaki ifadesini ekleyin:

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
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

Yüksek düzeyde, bu kod, uygulama tarafından el ile yapmak zorunda kalmak yerine daha sonra kullanılmak üzere nesneleri ve hizmetleri otomatik olarak başlatir.

Makine öğrenimi modelleri statik değildir. Yeni eğitim verileri kullanılabilir hale geldikçe, model yeniden eğitilir ve yeniden dağıtılır. Uygulamanıza modelin en son sürümünü almanın bir yolu, tüm uygulamayı yeniden dağıtmaktır. Ancak, bu uygulama kapalı kalma süresi tanır. Hizmet, `PredictionEnginePool` uygulamanızı kaldırmadan güncelleştirilmiş bir modeli yeniden yüklemek için bir mekanizma sağlar.

Parametreyi `watchForChanges` `true`ve dosya `PredictionEnginePool` sistemi [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) değişiklik bildirimlerini dinleyen ve dosyada bir değişiklik olduğunda olayları yükselten bir başlat' olarak ayarlayın. Bu, modeli `PredictionEnginePool` otomatik olarak yeniden yüklemesini ister.

`modelName` Model, uygulama başına birden fazla modelin değişiklik üzerine yeniden yüklenebilmeleri için parametre ile tanımlanır.

> [!TIP]
> Alternatif olarak, uzaktan `FromUri` depolanan modeller ile çalışırken yöntemi kullanabilirsiniz. Dosya değiştirilen olayları izlemek `FromUri` yerine, değişiklikler için uzak konumu yoklar. Yoklama aralığı varsayılan olarak 5 dakikadır. Uygulamanızın gereksinimlerine bağlı olarak yoklama aralığını artırabilir veya azaltabilirsiniz. Aşağıdaki kod örneğinde, `PredictionEnginePool` model her dakika belirtilen URI'de depolanır.
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a>Predict denetleyicisi oluştur

Gelen HTTP isteklerinizi işlemek için bir denetleyici oluşturun.

1. Çözüm Gezgini'nde, *Denetleyiciler* dizinine sağ tıklayın ve ardından **> Denetleyicisi Ekle'yi**seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **API Denetleyicisi Boş'u** seçin ve **Ekle'yi**seçin.
1. Komut istemiyle **Denetleyici Adı** alanını *PredictController.cs*olarak değiştirin. Ardından Ekle düğmesini seçin. kod düzenleyicisinde *PredictController.cs* dosyası açılır. *PredictController.cs*üst kısmında aşağıdaki ifadesini kullanarak deyimi ekleyin:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Varolan sınıf tanımını kaldırın ve *PredictController.cs* dosyasına aşağıdaki kodu ekleyin:

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

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

Bu kod, `PredictionEnginePool` bağımlılık enjeksiyonu yoluyla aldığınız denetleyicinin oluşturucuya geçirerek atar. Daha sonra, `Predict` denetleyicinin `Post` yöntemi `PredictionEnginePool` `SentimentAnalysisModel` `Startup` sınıfta kayıtlı kullanarak öngörüler yapmak için kullanır ve başarılı olursa sonuçları kullanıcıya geri döndürür.

## <a name="test-web-api-locally"></a>Web API'yi yerel olarak test edin

Her şey ayarlandıktan sonra, uygulamayı test etme zamanı.

1. Uygulamayı çalıştırın.
1. Powershell'i açın ve uygulamanızın dinlediği bağlantı noktası PORT'un bulunduğu aşağıdaki kodu girin.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Başarılı olursa, çıktı aşağıdaki metne benzer olmalıdır:

    ```powershell
    Negative
    ```

Tebrikler! ASP.NET Core Web API kullanarak internet üzerinden öngörülerde bulunmak için modelinizi başarıyla hizmet ettiniz.

## <a name="next-steps"></a>Sonraki Adımlar

- [Azure'a Dağıt](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
