---
title: ML.NET CLI kullanarak bir ikili dosya sınıflandırıcı otomatik oluştur
description: Otomatik olarak ML model oluşturmak ve ilgili C# bir örnek veri kodu
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 2679df0317fede9fa5f3885831c65bd87a14981a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960405"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a>CLI kullanarak bir ikili dosya sınıflandırıcı otomatik oluştur

ML.NET CLI otomatik olarak bir ML.NET modeli oluşturmak için kullanmayı öğrenin ve arka plandaki C# kod. Kümenizi ve makine öğrenimi uygulamak istediğiniz görev sağlar ve CLI ikili modelin yanı sıra model oluşturma ve dağıtım kaynak kodunu oluşturmak için AutoML altyapısı kullanır.

Bu öğreticide, aşağıdakileri yapar:
> [!div class="checklist"]
> * Seçilen makine öğrenimi görev için verilerinizi hazırlayın
> * CLI üzerinden 'mlnet otomatik train' komutunu çalıştırın
> * Kalite Ölçüm sonuçlarını gözden geçirin
> * Oluşturulan anlamak C# modelini kullanmak için kodu
> * Oluşturulan keşfedin C# modeli eğitmek için kullanılan kod

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET CLI aracını ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

ML.NET CLI ML.NET bir parçasıdır ve "ML.NET .NET geliştiricileri için kullanmaya başlamak için sıfırdan kodu zorunda kalmazsınız ML.NET öğrenme, herkesin için" ana hedefi sağlamaktır.

ML.NET CLI bir komut istemi (Windows, Mac veya Linux) kaliteli ML.NET modelleri ve sağladığınız eğitim veri kümeleri üzerinde temel kaynak kodunu üretmek için çalıştırabilirsiniz.

## <a name="pre-requisites"></a>Ön koşullar

- [.NET core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya üzeri
- (İsteğe bağlı) [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)
- [ML.NET CLI](../how-to-guides/install-ml-net-cli.md)

Çalıştırabilir ya da oluşturulan C# kod projelerini Visual Studio'dan veya ile `dotnet run` (.NET Core CLI).

## <a name="prepare-your-data"></a>Verilerinizi hazırlama

İkili sınıflandırma machine learning görev 'Yaklaşım analizi' senaryosu için kullanılan mevcut bir veri kümesini kullanmak için kullanacağız. Benzer şekilde kendi kümenizi kullanabilirsiniz ve model ve kod sizin için oluşturulur.

1. İndirme [UCI yaklaşım cümleler etiketli veri kümesini zip dosyası (alıntıları aşağıdaki nota bakın)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve seçtiğiniz herhangi bir klasörde sıkıştırmasını açın.

    > [!NOTE]
    > Veri kümeleri Bu öğreticide bir veri kümesinden 'kaynak grubuna ayrıntılı özelliklerini kullanarak her bir etiketi' Kotzias tarayıcılarınızda. 2015 ve barındırılan KDD UCI Machine Learning deposu - Dua, d ve Karra Taniskidou, e (2017). UCI Makine deposu [http://archive.ics.uci.edu/ml]. Irvine, CA: California Üniversitesi, okul bilgi ve bilgisayar Bilimine.

2. Kopyalama `yelp_labelled.txt` dosyasını daha önce oluşturduğunuz herhangi bir klasöre (örneğin `/cli-test`).

3. Tercih edilen bir komut istemi açın ve veri kümesi dosyasını kopyaladığınız klasöre gidin. Örneğin:

    ```console
    > cd /cli-test
    ```

    Visual Studio Code gibi herhangi bir metin düzenleyicisi kullanarak, açık keşfedin ve `yelp_labelled.txt` veri kümesi dosyası. Bir yapı olduğunu görebilirsiniz:

    - Üst bilgi dosyası vardır. Sütun dizini kullanır.

    - Yalnızca iki sütun vardır:

        | Metin (sütun dizini 0) | Etiket (sütun dizini 1)|
        |--------------------------|-------|
        | WOW... Burası sevdiği. | 1. |
        | Kabuk iyi değil. | 0 |
        | Değil tasty ve doku yalnızca sinir. | 0 |
        | ... ÇOK FAZLA METİN SATIR... | ... (1 veya 0)... |

    Veri kümesi dosyası düzenleyicisinden kapatmak emin olun.

    Şimdi, bu 'Yaklaşım analizi' senaryosu için CLI'yı kullanmaya başlamak hazırsınız.

    > [!NOTE]
    > Görevlerden herhangi biri olan şu anda ML.NET CLI Preview tarafından desteklenen ML için kullanılmaya hazır oldukları sürece bu öğreticiyi tamamladıktan sonra kendi veri kümeleriyle deneyebilirsiniz *'İkili sınıflandırma', 'Çok sınıflı sınıflandırma' ve ' Regresyon '*).

## <a name="run-the-mlnet-auto-train-command"></a>'Mlnet otomatik train' komutunu çalıştırın

1. Aşağıdaki ML.NET CLI komutunu çalıştırın:

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    Bu komut çalıştırır  **`mlnet auto-train` komut**:
    - için bir **ML görev** türü **`binary-classification`**
    - kullanan **veri kümesi dosyası `yelp_labelled.txt`**  eğitim ve test (dahili olarak CLI çapraz doğrulama kullanabileceğiniz veya iki veri kümesi içinde bir eğitim ve test etmek için bir bölme) veri kümesi olarak
    - Burada **hedefi/hedef sütun** tahmin etmek istediğiniz (genellikle adlı **'etiketi'**) olan **sütun dizini 1 olan** (dizin sıfır tabanlı olduğundan diğer bir deyişle ikinci sütun )
    - mu **dosya üst bilgisi kullanmamak** bu belirli veri kümesi dosyası üst bilgi olmadığı sütun adlarına sahip
    - **araştırma zaman hedeflenen** deneme için **10 saniye**

    CLI, benzer çıktıyı görürsünüz:

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    ![ML.NET CLI otomatik-PowerShell eğitme](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    ![ML.NET CLI otomatik-PowerShell eğitme](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    Bu durumda yalnızca 10 saniye içinde ve sağlanan, küçük veri kümesi ile CLI Aracı'nı farklı birleşimlerini algoritmaları/yapılandırma iç farklı verilerle birden çok kez temel eğitim anlamına gelen çok sayıda videonuz yinelemeler çalıştırabilir dönüşümler ve algoritma'nın hyper-parametreleriyle. 

    Son olarak, 10 saniye içinde bulunan "en iyi kalite" modeli, herhangi belirli bir yapılandırma ile belirli bir eğitmen/algoritmasını kullanarak bir modeldir. Araştırma süreye bağlı olarak, farklı bir sonuç komutu oluşturabilir. Seçimi gösterilen, gibi birden çok ölçümlere göre `Accuracy`.

    **Modelin kalite ölçüleri anlama**

    İkili sınıflandırma modeli değerlendirmek için ilk ve en kolay anlaşılması kolaydır doğruluğu unsurdur. "Doğruluk oranı sınama veri kümesi ile doğru tahminler sağlıyor.". % 100 (1.00) daha iyi yakın.

    Ancak, etiket (0 ve bu durumda 1) test kümesinde özellikle dengesiz, burada yalnızca doğruluğu Metrik ölçme yeterli değildir durumlar vardır.

    Ek Ölçümler ve daha fazlası için **ölçümleri hakkında ayrıntılı bilgi** doğruluğu, AUC, AUCPR F1 puanı farklı modelleri değerlendirmek için kullanılan, okuyabilirsiniz [anlama ML.NET ölçümleri](../resources/metrics.md)

    > [!NOTE]
    >  Bu çok aynı veri kümesini deneyin ve birkaç dakikalığına belirtin `--max-exploration-time` (örneği için üç 180 saniye belirttiğiniz şekilde dakika gibi), bir daha iyi "en iyi modeli" sizin için (Bu harika bu veri kümesi için farklı eğitim işlem hattı yapılandırmasıyla bulacaksınız küçük, 1000 satırı). 
        
    "Büyük veri kümeleri hedefleyen bir üretime hazır modeli" bir "en iyi/iyi kalite" modeli bulmak için genellikle dataset boyutuna bağlı olarak çok daha fazla araştırma süresini belirterek CLI ile denemeler yapmalısınız. Aslında, çoğu durumda özellikle veri kümesine satırlar ve sütunlar üzerinde büyük olursa birden çok keşif süresi saatlik gerektirebilir. 

1. Önceki komut yürütme şu varlıkları oluşturdu:

    - Serileştirilmiş modeli .zip ("en iyi modeli") kullanıma hazır. 
    - C#kod, Çalıştır/puan modeli (Bu modeli ile son kullanıcı uygulamalarınızda Öngörüler oluşturmak için) oluşturulur.
    - C#Bu model (öğrenme amacıyla) oluşturmak için kullanılan kod eğitimi.
    - Tüm yinelemeler sahip bir günlük dosyası, hyper-parametreleriyle ve veri dönüşümleri, birlikte çalıştığınız her bir algoritmanın hakkında ayrıntılı bilgilere sahip incelediniz. 

    İlk iki varlıkları (. ZIP dosyası modeli ve C# modelin çalıştırmak için kod) doğrudan ML model oluşturulan son kullanıcı uygulamalarınızda (ASP.NET Core web uygulaması, hizmetleri, masaüstü uygulaması, vb.) ile tahminlerde bulunmak üzere kullanılabilir.

    Üçüncü bir varlık, eğitim kod hangi ML.NET API kodu CLI tarafından hangi belirli trainer/algoritması araştırabilir ve hiper parametreler CLI tarafından seçilen oluşturulan modeli eğitmek için kullanılan gösterir.

Numaralandırılmış bu varlıkları öğreticinin aşağıdaki adımlarda açıklanmıştır.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Oluşturulan keşfedin C# tahminlerde bulunmak üzere modeli çalıştırmak için kullanılacak kodu

1. Visual Studio (2017 veya 2019) adlı klasöründe oluşturulan çözümü açın `SampleBinaryClassification` , özgün hedef klasördeki (öğreticide taşıyordu `/cli-test`). Benzer şekilde bir çözüm görmeniz gerekir:

    > [!NOTE]
    > Visual Studio kullanmak için önerdiğimiz öğreticide ancak da oluşturulan keşfedebilirsiniz C# ile oluşturulan konsol uygulaması (iki projeler) ile herhangi bir metin düzenleyicisi kod ve `dotnet CLI` MacOS, Linux veya Windows makinesi.

    ![VS çözüm CLI tarafından oluşturulan](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Oluşturulan **sınıf kitaplığı** serileştirilmiş ML model (.zip dosyası) ve veri sınıfları (veri modelleri) içeren, olan bir şey doğrudan kullanabilirsiniz, son kullanıcı uygulamanızda bile, sınıf kitaplığı doğrudan başvuruda (veya taşıma yazarken kodu tercih eder).
    - Oluşturulan **konsol uygulaması** gözden geçirmeniz gerekir ve genellikle daha sonra 'Puanlama code' yeniden yürütme kodunu içerir (ML model tahminler elde etmeye çalışan kodu), basit kod (yalnızca birkaç satır), son kullanıcıya taşıyarak Tahminde bulunmak istediğiniz uygulama. 

1. Açık **ModelInput.cs** ve **ModelOutput.cs** sınıf dosyaları içinde sınıf kitaplığı projesi. Bu sınıfların 'veri sınıfları' veya verileri tutmak için kullanılan POCO sınıflar olduğunu görürsünüz. 'Ortak kod' olan ancak onlarca veya sütunları hatta yüzlerce veri kümeniz varsa, kullanışlı olması oluşturulmuş. 
    - `ModelInput` Sınıfı, veri kümesinden okurken kullanılır. 
    - `ModelOutput` Sınıfı (tahmin veriler) tahmin sonucu elde etmek için kullanılır.

1. Program.cs dosyasını açın ve kodu keşfedin. Yalnızca birkaç satır içinde çalıştırmayı ve örnek tahminde bulunmak mümkün.

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

- Yalnızca ilk satırlık bir kod oluşturur bir `MLContext` ML.NET kod çalıştırdığınız zaman gerekli nesne. 

- Eğitim gerekmez çünkü ikinci kod satırının, zaten sizin için CLI aracı tarafından geliştirilen ve modele ait kayıtlı olduğundan modeli seri bırakılmıştır. ZIP dosyası. Ancak görmek istiyorsanız *"nasıl modeli eğitilir"* CLI tarafından size bu satırı açıklamadan çıkarın ve bu belirli ML model için kullanılan eğitim kod Çalıştır/hata ayıkla.

- Kod üçüncü satırında model serileştirilmiş modeli yüklenemiyor. ZIP dosyasıyla `mlContext.Model.Load()` modelin yolunu sağlayarak API. ZIP dosyası.

- Dördüncü yüklediğiniz kod satırında oluşturun `PredictionEngine` nesnesi ile `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API. Gereksinim duyduğunuz `PredictionEngine` verilerin (Bu durumda, tek bir parça, yaklaşım tahmin etmek için metin), tek bir örnek hedefleyen bir tahminde bulunmak istediğiniz her nesne.

- Beşinci kod satırının, oluşturduğunuz olan *tek örnek verileri* işleve çağrı yaparak tahmin için kullanılacak `CreateSingleDataSample()`. Bu işlev kastettiğinizi bilemez ne tür bir örnek verileri kullanmak için CLI aracı olduğundan, ilk satır kümesinin yüklüyor. Ancak, bu durumda, geçerli uygulaması yerine kendi 'sabit kodlanmış' veri oluşturabilirsiniz `CreateSingleDataSample()` güncelleştirerek bu işlevini uygulama bu basit kod işlevi:

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. Projeyi çalıştırmak, özgün örnek verileri kullanarak veri kümesinin veya kendi özel sabit kodlanmış örnek verileri sağlayarak ilk satırdan yüklendi. Tahmin için karşılaştırılabilir almanız gerekir:

    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    F5 tuşlarına basarak konsol uygulamasını Visual Studio'dan çalıştırma (Oynat düğmesini):

    ![ML.NET CLI otomatik-PowerShell eğitme](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    Konsol uygulaması, komut isteminden aşağıdaki komutları yazarak çalıştırın:

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![ML.NET CLI otomatik-PowerShell eğitme](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Sabit kodlanmış örnek veriler için diğer cümleleri farklı bir yaklaşım ile değiştirmeyi deneyin ve nasıl pozitif veya negatif yaklaşım modeli tahmin bakın. 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>ML model tahminlerini son kullanıcı uygulamaları ekleyin.

Benzer 'ML model Puanlama kod' için model, son kullanıcı uygulama ve marka Öngörüler çalıştırma kullanabilirsiniz. 

Örneğin, doğrudan bu kodu herhangi bir Windows masaüstü uygulaması için gibi taşıyabilirsiniz **WPF** ve **WinForms** ve konsol uygulamasında bitti dedik daha modeli aynı şekilde çalıştırın.

Ancak, bu ML model çalıştırmak için kod satırlarını uygulama yolu (yani, önbellek model .zip dosyası ve bir kez yük) hale getirilmiştir ve özellikle uygulamanızın gibi ölçeklenebilir olması gerekiyorsa her istek, bunları oluşturmak yerine tekil nesneleri bir web uygulaması veya aşağıdaki bölümünde anlatıldığı gibi dağıtılmış bir hizmet.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>ML.NET modelleri ölçeklenebilir ASP.NET Core web uygulamaları ve Hizmetleri (çok iş parçacıklı uygulamalar) çalışan

Model nesnesinin oluşturulmasını (`ITransformer` bir modelin .zip dosyasından yüklenen) ve `PredictionEngine` nesne en iyi duruma getirilmiş özellikle ölçeklenebilir web uygulamaları ve Dağıtılmış hizmetler üzerinde çalışırken. İlk durumda, model nesnesi için (`ITransformer`) en iyi duruma getirme oldukça basittir. Bu yana `ITransformer` nesne iş parçacığı açısından güvenli, modeli bir kez yüklemek için nesnenin bir singleton veya statik nesne olarak önbelleğe alabilir.

İkinci nesne için `PredictionEngine` nesne çok kolay değildir çünkü `PredictionEngine` nesne iş parçacığı açısından güvenli değildir, bu nedenle tekil veya statik nesnesinde bir ASP.NET Core uygulaması olarak bu nesne örneği oluşturulamıyor. Bu iş parçacığı açısından güvenli ve ölçeklenebilirlik sorun derin bu konuda açıklanan [Blog Gönderisi](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/). 

Ancak, şey sizin için bu blog gönderisinde açıklandığı daha çok daha kolaylaştırıldı. Üzerinde basit bir yaklaşım işinize ve güzel bir oluşturduğunuz **'.NET Core tümleştirme paketi'** kolayca içinde ASP.NET Core uygulamalarınızı ve hizmetlerinizi DI uygulama Hizmetleri (bağımlılık ekleme kaydederek kullanabileceğiniz Hizmetleri) ve doğrudan kodunuzdan kullanabilirsiniz. Şu öğretici ve örnek için bunu kontrol edin:

- [Öğretici: ML.NET modelleri üzerinde Ölçeklenebilir ASP.NET Core web uygulamaları ve WebAPIs çalıştırma](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Örnek: ASP.NET Core Webapı ölçeklenebilir ML.NET modeli](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Oluşturulan keşfedin C# "en iyi kalite" modeli eğitmek için kullanılan kod 

Öğrenme amacıyla daha gelişmiş için da oluşturulan keşfedebilirsiniz C# CLI aracı tarafından oluşturulan modeli eğitmek için kullanılan kod.

'Eğitim modeli kodu' şu anda oluşturulan özel bir sınıf içinde oluşturulduğunu adlı `ModelBuilder` eğitim kod araştırabileceği şekilde.

Daha da önemlisi, bu belirli senaryo (yaklaşım analizi modeli) için de kod ile oluşturulan eğitim kod aşağıdaki öğreticide açıklanan karşılaştırabilirsiniz:

- Karşılaştırma: [Öğretici: ML.NET bir yaklaşım analizi ikili sınıflandırma senaryosunda kullanmak](https://docs.microsoft.com/en-us/dotnet/machine-learning/tutorials/sentiment-analysis).

Bu öğreticide seçtiğiniz algoritması ve ardışık düzen yapılandırma CLI aracı tarafından oluşturulan kodu karşılaştırmak ilgi çekici olur. Yineleme ve arama için daha iyi modelleri harcadığınız ne kadar süre bağlı olarak seçilen algoritma ardışık düzen yapılandırması ve belirli hyper-parametreleriyle birlikte farklı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Model eğitiminin ML.NET CLI ile otomatikleştirme](../automate-training-with-cli.md)
- [Öğretici: ML.NET modelleri üzerinde Ölçeklenebilir ASP.NET Core web uygulamaları ve WebAPIs çalıştırma](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Örnek: ASP.NET Core Webapı ölçeklenebilir ML.NET modeli](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [ML.NET CLI otomatik train komut Başvuru Kılavuzu](../reference/ml-net-cli-reference.md) 
- [ML.NET komut satırı arabirimi (CLI) aracı yükleme](../how-to-guides/install-ml-net-cli.md)
- [ML.NET CLI'de telemetri](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> * Verilerinizi seçili ML görev (sorunu çözmek için) için hazırlama
> * CLI aracında 'mlnet otomatik train' komutunu çalıştırın
> * Kalite Ölçüm sonuçlarını gözden geçirin
> * Oluşturulan anlamak C# kod modeli (son kullanıcı uygulamayı kullanmak için kodu)
> * Oluşturulan keşfedin C# (öğrenme amacıyla) "en iyi kalite" modeli eğitmek için kullanılan kod

> [!div class="nextstepaction"]
> [Model eğitiminin ML.NET CLI ile otomatikleştirme](../automate-training-with-cli.md)
