---
title: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu
description: ML.NET ikili sınıflandırma senaryoda yaklaşım tahmin uygun eylemde için nasıl kullanılacağını anlamak için nasıl kullanılacağını keşfedin.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7d2935fafe9dbad28205c8a896d97d80474a686f
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580891"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="51203-103">Öğretici: Kullanımı bir yaklaşım analizi ikili sınıflandırma senaryosunda ML.NET</span><span class="sxs-lookup"><span data-stu-id="51203-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="51203-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="51203-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="51203-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="51203-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="51203-106">Bu örnek öğretici, C# kullanarak Visual Studio 2017'de .NET Core konsol uygulaması aracılığıyla bir yaklaşım sınıflandırıcı oluşturma ML.NET kullanılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="51203-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="51203-107">Bu öğreticide, şunların nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="51203-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="51203-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="51203-108">Understand the problem</span></span>
> * <span data-ttu-id="51203-109">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="51203-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="51203-110">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="51203-110">Prepare your data</span></span>
> * <span data-ttu-id="51203-111">Öğrenme işlem hattınızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="51203-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="51203-112">Sınıflandırıcı yükleme</span><span class="sxs-lookup"><span data-stu-id="51203-112">Load a classifier</span></span>
> * <span data-ttu-id="51203-113">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="51203-113">Train the model</span></span>
> * <span data-ttu-id="51203-114">Farklı bir veri kümesiyle modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="51203-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="51203-115">Modeli ile test veri sonuçlarını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="51203-115">Predict the test data outcomes with the model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="51203-116">Yaklaşım analizi örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="51203-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="51203-117">Örnek ML.NET sınıflandırır ve yaklaşım artı veya eksi olarak tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="51203-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="51203-118">Ayrıca, kalite analizi için ikinci bir veri kümesi modeliyle değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="51203-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="51203-119">Yaklaşım veri kümeleri WikiDetox projeden ' dir.</span><span class="sxs-lookup"><span data-stu-id="51203-119">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="51203-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="51203-120">Prerequisites</span></span>

* <span data-ttu-id="51203-121">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="51203-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="51203-122">[Wikipedia detox satır veri sekmeyle ayrılmış dosya (wikiPedia-detox-250-satırı-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="51203-122">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="51203-123">[Wikipedia detox satır test sekmeyle ayrılmış dosya (wikipedia-detox-250-satırı-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="51203-123">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="51203-124">Machine learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="51203-124">Machine learning workflow</span></span>

<span data-ttu-id="51203-125">Bu öğreticide, bir makine öğrenimi düzenli bir şekilde taşımak işlem sağlayan bir iş akışı izler.</span><span class="sxs-lookup"><span data-stu-id="51203-125">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="51203-126">İş akışı aşamalar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="51203-126">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="51203-127">**Sorunu anlama**</span><span class="sxs-lookup"><span data-stu-id="51203-127">**Understand the problem**</span></span>
2. <span data-ttu-id="51203-128">**Veri alma**</span><span class="sxs-lookup"><span data-stu-id="51203-128">**Ingest the data**</span></span>
3. <span data-ttu-id="51203-129">**Verileri önceden işleme ve özellik Mühendisliği**</span><span class="sxs-lookup"><span data-stu-id="51203-129">**Data preprocess and feature engineering**</span></span>
4. <span data-ttu-id="51203-130">**Eğitme ve modeli tahmin edin**</span><span class="sxs-lookup"><span data-stu-id="51203-130">**Train and predict the model**</span></span>
5. <span data-ttu-id="51203-131">**Modeli değerlendirme**</span><span class="sxs-lookup"><span data-stu-id="51203-131">**Evaluate the model**</span></span>
6. <span data-ttu-id="51203-132">**Modeli kullanıma hazır hale getirme**</span><span class="sxs-lookup"><span data-stu-id="51203-132">**Model operationalization**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="51203-133">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="51203-133">Understand the problem</span></span>

<span data-ttu-id="51203-134">Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="51203-134">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="51203-135">Sorun bozucu, tahmin edin ve sonuçları değerlendirin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="51203-135">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="51203-136">Sorun Bu öğretici için uygun eylemi gerçekleştirin gelen Web sitesi açıklama yaklaşım öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="51203-136">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="51203-137">Problemi yaklaşım metin ve duyarlılık değeri ile modeli eğitmek için istediğiniz verileri için ve tahmin edilen duyarlılık değeri değerlendirmek ve işletimsel olarak kullanmak dökümünü alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51203-137">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="51203-138">Ardından gerek **belirlemek** yaklaşımı, Görev Seçimi öğrenme makineyle yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="51203-138">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="51203-139">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="51203-139">Select the appropriate machine learning task</span></span>

<span data-ttu-id="51203-140">Bu sorun aşağıdaki gerçekleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="51203-140">With this problem, you know the following facts:</span></span>

<span data-ttu-id="51203-141">Eğitim verileri: Web sitesi açıklamaları pozitif veya negatif olabilir (**yaklaşım**).</span><span class="sxs-lookup"><span data-stu-id="51203-141">Training data: website comments can be positive or negative (**sentiment**).</span></span>
<span data-ttu-id="51203-142">Tahmin **yaklaşım** açıklamasının bir yeni Web sitesi, pozitif veya negatif gibi aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="51203-142">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="51203-143">Lütfen anlamsız Wikipedia için makalelerinizde.</span><span class="sxs-lookup"><span data-stu-id="51203-143">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="51203-144">Kendisi için en iyi yöntemdir ve makale, yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51203-144">He is the best, and the article should say that.</span></span>

<span data-ttu-id="51203-145">Sınıflandırma machine learning görevi bu senaryo için idealdir.</span><span class="sxs-lookup"><span data-stu-id="51203-145">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="51203-146">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="51203-146">About the classification task</span></span>

<span data-ttu-id="51203-147">Sınıflandırma olan verileri kullanan bir makine öğrenimi görev **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="51203-147">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="51203-148">Örneğin, sınıflandırma için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="51203-148">For example, you can use classification to:</span></span>

* <span data-ttu-id="51203-149">Artı veya eksi olarak duyguları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="51203-149">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="51203-150">E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.</span><span class="sxs-lookup"><span data-stu-id="51203-150">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="51203-151">Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="51203-151">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="51203-152">Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.</span><span class="sxs-lookup"><span data-stu-id="51203-152">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="51203-153">Sınıflandırma görevleri sık aşağıdaki türlerden biri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="51203-153">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="51203-154">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="51203-154">Binary: either A or B.</span></span>
* <span data-ttu-id="51203-155">Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="51203-155">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="51203-156">Bir konsol uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="51203-156">Create a console application</span></span>

1. <span data-ttu-id="51203-157">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="51203-157">Open Visual Studio 2017.</span></span> <span data-ttu-id="51203-158">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="51203-158">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="51203-159">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="51203-159">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="51203-160">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="51203-160">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="51203-161">İçinde **adı** metin kutusuna "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="51203-161">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="51203-162">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="51203-162">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="51203-163">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="51203-163">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="51203-164">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="51203-164">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="51203-165">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="51203-165">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="51203-166">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="51203-166">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="51203-167">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="51203-167">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="51203-168">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="51203-168">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="51203-169">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="51203-169">Prepare your data</span></span>

1. <span data-ttu-id="51203-170">İndirme [WikiPedia detox-250-satırı-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) ve [wikipedia-detox-250-satırı-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="51203-170">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="51203-171">İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51203-171">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="51203-172">Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="51203-172">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="51203-173">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="51203-173">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="51203-174">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="51203-174">Create classes and define paths</span></span>

<span data-ttu-id="51203-175">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="51203-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="51203-176">Yolları için kısa bir süre önce indirilen dosyaları tutmak için üç genel alanlar oluşturmak ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="51203-176">You need to create three global fields to hold the paths to the recently downloaded files:</span></span>

* <span data-ttu-id="51203-177">`_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="51203-177">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="51203-178">`_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="51203-178">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="51203-179">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="51203-179">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="51203-180">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="51203-180">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

<span data-ttu-id="51203-181">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51203-181">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="51203-182">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="51203-182">Add a new class to your project:</span></span>

1. <span data-ttu-id="51203-183">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="51203-183">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="51203-184">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="51203-184">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="51203-185">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="51203-185">Then, select the **Add** button.</span></span>

    <span data-ttu-id="51203-186">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="51203-186">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="51203-187">Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="51203-187">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="51203-188">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="51203-188">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="51203-189">`SentimentData` Giriş veri kümesi sınıfı ve bir `float` (`Sentiment`) pozitif veya negatif yaklaşım için bir değer ve bir dize yorumu için olan (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="51203-189">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="51203-190">Her iki alanınız `Column` öznitelikleri kendisine bağlı.</span><span class="sxs-lookup"><span data-stu-id="51203-190">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="51203-191">Bu öznitelik her bir alanın veri dosyası ve olduğu siparişi açıklayan `Label` alan.</span><span class="sxs-lookup"><span data-stu-id="51203-191">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="51203-192">`SentimentPrediction` eğitilen modelin sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51203-192">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="51203-193">Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="51203-193">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="51203-194">`Label` Oluşturup modeli ya da onun da model değerlendirmek için ikinci bir veri kümesi ile kullanılan eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51203-194">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="51203-195">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51203-195">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="51203-196">Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51203-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="51203-197">İçinde *Program.cs* dosya, değişiklik `Main` değiştirerek yöntem imzası `void` ile `async Task`, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="51203-197">In the *Program.cs* file, change the `Main` method signature by replacing `void` with `async Task`, as in the following example:</span></span>

```csharp
static async Task Main(string[] args) 
{

}
```

<span data-ttu-id="51203-198">Eklediğiniz `async` için `Main` ile bir <xref:System.Threading.Tasks.Task> dönüş türü bir zip dosyasına daha sonra modeli kaydediyorsanız ve program, dış görev tamamlanana kadar beklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="51203-198">You add `async` to `Main` with a <xref:System.Threading.Tasks.Task> return type because you're saving the model to a zip file later, and the program needs to wait until that external task completes.</span></span>

> [!NOTE]
> <span data-ttu-id="51203-199">Bir *async main* yöntemi kullanmanıza olanak sağlar `await` içinde `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="51203-199">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="51203-200">Daha fazla bilgi için [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) konusu C# programlama kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="51203-200">For more information, see the [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) topic in the C# programming guide.</span></span>

<span data-ttu-id="51203-201">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="51203-201">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

<span data-ttu-id="51203-202">`Train` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="51203-202">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="51203-203">Yükler veya verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="51203-203">Loads or ingests the data.</span></span>
* <span data-ttu-id="51203-204">Önceden işler ve featurizes verileri.</span><span class="sxs-lookup"><span data-stu-id="51203-204">Preprocesses and featurizes the data.</span></span>
* <span data-ttu-id="51203-205">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="51203-205">Trains the model.</span></span>
* <span data-ttu-id="51203-206">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="51203-206">Predicts sentiment based on test data.</span></span>

<span data-ttu-id="51203-207">Oluşturma `Train` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="51203-207">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a><span data-ttu-id="51203-208">Veri alma</span><span class="sxs-lookup"><span data-stu-id="51203-208">Ingest the data</span></span>

<span data-ttu-id="51203-209">Yeni bir örneğini başlatır <xref:Microsoft.ML.LearningPipeline> veri yükleme, veri işleme/özellik kazandırma sayesinde ve model içerecektir.</span><span class="sxs-lookup"><span data-stu-id="51203-209">Initialize a new instance of <xref:Microsoft.ML.LearningPipeline> that will include the data loading, data processing/featurization, and model.</span></span> <span data-ttu-id="51203-210">İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="51203-210">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<span data-ttu-id="51203-211"><xref:Microsoft.ML.Data.TextLoader> Nesne ilk işlem hattı parçasıdır ve eğitim dosya verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="51203-211">The <xref:Microsoft.ML.Data.TextLoader> object is the first part of the pipeline, and loads the training file data.</span></span>

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a><span data-ttu-id="51203-212">Verileri önceden işleme ve özellik Mühendisliği</span><span class="sxs-lookup"><span data-stu-id="51203-212">Data preprocess and feature engineering</span></span>

<span data-ttu-id="51203-213">Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="51203-213">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="51203-214">Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="51203-214">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="51203-215">Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="51203-215">Using data without these modeling tasks can produce misleading results.</span></span> <span data-ttu-id="51203-216">ML. NET dönüştürme işlem hatları, eğitim veya test etmeden önce verilerinizi uygulanan dönüştürmeler özel bir dizi oluşturmak izin verin.</span><span class="sxs-lookup"><span data-stu-id="51203-216">ML.NET's transform pipelines allow you to compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="51203-217">Dönüşümler birincil amacı veri özellik kazandırma sayesinde için ' dir.</span><span class="sxs-lookup"><span data-stu-id="51203-217">The transforms' primary purpose is for data featurization.</span></span> <span data-ttu-id="51203-218">Bir dönüştürme ardışık düzen avantajı, test verileri uygulamak için işlem hattı kaydetme dönüştürme işlem hattı tanımını sonra olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="51203-218">A transform pipeline's advantage is that after transform pipeline definition, save the pipeline to apply it to test data.</span></span>

<span data-ttu-id="51203-219">Geçerli bir <xref:Microsoft.ML.Transforms.TextFeaturizer> dönüştürülecek `SentimentText` sütununa bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector) adlı `Features` makine öğrenimi algoritması tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="51203-219">Apply a <xref:Microsoft.ML.Transforms.TextFeaturizer> to convert the `SentimentText` column into a [numeric vector](../resources/glossary.md#numerical-feature-vector) called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="51203-220">Bu ön işleme/özellik kazandırma sayesinde adımdır.</span><span class="sxs-lookup"><span data-stu-id="51203-220">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="51203-221">ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51203-221">Using additional components available in ML.NET can enable better results with your model.</span></span> <span data-ttu-id="51203-222">Ekleme `TextFeaturizer` ardışık düzenine sonraki kod satırına olarak:</span><span class="sxs-lookup"><span data-stu-id="51203-222">Add `TextFeaturizer` to the pipeline as the next line of code:</span></span>

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="51203-223">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="51203-223">Choose a learning algorithm</span></span>

<span data-ttu-id="51203-224"><xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Bu işlem hattında kullanacağınız karar ağacı learner nesnedir.</span><span class="sxs-lookup"><span data-stu-id="51203-224">The <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> object is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="51203-225">ML.NET ve kendi parametrelerini müşteri adayları için farklı sonuçlar değiştirerek mevcut farklı öğrencileriyle denemeye özellik kazandırma sayesinde adıma benzer.</span><span class="sxs-lookup"><span data-stu-id="51203-225">Similar to the featurization step, trying out different learners available in ML.NET and changing their parameters leads to different results.</span></span> <span data-ttu-id="51203-226">Ayarlayabileceğiniz ayarlama için [hiperparametreleri](../resources/glossary.md#hyperparameter) gibi <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, ve <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span><span class="sxs-lookup"><span data-stu-id="51203-226">For tuning, you can set [hyperparameters](../resources/glossary.md#hyperparameter) like <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, and <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span></span> <span data-ttu-id="51203-227">Bu hiperparametreleri herhangi bir şey model etkiler önce ayarlanır ve model özgüdür.</span><span class="sxs-lookup"><span data-stu-id="51203-227">These hyperparameters are set before anything affects the model and are model-specific.</span></span> <span data-ttu-id="51203-228">Karar ağacı performans için daha büyük bir değer performansı olumsuz yönde etkileyebilir şekilde ayarlamak için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="51203-228">They're used to tune the decision tree for performance, so larger values can negatively impact performance.</span></span>

<span data-ttu-id="51203-229">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="51203-229">Add the following code to the `Train` method:</span></span>

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a><span data-ttu-id="51203-230">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="51203-230">Train the model</span></span>

<span data-ttu-id="51203-231">Modeli eğitme <xref:Microsoft.ML.PredictionModel%602>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="51203-231">You train the model, <xref:Microsoft.ML.PredictionModel%602>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="51203-232">`pipeline.Train<SentimentData, SentimentPrediction>()` (veri trenler özelliği oluşturucu ve learner yükler) işlem hattı eğitir.</span><span class="sxs-lookup"><span data-stu-id="51203-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trains the pipeline (loads the data, trains the featurizer and learner).</span></span> <span data-ttu-id="51203-233">Denemeyi böyle kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="51203-233">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="51203-234">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="51203-234">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="51203-235">Kaydet ve değerlendirme için kullanılacak modeli eğitilir dön</span><span class="sxs-lookup"><span data-stu-id="51203-235">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="51203-236">Bu noktada, tüm mevcut veya yeni .NET uygulamalarınızı tümleşik bir model var.</span><span class="sxs-lookup"><span data-stu-id="51203-236">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="51203-237">Modelinizi döndürmeden önce bir .zip dosyası olarak kaydetmek için sonraki satıra aşağıdaki kodu ekleyin `Train`:</span><span class="sxs-lookup"><span data-stu-id="51203-237">To save your model to a .zip file before returning, add the following code to the next line in `Train`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

<span data-ttu-id="51203-238">Model sonunda dönüş `Train` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="51203-238">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="51203-239">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="51203-239">Evaluate the model</span></span>

<span data-ttu-id="51203-240">Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="51203-240">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="51203-241">İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `Train` değerlendirilecek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="51203-241">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="51203-242">Oluşturma `Evaluate` yöntemi hemen sonrasına `Train`, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="51203-242">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="51203-243">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="51203-243">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="51203-244">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="51203-244">Loads the test dataset.</span></span>
* <span data-ttu-id="51203-245">İkili değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51203-245">Creates the binary evaluator.</span></span>
* <span data-ttu-id="51203-246">Model değerlendirir ve metrikleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="51203-246">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="51203-247">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="51203-247">Displays the metrics.</span></span>

<span data-ttu-id="51203-248">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="51203-248">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<span data-ttu-id="51203-249"><xref:Microsoft.ML.Data.TextLoader> Sınıfı aynı şemaya sahip yeni test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="51203-249">The <xref:Microsoft.ML.Data.TextLoader> class loads the new test dataset with the same schema.</span></span> <span data-ttu-id="51203-250">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="51203-250">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="51203-251">Aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="51203-251">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<span data-ttu-id="51203-252"><xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Nesne hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma.</span><span class="sxs-lookup"><span data-stu-id="51203-252">The <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> object computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="51203-253">Bu ölçümler görmek için bir sonraki satırda olarak değerlendirici ekleyin `Evaluate` yöntemi, aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="51203-253">To see those metrics, add the evaluator as the next line in the `Evaluate` method, with the following code:</span></span>

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<span data-ttu-id="51203-254"><xref:Microsoft.ML.Models.BinaryClassificationMetrics> İkili sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="51203-254">The <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="51203-255">Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51203-255">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="51203-256">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="51203-256">Add the following code:</span></span>

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="51203-257">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="51203-257">Displaying the metrics for model validation</span></span>

<span data-ttu-id="51203-258">Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="51203-258">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a><span data-ttu-id="51203-259">Modeli ile test veri sonuçlarını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="51203-259">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="51203-260">Oluşturma `Predict` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="51203-260">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="51203-261">`Predict` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="51203-261">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="51203-262">Test verileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51203-262">Creates test data.</span></span>
* <span data-ttu-id="51203-263">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="51203-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="51203-264">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="51203-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="51203-265">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="51203-265">Displays the predicted results.</span></span>

<span data-ttu-id="51203-266">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="51203-266">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

<span data-ttu-id="51203-267">Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `Predict` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="51203-267">Add some comments to test the trained model's predictions in the `Predict` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

<span data-ttu-id="51203-268">Bir modeliniz olduğuna göre pozitif veya negatif yaklaşım açıklama verileri kullanarak tahmin etmek için kullanabileceğiniz <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="51203-268">Now that you have a model, you can use that to predict the positive or negative sentiment of the comment data using the <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="51203-269">Bir öngörü almak için kullanın `Predict` yeni veriler.</span><span class="sxs-lookup"><span data-stu-id="51203-269">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="51203-270">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="51203-270">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="51203-271">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="51203-271">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="51203-272">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="51203-272">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="51203-273">Modeli kullanıma hazır hale getirme: tahmin</span><span class="sxs-lookup"><span data-stu-id="51203-273">Model operationalization: prediction</span></span>

<span data-ttu-id="51203-274">Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için.</span><span class="sxs-lookup"><span data-stu-id="51203-274">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="51203-275">Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="51203-275">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="51203-276">Aşağıdakileri kullanarak sonuçları için bir başlık oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="51203-276">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

<span data-ttu-id="51203-277">Tahmin edilen sonuçlarını görüntülemeden önce yaklaşımını ve özgün açıklamayı, tahmin edilen yaklaşım ile birlikte görmek için tahmini birleştirin.</span><span class="sxs-lookup"><span data-stu-id="51203-277">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="51203-278">Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A> gerçekleşen, yapmanız gereken yöntemini bu nedenle bu kodunu ekleyin sonraki:</span><span class="sxs-lookup"><span data-stu-id="51203-278">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="51203-279">Birleştirilmiş göre `SentimentText` ve `Sentiment` bir sınıf kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="51203-279">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

<span data-ttu-id="51203-280">C# 7.0 C# 7.1 ve projenin varsayılan dil sürümü yeni bir özellik olan demet öğesi adları olan olayla olduğundan, C# 7.1 veya üzeri dil sürümünü değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="51203-280">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="51203-281">Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="51203-281">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="51203-282">Seçin **derleme** sekmenize **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="51203-282">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="51203-283">Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm).</span><span class="sxs-lookup"><span data-stu-id="51203-283">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="51203-284">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="51203-284">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="51203-285">Sonuçları</span><span class="sxs-lookup"><span data-stu-id="51203-285">Results</span></span>

<span data-ttu-id="51203-286">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51203-286">Your results should be similar to the following.</span></span> <span data-ttu-id="51203-287">İşlem hattı işlediği gibi iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="51203-287">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="51203-288">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51203-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="51203-289">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="51203-289">These have been removed from the following results for clarity.</span></span>

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

<span data-ttu-id="51203-290">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="51203-290">Congratulations!</span></span> <span data-ttu-id="51203-291">Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="51203-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="51203-292">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="51203-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="51203-293">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="51203-293">Next steps</span></span>

<span data-ttu-id="51203-294">Bu öğreticide şunları öğrendiniz: nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="51203-294">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="51203-295">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="51203-295">Understand the problem</span></span>
> * <span data-ttu-id="51203-296">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="51203-296">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="51203-297">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="51203-297">Prepare your data</span></span>
> * <span data-ttu-id="51203-298">Öğrenme işlem hattınızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="51203-298">Create the learning pipeline</span></span>
> * <span data-ttu-id="51203-299">Sınıflandırıcı yükleme</span><span class="sxs-lookup"><span data-stu-id="51203-299">Load a classifier</span></span>
> * <span data-ttu-id="51203-300">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="51203-300">Train the model</span></span>
> * <span data-ttu-id="51203-301">Farklı bir veri kümesiyle modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="51203-301">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="51203-302">Modeli ile test veri sonuçlarını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="51203-302">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="51203-303">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="51203-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="51203-304">Taksi taksi göstergesi</span><span class="sxs-lookup"><span data-stu-id="51203-304">Taxi Fare Predictor</span></span>](taxi-fare.md)
