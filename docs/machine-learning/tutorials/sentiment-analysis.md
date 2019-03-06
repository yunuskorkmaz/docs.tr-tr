---
title: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu
description: ML.NET ikili sınıflandırma senaryoda yaklaşım tahmin uygun eylemde için nasıl kullanılacağını anlamak için nasıl kullanılacağını keşfedin.
ms.date: 03/01/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 854330614713a6e05a47b3833634907027bda267
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368330"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="99afe-103">Öğretici: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu</span><span class="sxs-lookup"><span data-stu-id="99afe-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

<span data-ttu-id="99afe-104">Bu örnek öğretici, C# kullanarak Visual Studio 2017'de .NET Core konsol uygulaması aracılığıyla bir yaklaşım sınıflandırıcı oluşturma ML.NET kullanılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99afe-104">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

> [!NOTE]
> <span data-ttu-id="99afe-105">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="99afe-105">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="99afe-106">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="99afe-106">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="99afe-107">Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="99afe-107">This tutorial and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="99afe-108">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="99afe-108">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="99afe-109">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="99afe-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="99afe-110">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="99afe-110">Understand the problem</span></span>
> * <span data-ttu-id="99afe-111">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="99afe-111">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="99afe-112">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="99afe-112">Prepare your data</span></span>
> * <span data-ttu-id="99afe-113">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="99afe-113">Transform the data</span></span>
> * <span data-ttu-id="99afe-114">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="99afe-114">Train the model</span></span>
> * <span data-ttu-id="99afe-115">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="99afe-115">Evaluate the model</span></span>
> * <span data-ttu-id="99afe-116">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="99afe-116">Predict with the trained model</span></span>
> * <span data-ttu-id="99afe-117">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="99afe-117">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="99afe-118">Yaklaşım analizi örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="99afe-118">Sentiment analysis sample overview</span></span>

<span data-ttu-id="99afe-119">Örnek ML.NET sınıflandırır ve yaklaşım artı veya eksi olarak tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="99afe-119">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="99afe-120">Ayrıca, kalite analizi için ikinci bir veri kümesi modeliyle değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="99afe-120">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="99afe-121">Yaklaşım veri kümeleri WikiDetox projeden ' dir.</span><span class="sxs-lookup"><span data-stu-id="99afe-121">The sentiment datasets are from the WikiDetox project.</span></span>

<span data-ttu-id="99afe-122">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="99afe-122">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99afe-123">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="99afe-123">Prerequisites</span></span>

* <span data-ttu-id="99afe-124">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="99afe-124">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="99afe-125">[Wikipedia detox satır veri sekmeyle ayrılmış dosya (wikiPedia-detox-250-satırı-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="99afe-125">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="99afe-126">[Wikipedia detox satır test sekmeyle ayrılmış dosya (wikipedia-detox-250-satırı-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="99afe-126">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="99afe-127">Machine learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="99afe-127">Machine learning workflow</span></span>

<span data-ttu-id="99afe-128">Bu öğreticide, bir makine öğrenimi düzenli bir şekilde taşımak işlem sağlayan bir iş akışı izler.</span><span class="sxs-lookup"><span data-stu-id="99afe-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="99afe-129">İş akışı aşamalar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="99afe-129">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="99afe-130">**Sorunu anlama**</span><span class="sxs-lookup"><span data-stu-id="99afe-130">**Understand the problem**</span></span>
2. <span data-ttu-id="99afe-131">**Verilerinizi hazırlama**</span><span class="sxs-lookup"><span data-stu-id="99afe-131">**Prepare your data**</span></span>
   * <span data-ttu-id="99afe-132">**Verileri yükleme**</span><span class="sxs-lookup"><span data-stu-id="99afe-132">**Load the data**</span></span>
   * <span data-ttu-id="99afe-133">**Özellikler (verilerinizi dönüştürmek) ayıklayın**</span><span class="sxs-lookup"><span data-stu-id="99afe-133">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="99afe-134">**Derleme ve eğitme**</span><span class="sxs-lookup"><span data-stu-id="99afe-134">**Build and train**</span></span> 
   * <span data-ttu-id="99afe-135">**Modeli eğitme**</span><span class="sxs-lookup"><span data-stu-id="99afe-135">**Train the model**</span></span>
   * <span data-ttu-id="99afe-136">**Modeli değerlendirme**</span><span class="sxs-lookup"><span data-stu-id="99afe-136">**Evaluate the model**</span></span>
4. <span data-ttu-id="99afe-137">**Model dağıtma**</span><span class="sxs-lookup"><span data-stu-id="99afe-137">**Deploy Model**</span></span>
   * <span data-ttu-id="99afe-138">**Tahmin modelini kullanın**</span><span class="sxs-lookup"><span data-stu-id="99afe-138">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="99afe-139">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="99afe-139">Understand the problem</span></span>

<span data-ttu-id="99afe-140">Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="99afe-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="99afe-141">Sorun bozucu, tahmin edin ve sonuçları değerlendirin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="99afe-141">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="99afe-142">Sorun Bu öğretici için uygun eylemi gerçekleştirin gelen Web sitesi açıklama yaklaşım öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="99afe-142">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="99afe-143">Problemi yaklaşım metin ve duyarlılık değeri ile modeli eğitmek için istediğiniz verileri için ve tahmin edilen duyarlılık değeri değerlendirmek ve işletimsel olarak kullanmak dökümünü alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99afe-143">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="99afe-144">Ardından gerek **belirlemek** yaklaşımı, Görev Seçimi öğrenme makineyle yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="99afe-144">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="99afe-145">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="99afe-145">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="99afe-146">Bu sorun aşağıdaki gerçekleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="99afe-146">With this problem, you know the following facts:</span></span>

<span data-ttu-id="99afe-147">Eğitim verileri: Web sitesi açıklamaları toxic olabilir (1) olmadığını (0) toxic (**yaklaşım**).</span><span class="sxs-lookup"><span data-stu-id="99afe-147">Training data: website comments can be toxic (1) or not toxic (0) (**sentiment**).</span></span>
<span data-ttu-id="99afe-148">Tahmin **yaklaşım** açıklamasının bir yeni Web sitesi, toxic veya değil toxic, gibi aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="99afe-148">Predict the **sentiment** of a new website comment, either toxic or not toxic, such as in the following examples:</span></span>

* <span data-ttu-id="99afe-149">Lütfen anlamsız Wikipedia için makalelerinizde.</span><span class="sxs-lookup"><span data-stu-id="99afe-149">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="99afe-150">Kendisi için en iyi yöntemdir ve makale, yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99afe-150">He is the best, and the article should say that.</span></span>

<span data-ttu-id="99afe-151">Sınıflandırma makine öğrenimi algoritmasının bu senaryo için idealdir.</span><span class="sxs-lookup"><span data-stu-id="99afe-151">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="99afe-152">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="99afe-152">About the classification task</span></span>

<span data-ttu-id="99afe-153">Sınıflandırma olan verileri kullanan bir machine learning algoritmasını **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="99afe-153">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="99afe-154">Örneğin, sınıflandırma için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99afe-154">For example, you can use classification to:</span></span>

* <span data-ttu-id="99afe-155">Artı veya eksi olarak duyguları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="99afe-155">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="99afe-156">E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.</span><span class="sxs-lookup"><span data-stu-id="99afe-156">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="99afe-157">Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="99afe-157">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="99afe-158">Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.</span><span class="sxs-lookup"><span data-stu-id="99afe-158">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="99afe-159">Sınıflandırma algoritmaları sık aşağıdaki türlerden biri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="99afe-159">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="99afe-160">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="99afe-160">Binary: either A or B.</span></span>
* <span data-ttu-id="99afe-161">Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="99afe-161">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="99afe-162">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="99afe-162">Create a console application</span></span>

1. <span data-ttu-id="99afe-163">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="99afe-163">Open Visual Studio 2017.</span></span> <span data-ttu-id="99afe-164">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="99afe-164">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="99afe-165">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="99afe-165">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="99afe-166">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="99afe-166">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="99afe-167">İçinde **adı** metin kutusuna "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99afe-167">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="99afe-168">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="99afe-168">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="99afe-169">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="99afe-169">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="99afe-170">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="99afe-170">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="99afe-171">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="99afe-171">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="99afe-172">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="99afe-172">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="99afe-173">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99afe-173">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="99afe-174">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="99afe-174">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="99afe-175">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="99afe-175">Prepare your data</span></span>

1. <span data-ttu-id="99afe-176">İndirme [Wikipedia detox-250-satırı-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) ve [wikipedia-detox-250-satırı-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="99afe-176">Download the [Wikipedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="99afe-177">İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99afe-177">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="99afe-178">Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="99afe-178">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="99afe-179">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="99afe-179">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="99afe-180">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="99afe-180">Create classes and define paths</span></span>

<span data-ttu-id="99afe-181">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="99afe-181">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="99afe-182">Kısa bir süre önce indirilen dosyaları ve bir genel değişken için yollar tutmak için üç genel alanlar oluşturmak için ihtiyacınız `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="99afe-182">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="99afe-183">`_trainDataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="99afe-183">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="99afe-184">`_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="99afe-184">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="99afe-185">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="99afe-185">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="99afe-186">`_textLoader` olan <xref:Microsoft.ML.Data.TextLoader> yüklemek ve veri kümeleri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99afe-186">`_textLoader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="99afe-187">Satır sağ aşağıdaki kodu ekleyin `Main` bu yollarını belirtmek için yöntemi ve `_textLoader` değişkeni:</span><span class="sxs-lookup"><span data-stu-id="99afe-187">Add the following code to the line right above the `Main` method to specify those paths and the `_textLoader` variable:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

<span data-ttu-id="99afe-188">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99afe-188">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="99afe-189">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="99afe-189">Add a new class to your project:</span></span>

1. <span data-ttu-id="99afe-190">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="99afe-190">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="99afe-191">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="99afe-191">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="99afe-192">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99afe-192">Then, select the **Add** button.</span></span>

    <span data-ttu-id="99afe-193">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="99afe-193">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="99afe-194">Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="99afe-194">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="99afe-195">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="99afe-195">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="99afe-196">`SentimentData` Giriş veri kümesi sınıfı ve bir `float` (`Sentiment`) pozitif veya negatif yaklaşım için bir değer ve bir dize yorumu için olan (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="99afe-196">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="99afe-197">Her iki alanınız `Column` öznitelikleri kendisine bağlı.</span><span class="sxs-lookup"><span data-stu-id="99afe-197">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="99afe-198">Bu öznitelik her bir alanın veri dosyası ve olduğu siparişi açıklayan `Label` alan.</span><span class="sxs-lookup"><span data-stu-id="99afe-198">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="99afe-199">`SentimentPrediction` eğitilen modelin sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99afe-199">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="99afe-200">Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="99afe-200">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="99afe-201">`Label` Oluşturup modeli ya da onun da model değerlendirmek için ikinci bir veri kümesi ile kullanılan eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99afe-201">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="99afe-202">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99afe-202">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="99afe-203">Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99afe-203">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="99afe-204">ML.NET modeliyle oluştururken oluşturarak başlayın bir `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="99afe-204">When building a model with ML.NET you start by creating an `MLContext`.</span></span> <span data-ttu-id="99afe-205">Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="99afe-205">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="99afe-206">Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilecek ML işiniz için bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="99afe-206">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="99afe-207">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="99afe-207">Initialize variables in Main</span></span>

<span data-ttu-id="99afe-208">Adlı bir değişken oluşturma `mlContext` ve yeni bir örneğini ile başlatma `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="99afe-208">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="99afe-209">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-209">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="99afe-210">Sonra Kurulum başlatma veri yükleme için `_textLoader` yeniden kullanmak için genel değişkeni.</span><span class="sxs-lookup"><span data-stu-id="99afe-210">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span>  <span data-ttu-id="99afe-211">Oluşturduğunuzda, bir `TextLoader` kullanarak `MLContext.Data.CreateTextLoader`, gerekli bağlamı geçirdiğiniz ve <xref:Microsoft.ML.Data.TextLoader.Arguments> özelleştirme sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="99afe-211">When you create a `TextLoader` using  `MLContext.Data.CreateTextLoader`, you pass in the context needed and the <xref:Microsoft.ML.Data.TextLoader.Arguments> class which enables customization.</span></span>

 <span data-ttu-id="99afe-212">Bir dizi geçirerek veri şemasını belirtin <xref:Microsoft.ML.Data.TextLoader.Column> tüm sütun adlarını ve türlerini içeren yükleyicisi nesneleri.</span><span class="sxs-lookup"><span data-stu-id="99afe-212">Specify the data schema by passing an array of <xref:Microsoft.ML.Data.TextLoader.Column> objects to the loader containing all the column names and their types.</span></span> <span data-ttu-id="99afe-213">Oluşturduğunuz zaman veri şemasını önceden tanımlanmış bizim `SentimentData` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="99afe-213">You defined the data schema previously when you created our `SentimentData` class.</span></span> <span data-ttu-id="99afe-214">İlk sütun (etiketi) bizim şema için olan bir <xref:System.Boolean> (tahmin) ve ikinci sütun (SentimentText) türü metin/dizesi yaklaşımını tahminde için kullanılan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="99afe-214">For our schema, the first column (Label) is a <xref:System.Boolean> (the prediction) and the second column (SentimentText) is the feature of type text/string used for predicting the sentiment.</span></span>
<span data-ttu-id="99afe-215">`TextLoader` Sınıf tam olarak başlatılmış döndürür <xref:Microsoft.ML.Data.TextLoader></span><span class="sxs-lookup"><span data-stu-id="99afe-215">The `TextLoader` class returns a fully initialized <xref:Microsoft.ML.Data.TextLoader></span></span>  

<span data-ttu-id="99afe-216">Başlatmak için `_textLoader` gerekli veri kümeleri için yeniden kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:</span><span class="sxs-lookup"><span data-stu-id="99afe-216">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextLoader")]

<span data-ttu-id="99afe-217">Sonraki kod satırı olarak ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-217">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

<span data-ttu-id="99afe-218">`Train` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="99afe-218">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="99afe-219">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="99afe-219">Loads the data.</span></span>
* <span data-ttu-id="99afe-220">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="99afe-220">Extracts and transforms the data.</span></span>
* <span data-ttu-id="99afe-221">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="99afe-221">Trains the model.</span></span>
* <span data-ttu-id="99afe-222">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="99afe-222">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="99afe-223">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="99afe-223">Returns the model.</span></span>

<span data-ttu-id="99afe-224">Oluşturma `Train` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-224">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="99afe-225">İki parametre Train yönteme geçirilen dikkat edin; bir `MLContext` bağlamının (`mlContext`) ve <xref:System.String> veri kümesi yolu için (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="99afe-225">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and a <xref:System.String> for the dataset path (`dataPath`).</span></span> <span data-ttu-id="99afe-226">Eğitim ve test için bu yöntemi birden çok kez kullanın dağıtacağız.</span><span class="sxs-lookup"><span data-stu-id="99afe-226">You're going to use this method more than once for training and testing.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="99afe-227">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="99afe-227">Load the data</span></span>

<span data-ttu-id="99afe-228">Kullanarak verileri yüklemek `_textLoader` genel değişkenin `dataPath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="99afe-228">You'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="99afe-229">Döndürür bir <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="99afe-229">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> <span data-ttu-id="99afe-230">Giriş ve çıkış olarak `Transforms`, `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="99afe-230">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="99afe-231">ML.NET veriler SQL görünümüne benzer.</span><span class="sxs-lookup"><span data-stu-id="99afe-231">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="99afe-232">Bu, gevşek değerlendirilen, şema ve heterojen olur.</span><span class="sxs-lookup"><span data-stu-id="99afe-232">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="99afe-233">Nesne, işlem hattını ilk kısmı ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="99afe-233">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="99afe-234">Bu öğreticide, açıklama ve karşılık gelen toxic veya olmayan toxic yaklaşım bir veri kümesine yükler.</span><span class="sxs-lookup"><span data-stu-id="99afe-234">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="99afe-235">Bu model oluşturmayı ve bunu eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99afe-235">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="99afe-236">İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-236">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="99afe-237">Verileri dönüştürme ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="99afe-237">Extract and transform the data</span></span>

<span data-ttu-id="99afe-238">Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="99afe-238">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="99afe-239">Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="99afe-239">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="99afe-240">Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="99afe-240">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="99afe-241">ML. NET dönüştürme işlem hatları, verilerinizi, eğitim veya test etmeden önce uygulanan dönüştürmeler özel bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="99afe-241">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="99afe-242">Veri Dönüşümleri birincil amacı olan [özellik kazandırma sayesinde](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="99afe-242">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="99afe-243">Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) metinsel verilerimizi ML algoritmalarınızı tanıyacak bir biçime dönüştürmek için sonraki adım, bu nedenle veri.</span><span class="sxs-lookup"><span data-stu-id="99afe-243">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="99afe-244">Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="99afe-244">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="99afe-245">Ardından, arama `mlContext.Transforms.Text.FeaturizeText` hangi featurizes metin sütununu (`SentimentText`) adı verilen sayısal bir vektör sütununa `Features` makine öğrenimi algoritması tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="99afe-245">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="99afe-246">Bu döndüren bir sarmalayıcı çağrısı, bir <xref:Microsoft.ML.Data.EstimatorChain%601> bir işlem hattı etkin olacak.</span><span class="sxs-lookup"><span data-stu-id="99afe-246">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="99afe-247">Bu ad `pipeline` eğitmen için ardından ekleyeceği şekilde `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="99afe-247">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="99afe-248">Bu, sonraki kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="99afe-248">Add this as the next line of code:</span></span>

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

>[!WARNING]
> <span data-ttu-id="99afe-249">ML.NET sürüm 0.10 dönüştürme parametreleri sırası değişti.</span><span class="sxs-lookup"><span data-stu-id="99afe-249">ML.NET Version 0.10 has changed the order of the Transform parameters.</span></span> <span data-ttu-id="99afe-250">Bu, kullanıma alma hatası kadar uygulamayı çalıştırın ve model derleme.</span><span class="sxs-lookup"><span data-stu-id="99afe-250">This will not error out until you run the application and build the model.</span></span> <span data-ttu-id="99afe-251">Dönüşümlerin parametre adları, önceki kod parçacığında gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="99afe-251">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="99afe-252">Bu ön işleme/özellik kazandırma sayesinde adımdır.</span><span class="sxs-lookup"><span data-stu-id="99afe-252">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="99afe-253">ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99afe-253">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="99afe-254">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="99afe-254">Choose a learning algorithm</span></span>

<span data-ttu-id="99afe-255">Eğitmen eklemek için çağrı `mlContext.Transforms.Text.FeaturizeText` döndüren sarmalayıcı yöntemini bir <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> nesne.</span><span class="sxs-lookup"><span data-stu-id="99afe-255">To add the trainer, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="99afe-256">Bu işlem hattında kullanacağınız karar ağacı learner budur.</span><span class="sxs-lookup"><span data-stu-id="99afe-256">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="99afe-257">`FastTreeBinaryClassificationTrainer` Eklenir `pipeline` ve özellikleri tespit `SentimentText` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="99afe-257">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="99afe-258">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-258">Add the following code to the `Train` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="99afe-259">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="99afe-259">Train the model</span></span>

<span data-ttu-id="99afe-260">Modeli eğitme <xref:Microsoft.ML.Data.TransformerChain%601>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="99afe-260">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="99afe-261">Tahmin tanımlandıktan sonra kullanarak modelinize eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> zaten yüklenmiş eğitim verilerini sağlayarak.</span><span class="sxs-lookup"><span data-stu-id="99afe-261">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> while providing the already loaded training data.</span></span> <span data-ttu-id="99afe-262">Bu tahminler elde etmek için kullanılacak bir modelini döndürür.</span><span class="sxs-lookup"><span data-stu-id="99afe-262">This returns a model to use for predictions.</span></span> <span data-ttu-id="99afe-263">`pipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi.</span><span class="sxs-lookup"><span data-stu-id="99afe-263">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="99afe-264">Denemeyi böyle kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="99afe-264">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="99afe-265">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-265">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="99afe-266">Kaydet ve değerlendirme için kullanılacak modeli eğitilir dön</span><span class="sxs-lookup"><span data-stu-id="99afe-266">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="99afe-267">Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain%601> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine.</span><span class="sxs-lookup"><span data-stu-id="99afe-267">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="99afe-268">Model sonunda dönüş `Train` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99afe-268">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="99afe-269">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="99afe-269">Evaluate the model</span></span>

<span data-ttu-id="99afe-270">Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="99afe-270">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="99afe-271">İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `Train` değerlendirilecek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="99afe-271">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="99afe-272">Oluşturma `Evaluate` yöntemi hemen sonrasına `Train`, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="99afe-272">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="99afe-273">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="99afe-273">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="99afe-274">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="99afe-274">Loads the test dataset.</span></span>
* <span data-ttu-id="99afe-275">İkili değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99afe-275">Creates the binary evaluator.</span></span>
* <span data-ttu-id="99afe-276">Model değerlendirir ve metrikleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="99afe-276">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="99afe-277">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="99afe-277">Displays the metrics.</span></span>

<span data-ttu-id="99afe-278">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-278">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

<span data-ttu-id="99afe-279">Daha önce başlatılmış kullanarak test veri kümesini yük `_textLoader` genel değişkenin `_testDataPath` genel alan.</span><span class="sxs-lookup"><span data-stu-id="99afe-279">You'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="99afe-280">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="99afe-280">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="99afe-281">Aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-281">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

<span data-ttu-id="99afe-282">Ardından, makine öğrenimi kullanacağınız `model` özellikleri giriş ve tahmin döndürmek için parametre (dönüştürücü).</span><span class="sxs-lookup"><span data-stu-id="99afe-282">Next, you'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="99afe-283">Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-283">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

<span data-ttu-id="99afe-284">`BinaryClassificationContext.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma.</span><span class="sxs-lookup"><span data-stu-id="99afe-284">The `BinaryClassificationContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="99afe-285">Döndürür bir `BinaryClassificationEvaluator.CalibratedResult` nesne ikili sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="99afe-285">It returns a `BinaryClassificationEvaluator.CalibratedResult` object contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="99afe-286">Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99afe-286">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="99afe-287">Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-287">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="99afe-288">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="99afe-288">Displaying the metrics for model validation</span></span>

<span data-ttu-id="99afe-289">Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="99afe-289">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

<span data-ttu-id="99afe-290">Modelinizi dönmeden önce bir .zip dosyası olarak kaydetmek için çağırmak için aşağıdaki kodu ekleyin. `SaveModelAsFile` yöntemi olarak bir sonraki satırda `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="99afe-290">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="99afe-291">Modeli a.zip dosyası olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="99afe-291">Save the model as a.zip file</span></span>

<span data-ttu-id="99afe-292">Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-292">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="99afe-293">`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="99afe-293">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="99afe-294">Model bir .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="99afe-294">Saves the model as a .zip file.</span></span>

<span data-ttu-id="99afe-295">Ardından, yeniden kullanılabilir ve diğer uygulamalarda kullanılan model kaydetmek için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="99afe-295">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="99afe-296">`ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="99afe-296">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="99afe-297">Bu zip dosyası olarak kaydetmek için oluşturacağınız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99afe-297">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="99afe-298">Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-298">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]
<span data-ttu-id="99afe-299">Dağıtma ve tahmin da görüntü bir konsol iletisi ile yazarak dosyasının nerede yazılmıştır yüklenen modeliyle `_modelPath`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-299">Deploy and Predict with a loaded model You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="99afe-300">Kaydedilen modeli ile test veri sonucu tahmin edin</span><span class="sxs-lookup"><span data-stu-id="99afe-300">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="99afe-301">Oluşturma `Predict` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-301">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="99afe-302">`Predict` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="99afe-302">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="99afe-303">Test verilerini tek bir yorum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99afe-303">Creates a single comment of test data.</span></span>
* <span data-ttu-id="99afe-304">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="99afe-304">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="99afe-305">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="99afe-305">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="99afe-306">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="99afe-306">Displays the predicted results.</span></span>

<span data-ttu-id="99afe-307">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-307">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

<span data-ttu-id="99afe-308">Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="99afe-308">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="99afe-309"><xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99afe-309">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="99afe-310">Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` ilk satırı olarak `Predict` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-310">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionEngine")]
  
<span data-ttu-id="99afe-311">Eğitilen modelin tahmine test etmek için bir açıklama ekleyin `Predict` bir örneğini oluşturarak yöntemi `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="99afe-311">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]

 <span data-ttu-id="99afe-312">Bu açıklama verilerini tek bir örneğini Toxic veya olmayan Toxic duyarlılığını tahmin etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99afe-312">You can use that to predict the Toxic or Non Toxic sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="99afe-313">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="99afe-313">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="99afe-314">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="99afe-314">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="99afe-315">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="99afe-315">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="99afe-316">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="99afe-316">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="using-the-model-prediction"></a><span data-ttu-id="99afe-317">Modeli kullanılarak: tahmin</span><span class="sxs-lookup"><span data-stu-id="99afe-317">Using the model: prediction</span></span>

<span data-ttu-id="99afe-318">Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için.</span><span class="sxs-lookup"><span data-stu-id="99afe-318">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="99afe-319">Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="99afe-319">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="99afe-320">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="99afe-320">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="99afe-321">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="99afe-321">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="99afe-322">Oluşturma `PredictWithModelLoadedFromFile` yöntemi hemen önce `SaveModelAsFile` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-322">Create the `PredictWithModelLoadedFromFile` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

<span data-ttu-id="99afe-323">`PredictWithModelLoadedFromFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="99afe-323">The `PredictWithModelLoadedFromFile` method executes the following tasks:</span></span>

* <span data-ttu-id="99afe-324">Toplu test verilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99afe-324">Creates batch test data.</span></span>
* <span data-ttu-id="99afe-325">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="99afe-325">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="99afe-326">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="99afe-326">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="99afe-327">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="99afe-327">Displays the predicted results.</span></span>

<span data-ttu-id="99afe-328">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Predict` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="99afe-328">Add a call to the new method from the `Main` method, right under the `Predict` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

<span data-ttu-id="99afe-329">Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `PredictWithModelLoadedFromFile` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-329">Add some comments to test the trained model's predictions in the `PredictWithModelLoadedFromFile` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

<span data-ttu-id="99afe-330">Model yüklenemiyor</span><span class="sxs-lookup"><span data-stu-id="99afe-330">Load the model</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

<span data-ttu-id="99afe-331">Bir modeliniz olduğuna göre yorum kullanarak veri Toxic veya olmayan Toxic yaklaşım tahmin etmek için kullanabileceğiniz <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99afe-331">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="99afe-332">Bir öngörü almak için kullanın `Predict` yeni veriler.</span><span class="sxs-lookup"><span data-stu-id="99afe-332">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="99afe-333">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="99afe-333">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="99afe-334">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="99afe-334">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="99afe-335">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="99afe-335">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="99afe-336">Aşağıdaki kodu ekleyin `PredictWithModelLoadedFromFile` yöntemi tahminler elde etmek için:</span><span class="sxs-lookup"><span data-stu-id="99afe-336">Add the following code to the `PredictWithModelLoadedFromFile` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="99afe-337">Tahmin için yüklenen modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="99afe-337">Using the loaded model for prediction</span></span>

<span data-ttu-id="99afe-338">Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için.</span><span class="sxs-lookup"><span data-stu-id="99afe-338">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="99afe-339">Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="99afe-339">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="99afe-340">Aşağıdakileri kullanarak sonuçları için bir başlık oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="99afe-340">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

<span data-ttu-id="99afe-341">Tahmin edilen sonuçlarını görüntülemeden önce yaklaşımını ve özgün açıklamayı, tahmin edilen yaklaşım ile birlikte görmek için tahmini birleştirin.</span><span class="sxs-lookup"><span data-stu-id="99afe-341">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="99afe-342">Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A> gerçekleşen, yapmanız gereken yöntemini bu nedenle bu kodunu ekleyin sonraki:</span><span class="sxs-lookup"><span data-stu-id="99afe-342">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="99afe-343">Birleştirilmiş göre `SentimentText` ve `Sentiment` bir sınıf kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99afe-343">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

<span data-ttu-id="99afe-344">C# 7.0 C# 7.1 ve projenin varsayılan dil sürümü yeni bir özellik olan demet öğesi adları olan olayla olduğundan, C# 7.1 veya üzeri dil sürümünü değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="99afe-344">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="99afe-345">Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="99afe-345">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="99afe-346">Seçin **derleme** sekmenize **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99afe-346">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="99afe-347">Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm).</span><span class="sxs-lookup"><span data-stu-id="99afe-347">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="99afe-348">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="99afe-348">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="99afe-349">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="99afe-349">Results</span></span>

<span data-ttu-id="99afe-350">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99afe-350">Your results should be similar to the following.</span></span> <span data-ttu-id="99afe-351">İşlem hattı işlediği gibi iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="99afe-351">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="99afe-352">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99afe-352">You may see warnings, or processing messages.</span></span> <span data-ttu-id="99afe-353">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="99afe-353">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of loaded model with a multiple sample ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: I love this article. | Prediction: Not Toxic | Probability: 0.09454837

```

<span data-ttu-id="99afe-354">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="99afe-354">Congratulations!</span></span> <span data-ttu-id="99afe-355">Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="99afe-355">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="99afe-356">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="99afe-356">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="99afe-357">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="99afe-357">Next steps</span></span>

<span data-ttu-id="99afe-358">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="99afe-358">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="99afe-359">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="99afe-359">Understand the problem</span></span>
> * <span data-ttu-id="99afe-360">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="99afe-360">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="99afe-361">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="99afe-361">Prepare your data</span></span>
> * <span data-ttu-id="99afe-362">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="99afe-362">Transform the data</span></span>
> * <span data-ttu-id="99afe-363">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="99afe-363">Train the model</span></span>
> * <span data-ttu-id="99afe-364">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="99afe-364">Evaluate the model</span></span>
> * <span data-ttu-id="99afe-365">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="99afe-365">Predict with the trained model</span></span>
> * <span data-ttu-id="99afe-366">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="99afe-366">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="99afe-367">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="99afe-367">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="99afe-368">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="99afe-368">Issue Classification</span></span>](github-issue-classification.md)
