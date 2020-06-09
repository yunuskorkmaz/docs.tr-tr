---
title: ML.NET CLI kullanarak yaklaşımı çözümleme
description: Örnek veri kümesinden otomatik olarak ML modeli ve ilgili C# kodu oluşturma
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 64190546157bc9386314a3080c5364fd854d7704
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602261"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="b15c7-103">ML.NET CLI kullanarak yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="b15c7-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="b15c7-104">ML.NET CLı kullanarak otomatik olarak bir ML.NET modeli ve temel C# kodu oluşturma hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="b15c7-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="b15c7-105">Veri kümenizi ve uygulamak istediğiniz makine öğrenimi görevini sağlarsınız ve CLı, model oluşturma ve dağıtım kaynak kodu ve sınıflandırma modeli oluşturmak için oto ml altyapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the classification model.</span></span>

<span data-ttu-id="b15c7-106">Bu öğreticide, aşağıdaki adımları kullanacaksınız:</span><span class="sxs-lookup"><span data-stu-id="b15c7-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b15c7-107">Verilerinizi seçili makine öğrenimi görevi için hazırlayın</span><span class="sxs-lookup"><span data-stu-id="b15c7-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="b15c7-108">CLı 'dan ' mlnet sınıflandırması ' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b15c7-108">Run the 'mlnet classification' command from the CLI</span></span>
> - <span data-ttu-id="b15c7-109">Kalite ölçümü sonuçlarını gözden geçirme</span><span class="sxs-lookup"><span data-stu-id="b15c7-109">Review the quality metric results</span></span>
> - <span data-ttu-id="b15c7-110">Uygulamanızda modeli kullanmak için oluşturulan C# kodunu anlayın</span><span class="sxs-lookup"><span data-stu-id="b15c7-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="b15c7-111">Modeli eğitmek için kullanılan oluşturulan C# kodunu keşfet</span><span class="sxs-lookup"><span data-stu-id="b15c7-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="b15c7-112">Bu konu, şu anda önizleme aşamasında olan ML.NET CLı aracına başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="b15c7-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b15c7-113">Daha fazla bilgi için [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="b15c7-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="b15c7-114">ML.NET CLı, ML.NET 'in bir parçasıdır ve ana amacı, öğrenimi öğrenirken, kullanmaya başlamak için sıfırdan kod oluşturmanız gerekmeyen .NET geliştiricileri için "herkese" ML.NET.</span><span class="sxs-lookup"><span data-stu-id="b15c7-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="b15c7-115">Sağladığınız eğitim veri kümelerine göre iyi kalitede ML.NET modelleri ve kaynak kodu oluşturmak için ML.NET CLı 'yi herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="b15c7-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="b15c7-116">Pre-requisites</span></span>

- <span data-ttu-id="b15c7-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) veya üzeri</span><span class="sxs-lookup"><span data-stu-id="b15c7-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) or later</span></span>
- <span data-ttu-id="b15c7-118">Seçim [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="b15c7-118">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="b15c7-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="b15c7-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="b15c7-120">Oluşturulan C# kod projelerini Visual Studio 'dan veya `dotnet run` (.NET Core CLI) ile çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="b15c7-121">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="b15c7-121">Prepare your data</span></span>

<span data-ttu-id="b15c7-122">İkili sınıflandırma makinesi öğrenimi görevi olan ' Yaklaşım Analizi ' senaryosu için kullanılan mevcut bir veri kümesini kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="b15c7-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="b15c7-123">Kendi veri kümenizi benzer bir şekilde kullanabilirsiniz ve model ve kod sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b15c7-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="b15c7-124">[(Aşağıdaki notdaki alıntıların bulunduğu) cümleler veri kümesi ZIP dosyasını](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)indirin ve seçtiğiniz herhangi bir klasörde sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="b15c7-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b15c7-125">Bu öğreticide veri kümeleri, ' Kimden grubundan, derin özellikleri kullanarak tek tek etiketlere, Kotzıas et al ' ı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="b15c7-126">KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="b15c7-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="b15c7-127">UCI Machine Learning deposu [ http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="b15c7-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="b15c7-128">Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.</span><span class="sxs-lookup"><span data-stu-id="b15c7-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="b15c7-129">`yelp_labelled.txt`Dosyayı daha önce oluşturduğunuz herhangi bir klasöre (örneğin,) kopyalayın `/cli-test` .</span><span class="sxs-lookup"><span data-stu-id="b15c7-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="b15c7-130">Tercih ettiğiniz komut istemi ' ni açın ve veri kümesi dosyasını kopyaladığınız klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="b15c7-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="b15c7-131">Örnek:</span><span class="sxs-lookup"><span data-stu-id="b15c7-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="b15c7-132">Visual Studio Code gibi herhangi bir metin düzenleyicisini kullanarak `yelp_labelled.txt` veri kümesi dosyasını açabilir ve keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="b15c7-133">Yapının şu olduğunu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b15c7-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="b15c7-134">Dosya üst bilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="b15c7-134">The file has no header.</span></span> <span data-ttu-id="b15c7-135">Sütunun dizinini kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b15c7-135">You will use the column's index.</span></span>

    - <span data-ttu-id="b15c7-136">Yalnızca iki sütun vardır:</span><span class="sxs-lookup"><span data-stu-id="b15c7-136">There are just two columns:</span></span>

        | <span data-ttu-id="b15c7-137">Metin (sütun dizini 0)</span><span class="sxs-lookup"><span data-stu-id="b15c7-137">Text (Column index 0)</span></span> | <span data-ttu-id="b15c7-138">Etiket (sütun dizini 1)</span><span class="sxs-lookup"><span data-stu-id="b15c7-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="b15c7-139">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="b15c7-139">Wow... Loved this place.</span></span> | <span data-ttu-id="b15c7-140">1</span><span class="sxs-lookup"><span data-stu-id="b15c7-140">1</span></span> |
        | <span data-ttu-id="b15c7-141">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="b15c7-141">Crust is not good.</span></span> | <span data-ttu-id="b15c7-142">0</span><span class="sxs-lookup"><span data-stu-id="b15c7-142">0</span></span> |
        | <span data-ttu-id="b15c7-143">Nefis değildir ve doku yalnızca Nasty idi.</span><span class="sxs-lookup"><span data-stu-id="b15c7-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="b15c7-144">0</span><span class="sxs-lookup"><span data-stu-id="b15c7-144">0</span></span> |
        | <span data-ttu-id="b15c7-145">... ÇOK SAYıDA METIN SATıRı...</span><span class="sxs-lookup"><span data-stu-id="b15c7-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="b15c7-146">... (1 veya 0)...</span><span class="sxs-lookup"><span data-stu-id="b15c7-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="b15c7-147">Veri kümesi dosyasını düzenleyiciden kapattığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b15c7-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="b15c7-148">Şimdi bu ' Yaklaşım Analizi ' senaryosu için CLı kullanmaya başlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="b15c7-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b15c7-149">Bu Öğreticiyi tamamladıktan sonra, şu anda *' Ikili sınıflandırma ', ' sınıflandırma ', ' gerileme '* ve *' öneri '* olan ml.net CLI önizlemesi tarafından desteklenen herhangi bir ml görevi için kullanılmak üzere hazırlandıkları sürece kendi veri kümelerinizi de deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Classification', 'Regression',* and *'Recommendation'*.</span></span>

## <a name="run-the-mlnet-classification-command"></a><span data-ttu-id="b15c7-150">' Mlnet sınıflandırması ' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b15c7-150">Run the 'mlnet classification' command</span></span>

1. <span data-ttu-id="b15c7-151">Aşağıdaki ML.NET CLı komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b15c7-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    <span data-ttu-id="b15c7-152">Bu komut \*\* `mlnet classification` komutunu\*\*çalıştırır:</span><span class="sxs-lookup"><span data-stu-id="b15c7-152">This command runs the **`mlnet classification` command**:</span></span>
    - <span data-ttu-id="b15c7-153">*sınıflandırmanın* **ml görevi** için</span><span class="sxs-lookup"><span data-stu-id="b15c7-153">for the **ML task** of *classification*</span></span>
    - <span data-ttu-id="b15c7-154">\*\*veri kümesi dosyasını `yelp_labelled.txt` \*\* eğitim ve test veri kümesi olarak kullanır (dahili olarak CLI, çapraz doğrulama kullanır ya da bir diğeri de test için bir tane olmak üzere iki veri kümesinde bölüşlecektir)</span><span class="sxs-lookup"><span data-stu-id="b15c7-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="b15c7-155">tahmin etmek istediğiniz **amaç/hedef sütununun** (genellikle **' Label '** olarak adlandırılır) dizin 1 (Dizin sıfır tabanlı olduğundan ikinci sütun) **olan sütundur**</span><span class="sxs-lookup"><span data-stu-id="b15c7-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="b15c7-156">Bu veri kümesi dosyası bir üst bilgisine sahip olmadığından, sütun adlarıyla **bir dosya üstbilgisi kullanmaz**</span><span class="sxs-lookup"><span data-stu-id="b15c7-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="b15c7-157">deneme için **hedeflenen araştırma/tren süresi** **10 saniyedir**</span><span class="sxs-lookup"><span data-stu-id="b15c7-157">the **targeted exploration/train time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="b15c7-158">CLı 'dan aşağıdakine benzer bir çıktı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="b15c7-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 MD025 -->

    ![PowerShell 'de ML.NET CLı sınıflandırması](./media/mlnet-cli/mlnet-classification-powershell.gif)

    <span data-ttu-id="b15c7-160">Bu özel durumda, yalnızca 10 saniye içinde ve küçük veri kümesiyle sunulan CLı Aracı, farklı iç veri dönüştürmeleri ve algoritmaların Hyper-parametreleri ile farklı algoritma/yapılandırma birleşimlerine göre birden çok kez eğitim sağlayan çok sayıda yineleme çalıştırabiliyor.</span><span class="sxs-lookup"><span data-stu-id="b15c7-160">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="b15c7-161">Son olarak, 10 saniye içinde bulunan "en iyi kalite" modeli, belirli bir yapılandırma ile belirli bir oran/algoritma kullanan bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="b15c7-161">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="b15c7-162">Araştırma zamanına bağlı olarak, komut farklı bir sonuç oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b15c7-162">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="b15c7-163">Seçim, gösterilen çoklu ölçümleri temel alır `Accuracy` .</span><span class="sxs-lookup"><span data-stu-id="b15c7-163">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="b15c7-164">**Modelin kalite ölçümlerini anlama**</span><span class="sxs-lookup"><span data-stu-id="b15c7-164">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="b15c7-165">İkili sınıflandırma modelini değerlendirmek için ilk ve en kolay ölçüm, anlaşılması kolay bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="b15c7-165">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="b15c7-166">"Doğruluk, test veri kümesiyle doğru tahminlerden orandır.".</span><span class="sxs-lookup"><span data-stu-id="b15c7-166">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="b15c7-167">%100 ' e (1,00) yaklaşarak daha iyi.</span><span class="sxs-lookup"><span data-stu-id="b15c7-167">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="b15c7-168">Ancak, özellikle de doğruluk ölçümüyle ölçmeniz yeterli değildir, özellikle de (Bu durumda 0 ve 1) etiketi test veri kümesinde dengesiz olur.</span><span class="sxs-lookup"><span data-stu-id="b15c7-168">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="b15c7-169">Farklı modelleri değerlendirmek için kullanılan doğruluk, AUC, AUCPR ve F1-Score gibi ölçümler hakkında ek ölçümler ve daha **ayrıntılı bilgiler** için bkz. [ml.net ölçümlerini anlama](../resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="b15c7-169">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b15c7-170">Bu çok satırlı veri kümesini deneyebilir ve `--max-exploration-time` Bu veri kümesi için farklı bir eğitim işlem hattı yapılandırması (oldukça küçük, 1000 satır) ile sizin için daha iyi bir "en iyi model" bulunacak 180 şekilde birkaç dakika (örneğin, üç dakika) bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b15c7-170">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="b15c7-171">Daha büyük veri kümelerini hedefleyen "üretime hazır bir model" olan "en iyi/iyi kalite" modelini bulmak için, CLı ile denemeleri, genellikle veri kümesinin boyutuna bağlı olarak çok daha fazla araştırma süresi belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-171">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="b15c7-172">Aslında, çoğu durumda, özellikle veri kümesi satırlar ve sütunlar üzerinde büyükse, birden çok saat araştırma süresi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b15c7-172">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="b15c7-173">Önceki komut yürütmesi aşağıdaki varlıkları oluşturdu:</span><span class="sxs-lookup"><span data-stu-id="b15c7-173">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="b15c7-174">Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.</span><span class="sxs-lookup"><span data-stu-id="b15c7-174">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="b15c7-175">Oluşturulan modeli çalıştırmak/öğrenmek için C# kodu (bu modelle Son Kullanıcı uygulamalarınızda tahminleri yapmak Için).</span><span class="sxs-lookup"><span data-stu-id="b15c7-175">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="b15c7-176">Bu modeli oluşturmak için kullanılan C# eğitim kodu (öğrenme amaçları).</span><span class="sxs-lookup"><span data-stu-id="b15c7-176">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="b15c7-177">Her bir algoritmayla ilgili ayrıntılı bilgileri keşfeden tüm yinelemeleri içeren bir günlük dosyası, Hyper-parametreleri ve veri dönüştürmeleri birleşimine çalıştı.</span><span class="sxs-lookup"><span data-stu-id="b15c7-177">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="b15c7-178">İlk iki varlık (. Bu modeli çalıştırmak için ZIP dosya modeli ve C# kodu), bu oluşturulmuş ML modeliyle tahmine dayalı hale getirmek için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b15c7-178">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="b15c7-179">Eğitim kodu olan üçüncü varlık, CLI tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. bu sayede, CLı tarafından hangi belirli bir oran/algoritma ve Hyper-parametrelerinin seçili olduğunu araştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-179">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="b15c7-180">Bu numaralandırılabilir varlıklar, öğreticinin aşağıdaki adımlarında açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-180">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="b15c7-181">Tahmine dayalı hale getirmek üzere modeli çalıştırmak için kullanılacak oluşturulan C# kodunu keşfet</span><span class="sxs-lookup"><span data-stu-id="b15c7-181">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="b15c7-182">Visual Studio 'da (2017 veya 2019) özgün hedef klasörünüzün içindeki adlı klasörde oluşturulan çözümü açın `SampleClassification` (öğreticide adı altında `/cli-test` ).</span><span class="sxs-lookup"><span data-stu-id="b15c7-182">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="b15c7-183">Şuna benzer bir çözüm görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="b15c7-183">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="b15c7-184">Visual Studio 'Yu kullanmayı önerdiğimiz öğreticide, tüm metin düzenleyiciyle oluşturulan C# kodunu (iki proje) keşfedebilir ve oluşturulan konsol uygulamasını `dotnet CLI` macOS, Linux veya Windows makinesi ile çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-184">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![CLı tarafından oluşturulan VS çözümü](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - <span data-ttu-id="b15c7-186">Serileştirilmiş ML modeli (. zip dosyası) ve veri sınıfları (veri modelleri) içeren oluşturulmuş **sınıf kitaplığı** , doğrudan bu sınıf kitaplığına (veya istediğiniz şekilde kodu taşıyarak) doğrudan başvuru yaparak, Son Kullanıcı uygulamanızda doğrudan kullanabileceğiniz bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="b15c7-186">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="b15c7-187">Oluşturulan **konsol uygulaması** , gözden geçirmeniz gereken yürütme kodunu içerir ve ardından genellikle bu basit kodu (yalnızca birkaç satır) tahmine dayalı hale getirmek istediğiniz son kullanıcı uygulamanıza taşıyarak ' Puanlama kodu ' nu (tahminleri yapmak için ml modelini çalıştıran kod) yeniden kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b15c7-187">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="b15c7-188">**ModelInput.cs** ve **ModelOutput.cs** sınıf dosyalarını sınıf kitaplığı projesi içinde açın.</span><span class="sxs-lookup"><span data-stu-id="b15c7-188">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="b15c7-189">Bu sınıfların, verileri tutmak için kullanılan ' veri sınıfları ' veya POCO sınıfları olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-189">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="b15c7-190">Bu, ' ortak kod ', ancak veri kümeniz yüzlerce veya hatta yüzlerce sütun içeriyorsa oluşturulmasını sağlamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-190">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="b15c7-191">`ModelInput`Sınıf, veri kümesinden verileri okurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-191">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="b15c7-192">`ModelOutput`Sınıfı, tahmin sonucunu (tahmin verileri) almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-192">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="b15c7-193">Program.cs dosyasını açın ve kodu araştırın.</span><span class="sxs-lookup"><span data-stu-id="b15c7-193">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="b15c7-194">Yalnızca birkaç satırda modeli çalıştırabilir ve örnek bir tahmin yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-194">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - Kodun ilk satırı, bu örnekte tahmin için kullanılacak veri kümenizin ilk satırına göre *tek bir örnek veri*oluşturur. <span data-ttu-id="b15c7-196">Ayrıca, kodu güncelleştirerek ' sabit kodlanmış ' verileri de oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b15c7-196">You can also create you own 'hard-coded' data by updating the code:</span></span>

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - <span data-ttu-id="b15c7-197">Sonraki kod satırı, `ConsumeModel.Predict()` bir tahmin yapmak ve sonuçları döndürmek (ModelOutput.cs şemasına göre) için belirtilen giriş verilerinde yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-197">The next line of code uses the `ConsumeModel.Predict()` method on the specified input data to make a prediction and return the results (based on the ModelOutput.cs schema).</span></span>
    - <span data-ttu-id="b15c7-198">Kodun son satırları, örnek verilerin (Bu örnekte açıklama) yanı sıra pozitif yaklaşım (1) ve olumsuz yaklaşım (2) için yaklaşım tahminini ve karşılık gelen puanları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-198">The last lines of code print out the proprties of the sample data (in this case the Comment) as well as the Sentiment prediction and corresponding Scores for positive sentiment (1) and negative sentiment (2).</span></span>

1. <span data-ttu-id="b15c7-199">Veri kümesinin ilk satırından yüklenen özgün örnek verileri kullanarak ya da kendi özel sabit kodlanmış örnek verilerinizi sağlayarak projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b15c7-199">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="b15c7-200">Şu şekilde bir tahmin almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b15c7-200">You should get a prediction comparable to:</span></span>

![ML.NET CLı uygulamayı Visual Studio 'dan çalıştırma](./media/mlnet-cli/mlnet-cli-console-app.png)<span data-ttu-id="b15c7-202">)</span><span class="sxs-lookup"><span data-stu-id="b15c7-202">)</span></span>

1. <span data-ttu-id="b15c7-203">Sabit kodlanmış örnek verileri farklı bir yaklaşım ile diğer cümleler ile değiştirmeyi deneyin ve modelin olumlu veya negatif yaklaşımı nasıl tahmin eder olduğunu görün.</span><span class="sxs-lookup"><span data-stu-id="b15c7-203">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="b15c7-204">ML modeli tahminleri ile Son Kullanıcı uygulamalarınızı kullanın</span><span class="sxs-lookup"><span data-stu-id="b15c7-204">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="b15c7-205">Modeli son kullanıcı uygulamanızda çalıştırmak ve tahmin yapmak için benzer ' ML model Puanlama kodu ' kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-205">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="b15c7-206">Örneğin, bu kodu doğrudan **WPF** ve **WinForms** gibi herhangi bir Windows masaüstü uygulamasına taşıyabilir ve modeli konsol uygulamasında yapılmayla aynı şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-206">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="b15c7-207">Ancak, bir ML modelini çalıştırmak için bu kod satırlarını uyguladığınızda,, özellikle uygulamanızın aşağıdaki bölümde açıklandığı gibi bir Web uygulaması veya dağıtılmış hizmet gibi ölçeklenebilir olması gerekiyorsa, her istekte bunları oluşturmak yerine tek tek nesnelere sahip olması gerekir (yani, model. zip dosyasını önbelleğe alır ve bunları bir kez yükler).</span><span class="sxs-lookup"><span data-stu-id="b15c7-207">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="b15c7-208">Ölçeklenebilir ASP.NET Core Web uygulamaları ve Hizmetleri 'nde ML.NET modellerini çalıştırma (çok kanallı uygulamalar)</span><span class="sxs-lookup"><span data-stu-id="b15c7-208">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="b15c7-209">Model nesnesinin oluşturulması ( `ITransformer` bir modelin. zip dosyasından yüklenir) ve `PredictionEngine` nesne özellikle ölçeklenebilir Web uygulamaları ve dağıtılmış hizmetler üzerinde çalışırken iyileştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b15c7-209">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="b15c7-210">İlk durumda, model nesnesi ( `ITransformer` ) iyileştirmesi basittir.</span><span class="sxs-lookup"><span data-stu-id="b15c7-210">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="b15c7-211">`ITransformer`Nesne iş parçacığı açısından güvenli olduğundan, modeli bir kez yüklemeniz için nesneyi tek veya statik bir nesne olarak önbelleğe alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-211">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="b15c7-212">Nesne iş parçacığı açısından güvenli olmadığından, ikinci nesne için nesnesi `PredictionEngine` Bu kadar kolay değildir `PredictionEngine` , bu nedenle bu nesneyi ASP.NET Core uygulamasında tek veya statik nesne olarak örnekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-212">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="b15c7-213">Bu iş parçacığı güvenli ve ölçeklenebilirlik sorunu bu [blog gönderisine](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)göre ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="b15c7-213">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="b15c7-214">Ancak, bu blog gönderisinden açıklanamayan şeyler sizin için çok daha kolay.</span><span class="sxs-lookup"><span data-stu-id="b15c7-214">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="b15c7-215">Sizin için daha basit bir yaklaşımda çalıştık ve uygulamayı uygulama ve hizmetASP.NET Core lerinize uygulama dı Hizmetleri 'ne (bağımlılık ekleme Hizmetleri) kaydederek ve sonra doğrudan kodunuzda kullanarak kolayca kullanabileceğiniz iyi bir **' .NET Core Integration Package '** oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-215">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="b15c7-216">Şunları yapmak için aşağıdaki öğreticiyi ve örneğe bakın:</span><span class="sxs-lookup"><span data-stu-id="b15c7-216">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="b15c7-217">Öğretici: ML.NET modellerini ölçeklenebilir ASP.NET Core Web Apps ve WebAPIs üzerinde çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b15c7-217">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="b15c7-218">Örnek: ASP.NET Core WebAPI üzerinde ölçeklenebilir ML.NET modeli</span><span class="sxs-lookup"><span data-stu-id="b15c7-218">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="b15c7-219">"En iyi kalite" modelini eğitmek için kullanılan oluşturulan C# kodunu keşfet</span><span class="sxs-lookup"><span data-stu-id="b15c7-219">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="b15c7-220">Daha gelişmiş öğrenme amaçlarıyla, oluşturulan modeli eğitebilmeniz için CLı aracı tarafından kullanılan oluşturulan C# kodunu da keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-220">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="b15c7-221">' Eğitim modeli kodu ' Şu anda adında oluşturulan özel sınıfta oluşturulmuştur, `ModelBuilder` böylece bu eğitim kodunu araştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-221">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="b15c7-222">Daha önemlisi, bu senaryo (Yaklaşım Analizi modeli) için de, aşağıdaki öğreticide açıklanan kod ile bu üretilen eğitim kodunu karşılaştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b15c7-222">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="b15c7-223">Compare: [öğretici: bir yaklaşım Analizi ikili sınıflandırma senaryosunda ml.NET kullanın](sentiment-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="b15c7-223">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="b15c7-224">Öğreticide seçilen algoritma ve işlem hattı yapılandırmasını CLı aracı tarafından oluşturulan kodla karşılaştırmak ilginç.</span><span class="sxs-lookup"><span data-stu-id="b15c7-224">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="b15c7-225">Daha iyi modeller için ne kadar zaman harcadığınıza ve aradığınıza bağlı olarak, seçilen algoritma belirli Hyper-parametreleri ve işlem hattı yapılandırmasıyla birlikte farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b15c7-225">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="b15c7-226">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="b15c7-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b15c7-227">Verilerinizi seçilen ML görevi için hazırlayın (çözülme sorunu)</span><span class="sxs-lookup"><span data-stu-id="b15c7-227">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="b15c7-228">CLı aracında ' mlnet sınıflandırması ' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b15c7-228">Run the 'mlnet classification' command in the CLI tool</span></span>
> - <span data-ttu-id="b15c7-229">Kalite ölçümü sonuçlarını gözden geçirme</span><span class="sxs-lookup"><span data-stu-id="b15c7-229">Review the quality metric results</span></span>
> - <span data-ttu-id="b15c7-230">Modeli çalıştırmak için oluşturulan C# kodunu anlayın (Son Kullanıcı uygulamanızda kullanılacak kod)</span><span class="sxs-lookup"><span data-stu-id="b15c7-230">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="b15c7-231">"En iyi kalite" modelini (kazanlama amaçları) eğitmek için kullanılan oluşturulan C# kodunu keşfet</span><span class="sxs-lookup"><span data-stu-id="b15c7-231">Explore the generated C# code that was used to train the "best quality" model (earning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="b15c7-232">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b15c7-232">See also</span></span>

- [<span data-ttu-id="b15c7-233">ML.NET CLı ile model eğitimi otomatikleştirin</span><span class="sxs-lookup"><span data-stu-id="b15c7-233">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="b15c7-234">Öğretici: ML.NET modellerini ölçeklenebilir ASP.NET Core Web Apps ve WebAPIs üzerinde çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b15c7-234">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="b15c7-235">Örnek: ASP.NET Core WebAPI üzerinde ölçeklenebilir ML.NET modeli</span><span class="sxs-lookup"><span data-stu-id="b15c7-235">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="b15c7-236">ML.NET CLı otomatik eğitme komut başvuru kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b15c7-236">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="b15c7-237">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="b15c7-237">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
