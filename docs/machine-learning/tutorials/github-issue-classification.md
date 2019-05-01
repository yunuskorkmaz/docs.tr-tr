---
title: Bir GitHub sorunu sınıflı sınıflandırma senaryosunda ML.NET kullanın
description: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları için belirli bir alanla atamak sınıflandırmak için nasıl kullanılacağını keşfedin.
ms.date: 03/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e25f044247064db26e4e1e74590d6f4970fe4477
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019132"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="8c675-103">Öğretici: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları sınıflandırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c675-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues</span></span>

<span data-ttu-id="8c675-104">Bu örnek öğretici ML.NET kullanarak bir .NET Core konsol uygulaması kullanarak aracılığıyla bir GitHub sorunu sınıflandırıcı oluşturma gösterilmektedir C# Visual Studio 2017'de.</span><span class="sxs-lookup"><span data-stu-id="8c675-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="8c675-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="8c675-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8c675-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="8c675-106">Understand the problem</span></span>
> * <span data-ttu-id="8c675-107">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="8c675-107">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="8c675-108">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="8c675-108">Prepare your data</span></span>
> * <span data-ttu-id="8c675-109">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8c675-109">Transform the data</span></span>
> * <span data-ttu-id="8c675-110">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8c675-110">Train the model</span></span>
> * <span data-ttu-id="8c675-111">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8c675-111">Evaluate the model</span></span>
> * <span data-ttu-id="8c675-112">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="8c675-112">Predict with the trained model</span></span>
> * <span data-ttu-id="8c675-113">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="8c675-113">Deploy and Predict with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="8c675-114">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="8c675-114">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="8c675-115">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8c675-115">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="8c675-116">Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.11**.</span><span class="sxs-lookup"><span data-stu-id="8c675-116">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="8c675-117">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="8c675-117">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="8c675-118">GitHub sorunu örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="8c675-118">GitHub issue sample overview</span></span>

<span data-ttu-id="8c675-119">Örnek ML.NET sınıflandırır ve bir GitHub sorunu alan etiketini tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8c675-119">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="8c675-120">Ayrıca, kalite analizi için ikinci bir veri kümesi modeliyle değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8c675-120">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="8c675-121">Çıkış veri kümeleri dotnet/corefx'te GitHub deposundan ' dir.</span><span class="sxs-lookup"><span data-stu-id="8c675-121">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

<span data-ttu-id="8c675-122">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.</span><span class="sxs-lookup"><span data-stu-id="8c675-122">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c675-123">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8c675-123">Prerequisites</span></span>

* <span data-ttu-id="8c675-124">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8c675-124">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="8c675-125">[Github sorunlar sekmeyle dosyası (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="8c675-125">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="8c675-126">[Github sorunları sekmeyle dosyası (issues_test.tsv) test](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="8c675-126">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="8c675-127">Machine learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="8c675-127">Machine learning workflow</span></span>

<span data-ttu-id="8c675-128">Bu öğreticide, bir makine öğrenimi düzenli bir şekilde taşımak işlem sağlayan bir iş akışı izler.</span><span class="sxs-lookup"><span data-stu-id="8c675-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="8c675-129">İş akışı aşamalar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8c675-129">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="8c675-130">**Sorunu anlama**</span><span class="sxs-lookup"><span data-stu-id="8c675-130">**Understand the problem**</span></span>
2. <span data-ttu-id="8c675-131">**Verilerinizi hazırlama**</span><span class="sxs-lookup"><span data-stu-id="8c675-131">**Prepare your data**</span></span>
   * <span data-ttu-id="8c675-132">**Verileri yükleme**</span><span class="sxs-lookup"><span data-stu-id="8c675-132">**Load the data**</span></span>
   * <span data-ttu-id="8c675-133">**Özellikler (verilerinizi dönüştürmek) ayıklayın**</span><span class="sxs-lookup"><span data-stu-id="8c675-133">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="8c675-134">**Derleme ve eğitme**</span><span class="sxs-lookup"><span data-stu-id="8c675-134">**Build and train**</span></span> 
   * <span data-ttu-id="8c675-135">**Modeli eğitme**</span><span class="sxs-lookup"><span data-stu-id="8c675-135">**Train the model**</span></span>
   * <span data-ttu-id="8c675-136">**Modeli değerlendirme**</span><span class="sxs-lookup"><span data-stu-id="8c675-136">**Evaluate the model**</span></span>
4. <span data-ttu-id="8c675-137">**Model dağıtma**</span><span class="sxs-lookup"><span data-stu-id="8c675-137">**Deploy Model**</span></span>
   * <span data-ttu-id="8c675-138">**Tahmin modelini kullanın**</span><span class="sxs-lookup"><span data-stu-id="8c675-138">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="8c675-139">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="8c675-139">Understand the problem</span></span>

<span data-ttu-id="8c675-140">Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c675-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="8c675-141">Problemi parçalamak, tahmin edin ve sonuçları değerlendirin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8c675-141">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="8c675-142">Sorun Bu öğretici için hangi alan gelen GitHub sorunları bunları öncelik belirleme ve planlama için doğru etiket için ait öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="8c675-142">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="8c675-143">İçin aşağıdaki bölümleri problemi bölünebilir:</span><span class="sxs-lookup"><span data-stu-id="8c675-143">You can break down the problem to the following parts:</span></span>

* <span data-ttu-id="8c675-144">sorun başlık metni</span><span class="sxs-lookup"><span data-stu-id="8c675-144">the issue title text</span></span>
* <span data-ttu-id="8c675-145">Sorun açıklaması metni</span><span class="sxs-lookup"><span data-stu-id="8c675-145">the issue description text</span></span>
* <span data-ttu-id="8c675-146">model eğitim verileri için bir alan değeri</span><span class="sxs-lookup"><span data-stu-id="8c675-146">an area value for the model training data</span></span>
* <span data-ttu-id="8c675-147">bir tahmin edilen alan değeri değerlendirmek ve işletimsel olarak kullanın</span><span class="sxs-lookup"><span data-stu-id="8c675-147">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="8c675-148">Ardından gerek **belirlemek** alanı Görev Seçimi öğrenme makineyle yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="8c675-148">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="8c675-149">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="8c675-149">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="8c675-150">Bu sorun aşağıdaki gerçekleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="8c675-150">With this problem, you know the following facts:</span></span>

<span data-ttu-id="8c675-151">Eğitim verileri:</span><span class="sxs-lookup"><span data-stu-id="8c675-151">Training data:</span></span>

<span data-ttu-id="8c675-152">GitHub sorunları birçok alanda etiketli (**alan**) aşağıdaki örneklerde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="8c675-152">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="8c675-153">alan System.Numerics</span><span class="sxs-lookup"><span data-stu-id="8c675-153">area-System.Numerics</span></span>
* <span data-ttu-id="8c675-154">System.Xml alanı</span><span class="sxs-lookup"><span data-stu-id="8c675-154">area-System.Xml</span></span>
* <span data-ttu-id="8c675-155">alan altyapı</span><span class="sxs-lookup"><span data-stu-id="8c675-155">area-Infrastructure</span></span>
* <span data-ttu-id="8c675-156">alan System.Linq</span><span class="sxs-lookup"><span data-stu-id="8c675-156">area-System.Linq</span></span>
* <span data-ttu-id="8c675-157">alan System.IO</span><span class="sxs-lookup"><span data-stu-id="8c675-157">area-System.IO</span></span>

<span data-ttu-id="8c675-158">Tahmin **alan** yeni GitHub sorunu aşağıdaki örneklerde olduğu gibi böyle:</span><span class="sxs-lookup"><span data-stu-id="8c675-158">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="8c675-159">Debug.Assert Contract.Assert vs</span><span class="sxs-lookup"><span data-stu-id="8c675-159">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="8c675-160">System.Xml içinde alanları salt okunur yapın</span><span class="sxs-lookup"><span data-stu-id="8c675-160">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="8c675-161">Sınıflandırma makine öğrenimi algoritmasının bu senaryo için idealdir.</span><span class="sxs-lookup"><span data-stu-id="8c675-161">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-learning-algorithm"></a><span data-ttu-id="8c675-162">Sınıflandırma öğrenme algoritmasını hakkında</span><span class="sxs-lookup"><span data-stu-id="8c675-162">About the classification learning algorithm</span></span>

<span data-ttu-id="8c675-163">Sınıflandırma olan verileri kullanan bir machine learning algoritmasını **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c675-163">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="8c675-164">Örneğin, sınıflandırma için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c675-164">For example, you can use classification to:</span></span>

* <span data-ttu-id="8c675-165">Artı veya eksi olarak duyguları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="8c675-165">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="8c675-166">E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.</span><span class="sxs-lookup"><span data-stu-id="8c675-166">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="8c675-167">Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8c675-167">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="8c675-168">Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.</span><span class="sxs-lookup"><span data-stu-id="8c675-168">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="8c675-169">Sınıflandırma öğrenme algoritmasını kullanım durumları olan sık aşağıdaki türlerden biri:</span><span class="sxs-lookup"><span data-stu-id="8c675-169">Classification learning algorithm use cases are frequently one of the following types:</span></span>

* <span data-ttu-id="8c675-170">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="8c675-170">Binary: either A or B.</span></span>
* <span data-ttu-id="8c675-171">Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="8c675-171">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="8c675-172">Bu sorun türü için birden çok kategoriden (veya çoklu sınıflar) sorun kategorisi tahmininizde olabileceği algoritması, öğrenme veya çoklu sınıflar sınıflandırması yalnızca iki yerine kullanın (ikili).</span><span class="sxs-lookup"><span data-stu-id="8c675-172">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="8c675-173">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c675-173">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="8c675-174">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c675-174">Create a project</span></span>

1. <span data-ttu-id="8c675-175">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="8c675-175">Open Visual Studio 2017.</span></span> <span data-ttu-id="8c675-176">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="8c675-176">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="8c675-177">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="8c675-177">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="8c675-178">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="8c675-178">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="8c675-179">İçinde **adı** metin kutusuna "GitHubIssueClassification" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8c675-179">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="8c675-180">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="8c675-180">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="8c675-181">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="8c675-181">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="8c675-182">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8c675-182">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="8c675-183">Adlı bir dizin oluşturmak *modelleri* modelinizi kaydetmek için projenizde:</span><span class="sxs-lookup"><span data-stu-id="8c675-183">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="8c675-184">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="8c675-184">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="8c675-185">"Modeli" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8c675-185">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="8c675-186">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="8c675-186">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="8c675-187">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="8c675-187">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8c675-188">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8c675-188">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="8c675-189">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="8c675-189">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="8c675-190">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="8c675-190">Prepare your data</span></span>

1. <span data-ttu-id="8c675-191">İndirme [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="8c675-191">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="8c675-192">İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8c675-192">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="8c675-193">Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="8c675-193">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="8c675-194">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="8c675-194">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="8c675-195">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c675-195">Create classes and define paths</span></span>

<span data-ttu-id="8c675-196">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="8c675-196">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="8c675-197">Yolları kısa bir süre önce indirilen dosyaları ve genel değişkenleri tutmak için üç genel alanlar oluşturmak `MLContext`,`DataView`, `PredictionEngine`, ve `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="8c675-197">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, `PredictionEngine`, and `TextLoader`:</span></span>

* <span data-ttu-id="8c675-198">`_trainDataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8c675-198">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="8c675-199">`_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8c675-199">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="8c675-200">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="8c675-200">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="8c675-201">`_mlContext` olan <xref:Microsoft.ML.MLContext> , işlem bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c675-201">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="8c675-202">`_trainingDataView` olan <xref:Microsoft.Data.DataView.IDataView> eğitim veri kümesi işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-202">`_trainingDataView` is the <xref:Microsoft.Data.DataView.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="8c675-203">`_predEngine` olan <xref:Microsoft.ML.PredictionEngine%602> tek Tahminler elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-203">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* <span data-ttu-id="8c675-204">`_reader` olan <xref:Microsoft.ML.Data.TextLoader> yüklemek ve veri kümeleri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-204">`_reader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="8c675-205">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollar ve diğer değişkenlerini belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="8c675-205">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="8c675-206">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8c675-206">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="8c675-207">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8c675-207">Add a new class to your project:</span></span>

1. <span data-ttu-id="8c675-208">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="8c675-208">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="8c675-209">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="8c675-209">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="8c675-210">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8c675-210">Then, select the **Add** button.</span></span>

    <span data-ttu-id="8c675-211">*GitHubIssueData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-211">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="8c675-212">Aşağıdaki `using` üstüne deyimi *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="8c675-212">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="8c675-213">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `GitHubIssue` ve `IssuePrediction`, *GitHubIssueData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="8c675-213">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="8c675-214">`GitHubIssue` Giriş veri kümesi sınıfı ve aşağıdaki <xref:System.String> alanlar:</span><span class="sxs-lookup"><span data-stu-id="8c675-214">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="8c675-215">`ID` GitHub sorun kimliği için bir değer içeriyor</span><span class="sxs-lookup"><span data-stu-id="8c675-215">`ID` contains a value for the GitHub issue ID</span></span>
* <span data-ttu-id="8c675-216">`Area` için bir değer içeren `Area` etiketi</span><span class="sxs-lookup"><span data-stu-id="8c675-216">`Area` contains a value for the `Area` label</span></span>
* <span data-ttu-id="8c675-217">`Title` GitHub sorunu başlık içerir</span><span class="sxs-lookup"><span data-stu-id="8c675-217">`Title` contains the GitHub issue title</span></span>
* <span data-ttu-id="8c675-218">`Description` GitHub sorun açıklaması içerir</span><span class="sxs-lookup"><span data-stu-id="8c675-218">`Description` contains the GitHub issue description</span></span>

<span data-ttu-id="8c675-219">`IssuePrediction` eğitilen modelin sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-219">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="8c675-220">Tek bir sahip `string` (`Area`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8c675-220">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="8c675-221">`Label` Oluşturup modeli ya da onun da model değerlendirmek için ikinci bir veri kümesi ile kullanılan eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-221">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="8c675-222">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-222">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="8c675-223">Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-223">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="8c675-224">ML.NET modeliyle oluştururken oluşturarak başlayın bir <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="8c675-224">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="8c675-225">`MLContext` kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="8c675-225">`MLContext` is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="8c675-226">Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilecek ML işiniz için bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c675-226">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="8c675-227">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="8c675-227">Initialize variables in Main</span></span>

<span data-ttu-id="8c675-228">Başlatma `_mlContext` yeni bir örneğini genel değişkenin `MLContext` ile rastgele bir tohum (`seed: 0`) arasında birden çok eğitimleri/deterministic tekrarlanabilir sonuçlar.</span><span class="sxs-lookup"><span data-stu-id="8c675-228">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="8c675-229">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8c675-229">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="8c675-230">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="8c675-230">Load the data</span></span>

<span data-ttu-id="8c675-231">Ardından, başlatma `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> genel değişken ve ile veri yükleme `_trainDataPath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8c675-231">Next, initialize the `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="8c675-232">Giriş ve çıkış olarak [ `Transforms` ](../basic-concepts-model-training-in-mldotnet.md#transformer), `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="8c675-232">As the input and output of [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer), a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="8c675-233">ML.NET içinde veri benzer bir `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="8c675-233">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="8c675-234">Bu, gevşek değerlendirilen, şema ve heterojen olur.</span><span class="sxs-lookup"><span data-stu-id="8c675-234">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="8c675-235">Nesne, işlem hattını ilk kısmı ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="8c675-235">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="8c675-236">Bu öğreticide, bir veri kümesi sorunu başlıklarını, açıklamaları ve karşılık gelen alan GitHub etiketi ile yükler.</span><span class="sxs-lookup"><span data-stu-id="8c675-236">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="8c675-237">`DataView` Oluşturup modeli eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-237">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="8c675-238">Önceden oluşturduğunuz beri `GitHubIssue` veri modeli türüyle eşleşen veri kümesi şeması, başlatma, eşleme ve veri kümesi bir kod satırının içine yükleniyor birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c675-238">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="8c675-239">Kullanarak verileri yüklemek `MLContext.Data.LoadFromTextFile` için sarmalayıcı [LoadFromTextFile yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="8c675-239">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="8c675-240">Döndürür bir <xref:Microsoft.Data.DataView.IDataView> veri kümesi şema çıkarsar `GitHubIssue` veri türü model ve veri kümesi başlık kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c675-240">It returns a <xref:Microsoft.Data.DataView.IDataView> which infers the dataset schema from the `GitHubIssue` data model type and uses the dataset header.</span></span> 

<span data-ttu-id="8c675-241">Oluşturduğunuz zaman veri şemasını önceden tanımlanmış `GitHubIssue` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c675-241">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="8c675-242">Şemanızı için:</span><span class="sxs-lookup"><span data-stu-id="8c675-242">For your schema:</span></span>

* <span data-ttu-id="8c675-243">İlk sütun `ID` (GitHub sorunu kimliği)</span><span class="sxs-lookup"><span data-stu-id="8c675-243">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="8c675-244">ikinci sütunda `Area` (eğitim tahmin)</span><span class="sxs-lookup"><span data-stu-id="8c675-244">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="8c675-245">üçüncü sütunda `Title` (GitHub sorun başlığı) sanal makinede ilk [özellik](../resources/glossary.md##feature) tahmin etmek için kullanılan `Area`</span><span class="sxs-lookup"><span data-stu-id="8c675-245">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the `Area`</span></span>
* <span data-ttu-id="8c675-246">Dördüncü sütun `Description` tahmin etmek için kullanılan ikinci özelliğidir `Area`</span><span class="sxs-lookup"><span data-stu-id="8c675-246">the fourth column  `Description` is the second feature used for predicting the `Area`</span></span>

<span data-ttu-id="8c675-247">Başlatma ve yüklemek için `_trainingDataView` ardışık düzeni için kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:</span><span class="sxs-lookup"><span data-stu-id="8c675-247">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="8c675-248">Sonraki kod satırı olarak ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8c675-248">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="8c675-249">`ProcessData` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8c675-249">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="8c675-250">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8c675-250">Extracts and transforms the data.</span></span>
* <span data-ttu-id="8c675-251">İşleme işlem hattı döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c675-251">Returns the processing pipeline.</span></span>

<span data-ttu-id="8c675-252">Oluşturma `ProcessData` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8c675-252">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="8c675-253">Özellikleri ayıklayın ve verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8c675-253">Extract Features and transform the data</span></span>

<span data-ttu-id="8c675-254">Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="8c675-254">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="8c675-255">Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="8c675-255">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="8c675-256">Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8c675-256">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="8c675-257">ML. NET dönüştürme işlem hatları oluşturma özel `transforms`eğitim veya test etmeden önce verilerinizi uygulanan kümesi.</span><span class="sxs-lookup"><span data-stu-id="8c675-257">ML.NET's transform pipelines compose a custom `transforms`set that is applied to your data before training or testing.</span></span> <span data-ttu-id="8c675-258">Veri Dönüşümleri birincil amacı olan [özellik kazandırma sayesinde](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="8c675-258">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="8c675-259">Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) metinsel verilerimizi ML algoritmalarınızı tanıyacak bir biçime dönüştürmek için sonraki adım, bu nedenle veri.</span><span class="sxs-lookup"><span data-stu-id="8c675-259">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="8c675-260">Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="8c675-260">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="8c675-261">Sonraki adımlarda sütunlara adlarıyla tanımlanan diyoruz `GitHubIssue` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c675-261">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="8c675-262">Model eğitim ve diğer değerleri varsayılan olarak, hesaplanan zaman **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8c675-262">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="8c675-263">Alan GitHub etiketi tahmin etmek istediğimiz bir `GitHubIssue`, kopyalama `Area` sütuna **etiket** sütun.</span><span class="sxs-lookup"><span data-stu-id="8c675-263">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="8c675-264">Bunu yapmak için kullanın `MLContext.Transforms.Conversion.MapValueToKey`, bu değer için bir sarmalayıcı <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c675-264">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="8c675-265">`MapValueToKey` Döndürür bir <xref:Microsoft.ML.Data.EstimatorChain%601> bir işlem hattı etkin olacak.</span><span class="sxs-lookup"><span data-stu-id="8c675-265">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="8c675-266">Bu ad `pipeline` eğitmen için ardından ekleyeceği şekilde `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="8c675-266">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="8c675-267">Sonraki kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8c675-267">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 <span data-ttu-id="8c675-268">Featurizing farklı değerler her sütun için farklı sayısal anahtar değerleri atar ve makine öğrenme algoritmasına tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c675-268">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span> <span data-ttu-id="8c675-269">Ardından, arama `mlContext.Transforms.Text.FeaturizeText` hangi featurizes metni (`Title` ve `Description`) sayısal bir vektör her adlı sütuna `TitleFeaturized` ve `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="8c675-269">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="8c675-270">Aşağıdaki kod ile işlem hattı her iki sütun için özellik kazandırma sayesinde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8c675-270">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> <span data-ttu-id="8c675-271">ML.NET sürüm 0.10 dönüştürme parametreleri sırası değişti.</span><span class="sxs-lookup"><span data-stu-id="8c675-271">ML.NET Version 0.10 has changed the order of the Transform parameters.</span></span> <span data-ttu-id="8c675-272">Bu, kullanıma alma hatası, yapı kadar.</span><span class="sxs-lookup"><span data-stu-id="8c675-272">This will not error out until you build.</span></span> <span data-ttu-id="8c675-273">Dönüşümlerin parametre adları, önceki kod parçacığında gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c675-273">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="8c675-274">Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak `Concatenate` dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c675-274">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="8c675-275">Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="8c675-275">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="8c675-276">Aşağıdaki kod ile işlem hattı için bu dönüşümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8c675-276">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="8c675-277">Ardından, ekleme bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> üzerinden yineleme yapma, verileri birden çok kez önbellek kullanarak daha iyi performans için şu kod gibi alabilirsiniz şekilde DataView önbelleğe almak için:</span><span class="sxs-lookup"><span data-stu-id="8c675-277">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="8c675-278">Eğitim süresini azaltmak için AppendCacheCheckpoint küçük/Orta veri kümeleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c675-278">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="8c675-279">(Kaldırın. bunu kullanmayın Çok büyük veri kümelerinde işlerken AppendCacheCheckpoint()).</span><span class="sxs-lookup"><span data-stu-id="8c675-279">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="8c675-280">Ardışık Düzen sonunda dönüş `ProcessData` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c675-280">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="8c675-281">Bu adımda, ön işleme/özellik kazandırma sayesinde işler.</span><span class="sxs-lookup"><span data-stu-id="8c675-281">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="8c675-282">ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c675-282">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="8c675-283">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8c675-283">Build and train the model</span></span>

<span data-ttu-id="8c675-284">Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8c675-284">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="8c675-285">`BuildAndTrainModel` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8c675-285">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="8c675-286">Eğitim algoritması sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c675-286">Creates the training algorithm class.</span></span>
* <span data-ttu-id="8c675-287">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="8c675-287">Trains the model.</span></span>
* <span data-ttu-id="8c675-288">Eğitim verilerini temel alarak alan tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="8c675-288">Predicts area based on training data.</span></span>
* <span data-ttu-id="8c675-289">Modele kaydeder bir `.zip` dosya.</span><span class="sxs-lookup"><span data-stu-id="8c675-289">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="8c675-290">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c675-290">Returns the model.</span></span>

<span data-ttu-id="8c675-291">Oluşturma `BuildAndTrainModel` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8c675-291">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

<span data-ttu-id="8c675-292">İki parametre BuildAndTrainModel yönteme geçirilen dikkat edin; bir `IDataView` eğitim veri kümesi için (`trainingDataView`) ve <xref:Microsoft.ML.Data.EstimatorChain%601> ProcessData içinde oluşturulan işleme işlem hattının (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="8c675-292">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="8c675-293">İlk satırı olarak aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8c675-293">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-learning-algorithm"></a><span data-ttu-id="8c675-294">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="8c675-294">Choose a learning algorithm</span></span>

<span data-ttu-id="8c675-295">Öğrenme algoritmasını eklemek için çağrı `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` döndüren sarmalayıcı yöntemini bir <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> nesne.</span><span class="sxs-lookup"><span data-stu-id="8c675-295">To add the learning algorithm, call the `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span>  <span data-ttu-id="8c675-296">`SdcaMultiClassTrainer` Eklenir `pipeline` ve özellikleri tespit `Title` ve `Description` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="8c675-296">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span> <span data-ttu-id="8c675-297">Ayrıca okunabilir özgün durumuna döndürülecek değer etiketi eşlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c675-297">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="8c675-298">Aşağıdaki kod ile bu eylemlerin her ikisini birden yapın:</span><span class="sxs-lookup"><span data-stu-id="8c675-298">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="8c675-299">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8c675-299">Train the model</span></span>

<span data-ttu-id="8c675-300">Modeli eğitme <xref:Microsoft.ML.Data.TransformerChain%601>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="8c675-300">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="8c675-301">Tahmin tanımlandıktan sonra kullanarak modelinize eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> zaten yüklenmiş eğitim verilerini sağlayarak.</span><span class="sxs-lookup"><span data-stu-id="8c675-301">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="8c675-302">Bu yöntem, tahminler elde etmek için kullanılacak bir modelini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c675-302">This  method returns a model to use for predictions.</span></span> <span data-ttu-id="8c675-303">`trainingPipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi.</span><span class="sxs-lookup"><span data-stu-id="8c675-303">`trainingPipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="8c675-304">Denemeyi kadar yürütülmez `.Fit()` yöntemi çalışır.</span><span class="sxs-lookup"><span data-stu-id="8c675-304">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="8c675-305">Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8c675-305">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="8c675-306">Sırada `model` olduğu bir `transformer` ortak bir üretim senaryosu, tek tek örnekleri tahminler elde etmek için bir gereksinim, birçok veri satırı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="8c675-306">While the `model` is a `transformer` that operates on many rows of data, a need for predictions on individual examples is a common production scenario.</span></span> <span data-ttu-id="8c675-307"><xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c675-307">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="8c675-308">Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` sonraki satırı olarak `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8c675-308">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="8c675-309">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="8c675-309">Predict with the trained model</span></span>

<span data-ttu-id="8c675-310">Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="8c675-310">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="8c675-311">Bu tahmin etmek için kullanabileceğiniz `Area` sorun verileri tek bir örneğini etiketi.</span><span class="sxs-lookup"><span data-stu-id="8c675-311">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="8c675-312">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="8c675-312">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="8c675-313">Giriş verilerini bir dizedir ve özellik kazandırma sayesinde modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="8c675-313">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="8c675-314">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="8c675-314">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="8c675-315">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="8c675-315">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="8c675-316">Modeli kullanılarak: tahmin sonuçlarını</span><span class="sxs-lookup"><span data-stu-id="8c675-316">Using the model: prediction results</span></span>

<span data-ttu-id="8c675-317">Görüntü `GitHubIssue` ve karşılık gelen `Area` tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için etiket.</span><span class="sxs-lookup"><span data-stu-id="8c675-317">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="8c675-318">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="8c675-318">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="8c675-319">Değerlendirme için kullanılacak modeli eğitilir döndürür</span><span class="sxs-lookup"><span data-stu-id="8c675-319">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="8c675-320">Model sonunda dönüş `BuildAndTrainModel` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c675-320">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="8c675-321">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8c675-321">Evaluate the model</span></span>

<span data-ttu-id="8c675-322">Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c675-322">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="8c675-323">İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `BuildAndTrainModel` değerlendirilecek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8c675-323">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="8c675-324">Oluşturma `Evaluate` yöntemi hemen sonrasına `BuildAndTrainModel`, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="8c675-324">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="8c675-325">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8c675-325">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="8c675-326">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="8c675-326">Loads the test dataset.</span></span>
* <span data-ttu-id="8c675-327">Çok sınıflı değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c675-327">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="8c675-328">Model değerlendirir ve metrikleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8c675-328">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="8c675-329">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8c675-329">Displays the metrics.</span></span>

<span data-ttu-id="8c675-330">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `BuildAndTrainModel` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8c675-330">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="8c675-331">Eğitim veri kümesi ile daha önce yaptığınız gibi eşleme başlatma birleştirin ve sınama veri kümesi bir kod satırının içine yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="8c675-331">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="8c675-332">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="8c675-332">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="8c675-333">Aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8c675-333">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="8c675-334">`MulticlassClassificationContext.Evaluate` İçin bir sarmalayıcı olan <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> belirtilen veri kümesi kullanan model için Kalite Ölçümleri hesaplar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c675-334">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="8c675-335">Döndürür bir <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> sınıflı sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="8c675-335">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="8c675-336">Model kalitesini belirlemek için ölçümleri görüntülemek için bunları ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c675-336">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="8c675-337">Kullanımına dikkat edin `Transform` machine Learning yöntemi `_trainedModel` özellikleri giriş ve tahmin döndürmek için genel değişkeni (dönüştürücü).</span><span class="sxs-lookup"><span data-stu-id="8c675-337">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="8c675-338">Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="8c675-338">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="8c675-339">Aşağıdaki ölçümler sınıflı sınıflandırma için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="8c675-339">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="8c675-340">Mikro doğruluğu - her örnek sınıfı çifti eşit doğruluğu ölçüme katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8c675-340">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="8c675-341">Mikro doğruluğu, 1 olarak mümkün olduğunca yakın olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="8c675-341">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="8c675-342">Makro doğruluğu - her sınıf eşit doğruluğu ölçüme katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8c675-342">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="8c675-343">Azınlık sınıfları daha büyük bir sınıf olarak eşit ağırlık verilir.</span><span class="sxs-lookup"><span data-stu-id="8c675-343">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="8c675-344">Makrosu 1 olarak mümkün olduğunca yakın olmasını doğruluğu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c675-344">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="8c675-345">Günlük zarar - bkz [günlük kaybı](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="8c675-345">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="8c675-346">Sıfır olarak mümkün olduğunca yakın olmasını günlük zarar kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c675-346">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="8c675-347">Günlük kaybı azaltma - aralıkları gelen [-INF, 100], burada 100 mükemmel Öngörüler ve 0, ortalama Öngörüler gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c675-347">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="8c675-348">Günlük kaybı azaltma sıfır olarak mümkün olduğunca yakın olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="8c675-348">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="8c675-349">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8c675-349">Displaying the metrics for model validation</span></span>

<span data-ttu-id="8c675-350">Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8c675-350">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a><span data-ttu-id="8c675-351">Eğitilen ve değerlendirilen modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="8c675-351">Save the trained and evaluated model</span></span>

<span data-ttu-id="8c675-352">Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain%601> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine.</span><span class="sxs-lookup"><span data-stu-id="8c675-352">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="8c675-353">Eğitilen model bir .zip dosyası olarak kaydetmek için çağırmak için aşağıdaki kodu ekleyin. `SaveModelAsFile` yöntemi olarak bir sonraki satırda `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="8c675-353">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="8c675-354">Bir .zip dosyası olarak modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="8c675-354">Save the model as a .zip file</span></span>

<span data-ttu-id="8c675-355">Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8c675-355">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="8c675-356">`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8c675-356">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="8c675-357">Model bir .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8c675-357">Saves the model as a .zip file.</span></span>

<span data-ttu-id="8c675-358">Ardından, yeniden kullanılabilir ve diğer uygulamalarda kullanılan model kaydetmek için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8c675-358">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="8c675-359">`ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="8c675-359">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="8c675-360">Model zip dosyası olarak kaydetmek için oluşturacağınız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c675-360">To save the model as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="8c675-361">Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="8c675-361">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="8c675-362">Bir konsol iletisi ile yazarak dosyasının nerede yazılmıştır görüntüleyebilir `_modelPath`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8c675-362">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="8c675-363">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="8c675-363">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="8c675-364">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8c675-364">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="8c675-365">Oluşturma `PredictIssue` yöntemi hemen sonrasına `Evaluate` yöntemi (ve hemen önce `SaveModelAsFile` yöntemi), aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8c675-365">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="8c675-366">`PredictIssue` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8c675-366">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="8c675-367">Test verilerini tek bir konu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c675-367">Creates a single issue of test data.</span></span>
* <span data-ttu-id="8c675-368">Test verilerini temel alarak alan tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="8c675-368">Predicts Area based on test data.</span></span>
* <span data-ttu-id="8c675-369">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="8c675-369">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="8c675-370">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8c675-370">Displays the predicted results.</span></span>

<span data-ttu-id="8c675-371">İlk olarak, aşağıdaki kod ile daha önce kaydettiğiniz model yüklenemiyor:</span><span class="sxs-lookup"><span data-stu-id="8c675-371">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="8c675-372">Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="8c675-372">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="8c675-373">Bir modeliniz olduğuna göre tek bir GitHub sorunu veri örneğini alan GitHub etiketini tahmin etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c675-373">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="8c675-374">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="8c675-374">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="8c675-375">Giriş verilerini bir dizedir ve özellik kazandırma sayesinde modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="8c675-375">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="8c675-376">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="8c675-376">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="8c675-377">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="8c675-377">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="8c675-378">Aşağıdaki kodu ekleyin `PredictIssue` yöntemi tahminler elde etmek için:</span><span class="sxs-lookup"><span data-stu-id="8c675-378">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="8c675-379">Tahmin için yüklenen modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="8c675-379">Using the loaded model for prediction</span></span>

<span data-ttu-id="8c675-380">Görüntü `Area` sorunu kategorilere ayırmak ve buna göre hareket üzerinde için.</span><span class="sxs-lookup"><span data-stu-id="8c675-380">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="8c675-381">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="8c675-381">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="8c675-382">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="8c675-382">Results</span></span>

<span data-ttu-id="8c675-383">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c675-383">Your results should be similar to the following.</span></span> <span data-ttu-id="8c675-384">İşlem hattı işlediği gibi iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8c675-384">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="8c675-385">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c675-385">You may see warnings, or processing messages.</span></span> <span data-ttu-id="8c675-386">Bu iletiler, anlaşılması için aşağıdaki sonuçlarından kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="8c675-386">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="8c675-387">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="8c675-387">Congratulations!</span></span> <span data-ttu-id="8c675-388">Bir machine learning modeli sınıflandırmak ve bir alan etiketini bir GitHub sorunu için tahmin etmek için şimdi başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="8c675-388">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="8c675-389">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.</span><span class="sxs-lookup"><span data-stu-id="8c675-389">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8c675-390">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8c675-390">Next steps</span></span>

<span data-ttu-id="8c675-391">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="8c675-391">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8c675-392">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="8c675-392">Understand the problem</span></span>
> * <span data-ttu-id="8c675-393">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="8c675-393">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="8c675-394">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="8c675-394">Prepare your data</span></span>
> * <span data-ttu-id="8c675-395">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8c675-395">Transform the data</span></span>
> * <span data-ttu-id="8c675-396">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8c675-396">Train the model</span></span>
> * <span data-ttu-id="8c675-397">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8c675-397">Evaluate the model</span></span>
> * <span data-ttu-id="8c675-398">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="8c675-398">Predict with the trained model</span></span>
> * <span data-ttu-id="8c675-399">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="8c675-399">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="8c675-400">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="8c675-400">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8c675-401">Taksi taksi göstergesi</span><span class="sxs-lookup"><span data-stu-id="8c675-401">Taxi Fare Predictor</span></span>](taxi-fare.md)
