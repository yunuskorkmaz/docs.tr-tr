---
title: ML.NET CLI aracında otomatik train komutu
description: Genel bakış, örnekler ve ML.NET CLI aracında otomatik train komut başvurusu.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 28eb56eb018e3d1cc76f300ee78c298af77c9b91
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557936"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a><span data-ttu-id="b7c43-103">ML.NET CLI 'train otomatik' komutu</span><span class="sxs-lookup"><span data-stu-id="b7c43-103">The 'auto-train' command in ML.NET CLI</span></span>

> [!NOTE]
> <span data-ttu-id="b7c43-104">ML.NET CLI ve ML.NET AutoML şu anda önizlemede olan bu konuda ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-104">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="b7c43-105">`auto-train` Komuttur ML.NET CLI aracı tarafından sağlanan ana komutu.</span><span class="sxs-lookup"><span data-stu-id="b7c43-105">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="b7c43-106">Komut kaliteli ML.NET modeli (serileştirilmiş modeli .zip dosyası) örnek oluşturmanızı sağlar C# Çalıştır/puanı bu modeli için kod.</span><span class="sxs-lookup"><span data-stu-id="b7c43-106">The command allows you to generate a good quality ML.NET model (serialized model .zip file) plus the example C# code to run/score that model.</span></span> <span data-ttu-id="b7c43-107">Ayrıca, C# /bu modeli eğitme oluşturmak için kod da oluşturulur hangi algoritması ve ayarları için kullanılıyor "en iyi modeli" oluşturulan araştırmak için.</span><span class="sxs-lookup"><span data-stu-id="b7c43-107">In addition, the C# code to create/train that model is also generated for you to research what algorithm and settings it is using for that generated "best model".</span></span>

<span data-ttu-id="b7c43-108">ML.NET bildiğiniz olsa bile, ayrıca üretkenliğinizi artıran şekilde kendiniz, kodlama olmadan, bu varlıkları kendi veri kümeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7c43-108">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="b7c43-109">Şu anda, ML ML.NET CLI tarafından desteklenen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7c43-109">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`

- <span data-ttu-id="b7c43-110">Gelecekteki: Diğer makine öğrenimi görevlerini, aşağıdaki gibi</span><span class="sxs-lookup"><span data-stu-id="b7c43-110">Future: Other machine learning tasks, such as</span></span>
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

<span data-ttu-id="b7c43-111">Komut isteminde kullanım örneği:</span><span class="sxs-lookup"><span data-stu-id="b7c43-111">Example of usage on the command prompt:</span></span>

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="b7c43-112">`mlnet auto-train` Komutu şu varlıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b7c43-112">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="b7c43-113">Serileştirilmiş modeli .zip ("en iyi modeli") kullanıma hazır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-113">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="b7c43-114">C#kod, Çalıştır/puan modeli (Bu modeli ile son kullanıcı uygulamalarınızda Öngörüler oluşturmak için) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b7c43-114">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
- <span data-ttu-id="b7c43-115">C#Bu model (öğrenme amacıyla) oluşturmak için kullanılan eğitim kod ile kod.</span><span class="sxs-lookup"><span data-stu-id="b7c43-115">C# code with the training code used to generate that model (Learning purposes).</span></span>

<span data-ttu-id="b7c43-116">İlk iki varlıklar ile oluşturulan, ML model doğrudan, son kullanıcı uygulamaları (ASP.NET Core web uygulaması, hizmetleri, masaüstü uygulaması, vb.) tahminlerde bulunmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-116">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="b7c43-117">Üçüncü bir varlık, eğitim kod hangi ML.NET API kodu CLI tarafından hangi belirli trainer/algoritması araştırabilir ve parametrelerini hyper CLI ve ML.NET AutoML altyapısı tarafından seçilen oluşturulan modeli eğitmek için kullanılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-117">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-paramenters were selected by the CLI and the ML.NET AutoML engine.</span></span>

## <a name="the-auto-train-command-uses-the-automl-engine"></a><span data-ttu-id="b7c43-118">'Otomatik train' komut AutoML altyapısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-118">The 'auto-train' command uses the AutoML engine</span></span>

<span data-ttu-id="b7c43-119">CLI ML.NET AutoML altyapısı (NuGet paketi) en iyi kalite modelleri için akıllı bir şekilde aramak için aşağıdaki diyagramda gösterildiği gibi kullanır:</span><span class="sxs-lookup"><span data-stu-id="b7c43-119">The CLI uses the ML.NET AutoML engine (NuGet package) to intelligently search for the best quality models, as shown in the following diagram:</span></span>

<span data-ttu-id="b7c43-120">![Görüntü](./media/ml-net-automl-working-diagram.png "AutoML altyapısı ML.NET CLI içinde çalışma")</span><span class="sxs-lookup"><span data-stu-id="b7c43-120">![image](./media/ml-net-automl-working-diagram.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="b7c43-121">ML.NET CLI aracı ile çalışırken ' otomatik-train-komutu, birçok yineleme farklı algoritmalar ve yapılandırması bileşimleri ile çalışırken aracı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b7c43-121">When running the ML.NET CLI tool with the \`auto-train- command, you'll see the tool trying many iterations with different algorithms and combinations of configuration.</span></span>

## <a name="reference-for-auto-train-command"></a><span data-ttu-id="b7c43-122">'Otomatik train' komutu için başvuru</span><span class="sxs-lookup"><span data-stu-id="b7c43-122">Reference for 'auto-train' command</span></span>

## <a name="examples"></a><span data-ttu-id="b7c43-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b7c43-123">Examples</span></span>

<span data-ttu-id="b7c43-124">(AutoML sağlanan veri yapılandırmasından çoğunu çıkarsamak gerekir) basit CLI komutunu ikili sınıflandırma sorunu için:</span><span class="sxs-lookup"><span data-stu-id="b7c43-124">Simplest CLI command for a binary classification problem (AutoML will need to infer most of the configuration from the provided data):</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="b7c43-125">Başka bir basit CLI komutunu regresyon problemi için:</span><span class="sxs-lookup"><span data-stu-id="b7c43-125">Another simple CLI command for a regression problem:</span></span>

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="b7c43-126">Oluşturma ve eğitme veri kümesi, test veri kümesini ve daha fazla özelleştirme açık bağımsız bir ikili sınıflandırma modeli eğitme:</span><span class="sxs-lookup"><span data-stu-id="b7c43-126">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a><span data-ttu-id="b7c43-127">Ad</span><span class="sxs-lookup"><span data-stu-id="b7c43-127">Name</span></span>

<span data-ttu-id="b7c43-128">`mlnet auto-train` -Birden çok modeli eğitir ('n' yinelemeler) sağlanan bir veri kümesini temel alan ve son olarak en iyi modeli oluşturur ve bir seri hale getirilmiş bir .zip dosyası olarak ilgili kaydeder seçer C# Puanlama ve eğitim için kod.</span><span class="sxs-lookup"><span data-stu-id="b7c43-128">`mlnet auto-train` - Trains multiple models ('n' iterations) based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b7c43-129">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b7c43-129">Synopsis</span></span>

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

<span data-ttu-id="b7c43-130">Geçersiz giriş seçenekleri, geçerli girişler ve bu durumda, hangi arg eksik açıklayan bir hata iletisi listesini yaymak CLI aracını neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="b7c43-130">Invalid input options should cause the CLI tool to emit a list of valid inputs and an error message explaining which arg is missing, if that is the case.</span></span>

## <a name="options"></a><span data-ttu-id="b7c43-131">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b7c43-131">Options</span></span>

 ----------------------------------------------------------

<span data-ttu-id="b7c43-132">`--task | --mltask | -T` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-132">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="b7c43-133">ML sorunu çözmek için sağlama, tek bir dize.</span><span class="sxs-lookup"><span data-stu-id="b7c43-133">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="b7c43-134">Örneğin, (içinde AutoML desteklenen tüm görevler CLI sonunda destekleyecek) aşağıdaki görevlerden herhangi birini:</span><span class="sxs-lookup"><span data-stu-id="b7c43-134">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="b7c43-135">`regression` -Seçin ML Model sayısal bir değeri tahmin etmek için kullanılır</span><span class="sxs-lookup"><span data-stu-id="b7c43-135">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="b7c43-136">`binary-classification` -ML Model sonucu olası iki kategorik Boole değeri (0 veya 1) olup olmadığını seçin.</span><span class="sxs-lookup"><span data-stu-id="b7c43-136">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="b7c43-137">`multiclass-classification` -ML Model sonucu birden çok kategorik olası değerler olup olmadığını seçin.</span><span class="sxs-lookup"><span data-stu-id="b7c43-137">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="b7c43-138">Gelecekte ek ML görevler ve senaryolar gibi serbest `recommendations`, `clustering` ve `ranking` desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-138">In future releases additional ML Tasks and scenarios such as `recommendations`, `clustering` and `ranking` will be supported.</span></span>

 <span data-ttu-id="b7c43-139">Bu bağımsız değişken yalnızca bir ML görev sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-139">Only one ML task should be provided in this argument.</span></span>

 ----------------------------------------------------------

<span data-ttu-id="b7c43-140">`--dataset | -d` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-140">`--dataset | -d` (string)</span></span>

<span data-ttu-id="b7c43-141">Bu bağımsız değişken, aşağıdaki seçeneklerden birini yolu sağlar:</span><span class="sxs-lookup"><span data-stu-id="b7c43-141">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="b7c43-142">*Y: Tüm veri kümesi dosyası:* Bu seçenek ve kullanıcı kullanarak değil sağlıyorsa `--test-dataset` ve `--validation-dataset`, çapraz doğrulama (k Katlama, vb.) veya otomatik veri yaklaşımları bölme dahili olarak model doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-142">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="b7c43-143">Bu durumda, kullanıcı yalnızca veri kümesi dosya yolunu sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-143">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="b7c43-144">*B: Eğitim veri kümesi dosyası:* Kullanıcı veri kümeleri de model doğrulama için sağlayıp sağlamadığını (kullanarak `--test-dataset` ve isteğe bağlı olarak `--validation-dataset`), ardından `--dataset` bağımsız değişken anlamına gelir "eğitim veri kümesi" yalnızca sağlamak.</span><span class="sxs-lookup"><span data-stu-id="b7c43-144">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="b7c43-145">Örneğin, model kalitesini doğrulamak ve doğruluk ölçümleri elde etmek için bir % 80-%20 yaklaşımı kullanarak, verilerin %80 "eğitim veri kümesi" olacaktır ve verilerin %20 "test veri" gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-145">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-146">`--test-dataset | -t` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-146">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="b7c43-147">Test veri kümesi dosyası, % 80-%20 yaklaşım doğruluğu ölçümleri elde etmek için normal doğrulamaları yaparken kullanırken örneğin işaret eden dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="b7c43-147">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="b7c43-148">Kullanıyorsanız `--test-dataset`, ardından `--dataset` de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-148">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="b7c43-149">`--test-dataset` Bağımsız değişken isteğe bağlı sürece doğrulama veri kümesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-149">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="b7c43-150">Bu durumda, kullanıcı üç bağımsız değişken kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-150">In that case, the user must use the three arguments.</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-151">`--validation-dataset | -v` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-151">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="b7c43-152">Doğrulama dataset dosyasına işaret eden dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="b7c43-152">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="b7c43-153">Doğrulama veri kümesi, her durumda, isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b7c43-153">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="b7c43-154">Kullanılıyorsa bir `validation dataset`, davranışı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b7c43-154">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="b7c43-155">`test-dataset` Ve `--dataset` bağımsız değişkenleri gereklidir de.</span><span class="sxs-lookup"><span data-stu-id="b7c43-155">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="b7c43-156">`validation-dataset` Veri kümesi, model seçimi için tahmin hata tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-156">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="b7c43-157">`test-dataset` Modeli seçilen son Genelleştirme hata değerlendirmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-157">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="b7c43-158">İdeal olarak, test kümesi "kasada" tutulması gereken ve veri analizi yalnızca sonunda getirilmesi.</span><span class="sxs-lookup"><span data-stu-id="b7c43-158">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="b7c43-159">Temelde, kullanırken bir `validation dataset` artı `test dataset`, doğrulama aşamasını iki bölüme ayrılır:</span><span class="sxs-lookup"><span data-stu-id="b7c43-159">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="b7c43-160">İlk bölüm, yalnızca, model bakın ve en iyi performansa sahip (doğrulama =) doğrulama verileri kullanarak bir yaklaşım seçin</span><span class="sxs-lookup"><span data-stu-id="b7c43-160">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="b7c43-161">Ardından (test =) seçili yaklaşım doğruluğunu tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="b7c43-161">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="b7c43-162">Bu nedenle, veri ayrımı 80/10/10 veya 75/15/10 olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-162">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="b7c43-163">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b7c43-163">For example:</span></span>

- <span data-ttu-id="b7c43-164">`training-dataset` Dosya, verilerin %75 olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-164">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="b7c43-165">`validation-dataset` Dosya, verilerin %15 olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-165">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="b7c43-166">`test-dataset` Dosya, verilerin %10 olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-166">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="b7c43-167">Herhangi bir durumda, söz konusu yüzdeleri dosyaya zaten bölme sağlayacak CLI kullanarak kullanıcı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-167">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-168">`--label-column-name | -n` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-168">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="b7c43-169">Bu bağımsız değişken kümesinin üstbilgisinde ayarlanan sütunun adını kullanarak belirli bir amaç/hedef sütun (tahmin etmek istediğiniz değişken) belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="b7c43-170">Bu bağımsız değişken gibi yalnızca denetimli ML görevler için kullanılan bir *sınıflandırma problemi*.</span><span class="sxs-lookup"><span data-stu-id="b7c43-170">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="b7c43-171">Bu gibi Denetimsiz ML görevler için kullanılamaz *Kümeleme*.</span><span class="sxs-lookup"><span data-stu-id="b7c43-171">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-172">`--label-column-index | -i` (int)</span><span class="sxs-lookup"><span data-stu-id="b7c43-172">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="b7c43-173">Bu bağımsız değişken kümesinin dosyasında (sütun dizini değerleri 1'den başlar) sütunun sayısal dizin kullanarak belirli bir amaç/hedef sütun (tahmin etmek istediğiniz değişken) belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-173">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="b7c43-174">*Not:* Kullanıcı ayrıca kullanıyorsa `--label-column-name`, `--label-column-name` olduğu kullanılan bir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-174">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="b7c43-175">Bu bağımsız değişken gibi yalnızca denetimli ML görev için kullanılan bir *sınıflandırma problemi*.</span><span class="sxs-lookup"><span data-stu-id="b7c43-175">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="b7c43-176">Bu gibi Denetimsiz ML görevler için kullanılamaz *Kümeleme*.</span><span class="sxs-lookup"><span data-stu-id="b7c43-176">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-177">`--ignore-columns | -I` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-177">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="b7c43-178">Bu değişkeni, bu nedenle bunlar değil yüklendi ve eğitim işlemler tarafından kullanılan veri kümesi dosyası mevcut sütunlardaki yoksayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7c43-178">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="b7c43-179">Yok saymak için istediğiniz sütun adlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b7c43-179">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="b7c43-180">Kullanım ',' (boşluk ile ayrılmış) veya ' ' (birden çok sütun adını ayırmak için alanı).</span><span class="sxs-lookup"><span data-stu-id="b7c43-180">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="b7c43-181">Tırnak işaretleri (örn: "oturum açmış") boşluk içeren sütun adları için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7c43-181">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="b7c43-182">Örnek:</span><span class="sxs-lookup"><span data-stu-id="b7c43-182">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

<span data-ttu-id="b7c43-183">`--has-header | -h` (Boole)</span><span class="sxs-lookup"><span data-stu-id="b7c43-183">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="b7c43-184">Veri kümesi dosyaları bir üst bilgi satırı varsa belirtin.</span><span class="sxs-lookup"><span data-stu-id="b7c43-184">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="b7c43-185">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7c43-185">Possible values are:</span></span>
- `true`
- `false`

<span data-ttu-id="b7c43-186">Varsayılan değerdir `true` kullanıcı tarafından bu bağımsız değişken belirtilmezse.</span><span class="sxs-lookup"><span data-stu-id="b7c43-186">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="b7c43-187">Kullanmak için `--label-column-name` bağımsız değişkeni, bir üst bilgi veri kümesi dosyasında olması gerekir ve `--has-header` kümesine `true` (varsayılan olarak olmayan).</span><span class="sxs-lookup"><span data-stu-id="b7c43-187">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-188">`--max-exploration-time | -x` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-188">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="b7c43-189">Varsayılan olarak, en fazla araştırma süre 10 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-189">By default, the maximum exploration time is 10 seconds.</span></span>

<span data-ttu-id="b7c43-190">Bu bağımsız değişken birden çok eğitmenler ve yapılandırmalarını keşfetmek işlemi için en uzun süreyi (saniye cinsinden) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b7c43-190">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="b7c43-191">Belirtilen saat (örneğin, 2 saniye) tek bir yineleme için çok kısa ise, yapılandırılan süre aşılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-191">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="b7c43-192">Bu durumda, gerçek bir model yapılandırmasında tek bir yineleme oluşturmak için gereken zamanı zamandır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-192">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="b7c43-193">Yinelemeler için gereken zaman, veri kümesinin boyutuna bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-193">The needed time for iterations can vary depending on the size of the dataset.</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-194">`--cache | -c` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="b7c43-195">Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellekteki yüklü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="b7c43-196">Küçük ve orta ölçekli veri kümeleri için önbellek kullanarak eğitim süresini önbellek zaman kullanmayın daha kısa olabilir yani eğitim performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="b7c43-197">Bellek yetersiz aldığından ancak, büyük veri kümeleri için bellekteki tüm verileri yüklenirken olumsuz yönde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="b7c43-198">Ne zaman eğitim sırasında daha fazla veri yüklemek gerektiğinde eğitim büyük veri dosyalarını ve önbellek, ML.NET sürücüsünden veri öbekleri akış.</span><span class="sxs-lookup"><span data-stu-id="b7c43-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="b7c43-199">Aşağıdaki değerleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b7c43-199">You can specify the following values:</span></span>

<span data-ttu-id="b7c43-200">`on`: Eğitim yapılırken kullanılacak önbellek zorlar.</span><span class="sxs-lookup"><span data-stu-id="b7c43-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="b7c43-201">`off`: Eğitimindeki kullanılamaz önbellek zorlar.</span><span class="sxs-lookup"><span data-stu-id="b7c43-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="b7c43-202">`auto`: Önbellek veya AutoML buluşsal bağlı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="b7c43-203">Genellikle, küçük/Orta veri kümeleri önbelleğini kullanır ve büyük veri kümeleri, önbellek kullanmayacağınız, kullanırsanız `auto` seçim.</span><span class="sxs-lookup"><span data-stu-id="b7c43-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="b7c43-204">Belirtmezseniz `--cache` parametresi, ardından da önbelleğe `auto` yapılandırma varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-205">`--name | -N` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-205">`--name | -N` (string)</span></span>

<span data-ttu-id="b7c43-206">Oluşturulan çıktı proje veya çözüm adı.</span><span class="sxs-lookup"><span data-stu-id="b7c43-206">The name for the created output project or solution.</span></span> <span data-ttu-id="b7c43-207">Hiçbir ad belirtilmediği takdirde, ad `sample-{mltask}` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-207">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="b7c43-208">ML.NET model dosyası (. ZIP dosyası), aynı adı da alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b7c43-208">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-209">`--output-path | -o` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-209">`--output-path | -o` (string)</span></span>

<span data-ttu-id="b7c43-210">Kök konumu/oluşturulan çıktı yerleştirileceği klasör.</span><span class="sxs-lookup"><span data-stu-id="b7c43-210">Root location/folder to place the generated output.</span></span> <span data-ttu-id="b7c43-211">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-211">The default is the current directory.</span></span>

----------------------------------------------------------

<span data-ttu-id="b7c43-212">`--verbosity | -V` (dize)</span><span class="sxs-lookup"><span data-stu-id="b7c43-212">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="b7c43-213">Standart çıkış ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b7c43-213">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="b7c43-214">İzin verilen değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7c43-214">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="b7c43-215">`m[inimal]`  (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="b7c43-215">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="b7c43-216">`diag[nostic]` (günlük bilgi düzeyi)</span><span class="sxs-lookup"><span data-stu-id="b7c43-216">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="b7c43-217">Varsayılan olarak CLI aracı en az birkaç geri bildirim (minimum) çalışırken, çalışıyor ve eğer mümkünse ne kadar süre sol hangi % sürede tamamlandı mı bahseden gibi göstermelidir.</span><span class="sxs-lookup"><span data-stu-id="b7c43-217">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

----------------------------------------------------------

`-h|--help`

<span data-ttu-id="b7c43-218">Komut için Yardım her komutun parametresi için bir açıklama ile yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b7c43-218">Prints out help for the command with a description for each command's parameter.</span></span>

----------------------------------------------------------

## <a name="see-also"></a><span data-ttu-id="b7c43-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7c43-219">See also</span></span>

- [<span data-ttu-id="b7c43-220">ML.NET CLI Aracı'nı yükleme</span><span class="sxs-lookup"><span data-stu-id="b7c43-220">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="b7c43-221">Model eğitiminin ML.NET CLI ile otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="b7c43-221">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="b7c43-222">Öğretici: ML.NET CLI kullanarak bir ikili dosya sınıflandırıcı otomatik oluştur</span><span class="sxs-lookup"><span data-stu-id="b7c43-222">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="b7c43-223">ML.NET CLI'de telemetri</span><span class="sxs-lookup"><span data-stu-id="b7c43-223">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
