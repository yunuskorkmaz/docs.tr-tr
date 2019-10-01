---
title: 'Öğretici: destek sorunlarını kategorilere ayırma-birden çok Lass sınıflandırması'
description: Birden çok Lass sınıflandırma senaryosunda ML.NET kullanarak bunları belirli bir alana atamaya yönelik GitHub sorunlarını sınıflandırın.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: a6d158d51e6775feaed669c678bb9a36984f08f3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698982"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a><span data-ttu-id="f7711-103">Öğretici: ML .NET ile birden çok Lass sınıflandırması kullanarak destek sorunlarını kategorilere ayırma</span><span class="sxs-lookup"><span data-stu-id="f7711-103">Tutorial: Categorize support issues using multiclass classification with ML .NET</span></span>

<span data-ttu-id="f7711-104">Bu örnek öğreticide, Visual Studio 'da kullanılan C# bir .NET Core konsol uygulaması aracılığıyla bir GitHub sorununun alan etiketini sınıflandırdığı ve tahmin eden bir modeli eğiten bir GitHub sorunu Sınıflandırıcısı oluşturmak için ml.NET kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f7711-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="f7711-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="f7711-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f7711-106">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="f7711-106">Prepare your data</span></span>
> * <span data-ttu-id="f7711-107">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f7711-107">Transform the data</span></span>
> * <span data-ttu-id="f7711-108">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f7711-108">Train the model</span></span>
> * <span data-ttu-id="f7711-109">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f7711-109">Evaluate the model</span></span>
> * <span data-ttu-id="f7711-110">Eğitilen modelle birlikte tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f7711-110">Predict with the trained model</span></span>
> * <span data-ttu-id="f7711-111">Yüklü bir modelle dağıtım ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="f7711-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="f7711-112">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7711-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7711-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f7711-113">Prerequisites</span></span>

* <span data-ttu-id="f7711-114">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="f7711-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="f7711-115">[GitHub sorunları sekmeyle ayrılmış dosya (issues_train. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="f7711-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="f7711-116">[GitHub, test sekmeyle ayrılmış dosyası (issues_test. TSV) ile karşılaşır](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="f7711-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f7711-117">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7711-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="f7711-118">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7711-118">Create a project</span></span>

1. <span data-ttu-id="f7711-119">Visual Studio 2017 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="f7711-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="f7711-120">Menü çubuğundan **dosya** > **Yeni** > **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="f7711-121">**Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="f7711-122">Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="f7711-123">**Ad** metin kutusuna "Githubıssueclassıflıve" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="f7711-124">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="f7711-125">**Çözüm Gezgini**, projenize sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="f7711-126">"Data" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f7711-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="f7711-127">Modelinize kaydetmek için projenizde *modeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="f7711-128">**Çözüm Gezgini**, projenize sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="f7711-129">"Modeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f7711-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="f7711-130">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="f7711-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f7711-131">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f7711-132">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden **v 1.0.0** paketini seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v 1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="f7711-133">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="f7711-134">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="f7711-134">Prepare your data</span></span>

1. <span data-ttu-id="f7711-135">[İssues_train. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri kümelerini indirin ve daha önce oluşturulan *veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f7711-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="f7711-136">Makine öğrenimi modelini ve ikincisini gösteren ilk veri kümesi, modelinizin ne kadar doğru olduğunu değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7711-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="f7711-137">Çözüm Gezgini, @no__t -0. tsv dosyalarının her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="f7711-138">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f7711-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f7711-139">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="f7711-139">Create classes and define paths</span></span>

<span data-ttu-id="f7711-140">*Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="f7711-141">Son indirilen dosyaları ve `MLContext`, `DataView` ve `PredictionEngine` için genel değişkenleri tutmak üzere üç genel alan oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="f7711-142">`_trainDataPath`, modeli eğitmek için kullanılan veri kümesinin yoluna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7711-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="f7711-143">`_testDataPath` ' ın, modeli değerlendirmek için kullanılan veri kümesinin yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="f7711-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="f7711-144">`_modelPath`, eğitilen modelin kaydedildiği yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="f7711-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="f7711-145">`_mlContext`, işleme bağlamı sağlayan <xref:Microsoft.ML.MLContext> ' dir.</span><span class="sxs-lookup"><span data-stu-id="f7711-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="f7711-146">`_trainingDataView`, eğitim veri kümesini işlemek için kullanılan <xref:Microsoft.ML.IDataView> ' dir.</span><span class="sxs-lookup"><span data-stu-id="f7711-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="f7711-147">`_predEngine`, tek tahmin için kullanılan <xref:Microsoft.ML.PredictionEngine%602> ' dir.</span><span class="sxs-lookup"><span data-stu-id="f7711-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="f7711-148">Aşağıdaki kodu, bu yolları ve diğer değişkenleri belirtmek için `Main` yönteminin üstüne doğru satıra ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="f7711-149">Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f7711-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="f7711-150">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="f7711-151">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="f7711-152">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *GitHubIssueData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f7711-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="f7711-153">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f7711-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="f7711-154">*GitHubIssueData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="f7711-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="f7711-155">Aşağıdaki `using` ifadesini *GitHubIssueData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="f7711-156">Mevcut sınıf tanımını kaldırın ve *GitHubIssueData.cs* dosyasına `GitHubIssue` ve `IssuePrediction` olmak üzere iki sınıfa sahip aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="f7711-157">@No__t-0, tahmin etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="f7711-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="f7711-158">Tanımlanan `Features`, modele, etiketi tahmin etmek için verdiğiniz girişlerdir.</span><span class="sxs-lookup"><span data-stu-id="f7711-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="f7711-159">Veri kümesindeki kaynak sütunlarının dizinlerini belirtmek için [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7711-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="f7711-160">`GitHubIssue`, giriş veri kümesi sınıfıdır ve aşağıdaki <xref:System.String> alanlarına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f7711-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="f7711-161">ilk sütun `ID` (GitHub sorun KIMLIĞI)</span><span class="sxs-lookup"><span data-stu-id="f7711-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="f7711-162">ikinci sütun `Area` (eğitim tahmini)</span><span class="sxs-lookup"><span data-stu-id="f7711-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="f7711-163">üçüncü sütun `Title` (GitHub sorun başlığı) `Area` ' i tahmin etmek için kullanılan ilk `feature` ' dir</span><span class="sxs-lookup"><span data-stu-id="f7711-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="f7711-164">`Description` dördüncü sütun, `Area` ' i tahmin etmek için kullanılan ikinci `feature` ' dir</span><span class="sxs-lookup"><span data-stu-id="f7711-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="f7711-165">`IssuePrediction`, model eğitilen bir tahmin için kullanılan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="f7711-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="f7711-166">Tek bir `string` (`Area`) ve `PredictedLabel` `ColumnName` özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="f7711-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="f7711-167">@No__t-0, tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7711-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="f7711-168">Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7711-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="f7711-169">Tüm ML.NET işlemleri [Mlcontext](xref:Microsoft.ML.MLContext) sınıfında başlar.</span><span class="sxs-lookup"><span data-stu-id="f7711-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="f7711-170">@No__t başlatılıyor-0, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7711-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f7711-171">@No__t, kavramsal olarak, `Entity Framework` ' de 0 ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="f7711-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="f7711-172">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="f7711-172">Initialize variables in Main</span></span>

<span data-ttu-id="f7711-173">Birden çok harekette tekrarlanabilir/belirleyici sonuçlar için rastgele bir çekirdek (`seed: 0`) ile `_mlContext` genel değişkenini yeni bir `MLContext` örneğiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="f7711-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="f7711-174">@No__t-0 satırını `Main` yönteminde aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f7711-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="f7711-175">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f7711-175">Load the data</span></span>

<span data-ttu-id="f7711-176">ML.NET, sayısal veya metin tablolu verileri tanımlamaya yönelik esnek ve verimli bir yöntem olarak [ıdataview sınıfını](xref:Microsoft.ML.IDataView) kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7711-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="f7711-177">`IDataView`, metin dosyalarını veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f7711-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="f7711-178">@No__t-0 genel değişkenini, işlem hattı için kullanmak üzere başlatmak ve yüklemek için, `mlContext` başlatılmasından sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="f7711-179">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7711-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="f7711-180">Veri yolu değişkenlerini alır ve `IDataView` döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7711-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="f7711-181">@No__t-0 yöntemine sonraki kod satırı olarak aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="f7711-182">@No__t-0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f7711-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="f7711-183">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f7711-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="f7711-184">İşlem ardışık düzenini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7711-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="f7711-185">Aşağıdaki kodu kullanarak, `Main` yönteminden hemen sonra `ProcessData` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="f7711-186">Özellikleri Ayıkla ve verileri Dönüştür</span><span class="sxs-lookup"><span data-stu-id="f7711-186">Extract Features and transform the data</span></span>

<span data-ttu-id="f7711-187">Bir @no__t için GitHub etiketini tahmin etmek istediğinizde, `Area` sütununu `Label` sütununa (sınıflandırma algoritmalarının tarafından kabul edilen bir biçimde) dönüştürmek ve yeni bir veri kümesi sütunu olarak eklemek için [Mapvaluetokey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanın:</span><span class="sxs-lookup"><span data-stu-id="f7711-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="f7711-188">Sonra, metin (`Title` ve `Description`) sütunlarını `TitleFeaturized` ve `DescriptionFeaturized` olarak adlandırılan her bir sayısal vector öğesine dönüştüren `mlContext.Transforms.Text.FeaturizeText` ' ı çağırın.</span><span class="sxs-lookup"><span data-stu-id="f7711-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="f7711-189">Aşağıdaki kodla, her iki sütun için de işlem hattına bir şekilde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="f7711-190">Veri hazırlığında son adım, [Birleştir ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) yöntemini kullanarak tüm özellik sütunlarını **Özellikler** sütunuyla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f7711-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="f7711-191">Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler.</span><span class="sxs-lookup"><span data-stu-id="f7711-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="f7711-192">Aşağıdaki kodla bu dönüşümü işlem hattına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="f7711-193">Daha sonra, verileri birden çok kez yinelemek için bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> ' ı, aşağıdaki kodda olduğu gibi daha iyi bir performans alabilir:</span><span class="sxs-lookup"><span data-stu-id="f7711-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="f7711-194">Eğitim süresini azaltmak için küçük/orta veri kümeleri için AppendCacheCheckpoint kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7711-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="f7711-195">Bunu kullanmayın (kaldırın. Çok büyük veri kümelerini işlerken AppendCacheCheckpoint ()).</span><span class="sxs-lookup"><span data-stu-id="f7711-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="f7711-196">@No__t-0 yönteminin sonundaki işlem hattını döndürün.</span><span class="sxs-lookup"><span data-stu-id="f7711-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="f7711-197">Bu adım ön işleme/korleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f7711-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="f7711-198">ML.NET ' de kullanılabilen ek bileşenleri kullanmak modelinize daha iyi sonuçlar verebilir.</span><span class="sxs-lookup"><span data-stu-id="f7711-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="f7711-199">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="f7711-199">Build and train the model</span></span>

<span data-ttu-id="f7711-200">@No__t-0yöntemine `Main` yönteminde sonraki kod satırı olarak aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="f7711-201">@No__t-0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f7711-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="f7711-202">Eğitim algoritması sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7711-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="f7711-203">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="f7711-203">Trains the model.</span></span>
* <span data-ttu-id="f7711-204">Eğitim verilerine göre alanı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="f7711-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="f7711-205">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7711-205">Returns the model.</span></span>

<span data-ttu-id="f7711-206">Aşağıdaki kodu kullanarak, `Main` yönteminden hemen sonra `BuildAndTrainModel` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="f7711-207">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="f7711-207">About the classification task</span></span>

<span data-ttu-id="f7711-208">Sınıflandırma, bir öğe veya veri satırının kategorisini, türünü veya sınıfını **tespit** etmek için verileri kullanan bir makine öğrenimi görevi ve genellikle aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="f7711-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="f7711-209">İkili: A veya B.</span><span class="sxs-lookup"><span data-stu-id="f7711-209">Binary: either A or B.</span></span>
* <span data-ttu-id="f7711-210">Birden çok sınıf: tek bir model kullanılarak tahmin edilebilir birden fazla kategori.</span><span class="sxs-lookup"><span data-stu-id="f7711-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="f7711-211">Bu tür bir sorun için, tek bir Lass sınıflandırma öğrenme algoritması kullanın, çünkü sorun kategorisi tahmininizde yalnızca iki (ikili) yerine birden çok kategori (birden çok Lass) olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7711-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="f7711-212">@No__t-0 ' daki ilk kod satırı olarak aşağıdakini ekleyerek makine öğrenimi algoritmasını veri dönüştürme tanımlarına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

<span data-ttu-id="f7711-213">[Sdcamaximumentropi](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) , birden çok Lass sınıflandırma eğitim algoritmadır.</span><span class="sxs-lookup"><span data-stu-id="f7711-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="f7711-214">Bu `pipeline` ' a eklenir ve geçmiş verilerden öğrenme `Title` ve `Description` (`Features`) ve `Label` giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f7711-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="f7711-215">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f7711-215">Train the model</span></span>

<span data-ttu-id="f7711-216">Modeli `splitTrainSet` verilerine sığdırın ve `BuildAndTrainModel()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="f7711-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="f7711-217">@No__t-0yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi ister.</span><span class="sxs-lookup"><span data-stu-id="f7711-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="f7711-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneği üzerinde bir tahmin gerçekleştirmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="f7711-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="f7711-219">Bunu `BuildAndTrainModel()` yönteminde bir sonraki satır olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="f7711-220">Eğitilen modelle birlikte tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f7711-220">Predict with the trained model</span></span>

<span data-ttu-id="f7711-221">@No__t-1 ' in bir örneğini oluşturarak eğitilen modelin tahminini `Predict` yönteminde test etmek için bir GitHub sorunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="f7711-222">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevini kullanın, tek bir veri satırında tahmin yapar:</span><span class="sxs-lookup"><span data-stu-id="f7711-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="f7711-223">Modeli kullanma: tahmin sonuçları</span><span class="sxs-lookup"><span data-stu-id="f7711-223">Using the model: prediction results</span></span>

<span data-ttu-id="f7711-224">Sonuçları paylaşmak ve bunlara göre işlem yapmak için `GitHubIssue` ve karşılık gelen `Area` etiket tahminini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f7711-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="f7711-225">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodunu kullanarak sonuçlar için bir görüntü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="f7711-226">Değerlendirme için kullanılmak üzere eğitilen modeli döndürün</span><span class="sxs-lookup"><span data-stu-id="f7711-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="f7711-227">@No__t-0 yönteminin sonundaki modeli döndürün.</span><span class="sxs-lookup"><span data-stu-id="f7711-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="f7711-228">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f7711-228">Evaluate the model</span></span>

<span data-ttu-id="f7711-229">Modeli oluşturup eğitildiniz, artık kalite güvencesi ve doğrulama için farklı bir veri kümesiyle değerlendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7711-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="f7711-230">@No__t-0 yönteminde, `BuildAndTrainModel` ' de oluşturulan model değerlendirilmek üzere geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f7711-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="f7711-231">Aşağıdaki kodda olduğu gibi `Evaluate` yöntemini `BuildAndTrainModel` ' den sonra oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="f7711-232">@No__t-0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f7711-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="f7711-233">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="f7711-233">Loads the test dataset.</span></span>
* <span data-ttu-id="f7711-234">Birden çok Lass değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7711-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="f7711-235">Modeli değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7711-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="f7711-236">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f7711-236">Displays the metrics.</span></span>

<span data-ttu-id="f7711-237">Aşağıdaki kodu kullanarak, `Main` yönteminden yeni yönteme bir çağrı ekleyin, `BuildAndTrainModel` yöntem çağrısının altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="f7711-238">Daha önce eğitim veri kümesiyle yaptığınız gibi, `Evaluate` yöntemine aşağıdaki kodu ekleyerek test veri kümesini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="f7711-239">[Değerlendir ()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) yöntemi, belirtilen veri kümesini kullanarak model için kalite ölçümlerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f7711-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="f7711-240">Birden çok Lass Classification değerlendiricileri tarafından hesaplanan genel ölçümleri içeren <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7711-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="f7711-241">Modelin kalitesini belirleme ölçümlerini göstermek için önce bunları almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7711-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="f7711-242">Özellikleri girmek ve tahminleri döndürmek için Machine Learning `_trainedModel` genel değişkeninin (bir [ıranseski](xref:Microsoft.ML.ITransformer)) [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yönteminin kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7711-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="f7711-243">Aşağıdaki kodu `Evaluate` yöntemine sonraki satır olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="f7711-244">Aşağıdaki ölçümler birden çok Lass sınıflandırması için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="f7711-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="f7711-245">Mikro doğruluk-her örnek sınıf çifti, doğruluk ölçüsüne eşit olarak katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="f7711-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="f7711-246">Mikro doğruluk ' ın olabildiğince 1 ' e yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f7711-246">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="f7711-247">Makro doğruluğu-her sınıf, doğruluk ölçüsüne eşit olarak katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="f7711-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="f7711-248">Minınlık sınıflarına daha büyük sınıflar olarak eşit ağırlık verilir.</span><span class="sxs-lookup"><span data-stu-id="f7711-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="f7711-249">Makro doğruluğunu mümkün olduğunca 1 ' e yakın olacak şekilde istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f7711-249">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="f7711-250">Günlük-kayıp- [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f7711-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="f7711-251">Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f7711-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="f7711-252">Günlük kaybı azaltma-[-inf, 100] aralığından, 100 ' nin kusursuz tahminlerden ve 0 ' ın, ortalama tahmine dayalı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7711-252">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="f7711-253">Günlük kaybını azaltmanın mümkün olduğunca sıfıra yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f7711-253">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="f7711-254">Model doğrulama ölçümlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f7711-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="f7711-255">Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f7711-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="f7711-256">Modeli bir dosyaya kaydet</span><span class="sxs-lookup"><span data-stu-id="f7711-256">Save the model to a file</span></span>

<span data-ttu-id="f7711-257">Modelinize her memnun olduktan sonra, daha sonra veya başka bir uygulamada tahmine dayalı hale getirmek için dosyayı bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f7711-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="f7711-258">@No__t-0 yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7711-258">Add the following code to the `Evaluate` method.</span></span> 

[!code-csharp[SnippetCallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="f7711-259">@No__t-1 yönteminizin altında `SaveModelAsFile` yöntemini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f7711-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="f7711-260">@No__t-0 yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7711-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="f7711-261">Bu kod, eğitilen modeli seri hale getirmek ve bir ZIP dosyası olarak depolamak için [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7711-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="f7711-262">Bir modelle dağıtım ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="f7711-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="f7711-263">Aşağıdaki kodu kullanarak, `Main` yönteminden yeni yönteme bir çağrı ekleyin, `Evaluate` yöntem çağrısının altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="f7711-264">Aşağıdaki kodu kullanarak, `Evaluate` yönteminden hemen sonra (ve `SaveModelAsFile` yönteminden önce) `PredictIssue` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="f7711-265">@No__t-0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f7711-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="f7711-266">Kaydedilen modeli yükler</span><span class="sxs-lookup"><span data-stu-id="f7711-266">Loads the saved model</span></span>
* <span data-ttu-id="f7711-267">Test verileri için tek bir sorun oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7711-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="f7711-268">Test verilerine göre alanı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="f7711-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="f7711-269">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f7711-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="f7711-270">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f7711-270">Displays the predicted results.</span></span>

<span data-ttu-id="f7711-271">@No__t-0 yöntemine aşağıdaki kodu ekleyerek kayıtlı modeli uygulamanıza yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetLoadModel)]

<span data-ttu-id="f7711-272">@No__t-1 ' in bir örneğini oluşturarak eğitilen modelin tahminini `Predict` yönteminde test etmek için bir GitHub sorunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7711-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

<span data-ttu-id="f7711-273">Daha önce yaptığınız gibi, aşağıdaki kodla bir `PredictionEngine` örneği oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="f7711-274">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="f7711-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="f7711-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="f7711-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="f7711-276">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="f7711-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="f7711-277">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7711-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="f7711-278">[ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın</span><span class="sxs-lookup"><span data-stu-id="f7711-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="f7711-279">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="f7711-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="f7711-280">Tahmine yönelik `PredictIssue` yöntemine aşağıdaki kodu ekleyerek alan GitHub etiketini tahmin etmek için `PredictionEngine` kullanın:</span><span class="sxs-lookup"><span data-stu-id="f7711-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="f7711-281">Yüklü modeli tahmin için kullanma</span><span class="sxs-lookup"><span data-stu-id="f7711-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="f7711-282">Sorunu kategorilere ayırarak ve buna uygun şekilde hareket edebilmek için `Area` ' yı görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f7711-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="f7711-283">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodunu kullanarak sonuçlar için bir görüntü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f7711-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="f7711-284">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="f7711-284">Results</span></span>

<span data-ttu-id="f7711-285">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7711-285">Your results should be similar to the following.</span></span> <span data-ttu-id="f7711-286">İşlem hattı sırasında iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f7711-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="f7711-287">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7711-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="f7711-288">Bu iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f7711-288">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="f7711-289">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="f7711-289">Congratulations!</span></span> <span data-ttu-id="f7711-290">Artık bir GitHub sorunu için bir alan etiketini sınıflandırmak ve tahmin etmek üzere bir makine öğrenimi modeli oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="f7711-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="f7711-291">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7711-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f7711-292">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f7711-292">Next steps</span></span>

<span data-ttu-id="f7711-293">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="f7711-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f7711-294">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="f7711-294">Prepare your data</span></span>
> * <span data-ttu-id="f7711-295">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f7711-295">Transform the data</span></span>
> * <span data-ttu-id="f7711-296">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f7711-296">Train the model</span></span>
> * <span data-ttu-id="f7711-297">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f7711-297">Evaluate the model</span></span>
> * <span data-ttu-id="f7711-298">Eğitilen modelle birlikte tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f7711-298">Predict with the trained model</span></span>
> * <span data-ttu-id="f7711-299">Yüklü bir modelle dağıtım ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="f7711-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="f7711-300">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="f7711-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f7711-301">Taxı tarifeli havayolu Predictor</span><span class="sxs-lookup"><span data-stu-id="f7711-301">Taxi Fare Predictor</span></span>](taxi-fare.md)
