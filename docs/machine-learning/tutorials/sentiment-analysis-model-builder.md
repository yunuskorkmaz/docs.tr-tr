---
title: 'Öğretici: Yaklaşım-ikili sınıflandırmayı çözümle'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir Razor Pages uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio 'da model Oluşturucu kullanır.
ms.date: 09/13/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6184e097daf4604173db9e2a34606e68eb0fdc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054323"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>Öğretici: ML.NET model Oluşturucu kullanarak Web uygulamasındaki Web sitesindeki açıklamaları çözümleme

Bir Web uygulamasının içinde gerçek zamanlı açıklamalardan yaklaşımı çözümleme hakkında bilgi edinin.

Bu öğreticide, Web sitesi açıklamalarından gerçek zamanlı olarak yaklaşım sınıflandıran bir ASP.NET Core Razor Pages uygulamasının nasıl oluşturulacağı gösterilmektedir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:

> [!div class="checklist"]
> * ASP.NET Core Razor Pages uygulaması oluşturma
> * Verileri hazırlama ve anlama
> * Senaryo seçin
> * Verileri yükleme
> * Modeli eğitme
> * Modeli değerlendirme
> * Tahmin için modeli kullanma

> [!NOTE]
> Model Oluşturucu Şu anda önizleme aşamasındadır.

Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples) deposunda bulabilirsiniz.

## <a name="pre-requisites"></a>Ön koşullar

Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.

## <a name="create-a-razor-pages-application"></a>Razor Pages uygulaması oluşturma

1. ASP.NET Core bir **Razor Pages uygulaması**oluşturun.

    1. Visual Studio 'Yu açın ve menü çubuğundan **dosya > yeni > projesi** öğesini seçin. 
    1. Yeni proje iletişim kutusunda, **Visual C#**  düğümünü ve ardından **Web** düğümünü seçin. 
    1. **ASP.NET Core Web uygulaması** proje şablonunu seçin. 
    1. **Ad** metin kutusuna "SentimentRazor" yazın.
    1. **Çözüm için dizin oluşturma** onay kutusu varsayılan olarak denetlenmelidir. Böyle bir durum söz konusu değilse, kontrol edin. 
    1. **Tamam** düğmesini seçin.
    1. Pencerede farklı ASP.NET Core proje türlerini görüntüleyen **Web uygulaması** ' nı seçin ve ardından **Tamam** düğmesini seçin.

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

[Vikipedi Detox veri kümesini](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)indirin. Web sayfası açıldığında, sayfaya sağ tıklayın, **farklı kaydet** ' i seçin ve dosyayı bilgisayarınızda herhangi bir yere kaydedin. 

*Vivtox-250-Line-Data. tsv* veri kümesindeki her satır, visede bir kullanıcı tarafından bırakılan farklı bir gözden geçirmeyi temsil eder. İlk sütun metnin (0-Toxic, 1 ' in Toxic) yaklaşımını temsil eder ve ikinci sütun Kullanıcı tarafından bırakılan yorumu temsil eder. Sütunlar sekmelerle ayrılır. Veriler aşağıdaki gibi görünür:

| Yaklaşım | Sentimentmetni |
| :---: | :---: |
1\. | = = İşlenmemiş = = dude, o Carl resmini geri yüklemeniz veya başka bir şey yapmanız gerekir.
1\. | = = TAMAM! = = IM, DAHA SONRA BIR WIKI 'YI DAHA SONRA!!!
0 | Bunu umuyoruz.

## <a name="choose-a-scenario"></a>Senaryo seçin

![](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir. 

1. **Çözüm Gezgini**, *SentimentRazor* projesine sağ tıklayın ve**Machine Learning** **Ekle** > ' yi seçin.
1. Bu örnek için senaryo, yaklaşım analiziydi. Model Oluşturucu aracının *senaryo* adımında **yaklaşım Analizi** senaryosunu seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model Oluşturucu iki kaynaktan (bir SQL Server veritabanı ya da yerel bir dosya `csv` ) veya `tsv` biçimdeki verileri kabul eder.

1. Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden **Dosya** ' yı seçin.
1. **Dosya seçin** metin kutusunun yanındaki düğmeyi seçin ve dosya Gezgini 'ni kullanarak, *vibtox-250-Line-Data. tsv* dosyasına gidin ve seçin.
1. Açılan menüyü **tahmin etmek Için etiket veya sütundaki** **yaklaşımı seçin**
1. Model Oluşturucu aracında bir sonraki adıma geçmek için **eğitme** bağlantısını seçin.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğreticide fiyat tahmin modelini eğitmek için kullanılan makine öğrenimi görevi ikili sınıflandırmasıdır. Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı ikili sınıflandırma algoritmalarını ve ayarlarını kullanarak modelleri ayrı ayrı işler.

Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı. Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer. 

1. Model Oluşturucu değeri, " **saniye)** ila 10 saniye arasında bir süre olarak ayarlasa da, 30 saniyeye yükseltin. Daha uzun bir süre için eğitim, model oluşturucunun en iyi modeli aramada daha fazla sayıda algoritmaların ve parametrelerin birleşimini keşfetmesine olanak tanır.
1. **Eğitimi Başlat**' ı seçin.

    Eğitim süreci boyunca, ilerleme verileri eğitme adımının `Progress` bölümünde görüntülenir.

    - Durum, eğitim sürecinin tamamlanma durumunu görüntüler.
    - En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir. Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.
    - En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.
    - Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.

1. Eğitim tamamlandıktan sonra bir sonraki adıma geçmek için bağlantıyı **değerlendir** ' i seçin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır. Model Oluşturucu aracının değerlendir adımında, çıkış bölümü en iyi **model girişinde en** iyi işlem modeli tarafından kullanılan algoritmayı **(RKARE)** içerir. Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu.

Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu denemeye yönelik bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır. Aksi takdirde, model Oluşturucu aracında son adıma geçmek için **kod** bağlantısını seçin.

## <a name="add-the-code-to-make-predictions"></a>Tahminleri yapmak için kodu ekleyin

Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.

### <a name="reference-the-trained-model"></a>Eğitilen modele başvur

1. Model Oluşturucu aracının *kod* adımında, otomatik olarak oluşturulan projeleri çözüme eklemek Için **Proje Ekle** ' yi seçin.

    Aşağıdaki projeler **Çözüm Gezgini**görünmelidir:

    - *SentimentRazorML. ConsoleApp*: Model eğitimi ve tahmin kodunu içeren bir .NET Core konsol uygulaması.
    - *SentimentRazorML. model*: Eğitim sırasında en iyi gerçekleştirme modelinin kalıcı sürümü ve giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini içeren .NET Standard sınıf kitaplığı.

    Bu öğretici için, *SentimentRazorML. model* projesi yalnızca, tahmine dayalı olarak konsolu yerine *SentimentRazor* Web uygulamasında yapılabilmesi için kullanılır. *SentimentRazorML. ConsoleApp* , Puanlama için kullanılmayacak olsa da, daha sonra yeni verileri kullanarak modeli yeniden eğitebilmek için kullanılabilir. Yeniden eğitim, Bu öğreticinin kapsamı dışındadır.

1. Razor Pages uygulamanızın içinde eğitilen modeli kullanmak için, *SentimentRazorML. model* projesine bir başvuru ekleyin.

    1. **SentimentRazor** projesi öğesine sağ tıklayın. 
    1. **> başvuru Ekle**' yi seçin. 
    1. **Projeler > çözüm** düğümünü seçin ve listeden **SentimentRazorML. model** projesini kontrol edin.
    1. **Tamam**’ı seçin.

### <a name="configure-the-predictionengine-pool"></a>PredictionEngine havuzunu yapılandırma

Tek bir tahmin yapmak için kullanın [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). Uygulamanızda kullanabilmeniz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, gerektiğinde oluşturmanız gerekir. Bu durumda, dikkate alınması gereken en iyi yöntem bağımlılık ekleme yöntemidir.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir. Gelişmiş performans ve iş parçacığı güvenliği için, uygulama `PredictionEnginePool` kullanımı için `PredictionEngine` bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) nesne oluşturan hizmetini kullanın. [ASP.NET Core içinde nesne havuzları `PredictionEngine` oluşturma ve kullanma](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)hakkında daha fazla bilgi edinmek için aşağıdaki blog gönderisini okuyun. 

1. *Microsoft.Extensions.ml* NuGet paketini yükler:

    1. **Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. 
    1. Paket kaynağı olarak "nuget.org" öğesini seçin. 
    1. **Araştır** sekmesini seçin ve **Microsoft.Extensions.ml**için arama yapın. 
    1. Listeden paketi seçin ve ardından **Install** düğmesini seçin. 
    1. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin
    1. Listelenen paketlerin lisans koşullarını kabul ediyorsanız, **Lisans kabulü** Iletişim kutusunda **kabul ediyorum** düğmesini seçin. 

1. *SentimentRazor* projesindeki *Startup.cs* dosyasını açın.
1. *Microsoft.Extensions.ml* NuGet paketini ve *SentimentRazorML. model* projesine başvurmak için aşağıdaki using deyimlerini ekleyin:

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L12-L14)]        

1. Eğitilen model dosyasının konumunu depolamak için genel bir değişken oluşturun.

    [!code-csharp [ModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L20)]

1. Model dosyası, uygulamanızın derleme dosyalarının yanı sıra derleme dizininde depolanır. Daha kolay erişim sağlamak için, `GetAbsolutePath` `Configure` yönteminden sonra adlı bir yardımcı yöntem oluşturun

    [!code-csharp [GetAbsolutePathMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L66-L73)]

1. Öğesini ayarlamak için `Startup` `GetAbsolutePath` sınıf`_modelPath`oluşturucusunda metodunu kullanın.

    [!code-csharp [InitModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L25)]

1. `ConfigureServices` Yöntemi için `PredictionEnginePool` uygulamanızı için yapılandırın:

    [!code-csharp [InitPredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L42)]

### <a name="create-sentiment-analysis-handler"></a>Yaklaşım Analizi işleyicisi oluşturma

Tahmine dayalı, uygulamanın ana sayfasında yapılır. Bu nedenle, Kullanıcı girişini alan ve bir tahmin eklenmesi `PredictionEnginePool` için kullanması gereken bir yöntem.

1. *Pages* dizininde bulunan *Index.cshtml.cs* dosyasını açın ve aşağıdaki using deyimlerini ekleyin:

    [!code-csharp [IndexUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L7-L8)]

    `PredictionEnginePool` Sınıfında yapılandırılan`Startup` ' ı kullanmak için, onu kullanmak istediğiniz modelin oluşturucusuna eklemek gerekir. 

1. `PredictionEnginePool` Sınıfının içine başvurmak için bir değişken ekleyin. `IndexModel`

    [!code-csharp [PredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L14)]

1. `IndexModel` Sınıfında bir Oluşturucu oluşturun ve `PredictionEnginePool` hizmeti ona ekleyin.

    [!code-csharp [IndexConstructor](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L16-L19)]

1. Web sayfasından alınan Kullanıcı girişinden tahminleri yapmak `PredictionEnginePool` için öğesini kullanan bir yöntem işleyicisi oluşturun.

    1. `OnGet` Yönteminin altında, adlı yeni bir yöntem oluşturun`OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. Yöntemi içinde, kullanıcının girişi boş veya null olduğunda nötr yaklaşım döndürün. `OnGetAnalyzeSentiment`

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L28)] 
    
    1. Geçerli bir giriş verildiğinde yeni bir örneğini `ModelInput`oluşturun. 

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L29)] 

    1. Yaklaşımı tahmin `PredictionEnginePool` etmek için kullanın.

        [!code-csharp [MakePrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L30)] 

    1. Tahmin `bool` edilen değeri, aşağıdaki kodla birlikte Toxic öğesine dönüştürün.

        [!code-csharp [ConvertPrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L31)]

    1. Son olarak, yaklaşımı Web sayfasına geri döndürün.

        [!code-csharp [ReturnSentiment](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L32)]

### <a name="configure-the-web-page"></a>Web sayfasını yapılandırma

Tarafından döndürülen sonuçlar, `OnGetAnalyzeSentiment` `Index` Web sayfasında dinamik olarak görüntülenir.

1. *Pages* dizinindeki *Index. cshtml* dosyasını açın ve içeriğini şu kodla değiştirin: 

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. Ardından, *wwwroot\css* dizinindeki *site. css* sayfasının sonuna CSS stil oluşturma kodu ekleyin:

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. Bundan sonra, Web sayfasından `OnGetAnalyzeSentiment` işleyiciye giriş göndermek için kod ekleyin.

    1. *Wwwroot\js* dizininde bulunan *site. js* dosyasında, `OnGetAnalyzeSentiment` işleyiciye Kullanıcı girişiyle bir http isteği almak için `getSentiment` adlı bir işlev oluşturun.

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. Bunun altında, yaklaşım tahmin edildiğinde Web `updateMarker` sayfasındaki işaretin konumunu dinamik olarak güncelleştirmek için adlı başka bir işlev ekleyin.

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. Kullanıcıdan girişi almak `updateSentiment` için çağrılan bir olay işleyici işlevi oluşturun, `getSentiment` işlevi kullanarak `OnGetAnalyzeSentiment` işleve gönderin ve işaretleyiciyi `updateMarker` işlevle güncelleştirin.

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. Son olarak, olay işleyicisini kaydedin ve `textarea` `id=Message` özniteliği ile öğesine bağlayın.

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamanız ayarlandığına göre, tarayıcınızda başlatması gereken uygulamayı çalıştırın.

Uygulama başlatıldığında, *model Oluşturucu* seyrek erişimli yazın! metin alanına. Görünen tahmini yaklaşım, *Toxic*olmamalıdır.

![](./media/sentiment-analysis-model-builder/web-app.png)

Model Oluşturucu tarafından oluşturulan projelere daha sonra başka bir çözümün içinde başvurulmaları gerekiyorsa, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizin içinde bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> * ASP.NET Core Razor Pages uygulaması oluşturma
> * Verileri hazırlama ve anlama
> * Senaryo seçin
> * Verileri yükleme
> * Modeli eğitme
> * Modeli değerlendirme
> * Tahmin için modeli kullanma

### <a name="additional-resources"></a>Ek Kaynaklar

Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:

- [Model Oluşturucu senaryoları](../automate-training-with-model-builder.md#scenarios)
- [İkili sınıflandırma](../resources/glossary.md#binary-classification)
- [İkili sınıflandırma modeli ölçümleri](../resources/metrics.md#metrics-for-binary-classification)