---
title: ML.NET CLı ile model eğitimi otomatikleştirin
description: Komut satırından en iyi modeli otomatik olarak eğiteiçin ML.NET CLı aracının nasıl kullanılacağını öğrenin.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: c147464ff59563d336363eed73fc6337bdb12e85
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275853"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="c037f-103">ML.NET CLı ile model eğitimi otomatikleştirin</span><span class="sxs-lookup"><span data-stu-id="c037f-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="c037f-104">ML.NET öğrenirken .NET geliştiricileri için ML.NET CLı "verilerinizi keşfetmenizi sunan" ML.NET.</span><span class="sxs-lookup"><span data-stu-id="c037f-104">The ML.NET CLI "democratizes" ML.NET for .NET developers when learning ML.NET.</span></span>

<span data-ttu-id="c037f-105">ML.NET API 'sini kendisiyle kullanmak için (ML.NET Düzml CLı olmadan), bir daha (belirli bir görev için makine öğrenimi algoritması uygulaması) ve verilerinize uygulanacak veri dönüştürmeleri (özellik Mühendisliği) kümesini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c037f-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="c037f-106">En iyi işlem hattı her bir veri kümesi için farklılık gösterir ve tüm seçeneklerden en uygun algoritmayı belirlemek karmaşıklığa ekler.</span><span class="sxs-lookup"><span data-stu-id="c037f-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="c037f-107">Ayrıca, her algoritmanın ayarlanabilir bir hiper parametre kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="c037f-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="c037f-108">Bu nedenle, özellik mühendisliğinin, öğrenme algoritmalarının ve hiper parametrelerin en iyi birleşimlerini bulmaya çalışarak, hafta ve bazen aylık olarak makine öğrenimi modeli iyileştirmesi harcamanıza izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c037f-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="c037f-109">Bu işlem, ML.NET Otomatikml akıllı altyapısını uygulayan ML.NET CLı ile otomatikleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c037f-109">This process can be automated with the ML.NET CLI, which implements the ML.NET AutoML intelligent engine.</span></span>

> [!NOTE]
> <span data-ttu-id="c037f-110">Bu konu, şu anda önizleme aşamasında olan ML.NET **CLI** ve ml.net **oto ml**'ye başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c037f-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="c037f-111">ML.NET komut satırı arabirimi (CLı) nedir?</span><span class="sxs-lookup"><span data-stu-id="c037f-111">What is the ML.NET Command-line Interface (CLI)?</span></span>

<span data-ttu-id="c037f-112">Eğitim veri kümenize göre iyi kalitede ML.NET modelleri ve kaynak kodu oluşturmak için ML.NET CLı 'yi herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c037f-112">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on your training dataset.</span></span>

<span data-ttu-id="c037f-113">Aşağıdaki şekilde gösterildiği gibi, yüksek kaliteli bir ML.NET modeli (serileştirilmiş model. zip dosyası) ve bu modeli çalıştırmak/skor için örnek C# kodu oluşturmak basittir.</span><span class="sxs-lookup"><span data-stu-id="c037f-113">As shown in the figure below, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="c037f-114">Ayrıca, bu model C# oluşturma/eğitme kodu da oluşturulur. böylece, bu oluşturulan "en iyi model" için kullanılan algoritmayı ve ayarları araştırıp yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c037f-114">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="c037f-115">![](media/automate-training-with-cli/cli-high-level-process.png "ml.net CLI içinde çalışan görüntü oto ml altyapısı")</span><span class="sxs-lookup"><span data-stu-id="c037f-115">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="c037f-116">Kendi veri kümelerinizde, sizin tarafınızdan kodlamadan bu varlıkları oluşturabilirsiniz. bu sayede, ML.NET zaten tanıyor olsanız bile üretkenliğinizi de artırır.</span><span class="sxs-lookup"><span data-stu-id="c037f-116">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="c037f-117">Şu anda, ML.NET CLı tarafından desteklenen ML görevleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c037f-117">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="c037f-118">Gelecekte: `recommendation`, `ranking`, `anomaly-detection`, `clustering` gibi diğer makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="c037f-118">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="c037f-119">Kullanım örneği:</span><span class="sxs-lookup"><span data-stu-id="c037f-119">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="c037f-121">*Windows PowerShell*, \* MacOS/Linux Bash veya *Windows cmd*' de aynı şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c037f-121">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="c037f-122">Ancak, tablo otomatik tamamlama (parametre önerileri) *WINDOWS cmd*'de çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="c037f-122">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="c037f-123">Oluşturulan çıkış varlıkları</span><span class="sxs-lookup"><span data-stu-id="c037f-123">Output assets generated</span></span>

<span data-ttu-id="c037f-124">CLı `auto-train` komutu çıkış klasöründe aşağıdaki varlıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c037f-124">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="c037f-125">Bir seri hale getirilmiş model. zip ("en iyi model"), tahminleri çalıştırmak için kullanıma uygun.</span><span class="sxs-lookup"><span data-stu-id="c037f-125">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="c037f-126">C#Çözüm:</span><span class="sxs-lookup"><span data-stu-id="c037f-126">C# solution with:</span></span>
  - <span data-ttu-id="c037f-127">C#oluşturulan model (bu modelle Son Kullanıcı uygulamalarınızda tahmine dayalı hale getirmek için) çalıştırılacak/puan veren kod.</span><span class="sxs-lookup"><span data-stu-id="c037f-127">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="c037f-128">C#Bu modeli oluşturmak için kullanılan eğitim koduna sahip kod (öğrenme amaçları veya model yeniden eğitimi için).</span><span class="sxs-lookup"><span data-stu-id="c037f-128">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="c037f-129">Ayrıntılı yapılandırma/işlem hattı da dahil olmak üzere, değerlendirilen birden çok algoritmayana tüm yinelemeler/sweeps bilgileri içeren günlük dosyası.</span><span class="sxs-lookup"><span data-stu-id="c037f-129">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="c037f-130">İlk iki varlık, bu oluşturulmuş ML modeliyle tahminler yapmak için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c037f-130">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="c037f-131">Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğmek için hangi ML.NET API kodunun kullanıldığını gösterir. böylece modelinize yeniden eğitebilir ve CLı ve oto ml tarafından hangi özel eğitimin/algoritma ve hiper parametrelerin seçili olduğunu araştırabilir ve yineleyebilirsiniz içerir.</span><span class="sxs-lookup"><span data-stu-id="c037f-131">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="c037f-132">Modelin kalitesini anlama</span><span class="sxs-lookup"><span data-stu-id="c037f-132">Understanding the quality of the model</span></span>

<span data-ttu-id="c037f-133">CLı aracıyla ' en iyi model ' oluşturduğunuzda, hedeflediğiniz ML görevi için uygun olan kalite ölçümlerini (doğruluk ve R-kare) görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c037f-133">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy, and R-Squared) as appropriate for the ML task you are targeting.</span></span>

<span data-ttu-id="c037f-134">Burada, otomatik olarak oluşturulan ' en iyi modellerinizin kalitesini anlayabilmeniz için ML görevine göre gruplanmış olan ölçümler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c037f-134">Here we summarize those metrics grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="c037f-135">Ikili sınıflandırma modelleriyle ilgili ölçümler</span><span class="sxs-lookup"><span data-stu-id="c037f-135">Metrics for Binary Classification models</span></span>

<span data-ttu-id="c037f-136">Aşağıda, CLı tarafından bulunan en iyi beş modelin ikili sınıflandırma ML görev ölçümleri listesi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="c037f-136">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="c037f-138">Doğruluk, sınıflandırma sorunları için popüler bir ölçümdür, ancak aşağıdaki başvurularda açıklanacak şekilde en iyi modeli seçmek için doğruluk her zaman en iyi ölçüm değildir.</span><span class="sxs-lookup"><span data-stu-id="c037f-138">Accuracy is a popular metric for classification problems, however accuracy is not always the best metric to select the best model from as explained in the references below.</span></span> <span data-ttu-id="c037f-139">Ek ölçümler ile modelinizin kalitesini değerlendirmeniz gereken durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="c037f-139">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="c037f-140">CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [ikili sınıflandırma ölçümleri](resources/metrics.md#metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="c037f-140">To explore and understand the metrics that are output by the CLI, see [Metrics for binary classification](resources/metrics.md#metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="c037f-141">Çok sınıflı sınıflandırma modelleriyle ilgili ölçümler</span><span class="sxs-lookup"><span data-stu-id="c037f-141">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="c037f-142">Aşağıda, CLı tarafından bulunan en iyi beş model için çok sınıf sınıflandırma ML görev ölçümleri listesi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="c037f-142">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="c037f-144">CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [birden çok Lass sınıflandırması Için ölçümler](resources/metrics.md#metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="c037f-144">To explore and understand the metrics that are output by the CLI, see [Metrics for multiclass classification](resources/metrics.md#metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-models"></a><span data-ttu-id="c037f-145">Regresyon modelleriyle ilgili ölçümler</span><span class="sxs-lookup"><span data-stu-id="c037f-145">Metrics for Regression models</span></span>

<span data-ttu-id="c037f-146">Gözlemlenen değerler ve modelin öngörülen değerleri arasındaki farklılıklar küçük ve taraflı değilse, regresyon modeli verileri iyi bir şekilde sığdırır.</span><span class="sxs-lookup"><span data-stu-id="c037f-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="c037f-147">Gerileme, belirli ölçümler ile değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c037f-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="c037f-148">CLı tarafından bulunan en iyi önde gelen beş kalite modelinin ölçüm bir listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c037f-148">You will see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="c037f-149">Regresyon ML göreviyle ilgili bu durumda:</span><span class="sxs-lookup"><span data-stu-id="c037f-149">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="c037f-151">CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [gerileme ölçümleri](resources/metrics.md#metrics-for-regression).</span><span class="sxs-lookup"><span data-stu-id="c037f-151">To explore and understand the metrics that are output by the CLI, see [Metrics for regression](resources/metrics.md#metrics-for-regression).</span></span>

## <a name="see-also"></a><span data-ttu-id="c037f-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c037f-152">See also</span></span>

- [<span data-ttu-id="c037f-153">ML.NET CLı aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="c037f-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="c037f-154">Öğretici: ML.NET CLı kullanarak ikili bir sınıflandırıcı otomatik oluşturma</span><span class="sxs-lookup"><span data-stu-id="c037f-154">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](tutorials/mlnet-cli.md)
- [<span data-ttu-id="c037f-155">ML.NET CLı komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="c037f-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="c037f-156">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="c037f-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
