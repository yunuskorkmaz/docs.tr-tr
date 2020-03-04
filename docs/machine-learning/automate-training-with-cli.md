---
title: ML.NET CLı ile model eğitimi otomatikleştirin
description: Komut satırından en iyi modeli otomatik olarak eğiteiçin ML.NET CLı aracının nasıl kullanılacağını öğrenin.
ms.date: 12/17/2019
ms.custom: how-to
ms.openlocfilehash: 9c493b1df0dd326ad2f0a5d1cac0fc11d7cf37e2
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240629"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="8ef0d-103">ML.NET CLı ile model eğitimi otomatikleştirin</span><span class="sxs-lookup"><span data-stu-id="8ef0d-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="8ef0d-104">ML.NET CLı, .NET geliştiricileri için model oluşturmayı otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="8ef0d-105">ML.NET API 'sini kendisiyle kullanmak için (ML.NET Düzml CLı olmadan), bir daha (belirli bir görev için makine öğrenimi algoritması uygulaması) ve verilerinize uygulanacak veri dönüştürmeleri (özellik Mühendisliği) kümesini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="8ef0d-106">En iyi işlem hattı her bir veri kümesi için farklılık gösterir ve tüm seçeneklerden en uygun algoritmayı belirlemek karmaşıklığa ekler.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="8ef0d-107">Ayrıca, her algoritmanın ayarlanabilir bir hiper parametre kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="8ef0d-108">Bu nedenle, özellik mühendisliğinin, öğrenme algoritmalarının ve hiper parametrelerin en iyi birleşimlerini bulmaya çalışarak, hafta ve bazen aylık olarak makine öğrenimi modeli iyileştirmesi harcamanıza izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="8ef0d-109">ML.NET CLı, otomatik makine öğrenimi (Otomatikml) kullanarak bu işlemi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span> 

> [!NOTE]
> <span data-ttu-id="8ef0d-110">Bu konu, şu anda önizleme aşamasında olan ML.NET **CLI** ve ml.net **oto ml**'ye başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="8ef0d-111">ML.NET komut satırı arabirimi (CLı) nedir?</span><span class="sxs-lookup"><span data-stu-id="8ef0d-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="8ef0d-112">ML.NET CLı, bir [.NET Core aracıdır](../core/tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="8ef0d-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="8ef0d-113">Yüklendikten sonra, bir makine öğrenimi görevi ve eğitim veri kümesi verirsiniz ve bir ML.NET modeli, ayrıca uygulamanızdaki modeli kullanmak için çalıştırılacak C# kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="8ef0d-114">Aşağıdaki şekilde gösterildiği gibi, yüksek kaliteli bir ML.NET modeli (serileştirilmiş model. zip dosyası) ve bu modeli çalıştırmak/skor için örnek C# kodu oluşturmak basittir.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="8ef0d-115">Ayrıca, bu model C# oluşturma/eğitme kodu da oluşturulur. böylece, bu oluşturulan "en iyi model" için kullanılan algoritmayı ve ayarları araştırıp yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="8ef0d-116">![görüntüyle](media/automate-training-with-cli/cli-high-level-process.png "ML.NET CLı içinde çalışan oto ml altyapısı")</span><span class="sxs-lookup"><span data-stu-id="8ef0d-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="8ef0d-117">Kendi veri kümelerinizde, sizin tarafınızdan kodlamadan bu varlıkları oluşturabilirsiniz. bu sayede, ML.NET zaten tanıyor olsanız bile üretkenliğinizi de artırır.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="8ef0d-118">Şu anda, ML.NET CLı tarafından desteklenen ML görevleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8ef0d-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="8ef0d-119">Gelecekte: `recommendation`, `ranking`, `anomaly-detection`, `clustering` gibi diğer makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="8ef0d-119">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="8ef0d-120">Kullanım örneği:</span><span class="sxs-lookup"><span data-stu-id="8ef0d-120">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![görüntü](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="8ef0d-122">*Windows PowerShell*, \* MacOS/Linux Bash veya *Windows cmd*' de aynı şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-122">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="8ef0d-123">Ancak, tablo otomatik tamamlama (parametre önerileri) *WINDOWS cmd*'de çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-123">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="8ef0d-124">Oluşturulan çıkış varlıkları</span><span class="sxs-lookup"><span data-stu-id="8ef0d-124">Output assets generated</span></span>

<span data-ttu-id="8ef0d-125">CLı `auto-train` komutu, çıkış klasöründe aşağıdaki varlıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8ef0d-125">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="8ef0d-126">Bir seri hale getirilmiş model. zip ("en iyi model"), tahminleri çalıştırmak için kullanıma uygun.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-126">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="8ef0d-127">C#Çözüm:</span><span class="sxs-lookup"><span data-stu-id="8ef0d-127">C# solution with:</span></span>
  - <span data-ttu-id="8ef0d-128">C#oluşturulan model (bu modelle Son Kullanıcı uygulamalarınızda tahmine dayalı hale getirmek için) çalıştırılacak/puan veren kod.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-128">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="8ef0d-129">C#Bu modeli oluşturmak için kullanılan eğitim koduna sahip kod (öğrenme amaçları veya model yeniden eğitimi için).</span><span class="sxs-lookup"><span data-stu-id="8ef0d-129">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="8ef0d-130">Ayrıntılı yapılandırma/işlem hattı da dahil olmak üzere, değerlendirilen birden çok algoritmayana tüm yinelemeler/sweeps bilgileri içeren günlük dosyası.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-130">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="8ef0d-131">İlk iki varlık, bu oluşturulmuş ML modeliyle tahminler yapmak için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-131">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="8ef0d-132">Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. böylece, modelinize yeniden eğitebilir ve tüm özel bir oran/algoritma ve hiper parametrelerin, kapsamaların altındaki CLı ve oto ml tarafından seçili olduğunu araştırın ve yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-132">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="8ef0d-133">Modelin kalitesini anlama</span><span class="sxs-lookup"><span data-stu-id="8ef0d-133">Understanding the quality of the model</span></span>

<span data-ttu-id="8ef0d-134">CLı aracıyla ' en iyi model ' oluşturduğunuzda, hedeflediğiniz ML görevi için uygun olan kalite ölçümlerini (doğruluk ve R-kare gibi) görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-134">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="8ef0d-135">Burada, otomatik olarak oluşturulan ' en iyi modellerinizin kalitesini anlayabilmeniz için bu ölçümler ML görevine göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-135">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="8ef0d-136">Ikili sınıflandırma modelleriyle ilgili ölçümler</span><span class="sxs-lookup"><span data-stu-id="8ef0d-136">Metrics for Binary Classification models</span></span>

<span data-ttu-id="8ef0d-137">Aşağıda, CLı tarafından bulunan en iyi beş modelin ikili sınıflandırma ML görev ölçümleri listesi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="8ef0d-137">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![görüntü](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="8ef0d-139">Doğruluk, sınıflandırma sorunları için popüler bir ölçümdür, ancak doğruluk, aşağıdaki başvurularda açıklanacak şekilde en iyi modeli seçmek için her zaman en iyi ölçüm değildir.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-139">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="8ef0d-140">Ek ölçümler ile modelinizin kalitesini değerlendirmeniz gereken durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-140">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="8ef0d-141">CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [ikili sınıflandırma Için değerlendirme ölçümleri](resources/metrics.md#evaluation-metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="8ef0d-141">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for binary classification](resources/metrics.md#evaluation-metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="8ef0d-142">Çok sınıflı sınıflandırma modelleriyle ilgili ölçümler</span><span class="sxs-lookup"><span data-stu-id="8ef0d-142">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="8ef0d-143">Aşağıda, CLı tarafından bulunan en iyi beş model için çok sınıf sınıflandırma ML görev ölçümleri listesi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="8ef0d-143">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![görüntü](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="8ef0d-145">CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [birden çok Lass sınıflandırması Için değerlendirme ölçümleri](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="8ef0d-145">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for multiclass classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="8ef0d-146">Gerileme ve öneri modelleriyle ilgili ölçümler</span><span class="sxs-lookup"><span data-stu-id="8ef0d-146">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="8ef0d-147">Gözlemlenen değerler ve modelin öngörülen değerleri arasındaki farklılıklar küçük ve taraflı değilse, regresyon modeli verileri iyi bir şekilde sığdırır.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-147">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="8ef0d-148">Gerileme, belirli ölçümler ile değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-148">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="8ef0d-149">CLı tarafından bulunan en iyi önde gelen beş kalite modeli için aynı ölçüm listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-149">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="8ef0d-150">Regresyon ML göreviyle ilgili bu durumda:</span><span class="sxs-lookup"><span data-stu-id="8ef0d-150">In this particular case related to a regression ML task:</span></span>

![görüntü](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="8ef0d-152">CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [gerileme Için değerlendirme ölçümleri](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="8ef0d-152">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ef0d-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ef0d-153">See also</span></span>

- [<span data-ttu-id="8ef0d-154">ML.NET CLı aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="8ef0d-154">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="8ef0d-155">Öğretici: ML.NET CLı kullanarak yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="8ef0d-155">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="8ef0d-156">ML.NET CLı komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="8ef0d-156">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="8ef0d-157">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="8ef0d-157">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
