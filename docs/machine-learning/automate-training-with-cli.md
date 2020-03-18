---
title: ML.NET CLI ile model eğitimini otomatikleştirin
description: Komut satırından en iyi modeli otomatik olarak eğitmek için ML.NET CLI aracını nasıl kullanacağımı keşfedin.
ms.date: 12/17/2019
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 3344ed15266503d4d5c7cd9db0a0596f58a904fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185889"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="50a90-103">ML.NET CLI ile model eğitimini otomatikleştirin</span><span class="sxs-lookup"><span data-stu-id="50a90-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="50a90-104">cli ML.NET .NET geliştiricileri için model oluşturma otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="50a90-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="50a90-105">ML.NET API'yi tek başına kullanmak için (automl CLI ML.NET olmadan) bir eğitmen (belirli bir görev için makine öğrenimi algoritması uygulaması) ve verilerinize uygulamak için veri dönüşümleri kümesini (özellik mühendisliği) seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="50a90-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="50a90-106">En uygun ardışık düzen hattı her veri kümesi için değişir ve tüm seçeneklerden en uygun algoritmaseçerek karmaşıklığı ekler.</span><span class="sxs-lookup"><span data-stu-id="50a90-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="50a90-107">Dahası, her algoritmanın ayarlanacak bir dizi hiperparametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="50a90-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="50a90-108">Bu nedenle, özellik mühendisliği, öğrenme algoritmaları ve hiperparametrelerin en iyi kombinasyonlarını bulmaya çalışarak makine öğrenimi modeli optimizasyonu üzerinde haftalar ve bazen aylar geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50a90-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="50a90-109">CLI ML.NET otomatik makine öğrenimi (AutoML) kullanarak bu işlemi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="50a90-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="50a90-110">Bu konu, şu anda Önizleme'de olan **cli** ve ML.NET **AutoML**ML.NET anlamına gelir ve malzeme değişebilir.</span><span class="sxs-lookup"><span data-stu-id="50a90-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="50a90-111">komut satırı arabirimi (CLI) ML.NET nedir?</span><span class="sxs-lookup"><span data-stu-id="50a90-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="50a90-112">CLI ML.NET bir [.NET Core aracıdır.](../core/tools/global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="50a90-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="50a90-113">Yüklendikten sonra, bir makine öğrenme görevi ve bir eğitim veri seti vermek ve bir ML.NET modeli yanı sıra uygulamanızda modeli kullanmak için çalıştırmak için C# kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50a90-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="50a90-114">Aşağıdaki şekilde gösterildiği gibi, yüksek kaliteli bir ML.NET modeli (serileştirilmiş model .zip dosyası) artı örnek C# kodu çalıştırmak / bu modeli puan oluşturmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="50a90-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="50a90-115">Buna ek olarak, bu modeli oluşturmak/eğitmek için C# kodu da oluşturulur, böylece "en iyi model" için kullanılan algoritma ve ayarları araştırabilir ve yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50a90-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="50a90-116">![Görüntü](media/automate-training-with-cli/cli-high-level-process.png "CLI ML.NET içinde çalışan AutoML motoru")</span><span class="sxs-lookup"><span data-stu-id="50a90-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="50a90-117">Bu varlıkları kendi veri kümelerinizden kendi kodlamadan oluşturabilirsiniz, bu nedenle ML.NET bildiğiniz halde üretkenliğinizi de artırır.</span><span class="sxs-lookup"><span data-stu-id="50a90-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="50a90-118">Şu anda, CLI ML.NET tarafından desteklenen ML Görevleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="50a90-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="50a90-119">Gelecek: gibi diğer makine `recommendation` `ranking`öğrenme `anomaly-detection`görevleri , , ,`clustering`</span><span class="sxs-lookup"><span data-stu-id="50a90-119">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="50a90-120">Kullanım örneği:</span><span class="sxs-lookup"><span data-stu-id="50a90-120">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="50a90-122">*Windows PowerShell*, \*macOS/Linux bash veya *Windows CMD'de*aynı şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50a90-122">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="50a90-123">Ancak, tabular otomatik tamamlama (parametre önerileri) *Windows CMD*üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="50a90-123">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="50a90-124">Üretilen çıktı varlıkları</span><span class="sxs-lookup"><span data-stu-id="50a90-124">Output assets generated</span></span>

<span data-ttu-id="50a90-125">CLI `auto-train` komutu çıktı klasöründe aşağıdaki varlıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="50a90-125">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="50a90-126">Serileştirilmiş bir model .zip ("en iyi model") tahminleri çalıştırmak için kullanıma hazır.</span><span class="sxs-lookup"><span data-stu-id="50a90-126">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="50a90-127">C# çözeltisi:</span><span class="sxs-lookup"><span data-stu-id="50a90-127">C# solution with:</span></span>
  - <span data-ttu-id="50a90-128">C# kodu ( bu model ile son kullanıcı uygulamalarında öngörüler yapmak için) oluşturulan modeli çalıştırmak / puan.</span><span class="sxs-lookup"><span data-stu-id="50a90-128">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="50a90-129">Bu modeli oluşturmak için kullanılan eğitim kodu ile C# kodu (öğrenme amaçlı veya model yeniden eğitim için).</span><span class="sxs-lookup"><span data-stu-id="50a90-129">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="50a90-130">Ayrıntılı yapılandırma/ardışık hatlar da dahil olmak üzere, değerlendirilen birden çok algoritma arasında tüm yinelemelerin/taramaların bilgilerini içeren günlük dosyası.</span><span class="sxs-lookup"><span data-stu-id="50a90-130">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="50a90-131">İlk iki varlık, oluşturulan ML modeliyle öngörülerde bulunmak için son kullanıcı uygulamalarınızda (ASP.NET Core web uygulaması, hizmetler, masaüstü uygulaması, vb.) doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50a90-131">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="50a90-132">Üçüncü varlık, eğitim kodu, oluşturulan modeli eğitmek için CLI tarafından ne ML.NET API kodunun kullanıldığını gösterir, böylece modelinizi yeniden eğitebilir ve cli ve AutoML tarafından kapakların altında belirli eğitmen/algoritma ve hiperparametrelerin seçildiğini araştırabilir ve yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50a90-132">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="50a90-133">Modelin kalitesini anlama</span><span class="sxs-lookup"><span data-stu-id="50a90-133">Understanding the quality of the model</span></span>

<span data-ttu-id="50a90-134">CLI aracıyla bir 'en iyi model' oluşturduğunuzda, hedeflediğiniz ML görevi için uygun olarak kalite ölçümleri (doğruluk ve R-Squared gibi) görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="50a90-134">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="50a90-135">Burada bu ölçümler ML görev tarafından gruplandırılır, böylece otomatik olarak oluşturulan 'en iyi model'in kalitesini anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50a90-135">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="50a90-136">İkili Sınıflandırma modelleri için ölçümler</span><span class="sxs-lookup"><span data-stu-id="50a90-136">Metrics for Binary Classification models</span></span>

<span data-ttu-id="50a90-137">Aşağıdaki cli tarafından bulunan ilk beş model için ikili sınıflandırma ML görev ölçümleri listesini görüntüler:</span><span class="sxs-lookup"><span data-stu-id="50a90-137">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="50a90-139">Doğruluk sınıflandırma sorunları için popüler bir metriktir, ancak doğruluk her zaman aşağıdaki başvurularda açıklandığı gibi en iyi modeli seçmek için en iyi metrik değildir.</span><span class="sxs-lookup"><span data-stu-id="50a90-139">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="50a90-140">Ek ölçümlerle modelinizin kalitesini değerlendirmeniz gereken durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="50a90-140">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="50a90-141">CLI tarafından çıktı edilen ölçümleri keşfetmek ve anlamak [için ikili sınıflandırma için Değerlendirme ölçümlerine](resources/metrics.md#evaluation-metrics-for-binary-classification)bakın.</span><span class="sxs-lookup"><span data-stu-id="50a90-141">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for binary classification](resources/metrics.md#evaluation-metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="50a90-142">Çok Sınıflı Sınıflandırma modelleri için ölçümler</span><span class="sxs-lookup"><span data-stu-id="50a90-142">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="50a90-143">CLI tarafından bulunan ilk beş model için çok sınıflı sınıflandırma ML görev ölçümleri listesini aşağıda görüntüler:</span><span class="sxs-lookup"><span data-stu-id="50a90-143">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="50a90-145">CLI tarafından çıktı edilen ölçümleri keşfetmek ve anlamak [için, çok sınıflı sınıflandırma için Değerlendirme ölçümlerine](resources/metrics.md#evaluation-metrics-for-multi-class-classification)bakın.</span><span class="sxs-lookup"><span data-stu-id="50a90-145">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for multiclass classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="50a90-146">Regresyon ve Öneri modelleri için ölçümler</span><span class="sxs-lookup"><span data-stu-id="50a90-146">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="50a90-147">Gözlenen değerler ile modelin öngörülen değerleri arasındaki farklar küçük ve tarafsızsa, bir regresyon modeli verilere iyi uyar.</span><span class="sxs-lookup"><span data-stu-id="50a90-147">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="50a90-148">Regresyon belirli ölçümlerle değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="50a90-148">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="50a90-149">CLI tarafından bulunan en iyi beş kaliteli model için benzer bir ölçüm listesi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="50a90-149">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="50a90-150">Bu özel durumda bir regresyon ML görev ile ilgili:</span><span class="sxs-lookup"><span data-stu-id="50a90-150">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="50a90-152">CLI tarafından çıktı edilen ölçümleri keşfetmek ve anlamak [için, regresyon için Değerlendirme ölçümlerine](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)bakın.</span><span class="sxs-lookup"><span data-stu-id="50a90-152">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="50a90-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50a90-153">See also</span></span>

- [<span data-ttu-id="50a90-154">ML.NET CLI aracı nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="50a90-154">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="50a90-155">Öğretici: CLI ML.NET kullanarak duyguları analiz edin</span><span class="sxs-lookup"><span data-stu-id="50a90-155">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="50a90-156">ML.NET CLI komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="50a90-156">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="50a90-157">ML.NET CLI'de telemetri</span><span class="sxs-lookup"><span data-stu-id="50a90-157">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
