---
title: ML.NET CLI kullanarak yaklaşımı çözümleme
description: Bir ML modelini ve bir örnek veri C# kümesinden ilgili kodu otomatik olarak oluştur
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 6dbd69c8424227f85d8bf3cdcaf6cf9dbf7e1f4c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856024"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="ac8d0-103">ML.NET CLI kullanarak yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="ac8d0-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="ac8d0-104">ML.NET CLı kullanarak bir ML.NET modeli ve temel alınan C# kodu otomatik olarak oluşturma hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="ac8d0-105">Veri kümenizi ve uygulamak istediğiniz makine öğrenimi görevini sağlarsınız ve CLı, model oluşturma ve dağıtım kaynak kodu ve ikili modeli oluşturmak için, oto ml altyapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="ac8d0-106">Bu öğreticide, aşağıdaki adımları kullanacaksınız:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="ac8d0-107">Verilerinizi seçili makine öğrenimi görevi için hazırlayın</span><span class="sxs-lookup"><span data-stu-id="ac8d0-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="ac8d0-108">CLı 'dan ' mlnet Auto-eğitme ' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="ac8d0-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> - <span data-ttu-id="ac8d0-109">Kalite ölçümü sonuçlarını gözden geçirme</span><span class="sxs-lookup"><span data-stu-id="ac8d0-109">Review the quality metric results</span></span>
> - <span data-ttu-id="ac8d0-110">Uygulamanızda modeli kullanmak C# için oluşturulan kodu anlayın</span><span class="sxs-lookup"><span data-stu-id="ac8d0-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="ac8d0-111">Modeli eğitmek için C# kullanılan üretilen kodu keşfet</span><span class="sxs-lookup"><span data-stu-id="ac8d0-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="ac8d0-112">Bu konu, şu anda önizleme aşamasında olan ML.NET CLı aracına başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ac8d0-113">Daha fazla bilgi için [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="ac8d0-114">ML.NET CLı, ML.NET 'in bir parçasıdır ve ana amacı, öğrenimi öğrenirken, kullanmaya başlamak için sıfırdan kod oluşturmanız gerekmeyen .NET geliştiricileri için "herkese" ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="ac8d0-115">Sağladığınız eğitim veri kümelerine göre iyi kalitede ML.NET modelleri ve kaynak kodu oluşturmak için ML.NET CLı 'yi herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="ac8d0-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="ac8d0-116">Pre-requisites</span></span>

- <span data-ttu-id="ac8d0-117">[.NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya üzeri</span><span class="sxs-lookup"><span data-stu-id="ac8d0-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="ac8d0-118">Seçim [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="ac8d0-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="ac8d0-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="ac8d0-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="ac8d0-120">Oluşturulan C# kod projelerini Visual Studio 'dan veya (.NET Core CLI) ile `dotnet run` çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="ac8d0-121">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="ac8d0-121">Prepare your data</span></span>

<span data-ttu-id="ac8d0-122">İkili sınıflandırma makinesi öğrenimi görevi olan ' Yaklaşım Analizi ' senaryosu için kullanılan mevcut bir veri kümesini kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="ac8d0-123">Kendi veri kümenizi benzer bir şekilde kullanabilirsiniz ve model ve kod sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="ac8d0-124">[(Aşağıdaki notdaki alıntıların bulunduğu) cümleler veri kümesi ZIP dosyasını](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)indirin ve seçtiğiniz herhangi bir klasörde sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ac8d0-125">Bu öğreticide veri kümeleri, ' Kimden grubundan, derin özellikleri kullanarak tek tek etiketlere, Kotzıas et al ' ı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="ac8d0-126">KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="ac8d0-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="ac8d0-127">UCI Machine Learning deposu [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="ac8d0-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="ac8d0-128">Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="ac8d0-129">Dosyayı daha önce oluşturduğunuz herhangi bir klasöre ( `/cli-test`Örneğin,) kopyalayın. `yelp_labelled.txt`</span><span class="sxs-lookup"><span data-stu-id="ac8d0-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="ac8d0-130">Tercih ettiğiniz komut istemi ' ni açın ve veri kümesi dosyasını kopyaladığınız klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="ac8d0-131">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-131">For example:</span></span>

    ```console
    > cd /cli-test
    ```

    <span data-ttu-id="ac8d0-132">Visual Studio Code gibi herhangi bir metin düzenleyicisini kullanarak `yelp_labelled.txt` veri kümesi dosyasını açabilir ve keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="ac8d0-133">Yapının şu olduğunu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="ac8d0-134">Dosya üst bilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-134">The file has no header.</span></span> <span data-ttu-id="ac8d0-135">Sütunun dizinini kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-135">You will use the column's index.</span></span>

    - <span data-ttu-id="ac8d0-136">Yalnızca iki sütun vardır:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-136">There are just two columns:</span></span>

        | <span data-ttu-id="ac8d0-137">Metin (sütun dizini 0)</span><span class="sxs-lookup"><span data-stu-id="ac8d0-137">Text (Column index 0)</span></span> | <span data-ttu-id="ac8d0-138">Etiket (sütun dizini 1)</span><span class="sxs-lookup"><span data-stu-id="ac8d0-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="ac8d0-139">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-139">Wow... Loved this place.</span></span> | <span data-ttu-id="ac8d0-140">1\.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-140">1</span></span> |
        | <span data-ttu-id="ac8d0-141">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-141">Crust is not good.</span></span> | <span data-ttu-id="ac8d0-142">0</span><span class="sxs-lookup"><span data-stu-id="ac8d0-142">0</span></span> |
        | <span data-ttu-id="ac8d0-143">Nefis değildir ve doku yalnızca Nasty idi.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="ac8d0-144">0</span><span class="sxs-lookup"><span data-stu-id="ac8d0-144">0</span></span> |
        | <span data-ttu-id="ac8d0-145">... ÇOK SAYIDA METIN SATIRI...</span><span class="sxs-lookup"><span data-stu-id="ac8d0-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="ac8d0-146">... (1 veya 0)...</span><span class="sxs-lookup"><span data-stu-id="ac8d0-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="ac8d0-147">Veri kümesi dosyasını düzenleyiciden kapattığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="ac8d0-148">Şimdi bu ' Yaklaşım Analizi ' senaryosu için CLı kullanmaya başlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ac8d0-149">Bu Öğreticiyi tamamladıktan sonra, şu anda *' Ikili sınıflandırma ', ' Multi-Class Classification ' ve ' regresyon '* olan ml.net CLI önizlemesi tarafından desteklenen HERHANGI bir ml görevi için kullanılmak üzere hazırlandıkları sürece kendi veri kümelerinizi de deneyebilirsiniz ).</span><span class="sxs-lookup"><span data-stu-id="ac8d0-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="ac8d0-150">' Mlnet otomatik-eğitme ' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="ac8d0-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="ac8d0-151">Aşağıdaki ML.NET CLı komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-151">Run the following ML.NET CLI command:</span></span>

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="ac8d0-152">Bu komut  **`mlnet auto-train` komutunu**çalıştırır:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="ac8d0-153">türündeki **ml görevi** için **`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="ac8d0-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="ac8d0-154">**veri kümesi dosyasını `yelp_labelled.txt`**  eğitim ve test veri kümesi olarak kullanır (dahili olarak CLI, çapraz doğrulama kullanır ya da bir diğeri de test için bir tane olmak üzere iki veri kümesinde bölüşlecektir)</span><span class="sxs-lookup"><span data-stu-id="ac8d0-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="ac8d0-155">tahmin etmek istediğiniz **amaç/hedef sütununun** (genellikle **' Label '** olarak adlandırılır) dizin 1 (Dizin sıfır tabanlı olduğundan ikinci sütun) **olan sütundur**</span><span class="sxs-lookup"><span data-stu-id="ac8d0-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="ac8d0-156">Bu veri kümesi dosyası bir üst bilgisine sahip olmadığından, sütun adlarıyla **bir dosya üstbilgisi kullanmaz**</span><span class="sxs-lookup"><span data-stu-id="ac8d0-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="ac8d0-157">deneme için **hedeflenen araştırma süresi** **10 saniyedir**</span><span class="sxs-lookup"><span data-stu-id="ac8d0-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="ac8d0-158">CLı 'dan aşağıdakine benzer bir çıktı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[<span data-ttu-id="ac8d0-159">Windows</span><span class="sxs-lookup"><span data-stu-id="ac8d0-159">Windows</span></span>](#tab/windows)

    ![PowerShell 'de ML.NET CLı otomatik eğitimi](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="ac8d0-161">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="ac8d0-161">macOS Bash</span></span>](#tab/macosbash)

    ![PowerShell 'de ML.NET CLı otomatik eğitimi](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="ac8d0-163">Bu özel durumda, yalnızca 10 saniye içinde ve küçük veri kümesiyle sunulan CLı Aracı, farklı iç verilerle farklı algoritmaların/yapılandırmanın farklı birleşimlerine göre birden çok kez birkaç yineleme çalıştırabiliyor dönüşümler ve algoritmanın Hyper-parametreleri.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span> 

    <span data-ttu-id="ac8d0-164">Son olarak, 10 saniye içinde bulunan "en iyi kalite" modeli, belirli bir yapılandırma ile belirli bir oran/algoritma kullanan bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="ac8d0-165">Araştırma zamanına bağlı olarak, komut farklı bir sonuç oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="ac8d0-166">Seçim, gösterilen `Accuracy`çoklu ölçümleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="ac8d0-167">**Modelin kalite ölçümlerini anlama**</span><span class="sxs-lookup"><span data-stu-id="ac8d0-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="ac8d0-168">İkili sınıflandırma modelini değerlendirmek için ilk ve en kolay ölçüm, anlaşılması kolay bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="ac8d0-169">"Doğruluk, test veri kümesiyle doğru tahminlerden orandır.".</span><span class="sxs-lookup"><span data-stu-id="ac8d0-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="ac8d0-170">% 100 ' e (1,00) yaklaşarak daha iyi.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="ac8d0-171">Ancak, özellikle de doğruluk ölçümüyle ölçmeniz yeterli değildir, özellikle de (Bu durumda 0 ve 1) etiketi test veri kümesinde dengesiz olur.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="ac8d0-172">Farklı modelleri değerlendirmek için kullanılan doğruluk, AUC, AUCPR, F1-Score gibi ölçümler hakkında ek ölçümler ve daha **ayrıntılı bilgiler** için, [ml.net ölçümlerini anlama](../resources/metrics.md) makalesini okuyabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="ac8d0-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, F1-score used to evaluate the different models, you can read [Understanding ML.NET metrics](../resources/metrics.md)</span></span>

    > [!NOTE]
    > <span data-ttu-id="ac8d0-173">Bu çok sayıda aynı veri kümesini deneyebilir ve bu veri kümesi için farklı `--max-exploration-time` bir eğitim işlem hattı yapılandırması ile sizin için daha iyi bir "en iyi model" bulacak olan (örneğin, üç 180 dakika) için birkaç dakika belirtebilirsiniz (Bu durum oldukça küçük, 1000 satır).</span><span class="sxs-lookup"><span data-stu-id="ac8d0-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span> 
        
    <span data-ttu-id="ac8d0-174">Daha büyük veri kümelerini hedefleyen "üretime hazır bir model" olan "en iyi/iyi kalite" modelini bulmak için, CLı ile denemeleri, genellikle veri kümesinin boyutuna bağlı olarak çok daha fazla araştırma süresi belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="ac8d0-175">Aslında, çoğu durumda, özellikle veri kümesi satırlar ve sütunlar üzerinde büyükse, birden çok saat araştırma süresi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span> 

1. <span data-ttu-id="ac8d0-176">Önceki komut yürütmesi aşağıdaki varlıkları oluşturdu:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="ac8d0-177">Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-177">A serialized model .zip ("best model") ready to use.</span></span> 
    - <span data-ttu-id="ac8d0-178">C#oluşturulan model (bu modelle Son Kullanıcı uygulamalarınızda tahmine dayalı hale getirmek Için) çalıştırılacak/puan veren kod.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="ac8d0-179">C#Bu modeli oluşturmak için kullanılan eğitim kodu (öğrenme amaçları).</span><span class="sxs-lookup"><span data-stu-id="ac8d0-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="ac8d0-180">Her bir algoritmayla ilgili ayrıntılı bilgileri keşfeden tüm yinelemeleri içeren bir günlük dosyası, Hyper-parametreleri ve veri dönüştürmeleri birleşimine çalıştı.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span> 

    <span data-ttu-id="ac8d0-181">İlk iki varlık (. ZIP dosya modeli ve C# bu modeli çalıştırmaya yönelik kod), bu oluşturulmuş ml modeliyle tahminler yapmak için doğrudan Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="ac8d0-182">Eğitim kodu olan üçüncü varlık, CLI tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. bu sayede, CLı tarafından hangi belirli bir oran/algoritma ve Hyper-parametrelerinin seçili olduğunu araştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="ac8d0-183">Bu numaralandırılabilir varlıklar, öğreticinin aşağıdaki adımlarında açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="ac8d0-184">Tahmine dayalı hale C# getirmek üzere modeli çalıştırmak için kullanılacak oluşturulan kodu keşfet</span><span class="sxs-lookup"><span data-stu-id="ac8d0-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="ac8d0-185">Visual Studio 'da (2017 veya 2019) özgün hedef klasörünüzün içindeki adlı `SampleBinaryClassification` klasörde oluşturulan çözümü açın (öğreticide adı `/cli-test`altında).</span><span class="sxs-lookup"><span data-stu-id="ac8d0-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="ac8d0-186">Şuna benzer bir çözüm görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="ac8d0-187">Visual Studio 'yu kullanmayı önerdiğimiz öğreticide, tüm metin düzenleyiciyle oluşturulan C# kodu (iki proje) keşfedebilir ve oluşturulan konsol uygulamasını MacOS, Linux veya Windows makinesi ile `dotnet CLI` çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![CLı tarafından oluşturulan VS çözümü](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="ac8d0-189">Seri hale getirilmiş ML modeli (. zip dosyası) ve veri sınıfları (veri modelleri) içeren oluşturulmuş **sınıf kitaplığı** , doğrudan Son Kullanıcı uygulamanızda kullanabileceğiniz bir şeydir (ya da istediğiniz şekilde kodu taşıyarak). ).</span><span class="sxs-lookup"><span data-stu-id="ac8d0-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="ac8d0-190">Oluşturulan **konsol uygulaması** , gözden geçirmeniz gereken yürütme kodunu içerir ve ardından genellikle bu basit kodu (yalnızca birkaç satır) Son Kullanıcı uygulamanıza taşımak istediğiniz yere taşıyarak ' Puanlama kodu ' nu (tahmine dayalı hale getırmek için ml modelini çalıştıran kod) yeniden kullanırsınız. tahminleri yapın.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span> 

1. <span data-ttu-id="ac8d0-191">**ModelInput.cs** ve **ModelOutput.cs** sınıf dosyalarını sınıf kitaplığı projesi içinde açın.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="ac8d0-192">Bu sınıfların, verileri tutmak için kullanılan ' veri sınıfları ' veya POCO sınıfları olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="ac8d0-193">Bu, ' ortak kod ', ancak veri kümeniz yüzlerce veya hatta yüzlerce sütun içeriyorsa oluşturulmasını sağlamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span> 
    - <span data-ttu-id="ac8d0-194">`ModelInput` Sınıf, veri kümesinden verileri okurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-194">The `ModelInput` class is used when reading data from the dataset.</span></span> 
    - <span data-ttu-id="ac8d0-195">`ModelOutput` Sınıfı, tahmin sonucunu (tahmin verileri) almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="ac8d0-196">Program.cs dosyasını açın ve kodu araştırın.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="ac8d0-197">Yalnızca birkaç satırda modeli çalıştırabilir ve örnek bir tahmin yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

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

- <span data-ttu-id="ac8d0-198">Kodun ilk satırı, ml.NET kodunu her çalıştırdığınızda `MLContext` gereken bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span> 

- <span data-ttu-id="ac8d0-199">İkinci kod satırı, CLı aracı tarafından zaten eğitilen ve modelin seri hale getirilmiş olduğundan modeli eğmenize gerek olmadığı için yorumlandı. ZIP dosyası.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="ac8d0-200">Ancak CLı tarafından *"modelin eğitilme şekli"* ni görmek isterseniz, söz konusu satırın açıklamasını kaldırın ve söz konusu ml modeli için kullanılan eğitim kodunu çalıştırın/hata ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

- <span data-ttu-id="ac8d0-201">Üçüncü kod satırında modeli serileştirilmiş modelden yüklersiniz. Bu modelin yolunu sağlayarak `mlContext.Model.Load()` API ile ZIP dosyası. ZIP dosyası.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

- <span data-ttu-id="ac8d0-202">Yüklediğiniz dördüncü kod satırında, `PredictionEngine` `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API ile nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="ac8d0-203">Tek bir veri `PredictionEngine` örneğini (Bu durumda, kendi yaklaşımını tahmin etmek için tek bir metin parçası) hedefleyen bir tahmin oluşturmak istediğinizde nesneye ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

- <span data-ttu-id="ac8d0-204">Beşinci kod satırı, işlevi `CreateSingleDataSample()`çağırarak tahmin için kullanılacak *tek örnek verileri* oluşturduğunuz yerdir.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="ac8d0-205">CLı aracı ne tür örnek verileri kullanacağınızı bilmediğinden, bu işlev içinde veri kümesinin ilk satırını yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="ac8d0-206">Ancak bu durumda, bu işlevi uygulayan bu daha basit kodu güncelleştirerek `CreateSingleDataSample()` işlevin geçerli uygulaması yerine ' sabit kodlanmış ' verileri de oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. <span data-ttu-id="ac8d0-207">Veri kümesinin ilk satırından yüklenen özgün örnek verileri kullanarak ya da kendi özel sabit kodlanmış örnek verilerinizi sağlayarak projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="ac8d0-208">Şu şekilde bir tahmin almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-208">You should get a prediction comparable to:</span></span>

    # <a name="windowstabwindows"></a>[<span data-ttu-id="ac8d0-209">Windows</span><span class="sxs-lookup"><span data-stu-id="ac8d0-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="ac8d0-210">F5 tuşuna basarak (Play Button) konsol uygulamasını Visual Studio 'dan çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![PowerShell 'de ML.NET CLı otomatik eğitimi](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="ac8d0-212">)</span><span class="sxs-lookup"><span data-stu-id="ac8d0-212">)</span></span>

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="ac8d0-213">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="ac8d0-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="ac8d0-214">Aşağıdaki komutları yazarak konsol uygulamasını komut isteminden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-214">Run the console app from the command-prompt by typing the following commands:</span></span>

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![PowerShell 'de ML.NET CLı otomatik eğitimi](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="ac8d0-216">)</span><span class="sxs-lookup"><span data-stu-id="ac8d0-216">)</span></span>

    ---

1. <span data-ttu-id="ac8d0-217">Sabit kodlanmış örnek verileri farklı bir yaklaşım ile diğer cümleler ile değiştirmeyi deneyin ve modelin olumlu veya negatif yaklaşımı nasıl tahmin eder olduğunu görün.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span> 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="ac8d0-218">ML modeli tahminleri ile Son Kullanıcı uygulamalarınızı kullanın</span><span class="sxs-lookup"><span data-stu-id="ac8d0-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="ac8d0-219">Modeli son kullanıcı uygulamanızda çalıştırmak ve tahmin yapmak için benzer ' ML model Puanlama kodu ' kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span> 

<span data-ttu-id="ac8d0-220">Örneğin, bu kodu doğrudan **WPF** ve **WinForms** gibi herhangi bir Windows masaüstü uygulamasına taşıyabilir ve modeli konsol uygulamasında yapılmayla aynı şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="ac8d0-221">Bununla birlikte, bir ML modelini çalıştırmak için bu kod satırlarını uygulama yolu en iyi duruma gelmelidir (yani, model. zip dosyasını önbelleğe alır ve bir kez yükler) ve özellikle uygulamanızın ölçeklenebilir olması gerekiyorsa, her istekte bunları oluşturmak yerine tek nesneleri vardır. Aşağıdaki bölümde açıklandığı gibi bir Web uygulaması veya dağıtılmış hizmeti.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="ac8d0-222">Ölçeklenebilir ASP.NET Core Web uygulamaları ve Hizmetleri 'nde ML.NET modellerini çalıştırma (çok kanallı uygulamalar)</span><span class="sxs-lookup"><span data-stu-id="ac8d0-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="ac8d0-223">Model nesnesinin oluşturulması (`ITransformer` bir modelin. zip dosyasından yüklenir) `PredictionEngine` ve nesne özellikle ölçeklenebilir Web uygulamaları ve dağıtılmış hizmetler üzerinde çalışırken iyileştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="ac8d0-224">İlk durumda, model nesnesi (`ITransformer`) iyileştirmesi basittir.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="ac8d0-225">`ITransformer` Nesne iş parçacığı açısından güvenli olduğundan, modeli bir kez yüklemeniz için nesneyi tek veya statik bir nesne olarak önbelleğe alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="ac8d0-226">Nesne iş parçacığı açısından güvenli olmadığından `PredictionEngine` , ikinci nesne için nesnesi bu kadar kolay `PredictionEngine` değildir, bu nedenle bu nesneyi ASP.NET Core uygulamasında tek veya statik nesne olarak örnekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="ac8d0-227">Bu iş parçacığı güvenli ve ölçeklenebilirlik sorunu bu [blog gönderisine](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)göre ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

<span data-ttu-id="ac8d0-228">Ancak, bu blog gönderisinden açıklanamayan şeyler sizin için çok daha kolay.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="ac8d0-229">Sizin için daha basit bir yaklaşımda çalıştık ve uygulama ve hizmetASP.NET Core lerinize kolayca bir şekilde kullanabileceğiniz iyi bir **' .NET Core Integration Package '** oluşturdunuz, bu uygulamayı App dı Hizmetleri 'Ne (bağımlılık ekleme Hizmetleri) kaydederek ve doğrudan kodunuzda kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="ac8d0-230">Şunları yapmak için aşağıdaki öğreticiyi ve örneğe bakın:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="ac8d0-231">Öğretici: ML.NET modellerini ölçeklenebilir ASP.NET Core Web Apps ve WebAPIs üzerinde çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ac8d0-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="ac8d0-232">Örnekli ASP.NET Core WebAPI üzerinde ölçeklenebilir ML.NET modeli</span><span class="sxs-lookup"><span data-stu-id="ac8d0-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="ac8d0-233">"En iyi C# kalite" modelini eğitmek için kullanılan üretilen kodu keşfet</span><span class="sxs-lookup"><span data-stu-id="ac8d0-233">Explore the generated C# code that was used to train the "best quality" model</span></span> 

<span data-ttu-id="ac8d0-234">Daha gelişmiş öğrenme amaçlarıyla, oluşturulan modeli eğitebilmeniz için CLı C# aracı tarafından kullanılan oluşturulan kodu da keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="ac8d0-235">' Eğitim modeli kodu ' Şu anda adında `ModelBuilder` oluşturulan özel sınıfta oluşturulmuştur, böylece bu eğitim kodunu araştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="ac8d0-236">Daha önemlisi, bu senaryo (Yaklaşım Analizi modeli) için de, aşağıdaki öğreticide açıklanan kod ile bu üretilen eğitim kodunu karşılaştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="ac8d0-237">Karşılaştır [Öğretici: Bir yaklaşım Analizi ikili sınıflandırma senaryosunda](sentiment-analysis.md)ml.NET kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="ac8d0-238">Öğreticide seçilen algoritma ve işlem hattı yapılandırmasını CLı aracı tarafından oluşturulan kodla karşılaştırmak ilginç.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="ac8d0-239">Daha iyi modeller için ne kadar zaman harcadığınıza ve aradığınıza bağlı olarak, seçilen algoritma belirli Hyper-parametreleri ve işlem hattı yapılandırmasıyla birlikte farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac8d0-240">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac8d0-240">See also</span></span>

- [<span data-ttu-id="ac8d0-241">ML.NET CLı ile model eğitimi otomatikleştirin</span><span class="sxs-lookup"><span data-stu-id="ac8d0-241">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="ac8d0-242">Öğretici: ML.NET modellerini ölçeklenebilir ASP.NET Core Web Apps ve WebAPIs üzerinde çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ac8d0-242">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="ac8d0-243">Örnekli ASP.NET Core WebAPI üzerinde ölçeklenebilir ML.NET modeli</span><span class="sxs-lookup"><span data-stu-id="ac8d0-243">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="ac8d0-244">ML.NET CLı otomatik eğitme komut başvuru kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ac8d0-244">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="ac8d0-245">ML.NET komut satırı arabirimi (CLı) aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="ac8d0-245">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="ac8d0-246">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="ac8d0-246">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a><span data-ttu-id="ac8d0-247">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ac8d0-247">Next steps</span></span>

<span data-ttu-id="ac8d0-248">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="ac8d0-248">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="ac8d0-249">Verilerinizi seçilen ML görevi için hazırlayın (çözülme sorunu)</span><span class="sxs-lookup"><span data-stu-id="ac8d0-249">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="ac8d0-250">CLı aracında ' mlnet Auto-eğitme ' komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="ac8d0-250">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> - <span data-ttu-id="ac8d0-251">Kalite ölçümü sonuçlarını gözden geçirme</span><span class="sxs-lookup"><span data-stu-id="ac8d0-251">Review the quality metric results</span></span>
> - <span data-ttu-id="ac8d0-252">Modeli çalıştırmak için C# oluşturulan kodu anlayın (Son Kullanıcı uygulamanızda kullanılacak kod)</span><span class="sxs-lookup"><span data-stu-id="ac8d0-252">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="ac8d0-253">"En iyi C# kalite" modelini (öğrenme amaçları) eğitmek için kullanılan üretilen kodu keşfet</span><span class="sxs-lookup"><span data-stu-id="ac8d0-253">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac8d0-254">ML.NET CLı ile model eğitimi otomatikleştirin</span><span class="sxs-lookup"><span data-stu-id="ac8d0-254">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
