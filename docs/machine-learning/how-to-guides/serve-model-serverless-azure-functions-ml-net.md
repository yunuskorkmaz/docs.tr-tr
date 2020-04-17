---
title: Modeli Azure İşlevleri’ne dağıtma
description: Azure Fonksiyonlarını kullanarak internet üzerinden tahmin için ML.NET duygu analizi makine öğrenme modeline hizmet edin
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2f340805200a14e0e145ffe1bf20f8059df63555
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608055"
---
# <a name="deploy-a-model-to-azure-functions"></a>Modeli Azure İşlevleri’ne dağıtma

Azure İşlevler sunucusuz bir ortam aracılığıyla HTTP üzerinden öngörüler için önceden eğitilmiş bir ML.NET makine öğrenimi modelini nasıl dağıtılacayacak gerektiğini öğrenin.

> [!NOTE]
> Bu örnek, hizmetin `PredictionEnginePool` önizleme sürümünü çalıştırın.

## <a name="prerequisites"></a>Ön koşullar

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonraki sürüm 15.6 veya daha sonra ".NET Core çapraz platform geliştirme" ve "Azure geliştirme" iş yükleri yüklü.
- [Azure İşlevaraçları](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- Önceden eğitilmiş bir model. Kendi modelinizi oluşturmak veya bu [önceden eğitilmiş duygu analizi makine öğrenme modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirmek için ML.NET Sentiment Analysis [öğreticisini](../tutorials/sentiment-analysis.md) kullanın

## <a name="azure-functions-sample-overview"></a>Azure Fonksiyonları örnek genel bakış

Bu örnek, metnin duyarlılığını olumlu veya negatif olarak kategorilere ayırmak için önceden eğitilmiş bir ikili sınıflandırma modeli kullanan bir **C# HTTP Trigger Azure İşleme uygulamasıdır.** Azure İşlevler, bulutta yönetilen sunucusuz bir ortamda küçük kod parçalarını ölçekte çalıştırmanın kolay bir yolunu sağlar. Bu örneğin kodu GitHub'daki [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) deposunda bulunabilir.

## <a name="create-azure-functions-project"></a>Azure İşlevleri projesi oluşturma

1. Visual Studio 2017'yi açın. Menü çubuğundan**Yeni** > **Proje** **Dosyası'nı** > seçin. Yeni **Proje** iletişim kutusunda, **Bulut** düğümü tarafından izlenen **Visual C#** düğümünü seçin. Ardından **Azure İşlevleri** proje şablonuna katılın. **Ad** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve **ardından Tamam** düğmesini seçin.
1. Yeni **Proje** iletişim kutusunda, proje seçeneklerinin üzerindeki açılır dosyayı açın ve **Azure İşlevleri v2 (.NET Core)** seçeneğini seçin. Ardından, **Http tetikleyici** projesini seçin ve ardından **Tamam** düğmesini seçin.
1. Modelinizi kaydetmek için projenizde *MLModels* adlı bir dizin oluşturun:

    **Çözüm Gezgini'nde,** projenize sağ tıklayın ve**Yeni Klasör** **Ekle'yi** > seçin. "MLModels" yazın ve Enter tuşuna basın.

1. Microsoft.ML **NuGet Paketi** sürüm **1.3.1**yükleyin:

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.

1. **Microsoft.Azure.Functions.Extensions NuGet Paketini Yükleyin:**

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org"yi seçin, Gözat sekmesini seçin, **Microsoft.Azure.Functions.Extensions'ı**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.

1. Microsoft.Extensions.ML **NuGet Paketi** sürümünü **0.15.1 yükleyin:**

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.Extensions.ML**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.

1. **Microsoft.NET.Sdk.Functions NuGet Paketi** sürümünü **1.0.31**yükleyin:

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org"yi seçin, Yüklü sekmesini seçin, **Microsoft.NET.Sdk.Functions'i**arayın, listedeki paketi seçin, Sürüm açılır listesinden **1.0.31'i** seçin ve **Güncelleştir** düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.

## <a name="add-pre-trained-model-to-project"></a>Projeye önceden eğitilmiş modeli ekleme

1. Önceden oluşturulmuş modelinizi *MLModels* klasörüne kopyalayın.
1. Çözüm Gezgini'nde, önceden oluşturulmuş model dosyanıza sağ tıklayın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

## <a name="create-azure-function-to-analyze-sentiment"></a>Duyarlılığı analiz etmek için Azure İşlevi oluşturma

Duyguları tahmin etmek için bir sınıf oluşturun. Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.

1. Yeni **Öğe Ekle** iletişim kutusunda **Azure İşlev'i** seçin ve **Ad** alanını *AnalyzeSentiment.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

1. Yeni **Azure İşlevi** iletişim kutusunda **Http Tetikle'yi**seçin. Ardından **Tamam** düğmesini seçin.

    *AnalyzeSentiment.cs* dosyası kod düzenleyicisinde açılır. AnalyzeSentiment.cs üstüne `using` aşağıdaki ifadeyi *AnalyzeSentiment.cs*ekleyin:

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    Varsayılan olarak, `AnalyzeSentiment` sınıf `static`. Anahtar kelimeyi `static` sınıf tanımından kaldırdıktan emin olun.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Veri modelleri oluşturma

Giriş verileriniz ve öngörüleriniz için bazı sınıflar oluşturmanız gerekir. Projenize yeni bir sınıf ekleyin:

1. Veri modellerinizi kaydetmek için projenizde *Veri Modelleri* adlı bir dizin oluşturun: Çözüm Gezgini'nde, projenize sağ tıklayın ve Yeni Klasör **> ekle'yi**seçin. "Veri Modelleri" yazın ve Enter tuşuna basın.
2. Çözüm Gezgini'nde, *DataModels* dizinini sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.
3. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentData.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

    *SentimentData.cs* dosyası kod düzenleyicisinde açılır. *SentimentData.cs*üst kısmında aşağıdaki ifadesini kullanarak ekleyin:

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Varolan sınıf tanımını kaldırın ve *SentimentData.cs* dosyasına aşağıdaki kodu ekleyin:

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. Çözüm Gezgini'nde, *DataModels* dizinini sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.
5. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentPrediction.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin. kod düzenleyicisinde *SentimentPrediction.cs* dosyası açılır. *SentimentPrediction.cs*üstüne aşağıdaki ifadesini kullanarak ekleyin:

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Varolan sınıf tanımını kaldırın ve *SentimentPrediction.cs* dosyasına aşağıdaki kodu ekleyin:

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction`özellikteki özgün verilere ve model tarafından oluşturulan çıktıya erişim sağlayan devralır. `SentimentData` `SentimentText`

## <a name="register-predictionenginepool-service"></a>Kayıt TahminEnginePool hizmeti

Tek bir tahmin yapmak için, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)bir . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Ayrıca, uygulamanız içinde gerekli olan her yerde bunun bir örneğini oluşturmanız gerekir. Uygulamanız büyüdükçe, bu işlem yönetilemez hale gelebilir. Daha iyi performans ve iş parçacığı güvenliği için, `PredictionEnginePool` uygulamanız boyunca [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) kullanılmak [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) üzere bir nesne oluşturan bağımlılık enjeksiyonu ve hizmetin bir birleşimini kullanın.

Bağımlılık [enjeksiyonu](https://en.wikipedia.org/wiki/Dependency_injection)hakkında daha fazla bilgi edinmek istiyorsanız aşağıdaki bağlantı daha fazla bilgi sağlar.

1. **Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *Startup.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.
1. *Startup.cs*üst kısmında aşağıdaki ifadeleri kullanarak ekleyin:

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. Aşağıdaki ifadeleri kullanarak ifadeleri altında varolan kodu kaldırın ve aşağıdaki kodu ekleyin:

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. Uygulamanın çalıştığı ortamı ve modelin sınıfın içinde bulunduğu dosya yolunu depolamak `Startup` için değişkenleri tanımlayın

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. Bunun altında, `_environment` ve `_modelPath` değişkenlerin değerlerini ayarlamak için bir oluşturucu oluşturun. Uygulama yerel olarak çalışırken, varsayılan ortam *Development*Geliştirme'dir.

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Ardından, hizmeti oluşturucunun `Configure` `PredictionEnginePool` altına kaydetmek için çağrılan yeni bir yöntem ekleyin.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

Yüksek düzeyde, bu kod, uygulama tarafından el ile yapmak zorunda kalmak yerine daha sonra kullanılmak üzere nesneleri ve hizmetleri otomatik olarak başlatir.

Makine öğrenimi modelleri statik değildir. Yeni eğitim verileri kullanılabilir hale geldikçe, model yeniden eğitilir ve yeniden dağıtılır. Uygulamanıza modelin en son sürümünü almanın bir yolu, tüm uygulamayı yeniden dağıtmaktır. Ancak, bu uygulama kapalı kalma süresi tanır. Hizmet, `PredictionEnginePool` uygulamanızı kaldırmadan güncelleştirilmiş bir modeli yeniden yüklemek için bir mekanizma sağlar.

Parametreyi `watchForChanges` `true`ve dosya `PredictionEnginePool` sistemi [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) değişiklik bildirimlerini dinleyen ve dosyada bir değişiklik olduğunda olayları yükselten bir başlat' olarak ayarlayın. Bu, modeli `PredictionEnginePool` otomatik olarak yeniden yüklemesini ister.

`modelName` Model, uygulama başına birden fazla modelin değişiklik üzerine yeniden yüklenebilmeleri için parametre ile tanımlanır.

> [!TIP]
> Alternatif olarak, uzaktan `FromUri` depolanan modeller ile çalışırken yöntemi kullanabilirsiniz. Dosya değiştirilen olayları izlemek `FromUri` yerine, değişiklikler için uzak konumu yoklar. Yoklama aralığı varsayılan olarak 5 dakikadır. Uygulamanızın gereksinimlerine bağlı olarak yoklama aralığını artırabilir veya azaltabilirsiniz. Aşağıdaki kod örneğinde, `PredictionEnginePool` model her dakika belirtilen URI'de depolanır.
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>Modeli işleve yükleyin

*AnalyzeSentiment* sınıfına aşağıdaki kodu ekleyin:

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

Bu kod, `PredictionEnginePool` bağımlılık enjeksiyonu yoluyla elde ettiğiniz işlevin oluşturucuya geçirerek atar.

## <a name="use-the-model-to-make-predictions"></a>Öngörülerde bulunmak için modeli kullanma

*AnalyzeSentiment* sınıfında *Run* yönteminin varolan uygulamasını aşağıdaki kodla değiştirin:

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

`Run` Yöntem yürütüldüğünde, HTTP isteğinden gelen veriler deserialized ve giriş olarak `PredictionEnginePool`kullanılır . Yöntem `Predict` daha sonra `SentimentAnalysisModel` `Startup` sınıfta kayıtlı kullanarak öngörüler yapmak için çağrılır ve başarılı olursa sonuçları kullanıcıya geri döndürür.

## <a name="test-locally"></a>Yerel olarak test edin

Artık her şey ayarlandı, uygulamayı test etme zamanı geldi:

1. Uygulamayı çalıştırma
1. PowerShell'i açın ve kodu uygulamanızın çalıştığı port PORT PORT'un bulunduğu komut istemine girin. Genellikle bağlantı noktası 7071'dir.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Başarılı olursa, çıktı aşağıdaki metne benzer olmalıdır:

    ```powershell
    Negative
    ```

Tebrikler! Azure İşlevi kullanarak internet üzerinden öngörülerde bulunmak için modelinizi başarıyla kullandınız.

## <a name="next-steps"></a>Sonraki Adımlar

- [Azure’a dağıtma](/azure/azure-functions/functions-develop-vs#publish-to-azure)
