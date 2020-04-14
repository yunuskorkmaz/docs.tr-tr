---
title: ML.NET CLI kullanarak yaklaşımı çözümleme
description: Örnek bir veri kümesinden otomatik olarak ml modeli ve ilgili C# kodu oluşturun
author: cesardl
ms.author: cesardl
ms.date: 12/23/2019
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 832124e6d027b240c4d06692ee87c84f57b982d3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243342"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="66352-103">ML.NET CLI kullanarak yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="66352-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="66352-104">otomatik olarak bir ML.NET modeli ve altta yatan C# kodu oluşturmak için cli ML.NET nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="66352-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="66352-105">Veri kümenizi ve uygulamak istediğiniz makine öğrenimi görevini sağlarsınız ve CLI, model oluşturma ve dağıtım kaynak kodunun yanı sıra ikili modeli oluşturmak için AutoML altyapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="66352-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="66352-106">Bu öğreticide, aşağıdaki adımları yapacaksınız:</span><span class="sxs-lookup"><span data-stu-id="66352-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="66352-107">Verilerinizi seçili makine öğrenimi görevi için hazırlayın</span><span class="sxs-lookup"><span data-stu-id="66352-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="66352-108">CLI'dan 'mlnet otomatik tren' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="66352-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> - <span data-ttu-id="66352-109">Kalite metrik sonuçlarını gözden geçirin</span><span class="sxs-lookup"><span data-stu-id="66352-109">Review the quality metric results</span></span>
> - <span data-ttu-id="66352-110">Uygulamanızdaki modeli kullanmak için oluşturulan C# kodunu anlama</span><span class="sxs-lookup"><span data-stu-id="66352-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="66352-111">Modeli eğitmek için kullanılan oluşturulan C# kodunu keşfedin</span><span class="sxs-lookup"><span data-stu-id="66352-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="66352-112">Bu konu, şu anda Önizleme'de bulunan ML.NET CLI aracını ifade eder ve malzeme değişebilir.</span><span class="sxs-lookup"><span data-stu-id="66352-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="66352-113">Daha fazla bilgi için ML.NET sayfasını ziyaret [edin.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="66352-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="66352-114">cli ML.NET ML.NET bir parçasıdır ve ana hedefi başlamak için sıfırdan kodlamak gerekmez, böylece ML.NET öğrenirken .NET geliştiriciler için ML.NET "demokratikleştirmek" tir.</span><span class="sxs-lookup"><span data-stu-id="66352-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="66352-115">Sağladığınız eğitim veri kümelerini temel alan kaliteli ML.NET modelleri ve kaynak kodu oluşturmak için cli ML.NET herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="66352-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="66352-116">Pre-requisites</span></span>

- <span data-ttu-id="66352-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya sonrası</span><span class="sxs-lookup"><span data-stu-id="66352-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="66352-118">(İsteğe bağlı) [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="66352-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="66352-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="66352-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="66352-120">Oluşturulan C# kodu projelerini Visual Studio'dan `dotnet run` veya (.NET Core CLI) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="66352-121">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="66352-121">Prepare your data</span></span>

<span data-ttu-id="66352-122">İkili sınıflandırma makinesi öğrenme görevi olan 'Sentiment Analysis' senaryosu için kullanılan varolan bir veri kümesini kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="66352-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="66352-123">Kendi veri kümenizi benzer bir şekilde kullanabilirsiniz ve model ve kod sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66352-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="66352-124">UCI Sentiment Etiketli Cümleler dataset zip dosyasını indirin [(aşağıdaki nottaki alıntılara bakın)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve seçtiğiniz herhangi bir klasörde zip'i açın.</span><span class="sxs-lookup"><span data-stu-id="66352-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="66352-125">Bu öğreticideki veri kümeleri, Kotzias ve ark.'nın 'Derin Özellikleri Kullanarak Gruptan Bireysel Etiketlere' bir veri kümesi ni kullanır.</span><span class="sxs-lookup"><span data-stu-id="66352-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="66352-126">KDD 2015 ve UCI Machine Learning Deposu - Dua, D. ve Karra Taniskidou, E. (2017) ev sahipliği yaptı.</span><span class="sxs-lookup"><span data-stu-id="66352-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="66352-127">UCI Makine Öğrenme Deposuhttp://archive.ics.uci.edu/ml[ ].</span><span class="sxs-lookup"><span data-stu-id="66352-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="66352-128">Irvine, CA: Kaliforniya Üniversitesi, Bilgi ve Bilgisayar Bilimleri Fakültesi.</span><span class="sxs-lookup"><span data-stu-id="66352-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="66352-129">Dosyayı `yelp_labelled.txt` daha önce oluşturduğunuz herhangi bir `/cli-test`klasöre kopyalayın (örneğin).</span><span class="sxs-lookup"><span data-stu-id="66352-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="66352-130">Tercih ettiğiniz komut istemini açın ve veri kümesi dosyasını kopyaladığınız klasöre geçin.</span><span class="sxs-lookup"><span data-stu-id="66352-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="66352-131">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="66352-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="66352-132">Visual Studio Code gibi herhangi bir metin düzenleyicisini `yelp_labelled.txt` kullanarak veri kümesi dosyasını açabilir ve keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="66352-133">Yapının aşağıdaki leri görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66352-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="66352-134">Dosyanın üstbilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="66352-134">The file has no header.</span></span> <span data-ttu-id="66352-135">Sütundizini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="66352-135">You will use the column's index.</span></span>

    - <span data-ttu-id="66352-136">Sadece iki sütun vardır:</span><span class="sxs-lookup"><span data-stu-id="66352-136">There are just two columns:</span></span>

        | <span data-ttu-id="66352-137">Metin (Sütun dizini 0)</span><span class="sxs-lookup"><span data-stu-id="66352-137">Text (Column index 0)</span></span> | <span data-ttu-id="66352-138">Etiket (Sütun dizini 1)</span><span class="sxs-lookup"><span data-stu-id="66352-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="66352-139">Wow... Burayı çok severdim.</span><span class="sxs-lookup"><span data-stu-id="66352-139">Wow... Loved this place.</span></span> | <span data-ttu-id="66352-140">1</span><span class="sxs-lookup"><span data-stu-id="66352-140">1</span></span> |
        | <span data-ttu-id="66352-141">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="66352-141">Crust is not good.</span></span> | <span data-ttu-id="66352-142">0</span><span class="sxs-lookup"><span data-stu-id="66352-142">0</span></span> |
        | <span data-ttu-id="66352-143">Lezzetli değil ve doku sadece kötü oldu.</span><span class="sxs-lookup"><span data-stu-id="66352-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="66352-144">0</span><span class="sxs-lookup"><span data-stu-id="66352-144">0</span></span> |
        | <span data-ttu-id="66352-145">... ÇOK DAHA FAZLA TEKSTİl SATıRLARI...</span><span class="sxs-lookup"><span data-stu-id="66352-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="66352-146">... (1 veya 0)...</span><span class="sxs-lookup"><span data-stu-id="66352-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="66352-147">Düzenleyiciden gelen veri kümesi dosyasını kapattığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="66352-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="66352-148">Şimdi, bu 'Duygu Analizi' senaryosu için CLI kullanmaya başlamak için hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="66352-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="66352-149">Bu öğreticiyi bitirdikten sonra, *'İkili Sınıflandırma', 'Çok sınıflı Sınıflandırma' ve 'Regresyon'* ML.NET CLI Preview tarafından desteklenen ML görevlerinden herhangi biri için kullanılmaya hazır oldukları sürece kendi veri kümelerinizi de deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="66352-150">'mlnet otomatik tren' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="66352-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="66352-151">Aşağıdaki ML.NET CLI komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="66352-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="66352-152">Bu komut \*\* `mlnet auto-train` komutu\*\*çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="66352-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="66352-153">türünde bir **ML görevi** için**`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="66352-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="66352-154">veri \*\*kümesi dosyasını `yelp_labelled.txt` \*\* eğitim ve test veri seti olarak kullanır (dahili olarak CLI çapraz doğrulama kullanır veya biri eğitim, diğeri test etmek için olmak üzere iki veri kümesine böler)</span><span class="sxs-lookup"><span data-stu-id="66352-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="66352-155">tahmin etmek istediğiniz **hedef/hedef sütunun** (genellikle **'etiket'** olarak adlandırılır) **dizin 1'li sütun** olduğu yerde (dizin sıfır tabanlı olduğundan, ikinci sütundur)</span><span class="sxs-lookup"><span data-stu-id="66352-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="66352-156">bu özel veri kümesi dosyasıüstbilgisi olmadığından sütun adları içeren bir **dosya üstbilgisi kullanmaz**</span><span class="sxs-lookup"><span data-stu-id="66352-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="66352-157">deney için **hedeflenen keşif süresi** **10 saniyedir**</span><span class="sxs-lookup"><span data-stu-id="66352-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="66352-158">CLI'den aşağıdakilere benzer çıktılar görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="66352-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windows"></a>[<span data-ttu-id="66352-159">Windows</span><span class="sxs-lookup"><span data-stu-id="66352-159">Windows</span></span>](#tab/windows)

    ![PowerShell üzerinde ML.NET CLI otomatik tren](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bash"></a>[<span data-ttu-id="66352-161">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="66352-161">macOS Bash</span></span>](#tab/macosbash)

    ![PowerShell üzerinde ML.NET CLI otomatik tren](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="66352-163">Bu özel durumda, sadece 10 saniye içinde ve sağlanan küçük veri kümesi ile, CLI aracı farklı iç veri dönüşümleri ve algoritma hiper-parametreleri ile algoritma / yapılandırma farklı kombinasyonları dayalı birden çok kez eğitim anlamına gelen oldukça birkaç yineleme çalıştırmak başardı.</span><span class="sxs-lookup"><span data-stu-id="66352-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="66352-164">Son olarak, 10 saniye içinde bulunan "en kaliteli" model belirli bir yapılandırma ile belirli bir eğitmen / algoritma kullanarak bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="66352-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="66352-165">Arama süresine bağlı olarak, komut farklı bir sonuç üretebilir.</span><span class="sxs-lookup"><span data-stu-id="66352-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="66352-166">Seçim, `Accuracy`'.</span><span class="sxs-lookup"><span data-stu-id="66352-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="66352-167">**Modelin kalite ölçümlerini anlama**</span><span class="sxs-lookup"><span data-stu-id="66352-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="66352-168">İkili sınıflandırma modelini değerlendirmek için ilk ve en kolay metrik, anlaşılması kolay olan doğruluktır.</span><span class="sxs-lookup"><span data-stu-id="66352-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="66352-169">"Doğruluk, bir test veri kümesi ile doğru tahminlerin oranıdır.".</span><span class="sxs-lookup"><span data-stu-id="66352-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="66352-170">%100'e (1.00) ne kadar yakınsa o kadar iyi.</span><span class="sxs-lookup"><span data-stu-id="66352-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="66352-171">Ancak, özellikle test veri kümesinde etiket (bu durumda 0 ve 1) dengesizse, Doğruluk ölçümü ile ölçmenin yeterli olmadığı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="66352-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="66352-172">Doğruluk, AUC, AUCPR ve Farklı modelleri değerlendirmek için kullanılan F1 puanı gibi ölçümler hakkında ek ölçümler ve daha **ayrıntılı bilgi** için [ML.NET](../resources/metrics.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="66352-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="66352-173">Bu çok aynı veri kümesini deneyebilir `--max-exploration-time` ve bu veri kümesi için farklı bir eğitim boru hattı yapılandırması (oldukça küçük, 1000 satır) ile sizin için daha iyi bir "en iyi model" bulacaksınız (örneğin üç dakika, 180 saniye belirtin) için birkaç dakika belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="66352-174">Daha büyük veri kümelerini hedefleyen bir "üretime hazır model" olan "en iyi/kaliteli" modeli bulmak için, genellikle veri kümesinin boyutuna bağlı olarak çok daha fazla keşif süresi belirten CLI ile denemeler yapmalısınız.</span><span class="sxs-lookup"><span data-stu-id="66352-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="66352-175">Aslında, çoğu durumda, özellikle veri kümesi satırve sütunlarda büyükse, birden çok saat arama süresi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="66352-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="66352-176">Önceki komut yürütme aşağıdaki varlıkları oluşturdu:</span><span class="sxs-lookup"><span data-stu-id="66352-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="66352-177">Serileştirilmiş bir model .zip ("en iyi model") kullanıma hazır.</span><span class="sxs-lookup"><span data-stu-id="66352-177">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="66352-178">C# kodu, oluşturulan modeli çalıştırmak/puanlamak için (Bu modelle son kullanıcı uygulamalarınızda öngörülerde bulunmak için).</span><span class="sxs-lookup"><span data-stu-id="66352-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="66352-179">C# eğitim kodu bu modeli oluşturmak için kullanılır (Öğrenme amaçlı).</span><span class="sxs-lookup"><span data-stu-id="66352-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="66352-180">Tüm yinelemelerin yer verdiği bir günlük dosyası, hiper parametreler ve veri dönüşümleri birleşimi ile denenmiş her algoritma hakkında belirli ayrıntılı bilgilere sahip olarak araştırılmış.</span><span class="sxs-lookup"><span data-stu-id="66352-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="66352-181">İlk iki varlık (. Posta dosyası modeli ve C# kodu bu modeli çalıştırmak için) doğrudan son kullanıcı uygulamaları (ASP.NET Core web uygulaması, hizmetler, masaüstü uygulaması, vb) bu oluşturulan ML modeli ile tahminler yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66352-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="66352-182">Üçüncü varlık, eğitim kodu, oluşturulan modeli eğitmek için CLI tarafından ML.NET API kodunun ne ML.NET kullanıldığını gösterir, böylece CLI tarafından hangi özel eğitmen/algoritma ve hiper parametrelerin seçildiğini araştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="66352-183">Numaralandırılmış varlıklar öğreticinin aşağıdaki adımlarında açıklanır.</span><span class="sxs-lookup"><span data-stu-id="66352-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="66352-184">Öngörülerde bulunmak için modeli çalıştırmak için kullanılacak oluşturulan C# kodunu keşfedin</span><span class="sxs-lookup"><span data-stu-id="66352-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="66352-185">Visual Studio'da (2017 veya 2019) özgün `SampleBinaryClassification` hedef klasörünüzde (öğreticinin `/cli-test`adı geçen) adlı klasörde oluşturulan çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="66352-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="66352-186">Şuna benzer bir çözüm görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="66352-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="66352-187">Eğitimde Visual Studio'yu kullanmanızı öneririz, ancak oluşturulan C# kodunu (iki proje) herhangi bir metin `dotnet CLI` düzenleyicisi ile keşfedebilir ve oluşturulan konsol uygulamasını macOS, Linux veya Windows makinesiyle çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![CLI tarafından oluşturulan VS çözümü](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="66352-189">Serileştirilmiş ML modelini (.zip dosyası) ve veri sınıflarını (veri modelleri) içeren oluşturulan **sınıf kitaplığı,** sınıf kitaplığını doğrudan başvurarak (veya kodu istediğiniz gibi taşıyarak) son kullanıcı uygulamanızda doğrudan kullanabileceğiniz bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="66352-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="66352-190">Oluşturulan **konsol uygulaması** gözden geçirmeniz gereken yürütme kodu içerir ve daha sonra genellikle bu basit kodu (yalnızca birkaç satır) öngörüler yapmak istediğiniz son kullanıcı uygulamanıza taşıyarak 'puanlama kodunu' (tahminleri yapmak için ML modelini çalıştıran kod) yeniden kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="66352-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="66352-191">Sınıf kitaplığı projesinde **ModelInput.cs** ve **ModelOutput.cs** sınıf dosyalarını açın.</span><span class="sxs-lookup"><span data-stu-id="66352-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="66352-192">Bu sınıfların 'veri sınıfları' veya veri tutmak için kullanılan POCO sınıfları olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="66352-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="66352-193">Bu 'ortak kod' ancak veri seti onlarca hatta yüzlerce sütun varsa oluşturulan olması yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="66352-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="66352-194">Sınıf, `ModelInput` veri kümesinden gelen verileri okurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66352-194">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="66352-195">Sınıf `ModelOutput` tahmin sonucu (tahmin verileri) almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66352-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="66352-196">Program.cs dosyasını açın ve kodu keşfedin.</span><span class="sxs-lookup"><span data-stu-id="66352-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="66352-197">Sadece birkaç satırda, modeli çalıştırabilir ve örnek bir tahmin de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

    - <span data-ttu-id="66352-198">İlk kod satırı, ML.NET `MLContext` kodu çalıştırdığınızda gereken bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66352-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span>

    - <span data-ttu-id="66352-199">Zaten CLI aracı tarafından sizin için eğitilmiş ve modelin seri içine kaydedilmiş olduğundan kodun ikinci satırı modeli eğitmek gerekmez çünkü yorumlanır. ZIP dosyası.</span><span class="sxs-lookup"><span data-stu-id="66352-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="66352-200">Ancak CLI tarafından *"modelin nasıl eğitildiğini"* görmek istiyorsanız, bu satırı yorumlayabilir ve söz konusu ML modeli için kullanılan eğitim kodunu çalıştırabilirsiniz/hata ayıklamanız olabilir.</span><span class="sxs-lookup"><span data-stu-id="66352-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

    - <span data-ttu-id="66352-201">Üçüncü kod satırında, modeli serileştirilmiş modelden yüklersiniz. Bu modele `mlContext.Model.Load()` giden yolu sağlayarak API ile ZIP dosyası. ZIP dosyası.</span><span class="sxs-lookup"><span data-stu-id="66352-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

    - <span data-ttu-id="66352-202">Dördüncü kod satırında, `PredictionEngine` `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` ösy'yi API ile yükleyin.</span><span class="sxs-lookup"><span data-stu-id="66352-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="66352-203">Tek bir `PredictionEngine` veri örneğini hedefleyen bir tahminde bulunmak istediğinizde nesneye ihtiyacınız vardır (bu durumda, duyarlılığını tahmin etmek için tek bir metin parçası).</span><span class="sxs-lookup"><span data-stu-id="66352-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

    - <span data-ttu-id="66352-204">Beşinci kod satırı, işlevi `CreateSingleDataSample()`çağırarak tahmin için kullanılacak tek örnek *verileri* oluşturduğunuz satırdır.</span><span class="sxs-lookup"><span data-stu-id="66352-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="66352-205">CLI aracı ne tür örnek veri kullanılacağını bilmediğinden, bu işlev içinde veri kümesinin ilk satırını yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="66352-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="66352-206">Ancak, bu durumda, bu `CreateSingleDataSample()` işlevi uygulayan bu basit kodu güncelleştirerek işlevin geçerli uygulaması yerine kendi 'sabit kodlu' verileri de oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66352-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

        ```csharp
        private static ModelInput CreateSingleDataSample()
        {
            ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
            return sampleForPrediction;
        }
        ```

1. <span data-ttu-id="66352-207">Projeyi, veri kümesinin ilk satırından yüklenen özgün örnek verileri kullanarak veya kendi özel sabit kodlanmış örnek verilerinizi sağlayarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="66352-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="66352-208">Karşılaştırılabilir bir tahmin almalısınız:</span><span class="sxs-lookup"><span data-stu-id="66352-208">You should get a prediction comparable to:</span></span>

    # <a name="windows"></a>[<span data-ttu-id="66352-209">Windows</span><span class="sxs-lookup"><span data-stu-id="66352-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="66352-210">F5 (Play tuşu) tuşuna basarak Visual Studio'daki konsol uygulamasını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="66352-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![PowerShell üzerinde ML.NET CLI otomatik tren](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="66352-212">)</span><span class="sxs-lookup"><span data-stu-id="66352-212">)</span></span>

    # <a name="macos-bash"></a>[<span data-ttu-id="66352-213">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="66352-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="66352-214">Aşağıdaki komutları yazarak konsol uygulamasını komut isteminden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="66352-214">Run the console app from the command-prompt by typing the following commands:</span></span>

    ```dotnetcli
    cd SampleBinaryClassification
    cd SampleBinaryClassification.ConsoleApp

    dotnet run
    ```

    ![PowerShell üzerinde ML.NET CLI otomatik tren](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="66352-216">)</span><span class="sxs-lookup"><span data-stu-id="66352-216">)</span></span>

    ---

1. <span data-ttu-id="66352-217">Sabit kodlanmış örnek verileri farklı duygularla diğer cümlelerle değiştirmeyi deneyin ve modelin olumlu veya olumsuz duyguları nasıl öngördüğünü görün.</span><span class="sxs-lookup"><span data-stu-id="66352-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="66352-218">Son kullanıcı uygulamalarınızı ML model tahminleri ile aşıla</span><span class="sxs-lookup"><span data-stu-id="66352-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="66352-219">Modeli son kullanıcı uygulamanızda çalıştırmak ve öngörülerde bulunmak için benzer 'ML model puanlama kodu' kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="66352-220">Örneğin, bu kodu doğrudan **WPF** ve **WinForms** gibi herhangi bir Windows masaüstü uygulamasına taşıyabilir ve modeli konsol uygulamasında yapılandan aynı şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="66352-221">Ancak, bir ML modelini çalıştırmak için bu kod satırlarını uygulama şekliniz en iyi duruma getirilmelidir (diğer bir deyişle, modeli .zip dosyasını önbelleğe alın ve bir kez yükleyin) ve özellikle uygulamanızın aşağıdaki bölümde açıklandığı gibi web uygulaması veya dağıtılmış hizmet gibi ölçeklenebilir olması gerekiyorsa, her istekte bunları oluşturmak yerine tekton nesnelere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66352-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="66352-222">Ölçeklenebilir ASP.NET Core web uygulamalarında ve hizmetlerinde ML.NET modelleri çalıştırma (çok iş parçacığı uygulamaları)</span><span class="sxs-lookup"><span data-stu-id="66352-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="66352-223">Model nesnesinin oluşturulması`ITransformer` (modelin .zip dosyasından yüklenen) `PredictionEngine` ve nesne özellikle ölçeklenebilir web uygulamaları ve dağıtılmış hizmetler üzerinde çalışırken en iyi duruma getirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="66352-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="66352-224">İlk durumda, model nesnesi (`ITransformer`) en iyi duruma getirilmesi basittir.</span><span class="sxs-lookup"><span data-stu-id="66352-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="66352-225">`ITransformer` Nesne iş parçacığı için güvenli olduğundan, modeli bir kez yükleyebilmeniz için nesneyi singleton veya statik nesne olarak önbelleğe alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="66352-226">İkinci nesne, `PredictionEngine` nesne için, `PredictionEngine` nesne iş parçacığı güvenli olmadığından, bu nedenle bir ASP.NET Core uygulamasında singleton veya statik nesne olarak bu nesneyi anında olamaz, çünkü o kadar kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="66352-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="66352-227">Bu iş parçacığı güvenli ve ölçeklenebilirlik sorunu derinden bu [Blog Yazısı](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)tartışılır .</span><span class="sxs-lookup"><span data-stu-id="66352-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="66352-228">Ancak, işler sizin için bu blog yazısı açıklanan ne daha çok daha kolay var.</span><span class="sxs-lookup"><span data-stu-id="66352-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="66352-229">Sizin için daha basit bir yaklaşım üzerinde çalıştık ve uygulama DI hizmetlerine (Bağımlılık Enjeksiyonhizmetleri) kaydederek ve ardından doğrudan kodundan kullanabilirsiniz ASP.NET Core uygulamaları ve hizmetlerinde kolayca kullanabileceğiniz güzel bir **'.NET Çekirdek Entegrasyon Paketi'** oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="66352-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="66352-230">Bunu yapmak için aşağıdaki öğretici ve örnek kontrol edin:</span><span class="sxs-lookup"><span data-stu-id="66352-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="66352-231">Öğretici: Ölçeklenebilir ASP.NET Core web uygulamaları ve WebAPI'lerde ML.NET modelleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="66352-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="66352-232">Örnek: ASP.NET Core WebAPI'de ölçeklenebilir ML.NET modeli</span><span class="sxs-lookup"><span data-stu-id="66352-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="66352-233">"En kaliteli" modeli eğitmek için kullanılan oluşturulan C# kodunu keşfedin</span><span class="sxs-lookup"><span data-stu-id="66352-233">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="66352-234">Daha gelişmiş öğrenme amaçları için, cli aracı tarafından oluşturulan modeli eğitmek için kullanılan oluşturulan C# kodunu da keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66352-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="66352-235">Bu 'eğitim modeli kodu' şu anda `ModelBuilder` bu eğitim kodunu araştırmak böylece oluşturulan özel sınıfta oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66352-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="66352-236">Daha da önemlisi, bu özel senaryo için (Sentiment Analysis modeli) oluşturulan eğitim kodunu aşağıdaki öğreticide açıklanan kodla karşılaştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66352-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="66352-237">Karşılaştır: [Öğretici: Bir duygu analizi ikili sınıflandırma senaryosunda ML.NET kullanın.](sentiment-analysis.md)</span><span class="sxs-lookup"><span data-stu-id="66352-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="66352-238">Seçilen algoritmayı ve ardışık yapı yapılandırmasını öğreticide CLI aracı tarafından oluşturulan kodla karşılaştırmak ilginçtir.</span><span class="sxs-lookup"><span data-stu-id="66352-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="66352-239">Daha iyi modelleri yineleyerek ve aramak için ne kadar zaman harcadığınıza bağlı olarak, seçilen algoritma belirli hiper parametreleri ve ardışık yapı yapılandırmasıyla birlikte farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="66352-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="66352-240">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="66352-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="66352-241">Verilerinizi seçili ML görevi (çözülmesi gereken sorun) için hazırlayın</span><span class="sxs-lookup"><span data-stu-id="66352-241">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="66352-242">CLI aracında 'mlnet otomatik tren' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="66352-242">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> - <span data-ttu-id="66352-243">Kalite metrik sonuçlarını gözden geçirin</span><span class="sxs-lookup"><span data-stu-id="66352-243">Review the quality metric results</span></span>
> - <span data-ttu-id="66352-244">Modeli çalıştırmak için oluşturulan C# kodunu anlama (Son kullanıcı uygulamanızda kullanılacak kod)</span><span class="sxs-lookup"><span data-stu-id="66352-244">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="66352-245">"En kaliteli" modeli (Öğrenme amaçlı) eğitmek için kullanılan oluşturulan C# kodunu keşfedin</span><span class="sxs-lookup"><span data-stu-id="66352-245">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="66352-246">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66352-246">See also</span></span>

- [<span data-ttu-id="66352-247">ML.NET CLI ile model eğitimini otomatikleştirin</span><span class="sxs-lookup"><span data-stu-id="66352-247">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="66352-248">Öğretici: Ölçeklenebilir ASP.NET Core web uygulamaları ve WebAPI'lerde ML.NET modelleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="66352-248">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="66352-249">Örnek: ASP.NET Core WebAPI'de ölçeklenebilir ML.NET modeli</span><span class="sxs-lookup"><span data-stu-id="66352-249">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="66352-250">ML.NET CLI otomatik tren komutu başvuru kılavuzu</span><span class="sxs-lookup"><span data-stu-id="66352-250">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="66352-251">ML.NET CLI'de telemetri</span><span class="sxs-lookup"><span data-stu-id="66352-251">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
