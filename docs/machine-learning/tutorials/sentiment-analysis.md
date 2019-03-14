---
title: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu
description: ML.NET ikili sınıflandırma senaryoda yaklaşım tahmin uygun eylemde için nasıl kullanılacağını anlamak için nasıl kullanılacağını keşfedin.
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d94e254f0cdf56c21c94012f824f05a550e4da2f
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788472"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="3f409-103">Öğretici: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu</span><span class="sxs-lookup"><span data-stu-id="3f409-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

<span data-ttu-id="3f409-104">Bu örnek öğretici ML.NET kullanarak bir .NET Core konsol uygulaması kullanarak aracılığıyla pozitif veya negatif yaklaşım tahmin etmek için bir yaklaşım sınıflandırıcı oluşturma gösterilmektedir C# Visual Studio 2017'de.</span><span class="sxs-lookup"><span data-stu-id="3f409-104">This sample tutorial illustrates using ML.NET to create a sentiment classifier to predict either positive or negative sentiment via a .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="3f409-105">Machine learning dünyasında, bu tür bir tahmin ikili sınıflandırma bilinir.</span><span class="sxs-lookup"><span data-stu-id="3f409-105">In the world of machine learning, this type of prediction is known as binary classification.</span></span>

> [!NOTE]
> <span data-ttu-id="3f409-106">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3f409-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="3f409-107">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="3f409-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="3f409-108">Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.11**.</span><span class="sxs-lookup"><span data-stu-id="3f409-108">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="3f409-109">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="3f409-109">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="3f409-110">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="3f409-110">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3f409-111">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="3f409-111">Understand the problem</span></span>
> * <span data-ttu-id="3f409-112">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="3f409-112">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="3f409-113">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="3f409-113">Prepare your data</span></span>
> * <span data-ttu-id="3f409-114">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3f409-114">Transform the data</span></span>
> * <span data-ttu-id="3f409-115">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="3f409-115">Train the model</span></span>
> * <span data-ttu-id="3f409-116">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="3f409-116">Evaluate the model</span></span>
> * <span data-ttu-id="3f409-117">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="3f409-117">Predict with the trained model</span></span>
> * <span data-ttu-id="3f409-118">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="3f409-118">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="3f409-119">Yaklaşım analizi örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="3f409-119">Sentiment analysis sample overview</span></span>

<span data-ttu-id="3f409-120">Örnek ML.NET sınıflandırır ve yaklaşım artı veya eksi olarak tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="3f409-120">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="3f409-121">California Üniversitesi, Irvine (hangi train veri kümesi ve bir test veri kümesini halinde bölme UCI), Yelp yaklaşım dataset arasındadır.</span><span class="sxs-lookup"><span data-stu-id="3f409-121">The Yelp sentiment dataset is from University of California, Irvine (UCI), which is split into a train dataset and a test dataset.</span></span> <span data-ttu-id="3f409-122">Örnek kalite analizi için test veri modeliyle değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="3f409-122">The sample evaluates the model with the test dataset for quality analysis.</span></span> 

<span data-ttu-id="3f409-123">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="3f409-123">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f409-124">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3f409-124">Prerequisites</span></span>

* <span data-ttu-id="3f409-125">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3f409-125">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="3f409-126">UCI yaklaşım cümleler etiketli veri kümesini zip dosyası</span><span class="sxs-lookup"><span data-stu-id="3f409-126">The UCI Sentiment Labeled Sentences dataset zip file</span></span>](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a><span data-ttu-id="3f409-127">Machine learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="3f409-127">Machine learning workflow</span></span>

<span data-ttu-id="3f409-128">Bu öğreticide, bir makine öğrenimi düzenli bir şekilde taşımak işlem sağlayan bir iş akışı izler.</span><span class="sxs-lookup"><span data-stu-id="3f409-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="3f409-129">İş akışı aşamalar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3f409-129">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="3f409-130">**Sorunu anlama**</span><span class="sxs-lookup"><span data-stu-id="3f409-130">**Understand the problem**</span></span>
2. <span data-ttu-id="3f409-131">**Verilerinizi hazırlama**</span><span class="sxs-lookup"><span data-stu-id="3f409-131">**Prepare your data**</span></span>
   * <span data-ttu-id="3f409-132">**Verileri yükleme**</span><span class="sxs-lookup"><span data-stu-id="3f409-132">**Load the data**</span></span>
   * <span data-ttu-id="3f409-133">**Özellikler (verilerinizi dönüştürmek) ayıklayın**</span><span class="sxs-lookup"><span data-stu-id="3f409-133">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="3f409-134">**Derleme ve eğitme**</span><span class="sxs-lookup"><span data-stu-id="3f409-134">**Build and train**</span></span> 
   * <span data-ttu-id="3f409-135">**Modeli eğitme**</span><span class="sxs-lookup"><span data-stu-id="3f409-135">**Train the model**</span></span>
   * <span data-ttu-id="3f409-136">**Modeli değerlendirme**</span><span class="sxs-lookup"><span data-stu-id="3f409-136">**Evaluate the model**</span></span>
4. <span data-ttu-id="3f409-137">**Model dağıtma**</span><span class="sxs-lookup"><span data-stu-id="3f409-137">**Deploy Model**</span></span>
   * <span data-ttu-id="3f409-138">**Tahmin modelini kullanın**</span><span class="sxs-lookup"><span data-stu-id="3f409-138">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="3f409-139">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="3f409-139">Understand the problem</span></span>

<span data-ttu-id="3f409-140">Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f409-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="3f409-141">Sorun bozucu, tahmin edin ve sonuçları değerlendirin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3f409-141">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="3f409-142">Sorun Bu öğretici için uygun eylemi gerçekleştirin gelen Web sitesi açıklama yaklaşım öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="3f409-142">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="3f409-143">Problemi yaklaşım metin ve duyarlılık değeri ile modeli eğitmek için istediğiniz verileri için ve tahmin edilen duyarlılık değeri değerlendirmek ve işletimsel olarak kullanmak dökümünü alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f409-143">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="3f409-144">Ardından gerek **belirlemek** yaklaşımı, Görev Seçimi öğrenme makineyle yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="3f409-144">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="3f409-145">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="3f409-145">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="3f409-146">Bu sorun aşağıdaki gerçekleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="3f409-146">With this problem, you know the following facts:</span></span>

<span data-ttu-id="3f409-147">Eğitim verileri: Web sitesi açıklamaları pozitif olabilir (1) veya negatif (0) (**yaklaşım**).</span><span class="sxs-lookup"><span data-stu-id="3f409-147">Training data: website comments can be positive (1) or negative (0) (**sentiment**).</span></span>

<span data-ttu-id="3f409-148">Tahmin **yaklaşım** açıklamasının bir yeni Web sitesi, pozitif veya negatif gibi aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="3f409-148">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="3f409-149">Burada bekleme Hastanenin seviyorum.</span><span class="sxs-lookup"><span data-stu-id="3f409-149">I love the wait staff here.</span></span> <span data-ttu-id="3f409-150">Bunlar Kaya.</span><span class="sxs-lookup"><span data-stu-id="3f409-150">They rock.</span></span>
* <span data-ttu-id="3f409-151">Burası, en kötü A'dan sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3f409-151">This place has the worst soup.</span></span>

<span data-ttu-id="3f409-152">Sınıflandırma makine öğrenimi algoritmasının bu senaryo için idealdir.</span><span class="sxs-lookup"><span data-stu-id="3f409-152">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-algorithm"></a><span data-ttu-id="3f409-153">Sınıflandırma algoritmasıdır hakkında</span><span class="sxs-lookup"><span data-stu-id="3f409-153">About the classification algorithm</span></span>

<span data-ttu-id="3f409-154">Sınıflandırma olan verileri kullanan bir machine learning algoritmasını **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3f409-154">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="3f409-155">Örneğin, sınıflandırma için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3f409-155">For example, you can use classification to:</span></span>

* <span data-ttu-id="3f409-156">Artı veya eksi olarak duyguları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3f409-156">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="3f409-157">E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.</span><span class="sxs-lookup"><span data-stu-id="3f409-157">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="3f409-158">Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3f409-158">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="3f409-159">Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.</span><span class="sxs-lookup"><span data-stu-id="3f409-159">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="3f409-160">Sınıflandırma algoritmaları sık aşağıdaki türlerden biri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3f409-160">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="3f409-161">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="3f409-161">Binary: either A or B.</span></span>
* <span data-ttu-id="3f409-162">Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="3f409-162">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="3f409-163">Web sitesi açıklamaları pozitif veya negatif olarak sınıflandırılması gerektiğinden, ikili sınıflandırma algoritmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f409-163">Because the website comments need to be classified as either positive or negative, you use the Binary Classification algorithm.</span></span> 

## <a name="create-a-console-application"></a><span data-ttu-id="3f409-164">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3f409-164">Create a console application</span></span>

1. <span data-ttu-id="3f409-165">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="3f409-165">Open Visual Studio 2017.</span></span> <span data-ttu-id="3f409-166">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="3f409-166">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="3f409-167">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="3f409-167">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="3f409-168">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="3f409-168">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="3f409-169">İçinde **adı** metin kutusuna "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3f409-169">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="3f409-170">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="3f409-170">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="3f409-171">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="3f409-171">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="3f409-172">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3f409-172">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="3f409-173">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="3f409-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="3f409-174">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="3f409-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="3f409-175">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3f409-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="3f409-176">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="3f409-176">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="3f409-177">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="3f409-177">Prepare your data</span></span>

1. <span data-ttu-id="3f409-178">İndirme [UCI yaklaşım cümleler etiketli veri kümesini zip dosyası (alıntıları aşağıdaki nota bakın)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="3f409-178">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="3f409-179">Kopyalama `yelp_labelled.txt` doyasını *veri* oluşturduğunuz dizin.</span><span class="sxs-lookup"><span data-stu-id="3f409-179">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

> [!NOTE]
> <span data-ttu-id="3f409-180">Bu öğreticide veri kümeleri Kotzias 'kaynak grubundan ayrıntılı özelliklerini kullanarak her bir etiketi için' olan et.</span><span class="sxs-lookup"><span data-stu-id="3f409-180">The datasets this tutorial uses are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="3f409-181">Al.</span><span class="sxs-lookup"><span data-stu-id="3f409-181">al,.</span></span> <span data-ttu-id="3f409-182">2015 ve barındırılan KDD UCI Machine Learning deposu - Dua, d ve Karra Taniskidou, e (2017).</span><span class="sxs-lookup"><span data-stu-id="3f409-182">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="3f409-183">UCI Makine deposu [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="3f409-183">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="3f409-184">Irvine, CA: California Üniversitesi, okul bilgi ve bilgisayar Bilimine.</span><span class="sxs-lookup"><span data-stu-id="3f409-184">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

3. <span data-ttu-id="3f409-185">Çözüm Gezgini'nde sağ `yelp_labeled.txt` seçin ve dosya **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="3f409-185">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="3f409-186">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="3f409-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="3f409-187">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="3f409-187">Create classes and define paths</span></span>

<span data-ttu-id="3f409-188">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="3f409-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="3f409-189">En son indirilen veri kümesi dosyası yolu ve kayıtlı modeli dosya yolu tutmak için iki genel alanlar oluşturmak ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="3f409-189">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="3f409-190">`_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3f409-190">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="3f409-191">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="3f409-191">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="3f409-192">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="3f409-192">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="3f409-193">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f409-193">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="3f409-194">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3f409-194">Add a new class to your project:</span></span>

1. <span data-ttu-id="3f409-195">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="3f409-195">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="3f409-196">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="3f409-196">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="3f409-197">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3f409-197">Then, select the **Add** button.</span></span>

    <span data-ttu-id="3f409-198">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="3f409-198">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="3f409-199">Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="3f409-199">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="3f409-200">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="3f409-200">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="3f409-201">Giriş veri kümesi sınıfı `SentimentData`, sahip bir `string` Açıklama (`SentimentText`) ve bir `bool` (`Sentiment`) pozitif veya negatif yaklaşım için bir değer olan.</span><span class="sxs-lookup"><span data-stu-id="3f409-201">The input dataset class, `SentimentData`, has a `string` for the comment (`SentimentText`) and a `bool` (`Sentiment`) that has a value for sentiment of either positive or negative.</span></span> <span data-ttu-id="3f409-202">Her iki alanınız <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> öznitelikleri kendisine bağlı.</span><span class="sxs-lookup"><span data-stu-id="3f409-202">Both fields have <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> attributes attached to them.</span></span> <span data-ttu-id="3f409-203">Bu öznitelik veri dosyasındaki her bir alanın sırasını anlatır.</span><span class="sxs-lookup"><span data-stu-id="3f409-203">This attribute describes the order of each field in the data file.</span></span>  <span data-ttu-id="3f409-204">Ayrıca, `Sentiment` özelliğine sahip bir <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> olarak belirlemek için `Label` alan.</span><span class="sxs-lookup"><span data-stu-id="3f409-204">In addition, the `Sentiment` property has a <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> to designate it as the `Label` field.</span></span> <span data-ttu-id="3f409-205">`SentimentPrediction` eğitilen modelin sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f409-205">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="3f409-206">Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3f409-206">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="3f409-207">`Label` Oluşturabilir ve ayrıca bölünmüş test veri kümesini kullanıma ile model değerlendirmek için kullanılan model ya da onun eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f409-207">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="3f409-208">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f409-208">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="3f409-209">Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f409-209">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="3f409-210">ML.NET modeliyle oluştururken oluşturarak başlayın bir <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="3f409-210">When building a model with ML.NET you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="3f409-211">`MLContext` kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="3f409-211">`MLContext` is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="3f409-212">Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilecek ML işiniz için bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f409-212">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="3f409-213">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="3f409-213">Initialize variables in Main</span></span>

<span data-ttu-id="3f409-214">Adlı bir değişken oluşturma `mlContext` ve yeni bir örneğini ile başlatma `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="3f409-214">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="3f409-215">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-215">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

<span data-ttu-id="3f409-216">Sonraki kod satırı olarak ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-216">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallLoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

<span data-ttu-id="3f409-217">`LoadData` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="3f409-217">The `LoadData` method executes the following tasks:</span></span>

* <span data-ttu-id="3f409-218">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="3f409-218">Loads the data.</span></span>
* <span data-ttu-id="3f409-219">Yüklenen veri kümesi train böler ve test edin, veri kümeleri.</span><span class="sxs-lookup"><span data-stu-id="3f409-219">Splits the loaded dataset into train and test datasets.</span></span>
* <span data-ttu-id="3f409-220">Bölme döndürür eğitme ve test etme, veri kümeleri.</span><span class="sxs-lookup"><span data-stu-id="3f409-220">Returns the split train and test datasets.</span></span>

<span data-ttu-id="3f409-221">Oluşturma `LoadData` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-221">Create the `LoadData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static (IDataView trainSet, IDataView testSet) LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a><span data-ttu-id="3f409-222">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="3f409-222">Load the data</span></span>

<span data-ttu-id="3f409-223">Önceden oluşturduğunuz beri `SentimentData` veri modeli türüyle eşleşen veri kümesi şeması, başlatma, eşleme ve veri kümesi bir satır kod kullanarak yüklerken Birleştir `MLContext.Data.ReadFromTextFile` için sarmalayıcı <xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="3f409-223">Since your previously created `SentimentData` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code using the `MLContext.Data.ReadFromTextFile` wrapper for <xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29>.</span></span> <span data-ttu-id="3f409-224">Döndürür bir <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="3f409-224">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> 

 <span data-ttu-id="3f409-225">Giriş ve çıkış olarak `Transforms`, `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="3f409-225">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="3f409-226">ML.NET veriler SQL görünümüne benzer.</span><span class="sxs-lookup"><span data-stu-id="3f409-226">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="3f409-227">Bu, gevşek değerlendirilen, şema ve heterojen olur.</span><span class="sxs-lookup"><span data-stu-id="3f409-227">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="3f409-228">Nesne, işlem hattını ilk kısmı ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="3f409-228">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="3f409-229">Bu öğreticide, açıklama ve karşılık gelen toxic veya olmayan toxic yaklaşım bir veri kümesine yükler.</span><span class="sxs-lookup"><span data-stu-id="3f409-229">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="3f409-230">Bu model oluşturmayı ve bunu eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f409-230">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="3f409-231">İlk satırı olarak aşağıdaki kodu ekleyin `LoadData` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-231">Add the following code as the first line of the `LoadData` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="3f409-232">Eğitim ve test modeli için veri kümesi bölünemiyor</span><span class="sxs-lookup"><span data-stu-id="3f409-232">Split the dataset for model training and testing</span></span>

<span data-ttu-id="3f409-233">Ardından, hem bir eğitim veri kümesi modeli eğitmek için hem de model değerlendirmek için test veri kümesini gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f409-233">Next, you need both a training dataset to train the model and a test dataset to evaluate the model.</span></span> <span data-ttu-id="3f409-234">Kullanım `MLContext.BinaryClassification.TrainTestSplit` sarmalayan <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> train yüklenen veri kümesi bölün ve veri kümeleri sınayabilir ve bunları içine bir <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>.</span><span class="sxs-lookup"><span data-stu-id="3f409-234">Use the `MLContext.BinaryClassification.TrainTestSplit` which wraps <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> to split the loaded dataset into train and test datasets and return them inside of a <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>.</span></span> <span data-ttu-id="3f409-235">Test kümesi için kısa bir veri belirtebilirsiniz `testFraction`parametresi.</span><span class="sxs-lookup"><span data-stu-id="3f409-235">You can specify the fraction of data for the test set with the `testFraction`parameter.</span></span> <span data-ttu-id="3f409-236">Varsayılan % 10'dur ancak, % 20 Bu durumda daha fazla veri Değerlendirme amacıyla kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f409-236">The default is 10% but you use 20% in this case to use more data for the evaluation.</span></span>  

<span data-ttu-id="3f409-237">Yüklenen verilere gerekli veri kümelerine ayırmak için bir sonraki satırda olarak aşağıdaki kodu ekleyin `LoadData` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-237">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData` method:</span></span>

[!code-csharp[SplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

<span data-ttu-id="3f409-238">Dönüş `splitDataView` sonunda `LoadData` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-238">Return the `splitDataView` at the end of the `LoadData` method:</span></span>

[!code-csharp[ReturnSplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="3f409-239">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="3f409-239">Build and train the model</span></span>

<span data-ttu-id="3f409-240">Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-240">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="3f409-241">`BuildAndTrainModel` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="3f409-241">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="3f409-242">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3f409-242">Extracts and transforms the data.</span></span>
* <span data-ttu-id="3f409-243">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="3f409-243">Trains the model.</span></span>
* <span data-ttu-id="3f409-244">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="3f409-244">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="3f409-245">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="3f409-245">Returns the model.</span></span>

<span data-ttu-id="3f409-246">Oluşturma `BuildAndTrainModel` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-246">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

<span data-ttu-id="3f409-247">İki parametre Train yönteme geçirilen dikkat edin; bir `MLContext` bağlamının (`mlContext`) ve bir `IDataView`eğitim veri kümesi için (`splitTrainSet`).</span><span class="sxs-lookup"><span data-stu-id="3f409-247">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and an `IDataView`for the training dataset (`splitTrainSet`).</span></span> 

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="3f409-248">Verileri dönüştürme ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="3f409-248">Extract and transform the data</span></span>

<span data-ttu-id="3f409-249">Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="3f409-249">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="3f409-250">Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f409-250">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="3f409-251">Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f409-251">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="3f409-252">ML. NET dönüştürme işlem hatları, verilerinizi, eğitim veya test etmeden önce uygulanan dönüştürmeler özel bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f409-252">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="3f409-253">Veri Dönüşümleri birincil amacı olan [özellik kazandırma sayesinde](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="3f409-253">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="3f409-254">Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) metinsel verilerimizi ML algoritmalarınızı tanıyacak bir biçime dönüştürmek için sonraki adım, bu nedenle veri.</span><span class="sxs-lookup"><span data-stu-id="3f409-254">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="3f409-255">Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="3f409-255">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="3f409-256">Ardından, arama `mlContext.Transforms.Text.FeaturizeText` hangi featurizes metin sütununu (`SentimentText`) adı verilen sayısal bir vektör sütununa `Features` makine öğrenimi algoritması tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="3f409-256">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="3f409-257">Bu döndüren bir sarmalayıcı çağrısı, bir <xref:Microsoft.ML.Data.EstimatorChain%601> bir işlem hattı etkin olacak.</span><span class="sxs-lookup"><span data-stu-id="3f409-257">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="3f409-258">Bu ad `pipeline` eğitmen için ardından ekleyeceği şekilde `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="3f409-258">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="3f409-259">Bu, sonraki kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3f409-259">Add this as the next line of code:</span></span>

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> <span data-ttu-id="3f409-260">ML.NET sürüm 0.10 dönüştürme parametrelerinin sırasını değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="3f409-260">ML.NET Version 0.10 changed the order of the Transform parameters.</span></span> <span data-ttu-id="3f409-261">Bu, kullanıma alma hatası kadar uygulamayı çalıştırın ve model derleme.</span><span class="sxs-lookup"><span data-stu-id="3f409-261">This will not error out until you run the application and build the model.</span></span> <span data-ttu-id="3f409-262">Dönüşümlerin parametre adları, önceki kod parçacığında gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f409-262">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="3f409-263">Bu ön işleme/özellik kazandırma sayesinde adımdır.</span><span class="sxs-lookup"><span data-stu-id="3f409-263">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="3f409-264">ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f409-264">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="3f409-265">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="3f409-265">Choose a learning algorithm</span></span>

<span data-ttu-id="3f409-266">Eğitmen eklemek için çağrı `mlContext.BinaryClassification.Trainers.FastTree` döndüren sarmalayıcı yöntemini bir <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> nesne.</span><span class="sxs-lookup"><span data-stu-id="3f409-266">To add the trainer, call the `mlContext.BinaryClassification.Trainers.FastTree` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="3f409-267">Bu işlem hattında kullanacağınız karar ağacı learner budur.</span><span class="sxs-lookup"><span data-stu-id="3f409-267">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="3f409-268">`FastTreeBinaryClassificationTrainer` Eklenir `pipeline` ve özellikleri tespit `SentimentText` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="3f409-268">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="3f409-269">Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-269">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="3f409-270">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="3f409-270">Train the model</span></span>

<span data-ttu-id="3f409-271">Modeli eğitme <xref:Microsoft.ML.Data.TransformerChain%601>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="3f409-271">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="3f409-272">Tahmin tanımlandıktan sonra kullanarak modelinize eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> zaten yüklenmiş eğitim verilerini sağlayarak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f409-272">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> method while providing the already loaded training data.</span></span> <span data-ttu-id="3f409-273">Bu tahminler elde etmek için kullanılacak bir modelini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3f409-273">This returns a model to use for predictions.</span></span> <span data-ttu-id="3f409-274">`pipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi.</span><span class="sxs-lookup"><span data-stu-id="3f409-274">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="3f409-275">Denemeyi kadar yürütülmez `.Fit()` yöntemi çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f409-275">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="3f409-276">Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-276">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="3f409-277">Kaydet ve değerlendirme için kullanılacak modeli eğitilir dön</span><span class="sxs-lookup"><span data-stu-id="3f409-277">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="3f409-278">Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain%601> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine.</span><span class="sxs-lookup"><span data-stu-id="3f409-278">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="3f409-279">Model sonunda dönüş `BuildAndTrainModel` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f409-279">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="3f409-280">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="3f409-280">Evaluate the model</span></span>

<span data-ttu-id="3f409-281">Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f409-281">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="3f409-282">İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `BuildAndTrainModel` değerlendirilecek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3f409-282">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="3f409-283">Oluşturma `Evaluate` yöntemi hemen sonrasına `BuildAndTrainModel`, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="3f409-283">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

<span data-ttu-id="3f409-284">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="3f409-284">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="3f409-285">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="3f409-285">Loads the test dataset.</span></span>
* <span data-ttu-id="3f409-286">Binaryclassification değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f409-286">Creates the binaryclassification evaluator.</span></span>
* <span data-ttu-id="3f409-287">Model değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f409-287">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="3f409-288">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3f409-288">Displays the metrics.</span></span>

<span data-ttu-id="3f409-289">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-289">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

<span data-ttu-id="3f409-290">Ardından, makine öğrenimi kullanacağınız `model` parametre (dönüştürücü) ve `splitTestSet` özellikleri giriş ve tahmin döndürmek için parametre.</span><span class="sxs-lookup"><span data-stu-id="3f409-290">Next, you'll use the machine learning `model` parameter (a transformer) and the `splitTestSet` parameter to input the features and return predictions.</span></span> <span data-ttu-id="3f409-291">Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-291">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

<span data-ttu-id="3f409-292">`mlContext.BinaryClassification.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma.</span><span class="sxs-lookup"><span data-stu-id="3f409-292">The `mlContext.BinaryClassification.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="3f409-293">Döndürür bir <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> ikili sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="3f409-293">It returns a <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> object that contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="3f409-294">Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f409-294">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="3f409-295">Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-295">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="3f409-296">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="3f409-296">Displaying the metrics for model validation</span></span>

<span data-ttu-id="3f409-297">Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="3f409-297">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

<span data-ttu-id="3f409-298">Modelinizi dönmeden önce bir .zip dosyası olarak kaydetmek için çağırmak için aşağıdaki kodu ekleyin. `SaveModelAsFile` yöntemi olarak bir sonraki satırda `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="3f409-298">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="3f409-299">Modeli a.zip dosyası olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3f409-299">Save the model as a.zip file</span></span>

<span data-ttu-id="3f409-300">Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-300">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="3f409-301">`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="3f409-301">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="3f409-302">Model bir .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3f409-302">Saves the model as a .zip file.</span></span>

<span data-ttu-id="3f409-303">Ardından, yeniden kullanılabilir ve diğer uygulamalarda kullanılan model kaydetmek için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f409-303">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="3f409-304">`ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="3f409-304">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="3f409-305">Bu zip dosyası olarak kaydetmek için oluşturacağınız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f409-305">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="3f409-306">Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-306">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="3f409-307">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="3f409-307">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="3f409-308">Bir konsol iletisi ile yazarak dosyasının nerede yazılmıştır görüntüleyebilir `_modelPath`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-308">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="3f409-309">Kaydedilen modeli ile test veri sonucu tahmin edin</span><span class="sxs-lookup"><span data-stu-id="3f409-309">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="3f409-310">Oluşturma `UseModelWithSingleItem` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-310">Create the `UseModelWithSingleItem` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="3f409-311">`UseModelWithSingleItem` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="3f409-311">The `UseModelWithSingleItem` method executes the following tasks:</span></span>

* <span data-ttu-id="3f409-312">Test verilerini tek bir yorum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f409-312">Creates a single comment of test data.</span></span>
* <span data-ttu-id="3f409-313">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="3f409-313">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="3f409-314">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="3f409-314">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="3f409-315">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3f409-315">Displays the predicted results.</span></span>

<span data-ttu-id="3f409-316">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-316">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallUseModelWithSingleItem](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

<span data-ttu-id="3f409-317">Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f409-317">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="3f409-318"><xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f409-318">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="3f409-319">Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` ilk satırı olarak `Predict` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-319">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
<span data-ttu-id="3f409-320">Eğitilen modelin tahmine test etmek için bir açıklama ekleyin `Predict` bir örneğini oluşturarak yöntemi `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="3f409-320">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 <span data-ttu-id="3f409-321">Bu açıklama verilerini tek bir örneğini pozitif veya negatif duyarlılığını tahmin etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f409-321">You can use that to predict the positive or negative sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="3f409-322">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="3f409-322">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="3f409-323">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3f409-323">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="3f409-324">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="3f409-324">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="3f409-325">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="3f409-325">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a><span data-ttu-id="3f409-326">Model kullanmak: tahmin</span><span class="sxs-lookup"><span data-stu-id="3f409-326">Use the model: prediction</span></span>

<span data-ttu-id="3f409-327">Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için.</span><span class="sxs-lookup"><span data-stu-id="3f409-327">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="3f409-328">Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3f409-328">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="3f409-329">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="3f409-329">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="3f409-330">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="3f409-330">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="3f409-331">Oluşturma `UseLoadedModelWithBatchItems` yöntemi hemen önce `SaveModelAsFile` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-331">Create the `UseLoadedModelWithBatchItems` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

<span data-ttu-id="3f409-332">`UseLoadedModelWithBatchItems` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="3f409-332">The `UseLoadedModelWithBatchItems` method executes the following tasks:</span></span>

* <span data-ttu-id="3f409-333">Toplu test verilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f409-333">Creates batch test data.</span></span>
* <span data-ttu-id="3f409-334">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="3f409-334">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="3f409-335">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="3f409-335">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="3f409-336">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3f409-336">Displays the predicted results.</span></span>

<span data-ttu-id="3f409-337">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `UseModelWithSingleItem` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3f409-337">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

<span data-ttu-id="3f409-338">Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `UseLoadedModelWithBatchItems` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-338">Add some comments to test the trained model's predictions in the `UseLoadedModelWithBatchItems` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

<span data-ttu-id="3f409-339">Model yüklenemiyor</span><span class="sxs-lookup"><span data-stu-id="3f409-339">Load the model</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

<span data-ttu-id="3f409-340">Bir modeliniz olduğuna göre yorum kullanarak veri Toxic veya olmayan Toxic yaklaşım tahmin etmek için kullanabileceğiniz <xref:Microsoft.ML.ITransformer.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f409-340">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="3f409-341">Bir öngörü almak için kullanın `Predict` yeni veriler.</span><span class="sxs-lookup"><span data-stu-id="3f409-341">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="3f409-342">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3f409-342">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="3f409-343">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="3f409-343">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="3f409-344">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="3f409-344">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="3f409-345">Aşağıdaki kodu ekleyin `UseLoadedModelWithBatchItems` yöntemi tahminler elde etmek için:</span><span class="sxs-lookup"><span data-stu-id="3f409-345">Add the following code to the `UseLoadedModelWithBatchItems` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a><span data-ttu-id="3f409-346">Tahmin için yüklenen modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="3f409-346">Use the loaded model for prediction</span></span>

<span data-ttu-id="3f409-347">Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için.</span><span class="sxs-lookup"><span data-stu-id="3f409-347">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="3f409-348">Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3f409-348">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="3f409-349">Aşağıdakileri kullanarak sonuçları için bir başlık oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="3f409-349">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="3f409-350">Tahmin edilen sonuçlarını görüntülemeden önce yaklaşımını ve özgün açıklamayı, tahmin edilen yaklaşım ile birlikte görmek için tahmini birleştirin.</span><span class="sxs-lookup"><span data-stu-id="3f409-350">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="3f409-351">Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A> gerçekleşen, yapmanız gereken yöntemini bu nedenle bu kodunu ekleyin sonraki:</span><span class="sxs-lookup"><span data-stu-id="3f409-351">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="3f409-352">Birleştirilmiş göre `SentimentText` ve `Sentiment` bir sınıf kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3f409-352">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

<span data-ttu-id="3f409-353">C# 7.0 C# 7.1 ve projenin varsayılan dil sürümü yeni bir özellik olan demet öğesi adları olan olayla olduğundan, C# 7.1 veya üzeri dil sürümünü değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f409-353">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="3f409-354">Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="3f409-354">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="3f409-355">Seçin **derleme** sekmenize **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3f409-355">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="3f409-356">Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm).</span><span class="sxs-lookup"><span data-stu-id="3f409-356">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="3f409-357">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="3f409-357">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="3f409-358">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="3f409-358">Results</span></span>

<span data-ttu-id="3f409-359">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f409-359">Your results should be similar to the following.</span></span> <span data-ttu-id="3f409-360">İşlem hattı işlediği gibi iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3f409-360">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="3f409-361">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f409-361">You may see warnings, or processing messages.</span></span> <span data-ttu-id="3f409-362">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3f409-362">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="3f409-363">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="3f409-363">Congratulations!</span></span> <span data-ttu-id="3f409-364">Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="3f409-364">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> 

<span data-ttu-id="3f409-365">Başarılı modeller oluşturma yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="3f409-365">Building successful models is an iterative process.</span></span> <span data-ttu-id="3f409-366">Bu model düşük ilk kalite hızlı modeli eğitimi sağlamak için öğretici kullanan küçük veri kümeleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3f409-366">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="3f409-367">Model kalitesi memnun değilseniz daha büyük bir eğitim veri kümeleri sağlama veya farklı hyper-parametreleriyle her bir algoritmanın için farklı eğitim algoritmalarıyla seçerek geliştirmek deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f409-367">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span>

<span data-ttu-id="3f409-368">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="3f409-368">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f409-369">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3f409-369">Next steps</span></span>

<span data-ttu-id="3f409-370">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="3f409-370">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3f409-371">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="3f409-371">Understand the problem</span></span>
> * <span data-ttu-id="3f409-372">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="3f409-372">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="3f409-373">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="3f409-373">Prepare your data</span></span>
> * <span data-ttu-id="3f409-374">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3f409-374">Transform the data</span></span>
> * <span data-ttu-id="3f409-375">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="3f409-375">Train the model</span></span>
> * <span data-ttu-id="3f409-376">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="3f409-376">Evaluate the model</span></span>
> * <span data-ttu-id="3f409-377">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="3f409-377">Predict with the trained model</span></span>
> * <span data-ttu-id="3f409-378">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="3f409-378">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="3f409-379">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="3f409-379">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3f409-380">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="3f409-380">Issue Classification</span></span>](github-issue-classification.md)
