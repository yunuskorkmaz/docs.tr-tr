---
title: ML.NET CLı komut başvurusu
description: ML.NET CLı aracında otomatik eğitme komutuna genel bakış, örnekler ve başvuru.
ms.date: 12/18/2019
ms.openlocfilehash: 5e59eba91721b26622360818a73adb07a654dc28
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636126"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="bbfa4-103">ML.NET CLı komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="bbfa4-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="bbfa4-104">`auto-train` komutu, ML.NET CLı aracı tarafından sunulan ana komuttur.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-104">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="bbfa4-105">Komut otomatik makine öğrenimi (Otomatikml) kullanarak iyi bir kalite ML.NET modeli oluşturmanıza ve bu modeli çalıştırmak/skor yapmak için örnek C# kodu oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-105">The command allows you to generate a good quality ML.NET model using automated machine learning (AutoML) as well as the the example C# code to run/score that model.</span></span> <span data-ttu-id="bbfa4-106">Ayrıca, modelin eğiteme C# kodu, modelin algoritmasını ve ayarlarını araştırmanız için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="bbfa4-107">Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="bbfa4-108">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="bbfa4-108">Overview</span></span>

<span data-ttu-id="bbfa4-109">Örnek kullanım:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-109">Example usage:</span></span>

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="bbfa4-110">`mlnet auto-train` komutu aşağıdaki varlıkları üretir:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-110">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="bbfa4-111">Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="bbfa4-112">C#oluşturulan modeli çalıştırmak/skor kodu.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="bbfa4-113">C#Bu modeli oluşturmak için kullanılan eğitim koduna sahip kod.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="bbfa4-114">İlk iki varlık, model ile tahmine dayalı hale getirmek için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması ve daha fazlası) doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="bbfa4-115">Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. böylece modelin belirli algoritmasını ve ayarlarını araştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="bbfa4-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="bbfa4-116">Examples</span></span>

<span data-ttu-id="bbfa4-117">İkili sınıflandırma sorunu için en basit CLı komutu (Oto ml, belirtilen verilerden çoğu yapılandırmanın çoğunu):</span><span class="sxs-lookup"><span data-stu-id="bbfa4-117">The simplest CLI command for a binary classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="bbfa4-118">Gerileme sorunu için başka bir basit CLı komutu:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="bbfa4-119">Bir tren veri kümesiyle, test veri kümesiyle ve daha fazla özelleştirme açık bağımsız değişkenlerle bir ikili sınıflandırma modeli oluşturun ve eğitme:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-119">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a><span data-ttu-id="bbfa4-120">Komut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bbfa4-120">Command options</span></span>

<span data-ttu-id="bbfa4-121">`mlnet auto-train`, belirtilen veri kümesine bağlı olarak birden çok model ve son olarak en iyi modeli seçer, bunu serileştirilmiş bir. zip dosyası olarak kaydeder ve Puanlama C# ve eğitim için ilgili kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-121">`mlnet auto-train` trains multiple models based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

```console
mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

<span data-ttu-id="bbfa4-122">Geçersiz giriş seçenekleri, CLı aracının geçerli girişlerin bir listesini ve bir hata iletisini yaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-122">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="task"></a><span data-ttu-id="bbfa4-123">Görev</span><span class="sxs-lookup"><span data-stu-id="bbfa4-123">Task</span></span>

<span data-ttu-id="bbfa4-124">`--task | --mltask | -T` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-124">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="bbfa4-125">Çözülecek ML sorununu sağlayan tek bir dize.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-125">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="bbfa4-126">Örneğin, aşağıdaki görevlerden herhangi biri (CLı, sonunda, her zaman oto ml 'de desteklenen tüm görevleri destekleyecektir):</span><span class="sxs-lookup"><span data-stu-id="bbfa4-126">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="bbfa4-127">`regression`-bir sayısal değeri tahmin etmek için ML modelinin kullanılacağını seçin</span><span class="sxs-lookup"><span data-stu-id="bbfa4-127">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="bbfa4-128">`binary-classification`-ML modeli sonucunun iki olası kategorik Boole değeri (0 veya 1) olup olmadığını seçin.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-128">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="bbfa4-129">`multiclass-classification`-ML modeli sonucunda birden çok kategorik olası değer olup olmadığını seçin.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-129">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="bbfa4-130">Bu bağımsız değişkende yalnızca bir ML görevi sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-130">Only one ML task should be provided in this argument.</span></span>

## <a name="dataset"></a><span data-ttu-id="bbfa4-131">Veri kümesi</span><span class="sxs-lookup"><span data-stu-id="bbfa4-131">Dataset</span></span>

<span data-ttu-id="bbfa4-132">`--dataset | -d` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-132">`--dataset | -d` (string)</span></span>

<span data-ttu-id="bbfa4-133">Bu bağımsız değişken, FilePath öğesini aşağıdaki seçeneklerden birine sağlar:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-133">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="bbfa4-134">Y *: tüm veri kümesi dosyası:* Bu seçenek kullanılıyorsa ve Kullanıcı `--test-dataset` ve `--validation-dataset`sağlamadıysanız, modelin doğrulanması için çapraz doğrulama (k-katlama, vb.) veya otomatik veri bölünmüş yaklaşımlar dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-134">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="bbfa4-135">Bu durumda, kullanıcının DataSet FilePath 'i sağlaması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-135">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="bbfa4-136">*B: eğitim veri kümesi dosyası:* Kullanıcı ayrıca model doğrulaması için (`--test-dataset` kullanarak ve isteğe bağlı `--validation-dataset`) veri kümeleri sağladıysanız `--dataset` bağımsız değişkeni yalnızca "eğitim veri kümesi" olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-136">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="bbfa4-137">Örneğin, modelin kalitesini doğrulamak ve doğruluk ölçümlerini elde etmek için %80-%20 yaklaşımını kullanırken, "eğitim veri kümesi" verilerin %80 ' sini alacak ve "test veri kümesi" verilerin %20 ' sini alacak.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-137">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="bbfa4-138">Test veri kümesi</span><span class="sxs-lookup"><span data-stu-id="bbfa4-138">Test dataset</span></span>

<span data-ttu-id="bbfa4-139">`--test-dataset | -t` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-139">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="bbfa4-140">Test veri kümesi dosyasına işaret eden dosya yolu; Örneğin, doğruluk ölçümlerini elde etmek için düzenli doğrulamalar yaparken %80-%20 yaklaşım kullanma.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-140">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="bbfa4-141">`--test-dataset`kullanıyorsanız, `--dataset` de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-141">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="bbfa4-142">--Validation-DataSet kullanılmadığı müddetçe `--test-dataset` bağımsız değişkeni isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-142">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="bbfa4-143">Bu durumda, kullanıcının üç bağımsız değişkenini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-143">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="bbfa4-144">Doğrulama veri kümesi</span><span class="sxs-lookup"><span data-stu-id="bbfa4-144">Validation dataset</span></span>

<span data-ttu-id="bbfa4-145">`--validation-dataset | -v` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-145">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="bbfa4-146">Doğrulama veri kümesi dosyasına işaret eden dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-146">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="bbfa4-147">Doğrulama veri kümesi, her durumda isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-147">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="bbfa4-148">`validation dataset`kullanılıyorsa, davranış şu şekilde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-148">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="bbfa4-149">`test-dataset` ve `--dataset` bağımsız değişkenleri de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-149">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="bbfa4-150">`validation-dataset` veri kümesi, model seçiminde tahmin hatasını tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-150">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="bbfa4-151">`test-dataset`, son seçilen modeldeki Genelleştirme hatası değerlendirmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-151">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="bbfa4-152">İdeal olarak, test kümesinin bir "kasa" içinde tutulması ve yalnızca veri analizinin sonunda getirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-152">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="bbfa4-153">Temel olarak, bir `validation dataset` ve `test dataset`kullanılırken, doğrulama aşaması iki parçaya bölünür:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-153">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="bbfa4-154">İlk bölümde, modellerinize göz atadınız ve doğrulama verilerini kullanarak en iyi şekilde gerçekleştirdiğiniz yaklaşımı seçersiniz (= doğrulama)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-154">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="bbfa4-155">Ardından seçili yaklaşımın doğruluğunu tahmin edersiniz (= test).</span><span class="sxs-lookup"><span data-stu-id="bbfa4-155">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="bbfa4-156">Bu nedenle, verilerin ayrımı 80/10/10 veya 75/15/10 olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-156">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="bbfa4-157">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-157">For example:</span></span>

- <span data-ttu-id="bbfa4-158">`training-dataset` dosya verilerin %75 ' i olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-158">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="bbfa4-159">`validation-dataset` dosya verilerin %15 ' i olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-159">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="bbfa4-160">`test-dataset` dosya verilerin %10 ' a sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-160">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="bbfa4-161">Herhangi bir durumda, bu yüzdeleri Kullanıcı tarafından zaten bölünmüş dosyaları sağlayacak CLı kullanarak kararlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-161">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column-name"></a><span data-ttu-id="bbfa4-162">Etiket sütun adı</span><span class="sxs-lookup"><span data-stu-id="bbfa4-162">Label column name</span></span>

<span data-ttu-id="bbfa4-163">`--label-column-name | -n` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-163">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="bbfa4-164">Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin üst bilgisinde ayarlanan sütunun adı kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-164">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="bbfa4-165">Bu bağımsız değişken yalnızca bir *Sınıflandırma sorunu*gıbı denetimli ml görevleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-165">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="bbfa4-166">*Kümeleme*gıbı denetimli ml görevleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-166">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="label-column-index"></a><span data-ttu-id="bbfa4-167">Etiket sütun dizini</span><span class="sxs-lookup"><span data-stu-id="bbfa4-167">Label column index</span></span>

<span data-ttu-id="bbfa4-168">`--label-column-index | -i` (int)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-168">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="bbfa4-169">Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin dosyasındaki sayısal dizin kullanılarak belirtilebilir (sütun dizini değerleri 1 ' den başlar).</span><span class="sxs-lookup"><span data-stu-id="bbfa4-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="bbfa4-170">*Note:* Kullanıcı `--label-column-name`de kullanıyorsa, `--label-column-name` kullanılan bir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-170">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="bbfa4-171">Bu bağımsız değişken yalnızca bir *Sınıflandırma sorunu*gıbı denetimli ml görevi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-171">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="bbfa4-172">*Kümeleme*gıbı denetimli ml görevleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-172">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="bbfa4-173">Sütunları yoksay</span><span class="sxs-lookup"><span data-stu-id="bbfa4-173">Ignore columns</span></span>

<span data-ttu-id="bbfa4-174">`--ignore-columns | -I` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-174">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="bbfa4-175">Bu bağımsız değişkenle, veri kümesi dosyasında var olan sütunları yoksayabilirsiniz ve bu sayede eğitim işlemleriyle birlikte kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-175">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="bbfa4-176">Yoksaymak istediğiniz sütun adlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-176">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="bbfa4-177">Birden çok sütun adını ayırmak için ', ' (boşluk ile virgül) veya ' ' (boşluk) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-177">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="bbfa4-178">Boşluk içeren sütun adları için tırnak işareti kullanabilirsiniz (örneğin, "oturum açmış").</span><span class="sxs-lookup"><span data-stu-id="bbfa4-178">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="bbfa4-179">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-179">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="bbfa4-180">Üst bilgisi vardır</span><span class="sxs-lookup"><span data-stu-id="bbfa4-180">Has header</span></span>

<span data-ttu-id="bbfa4-181">`--has-header | -h` (bool)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-181">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="bbfa4-182">Veri kümesi dosyalarının bir üst bilgi satırına sahip olup olmadığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-182">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="bbfa4-183">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-183">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="bbfa4-184">Bu bağımsız değişken Kullanıcı tarafından belirtilmemişse, varsayılan değer olarak `true`.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-184">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="bbfa4-185">`--label-column-name` bağımsız değişkenini kullanmak için, veri kümesi dosyasında bir üst bilgiye sahip olmanız ve `--has-header` `true` (varsayılan olarak) olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-185">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

## <a name="max-exploration-time"></a><span data-ttu-id="bbfa4-186">En fazla araştırma süresi</span><span class="sxs-lookup"><span data-stu-id="bbfa4-186">Max exploration time</span></span>

<span data-ttu-id="bbfa4-187">`--max-exploration-time | -x` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-187">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="bbfa4-188">Varsayılan olarak, en fazla araştırma süresi 30 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-188">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="bbfa4-189">Bu bağımsız değişken, birden fazla taş ve yapılandırmayı araştırmak için işlem için en uzun süreyi (saniye cinsinden) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-189">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="bbfa4-190">Belirtilen süre çok kısaysa (2 saniye), tek bir yineleme için yapılandırılan saat kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-190">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="bbfa4-191">Bu durumda, gerçek süre, tek bir yinelemede tek bir model yapılandırması üretmek için gereken süredir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-191">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="bbfa4-192">Yinelemeler için gereken süre, veri kümesinin boyutuna bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-192">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="bbfa4-193">Önbellek</span><span class="sxs-lookup"><span data-stu-id="bbfa4-193">Cache</span></span>

<span data-ttu-id="bbfa4-194">`--cache | -c` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="bbfa4-195">Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellek içinde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="bbfa4-196">Küçük ve orta ölçekli veri kümelerinde, önbelleğin kullanılması eğitim performansını önemli ölçüde iyileştirebilir, bu da eğitim süresi önbelleği kullanmadığınız zamandan daha kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="bbfa4-197">Ancak, büyük veri kümeleri için bellekteki tüm verilerin yüklenmesi, bellek yetersiz olduğundan olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="bbfa4-198">Büyük veri kümesi dosyalarıyla eğitim yaparken ve önbellek kullanmayan ML.NET, eğitim sırasında daha fazla veri yüklemesi gerektiğinde sürücüdeki veri öbeklerini akışa alabilir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="bbfa4-199">Aşağıdaki değerleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-199">You can specify the following values:</span></span>

<span data-ttu-id="bbfa4-200">`on`: eğitim sırasında önbelleğin kullanılmasına zorlar.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="bbfa4-201">`off`: eğitim sırasında önbelleğin kullanılmamaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="bbfa4-202">`auto`:, oto ml buluşsal lerine bağlı olarak, önbellek kullanılır veya değildir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="bbfa4-203">Genellikle, küçük/orta veri kümeleri önbelleği kullanır ve büyük veri kümeleri `auto` seçeneğini kullanırsanız önbelleği kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="bbfa4-204">`--cache` parametresini belirtmezseniz, varsayılan olarak önbellek `auto` yapılandırması kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="bbfa4-205">Name</span><span class="sxs-lookup"><span data-stu-id="bbfa4-205">Name</span></span>

<span data-ttu-id="bbfa4-206">`--name | -N` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-206">`--name | -N` (string)</span></span>

<span data-ttu-id="bbfa4-207">Oluşturulan çıkış projesinin veya çözümünün adı.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-207">The name for the created output project or solution.</span></span> <span data-ttu-id="bbfa4-208">Ad belirtilmemişse, `sample-{mltask}` adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-208">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="bbfa4-209">ML.NET model dosyası (. ZIP dosyası) de aynı adı alır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-209">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="bbfa4-210">Çıkış yolu</span><span class="sxs-lookup"><span data-stu-id="bbfa4-210">Output path</span></span>

<span data-ttu-id="bbfa4-211">`--output-path | -o` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-211">`--output-path | -o` (string)</span></span>

<span data-ttu-id="bbfa4-212">Oluşturulan çıkışın yerleştirileceği kök konumu/klasörü.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-212">Root location/folder to place the generated output.</span></span> <span data-ttu-id="bbfa4-213">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-213">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="bbfa4-214">Ayrıntı Düzeyi</span><span class="sxs-lookup"><span data-stu-id="bbfa4-214">Verbosity</span></span>

<span data-ttu-id="bbfa4-215">`--verbosity | -V` (dize)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-215">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="bbfa4-216">Standart çıkışın ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-216">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="bbfa4-217">İzin verilen değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bbfa4-217">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="bbfa4-218">`m[inimal]` (varsayılan olarak)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-218">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="bbfa4-219">`diag[nostic]` (günlüğe kaydetme bilgileri düzeyi)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-219">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="bbfa4-220">Varsayılan olarak, CLı aracı çalışırken, çalıştığı ve ne kadar süre kaldığını ya da zamanın ne kadar tamamlandığını belirten en düşük geri bildirimleri (en az) göstermelidir.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-220">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="bbfa4-221">Yardım</span><span class="sxs-lookup"><span data-stu-id="bbfa4-221">Help</span></span>

`-h|--help`

<span data-ttu-id="bbfa4-222">Komut için, her komutun parametresi için bir açıklama içeren yardımı yazdırır.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-222">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbfa4-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-223">See also</span></span>

- [<span data-ttu-id="bbfa4-224">ML.NET CLı aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="bbfa4-224">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="bbfa4-225">ML.NET CLı 'ye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bbfa4-225">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="bbfa4-226">Öğretici: ML.NET CLı kullanarak yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="bbfa4-226">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="bbfa4-227">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="bbfa4-227">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
