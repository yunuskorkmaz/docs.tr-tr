---
title: 'Öğretici: destek sorunlarını kategorilere ayırma-birden çok Lass sınıflandırması'
description: Birden çok Lass sınıflandırma senaryosunda ML.NET kullanarak bunları belirli bir alana atamaya yönelik GitHub sorunlarını sınıflandırın.
ms.date: 10/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 1cd213653c23c4d713e03d53394885f1f3ebb6f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094585"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a><span data-ttu-id="1e00f-103">Öğretici: ML .NET ile birden çok Lass sınıflandırması kullanarak destek sorunlarını kategorilere ayırma</span><span class="sxs-lookup"><span data-stu-id="1e00f-103">Tutorial: Categorize support issues using multiclass classification with ML .NET</span></span>

<span data-ttu-id="1e00f-104">Bu örnek öğreticide, Visual Studio 'da kullanılan C# bir .NET Core konsol uygulaması aracılığıyla bir GitHub sorununun alan etiketini sınıflandırdığı ve tahmin eden bir modeli eğiten bir GitHub sorunu Sınıflandırıcısı oluşturmak için ml.NET kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="1e00f-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1e00f-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="1e00f-106">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="1e00f-106">Prepare your data</span></span>
> * <span data-ttu-id="1e00f-107">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1e00f-107">Transform the data</span></span>
> * <span data-ttu-id="1e00f-108">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="1e00f-108">Train the model</span></span>
> * <span data-ttu-id="1e00f-109">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1e00f-109">Evaluate the model</span></span>
> * <span data-ttu-id="1e00f-110">Eğitilen modelle birlikte tahmin edin</span><span class="sxs-lookup"><span data-stu-id="1e00f-110">Predict with the trained model</span></span>
> * <span data-ttu-id="1e00f-111">Yüklü bir modelle dağıtım ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="1e00f-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="1e00f-112">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e00f-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1e00f-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="1e00f-113">Prerequisites</span></span>

* <span data-ttu-id="1e00f-114">[Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="1e00f-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="1e00f-115">[GitHub sorunları sekmeyle ayrılmış dosya (issues_train. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="1e00f-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="1e00f-116">[GitHub, test sekmeyle ayrılmış dosyası (issues_test. TSV) ile karşılaşır](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="1e00f-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="1e00f-117">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e00f-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="1e00f-118">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e00f-118">Create a project</span></span>

1. <span data-ttu-id="1e00f-119">Visual Studio 2017 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="1e00f-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="1e00f-120">Menü çubuğundan **dosya** > **Yeni** > **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="1e00f-121">**Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="1e00f-122">Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="1e00f-123">**Ad** metin kutusuna "Githubıssueclassıflıve" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="1e00f-124">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="1e00f-125">**Çözüm Gezgini**, projenize sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="1e00f-126">"Data" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e00f-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="1e00f-127">Modelinize kaydetmek için projenizde *modeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="1e00f-128">**Çözüm Gezgini**, projenize sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="1e00f-129">"Modeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e00f-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="1e00f-130">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="1e00f-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="1e00f-131">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="1e00f-132">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden **v 1.0.0** paketini seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v 1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="1e00f-133">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="1e00f-134">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="1e00f-134">Prepare your data</span></span>

1. <span data-ttu-id="1e00f-135">[İssues_train. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri kümelerini indirin ve daha önce oluşturulan *veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="1e00f-136">Makine öğrenimi modelini ve ikincisini gösteren ilk veri kümesi, modelinizin ne kadar doğru olduğunu değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="1e00f-137">Çözüm Gezgini, \*. tsv dosyalarının her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="1e00f-138">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="1e00f-139">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="1e00f-139">Create classes and define paths</span></span>

<span data-ttu-id="1e00f-140">*Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="1e00f-141">Son indirilen dosyaların yollarını ve `MLContext`, `DataView` ve `PredictionEngine` için genel değişkenleri tutmak üzere üç genel alan oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="1e00f-142">`_trainDataPath`, modeli eğitmek için kullanılan veri kümesinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="1e00f-143">`_testDataPath`, modeli değerlendirmek için kullanılan veri kümesinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="1e00f-144">`_modelPath`, eğitilen modelin kaydedildiği yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="1e00f-145">`_mlContext`, işleme bağlamı sağlayan <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="1e00f-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="1e00f-146">eğitim veri kümesini işlemek için kullanılan <xref:Microsoft.ML.IDataView> `_trainingDataView`.</span><span class="sxs-lookup"><span data-stu-id="1e00f-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="1e00f-147">`_predEngine`, tek tahminlerde kullanılan <xref:Microsoft.ML.PredictionEngine%602>.</span><span class="sxs-lookup"><span data-stu-id="1e00f-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="1e00f-148">Aşağıdaki kodu, bu yolları ve diğer değişkenleri belirtmek için `Main` yönteminin hemen üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="1e00f-149">Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1e00f-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="1e00f-150">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="1e00f-151">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="1e00f-152">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *GitHubIssueData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="1e00f-153">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="1e00f-154">*GitHubIssueData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="1e00f-155">Aşağıdaki `using` ifadesini *GitHubIssueData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="1e00f-156">Mevcut sınıf tanımını kaldırın ve *GitHubIssueData.cs* dosyasına `GitHubIssue` ve `IssuePrediction` iki sınıfa sahip aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="1e00f-157">`label`, tahmin etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="1e00f-158">Tanımlanan `Features`, modele bir etiketi tahmin etmek için verdiğiniz girişlerdir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="1e00f-159">Veri kümesindeki kaynak sütunlarının dizinlerini belirtmek için [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1e00f-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="1e00f-160">`GitHubIssue`, giriş veri kümesi sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1e00f-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="1e00f-161">`ID` ilk sütun (GitHub sorun KIMLIĞI)</span><span class="sxs-lookup"><span data-stu-id="1e00f-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="1e00f-162">ikinci sütun `Area` (eğitim tahmini)</span><span class="sxs-lookup"><span data-stu-id="1e00f-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="1e00f-163">üçüncü sütun `Title` (GitHub sorun başlığı), `Area` tahmin etmek için kullanılan ilk `feature`.</span><span class="sxs-lookup"><span data-stu-id="1e00f-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="1e00f-164">dördüncü sütun `Description`, `Area` tahmin etmek için kullanılan ikinci `feature`</span><span class="sxs-lookup"><span data-stu-id="1e00f-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="1e00f-165">`IssuePrediction`, model eğitilen bir tahmin için kullanılan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="1e00f-166">Tek bir `string` (`Area`) ve bir `PredictedLabel` `ColumnName` özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="1e00f-167">`PredictedLabel`, tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="1e00f-168">Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="1e00f-169">Tüm ML.NET işlemleri [Mlcontext](xref:Microsoft.ML.MLContext) sınıfında başlar.</span><span class="sxs-lookup"><span data-stu-id="1e00f-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="1e00f-170">`mlContext` başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="1e00f-171">Benzer, kavramsal olarak, `Entity Framework` `DBContext`.</span><span class="sxs-lookup"><span data-stu-id="1e00f-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="1e00f-172">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="1e00f-172">Initialize variables in Main</span></span>

<span data-ttu-id="1e00f-173">Birden çok harekette tekrarlanabilir/belirleyici sonuçlar için rastgele çekirdek (`seed: 0`) ile `_mlContext` genel değişkenini yeni bir `MLContext` örneğiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="1e00f-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="1e00f-174">`Console.WriteLine("Hello World!")` satırını `Main` yönteminde aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="1e00f-175">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="1e00f-175">Load the data</span></span>

<span data-ttu-id="1e00f-176">ML.NET, sayısal veya metin tablolu verileri tanımlamaya yönelik esnek ve verimli bir yöntem olarak [ıdataview sınıfını](xref:Microsoft.ML.IDataView) kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="1e00f-177">`IDataView` metin dosyalarını veya gerçek zamanlı olarak yükleyebilirsiniz (örneğin, SQL veritabanı veya günlük dosyaları).</span><span class="sxs-lookup"><span data-stu-id="1e00f-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="1e00f-178">`_trainingDataView` genel değişkenini, işlem hattı için kullanmak üzere başlatmak ve yüklemek için, `mlContext` başlatmadan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="1e00f-179">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e00f-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="1e00f-180">Veri yolu değişkenlerini alır ve `IDataView` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e00f-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="1e00f-181">`Main` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="1e00f-182">`ProcessData` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="1e00f-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="1e00f-183">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1e00f-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="1e00f-184">İşlem ardışık düzenini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e00f-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="1e00f-185">Aşağıdaki kodu kullanarak, `Main` yönteminden hemen sonra `ProcessData` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="1e00f-186">Özellikleri Ayıkla ve verileri Dönüştür</span><span class="sxs-lookup"><span data-stu-id="1e00f-186">Extract Features and transform the data</span></span>

<span data-ttu-id="1e00f-187">`GitHubIssue`için GitHub etiketini tahmin etmek istediğiniz için [Mapvaluetokey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanarak `Area` sütununu bir sayısal anahtar türü `Label` sütununa (sınıflandırma algoritmaları tarafından kabul edilen bir biçim) dönüştürün ve yeni bir veri kümesi sütunu olarak ekleyin :</span><span class="sxs-lookup"><span data-stu-id="1e00f-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="1e00f-188">Sonra, metin (`Title` ve `Description`) sütunlarını her bir `TitleFeaturized` ve `DescriptionFeaturized` için sayısal bir vektöre dönüştüren `mlContext.Transforms.Text.FeaturizeText` çağırın.</span><span class="sxs-lookup"><span data-stu-id="1e00f-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="1e00f-189">Aşağıdaki kodla, her iki sütun için de işlem hattına bir şekilde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="1e00f-190">Veri hazırlığında son adım, [Birleştir ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) yöntemini kullanarak tüm özellik sütunlarını **Özellikler** sütunuyla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="1e00f-191">Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler.</span><span class="sxs-lookup"><span data-stu-id="1e00f-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="1e00f-192">Aşağıdaki kodla bu dönüşümü işlem hattına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="1e00f-193">Daha sonra, verileri birden çok kez yinelemek için bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> ekleyin. bu nedenle, aşağıdaki kodda olduğu gibi, önbelleği kullanmak daha iyi bir performans alabilir:</span><span class="sxs-lookup"><span data-stu-id="1e00f-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="1e00f-194">Eğitim süresini azaltmak için küçük/orta veri kümeleri için AppendCacheCheckpoint kullanın.</span><span class="sxs-lookup"><span data-stu-id="1e00f-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="1e00f-195">Bunu kullanmayın (kaldırın. Çok büyük veri kümelerini işlerken AppendCacheCheckpoint ()).</span><span class="sxs-lookup"><span data-stu-id="1e00f-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="1e00f-196">`ProcessData` yönteminin sonundaki işlem hattını döndürün.</span><span class="sxs-lookup"><span data-stu-id="1e00f-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="1e00f-197">Bu adım ön işleme/korleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="1e00f-198">ML.NET ' de kullanılabilen ek bileşenleri kullanmak modelinize daha iyi sonuçlar verebilir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="1e00f-199">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="1e00f-199">Build and train the model</span></span>

<span data-ttu-id="1e00f-200">Aşağıdaki çağrıyı, `Main` yönteminde sonraki kod satırı olarak `BuildAndTrainModel`method ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="1e00f-201">`BuildAndTrainModel` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="1e00f-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="1e00f-202">Eğitim algoritması sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="1e00f-203">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="1e00f-203">Trains the model.</span></span>
* <span data-ttu-id="1e00f-204">Eğitim verilerine göre alanı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="1e00f-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="1e00f-205">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e00f-205">Returns the model.</span></span>

<span data-ttu-id="1e00f-206">Aşağıdaki kodu kullanarak, `Main` yönteminden hemen sonra `BuildAndTrainModel` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="1e00f-207">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="1e00f-207">About the classification task</span></span>

<span data-ttu-id="1e00f-208">Sınıflandırma, bir öğe veya veri satırının kategorisini, türünü veya sınıfını **tespit** etmek için verileri kullanan bir makine öğrenimi görevi ve genellikle aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="1e00f-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="1e00f-209">İkili: A veya B.</span><span class="sxs-lookup"><span data-stu-id="1e00f-209">Binary: either A or B.</span></span>
* <span data-ttu-id="1e00f-210">Birden çok sınıf: tek bir model kullanılarak tahmin edilebilir birden fazla kategori.</span><span class="sxs-lookup"><span data-stu-id="1e00f-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="1e00f-211">Bu tür bir sorun için, tek bir Lass sınıflandırma öğrenme algoritması kullanın, çünkü sorun kategorisi tahmininizde yalnızca iki (ikili) yerine birden çok kategori (birden çok Lass) olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="1e00f-212">`BuildAndTrainModel()`' deki ilk kod satırı olarak aşağıdakini ekleyerek, makine öğrenimi algoritmasını veri dönüştürme tanımlarına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

<span data-ttu-id="1e00f-213">[Sdcamaximumentropi](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) , birden çok Lass sınıflandırma eğitim algoritmadır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="1e00f-214">Bu, `pipeline` eklenir ve geçmiş verilerden öğrenme `Title` ve `Description` (`Features`) ve `Label` giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1e00f-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="1e00f-215">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="1e00f-215">Train the model</span></span>

<span data-ttu-id="1e00f-216">Modeli `splitTrainSet` verilerine sığdırın ve `BuildAndTrainModel()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="1e00f-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="1e00f-217">`Fit()`yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi ister.</span><span class="sxs-lookup"><span data-stu-id="1e00f-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="1e00f-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneği üzerinde bir tahmin gerçekleştirmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="1e00f-219">`BuildAndTrainModel()` yönteminin sonraki satırı olarak bunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="1e00f-220">Eğitilen modelle birlikte tahmin edin</span><span class="sxs-lookup"><span data-stu-id="1e00f-220">Predict with the trained model</span></span>

<span data-ttu-id="1e00f-221">Bir `GitHubIssue` örneği oluşturarak eğitilen modelin `Predict` yönteminde tahminini test etmek için bir GitHub sorunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="1e00f-222">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevini kullanın, tek bir veri satırında tahmin yapar:</span><span class="sxs-lookup"><span data-stu-id="1e00f-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="1e00f-223">Modeli kullanma: tahmin sonuçları</span><span class="sxs-lookup"><span data-stu-id="1e00f-223">Using the model: prediction results</span></span>

<span data-ttu-id="1e00f-224">Sonuçları paylaşmak ve bunlara göre işlem yapmak için `GitHubIssue` ve karşılık gelen `Area` etiket tahminini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="1e00f-225">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodunu kullanarak sonuçlar için bir görüntü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="1e00f-226">Değerlendirme için kullanılmak üzere eğitilen modeli döndürün</span><span class="sxs-lookup"><span data-stu-id="1e00f-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="1e00f-227">`BuildAndTrainModel` yönteminin sonundaki modeli döndürün.</span><span class="sxs-lookup"><span data-stu-id="1e00f-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="1e00f-228">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1e00f-228">Evaluate the model</span></span>

<span data-ttu-id="1e00f-229">Modeli oluşturup eğitildiniz, artık kalite güvencesi ve doğrulama için farklı bir veri kümesiyle değerlendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="1e00f-230">`Evaluate` yönteminde, `BuildAndTrainModel` oluşturulan model değerlendirilmek üzere geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="1e00f-231">Aşağıdaki kodda olduğu gibi, `BuildAndTrainModel` hemen sonra `Evaluate` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="1e00f-232">`Evaluate` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="1e00f-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="1e00f-233">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="1e00f-233">Loads the test dataset.</span></span>
* <span data-ttu-id="1e00f-234">Birden çok Lass değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="1e00f-235">Modeli değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="1e00f-236">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1e00f-236">Displays the metrics.</span></span>

<span data-ttu-id="1e00f-237">Aşağıdaki kodu kullanarak, `BuildAndTrainModel` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="1e00f-238">Daha önce eğitim veri kümesiyle yaptığınız gibi, `Evaluate` yöntemine aşağıdaki kodu ekleyerek test veri kümesini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="1e00f-239">[Değerlendir ()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) yöntemi, belirtilen veri kümesini kullanarak model için kalite ölçümlerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1e00f-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="1e00f-240">Birden çok Lass Classification değerlendiricileri tarafından hesaplanan genel ölçümleri içeren bir <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e00f-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="1e00f-241">Modelin kalitesini belirleme ölçümlerini göstermek için önce bunları almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="1e00f-242">Özellikleri girmek ve tahmin getirmeleri için Machine Learning `_trainedModel` genel değişkeninin (bir [ıranseski](xref:Microsoft.ML.ITransformer)) [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yönteminin kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="1e00f-243">Aşağıdaki kodu `Evaluate` yöntemine sonraki satır olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="1e00f-244">Aşağıdaki ölçümler birden çok Lass sınıflandırması için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="1e00f-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="1e00f-245">Mikro doğruluk-her örnek sınıf çifti, doğruluk ölçüsüne eşit olarak katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="1e00f-246">Mikro doğruluk ' ın mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="1e00f-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="1e00f-247">Makro doğruluğu-her sınıf, doğruluk ölçüsüne eşit olarak katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="1e00f-248">Minınlık sınıflarına daha büyük sınıflar olarak eşit ağırlık verilir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="1e00f-249">Makro doğruluğunu mümkün olduğunca yakın bir şekilde tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e00f-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="1e00f-250">Günlük-kayıp- [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="1e00f-251">Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="1e00f-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="1e00f-252">Günlük kaybı azaltma-[-inf, 1,00] aralığından, 1,00 ' nin kusursuz tahminlerden ve 0 ' ın, ortalama tahmine dayalı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="1e00f-253">Günlük kaybını azaltmanın mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="1e00f-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="1e00f-254">Model doğrulama ölçümlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1e00f-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="1e00f-255">Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1e00f-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="1e00f-256">Modeli bir dosyaya kaydet</span><span class="sxs-lookup"><span data-stu-id="1e00f-256">Save the model to a file</span></span>

<span data-ttu-id="1e00f-257">Modelinize her memnun olduktan sonra, daha sonra veya başka bir uygulamada tahmine dayalı hale getirmek için dosyayı bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="1e00f-258">`Evaluate` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="1e00f-259">`Evaluate` yönteminizin altında `SaveModelAsFile` yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1e00f-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="1e00f-260">Aşağıdaki kodu `SaveModelAsFile` yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="1e00f-261">Bu kod, eğitilen modeli seri hale getirmek ve bir ZIP dosyası olarak depolamak için [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="1e00f-262">Bir modelle dağıtım ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="1e00f-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="1e00f-263">Aşağıdaki kodu kullanarak, `Evaluate` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="1e00f-264">Aşağıdaki kodu kullanarak, `Evaluate` yönteminden hemen sonra (ve `SaveModelAsFile` yönteminden hemen önce) `PredictIssue` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="1e00f-265">`PredictIssue` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="1e00f-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="1e00f-266">Kaydedilen modeli yükler</span><span class="sxs-lookup"><span data-stu-id="1e00f-266">Loads the saved model</span></span>
* <span data-ttu-id="1e00f-267">Test verileri için tek bir sorun oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e00f-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="1e00f-268">Test verilerine göre alanı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="1e00f-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="1e00f-269">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="1e00f-270">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1e00f-270">Displays the predicted results.</span></span>

<span data-ttu-id="1e00f-271">`PredictIssue` yöntemine aşağıdaki kodu ekleyerek kayıtlı modeli uygulamanıza yükleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetLoadModel)]

<span data-ttu-id="1e00f-272">Bir `GitHubIssue` örneği oluşturarak eğitilen modelin `Predict` yönteminde tahminini test etmek için bir GitHub sorunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1e00f-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

<span data-ttu-id="1e00f-273">Daha önce yaptığınız gibi, aşağıdaki kodla bir `PredictionEngine` örneği oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="1e00f-274">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="1e00f-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="1e00f-276">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="1e00f-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="1e00f-277">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1e00f-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="1e00f-278">[ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın</span><span class="sxs-lookup"><span data-stu-id="1e00f-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="1e00f-279">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="1e00f-280">Aşağıdaki kodu tahmin için `PredictIssue` yöntemine ekleyerek GitHub etiketini tahmin etmek için `PredictionEngine` kullanın:</span><span class="sxs-lookup"><span data-stu-id="1e00f-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="1e00f-281">Yüklü modeli tahmin için kullanma</span><span class="sxs-lookup"><span data-stu-id="1e00f-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="1e00f-282">Sorunu kategorilere ayırarak ve buna uygun şekilde hareket edebilmek için `Area` görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="1e00f-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="1e00f-283">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodunu kullanarak sonuçlar için bir görüntü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e00f-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="1e00f-284">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="1e00f-284">Results</span></span>

<span data-ttu-id="1e00f-285">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-285">Your results should be similar to the following.</span></span> <span data-ttu-id="1e00f-286">İşlem hattı sırasında iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1e00f-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="1e00f-287">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e00f-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="1e00f-288">Bu iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1e00f-288">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="1e00f-289">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="1e00f-289">Congratulations!</span></span> <span data-ttu-id="1e00f-290">Artık bir GitHub sorunu için bir alan etiketini sınıflandırmak ve tahmin etmek üzere bir makine öğrenimi modeli oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="1e00f-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="1e00f-291">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e00f-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1e00f-292">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1e00f-292">Next steps</span></span>

<span data-ttu-id="1e00f-293">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="1e00f-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="1e00f-294">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="1e00f-294">Prepare your data</span></span>
> * <span data-ttu-id="1e00f-295">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1e00f-295">Transform the data</span></span>
> * <span data-ttu-id="1e00f-296">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="1e00f-296">Train the model</span></span>
> * <span data-ttu-id="1e00f-297">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1e00f-297">Evaluate the model</span></span>
> * <span data-ttu-id="1e00f-298">Eğitilen modelle birlikte tahmin edin</span><span class="sxs-lookup"><span data-stu-id="1e00f-298">Predict with the trained model</span></span>
> * <span data-ttu-id="1e00f-299">Yüklü bir modelle dağıtım ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="1e00f-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="1e00f-300">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="1e00f-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="1e00f-301">Taxı tarifeli havayolu Predictor</span><span class="sxs-lookup"><span data-stu-id="1e00f-301">Taxi Fare Predictor</span></span>](taxi-fare.md)
