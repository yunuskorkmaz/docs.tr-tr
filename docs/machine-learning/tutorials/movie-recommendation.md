---
title: 'Öğretici: film oluşturma öneren-matris oluşturma'
description: Bu öğreticide, bir .NET Core konsol uygulamasında ML.NET ile bir film öneren oluşturma yöntemi gösterilmektedir. Adımları ve Visual C# Studio 2019 ' i kullanın.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 1db2ad6c078cb6201b2a6a4e2f8572f589cee684
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700960"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a>Öğretici: ML.NET ile matris factorizaton kullanarak bir film öneren oluşturma

Bu öğreticide, bir .NET Core konsol uygulamasında ML.NET ile bir film öneren oluşturma yöntemi gösterilmektedir. Adımları ve Visual C# Studio 2019 ' i kullanın.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Makine öğrenimi algoritması seçin
> * Verilerinizi hazırlayın ve yükleyin
> * Model oluşturma ve eğitme
> * Modeli değerlendirme
> * Bir modeli dağıtma ve kullanma

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.

## <a name="machine-learning-workflow"></a>Machine Learning iş akışı

Görevinizi ve diğer ML.NET görevlerini gerçekleştirmek için aşağıdaki adımları kullanacaksınız:

1. [Verilerinizi yükleme](#load-your-data)
2. [Modelinizi derleyin ve eğitme](#build-and-train-your-model)
3. [Modelinizi değerlendirin](#evaluate-your-model)
4. [Modelinizi kullanın](#use-your-model)

## <a name="prerequisites"></a>Prerequisites

* [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Bir film listesi önermek veya ilgili ürünlerin bir listesini önermek gibi öneri sorunlarına yaklaşımak için birkaç yol vardır. Bu durumda, bir kullanıcının belirli bir filmi hangi derecelendirmeye sunduu (1-5) tahmin edecek ve bu filmin tanımlı eşikten yüksek (derecelendirme arttıkça, bir kullanıcının belirli bir filmi beğenme olasılığı yüksektir).

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 2017 ' i açın. Menü çubuğundan **dosya** > **Yeni** > **Proje** ' yi seçin. **Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin. Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna "MovieRecommender" yazın ve **Tamam** düğmesini seçin.

2. Veri kümesini depolamak için projenizde *veri* adlı bir dizin oluşturun:

    **Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin. "Data" yazın ve ENTER tuşuna basın.

3. **Microsoft.ml** ve **Microsoft. ml. öneren** NuGet paketlerini yükler:

    **Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, **Araştır** sekmesini seçin, **Microsoft.ml**için arama yapın, listeden paketi seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin. **Microsoft. ml. öneren**için bu adımları tekrarlayın.

4. Aşağıdaki `using` deyimlerini *program.cs* dosyanızın üst kısmına ekleyin:

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Verilerinizi indirin

1. İki veri kümesini indirin ve daha önce oluşturduğunuz *veri* klasörüne kaydedin:

   * [*Recommendation-Ratings-train. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) ' ye sağ tıklayın ve "bağlantıyı (veya hedefi) farklı kaydet" i seçin.
   * [*Recommendation-Ratings-test. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) ' ye sağ tıklayın ve "bağlantıyı (veya hedefi) farklı kaydet" i seçin.

     @No__t -0. csv dosyalarını *veri* klasörüne kaydettiğinizden ya da başka bir yere kaydettikten sonra, @no__t -2. csv dosyalarını *veri* klasörüne taşıyın.

2. Çözüm Gezgini, @no__t -0. csv dosyalarının her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

   ![VS 'de daha yeniyse kopyala](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a>Verilerinizi yükleme

ML.NET işlemindeki ilk adım, model eğitimi ve test verilerini hazırlamaktır ve yükler.

Öneri derecelendirme verileri `Train` ve `Test` veri kümelerine bölünür. @No__t-0 verisi modelinize uyacak şekilde kullanılır. @No__t-0 verisi, eğitilen modelinizdeki tahminleri yapmak ve model performansını değerlendirmek için kullanılır. @No__t-0 ve `Test` verileri ile 80/20 bölüneceği için yaygındır.

Aşağıda @no__t -0. csv dosyalarınızda verilerin önizlemesi verilmiştir:

![verilerin önizlemesi](./media/movie-recommendation/csv-dataset-preview.png)

@No__t -0. csv dosyalarında dört sütun vardır:

* `userId`
* `movieId`
* `rating`
* `timestamp`

Machine Learning 'de, bir tahmin yapmak için kullanılan sütunlara [Özellikler](../resources/glossary.md#feature)denir ve döndürülen tahmine sahip olan sütuna [etiket](../resources/glossary.md#label)denir.

Film derecelendirmelerini tahmin etmek istiyorsunuz, bu nedenle Derecelendirme sütunu `Label` olur. @No__t-0, `movieId` ve `timestamp` diğer üç sütun, `Label` ' ü tahmin etmek için kullanılan `Features` ' ü kullanır.

| Özellikler      | Etiketle         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

@No__t-1 ' i tahmin etmek için kullanılacak `Features` ' a karar verirsiniz. Ayrıca, `Features` ' i seçmeye yardımcı olması için [özellik permütasyon önem derecesi](../how-to-guides/determine-global-feature-importance-in-model.md) gibi yöntemleri de kullanabilirsiniz.

Bu durumda, zaman damgası bir kullanıcının belirli bir filmi nasıl fiyatlandırdığı ve bu nedenle daha doğru bir tahmin yapma konusunda katkıda bulunmamasının gerektiği için `timestamp` sütununu `Feature` olarak ortadan kaldırmanız gerekir:

| Özellikler      | Etiketle         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Ardından, giriş sınıfı için veri yapınızı tanımlamanız gerekir.

Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **> yeni öğe Ekle**' yi seçin.

2. **Yeni öğe Ekle iletişim kutusunda** **sınıf** ' ı seçin ve **ad** alanını *MovieRatingData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

*MovieRatingData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadesini *MovieRatingData.cs*öğesinin en üstüne ekleyin:

```csharp
using Microsoft.ML.Data;
```

Mevcut sınıf tanımını kaldırarak `MovieRating` adlı bir sınıf oluşturun ve aşağıdaki kodu *MovieRatingData.cs*içine ekleyin:

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating` bir giriş veri sınıfını belirtir. [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yükleneceğini belirtir. @No__t-0 ve `movieId` sütunları `Features` ' dir (modele `Label` ' ü tahmin etmek için izin verdiğiniz girişler) ve derecelendirme sütunu, tahmin ettiğiniz `Label` ' ü (modelin çıktısı) sağlar.

*MovieRatingData.cs*içindeki `MovieRating` sınıfından sonra aşağıdaki kodu ekleyerek tahmin edilen sonuçları göstermek için `MovieRatingPrediction` olan başka bir sınıf oluşturun:

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

*Program.cs*' de `Console.WriteLine("Hello World!")` ' i `Main()` içindeki aşağıdaki kodla değiştirin:

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve @no__t başlatılıyor-1, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.

@No__t-0 ' dan sonra, `LoadData()` adlı bir yöntem oluşturun:

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Bu yöntem, aşağıdaki adımlarda bir return ifadesini eklemeene kadar bir hata verir.

Veri yolu değişkenlerinizi başlatın, @no__t -0. csv dosyalarından verileri yükleyin ve `LoadData()` ' te sonraki kod satırı olarak aşağıdakini ekleyerek @no__t 3 nesne olarak `Train` ve `Test` verileri döndürün:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) `IDataView` nesnesine yüklenebilir.

[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar. Veri yolu değişkenlerini alır ve `IDataView` döndürür. Bu durumda, `Test` ve `Train` dosyalarınız için yol sağlar ve hem metin dosyası üst bilgisini hem de (sütun adlarını düzgün bir şekilde kullanabilmesi için) virgül karakter veri ayırıcısını (varsayılan ayırıcı bir sekmedir) belirtin.

@No__t-1 yönteminizi çağırmak için `Main()` yöntemine aşağıdaki kodu ekleyin ve `Train` ve `Test` verilerini geri döndürün:

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Modelinizi derleyin ve eğitme

ML.NET: [Data](../resources/glossary.md#data), [dönüştürücüler](../resources/glossary.md#transformer)ve [estimators](../resources/glossary.md#estimator)'da üç önemli kavram vardır.

Machine Learning eğitim algoritmaları, verileri belirli bir biçimde gerektirir. `Transformers`, tablo verilerini uyumlu bir biçime dönüştürmek için kullanılır.

![Transformatör resmi](./media/movie-recommendation/transformer.png)

@No__t-1 oluşturarak, ML.NET içinde `Transformers` oluşturun. `Estimators` verileri alın ve `Transformers` döndürün.

![tahmin aracı resmi](./media/movie-recommendation/estimator.png)

Modelinize eğitim için kullanacağınız öneri eğitimi algoritması, `Estimator` ' a bir örnektir.

Aşağıdaki adımlarla bir `Estimator` oluşturun:

Aşağıdaki kodu kullanarak, `LoadData()` yönteminden hemen sonra `BuildAndTrainModel()` yöntemini oluşturun:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Bu yöntem, aşağıdaki adımlarda bir return ifadesini eklemeene kadar bir hata verir.

@No__t-0 ' a aşağıdaki kodu ekleyerek veri dönüşümlerini tanımlayın:

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

@No__t-0 ve `movieId`, gerçek değerleri değil kullanıcıları ve film başlıklarını temsil ettiğinden, her bir `userId` ' ü ve her `movieId` ' ü bir sayısal anahtar türü `Feature` sütununa (öneri algoritmalarının tarafından kabul edilen bir biçim) dönüştürmek için [Mapvaluetokey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanırsınız ve bunları yeni veri kümesi sütunları olarak ekleyin:

| UserID | Movieıd | Etiketle | Userıdencoded | Movieıdencoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1\. | 1\. | 4 | userKey1 | movieKey1 |
| 1\. | 3 | 4 | userKey1 | movieKey2 |
| 1\. | 6 | 4 | userKey1 | movieKey3 |

Machine Learning algoritmasını seçin ve `BuildAndTrainModel()` ' a bir sonraki kod satırı olarak aşağıdakini ekleyerek veri dönüştürme tanımlarına ekleyin:

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[Matrixfactorizationtrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) , öneri eğitim algoritmanız.  [Matris](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) , kullanıcıların geçmişte ürünleri derecelendirirken, bu öğreticideki veri kümeleri için büyük/küçük bir yaklaşım olan genel bir yaklaşımdır. Farklı verilere sahip olduğunuzda kullanabileceğiniz başka öneri algoritmaları vardır (daha fazla bilgi için aşağıdaki [diğer öneri algoritmaları](#other-recommendation-algorithms) bölümüne bakın).

Bu durumda, `Matrix Factorization` algoritması "işbirliğine dayalı filtreleme" adlı bir yöntem kullanır. Bu, Kullanıcı 1 ' in belirli bir sorun üzerinde Kullanıcı 2 ' de aynı görüşe sahip olduğunu varsaymışsa, 1. Kullanıcı farklı bir sorun hakkında Kullanıcı 2 ' ye benzer şekilde daha olasıdır.

Örneğin, Kullanıcı 1 ve Kullanıcı 2 filmleri benzer şekilde kullanıyorsanız, 1. Kullanıcı 2 ' nin, Kullanıcı 1 ' in izlenen ve yüksek oranda derecelendirdikleri bir filmin keyfini çıkarmak daha yüksektir:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Kullanıcı 1 | İzlenen ve beğenilen film | İzlenen ve beğenilen film | İzlenen ve beğenilen film |
| Kullanıcı 2 | İzlenen ve beğenilen film | İzlenen ve beğenilen film | İzleniyor--film öner |

@No__t-0 eğitmen, aşağıdaki [algoritma hiper parametreleri](#algorithm-hyperparameters) bölümünde hakkında daha fazla bilgi edinmek için çeşitli [seçeneklere](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options)sahiptir.

Modeli `Train` verilerine sığdırın ve `BuildAndTrainModel()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen modeli döndürün:

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, modelinizi belirtilen eğitim veri kümesiyle eğliyor. Teknik olarak, verileri dönüştürerek ve eğitimi uygulayarak `Estimator` tanımlarını yürütür ve bir `Transformer` olan eğitilen modeli geri döndürür.

@No__t-1 yönteminizi çağırmak ve eğitilen modeli döndürmek için `Main()` yöntemine sonraki kod satırı olarak aşağıdakini ekleyin:

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Modelinizi değerlendirin

Modelinizi eğittikten sonra, modelinizin nasıl çalıştığını değerlendirmek için test verilerinizi kullanın.

Aşağıdaki kodu kullanarak, `BuildAndTrainModel()` yönteminden hemen sonra `EvaluateModel()` yöntemini oluşturun:

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Aşağıdaki kodu `EvaluateModel()` ' e ekleyerek `Test` verisini dönüştürün:

[!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapar.

@No__t-0 yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirin:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Tahmin kümesine sahip olduktan sonra, değerlendirir [()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi, tahmin edilen değerleri test veri kümesindeki gerçek `Labels` ile karşılaştıran ve modelin nasıl çalıştığı ile ilgili ölçümleri döndüren modeli.

Aşağıdaki kod satırı olarak `EvaluateModel()` yöntemine ekleyerek değerlendirme ölçümlerini konsola yazdırın:

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

@No__t-1 yönteminizi çağırmak için `Main()` yöntemine sonraki kod satırı olarak aşağıdakini ekleyin:

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

Şu ana kadar çıkış aşağıdaki metne benzer görünmelidir:

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

Bu çıktıda 20 yineleme vardır. Her yinelemede, hata ölçüsü azalır ve 0 ' a yaklaştırır.

@No__t-0 (RMS veya rmo), model tahmin edilen değerler ve test veri kümesi gözlenen değerleri arasındaki farkları ölçmek için kullanılır. Teknik olarak, hataların karelerinin ortalamasının karekökünü temel alır. Bunun ne kadar küçük olması, modelin ne kadar iyi olduğu.

`R Squared`, verilerin modele ne kadar iyi uyduğunu gösterir. 0 ile 1 arasında aralıklar. 0 değeri, verilerin rastgele olması veya başka türlü modele sığamayacak olması anlamına gelir. 1 değeri, modelin verilerle tam olarak eşleştiği anlamına gelir. @No__t-0 puanınızın mümkün olduğunca 1 ' e yakın olmasını istiyorsunuz.

Başarılı modellerin oluşturulması, yinelemeli bir işlemdir. Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır. Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı Hyper-parametreleri ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz. Daha fazla bilgi için aşağıdaki [modelinizi geliştirme](#improve-your-model) bölümünü inceleyin.

## <a name="use-your-model"></a>Modelinizi kullanın

Artık yeni verilerde öngörülere sahip olmak için eğitilen modeli kullanabilirsiniz.

Aşağıdaki kodu kullanarak, `EvaluateModel()` yönteminden hemen sonra `UseModelForSinglePrediction()` yöntemini oluşturun:

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Aşağıdaki kodu `UseModelForSinglePrediction()` ' e ekleyerek derecelendirmeyi tahmin etmek için `PredictionEngine` kullanın:

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın. [ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın

> [!NOTE]
> `PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.

@No__t-1 adlı @no__t bir örnek oluşturun ve aşağıdaki kod satırları `UseModelForSinglePrediction()` yöntemine ekleyerek bunu tahmin altyapısına geçirin:

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

PREDICT [()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütunu üzerinde bir tahmin yapar.

Ardından, filmi Kullanıcı 6 ' ya Movieıd 10 ile önermek isteyip istemediğinizi öğrenmek için `Score` veya tahmin edilen derecelendirmeyi kullanabilirsiniz. @No__t-0 arttıkça, bir kullanıcının belirli bir filmi beğenme olasılığı yüksektir. Bu durumda, > 3,5 ' nin tahmin edilen derecelendirmesine sahip filmler önertiğinizi varsayalım.

Sonuçları yazdırmak için, `UseModelForSinglePrediction()` yöntemine sonraki kod satırları olarak aşağıdakini ekleyin:

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

@No__t-1 yönteminizi çağırmak için `Main()` yöntemine sonraki kod satırı olarak aşağıdakini ekleyin:

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Bu yöntemin çıktısı aşağıdaki metne benzer görünmelidir:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Modelinizi kaydetme

Son Kullanıcı uygulamalarında tahmine dayalı hale getirmek üzere modelinizi kullanmak için önce modeli kaydetmeniz gerekir.

Aşağıdaki kodu kullanarak, `UseModelForSinglePrediction()` yönteminden hemen sonra `SaveModel()` yöntemini oluşturun:

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

@No__t-0 yöntemine aşağıdaki kodu ekleyerek eğitilen modelinizi kaydedin:

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

Bu yöntem, eğitilen modelinizi, daha sonra tahmine dayalı hale getirmek için diğer .NET uygulamalarında kullanılabilecek bir. zip dosyasına ("veri" klasöründe) kaydeder.

@No__t-1 yönteminizi çağırmak için `Main()` yöntemine sonraki kod satırı olarak aşağıdakini ekleyin:

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Kayıtlı modelinizi kullanın

Eğitilen modelinizi kaydettikten sonra modeli farklı ortamlarda kullanabilirsiniz (uygulamalarda eğitilen bir makine öğrenimi modelinin nasıl yapılacağını öğrenmek için bkz. ["nasıl yapılır Kılavuzu"](../how-to-guides/consuming-model-ml-net.md) ).

## <a name="results"></a>Sonuçlar

Yukarıdaki adımları tamamladıktan sonra konsol uygulamanızı çalıştırın (CTRL + F5). Yukarıdaki tek bir tahmine ait sonuçlarınız aşağıdakine benzer olmalıdır. Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.

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

Mühendisi! Artık film öneren bir makine öğrenimi modelini başarıyla oluşturdunuz. Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.

## <a name="improve-your-model"></a>Modelinizi geliştirme

Daha doğru öngörülere ulaşmak için modelinizin performansını iyileştirebilmeniz için birkaç yol vardır.

### <a name="data"></a>Veri

Her Kullanıcı ve film kimliği için yeterli sayıda örnek içeren eğitim verileri eklemek, öneri modelinin kalitesini artırmaya yardımcı olabilir.

[Çapraz doğrulama](../how-to-guides/train-cross-validation-ml-net.md) , verileri rastgele kümeler halinde ayırır (Bu öğreticide yaptığınız gibi veri kümesinden test verilerinin ayıklanmasının yerine) ve bazı gruplardan verileri test verileri olarak eğitme ve gruplardan bazılarını alan bir yöntem. Bu yöntem, model kalitesi açısından bir eğitme testi ayırma yapmayı gerçekleştirir.

### <a name="features"></a>Özellikler

Bu öğreticide, yalnızca veri kümesi tarafından sunulan üç @no__t (`user id`, `movie id` ve `rating`) kullanacaksınız.

Bu iyi bir başlangıç olsa da, gerçekte veri kümesine dahil ediliyorlarsa diğer öznitelikleri veya `Features` (örneğin, Age, cinsiyet, coğrafi konum vb.) eklemek isteyebilirsiniz. Daha fazla ilgili @no__t eklemek, öneri modelinizin performansını artırmaya yardımcı olabilir.

Machine Learning göreviniz için en uygun olan `Features` ' ı bilmiyorsanız, özellik katkı hesaplaması (FCC) ve [özellik permütasyon önem](../how-to-guides/determine-global-feature-importance-in-model.md)derecesini de kullanabilirsiniz. bu, ml.net 'in en etkili olduğunu keşfetmesini sağlar `Features`.

### <a name="algorithm-hyperparameters"></a>Algoritma hiper parametreleri

ML.NET, iyi varsayılan eğitim algoritmaları sağlarken, algoritmanın [hiper parametrelerini](../resources/glossary.md#hyperparameter)değiştirerek performansı daha ayrıntılı bir şekilde ayarlayabilirsiniz.

@No__t-0 için, [Numberofiterasyonların](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) ve [yaklaşık](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) olarak daha iyi sonuçlar verir.

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

### <a name="other-recommendation-algorithms"></a>Diğer öneri algoritmaları

Ortak filtreleme ile matris ayırma algoritması, film önerileri gerçekleştirmeye yönelik yalnızca bir yaklaşımdır. Çoğu durumda, derecelendirme verileri kullanılabilir olmayabilir ve yalnızca film geçmişi kullanıcılardan bulunabilir. Diğer durumlarda, yalnızca kullanıcının derecelendirme verilerinden daha fazlasına sahip olabilirsiniz.

| Algoritmalar       | Senaryo           | Örnek  |
| ------------- |:-------------:| -----:|
| Bir sınıf matrisi oluşturma | Yalnızca Kullanıcı kimliği ve Movieıd olduğunda bunu kullanın. Bu öneri stili, ortak satın alma senaryosuna veya genellikle birlikte satın alınan ürünlere dayalıdır. Bu, müşterilerin kendi satın alma siparişi geçmişine göre bir ürün kümesi önermesini önermeyeceği anlamına gelir. | [> deneyin](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Alan duyarlı bir ayırma makinesi | Kullanıcı kimliği, ProductID ve derecelendirmeden daha fazla özelliğe sahip olduğunuzda (ürün açıklaması veya ürün fiyatı gibi) öneri sağlamak için bunu kullanın. Bu yöntem ayrıca birlikte çalışan bir filtreleme yaklaşımı kullanır. | [> deneyin](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Yeni Kullanıcı senaryosu

İşbirliğine dayalı filtrelemede yaygın olarak karşılaşılan bir sorun, yeni bir kullanıcıya, ıntreler eklemek için önceki verileri olmayan yeni bir kullanıcı olduğunda oluşan soğuk başlatma sorunudur. Bu sorun genellikle yeni kullanıcılardan bir profil oluşturmasını isteyerek ve örneğin, geçmişte gördüğü filmleri derecelendirmek için çözülür. Bu yöntem kullanıcıya bazı yük koyar, ancak derecelendirme geçmişi olmayan yeni kullanıcılar için bazı veri başlatma verileri sağlar.

## <a name="resources"></a>Kaynaklar

Bu öğreticide kullanılan veriler [Movielens veri kümesinden](http://files.grouplens.org/datasets/movielens/)türetilir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, nasıl yapılacağını öğrendiniz:

> [!div class="checklist"]
>
> * Makine öğrenimi algoritması seçin
> * Verilerinizi hazırlayın ve yükleyin
> * Model oluşturma ve eğitme
> * Modeli değerlendirme
> * Bir modeli dağıtma ve kullanma

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin
> [!div class="nextstepaction"]
> [Yaklaşım Analizi](sentiment-analysis.md)
