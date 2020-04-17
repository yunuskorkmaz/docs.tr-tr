---
title: 'Öğretici: Destek sorunlarını kategorilere ayırın - çok sınıflı sınıflandırma'
description: ML.NET,ML.NET belirli bir alana atamak üzere GitHub sorunlarını sınıflandırmak için çok sınıflı bir sınıflandırma senaryosunda nasıl kullanacağını keşfedin.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: fc0e935a36c52627903dac2a7b29d6f534695ea0
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608068"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a><span data-ttu-id="2bfab-103">Öğretici: ML.NET ile çok sınıflı sınıflandırma kullanarak destek sorunlarını kategorilere ayırın</span><span class="sxs-lookup"><span data-stu-id="2bfab-103">Tutorial: Categorize support issues using multiclass classification with ML.NET</span></span>

<span data-ttu-id="2bfab-104">Bu örnek öğretici, Visual Studio'da C# kullanarak bir .NET Core konsol uygulaması aracılığıyla GitHub sorunu için Alan etiketini sınıflandıran ve tahmin eden bir modeli eğitmek için bir GitHub sorun sınıflandırıcısı oluşturmak için ML.NET kullanılmasını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="2bfab-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="2bfab-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2bfab-106">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="2bfab-106">Prepare your data</span></span>
> * <span data-ttu-id="2bfab-107">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2bfab-107">Transform the data</span></span>
> * <span data-ttu-id="2bfab-108">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2bfab-108">Train the model</span></span>
> * <span data-ttu-id="2bfab-109">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="2bfab-109">Evaluate the model</span></span>
> * <span data-ttu-id="2bfab-110">Eğitimli model ile tahmin edin</span><span class="sxs-lookup"><span data-stu-id="2bfab-110">Predict with the trained model</span></span>
> * <span data-ttu-id="2bfab-111">Yüklü bir modelle Dağıtma ve Tahmin Etme</span><span class="sxs-lookup"><span data-stu-id="2bfab-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="2bfab-112">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bfab-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2bfab-113">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="2bfab-113">Prerequisites</span></span>

* <span data-ttu-id="2bfab-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonrası veya Visual Studio 2017 sürümü 15.6 veya daha sonra ".NET Core çapraz platform geliştirme" iş yükü yüklü.</span><span class="sxs-lookup"><span data-stu-id="2bfab-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* <span data-ttu-id="2bfab-115">[Github sorunları sekmesi ayrılmış dosya (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="2bfab-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="2bfab-116">[Github sorunları test sekmesi ayrılmış dosya (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="2bfab-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2bfab-117">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bfab-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="2bfab-118">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bfab-118">Create a project</span></span>

1. <span data-ttu-id="2bfab-119">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="2bfab-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="2bfab-120">Menü çubuğundan**Yeni** > **Proje** **Dosyası'nı** > seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="2bfab-121">Yeni **Proje** iletişim kutusunda, **.NET Core** düğümünü izleyen **Visual C#** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="2bfab-122">Ardından **Konsol Uygulaması (.NET Core)** proje şablonu'nu seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="2bfab-123">**Ad** metin kutusunda "GitHubIssueClassification" yazın ve **ardından Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="2bfab-124">Veri seti dosyalarınızı kaydetmek için projenizde *Veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="2bfab-125">**Çözüm Gezgini'nde,** projenize sağ tıklayın ve**Yeni Klasör** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="2bfab-126">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2bfab-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="2bfab-127">Modelinizi kaydetmek için projenizde *Modeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="2bfab-128">**Çözüm Gezgini'nde,** projenize sağ tıklayın ve**Yeni Klasör** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="2bfab-129">"Modeller" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2bfab-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="2bfab-130">Microsoft.ML **NuGet Paketini**Yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="2bfab-131">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2bfab-132">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML** arayın ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="2bfab-133">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="2bfab-134">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="2bfab-134">Prepare your data</span></span>

1. <span data-ttu-id="2bfab-135">[issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri kümelerini indirin ve bunları daha önce oluşturulmuş *Veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="2bfab-136">İlk veri seti makine öğrenme modelini eğitir ve ikincisi modelinizin ne kadar doğru olduğunu değerlendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="2bfab-137">Çözüm Gezgini'nde \*,tsv dosyalarının her birini sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="2bfab-138">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="2bfab-139">Sınıflar oluşturma ve yolları tanımlama</span><span class="sxs-lookup"><span data-stu-id="2bfab-139">Create classes and define paths</span></span>

<span data-ttu-id="2bfab-140">Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

<span data-ttu-id="2bfab-141">En son indirilen dosyalara giden yolları tutmak için üç genel `MLContext`alan`DataView`ve `PredictionEngine`aşağıdakiler için genel değişkenler oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="2bfab-142">`_trainDataPath`modeli eğitmek için kullanılan veri kümesine giden yola sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="2bfab-143">`_testDataPath`modeli değerlendirmek için kullanılan veri kümesine giden yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="2bfab-144">`_modelPath`eğitilmiş modelin kaydedildiği yola sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="2bfab-145">`_mlContext`işleme <xref:Microsoft.ML.MLContext> bağlamını sağlayan dır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="2bfab-146">`_trainingDataView`eğitim <xref:Microsoft.ML.IDataView> veri kümesini işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="2bfab-147">`_predEngine`tek <xref:Microsoft.ML.PredictionEngine%602> tahminler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="2bfab-148">Bu yolları ve diğer değişkenleri `Main` belirtmek için yöntemin hemen üstündeki satıra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="2bfab-149">Giriş verileriniz ve öngörüleriniz için bazı sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2bfab-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="2bfab-150">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="2bfab-151">**Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="2bfab-152">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *GitHubIssueData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="2bfab-153">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="2bfab-154">kod düzenleyicisinde *GitHubIssueData.cs* dosya açılır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="2bfab-155">GitHubIssueData.cs üstüne `using` aşağıdaki ifadeyi *GitHubIssueData.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="2bfab-156">Varolan sınıf tanımını kaldırın ve iki sınıfı `GitHubIssue` `IssuePrediction`ve *GitHubIssueData.cs* dosyasına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="2bfab-157">Tahmin `label` etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="2bfab-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="2bfab-158">Tanımlanan, `Features` Etiketi tahmin etmek için modele verdiğiniz girdilerdir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="2bfab-159">Veri kümesindeki kaynak sütunların dizinlerini belirtmek için [LoadColumnAtöz'ü](xref:Microsoft.ML.Data.LoadColumnAttribute) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bfab-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="2bfab-160">`GitHubIssue`giriş veri kümesi sınıfıdır ve <xref:System.String> aşağıdaki alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2bfab-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="2bfab-161">ilk sütun `ID` (GitHub Sorun Kimliği)</span><span class="sxs-lookup"><span data-stu-id="2bfab-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="2bfab-162">ikinci sütun `Area` (eğitim için tahmin)</span><span class="sxs-lookup"><span data-stu-id="2bfab-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="2bfab-163">üçüncü sütun `Title` (GitHub sorun başlığı) `feature` ilk tahmin etmek için kullanılan`Area`</span><span class="sxs-lookup"><span data-stu-id="2bfab-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="2bfab-164">dördüncü sütun, `Description` `feature``Area`</span><span class="sxs-lookup"><span data-stu-id="2bfab-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="2bfab-165">`IssuePrediction`model eğitildikten sonra tahmin için kullanılan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="2bfab-166">Tek `string` bir (`Area`) `PredictedLabel` `ColumnName` ve bir özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="2bfab-167">Tahmin `PredictedLabel` ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="2bfab-168">Değerlendirme için, eğitim verileri, öngörülen değerler ve model ile bir giriş kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="2bfab-169">Tüm ML.NET işlemleri [MLContext](xref:Microsoft.ML.MLContext) sınıfında başlar.</span><span class="sxs-lookup"><span data-stu-id="2bfab-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="2bfab-170">İlk `mlContext` başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bfab-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2bfab-171">Kavramsal olarak `DBContext` `Entity Framework`benzer.</span><span class="sxs-lookup"><span data-stu-id="2bfab-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="2bfab-172">Main'deki değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="2bfab-172">Initialize variables in Main</span></span>

<span data-ttu-id="2bfab-173">`_mlContext` Birden çok eğitim arasında tekrarlanabilir/deterministik sonuçlar için rasgele bir tohum () `MLContext` `seed: 0`ile yeni bir örnek ile küresel değişkeni başlangıç.</span><span class="sxs-lookup"><span data-stu-id="2bfab-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="2bfab-174">`Console.WriteLine("Hello World!")` Satırı yöntemde aşağıdaki kodla `Main` değiştirin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="2bfab-175">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="2bfab-175">Load the data</span></span>

<span data-ttu-id="2bfab-176">ML.NET, sayısal veya metin tabular verileri açıklamanın esnek ve verimli bir yolu olarak [IDataView sınıfını](xref:Microsoft.ML.IDataView) kullanır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="2bfab-177">`IDataView`metin dosyalarını veya gerçek zamanlı olarak yükleyebilir (örneğin, SQL veritabanı veya günlük dosyaları).</span><span class="sxs-lookup"><span data-stu-id="2bfab-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="2bfab-178">Ardışık `_trainingDataView` düzen için kullanmak için global değişkeni başlatmave yüklemek için, `mlContext` başlatmadan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

<span data-ttu-id="2bfab-179">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyada okur.</span><span class="sxs-lookup"><span data-stu-id="2bfab-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="2bfab-180">Veri yolu değişkenlerini alır ve `IDataView`bir .</span><span class="sxs-lookup"><span data-stu-id="2bfab-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="2bfab-181">`Main` Yöntemde bir sonraki kod satırı olarak aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

<span data-ttu-id="2bfab-182">Yöntem `ProcessData` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="2bfab-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="2bfab-183">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2bfab-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="2bfab-184">İşleme ardışık hattını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2bfab-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="2bfab-185">Yöntemden `ProcessData` `Main` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="2bfab-186">Özellikleri Ayıklayın ve verileri dönüştürün</span><span class="sxs-lookup"><span data-stu-id="2bfab-186">Extract Features and transform the data</span></span>

<span data-ttu-id="2bfab-187">Bir için Alan GitHub etiketini `GitHubIssue`tahmin etmek istediğinizde, `Area` sütunu sayısal anahtar türü `Label` sütununa (sınıflandırma algoritmaları tarafından kabul edilen bir biçim) dönüştürmek ve yeni bir veri kümesi sütunu olarak eklemek için [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanın:</span><span class="sxs-lookup"><span data-stu-id="2bfab-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

<span data-ttu-id="2bfab-188">Ardından, `mlContext.Transforms.Text.FeaturizeText` metin (`Title` ve `Description`) sütunlarını çağrılan `TitleFeaturized` her biri için `DescriptionFeaturized`sayısal bir vektöre dönüştüren çağrı ve .</span><span class="sxs-lookup"><span data-stu-id="2bfab-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="2bfab-189">Her iki sütun için de aşağıdaki kodla ardışık ardışıklaştırmayı tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="2bfab-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

<span data-ttu-id="2bfab-190">Veri hazırlamadaki son adım, Tüm özellik sütunlarını [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) yöntemini kullanarak **Özellikler** sütununa birleştirir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="2bfab-191">Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler.</span><span class="sxs-lookup"><span data-stu-id="2bfab-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="2bfab-192">Bu dönüşümü aşağıdaki kodla ardışık ardışık olarak tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="2bfab-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 <span data-ttu-id="2bfab-193">Ardından, önbelleği kullanarak verileri birden çok kez yinelediğinizde aşağıdaki kodda olduğu gibi daha iyi performans elde edilebilsin diye DataView'ı önbelleğe almak için bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="2bfab-194">Eğitim süresini düşürmek için küçük/orta veri kümeleri için AppendCacheCheckpoint'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bfab-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="2bfab-195">KULLANMAYIN (kaldırın. Çok büyük veri kümelerini işlerken AppendCacheCheckpoint())</span><span class="sxs-lookup"><span data-stu-id="2bfab-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="2bfab-196">Yöntemin sonunda boru hattını `ProcessData` döndürün.</span><span class="sxs-lookup"><span data-stu-id="2bfab-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

<span data-ttu-id="2bfab-197">Bu adım, ön işleme/featurization işler.</span><span class="sxs-lookup"><span data-stu-id="2bfab-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="2bfab-198">ML.NET'da bulunan ek bileşenleri kullanmak, modelinizde daha iyi sonuçlar elde etmenizi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="2bfab-199">Modeli oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="2bfab-199">Build and train the model</span></span>

<span data-ttu-id="2bfab-200">Yöntemde `BuildAndTrainModel`bir sonraki kod satırı olarak yönteme `Main` aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="2bfab-201">Yöntem `BuildAndTrainModel` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="2bfab-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="2bfab-202">Eğitim algoritması sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bfab-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="2bfab-203">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-203">Trains the model.</span></span>
* <span data-ttu-id="2bfab-204">Eğitim verilerine göre alanı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="2bfab-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="2bfab-205">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="2bfab-205">Returns the model.</span></span>

<span data-ttu-id="2bfab-206">Yöntemden `BuildAndTrainModel` `Main` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="2bfab-207">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="2bfab-207">About the classification task</span></span>

<span data-ttu-id="2bfab-208">Sınıflandırma, bir öğenin veya veri satırının kategorisini, türünü veya sınıfını **belirlemek** için verileri kullanan ve sık sık aşağıdaki türlerden biri olan bir makine öğrenimi görevidir:</span><span class="sxs-lookup"><span data-stu-id="2bfab-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="2bfab-209">İkili: A veya B.</span><span class="sxs-lookup"><span data-stu-id="2bfab-209">Binary: either A or B.</span></span>
* <span data-ttu-id="2bfab-210">Çok sınıflı: Tek bir model kullanılarak tahmin edilebilen birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="2bfab-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="2bfab-211">Sorun kategorisi tahmini yalnızca iki (ikili) yerine birden çok kategoriden (çok sınıflı) biri olabileceğinden, bu tür bir sorun için çok sınıflı sınıflandırma öğrenme algoritması kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bfab-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="2bfab-212">Makine öğrenme algoritmasını veri dönüştürme tanımlarına ilk kod satırı olarak ekleyerek `BuildAndTrainModel()`ekle:</span><span class="sxs-lookup"><span data-stu-id="2bfab-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

<span data-ttu-id="2bfab-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) sizin çok sınıflı sınıflandırma eğitim algoritmanızdır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="2bfab-214">Bu, geçmiş `pipeline` verilerden öğrenmek için featurized`Features` `Label` `Title` ve `Description` ( ) ve giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="2bfab-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="2bfab-215">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2bfab-215">Train the model</span></span>

<span data-ttu-id="2bfab-216">Modeli `splitTrainSet` verilere sığdırın ve yöntemde bir sonraki kod satırı olarak `BuildAndTrainModel()` aşağıdakileri ekleyerek eğitilmiş modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="2bfab-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

<span data-ttu-id="2bfab-217">Yöntem, `Fit()`veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitiyor.</span><span class="sxs-lookup"><span data-stu-id="2bfab-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="2bfab-218">[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde bir tahmin gerçekleştirmenize ve geçiş yapmanızı sağlayan kolaylık api'sidir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="2bfab-219">`BuildAndTrainModel()` Yöntemde bir sonraki satır olarak bunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="2bfab-220">Eğitimli model ile tahmin edin</span><span class="sxs-lookup"><span data-stu-id="2bfab-220">Predict with the trained model</span></span>

<span data-ttu-id="2bfab-221">Bir örnek oluşturarak `Predict` yöntemde eğitimli modelin tahmin test etmek `GitHubIssue`için bir GitHub sorunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

<span data-ttu-id="2bfab-222">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevini kullanma, tek bir veri satırı nda öngörüyapar:</span><span class="sxs-lookup"><span data-stu-id="2bfab-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="2bfab-223">Modeli kullanma: tahmin sonuçları</span><span class="sxs-lookup"><span data-stu-id="2bfab-223">Using the model: prediction results</span></span>

<span data-ttu-id="2bfab-224">Sonuçları `GitHubIssue` paylaşmak `Area` ve buna göre hareket etmek için etiket tahminini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="2bfab-225">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu kullanarak sonuçlar için bir ekran oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="2bfab-226">Değerlendirme için kullanılmak üzere eğitilmiş modeli döndürme</span><span class="sxs-lookup"><span data-stu-id="2bfab-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="2bfab-227">Yöntemin sonunda modeli döndürün. `BuildAndTrainModel`</span><span class="sxs-lookup"><span data-stu-id="2bfab-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="2bfab-228">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="2bfab-228">Evaluate the model</span></span>

<span data-ttu-id="2bfab-229">Modeli oluşturduğunuz ve eğittiğinize göre, modeli kalite güvencesi ve doğrulama için farklı bir veri kümesiyle değerlendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="2bfab-230">`Evaluate` Yöntemde, oluşturulan model `BuildAndTrainModel` değerlendirilmek üzere geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="2bfab-231">Aşağıdaki `Evaluate` kodda olduğu `BuildAndTrainModel`gibi, hemen sonra yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="2bfab-232">Yöntem `Evaluate` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="2bfab-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="2bfab-233">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="2bfab-233">Loads the test dataset.</span></span>
* <span data-ttu-id="2bfab-234">Çok sınıflı değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bfab-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="2bfab-235">Modeli değerlendirir ve ölçümleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bfab-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="2bfab-236">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2bfab-236">Displays the metrics.</span></span>

<span data-ttu-id="2bfab-237">Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `BuildAndTrainModel` hemen altında, yöntemden yeni yönteme çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

<span data-ttu-id="2bfab-238">Daha önce eğitim veri setinde yaptığınız gibi, yönteme aşağıdaki kodu ekleyerek `Evaluate` test veri kümesini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

<span data-ttu-id="2bfab-239">[Değerlendirme()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) yöntemi, belirtilen veri kümesini kullanarak modelin kalite ölçümlerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="2bfab-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="2bfab-240">Çok sınıflı sınıflandırma değerlendiriciler tarafından hesaplanan genel ölçümleri içeren bir <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="2bfab-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="2bfab-241">Modelin kalitesini belirlemek için ölçümleri görüntülemek için önce bunları almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="2bfab-242">Özellikleri ve dönüş tahminlerini girdi etmek `_trainedModel` için makine öğrenme global değişkeninin (bir [ITransformer)](xref:Microsoft.ML.ITransformer) [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yönteminin kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="2bfab-243">`Evaluate` Yönteme sonraki satır olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

<span data-ttu-id="2bfab-244">Aşağıdaki ölçümler çok sınıflı sınıflandırma için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="2bfab-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="2bfab-245">Mikro Doğruluk - Her örnek sınıfı çifti doğruluk ölçümüne eşit katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="2bfab-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="2bfab-246">Micro Accuracy'in mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2bfab-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="2bfab-247">Makro Doğruluğu - Her sınıf doğruluk ölçümüne eşit katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="2bfab-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="2bfab-248">Azınlık sınıfları daha büyük sınıflar olarak eşit ağırlık verilir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="2bfab-249">Makro Doğruluğu'nun mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2bfab-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="2bfab-250">Günlük kaybı - [bkz.](../resources/glossary.md#log-loss)</span><span class="sxs-lookup"><span data-stu-id="2bfab-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="2bfab-251">Log-loss'un mümkün olduğunca sıfıra yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2bfab-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="2bfab-252">Günlük kaybı azaltma - 1.00'In mükemmel tahminleri olduğu ve 0'ın ortalama tahminleri gösterdiği [-inf, 1.00]'den aralıklar.</span><span class="sxs-lookup"><span data-stu-id="2bfab-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="2bfab-253">Günlük kaybı azaltmanın mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2bfab-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="2bfab-254">Model doğrulama için ölçümlerin görüntülenmesi</span><span class="sxs-lookup"><span data-stu-id="2bfab-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="2bfab-255">Ölçümleri görüntülemek, sonuçları paylaşmak ve sonra bunlara göre hareket etmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="2bfab-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="2bfab-256">Modeli bir dosyaya kaydetme</span><span class="sxs-lookup"><span data-stu-id="2bfab-256">Save the model to a file</span></span>

<span data-ttu-id="2bfab-257">Modelinizden memnun kaldıktan sonra, daha sonra veya başka bir uygulamada öngörülerde bulunmak için dosyayı bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="2bfab-258">`Evaluate` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="2bfab-259">Yönteminizin `SaveModelAsFile` `Evaluate` altındaki yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2bfab-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="2bfab-260">Yönteminize `SaveModelAsFile` aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="2bfab-261">Bu kod, [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) eğitilen modeli zip dosyası olarak seri hale getirmek ve depolamak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="2bfab-262">Bir modelle Dağıtma ve Tahmin Etme</span><span class="sxs-lookup"><span data-stu-id="2bfab-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="2bfab-263">Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `Evaluate` hemen altında, yöntemden yeni yönteme çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

<span data-ttu-id="2bfab-264">Yöntemden `PredictIssue` `Evaluate` hemen sonra (ve yöntemden `SaveModelAsFile` hemen önce) aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="2bfab-265">Yöntem `PredictIssue` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="2bfab-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="2bfab-266">Kaydedilen modeli yükler</span><span class="sxs-lookup"><span data-stu-id="2bfab-266">Loads the saved model</span></span>
* <span data-ttu-id="2bfab-267">Tek bir test verisi sorunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bfab-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="2bfab-268">Test verilerine göre Alanı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="2bfab-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="2bfab-269">Raporlama için test verilerini ve öngörüleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="2bfab-270">Öngörülen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2bfab-270">Displays the predicted results.</span></span>

<span data-ttu-id="2bfab-271">Yönteme aşağıdaki kodu ekleyerek kaydedilen modeli uygulamanıza yükleyin: `PredictIssue`</span><span class="sxs-lookup"><span data-stu-id="2bfab-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

<span data-ttu-id="2bfab-272">Bir örnek oluşturarak `Predict` yöntemde eğitimli modelin tahmin test etmek `GitHubIssue`için bir GitHub sorunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2bfab-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

<span data-ttu-id="2bfab-273">Daha önce yaptığınız gibi, `PredictionEngine` aşağıdaki kodu içeren bir örnek oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="2bfab-274">[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="2bfab-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2bfab-276">Tek dişli veya prototip ortamlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="2bfab-277">Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bfab-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="2bfab-278">ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="2bfab-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="2bfab-279">`PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="2bfab-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="2bfab-280">Tahmin `PredictionEngine` `PredictIssue` yöntemine aşağıdaki kodu ekleyerek Area GitHub etiketini tahmin etmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="2bfab-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="2bfab-281">Tahmin için yüklenen modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="2bfab-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="2bfab-282">Sorunu `Area` kategorilere ayırmak ve buna göre hareket etmek için görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="2bfab-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="2bfab-283">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu kullanarak sonuçlar için bir ekran oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2bfab-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="2bfab-284">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="2bfab-284">Results</span></span>

<span data-ttu-id="2bfab-285">Sonuçlarınız aşağıdakilere benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2bfab-285">Your results should be similar to the following.</span></span> <span data-ttu-id="2bfab-286">Ardışık işlem olarak, iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2bfab-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="2bfab-287">Uyarılar veya iletileri işleme görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bfab-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="2bfab-288">Bu iletiler netlik için aşağıdaki sonuçlardan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="2bfab-288">These messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="2bfab-289">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="2bfab-289">Congratulations!</span></span> <span data-ttu-id="2bfab-290">Şimdi başarılı bir şekilde sınıflandırmak ve bir GitHub sorunu için bir Alan etiketi tahmin için bir makine öğrenme modeli inşa ettik.</span><span class="sxs-lookup"><span data-stu-id="2bfab-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="2bfab-291">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bfab-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2bfab-292">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2bfab-292">Next steps</span></span>

<span data-ttu-id="2bfab-293">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="2bfab-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2bfab-294">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="2bfab-294">Prepare your data</span></span>
> * <span data-ttu-id="2bfab-295">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2bfab-295">Transform the data</span></span>
> * <span data-ttu-id="2bfab-296">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2bfab-296">Train the model</span></span>
> * <span data-ttu-id="2bfab-297">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="2bfab-297">Evaluate the model</span></span>
> * <span data-ttu-id="2bfab-298">Eğitimli model ile tahmin edin</span><span class="sxs-lookup"><span data-stu-id="2bfab-298">Predict with the trained model</span></span>
> * <span data-ttu-id="2bfab-299">Yüklü bir modelle Dağıtma ve Tahmin Etme</span><span class="sxs-lookup"><span data-stu-id="2bfab-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="2bfab-300">Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="2bfab-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2bfab-301">Taksi Ücreti Tahmincisi</span><span class="sxs-lookup"><span data-stu-id="2bfab-301">Taxi Fare Predictor</span></span>](predict-prices.md)
