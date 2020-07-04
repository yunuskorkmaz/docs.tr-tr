---
title: ML.NET CLı komut başvurusu
description: ML.NET CLı aracında otomatik eğitme komutuna genel bakış, örnekler ve başvuru.
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 4c6cb1346c16f6162077d3414140d693de9e0d8c
ms.sourcegitcommit: 182c7b6c079ebcc0e1898dfd9e921b9ef472ea2c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85946947"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="e5d41-103">ML.NET CLı komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="e5d41-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="e5d41-104">`classification`, `regression` Ve komutları, `recommendation` ml.net CLI aracı tarafından sunulan ana komutlardır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="e5d41-105">Bu komutlar otomatik makine öğrenimi (Otomatikml) kullanarak sınıflandırma, regresyon ve öneri modelleri için iyi kaliteli ML.NET modelleri oluşturmanızı ve bu modeli çalıştırmak/skor yapmak için örnek C# kodunu oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5d41-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="e5d41-106">Ayrıca, modeli eğitmek için C# kodu, modelin algoritmasını ve ayarlarını araştırmanız için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e5d41-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="e5d41-107">Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="e5d41-108">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5d41-108">Overview</span></span>

<span data-ttu-id="e5d41-109">Örnek kullanım: </span><span class="sxs-lookup"><span data-stu-id="e5d41-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="e5d41-110">`mlnet`Ml görev komutları ( `classification` , `regression` , ve `recommendation` ) aşağıdaki varlıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e5d41-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="e5d41-111">Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.</span><span class="sxs-lookup"><span data-stu-id="e5d41-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="e5d41-112">Oluşturulan modeli çalıştırmak/öğrenmek için C# kodu.</span><span class="sxs-lookup"><span data-stu-id="e5d41-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="e5d41-113">Bu modeli oluşturmak için kullanılan eğitim koduna sahip C# kodu.</span><span class="sxs-lookup"><span data-stu-id="e5d41-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="e5d41-114">İlk iki varlık, model ile tahmine dayalı hale getirmek için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması ve daha fazlası) doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="e5d41-115">Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. böylece modelin belirli algoritmasını ve ayarlarını araştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5d41-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="e5d41-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e5d41-116">Examples</span></span>

<span data-ttu-id="e5d41-117">Bir sınıflandırma sorunu için en basit CLı komutu (Oto ml 'nin, belirtilen verilerden çoğu yapılandırmanın çoğunu):</span><span class="sxs-lookup"><span data-stu-id="e5d41-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="e5d41-118">Gerileme sorunu için başka bir basit CLı komutu:</span><span class="sxs-lookup"><span data-stu-id="e5d41-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="e5d41-119">Bir eğitim veri kümesi, test veri kümesi ve daha fazla özelleştirme açık bağımsız değişkenlerle bir sınıflandırma modeli oluşturun ve eğitme:</span><span class="sxs-lookup"><span data-stu-id="e5d41-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="e5d41-120">Komut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e5d41-120">Command options</span></span>

<span data-ttu-id="e5d41-121">`mlnet`Ml görev komutları ( `classification` , `regression` ve), `recommendation` belirtilen VERI kümesi ve ml.net CLI seçeneklerine göre birden çok modeli eğitme.</span><span class="sxs-lookup"><span data-stu-id="e5d41-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="e5d41-122">Bu komutlar Ayrıca en iyi modeli seçer, modeli serileştirilmiş bir. zip dosyası olarak kaydeder ve Puanlama ve eğitim için ilgili C# kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5d41-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="e5d41-123">Sınıflandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e5d41-123">Classification options</span></span>

<span data-ttu-id="e5d41-124">Çalışan `mlnet classification` bir sınıflandırma modelini eğitecektir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="e5d41-125">ML modelinin verileri 2 veya daha fazla sınıfa (ör. yaklaşım Analizi) sınıflandırmasına istiyorsanız bu komutu seçin.</span><span class="sxs-lookup"><span data-stu-id="e5d41-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a><span data-ttu-id="e5d41-126">Regresyon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e5d41-126">Regression options</span></span>

<span data-ttu-id="e5d41-127">Çalıştırmak `mlnet regression` , regresyon modeli eğitecektir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="e5d41-128">Bir ML modelinin sayısal bir değer (örn. fiyat tahmini) tahmin etmek istiyorsanız bu komutu seçin.</span><span class="sxs-lookup"><span data-stu-id="e5d41-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a><span data-ttu-id="e5d41-129">Öneri seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e5d41-129">Recommendation options</span></span>

<span data-ttu-id="e5d41-130">Çalışan `mlnet recommendation` bir öneri modeli eğitecektir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="e5d41-131">Bir ML modelinin derecelendirmelere göre kullanıcılara (örn. ürün önerisi) öğe önermesini istiyorsanız bu komutu seçin.</span><span class="sxs-lookup"><span data-stu-id="e5d41-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

<span data-ttu-id="e5d41-132">Geçersiz giriş seçenekleri, CLı aracının geçerli girişlerin bir listesini ve bir hata iletisini yaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e5d41-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="e5d41-133">Veri kümesi</span><span class="sxs-lookup"><span data-stu-id="e5d41-133">Dataset</span></span>

<span data-ttu-id="e5d41-134">`--dataset | -d`dizisinde</span><span class="sxs-lookup"><span data-stu-id="e5d41-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="e5d41-135">Bu bağımsız değişken, FilePath öğesini aşağıdaki seçeneklerden birine sağlar:</span><span class="sxs-lookup"><span data-stu-id="e5d41-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="e5d41-136">Y *: tüm veri kümesi dosyası:* Bu seçenek kullanılıyorsa ve Kullanıcı ve sağlamadıysanız `--test-dataset` `--validation-dataset` çapraz doğrulama (k-katlama, vb.) veya otomatik veri bölme yaklaşımları, modeli doğrulamak için dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="e5d41-137">Bu durumda, kullanıcının DataSet FilePath 'i sağlaması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="e5d41-138">*B: eğitim veri kümesi dosyası:* Kullanıcı ayrıca model doğrulaması için ( `--test-dataset` ve isteğe bağlı olarak) veri kümeleri sağladıysanız `--validation-dataset` , `--dataset` bağımsız değişken yalnızca "eğitim veri kümesi" olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="e5d41-139">Örneğin, modelin kalitesini doğrulamak ve doğruluk ölçümlerini elde etmek için %80-%20 yaklaşımını kullanırken, "eğitim veri kümesi" verilerin %80 ' sini alacak ve "test veri kümesi" verilerin %20 ' sini alacak.</span><span class="sxs-lookup"><span data-stu-id="e5d41-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="e5d41-140">Test veri kümesi</span><span class="sxs-lookup"><span data-stu-id="e5d41-140">Test dataset</span></span>

<span data-ttu-id="e5d41-141">`--test-dataset | -t`dizisinde</span><span class="sxs-lookup"><span data-stu-id="e5d41-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="e5d41-142">Test veri kümesi dosyasına işaret eden dosya yolu; Örneğin, doğruluk ölçümlerini elde etmek için düzenli doğrulamalar yaparken %80-%20 yaklaşım kullanma.</span><span class="sxs-lookup"><span data-stu-id="e5d41-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="e5d41-143">Kullanılıyorsa `--test-dataset` , `--dataset` de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="e5d41-144">`--test-dataset`--Validation-DataSet kullanılmadığı müddetçe bağımsız değişken isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="e5d41-145">Bu durumda, kullanıcının üç bağımsız değişkenini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="e5d41-146">Doğrulama veri kümesi</span><span class="sxs-lookup"><span data-stu-id="e5d41-146">Validation dataset</span></span>

<span data-ttu-id="e5d41-147">`--validation-dataset | -v`dizisinde</span><span class="sxs-lookup"><span data-stu-id="e5d41-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="e5d41-148">Doğrulama veri kümesi dosyasına işaret eden dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="e5d41-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="e5d41-149">Doğrulama veri kümesi, her durumda isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="e5d41-150">Bir kullanıyorsanız `validation dataset` , davranış şu şekilde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e5d41-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="e5d41-151">`test-dataset`Ve `--dataset` bağımsız değişkenleri de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="e5d41-152">`validation-dataset`Veri kümesi, model seçimine yönelik tahmin hatasını tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="e5d41-153">, `test-dataset` Seçili son modeldeki Genelleştirme hatası değerlendirmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="e5d41-154">İdeal olarak, test kümesinin bir "kasa" içinde tutulması ve yalnızca veri analizinin sonunda getirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="e5d41-155">Temel olarak, bir `validation dataset` artı kullandığınızda `test dataset` , doğrulama aşaması iki parçaya ayrılır:</span><span class="sxs-lookup"><span data-stu-id="e5d41-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="e5d41-156">İlk bölümde, modellerinize göz atadınız ve doğrulama verilerini kullanarak en iyi şekilde gerçekleştirdiğiniz yaklaşımı seçersiniz (= doğrulama)</span><span class="sxs-lookup"><span data-stu-id="e5d41-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="e5d41-157">Ardından seçili yaklaşımın doğruluğunu tahmin edersiniz (= test).</span><span class="sxs-lookup"><span data-stu-id="e5d41-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="e5d41-158">Bu nedenle, verilerin ayrımı 80/10/10 veya 75/15/10 olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="e5d41-159">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e5d41-159">For example:</span></span>

- <span data-ttu-id="e5d41-160">`training-dataset`Dosya, verilerin %75 ' i olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="e5d41-161">`validation-dataset`Dosya, verilerin %15 ' i olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="e5d41-162">`test-dataset`Dosya, verilerin %10 ' a sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="e5d41-163">Herhangi bir durumda, bu yüzdeleri Kullanıcı tarafından zaten bölünmüş dosyaları sağlayacak CLı kullanarak kararlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="e5d41-164">Etiket sütunu</span><span class="sxs-lookup"><span data-stu-id="e5d41-164">Label column</span></span>

<span data-ttu-id="e5d41-165">`--label-col`(int veya String)</span><span class="sxs-lookup"><span data-stu-id="e5d41-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="e5d41-166">Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin üstbilgisinde veya sütunun veri kümesinin dosyasındaki sayısal dizininde bulunan sütunun adı kullanılarak belirtilebilir (sütun dizini değerleri 0 ' dan başlar).</span><span class="sxs-lookup"><span data-stu-id="e5d41-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e5d41-167">Bu bağımsız değişken, *Sınıflandırma* ve *gerileme* sorunları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="e5d41-168">Öğe sütunu</span><span class="sxs-lookup"><span data-stu-id="e5d41-168">Item column</span></span>

<span data-ttu-id="e5d41-169">`--item-col`(int veya String)</span><span class="sxs-lookup"><span data-stu-id="e5d41-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="e5d41-170">Öğe sütunu, kullanıcıların hızaldığı öğelerin listesini içerir (öğeler kullanıcılara önerilir).</span><span class="sxs-lookup"><span data-stu-id="e5d41-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="e5d41-171">Bu sütun, veri kümesinin üstbilgisinde sütun adı kümesi veya veri kümesinin dosyasında sütunun sayısal dizini kullanılarak belirtilebilir (sütun dizini değerleri 0 ' dan başlar).</span><span class="sxs-lookup"><span data-stu-id="e5d41-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e5d41-172">Bu bağımsız değişken yalnızca *öneri* görevi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="e5d41-173">Derecelendirme sütunu</span><span class="sxs-lookup"><span data-stu-id="e5d41-173">Rating column</span></span>

<span data-ttu-id="e5d41-174">`--rating-col`(int veya String)</span><span class="sxs-lookup"><span data-stu-id="e5d41-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="e5d41-175">Derecelendirme sütunu kullanıcılara göre öğelere verilen derecelendirmelerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="e5d41-176">Bu sütun, veri kümesinin üstbilgisinde sütun adı kümesi veya veri kümesinin dosyasında sütunun sayısal dizini kullanılarak belirtilebilir (sütun dizini değerleri 0 ' dan başlar).</span><span class="sxs-lookup"><span data-stu-id="e5d41-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e5d41-177">Bu bağımsız değişken yalnızca *öneri* görevi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="e5d41-178">Kullanıcı sütunu</span><span class="sxs-lookup"><span data-stu-id="e5d41-178">User column</span></span>

<span data-ttu-id="e5d41-179">`--user-col`(int veya String)</span><span class="sxs-lookup"><span data-stu-id="e5d41-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="e5d41-180">Kullanıcı sütunu, öğelere derecelendirme veren kullanıcıların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="e5d41-181">Bu sütun, veri kümesinin üstbilgisinde sütun adı kümesi veya veri kümesinin dosyasında sütunun sayısal dizini kullanılarak belirtilebilir (sütun dizini değerleri 0 ' dan başlar).</span><span class="sxs-lookup"><span data-stu-id="e5d41-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e5d41-182">Bu bağımsız değişken yalnızca *öneri* görevi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="e5d41-183">Sütunları yoksay</span><span class="sxs-lookup"><span data-stu-id="e5d41-183">Ignore columns</span></span>

<span data-ttu-id="e5d41-184">`--ignore-columns`dizisinde</span><span class="sxs-lookup"><span data-stu-id="e5d41-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="e5d41-185">Bu bağımsız değişkenle, veri kümesi dosyasında var olan sütunları yoksayabilirsiniz ve bu sayede eğitim işlemleriyle birlikte kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e5d41-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="e5d41-186">Yoksaymak istediğiniz sütun adlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e5d41-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="e5d41-187">Birden çok sütun adını ayırmak için ', ' (boşluk ile virgül) veya ' ' (boşluk) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5d41-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="e5d41-188">Boşluk içeren sütun adları için tırnak işareti kullanabilirsiniz (örneğin, "oturum açmış").</span><span class="sxs-lookup"><span data-stu-id="e5d41-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="e5d41-189">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e5d41-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="e5d41-190">Üst bilgisi vardır</span><span class="sxs-lookup"><span data-stu-id="e5d41-190">Has header</span></span>

<span data-ttu-id="e5d41-191">`--has-header`bool</span><span class="sxs-lookup"><span data-stu-id="e5d41-191">`--has-header` (bool)</span></span>

<span data-ttu-id="e5d41-192">Veri kümesi dosyalarının bir üst bilgi satırına sahip olup olmadığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e5d41-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="e5d41-193">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e5d41-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="e5d41-194">Bu bağımsız değişken Kullanıcı tarafından belirtilmemişse, ML.NET CLı bu özelliği algılamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="e5d41-195">Eğitim süresi</span><span class="sxs-lookup"><span data-stu-id="e5d41-195">Train time</span></span>

<span data-ttu-id="e5d41-196">`--train-time`dizisinde</span><span class="sxs-lookup"><span data-stu-id="e5d41-196">`--train-time` (string)</span></span>

<span data-ttu-id="e5d41-197">Varsayılan olarak, en fazla araştırma/tren süresi 30 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="e5d41-198">Bu bağımsız değişken, birden fazla taş ve yapılandırmayı araştırmak için işlem için en uzun süreyi (saniye cinsinden) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e5d41-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="e5d41-199">Belirtilen süre çok kısaysa (2 saniye), tek bir yineleme için yapılandırılan saat kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="e5d41-200">Bu durumda, gerçek süre, tek bir yinelemede tek bir model yapılandırması üretmek için gereken süredir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="e5d41-201">Yinelemeler için gereken süre, veri kümesinin boyutuna bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="e5d41-202">Önbellek</span><span class="sxs-lookup"><span data-stu-id="e5d41-202">Cache</span></span>

<span data-ttu-id="e5d41-203">`--cache`dizisinde</span><span class="sxs-lookup"><span data-stu-id="e5d41-203">`--cache` (string)</span></span>

<span data-ttu-id="e5d41-204">Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellek içinde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="e5d41-205">Küçük ve orta ölçekli veri kümelerinde, önbelleğin kullanılması eğitim performansını önemli ölçüde iyileştirebilir, bu da eğitim süresi önbelleği kullanmadığınız zamandan daha kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="e5d41-206">Ancak, büyük veri kümeleri için bellekteki tüm verilerin yüklenmesi, bellek yetersiz olduğundan olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="e5d41-207">Büyük veri kümesi dosyalarıyla eğitim yaparken ve önbellek kullanmayan ML.NET, eğitim sırasında daha fazla veri yüklemesi gerektiğinde sürücüdeki veri öbeklerini akışa alabilir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="e5d41-208">Aşağıdaki değerleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e5d41-208">You can specify the following values:</span></span>

<span data-ttu-id="e5d41-209">`on`: Eğitim sırasında önbelleğin kullanılmasına zorlar.</span><span class="sxs-lookup"><span data-stu-id="e5d41-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="e5d41-210">`off`: Eğitim sırasında önbelleğin kullanılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="e5d41-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="e5d41-211">`auto`: Bu, oto ml buluşsal türüne bağlı olarak, önbellek kullanılır veya değildir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="e5d41-212">Genellikle, küçük/orta veri kümeleri önbelleği kullanır ve büyük veri kümeleri seçeneği kullanırsanız önbelleği kullanmaz `auto` .</span><span class="sxs-lookup"><span data-stu-id="e5d41-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="e5d41-213">`--cache`Parametresini belirtmezseniz, `auto` Varsayılan olarak önbellek yapılandırması kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="e5d41-214">Adı</span><span class="sxs-lookup"><span data-stu-id="e5d41-214">Name</span></span>

<span data-ttu-id="e5d41-215">`--name`dizisinde</span><span class="sxs-lookup"><span data-stu-id="e5d41-215">`--name` (string)</span></span>

<span data-ttu-id="e5d41-216">Oluşturulan çıkış projesinin veya çözümünün adı.</span><span class="sxs-lookup"><span data-stu-id="e5d41-216">The name for the created output project or solution.</span></span> <span data-ttu-id="e5d41-217">Ad belirtilmemişse, ad `sample-{mltask}` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="e5d41-218">ML.NET model dosyası (. ZIP dosyası) de aynı adı alır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="e5d41-219">Çıkış yolu</span><span class="sxs-lookup"><span data-stu-id="e5d41-219">Output path</span></span>

<span data-ttu-id="e5d41-220">`--output | -o`dizisinde</span><span class="sxs-lookup"><span data-stu-id="e5d41-220">`--output | -o` (string)</span></span>

<span data-ttu-id="e5d41-221">Oluşturulan çıkışın yerleştirileceği kök konumu/klasörü.</span><span class="sxs-lookup"><span data-stu-id="e5d41-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="e5d41-222">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="e5d41-223">Ayrıntı Düzeyi</span><span class="sxs-lookup"><span data-stu-id="e5d41-223">Verbosity</span></span>

<span data-ttu-id="e5d41-224">`--verbosity | -v`dizisinde</span><span class="sxs-lookup"><span data-stu-id="e5d41-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="e5d41-225">Standart çıkışın ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e5d41-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="e5d41-226">İzin verilen değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e5d41-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="e5d41-227">`m[inimal]`(varsayılan olarak)</span><span class="sxs-lookup"><span data-stu-id="e5d41-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="e5d41-228">`diag[nostic]`(günlük bilgisi düzeyi)</span><span class="sxs-lookup"><span data-stu-id="e5d41-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="e5d41-229">Varsayılan olarak, CLı aracı çalışırken en az geri bildirim ( `minimal` ), çalışıp çalışmadığını ve ne kadar süre kaldığını veya sürenin% ne kadar tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5d41-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="e5d41-230">Yardım</span><span class="sxs-lookup"><span data-stu-id="e5d41-230">Help</span></span>

`-h |--help`

<span data-ttu-id="e5d41-231">Komut için, her komutun parametresi için bir açıklama içeren yardımı yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e5d41-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5d41-232">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5d41-232">See also</span></span>

- [<span data-ttu-id="e5d41-233">ML.NET CLı aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="e5d41-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="e5d41-234">ML.NET CLı 'ye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5d41-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="e5d41-235">Öğretici: ML.NET CLı kullanarak yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="e5d41-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="e5d41-236">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="e5d41-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
