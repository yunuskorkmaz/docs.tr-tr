---
title: 'Öğretici: Destek sorunları - sınıflı sınıflandırma kategorilere ayırma'
description: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları için belirli bir alanla atamak sınıflandırmak için nasıl kullanılacağını keşfedin.
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: d47522bef632de1aac890d4de384c1b2c16b7a50
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877338"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a><span data-ttu-id="f32cc-103">Öğretici: Destek sorunları çok sınıflı sınıflandırma kullanarak ML .NET ile kategorilere ayırma</span><span class="sxs-lookup"><span data-stu-id="f32cc-103">Tutorial: Categorize support issues using multiclass classification with ML .NET</span></span>

<span data-ttu-id="f32cc-104">Bu örnek öğretici ML.NET sınıflandırır ve bir .NET Core konsol uygulaması kullanarak aracılığıyla bir GitHub sorunu alan etiketini tahmin modeli eğitmek için bir GitHub sorunu sınıflandırıcı oluşturma kullanmayı göstermektedir C# Visual Studio'da.</span><span class="sxs-lookup"><span data-stu-id="f32cc-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="f32cc-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="f32cc-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="f32cc-106">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="f32cc-106">Prepare your data</span></span>
> * <span data-ttu-id="f32cc-107">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f32cc-107">Transform the data</span></span>
> * <span data-ttu-id="f32cc-108">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f32cc-108">Train the model</span></span>
> * <span data-ttu-id="f32cc-109">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f32cc-109">Evaluate the model</span></span>
> * <span data-ttu-id="f32cc-110">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f32cc-110">Predict with the trained model</span></span>
> * <span data-ttu-id="f32cc-111">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f32cc-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="f32cc-112">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.</span><span class="sxs-lookup"><span data-stu-id="f32cc-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f32cc-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f32cc-113">Prerequisites</span></span>

* <span data-ttu-id="f32cc-114">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="f32cc-115">[Github sorunlar sekmeyle dosyası (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="f32cc-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="f32cc-116">[Github sorunları sekmeyle dosyası (issues_test.tsv) test](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="f32cc-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f32cc-117">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f32cc-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="f32cc-118">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="f32cc-118">Create a project</span></span>

1. <span data-ttu-id="f32cc-119">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="f32cc-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="f32cc-120">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="f32cc-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="f32cc-121">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="f32cc-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="f32cc-122">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="f32cc-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="f32cc-123">İçinde **adı** metin kutusuna "GitHubIssueClassification" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f32cc-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="f32cc-124">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="f32cc-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="f32cc-125">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="f32cc-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="f32cc-126">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f32cc-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="f32cc-127">Adlı bir dizin oluşturmak *modelleri* modelinizi kaydetmek için projenizde:</span><span class="sxs-lookup"><span data-stu-id="f32cc-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="f32cc-128">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="f32cc-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="f32cc-129">"Modeli" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f32cc-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="f32cc-130">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="f32cc-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f32cc-131">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="f32cc-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f32cc-132">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**seçin **v 1.0.0** paketini listede bulun ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f32cc-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v 1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="f32cc-133">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="f32cc-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="f32cc-134">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="f32cc-134">Prepare your data</span></span>

1. <span data-ttu-id="f32cc-135">İndirme [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="f32cc-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="f32cc-136">İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="f32cc-137">Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="f32cc-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="f32cc-138">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="f32cc-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f32cc-139">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="f32cc-139">Create classes and define paths</span></span>

<span data-ttu-id="f32cc-140">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="f32cc-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="f32cc-141">Yolları kısa bir süre önce indirilen dosyaları ve genel değişkenleri tutmak için üç genel alanlar oluşturmak `MLContext`,`DataView`, ve `PredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="f32cc-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="f32cc-142">`_trainDataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="f32cc-143">`_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="f32cc-144">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="f32cc-145">`_mlContext` olan <xref:Microsoft.ML.MLContext> , işlem bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f32cc-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="f32cc-146">`_trainingDataView` olan <xref:Microsoft.ML.IDataView> eğitim veri kümesi işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="f32cc-147">`_predEngine` olan <xref:Microsoft.ML.PredictionEngine%602> tek Tahminler elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="f32cc-148">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollar ve diğer değişkenlerini belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="f32cc-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="f32cc-149">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f32cc-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="f32cc-150">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f32cc-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="f32cc-151">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="f32cc-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="f32cc-152">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="f32cc-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="f32cc-153">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f32cc-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f32cc-154">*GitHubIssueData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="f32cc-155">Aşağıdaki `using` üstüne deyimi *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="f32cc-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="f32cc-156">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `GitHubIssue` ve `IssuePrediction`, *GitHubIssueData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="f32cc-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="f32cc-157">`label` Tahmin etmek istediğiniz sütun.</span><span class="sxs-lookup"><span data-stu-id="f32cc-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="f32cc-158">Tanımlanan `Features` etiketi tahmin modelini size girişleri.</span><span class="sxs-lookup"><span data-stu-id="f32cc-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="f32cc-159">Kullanım [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) veri kümesinde kaynak sütunları dizin belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f32cc-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="f32cc-160">`GitHubIssue` Giriş veri kümesi sınıfı ve aşağıdaki <xref:System.String> alanlar:</span><span class="sxs-lookup"><span data-stu-id="f32cc-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="f32cc-161">İlk sütun `ID` (GitHub sorunu kimliği)</span><span class="sxs-lookup"><span data-stu-id="f32cc-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="f32cc-162">ikinci sütunda `Area` (eğitim tahmin)</span><span class="sxs-lookup"><span data-stu-id="f32cc-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="f32cc-163">üçüncü sütunda `Title` (GitHub sorun başlığı) sanal makinede ilk `feature` tahmin etmek için kullanılan `Area`</span><span class="sxs-lookup"><span data-stu-id="f32cc-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="f32cc-164">Dördüncü sütun `Description` ikinci `feature` tahmin etmek için kullanılan `Area`</span><span class="sxs-lookup"><span data-stu-id="f32cc-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="f32cc-165">`IssuePrediction` eğitilen modelin sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="f32cc-166">Tek bir sahip `string` (`Area`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f32cc-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="f32cc-167">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="f32cc-168">Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="f32cc-169">Tüm ML.NET işlemleri başlangıç süresi [MLContext](xref:Microsoft.ML.MLContext) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f32cc-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="f32cc-170">Başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f32cc-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f32cc-171">Bu, kavramsal olarak, benzer `DBContext` içinde `Entity Framework`.</span><span class="sxs-lookup"><span data-stu-id="f32cc-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="f32cc-172">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="f32cc-172">Initialize variables in Main</span></span>

<span data-ttu-id="f32cc-173">Başlatma `_mlContext` yeni bir örneğini genel değişkenin `MLContext` ile rastgele bir tohum (`seed: 0`) arasında birden çok eğitimleri/deterministic tekrarlanabilir sonuçlar.</span><span class="sxs-lookup"><span data-stu-id="f32cc-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="f32cc-174">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f32cc-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="f32cc-175">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f32cc-175">Load the data</span></span>

<span data-ttu-id="f32cc-176">ML.NET kullanan [IDataView sınıfı](xref:Microsoft.ML.IDataView) sayısal ya da metin tablosal verileri açıklamak esnek ve verimli bir yolu olarak.</span><span class="sxs-lookup"><span data-stu-id="f32cc-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="f32cc-177">`IDataView` iki metin dosyalarını yükleyebilir veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları).</span><span class="sxs-lookup"><span data-stu-id="f32cc-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="f32cc-178">Başlatma ve yüklemek için `_trainingDataView` ardışık düzeni için kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:</span><span class="sxs-lookup"><span data-stu-id="f32cc-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="f32cc-179">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur.</span><span class="sxs-lookup"><span data-stu-id="f32cc-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="f32cc-180">Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="f32cc-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="f32cc-181">Sonraki kod satırı olarak ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f32cc-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="f32cc-182">`ProcessData` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f32cc-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="f32cc-183">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f32cc-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="f32cc-184">İşleme işlem hattı döndürür.</span><span class="sxs-lookup"><span data-stu-id="f32cc-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="f32cc-185">Oluşturma `ProcessData` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="f32cc-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="f32cc-186">Özellikleri ayıklayın ve verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f32cc-186">Extract Features and transform the data</span></span>

<span data-ttu-id="f32cc-187">Alan GitHub etiketi tahmin etmek istediğiniz gibi bir `GitHubIssue`, kullanın [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) dönüştürmek için yöntemi `Area` sayısal bir anahtar türü sütununa `Label` sütun (sınıflandırma algoritmalarda kabul bir biçimi ) ve yeni veri kümesi bir sütun olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f32cc-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="f32cc-188">Ardından, arama `mlContext.Transforms.Text.FeaturizeText` metin dönüştürür (`Title` ve `Description`) sayısal bir vektör her adlı sütuna `TitleFeaturized` ve `DescriptionFeaturized`.</span><span class="sxs-lookup"><span data-stu-id="f32cc-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="f32cc-189">Aşağıdaki kod ile işlem hattı her iki sütun için özellik kazandırma sayesinde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f32cc-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="f32cc-190">Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f32cc-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="f32cc-191">Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="f32cc-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="f32cc-192">Aşağıdaki kod ile işlem hattı için bu dönüşümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f32cc-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="f32cc-193">Ardından, ekleme bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> üzerinden yineleme yapma, verileri birden çok kez önbellek kullanarak daha iyi performans için şu kod gibi alabilirsiniz şekilde DataView önbelleğe almak için:</span><span class="sxs-lookup"><span data-stu-id="f32cc-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="f32cc-194">Eğitim süresini azaltmak için AppendCacheCheckpoint küçük/Orta veri kümeleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f32cc-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="f32cc-195">(Kaldırın. bunu kullanmayın Çok büyük veri kümelerinde işlerken AppendCacheCheckpoint()).</span><span class="sxs-lookup"><span data-stu-id="f32cc-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="f32cc-196">Ardışık Düzen sonunda dönüş `ProcessData` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f32cc-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="f32cc-197">Bu adımda, ön işleme/özellik kazandırma sayesinde işler.</span><span class="sxs-lookup"><span data-stu-id="f32cc-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="f32cc-198">ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f32cc-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="f32cc-199">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f32cc-199">Build and train the model</span></span>

<span data-ttu-id="f32cc-200">Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f32cc-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="f32cc-201">`BuildAndTrainModel` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f32cc-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="f32cc-202">Eğitim algoritması sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f32cc-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="f32cc-203">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-203">Trains the model.</span></span>
* <span data-ttu-id="f32cc-204">Eğitim verilerini temel alarak alan tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="f32cc-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="f32cc-205">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="f32cc-205">Returns the model.</span></span>

<span data-ttu-id="f32cc-206">Oluşturma `BuildAndTrainModel` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="f32cc-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="f32cc-207">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="f32cc-207">About the classification task</span></span>

<span data-ttu-id="f32cc-208">Sınıflandırma olan verileri kullanan bir makine öğrenimi görev **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı ve sık sık aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="f32cc-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="f32cc-209">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="f32cc-209">Binary: either A or B.</span></span>
* <span data-ttu-id="f32cc-210">Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="f32cc-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="f32cc-211">Bu sorun türü için birden çok kategoriden (veya çoklu sınıflar) sorun kategorisi tahmininizde olabileceği algoritması, öğrenme veya çoklu sınıflar sınıflandırması yalnızca iki yerine kullanın (ikili).</span><span class="sxs-lookup"><span data-stu-id="f32cc-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="f32cc-212">Machine learning algoritmasını kod ilk satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını ekleme `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="f32cc-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

<span data-ttu-id="f32cc-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) sınıflı sınıflandırma eğitim algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="f32cc-214">Bu eklenen `pipeline` ve özellikleri tespit `Title` ve `Description` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="f32cc-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="f32cc-215">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f32cc-215">Train the model</span></span>

<span data-ttu-id="f32cc-216">Modele uygun `splitTrainSet` veri ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `BuildAndTrainModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f32cc-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="f32cc-217">`Fit()`Yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="f32cc-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) geçirin ve ardından verileri tek bir örneğini tahmin gerçekleştirin izin veren bir kolaylık API, bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="f32cc-219">Bu sonraki satırı olarak ekleyin `BuildAndTrainModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f32cc-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="f32cc-220">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f32cc-220">Predict with the trained model</span></span>

<span data-ttu-id="f32cc-221">Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="f32cc-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="f32cc-222">Kullanım [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi tahmin verilerinin tek bir satırda yapar:</span><span class="sxs-lookup"><span data-stu-id="f32cc-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="f32cc-223">Modeli kullanılarak: tahmin sonuçlarını</span><span class="sxs-lookup"><span data-stu-id="f32cc-223">Using the model: prediction results</span></span>

<span data-ttu-id="f32cc-224">Görüntü `GitHubIssue` ve karşılık gelen `Area` tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için etiket.</span><span class="sxs-lookup"><span data-stu-id="f32cc-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="f32cc-225">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="f32cc-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="f32cc-226">Değerlendirme için kullanılacak modeli eğitilir döndürür</span><span class="sxs-lookup"><span data-stu-id="f32cc-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="f32cc-227">Model sonunda dönüş `BuildAndTrainModel` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f32cc-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="f32cc-228">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f32cc-228">Evaluate the model</span></span>

<span data-ttu-id="f32cc-229">Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="f32cc-230">İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `BuildAndTrainModel` değerlendirilecek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="f32cc-231">Oluşturma `Evaluate` yöntemi hemen sonrasına `BuildAndTrainModel`, aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="f32cc-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate()
{

}
```

<span data-ttu-id="f32cc-232">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f32cc-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="f32cc-233">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="f32cc-233">Loads the test dataset.</span></span>
* <span data-ttu-id="f32cc-234">Çok sınıflı değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f32cc-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="f32cc-235">Model değerlendirir ve metrikleri oluşturma.</span><span class="sxs-lookup"><span data-stu-id="f32cc-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="f32cc-236">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f32cc-236">Displays the metrics.</span></span>

<span data-ttu-id="f32cc-237">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `BuildAndTrainModel` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="f32cc-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="f32cc-238">Aşağıdaki kodu ekleyerek eğitim veri kümesi ile daha önce yaptığınız gibi test veri kümesini yüklemek `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f32cc-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="f32cc-239">[Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) yöntemi, belirtilen veri kümesi kullanan model için Kalite Ölçümleri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f32cc-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="f32cc-240">Döndürür bir <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> sınıflı sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="f32cc-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="f32cc-241">Model kalitesini belirlemek için ölçümleri görüntülemek için bunları ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="f32cc-242">Kullanımına dikkat edin [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) machine Learning yöntemi `_trainedModel` genel değişkeni (bir [ITransformer](xref:Microsoft.ML.ITransformer)) özellikleri giriş ve tahmin döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="f32cc-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="f32cc-243">Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="f32cc-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="f32cc-244">Aşağıdaki ölçümler sınıflı sınıflandırma için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="f32cc-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="f32cc-245">Mikro doğruluğu - her örnek sınıfı çifti eşit doğruluğu ölçüme katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="f32cc-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="f32cc-246">Mikro doğruluğu, 1 olarak mümkün olduğunca yakın olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="f32cc-246">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="f32cc-247">Makro doğruluğu - her sınıf eşit doğruluğu ölçüme katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="f32cc-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="f32cc-248">Azınlık sınıfları daha büyük bir sınıf olarak eşit ağırlık verilir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="f32cc-249">Makrosu 1 olarak mümkün olduğunca yakın olmasını doğruluğu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-249">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="f32cc-250">Günlük zarar - bkz [günlük kaybı](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="f32cc-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="f32cc-251">Sıfır olarak mümkün olduğunca yakın olmasını günlük zarar kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="f32cc-252">Günlük kaybı azaltma - aralıkları gelen [-INF, 100], burada 100 mükemmel Öngörüler ve 0, ortalama Öngörüler gösterir.</span><span class="sxs-lookup"><span data-stu-id="f32cc-252">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="f32cc-253">Günlük kaybı azaltma sıfır olarak mümkün olduğunca yakın olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="f32cc-253">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="f32cc-254">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f32cc-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="f32cc-255">Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f32cc-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="f32cc-256">Dağıtma ve bir modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f32cc-256">Deploy and Predict with a model</span></span>

<span data-ttu-id="f32cc-257">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="f32cc-257">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="f32cc-258">Oluşturma `PredictIssue` yöntemi hemen sonrasına `Evaluate` yöntemi (ve hemen önce `SaveModelAsFile` yöntemi), aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="f32cc-258">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="f32cc-259">`PredictIssue` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f32cc-259">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="f32cc-260">Test verilerini tek bir konu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f32cc-260">Creates a single issue of test data.</span></span>
* <span data-ttu-id="f32cc-261">Test verilerini temel alarak alan tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="f32cc-261">Predicts Area based on test data.</span></span>
* <span data-ttu-id="f32cc-262">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="f32cc-262">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="f32cc-263">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f32cc-263">Displays the predicted results.</span></span>

<span data-ttu-id="f32cc-264">Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:</span><span class="sxs-lookup"><span data-stu-id="f32cc-264">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

<span data-ttu-id="f32cc-265">Daha önce yaptığınız gibi oluşturun bir `PredictionEngine` aşağıdaki kod örneği:</span><span class="sxs-lookup"><span data-stu-id="f32cc-265">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="f32cc-266">Kullanım `PredictionEngine` alan GitHub etiketi için aşağıdaki kodu ekleyerek tahmin etmek için `PredictIssue` yöntemi tahmin için:</span><span class="sxs-lookup"><span data-stu-id="f32cc-266">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="f32cc-267">Tahmin için yüklenen modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="f32cc-267">Using the loaded model for prediction</span></span>

<span data-ttu-id="f32cc-268">Görüntü `Area` sorunu kategorilere ayırmak ve buna göre hareket üzerinde için.</span><span class="sxs-lookup"><span data-stu-id="f32cc-268">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="f32cc-269">Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="f32cc-269">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="f32cc-270">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="f32cc-270">Results</span></span>

<span data-ttu-id="f32cc-271">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f32cc-271">Your results should be similar to the following.</span></span> <span data-ttu-id="f32cc-272">İşlem hattı işlediği gibi iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f32cc-272">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="f32cc-273">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f32cc-273">You may see warnings, or processing messages.</span></span> <span data-ttu-id="f32cc-274">Bu iletiler, anlaşılması için aşağıdaki sonuçlarından kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="f32cc-274">These messages have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="f32cc-275">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="f32cc-275">Congratulations!</span></span> <span data-ttu-id="f32cc-276">Bir machine learning modeli sınıflandırmak ve bir alan etiketini bir GitHub sorunu için tahmin etmek için şimdi başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="f32cc-276">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="f32cc-277">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.</span><span class="sxs-lookup"><span data-stu-id="f32cc-277">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f32cc-278">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f32cc-278">Next steps</span></span>

<span data-ttu-id="f32cc-279">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="f32cc-279">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="f32cc-280">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="f32cc-280">Prepare your data</span></span>
> * <span data-ttu-id="f32cc-281">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f32cc-281">Transform the data</span></span>
> * <span data-ttu-id="f32cc-282">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f32cc-282">Train the model</span></span>
> * <span data-ttu-id="f32cc-283">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f32cc-283">Evaluate the model</span></span>
> * <span data-ttu-id="f32cc-284">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f32cc-284">Predict with the trained model</span></span>
> * <span data-ttu-id="f32cc-285">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f32cc-285">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="f32cc-286">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="f32cc-286">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f32cc-287">Taksi taksi göstergesi</span><span class="sxs-lookup"><span data-stu-id="f32cc-287">Taxi Fare Predictor</span></span>](taxi-fare.md)
