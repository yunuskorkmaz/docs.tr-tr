---
title: 'Öğretici: Duyarlılığı analiz et - ikili sınıflandırma'
description: Bu öğretici, web sitesi yorumlarından duyguları sınıflandıran ve uygun eylemi yapan bir Razor Pages uygulamasını nasıl oluşturabileceğinizi gösterir. İkili duygu sınıflandırıcı Visual Studio Model Builder kullanır.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 3419afb36d73599b8fdb0417a8c0cc4057f60089
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187628"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>Öğretici: ML.NET Model Builder kullanarak bir web uygulamasında web sitesi yorumlarının duyarlılığını analiz edin

Bir web uygulaması içinde gerçek zamanlı olarak yorumlardan duyguları analiz etmeyi öğrenin.

Bu öğretici, web sitesi yorumlarından gelen duyguları gerçek zamanlı olarak sınıflandıran bir ASP.NET Core Razor Pages uygulamasını nasıl oluşturabileceğinizi gösterir.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
>
> - ASP.NET Core Razor Pages uygulaması oluşturma
> - Verileri hazırlama ve anlama
> - Bir senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Öngörüler için modeli kullanma

> [!NOTE]
> Model Oluşturucu şu anda Önizleme'de.

Bu öğreticinin kaynak kodunu [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) deposunda bulabilirsiniz.

## <a name="pre-requisites"></a>Ön koşullar

Ön koşul ve yükleme yönergelerinin listesi için [Model Oluşturucu yükleme kılavuzunu ziyaret edin.](../how-to-guides/install-model-builder.md)

## <a name="create-a-razor-pages-application"></a>Jilet Sayfaları uygulaması oluşturma

1. Core **Razor Pages Uygulaması ASP.NET**oluşturun.

    1. Visual Studio'yu açın ve menü çubuğundan **Dosya > Yeni > Projesi'ni** seçin.
    1. Yeni Proje iletişim kutusunda, **Web** düğümü tarafından izlenen **Visual C#** düğümünü seçin.
    1. Ardından **ASP.NET Çekirdek Web Uygulaması** proje şablonuna gidin.
    1. **Ad** metin kutusuna "SentimentRazor" yazın.
    1. Çözüm **ve projeyi aynı dizindeki yerleştir** çözümve proje **işaretsiz** olduğundan emin olun (VS 2019) veya **çözüm için create directory** (VS 2017) **işaretlenir.**
    1. **Tamam** düğmesini seçin.
    1. Farklı ASP.NET çekirdek projeleri görüntüleyen pencerede **Web Uygulaması'nı** seçin ve ardından **Tamam** düğmesini seçin.

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

[Vikipedi detoks dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)indirin. Web sayfası açıldığında, sayfaya sağ tıklayın, **Farklı Kaydet'i** seçin ve dosyayı bilgisayarınızın herhangi bir yerine kaydedin.

*wikipedia-detox-250-line-data.tsv* veri kümesindeki her satır, Wikipedia'daki bir kullanıcı tarafından bırakılan farklı bir incelemeyi temsil eder. İlk sütun metnin duyarlılığını temsil eder (0 toksik değildir, 1 zehirlidir) ve ikinci sütun kullanıcı tarafından bırakılan yorumu temsil eder. Sütunlar sekmelerle ayrılır. Veriler aşağıdaki gibi görünür:

| Yaklaşım | SentimentText |
| :---: | :---: |
1 | == RUDE == Dostum, o carl resmini geri yükle, yoksa kabasın.
1 | == Tamam! == IM WILD ONES WIKI SONRA VANDALIZE OLACAK!!!
0 | Umarım yardımı olur.

## <a name="choose-a-scenario"></a>Bir senaryo seçin

![Model Oluşturucu sihirbazı Visual Studio'da](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Modelinizi eğitmek için Model Builder tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir.

1. **Solution Explorer'da** *SentimentRazor* projesine sağ tıklayın ve**Machine Learning** **Ekle'yi** > seçin.
1. Bu örnek için, senaryo duygu analizidir. Model Oluşturucu aracının *senaryo* adımında, **Duyarlılık Analizi** senaryosunu seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model Oluşturucu, iki kaynaktan, bir SQL Server `csv` veritabanından veya yerel bir dosyadan veya `tsv` biçimdeki verileri kabul eder.

1. Model Oluşturucu aracının veri adımında, veri kaynağı açılır tarafından **Dosya'yı** seçin.
1. Dosya metin kutusunu **seç'in** yanındaki düğmeyi seçin ve *wikipedia-detoks-250-line-data.tsv* dosyasına göz atmak ve seçmek için Dosya Gezgini'ni kullanın.
1. Sütundaki **Duygu'yu** seçin ve açılır düşüşü **tahmin edin (Etiket)** yazın.
1. **Giriş Sütunları (Özellikler)** açılır açılır açılır için varsayılan değerleri bırakın.
1. Model Oluşturucu aracında bir sonraki adıma geçmek için **Tren** bağlantısını seçin.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğreticide duygu analizi modelini eğitmek için kullanılan makine öğrenme görevi ikili sınıflandırmadır. Model eğitim işlemi sırasında Model Builder, veri setiniz için en iyi performans gösteren modeli bulmak için farklı ikili sınıflandırma algoritmaları ve ayarları kullanarak ayrı modeller eğitir.

Modelin eğitilmesi için gereken süre veri miktarıyla orantılıdır. Model Oluşturucu, veri kaynağınızın boyutuna bağlı **olarak, eğitme Süresi (saniye)** için varsayılan bir değer seçer.

1. Model Oluşturucu, **(saniye) eğitmek için Zamanın** değerini 10 saniyeye ayarlasa da, bunu 30 saniyeye yükseltin. Daha uzun bir süre için eğitim Model Builder algoritmaları ve en iyi modeli arama parametrelerinin kombinasyonu daha fazla sayıda keşfetmek için izin verir.
1. **Start Training'i**seçin.

    Eğitim süreci boyunca, ilerleme verileri tren `Progress` adımı bölümünde görüntülenir.

    - Durum, eğitim sürecinin tamamlanma durumunu görüntüler.
    - En iyi doğruluk, Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren modelin doğruluğunu görüntüler. Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin ettiği anlamına gelir.
    - En iyi algoritma, Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren algoritmanın adını görüntüler.
    - Son algoritma, modeli eğitmek için Model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.

1. Eğitim tamamlandıktan sonra, bir sonraki adıma geçmek için **değerlendirme** bağlantısını seçin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Eğitim adımının sonucu en iyi performansa sahip bir model olacaktır. Model Oluşturucu aracının değerlendirme adımında, çıkış bölümü, **Best Model** Girişinde en iyi performans gösteren model tarafından kullanılan algoritmayı ve En İyi **Model Doğruluğu'ndaki**ölçümleri içerecektir. Ayrıca, en iyi beş modeli ve bunların ölçümlerini içeren bir özet tablo.

Doğruluk ölçümlerinizden memnun değilseniz, model doğruluğunu geliştirmeyi denemenin ve geliştirmenin bazı kolay yolları, modeli eğitmek veya daha fazla veri kullanmak için gereken süreyi artırmakiçindir. Aksi takdirde, Model Oluşturucu aracında son adıma geçmek için **kod** bağlantısını seçin.

## <a name="add-the-code-to-make-predictions"></a>Tahminlerde bulunmak için kodu ekleme

Eğitim süreci sonucunda iki proje oluşturulacaktır.

### <a name="reference-the-trained-model"></a>Eğitimli modele başvurun

1. Model Oluşturucu aracının *kod* adımında, çözüme otomatik oluşturulan projeleri eklemek için **Projeler Ekle'yi** seçin.

    Çözüm Gezgini'nde **Solution Explorer**aşağıdaki projeler görünmelidir:

    - *SentimentRazorML.ConsoleApp*: Model eğitimi ve tahmin kodunu içeren bir .NET Core Console uygulaması.
    - *SentimentRazorML.Model*: Giriş ve çıktı modeli verilerinin şemalarının yanı sıra eğitim sırasında en iyi performans gösteren modelin kaydedilmiş sürümünü tanımlayan veri modellerini içeren bir .NET Standart sınıf kitaplığı.

    Tahminler *sentimentrazor* web uygulaması yerine konsolda yapılacaktır, çünkü bu öğretici için, sadece *SentimentRazorML.Model* proje kullanılır. *SentimentRazorML.ConsoleApp* puanlama için kullanılmayacak olsa da, daha sonra yeni veriler kullanarak modeli yeniden eğitmek için kullanılabilir. Yeniden eğitim olsa bu öğretici kapsamı dışındadır.

### <a name="configure-the-predictionengine-pool"></a>PredictionEngine havuzunu yapılandırın

Tek bir tahmin yapmak için, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)bir . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Ayrıca, uygulamanız içinde gerekli olan her yerde bunun bir örneğini oluşturmanız gerekir. Uygulamanız büyüdükçe, bu işlem yönetilemez hale gelebilir. Daha iyi performans ve iş parçacığı güvenliği için, `PredictionEnginePool` uygulamanız boyunca [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) kullanılmak [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) üzere bir nesne oluşturan bağımlılık enjeksiyonu ve hizmetin bir birleşimini kullanın.

1. *Microsoft.Extensions.ML* NuGet paketini yükleyin:

    1. **Çözüm Gezgini'nde**projeyi sağ tıklatın ve **NuGet Paketlerini Yönet'i**seçin.
    1. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin.
    1. **Gözat** sekmesini seçin ve **Microsoft.Extensions.ML**arayın.
    1. Listedeki paketi seçin ve **Yükle** düğmesini seçin.
    1. **Değişiklikleri Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin
    1. Listelenen paketlerin lisans koşullarını kabul **ederseniz, Lisans Kabul** iletişim kutusundaki **I Kabul** düğmesini seçin.

1. *SentimentRazor* projesindeki *Startup.cs* dosyasını açın.
1. *Microsoft.Extensions.ML* NuGet paketi ve *SentimentRazorML.Model* projesine atıfta bulunmak için aşağıdaki ifadeleri ekleyin:

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. Eğitilen model dosyasının konumunu depolamak için genel bir değişken oluşturun.

    ```csharp
    private readonly string _modelPath;
    ```

1. Model dosyası, uygulamanızın derleme dosyalarının yanında yapı dizininde depolanır. Erişimi kolaylaştırmak için, yöntemden `GetAbsolutePath` `Configure` sonra çağrılan bir yardımcı yöntemi oluşturun

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. 'yi `GetAbsolutePath` `Startup` ayarlamak için sınıf oluşturucudaki yöntemi `_modelPath`kullanın.

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. `ConfigureServices` Uygulamanız `PredictionEnginePool` için yöntemi yapılandırın:

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>Duyarlılık analizi işleyicisi oluşturma

Tahminler uygulamanın ana sayfası içinde yapılacaktır. Bu nedenle, kullanıcı girişi alır ve `PredictionEnginePool` bir tahmin dönmek için kullanan bir yöntem eklenmesi gerekir.

1. *Sayfalar* dizininde bulunan *Index.cshtml.cs* dosyasını açın ve aşağıdaki ifadeleri ekleyin:

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    `Startup` Sınıfta `PredictionEnginePool` yapılandırılan kullanımı için, kullanmak istediğiniz modelin oluşturucuiçine enjekte etmek zorunda.

1. `IndexModel` Sınıfın içine `PredictionEnginePool` başvurmak için bir değişken ekleyin.

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. `IndexModel` Sınıfta bir oluşturucu oluşturun ve `PredictionEnginePool` hizmeti ona enjekte edin.

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. Web sayfasından alınan kullanıcı `PredictionEnginePool` girişinden öngörüler yapmak için bir yöntem işleyicisi oluşturun.

    1. Yöntemin `OnGet` altında, yeni bir yöntem oluşturmak`OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. Yöntemin `OnGetAnalyzeSentiment` içinde, kullanıcıdan giriş boş veya null ise *Nötr* duyarlılığı döndürün.

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. Geçerli bir giriş göz önüne alındığında, yeni bir örnek `ModelInput`oluşturun.

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. Duyguları `PredictionEnginePool` tahmin etmek için kullan.

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. Aşağıdaki kodla `bool` öngörülen değeri toksik veya toksik olmayan bir değere dönüştürün.

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. Son olarak, duyguları web sayfasına geri döndürün.

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>Web sayfasını yapılandırma

Döndürülen `OnGetAnalyzeSentiment` sonuçlar `Index` web sayfasında dinamik olarak görüntülenir.

1. *Pages* dizinindeki *Index.cshtml* dosyasını açın ve içeriğini aşağıdaki kodla değiştirin:

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. Ardından, *wwwroot\css* dizininde *site.css* sayfasının sonuna css stil kodu ekleyin:

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. Bundan sonra, web sayfasından `OnGetAnalyzeSentiment` işleyiciye giriş göndermek için kod ekleyin.

    1. *wwwroot\js* dizininde bulunan *site.js* dosyasında, `OnGetAnalyzeSentiment` işleyiciye `getSentiment` kullanıcı girişi yle GET HTTP isteği nde bulunmak için çağrılan bir işlev oluşturun.

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. Bunun altında, duyarlılık `updateMarker` tahmin edildiği gibi web sayfasında işaretçinin konumunu dinamik olarak güncelleştirmek için çağrılan başka bir işlev ekleyin.

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. Kullanıcıdan giriş almak `updateSentiment` için çağrılan bir olay işleyicisi `OnGetAnalyzeSentiment` işlevi oluşturun, `getSentiment` işlevi kullanarak işleve gönderin ve işaretçiyi `updateMarker` işlek ile güncelleştirin.

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. Son olarak, olay işleyicisini kaydedin `textarea` ve `id=Message` öznitelik ile öğeye bağla.

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamanız ayarlandığına göre, tarayıcınızda başlatılması gereken uygulamayı çalıştırın.

Uygulama başlatıldığında, *Model Oluşturucu girin serin!* metin alanına. Görüntülenen öngörülen duyarlılık *Toksik olmamalıdır.*

![Öngörülen duyarlılık penceresi ile çalışan pencere](./media/sentiment-analysis-model-builder/web-app.png)

Model Oluşturucu'nun oluşturduğu projeleri başka bir çözüm içinde daha sonra göndermeniz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` gerekiyorsa, bunları dizinin içinde bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - ASP.NET Core Razor Pages uygulaması oluşturma
> - Verileri hazırlama ve anlama
> - Bir senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Öngörüler için modeli kullanma

### <a name="additional-resources"></a>Ek Kaynaklar

Bu eğitimde bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:

- [Model Oluşturucu Senaryolar](../automate-training-with-model-builder.md#scenarios)
- [İkili Sınıflandırma](../resources/glossary.md#binary-classification)
- [İkili Sınıflandırma Modeli Ölçümleri](../resources/metrics.md#evaluation-metrics-for-binary-classification)
