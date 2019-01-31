---
title: Bir GitHub sorunu sınıflı sınıflandırma senaryosunda ML.NET kullanın
description: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları için belirli bir alanla atamak sınıflandırmak için nasıl kullanılacağını keşfedin.
ms.date: 01/24/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a951e884a7494b0dcc808fc3dafbfadebc5577dc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254996"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="d49b5-103">Öğretici: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları sınıflandırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d49b5-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues.</span></span>

<span data-ttu-id="d49b5-104">Bu örnek öğretici ML.NET kullanarak bir .NET Core konsol uygulaması kullanarak aracılığıyla bir GitHub sorunu sınıflandırıcı oluşturma gösterilmektedir C# Visual Studio 2017'de.</span><span class="sxs-lookup"><span data-stu-id="d49b5-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="d49b5-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="d49b5-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d49b5-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="d49b5-106">Understand the problem</span></span>
> * <span data-ttu-id="d49b5-107">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="d49b5-107">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="d49b5-108">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="d49b5-108">Prepare your data</span></span>
> * <span data-ttu-id="d49b5-109">Öğrenme işlem hattınızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="d49b5-109">Create the learning pipeline</span></span>
> * <span data-ttu-id="d49b5-110">Sınıflandırıcı yükleme</span><span class="sxs-lookup"><span data-stu-id="d49b5-110">Load a classifier</span></span>
> * <span data-ttu-id="d49b5-111">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="d49b5-111">Train the model</span></span>
> * <span data-ttu-id="d49b5-112">Farklı bir veri kümesiyle modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="d49b5-112">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="d49b5-113">Test verileri sonucu modeli ile tek bir örneğini tahmin edin</span><span class="sxs-lookup"><span data-stu-id="d49b5-113">Predict a single instance of test data outcome with the model</span></span>
> * <span data-ttu-id="d49b5-114">Yüklenen modeli test veri sonuçlarını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="d49b5-114">Predict the test data outcomes with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="d49b5-115">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-115">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="d49b5-116">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d49b5-116">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="d49b5-117">GitHub sorunu örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="d49b5-117">GitHub issue sample overview</span></span>

<span data-ttu-id="d49b5-118">Örnek ML.NET sınıflandırır ve bir GitHub sorunu alan etiketini tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-118">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="d49b5-119">Ayrıca, kalite analizi için ikinci bir veri kümesi modeliyle değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-119">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="d49b5-120">Çıkış veri kümeleri dotnet/corefx'te GitHub deposundan ' dir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-120">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d49b5-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d49b5-121">Prerequisites</span></span>

* <span data-ttu-id="d49b5-122">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="d49b5-123">[Github sorunlar sekmeyle dosyası (issues_train.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="d49b5-123">The [Github issues tab separated file (issues_train.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="d49b5-124">[Github sorunları sekmeyle dosyası (issues_test.tsv) test](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="d49b5-124">The [Github issues test tab separated file (issues_test.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="d49b5-125">Machine learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="d49b5-125">Machine learning workflow</span></span>

<span data-ttu-id="d49b5-126">Bu öğreticide, bir makine öğrenimi düzenli bir şekilde taşımak işlem sağlayan bir iş akışı izler.</span><span class="sxs-lookup"><span data-stu-id="d49b5-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="d49b5-127">İş akışı aşamalar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d49b5-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="d49b5-128">**Sorunu anlama**</span><span class="sxs-lookup"><span data-stu-id="d49b5-128">**Understand the problem**</span></span>
2. <span data-ttu-id="d49b5-129">**Verilerinizi hazırlama**</span><span class="sxs-lookup"><span data-stu-id="d49b5-129">**Prepare your data**</span></span>
   * <span data-ttu-id="d49b5-130">**Verileri yükleme**</span><span class="sxs-lookup"><span data-stu-id="d49b5-130">**Load the data**</span></span>
   * <span data-ttu-id="d49b5-131">**Özellikler (verilerinizi dönüştürmek) ayıklayın**</span><span class="sxs-lookup"><span data-stu-id="d49b5-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="d49b5-132">**Derleme ve eğitme**</span><span class="sxs-lookup"><span data-stu-id="d49b5-132">**Build and train**</span></span> 
   * <span data-ttu-id="d49b5-133">**Modeli eğitme**</span><span class="sxs-lookup"><span data-stu-id="d49b5-133">**Train the model**</span></span>
   * <span data-ttu-id="d49b5-134">**Modeli değerlendirme**</span><span class="sxs-lookup"><span data-stu-id="d49b5-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="d49b5-135">**Çalıştır**</span><span class="sxs-lookup"><span data-stu-id="d49b5-135">**Run**</span></span>
   * <span data-ttu-id="d49b5-136">**Model tüketim**</span><span class="sxs-lookup"><span data-stu-id="d49b5-136">**Model consumption**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="d49b5-137">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="d49b5-137">Understand the problem</span></span>

<span data-ttu-id="d49b5-138">Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="d49b5-139">Problemi parçalamak, tahmin edin ve sonuçları değerlendirin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-139">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="d49b5-140">Sorun Bu öğretici için hangi alan gelen GitHub sorunları bunları öncelik belirleme ve planlama için doğru etiket için ait öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-140">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="d49b5-141">Aşağıdaki problemi bölünebilir:</span><span class="sxs-lookup"><span data-stu-id="d49b5-141">You can break down the problem to the following:</span></span>

* <span data-ttu-id="d49b5-142">sorun başlık metni</span><span class="sxs-lookup"><span data-stu-id="d49b5-142">the issue title text</span></span>
* <span data-ttu-id="d49b5-143">Sorun açıklaması metni</span><span class="sxs-lookup"><span data-stu-id="d49b5-143">the issue description text</span></span>
* <span data-ttu-id="d49b5-144">model eğitim verileri için bir alan değeri</span><span class="sxs-lookup"><span data-stu-id="d49b5-144">an area value for the model training data</span></span>
* <span data-ttu-id="d49b5-145">bir tahmin edilen alan değeri değerlendirmek ve işletimsel olarak kullanın</span><span class="sxs-lookup"><span data-stu-id="d49b5-145">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="d49b5-146">Ardından gerek **belirlemek** alanı Görev Seçimi öğrenme makineyle yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d49b5-146">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="d49b5-147">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="d49b5-147">Select the appropriate machine learning task</span></span>

<span data-ttu-id="d49b5-148">Bu sorun aşağıdaki gerçekleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="d49b5-148">With this problem, you know the following facts:</span></span>

<span data-ttu-id="d49b5-149">Eğitim verileri:</span><span class="sxs-lookup"><span data-stu-id="d49b5-149">Training data:</span></span>

<span data-ttu-id="d49b5-150">GitHub sorunları birçok alanda etiketli (**alan**) aşağıdaki örneklerde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-150">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="d49b5-151">alan System.Numerics</span><span class="sxs-lookup"><span data-stu-id="d49b5-151">area-System.Numerics</span></span>
* <span data-ttu-id="d49b5-152">System.Xml alanı</span><span class="sxs-lookup"><span data-stu-id="d49b5-152">area-System.Xml</span></span>
* <span data-ttu-id="d49b5-153">alan altyapı</span><span class="sxs-lookup"><span data-stu-id="d49b5-153">area-Infrastructure</span></span>
* <span data-ttu-id="d49b5-154">alan System.Linq</span><span class="sxs-lookup"><span data-stu-id="d49b5-154">area-System.Linq</span></span>
* <span data-ttu-id="d49b5-155">alan System.IO</span><span class="sxs-lookup"><span data-stu-id="d49b5-155">area-System.IO</span></span>

<span data-ttu-id="d49b5-156">Tahmin **alan** yeni GitHub sorunu aşağıdaki örneklerde olduğu gibi böyle:</span><span class="sxs-lookup"><span data-stu-id="d49b5-156">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="d49b5-157">Debug.Assert Contract.Assert vs</span><span class="sxs-lookup"><span data-stu-id="d49b5-157">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="d49b5-158">System.Xml içinde alanları salt okunur yapın</span><span class="sxs-lookup"><span data-stu-id="d49b5-158">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="d49b5-159">Sınıflandırma machine learning görevi bu senaryo için idealdir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-159">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="d49b5-160">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="d49b5-160">About the classification task</span></span>

<span data-ttu-id="d49b5-161">Sınıflandırma olan verileri kullanan bir makine öğrenimi görev **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d49b5-161">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="d49b5-162">Örneğin, sınıflandırma için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d49b5-162">For example, you can use classification to:</span></span>

* <span data-ttu-id="d49b5-163">Artı veya eksi olarak duyguları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d49b5-163">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="d49b5-164">E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.</span><span class="sxs-lookup"><span data-stu-id="d49b5-164">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="d49b5-165">Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d49b5-165">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="d49b5-166">Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.</span><span class="sxs-lookup"><span data-stu-id="d49b5-166">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="d49b5-167">Sınıflandırma görevleri sık aşağıdaki türlerden biri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d49b5-167">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="d49b5-168">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="d49b5-168">Binary: either A or B.</span></span>
* <span data-ttu-id="d49b5-169">Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="d49b5-169">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="d49b5-170">Sorun kategorisi tahmininizde birden çok kategoriden (veya çoklu sınıflar) olamayacağından bu sorun türünün veya çoklu sınıflar sınıflandırma görevi yerine iki kullanın (ikili).</span><span class="sxs-lookup"><span data-stu-id="d49b5-170">For this type of problem, use a Multiclass classification task, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="d49b5-171">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d49b5-171">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="d49b5-172">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="d49b5-172">Create a project</span></span>

1. <span data-ttu-id="d49b5-173">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="d49b5-173">Open Visual Studio 2017.</span></span> <span data-ttu-id="d49b5-174">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="d49b5-174">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="d49b5-175">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="d49b5-175">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="d49b5-176">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="d49b5-176">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="d49b5-177">İçinde **adı** metin kutusuna "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-177">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="d49b5-178">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="d49b5-178">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="d49b5-179">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="d49b5-179">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="d49b5-180">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d49b5-180">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="d49b5-181">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="d49b5-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="d49b5-182">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="d49b5-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d49b5-183">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="d49b5-184">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="d49b5-184">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="d49b5-185">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="d49b5-185">Prepare your data</span></span>

1. <span data-ttu-id="d49b5-186">İndirme [issues_train.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="d49b5-186">Download the [issues_train.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="d49b5-187">İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-187">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="d49b5-188">Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d49b5-188">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="d49b5-189">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="d49b5-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="d49b5-190">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="d49b5-190">Create classes and define paths</span></span>

<span data-ttu-id="d49b5-191">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="d49b5-191">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="d49b5-192">Kısa bir süre önce indirilen dosyaları ve bir genel değişken için yollar tutmak için üç genel alanlar oluşturmak için ihtiyacınız `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="d49b5-192">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="d49b5-193">`_trainDataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-193">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="d49b5-194">`_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-194">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="d49b5-195">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-195">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="d49b5-196">`_mlContext` olan <xref:Microsoft.ML.MLContext> , işlem bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d49b5-196">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="d49b5-197">`_trainingDataView` olan <xref:Microsoft.ML.Data.IDataView> eğitim veri kümesi işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-197">`_trainingDataView` is the <xref:Microsoft.ML.Data.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="d49b5-198">`_predEngine` olan <xref:Microsoft.ML.PredictionEngine%602> tek Tahminler elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-198">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* <span data-ttu-id="d49b5-199">`_reader` olan <xref:Microsoft.ML.Data.TextLoader> yüklemek ve veri kümeleri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-199">`_reader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="d49b5-200">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollar ve diğer değişkenlerini belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="d49b5-200">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="d49b5-201">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-201">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="d49b5-202">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d49b5-202">Add a new class to your project:</span></span>

1. <span data-ttu-id="d49b5-203">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="d49b5-203">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="d49b5-204">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="d49b5-204">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="d49b5-205">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-205">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d49b5-206">*GitHubIssueData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-206">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="d49b5-207">Aşağıdaki `using` üstüne deyimi *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="d49b5-207">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="d49b5-208">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `GitHubIssue` ve `IssuePrediction`, *GitHubIssueData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="d49b5-208">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="d49b5-209">`GitHubIssue` Giriş veri kümesi sınıfı ve aşağıdaki <xref:System.String> alanlar:</span><span class="sxs-lookup"><span data-stu-id="d49b5-209">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="d49b5-210">`ID` GitHub sorun kimliği için bir değer içeriyor</span><span class="sxs-lookup"><span data-stu-id="d49b5-210">`ID` contains a value for the GitHub issue ID</span></span>
* <span data-ttu-id="d49b5-211">`Area` için bir değer içeren `Area` etiketi</span><span class="sxs-lookup"><span data-stu-id="d49b5-211">`Area` contains a value for the `Area` label</span></span>
* <span data-ttu-id="d49b5-212">`Title` GitHub sorunu başlık içerir</span><span class="sxs-lookup"><span data-stu-id="d49b5-212">`Title` contains the GitHub issue title</span></span>
* <span data-ttu-id="d49b5-213">`Description` GitHub sorun açıklaması içerir</span><span class="sxs-lookup"><span data-stu-id="d49b5-213">`Description` contains the GitHub issue description</span></span>

<span data-ttu-id="d49b5-214">`IssuePrediction` eğitilen modelin sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-214">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="d49b5-215">Tek bir sahip `string` (`Area`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d49b5-215">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="d49b5-216">`Label` Oluşturup modeli ya da onun da model değerlendirmek için ikinci bir veri kümesi ile kullanılan eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-216">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="d49b5-217">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-217">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="d49b5-218">Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-218">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="d49b5-219">ML.NET modeliyle oluştururken oluşturarak başlayın bir <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="d49b5-219">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="d49b5-220">Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d49b5-220">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="d49b5-221">Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilecek ML işiniz için bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="d49b5-221">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="d49b5-222">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="d49b5-222">Initialize variables in Main</span></span>

<span data-ttu-id="d49b5-223">Başlatma `_mlContext` yeni bir örneğini genel değişkenin `MLContext` ile rastgele bir tohum (`seed: 0`) arasında birden çok eğitimleri/deterministic tekrarlanabilir sonuçlar.</span><span class="sxs-lookup"><span data-stu-id="d49b5-223">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="d49b5-224">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-224">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="d49b5-225">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="d49b5-225">Load the data</span></span>

<span data-ttu-id="d49b5-226">Ardından, başlatma `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> genel değişken ve ile veri yükleme `_trainDataPath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-226">Next, initialize the `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="d49b5-227">Giriş ve çıkış olarak `Transforms`, `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="d49b5-227">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="d49b5-228">ML.NET içinde veri benzer bir `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="d49b5-228">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="d49b5-229">Bu, gevşek değerlendirilen, şema ve heterojen olur.</span><span class="sxs-lookup"><span data-stu-id="d49b5-229">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="d49b5-230">Nesne, işlem hattını ilk kısmı ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="d49b5-230">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="d49b5-231">Bu öğreticide, bir veri kümesi sorunu başlıklarını, açıklamaları ve karşılık gelen alan GitHub etiketi ile yükler.</span><span class="sxs-lookup"><span data-stu-id="d49b5-231">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="d49b5-232">`DataView` Oluşturup modeli eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-232">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="d49b5-233">Önceden oluşturduğunuz beri `GitHubIssue` veri modeli türüyle eşleşen veri kümesi şeması, başlatma, eşleme ve veri kümesi bir kod satırının içine yükleniyor birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d49b5-233">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="d49b5-234">Satırın ilk bölümü (`CreateTextReader<GitHubIssue>(hasHeader: true)`) oluşturur bir <xref:Microsoft.ML.Data.TextLoader> çıkarım veri kümesi şeması tarafından gelen `GitHubIssue` veri türü ve veri kümesi üst bilgisini kullanarak model.</span><span class="sxs-lookup"><span data-stu-id="d49b5-234">The first part of the line (`CreateTextReader<GitHubIssue>(hasHeader: true)`) creates a <xref:Microsoft.ML.Data.TextLoader> by inferencing the dataset schema from the `GitHubIssue` data model type and using the dataset header.</span></span>

<span data-ttu-id="d49b5-235">Oluşturduğunuz zaman veri şemasını önceden tanımlanmış `GitHubIssue` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d49b5-235">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="d49b5-236">Şemanızı için:</span><span class="sxs-lookup"><span data-stu-id="d49b5-236">For your schema:</span></span>

* <span data-ttu-id="d49b5-237">İlk sütun `ID` (GitHub sorunu kimliği)</span><span class="sxs-lookup"><span data-stu-id="d49b5-237">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="d49b5-238">ikinci sütunda `Area` (eğitim tahmin)</span><span class="sxs-lookup"><span data-stu-id="d49b5-238">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="d49b5-239">üçüncü sütunda `Title` (GitHub sorun başlığı) sanal makinede ilk [özellik](../resources/glossary.md##feature) tahmin etmek için kullanılan `Area`</span><span class="sxs-lookup"><span data-stu-id="d49b5-239">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the `Area`</span></span>
* <span data-ttu-id="d49b5-240">Dördüncü sütun `Description` tahmin etmek için kullanılan ikinci özelliğidir `Area`</span><span class="sxs-lookup"><span data-stu-id="d49b5-240">the fourth column  `Description` is the second feature used for predicting the `Area`</span></span>

<span data-ttu-id="d49b5-241">Satırın ikinci bölümü (`.Read(_trainDataPath)`) kullanan <xref:Microsoft.ML.Data.TextLoader.Read%2A> eğitim metni yüklemek için gereken yöntemini kullanarak dosya `_trainDataPath` içine `IDataView` (`_trainingDataView`) genel değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d49b5-241">The second part of the line  (`.Read(_trainDataPath)`) uses <xref:Microsoft.ML.Data.TextLoader.Read%2A> method to load the training text file using `_trainDataPath` into the `IDataView` (`_trainingDataView`) global variable.</span></span>  

<span data-ttu-id="d49b5-242">Başlatma ve yüklemek için `_trainingDataView` ardışık düzeni için kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:</span><span class="sxs-lookup"><span data-stu-id="d49b5-242">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]


<span data-ttu-id="d49b5-243">Sonraki kod satırı olarak ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-243">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="d49b5-244">`ProcessData` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d49b5-244">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="d49b5-245">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d49b5-245">Extracts and transforms the data.</span></span>
* <span data-ttu-id="d49b5-246">İşleme işlem hattı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d49b5-246">Returns the processing pipeline.</span></span>

<span data-ttu-id="d49b5-247">Oluşturma `ProcessData` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="d49b5-247">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static EstimatorChain<ITransformer> ProcessData()
{

}
```

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="d49b5-248">Verileri dönüştürme ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="d49b5-248">Extract and transform the data</span></span>

<span data-ttu-id="d49b5-249">Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-249">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="d49b5-250">Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-250">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="d49b5-251">Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-251">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="d49b5-252">ML. NET dönüştürme işlem hatları, verilerinizi, eğitim veya test etmeden önce uygulanan dönüştürmeler özel bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d49b5-252">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="d49b5-253">Veri Dönüşümleri birincil amacı olan [özellik kazandırma sayesinde](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="d49b5-253">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="d49b5-254">Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) metinsel verilerimizi ML algoritmalarınızı tanıyacak bir biçime dönüştürmek için sonraki adım, bu nedenle veri.</span><span class="sxs-lookup"><span data-stu-id="d49b5-254">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="d49b5-255">Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="d49b5-255">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="d49b5-256">Sonraki adımlarda sütunlara adlarıyla tanımlanan diyoruz `GitHubIssue` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d49b5-256">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="d49b5-257">Model eğitim ve diğer değerleri varsayılan olarak, hesaplanan zaman **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-257">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="d49b5-258">Alan GitHub etiketi tahmin etmek istediğimiz bir `GitHubIssue`, kopyalama `Area` sütuna **etiket** sütun.</span><span class="sxs-lookup"><span data-stu-id="d49b5-258">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="d49b5-259">Bunu yapmak için kullanın `MLContext.Transforms.Conversion.MapValueToKey`, bu değer için bir sarmalayıcı <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d49b5-259">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="d49b5-260">`MapValueToKey` Döndürür bir <xref:Microsoft.ML.Data.EstimatorChain%601> bir işlem hattı etkin olacak.</span><span class="sxs-lookup"><span data-stu-id="d49b5-260">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="d49b5-261">Bu ad `pipeline` eğitmen için ardından ekleyeceği şekilde `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="d49b5-261">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="d49b5-262">Bu, sonraki kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d49b5-262">Add this as the next line of code:</span></span>

[!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="d49b5-263">Modeli eğitir algoritması **sayısal** yanında, böylece özellikleri çağrı `mlContext.Transforms.Text.FeaturizeText` hangi featurizes metni (`Title` ve `Description`) sayısal bir vektör her adlı sütuna `TitleFeaturized` ve `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="d49b5-263">The algorithm that trains the model requires **numeric** features, so you have Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="d49b5-264">Featurizing farklı değerler her sütun için farklı sayısal anahtar değerleri atar ve makine öğrenme algoritmasına tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-264">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span>
<span data-ttu-id="d49b5-265">Aşağıdaki kod ile işlem hattı her iki sütun için özellik kazandırma sayesinde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d49b5-265">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="d49b5-266">Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak `Concatenate` dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d49b5-266">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="d49b5-267">Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="d49b5-267">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="d49b5-268">Aşağıdaki kod ile işlem hattı için bu dönüşümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d49b5-268">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="d49b5-269">Ardından, ekleme bir <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> üzerinden yineleme yapma, verileri birden çok kez önbellek kullanarak daha iyi performans için şu kod gibi alabilirsiniz şekilde DataView önbelleğe almak için</span><span class="sxs-lookup"><span data-stu-id="d49b5-269">Next, append a <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code</span></span>

[!code-csharp[AppendCache](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

<span data-ttu-id="d49b5-270">Ardışık Düzen sonunda dönüş `ProcessData` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-270">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="d49b5-271">Bu adımda, ön işleme/özellik kazandırma sayesinde işler.</span><span class="sxs-lookup"><span data-stu-id="d49b5-271">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="d49b5-272">ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d49b5-272">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="d49b5-273">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="d49b5-273">Build and train the model</span></span>

<span data-ttu-id="d49b5-274">Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-274">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="d49b5-275">`BuildAndTrainModel` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d49b5-275">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="d49b5-276">Eğitim algoritması sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d49b5-276">Creates the training algorithm class.</span></span>
* <span data-ttu-id="d49b5-277">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-277">Trains the model.</span></span>
* <span data-ttu-id="d49b5-278">Eğitim verilerini temel alarak alan tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="d49b5-278">Predicts area based on training data.</span></span>
* <span data-ttu-id="d49b5-279">Modele kaydeder bir `.zip` dosya.</span><span class="sxs-lookup"><span data-stu-id="d49b5-279">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="d49b5-280">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="d49b5-280">Returns the model.</span></span>

<span data-ttu-id="d49b5-281">Oluşturma `BuildAndTrainModel` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="d49b5-281">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static void BuildAndTrainModel()
{

}
```

<span data-ttu-id="d49b5-282">İki parametre BuildAndTrainModel yönteme geçirilen dikkat edin; bir `IDataView` eğitim veri kümesi için (`trainingDataView`) ve <xref:Microsoft.ML.Data.EstimatorChain%601> ProcessData içinde oluşturulan işleme işlem hattının (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="d49b5-282">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="d49b5-283">İlk satırı olarak aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-283">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-trainer-algorithm"></a><span data-ttu-id="d49b5-284">Eğitmen algoritma seçme</span><span class="sxs-lookup"><span data-stu-id="d49b5-284">Choose a trainer algorithm</span></span>

<span data-ttu-id="d49b5-285">Eğitmen algoritması eklemek için çağrı `mlContext.Transforms.Text.FeaturizeText` döndüren sarmalayıcı yöntemini bir <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> nesne.</span><span class="sxs-lookup"><span data-stu-id="d49b5-285">To add the trainer algorithm, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span> <span data-ttu-id="d49b5-286">Bu işlem hattında kullanacağınız karar ağacı learner budur.</span><span class="sxs-lookup"><span data-stu-id="d49b5-286">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="d49b5-287">`SdcaMultiClassTrainer` Eklenir `pipeline` ve özellikleri tespit `Title` ve `Description` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="d49b5-287">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="d49b5-288">Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-288">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[SdcaMultiClassTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SdcaMultiClassTrainer)]

<span data-ttu-id="d49b5-289">Eğitmen algoritması oluşturduğunuza göre eklenecek `pipeline`.</span><span class="sxs-lookup"><span data-stu-id="d49b5-289">Now that you've created a trainer algorithm, append it to the `pipeline`.</span></span> <span data-ttu-id="d49b5-290">Ayrıca okunabilir özgün durumuna döndürülecek değer etiketi eşlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-290">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="d49b5-291">Aşağıdaki kod ile bu eylemlerin her ikisini birden yapın:</span><span class="sxs-lookup"><span data-stu-id="d49b5-291">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="d49b5-292">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="d49b5-292">Train the model</span></span>

<span data-ttu-id="d49b5-293">Modeli eğitme <xref:Microsoft.ML.Data.TransformerChain%601>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-293">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="d49b5-294">Tahmin tanımlandıktan sonra kullanarak modelinize eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> zaten yüklenmiş eğitim verilerini sağlayarak.</span><span class="sxs-lookup"><span data-stu-id="d49b5-294">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="d49b5-295">Bu tahminler elde etmek için kullanılacak bir modelini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d49b5-295">This returns a model to use for predictions.</span></span> <span data-ttu-id="d49b5-296">`trainingPipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-296">`trainingPipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="d49b5-297">Denemeyi böyle kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d49b5-297">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="d49b5-298">Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-298">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="d49b5-299">Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-299">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="d49b5-300"><xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-300">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="d49b5-301">Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` sonraki satırı olarak `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-301">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="d49b5-302">Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="d49b5-302">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="d49b5-303">Bu tahmin etmek için kullanabileceğiniz `Area` sorun verileri tek bir örneğini etiketi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-303">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="d49b5-304">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="d49b5-304">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="d49b5-305">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d49b5-305">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="d49b5-306">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="d49b5-306">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="d49b5-307">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-307">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="d49b5-308">Modeli kullanıma hazır hale getirme: tahmin</span><span class="sxs-lookup"><span data-stu-id="d49b5-308">Model operationalization: prediction</span></span>

<span data-ttu-id="d49b5-309">Görüntü `GitHubIssue` ve karşılık gelen `Area` tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için etiket.</span><span class="sxs-lookup"><span data-stu-id="d49b5-309">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="d49b5-310">Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-310">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="d49b5-311">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="d49b5-311">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="d49b5-312">Kaydet ve değerlendirme için kullanılacak modeli eğitilir dön</span><span class="sxs-lookup"><span data-stu-id="d49b5-312">Save and return the model trained to use for evaluation</span></span>

<span data-ttu-id="d49b5-313">Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain%601> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine.</span><span class="sxs-lookup"><span data-stu-id="d49b5-313">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="d49b5-314">Eğitilen model bir .zip dosyası olarak kaydetmek için çağırmak için aşağıdaki kodu ekleyin. `SaveModelAsFile` yöntemi olarak bir sonraki satırda `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="d49b5-314">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

<span data-ttu-id="d49b5-315">Model sonunda dönüş `BuildAndTrainModel` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-315">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="d49b5-316">Modeli a.zip dosyası olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d49b5-316">Save the model as a.zip file</span></span>

<span data-ttu-id="d49b5-317">Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `BuildAndTrainModel` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="d49b5-317">Create the `SaveModelAsFile` method, just after the `BuildAndTrainModel` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="d49b5-318">`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d49b5-318">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="d49b5-319">Model bir .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d49b5-319">Saves the model as a .zip file.</span></span>

<span data-ttu-id="d49b5-320">Ardından, yeniden kullanılabilir ve diğer uygulamalarda kullanılan model kaydetmek için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d49b5-320">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="d49b5-321">`ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="d49b5-321">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="d49b5-322">Bu zip dosyası olarak kaydetmek için oluşturacağınız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-322">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="d49b5-323">Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="d49b5-323">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="d49b5-324">Bir konsol iletisi ile yazarak dosyasının nerede yazılmıştır görüntüleyebilir `_modelPath`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="d49b5-324">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="d49b5-325">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="d49b5-325">Evaluate the model</span></span>

<span data-ttu-id="d49b5-326">Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-326">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="d49b5-327">İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `BuildAndTrainModel` değerlendirilecek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-327">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="d49b5-328">Oluşturma `Evaluate` yöntemi hemen sonrasına `BuildAndTrainModel`, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-328">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="d49b5-329">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d49b5-329">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="d49b5-330">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="d49b5-330">Loads the test dataset.</span></span>
* <span data-ttu-id="d49b5-331">Çok sınıflı değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d49b5-331">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="d49b5-332">Model değerlendirir ve metrikleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="d49b5-332">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="d49b5-333">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d49b5-333">Displays the metrics.</span></span>

<span data-ttu-id="d49b5-334">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `BuildAndTrainModel` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="d49b5-334">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="d49b5-335">Eğitim veri kümesi ile daha önce yaptığınız gibi eşleme başlatma birleştirin ve sınama veri kümesi bir kod satırının içine yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="d49b5-335">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="d49b5-336">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-336">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="d49b5-337">Aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d49b5-337">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="d49b5-338">`MulticlassClassificationContext.Evaluate` İçin bir sarmalayıcı olan <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A> belirtilen veri kümesi kullanan model için Kalite Ölçümleri hesaplar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d49b5-338">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="d49b5-339">Döndürür bir <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> sınıflı sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="d49b5-339">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="d49b5-340">Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-340">To display these to determine the quality of the model, you need to get the metrics first.</span></span>
<span data-ttu-id="d49b5-341">Kullanımına dikkat edin `Transform` machine Learning yöntemi `_trainedModel` özellikleri giriş ve tahmin döndürmek için genel değişkeni (dönüştürücü).</span><span class="sxs-lookup"><span data-stu-id="d49b5-341">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="d49b5-342">Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="d49b5-342">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="d49b5-343">Aşağıdaki ölçümler sınıflı sınıflandırma için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="d49b5-343">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="d49b5-344">Mikro doğruluğu - her örnek sınıfı çifti eşit doğruluğu ölçüme katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d49b5-344">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="d49b5-345">Mikro doğruluğu, 1 olarak mümkün olduğunca yakın olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="d49b5-345">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="d49b5-346">Makro doğruluğu - her sınıf eşit doğruluğu ölçüme katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d49b5-346">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="d49b5-347">Azınlık sınıfları daha büyük bir sınıf olarak eşit ağırlık verilir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-347">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="d49b5-348">Makrosu 1 olarak mümkün olduğunca yakın olmasını doğruluğu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-348">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="d49b5-349">Günlük zarar - bkz [günlük kaybı](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="d49b5-349">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="d49b5-350">Sıfır olarak mümkün olduğunca yakın olmasını günlük zarar kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-350">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="d49b5-351">Günlük kaybı azaltma - aralıkları gelen [-INF, 100], burada 100 mükemmel Öngörüler ve 0, ortalama Öngörüler gösterir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-351">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="d49b5-352">Günlük kaybı azaltma sıfır olarak mümkün olduğunca yakın olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="d49b5-352">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="d49b5-353">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d49b5-353">Displaying the metrics for model validation</span></span>

<span data-ttu-id="d49b5-354">Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d49b5-354">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="d49b5-355">Kaydedilen modeli ile test veri sonucu tahmin edin</span><span class="sxs-lookup"><span data-stu-id="d49b5-355">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="d49b5-356">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="d49b5-356">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="d49b5-357">Oluşturma `PredictIssue` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="d49b5-357">Create the `PredictIssue` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="d49b5-358">`PredictIssue` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d49b5-358">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="d49b5-359">Test verilerini tek bir konu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d49b5-359">Creates a single issue of test data.</span></span>
* <span data-ttu-id="d49b5-360">Test verilerini temel alarak alan tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="d49b5-360">Predicts Area based on test data.</span></span>
* <span data-ttu-id="d49b5-361">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="d49b5-361">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="d49b5-362">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d49b5-362">Displays the predicted results.</span></span>

<span data-ttu-id="d49b5-363">İlk olarak, aşağıdaki kod ile daha önce kaydettiğiniz model yüklenemiyor:</span><span class="sxs-lookup"><span data-stu-id="d49b5-363">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="d49b5-364">Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="d49b5-364">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="d49b5-365">Bir modeliniz olduğuna göre tek bir GitHub sorunu veri örneğini alan GitHub etiketini tahmin etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d49b5-365">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="d49b5-366">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="d49b5-366">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="d49b5-367">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d49b5-367">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="d49b5-368">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="d49b5-368">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="d49b5-369">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="d49b5-369">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="d49b5-370">Aşağıdaki kodu ekleyin `PredictIssue` yöntemi tahminler elde etmek için:</span><span class="sxs-lookup"><span data-stu-id="d49b5-370">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="d49b5-371">Modeli kullanıma hazır hale getirme: tahmin</span><span class="sxs-lookup"><span data-stu-id="d49b5-371">Model operationalization: prediction</span></span>

<span data-ttu-id="d49b5-372">Görüntü `Area` sorunu kategorilere ayırmak ve buna göre hareket üzerinde için.</span><span class="sxs-lookup"><span data-stu-id="d49b5-372">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="d49b5-373">Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-373">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="d49b5-374">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="d49b5-374">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="d49b5-375">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="d49b5-375">Results</span></span>

<span data-ttu-id="d49b5-376">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-376">Your results should be similar to the following.</span></span> <span data-ttu-id="d49b5-377">İşlem hattı işlediği gibi iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d49b5-377">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="d49b5-378">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d49b5-378">You may see warnings, or processing messages.</span></span> <span data-ttu-id="d49b5-379">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d49b5-379">These have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="d49b5-380">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="d49b5-380">Congratulations!</span></span> <span data-ttu-id="d49b5-381">Bir machine learning modeli sınıflandırmak ve bir alan etiketini bir GitHub sorunu için tahmin etmek için şimdi başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="d49b5-381">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="d49b5-382">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.</span><span class="sxs-lookup"><span data-stu-id="d49b5-382">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d49b5-383">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d49b5-383">Next steps</span></span>

<span data-ttu-id="d49b5-384">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="d49b5-384">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d49b5-385">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="d49b5-385">Understand the problem</span></span>
> * <span data-ttu-id="d49b5-386">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="d49b5-386">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="d49b5-387">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="d49b5-387">Prepare your data</span></span>
> * <span data-ttu-id="d49b5-388">Öğrenme işlem hattınızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="d49b5-388">Create the learning pipeline</span></span>
> * <span data-ttu-id="d49b5-389">Sınıflandırıcı yükleme</span><span class="sxs-lookup"><span data-stu-id="d49b5-389">Load a classifier</span></span>
> * <span data-ttu-id="d49b5-390">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="d49b5-390">Train the model</span></span>
> * <span data-ttu-id="d49b5-391">Farklı bir veri kümesiyle modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="d49b5-391">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="d49b5-392">Modeli ile test veri sonuçlarını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="d49b5-392">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="d49b5-393">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="d49b5-393">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d49b5-394">Taksi taksi göstergesi</span><span class="sxs-lookup"><span data-stu-id="d49b5-394">Taxi Fare Predictor</span></span>](taxi-fare.md)
