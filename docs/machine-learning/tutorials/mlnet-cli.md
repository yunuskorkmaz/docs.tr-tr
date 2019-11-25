---
title: ML.NET CLI kullanarak yaklaşımı çözümleme
description: Bir ML modelini ve bir örnek veri C# kümesinden ilgili kodu otomatik olarak oluştur
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: bea5cd1b42773e62601edbc113b2155ff78cf884
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977406"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>ML.NET CLI kullanarak yaklaşımı çözümleme

ML.NET CLı kullanarak bir ML.NET modeli ve temel alınan C# kodu otomatik olarak oluşturma hakkında bilgi edinin. Veri kümenizi ve uygulamak istediğiniz makine öğrenimi görevini sağlarsınız ve CLı, model oluşturma ve dağıtım kaynak kodu ve ikili modeli oluşturmak için, oto ml altyapısını kullanır.

Bu öğreticide, aşağıdaki adımları kullanacaksınız:
> [!div class="checklist"]
>
> - Verilerinizi seçili makine öğrenimi görevi için hazırlayın
> - CLı 'dan ' mlnet Auto-eğitme ' komutunu çalıştırın
> - Kalite ölçümü sonuçlarını gözden geçirme
> - Uygulamanızda modeli kullanmak C# için oluşturulan kodu anlayın
> - Modeli eğitmek için C# kullanılan üretilen kodu keşfet

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET CLı aracına başvurur ve malzemeler değişebilir. Daha fazla bilgi için [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) sayfasını ziyaret edin.

ML.NET CLı, ML.NET 'in bir parçasıdır ve ana amacı, öğrenimi öğrenirken, kullanmaya başlamak için sıfırdan kod oluşturmanız gerekmeyen .NET geliştiricileri için "herkese" ML.NET.

Sağladığınız eğitim veri kümelerine göre iyi kalitede ML.NET modelleri ve kaynak kodu oluşturmak için ML.NET CLı 'yi herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabilirsiniz.

## <a name="pre-requisites"></a>Ön koşullar

- [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya üzeri
- Seçim [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)
- [ML.NET CLı](../how-to-guides/install-ml-net-cli.md)

Oluşturulan C# kod projelerini Visual Studio 'dan veya `dotnet run` (.NET Core CLI) ile çalıştırabilirsiniz.

## <a name="prepare-your-data"></a>Verilerinizi hazırlayın

İkili sınıflandırma makinesi öğrenimi görevi olan ' Yaklaşım Analizi ' senaryosu için kullanılan mevcut bir veri kümesini kullanacağız. Kendi veri kümenizi benzer bir şekilde kullanabilirsiniz ve model ve kod sizin için oluşturulur.

1. [(Aşağıdaki notdaki alıntıların bulunduğu) cümleler veri kümesi ZIP dosyasını](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)indirin ve seçtiğiniz herhangi bir klasörde sıkıştırmayı açın.

    > [!NOTE]
    > Bu öğreticide veri kümeleri, ' Kimden grubundan, derin özellikleri kullanarak tek tek etiketlere, Kotzıas et al ' ı kullanır. KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017). UCI Machine Learning deposu [http://archive.ics.uci.edu/ml ]. Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.

2. `yelp_labelled.txt` dosyasını daha önce oluşturduğunuz herhangi bir klasöre (`/cli-test`gibi) kopyalayın.

3. Tercih ettiğiniz komut istemi ' ni açın ve veri kümesi dosyasını kopyaladığınız klasöre gidin. Örneğin:

    ```console
    > cd /cli-test
    ```

    Visual Studio Code gibi herhangi bir metin düzenleyicisini kullanarak `yelp_labelled.txt` veri kümesi dosyasını açabilir ve inceleyebilirsiniz. Yapının şu olduğunu görebilirsiniz:

    - Dosya üst bilgisi yok. Sütunun dizinini kullanacaksınız.

    - Yalnızca iki sütun vardır:

        | Metin (sütun dizini 0) | Etiket (sütun dizini 1)|
        |--------------------------|-------|
        | Wow... Bu yere iner. | 1\. |
        | Crust iyi değil. | 0 |
        | Nefis değildir ve doku yalnızca Nasty idi. | 0 |
        | ... ÇOK SAYıDA METIN SATıRı... | ... (1 veya 0)... |

    Veri kümesi dosyasını düzenleyiciden kapattığınızdan emin olun.

    Şimdi bu ' Yaklaşım Analizi ' senaryosu için CLı kullanmaya başlamaya hazırsınız.

    > [!NOTE]
    > Bu Öğreticiyi tamamladıktan sonra, şu anda *' Ikili sınıflandırma ', ' Multi-Class Classification ' ve ' regresyon '* olan ml.net CLI önizlemesi tarafından desteklenen HERHANGI bir ml görevi için kullanılmak üzere hazırlandıkları sürece kendi veri kümelerinizi de deneyebilirsiniz.

## <a name="run-the-mlnet-auto-train-command"></a>' Mlnet otomatik-eğitme ' komutunu çalıştırın

1. Aşağıdaki ML.NET CLı komutunu çalıştırın:

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    Bu komut **`mlnet auto-train` komutunu**çalıştırır:
    - **`binary-classification`** türünde bir **ml görevi** için
    - Eğitim ve test veri kümesi olarak **`yelp_labelled.txt`veri kümesi dosyasını** kullanır (DAHILI olarak CLI, çapraz doğrulama kullanır veya biri eğitim ve test için bir tane olmak üzere iki veri kümesinde bölünür)
    - tahmin etmek istediğiniz **amaç/hedef sütununun** (genellikle **' Label '** olarak adlandırılır) dizin 1 (Dizin sıfır tabanlı olduğundan ikinci sütun) **olan sütundur**
    - Bu veri kümesi dosyası bir üst bilgisine sahip olmadığından, sütun adlarıyla **bir dosya üstbilgisi kullanmaz**
    - deneme için **hedeflenen araştırma süresi** **10 saniyedir**

    CLı 'dan aşağıdakine benzer bir çıktı görürsünüz:

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    ![PowerShell 'de ML.NET CLı otomatik eğitimi](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    ![PowerShell 'de ML.NET CLı otomatik eğitimi](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    Bu özel durumda, yalnızca 10 saniye içinde ve küçük veri kümesiyle sunulan CLı Aracı, farklı iç veri dönüştürmeleri ve algoritmaların Hyper-parametreleri ile farklı algoritma/yapılandırma birleşimlerine göre birden çok kez eğitim sağlayan çok sayıda yineleme çalıştırabiliyor.

    Son olarak, 10 saniye içinde bulunan "en iyi kalite" modeli, belirli bir yapılandırma ile belirli bir oran/algoritma kullanan bir modeldir. Araştırma zamanına bağlı olarak, komut farklı bir sonuç oluşturabilir. Seçim, `Accuracy`gibi, gösterilen birden çok ölçümü temel alır.

    **Modelin kalite ölçümlerini anlama**

    İkili sınıflandırma modelini değerlendirmek için ilk ve en kolay ölçüm, anlaşılması kolay bir yoldur. "Doğruluk, test veri kümesiyle doğru tahminlerden orandır.". %100 ' e (1,00) yaklaşarak daha iyi.

    Ancak, özellikle de doğruluk ölçümüyle ölçmeniz yeterli değildir, özellikle de (Bu durumda 0 ve 1) etiketi test veri kümesinde dengesiz olur.

    Farklı modelleri değerlendirmek için kullanılan doğruluk, AUC, AUCPR, F1-Score gibi ölçümler hakkında ek ölçümler ve daha **ayrıntılı bilgiler** için, [ml.net ölçümlerini anlama](../resources/metrics.md) makalesini okuyabilirsiniz

    > [!NOTE]
    > Bu çok satırlı veri kümesini deneyebilir ve bu veri kümesi için farklı bir eğitim işlem hattı yapılandırması (oldukça küçük, 1000 satır) ile sizin için daha iyi bir "en iyi model" bulacak olan `--max-exploration-time` için birkaç dakika belirtebilirsiniz (örneğin, üç 180 dakika).

    Daha büyük veri kümelerini hedefleyen "üretime hazır bir model" olan "en iyi/iyi kalite" modelini bulmak için, CLı ile denemeleri, genellikle veri kümesinin boyutuna bağlı olarak çok daha fazla araştırma süresi belirtmelisiniz. Aslında, çoğu durumda, özellikle veri kümesi satırlar ve sütunlar üzerinde büyükse, birden çok saat araştırma süresi gerekebilir.

1. Önceki komut yürütmesi aşağıdaki varlıkları oluşturdu:

    - Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.
    - C#oluşturulan model (bu modelle Son Kullanıcı uygulamalarınızda tahmine dayalı hale getirmek Için) çalıştırılacak/puan veren kod.
    - C#Bu modeli oluşturmak için kullanılan eğitim kodu (öğrenme amaçları).
    - Her bir algoritmayla ilgili ayrıntılı bilgileri keşfeden tüm yinelemeleri içeren bir günlük dosyası, Hyper-parametreleri ve veri dönüştürmeleri birleşimine çalıştı.

    İlk iki varlık (. ZIP dosya modeli ve C# bu modeli çalıştırmaya yönelik kod), bu oluşturulmuş ml modeliyle tahminler yapmak için doğrudan Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) kullanılabilir.

    Eğitim kodu olan üçüncü varlık, CLI tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. bu sayede, CLı tarafından hangi belirli bir oran/algoritma ve Hyper-parametrelerinin seçili olduğunu araştırabilirsiniz.

Bu numaralandırılabilir varlıklar, öğreticinin aşağıdaki adımlarında açıklanmıştır.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Tahmine dayalı hale C# getirmek üzere modeli çalıştırmak için kullanılacak oluşturulan kodu keşfet

1. Visual Studio 'da (2017 veya 2019) özgün hedef klasörünüzdeki `SampleBinaryClassification` adlı klasörde oluşturulan çözümü açın (öğreticide `/cli-test`adı verildi). Şuna benzer bir çözüm görmeniz gerekir:

    > [!NOTE]
    > Visual Studio 'Yu kullanmayı önerdiğimiz öğreticide, tüm metin düzenleyiciyle oluşturulan C# kodu (iki proje) keşfedebilir ve oluşturulan konsol uygulamasını MacOS, Linux veya Windows makinesinde `dotnet CLI` çalıştırabilirsiniz.

    ![CLı tarafından oluşturulan VS çözümü](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Serileştirilmiş ML modeli (. zip dosyası) ve veri sınıfları (veri modelleri) içeren oluşturulmuş **sınıf kitaplığı** , doğrudan bu sınıf kitaplığına (veya istediğiniz şekilde kodu taşıyarak) doğrudan başvuru yaparak, Son Kullanıcı uygulamanızda doğrudan kullanabileceğiniz bir şeydir.
    - Oluşturulan **konsol uygulaması** , gözden geçirmeniz gereken yürütme kodunu içerir ve ardından genellikle bu basit kodu (yalnızca birkaç satır) tahmine dayalı hale getirmek istediğiniz son kullanıcı uygulamanıza taşıyarak ' Puanlama kodu ' nu (tahminleri yapmak için ml modelini çalıştıran kod) yeniden kullanırsınız.

1. **ModelInput.cs** ve **ModelOutput.cs** sınıf dosyalarını sınıf kitaplığı projesi içinde açın. Bu sınıfların, verileri tutmak için kullanılan ' veri sınıfları ' veya POCO sınıfları olduğunu görürsünüz. Bu, ' ortak kod ', ancak veri kümeniz yüzlerce veya hatta yüzlerce sütun içeriyorsa oluşturulmasını sağlamak için yararlıdır.
    - `ModelInput` sınıfı veri kümesinden verileri okurken kullanılır.
    - `ModelOutput` sınıfı, tahmin sonucunu (tahmin verileri) almak için kullanılır.

1. Program.cs dosyasını açın ve kodu araştırın. Yalnızca birkaç satırda modeli çalıştırabilir ve örnek bir tahmin yapabilirsiniz.

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

- Kodun ilk satırı, ML.NET kodunu her çalıştırdığınızda gerekli bir `MLContext` nesnesi oluşturur.

- İkinci kod satırı, CLı aracı tarafından zaten eğitilen ve modelin seri hale getirilmiş olduğundan modeli eğmenize gerek olmadığı için yorumlandı. ZIP dosyası. Ancak CLı tarafından *"modelin eğitilme şekli"* ni görmek isterseniz, söz konusu satırın açıklamasını kaldırın ve söz konusu ml modeli için kullanılan eğitim kodunu çalıştırın/hata ayıklayın.

- Üçüncü kod satırında modeli serileştirilmiş modelden yüklersiniz. Bu modelin yolunu sağlayarak `mlContext.Model.Load()` API 'SI ile ZIP dosyası. ZIP dosyası.

- Yüklediğiniz dördüncü kod satırında, `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API 'siyle `PredictionEngine` nesnesini oluşturun. Tek bir veri örneğini (Bu durumda, kendi yaklaşımını tahmin etmek için tek bir metin parçası) hedefleyen bir tahmin yapmak istediğinizde `PredictionEngine` nesnesine ihtiyacınız vardır.

- Beşinci kod satırı, `CreateSingleDataSample()`işlevini çağırarak tahmin için kullanılacak *tek örnek verileri* oluşturduğunuz yerdir. CLı aracı ne tür örnek verileri kullanacağınızı bilmediğinden, bu işlev içinde veri kümesinin ilk satırını yüklüyor. Ancak, bu durumda, bu işlevi uygulayan daha basit kodu güncelleştirerek `CreateSingleDataSample()` işlevinin geçerli uygulaması yerine ' sabit kodlanmış ' verileri de oluşturabilirsiniz:

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. Veri kümesinin ilk satırından yüklenen özgün örnek verileri kullanarak ya da kendi özel sabit kodlanmış örnek verilerinizi sağlayarak projeyi çalıştırın. Şu şekilde bir tahmin almanız gerekir:

    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    F5 tuşuna basarak (Play Button) konsol uygulamasını Visual Studio 'dan çalıştırın:

    ![PowerShell 'de ML.NET CLı otomatik eğitimi](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    Aşağıdaki komutları yazarak konsol uygulamasını komut isteminden çalıştırın:

     ```bash
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![PowerShell 'de ML.NET CLı otomatik eğitimi](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Sabit kodlanmış örnek verileri farklı bir yaklaşım ile diğer cümleler ile değiştirmeyi deneyin ve modelin olumlu veya negatif yaklaşımı nasıl tahmin eder olduğunu görün.

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>ML modeli tahminleri ile Son Kullanıcı uygulamalarınızı kullanın

Modeli son kullanıcı uygulamanızda çalıştırmak ve tahmin yapmak için benzer ' ML model Puanlama kodu ' kullanabilirsiniz.

Örneğin, bu kodu doğrudan **WPF** ve **WinForms** gibi herhangi bir Windows masaüstü uygulamasına taşıyabilir ve modeli konsol uygulamasında yapılmayla aynı şekilde çalıştırabilirsiniz.

Bununla birlikte, bir ML modelini çalıştırmak için bu kod satırlarını uygulama yolu en iyi duruma gelmelidir (yani, model. zip dosyasını önbelleğe alır ve bir kez yükler) ve özellikle uygulamanızın ölçeklenebilir olması gerekiyorsa, her istekte bunları oluşturmak yerine tek nesneleri vardır. Aşağıdaki bölümde açıklandığı gibi bir Web uygulaması veya dağıtılmış hizmeti.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Ölçeklenebilir ASP.NET Core Web uygulamaları ve Hizmetleri 'nde ML.NET modellerini çalıştırma (çok kanallı uygulamalar)

Model nesnesinin oluşturulması (bir modelin. zip dosyasından yüklenen`ITransformer`) ve `PredictionEngine` nesnesi özellikle ölçeklenebilir Web uygulamaları ve dağıtılmış hizmetler üzerinde çalışırken iyileştirilmelidir. İlk durumda, model nesnesi (`ITransformer`) iyileştirmesi basittir. `ITransformer` nesne iş parçacığı açısından güvenli olduğundan, modeli bir kez yüklemeniz için nesneyi tek veya statik bir nesne olarak önbelleğe alabilirsiniz.

İkinci nesne olan `PredictionEngine` nesnesi, `PredictionEngine` nesnesi iş parçacığı açısından güvenli olmadığından, bu nedenle bu nesneyi bir ASP.NET Core uygulamasında tek veya statik nesne olarak örnekleyemezsiniz. Bu iş parçacığı güvenli ve ölçeklenebilirlik sorunu bu [blog gönderisine](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)göre ele alınmıştır.

Ancak, bu blog gönderisinden açıklanamayan şeyler sizin için çok daha kolay. Sizin için daha basit bir yaklaşımda çalıştık ve uygulamayı uygulama ve hizmetASP.NET Core lerinize uygulama dı Hizmetleri 'ne (bağımlılık ekleme Hizmetleri) kaydederek ve sonra doğrudan kodunuzda kullanarak kolayca kullanabileceğiniz iyi bir **' .NET Core Integration Package '** oluşturdunuz. Şunları yapmak için aşağıdaki öğreticiyi ve örneğe bakın:

- [Öğretici: ML.NET modellerini ölçeklenebilir ASP.NET Core Web Apps ve WebAPIs üzerinde çalıştırma](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Örnek: ASP.NET Core WebAPI üzerinde ölçeklenebilir ML.NET modeli](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>"En iyi C# kalite" modelini eğitmek için kullanılan üretilen kodu keşfet

Daha gelişmiş öğrenme amaçlarıyla, oluşturulan modeli eğitebilmeniz için CLı C# aracı tarafından kullanılan oluşturulan kodu da keşfedebilirsiniz.

' Eğitim modeli kodu ' Şu anda, bu eğitim kodunu araştırmak için `ModelBuilder` adlı özel sınıfta oluşturulmuştur.

Daha önemlisi, bu senaryo (Yaklaşım Analizi modeli) için de, aşağıdaki öğreticide açıklanan kod ile bu üretilen eğitim kodunu karşılaştırabilirsiniz:

- Compare: [öğretici: bir yaklaşım Analizi ikili sınıflandırma senaryosunda ml.NET kullanın](sentiment-analysis.md).

Öğreticide seçilen algoritma ve işlem hattı yapılandırmasını CLı aracı tarafından oluşturulan kodla karşılaştırmak ilginç. Daha iyi modeller için ne kadar zaman harcadığınıza ve aradığınıza bağlı olarak, seçilen algoritma belirli Hyper-parametreleri ve işlem hattı yapılandırmasıyla birlikte farklı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLı ile model eğitimi otomatikleştirin](../automate-training-with-cli.md)
- [Öğretici: ML.NET modellerini ölçeklenebilir ASP.NET Core Web Apps ve WebAPIs üzerinde çalıştırma](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Örnek: ASP.NET Core WebAPI üzerinde ölçeklenebilir ML.NET modeli](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [ML.NET CLı otomatik eğitme komut başvuru kılavuzu](../reference/ml-net-cli-reference.md)
- [ML.NET komut satırı arabirimi (CLı) aracını yüklemek](../how-to-guides/install-ml-net-cli.md)
- [ML.NET CLı 'de telemetri](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, nasıl yapılacağını öğrendiniz:
> [!div class="checklist"]
>
> - Verilerinizi seçilen ML görevi için hazırlayın (çözülme sorunu)
> - CLı aracında ' mlnet Auto-eğitme ' komutunu çalıştırın
> - Kalite ölçümü sonuçlarını gözden geçirme
> - Modeli çalıştırmak için C# oluşturulan kodu anlayın (Son Kullanıcı uygulamanızda kullanılacak kod)
> - "En iyi C# kalite" modelini (öğrenme amaçları) eğitmek için kullanılan üretilen kodu keşfet

> [!div class="nextstepaction"]
> [ML.NET CLı ile model eğitimi otomatikleştirin](../automate-training-with-cli.md)
