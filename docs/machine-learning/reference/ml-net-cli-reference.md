---
title: ML.NET CLı aracında otomatik eğitme komutu
description: ML.NET CLı aracında otomatik eğitme komutuna genel bakış, örnekler ve başvuru.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8363a16ab5e793e715131ac37283106517850439
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929195"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a><span data-ttu-id="627a2-103">ML.NET CLı içindeki ' Auto-eğitme ' komutu</span><span class="sxs-lookup"><span data-stu-id="627a2-103">The 'auto-train' command in ML.NET CLI</span></span>

> [!NOTE]
> <span data-ttu-id="627a2-104">Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="627a2-104">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="627a2-105">`auto-train` Komut, ml.net CLI aracı tarafından sunulan ana komuttur.</span><span class="sxs-lookup"><span data-stu-id="627a2-105">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="627a2-106">Komutu iyi bir Quality ML.NET modeli (serileştirilmiş model. zip dosyası) ve bu modeli çalıştırmak/skor için örnek C# kodu oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="627a2-106">The command allows you to generate a good quality ML.NET model (serialized model .zip file) plus the example C# code to run/score that model.</span></span> <span data-ttu-id="627a2-107">Ayrıca, bu model C# oluşturma/eğitme kodu, oluşturulan "en iyi model" için hangi algoritmaların ve hangi ayarların kullandığını araştırmak için de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="627a2-107">In addition, the C# code to create/train that model is also generated for you to research what algorithm and settings it is using for that generated "best model".</span></span>

<span data-ttu-id="627a2-108">Kendi veri kümelerinizde, sizin tarafınızdan kodlamadan bu varlıkları oluşturabilirsiniz. bu sayede, ML.NET zaten tanıyor olsanız bile üretkenliğinizi de artırır.</span><span class="sxs-lookup"><span data-stu-id="627a2-108">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="627a2-109">Şu anda, ML.NET CLı tarafından desteklenen ML görevleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="627a2-109">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`

- <span data-ttu-id="627a2-110">Yayımlanacak Gibi diğer makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="627a2-110">Future: Other machine learning tasks, such as</span></span>
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

<span data-ttu-id="627a2-111">Komut isteminde kullanım örneği:</span><span class="sxs-lookup"><span data-stu-id="627a2-111">Example of usage on the command prompt:</span></span>

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="627a2-112">`mlnet auto-train` Komut aşağıdaki varlıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="627a2-112">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="627a2-113">Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.</span><span class="sxs-lookup"><span data-stu-id="627a2-113">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="627a2-114">C#oluşturulan model (bu modelle Son Kullanıcı uygulamalarınızda tahmine dayalı hale getirmek Için) çalıştırılacak/puan veren kod.</span><span class="sxs-lookup"><span data-stu-id="627a2-114">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
- <span data-ttu-id="627a2-115">C#Bu modeli oluşturmak için kullanılan eğitim koduna sahip kod (öğrenme amaçları).</span><span class="sxs-lookup"><span data-stu-id="627a2-115">C# code with the training code used to generate that model (Learning purposes).</span></span>

<span data-ttu-id="627a2-116">İlk iki varlık, bu oluşturulmuş ML modeliyle tahminler yapmak için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="627a2-116">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="627a2-117">Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. bu sayede, CLı ve ML.NET oto altyapısı tarafından hangi özel oran/algoritma ve Hyper-parametrelerinin seçili olduğunu araştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="627a2-117">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI and the ML.NET AutoML engine.</span></span>

## <a name="the-auto-train-command-uses-the-automl-engine"></a><span data-ttu-id="627a2-118">' Auto-eğitme ' komutu otomatik ml altyapısını kullanır</span><span class="sxs-lookup"><span data-stu-id="627a2-118">The 'auto-train' command uses the AutoML engine</span></span>

<span data-ttu-id="627a2-119">CLı, aşağıdaki diyagramda gösterildiği gibi en iyi kalite modellerini bulmak için ML.NET oto ml altyapısını (NuGet paketi) kullanır:</span><span class="sxs-lookup"><span data-stu-id="627a2-119">The CLI uses the ML.NET AutoML engine (NuGet package) to intelligently search for the best quality models, as shown in the following diagram:</span></span>

<span data-ttu-id="627a2-120">![görüntü](./media/ml-net-automl-working-diagram.png "Ml.net CLI içinde çalışan oto ml altyapısı")</span><span class="sxs-lookup"><span data-stu-id="627a2-120">![image](./media/ml-net-automl-working-diagram.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="627a2-121">' Auto-tren-komutuyla ML.NET CLı aracını çalıştırırken, farklı algoritmalara ve yapılandırma birleşimlerine sahip çok sayıda yineleme gerçekleştirmeye çalışan aracı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="627a2-121">When running the ML.NET CLI tool with the \`auto-train- command, you'll see the tool trying many iterations with different algorithms and combinations of configuration.</span></span>

## <a name="reference-for-auto-train-command"></a><span data-ttu-id="627a2-122">' Auto-eğitme ' komutu başvurusu</span><span class="sxs-lookup"><span data-stu-id="627a2-122">Reference for 'auto-train' command</span></span>

## <a name="examples"></a><span data-ttu-id="627a2-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="627a2-123">Examples</span></span>

<span data-ttu-id="627a2-124">İkili sınıflandırma sorunu için en basit CLı komutu (Oto ml 'nin, bu yapılandırmanın çoğunu belirtilen verilerden çıkarması gerekir):</span><span class="sxs-lookup"><span data-stu-id="627a2-124">Simplest CLI command for a binary classification problem (AutoML will need to infer most of the configuration from the provided data):</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="627a2-125">Gerileme sorunu için başka bir basit CLı komutu:</span><span class="sxs-lookup"><span data-stu-id="627a2-125">Another simple CLI command for a regression problem:</span></span>

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="627a2-126">Bir tren veri kümesiyle, test veri kümesiyle ve daha fazla özelleştirme açık bağımsız değişkenlerle bir ikili sınıflandırma modeli oluşturun ve eğitme:</span><span class="sxs-lookup"><span data-stu-id="627a2-126">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a><span data-ttu-id="627a2-127">Ad</span><span class="sxs-lookup"><span data-stu-id="627a2-127">Name</span></span>

<span data-ttu-id="627a2-128">`mlnet auto-train`-Belirtilen veri kümesine bağlı olarak birden çok model (' n ' yineleme) yapın ve son olarak en iyi modeli seçer, onu serileştirilmiş bir. zip dosyası olarak kaydeder ve ayrıca C# Puanlama ve eğitim için ilgili kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="627a2-128">`mlnet auto-train` - Trains multiple models ('n' iterations) based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

## <a name="synopsis"></a><span data-ttu-id="627a2-129">Özeti</span><span class="sxs-lookup"><span data-stu-id="627a2-129">Synopsis</span></span>

```console
> mlnet auto-train

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

<span data-ttu-id="627a2-130">Geçersiz giriş seçenekleri, CLı aracının geçerli girişlerin bir listesini ve bu durumda söz konusu bağımsız değişken 'in eksik olduğunu açıklayan bir hata iletisini yaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="627a2-130">Invalid input options should cause the CLI tool to emit a list of valid inputs and an error message explaining which arg is missing, if that is the case.</span></span>

## <a name="options"></a><span data-ttu-id="627a2-131">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="627a2-131">Options</span></span>

 ----------------------------------------------------------

<span data-ttu-id="627a2-132">`--task | --mltask | -T`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-132">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="627a2-133">Çözülecek ML sorununu sağlayan tek bir dize.</span><span class="sxs-lookup"><span data-stu-id="627a2-133">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="627a2-134">Örneğin, aşağıdaki görevlerden herhangi biri (CLı, sonunda, her zaman oto ml 'de desteklenen tüm görevleri destekleyecektir):</span><span class="sxs-lookup"><span data-stu-id="627a2-134">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="627a2-135">`regression`-Bir sayısal değeri tahmin etmek için ML modelinin kullanılacağını seçin</span><span class="sxs-lookup"><span data-stu-id="627a2-135">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="627a2-136">`binary-classification`-ML modelinde sonucun iki olası kategorik Boole değeri (0 veya 1) olup olmadığını seçin.</span><span class="sxs-lookup"><span data-stu-id="627a2-136">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="627a2-137">`multiclass-classification`-ML modeli sonucunun birden çok kategorik olası değeri olup olmadığını seçin.</span><span class="sxs-lookup"><span data-stu-id="627a2-137">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="627a2-138">Gelecekte `recommendations` `ranking` , `clustering` gibi ek ml görevleri ve senaryoları yayınlar ve desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="627a2-138">In future releases additional ML Tasks and scenarios such as `recommendations`, `clustering` and `ranking` will be supported.</span></span>

 <span data-ttu-id="627a2-139">Bu bağımsız değişkende yalnızca bir ML görevi sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="627a2-139">Only one ML task should be provided in this argument.</span></span>

 ----------------------------------------------------------

<span data-ttu-id="627a2-140">`--dataset | -d`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-140">`--dataset | -d` (string)</span></span>

<span data-ttu-id="627a2-141">Bu bağımsız değişken, FilePath öğesini aşağıdaki seçeneklerden birine sağlar:</span><span class="sxs-lookup"><span data-stu-id="627a2-141">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="627a2-142">*A Tüm veri kümesi dosyası:* Bu seçenek kullanılıyorsa ve Kullanıcı ve `--test-dataset` `--validation-dataset`sağlamadıysanız çapraz doğrulama (k-katlama, vb.) veya otomatik veri bölme yaklaşımları, modeli doğrulamak için dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="627a2-142">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="627a2-143">Bu durumda, kullanıcının DataSet FilePath 'i sağlaması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="627a2-143">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="627a2-144">*KENARI Eğitim veri kümesi dosyası:* Kullanıcı ayrıca model doğrulaması için ( `--test-dataset` ve isteğe bağlı olarak `--validation-dataset`) veri kümeleri sağladıysanız, `--dataset` bağımsız değişken yalnızca "eğitim veri kümesi" olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="627a2-144">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="627a2-145">Örneğin, modelin kalitesini doğrulamak ve doğruluk ölçümlerini elde etmek için% 80-% 20 yaklaşımını kullanırken, "eğitim veri kümesi" verilerin% 80 ' sini alacak ve "test veri kümesi" verilerin% 20 ' sini alacak.</span><span class="sxs-lookup"><span data-stu-id="627a2-145">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-146">`--test-dataset | -t`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-146">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="627a2-147">Test veri kümesi dosyasına işaret eden dosya yolu; Örneğin, doğruluk ölçümlerini elde etmek için düzenli doğrulamalar yaparken% 80-% 20 yaklaşım kullanma.</span><span class="sxs-lookup"><span data-stu-id="627a2-147">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="627a2-148">`--test-dataset` Kullanılıyorsa`--dataset` , de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="627a2-148">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="627a2-149">--Validation-DataSet kullanılmadığı müddetçe bağımsızdeğişkenisteğebağlıdır.`--test-dataset`</span><span class="sxs-lookup"><span data-stu-id="627a2-149">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="627a2-150">Bu durumda, kullanıcının üç bağımsız değişkenini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="627a2-150">In that case, the user must use the three arguments.</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-151">`--validation-dataset | -v`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-151">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="627a2-152">Doğrulama veri kümesi dosyasına işaret eden dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="627a2-152">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="627a2-153">Doğrulama veri kümesi, her durumda isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="627a2-153">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="627a2-154">Bir `validation dataset`kullanıyorsanız, davranış şu şekilde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="627a2-154">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="627a2-155">`test-dataset` Ve`--dataset` bağımsız değişkenleri de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="627a2-155">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="627a2-156">Veri `validation-dataset` kümesi, model seçimine yönelik tahmin hatasını tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="627a2-156">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="627a2-157">, `test-dataset` Seçili son modeldeki Genelleştirme hatası değerlendirmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="627a2-157">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="627a2-158">İdeal olarak, test kümesinin bir "kasa" içinde tutulması ve yalnızca veri analizinin sonunda getirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="627a2-158">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="627a2-159">Temel olarak, bir `validation dataset` `test dataset`artı kullandığınızda, doğrulama aşaması iki parçaya ayrılır:</span><span class="sxs-lookup"><span data-stu-id="627a2-159">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="627a2-160">İlk bölümde, modellerinize göz atadınız ve doğrulama verilerini kullanarak en iyi şekilde gerçekleştirdiğiniz yaklaşımı seçersiniz (= doğrulama)</span><span class="sxs-lookup"><span data-stu-id="627a2-160">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="627a2-161">Ardından seçili yaklaşımın doğruluğunu tahmin edersiniz (= test).</span><span class="sxs-lookup"><span data-stu-id="627a2-161">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="627a2-162">Bu nedenle, verilerin ayrımı 80/10/10 veya 75/15/10 olabilir.</span><span class="sxs-lookup"><span data-stu-id="627a2-162">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="627a2-163">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="627a2-163">For example:</span></span>

- <span data-ttu-id="627a2-164">`training-dataset`Dosya, verilerin% 75 ' i olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="627a2-164">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="627a2-165">`validation-dataset`Dosya, verilerin% 15 ' i olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="627a2-165">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="627a2-166">`test-dataset`Dosya, verilerin% 10 ' a sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="627a2-166">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="627a2-167">Herhangi bir durumda, bu yüzdeleri Kullanıcı tarafından zaten bölünmüş dosyaları sağlayacak CLı kullanarak kararlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="627a2-167">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-168">`--label-column-name | -n`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-168">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="627a2-169">Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin üst bilgisinde ayarlanan sütunun adı kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="627a2-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="627a2-170">Bu bağımsız değişken yalnızca bir *Sınıflandırma sorunu*gıbı denetimli ml görevleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="627a2-170">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="627a2-171">*Kümeleme*gıbı denetimli ml görevleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="627a2-171">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-172">`--label-column-index | -i`'tir</span><span class="sxs-lookup"><span data-stu-id="627a2-172">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="627a2-173">Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin dosyasındaki sayısal dizin kullanılarak belirtilebilir (sütun dizini değerleri 1 ' den başlar).</span><span class="sxs-lookup"><span data-stu-id="627a2-173">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="627a2-174">*Not:* Kullanıcı da kullanıyorsa `--label-column-name` `--label-column-name` , kullanılmakta olan olur.</span><span class="sxs-lookup"><span data-stu-id="627a2-174">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="627a2-175">Bu bağımsız değişken yalnızca bir *Sınıflandırma sorunu*gıbı denetimli ml görevi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="627a2-175">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="627a2-176">*Kümeleme*gıbı denetimli ml görevleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="627a2-176">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-177">`--ignore-columns | -I`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-177">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="627a2-178">Bu bağımsız değişkenle, veri kümesi dosyasında var olan sütunları yoksayabilirsiniz ve bu sayede eğitim işlemleriyle birlikte kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="627a2-178">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="627a2-179">Yoksaymak istediğiniz sütun adlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="627a2-179">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="627a2-180">Birden çok sütun adını ayırmak için ', ' (boşluk ile virgül) veya ' ' (boşluk) kullanın.</span><span class="sxs-lookup"><span data-stu-id="627a2-180">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="627a2-181">Boşluk içeren sütun adları için tırnak işareti kullanabilirsiniz (örneğin, "oturum açmış").</span><span class="sxs-lookup"><span data-stu-id="627a2-181">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="627a2-182">Örnek:</span><span class="sxs-lookup"><span data-stu-id="627a2-182">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

<span data-ttu-id="627a2-183">`--has-header | -h`bool</span><span class="sxs-lookup"><span data-stu-id="627a2-183">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="627a2-184">Veri kümesi dosyalarının bir üst bilgi satırına sahip olup olmadığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="627a2-184">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="627a2-185">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="627a2-185">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="627a2-186">Bu bağımsız değişken Kullanıcı tarafından `true` belirtilmemişse, varsayılan olarak değeri.</span><span class="sxs-lookup"><span data-stu-id="627a2-186">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="627a2-187">`--label-column-name` Bağımsız değişkenini kullanmak için, veri kümesi dosyasında bir üst bilgiye sahip olmanız ve `--has-header` (varsayılan olarak) olarak `true` ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="627a2-187">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-188">`--max-exploration-time | -x`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-188">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="627a2-189">Varsayılan olarak, en fazla araştırma süresi 30 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="627a2-189">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="627a2-190">Bu bağımsız değişken, birden fazla taş ve yapılandırmayı araştırmak için işlem için en uzun süreyi (saniye cinsinden) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="627a2-190">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="627a2-191">Belirtilen süre çok kısaysa (2 saniye), tek bir yineleme için yapılandırılan saat kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="627a2-191">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="627a2-192">Bu durumda, gerçek süre, tek bir yinelemede tek bir model yapılandırması üretmek için gereken süredir.</span><span class="sxs-lookup"><span data-stu-id="627a2-192">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="627a2-193">Yinelemeler için gereken süre, veri kümesinin boyutuna bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="627a2-193">The needed time for iterations can vary depending on the size of the dataset.</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-194">`--cache | -c`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="627a2-195">Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellek içinde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="627a2-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="627a2-196">Küçük ve orta ölçekli veri kümelerinde, önbelleğin kullanılması eğitim performansını önemli ölçüde iyileştirebilir, bu da eğitim süresi önbelleği kullanmadığınız zamandan daha kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="627a2-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="627a2-197">Ancak, büyük veri kümeleri için bellekteki tüm verilerin yüklenmesi, bellek yetersiz olduğundan olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="627a2-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="627a2-198">Büyük veri kümesi dosyalarıyla eğitim yaparken ve önbellek kullanmayan ML.NET, eğitim sırasında daha fazla veri yüklemesi gerektiğinde sürücüdeki veri öbeklerini akışa alabilir.</span><span class="sxs-lookup"><span data-stu-id="627a2-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="627a2-199">Aşağıdaki değerleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="627a2-199">You can specify the following values:</span></span>

<span data-ttu-id="627a2-200">`on`: Eğitim sırasında önbelleğin kullanılmasına zorlar.</span><span class="sxs-lookup"><span data-stu-id="627a2-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="627a2-201">`off`: Eğitim sırasında önbelleğin kullanılmamaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="627a2-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="627a2-202">`auto`: Oto ml buluşsal türüne bağlı olarak, önbellek kullanılır veya değildir.</span><span class="sxs-lookup"><span data-stu-id="627a2-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="627a2-203">Genellikle, küçük/orta veri kümeleri önbelleği kullanır ve büyük veri kümeleri `auto` seçeneği kullanırsanız önbelleği kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="627a2-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="627a2-204">`--cache` Parametresini belirtmezseniz, varsayılan olarak önbellek `auto` yapılandırması kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="627a2-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-205">`--name | -N`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-205">`--name | -N` (string)</span></span>

<span data-ttu-id="627a2-206">Oluşturulan çıkış projesinin veya çözümünün adı.</span><span class="sxs-lookup"><span data-stu-id="627a2-206">The name for the created output project or solution.</span></span> <span data-ttu-id="627a2-207">Ad belirtilmemişse, ad `sample-{mltask}` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="627a2-207">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="627a2-208">ML.NET model dosyası (. ZIP dosyası) de aynı adı alır.</span><span class="sxs-lookup"><span data-stu-id="627a2-208">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-209">`--output-path | -o`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-209">`--output-path | -o` (string)</span></span>

<span data-ttu-id="627a2-210">Oluşturulan çıkışın yerleştirileceği kök konumu/klasörü.</span><span class="sxs-lookup"><span data-stu-id="627a2-210">Root location/folder to place the generated output.</span></span> <span data-ttu-id="627a2-211">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="627a2-211">The default is the current directory.</span></span>

----------------------------------------------------------

<span data-ttu-id="627a2-212">`--verbosity | -V`dizisinde</span><span class="sxs-lookup"><span data-stu-id="627a2-212">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="627a2-213">Standart çıkışın ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="627a2-213">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="627a2-214">İzin verilen değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="627a2-214">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="627a2-215">`m[inimal]`(varsayılan olarak)</span><span class="sxs-lookup"><span data-stu-id="627a2-215">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="627a2-216">`diag[nostic]`(günlük bilgisi düzeyi)</span><span class="sxs-lookup"><span data-stu-id="627a2-216">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="627a2-217">Varsayılan olarak, CLı aracı çalışırken, çalıştığı ve ne kadar süre kaldığını ya da zamanın ne kadar tamamlandığını belirten en düşük geri bildirimleri (en az) göstermelidir.</span><span class="sxs-lookup"><span data-stu-id="627a2-217">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

----------------------------------------------------------

`-h|--help`

<span data-ttu-id="627a2-218">Komut için, her komutun parametresi için bir açıklama içeren yardımı yazdırır.</span><span class="sxs-lookup"><span data-stu-id="627a2-218">Prints out help for the command with a description for each command's parameter.</span></span>

----------------------------------------------------------

## <a name="see-also"></a><span data-ttu-id="627a2-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="627a2-219">See also</span></span>

- [<span data-ttu-id="627a2-220">ML.NET CLı aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="627a2-220">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="627a2-221">ML.NET CLı ile model eğitimi otomatikleştirin</span><span class="sxs-lookup"><span data-stu-id="627a2-221">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="627a2-222">Öğretici: ML.NET CLı kullanarak ikili bir sınıflandırıcı otomatik oluşturma</span><span class="sxs-lookup"><span data-stu-id="627a2-222">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="627a2-223">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="627a2-223">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
