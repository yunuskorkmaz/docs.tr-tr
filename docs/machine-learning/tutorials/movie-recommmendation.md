---
title: 'Öğretici: Bir film öneren - matris factorization oluşturun'
description: Bu öğreticide bir .NET Core konsol uygulaması içinde bir film öneren ML.NET ile derleme gösterilmektedir. Adımları C# ve Visual Studio 2019.
author: briacht
ms.author: johalex
ms.date: 05/06/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 512c8d663835da77c05fb24926ff85c56afd11ca
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882261"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a>Öğretici: Matris factorizaton ML.NET ile kullanarak bir film öneren oluşturun

Bu öğreticide bir .NET Core konsol uygulaması içinde bir film öneren ML.NET ile derleme gösterilmektedir. Adımları C# ve Visual Studio 2019.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Bir machine learning algoritması seçin
> * Verilerinizi yüklemek ve hazırlamak
> * Yapı ve model eğitme
> * Bir modeli değerlendirme
> * Dağıtma ve bir modeli kullanma

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) depo.

## <a name="machine-learning-workflow"></a>Machine learning iş akışı

Göreviniz yanı sıra diğer ML.NET görev gerçekleştirmek için aşağıdaki adımları kullanın:

1. [Veri yükleme](#load-your-data)
2. [Derleme ve modelinizi eğitin](#build-and-train-your-model)
3. [Modelinizi değerlendir](#evaluate-your-model)
4. [Modelinizi kullanın](#use-your-model)

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Öneri sorunları, filmler listesini önerme veya ilgili ürünler listesi öneren gibi yaklaşan çeşitli yolları vardır, ancak derecelendirme hangi (1-5) bir kullanıcı belirli bir filmi verin ve da ise, film önerir. Bu durumda tahmin tanımlı bir eşiğin (yüksek derecelendirme, bir kullanıcı belirli bir filmi özelleştirebilir olma olasılığı daha) daha yüksek.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "MovieRecommender" yazın ve ardından **Tamam** düğmesi.

2. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi depolamak için:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**. "Veri" yazın ve Enter tuşuna basın.

3. Yükleme **Microsoft.ML** ve **Microsoft.ML.Recommender** NuGet paketleri:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**. Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**seçin **1.0.0** paketini listede bulun ve seçin  **Yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz. Bu adımı yineleyin **Microsoft.ML.Recommender v0.12.0**.

4. Aşağıdaki `using` en üstündeki deyimleri, *Program.cs* dosyası:

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Verilerinizi indirin

1. İki veri kümesi indirmek ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör:

   * Sağ tıklayın [ *öneri derecelendirmeleri train.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) seçip "bağlantısına (veya hedef) olarak kaydedin. …"
   * Sağ tıklayın [ *öneri derecelendirmeleri test.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) seçip "bağlantısına (veya hedef) olarak kaydedin. …"

     Ya da kaydettiğinizden emin olun \*.csv dosyalarını *veri* klasöründe veya başka bir yerde kaydettikten sonra taşıma \*.csv dosyalarını *veri* klasör.

2. Her bir Çözüm Gezgini'nde sağ \*.csv dosyalarını ve select **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

   ![vs'de yeniyse Kopyala](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a>Veri yükleme

ML.NET sürecinde ilk adım, hazırlama ve model eğitiminin ve test verilerinin yük sağlamaktır.

Öneri derecelendirmeleri verileri bölün `Train` ve `Test` veri kümeleri. `Train` Veri modelinizi sığdırmak için kullanılır. `Test` Veri modeliniz eğitilen tahminlerde bulunabilir ve model performansını değerlendirme için kullanılır. Bölme bir 80/20 çok yaygındır `Train` ve `Test` veri.

Aşağıda verilerden önizlemesidir, \*.csv dosyaları:

![Veri önizlemesi](./media/movie-recommendation/csv-dataset-preview.png)

İçinde \*.csv dosyalarını dört sütun vardır:

* `userId`
* `movieId`
* `rating`
* `timestamp`

Machine learning'de bir tahminde bulunmak için kullanılan sütun olarak adlandırılan [özellikleri](../resources/glossary.md#feature), ve döndürülen tahmin sütunla çağrılır [etiket](../resources/glossary.md#label).

Film derecelendirme Derecelendirme sütunu, bu nedenle tahmin etmek istediğiniz `Label`. Diğer üç sütun `userId`, `movieId`, ve `timestamp` tümü `Features` tahmin etmek için kullanılan `Label`.

| Özellikler      | Etiketle         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

Hangi karar vermek için size kalmıştır `Features` tahmin etmek için kullanılan `Label`. Gibi yöntemleri de kullanabilirsiniz [özellik permütasyon önem](../how-to-guides/determine-global-feature-importance-in-model.md) en iyi seçme ile yardımcı olmak için `Features`.

Bu durumda, ortadan `timestamp` sütun olarak bir `Feature` zaman damgası gerçekten ne bir kullanıcı belirli bir filmi derecelendirir etkilemez ve böylece daha doğru bir tahmin yapmaya katkıda değil çünkü:

| Özellikler      | Etiketle         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Sonraki giriş sınıfı için data yapınız tanımlamanız gerekir.

Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle > Yeni öğe**.

2. İçinde **Yeni Öğe Ekle iletişim kutusu**seçin **sınıfı** değiştirip **adı** alanı *MovieRatingData.cs*. Ardından, **Ekle** düğmesi.

*MovieRatingData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *MovieRatingData.cs*:

```csharp
using Microsoft.ML.Data;
```

Adlı bir sınıf oluşturmak `MovieRating` varolan sınıf tanımına kaldırma ve aşağıdaki kodu ekleyerek *MovieRatingData.cs*:

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating` bir giriş veri sınıfı belirtir. [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği (sütun dizini tarafından) veri kümesindeki sütunları yüklenmesi gerektiğini belirtir. `userId` Ve `movieId` sütunlar, `Features` (girişleri tahmin modelini sunacak `Label`), ve Derecelendirme sütunu `Label` (modelin çıkış) tahmin.

Başka bir sınıf oluşturun `MovieRatingPrediction`, sonra aşağıdaki kodu ekleyerek tahmin edilen sonuçları göstermek için `MovieRating` sınıfını *MovieRatingData.cs*:

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

İçinde *Program.cs*, değiştirin `Console.WriteLine("Hello World!")` içinde aşağıdaki kodla `Main()`:

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

[MLContext sınıfı](xref:Microsoft.ML.MLContext) bir tüm ML.NET işlemleri için başlangıç noktası ve başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur. Bu, kavramsal olarak, benzer `DBContext` Entity Framework.

Sonra `Main()`, adında bir yöntem oluşturun `LoadData()`:

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Aşağıdaki adımlarda bir dönüş ifadesi eklenene kadar bu yöntem bir hata verir.

Veri yolu değişkenlerinizi başlatmak, verilerden yük \*.csv dosyalarını ve dönüş `Train` ve `Test` verileri olarak `IDataView` sonraki kod satırı olarak aşağıdakileri ekleyerek nesneleri `LoadData()`:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView). `IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur. Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur. Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`. Bu durumda, yolu sağlamak, `Test` ve `Train` dosyaları ve hem (sütun adları düzgün kullanabilmesi için) metin dosya üstbilgisi hem de (varsayılan ayırıcısı olan bir sekme) virgülle karakter veri ayırıcısı gösterir.

Sonraki iki kod satırlarını olarak aşağıdakileri ekleyin `Main()` çağrılacak yöntem, `LoadData()` yöntemi ve dönüş `Train` ve `Test` veri:

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Derleme ve modelinizi eğitin

ML.NET içinde üç ana kavramı vardır: [Veri](../resources/glossary.md#data), [dönüştürücüler](../resources/glossary.md#transformer), ve [Estimators](../resources/glossary.md#estimator).

Makine öğrenimi eğitim algoritmalar, verileri belirli bir biçimde gerektirir. `Transformers` tablosal veri uyumlu bir biçime dönüştürmek için kullanılır.

![Transformer görüntüsü](./media/movie-recommendation/transformer.png)

Oluşturduğunuz `Transformers` oluşturarak ML.NET içinde `Estimators`. `Estimators` veri ve dönüş ele `Transformers`.

![Tahmin görüntüsü](./media/movie-recommendation/estimator.png)

Örneğidir, modeli eğitmek için kullanacağınız öneri eğitim algoritması bir `Estimator`.

Derleme bir `Estimator` aşağıdaki adımları:

Oluşturma `BuildAndTrainModel()` yöntemi hemen sonrasına `LoadData()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Aşağıdaki adımlarda bir dönüş ifadesi eklenene kadar bu yöntem bir hata verir.

Aşağıdaki kodu ekleyerek veri dönüşümlerini tanımlamak `BuildAndTrainModel()`:

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

Bu yana `userId` ve `movieId` temsil kullanıcılar ve başlık, değil gerçek değerler kullandığınız [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) her dönüştürmek için yöntemi `userId` ve her `movieId` sayısal anahtar türü `Feature`sütun (öneri algoritmalarda kabul biçimi) ve bunları yeni dataset sütunları ekleyin:

| userId | movieId | Etiketle | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1. | 1. | 4 | userKey1 | movieKey1 |
| 1. | 3 | 4 | userKey1 | movieKey2 |
| 1. | 6 | 4 | userKey1 | movieKey3 |

Makine öğrenme algoritmasını seçin ve sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını ekleme `BuildAndTrainModel()`:

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) öneri eğitim algoritmasıdır.  [Matris Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) kullanıcıların geçmişte veri kümeleri için Bu öğreticide olduğu ürünleri nasıl değerlendirmiş şirket verileriniz öneri için yaygın bir yaklaşım gerekir. Farklı veri kullanılabilir olduğunda için diğer öneri algoritmalar vardır (bkz [diğer öneri algoritmalar](#other-recommendation-algorithms) daha fazla bilgi için aşağıdaki bölümü).

Bu durumda, `Matrix Factorization` daha sonra kullanıcı 1. büyük olasılıkla aynı biçimde kullanıcı 2 farklı bir sorunla ilgili olarak algoritması kullanıcı 1 kullanıcı 2 belirli bir sorunla ilgili olarak aynı fikrim varsa, olduğunu varsayar, "işbirliğine dayalı filtreleme" adlı bir yöntem kullanır.

Kullanıcı 1, kullanıcı 2 filmler benzer şekilde oranı, örneğin, ardından kullanıcı 2 kullanıcı 1 olan ve izlenen yüksek dereceli bir filmi keyfini çıkarın daha kolaydır:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Kullanıcı 1 | İzlenen ve bağlanan film | İzlenen ve bağlanan film | İzlenen ve bağlanan film |
| Kullanıcı 2 | İzlenen ve bağlanan film | İzlenen ve bağlanan film | Olmayan izlenen--ÖNERİ film |

`Matrix Factorization` Trainer sahip birkaç [seçenekleri](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), daha fazla ilgili bilgi de edinebilirsiniz hangi [algoritması hiperparametreleri](#algorithm-hyperparameters) bölümüne bakın.

Modele uygun `Train` veri ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `BuildAndTrainModel()` yöntemi:

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemine sağlanan bir eğitim veri kümesi modelinizi eğitir. Teknik olarak yürütür `Estimator` verileri dönüştürme ve eğitim ve uygulama tanımlarını döndürür geri olan eğitilen model bir `Transformer`.

Sonraki kod satırı olarak ekleyin `Main()` çağrılacak yöntem, `BuildAndTrainModel()` yöntemi ve dönüş eğitim modeli:

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Modelinizi değerlendir

Modelinizi eğitim almış sonra modelinizi performansını değerlendirmek için test verilerini kullanın.

Oluşturma `EvaluateModel()` yöntemi hemen sonrasına `BuildAndTrainModel()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Dönüştürme `Test` aşağıdakileri ekleyerek veri kod için `EvaluateModel()`: [!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, birden çok test veri kümesini girdi satırları sağlanan için Öngörüler sağlar.

Sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirme `EvaluateModel()` yöntemi:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Ayarlanırsa, tahmin sonra [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi değerlendirir gerçek tahmin edilen değerlerle karşılaştırır modeli `Labels` modelin nasıl performans gösterdiğini üzerinde test veri kümesini ve döndürür ölçümleri de.

Sonraki kod satırı olarak aşağıdakileri ekleyerek değerlendirme ölçümlerinizi konsola yazdırma `EvaluateModel()` yöntemi:

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

Sonraki kod satırı olarak ekleyin `Main()` çağrılacak yöntem, `EvaluateModel()` yöntemi:

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

Şu ana kadar çıktı aşağıdaki metne benzer görünmelidir:

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

Bu çıkış, 20 yinelemeler vardır. Her yinelemede hata ölçü azaltır ve daha yakın ve 0 yakın uygun sonuç verir.

`root of mean squared error` (RMS veya RMSE) tahmin modeli arasındaki farklılıklar ölçmek için kullanılan değerleri ve test veri kümesini gözlenen değerler. Teknik olarak hataları kareler Ortalama kare kökünü olduğu. Daha düşük olan, daha iyi modelidir.

`R Squared` veri modeli ne kadar iyi uyduğunu gösterir. 1 Aralık 0. Değeri 0 anlamına gelir veri rastgele veya başka türlü modele sığamıyorsa. Değeri model verileri tam olarak eşleşen 1 anlamına gelir. İstediğiniz, `R Squared` 1 olarak mümkün olduğunca yakın olmasını puanı.

Başarılı modeller oluşturma yinelemeli bir işlemdir. Bu model düşük ilk kalite hızlı modeli eğitimi sağlamak için öğretici kullanan küçük veri kümeleri sahiptir. Model kalitesi memnun değilseniz daha büyük bir eğitim veri kümeleri sağlama veya farklı hyper-parametreleriyle her bir algoritmanın için farklı eğitim algoritmalarıyla seçerek geliştirmek deneyebilirsiniz. Daha fazla bilgi için kullanıma [modelinizin geliştirilmesine](#improve-your-model) bölümüne bakın.

## <a name="use-your-model"></a>Modelinizi kullanın

Artık, eğitilen model üzerinde yeni veri tahmininde bulunmak amacıyla kullanabilirsiniz.

Oluşturma `UseModelForSinglePrediction()` yöntemi hemen sonrasına `EvaluateModel()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Kullanım `PredictionEngine` derecelendirme aşağıdaki kodu ekleyerek tahmin etmek için `UseModelForSinglePrediction()`:

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

[PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) verileri tek bir örneğini geçirin ve ardından bu tek veri örneğinde bir tahmin gerçekleştirin izin veren bir kolaylık API.

Bir örneğini oluşturmak `MovieRating` adlı `testInput` ve aşağıdaki kodda bir sonraki satırı olarak ekleyerek tahmin Altyapısı'na geçme `UseModelForSinglePrediction()` yöntemi:

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütununu tahmin sağlar.

Ardından `Score`, ya da kullanıcı 6 movieId 10 film önerilir isteyip istemediğinizi belirlemek için tahmin edilen derecelendirmesi. En yüksek `Score`, daha yüksek bir kullanıcı olasılığını belirli bir filmi özelleştirebilir. Bu durumda, tahmin edilen bir derecelendirme > 3.5 filmlerle önerilir varsayalım.

Sonuçları yazdırmak için sonraki kod satırlarını olarak aşağıdakileri ekleyin `UseModelForSinglePrediction()` yöntemi:

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

Sonraki kod satırı olarak ekleyin `Main()` çağrılacak yöntem, `UseModelForSinglePrediction()` yöntemi:

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Bu yöntem, çıktı aşağıdaki metne benzer görünmelidir:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Modelinizi Kaydet

Son kullanıcı uygulamaları tahminlerde bulunmak üzere modelinizi kullanmak için önce model kaydetmeniz gerekir.

Oluşturma `SaveModel()` yöntemi hemen sonrasına `UseModelForSinglePrediction()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void SaveModel(MLContext mlContext, ITransformer model)
{

}
```

Aşağıdaki kodu ekleyerek, eğitilen modeli kaydedin `SaveModel()` yöntemi:

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

Bu yöntem, eğitilen model sonra diğer .NET uygulamalarında tahminlerde bulunmak için kullanılabilecek bir .zip dosyası olarak ("Veri" klasöründe farklı olarak) kaydeder.

Sonraki kod satırı olarak ekleyin `Main()` çağrılacak yöntem, `SaveModel()` yöntemi:

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Kaydedilen modelinizi kullanın

Eğitilen model kaydedildikten sonra farklı ortamlarda modeli raporlarını kullanabilirsiniz (bkz ["Nasıl yapılır kılavuzunda"](../how-to-guides/consuming-model-ml-net.md) uygulamalarında eğitilen machine learning modeli kullanıma hazır hale getirme hakkında bilgi edinmek için).

## <a name="results"></a>Sonuçlar

Yukarıdaki adımları tamamladıktan sonra Konsol uygulamanızı (Ctrl + F5) çalıştırın. Yukarıdaki tek tahmin sonuçlarınızdan aşağıdakine benzer olmalıdır. Uyarı veya işlem iletileri görebilirsiniz, ancak bu iletiler anlaşılması için aşağıdaki sonuçları kaldırılmış olan.

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

Tebrikler! Bir machine learning modeli filmler önermek için artık başarıyla oluşturdunuz. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) depo.

## <a name="improve-your-model"></a>Modelinizi geliştirin

Daha doğru tahminler alabilmesi modelinizi performansını artırmak birkaç yol vardır.

### <a name="data"></a>Veri

Her kullanıcı ve film kimliği için yeterli örnekleri içeren daha fazla eğitim veri ekleme, öneri model kalitesini artırmaya yardımcı olabilir.

[Çapraz doğrulama](../how-to-guides/train-cross-validation-ml-net.md) değerlendirme modelleri, rastgele verilerin (Bu öğreticide yaptığınız gibi yerine test veri kümesindeki verileri dışarı ayıklanıyor) alt kümelerini böler ve bazı grupların test verileri ve bazı grupları eğitin alır bir tekniktir veriler. Bu yöntem, model kalitesi açısından bölme train-test yaparak daha iyi.

### <a name="features"></a>Özellikler

Bu öğreticide, yalnızca üç kullandığınız `Features` (`user id`, `movie id`, ve `rating`) veri kümesi tarafından sağlanır.

Bu çok iyi bir başlangıç olsa da, gerçekte, diğer öznitelikleri eklemek isteyebilirsiniz veya `Features` (örneğin, yaş, cinsiyet, coğrafi konum, vb.) kümesinde içeriyorsa. Daha fazla ilgili ekleme `Features` öneri modelinizin performansını artırmaya yardımcı olabilir.

Konusunda emin değilseniz `Features` machine learning göreviniz için en uygun olabilir, özellik katkı hesaplama (FCC) birini kullanmak de yapabilirsiniz ve [özellik permütasyon önem](../how-to-guides/determine-global-feature-importance-in-model.md), hangi ML.NET sağlar en etkili Bul `Features`.

### <a name="algorithm-hyperparameters"></a>Algoritma hiperparametreleri

ML.NET eğitim algoritmaları iyi varsayılan sağlasa da, daha fazla performans algoritması'nın değiştirerek ince ayar yapabilirsiniz [hiperparametreleri](../resources/glossary.md#hyperparameter).

İçin `Matrix Factorization`, gibi hiperparametreleri ile denemeler [Numberofıterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) ve [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) , size daha iyi sonuç verdiğini olmadığını görmek için.

Örneğin, bu öğreticide algoritması Seçenekler şunlardır:

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

### <a name="other-recommendation-algorithms"></a>Diğer öneri algoritmalar

Matris factorization algoritma işbirliğine dayalı filtreleme ile film önerileri gerçekleştirmek için yalnızca bir yaklaşımdır. Çoğu durumda, değil kullanılabilir derecelendirmeleri verilere sahip ve kullanıcıların film geçmiş yeterlidir. Diğer durumlarda, daha fazlasını kullanıcının derecelendirme veri olabilir.

| Algoritması       | Senaryo           | Örnek  |
| ------------- |:-------------:| -----:|
| Bir sınıf matris Factorization | Kullanıcı kimliği ve movieId yalnızca varsa bunu kullanın. Ortak satın alma senaryosu bu stil önerileri temel alır ve ürünleri sık birlikte müşterilere ürün kendi satın alma siparişi geçmişi dayalı bir kümesi dtu'lara anlamına satın. | [> deneyin](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Alan kullanan Factorization makineler | Daha fazla özellik UserID, ProductID ve derecelendirme (örneğin, ürün açıklaması veya ürün fiyatı) dışında olduğunda önerilerde için bunu kullanın. Bu yöntem, işbirliğine dayalı bir filtre yaklaşım da kullanır. | [> deneyin](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Yeni kullanıcı senaryosu

Ortak filtreleme bir yaygın sorun çıkarımı gelen çizmek için önceki veri içermeyen yeni bir kullanıcı varsa, hazırlıksız başlatma sorunudur. Bu sorun genellikle bir profil oluşturmak için yeni kullanıcılar isteyerek çözülür ve örneği için oranı filmler, geçmişte gördünüz. Bu yöntem, kullanıcı bazı yük koyar, ancak hiçbir derecelendirme geçmişi ile yeni kullanıcılar için bazı başlangıç verileri sağlar.

## <a name="resources"></a>Kaynaklar

Bu öğreticide kullanılan veri türetilir [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:

> [!div class="checklist"]
> * Bir machine learning algoritması seçin
> * Verilerinizi yüklemek ve hazırlamak
> * Yapı ve model eğitme
> * Bir modeli değerlendirme
> * Dağıtma ve bir modeli kullanma

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Yaklaşım analizi](sentiment-analysis.md)
