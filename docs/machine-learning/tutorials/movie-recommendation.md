---
title: 'Öğretici: film oluşturma öneren-matris oluşturma'
description: Bu öğreticide, bir .NET Core konsol uygulamasında ML.NET ile bir film öneren oluşturma yöntemi gösterilmektedir. Bu adımlarda C# ve Visual Studio 2019 kullanılır.
author: briacht
ms.date: 06/30/2020
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 39c4aeef0b02a6bf47d78e6bf53cd42b4f592946
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282105"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a>Öğretici: ML.NET ile matris factoru kullanarak bir film öneren oluşturma

Bu öğreticide, bir .NET Core konsol uygulamasında ML.NET ile bir film öneren oluşturma yöntemi gösterilmektedir. Bu adımlarda C# ve Visual Studio 2019 kullanılır.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:
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
3. [Modelinizi değerlendirme](#evaluate-your-model)
4. [Modelinizi kullanma](#use-your-model)

## <a name="prerequisites"></a>Ön koşullar

* [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri, ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Bir film listesi önermek veya ilgili ürünlerin bir listesini önermek gibi öneri sorunlarına yaklaşımak için birkaç yol vardır. Bu durumda, bir kullanıcının belirli bir filmi hangi derecelendirmeden (1-5) sunabileceği ve bu filmin tanımlı bir eşikten yüksek olması (derecelendirme arttıkça, bir kullanıcının belirli bir filmi beğenmesinin daha yükseği) tahmin edilmesi önerilir.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 2017'yi açın. Menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje** ' yi seçin. **Yeni proje** iletişim kutusunda, **Visual C#** düğümünü ve ardından **.NET Core** düğümünü seçin. Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna "MovieRecommender" yazın ve **Tamam** düğmesini seçin.

2. Veri kümesini depolamak için projenizde *veri* adlı bir dizin oluşturun:

    **Çözüm Gezgini**, projeye sağ tıklayın ve **Add**  >  **Yeni klasör**Ekle ' yi seçin. "Data" yazın ve ENTER tuşuna basın.

3. **Microsoft.ml** ve **Microsoft. ml. öneren** NuGet paketlerini yükler:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    **Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, **Araştır** sekmesini seçin, **Microsoft.ml**için arama yapın, listeden paketi seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin. **Microsoft. ml. öneren**için bu adımları tekrarlayın.

4. `using` *Program.cs* dosyanızın en üstüne aşağıdaki deyimleri ekleyin:

    [!code-csharp[UsingStatements](./snippets/movie-recommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Verilerinizi indirin

1. İki veri kümesini indirin ve daha önce oluşturduğunuz *veri* klasörüne kaydedin:

   * [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) sağ tıklayıp "bağlantıyı (veya hedefi) farklı kaydet" i seçin.
   * [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) sağ tıklayıp "bağlantıyı (veya hedefi) farklı kaydet" i seçin.

     \*. Csv dosyalarını *veri* klasörüne kaydettiğinizden emin olun veya başka bir yere kaydettikten sonra \* . csv dosyalarını *veri* klasörüne taşıyın.

2. Çözüm Gezgini,. csv dosyalarının her birine sağ tıklayın \* ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

   ![Bir kullanıcının GIF 'i, VS 'de daha yeniyse kopyala ' yı seçin.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a>Verilerinizi yükleme

ML.NET işlemindeki ilk adım, model eğitimi ve test verilerini hazırlamaktır ve yükler.

Öneri derecelendirme verileri, `Train` ve veri kümelerine ayrılır `Test` . `Train`Veriler modelinize uyacak şekilde kullanılır. `Test`Veriler, eğitilen modelinizdeki tahminleri yapmak ve model performansını değerlendirmek için kullanılır. Ve verileri içeren bir 80/20 bölünmesi yaygındır `Train` `Test` .

. Csv dosyalarınızda verilerin önizlemesi aşağıda verilmiştir \* :

![CVS veri kümesinin önizlemesinin ekran görüntüsü.](./media/movie-recommendation/csv-file-dataset-preview.png)

\*. Csv dosyalarında dört sütun vardır:

* `userId`
* `movieId`
* `rating`
* `timestamp`

Machine Learning 'de, bir tahmin yapmak için kullanılan sütunlara [Özellikler](../resources/glossary.md#feature)denir ve döndürülen tahmine sahip olan sütuna [etiket](../resources/glossary.md#label)denir.

Film derecelendirmelerini tahmin etmek istiyorsunuz, bu nedenle Derecelendirme sütunu `Label` . Diğer üç sütun,, `userId` `movieId` ve, `timestamp` `Features` tahmin etmek için kullanılır `Label` .

| Özellikler      | Etiketle         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

' İ `Features` tahmin etmek için ne kadar kullanıldığına karar verirsiniz `Label` . En iyi seçimi seçmenize yardımcı olmak için [permütasyon özelliği önem derecesi](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) gibi yöntemleri de kullanabilirsiniz `Features` .

Bu durumda, `timestamp` `Feature` zaman damgası bir kullanıcının belirli bir filmi nasıl derecelendirmediğini etkilemediği ve bu nedenle daha doğru bir tahmin yapmaya katkıda bulunmamasının gerektiği için sütunu bir olarak kaldırmanız gerekir:

| Özellikler      | Etiketle         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Ardından, giriş sınıfı için veri yapınızı tanımlamanız gerekir.

Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **> yeni öğe Ekle**' yi seçin.

2. **Yeni öğe Ekle iletişim kutusunda** **sınıf** ' ı seçin ve **ad** alanını *MovieRatingData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

*MovieRatingData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *MovieRatingData.cs*öğesinin en üstüne ekleyin:

```csharp
using Microsoft.ML.Data;
```

`MovieRating`Var olan sınıf tanımını kaldırarak ve *MovieRatingData.cs*içinde aşağıdaki kodu ekleyerek adlı bir sınıf oluşturun:

[!code-csharp[MovieRatingClass](./snippets/movie-recommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating`bir giriş veri sınıfını belirtir. [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yükleneceğini belirtir. `userId`Ve `movieId` sütunları `Features` (modelin tahmin edilmesine izin verilecek girişler `Label` ) ve derecelendirme sütunu, tahmin ettiğiniz ' dir `Label` (modelin çıktısı).

`MovieRatingPrediction` `MovieRating` *MovieRatingData.cs*içindeki sınıftan sonra aşağıdaki kodu ekleyerek tahmin edilen sonuçları temsil eden başka bir sınıf oluşturun:

[!code-csharp[PredictionClass](./snippets/movie-recommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

*Program.cs*' de, öğesini `Console.WriteLine("Hello World!")` içinde aşağıdaki kodla değiştirin `Main()` :

[!code-csharp[MLContext](./snippets/movie-recommendation/csharp/Program.cs#MLContext "Add MLContext")]

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor, `mlContext` model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal olarak da benzerdir `DBContext` .

Sonra `Main()` , adlı bir yöntem oluşturun `LoadData()` :

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Bu yöntem, aşağıdaki adımlarda bir return ifadesini eklemeene kadar bir hata verir.

Veri yolu değişkenlerinizi başlatın, \* . csv dosyalarından verileri yükleyin ve `Train` `Test` `IDataView` Aşağıdaki kod satırı olarak aşağıdakini ekleyerek nesne olarak ve verileri döndürün `LoadData()` :

[!code-csharp[LoadData](./snippets/movie-recommendation/csharp/Program.cs#LoadData "Load data from data paths")]

ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.

[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar. Veri yolu değişkenlerini alır ve döndürür `IDataView` . Bu durumda, ve dosyalarınız için yol sağlar `Test` `Train` ve hem metin dosyası üst bilgisini hem de (sütun adlarını düzgün bir şekilde kullanabilmesi için) virgül karakter veri ayırıcısını (varsayılan ayırıcı bir sekmedir) belirtin.

Yöntemi `Main()` çağırmak `LoadData()` ve ve verilerini döndürmek için yöntemine aşağıdaki kodu ekleyin `Train` `Test` :

[!code-csharp[LoadDataMain](./snippets/movie-recommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Modelinizi derleyin ve eğitme

ML.NET: [Data](../resources/glossary.md#data), [dönüştürücüler](../resources/glossary.md#transformer)ve [estimators](../resources/glossary.md#estimator)'da üç önemli kavram vardır.

Machine Learning eğitim algoritmaları, verileri belirli bir biçimde gerektirir. `Transformers`tablo verilerini uyumlu bir biçime dönüştürmek için kullanılır.

![Transformatör veri akışının diyagramı.](./media/movie-recommendation/data-transformer-transformed.png)

`Transformers`Oluşturarak ml.NET içinde oluşturursunuz `Estimators` . `Estimators`verileri alın ve döndürün `Transformers` .

![Estimator veri akışının diyagramı.](./media/movie-recommendation/data-estimator-transformer.png)

Modelinize eğitim için kullanacağınız öneri eğitimi algoritması bir örneğidir `Estimator` .

`Estimator`Aşağıdaki adımlarla bir oluşturun:

`BuildAndTrainModel()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `LoadData()` :

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Bu yöntem, aşağıdaki adımlarda bir return ifadesini eklemeene kadar bir hata verir.

Aşağıdaki kodu öğesine ekleyerek veri dönüşümlerini tanımlayın `BuildAndTrainModel()` :

[!code-csharp[DataTransformations](./snippets/movie-recommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

, `userId` `movieId` Gerçek değerleri değil kullanıcıları ve film başlıklarını da temsil ettiğinden, her bir sayısal anahtar türü sütununa (öneri algoritmaları tarafından kabul edilen bir biçim) dönüştürmek ve bunları yeni veri kümesi sütunları olarak eklemek Için [Mapvaluetokey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanırsınız `userId` `movieId` `Feature` :

| userId | Movieıd | Etiketle | Userıdencoded | Movieıdencoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | movieKey1 |
| 1 | 3 | 4 | userKey1 | movieKey2 |
| 1 | 6 | 4 | userKey1 | movieKey3 |

Machine Learning algoritmasını seçin ve aşağıdaki kod satırı olarak aşağıdakini ekleyerek veri dönüştürme tanımlarına ekleyin `BuildAndTrainModel()` :

[!code-csharp[AddAlgorithm](./snippets/movie-recommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[Matrixfactorizationtrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) , öneri eğitim algoritmanız.  [Matris](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) , kullanıcıların geçmişte ürünleri derecelendirirken, bu öğreticideki veri kümeleri için büyük/küçük bir yaklaşım olan genel bir yaklaşımdır. Farklı verilere sahip olduğunuzda kullanabileceğiniz başka öneri algoritmaları vardır (daha fazla bilgi için aşağıdaki [diğer öneri algoritmaları](#other-recommendation-algorithms) bölümüne bakın).

Bu durumda, `Matrix Factorization` algoritma "işbirliğine dayalı filtreleme" adlı bir yöntem kullanır. Bu, Kullanıcı 1 ' in belirli bir sorun üzerinde Kullanıcı 2 ' de aynı görüşe sahip olduğunu varsaydığı, 1. Kullanıcı farklı bir sorun hakkında Kullanıcı 2 ' yi aynı şekilde hissetmesinin daha olasıdır.

Örneğin, Kullanıcı 1 ve Kullanıcı 2 filmleri benzer şekilde kullanıyorsanız, 1. Kullanıcı 2 ' nin, Kullanıcı 1 ' in izlenen ve yüksek oranda derecelendirdikleri bir filmin keyfini çıkarmak daha yüksektir:

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Kullanıcı 1 | İzlenen ve beğenilen film | İzlenen ve beğenilen film | İzlenen ve beğenilen film |
| Kullanıcı 2 | İzlenen ve beğenilen film | İzlenen ve beğenilen film | İzleniyor--film öner |

`Matrix Factorization`Eğitimci, aşağıdaki [algoritma hiper parametreleri](#algorithm-hyperparameters) bölümünde hakkında daha fazla bilgi edinmek için çeşitli [seçeneklere](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options)sahiptir.

`Train`Yöntemine bir sonraki kod satırı olarak aşağıdakileri ekleyerek modeli verilere sığdırın ve eğitilen modeli döndürün `BuildAndTrainModel()` :

[!code-csharp[FitModel](./snippets/movie-recommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, modelinizi belirtilen eğitim veri kümesiyle eğliyor. Teknik olarak, `Estimator` verileri dönüştürerek ve eğitimi uygulayarak tanımları yürütür ve bir olan eğitilen modeli geri döndürür `Transformer` .

`Main()` `BuildAndTrainModel()` Yönteminizi çağırmak ve eğitilen modeli döndürmek için yöntemine bir sonraki kod satırı olarak aşağıdakini ekleyin:

[!code-csharp[BuildTrainModelMain](./snippets/movie-recommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Modelinizi değerlendirme

Modelinizi eğittikten sonra, modelinizin nasıl çalıştığını değerlendirmek için test verilerinizi kullanın.

`EvaluateModel()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `BuildAndTrainModel()` :

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

`Test`Aşağıdaki kodu öğesine ekleyerek verileri dönüştürün `EvaluateModel()` :

[!code-csharp[Transform](./snippets/movie-recommendation/csharp/Program.cs#Transform "Transform the test data")]

[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapar.

Yöntemine aşağıdaki kod satırı olarak aşağıdakini ekleyerek modeli değerlendirin `EvaluateModel()` :

[!code-csharp[Evaluate](./snippets/movie-recommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Tahmin kümesine sahip olduktan sonra, tahmin edilen değerleri test veri kümesindeki gerçek ile karşılaştıran ve modelin nasıl çalıştığı hakkında ölçümler döndüren [değerlendir ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi, modeli değerlendirir `Labels` .

Aşağıdaki kod satırını yöntemine ekleyerek değerlendirme ölçümlerinizi konsola yazdırın `EvaluateModel()` :

[!code-csharp[PrintMetrics](./snippets/movie-recommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

`Main()`Yönteminizi çağırmak için yöntemi içindeki sonraki kod satırı olarak aşağıdakini ekleyin `EvaluateModel()` :

[!code-csharp[EvaluateModelMain](./snippets/movie-recommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

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

`root of mean squared error`(RMS veya rmo), model tahmin edilen değerler ve test veri kümesi gözlenen değerleri arasındaki farkları ölçmek için kullanılır. Teknik olarak, hataların karelerinin ortalamasının karekökünü temel alır. Bunun ne kadar küçük olması, modelin ne kadar iyi olduğu.

`R Squared`verilerin bir modele ne kadar uygun olduğunu gösterir. 0 ile 1 arasında aralıklar. 0 değeri, verilerin rastgele olması veya başka türlü modele sığamayacak olması anlamına gelir. 1 değeri, modelin verilerle tam olarak eşleştiği anlamına gelir. `R Squared`Puanınızın mümkün olduğunca 1 ' e yakın olmasını istiyorsunuz.

Başarılı modellerin oluşturulması, yinelemeli bir işlemdir. Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır. Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı Hyper-parametreleri ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz. Daha fazla bilgi için aşağıdaki [modelinizi geliştirme](#improve-your-model) bölümünü inceleyin.

## <a name="use-your-model"></a>Modelinizi kullanma

Artık yeni verilerde öngörülere sahip olmak için eğitilen modeli kullanabilirsiniz.

`UseModelForSinglePrediction()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `EvaluateModel()` :

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

`PredictionEngine`Aşağıdaki kodu öğesine ekleyerek derecelendirmeyi tahmin etmek için öğesini kullanın `UseModelForSinglePrediction()` :

[!code-csharp[PredictionEngine](./snippets/movie-recommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan hizmetini kullanın. [ `PredictionEnginePool` ASP.NET Core Web API 'sinde kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.

> [!NOTE]
> `PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.

`MovieRating` `testInput` Aşağıdaki kod satırlarını yöntemine ekleyerek, çağrılan bir örneği oluşturun ve bunu tahmin altyapısına geçirin `UseModelForSinglePrediction()` :

[!code-csharp[MakeSinglePrediction](./snippets/movie-recommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

PREDICT [()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütunu üzerinde bir tahmin yapar.

Daha sonra `Score` , filmi Kullanıcı 6 ' ya Movieıd 10 ile önermek isteyip istemediğinizi öğrenmek için veya tahmin edilen derecelendirmeyi kullanabilirsiniz. Ne kadar yüksekse, `Score` bir kullanıcının belirli bir filmi beğenme olasılığı yüksektir. Bu durumda, > 3,5 ' nin tahmin edilen derecelendirmesine sahip filmler önertiğinizi varsayalım.

Sonuçları yazdırmak için aşağıdaki kod satırları `UseModelForSinglePrediction()` yöntemine ekleyin:

[!code-csharp[PrintResults](./snippets/movie-recommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

`Main()`Yönteminizi çağırmak için yöntemi içindeki sonraki kod satırı olarak aşağıdakini ekleyin `UseModelForSinglePrediction()` :

[!code-csharp[UseModelMain](./snippets/movie-recommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Bu yöntemin çıktısı aşağıdaki metne benzer görünmelidir:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Modelinizi kaydetme

Son Kullanıcı uygulamalarında tahmine dayalı hale getirmek üzere modelinizi kullanmak için önce modeli kaydetmeniz gerekir.

`SaveModel()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `UseModelForSinglePrediction()` :

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Aşağıdaki kodu yöntemine ekleyerek eğitilen modelinizi kaydedin `SaveModel()` :

[!code-csharp[SaveModel](./snippets/movie-recommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

Bu yöntem, eğitilen modelinizi, daha sonra tahmine dayalı hale getirmek için diğer .NET uygulamalarında kullanılabilecek bir. zip dosyasına ("veri" klasöründe) kaydeder.

`Main()`Yönteminizi çağırmak için yöntemi içindeki sonraki kod satırı olarak aşağıdakini ekleyin `SaveModel()` :

[!code-csharp[SaveModelMain](./snippets/movie-recommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Kayıtlı modelinizi kullanın

Eğitilen modelinizi kaydettikten sonra modeli farklı ortamlarda kullanabilirsiniz. Uygulamalarda eğitilen makine öğrenimi modelini nasıl gerçekleştireceğinizi öğrenmek için [eğitilen modelleri kaydetme ve yükleme](../how-to-guides/save-load-machine-learning-models-ml-net.md) konusuna bakın.

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

Tebrikler! Artık film öneren bir makine öğrenimi modelini başarıyla oluşturdunuz. Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.

## <a name="improve-your-model"></a>Modelinizi geliştirme

Daha doğru öngörülere ulaşmak için modelinizin performansını iyileştirebilmeniz için birkaç yol vardır.

### <a name="data"></a>Veriler

Her Kullanıcı ve film kimliği için yeterli sayıda örnek içeren eğitim verileri eklemek, öneri modelinin kalitesini artırmaya yardımcı olabilir.

[Çapraz doğrulama](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) , verileri rastgele kümeler halinde ayırır (Bu öğreticide yaptığınız gibi veri kümesinden test verilerinin ayıklanmasının yerine) ve bazı gruplardan verileri test verileri olarak eğitme ve gruplardan bazılarını alan bir yöntem. Bu yöntem, model kalitesi açısından bir eğitme testi ayırma yapmayı gerçekleştirir.

### <a name="features"></a>Özellikler

Bu öğreticide, yalnızca `Features` `user id` `movie id` `rating` veri kümesi tarafından sunulan üç (,, ve) kullanın.

Bu iyi bir başlangıç olsa da, gerçekte `Features` veri kümesine dahil edildiklerinde başka öznitelikler veya (örneğin, Age, cinsiyeti, coğrafi konum vb.) eklemek isteyebilirsiniz. Daha fazla ilgisi eklemek, `Features` öneri modelinizin performansını artırmaya yardımcı olabilir.

`Features`Makinenizin öğrenimi göreviniz için en uygun olabilecek bir işlem olduğundan emin değilseniz, ml.net 'in en etkili olduğunu keşfetmesi için sunduğu Özellik katkısı hesaplama (FCC) ve [permütasyon özelliği önem derecesi](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)de kullanabilirsiniz `Features` .

### <a name="algorithm-hyperparameters"></a>Algoritma hiper parametreleri

ML.NET, iyi varsayılan eğitim algoritmaları sağlarken, algoritmanın [hiper parametrelerini](../resources/glossary.md#hyperparameter)değiştirerek performansı daha ayrıntılı bir şekilde ayarlayabilirsiniz.

İçin `Matrix Factorization` , [Numberofıterlationve yaklaşık](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) olarak, daha [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) iyi sonuçlar verir.

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

| Algoritma       | Senaryo           | Örnek  |
| ------------- |:-------------:| -----:|
| Bir sınıf matrisi oluşturma | Yalnızca Kullanıcı kimliği ve Movieıd olduğunda bunu kullanın. Bu öneri stili, ortak satın alma senaryosuna veya genellikle birlikte satın alınan ürünlere dayalıdır. Bu, müşterilerin kendi satın alma siparişi geçmişine göre bir ürün kümesi önermesini önermeyeceği anlamına gelir. | [>deneyin](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Alan duyarlı bir ayırma makinesi | Kullanıcı kimliği, ProductID ve derecelendirmeden daha fazla özelliğe sahip olduğunuzda (ürün açıklaması veya ürün fiyatı gibi) öneri sağlamak için bunu kullanın. Bu yöntem ayrıca birlikte çalışan bir filtreleme yaklaşımı kullanır. | [>deneyin](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Yeni Kullanıcı senaryosu

İşbirliğine dayalı filtrelemede yaygın olarak karşılaşılan bir sorun, yeni bir kullanıcıya, ıntreler eklemek için önceki verileri olmayan yeni bir kullanıcı olduğunda oluşan soğuk başlatma sorunudur. Bu sorun genellikle yeni kullanıcılardan bir profil oluşturmasını isteyerek ve örneğin, geçmişte gördüğü filmleri derecelendirmek için çözülür. Bu yöntem kullanıcıya bazı yük koyar, ancak derecelendirme geçmişi olmayan yeni kullanıcılar için bazı veri başlatma verileri sağlar.

## <a name="resources"></a>Kaynaklar

Bu öğreticide kullanılan veriler [Movielens veri kümesinden](http://files.grouplens.org/datasets/movielens/)türetilir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:

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
