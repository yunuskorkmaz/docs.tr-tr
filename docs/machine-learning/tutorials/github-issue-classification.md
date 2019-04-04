---
title: Bir GitHub sorunu sınıflı sınıflandırma senaryosunda ML.NET kullanın
description: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları için belirli bir alanla atamak sınıflandırmak için nasıl kullanılacağını keşfedin.
ms.date: 03/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: fc21a37fe585ed4b9880ec86ee26815e0668108c
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920993"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a><span data-ttu-id="a4b51-103">Öğretici: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları sınıflandırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4b51-103">Tutorial: Use ML.NET in a multiclass classification scenario to classify GitHub issues</span></span>

<span data-ttu-id="a4b51-104">Bu örnek öğretici ML.NET kullanarak bir .NET Core konsol uygulaması kullanarak aracılığıyla bir GitHub sorunu sınıflandırıcı oluşturma gösterilmektedir C# Visual Studio 2017'de.</span><span class="sxs-lookup"><span data-stu-id="a4b51-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="a4b51-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="a4b51-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a4b51-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="a4b51-106">Understand the problem</span></span>
> * <span data-ttu-id="a4b51-107">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="a4b51-107">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="a4b51-108">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="a4b51-108">Prepare your data</span></span>
> * <span data-ttu-id="a4b51-109">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a4b51-109">Transform the data</span></span>
> * <span data-ttu-id="a4b51-110">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="a4b51-110">Train the model</span></span>
> * <span data-ttu-id="a4b51-111">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="a4b51-111">Evaluate the model</span></span>
> * <span data-ttu-id="a4b51-112">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="a4b51-112">Predict with the trained model</span></span>
> * <span data-ttu-id="a4b51-113">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="a4b51-113">Deploy and Predict with a loaded model</span></span>

> [!NOTE]
> <span data-ttu-id="a4b51-114">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-114">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="a4b51-115">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a4b51-115">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="a4b51-116">Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.11**.</span><span class="sxs-lookup"><span data-stu-id="a4b51-116">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="a4b51-117">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="a4b51-117">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="github-issue-sample-overview"></a><span data-ttu-id="a4b51-118">GitHub sorunu örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="a4b51-118">GitHub issue sample overview</span></span>

<span data-ttu-id="a4b51-119">Örnek ML.NET sınıflandırır ve bir GitHub sorunu alan etiketini tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-119">The sample is a console app that uses ML.NET to train a model that classifies and predicts the Area label for a GitHub issue.</span></span> <span data-ttu-id="a4b51-120">Ayrıca, kalite analizi için ikinci bir veri kümesi modeliyle değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-120">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="a4b51-121">Çıkış veri kümeleri dotnet/corefx'te GitHub deposundan ' dir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-121">The issue datasets are from the dotnet/corefx GitHub repo.</span></span>

<span data-ttu-id="a4b51-122">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.</span><span class="sxs-lookup"><span data-stu-id="a4b51-122">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a4b51-123">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a4b51-123">Prerequisites</span></span>

* <span data-ttu-id="a4b51-124">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-124">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="a4b51-125">[Github sorunlar sekmeyle dosyası (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="a4b51-125">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="a4b51-126">[Github sorunları sekmeyle dosyası (issues_test.tsv) test](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="a4b51-126">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="a4b51-127">Machine learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="a4b51-127">Machine learning workflow</span></span>

<span data-ttu-id="a4b51-128">Bu öğreticide, bir makine öğrenimi düzenli bir şekilde taşımak işlem sağlayan bir iş akışı izler.</span><span class="sxs-lookup"><span data-stu-id="a4b51-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="a4b51-129">İş akışı aşamalar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a4b51-129">The workflow phases are as follows:</span></span>

1. **<span data-ttu-id="a4b51-130">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="a4b51-130">Understand the problem</span></span>**
2. **<span data-ttu-id="a4b51-131">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="a4b51-131">Prepare your data</span></span>**
   * **<span data-ttu-id="a4b51-132">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="a4b51-132">Load the data</span></span>**
   * **<span data-ttu-id="a4b51-133">Özellikler (verilerinizi dönüştürmek) ayıklayın</span><span class="sxs-lookup"><span data-stu-id="a4b51-133">Extract features (Transform your data)</span></span>**
3. **<span data-ttu-id="a4b51-134">Derleme ve eğitme</span><span class="sxs-lookup"><span data-stu-id="a4b51-134">Build and train</span></span>** 
   * **<span data-ttu-id="a4b51-135">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="a4b51-135">Train the model</span></span>**
   * **<span data-ttu-id="a4b51-136">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="a4b51-136">Evaluate the model</span></span>**
4. **<span data-ttu-id="a4b51-137">Model dağıtma</span><span class="sxs-lookup"><span data-stu-id="a4b51-137">Deploy Model</span></span>**
   * **<span data-ttu-id="a4b51-138">Tahmin modelini kullanın</span><span class="sxs-lookup"><span data-stu-id="a4b51-138">Use the Model to predict</span></span>**

### <a name="understand-the-problem"></a><span data-ttu-id="a4b51-139">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="a4b51-139">Understand the problem</span></span>

<span data-ttu-id="a4b51-140">Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="a4b51-141">Problemi parçalamak, tahmin edin ve sonuçları değerlendirin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-141">Breaking  down the problem allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="a4b51-142">Sorun Bu öğretici için hangi alan gelen GitHub sorunları bunları öncelik belirleme ve planlama için doğru etiket için ait öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-142">The problem for this tutorial is to understand what area incoming GitHub issues belong to in order to label them correctly for prioritization and scheduling.</span></span>

<span data-ttu-id="a4b51-143">İçin aşağıdaki bölümleri problemi bölünebilir:</span><span class="sxs-lookup"><span data-stu-id="a4b51-143">You can break down the problem to the following parts:</span></span>

* <span data-ttu-id="a4b51-144">sorun başlık metni</span><span class="sxs-lookup"><span data-stu-id="a4b51-144">the issue title text</span></span>
* <span data-ttu-id="a4b51-145">Sorun açıklaması metni</span><span class="sxs-lookup"><span data-stu-id="a4b51-145">the issue description text</span></span>
* <span data-ttu-id="a4b51-146">model eğitim verileri için bir alan değeri</span><span class="sxs-lookup"><span data-stu-id="a4b51-146">an area value for the model training data</span></span>
* <span data-ttu-id="a4b51-147">bir tahmin edilen alan değeri değerlendirmek ve işletimsel olarak kullanın</span><span class="sxs-lookup"><span data-stu-id="a4b51-147">a predicted area value that you can evaluate and then use operationally</span></span>

<span data-ttu-id="a4b51-148">Ardından gerek **belirlemek** alanı Görev Seçimi öğrenme makineyle yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a4b51-148">You then need to **determine** the area, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="a4b51-149">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="a4b51-149">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="a4b51-150">Bu sorun aşağıdaki gerçekleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="a4b51-150">With this problem, you know the following facts:</span></span>

<span data-ttu-id="a4b51-151">Eğitim verileri:</span><span class="sxs-lookup"><span data-stu-id="a4b51-151">Training data:</span></span>

<span data-ttu-id="a4b51-152">GitHub sorunları birçok alanda etiketli (**alan**) aşağıdaki örneklerde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="a4b51-152">GitHub issues can be labeled in several areas (**Area**) as in the following examples:</span></span>

* <span data-ttu-id="a4b51-153">alan System.Numerics</span><span class="sxs-lookup"><span data-stu-id="a4b51-153">area-System.Numerics</span></span>
* <span data-ttu-id="a4b51-154">System.Xml alanı</span><span class="sxs-lookup"><span data-stu-id="a4b51-154">area-System.Xml</span></span>
* <span data-ttu-id="a4b51-155">alan altyapı</span><span class="sxs-lookup"><span data-stu-id="a4b51-155">area-Infrastructure</span></span>
* <span data-ttu-id="a4b51-156">alan System.Linq</span><span class="sxs-lookup"><span data-stu-id="a4b51-156">area-System.Linq</span></span>
* <span data-ttu-id="a4b51-157">alan System.IO</span><span class="sxs-lookup"><span data-stu-id="a4b51-157">area-System.IO</span></span>

<span data-ttu-id="a4b51-158">Tahmin **alan** yeni GitHub sorunu aşağıdaki örneklerde olduğu gibi böyle:</span><span class="sxs-lookup"><span data-stu-id="a4b51-158">Predict the **Area** of a new GitHub Issue such as in the following examples:</span></span>

* <span data-ttu-id="a4b51-159">Debug.Assert Contract.Assert vs</span><span class="sxs-lookup"><span data-stu-id="a4b51-159">Contract.Assert vs Debug.Assert</span></span>
* <span data-ttu-id="a4b51-160">System.Xml içinde alanları salt okunur yapın</span><span class="sxs-lookup"><span data-stu-id="a4b51-160">Make fields readonly in System.Xml</span></span>

<span data-ttu-id="a4b51-161">Sınıflandırma makine öğrenimi algoritmasının bu senaryo için idealdir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-161">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-learning-algorithm"></a><span data-ttu-id="a4b51-162">Sınıflandırma öğrenme algoritmasını hakkında</span><span class="sxs-lookup"><span data-stu-id="a4b51-162">About the classification learning algorithm</span></span>

<span data-ttu-id="a4b51-163">Sınıflandırma olan verileri kullanan bir machine learning algoritmasını **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a4b51-163">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="a4b51-164">Örneğin, sınıflandırma için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a4b51-164">For example, you can use classification to:</span></span>

* <span data-ttu-id="a4b51-165">Artı veya eksi olarak duyguları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a4b51-165">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="a4b51-166">E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.</span><span class="sxs-lookup"><span data-stu-id="a4b51-166">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="a4b51-167">Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a4b51-167">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="a4b51-168">Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.</span><span class="sxs-lookup"><span data-stu-id="a4b51-168">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="a4b51-169">Sınıflandırma öğrenme algoritmasını kullanım durumları olan sık aşağıdaki türlerden biri:</span><span class="sxs-lookup"><span data-stu-id="a4b51-169">Classification learning algorithm use cases are frequently one of the following types:</span></span>

* <span data-ttu-id="a4b51-170">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="a4b51-170">Binary: either A or B.</span></span>
* <span data-ttu-id="a4b51-171">Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="a4b51-171">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="a4b51-172">Bu sorun türü için birden çok kategoriden (veya çoklu sınıflar) sorun kategorisi tahmininizde olabileceği algoritması, öğrenme veya çoklu sınıflar sınıflandırması yalnızca iki yerine kullanın (ikili).</span><span class="sxs-lookup"><span data-stu-id="a4b51-172">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a4b51-173">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4b51-173">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="a4b51-174">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4b51-174">Create a project</span></span>

1. <span data-ttu-id="a4b51-175">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="a4b51-175">Open Visual Studio 2017.</span></span> <span data-ttu-id="a4b51-176">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="a4b51-176">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="a4b51-177">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="a4b51-177">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="a4b51-178">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="a4b51-178">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="a4b51-179">İçinde **adı** metin kutusuna "GitHubIssueClassification" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-179">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="a4b51-180">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="a4b51-180">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="a4b51-181">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="a4b51-181">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="a4b51-182">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a4b51-182">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="a4b51-183">Adlı bir dizin oluşturmak *modelleri* modelinizi kaydetmek için projenizde:</span><span class="sxs-lookup"><span data-stu-id="a4b51-183">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="a4b51-184">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="a4b51-184">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="a4b51-185">"Modeli" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a4b51-185">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="a4b51-186">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="a4b51-186">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="a4b51-187">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="a4b51-187">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="a4b51-188">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-188">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="a4b51-189">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="a4b51-189">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="a4b51-190">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="a4b51-190">Prepare your data</span></span>

1. <span data-ttu-id="a4b51-191">İndirme [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="a4b51-191">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="a4b51-192">İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-192">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="a4b51-193">Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="a4b51-193">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="a4b51-194">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="a4b51-194">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="a4b51-195">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4b51-195">Create classes and define paths</span></span>

<span data-ttu-id="a4b51-196">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="a4b51-196">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="a4b51-197">Yolları kısa bir süre önce indirilen dosyaları ve genel değişkenleri tutmak için üç genel alanlar oluşturmak `MLContext`,`DataView`, `PredictionEngine`, ve `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="a4b51-197">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, `PredictionEngine`, and `TextLoader`:</span></span>

* `_trainDataPath` <span data-ttu-id="a4b51-198">Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-198">has the path to the dataset used to train the model.</span></span>
* `_testDataPath` <span data-ttu-id="a4b51-199">Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-199">has the path to the dataset used to evaluate the model.</span></span>
* `_modelPath` <span data-ttu-id="a4b51-200">eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-200">has the path where the trained model is saved.</span></span>
* `_mlContext` <span data-ttu-id="a4b51-201">olan <xref:Microsoft.ML.MLContext> , işlem bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4b51-201">is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* `_trainingDataView` <span data-ttu-id="a4b51-202">olan <xref:Microsoft.Data.DataView.IDataView> eğitim veri kümesi işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-202">is the <xref:Microsoft.Data.DataView.IDataView> used to process the training dataset.</span></span>
* `_predEngine` <span data-ttu-id="a4b51-203">olan <xref:Microsoft.ML.PredictionEngine%602> tek Tahminler elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-203">is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>
* `_reader` <span data-ttu-id="a4b51-204">olan <xref:Microsoft.ML.Data.TextLoader> yüklemek ve veri kümeleri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-204">is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="a4b51-205">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollar ve diğer değişkenlerini belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="a4b51-205">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="a4b51-206">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4b51-206">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="a4b51-207">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a4b51-207">Add a new class to your project:</span></span>

1. <span data-ttu-id="a4b51-208">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="a4b51-208">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="a4b51-209">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="a4b51-209">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="a4b51-210">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-210">Then, select the **Add** button.</span></span>

    <span data-ttu-id="a4b51-211">*GitHubIssueData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-211">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="a4b51-212">Aşağıdaki `using` üstüne deyimi *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="a4b51-212">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="a4b51-213">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `GitHubIssue` ve `IssuePrediction`, *GitHubIssueData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="a4b51-213">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`GitHubIssue` <span data-ttu-id="a4b51-214">Giriş veri kümesi sınıfı ve aşağıdaki <xref:System.String> alanlar:</span><span class="sxs-lookup"><span data-stu-id="a4b51-214">is the input dataset class and has the following <xref:System.String> fields:</span></span>

* `ID` <span data-ttu-id="a4b51-215">GitHub sorun kimliği için bir değer içeriyor</span><span class="sxs-lookup"><span data-stu-id="a4b51-215">contains a value for the GitHub issue ID</span></span>
* `Area` <span data-ttu-id="a4b51-216">için bir değer içeren `Area` etiketi</span><span class="sxs-lookup"><span data-stu-id="a4b51-216">contains a value for the `Area` label</span></span>
* `Title` <span data-ttu-id="a4b51-217">GitHub sorunu başlık içerir</span><span class="sxs-lookup"><span data-stu-id="a4b51-217">contains the GitHub issue title</span></span>
* `Description` <span data-ttu-id="a4b51-218">GitHub sorun açıklaması içerir</span><span class="sxs-lookup"><span data-stu-id="a4b51-218">contains the GitHub issue description</span></span>

`IssuePrediction` <span data-ttu-id="a4b51-219">eğitilen modelin sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-219">is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="a4b51-220">Tek bir sahip `string` (`Area`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a4b51-220">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="a4b51-221">`Label` Oluşturup modeli ya da onun da model değerlendirmek için ikinci bir veri kümesi ile kullanılan eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-221">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="a4b51-222">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-222">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="a4b51-223">Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-223">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="a4b51-224">ML.NET modeliyle oluştururken oluşturarak başlayın bir <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="a4b51-224">When building a model with ML.NET, you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> `MLContext` <span data-ttu-id="a4b51-225">kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a4b51-225">is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="a4b51-226">Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilecek ML işiniz için bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4b51-226">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="a4b51-227">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="a4b51-227">Initialize variables in Main</span></span>

<span data-ttu-id="a4b51-228">Başlatma `_mlContext` yeni bir örneğini genel değişkenin `MLContext` ile rastgele bir tohum (`seed: 0`) arasında birden çok eğitimleri/deterministic tekrarlanabilir sonuçlar.</span><span class="sxs-lookup"><span data-stu-id="a4b51-228">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="a4b51-229">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a4b51-229">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="a4b51-230">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="a4b51-230">Load the data</span></span>

<span data-ttu-id="a4b51-231">Ardından, başlatma `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> genel değişken ve ile veri yükleme `_trainDataPath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-231">Next, initialize the `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> global variable and load the data with the `_trainDataPath` parameter.</span></span>

 <span data-ttu-id="a4b51-232">Giriş ve çıkış olarak [ `Transforms` ](../basic-concepts-model-training-in-mldotnet.md#transformer), `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="a4b51-232">As the input and output of [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer), a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="a4b51-233">ML.NET içinde veri benzer bir `SQL view`.</span><span class="sxs-lookup"><span data-stu-id="a4b51-233">In ML.NET, data is similar to a `SQL view`.</span></span> <span data-ttu-id="a4b51-234">Bu, gevşek değerlendirilen, şema ve heterojen olur.</span><span class="sxs-lookup"><span data-stu-id="a4b51-234">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="a4b51-235">Nesne, işlem hattını ilk kısmı ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="a4b51-235">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="a4b51-236">Bu öğreticide, bir veri kümesi sorunu başlıklarını, açıklamaları ve karşılık gelen alan GitHub etiketi ile yükler.</span><span class="sxs-lookup"><span data-stu-id="a4b51-236">For this tutorial, it loads a dataset with issue titles, descriptions, and corresponding area GitHub label.</span></span> <span data-ttu-id="a4b51-237">`DataView` Oluşturup modeli eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-237">The `DataView` is used to create and train the model.</span></span>

<span data-ttu-id="a4b51-238">Önceden oluşturduğunuz beri `GitHubIssue` veri modeli türüyle eşleşen veri kümesi şeması, başlatma, eşleme ve veri kümesi bir kod satırının içine yükleniyor birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b51-238">Since your previously created `GitHubIssue` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code.</span></span>

<span data-ttu-id="a4b51-239">Kullanarak verileri yüklemek `MLContext.Data.LoadFromTextFile` için sarmalayıcı [LoadFromTextFile yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="a4b51-239">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="a4b51-240">Döndürür bir <xref:Microsoft.Data.DataView.IDataView> veri kümesi şema çıkarsar `GitHubIssue` veri türü model ve veri kümesi başlık kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-240">It returns a <xref:Microsoft.Data.DataView.IDataView> which infers the dataset schema from the `GitHubIssue` data model type and uses the dataset header.</span></span> 

<span data-ttu-id="a4b51-241">Oluşturduğunuz zaman veri şemasını önceden tanımlanmış `GitHubIssue` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a4b51-241">You defined the data schema previously when you created the `GitHubIssue` class.</span></span> <span data-ttu-id="a4b51-242">Şemanızı için:</span><span class="sxs-lookup"><span data-stu-id="a4b51-242">For your schema:</span></span>

* <span data-ttu-id="a4b51-243">İlk sütun `ID` (GitHub sorunu kimliği)</span><span class="sxs-lookup"><span data-stu-id="a4b51-243">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="a4b51-244">ikinci sütunda `Area` (eğitim tahmin)</span><span class="sxs-lookup"><span data-stu-id="a4b51-244">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="a4b51-245">üçüncü sütunda `Title` (GitHub sorun başlığı) sanal makinede ilk [özellik](../resources/glossary.md##feature) tahmin etmek için kullanılan</span><span class="sxs-lookup"><span data-stu-id="a4b51-245">the third column `Title` (GitHub issue title) is the first [feature](../resources/glossary.md##feature)  used for predicting the</span></span> `Area`
* <span data-ttu-id="a4b51-246">Dördüncü sütun `Description` tahmin etmek için kullanılan ikinci özelliğidir</span><span class="sxs-lookup"><span data-stu-id="a4b51-246">the fourth column  `Description` is the second feature used for predicting the</span></span> `Area`

<span data-ttu-id="a4b51-247">Başlatma ve yüklemek için `_trainingDataView` ardışık düzeni için kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:</span><span class="sxs-lookup"><span data-stu-id="a4b51-247">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="a4b51-248">Sonraki kod satırı olarak ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a4b51-248">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="a4b51-249">`ProcessData` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="a4b51-249">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="a4b51-250">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a4b51-250">Extracts and transforms the data.</span></span>
* <span data-ttu-id="a4b51-251">İşleme işlem hattı döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4b51-251">Returns the processing pipeline.</span></span>

<span data-ttu-id="a4b51-252">Oluşturma `ProcessData` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="a4b51-252">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="a4b51-253">Özellikleri ayıklayın ve verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a4b51-253">Extract Features and transform the data</span></span>

<span data-ttu-id="a4b51-254">Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-254">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="a4b51-255">Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-255">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="a4b51-256">Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-256">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="a4b51-257">ML. NET dönüştürme işlem hatları oluşturma özel `transforms`eğitim veya test etmeden önce verilerinizi uygulanan kümesi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-257">ML.NET's transform pipelines compose a custom `transforms`set that is applied to your data before training or testing.</span></span> <span data-ttu-id="a4b51-258">Veri Dönüşümleri birincil amacı olan [özellik kazandırma sayesinde](../resources/glossary.md#feature-engineering).</span><span class="sxs-lookup"><span data-stu-id="a4b51-258">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="a4b51-259">Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) metinsel verilerimizi ML algoritmalarınızı tanıyacak bir biçime dönüştürmek için sonraki adım, bu nedenle veri.</span><span class="sxs-lookup"><span data-stu-id="a4b51-259">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="a4b51-260">Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="a4b51-260">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="a4b51-261">Sonraki adımlarda sütunlara adlarıyla tanımlanan diyoruz `GitHubIssue` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a4b51-261">In the next steps, we refer to the columns by the names defined in the `GitHubIssue` class.</span></span>

<span data-ttu-id="a4b51-262">Model eğitim ve diğer değerleri varsayılan olarak, hesaplanan zaman **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-262">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="a4b51-263">Alan GitHub etiketi tahmin etmek istediğimiz bir `GitHubIssue`, kopyalama `Area` sütuna **etiket** sütun.</span><span class="sxs-lookup"><span data-stu-id="a4b51-263">As we want to predict the Area GitHub label for a `GitHubIssue`, copy the `Area` column into the **Label** column.</span></span> <span data-ttu-id="a4b51-264">Bunu yapmak için kullanın `MLContext.Transforms.Conversion.MapValueToKey`, bu değer için bir sarmalayıcı <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a4b51-264">To do that, use the `MLContext.Transforms.Conversion.MapValueToKey`, which is a wrapper for the <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> transformation class.</span></span>  <span data-ttu-id="a4b51-265">`MapValueToKey` Döndürür bir <xref:Microsoft.ML.Data.EstimatorChain%601> bir işlem hattı etkin olacak.</span><span class="sxs-lookup"><span data-stu-id="a4b51-265">The `MapValueToKey` returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="a4b51-266">Bu ad `pipeline` eğitmen için ardından ekleyeceği şekilde `EstimatorChain`.</span><span class="sxs-lookup"><span data-stu-id="a4b51-266">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="a4b51-267">Sonraki kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a4b51-267">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 <span data-ttu-id="a4b51-268">Featurizing farklı değerler her sütun için farklı sayısal anahtar değerleri atar ve makine öğrenme algoritmasına tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-268">Featurizing assigns different numeric key values to the different values in each of the columns and is used by the machine learning algorithm.</span></span> <span data-ttu-id="a4b51-269">Ardından, arama `mlContext.Transforms.Text.FeaturizeText` hangi featurizes metni (`Title` ve `Description`) sayısal bir vektör her adlı sütuna `TitleFeaturized` ve `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="a4b51-269">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="a4b51-270">Aşağıdaki kod ile işlem hattı her iki sütun için özellik kazandırma sayesinde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a4b51-270">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> <span data-ttu-id="a4b51-271">ML.NET sürüm 0.10 dönüştürme parametreleri sırası değişti.</span><span class="sxs-lookup"><span data-stu-id="a4b51-271">ML.NET Version 0.10 has changed the order of the Transform parameters.</span></span> <span data-ttu-id="a4b51-272">Bu, kullanıma alma hatası, yapı kadar.</span><span class="sxs-lookup"><span data-stu-id="a4b51-272">This will not error out until you build.</span></span> <span data-ttu-id="a4b51-273">Dönüşümlerin parametre adları, önceki kod parçacığında gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4b51-273">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="a4b51-274">Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak `Concatenate` dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a4b51-274">The last step in data preparation combines all of the feature columns into the **Features** column using the `Concatenate` transformation class.</span></span> <span data-ttu-id="a4b51-275">Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="a4b51-275">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="a4b51-276">Aşağıdaki kod ile işlem hattı için bu dönüşümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a4b51-276">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="a4b51-277">Ardından, ekleme bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> üzerinden yineleme yapma, verileri birden çok kez önbellek kullanarak daha iyi performans için şu kod gibi alabilirsiniz şekilde DataView önbelleğe almak için:</span><span class="sxs-lookup"><span data-stu-id="a4b51-277">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="a4b51-278">Eğitim süresini azaltmak için AppendCacheCheckpoint küçük/Orta veri kümeleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4b51-278">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="a4b51-279">(Kaldırın. bunu kullanmayın Çok büyük veri kümelerinde işlerken AppendCacheCheckpoint()).</span><span class="sxs-lookup"><span data-stu-id="a4b51-279">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="a4b51-280">Ardışık Düzen sonunda dönüş `ProcessData` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-280">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="a4b51-281">Bu adımda, ön işleme/özellik kazandırma sayesinde işler.</span><span class="sxs-lookup"><span data-stu-id="a4b51-281">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="a4b51-282">ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b51-282">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="a4b51-283">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="a4b51-283">Build and train the model</span></span>

<span data-ttu-id="a4b51-284">Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a4b51-284">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="a4b51-285">`BuildAndTrainModel` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="a4b51-285">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="a4b51-286">Eğitim algoritması sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a4b51-286">Creates the training algorithm class.</span></span>
* <span data-ttu-id="a4b51-287">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-287">Trains the model.</span></span>
* <span data-ttu-id="a4b51-288">Eğitim verilerini temel alarak alan tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="a4b51-288">Predicts area based on training data.</span></span>
* <span data-ttu-id="a4b51-289">Modele kaydeder bir `.zip` dosya.</span><span class="sxs-lookup"><span data-stu-id="a4b51-289">Saves the model to a `.zip` file.</span></span>
* <span data-ttu-id="a4b51-290">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4b51-290">Returns the model.</span></span>

<span data-ttu-id="a4b51-291">Oluşturma `BuildAndTrainModel` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="a4b51-291">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

<span data-ttu-id="a4b51-292">İki parametre BuildAndTrainModel yönteme geçirilen dikkat edin; bir `IDataView` eğitim veri kümesi için (`trainingDataView`) ve <xref:Microsoft.ML.Data.EstimatorChain%601> ProcessData içinde oluşturulan işleme işlem hattının (`pipeline`).</span><span class="sxs-lookup"><span data-stu-id="a4b51-292">Notice that two parameters are passed into the BuildAndTrainModel method; an `IDataView` for the training dataset (`trainingDataView`), and a <xref:Microsoft.ML.Data.EstimatorChain%601> for the processing pipeline created in ProcessData (`pipeline`).</span></span>

 <span data-ttu-id="a4b51-293">İlk satırı olarak aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a4b51-293">Add the following code as the first line of the `BuildAndTrainModel` method:</span></span>

### <a name="choose-a-learning-algorithm"></a><span data-ttu-id="a4b51-294">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="a4b51-294">Choose a learning algorithm</span></span>

<span data-ttu-id="a4b51-295">Öğrenme algoritmasını eklemek için çağrı `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` döndüren sarmalayıcı yöntemini bir <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> nesne.</span><span class="sxs-lookup"><span data-stu-id="a4b51-295">To add the learning algorithm, call the `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` wrapper method which returns a <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> object.</span></span>  <span data-ttu-id="a4b51-296">`SdcaMultiClassTrainer` Eklenir `pipeline` ve özellikleri tespit `Title` ve `Description` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="a4b51-296">The `SdcaMultiClassTrainer` is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span> <span data-ttu-id="a4b51-297">Ayrıca okunabilir özgün durumuna döndürülecek değer etiketi eşlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-297">You also need to map the label to the value to return to its original readable state.</span></span> <span data-ttu-id="a4b51-298">Aşağıdaki kod ile bu eylemlerin her ikisini birden yapın:</span><span class="sxs-lookup"><span data-stu-id="a4b51-298">Do both of those actions with the following code:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a><span data-ttu-id="a4b51-299">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="a4b51-299">Train the model</span></span>

<span data-ttu-id="a4b51-300">Modeli eğitme <xref:Microsoft.ML.Data.TransformerChain%601>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-300">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="a4b51-301">Tahmin tanımlandıktan sonra kullanarak modelinize eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> zaten yüklenmiş eğitim verilerini sağlayarak.</span><span class="sxs-lookup"><span data-stu-id="a4b51-301">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="a4b51-302">Bu yöntem, tahminler elde etmek için kullanılacak bir modelini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4b51-302">This  method returns a model to use for predictions.</span></span> `trainingPipeline.Fit()` <span data-ttu-id="a4b51-303">işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-303">trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="a4b51-304">Denemeyi kadar yürütülmez `.Fit()` yöntemi çalışır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-304">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="a4b51-305">Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a4b51-305">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="a4b51-306">Sırada `model` olduğu bir `transformer` ortak bir üretim senaryosu, tek tek örnekleri tahminler elde etmek için bir gereksinim, birçok veri satırı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-306">While the `model` is a `transformer` that operates on many rows of data, a need for predictions on individual examples is a common production scenario.</span></span> <span data-ttu-id="a4b51-307"><xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-307">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="a4b51-308">Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` sonraki satırı olarak `BuildAndTrainModel` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a4b51-308">Let's add the following code to create the `PredictionEngine` as the next line in the `BuildAndTrainModel` Method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="a4b51-309">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="a4b51-309">Predict with the trained model</span></span>

<span data-ttu-id="a4b51-310">Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="a4b51-310">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="a4b51-311">Bu tahmin etmek için kullanabileceğiniz `Area` sorun verileri tek bir örneğini etiketi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-311">You can use that to predict the `Area` label of a single instance of the issue data.</span></span> <span data-ttu-id="a4b51-312">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="a4b51-312">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="a4b51-313">Giriş verilerini bir dizedir ve özellik kazandırma sayesinde modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-313">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="a4b51-314">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="a4b51-314">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="a4b51-315">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-315">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="a4b51-316">Modeli kullanılarak: tahmin sonuçlarını</span><span class="sxs-lookup"><span data-stu-id="a4b51-316">Using the model: prediction results</span></span>

<span data-ttu-id="a4b51-317">Görüntü `GitHubIssue` ve karşılık gelen `Area` tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için etiket.</span><span class="sxs-lookup"><span data-stu-id="a4b51-317">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="a4b51-318">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="a4b51-318">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="a4b51-319">Değerlendirme için kullanılacak modeli eğitilir döndürür</span><span class="sxs-lookup"><span data-stu-id="a4b51-319">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="a4b51-320">Model sonunda dönüş `BuildAndTrainModel` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-320">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="a4b51-321">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="a4b51-321">Evaluate the model</span></span>

<span data-ttu-id="a4b51-322">Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-322">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="a4b51-323">İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `BuildAndTrainModel` değerlendirilecek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-323">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="a4b51-324">Oluşturma `Evaluate` yöntemi hemen sonrasına `BuildAndTrainModel`, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="a4b51-324">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="a4b51-325">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="a4b51-325">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="a4b51-326">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="a4b51-326">Loads the test dataset.</span></span>
* <span data-ttu-id="a4b51-327">Çok sınıflı değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a4b51-327">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="a4b51-328">Model değerlendirir ve metrikleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a4b51-328">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="a4b51-329">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4b51-329">Displays the metrics.</span></span>

<span data-ttu-id="a4b51-330">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `BuildAndTrainModel` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="a4b51-330">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="a4b51-331">Eğitim veri kümesi ile daha önce yaptığınız gibi eşleme başlatma birleştirin ve sınama veri kümesi bir kod satırının içine yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="a4b51-331">As you did previously with the training dataset, you can combine the initialization, mapping, and test dataset loading into one line of code.</span></span> <span data-ttu-id="a4b51-332">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-332">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="a4b51-333">Aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a4b51-333">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="a4b51-334">`MulticlassClassificationContext.Evaluate` İçin bir sarmalayıcı olan <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> belirtilen veri kümesi kullanan model için Kalite Ölçümleri hesaplar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-334">The `MulticlassClassificationContext.Evaluate` is a wrapper for the <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> method that computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="a4b51-335">Döndürür bir <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> sınıflı sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="a4b51-335">It returns a <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="a4b51-336">Model kalitesini belirlemek için ölçümleri görüntülemek için bunları ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-336">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="a4b51-337">Kullanımına dikkat edin `Transform` machine Learning yöntemi `_trainedModel` özellikleri giriş ve tahmin döndürmek için genel değişkeni (dönüştürücü).</span><span class="sxs-lookup"><span data-stu-id="a4b51-337">Notice the use of the `Transform` method of the machine learning `_trainedModel` global variable (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="a4b51-338">Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="a4b51-338">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="a4b51-339">Aşağıdaki ölçümler sınıflı sınıflandırma için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="a4b51-339">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="a4b51-340">Mikro doğruluğu - her örnek sınıfı çifti eşit doğruluğu ölçüme katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a4b51-340">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="a4b51-341">Mikro doğruluğu, 1 olarak mümkün olduğunca yakın olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b51-341">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="a4b51-342">Makro doğruluğu - her sınıf eşit doğruluğu ölçüme katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a4b51-342">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="a4b51-343">Azınlık sınıfları daha büyük bir sınıf olarak eşit ağırlık verilir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-343">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="a4b51-344">Makrosu 1 olarak mümkün olduğunca yakın olmasını doğruluğu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-344">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="a4b51-345">Günlük zarar - bkz [günlük kaybı](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="a4b51-345">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="a4b51-346">Sıfır olarak mümkün olduğunca yakın olmasını günlük zarar kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-346">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="a4b51-347">Günlük kaybı azaltma - aralıkları gelen [-INF, 100], burada 100 mükemmel Öngörüler ve 0, ortalama Öngörüler gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-347">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="a4b51-348">Günlük kaybı azaltma sıfır olarak mümkün olduğunca yakın olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b51-348">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="a4b51-349">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a4b51-349">Displaying the metrics for model validation</span></span>

<span data-ttu-id="a4b51-350">Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a4b51-350">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a><span data-ttu-id="a4b51-351">Eğitilen ve değerlendirilen modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="a4b51-351">Save the trained and evaluated model</span></span>

<span data-ttu-id="a4b51-352">Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain%601> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine.</span><span class="sxs-lookup"><span data-stu-id="a4b51-352">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="a4b51-353">Eğitilen model bir .zip dosyası olarak kaydetmek için çağırmak için aşağıdaki kodu ekleyin. `SaveModelAsFile` yöntemi olarak bir sonraki satırda `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="a4b51-353">To save your trained model to a .zip file, add the following code to call the `SaveModelAsFile` method as the next line in `BuildAndTrainModel`:</span></span>

[!code-csharp[CallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="a4b51-354">Bir .zip dosyası olarak modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="a4b51-354">Save the model as a .zip file</span></span>

<span data-ttu-id="a4b51-355">Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="a4b51-355">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="a4b51-356">`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="a4b51-356">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="a4b51-357">Model bir .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a4b51-357">Saves the model as a .zip file.</span></span>

<span data-ttu-id="a4b51-358">Ardından, yeniden kullanılabilir ve diğer uygulamalarda kullanılan model kaydetmek için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4b51-358">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="a4b51-359">`ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="a4b51-359">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="a4b51-360">Model zip dosyası olarak kaydetmek için oluşturacağınız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a4b51-360">To save the model as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="a4b51-361">Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="a4b51-361">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

<span data-ttu-id="a4b51-362">Bir konsol iletisi ile yazarak dosyasının nerede yazılmıştır görüntüleyebilir `_modelPath`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="a4b51-362">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="a4b51-363">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="a4b51-363">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="a4b51-364">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="a4b51-364">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="a4b51-365">Oluşturma `PredictIssue` yöntemi hemen sonrasına `Evaluate` yöntemi (ve hemen önce `SaveModelAsFile` yöntemi), aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="a4b51-365">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="a4b51-366">`PredictIssue` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="a4b51-366">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="a4b51-367">Test verilerini tek bir konu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a4b51-367">Creates a single issue of test data.</span></span>
* <span data-ttu-id="a4b51-368">Test verilerini temel alarak alan tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="a4b51-368">Predicts Area based on test data.</span></span>
* <span data-ttu-id="a4b51-369">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="a4b51-369">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="a4b51-370">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4b51-370">Displays the predicted results.</span></span>

<span data-ttu-id="a4b51-371">İlk olarak, aşağıdaki kod ile daha önce kaydettiğiniz model yüklenemiyor:</span><span class="sxs-lookup"><span data-stu-id="a4b51-371">First, load the model that you saved previously with the following code:</span></span>

[!code-csharp[LoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

<span data-ttu-id="a4b51-372">Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="a4b51-372">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="a4b51-373">Bir modeliniz olduğuna göre tek bir GitHub sorunu veri örneğini alan GitHub etiketini tahmin etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b51-373">Now that you have a model, you can use that to predict the Area GitHub label of a single instance of the GitHub issue data.</span></span> <span data-ttu-id="a4b51-374">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="a4b51-374">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="a4b51-375">Giriş verilerini bir dizedir ve özellik kazandırma sayesinde modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-375">The input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="a4b51-376">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="a4b51-376">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="a4b51-377">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="a4b51-377">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="a4b51-378">Aşağıdaki kodu ekleyin `PredictIssue` yöntemi tahminler elde etmek için:</span><span class="sxs-lookup"><span data-stu-id="a4b51-378">Add the following code to the `PredictIssue` method for the predictions:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="a4b51-379">Tahmin için yüklenen modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="a4b51-379">Using the loaded model for prediction</span></span>

<span data-ttu-id="a4b51-380">Görüntü `Area` sorunu kategorilere ayırmak ve buna göre hareket üzerinde için.</span><span class="sxs-lookup"><span data-stu-id="a4b51-380">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="a4b51-381">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="a4b51-381">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="a4b51-382">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="a4b51-382">Results</span></span>

<span data-ttu-id="a4b51-383">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4b51-383">Your results should be similar to the following.</span></span> <span data-ttu-id="a4b51-384">İşlem hattı işlediği gibi iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4b51-384">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="a4b51-385">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b51-385">You may see warnings, or processing messages.</span></span> <span data-ttu-id="a4b51-386">Bu iletiler, anlaşılması için aşağıdaki sonuçlarından kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="a4b51-386">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="a4b51-387">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="a4b51-387">Congratulations!</span></span> <span data-ttu-id="a4b51-388">Bir machine learning modeli sınıflandırmak ve bir alan etiketini bir GitHub sorunu için tahmin etmek için şimdi başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="a4b51-388">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="a4b51-389">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.</span><span class="sxs-lookup"><span data-stu-id="a4b51-389">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a4b51-390">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a4b51-390">Next steps</span></span>

<span data-ttu-id="a4b51-391">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="a4b51-391">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a4b51-392">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="a4b51-392">Understand the problem</span></span>
> * <span data-ttu-id="a4b51-393">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="a4b51-393">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="a4b51-394">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="a4b51-394">Prepare your data</span></span>
> * <span data-ttu-id="a4b51-395">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a4b51-395">Transform the data</span></span>
> * <span data-ttu-id="a4b51-396">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="a4b51-396">Train the model</span></span>
> * <span data-ttu-id="a4b51-397">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="a4b51-397">Evaluate the model</span></span>
> * <span data-ttu-id="a4b51-398">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="a4b51-398">Predict with the trained model</span></span>
> * <span data-ttu-id="a4b51-399">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="a4b51-399">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="a4b51-400">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="a4b51-400">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a4b51-401">Taksi taksi göstergesi</span><span class="sxs-lookup"><span data-stu-id="a4b51-401">Taxi Fare Predictor</span></span>](taxi-fare.md)
