---
title: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu
description: ML.NET ikili sınıflandırma senaryoda yaklaşım tahmin uygun eylemde için nasıl kullanılacağını anlamak için nasıl kullanılacağını keşfedin.
ms.date: 02/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 9afdf1d8369e71f9614ebc2bf327e98d31b988ff
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748394"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="48ffa-103">Öğretici: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu</span><span class="sxs-lookup"><span data-stu-id="48ffa-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="48ffa-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="48ffa-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="48ffa-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="48ffa-106">Bu örnek öğretici, C# kullanarak Visual Studio 2017'de .NET Core konsol uygulaması aracılığıyla bir yaklaşım sınıflandırıcı oluşturma ML.NET kullanılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="48ffa-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="48ffa-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="48ffa-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="48ffa-108">Understand the problem</span></span>
> * <span data-ttu-id="48ffa-109">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="48ffa-109">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="48ffa-110">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="48ffa-110">Prepare your data</span></span>
> * <span data-ttu-id="48ffa-111">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="48ffa-111">Transform the data</span></span>
> * <span data-ttu-id="48ffa-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="48ffa-112">Train the model</span></span>
> * <span data-ttu-id="48ffa-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="48ffa-113">Evaluate the model</span></span>
> * <span data-ttu-id="48ffa-114">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="48ffa-114">Predict with the trained model</span></span>
> * <span data-ttu-id="48ffa-115">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="48ffa-115">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="48ffa-116">Yaklaşım analizi örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="48ffa-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="48ffa-117">Örnek ML.NET sınıflandırır ve yaklaşım artı veya eksi olarak tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="48ffa-118">Ayrıca, kalite analizi için ikinci bir veri kümesi modeliyle değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="48ffa-119">Yaklaşım veri kümeleri WikiDetox projeden ' dir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-119">The sentiment datasets are from the WikiDetox project.</span></span>

<span data-ttu-id="48ffa-120">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="48ffa-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48ffa-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="48ffa-121">Prerequisites</span></span>

* <span data-ttu-id="48ffa-122">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="48ffa-123">[Wikipedia detox satır veri sekmeyle ayrılmış dosya (wikiPedia-detox-250-satırı-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="48ffa-123">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="48ffa-124">[Wikipedia detox satır test sekmeyle ayrılmış dosya (wikipedia-detox-250-satırı-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="48ffa-124">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="48ffa-125">Machine learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="48ffa-125">Machine learning workflow</span></span>

<span data-ttu-id="48ffa-126">Bu öğreticide, bir makine öğrenimi düzenli bir şekilde taşımak işlem sağlayan bir iş akışı izler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="48ffa-127">İş akışı aşamalar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="48ffa-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="48ffa-128">**Sorunu anlama**</span><span class="sxs-lookup"><span data-stu-id="48ffa-128">**Understand the problem**</span></span>
2. <span data-ttu-id="48ffa-129">**Verilerinizi hazırlama**</span><span class="sxs-lookup"><span data-stu-id="48ffa-129">**Prepare your data**</span></span>
   * <span data-ttu-id="48ffa-130">**Verileri yükleme**</span><span class="sxs-lookup"><span data-stu-id="48ffa-130">**Load the data**</span></span>
   * <span data-ttu-id="48ffa-131">**Özellikler (verilerinizi dönüştürmek) ayıklayın**</span><span class="sxs-lookup"><span data-stu-id="48ffa-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="48ffa-132">**Derleme ve eğitme**</span><span class="sxs-lookup"><span data-stu-id="48ffa-132">**Build and train**</span></span> 
   * <span data-ttu-id="48ffa-133">**Modeli eğitme**</span><span class="sxs-lookup"><span data-stu-id="48ffa-133">**Train the model**</span></span>
   * <span data-ttu-id="48ffa-134">**Modeli değerlendirme**</span><span class="sxs-lookup"><span data-stu-id="48ffa-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="48ffa-135">**Model dağıtma**</span><span class="sxs-lookup"><span data-stu-id="48ffa-135">**Deploy Model**</span></span>
   * <span data-ttu-id="48ffa-136">**Tahmin modelini kullanın**</span><span class="sxs-lookup"><span data-stu-id="48ffa-136">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="48ffa-137">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="48ffa-137">Understand the problem</span></span>

<span data-ttu-id="48ffa-138">Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="48ffa-139">Sorun bozucu, tahmin edin ve sonuçları değerlendirin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-139">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="48ffa-140">Sorun Bu öğretici için uygun eylemi gerçekleştirin gelen Web sitesi açıklama yaklaşım öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-140">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="48ffa-141">Problemi yaklaşım metin ve duyarlılık değeri ile modeli eğitmek için istediğiniz verileri için ve tahmin edilen duyarlılık değeri değerlendirmek ve işletimsel olarak kullanmak dökümünü alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48ffa-141">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="48ffa-142">Ardından gerek **belirlemek** yaklaşımı, Görev Seçimi öğrenme makineyle yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="48ffa-142">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="48ffa-143">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="48ffa-143">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="48ffa-144">Bu sorun aşağıdaki gerçekleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="48ffa-144">With this problem, you know the following facts:</span></span>

<span data-ttu-id="48ffa-145">Eğitim verileri: Web sitesi açıklamaları toxic olabilir (1) olmadığını (0) toxic (**yaklaşım**).</span><span class="sxs-lookup"><span data-stu-id="48ffa-145">Training data: website comments can be toxic (1) or not toxic (0) (**sentiment**).</span></span>
<span data-ttu-id="48ffa-146">Tahmin **yaklaşım** açıklamasının bir yeni Web sitesi, toxic veya değil toxic, gibi aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="48ffa-146">Predict the **sentiment** of a new website comment, either toxic or not toxic, such as in the following examples:</span></span>

* <span data-ttu-id="48ffa-147">Lütfen anlamsız Wikipedia için makalelerinizde.</span><span class="sxs-lookup"><span data-stu-id="48ffa-147">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="48ffa-148">Kendisi için en iyi yöntemdir ve makale, yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-148">He is the best, and the article should say that.</span></span>

<span data-ttu-id="48ffa-149">Sınıflandırma makine öğrenimi algoritmasının bu senaryo için idealdir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-149">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="48ffa-150">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="48ffa-150">About the classification task</span></span>

<span data-ttu-id="48ffa-151">Sınıflandırma olan verileri kullanan bir machine learning algoritmasını **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="48ffa-151">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="48ffa-152">Örneğin, sınıflandırma için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="48ffa-152">For example, you can use classification to:</span></span>

* <span data-ttu-id="48ffa-153">Artı veya eksi olarak duyguları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="48ffa-153">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="48ffa-154">E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.</span><span class="sxs-lookup"><span data-stu-id="48ffa-154">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="48ffa-155">Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-155">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="48ffa-156">Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.</span><span class="sxs-lookup"><span data-stu-id="48ffa-156">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="48ffa-157">Sınıflandırma algoritmaları sık aşağıdaki türlerden biri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="48ffa-157">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="48ffa-158">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="48ffa-158">Binary: either A or B.</span></span>
* <span data-ttu-id="48ffa-159">Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="48ffa-159">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="48ffa-160">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="48ffa-160">Create a console application</span></span>

1. <span data-ttu-id="48ffa-161">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="48ffa-161">Open Visual Studio 2017.</span></span> <span data-ttu-id="48ffa-162">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="48ffa-162">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="48ffa-163">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="48ffa-163">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="48ffa-164">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="48ffa-164">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="48ffa-165">İçinde **adı** metin kutusuna "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-165">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="48ffa-166">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="48ffa-166">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="48ffa-167">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="48ffa-167">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="48ffa-168">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="48ffa-168">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="48ffa-169">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="48ffa-169">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="48ffa-170">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="48ffa-170">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="48ffa-171">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-171">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="48ffa-172">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="48ffa-172">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="48ffa-173">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="48ffa-173">Prepare your data</span></span>

1. <span data-ttu-id="48ffa-174">İndirme [Wikipedia detox-250-satırı-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) ve [wikipedia-detox-250-satırı-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="48ffa-174">Download the [Wikipedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="48ffa-175">İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-175">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="48ffa-176">Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="48ffa-176">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="48ffa-177">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="48ffa-177">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="48ffa-178">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="48ffa-178">Create classes and define paths</span></span>

<span data-ttu-id="48ffa-179">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="48ffa-179">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="48ffa-180">Kısa bir süre önce indirilen dosyaları ve bir genel değişken için yollar tutmak için üç genel alanlar oluşturmak için ihtiyacınız `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="48ffa-180">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="48ffa-181">`_trainDataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-181">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="48ffa-182">`_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-182">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="48ffa-183">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-183">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="48ffa-184">`_textLoader` olan <xref:Microsoft.ML.Data.TextLoader> yüklemek ve veri kümeleri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-184">`_textLoader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="48ffa-185">Satır sağ aşağıdaki kodu ekleyin `Main` bu yollarını belirtmek için yöntemi ve `_textLoader` değişkeni:</span><span class="sxs-lookup"><span data-stu-id="48ffa-185">Add the following code to the line right above the `Main` method to specify those paths and the `_textLoader` variable:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

<span data-ttu-id="48ffa-186">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-186">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="48ffa-187">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="48ffa-187">Add a new class to your project:</span></span>

1. <span data-ttu-id="48ffa-188">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="48ffa-188">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="48ffa-189">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="48ffa-189">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="48ffa-190">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-190">Then, select the **Add** button.</span></span>

    <span data-ttu-id="48ffa-191">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-191">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="48ffa-192">Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="48ffa-192">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="48ffa-193">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="48ffa-193">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="48ffa-194">`SentimentData` Giriş veri kümesi sınıfı ve bir `float` (`Sentiment`) pozitif veya negatif yaklaşım için bir değer ve bir dize yorumu için olan (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="48ffa-194">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="48ffa-195">Her iki alanınız `Column` öznitelikleri kendisine bağlı.</span><span class="sxs-lookup"><span data-stu-id="48ffa-195">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="48ffa-196">Bu öznitelik her bir alanın veri dosyası ve olduğu siparişi açıklayan `Label` alan.</span><span class="sxs-lookup"><span data-stu-id="48ffa-196">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="48ffa-197">`SentimentPrediction` eğitilen modelin sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-197">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="48ffa-198">Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="48ffa-198">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="48ffa-199">`Label` Oluşturup modeli ya da onun da model değerlendirmek için ikinci bir veri kümesi ile kullanılan eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-199">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="48ffa-200">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-200">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="48ffa-201">Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-201">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="48ffa-202">ML.NET modeliyle oluştururken oluşturarak başlayın bir `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="48ffa-202">When building a model with ML.NET you start by creating an `MLContext`.</span></span> <span data-ttu-id="48ffa-203">Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="48ffa-203">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="48ffa-204">Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilecek ML işiniz için bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="48ffa-204">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="48ffa-205">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="48ffa-205">Initialize variables in Main</span></span>

<span data-ttu-id="48ffa-206">Adlı bir değişken oluşturma `mlContext` ve yeni bir örneğini ile başlatma `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="48ffa-206">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="48ffa-207">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-207">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="48ffa-208">Sonra Kurulum başlatma veri yükleme için `_textLoader` yeniden kullanmak için genel değişkeni.</span><span class="sxs-lookup"><span data-stu-id="48ffa-208">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span>  <span data-ttu-id="48ffa-209">Oluşturduğunuzda, bir `TextLoader` kullanarak `MLContext.Data.CreateTextLoader`, gerekli bağlamı geçirdiğiniz ve <xref:Microsoft.ML.Data.TextLoader.Arguments> özelleştirme sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="48ffa-209">When you create a `TextLoader` using  `MLContext.Data.CreateTextLoader`, you pass in the context needed and the <xref:Microsoft.ML.Data.TextLoader.Arguments> class which enables customization.</span></span>

 <span data-ttu-id="48ffa-210">Bir dizi geçirerek veri şemasını belirtin <xref:Microsoft.ML.Data.TextLoader.Column> tüm sütun adlarını ve türlerini içeren yükleyicisi nesneleri.</span><span class="sxs-lookup"><span data-stu-id="48ffa-210">Specify the data schema by passing an array of <xref:Microsoft.ML.Data.TextLoader.Column> objects to the loader containing all the column names and their types.</span></span> <span data-ttu-id="48ffa-211">Oluşturduğunuz zaman veri şemasını önceden tanımlanmış bizim `SentimentData` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="48ffa-211">You defined the data schema previously when you created our `SentimentData` class.</span></span> <span data-ttu-id="48ffa-212">İlk sütun (etiketi) bizim şema için olan bir <xref:System.Boolean> (tahmin) ve ikinci sütun (SentimentText) türü metin/dizesi yaklaşımını tahminde için kullanılan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-212">For our schema, the first column (Label) is a <xref:System.Boolean> (the prediction) and the second column (SentimentText) is the feature of type text/string used for predicting the sentiment.</span></span>
<span data-ttu-id="48ffa-213">`TextLoader` Sınıf tam olarak başlatılmış döndürür <xref:Microsoft.ML.Data.TextLoader></span><span class="sxs-lookup"><span data-stu-id="48ffa-213">The `TextLoader` class returns a fully initialized <xref:Microsoft.ML.Data.TextLoader></span></span>  

<span data-ttu-id="48ffa-214">Başlatmak için `_textLoader` gerekli veri kümeleri için yeniden kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:</span><span class="sxs-lookup"><span data-stu-id="48ffa-214">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextLoader")]

<span data-ttu-id="48ffa-215">Sonraki kod satırı olarak ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-215">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

<span data-ttu-id="48ffa-216">`Train` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="48ffa-216">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="48ffa-217">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-217">Loads the data.</span></span>
* <span data-ttu-id="48ffa-218">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="48ffa-218">Extracts and transforms the data.</span></span>
* <span data-ttu-id="48ffa-219">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-219">Trains the model.</span></span>
* <span data-ttu-id="48ffa-220">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="48ffa-220">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="48ffa-221">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="48ffa-221">Returns the model.</span></span>

<span data-ttu-id="48ffa-222">Oluşturma `Train` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-222">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="48ffa-223">İki parametre Train yönteme geçirilen dikkat edin; bir `MLContext` bağlamının (`mlContext`) ve <xref:System.String> veri kümesi yolu için (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="48ffa-223">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and a <xref:System.String> for the dataset path (`dataPath`).</span></span> <span data-ttu-id="48ffa-224">Eğitim ve test için bu yöntemi birden çok kez kullanın dağıtacağız.</span><span class="sxs-lookup"><span data-stu-id="48ffa-224">You're going to use this method more than once for training and testing.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="48ffa-225">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="48ffa-225">Load the data</span></span>

<span data-ttu-id="48ffa-226">Kullanarak verileri yüklemek `_textLoader` genel değişkenin `dataPath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-226">You'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="48ffa-227">Döndürür bir <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="48ffa-227">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> <span data-ttu-id="48ffa-228">Giriş ve çıkış olarak `Transforms`, `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="48ffa-228">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="48ffa-229">ML.NET veriler SQL görünümüne benzer.</span><span class="sxs-lookup"><span data-stu-id="48ffa-229">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="48ffa-230">Bu, gevşek değerlendirilen, şema ve heterojen olur.</span><span class="sxs-lookup"><span data-stu-id="48ffa-230">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="48ffa-231">Nesne, işlem hattını ilk kısmı ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-231">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="48ffa-232">Bu öğreticide, açıklama ve karşılık gelen toxic veya olmayan toxic yaklaşım bir veri kümesine yükler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-232">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="48ffa-233">Bu model oluşturmayı ve bunu eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-233">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="48ffa-234">İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-234">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="48ffa-235">Verileri dönüştürme ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="48ffa-235">Extract and transform the data</span></span>

<span data-ttu-id="48ffa-236">Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-236">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="48ffa-237">Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-237">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="48ffa-238">Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-238">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="48ffa-239">ML. NET dönüştürme işlem hatları, verilerinizi, eğitim veya test etmeden önce uygulanan dönüştürmeler özel bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48ffa-239">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="48ffa-240">Veri Dönüşümleri birincil amacı olan [özellik kazandırma sayesinde](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="48ffa-240">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="48ffa-241">Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) metinsel verilerimizi ML algoritmalarınızı tanıyacak bir biçime dönüştürmek için sonraki adım, bu nedenle veri.</span><span class="sxs-lookup"><span data-stu-id="48ffa-241">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="48ffa-242">Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="48ffa-242">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="48ffa-243">Ardından, arama `mlContext.Transforms.Text.FeaturizeText` hangi featurizes metin sütununu (`SentimentText`) adı verilen sayısal bir vektör sütununa `Features` makine öğrenimi algoritması tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="48ffa-243">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="48ffa-244">Bu döndüren bir sarmalayıcı çağrısı, bir <xref:Microsoft.ML.Data.EstimatorChain%601> bir işlem hattı etkin olacak.</span><span class="sxs-lookup"><span data-stu-id="48ffa-244">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="48ffa-245">Bu ad `pipeline` eğitmen için ardından ekleyeceği şekilde `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="48ffa-245">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="48ffa-246">Bu, sonraki kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="48ffa-246">Add this as the next line of code:</span></span>

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

>[!WARNING]
> <span data-ttu-id="48ffa-247">ML.NET sürüm 0.10 dönüştürme parametreleri sırası değişti.</span><span class="sxs-lookup"><span data-stu-id="48ffa-247">ML.NET Version 0.10 has changed the order of the Transform parameters.</span></span> <span data-ttu-id="48ffa-248">Bu, kullanıma alma hatası kadar uygulamayı çalıştırın ve model derleme.</span><span class="sxs-lookup"><span data-stu-id="48ffa-248">This will not error out until you run the application and build the model.</span></span> <span data-ttu-id="48ffa-249">Dönüşümlerin parametre adları, önceki kod parçacığında gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="48ffa-249">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="48ffa-250">Bu ön işleme/özellik kazandırma sayesinde adımdır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-250">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="48ffa-251">ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48ffa-251">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="48ffa-252">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="48ffa-252">Choose a learning algorithm</span></span>

<span data-ttu-id="48ffa-253">Eğitmen eklemek için çağrı `mlContext.Transforms.Text.FeaturizeText` döndüren sarmalayıcı yöntemini bir <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> nesne.</span><span class="sxs-lookup"><span data-stu-id="48ffa-253">To add the trainer, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="48ffa-254">Bu işlem hattında kullanacağınız karar ağacı learner budur.</span><span class="sxs-lookup"><span data-stu-id="48ffa-254">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="48ffa-255">`FastTreeBinaryClassificationTrainer` Eklenir `pipeline` ve özellikleri tespit `SentimentText` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="48ffa-255">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="48ffa-256">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-256">Add the following code to the `Train` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="48ffa-257">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="48ffa-257">Train the model</span></span>

<span data-ttu-id="48ffa-258">Modeli eğitme <xref:Microsoft.ML.Data.TransformerChain%601>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-258">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="48ffa-259">Tahmin tanımlandıktan sonra kullanarak modelinize eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> zaten yüklenmiş eğitim verilerini sağlayarak.</span><span class="sxs-lookup"><span data-stu-id="48ffa-259">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> while providing the already loaded training data.</span></span> <span data-ttu-id="48ffa-260">Bu tahminler elde etmek için kullanılacak bir modelini döndürür.</span><span class="sxs-lookup"><span data-stu-id="48ffa-260">This returns a model to use for predictions.</span></span> <span data-ttu-id="48ffa-261">`pipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-261">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="48ffa-262">Denemeyi böyle kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="48ffa-262">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="48ffa-263">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-263">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="48ffa-264">Kaydet ve değerlendirme için kullanılacak modeli eğitilir dön</span><span class="sxs-lookup"><span data-stu-id="48ffa-264">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="48ffa-265">Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain%601> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine.</span><span class="sxs-lookup"><span data-stu-id="48ffa-265">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="48ffa-266">Model sonunda dönüş `Train` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-266">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="48ffa-267">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="48ffa-267">Evaluate the model</span></span>

<span data-ttu-id="48ffa-268">Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-268">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="48ffa-269">İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `Train` değerlendirilecek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-269">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="48ffa-270">Oluşturma `Evaluate` yöntemi hemen sonrasına `Train`, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-270">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="48ffa-271">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="48ffa-271">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="48ffa-272">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-272">Loads the test dataset.</span></span>
* <span data-ttu-id="48ffa-273">İkili değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48ffa-273">Creates the binary evaluator.</span></span>
* <span data-ttu-id="48ffa-274">Model değerlendirir ve metrikleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="48ffa-274">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="48ffa-275">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-275">Displays the metrics.</span></span>

<span data-ttu-id="48ffa-276">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-276">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

<span data-ttu-id="48ffa-277">Daha önce başlatılmış kullanarak test veri kümesini yük `_textLoader` genel değişkenin `_testDataPath` genel alan.</span><span class="sxs-lookup"><span data-stu-id="48ffa-277">You'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="48ffa-278">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-278">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="48ffa-279">Aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-279">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

<span data-ttu-id="48ffa-280">Ardından, makine öğrenimi kullanacağınız `model` özellikleri giriş ve tahmin döndürmek için parametre (dönüştürücü).</span><span class="sxs-lookup"><span data-stu-id="48ffa-280">Next, you'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="48ffa-281">Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-281">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

<span data-ttu-id="48ffa-282">`BinaryClassificationContext.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma.</span><span class="sxs-lookup"><span data-stu-id="48ffa-282">The `BinaryClassificationContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="48ffa-283">Döndürür bir `BinaryClassificationEvaluator.CalibratedResult` nesne ikili sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-283">It returns a `BinaryClassificationEvaluator.CalibratedResult` object contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="48ffa-284">Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-284">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="48ffa-285">Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-285">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="48ffa-286">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="48ffa-286">Displaying the metrics for model validation</span></span>

<span data-ttu-id="48ffa-287">Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="48ffa-287">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

<span data-ttu-id="48ffa-288">Modelinizi dönmeden önce bir .zip dosyası olarak kaydetmek için çağırmak için aşağıdaki kodu ekleyin. `SaveModelAsFile` yöntemi olarak bir sonraki satırda `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="48ffa-288">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="48ffa-289">Modeli a.zip dosyası olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="48ffa-289">Save the model as a.zip file</span></span>

<span data-ttu-id="48ffa-290">Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-290">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="48ffa-291">`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="48ffa-291">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="48ffa-292">Model bir .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="48ffa-292">Saves the model as a .zip file.</span></span>

<span data-ttu-id="48ffa-293">Ardından, yeniden kullanılabilir ve diğer uygulamalarda kullanılan model kaydetmek için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48ffa-293">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="48ffa-294">`ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="48ffa-294">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="48ffa-295">Bu zip dosyası olarak kaydetmek için oluşturacağınız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-295">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="48ffa-296">Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-296">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]
<span data-ttu-id="48ffa-297">Dağıtma ve tahmin da görüntü bir konsol iletisi ile yazarak dosyasının nerede yazılmıştır yüklenen modeliyle `_modelPath`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-297">Deploy and Predict with a loaded model You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="48ffa-298">Kaydedilen modeli ile test veri sonucu tahmin edin</span><span class="sxs-lookup"><span data-stu-id="48ffa-298">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="48ffa-299">Oluşturma `Predict` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-299">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="48ffa-300">`Predict` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="48ffa-300">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="48ffa-301">Test verilerini tek bir yorum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48ffa-301">Creates a single comment of test data.</span></span>
* <span data-ttu-id="48ffa-302">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="48ffa-302">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="48ffa-303">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="48ffa-303">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="48ffa-304">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-304">Displays the predicted results.</span></span>

<span data-ttu-id="48ffa-305">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-305">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

<span data-ttu-id="48ffa-306">Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-306">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="48ffa-307"><xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-307">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="48ffa-308">Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` ilk satırı olarak `Predict` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-308">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionEngine")]
  
<span data-ttu-id="48ffa-309">Eğitilen modelin tahmine test etmek için bir açıklama ekleyin `Predict` bir örneğini oluşturarak yöntemi `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="48ffa-309">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]

 <span data-ttu-id="48ffa-310">Bu açıklama verilerini tek bir örneğini Toxic veya olmayan Toxic duyarlılığını tahmin etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48ffa-310">You can use that to predict the Toxic or Non Toxic sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="48ffa-311">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="48ffa-311">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="48ffa-312">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="48ffa-312">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="48ffa-313">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="48ffa-313">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="48ffa-314">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-314">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="using-the-model-prediction"></a><span data-ttu-id="48ffa-315">Modeli kullanılarak: tahmin</span><span class="sxs-lookup"><span data-stu-id="48ffa-315">Using the model: prediction</span></span>

<span data-ttu-id="48ffa-316">Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için.</span><span class="sxs-lookup"><span data-stu-id="48ffa-316">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="48ffa-317">Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-317">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="48ffa-318">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="48ffa-318">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="48ffa-319">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="48ffa-319">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="48ffa-320">Oluşturma `PredictWithModelLoadedFromFile` yöntemi hemen önce `SaveModelAsFile` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-320">Create the `PredictWithModelLoadedFromFile` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

<span data-ttu-id="48ffa-321">`PredictWithModelLoadedFromFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="48ffa-321">The `PredictWithModelLoadedFromFile` method executes the following tasks:</span></span>

* <span data-ttu-id="48ffa-322">Toplu test verilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48ffa-322">Creates batch test data.</span></span>
* <span data-ttu-id="48ffa-323">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="48ffa-323">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="48ffa-324">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="48ffa-324">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="48ffa-325">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-325">Displays the predicted results.</span></span>

<span data-ttu-id="48ffa-326">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Predict` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="48ffa-326">Add a call to the new method from the `Main` method, right under the `Predict` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

<span data-ttu-id="48ffa-327">Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `PredictWithModelLoadedFromFile` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-327">Add some comments to test the trained model's predictions in the `PredictWithModelLoadedFromFile` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

<span data-ttu-id="48ffa-328">Model yüklenemiyor</span><span class="sxs-lookup"><span data-stu-id="48ffa-328">Load the model</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

<span data-ttu-id="48ffa-329">Bir modeliniz olduğuna göre yorum kullanarak veri Toxic veya olmayan Toxic yaklaşım tahmin etmek için kullanabileceğiniz <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-329">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="48ffa-330">Bir öngörü almak için kullanın `Predict` yeni veriler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-330">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="48ffa-331">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="48ffa-331">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="48ffa-332">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="48ffa-332">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="48ffa-333">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-333">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="48ffa-334">Aşağıdaki kodu ekleyin `PredictWithModelLoadedFromFile` yöntemi tahminler elde etmek için:</span><span class="sxs-lookup"><span data-stu-id="48ffa-334">Add the following code to the `PredictWithModelLoadedFromFile` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="48ffa-335">Tahmin için yüklenen modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="48ffa-335">Using the loaded model for prediction</span></span>

<span data-ttu-id="48ffa-336">Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için.</span><span class="sxs-lookup"><span data-stu-id="48ffa-336">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="48ffa-337">Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-337">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="48ffa-338">Aşağıdakileri kullanarak sonuçları için bir başlık oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="48ffa-338">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

<span data-ttu-id="48ffa-339">Tahmin edilen sonuçlarını görüntülemeden önce yaklaşımını ve özgün açıklamayı, tahmin edilen yaklaşım ile birlikte görmek için tahmini birleştirin.</span><span class="sxs-lookup"><span data-stu-id="48ffa-339">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="48ffa-340">Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A> gerçekleşen, yapmanız gereken yöntemini bu nedenle bu kodunu ekleyin sonraki:</span><span class="sxs-lookup"><span data-stu-id="48ffa-340">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="48ffa-341">Birleştirilmiş göre `SentimentText` ve `Sentiment` bir sınıf kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="48ffa-341">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

<span data-ttu-id="48ffa-342">C# 7.0 C# 7.1 ve projenin varsayılan dil sürümü yeni bir özellik olan demet öğesi adları olan olayla olduğundan, C# 7.1 veya üzeri dil sürümünü değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="48ffa-342">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="48ffa-343">Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="48ffa-343">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="48ffa-344">Seçin **derleme** sekmenize **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="48ffa-344">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="48ffa-345">Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm).</span><span class="sxs-lookup"><span data-stu-id="48ffa-345">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="48ffa-346">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="48ffa-346">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="48ffa-347">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="48ffa-347">Results</span></span>

<span data-ttu-id="48ffa-348">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-348">Your results should be similar to the following.</span></span> <span data-ttu-id="48ffa-349">İşlem hattı işlediği gibi iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="48ffa-349">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="48ffa-350">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48ffa-350">You may see warnings, or processing messages.</span></span> <span data-ttu-id="48ffa-351">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="48ffa-351">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="48ffa-352">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="48ffa-352">Congratulations!</span></span> <span data-ttu-id="48ffa-353">Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="48ffa-353">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="48ffa-354">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="48ffa-354">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="48ffa-355">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="48ffa-355">Next steps</span></span>

<span data-ttu-id="48ffa-356">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="48ffa-356">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="48ffa-357">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="48ffa-357">Understand the problem</span></span>
> * <span data-ttu-id="48ffa-358">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="48ffa-358">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="48ffa-359">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="48ffa-359">Prepare your data</span></span>
> * <span data-ttu-id="48ffa-360">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="48ffa-360">Transform the data</span></span>
> * <span data-ttu-id="48ffa-361">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="48ffa-361">Train the model</span></span>
> * <span data-ttu-id="48ffa-362">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="48ffa-362">Evaluate the model</span></span>
> * <span data-ttu-id="48ffa-363">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="48ffa-363">Predict with the trained model</span></span>
> * <span data-ttu-id="48ffa-364">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="48ffa-364">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="48ffa-365">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="48ffa-365">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="48ffa-366">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="48ffa-366">Issue Classification</span></span>](github-issue-classification.md)
