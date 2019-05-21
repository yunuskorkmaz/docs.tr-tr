---
title: ML.NET CLI kullanarak bir ikili dosya sınıflandırıcı otomatik oluştur
description: Otomatik olarak ML model oluşturmak ve ilgili C# bir örnek veri kodu
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 2679df0317fede9fa5f3885831c65bd87a14981a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960405"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a><span data-ttu-id="aafed-103">CLI kullanarak bir ikili dosya sınıflandırıcı otomatik oluştur</span><span class="sxs-lookup"><span data-stu-id="aafed-103">Auto generate a binary classifier using the CLI</span></span>

<span data-ttu-id="aafed-104">ML.NET CLI otomatik olarak bir ML.NET modeli oluşturmak için kullanmayı öğrenin ve arka plandaki C# kod.</span><span class="sxs-lookup"><span data-stu-id="aafed-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="aafed-105">Kümenizi ve makine öğrenimi uygulamak istediğiniz görev sağlar ve CLI ikili modelin yanı sıra model oluşturma ve dağıtım kaynak kodunu oluşturmak için AutoML altyapısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="aafed-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="aafed-106">Bu öğreticide, aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="aafed-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="aafed-107">Seçilen makine öğrenimi görev için verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="aafed-107">Prepare your data for the selected machine learning task</span></span>
> * <span data-ttu-id="aafed-108">CLI üzerinden 'mlnet otomatik train' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="aafed-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> * <span data-ttu-id="aafed-109">Kalite Ölçüm sonuçlarını gözden geçirin</span><span class="sxs-lookup"><span data-stu-id="aafed-109">Review the quality metric results</span></span>
> * <span data-ttu-id="aafed-110">Oluşturulan anlamak C# modelini kullanmak için kodu</span><span class="sxs-lookup"><span data-stu-id="aafed-110">Understand the generated C# code to use the model in your application</span></span>
> * <span data-ttu-id="aafed-111">Oluşturulan keşfedin C# modeli eğitmek için kullanılan kod</span><span class="sxs-lookup"><span data-stu-id="aafed-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="aafed-112">Bu konu şu anda Önizleme aşamasında olan ML.NET CLI aracını ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="aafed-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="aafed-113">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="aafed-113">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="aafed-114">ML.NET CLI ML.NET bir parçasıdır ve "ML.NET .NET geliştiricileri için kullanmaya başlamak için sıfırdan kodu zorunda kalmazsınız ML.NET öğrenme, herkesin için" ana hedefi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="aafed-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="aafed-115">ML.NET CLI bir komut istemi (Windows, Mac veya Linux) kaliteli ML.NET modelleri ve sağladığınız eğitim veri kümeleri üzerinde temel kaynak kodunu üretmek için çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aafed-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="aafed-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="aafed-116">Pre-requisites</span></span>

- <span data-ttu-id="aafed-117">[.NET core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya üzeri</span><span class="sxs-lookup"><span data-stu-id="aafed-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="aafed-118">(İsteğe bağlı) [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="aafed-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="aafed-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="aafed-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="aafed-120">Çalıştırabilir ya da oluşturulan C# kod projelerini Visual Studio'dan veya ile `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="aafed-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="aafed-121">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="aafed-121">Prepare your data</span></span>

<span data-ttu-id="aafed-122">İkili sınıflandırma machine learning görev 'Yaklaşım analizi' senaryosu için kullanılan mevcut bir veri kümesini kullanmak için kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="aafed-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="aafed-123">Benzer şekilde kendi kümenizi kullanabilirsiniz ve model ve kod sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aafed-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="aafed-124">İndirme [UCI yaklaşım cümleler etiketli veri kümesini zip dosyası (alıntıları aşağıdaki nota bakın)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve seçtiğiniz herhangi bir klasörde sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="aafed-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aafed-125">Veri kümeleri Bu öğreticide bir veri kümesinden 'kaynak grubuna ayrıntılı özelliklerini kullanarak her bir etiketi' Kotzias tarayıcılarınızda.</span><span class="sxs-lookup"><span data-stu-id="aafed-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="aafed-126">2015 ve barındırılan KDD UCI Machine Learning deposu - Dua, d ve Karra Taniskidou, e (2017).</span><span class="sxs-lookup"><span data-stu-id="aafed-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="aafed-127">UCI Makine deposu [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="aafed-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="aafed-128">Irvine, CA: California Üniversitesi, okul bilgi ve bilgisayar Bilimine.</span><span class="sxs-lookup"><span data-stu-id="aafed-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="aafed-129">Kopyalama `yelp_labelled.txt` dosyasını daha önce oluşturduğunuz herhangi bir klasöre (örneğin `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="aafed-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="aafed-130">Tercih edilen bir komut istemi açın ve veri kümesi dosyasını kopyaladığınız klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="aafed-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="aafed-131">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="aafed-131">For example:</span></span>

    ```console
    > cd /cli-test
    ```

    <span data-ttu-id="aafed-132">Visual Studio Code gibi herhangi bir metin düzenleyicisi kullanarak, açık keşfedin ve `yelp_labelled.txt` veri kümesi dosyası.</span><span class="sxs-lookup"><span data-stu-id="aafed-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="aafed-133">Bir yapı olduğunu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aafed-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="aafed-134">Üst bilgi dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="aafed-134">The file has no header.</span></span> <span data-ttu-id="aafed-135">Sütun dizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="aafed-135">You will use the column's index.</span></span>

    - <span data-ttu-id="aafed-136">Yalnızca iki sütun vardır:</span><span class="sxs-lookup"><span data-stu-id="aafed-136">There are just two columns:</span></span>

        | <span data-ttu-id="aafed-137">Metin (sütun dizini 0)</span><span class="sxs-lookup"><span data-stu-id="aafed-137">Text (Column index 0)</span></span> | <span data-ttu-id="aafed-138">Etiket (sütun dizini 1)</span><span class="sxs-lookup"><span data-stu-id="aafed-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="aafed-139">WOW... Burası sevdiği.</span><span class="sxs-lookup"><span data-stu-id="aafed-139">Wow... Loved this place.</span></span> | <span data-ttu-id="aafed-140">1.</span><span class="sxs-lookup"><span data-stu-id="aafed-140">1</span></span> |
        | <span data-ttu-id="aafed-141">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="aafed-141">Crust is not good.</span></span> | <span data-ttu-id="aafed-142">0</span><span class="sxs-lookup"><span data-stu-id="aafed-142">0</span></span> |
        | <span data-ttu-id="aafed-143">Değil tasty ve doku yalnızca sinir.</span><span class="sxs-lookup"><span data-stu-id="aafed-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="aafed-144">0</span><span class="sxs-lookup"><span data-stu-id="aafed-144">0</span></span> |
        | <span data-ttu-id="aafed-145">... ÇOK FAZLA METİN SATIR...</span><span class="sxs-lookup"><span data-stu-id="aafed-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="aafed-146">... (1 veya 0)...</span><span class="sxs-lookup"><span data-stu-id="aafed-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="aafed-147">Veri kümesi dosyası düzenleyicisinden kapatmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="aafed-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="aafed-148">Şimdi, bu 'Yaklaşım analizi' senaryosu için CLI'yı kullanmaya başlamak hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="aafed-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aafed-149">Görevlerden herhangi biri olan şu anda ML.NET CLI Preview tarafından desteklenen ML için kullanılmaya hazır oldukları sürece bu öğreticiyi tamamladıktan sonra kendi veri kümeleriyle deneyebilirsiniz *'İkili sınıflandırma', 'Çok sınıflı sınıflandırma' ve ' Regresyon '*).</span><span class="sxs-lookup"><span data-stu-id="aafed-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="aafed-150">'Mlnet otomatik train' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="aafed-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="aafed-151">Aşağıdaki ML.NET CLI komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="aafed-151">Run the following ML.NET CLI command:</span></span>

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="aafed-152">Bu komut çalıştırır  **`mlnet auto-train` komut**:</span><span class="sxs-lookup"><span data-stu-id="aafed-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="aafed-153">için bir **ML görev** türü **`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="aafed-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="aafed-154">kullanan **veri kümesi dosyası `yelp_labelled.txt`**  eğitim ve test (dahili olarak CLI çapraz doğrulama kullanabileceğiniz veya iki veri kümesi içinde bir eğitim ve test etmek için bir bölme) veri kümesi olarak</span><span class="sxs-lookup"><span data-stu-id="aafed-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="aafed-155">Burada **hedefi/hedef sütun** tahmin etmek istediğiniz (genellikle adlı **'etiketi'**) olan **sütun dizini 1 olan** (dizin sıfır tabanlı olduğundan diğer bir deyişle ikinci sütun )</span><span class="sxs-lookup"><span data-stu-id="aafed-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="aafed-156">mu **dosya üst bilgisi kullanmamak** bu belirli veri kümesi dosyası üst bilgi olmadığı sütun adlarına sahip</span><span class="sxs-lookup"><span data-stu-id="aafed-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="aafed-157">**araştırma zaman hedeflenen** deneme için **10 saniye**</span><span class="sxs-lookup"><span data-stu-id="aafed-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="aafed-158">CLI, benzer çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="aafed-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[<span data-ttu-id="aafed-159">Windows</span><span class="sxs-lookup"><span data-stu-id="aafed-159">Windows</span></span>](#tab/windows)

    ![ML.NET CLI otomatik-PowerShell eğitme](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="aafed-161">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="aafed-161">macOS Bash</span></span>](#tab/macosbash)

    ![ML.NET CLI otomatik-PowerShell eğitme](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="aafed-163">Bu durumda yalnızca 10 saniye içinde ve sağlanan, küçük veri kümesi ile CLI Aracı'nı farklı birleşimlerini algoritmaları/yapılandırma iç farklı verilerle birden çok kez temel eğitim anlamına gelen çok sayıda videonuz yinelemeler çalıştırabilir dönüşümler ve algoritma'nın hyper-parametreleriyle.</span><span class="sxs-lookup"><span data-stu-id="aafed-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span> 

    <span data-ttu-id="aafed-164">Son olarak, 10 saniye içinde bulunan "en iyi kalite" modeli, herhangi belirli bir yapılandırma ile belirli bir eğitmen/algoritmasını kullanarak bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="aafed-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="aafed-165">Araştırma süreye bağlı olarak, farklı bir sonuç komutu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="aafed-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="aafed-166">Seçimi gösterilen, gibi birden çok ölçümlere göre `Accuracy`.</span><span class="sxs-lookup"><span data-stu-id="aafed-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="aafed-167">**Modelin kalite ölçüleri anlama**</span><span class="sxs-lookup"><span data-stu-id="aafed-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="aafed-168">İkili sınıflandırma modeli değerlendirmek için ilk ve en kolay anlaşılması kolaydır doğruluğu unsurdur.</span><span class="sxs-lookup"><span data-stu-id="aafed-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="aafed-169">"Doğruluk oranı sınama veri kümesi ile doğru tahminler sağlıyor.".</span><span class="sxs-lookup"><span data-stu-id="aafed-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="aafed-170">% 100 (1.00) daha iyi yakın.</span><span class="sxs-lookup"><span data-stu-id="aafed-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="aafed-171">Ancak, etiket (0 ve bu durumda 1) test kümesinde özellikle dengesiz, burada yalnızca doğruluğu Metrik ölçme yeterli değildir durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="aafed-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="aafed-172">Ek Ölçümler ve daha fazlası için **ölçümleri hakkında ayrıntılı bilgi** doğruluğu, AUC, AUCPR F1 puanı farklı modelleri değerlendirmek için kullanılan, okuyabilirsiniz [anlama ML.NET ölçümleri](../resources/metrics.md)</span><span class="sxs-lookup"><span data-stu-id="aafed-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, F1-score used to evaluate the different models, you can read [Understanding ML.NET metrics](../resources/metrics.md)</span></span>

    > [!NOTE]
    >  <span data-ttu-id="aafed-173">Bu çok aynı veri kümesini deneyin ve birkaç dakikalığına belirtin `--max-exploration-time` (örneği için üç 180 saniye belirttiğiniz şekilde dakika gibi), bir daha iyi "en iyi modeli" sizin için (Bu harika bu veri kümesi için farklı eğitim işlem hattı yapılandırmasıyla bulacaksınız küçük, 1000 satırı).</span><span class="sxs-lookup"><span data-stu-id="aafed-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span> 
        
    <span data-ttu-id="aafed-174">"Büyük veri kümeleri hedefleyen bir üretime hazır modeli" bir "en iyi/iyi kalite" modeli bulmak için genellikle dataset boyutuna bağlı olarak çok daha fazla araştırma süresini belirterek CLI ile denemeler yapmalısınız.</span><span class="sxs-lookup"><span data-stu-id="aafed-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="aafed-175">Aslında, çoğu durumda özellikle veri kümesine satırlar ve sütunlar üzerinde büyük olursa birden çok keşif süresi saatlik gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="aafed-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span> 

1. <span data-ttu-id="aafed-176">Önceki komut yürütme şu varlıkları oluşturdu:</span><span class="sxs-lookup"><span data-stu-id="aafed-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="aafed-177">Serileştirilmiş modeli .zip ("en iyi modeli") kullanıma hazır.</span><span class="sxs-lookup"><span data-stu-id="aafed-177">A serialized model .zip ("best model") ready to use.</span></span> 
    - <span data-ttu-id="aafed-178">C#kod, Çalıştır/puan modeli (Bu modeli ile son kullanıcı uygulamalarınızda Öngörüler oluşturmak için) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aafed-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="aafed-179">C#Bu model (öğrenme amacıyla) oluşturmak için kullanılan kod eğitimi.</span><span class="sxs-lookup"><span data-stu-id="aafed-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="aafed-180">Tüm yinelemeler sahip bir günlük dosyası, hyper-parametreleriyle ve veri dönüşümleri, birlikte çalıştığınız her bir algoritmanın hakkında ayrıntılı bilgilere sahip incelediniz.</span><span class="sxs-lookup"><span data-stu-id="aafed-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span> 

    <span data-ttu-id="aafed-181">İlk iki varlıkları (. ZIP dosyası modeli ve C# modelin çalıştırmak için kod) doğrudan ML model oluşturulan son kullanıcı uygulamalarınızda (ASP.NET Core web uygulaması, hizmetleri, masaüstü uygulaması, vb.) ile tahminlerde bulunmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aafed-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="aafed-182">Üçüncü bir varlık, eğitim kod hangi ML.NET API kodu CLI tarafından hangi belirli trainer/algoritması araştırabilir ve hiper parametreler CLI tarafından seçilen oluşturulan modeli eğitmek için kullanılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="aafed-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="aafed-183">Numaralandırılmış bu varlıkları öğreticinin aşağıdaki adımlarda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aafed-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="aafed-184">Oluşturulan keşfedin C# tahminlerde bulunmak üzere modeli çalıştırmak için kullanılacak kodu</span><span class="sxs-lookup"><span data-stu-id="aafed-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="aafed-185">Visual Studio (2017 veya 2019) adlı klasöründe oluşturulan çözümü açın `SampleBinaryClassification` , özgün hedef klasördeki (öğreticide taşıyordu `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="aafed-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="aafed-186">Benzer şekilde bir çözüm görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="aafed-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="aafed-187">Visual Studio kullanmak için önerdiğimiz öğreticide ancak da oluşturulan keşfedebilirsiniz C# ile oluşturulan konsol uygulaması (iki projeler) ile herhangi bir metin düzenleyicisi kod ve `dotnet CLI` MacOS, Linux veya Windows makinesi.</span><span class="sxs-lookup"><span data-stu-id="aafed-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![VS çözüm CLI tarafından oluşturulan](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="aafed-189">Oluşturulan **sınıf kitaplığı** serileştirilmiş ML model (.zip dosyası) ve veri sınıfları (veri modelleri) içeren, olan bir şey doğrudan kullanabilirsiniz, son kullanıcı uygulamanızda bile, sınıf kitaplığı doğrudan başvuruda (veya taşıma yazarken kodu tercih eder).</span><span class="sxs-lookup"><span data-stu-id="aafed-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="aafed-190">Oluşturulan **konsol uygulaması** gözden geçirmeniz gerekir ve genellikle daha sonra 'Puanlama code' yeniden yürütme kodunu içerir (ML model tahminler elde etmeye çalışan kodu), basit kod (yalnızca birkaç satır), son kullanıcıya taşıyarak Tahminde bulunmak istediğiniz uygulama.</span><span class="sxs-lookup"><span data-stu-id="aafed-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span> 

1. <span data-ttu-id="aafed-191">Açık **ModelInput.cs** ve **ModelOutput.cs** sınıf dosyaları içinde sınıf kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="aafed-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="aafed-192">Bu sınıfların 'veri sınıfları' veya verileri tutmak için kullanılan POCO sınıflar olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="aafed-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="aafed-193">'Ortak kod' olan ancak onlarca veya sütunları hatta yüzlerce veri kümeniz varsa, kullanışlı olması oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="aafed-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span> 
    - <span data-ttu-id="aafed-194">`ModelInput` Sınıfı, veri kümesinden okurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafed-194">The `ModelInput` class is used when reading data from the dataset.</span></span> 
    - <span data-ttu-id="aafed-195">`ModelOutput` Sınıfı (tahmin veriler) tahmin sonucu elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafed-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="aafed-196">Program.cs dosyasını açın ve kodu keşfedin.</span><span class="sxs-lookup"><span data-stu-id="aafed-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="aafed-197">Yalnızca birkaç satır içinde çalıştırmayı ve örnek tahminde bulunmak mümkün.</span><span class="sxs-lookup"><span data-stu-id="aafed-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

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

- <span data-ttu-id="aafed-198">Yalnızca ilk satırlık bir kod oluşturur bir `MLContext` ML.NET kod çalıştırdığınız zaman gerekli nesne.</span><span class="sxs-lookup"><span data-stu-id="aafed-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span> 

- <span data-ttu-id="aafed-199">Eğitim gerekmez çünkü ikinci kod satırının, zaten sizin için CLI aracı tarafından geliştirilen ve modele ait kayıtlı olduğundan modeli seri bırakılmıştır. ZIP dosyası.</span><span class="sxs-lookup"><span data-stu-id="aafed-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="aafed-200">Ancak görmek istiyorsanız *"nasıl modeli eğitilir"* CLI tarafından size bu satırı açıklamadan çıkarın ve bu belirli ML model için kullanılan eğitim kod Çalıştır/hata ayıkla.</span><span class="sxs-lookup"><span data-stu-id="aafed-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

- <span data-ttu-id="aafed-201">Kod üçüncü satırında model serileştirilmiş modeli yüklenemiyor. ZIP dosyasıyla `mlContext.Model.Load()` modelin yolunu sağlayarak API. ZIP dosyası.</span><span class="sxs-lookup"><span data-stu-id="aafed-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

- <span data-ttu-id="aafed-202">Dördüncü yüklediğiniz kod satırında oluşturun `PredictionEngine` nesnesi ile `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span><span class="sxs-lookup"><span data-stu-id="aafed-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="aafed-203">Gereksinim duyduğunuz `PredictionEngine` verilerin (Bu durumda, tek bir parça, yaklaşım tahmin etmek için metin), tek bir örnek hedefleyen bir tahminde bulunmak istediğiniz her nesne.</span><span class="sxs-lookup"><span data-stu-id="aafed-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

- <span data-ttu-id="aafed-204">Beşinci kod satırının, oluşturduğunuz olan *tek örnek verileri* işleve çağrı yaparak tahmin için kullanılacak `CreateSingleDataSample()`.</span><span class="sxs-lookup"><span data-stu-id="aafed-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="aafed-205">Bu işlev kastettiğinizi bilemez ne tür bir örnek verileri kullanmak için CLI aracı olduğundan, ilk satır kümesinin yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="aafed-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="aafed-206">Ancak, bu durumda, geçerli uygulaması yerine kendi 'sabit kodlanmış' veri oluşturabilirsiniz `CreateSingleDataSample()` güncelleştirerek bu işlevini uygulama bu basit kod işlevi:</span><span class="sxs-lookup"><span data-stu-id="aafed-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. <span data-ttu-id="aafed-207">Projeyi çalıştırmak, özgün örnek verileri kullanarak veri kümesinin veya kendi özel sabit kodlanmış örnek verileri sağlayarak ilk satırdan yüklendi.</span><span class="sxs-lookup"><span data-stu-id="aafed-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="aafed-208">Tahmin için karşılaştırılabilir almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="aafed-208">You should get a prediction comparable to:</span></span>

    # <a name="windowstabwindows"></a>[<span data-ttu-id="aafed-209">Windows</span><span class="sxs-lookup"><span data-stu-id="aafed-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="aafed-210">F5 tuşlarına basarak konsol uygulamasını Visual Studio'dan çalıştırma (Oynat düğmesini):</span><span class="sxs-lookup"><span data-stu-id="aafed-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![ML.NET CLI otomatik-PowerShell eğitme](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="aafed-212">)</span><span class="sxs-lookup"><span data-stu-id="aafed-212">)</span></span>

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="aafed-213">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="aafed-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="aafed-214">Konsol uygulaması, komut isteminden aşağıdaki komutları yazarak çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="aafed-214">Run the console app from the command-prompt by typing the following commands:</span></span>

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![ML.NET CLI otomatik-PowerShell eğitme](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="aafed-216">)</span><span class="sxs-lookup"><span data-stu-id="aafed-216">)</span></span>

    ---

1. <span data-ttu-id="aafed-217">Sabit kodlanmış örnek veriler için diğer cümleleri farklı bir yaklaşım ile değiştirmeyi deneyin ve nasıl pozitif veya negatif yaklaşım modeli tahmin bakın.</span><span class="sxs-lookup"><span data-stu-id="aafed-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span> 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="aafed-218">ML model tahminlerini son kullanıcı uygulamaları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aafed-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="aafed-219">Benzer 'ML model Puanlama kod' için model, son kullanıcı uygulama ve marka Öngörüler çalıştırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aafed-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span> 

<span data-ttu-id="aafed-220">Örneğin, doğrudan bu kodu herhangi bir Windows masaüstü uygulaması için gibi taşıyabilirsiniz **WPF** ve **WinForms** ve konsol uygulamasında bitti dedik daha modeli aynı şekilde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aafed-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="aafed-221">Ancak, bu ML model çalıştırmak için kod satırlarını uygulama yolu (yani, önbellek model .zip dosyası ve bir kez yük) hale getirilmiştir ve özellikle uygulamanızın gibi ölçeklenebilir olması gerekiyorsa her istek, bunları oluşturmak yerine tekil nesneleri bir web uygulaması veya aşağıdaki bölümünde anlatıldığı gibi dağıtılmış bir hizmet.</span><span class="sxs-lookup"><span data-stu-id="aafed-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="aafed-222">ML.NET modelleri ölçeklenebilir ASP.NET Core web uygulamaları ve Hizmetleri (çok iş parçacıklı uygulamalar) çalışan</span><span class="sxs-lookup"><span data-stu-id="aafed-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="aafed-223">Model nesnesinin oluşturulmasını (`ITransformer` bir modelin .zip dosyasından yüklenen) ve `PredictionEngine` nesne en iyi duruma getirilmiş özellikle ölçeklenebilir web uygulamaları ve Dağıtılmış hizmetler üzerinde çalışırken.</span><span class="sxs-lookup"><span data-stu-id="aafed-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="aafed-224">İlk durumda, model nesnesi için (`ITransformer`) en iyi duruma getirme oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="aafed-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="aafed-225">Bu yana `ITransformer` nesne iş parçacığı açısından güvenli, modeli bir kez yüklemek için nesnenin bir singleton veya statik nesne olarak önbelleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="aafed-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="aafed-226">İkinci nesne için `PredictionEngine` nesne çok kolay değildir çünkü `PredictionEngine` nesne iş parçacığı açısından güvenli değildir, bu nedenle tekil veya statik nesnesinde bir ASP.NET Core uygulaması olarak bu nesne örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="aafed-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="aafed-227">Bu iş parçacığı açısından güvenli ve ölçeklenebilirlik sorun derin bu konuda açıklanan [Blog Gönderisi](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="aafed-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

<span data-ttu-id="aafed-228">Ancak, şey sizin için bu blog gönderisinde açıklandığı daha çok daha kolaylaştırıldı.</span><span class="sxs-lookup"><span data-stu-id="aafed-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="aafed-229">Üzerinde basit bir yaklaşım işinize ve güzel bir oluşturduğunuz **'.NET Core tümleştirme paketi'** kolayca içinde ASP.NET Core uygulamalarınızı ve hizmetlerinizi DI uygulama Hizmetleri (bağımlılık ekleme kaydederek kullanabileceğiniz Hizmetleri) ve doğrudan kodunuzdan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aafed-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="aafed-230">Şu öğretici ve örnek için bunu kontrol edin:</span><span class="sxs-lookup"><span data-stu-id="aafed-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="aafed-231">Öğretici: ML.NET modelleri üzerinde Ölçeklenebilir ASP.NET Core web uygulamaları ve WebAPIs çalıştırma</span><span class="sxs-lookup"><span data-stu-id="aafed-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="aafed-232">Örnek: ASP.NET Core Webapı ölçeklenebilir ML.NET modeli</span><span class="sxs-lookup"><span data-stu-id="aafed-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="aafed-233">Oluşturulan keşfedin C# "en iyi kalite" modeli eğitmek için kullanılan kod</span><span class="sxs-lookup"><span data-stu-id="aafed-233">Explore the generated C# code that was used to train the "best quality" model</span></span> 

<span data-ttu-id="aafed-234">Öğrenme amacıyla daha gelişmiş için da oluşturulan keşfedebilirsiniz C# CLI aracı tarafından oluşturulan modeli eğitmek için kullanılan kod.</span><span class="sxs-lookup"><span data-stu-id="aafed-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="aafed-235">'Eğitim modeli kodu' şu anda oluşturulan özel bir sınıf içinde oluşturulduğunu adlı `ModelBuilder` eğitim kod araştırabileceği şekilde.</span><span class="sxs-lookup"><span data-stu-id="aafed-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="aafed-236">Daha da önemlisi, bu belirli senaryo (yaklaşım analizi modeli) için de kod ile oluşturulan eğitim kod aşağıdaki öğreticide açıklanan karşılaştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aafed-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="aafed-237">Karşılaştırma: [Öğretici: ML.NET bir yaklaşım analizi ikili sınıflandırma senaryosunda kullanmak](https://docs.microsoft.com/en-us/dotnet/machine-learning/tutorials/sentiment-analysis).</span><span class="sxs-lookup"><span data-stu-id="aafed-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](https://docs.microsoft.com/en-us/dotnet/machine-learning/tutorials/sentiment-analysis).</span></span>

<span data-ttu-id="aafed-238">Bu öğreticide seçtiğiniz algoritması ve ardışık düzen yapılandırma CLI aracı tarafından oluşturulan kodu karşılaştırmak ilgi çekici olur.</span><span class="sxs-lookup"><span data-stu-id="aafed-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="aafed-239">Yineleme ve arama için daha iyi modelleri harcadığınız ne kadar süre bağlı olarak seçilen algoritma ardışık düzen yapılandırması ve belirli hyper-parametreleriyle birlikte farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="aafed-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="aafed-240">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aafed-240">See also</span></span>

- [<span data-ttu-id="aafed-241">Model eğitiminin ML.NET CLI ile otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="aafed-241">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="aafed-242">Öğretici: ML.NET modelleri üzerinde Ölçeklenebilir ASP.NET Core web uygulamaları ve WebAPIs çalıştırma</span><span class="sxs-lookup"><span data-stu-id="aafed-242">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="aafed-243">Örnek: ASP.NET Core Webapı ölçeklenebilir ML.NET modeli</span><span class="sxs-lookup"><span data-stu-id="aafed-243">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="aafed-244">ML.NET CLI otomatik train komut Başvuru Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aafed-244">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="aafed-245">ML.NET komut satırı arabirimi (CLI) aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="aafed-245">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="aafed-246">ML.NET CLI'de telemetri</span><span class="sxs-lookup"><span data-stu-id="aafed-246">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a><span data-ttu-id="aafed-247">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="aafed-247">Next steps</span></span>

<span data-ttu-id="aafed-248">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="aafed-248">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="aafed-249">Verilerinizi seçili ML görev (sorunu çözmek için) için hazırlama</span><span class="sxs-lookup"><span data-stu-id="aafed-249">Prepare your data for the selected ML task (problem to solve)</span></span>
> * <span data-ttu-id="aafed-250">CLI aracında 'mlnet otomatik train' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="aafed-250">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> * <span data-ttu-id="aafed-251">Kalite Ölçüm sonuçlarını gözden geçirin</span><span class="sxs-lookup"><span data-stu-id="aafed-251">Review the quality metric results</span></span>
> * <span data-ttu-id="aafed-252">Oluşturulan anlamak C# kod modeli (son kullanıcı uygulamayı kullanmak için kodu)</span><span class="sxs-lookup"><span data-stu-id="aafed-252">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> * <span data-ttu-id="aafed-253">Oluşturulan keşfedin C# (öğrenme amacıyla) "en iyi kalite" modeli eğitmek için kullanılan kod</span><span class="sxs-lookup"><span data-stu-id="aafed-253">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aafed-254">Model eğitiminin ML.NET CLI ile otomatikleştirme</span><span class="sxs-lookup"><span data-stu-id="aafed-254">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
