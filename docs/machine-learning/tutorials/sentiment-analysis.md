---
title: Bir düşünceleri analiz ikili sınıflandırma senaryosunda ML.NET kullanın
description: ML.NET bir ikili sınıflandırma senaryosunda düşünceleri tahmin uygun eylemi gerçekleştirin için nasıl kullanılacağını anlamak için nasıl kullanılacağını bulur.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 85fb55582d891c67f172effa4952f15ac5604d50
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207670"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="de924-103">Öğretici: Kullanım düşünceleri analiz ikili sınıflandırma senaryosunda ML.NET</span><span class="sxs-lookup"><span data-stu-id="de924-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="de924-104">Bu konuda şu anda önizlemede değil, ML.NET başvuruyor ve malzeme değiştirilebilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="de924-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="de924-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="de924-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="de924-106">Bu örnek öğretici ML.NET düşünceleri sınıflandırıcı aracılığıyla C# Visual Studio 2017 kullanarak bir .NET Core konsol uygulaması oluşturmak için kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="de924-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="de924-107">Bu öğreticide, bilgi nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="de924-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="de924-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="de924-108">Understand the problem</span></span>
> * <span data-ttu-id="de924-109">Uygun makine öğrenme görevini seçin</span><span class="sxs-lookup"><span data-stu-id="de924-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="de924-110">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="de924-110">Prepare your data</span></span>
> * <span data-ttu-id="de924-111">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="de924-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="de924-112">Bir sınıflandırıcı yükleme</span><span class="sxs-lookup"><span data-stu-id="de924-112">Load a classifier</span></span>
> * <span data-ttu-id="de924-113">Modeli eğitmek</span><span class="sxs-lookup"><span data-stu-id="de924-113">Train the model</span></span>
> * <span data-ttu-id="de924-114">Farklı bir veri kümesi ile modelini değerlendir</span><span class="sxs-lookup"><span data-stu-id="de924-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="de924-115">Model ile test veri sonuçlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="de924-115">Predict the test data outcomes with the model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="de924-116">Düşünceleri analiz örnek genel bakış</span><span class="sxs-lookup"><span data-stu-id="de924-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="de924-117">Örnek ML.NET sınıflandırır ve düşünceleri olumlu veya olumsuz olarak tahmin modeli eğitmek için kullandığı bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="de924-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="de924-118">Ayrıca, ikinci bir veri kümesi kalitesini analiz için modeliyle değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="de924-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="de924-119">Düşünceleri veri kümeleri WikiDetox projeden ' dir.</span><span class="sxs-lookup"><span data-stu-id="de924-119">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="de924-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="de924-120">Prerequisites</span></span>

* <span data-ttu-id="de924-121">[Visual Studio 2017 15,6 veya üstü](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile.</span><span class="sxs-lookup"><span data-stu-id="de924-121">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="de924-122">[Wikipedia detox satır veri sekmeyle ayrılmış dosya (wikiPedia-detox-250-satır-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="de924-122">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="de924-123">[Wikipedia detox satırı test sekmeyle ayrılmış dosya (wikipedia-detox-250-satır-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span><span class="sxs-lookup"><span data-stu-id="de924-123">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="de924-124">Machine learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="de924-124">Machine learning workflow</span></span>

<span data-ttu-id="de924-125">Bu öğretici bir machine learning düzenli bir şekilde taşımak işlem tanır iş akışı izler.</span><span class="sxs-lookup"><span data-stu-id="de924-125">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="de924-126">İş akışı aşamaları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="de924-126">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="de924-127">**Sorunu anlamak**</span><span class="sxs-lookup"><span data-stu-id="de924-127">**Understand the problem**</span></span>
2. <span data-ttu-id="de924-128">**Veri alma**</span><span class="sxs-lookup"><span data-stu-id="de924-128">**Ingest the data**</span></span>
3. <span data-ttu-id="de924-129">**Veri önişle ve mühendislik özellik**</span><span class="sxs-lookup"><span data-stu-id="de924-129">**Data preprocess and feature engineering**</span></span>
4. <span data-ttu-id="de924-130">**Eğitmek ve modeli tahmin etme**</span><span class="sxs-lookup"><span data-stu-id="de924-130">**Train and predict the model**</span></span>
5. <span data-ttu-id="de924-131">**Modeli değerlendirin**</span><span class="sxs-lookup"><span data-stu-id="de924-131">**Evaluate the model**</span></span>
6. <span data-ttu-id="de924-132">**Model operationalization**</span><span class="sxs-lookup"><span data-stu-id="de924-132">**Model operationalization**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="de924-133">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="de924-133">Understand the problem</span></span>

<span data-ttu-id="de924-134">İlk oluşturma ve eğitim modeli destekleyebilir bölümleri aşağıya doğru bölün şekilde sorun anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de924-134">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="de924-135">Tahmin etmek ve sonuçları değerlendirin problemi kesiliyor.</span><span class="sxs-lookup"><span data-stu-id="de924-135">Breaking the problem down you to predict and evaluate the results.</span></span>

<span data-ttu-id="de924-136">Sorun Bu öğretici için uygun eylemi gerçekleştirin için gelen Web sitesi yorum düşünceleri anlamaktır.</span><span class="sxs-lookup"><span data-stu-id="de924-136">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="de924-137">Problemi düşünceleri metin ve düşünceleri değer ile modeli eğitmek için istediğiniz veriler için ve değerlendirmek ve işletimsel kullanmak bir tahmin edilen düşünceleri değer bozulabilir.</span><span class="sxs-lookup"><span data-stu-id="de924-137">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="de924-138">Ardından gerek **belirlemek** Görev Seçimi öğrenme makineyle yardımcı düşünceleri.</span><span class="sxs-lookup"><span data-stu-id="de924-138">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="de924-139">Uygun makine öğrenme görevini seçin</span><span class="sxs-lookup"><span data-stu-id="de924-139">Select the appropriate machine learning task</span></span>

<span data-ttu-id="de924-140">Bu sorun aşağıdaki gerçekleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="de924-140">With this problem, you know the following facts:</span></span>

<span data-ttu-id="de924-141">Verileri eğitim: Web sitesi açıklamaları olumlu veya olumsuz olabilir (**düşünceleri**).</span><span class="sxs-lookup"><span data-stu-id="de924-141">Training data: website comments can be positive or negative (**sentiment**).</span></span>
<span data-ttu-id="de924-142">Tahmin **düşünceleri** açıklamasının bir yeni Web sitesi, pozitif veya negatif gibi aşağıdaki örneklerde:</span><span class="sxs-lookup"><span data-stu-id="de924-142">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="de924-143">Wikipedia için anlamsız ekleme kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="de924-143">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="de924-144">Kendisine en iyi olduğu ve makale, yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="de924-144">He is the best, and the article should say that.</span></span>

<span data-ttu-id="de924-145">Sınıflandırma machine learning görevi bu senaryo için uygundur.</span><span class="sxs-lookup"><span data-stu-id="de924-145">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="de924-146">Sınıflandırma görev hakkında</span><span class="sxs-lookup"><span data-stu-id="de924-146">About the classification task</span></span>

<span data-ttu-id="de924-147">Sınıflandırma olan verileri kullanan bir machine learning görevi **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="de924-147">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="de924-148">Örneğin, sınıflandırma için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="de924-148">For example, you can use classification to:</span></span>

* <span data-ttu-id="de924-149">Düşünceleri olumlu veya olumsuz olarak belirleyin.</span><span class="sxs-lookup"><span data-stu-id="de924-149">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="de924-150">E-posta istenmeyen posta olarak Önemsiz veya iyi sınıflandırır.</span><span class="sxs-lookup"><span data-stu-id="de924-150">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="de924-151">Hasta'nın lab örnek cancerous olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="de924-151">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="de924-152">Müşterilerin bir satış kampanyası yanıtlamak için kendi propensity göre kategorilere ayır.</span><span class="sxs-lookup"><span data-stu-id="de924-152">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="de924-153">Sınıflandırma görevleri sık aşağıdaki türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="de924-153">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="de924-154">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="de924-154">Binary: either A or B.</span></span>
* <span data-ttu-id="de924-155">Veya çoklu sınıflar: tek bir model kullanarak tahmin birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="de924-155">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="de924-156">Bir konsol uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="de924-156">Create a console application</span></span>

1. <span data-ttu-id="de924-157">Visual Studio 2017'ni açın.</span><span class="sxs-lookup"><span data-stu-id="de924-157">Open Visual Studio 2017.</span></span> <span data-ttu-id="de924-158">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="de924-158">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="de924-159">İçinde *yeni proje*\* iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="de924-159">In the *New Project*\* dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="de924-160">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="de924-160">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="de924-161">İçinde **adı** metin kutusu, "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="de924-161">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="de924-162">Adlı bir dizin oluşturun *veri* projenize veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="de924-162">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="de924-163">İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="de924-163">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="de924-164">"Data" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="de924-164">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="de924-165">Yükleme **Microsoft.ML NuGet paketi**:</span><span class="sxs-lookup"><span data-stu-id="de924-165">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="de924-166">Çözüm Gezgini'nde projenizi ve select üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="de924-166">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="de924-167">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="de924-167">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="de924-168">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulünü** iletişim varsa, listelenen paketler için lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="de924-168">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="de924-169">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="de924-169">Prepare your data</span></span>

1. <span data-ttu-id="de924-170">Karşıdan [WikiPedia detox-250-satır-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) ve [wikipedia-detox-250-satır-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="de924-170">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="de924-171">İlk veri kümesini makine öğrenimi modeline eğitir ve ikinci nasıl modelinizi doğrudur değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de924-171">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="de924-172">Çözüm Gezgini'nde, her biri sağ \*.tsv dosyaları ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="de924-172">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="de924-173">Altında **Gelişmiş**, değerini değiştirme **çıktı dizinine Kopyala** için **her zaman**.</span><span class="sxs-lookup"><span data-stu-id="de924-173">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="de924-174">Sınıflar oluşturma ve yolları tanımla</span><span class="sxs-lookup"><span data-stu-id="de924-174">Create classes and define paths</span></span>

<span data-ttu-id="de924-175">Aşağıdaki ek ekleyin `using` deyimleri üstüne *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="de924-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="de924-176">Yolun son indirilen dosyaları tutmak için üç genel değişkenler oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="de924-176">You need to create three global variables to hold the path to the recently downloaded files:</span></span>

* <span data-ttu-id="de924-177">`_dataPath` modeli eğitmek için kullanılan veri kümesi yolu.</span><span class="sxs-lookup"><span data-stu-id="de924-177">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="de924-178">`_testDataPath` model değerlendirmek için kullanılan veri kümesi yolu.</span><span class="sxs-lookup"><span data-stu-id="de924-178">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="de924-179">`_modelPath` Eğitim modeli kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="de924-179">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="de924-180">Satırının sağındaki aşağıdaki kodu ekleyin `Main` yöntemi en son indirilen dosyaları belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="de924-180">Add the following code to the line right above the `Main` method to specify the recently downloaded files:</span></span>

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

<span data-ttu-id="de924-181">Giriş verisi ve tahminleri için bazı sınıfları oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de924-181">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="de924-182">Yeni bir sınıf projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="de924-182">Add a new class to your project:</span></span>

1. <span data-ttu-id="de924-183">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="de924-183">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="de924-184">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="de924-184">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="de924-185">Ardından, seçin **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="de924-185">Then, select the **Add** button.</span></span>

    <span data-ttu-id="de924-186">*SentimentData.cs* dosyasını Kod Düzenleyicisi'nde açar.</span><span class="sxs-lookup"><span data-stu-id="de924-186">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="de924-187">Aşağıdakileri ekleyin `using` deyimi üstüne *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="de924-187">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="de924-188">Varolan sınıf tanımına kaldırmak ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="de924-188">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="de924-189">`SentimentData` girdi veri kümesi sınıfı ve sahip bir `float` (`Sentiment`) düşünceleri pozitif veya negatif bir değer ve açıklama için bir dize olan (`SentimentText`).</span><span class="sxs-lookup"><span data-stu-id="de924-189">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="de924-190">Her iki alana sahip `Column` öznitelikleri kendisine bağlı.</span><span class="sxs-lookup"><span data-stu-id="de924-190">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="de924-191">Bu öznitelik veri dosyası ve olduğu her bir alan sıralamasını açıklar `Label` alan.</span><span class="sxs-lookup"><span data-stu-id="de924-191">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="de924-192">`SentimentPrediction` model eğitilmiş sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de924-192">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="de924-193">Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="de924-193">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="de924-194">`Label` Oluşturabilir ve ayrıca sahip ikinci bir veri kümesi model değerlendirmek için kullanılan model ve onun eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de924-194">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="de924-195">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de924-195">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="de924-196">Değerlendirme için bir giriş eğitim verilerini, tahmin edilen değerler ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de924-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="de924-197">İçinde *Program.cs* dosya, değişiklik `Main` değiştirerek yöntem imzası `void` ile `async Task`, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="de924-197">In the *Program.cs* file, change the `Main` method signature by replacing `void` with `async Task`, as in the following example:</span></span>

```csharp
static async Task Main(string[] args) 
{

}
```

<span data-ttu-id="de924-198">Eklediğiniz `async` için `Main` ile bir <xref:System.Threading.Tasks.Task> daha sonra bir zip dosyasına model kaydediyorsanız ve program dış görev tamamlanana dek bekleyin gerekir çünkü dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="de924-198">You add `async` to `Main` with a <xref:System.Threading.Tasks.Task> return type because you're saving the model to a zip file later, and the program needs to wait until that external task completes.</span></span>

> [!NOTE]
> <span data-ttu-id="de924-199">Bir *zaman uyumsuz ana* yöntemi kullanmanıza olanak sağlayan `await` içinde `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de924-199">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="de924-200">Daha fazla bilgi için bkz: [zaman uyumsuz ana](../../../docs/csharp/programming-guide/main-and-command-args/index.md) konusu C# programlama kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="de924-200">For more information, see the [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) topic in the C# programming guide.</span></span>

<span data-ttu-id="de924-201">Değiştir `Console.WriteLine("Hello World!")` aşağıdaki kodda satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="de924-201">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

<span data-ttu-id="de924-202">`Train` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="de924-202">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="de924-203">Yükler veya verileri alır.</span><span class="sxs-lookup"><span data-stu-id="de924-203">Loads or ingests the data.</span></span>
* <span data-ttu-id="de924-204">Preprocesses ve featurizes verileri.</span><span class="sxs-lookup"><span data-stu-id="de924-204">Preprocesses and featurizes the data.</span></span>
* <span data-ttu-id="de924-205">Model eğitir.</span><span class="sxs-lookup"><span data-stu-id="de924-205">Trains the model.</span></span>
* <span data-ttu-id="de924-206">Test verilerine dayalı düşünceleri tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="de924-206">Predicts sentiment based on test data.</span></span>

<span data-ttu-id="de924-207">Oluşturma `Train` yöntemi, hemen sonra `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="de924-207">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static PredictionModel<SentimentData, SentimentPrediction> Train()
{

}
```

## <a name="ingest-the-data"></a><span data-ttu-id="de924-208">Veri alma</span><span class="sxs-lookup"><span data-stu-id="de924-208">Ingest the data</span></span>

<span data-ttu-id="de924-209">Yeni bir örneğini başlatır <xref:Microsoft.ML.LearningPipeline> veri yükleme, veri işleme/featurization ve modeli içerecektir.</span><span class="sxs-lookup"><span data-stu-id="de924-209">Initialize a new instance of <xref:Microsoft.ML.LearningPipeline> that will include the data loading, data processing/featurization, and model.</span></span> <span data-ttu-id="de924-210">İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="de924-210">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<span data-ttu-id="de924-211"><xref:Microsoft.ML.Data.TextLoader> Nesne Ardışık düzenin ilk bir parçasıdır ve eğitim dosya verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="de924-211">The <xref:Microsoft.ML.Data.TextLoader> object is the first part of the pipeline, and loads the training file data.</span></span>

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a><span data-ttu-id="de924-212">Veri önişle ve mühendislik özellik</span><span class="sxs-lookup"><span data-stu-id="de924-212">Data preprocess and feature engineering</span></span>

<span data-ttu-id="de924-213">Ön işleme ve veri temizleme bir veri kümesi etkili bir şekilde machine learning için kullanılmadan önce gerçekleşen önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="de924-213">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="de924-214">Ham verileri gürültülü ve güvenilmeyen görülür ve değerleri eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="de924-214">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="de924-215">Bu model görevleri olmadan verileri kullanarak yanıltıcı sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="de924-215">Using data without these modeling tasks can produce misleading results.</span></span> <span data-ttu-id="de924-216">ML. NET'in dönüşüm işlem hatlarını, eğitim veya test önce verilerinizi uygulanan Dönüşümlerin özel kümesi oluşturmak izin verir.</span><span class="sxs-lookup"><span data-stu-id="de924-216">ML.NET's transform pipelines allow you to compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="de924-217">Dönüşümler birincil amacı için veri featurization ' dir.</span><span class="sxs-lookup"><span data-stu-id="de924-217">The transforms' primary purpose is for data featurization.</span></span> <span data-ttu-id="de924-218">Bir dönüştürme ardışık düzen avantajı, test verileri uygulamak için ardışık düzen kaydetme dönüştürme ardışık düzen tanımı sonra olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="de924-218">A transform pipeline's advantage is that after transform pipeline definition, save the pipeline to apply it to test data.</span></span>

<span data-ttu-id="de924-219">Geçerli bir <xref:Microsoft.ML.Transforms.TextFeaturizer> dönüştürmek için `SentimentText` sütununa bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector) adlı `Features` makine öğrenimi algoritması tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="de924-219">Apply a <xref:Microsoft.ML.Transforms.TextFeaturizer> to convert the `SentimentText` column into a [numeric vector](../resources/glossary.md#numerical-feature-vector) called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="de924-220">Bu ön işleme featurization adımdır.</span><span class="sxs-lookup"><span data-stu-id="de924-220">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="de924-221">ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de924-221">Using additional components available in ML.NET can enable better results with your model.</span></span> <span data-ttu-id="de924-222">Ekleme `TextFeaturizer` ardışık düzenine kodun sonraki satırında, olarak:</span><span class="sxs-lookup"><span data-stu-id="de924-222">Add `TextFeaturizer` to the pipeline as the next line of code:</span></span>

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="de924-223">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="de924-223">Choose a learning algorithm</span></span>

<span data-ttu-id="de924-224"><xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Nesnesidir bir karar ağacı öğrenen bu ardışık düzeninde kullanmanız.</span><span class="sxs-lookup"><span data-stu-id="de924-224">The <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> object is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="de924-225">Farklı öğrencileriyle ML.NET ve bunların parametrelerini müşteri adayları farklı sonuçlar değiştirme kullanılabilir çıkışı çalışırken featurization adıma benzer.</span><span class="sxs-lookup"><span data-stu-id="de924-225">Similar to the featurization step, trying out different learners available in ML.NET and changing their parameters leads to different results.</span></span> <span data-ttu-id="de924-226">Ayarlayabileceğiniz ayarlamak için [hyperparameters](../resources/glossary.md#hyperparameter) gibi <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, ve <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span><span class="sxs-lookup"><span data-stu-id="de924-226">For tuning, you can set [hyperparameters](../resources/glossary.md#hyperparameter) like <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, and <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span></span> <span data-ttu-id="de924-227">Bu hyperparameters herhangi bir şey model etkiler önce ayarlanır ve modeline özgüdür.</span><span class="sxs-lookup"><span data-stu-id="de924-227">These hyperparameters are set before anything affects the model and are model-specific.</span></span> <span data-ttu-id="de924-228">Performans için karar ağacı büyük değerler performansı olumsuz yönde etkileyebilir şekilde ayarlamak için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="de924-228">They're used to tune the decision tree for performance, so larger values can negatively impact performance.</span></span>

<span data-ttu-id="de924-229">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="de924-229">Add the following code to the `Train` method:</span></span>

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a><span data-ttu-id="de924-230">Modeli eğitmek</span><span class="sxs-lookup"><span data-stu-id="de924-230">Train the model</span></span>

<span data-ttu-id="de924-231">Modeli eğitmek <xref:Microsoft.ML.PredictionModel%602>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="de924-231">You train the model, <xref:Microsoft.ML.PredictionModel%602>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="de924-232">`pipeline.Train<SentimentData, SentimentPrediction>()` (verileri trenler featurizer ve öğrenen yükler) ardışık düzen eğitir.</span><span class="sxs-lookup"><span data-stu-id="de924-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trains the pipeline (loads the data, trains the featurizer and learner).</span></span> <span data-ttu-id="de924-233">Bu işlem yapılana kadar deneme yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="de924-233">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="de924-234">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="de924-234">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="de924-235">Kaydet ve değerlendirme amacıyla kullanmak model eğitilmiş dön</span><span class="sxs-lookup"><span data-stu-id="de924-235">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="de924-236">Bu noktada, mevcut veya yeni .NET uygulamalarınızın hiçbirine tümleşik bir modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="de924-236">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="de924-237">Modelinizi döndürmeden önce bir .zip dosyasına kaydetmek için bir sonraki satırda aşağıdaki kodu ekleyin `Train`:</span><span class="sxs-lookup"><span data-stu-id="de924-237">To save your model to a .zip file before returning, add the following code to the next line in `Train`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

<span data-ttu-id="de924-238">Modelin sonunda dönmek `Train` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de924-238">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="de924-239">Modeli değerlendirin</span><span class="sxs-lookup"><span data-stu-id="de924-239">Evaluate the model</span></span>

<span data-ttu-id="de924-240">Oluşturulan ve model eğitilmiş göre kalite ve doğrulama için farklı bir veri kümesi ile değerlendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="de924-240">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="de924-241">İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `Train` değerlendirilecek geçirildi.</span><span class="sxs-lookup"><span data-stu-id="de924-241">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="de924-242">Oluşturma `Evaluate` yöntemi, hemen sonra `Train`, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="de924-242">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="de924-243">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="de924-243">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="de924-244">Test veri yükler.</span><span class="sxs-lookup"><span data-stu-id="de924-244">Loads the test dataset.</span></span>
* <span data-ttu-id="de924-245">İkili değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de924-245">Creates the binary evaluator.</span></span>
* <span data-ttu-id="de924-246">Model değerlendirir ve ölçümleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="de924-246">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="de924-247">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="de924-247">Displays the metrics.</span></span>

<span data-ttu-id="de924-248">Yeni yönteminden bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntem çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="de924-248">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<span data-ttu-id="de924-249"><xref:Microsoft.ML.Data.TextLoader> Sınıfı aynı şema yeni test veri yükler.</span><span class="sxs-lookup"><span data-stu-id="de924-249">The <xref:Microsoft.ML.Data.TextLoader> class loads the new test dataset with the same schema.</span></span> <span data-ttu-id="de924-250">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de924-250">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="de924-251">Aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="de924-251">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<span data-ttu-id="de924-252"><xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Nesne hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma.</span><span class="sxs-lookup"><span data-stu-id="de924-252">The <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> object computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="de924-253">Bu ölçümler görmek için bir sonraki satırda olarak değerlendirici eklemek `Evaluate` aşağıdaki kod ile yöntemi:</span><span class="sxs-lookup"><span data-stu-id="de924-253">To see those metrics, add the evaluator as the next line in the `Evaluate` method, with the following code:</span></span>

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<span data-ttu-id="de924-254"><xref:Microsoft.ML.Models.BinaryClassificationMetrics> İkili sınıflandırma değerlendiricisi tarafından hesaplanan genel ölçümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="de924-254">The <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="de924-255">Bu model kalitesini belirlemek için görüntü için ölçümleri ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de924-255">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="de924-256">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="de924-256">Add the following code:</span></span>

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="de924-257">Model doğrulama için ölçümler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="de924-257">Displaying the metrics for model validation</span></span>

<span data-ttu-id="de924-258">Bunlar üzerinde işlem ölçümleri görüntülemek ve sonuçları paylaşmak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="de924-258">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a><span data-ttu-id="de924-259">Model ile test veri sonuçlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="de924-259">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="de924-260">Oluşturma `Predict` yöntemi, hemen sonra `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="de924-260">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="de924-261">`Predict` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="de924-261">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="de924-262">Test verileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de924-262">Creates test data.</span></span>
* <span data-ttu-id="de924-263">Test verilerine dayalı düşünceleri tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="de924-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="de924-264">Test veri ve raporlama için tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="de924-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="de924-265">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="de924-265">Displays the predicted results.</span></span>

<span data-ttu-id="de924-266">Yeni yönteminden bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntem çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="de924-266">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

<span data-ttu-id="de924-267">Eğitilmiş modelinin tahminleri test etmek için bazı açıklamalar ekleme `Predict` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="de924-267">Add some comments to test the trained model's predictions in the `Predict` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

<span data-ttu-id="de924-268">Bir model sahip olduğunuza göre yorum veri kullanmanın olumlu veya olumsuz düşünceleri tahmin etmek için kullanabileceğiniz <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de924-268">Now that you have a model, you can use that to predict the positive or negative sentiment of the comment data using the <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="de924-269">Tahmin almak için `Predict` yeni verileri.</span><span class="sxs-lookup"><span data-stu-id="de924-269">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="de924-270">Giriş verisi dize ve model olduğuna dikkat edin featurization içerir.</span><span class="sxs-lookup"><span data-stu-id="de924-270">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="de924-271">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="de924-271">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="de924-272">Özellikle tahminleri için ön işleme featurization kod yazmak zorunda kaydetmedi ve aynı API batch ve tek seferlik tahminleri mvc'deki.</span><span class="sxs-lookup"><span data-stu-id="de924-272">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="de924-273">Model operationalization: tahmin</span><span class="sxs-lookup"><span data-stu-id="de924-273">Model operationalization: prediction</span></span>

<span data-ttu-id="de924-274">Görüntü `SentimentText` ve sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için karşılık gelen düşünceleri tahmin.</span><span class="sxs-lookup"><span data-stu-id="de924-274">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="de924-275">Bu işlem ilkeleri bir parçası olarak döndürülen verileri kullanarak operationalization çağrılır.</span><span class="sxs-lookup"><span data-stu-id="de924-275">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="de924-276">Aşağıdaki kullanarak sonuçları için bir başlık oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="de924-276">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

<span data-ttu-id="de924-277">Tahmin edilen sonuçları görüntülemeden önce düşünceleri ve özgün yorum tahmin edilen düşünceleri ile birlikte görmek için tahmini birleştirin.</span><span class="sxs-lookup"><span data-stu-id="de924-277">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="de924-278">Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A> yöntemini gerçekleşen, sağlamak için bu nedenle bu kodu ekleyin sonraki:</span><span class="sxs-lookup"><span data-stu-id="de924-278">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="de924-279">Birleştirilmiş göre `SentimentText` ve `Sentiment` bir sınıfına kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="de924-279">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

<span data-ttu-id="de924-280">C# 7.0 C# 7.1 ve projeyi varsayılan dil sürümü yeni bir özellik olan tanımlama grubu öğe adları olan olayla olduğundan, C# 7.1 veya üzeri dil sürümü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="de924-280">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="de924-281">Bunu yapmak için proje düğümüne sağ tıklayın **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="de924-281">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="de924-282">Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="de924-282">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="de924-283">Açılır listede seçin **C# 7.1** (veya daha yüksek bir sürüm).</span><span class="sxs-lookup"><span data-stu-id="de924-283">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="de924-284">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="de924-284">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="de924-285">Sonuçları</span><span class="sxs-lookup"><span data-stu-id="de924-285">Results</span></span>

<span data-ttu-id="de924-286">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de924-286">Your results should be similar to the following.</span></span> <span data-ttu-id="de924-287">Ardışık Düzen işleme gibi iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="de924-287">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="de924-288">Uyarı veya işlem iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de924-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="de924-289">Bunlar daha anlaşılır olması için aşağıdaki sonuçları kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="de924-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="de924-290">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="de924-290">Congratulations!</span></span> <span data-ttu-id="de924-291">Sınıflandırma ve iletileri düşünceleri tahmin için makine öğrenimi modeli şimdi başarıyla oluşturuncaya.</span><span class="sxs-lookup"><span data-stu-id="de924-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="de924-292">Bu öğreticinin için kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposu.</span><span class="sxs-lookup"><span data-stu-id="de924-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="de924-293">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="de924-293">Next steps</span></span>

<span data-ttu-id="de924-294">Bu öğreticide, öğrenilen nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="de924-294">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="de924-295">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="de924-295">Understand the problem</span></span>
> * <span data-ttu-id="de924-296">Uygun makine öğrenme görevini seçin</span><span class="sxs-lookup"><span data-stu-id="de924-296">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="de924-297">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="de924-297">Prepare your data</span></span>
> * <span data-ttu-id="de924-298">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="de924-298">Create the learning pipeline</span></span>
> * <span data-ttu-id="de924-299">Bir sınıflandırıcı yükleme</span><span class="sxs-lookup"><span data-stu-id="de924-299">Load a classifier</span></span>
> * <span data-ttu-id="de924-300">Modeli eğitmek</span><span class="sxs-lookup"><span data-stu-id="de924-300">Train the model</span></span>
> * <span data-ttu-id="de924-301">Farklı bir veri kümesi ile modelini değerlendir</span><span class="sxs-lookup"><span data-stu-id="de924-301">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="de924-302">Model ile test veri sonuçlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="de924-302">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="de924-303">Daha fazla bilgi için sonraki öğretici ilerleyin</span><span class="sxs-lookup"><span data-stu-id="de924-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="de924-304">Ücreti bir göstergesi olduğu ücreti</span><span class="sxs-lookup"><span data-stu-id="de924-304">Taxi Fare Predictor</span></span>](taxi-fare.md)
