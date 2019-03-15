---
title: Machine Learning modeli ASP.NET Core Web API hizmet
description: ML.NET yaklaşım analizi, makine öğrenme modelinin ASP.NET Core Web API'si kullanarak internet üzerinden hizmet
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 07b751caff8ef0ca9a23bed68ddf88feb7b5ae4f
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57849064"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a>Nasıl yapılır: Machine Learning modeli ASP.NET Core Web API'si aracılığıyla hizmet

Bu nasıl yapılır, önceden oluşturulmuş ML.NET makine öğrenme modeli kullanarak bir ASP.NET Core Web API'si Web hizmet işlemi gösterilmektedir. Bunun yapılması kullanıcıların tahmin amacıyla standart HTTP yöntemleri aracılığıyla API'sine erişim sağlar.

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**. Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.
- PowerShell.
- Önceden eğitilmiş model.
    - Kullanım [ML.NET yaklaşım analizi Öğreticisi](../tutorials/sentiment-analysis.md) kendi modeli derler.
    - Bu indirme [önceden eğitilmiş yaklaşım analizi, machine learning modeli](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>ASP.NET Core Web API projesi oluşturma

1. Visual Studio 2017'yi açın. Seçin **Dosya > Yeni > Proje** menü çubuğundan. Yeni Proje iletişim kutusunda, seçmek **Visual C#**  düğümünü ve ardından **Web** düğümü. Ardından **ASP.NET Core Web uygulaması** proje şablonu. İçinde **adı** metin kutusuna "SentimentAnalysisWebAPI" yazın ve ardından **Tamam** düğmesi.
1. ASP.NET Core projeleri farklı türde görüntüler penceresinde seçin **API** ve select **Tamam** düğmesi.
1. Adlı bir dizin oluşturmak *MLModels* projenizde, önceden oluşturulmuş makine öğrenimi modeli dosyaları kaydetmek için:

    Çözüm Gezgini'nde projenize sağ tıklayın ve Ekle > Yeni bir klasör. "MLModels" yazın ve Enter tuşuna basın.

1. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, listesinde o paketi seçin ve Yükle düğmesini seçin. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** için lisans şartlarını kabul ediyorsanız lisans kabulü iletişim kutusunda düğmesi listelenen paketler.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Model için ASP.NET Core Web API projesi Ekle

1. Önceden oluşturulmuş modelinizi kopyalama *MLModels* dizini
1. Çözüm Gezgini'nde, model zip dosyasını sağ tıklayın ve Özellikler'i seçin. Gelişmiş altında kopyalama çıkış dizinine kopyalanacak yeniyse değiştirin.

## <a name="build-data-models"></a>Veri modelleri oluşturabilir

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir. Yeni bir sınıf, projenize ekleyin:

1. Adlı bir dizin oluşturmak *DataModels* projenizde veri Modellerinizi kaydetmek için:

    Çözüm Gezgini'nde projenize sağ tıklayın ve Ekle > Yeni bir klasör. "DataModels" yazın ve isabet **Enter**.

2. Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından Ekle > Yeni öğe.
3. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*. Ardından, **Ekle** düğmesi. *SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *SentimentData.cs*:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin **SentimentData.cs** dosyası:

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
5. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentPrediction.cs*. Ardından Ekle düğmesini seçin. *SentimentPrediction.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *SentimentPrediction.cs*:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
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

## <a name="create-prediction-service"></a>Öngörü hizmeti oluşturma

Düzenleme ve tahmin mantıksal uygulamanın tamamı boyunca yeniden kullanmak için bir öngörü hizmeti oluşturun.

1. Adlı bir dizin oluşturmak *Hizmetleri* uygulama tarafından kullanılan hizmetler tutmak için projenizdeki:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **Ekle > Yeni klasör**. "Hizmetler" yazın ve isabet **Enter**.

1. Çözüm Gezgini'nde sağ *Hizmetleri* dizin ve ardından **Ekle > Yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *PredictionService.cs*. Ardından, **Ekle** düğmesi. *PredictionService.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *PredictionService.cs*:

```csharp
using System;
using System.IO;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
```

Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *PredictionService.cs* dosyası:

```csharp
public class PredictionService
{
    private readonly PredictionEngine<SentimentData, SentimentPrediction> _predictionEngine;
    public PredictionService(PredictionEngine<SentimentData,SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine;
    }

    public string Predict(SentimentData input)
    {
        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return isToxic;

    }
}
```

## <a name="register-predictions-service-for-use-in-application"></a>Uygulamada Öngörüler hizmeti kullanmak için kaydetme

Öngörü hizmeti kullanmak için gereken her zaman oluşturmanız gerekir. Bu durumda, dikkate alınması gereken bir en iyi ASP.NET Core bağımlılık ekleme yöntemidir.

Hakkında bilgi edinmek istiyorsanız aşağıdaki bağlantıda daha fazla bilgi sağlar. [bağımlılık ekleme](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Açık *Startup.cs* sınıfı ve aşağıdaki using deyimini dosyanın en üstüne:

```csharp
using System.IO;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
using SentimentAnalysisWebAPI.Services;
```

1. Aşağıdaki kod satırlarını ekleme *Createservicereplicalisteners()* yöntemi:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddSingleton<MLContext>();
    services.AddSingleton<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
    {
        MLContext mlContext = ctx.GetRequiredService<MLContext>();
        string modelFilePathName = "MLModels/sentiment_model.zip";

        //Load model from file
        ITransformer model;
        using (var stream = File.OpenRead(modelFilePathName))
        {
            model = mlContext.Model.Load(stream);
        }

        // Return prediction engine
        return model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);
    });
    services.AddSingleton<PredictionService>();
}
```

Yüksek düzeyde, bu kod nesneleri ve otomatik yerine el ile yapmanıza gerek kalmadan uygulama tarafından istendiğinde hizmetlerini başlatır.

## <a name="create-predict-controller"></a>Oluşturma denetleyicisi tahmin edin

Gelen HTTP isteklerini işlemek için bir denetleyici oluşturmanız gerekir.

1. Çözüm Gezgini'nde sağ *denetleyicileri* dizin ve ardından **Ekle > denetleyicisi**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **boş API denetleyicisi** seçip **Ekle**.
1. Komut istemi değişim **Denetleyici adı** alanı *PredictController.cs*. Ardından Ekle düğmesini seçin. *PredictController.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki using deyimini üstüne *PredictController.cs*:

```csharp
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using SentimentAnalysisWebAPI.Services;
```

Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *PredictController.cs* dosyası:

```csharp
public class PredictController : ControllerBase
{

    private readonly PredictionService _predictionService;

    public PredictController(PredictionService predictionService)
    {
        _predictionService = predictionService; //Define prediction service
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }
        return Ok(_predictionService.Predict(input));
    }

}
```

Bağımlılık ekleme erişmenizi denetleyicinin oluşturucusuna geçirerek bu tahmin hizmet atanmasıdır. Ardından, İLETİDE bu denetleyicinin öngörü hizmeti yöntemi tahminlerde bulunabilir ve kullanıcıya geri başarılı olursa sonuçları döndürmek için kullanılıyor.

## <a name="test-web-api-locally"></a>Web API'si yerel olarak test etme

Her şeyi ayarlandıktan sonra uygulama test etme vakti.

1. Uygulamayı çalıştırın.
1. PowerShell'i açın ve bağlantı noktası, bağlantı noktası olduğu aşağıdaki kodu girin. uygulamanızı dinlediği.

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

Başarılı olursa çıktı aşağıdaki metne benzer görünmelidir:

```powershell
Toxic
```

Tebrikler! Ayrıca, bir ASP.NET Core API'si kullanarak internet üzerinden tahminlerde bulunmak üzere modelinizi başarıyla hizmet vermektedir.

## <a name="next-steps"></a>Sonraki Adımlar

- [Azure’a dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)