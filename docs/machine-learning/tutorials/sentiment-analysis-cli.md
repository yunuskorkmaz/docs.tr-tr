---
title: ML.NET CLI kullanarak yaklaşımı çözümleme
description: Örnek bir veri kümesinden otomatik olarak ml modeli ve ilgili C# kodu oluşturun
author: cesardl
ms.author: cesardl
ms.date: 12/23/2019
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 832124e6d027b240c4d06692ee87c84f57b982d3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243342"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>ML.NET CLI kullanarak yaklaşımı çözümleme

otomatik olarak bir ML.NET modeli ve altta yatan C# kodu oluşturmak için cli ML.NET nasıl kullanacağınızı öğrenin. Veri kümenizi ve uygulamak istediğiniz makine öğrenimi görevini sağlarsınız ve CLI, model oluşturma ve dağıtım kaynak kodunun yanı sıra ikili modeli oluşturmak için AutoML altyapısını kullanır.

Bu öğreticide, aşağıdaki adımları yapacaksınız:
> [!div class="checklist"]
>
> - Verilerinizi seçili makine öğrenimi görevi için hazırlayın
> - CLI'dan 'mlnet otomatik tren' komutunu çalıştırın
> - Kalite metrik sonuçlarını gözden geçirin
> - Uygulamanızdaki modeli kullanmak için oluşturulan C# kodunu anlama
> - Modeli eğitmek için kullanılan oluşturulan C# kodunu keşfedin

> [!NOTE]
> Bu konu, şu anda Önizleme'de bulunan ML.NET CLI aracını ifade eder ve malzeme değişebilir. Daha fazla bilgi için ML.NET sayfasını ziyaret [edin.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)

cli ML.NET ML.NET bir parçasıdır ve ana hedefi başlamak için sıfırdan kodlamak gerekmez, böylece ML.NET öğrenirken .NET geliştiriciler için ML.NET "demokratikleştirmek" tir.

Sağladığınız eğitim veri kümelerini temel alan kaliteli ML.NET modelleri ve kaynak kodu oluşturmak için cli ML.NET herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabilirsiniz.

## <a name="pre-requisites"></a>Ön koşullar

- [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya sonrası
- (İsteğe bağlı) [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)
- [ML.NET CLI](../how-to-guides/install-ml-net-cli.md)

Oluşturulan C# kodu projelerini Visual Studio'dan `dotnet run` veya (.NET Core CLI) çalıştırabilirsiniz.

## <a name="prepare-your-data"></a>Verilerinizi hazırlama

İkili sınıflandırma makinesi öğrenme görevi olan 'Sentiment Analysis' senaryosu için kullanılan varolan bir veri kümesini kullanacağız. Kendi veri kümenizi benzer bir şekilde kullanabilirsiniz ve model ve kod sizin için oluşturulur.

1. UCI Sentiment Etiketli Cümleler dataset zip dosyasını indirin [(aşağıdaki nottaki alıntılara bakın)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve seçtiğiniz herhangi bir klasörde zip'i açın.

    > [!NOTE]
    > Bu öğreticideki veri kümeleri, Kotzias ve ark.'nın 'Derin Özellikleri Kullanarak Gruptan Bireysel Etiketlere' bir veri kümesi ni kullanır. KDD 2015 ve UCI Machine Learning Deposu - Dua, D. ve Karra Taniskidou, E. (2017) ev sahipliği yaptı. UCI Makine Öğrenme Deposuhttp://archive.ics.uci.edu/ml[ ]. Irvine, CA: Kaliforniya Üniversitesi, Bilgi ve Bilgisayar Bilimleri Fakültesi.

2. Dosyayı `yelp_labelled.txt` daha önce oluşturduğunuz herhangi bir `/cli-test`klasöre kopyalayın (örneğin).

3. Tercih ettiğiniz komut istemini açın ve veri kümesi dosyasını kopyaladığınız klasöre geçin. Örneğin:

    ```console
    cd /cli-test
    ```

    Visual Studio Code gibi herhangi bir metin düzenleyicisini `yelp_labelled.txt` kullanarak veri kümesi dosyasını açabilir ve keşfedebilirsiniz. Yapının aşağıdaki leri görebilirsiniz:

    - Dosyanın üstbilgisi yok. Sütundizini kullanırsınız.

    - Sadece iki sütun vardır:

        | Metin (Sütun dizini 0) | Etiket (Sütun dizini 1)|
        |--------------------------|-------|
        | Wow... Burayı çok severdim. | 1 |
        | Kabuk iyi değil. | 0 |
        | Lezzetli değil ve doku sadece kötü oldu. | 0 |
        | ... ÇOK DAHA FAZLA TEKSTİl SATıRLARI... | ... (1 veya 0)... |

    Düzenleyiciden gelen veri kümesi dosyasını kapattığınızdan emin olun.

    Şimdi, bu 'Duygu Analizi' senaryosu için CLI kullanmaya başlamak için hazırsınız.

    > [!NOTE]
    > Bu öğreticiyi bitirdikten sonra, *'İkili Sınıflandırma', 'Çok sınıflı Sınıflandırma' ve 'Regresyon'* ML.NET CLI Preview tarafından desteklenen ML görevlerinden herhangi biri için kullanılmaya hazır oldukları sürece kendi veri kümelerinizi de deneyebilirsiniz.

## <a name="run-the-mlnet-auto-train-command"></a>'mlnet otomatik tren' komutunu çalıştırın

1. Aşağıdaki ML.NET CLI komutunu çalıştırın:

    ```console
    mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    Bu komut ** `mlnet auto-train` komutu**çalıştırın:
    - türünde bir **ML görevi** için**`binary-classification`**
    - veri **kümesi dosyasını `yelp_labelled.txt` ** eğitim ve test veri seti olarak kullanır (dahili olarak CLI çapraz doğrulama kullanır veya biri eğitim, diğeri test etmek için olmak üzere iki veri kümesine böler)
    - tahmin etmek istediğiniz **hedef/hedef sütunun** (genellikle **'etiket'** olarak adlandırılır) **dizin 1'li sütun** olduğu yerde (dizin sıfır tabanlı olduğundan, ikinci sütundur)
    - bu özel veri kümesi dosyasıüstbilgisi olmadığından sütun adları içeren bir **dosya üstbilgisi kullanmaz**
    - deney için **hedeflenen keşif süresi** **10 saniyedir**

    CLI'den aşağıdakilere benzer çıktılar görürsünüz:

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windows"></a>[Windows](#tab/windows)

    ![PowerShell üzerinde ML.NET CLI otomatik tren](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bash"></a>[macOS Bash](#tab/macosbash)

    ![PowerShell üzerinde ML.NET CLI otomatik tren](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    Bu özel durumda, sadece 10 saniye içinde ve sağlanan küçük veri kümesi ile, CLI aracı farklı iç veri dönüşümleri ve algoritma hiper-parametreleri ile algoritma / yapılandırma farklı kombinasyonları dayalı birden çok kez eğitim anlamına gelen oldukça birkaç yineleme çalıştırmak başardı.

    Son olarak, 10 saniye içinde bulunan "en kaliteli" model belirli bir yapılandırma ile belirli bir eğitmen / algoritma kullanarak bir modeldir. Arama süresine bağlı olarak, komut farklı bir sonuç üretebilir. Seçim, `Accuracy`'.

    **Modelin kalite ölçümlerini anlama**

    İkili sınıflandırma modelini değerlendirmek için ilk ve en kolay metrik, anlaşılması kolay olan doğruluktır. "Doğruluk, bir test veri kümesi ile doğru tahminlerin oranıdır.". %100'e (1.00) ne kadar yakınsa o kadar iyi.

    Ancak, özellikle test veri kümesinde etiket (bu durumda 0 ve 1) dengesizse, Doğruluk ölçümü ile ölçmenin yeterli olmadığı durumlar vardır.

    Doğruluk, AUC, AUCPR ve Farklı modelleri değerlendirmek için kullanılan F1 puanı gibi ölçümler hakkında ek ölçümler ve daha **ayrıntılı bilgi** için [ML.NET](../resources/metrics.md)bkz.

    > [!NOTE]
    > Bu çok aynı veri kümesini deneyebilir `--max-exploration-time` ve bu veri kümesi için farklı bir eğitim boru hattı yapılandırması (oldukça küçük, 1000 satır) ile sizin için daha iyi bir "en iyi model" bulacaksınız (örneğin üç dakika, 180 saniye belirtin) için birkaç dakika belirtebilirsiniz.

    Daha büyük veri kümelerini hedefleyen bir "üretime hazır model" olan "en iyi/kaliteli" modeli bulmak için, genellikle veri kümesinin boyutuna bağlı olarak çok daha fazla keşif süresi belirten CLI ile denemeler yapmalısınız. Aslında, çoğu durumda, özellikle veri kümesi satırve sütunlarda büyükse, birden çok saat arama süresi gerekebilir.

1. Önceki komut yürütme aşağıdaki varlıkları oluşturdu:

    - Serileştirilmiş bir model .zip ("en iyi model") kullanıma hazır.
    - C# kodu, oluşturulan modeli çalıştırmak/puanlamak için (Bu modelle son kullanıcı uygulamalarınızda öngörülerde bulunmak için).
    - C# eğitim kodu bu modeli oluşturmak için kullanılır (Öğrenme amaçlı).
    - Tüm yinelemelerin yer verdiği bir günlük dosyası, hiper parametreler ve veri dönüşümleri birleşimi ile denenmiş her algoritma hakkında belirli ayrıntılı bilgilere sahip olarak araştırılmış.

    İlk iki varlık (. Posta dosyası modeli ve C# kodu bu modeli çalıştırmak için) doğrudan son kullanıcı uygulamaları (ASP.NET Core web uygulaması, hizmetler, masaüstü uygulaması, vb) bu oluşturulan ML modeli ile tahminler yapmak için kullanılabilir.

    Üçüncü varlık, eğitim kodu, oluşturulan modeli eğitmek için CLI tarafından ML.NET API kodunun ne ML.NET kullanıldığını gösterir, böylece CLI tarafından hangi özel eğitmen/algoritma ve hiper parametrelerin seçildiğini araştırabilirsiniz.

Numaralandırılmış varlıklar öğreticinin aşağıdaki adımlarında açıklanır.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Öngörülerde bulunmak için modeli çalıştırmak için kullanılacak oluşturulan C# kodunu keşfedin

1. Visual Studio'da (2017 veya 2019) özgün `SampleBinaryClassification` hedef klasörünüzde (öğreticinin `/cli-test`adı geçen) adlı klasörde oluşturulan çözümü açın. Şuna benzer bir çözüm görmeniz gerekir:

    > [!NOTE]
    > Eğitimde Visual Studio'yu kullanmanızı öneririz, ancak oluşturulan C# kodunu (iki proje) herhangi bir metin `dotnet CLI` düzenleyicisi ile keşfedebilir ve oluşturulan konsol uygulamasını macOS, Linux veya Windows makinesiyle çalıştırabilirsiniz.

    ![CLI tarafından oluşturulan VS çözümü](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Serileştirilmiş ML modelini (.zip dosyası) ve veri sınıflarını (veri modelleri) içeren oluşturulan **sınıf kitaplığı,** sınıf kitaplığını doğrudan başvurarak (veya kodu istediğiniz gibi taşıyarak) son kullanıcı uygulamanızda doğrudan kullanabileceğiniz bir şeydir.
    - Oluşturulan **konsol uygulaması** gözden geçirmeniz gereken yürütme kodu içerir ve daha sonra genellikle bu basit kodu (yalnızca birkaç satır) öngörüler yapmak istediğiniz son kullanıcı uygulamanıza taşıyarak 'puanlama kodunu' (tahminleri yapmak için ML modelini çalıştıran kod) yeniden kullanırsınız.

1. Sınıf kitaplığı projesinde **ModelInput.cs** ve **ModelOutput.cs** sınıf dosyalarını açın. Bu sınıfların 'veri sınıfları' veya veri tutmak için kullanılan POCO sınıfları olduğunu görürsünüz. Bu 'ortak kod' ancak veri seti onlarca hatta yüzlerce sütun varsa oluşturulan olması yararlıdır.
    - Sınıf, `ModelInput` veri kümesinden gelen verileri okurken kullanılır.
    - Sınıf `ModelOutput` tahmin sonucu (tahmin verileri) almak için kullanılır.

1. Program.cs dosyasını açın ve kodu keşfedin. Sadece birkaç satırda, modeli çalıştırabilir ve örnek bir tahmin de yapabilirsiniz.

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

    - İlk kod satırı, ML.NET `MLContext` kodu çalıştırdığınızda gereken bir nesne oluşturur.

    - Zaten CLI aracı tarafından sizin için eğitilmiş ve modelin seri içine kaydedilmiş olduğundan kodun ikinci satırı modeli eğitmek gerekmez çünkü yorumlanır. ZIP dosyası. Ancak CLI tarafından *"modelin nasıl eğitildiğini"* görmek istiyorsanız, bu satırı yorumlayabilir ve söz konusu ML modeli için kullanılan eğitim kodunu çalıştırabilirsiniz/hata ayıklamanız olabilir.

    - Üçüncü kod satırında, modeli serileştirilmiş modelden yüklersiniz. Bu modele `mlContext.Model.Load()` giden yolu sağlayarak API ile ZIP dosyası. ZIP dosyası.

    - Dördüncü kod satırında, `PredictionEngine` `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` ösy'yi API ile yükleyin. Tek bir `PredictionEngine` veri örneğini hedefleyen bir tahminde bulunmak istediğinizde nesneye ihtiyacınız vardır (bu durumda, duyarlılığını tahmin etmek için tek bir metin parçası).

    - Beşinci kod satırı, işlevi `CreateSingleDataSample()`çağırarak tahmin için kullanılacak tek örnek *verileri* oluşturduğunuz satırdır. CLI aracı ne tür örnek veri kullanılacağını bilmediğinden, bu işlev içinde veri kümesinin ilk satırını yüklüyor. Ancak, bu durumda, bu `CreateSingleDataSample()` işlevi uygulayan bu basit kodu güncelleştirerek işlevin geçerli uygulaması yerine kendi 'sabit kodlu' verileri de oluşturabilirsiniz:

        ```csharp
        private static ModelInput CreateSingleDataSample()
        {
            ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
            return sampleForPrediction;
        }
        ```

1. Projeyi, veri kümesinin ilk satırından yüklenen özgün örnek verileri kullanarak veya kendi özel sabit kodlanmış örnek verilerinizi sağlayarak çalıştırın. Karşılaştırılabilir bir tahmin almalısınız:

    # <a name="windows"></a>[Windows](#tab/windows)

    F5 (Play tuşu) tuşuna basarak Visual Studio'daki konsol uygulamasını çalıştırın:

    ![PowerShell üzerinde ML.NET CLI otomatik tren](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bash"></a>[macOS Bash](#tab/macosbash)

    Aşağıdaki komutları yazarak konsol uygulamasını komut isteminden çalıştırın:

    ```dotnetcli
    cd SampleBinaryClassification
    cd SampleBinaryClassification.ConsoleApp

    dotnet run
    ```

    ![PowerShell üzerinde ML.NET CLI otomatik tren](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Sabit kodlanmış örnek verileri farklı duygularla diğer cümlelerle değiştirmeyi deneyin ve modelin olumlu veya olumsuz duyguları nasıl öngördüğünü görün.

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Son kullanıcı uygulamalarınızı ML model tahminleri ile aşıla

Modeli son kullanıcı uygulamanızda çalıştırmak ve öngörülerde bulunmak için benzer 'ML model puanlama kodu' kullanabilirsiniz.

Örneğin, bu kodu doğrudan **WPF** ve **WinForms** gibi herhangi bir Windows masaüstü uygulamasına taşıyabilir ve modeli konsol uygulamasında yapılandan aynı şekilde çalıştırabilirsiniz.

Ancak, bir ML modelini çalıştırmak için bu kod satırlarını uygulama şekliniz en iyi duruma getirilmelidir (diğer bir deyişle, modeli .zip dosyasını önbelleğe alın ve bir kez yükleyin) ve özellikle uygulamanızın aşağıdaki bölümde açıklandığı gibi web uygulaması veya dağıtılmış hizmet gibi ölçeklenebilir olması gerekiyorsa, her istekte bunları oluşturmak yerine tekton nesnelere sahip olmalıdır.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Ölçeklenebilir ASP.NET Core web uygulamalarında ve hizmetlerinde ML.NET modelleri çalıştırma (çok iş parçacığı uygulamaları)

Model nesnesinin oluşturulması`ITransformer` (modelin .zip dosyasından yüklenen) `PredictionEngine` ve nesne özellikle ölçeklenebilir web uygulamaları ve dağıtılmış hizmetler üzerinde çalışırken en iyi duruma getirilmelidir. İlk durumda, model nesnesi (`ITransformer`) en iyi duruma getirilmesi basittir. `ITransformer` Nesne iş parçacığı için güvenli olduğundan, modeli bir kez yükleyebilmeniz için nesneyi singleton veya statik nesne olarak önbelleğe alabilirsiniz.

İkinci nesne, `PredictionEngine` nesne için, `PredictionEngine` nesne iş parçacığı güvenli olmadığından, bu nedenle bir ASP.NET Core uygulamasında singleton veya statik nesne olarak bu nesneyi anında olamaz, çünkü o kadar kolay değildir. Bu iş parçacığı güvenli ve ölçeklenebilirlik sorunu derinden bu [Blog Yazısı](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)tartışılır .

Ancak, işler sizin için bu blog yazısı açıklanan ne daha çok daha kolay var. Sizin için daha basit bir yaklaşım üzerinde çalıştık ve uygulama DI hizmetlerine (Bağımlılık Enjeksiyonhizmetleri) kaydederek ve ardından doğrudan kodundan kullanabilirsiniz ASP.NET Core uygulamaları ve hizmetlerinde kolayca kullanabileceğiniz güzel bir **'.NET Çekirdek Entegrasyon Paketi'** oluşturduk. Bunu yapmak için aşağıdaki öğretici ve örnek kontrol edin:

- [Öğretici: Ölçeklenebilir ASP.NET Core web uygulamaları ve WebAPI'lerde ML.NET modelleri çalıştırma](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Örnek: ASP.NET Core WebAPI'de ölçeklenebilir ML.NET modeli](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>"En kaliteli" modeli eğitmek için kullanılan oluşturulan C# kodunu keşfedin

Daha gelişmiş öğrenme amaçları için, cli aracı tarafından oluşturulan modeli eğitmek için kullanılan oluşturulan C# kodunu da keşfedebilirsiniz.

Bu 'eğitim modeli kodu' şu anda `ModelBuilder` bu eğitim kodunu araştırmak böylece oluşturulan özel sınıfta oluşturulur.

Daha da önemlisi, bu özel senaryo için (Sentiment Analysis modeli) oluşturulan eğitim kodunu aşağıdaki öğreticide açıklanan kodla karşılaştırabilirsiniz:

- Karşılaştır: [Öğretici: Bir duygu analizi ikili sınıflandırma senaryosunda ML.NET kullanın.](sentiment-analysis.md)

Seçilen algoritmayı ve ardışık yapı yapılandırmasını öğreticide CLI aracı tarafından oluşturulan kodla karşılaştırmak ilginçtir. Daha iyi modelleri yineleyerek ve aramak için ne kadar zaman harcadığınıza bağlı olarak, seçilen algoritma belirli hiper parametreleri ve ardışık yapı yapılandırmasıyla birlikte farklı olabilir.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Verilerinizi seçili ML görevi (çözülmesi gereken sorun) için hazırlayın
> - CLI aracında 'mlnet otomatik tren' komutunu çalıştırın
> - Kalite metrik sonuçlarını gözden geçirin
> - Modeli çalıştırmak için oluşturulan C# kodunu anlama (Son kullanıcı uygulamanızda kullanılacak kod)
> - "En kaliteli" modeli (Öğrenme amaçlı) eğitmek için kullanılan oluşturulan C# kodunu keşfedin

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLI ile model eğitimini otomatikleştirin](../automate-training-with-cli.md)
- [Öğretici: Ölçeklenebilir ASP.NET Core web uygulamaları ve WebAPI'lerde ML.NET modelleri çalıştırma](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Örnek: ASP.NET Core WebAPI'de ölçeklenebilir ML.NET modeli](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [ML.NET CLI otomatik tren komutu başvuru kılavuzu](../reference/ml-net-cli-reference.md)
- [ML.NET CLI'de telemetri](../resources/ml-net-cli-telemetry.md)
