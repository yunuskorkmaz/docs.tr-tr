---
title: 'Öğretici: Bir film tavsiye oluştur - matris faktörizasyon'
description: Bu öğretici, .NET Core konsol uygulamasında ML.NET ile nasıl bir film tavsiye oluşturabileceğinizi gösterir. Adımlar c# ve Visual Studio 2019'u kullanır.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: a221289d0c232863f03a275c26dce835f2878bf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241110"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a>Öğretici: ML.NET ile matris çarpansama kullanarak bir film tavsiye oluştur

Bu öğretici, .NET Core konsol uygulamasında ML.NET ile nasıl bir film tavsiye oluşturabileceğinizi gösterir. Adımlar c# ve Visual Studio 2019'u kullanır.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> * Makine öğrenimi algoritması seçin
> * Verilerinizi hazırlama ve yükleme
> * Bir model oluşturma ve eğitme
> * Bir modeli değerlendirme
> * Bir modeli dağıtma ve tüket

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.

## <a name="machine-learning-workflow"></a>Makine öğrenimi iş akışı

Görevinizi gerçekleştirmek için aşağıdaki adımları ve diğer ML.NET görevleri kullanırsınız:

1. [Verilerinizi yükleyin](#load-your-data)
2. [Modelinizi oluşturun ve eğitin](#build-and-train-your-model)
3. [Modelinizi değerlendirme](#evaluate-your-model)
4. [Modelinizi kullanma](#use-your-model)

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Film listesi önermek veya ilgili ürünlerin bir listesini önermek gibi öneri sorunlarına yaklaşmanın çeşitli yolları vardır, ancak bu durumda bir kullanıcının belirli bir filme hangi derecelendirmeyi (1-5) vereceğini tahmin eder ve bu film tanımlanmış bir eşiğe göre daha yüksektir (derecelendirme ne kadar yüksekse, kullanıcının belirli bir filmi sevme olasılığı da o kadar yüksektir).

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 2017'yi açın. Menü çubuğundan**Yeni** > **Proje** **Dosyası'nı** > seçin. Yeni **Proje** iletişim kutusunda, **.NET Core** düğümünü izleyen **Visual C#** düğümünü seçin. Ardından **Konsol Uygulaması (.NET Core)** proje şablonu'nu seçin. **Ad** metin kutusunda "MovieRecommender" yazın ve **ardından Tamam** düğmesini seçin.

2. Veri kümesini depolamak için projenizde *Veri* adlı bir dizin oluşturun:

    **Çözüm Gezgini'nde**projeyi sağ tıklatın ve**Yeni Klasör** **Ekle'yi** > seçin. "Veri" yazın ve Enter tuşuna basın.

3. **Microsoft.ML** ve **Microsoft.ML.Recommender** NuGet Paketlerini yükleyin:

    **Çözüm Gezgini'nde**projeyi sağ tıklatın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, **Gözat** sekmesini seçin, **Microsoft.ML**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin. **Microsoft.ML.Recommender**için bu adımları yineleyin.

4. `using` *Program.cs* dosyanızın üst kısmında aşağıdaki ifadeleri ekleyin:

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Verilerinizi indirin

1. İki veri kümesini indirin ve bunları daha önce oluşturduğunuz *Veri* klasörüne kaydedin:

   * [*Tavsiye-ratings-train.csv'ye*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) sağ tıklayın ve "Bağlantıyı Kaydet (veya Hedef) Olarak..." seçeneğini belirleyin.
   * [*Öneri-derecelendirme-test.csv'ye*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) sağ tıklayın ve "Bağlantıyı Kaydet (veya Hedef) Olarak..." seçeneğini belirleyin.

     .csv dosyalarını \* *Veri* klasörüne kaydettiğinizi veya başka bir yere kaydettikten sonra \*.csv dosyalarını *Veri* klasörüne taşıdığınızdan emin olun.

2. Çözüm Gezgini'nde \*,.csv dosyalarının her birini sağ tıklatın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

   ![VS'de daha yeniyse kopya seçen bir kullanıcının GIF'i.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a>Verilerinizi yükleyin

ML.NET sürecinin ilk adımı, model eğitim ve test verilerinizi hazırlamak ve yüklemektir.

Öneri derecelendirme verileri `Train` bölünür `Test` ve veri kümelenir. Veriler `Train` modelinize uymak için kullanılır. Veriler, `Test` eğitimli modelinizle öngörülerde bulunmak ve model performansını değerlendirmek için kullanılır. Bir 80/20 ile `Train` bölünmüş ve `Test` veri olması yaygındır.

Aşağıda .csv dosyalarınızdaki \*verilerin bir önizlemesi verilmiştir:

![CVS veri kümesinin önizlemesinin ekran görüntüsü.](./media/movie-recommendation/csv-file-dataset-preview.png)

\*.csv dosyalarında dört sütun vardır:

* `userId`
* `movieId`
* `rating`
* `timestamp`

Makine öğreniminde, tahmin yapmak için kullanılan sütunlara [Özellikler,](../resources/glossary.md#feature)döndürülen tahmin içeren sütuna [ise Etiket](../resources/glossary.md#label)denir.

Film derecelendirmelerini tahmin etmek istiyorsunuz, bu `Label`nedenle derecelendirme sütunu . Diğer `userId`üç sütun, `movieId`, `timestamp` , `Features` ve tüm `Label`tahmin etmek için kullanılır .

| Özellikler      | Etiketle         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

Hangilerinin tahmin etmek için `Features` kullanılacağına karar `Label`vermek size kalmış. Ayrıca en iyi `Features`seçimi ile yardımcı olmak için [permütasyon özelliği önemi](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) gibi yöntemler kullanabilirsiniz.

Bu durumda, `timestamp` zaman damgası bir `Feature` kullanıcının belirli bir filmi nasıl oranlarını nitelemeyeceğini gerçekten etkilemediği ve böylece daha doğru bir tahminde bulunmaya katkıda bulunmayacağını zedeyi panlama olarak ortadan kaldırmalısınız:

| Özellikler      | Etiketle         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Daha sonra giriş sınıfı için veri yapınızı tanımlamanız gerekir.

Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini'nde**projeyi sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.

2. Yeni **Öğe Ekle iletişim kutusunda,** **Sınıf'ı** seçin ve **Ad** alanını *MovieRatingData.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

kod düzenleyicisinde *MovieRatingData.cs* dosyası açılır. MovieRatingData.cs üstüne `using` aşağıdaki ifadeyi *MovieRatingData.cs*ekleyin:

```csharp
using Microsoft.ML.Data;
```

Varolan sınıf `MovieRating` tanımını kaldırarak ve *MovieRatingData.cs*aşağıdaki kodu ekleyerek çağrılan bir sınıf oluşturun:

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating`bir giriş veri sınıfı belirtir. [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yüklenmesi gerektiğini belirtir. Ve `userId` `movieId` sütunlar `Features` sizin (modeli tahmin etmek için vereceğiniz `Label`girdiler) ve `Label` derecelendirme sütunu tahmin edeceğiniz (modelin çıktısI).

`MovieRatingPrediction` `MovieRating` *MovieRatingData.cs'da*sınıftan sonra aşağıdaki kodu ekleyerek tahmin edilen sonuçları temsil edecek başka bir sınıf oluşturun:

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

Program.cs *Program.cs*olarak, `Console.WriteLine("Hello World!")` içinde `Main()`aşağıdaki kodu ile değiştirin:

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç `mlContext` noktasıdır ve başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.

Sonra `Main()`, adlı `LoadData()`bir yöntem oluşturmak:

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Bu yöntem, aşağıdaki adımlarda bir iade deyimi ekleyene kadar size bir hata verecektir.

Veri yolu değişkenlerinizi \*başlatma, .csv dosyalarından gelen verileri `Train` yükleme `Test` ve `IDataView` aşağıdaki kodun bir sonraki satırı olarak `LoadData()`aşağıdakileri ekleyerek ve verileri nesne olarak döndürün:

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

ML.NET'daki veriler [IDataView sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`tabular verileri (sayısal ve metin) tanımlamanın esnek ve etkili bir yoludur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı `IDataView` veya günlük dosyaları) bir nesneye yüklenebilir.

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyada okur. Veri yolu değişkenlerini alır ve `IDataView`bir . Bu durumda, sizin ve `Test` `Train` dosyalarınız için yolu sağlar sınız ve hem metin dosyası üstbilgisini (sütun adlarını düzgün kullanabilsin diye) hem de virgül karakter veri ayırıcısını (varsayılan ayırıcı bir sekmedir) gösterirsiniz.

Yönteminizi `Main()` `LoadData()` çağırmak ve `Train` verileri `Test` döndürmek için yönteme aşağıdaki kodu ekleyin:

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Modelinizi oluşturun ve eğitin

ML.NET üç ana kavram vardır: [Veri](../resources/glossary.md#data), [Transformatörler](../resources/glossary.md#transformer), ve [Tahminciler](../resources/glossary.md#estimator).

Makine öğrenimi eğitim algoritmaları belirli bir biçimde veri gerektirir. `Transformers`tabular verileri uyumlu bir biçime dönüştürmek için kullanılır.

![Transformatör veri akışının diyagramı.](./media/movie-recommendation/data-transformer-transformed.png)

ML.NET'da `Transformers` oluşturarak `Estimators`oluşturursunuz. `Estimators`veri almak ve `Transformers`geri.

![Tahminci veri akışının diyagramı.](./media/movie-recommendation/data-estimator-transformer.png)

Modelinizi eğitmek için kullanacağınız öneri eğitim algoritması `Estimator`bir .

Aşağıdaki `Estimator` adımları içeren bir yapı oluşturun:

Yöntemden `BuildAndTrainModel()` `LoadData()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Bu yöntem, aşağıdaki adımlarda bir iade deyimi ekleyene kadar size bir hata verecektir.

Aşağıdaki kodu ekleyerek veri dönüşümlerini `BuildAndTrainModel()`tanımlayın:

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

Kullanıcıları `userId` `movieId` ve film başlıklarını gerçek değerler değil, temsil ettiği için, her `movieId` `userId` birini sayısal anahtar türü `Feature` sütununa (öneri algoritmaları tarafından kabul edilen bir biçim) dönüştürmek ve bunları yeni veri kümesi sütunları olarak eklemek için [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanırsınız:

| userId | movieId | Etiketle | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | movieKey1 |
| 1 | 3 | 4 | userKey1 | movieKey2 |
| 1 | 6 | 4 | userKey1 | movieKey3 |

Makine öğrenme algoritmasını seçin ve aşağıdaki kodu aşağıdaki satır olarak ekleyerek veri dönüştürme `BuildAndTrainModel()`tanımlarına eklemek:

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) tavsiye eğitim algoritmasıdır.  [Matris Çarpanları,](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) kullanıcıların geçmişte ürünleri nasıl derecelendirdiği hakkında veri ye sahip olduğunuzda, bu öğreticideki veri kümeleri için de geçerli olan yaygın bir öneri yaklaşımıdır. Farklı verileriniz olduğunda başka öneri algoritmaları da vardır (daha fazla bilgi edinmek için aşağıdaki [Diğer öneri algoritmaları](#other-recommendation-algorithms) bölümüne bakın).

Bu durumda, `Matrix Factorization` algoritma "işbirlikçi filtreleme" adı verilen bir yöntem kullanır ve kullanıcı 1'in belirli bir konuda Kullanıcı 2 ile aynı görüşe sahip olması durumunda, Kullanıcı 1'in farklı bir sorun hakkında Kullanıcı 2 ile aynı şekilde hissetme olasılığının daha yüksek olduğunu varsayar.

Örneğin, Kullanıcı 1 ve Kullanıcı 2 oranı benzer şekilde film varsa, Kullanıcı 2 kullanıcı 1'in izlediği ve yüksek puan verdiği bir filmden daha çok keyif alma olasılığı daha yüksektir:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Kullanıcı 1 | İzlenen ve beğenilen film | İzlenen ve beğenilen film | İzlenen ve beğenilen film |
| Kullanıcı 2 | İzlenen ve beğenilen film | İzlenen ve beğenilen film | İzlemedi -- FİlM ÖNER |

Eğitmen, `Matrix Factorization` aşağıdaki [Algoritma hiperparametreleri](#algorithm-hyperparameters) bölümünde hakkında daha fazla bilgi edinebileceğiniz birkaç [seçenek](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options)vardır.

Modeli `Train` verilere sığdırın ve yöntemde bir sonraki kod satırı olarak `BuildAndTrainModel()` aşağıdakileri ekleyerek eğitilmiş modeli döndürün:

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, modelinizi sağlanan eğitim veri kümesiyle eğitir. Teknik olarak, verileri `Estimator` dönüştürerek ve eğitimi uygulayarak tanımları yürütür ve eğitilen `Transformer`modeli geri döndürür.

`Main()` Yöntemde bir sonraki kod satırı olarak aşağıdakileri `BuildAndTrainModel()` ekleyin ve yönteminizi çağırın ve eğitilmiş modeli döndürün:

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Modelinizi değerlendirme

Modelinizi eğittikten sonra, modelinizin nasıl performans gösterdiğini değerlendirmek için test verilerinizi kullanın.

Yöntemden `EvaluateModel()` `BuildAndTrainModel()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Aşağıdaki `Test` kodu ekleyerek verileri dönüştürün: `EvaluateModel()`

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, bir test veri kümesinin birden çok sağlanan giriş satırı için öngörüler yapar.

Yöntemde bir sonraki kod satırı olarak aşağıdakileri `EvaluateModel()` ekleyerek modeli değerlendirin:

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Tahmin kümesini aldıktan sonra, Tahmin edilen değerleri test veri kümesindeki gerçek `Labels` değerlerle karşılaştıran ve modelin nasıl performans gösterdiğine ilişkin ölçümleri döndüren modeli [değerlendirin.](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A)

Yöntemde bir sonraki kod satırı olarak aşağıdakileri ekleyerek değerlendirme `EvaluateModel()` ölçümlerinizi konsola yazdırın:

[!code-csharp[PrintMetrics](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

Yöntemde bir sonraki kod `Main()` satırı olarak aşağıdakileri `EvaluateModel()` ekleyin:

[!code-csharp[EvaluateModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

Çıktı şimdiye kadar aşağıdaki metne benzer görünmelidir:

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

Bu çıktıda, 20 yineleme vardır. Her yinelemede hata ölçüsü azalır ve 0'a yaklaştıkça yakınlaşır.

`root of mean squared error` (RMS veya RMSE) model öngörülen değerler ve test veri kümesi gözlenen değerler arasındaki farkları ölçmek için kullanılır. Teknik olarak hataların kareortalamasının kare kökü. Ne kadar düşükse, model o kadar iyi olur.

`R Squared`verilerin bir modele ne kadar iyi uyduğunu gösterir. 0 ile 1 arasında değişir. 0 değeri, verilerin rastgele olduğu veya modele başka bir şekilde sığamayacağı anlamına gelir. 1 değeri, modelin verilerle tam olarak eşleştiğini anlamına gelir. Puanınızın `R Squared` mümkün olduğunca 1'e yakın olmasını istiyorsunuz.

Başarılı modeller oluşturmak yinelemeli bir işlemdir. Öğretici hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu model in ilk düşük kaliteye sahiptir. Model kalitesinden memnun değilseniz, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı hiper parametrelere sahip farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz. Daha fazla bilgi için aşağıdaki [modeli geliştir bölümüne](#improve-your-model) göz atın.

## <a name="use-your-model"></a>Modelinizi kullanma

Artık yeni veriler üzerinde öngörülerde bulunmak için eğitilmiş modelinizi kullanabilirsiniz.

Yöntemden `UseModelForSinglePrediction()` `EvaluateModel()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Aşağıdaki `PredictionEngine` kodu ekleyerek derecelendirme tahmin etmek `UseModelForSinglePrediction()`için kullanın:

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Tek dişli veya prototip ortamlarda kullanılabilir. Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın. ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.

> [!NOTE]
> `PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.

`MovieRating` Çağrıda bulunan `testInput` bir örnek oluşturun ve yöntemde bir sonraki kod satırları olarak aşağıdakileri ekleyerek Tahmin Motoru'na geçirin: `UseModelForSinglePrediction()`

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütununda bir tahminde bulunur.

Daha sonra movieId 10'dan kullanıcı6'ya film önermek isteyip istemediğinizi belirlemek için `Score`, veya öngörülen derecelendirmeyi kullanabilirsiniz. Ne kadar `Score`yüksekse, kullanıcının belirli bir filmi sevme olasılığı da o kadar yüksek. Bu durumda, 3,5 > öngörülen bir dereceye sahip filmleri önerdiğinizi varsayalım.

Sonuçları yazdırmak için yöntemde `UseModelForSinglePrediction()` sonraki kod satırları olarak aşağıdakileri ekleyin:

[!code-csharp[PrintResults](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

Yöntemde bir sonraki kod `Main()` satırı olarak aşağıdakileri `UseModelForSinglePrediction()` ekleyin:

[!code-csharp[UseModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Bu yöntemin çıktısı aşağıdaki metne benzer olmalıdır:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Modelinizi kaydedin

Son kullanıcı uygulamalarında öngörülerde bulunmak için modelinizi kullanmak için önce modeli kaydetmeniz gerekir.

Yöntemden `SaveModel()` `UseModelForSinglePrediction()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Yönteme aşağıdaki kodu ekleyerek eğitimli `SaveModel()` modelinizi kaydedin:

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

Bu yöntem, eğitimli modelinizi bir .zip dosyasına ("Veri" klasöründe) kaydeder ve bu dosya daha sonra diğer .NET uygulamalarında öngörülerde bulunmak için kullanılabilir.

Yöntemde bir sonraki kod `Main()` satırı olarak aşağıdakileri `SaveModel()` ekleyin:

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Kaydettiğiniz modeli kullanma

Eğitimli modelinizi kurtardıktan sonra, modeli farklı ortamlarda tüketebilirsiniz. Uygulamalarda eğitimli bir makine öğrenimi modelini nasıl işlevsel hale erdireceklerini öğrenmek için [eğitilmiş modelleri kaydet ve yükleyin.](../how-to-guides/save-load-machine-learning-models-ml-net.md)

## <a name="results"></a>Sonuçlar

Yukarıdaki adımları takip ettikten sonra konsol uygulamanızı (Ctrl + F5) çalıştırın. Yukarıdaki tek tahminden elde edilen sonuçlar aşağıdakilere benzer olmalıdır. Uyarılar veya iletileri işleme görebilirsiniz, ancak bu iletiler netlik için aşağıdaki sonuçlardan kaldırılmıştır.

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

Tebrikler! Şimdi başarılı film tavsiye için bir makine öğrenme modeli inşa ettik. Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.

## <a name="improve-your-model"></a>Modelinizi geliştirme

Daha doğru tahminler elde etmek için modelinizin performansını artırmanın birkaç yolu vardır.

### <a name="data"></a>Veriler

Her kullanıcı ve film kimliği için yeterli örnek olan daha fazla eğitim verisi eklemek, öneri modelinin kalitesini artırmaya yardımcı olabilir.

[Çapraz doğrulama,](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) verileri rasgele alt kümelere bölen modelleri (bu öğreticide yaptığınız gibi veri kümesinden test verilerini ayıklamak yerine) değerlendirmek için bir tekniktir ve bazı grupları tren verileri olarak, bazı grupları da test verisi olarak alır. Bu yöntem, model kalitesi açısından bir tren testi bölünmüş yapma daha iyi performans gösterir.

### <a name="features"></a>Özellikler

Bu öğreticide, yalnızca veri `Features` `user id`kümesi `movie id`tarafından `rating`sağlanan üç ( , , ve ) kullanırsınız.

Bu iyi bir başlangıç olsa da, gerçekte başka `Features` öznitelikler eklemek veya veri kümesine dahil edilirse (örneğin, yaş, cinsiyet, coğrafi konum, vb.) eklemek isteyebilirsiniz. Daha alakalı `Features` eklemek, öneri modelinizin performansını artırmaya yardımcı olabilir.

Makine öğrenimi göreviniz `Features` için hangisinin en uygun olabileceğinden emin değilseniz, ML.NET en etkili `Features`yi keşfetmenizi sağlayan Özellik Katkısı Hesaplama (FCC) ve [permütasyon özelliğinin önemini](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)de kullanabilirsiniz.

### <a name="algorithm-hyperparameters"></a>Algoritma hiperparametreleri

ML.NET iyi varsayılan eğitim algoritmaları sağlarken, algoritmanın [hiperparametrelerini](../resources/glossary.md#hyperparameter)değiştirerek performansı daha da ince ayarlayabilirsiniz.

Için, `Matrix Factorization`Size daha iyi sonuçlar verir olmadığını görmek için [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) ve [YaklaşıkRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) gibi hiperparametreler i deneme yapabilirsiniz.

Örneğin, bu öğreticide algoritma seçenekleri şunlardır:

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded",
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a>Diğer Öneri Algoritmaları

İşbirlikçi filtreleme ile matris çarpanlara ayırma algoritması film önerileri gerçekleştirmek için yalnızca bir yaklaşımdır. Çoğu durumda, derecelendirme verileriniz olmayabilir ve yalnızca kullanıcılardan kullanılabilen film geçmişiniz olabilir. Diğer durumlarda, kullanıcının derecelendirme verilerinden daha fazlanız olabilir.

| Algoritma       | Senaryo           | Örnek  |
| ------------- |:-------------:| -----:|
| Bir Sınıf Matris Çarpanekatizasyonu | Yalnızca userId ve movieId'invarsa bunu kullanın. Bu öneri stili, ortak satın alma senaryosuna veya sık sık birlikte satın alınan ürünlere dayanır, bu da müşterilere kendi satınalma siparişi geçmişlerine dayalı bir ürün kümesi önereceği anlamına gelir. | [>Deneyin](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Alan Farkında Faktoring Makineleri | UserId, productId ve derecelendirmenin ötesinde (ürün açıklaması veya ürün fiyatı gibi) daha fazla Özelliğe sahip olduğunuzda önerilerde bulunmak için bunu kullanın. Bu yöntem, ortak bir filtreleme yaklaşımı da kullanır. | [>Deneyin](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Yeni kullanıcı senaryosu

İşbirlikçi filtrelemede sık karşılaşılan bir sorun, çıkarımları çıkarımları yapacak önceki verileri olmayan yeni bir kullanıcıya sahip olduğunuzda soğuk başlangıç sorunudur. Bu sorun genellikle yeni kullanıcılardan bir profil oluşturmalarını isteyerek ve örneğin geçmişte gördükleri filmleri derecelendirerek çözülür. Bu yöntem kullanıcıya bazı yükler getirse de, derecelendirme geçmişi olmayan yeni kullanıcılar için bazı başlangıç verileri sağlar.

## <a name="resources"></a>Kaynaklar

Bu eğitimde kullanılan veriler [MovieLens Dataset'ten](http://files.grouplens.org/datasets/movielens/)türetilmiştir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:

> [!div class="checklist"]
>
> * Makine öğrenimi algoritması seçin
> * Verilerinizi hazırlama ve yükleme
> * Bir model oluşturma ve eğitme
> * Bir modeli değerlendirme
> * Bir modeli dağıtma ve tüket

Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin
> [!div class="nextstepaction"]
> [Duygusallık Analizi](sentiment-analysis.md)
