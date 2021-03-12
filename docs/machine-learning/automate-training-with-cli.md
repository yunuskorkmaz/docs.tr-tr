---
title: ML.NET CLı ile model eğitimi otomatikleştirin
description: Komut satırından en iyi modeli otomatik olarak eğiteiçin ML.NET CLı aracının nasıl kullanılacağını öğrenin.
ms.date: 06/03/2020
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 95e85cdc7b1ca42f086bafaf99d3f3fa29db7aa5
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605275"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="2e552-103">ML.NET CLı ile model eğitimi otomatikleştirin</span><span class="sxs-lookup"><span data-stu-id="2e552-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="2e552-104">ML.NET CLı, .NET geliştiricileri için model oluşturmayı otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="2e552-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="2e552-105">ML.NET API 'sini kendisiyle kullanmak için (ML.NET Düzml CLı olmadan), bir daha (belirli bir görev için makine öğrenimi algoritması uygulaması) ve verilerinize uygulanacak veri dönüştürmeleri (özellik Mühendisliği) kümesini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e552-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="2e552-106">En iyi işlem hattı her bir veri kümesi için farklılık gösterir ve tüm seçeneklerden en uygun algoritmayı belirlemek karmaşıklığa ekler.</span><span class="sxs-lookup"><span data-stu-id="2e552-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="2e552-107">Ayrıca, her algoritmanın ayarlanabilir bir hiper parametre kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="2e552-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="2e552-108">Bu nedenle, özellik mühendisliğinin, öğrenme algoritmalarının ve hiper parametrelerin en iyi birleşimlerini bulmaya çalışarak, hafta ve bazen aylık olarak makine öğrenimi modeli iyileştirmesi harcamanıza izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e552-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="2e552-109">ML.NET CLı, otomatik makine öğrenimi (Otomatikml) kullanarak bu işlemi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="2e552-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="2e552-110">Bu konu, şu anda önizleme aşamasında olan ML.NET **CLI** ve ml.net **oto ml**'ye başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="2e552-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="2e552-111">ML.NET komut satırı arabirimi (CLı) nedir?</span><span class="sxs-lookup"><span data-stu-id="2e552-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="2e552-112">ML.NET CLı, bir [.NET Core aracıdır](../core/tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="2e552-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="2e552-113">Yüklendikten sonra, bir makine öğrenimi görevi ve eğitim veri kümesi verirsiniz ve bir ML.NET modeli, ayrıca uygulamanızdaki modeli kullanmak için çalıştırılacak C# kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2e552-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="2e552-114">Aşağıdaki şekilde gösterildiği gibi, bu modeli çalıştırmak/skor için yüksek kaliteli bir ML.NET modeli (serileştirilmiş model. zip dosyası) ve örnek C# kodu oluşturmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2e552-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="2e552-115">Ayrıca, bu modeli oluşturmak/eğitebilmek için C# kodu da oluşturulur. böylece, bu oluşturulan "en iyi model" için kullanılan algoritmayı ve ayarları araştırıp yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e552-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

![ML.NET CLı içinde çalışan oto ml altyapısı](media/automate-training-with-cli/cli-high-level-process.png)

<span data-ttu-id="2e552-117">Kendi veri kümelerinizde, sizin tarafınızdan kodlamadan bu varlıkları oluşturabilirsiniz. bu sayede, ML.NET zaten tanıyor olsanız bile üretkenliğinizi de artırır.</span><span class="sxs-lookup"><span data-stu-id="2e552-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="2e552-118">Şu anda, ML.NET CLı tarafından desteklenen ML görevleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2e552-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- <span data-ttu-id="2e552-119">Sınıflandırma (ikili ve çok sınıf)</span><span class="sxs-lookup"><span data-stu-id="2e552-119">classification (binary and multi-class)</span></span>
- <span data-ttu-id="2e552-120">regresyon</span><span class="sxs-lookup"><span data-stu-id="2e552-120">regression</span></span>
- <span data-ttu-id="2e552-121">Önerilen</span><span class="sxs-lookup"><span data-stu-id="2e552-121">recommendation</span></span>
- <span data-ttu-id="2e552-122">Gelecekte: görüntü sınıflandırması, derecelendirme, anomali algılama, kümeleme gibi diğer makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="2e552-122">Future: other machine learning tasks such as image-classification, ranking, anomaly-detection, clustering</span></span>

<span data-ttu-id="2e552-123">Kullanım örneği (sınıflandırma senaryosu):</span><span class="sxs-lookup"><span data-stu-id="2e552-123">Example of usage (classification scenario):</span></span>

```console
mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
```

![Komut satırından ML.NET sınıflandırması](media/automate-training-with-cli/mlnet-classification-powershell.gif)

<span data-ttu-id="2e552-125">*Windows PowerShell*, *MacOS/Linux Bash* veya *Windows cmd*' de aynı şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e552-125">You can run it the same way on *Windows PowerShell*, *macOS/Linux bash*, or *Windows CMD*.</span></span> <span data-ttu-id="2e552-126">Ancak, tablo otomatik tamamlama (parametre önerileri) *WINDOWS cmd*'de çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="2e552-126">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="2e552-127">Oluşturulan çıkış varlıkları</span><span class="sxs-lookup"><span data-stu-id="2e552-127">Output assets generated</span></span>

<span data-ttu-id="2e552-128">CLı 'deki ML görev komutları, çıkış klasöründe aşağıdaki varlıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2e552-128">The ML task commands in the CLI generate the following assets in the output folder:</span></span>

- <span data-ttu-id="2e552-129">Bir seri hale getirilmiş model. zip ("en iyi model"), tahminleri çalıştırmak için kullanıma uygun.</span><span class="sxs-lookup"><span data-stu-id="2e552-129">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="2e552-130">İle C# çözümü:</span><span class="sxs-lookup"><span data-stu-id="2e552-130">C# solution with:</span></span>
  - <span data-ttu-id="2e552-131">Oluşturulan modeli çalıştırmak/öğrenmek için C# kodu (bu modelle Son Kullanıcı uygulamalarınızda tahminleri yapmak için).</span><span class="sxs-lookup"><span data-stu-id="2e552-131">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="2e552-132">Bu modeli oluşturmak için kullanılan eğitim koduna sahip C# kodu (öğrenme amaçları veya model yeniden eğitimi için).</span><span class="sxs-lookup"><span data-stu-id="2e552-132">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="2e552-133">Ayrıntılı yapılandırma/işlem hattı da dahil olmak üzere, değerlendirilen birden çok algoritmayana tüm yinelemeler/sweeps bilgileri içeren günlük dosyası.</span><span class="sxs-lookup"><span data-stu-id="2e552-133">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="2e552-134">İlk iki varlık, bu oluşturulmuş ML modeliyle tahminler yapmak için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e552-134">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="2e552-135">Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. böylece, modelinize yeniden eğitebilir ve tüm özel bir oran/algoritma ve hiper parametrelerin, kapsamaların altındaki CLı ve oto ml tarafından seçili olduğunu araştırın ve yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e552-135">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="2e552-136">Modelin kalitesini anlama</span><span class="sxs-lookup"><span data-stu-id="2e552-136">Understanding the quality of the model</span></span>

<span data-ttu-id="2e552-137">CLı aracıyla ' en iyi model ' oluşturduğunuzda, hedeflediğiniz ML görevi için uygun olan kalite ölçümlerini (doğruluk ve R-kare gibi) görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="2e552-137">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="2e552-138">Burada, otomatik olarak oluşturulan ' en iyi modellerinizin kalitesini anlayabilmeniz için bu ölçümler ML görevine göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="2e552-138">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-classification-models"></a><span data-ttu-id="2e552-139">Sınıflandırma modelleriyle ilgili ölçümler</span><span class="sxs-lookup"><span data-stu-id="2e552-139">Metrics for Classification models</span></span>

<span data-ttu-id="2e552-140">Aşağıdaki görüntüde, CLı tarafından bulunan ilk beş modelin sınıflandırma ölçümleri listesi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="2e552-140">The following image displays the classification metrics list for the top five models found by the CLI:</span></span>

![İlk beş model için sınıflandırma ölçümleri](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

 <span data-ttu-id="2e552-142">Doğruluk, sınıflandırma sorunları için popüler bir ölçümdür, ancak doğruluk, aşağıdaki başvurularda açıklanacak şekilde en iyi modeli seçmek için her zaman en iyi ölçüm değildir.</span><span class="sxs-lookup"><span data-stu-id="2e552-142">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="2e552-143">Ek ölçümler ile modelinizin kalitesini değerlendirmeniz gereken durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="2e552-143">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="2e552-144">CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [Sınıflandırma Için değerlendirme ölçümleri](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="2e552-144">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="2e552-145">Gerileme ve öneri modelleriyle ilgili ölçümler</span><span class="sxs-lookup"><span data-stu-id="2e552-145">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="2e552-146">Gözlemlenen değerler ve modelin öngörülen değerleri arasındaki farklılıklar küçük ve taraflı değilse, regresyon modeli verileri iyi bir şekilde sığdırır.</span><span class="sxs-lookup"><span data-stu-id="2e552-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="2e552-147">Gerileme, belirli ölçümler ile değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2e552-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="2e552-148">CLı tarafından bulunan ilk beş kalite modeli için benzer bir ölçüm listesi görürsünüz, bu durum dışında, ilk beş bir gerileme ML göreviyle ilgilidir:</span><span class="sxs-lookup"><span data-stu-id="2e552-148">You'll see a similar list of metrics for the top five quality models found by the CLI, except in this case, the top five are related to a regression ML task:</span></span>

![İlk beş model için regresyon ölçümleri](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="2e552-150">CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [gerileme Için değerlendirme ölçümleri](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="2e552-150">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e552-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e552-151">See also</span></span>

- [<span data-ttu-id="2e552-152">ML.NET CLı aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="2e552-152">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="2e552-153">Öğretici: ML.NET CLı kullanarak yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="2e552-153">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="2e552-154">ML.NET CLı komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="2e552-154">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="2e552-155">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="2e552-155">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
