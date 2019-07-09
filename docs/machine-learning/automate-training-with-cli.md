---
title: Model eğitiminin ML.NET CLI ile otomatikleştirme
description: ML.NET CLI aracı otomatik olarak komut satırından en iyi modeli eğitmek için nasıl kullanılacağını keşfedin.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: e5f75dc70ea5a76951d8698ea9c0d07cb2d4ddec
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663932"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="24c26-103">Model eğitiminin ML.NET CLI ile otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="24c26-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="24c26-104">ML.NET CLI "ML.NET .NET geliştiricileri için ML.NET öğrenme, ıot'yi herkesin kullanımına sunan".</span><span class="sxs-lookup"><span data-stu-id="24c26-104">The ML.NET CLI "democratizes" ML.NET for .NET developers when learning ML.NET.</span></span>

<span data-ttu-id="24c26-105">ML.NET API kendisi tarafından (ML.NET AutoML CLI) kullanmak için verilere uygulanacak bir eğitmen (uygulaması belirli bir görev için makine öğrenimi algoritması) ve veri Dönüşümleri (özellik Mühendisliği) kümesini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="24c26-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="24c26-106">En iyi işlem hattı her veri kümesi için farklılık gösterir ve tüm seçenekler arasından en iyi algoritmayı seçerek karmaşıklığa ekler.</span><span class="sxs-lookup"><span data-stu-id="24c26-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="24c26-107">Dahası, her bir algoritmanın ayarlanmasına hiperparametreleri kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="24c26-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="24c26-108">Bu nedenle, özellik Mühendisliği, öğrenme algoritmaları ve hiperparametreleri en iyi kombinasyonu bulunmaya çalışılırken modeli iyileştirme öğrenme makinede haftalar ve bazen ay ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24c26-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="24c26-109">ML.NET AutoML akıllı altyapısı uygulayan ML.NET CLI ile bu işlem otomatikleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="24c26-109">This process can be automated with the ML.NET CLI, which implements the ML.NET AutoML intelligent engine.</span></span>

> [!NOTE]
> <span data-ttu-id="24c26-110">Bu konu için ML.NET başvuruyor **CLI** ve ML.NET **AutoML**, şu anda Önizleme aşamasındadır ve malzeme değişikliğe tabi olabilir.</span><span class="sxs-lookup"><span data-stu-id="24c26-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="24c26-111">ML.NET komut satırı arabirimi (CLI) nedir?</span><span class="sxs-lookup"><span data-stu-id="24c26-111">What is the ML.NET Command-line Interface (CLI)?</span></span>

<span data-ttu-id="24c26-112">ML.NET CLI herhangi komut kaliteli ML.NET modelleri ve eğitim veri kümenize dayalı kaynak kodu oluşturmak için istemi (Windows, Mac veya Linux) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24c26-112">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on your training dataset.</span></span>

<span data-ttu-id="24c26-113">Aşağıdaki çizimde gösterildiği gibi yüksek kaliteli ML.NET modeli (serileştirilmiş modeli .zip dosyası) örnek oluşturmak daha kolaydır C# Çalıştır/puanı bu modeli için kod.</span><span class="sxs-lookup"><span data-stu-id="24c26-113">As shown in the figure below, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="24c26-114">Ayrıca, C# /bu modeli eğitme oluşturmak için kod da oluşturulur, araştırma ve algoritmasına yinelemek ve ayarları için kullanılan oluşturulan "en iyi modeli".</span><span class="sxs-lookup"><span data-stu-id="24c26-114">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="24c26-115">![Görüntü](media/automate-training-with-cli/cli-high-level-process.png "AutoML altyapısı ML.NET CLI içinde çalışma")</span><span class="sxs-lookup"><span data-stu-id="24c26-115">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="24c26-116">ML.NET bildiğiniz olsa bile, ayrıca üretkenliğinizi artıran şekilde kendiniz, kodlama olmadan, bu varlıkları kendi veri kümeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24c26-116">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="24c26-117">Şu anda, ML ML.NET CLI tarafından desteklenen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="24c26-117">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="24c26-118">Gelecekteki: görevler gibi diğer makine öğrenimi `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span><span class="sxs-lookup"><span data-stu-id="24c26-118">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="24c26-119">Kullanım örneği:</span><span class="sxs-lookup"><span data-stu-id="24c26-119">Example of usage:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![görüntü](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="24c26-121">Aynı şekilde üzerinde çalıştırabilirsiniz *Windows PowerShell*, \* macOS/Linux bash veya *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="24c26-121">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="24c26-122">Ancak, tablosal otomatik tamamlama (parametre önerileri) üzerinde çalışmaz *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="24c26-122">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="24c26-123">Oluşturulan çıktı varlıkları</span><span class="sxs-lookup"><span data-stu-id="24c26-123">Output assets generated</span></span>

<span data-ttu-id="24c26-124">CLI'yı `auto-train` komut çıktı klasöründe şu varlıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="24c26-124">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="24c26-125">Serileştirilmiş modeli .zip ("en iyi modeli") Öngörüler çalıştırmak için kullanıma hazır.</span><span class="sxs-lookup"><span data-stu-id="24c26-125">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="24c26-126">C#Çözümle:</span><span class="sxs-lookup"><span data-stu-id="24c26-126">C# solution with:</span></span>
  - <span data-ttu-id="24c26-127">C#kod, Çalıştır/puan modeli (Bu modeli ile son kullanıcı uygulamalarınızda Öngörüler oluşturmak için) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24c26-127">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="24c26-128">C#Eğitim kodla (amacıyla veya modeli yeniden eğitme öğrenme için) Bu modeli oluşturmak için kullanılan kod.</span><span class="sxs-lookup"><span data-stu-id="24c26-128">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="24c26-129">Kendi ayrıntılı yapılandırma/işlem hattı dahil olmak üzere tüm yinelemeleri/süpürmeleri birden fazla bir algoritmalar arasında bilgi günlük dosyası değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="24c26-129">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="24c26-130">İlk iki varlıklar ile oluşturulan, ML model doğrudan, son kullanıcı uygulamaları (ASP.NET Core web uygulaması, hizmetleri, masaüstü uygulaması, vb.) tahminlerde bulunmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24c26-130">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="24c26-131">Üçüncü bir varlık, eğitim kod gösterir, hangi ML.NET API kodu CLI tarafından oluşturulan modeli eğitmek için kullanılan, modelinizi yeniden eğitme ve araştırabilir ve yineleme yapmak için hangi belirli trainer/algoritması ve hiperparametreleri AutoML ve CLI seçilmedi Perde.</span><span class="sxs-lookup"><span data-stu-id="24c26-131">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="24c26-132">Model kalitesini anlama</span><span class="sxs-lookup"><span data-stu-id="24c26-132">Understanding the quality of the model</span></span>

<span data-ttu-id="24c26-133">CLI aracını kullanarak 'en iyi modeli' oluştururken, hedeflediğiniz ML görev için uygun Kalite Ölçümleri (doğruluk gibi ve R karesi alınmış) bakın.</span><span class="sxs-lookup"><span data-stu-id="24c26-133">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy, and R-Squared) as appropriate for the ML task you are targeting.</span></span>

<span data-ttu-id="24c26-134">Burada bu ölçümleri otomatik olarak oluşturulan 'en iyi modelinizin kalitesini ' anlayabilmeniz ML görevine göre gruplandırılmış özetler.</span><span class="sxs-lookup"><span data-stu-id="24c26-134">Here we summarize those metrics grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="24c26-135">İkili sınıflandırma modelleri için ölçümleri</span><span class="sxs-lookup"><span data-stu-id="24c26-135">Metrics for Binary Classification models</span></span>

<span data-ttu-id="24c26-136">CLI tarafından bulunan ilk beş modelleri için ikili sınıflandırma ML görev ölçümleri listesi görüntüler:</span><span class="sxs-lookup"><span data-stu-id="24c26-136">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![görüntü](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="24c26-138">Doğruluk her zaman aşağıdaki başvuruları içinde anlatıldığı gibi en iyi modeli seçmek için en iyi ölçüm değildir ancak doğruluk sınıflandırma sorunlar için popüler bir unsurdur.</span><span class="sxs-lookup"><span data-stu-id="24c26-138">Accuracy is a popular metric for classification problems, however accuracy is not always the best metric to select the best model from as explained in the references below.</span></span> <span data-ttu-id="24c26-139">Ek ölçümler ile modelinizin kalitesini değerlendirmek için gerek duyduğunuz durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="24c26-139">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="24c26-140">Keşfedin ve CLI tarafından çıkarılan ölçümleri anlamak için bkz: [ikili sınıflandırma için ölçümleri](resources/metrics.md#metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="24c26-140">To explore and understand the metrics that are output by the CLI, see [Metrics for binary classification](resources/metrics.md#metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="24c26-141">Çok sınıflı sınıflandırma modelleri için ölçümleri</span><span class="sxs-lookup"><span data-stu-id="24c26-141">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="24c26-142">CLI tarafından bulunan ilk beş modellerine yönelik çok sınıflı sınıflandırma ML görev ölçümleri listesi görüntüler:</span><span class="sxs-lookup"><span data-stu-id="24c26-142">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![görüntü](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="24c26-144">Keşfedin ve CLI tarafından çıkarılan ölçümleri anlamak için bkz: [sınıflı sınıflandırma için ölçümleri](resources/metrics.md#metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="24c26-144">To explore and understand the metrics that are output by the CLI, see [Metrics for multiclass classification](resources/metrics.md#metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-models"></a><span data-ttu-id="24c26-145">Regresyon modelleri için ölçümleri</span><span class="sxs-lookup"><span data-stu-id="24c26-145">Metrics for Regression models</span></span>

<span data-ttu-id="24c26-146">Küçük ve popülasyon modelin tahmin edilen değerler gözlenen değerler arasındaki farkları da, verileri bir regresyon modeli uyar.</span><span class="sxs-lookup"><span data-stu-id="24c26-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="24c26-147">Regresyon, belirli ölçümleri ile değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="24c26-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="24c26-148">CLI tarafından bulunan en iyi en çok beş kalite modellerine yönelik ölçümleri, benzer bir listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="24c26-148">You will see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="24c26-149">Bu durumda, ML görev için bir regresyon ilgili:</span><span class="sxs-lookup"><span data-stu-id="24c26-149">In this particular case related to a regression ML task:</span></span>

![görüntü](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="24c26-151">Keşfedin ve CLI tarafından çıkarılan ölçümleri anlamak için bkz: [regresyon ölçümlerini](resources/metrics.md#metrics-for-regression).</span><span class="sxs-lookup"><span data-stu-id="24c26-151">To explore and understand the metrics that are output by the CLI, see [Metrics for regression](resources/metrics.md#metrics-for-regression).</span></span>

## <a name="see-also"></a><span data-ttu-id="24c26-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24c26-152">See also</span></span>

- [<span data-ttu-id="24c26-153">ML.NET CLI Aracı'nı yükleme</span><span class="sxs-lookup"><span data-stu-id="24c26-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="24c26-154">Öğretici: ML.NET CLI kullanarak bir ikili dosya sınıflandırıcı otomatik oluştur</span><span class="sxs-lookup"><span data-stu-id="24c26-154">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](tutorials/mlnet-cli.md)
- [<span data-ttu-id="24c26-155">ML.NET CLI komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="24c26-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="24c26-156">ML.NET CLI'de telemetri</span><span class="sxs-lookup"><span data-stu-id="24c26-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
