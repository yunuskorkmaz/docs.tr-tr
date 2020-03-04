---
title: 'Öğretici: destek sorunlarını kategorilere ayırma-birden çok Lass sınıflandırması'
description: Birden çok Lass sınıflandırma senaryosunda ML.NET kullanarak bunları belirli bir alana atamaya yönelik GitHub sorunlarını sınıflandırın.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 50980cd933054825bf21f955b0341dd8e66f3e62
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239943"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a><span data-ttu-id="8bf86-103">Öğretici: ML.NET ile birden çok Lass sınıflandırması kullanarak destek sorunlarını kategorilere ayırma</span><span class="sxs-lookup"><span data-stu-id="8bf86-103">Tutorial: Categorize support issues using multiclass classification with ML.NET</span></span>

<span data-ttu-id="8bf86-104">Bu örnek öğreticide, Visual Studio 'da kullanılan C# bir .NET Core konsol uygulaması aracılığıyla bir GitHub sorununun alan etiketini sınıflandırdığı ve tahmin eden bir modeli eğiten bir GitHub sorunu Sınıflandırıcısı oluşturmak için ml.NET kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="8bf86-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="8bf86-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="8bf86-106">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="8bf86-106">Prepare your data</span></span>
> * <span data-ttu-id="8bf86-107">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8bf86-107">Transform the data</span></span>
> * <span data-ttu-id="8bf86-108">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8bf86-108">Train the model</span></span>
> * <span data-ttu-id="8bf86-109">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8bf86-109">Evaluate the model</span></span>
> * <span data-ttu-id="8bf86-110">Eğitilen modelle birlikte tahmin edin</span><span class="sxs-lookup"><span data-stu-id="8bf86-110">Predict with the trained model</span></span>
> * <span data-ttu-id="8bf86-111">Yüklü bir modelle dağıtım ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="8bf86-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="8bf86-112">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bf86-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8bf86-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8bf86-113">Prerequisites</span></span>

* <span data-ttu-id="8bf86-114">[Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="8bf86-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="8bf86-115">[GitHub sorunları sekmeyle ayrılmış dosya (issues_train. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="8bf86-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="8bf86-116">[GitHub, test sekmeyle ayrılmış dosyası (issues_test. TSV) ile karşılaşır](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="8bf86-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="8bf86-117">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bf86-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="8bf86-118">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bf86-118">Create a project</span></span>

1. <span data-ttu-id="8bf86-119">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="8bf86-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="8bf86-120">Menü çubuğundan **dosya** > **Yeni** > **projesi** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="8bf86-121">**Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="8bf86-122">Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="8bf86-123">**Ad** metin kutusuna "Githubıssueclassıflıve" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="8bf86-124">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="8bf86-125">**Çözüm Gezgini**, projenize sağ tıklayın ve > **Yeni klasör** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="8bf86-126">"Data" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8bf86-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="8bf86-127">Modelinize kaydetmek için projenizde *modeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="8bf86-128">**Çözüm Gezgini**, projenize sağ tıklayın ve > **Yeni klasör** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="8bf86-129">"Modeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8bf86-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="8bf86-130">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="8bf86-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="8bf86-131">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8bf86-132">Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml** araması yapın ve **yüklemeyi** seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="8bf86-133">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="8bf86-134">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="8bf86-134">Prepare your data</span></span>

1. <span data-ttu-id="8bf86-135">[İssues_train. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri kümelerini indirin ve daha önce oluşturulan *veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="8bf86-136">Makine öğrenimi modelini ve ikincisini gösteren ilk veri kümesi, modelinizin ne kadar doğru olduğunu değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="8bf86-137">Çözüm Gezgini, \*. tsv dosyalarının her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="8bf86-138">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="8bf86-139">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="8bf86-139">Create classes and define paths</span></span>

<span data-ttu-id="8bf86-140">Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

<span data-ttu-id="8bf86-141">Son indirilen dosyaların yollarını ve `MLContext`,`DataView`ve `PredictionEngine`için genel değişkenleri tutmak üzere üç genel alan oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="8bf86-142">`_trainDataPath`, modeli eğitmek için kullanılan veri kümesinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="8bf86-143">`_testDataPath`, modeli değerlendirmek için kullanılan veri kümesinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="8bf86-144">`_modelPath`, eğitilen modelin kaydedildiği yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="8bf86-145">`_mlContext`, işleme bağlamı sağlayan <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="8bf86-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="8bf86-146">eğitim veri kümesini işlemek için kullanılan <xref:Microsoft.ML.IDataView> `_trainingDataView`.</span><span class="sxs-lookup"><span data-stu-id="8bf86-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="8bf86-147">`_predEngine`, tek tahminlerde kullanılan <xref:Microsoft.ML.PredictionEngine%602>.</span><span class="sxs-lookup"><span data-stu-id="8bf86-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="8bf86-148">Aşağıdaki kodu, bu yolları ve diğer değişkenleri belirtmek için `Main` yönteminin hemen üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="8bf86-149">Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8bf86-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="8bf86-150">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="8bf86-151">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="8bf86-152">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *GitHubIssueData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="8bf86-153">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="8bf86-154">*GitHubIssueData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="8bf86-155">Aşağıdaki `using` ifadesini *GitHubIssueData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="8bf86-156">Mevcut sınıf tanımını kaldırın ve *GitHubIssueData.cs* dosyasına `GitHubIssue` ve `IssuePrediction`iki sınıfa sahip aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="8bf86-157">`label`, tahmin etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="8bf86-158">Tanımlanan `Features`, modele bir etiketi tahmin etmek için verdiğiniz girişlerdir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="8bf86-159">Veri kümesindeki kaynak sütunlarının dizinlerini belirtmek için [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) kullanın.</span><span class="sxs-lookup"><span data-stu-id="8bf86-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="8bf86-160">`GitHubIssue`, giriş veri kümesi sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8bf86-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="8bf86-161">`ID` ilk sütun (GitHub sorun KIMLIĞI)</span><span class="sxs-lookup"><span data-stu-id="8bf86-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="8bf86-162">ikinci sütun `Area` (eğitim tahmini)</span><span class="sxs-lookup"><span data-stu-id="8bf86-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="8bf86-163">üçüncü sütun `Title` (GitHub sorun başlığı), `Area` tahmin etmek için kullanılan ilk `feature`.</span><span class="sxs-lookup"><span data-stu-id="8bf86-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="8bf86-164">dördüncü sütun `Description`, `Area` tahmin etmek için kullanılan ikinci `feature`</span><span class="sxs-lookup"><span data-stu-id="8bf86-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="8bf86-165">`IssuePrediction`, model eğitilen bir tahmin için kullanılan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="8bf86-166">Tek bir `string` (`Area`) ve bir `PredictedLabel` `ColumnName` özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="8bf86-167">`PredictedLabel`, tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="8bf86-168">Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="8bf86-169">Tüm ML.NET işlemleri [Mlcontext](xref:Microsoft.ML.MLContext) sınıfında başlar.</span><span class="sxs-lookup"><span data-stu-id="8bf86-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="8bf86-170">`mlContext` başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="8bf86-171">Benzer, kavramsal olarak, `Entity Framework``DBContext`.</span><span class="sxs-lookup"><span data-stu-id="8bf86-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="8bf86-172">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="8bf86-172">Initialize variables in Main</span></span>

<span data-ttu-id="8bf86-173">Birden çok harekette tekrarlanabilir/belirleyici sonuçlar için rastgele çekirdek (`seed: 0`) ile `_mlContext` genel değişkenini yeni bir `MLContext` örneğiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="8bf86-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="8bf86-174">`Console.WriteLine("Hello World!")` satırını `Main` yönteminde aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="8bf86-175">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="8bf86-175">Load the data</span></span>

<span data-ttu-id="8bf86-176">ML.NET, sayısal veya metin tablolu verileri tanımlamaya yönelik esnek ve verimli bir yöntem olarak [ıdataview sınıfını](xref:Microsoft.ML.IDataView) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="8bf86-177">`IDataView` metin dosyalarını veya gerçek zamanlı olarak yükleyebilirsiniz (örneğin, SQL veritabanı veya günlük dosyaları).</span><span class="sxs-lookup"><span data-stu-id="8bf86-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="8bf86-178">`_trainingDataView` genel değişkenini, işlem hattı için kullanmak üzere başlatmak ve yüklemek için, `mlContext` başlatmadan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

<span data-ttu-id="8bf86-179">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bf86-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="8bf86-180">Veri yolu değişkenlerini alır ve bir `IDataView`döndürür.</span><span class="sxs-lookup"><span data-stu-id="8bf86-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="8bf86-181">`Main` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

<span data-ttu-id="8bf86-182">`ProcessData` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8bf86-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="8bf86-183">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8bf86-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="8bf86-184">İşlem ardışık düzenini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8bf86-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="8bf86-185">Aşağıdaki kodu kullanarak, `Main` yönteminden hemen sonra `ProcessData` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="8bf86-186">Özellikleri Ayıkla ve verileri Dönüştür</span><span class="sxs-lookup"><span data-stu-id="8bf86-186">Extract Features and transform the data</span></span>

<span data-ttu-id="8bf86-187">Bir `GitHubIssue`için GitHub etiketini tahmin etmek istediğiniz için [Mapvaluetokey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanarak `Area` sütununu bir sayısal anahtar türü `Label` sütununa (sınıflandırma algoritmaları tarafından kabul edilen bir biçim) dönüştürün ve yeni bir veri kümesi sütunu olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

<span data-ttu-id="8bf86-188">Sonra, metin (`Title` ve `Description`) sütunlarını her bir `TitleFeaturized` ve `DescriptionFeaturized`için sayısal bir vektöre dönüştüren `mlContext.Transforms.Text.FeaturizeText` çağırın.</span><span class="sxs-lookup"><span data-stu-id="8bf86-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="8bf86-189">Aşağıdaki kodla, her iki sütun için de işlem hattına bir şekilde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

<span data-ttu-id="8bf86-190">Veri hazırlığında son adım, [Birleştir ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) yöntemini kullanarak tüm özellik sütunlarını **Özellikler** sütunuyla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="8bf86-191">Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler.</span><span class="sxs-lookup"><span data-stu-id="8bf86-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="8bf86-192">Aşağıdaki kodla bu dönüşümü işlem hattına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 <span data-ttu-id="8bf86-193">Daha sonra, verileri birden çok kez yinelemek için bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> ekleyin. bu nedenle, aşağıdaki kodda olduğu gibi, önbelleği kullanmak daha iyi bir performans alabilir:</span><span class="sxs-lookup"><span data-stu-id="8bf86-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="8bf86-194">Eğitim süresini azaltmak için küçük/orta veri kümeleri için AppendCacheCheckpoint kullanın.</span><span class="sxs-lookup"><span data-stu-id="8bf86-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="8bf86-195">Bunu kullanmayın (kaldırın. Çok büyük veri kümelerini işlerken AppendCacheCheckpoint ()).</span><span class="sxs-lookup"><span data-stu-id="8bf86-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="8bf86-196">`ProcessData` yönteminin sonundaki işlem hattını döndürün.</span><span class="sxs-lookup"><span data-stu-id="8bf86-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

<span data-ttu-id="8bf86-197">Bu adım ön işleme/korleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="8bf86-198">ML.NET ' de kullanılabilen ek bileşenleri kullanmak modelinize daha iyi sonuçlar verebilir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="8bf86-199">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="8bf86-199">Build and train the model</span></span>

<span data-ttu-id="8bf86-200">`BuildAndTrainModel`yöntemine aşağıdaki çağrıyı `Main` yönteminde sonraki kod satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="8bf86-201">`BuildAndTrainModel` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8bf86-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="8bf86-202">Eğitim algoritması sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="8bf86-203">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="8bf86-203">Trains the model.</span></span>
* <span data-ttu-id="8bf86-204">Eğitim verilerine göre alanı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="8bf86-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="8bf86-205">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="8bf86-205">Returns the model.</span></span>

<span data-ttu-id="8bf86-206">Aşağıdaki kodu kullanarak, `Main` yönteminden hemen sonra `BuildAndTrainModel` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="8bf86-207">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="8bf86-207">About the classification task</span></span>

<span data-ttu-id="8bf86-208">Sınıflandırma, bir öğe veya veri satırının kategorisini, türünü veya sınıfını **tespit** etmek için verileri kullanan bir makine öğrenimi görevi ve genellikle aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="8bf86-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="8bf86-209">İkili: A veya B.</span><span class="sxs-lookup"><span data-stu-id="8bf86-209">Binary: either A or B.</span></span>
* <span data-ttu-id="8bf86-210">Birden çok sınıf: tek bir model kullanılarak tahmin edilebilir birden fazla kategori.</span><span class="sxs-lookup"><span data-stu-id="8bf86-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="8bf86-211">Bu tür bir sorun için, tek bir Lass sınıflandırma öğrenme algoritması kullanın, çünkü sorun kategorisi tahmininizde yalnızca iki (ikili) yerine birden çok kategori (birden çok Lass) olabilir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="8bf86-212">`BuildAndTrainModel()`' deki ilk kod satırı olarak aşağıdakini ekleyerek, makine öğrenimi algoritmasını veri dönüştürme tanımlarına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

<span data-ttu-id="8bf86-213">[Sdcamaximumentropi](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) , birden çok Lass sınıflandırma eğitim algoritmadır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="8bf86-214">Bu, `pipeline` eklenir ve geçmiş verilerden öğrenme `Title` ve `Description` (`Features`) ve `Label` giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8bf86-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="8bf86-215">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8bf86-215">Train the model</span></span>

<span data-ttu-id="8bf86-216">Modeli `splitTrainSet` verilerine sığdırın ve `BuildAndTrainModel()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="8bf86-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

<span data-ttu-id="8bf86-217">`Fit()`yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi ister.</span><span class="sxs-lookup"><span data-stu-id="8bf86-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="8bf86-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneği üzerinde bir tahmin gerçekleştirmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="8bf86-219">`BuildAndTrainModel()` yönteminin sonraki satırı olarak bunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="8bf86-220">Eğitilen modelle birlikte tahmin edin</span><span class="sxs-lookup"><span data-stu-id="8bf86-220">Predict with the trained model</span></span>

<span data-ttu-id="8bf86-221">Bir `GitHubIssue`örneği oluşturarak eğitilen modelin `Predict` yönteminde tahminini test etmek için bir GitHub sorunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

<span data-ttu-id="8bf86-222">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevini kullanın, tek bir veri satırında tahmin yapar:</span><span class="sxs-lookup"><span data-stu-id="8bf86-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="8bf86-223">Modeli kullanma: tahmin sonuçları</span><span class="sxs-lookup"><span data-stu-id="8bf86-223">Using the model: prediction results</span></span>

<span data-ttu-id="8bf86-224">Sonuçları paylaşmak ve bunlara göre işlem yapmak için `GitHubIssue` ve karşılık gelen `Area` etiket tahminini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="8bf86-225">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodunu kullanarak sonuçlar için bir görüntü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="8bf86-226">Değerlendirme için kullanılmak üzere eğitilen modeli döndürün</span><span class="sxs-lookup"><span data-stu-id="8bf86-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="8bf86-227">`BuildAndTrainModel` yönteminin sonundaki modeli döndürün.</span><span class="sxs-lookup"><span data-stu-id="8bf86-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="8bf86-228">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8bf86-228">Evaluate the model</span></span>

<span data-ttu-id="8bf86-229">Modeli oluşturup eğitildiniz, artık kalite güvencesi ve doğrulama için farklı bir veri kümesiyle değerlendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="8bf86-230">`Evaluate` yönteminde, `BuildAndTrainModel` oluşturulan model değerlendirilmek üzere geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="8bf86-231">Aşağıdaki kodda olduğu gibi, `BuildAndTrainModel`hemen sonra `Evaluate` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="8bf86-232">`Evaluate` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8bf86-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="8bf86-233">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="8bf86-233">Loads the test dataset.</span></span>
* <span data-ttu-id="8bf86-234">Birden çok Lass değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="8bf86-235">Modeli değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="8bf86-236">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8bf86-236">Displays the metrics.</span></span>

<span data-ttu-id="8bf86-237">Aşağıdaki kodu kullanarak, `BuildAndTrainModel` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

<span data-ttu-id="8bf86-238">Daha önce eğitim veri kümesiyle yaptığınız gibi, `Evaluate` yöntemine aşağıdaki kodu ekleyerek test veri kümesini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

<span data-ttu-id="8bf86-239">[Değerlendir ()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) yöntemi, belirtilen veri kümesini kullanarak model için kalite ölçümlerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8bf86-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="8bf86-240">Birden çok Lass Classification değerlendiricileri tarafından hesaplanan genel ölçümleri içeren bir <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8bf86-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="8bf86-241">Modelin kalitesini belirleme ölçümlerini göstermek için önce bunları almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="8bf86-242">Özellikleri girmek ve tahmin getirmeleri için Machine Learning `_trainedModel` genel değişkeninin (bir [ıranseski](xref:Microsoft.ML.ITransformer)) [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yönteminin kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="8bf86-243">Aşağıdaki kodu `Evaluate` yöntemine sonraki satır olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

<span data-ttu-id="8bf86-244">Aşağıdaki ölçümler birden çok Lass sınıflandırması için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="8bf86-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="8bf86-245">Mikro doğruluk-her örnek sınıf çifti, doğruluk ölçüsüne eşit olarak katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="8bf86-246">Mikro doğruluk ' ın mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="8bf86-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="8bf86-247">Makro doğruluğu-her sınıf, doğruluk ölçüsüne eşit olarak katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="8bf86-248">Minınlık sınıflarına daha büyük sınıflar olarak eşit ağırlık verilir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="8bf86-249">Makro doğruluğunu mümkün olduğunca yakın bir şekilde tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bf86-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="8bf86-250">Günlük-kayıp- [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="8bf86-251">Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="8bf86-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="8bf86-252">Günlük kaybı azaltma-[-inf, 1,00] aralığından, 1,00 ' nin kusursuz tahminlerden ve 0 ' ın, ortalama tahmine dayalı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="8bf86-253">Günlük kaybını azaltmanın mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="8bf86-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="8bf86-254">Model doğrulama ölçümlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8bf86-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="8bf86-255">Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8bf86-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="8bf86-256">Modeli bir dosyaya kaydet</span><span class="sxs-lookup"><span data-stu-id="8bf86-256">Save the model to a file</span></span>

<span data-ttu-id="8bf86-257">Modelinize her memnun olduktan sonra, daha sonra veya başka bir uygulamada tahmine dayalı hale getirmek için dosyayı bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="8bf86-258">`Evaluate` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="8bf86-259">`Evaluate` yönteminizin altında `SaveModelAsFile` yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8bf86-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="8bf86-260">Aşağıdaki kodu `SaveModelAsFile` yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="8bf86-261">Bu kod, eğitilen modeli seri hale getirmek ve bir ZIP dosyası olarak depolamak için [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="8bf86-262">Bir modelle dağıtım ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="8bf86-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="8bf86-263">Aşağıdaki kodu kullanarak, `Evaluate` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

<span data-ttu-id="8bf86-264">Aşağıdaki kodu kullanarak, `Evaluate` yönteminden hemen sonra (ve `SaveModelAsFile` yönteminden hemen önce) `PredictIssue` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="8bf86-265">`PredictIssue` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8bf86-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="8bf86-266">Kaydedilen modeli yükler</span><span class="sxs-lookup"><span data-stu-id="8bf86-266">Loads the saved model</span></span>
* <span data-ttu-id="8bf86-267">Test verileri için tek bir sorun oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bf86-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="8bf86-268">Test verilerine göre alanı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="8bf86-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="8bf86-269">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="8bf86-270">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8bf86-270">Displays the predicted results.</span></span>

<span data-ttu-id="8bf86-271">`PredictIssue` yöntemine aşağıdaki kodu ekleyerek kayıtlı modeli uygulamanıza yükleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

<span data-ttu-id="8bf86-272">Bir `GitHubIssue`örneği oluşturarak eğitilen modelin `Predict` yönteminde tahminini test etmek için bir GitHub sorunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bf86-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

<span data-ttu-id="8bf86-273">Daha önce yaptığınız gibi, aşağıdaki kodla bir `PredictionEngine` örneği oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="8bf86-274">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="8bf86-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="8bf86-276">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="8bf86-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="8bf86-277">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanız genelinde kullanılmak üzere [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnelerinin bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8bf86-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="8bf86-278">[ASP.NET Core Web API 'sindeki `PredictionEnginePool` kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="8bf86-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="8bf86-279">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="8bf86-280">Aşağıdaki kodu tahmin için `PredictIssue` yöntemine ekleyerek GitHub etiketini tahmin etmek için `PredictionEngine` kullanın:</span><span class="sxs-lookup"><span data-stu-id="8bf86-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="8bf86-281">Yüklü modeli tahmin için kullanma</span><span class="sxs-lookup"><span data-stu-id="8bf86-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="8bf86-282">Sorunu kategorilere ayırarak ve buna uygun şekilde hareket edebilmek için `Area` görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="8bf86-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="8bf86-283">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodunu kullanarak sonuçlar için bir görüntü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8bf86-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="8bf86-284">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="8bf86-284">Results</span></span>

<span data-ttu-id="8bf86-285">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-285">Your results should be similar to the following.</span></span> <span data-ttu-id="8bf86-286">İşlem hattı sırasında iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8bf86-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="8bf86-287">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bf86-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="8bf86-288">Bu iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8bf86-288">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="8bf86-289">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="8bf86-289">Congratulations!</span></span> <span data-ttu-id="8bf86-290">Artık bir GitHub sorunu için bir alan etiketini sınıflandırmak ve tahmin etmek üzere bir makine öğrenimi modeli oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="8bf86-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="8bf86-291">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bf86-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8bf86-292">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8bf86-292">Next steps</span></span>

<span data-ttu-id="8bf86-293">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="8bf86-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="8bf86-294">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="8bf86-294">Prepare your data</span></span>
> * <span data-ttu-id="8bf86-295">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8bf86-295">Transform the data</span></span>
> * <span data-ttu-id="8bf86-296">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8bf86-296">Train the model</span></span>
> * <span data-ttu-id="8bf86-297">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8bf86-297">Evaluate the model</span></span>
> * <span data-ttu-id="8bf86-298">Eğitilen modelle birlikte tahmin edin</span><span class="sxs-lookup"><span data-stu-id="8bf86-298">Predict with the trained model</span></span>
> * <span data-ttu-id="8bf86-299">Yüklü bir modelle dağıtım ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="8bf86-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="8bf86-300">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="8bf86-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8bf86-301">Taxı tarifeli havayolu Predictor</span><span class="sxs-lookup"><span data-stu-id="8bf86-301">Taxi Fare Predictor</span></span>](predict-prices.md)
