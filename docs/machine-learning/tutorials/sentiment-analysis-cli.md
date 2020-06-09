---
title: ML.NET CLI kullanarak yaklaşımı çözümleme
description: Örnek veri kümesinden otomatik olarak ML modeli ve ilgili C# kodu oluşturma
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 64190546157bc9386314a3080c5364fd854d7704
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602261"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>ML.NET CLI kullanarak yaklaşımı çözümleme

ML.NET CLı kullanarak otomatik olarak bir ML.NET modeli ve temel C# kodu oluşturma hakkında bilgi edinin. Veri kümenizi ve uygulamak istediğiniz makine öğrenimi görevini sağlarsınız ve CLı, model oluşturma ve dağıtım kaynak kodu ve sınıflandırma modeli oluşturmak için oto ml altyapısını kullanır.

Bu öğreticide, aşağıdaki adımları kullanacaksınız:
> [!div class="checklist"]
>
> - Verilerinizi seçili makine öğrenimi görevi için hazırlayın
> - CLı 'dan ' mlnet sınıflandırması ' komutunu çalıştırın
> - Kalite ölçümü sonuçlarını gözden geçirme
> - Uygulamanızda modeli kullanmak için oluşturulan C# kodunu anlayın
> - Modeli eğitmek için kullanılan oluşturulan C# kodunu keşfet

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET CLı aracına başvurur ve malzemeler değişebilir. Daha fazla bilgi için [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) sayfasını ziyaret edin.

ML.NET CLı, ML.NET 'in bir parçasıdır ve ana amacı, öğrenimi öğrenirken, kullanmaya başlamak için sıfırdan kod oluşturmanız gerekmeyen .NET geliştiricileri için "herkese" ML.NET.

Sağladığınız eğitim veri kümelerine göre iyi kalitede ML.NET modelleri ve kaynak kodu oluşturmak için ML.NET CLı 'yi herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabilirsiniz.

## <a name="pre-requisites"></a>Ön koşullar

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) veya üzeri
- Seçim [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)
- [ML.NET CLI](../how-to-guides/install-ml-net-cli.md)

Oluşturulan C# kod projelerini Visual Studio 'dan veya `dotnet run` (.NET Core CLI) ile çalıştırabilirsiniz.

## <a name="prepare-your-data"></a>Verilerinizi hazırlama

İkili sınıflandırma makinesi öğrenimi görevi olan ' Yaklaşım Analizi ' senaryosu için kullanılan mevcut bir veri kümesini kullanacağız. Kendi veri kümenizi benzer bir şekilde kullanabilirsiniz ve model ve kod sizin için oluşturulur.

1. [(Aşağıdaki notdaki alıntıların bulunduğu) cümleler veri kümesi ZIP dosyasını](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)indirin ve seçtiğiniz herhangi bir klasörde sıkıştırmayı açın.

    > [!NOTE]
    > Bu öğreticide veri kümeleri, ' Kimden grubundan, derin özellikleri kullanarak tek tek etiketlere, Kotzıas et al ' ı kullanır. KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017). UCI Machine Learning deposu [ http://archive.ics.uci.edu/ml ]. Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.

2. `yelp_labelled.txt`Dosyayı daha önce oluşturduğunuz herhangi bir klasöre (örneğin,) kopyalayın `/cli-test` .

3. Tercih ettiğiniz komut istemi ' ni açın ve veri kümesi dosyasını kopyaladığınız klasöre gidin. Örnek:

    ```console
    cd /cli-test
    ```

    Visual Studio Code gibi herhangi bir metin düzenleyicisini kullanarak `yelp_labelled.txt` veri kümesi dosyasını açabilir ve keşfedebilirsiniz. Yapının şu olduğunu görebilirsiniz:

    - Dosya üst bilgisi yok. Sütunun dizinini kullanacaksınız.

    - Yalnızca iki sütun vardır:

        | Metin (sütun dizini 0) | Etiket (sütun dizini 1)|
        |--------------------------|-------|
        | Wow... Bu yere iner. | 1 |
        | Crust iyi değil. | 0 |
        | Nefis değildir ve doku yalnızca Nasty idi. | 0 |
        | ... ÇOK SAYıDA METIN SATıRı... | ... (1 veya 0)... |

    Veri kümesi dosyasını düzenleyiciden kapattığınızdan emin olun.

    Şimdi bu ' Yaklaşım Analizi ' senaryosu için CLı kullanmaya başlamaya hazırsınız.

    > [!NOTE]
    > Bu Öğreticiyi tamamladıktan sonra, şu anda *' Ikili sınıflandırma ', ' sınıflandırma ', ' gerileme '* ve *' öneri '* olan ml.net CLI önizlemesi tarafından desteklenen herhangi bir ml görevi için kullanılmak üzere hazırlandıkları sürece kendi veri kümelerinizi de deneyebilirsiniz.

## <a name="run-the-mlnet-classification-command"></a>' Mlnet sınıflandırması ' komutunu çalıştırın

1. Aşağıdaki ML.NET CLı komutunu çalıştırın:

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    Bu komut ** `mlnet classification` komutunu**çalıştırır:
    - *sınıflandırmanın* **ml görevi** için
    - **veri kümesi dosyasını `yelp_labelled.txt` ** eğitim ve test veri kümesi olarak kullanır (dahili olarak CLI, çapraz doğrulama kullanır ya da bir diğeri de test için bir tane olmak üzere iki veri kümesinde bölüşlecektir)
    - tahmin etmek istediğiniz **amaç/hedef sütununun** (genellikle **' Label '** olarak adlandırılır) dizin 1 (Dizin sıfır tabanlı olduğundan ikinci sütun) **olan sütundur**
    - Bu veri kümesi dosyası bir üst bilgisine sahip olmadığından, sütun adlarıyla **bir dosya üstbilgisi kullanmaz**
    - deneme için **hedeflenen araştırma/tren süresi** **10 saniyedir**

    CLı 'dan aşağıdakine benzer bir çıktı görürsünüz:

    <!-- markdownlint-disable MD023 MD025 -->

    ![PowerShell 'de ML.NET CLı sınıflandırması](./media/mlnet-cli/mlnet-classification-powershell.gif)

    Bu özel durumda, yalnızca 10 saniye içinde ve küçük veri kümesiyle sunulan CLı Aracı, farklı iç veri dönüştürmeleri ve algoritmaların Hyper-parametreleri ile farklı algoritma/yapılandırma birleşimlerine göre birden çok kez eğitim sağlayan çok sayıda yineleme çalıştırabiliyor.

    Son olarak, 10 saniye içinde bulunan "en iyi kalite" modeli, belirli bir yapılandırma ile belirli bir oran/algoritma kullanan bir modeldir. Araştırma zamanına bağlı olarak, komut farklı bir sonuç oluşturabilir. Seçim, gösterilen çoklu ölçümleri temel alır `Accuracy` .

    **Modelin kalite ölçümlerini anlama**

    İkili sınıflandırma modelini değerlendirmek için ilk ve en kolay ölçüm, anlaşılması kolay bir yoldur. "Doğruluk, test veri kümesiyle doğru tahminlerden orandır.". %100 ' e (1,00) yaklaşarak daha iyi.

    Ancak, özellikle de doğruluk ölçümüyle ölçmeniz yeterli değildir, özellikle de (Bu durumda 0 ve 1) etiketi test veri kümesinde dengesiz olur.

    Farklı modelleri değerlendirmek için kullanılan doğruluk, AUC, AUCPR ve F1-Score gibi ölçümler hakkında ek ölçümler ve daha **ayrıntılı bilgiler** için bkz. [ml.net ölçümlerini anlama](../resources/metrics.md).

    > [!NOTE]
    > Bu çok satırlı veri kümesini deneyebilir ve `--max-exploration-time` Bu veri kümesi için farklı bir eğitim işlem hattı yapılandırması (oldukça küçük, 1000 satır) ile sizin için daha iyi bir "en iyi model" bulunacak 180 şekilde birkaç dakika (örneğin, üç dakika) bulacaksınız.

    Daha büyük veri kümelerini hedefleyen "üretime hazır bir model" olan "en iyi/iyi kalite" modelini bulmak için, CLı ile denemeleri, genellikle veri kümesinin boyutuna bağlı olarak çok daha fazla araştırma süresi belirtmelisiniz. Aslında, çoğu durumda, özellikle veri kümesi satırlar ve sütunlar üzerinde büyükse, birden çok saat araştırma süresi gerekebilir.

1. Önceki komut yürütmesi aşağıdaki varlıkları oluşturdu:

    - Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.
    - Oluşturulan modeli çalıştırmak/öğrenmek için C# kodu (bu modelle Son Kullanıcı uygulamalarınızda tahminleri yapmak Için).
    - Bu modeli oluşturmak için kullanılan C# eğitim kodu (öğrenme amaçları).
    - Her bir algoritmayla ilgili ayrıntılı bilgileri keşfeden tüm yinelemeleri içeren bir günlük dosyası, Hyper-parametreleri ve veri dönüştürmeleri birleşimine çalıştı.

    İlk iki varlık (. Bu modeli çalıştırmak için ZIP dosya modeli ve C# kodu), bu oluşturulmuş ML modeliyle tahmine dayalı hale getirmek için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) doğrudan kullanılabilir.

    Eğitim kodu olan üçüncü varlık, CLI tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. bu sayede, CLı tarafından hangi belirli bir oran/algoritma ve Hyper-parametrelerinin seçili olduğunu araştırabilirsiniz.

Bu numaralandırılabilir varlıklar, öğreticinin aşağıdaki adımlarında açıklanmıştır.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Tahmine dayalı hale getirmek üzere modeli çalıştırmak için kullanılacak oluşturulan C# kodunu keşfet

1. Visual Studio 'da (2017 veya 2019) özgün hedef klasörünüzün içindeki adlı klasörde oluşturulan çözümü açın `SampleClassification` (öğreticide adı altında `/cli-test` ). Şuna benzer bir çözüm görmeniz gerekir:

    > [!NOTE]
    > Visual Studio 'Yu kullanmayı önerdiğimiz öğreticide, tüm metin düzenleyiciyle oluşturulan C# kodunu (iki proje) keşfedebilir ve oluşturulan konsol uygulamasını `dotnet CLI` macOS, Linux veya Windows makinesi ile çalıştırabilirsiniz.

    ![CLı tarafından oluşturulan VS çözümü](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - Serileştirilmiş ML modeli (. zip dosyası) ve veri sınıfları (veri modelleri) içeren oluşturulmuş **sınıf kitaplığı** , doğrudan bu sınıf kitaplığına (veya istediğiniz şekilde kodu taşıyarak) doğrudan başvuru yaparak, Son Kullanıcı uygulamanızda doğrudan kullanabileceğiniz bir şeydir.
    - Oluşturulan **konsol uygulaması** , gözden geçirmeniz gereken yürütme kodunu içerir ve ardından genellikle bu basit kodu (yalnızca birkaç satır) tahmine dayalı hale getirmek istediğiniz son kullanıcı uygulamanıza taşıyarak ' Puanlama kodu ' nu (tahminleri yapmak için ml modelini çalıştıran kod) yeniden kullanırsınız.

1. **ModelInput.cs** ve **ModelOutput.cs** sınıf dosyalarını sınıf kitaplığı projesi içinde açın. Bu sınıfların, verileri tutmak için kullanılan ' veri sınıfları ' veya POCO sınıfları olduğunu görürsünüz. Bu, ' ortak kod ', ancak veri kümeniz yüzlerce veya hatta yüzlerce sütun içeriyorsa oluşturulmasını sağlamak için yararlıdır.
    - `ModelInput`Sınıf, veri kümesinden verileri okurken kullanılır.
    - `ModelOutput`Sınıfı, tahmin sonucunu (tahmin verileri) almak için kullanılır.

1. Program.cs dosyasını açın ve kodu araştırın. Yalnızca birkaç satırda modeli çalıştırabilir ve örnek bir tahmin yapabilirsiniz.

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - Kodun ilk satırı, bu örnekte tahmin için kullanılacak veri kümenizin ilk satırına göre *tek bir örnek veri*oluşturur. Ayrıca, kodu güncelleştirerek ' sabit kodlanmış ' verileri de oluşturabilirsiniz:

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - Sonraki kod satırı, `ConsumeModel.Predict()` bir tahmin yapmak ve sonuçları döndürmek (ModelOutput.cs şemasına göre) için belirtilen giriş verilerinde yöntemini kullanır.
    - Kodun son satırları, örnek verilerin (Bu örnekte açıklama) yanı sıra pozitif yaklaşım (1) ve olumsuz yaklaşım (2) için yaklaşım tahminini ve karşılık gelen puanları yazdırır.

1. Veri kümesinin ilk satırından yüklenen özgün örnek verileri kullanarak ya da kendi özel sabit kodlanmış örnek verilerinizi sağlayarak projeyi çalıştırın. Şu şekilde bir tahmin almanız gerekir:

![ML.NET CLı uygulamayı Visual Studio 'dan çalıştırma](./media/mlnet-cli/mlnet-cli-console-app.png))

1. Sabit kodlanmış örnek verileri farklı bir yaklaşım ile diğer cümleler ile değiştirmeyi deneyin ve modelin olumlu veya negatif yaklaşımı nasıl tahmin eder olduğunu görün.

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>ML modeli tahminleri ile Son Kullanıcı uygulamalarınızı kullanın

Modeli son kullanıcı uygulamanızda çalıştırmak ve tahmin yapmak için benzer ' ML model Puanlama kodu ' kullanabilirsiniz.

Örneğin, bu kodu doğrudan **WPF** ve **WinForms** gibi herhangi bir Windows masaüstü uygulamasına taşıyabilir ve modeli konsol uygulamasında yapılmayla aynı şekilde çalıştırabilirsiniz.

Ancak, bir ML modelini çalıştırmak için bu kod satırlarını uyguladığınızda,, özellikle uygulamanızın aşağıdaki bölümde açıklandığı gibi bir Web uygulaması veya dağıtılmış hizmet gibi ölçeklenebilir olması gerekiyorsa, her istekte bunları oluşturmak yerine tek tek nesnelere sahip olması gerekir (yani, model. zip dosyasını önbelleğe alır ve bunları bir kez yükler).

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Ölçeklenebilir ASP.NET Core Web uygulamaları ve Hizmetleri 'nde ML.NET modellerini çalıştırma (çok kanallı uygulamalar)

Model nesnesinin oluşturulması ( `ITransformer` bir modelin. zip dosyasından yüklenir) ve `PredictionEngine` nesne özellikle ölçeklenebilir Web uygulamaları ve dağıtılmış hizmetler üzerinde çalışırken iyileştirilmelidir. İlk durumda, model nesnesi ( `ITransformer` ) iyileştirmesi basittir. `ITransformer`Nesne iş parçacığı açısından güvenli olduğundan, modeli bir kez yüklemeniz için nesneyi tek veya statik bir nesne olarak önbelleğe alabilirsiniz.

Nesne iş parçacığı açısından güvenli olmadığından, ikinci nesne için nesnesi `PredictionEngine` Bu kadar kolay değildir `PredictionEngine` , bu nedenle bu nesneyi ASP.NET Core uygulamasında tek veya statik nesne olarak örnekleyemezsiniz. Bu iş parçacığı güvenli ve ölçeklenebilirlik sorunu bu [blog gönderisine](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)göre ele alınmıştır.

Ancak, bu blog gönderisinden açıklanamayan şeyler sizin için çok daha kolay. Sizin için daha basit bir yaklaşımda çalıştık ve uygulamayı uygulama ve hizmetASP.NET Core lerinize uygulama dı Hizmetleri 'ne (bağımlılık ekleme Hizmetleri) kaydederek ve sonra doğrudan kodunuzda kullanarak kolayca kullanabileceğiniz iyi bir **' .NET Core Integration Package '** oluşturdunuz. Şunları yapmak için aşağıdaki öğreticiyi ve örneğe bakın:

- [Öğretici: ML.NET modellerini ölçeklenebilir ASP.NET Core Web Apps ve WebAPIs üzerinde çalıştırma](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Örnek: ASP.NET Core WebAPI üzerinde ölçeklenebilir ML.NET modeli](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>"En iyi kalite" modelini eğitmek için kullanılan oluşturulan C# kodunu keşfet

Daha gelişmiş öğrenme amaçlarıyla, oluşturulan modeli eğitebilmeniz için CLı aracı tarafından kullanılan oluşturulan C# kodunu da keşfedebilirsiniz.

' Eğitim modeli kodu ' Şu anda adında oluşturulan özel sınıfta oluşturulmuştur, `ModelBuilder` böylece bu eğitim kodunu araştırabilirsiniz.

Daha önemlisi, bu senaryo (Yaklaşım Analizi modeli) için de, aşağıdaki öğreticide açıklanan kod ile bu üretilen eğitim kodunu karşılaştırabilirsiniz:

- Compare: [öğretici: bir yaklaşım Analizi ikili sınıflandırma senaryosunda ml.NET kullanın](sentiment-analysis.md).

Öğreticide seçilen algoritma ve işlem hattı yapılandırmasını CLı aracı tarafından oluşturulan kodla karşılaştırmak ilginç. Daha iyi modeller için ne kadar zaman harcadığınıza ve aradığınıza bağlı olarak, seçilen algoritma belirli Hyper-parametreleri ve işlem hattı yapılandırmasıyla birlikte farklı olabilir.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Verilerinizi seçilen ML görevi için hazırlayın (çözülme sorunu)
> - CLı aracında ' mlnet sınıflandırması ' komutunu çalıştırın
> - Kalite ölçümü sonuçlarını gözden geçirme
> - Modeli çalıştırmak için oluşturulan C# kodunu anlayın (Son Kullanıcı uygulamanızda kullanılacak kod)
> - "En iyi kalite" modelini (kazanlama amaçları) eğitmek için kullanılan oluşturulan C# kodunu keşfet

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLı ile model eğitimi otomatikleştirin](../automate-training-with-cli.md)
- [Öğretici: ML.NET modellerini ölçeklenebilir ASP.NET Core Web Apps ve WebAPIs üzerinde çalıştırma](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Örnek: ASP.NET Core WebAPI üzerinde ölçeklenebilir ML.NET modeli](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [ML.NET CLı otomatik eğitme komut başvuru kılavuzu](../reference/ml-net-cli-reference.md)
- [ML.NET CLı 'de telemetri](../resources/ml-net-cli-telemetry.md)
