---
title: ML.NET CLI Komut Başvurusu
description: ML.NET CLI aracındaki otomatik tren komutu için genel bakış, örnekler ve başvuru.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: bb161c596a76134876ee2bf0a6229bc551e0dad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848931"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="86a63-103">cli komut başvurusu ML.NET</span><span class="sxs-lookup"><span data-stu-id="86a63-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="86a63-104">Komut, `auto-train` cli aracının ML.NET tarafından sağlanan ana komutdur.</span><span class="sxs-lookup"><span data-stu-id="86a63-104">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="86a63-105">Komut, otomatik makine öğrenimi (AutoML) yanı sıra bu modeli çalıştırmak / puan için örnek C# kodu kullanarak iyi bir kaliteli ML.NET modeli oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="86a63-105">The command allows you to generate a good quality ML.NET model using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="86a63-106">Buna ek olarak, modeli eğitmek için C# kodu, modelin algoritmasını ve ayarlarını araştırmanız için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="86a63-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="86a63-107">Bu konu, şu anda Önizleme'de olan cli ve ML.NET AutoML'ML.NET anlamına gelir ve malzeme değişebilir.</span><span class="sxs-lookup"><span data-stu-id="86a63-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="86a63-108">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86a63-108">Overview</span></span>

<span data-ttu-id="86a63-109">Örnek kullanım: </span><span class="sxs-lookup"><span data-stu-id="86a63-109">Example usage:</span></span>

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="86a63-110">Komut `mlnet auto-train` aşağıdaki varlıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="86a63-110">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="86a63-111">Serileştirilmiş bir model .zip ("en iyi model") kullanıma hazır.</span><span class="sxs-lookup"><span data-stu-id="86a63-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="86a63-112">C# kodu modeli oluşturulan çalıştırmak / puan.</span><span class="sxs-lookup"><span data-stu-id="86a63-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="86a63-113">Bu modeli oluşturmak için kullanılan eğitim kodu ile C# kodu.</span><span class="sxs-lookup"><span data-stu-id="86a63-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="86a63-114">İlk iki varlık, modelle ilgili öngörülerde bulunmak için doğrudan son kullanıcı uygulamalarınızda (ASP.NET Core web uygulaması, hizmetler, masaüstü uygulaması ve daha fazlası) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86a63-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="86a63-115">Üçüncü varlık, eğitim kodu, oluşturulan modeli eğitmek için CLI tarafından ML.NET API kodunun ne ML.NET kullanıldığını gösterir, böylece modelin belirli algoritmasını ve ayarlarını inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86a63-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="86a63-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="86a63-116">Examples</span></span>

<span data-ttu-id="86a63-117">İkili sınıflandırma sorunu için en basit CLI komutu (AutoML, sağlanan verilerden yapılandırmanın çoğunu çıkartır):</span><span class="sxs-lookup"><span data-stu-id="86a63-117">The simplest CLI command for a binary classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="86a63-118">Bir gerileme sorunu için başka bir basit CLI komutu:</span><span class="sxs-lookup"><span data-stu-id="86a63-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="86a63-119">Bir tren veri kümesi, test veri kümesi ve daha fazla özelleştirme açık bağımsız değişkenleri ile bir ikili sınıflandırma modeli oluşturun ve train:</span><span class="sxs-lookup"><span data-stu-id="86a63-119">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a><span data-ttu-id="86a63-120">Komut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="86a63-120">Command options</span></span>

<span data-ttu-id="86a63-121">`mlnet auto-train`sağlanan veri kümesine göre birden çok modeli eğitir ve son olarak en iyi modeli seçer, serileştirilmiş .zip dosyası olarak kaydeder artı puanlama ve eğitim için ilgili C# kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86a63-121">`mlnet auto-train` trains multiple models based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

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

<span data-ttu-id="86a63-122">Geçersiz giriş seçenekleri, CLI aracının geçerli girdilerin ve bir hata iletisinin listesini yarayabmasını neden olur.</span><span class="sxs-lookup"><span data-stu-id="86a63-122">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="task"></a><span data-ttu-id="86a63-123">Görev</span><span class="sxs-lookup"><span data-stu-id="86a63-123">Task</span></span>

<span data-ttu-id="86a63-124">`--task | --mltask | -T`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-124">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="86a63-125">Ml sorunu çözmek için sağlayan tek bir dize.</span><span class="sxs-lookup"><span data-stu-id="86a63-125">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="86a63-126">Örneğin, aşağıdaki görevlerden herhangi biri (CLI sonunda AutoML'de desteklenen tüm görevleri destekler):</span><span class="sxs-lookup"><span data-stu-id="86a63-126">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="86a63-127">`regression`- ML Modeli'nin sayısal bir değeri tahmin etmek için kullanIlip kullanılmeyeceğini seçin</span><span class="sxs-lookup"><span data-stu-id="86a63-127">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="86a63-128">`binary-classification`- ML Model sonucunun iki olası kategorik boolean değeri (0 veya 1) olup olmadığını seçin.</span><span class="sxs-lookup"><span data-stu-id="86a63-128">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="86a63-129">`multiclass-classification`- ML Model sonucunun birden çok kategorik olası değeri olup olmadığını seçin.</span><span class="sxs-lookup"><span data-stu-id="86a63-129">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="86a63-130">Bu bağımsız değişkende yalnızca bir ML görevi sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86a63-130">Only one ML task should be provided in this argument.</span></span>

## <a name="dataset"></a><span data-ttu-id="86a63-131">Veri kümesi</span><span class="sxs-lookup"><span data-stu-id="86a63-131">Dataset</span></span>

<span data-ttu-id="86a63-132">`--dataset | -d`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-132">`--dataset | -d` (string)</span></span>

<span data-ttu-id="86a63-133">Bu bağımsız değişken, aşağıdaki seçeneklerden birine dosya yolunu sağlar:</span><span class="sxs-lookup"><span data-stu-id="86a63-133">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="86a63-134">*C: Tüm veri kümesi dosyası:* Bu seçeneği kullanarak ve kullanıcı `--test-dataset` sağmıyorsa `--validation-dataset`ve sonra çapraz doğrulama (k-fold, vb) veya otomatik veri bölme yaklaşımları modeli doğrulamak için dahili olarak kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="86a63-134">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="86a63-135">Bu durumda, kullanıcının yalnızca veri kümesi dosya yolunu sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="86a63-135">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="86a63-136">*B: Eğitim veri seti dosyası:* Kullanıcı ayrıca model doğrulama (kullanarak `--test-dataset` ve isteğe bağlı `--validation-dataset`olarak) `--dataset` için veri kümeleri sağlıyorsa, bağımsız değişken yalnızca "eğitim veri kümesine" sahip olmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="86a63-136">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="86a63-137">Örneğin, modelin kalitesini doğrulamak ve doğruluk ölçümleri elde etmek için %80 - %20'lik bir yaklaşım kullanırken, "eğitim veri kümesi" verilerin %80'ine ve "test veri kümesi" verilerin %20'sine sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="86a63-137">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="86a63-138">Test veri kümesi</span><span class="sxs-lookup"><span data-stu-id="86a63-138">Test dataset</span></span>

<span data-ttu-id="86a63-139">`--test-dataset | -t`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-139">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="86a63-140">Doğruluk ölçümleri elde etmek için düzenli doğrulama yaparken örneğin %80 - %20'lik bir yaklaşım kullanırken, test veri kümesi dosyasını gösteren dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="86a63-140">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="86a63-141">Kullanıyorsanız, `--test-dataset` `--dataset` o zaman da gereklidir.</span><span class="sxs-lookup"><span data-stu-id="86a63-141">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="86a63-142">--doğrulama-veri kümesi kullanılmadığı sürece `--test-dataset` bağımsız değişken isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="86a63-142">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="86a63-143">Bu durumda, kullanıcı üç bağımsız değişkeni kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86a63-143">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="86a63-144">Doğrulama veri kümesi</span><span class="sxs-lookup"><span data-stu-id="86a63-144">Validation dataset</span></span>

<span data-ttu-id="86a63-145">`--validation-dataset | -v`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-145">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="86a63-146">Doğrulama veri kümesi dosyasını gösteren dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="86a63-146">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="86a63-147">Doğrulama veri kümesi her durumda isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="86a63-147">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="86a63-148">Bir `validation dataset`kullanıyorsanız, davranış olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="86a63-148">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="86a63-149">Ve `test-dataset` `--dataset` bağımsız değişkenler de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="86a63-149">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="86a63-150">Veri `validation-dataset` kümesi, model seçimi için tahmin hatasını tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86a63-150">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="86a63-151">Son `test-dataset` seçilen modelin genelleme hatasının değerlendirilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86a63-151">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="86a63-152">İdeal olarak, test seti bir "kasada" tutulmalı ve yalnızca veri analizinin sonunda çıkarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86a63-152">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="86a63-153">Temel olarak, `validation dataset` bir `test dataset`artı kullanırken , doğrulama aşaması iki bölüme ayrılır:</span><span class="sxs-lookup"><span data-stu-id="86a63-153">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="86a63-154">İlk bölümde, sadece modelleribakmak ve doğrulama verileri (= doğrulama) kullanarak en iyi performans yaklaşım seçin</span><span class="sxs-lookup"><span data-stu-id="86a63-154">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="86a63-155">Daha sonra seçili yaklaşımın (=test) doğruluğunu tahmin emzebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86a63-155">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="86a63-156">Bu nedenle, veri ayırma 80/10/10 veya 75/15/10 olabilir.</span><span class="sxs-lookup"><span data-stu-id="86a63-156">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="86a63-157">Örnek:</span><span class="sxs-lookup"><span data-stu-id="86a63-157">For example:</span></span>

- <span data-ttu-id="86a63-158">`training-dataset`dosya verilerin% 75 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86a63-158">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="86a63-159">`validation-dataset`dosya verilerin% 15 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86a63-159">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="86a63-160">`test-dataset`dosya verilerin% 10 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86a63-160">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="86a63-161">Her durumda, bu yüzdeler zaten bölünmüş dosyaları sağlayacak CLI kullanarak kullanıcı tarafından karar verilecektir.</span><span class="sxs-lookup"><span data-stu-id="86a63-161">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column-name"></a><span data-ttu-id="86a63-162">Etiket sütun adı</span><span class="sxs-lookup"><span data-stu-id="86a63-162">Label column name</span></span>

<span data-ttu-id="86a63-163">`--label-column-name | -n`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-163">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="86a63-164">Bu bağımsız değişkenle, belirli bir hedef/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin üstbilgisinde sütunun ad kümesi kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="86a63-164">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="86a63-165">Bu bağımsız değişken yalnızca *sınıflandırma sorunu*gibi denetlenen ML görevleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86a63-165">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="86a63-166">*Kümeleme*gibi denetimsiz ML Görevleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="86a63-166">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="label-column-index"></a><span data-ttu-id="86a63-167">Etiket sütun dizini</span><span class="sxs-lookup"><span data-stu-id="86a63-167">Label column index</span></span>

<span data-ttu-id="86a63-168">`--label-column-index | -i`(int)</span><span class="sxs-lookup"><span data-stu-id="86a63-168">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="86a63-169">Bu bağımsız değişkenle, belirli bir hedef/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin dosyasındaki sütunun sayısal dizini kullanılarak belirtilebilir (Sütun dizin değerleri 1'den başlar).</span><span class="sxs-lookup"><span data-stu-id="86a63-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="86a63-170">*Not:* Kullanıcı da `--label-column-name`kullanıyorsa, `--label-column-name` kullanılan biridir.</span><span class="sxs-lookup"><span data-stu-id="86a63-170">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="86a63-171">Bu bağımsız değişken yalnızca bir sınıflandırma *sorunu*gibi denetlenen ML görevi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86a63-171">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="86a63-172">*Kümeleme*gibi denetimsiz ML Görevleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="86a63-172">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="86a63-173">Sütunları yoksay</span><span class="sxs-lookup"><span data-stu-id="86a63-173">Ignore columns</span></span>

<span data-ttu-id="86a63-174">`--ignore-columns | -I`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-174">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="86a63-175">Bu bağımsız değişkenle, veri kümesi dosyasındaki varolan sütunları, eğitim işlemleri tarafından yüklenmedikleri ve kullanılmaması için yok sayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86a63-175">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="86a63-176">Yoksaymak istediğiniz sütun adlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="86a63-176">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="86a63-177">Birden çok sütun adını ayırmak için ',' (boşlukla virgül) veya ' ' (boşluk) kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a63-177">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="86a63-178">Beyaz boşluk içeren sütun adları için tırnak işaretleri kullanabilirsiniz (örn. "oturum açmış").</span><span class="sxs-lookup"><span data-stu-id="86a63-178">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="86a63-179">Örnek:</span><span class="sxs-lookup"><span data-stu-id="86a63-179">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="86a63-180">Üstbilgi var</span><span class="sxs-lookup"><span data-stu-id="86a63-180">Has header</span></span>

<span data-ttu-id="86a63-181">`--has-header | -h`(bool)</span><span class="sxs-lookup"><span data-stu-id="86a63-181">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="86a63-182">Veri kümesi dosyasının üstbilgi satırı olup olmadığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="86a63-182">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="86a63-183">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86a63-183">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="86a63-184">Varsayılan değer, `true` bu bağımsız değişkenin kullanıcı tarafından belirtilmemiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="86a63-184">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="86a63-185">Bağımsız değişkeni `--label-column-name` kullanmak için, veri kümesi dosyasında bir üstbilgi nin olması ve `--has-header` `true` (varsayılan olarak) ayarlanabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="86a63-185">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

## <a name="max-exploration-time"></a><span data-ttu-id="86a63-186">Maksimum arama süresi</span><span class="sxs-lookup"><span data-stu-id="86a63-186">Max exploration time</span></span>

<span data-ttu-id="86a63-187">`--max-exploration-time | -x`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-187">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="86a63-188">Varsayılan olarak, maksimum arama süresi 30 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="86a63-188">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="86a63-189">Bu bağımsız değişken, işlemin birden çok eğitmeni ve yapılandırmayı keşfetmesi için en fazla zamanı (saniye cinsinden) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="86a63-189">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="86a63-190">Sağlanan süre tek bir yineleme için çok kısaysa (örneğin 2 saniye) yapılandırılan süre aşılabilir.</span><span class="sxs-lookup"><span data-stu-id="86a63-190">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="86a63-191">Bu durumda, gerçek zaman tek bir yinelemede bir model yapılandırması üretmek için gerekli zamandır.</span><span class="sxs-lookup"><span data-stu-id="86a63-191">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="86a63-192">Yinelemeler için gereken süre, veri kümesinin boyutuna bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="86a63-192">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="86a63-193">Önbellek</span><span class="sxs-lookup"><span data-stu-id="86a63-193">Cache</span></span>

<span data-ttu-id="86a63-194">`--cache | -c`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="86a63-195">Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellekte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="86a63-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="86a63-196">Küçük ve orta veri kümeleri için önbellek kullanmak eğitim performansını önemli ölçüde artırabilir, bu da eğitim süresinin önbelleği kullanmadığınız zamankinden daha kısa olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="86a63-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="86a63-197">Ancak, büyük veri kümeleri için bellekteki tüm verilerin yüklenmesi, bellekten çıkabileceğiniz için olumsuz etki gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="86a63-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="86a63-198">Büyük veri kümesi dosyalarıyla eğitim alırken ve önbellek kullanmazken, ML.NET, eğitim sırasında daha fazla veri yüklemesi gerektiğinde sürücüden veri yığınları akışı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="86a63-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="86a63-199">Aşağıdaki değerleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86a63-199">You can specify the following values:</span></span>

<span data-ttu-id="86a63-200">`on`: Eğitim de kullanılacak önbelleği zorlar.</span><span class="sxs-lookup"><span data-stu-id="86a63-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="86a63-201">`off`: Eğitim de kullanılmaması için önbelleği zorlar.</span><span class="sxs-lookup"><span data-stu-id="86a63-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="86a63-202">`auto`: AutoML sezgisel bağlı olarak, önbellek kullanılacak veya kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="86a63-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="86a63-203">Genellikle, küçük/orta veri kümeleri önbellek kullanır ve `auto` seçimi kullanırsanız büyük veri kümeleri önbellek kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="86a63-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="86a63-204">Parametreyi `--cache` belirtmezseniz, önbellek `auto` yapılandırması varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86a63-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="86a63-205">Adı</span><span class="sxs-lookup"><span data-stu-id="86a63-205">Name</span></span>

<span data-ttu-id="86a63-206">`--name | -N`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-206">`--name | -N` (string)</span></span>

<span data-ttu-id="86a63-207">Oluşturulan çıktı projesinin veya çözümün adı.</span><span class="sxs-lookup"><span data-stu-id="86a63-207">The name for the created output project or solution.</span></span> <span data-ttu-id="86a63-208">Ad belirtilmemişse, `sample-{mltask}` ad kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86a63-208">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="86a63-209">ML.NET modeli dosyası (. ZIP dosyası) de aynı adı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="86a63-209">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="86a63-210">Çıkış yolu</span><span class="sxs-lookup"><span data-stu-id="86a63-210">Output path</span></span>

<span data-ttu-id="86a63-211">`--output-path | -o`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-211">`--output-path | -o` (string)</span></span>

<span data-ttu-id="86a63-212">Oluşturulan çıktıyı yerleştirmek için kök konumu/klasörü.</span><span class="sxs-lookup"><span data-stu-id="86a63-212">Root location/folder to place the generated output.</span></span> <span data-ttu-id="86a63-213">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="86a63-213">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="86a63-214">Ayrıntı Düzeyi</span><span class="sxs-lookup"><span data-stu-id="86a63-214">Verbosity</span></span>

<span data-ttu-id="86a63-215">`--verbosity | -V`(dize)</span><span class="sxs-lookup"><span data-stu-id="86a63-215">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="86a63-216">Standart çıktının ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="86a63-216">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="86a63-217">İzin verilen değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86a63-217">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="86a63-218">`m[inimal]`(varsayılan olarak)</span><span class="sxs-lookup"><span data-stu-id="86a63-218">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="86a63-219">`diag[nostic]`(günlük bilgi düzeyi)</span><span class="sxs-lookup"><span data-stu-id="86a63-219">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="86a63-220">Varsayılan olarak, CLI aracı çalışırken, çalıştığını ve mümkünse ne kadar zaman kaldığını veya %ne kadar Zaman'ın tamamlandığını belirtmek gibi bazı minimum geri bildirimleri (minimal) göstermelidir.</span><span class="sxs-lookup"><span data-stu-id="86a63-220">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="86a63-221">Yardım</span><span class="sxs-lookup"><span data-stu-id="86a63-221">Help</span></span>

`-h|--help`

<span data-ttu-id="86a63-222">Her komutun parametresi için bir açıklama içeren komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="86a63-222">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="86a63-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86a63-223">See also</span></span>

- [<span data-ttu-id="86a63-224">ML.NET CLI aracı nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="86a63-224">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="86a63-225">ML.NET CLI'ye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86a63-225">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="86a63-226">Öğretici: CLI ML.NET kullanarak duyguları analiz edin</span><span class="sxs-lookup"><span data-stu-id="86a63-226">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="86a63-227">ML.NET CLI'de telemetri</span><span class="sxs-lookup"><span data-stu-id="86a63-227">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
