---
title: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu
description: ML.NET ikili sınıflandırma senaryoda yaklaşım tahmin uygun eylemde için nasıl kullanılacağını anlamak için nasıl kullanılacağını keşfedin.
ms.date: 04/18/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 45e94e325fc4fbfaf1e71f7839d5083e44d5863e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973707"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="7df3d-103">Öğretici: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu</span><span class="sxs-lookup"><span data-stu-id="7df3d-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

<span data-ttu-id="7df3d-104">Bu örnek öğretici ML.NET gelen Web sitesi yorumların bir .NET Core konsol uygulaması kullanarak aracılığıyla uygun eylemde yaklaşımı anlamak için duyguları sınıflandırıcı oluşturma kullanmayı göstermektedir C# Visual Studio 2017'de.</span><span class="sxs-lookup"><span data-stu-id="7df3d-104">This sample tutorial illustrates using ML.NET to create a sentiment classifier to understand sentiment of incoming website comments to take the appropriate action via a .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="7df3d-105">Machine learning dünyasında, bu tür bir tahmin ikili sınıflandırma bilinir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-105">In the world of machine learning, this type of prediction is known as binary classification.</span></span>

> [!NOTE]
> <span data-ttu-id="7df3d-106">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="7df3d-107">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7df3d-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="7df3d-108">Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 1.0.0 Önizleme**.</span><span class="sxs-lookup"><span data-stu-id="7df3d-108">This tutorial and related sample are currently using **ML.NET version 1.0.0 preview**.</span></span> <span data-ttu-id="7df3d-109">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="7df3d-109">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="7df3d-110">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="7df3d-110">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7df3d-111">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="7df3d-111">Understand the problem</span></span>
> * <span data-ttu-id="7df3d-112">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="7df3d-112">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="7df3d-113">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="7df3d-113">Prepare your data</span></span>
> * <span data-ttu-id="7df3d-114">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7df3d-114">Transform the data</span></span>
> * <span data-ttu-id="7df3d-115">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="7df3d-115">Train the model</span></span>
> * <span data-ttu-id="7df3d-116">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="7df3d-116">Evaluate the model</span></span>
> * <span data-ttu-id="7df3d-117">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="7df3d-117">Predict with the trained model</span></span>
> * <span data-ttu-id="7df3d-118">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="7df3d-118">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="7df3d-119">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="7df3d-119">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7df3d-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7df3d-120">Prerequisites</span></span>

* <span data-ttu-id="7df3d-121">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="7df3d-122">UCI yaklaşım cümleler etiketli veri kümesini zip dosyası</span><span class="sxs-lookup"><span data-stu-id="7df3d-122">The UCI Sentiment Labeled Sentences dataset zip file</span></span>](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="create-a-console-application"></a><span data-ttu-id="7df3d-123">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="7df3d-123">Create a console application</span></span>

1. <span data-ttu-id="7df3d-124">Oluşturma bir **.NET Core konsol uygulaması** "SentimentAnalysis" denir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-124">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="7df3d-125">Adlı bir dizin oluşturmak *veri* , projenizdeki veri kümesi dosyalarınızı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7df3d-125">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="7df3d-126">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="7df3d-126">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="7df3d-127">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="7df3d-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="7df3d-128">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7df3d-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="7df3d-129">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="7df3d-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="7df3d-130">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="7df3d-130">Prepare your data</span></span>

1. <span data-ttu-id="7df3d-131">İndirme [UCI yaklaşım cümleler etiketli veri kümesini zip dosyası (alıntıları aşağıdaki nota bakın)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="7df3d-131">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="7df3d-132">Kopyalama `yelp_labelled.txt` doyasını *veri* oluşturduğunuz dizin.</span><span class="sxs-lookup"><span data-stu-id="7df3d-132">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7df3d-133">Bu öğreticide veri kümeleri Kotzias 'kaynak grubundan ayrıntılı özelliklerini kullanarak her bir etiketi için' olan et.</span><span class="sxs-lookup"><span data-stu-id="7df3d-133">The datasets this tutorial uses are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="7df3d-134">Al.</span><span class="sxs-lookup"><span data-stu-id="7df3d-134">al,.</span></span> <span data-ttu-id="7df3d-135">2015 ve barındırılan KDD UCI Machine Learning deposu - Dua, d ve Karra Taniskidou, e (2017).</span><span class="sxs-lookup"><span data-stu-id="7df3d-135">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="7df3d-136">UCI Makine deposu [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="7df3d-136">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="7df3d-137">Irvine, CA: California Üniversitesi, okul bilgi ve bilgisayar Bilimine.</span><span class="sxs-lookup"><span data-stu-id="7df3d-137">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

3. <span data-ttu-id="7df3d-138">Çözüm Gezgini'nde sağ `yelp_labeled.txt` seçin ve dosya **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="7df3d-138">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="7df3d-139">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="7df3d-139">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="7df3d-140">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7df3d-140">Create classes and define paths</span></span>

<span data-ttu-id="7df3d-141">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="7df3d-141">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="7df3d-142">En son indirilen veri kümesi dosyası yolu ve kayıtlı modeli dosya yolu tutmak için iki genel alanlar oluşturmak ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="7df3d-142">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="7df3d-143">`_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-143">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="7df3d-144">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-144">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="7df3d-145">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="7df3d-145">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="7df3d-146">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-146">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="7df3d-147">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7df3d-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="7df3d-148">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="7df3d-148">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="7df3d-149">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="7df3d-149">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="7df3d-150">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7df3d-150">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7df3d-151">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-151">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="7df3d-152">Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="7df3d-152">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="7df3d-153">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="7df3d-153">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="7df3d-154">Giriş veri kümesi sınıfı `SentimentData`, sahip bir `string` Açıklama (`SentimentText`) ve bir `bool` (`Sentiment`) yaklaşım ya da sıfırdan büyük (1) için bir değer olan veya negatif (0).</span><span class="sxs-lookup"><span data-stu-id="7df3d-154">The input dataset class, `SentimentData`, has a `string` for the comment (`SentimentText`) and a `bool` (`Sentiment`) that has a value for sentiment of either positive (1) or negative (0).</span></span> <span data-ttu-id="7df3d-155">Her iki alanınız [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri bağlı, her bir alanın veri dosyası siparişi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7df3d-155">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="7df3d-156">Ayrıca, `Sentiment` özelliğine sahip bir [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) olarak belirtmek için özniteliği `Label` alan.</span><span class="sxs-lookup"><span data-stu-id="7df3d-156">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="7df3d-157">Aşağıdaki örnek dosyası, bir başlık satırı yok ve şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="7df3d-157">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="7df3d-158">SentimentText</span><span class="sxs-lookup"><span data-stu-id="7df3d-158">SentimentText</span></span>                         |<span data-ttu-id="7df3d-159">Yaklaşım (etiketi)</span><span class="sxs-lookup"><span data-stu-id="7df3d-159">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="7df3d-160">Waitress hizmetinde biraz yavaş.</span><span class="sxs-lookup"><span data-stu-id="7df3d-160">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="7df3d-161">0</span><span class="sxs-lookup"><span data-stu-id="7df3d-161">0</span></span>     |
|<span data-ttu-id="7df3d-162">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="7df3d-162">Crust is not good.</span></span>                    |    <span data-ttu-id="7df3d-163">0</span><span class="sxs-lookup"><span data-stu-id="7df3d-163">0</span></span>     |
|<span data-ttu-id="7df3d-164">WOW... Burası sevdiği.</span><span class="sxs-lookup"><span data-stu-id="7df3d-164">Wow... Loved this place.</span></span>              |    <span data-ttu-id="7df3d-165">1.</span><span class="sxs-lookup"><span data-stu-id="7df3d-165">1</span></span>     |
|<span data-ttu-id="7df3d-166">Hizmet çok sor.</span><span class="sxs-lookup"><span data-stu-id="7df3d-166">Service was very prompt.</span></span>              |    <span data-ttu-id="7df3d-167">1.</span><span class="sxs-lookup"><span data-stu-id="7df3d-167">1</span></span>     |

<span data-ttu-id="7df3d-168">`SentimentPrediction` Tahmin sınıf, model eğitiminin sonra kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-168">`SentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="7df3d-169">Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7df3d-169">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="7df3d-170">`Label` Oluşturabilir ve ayrıca bölünmüş test veri kümesini kullanıma ile model değerlendirmek için kullanılan model ya da onun eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-170">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="7df3d-171">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-171">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="7df3d-172">Değerlendirme, eğitim verileri, tahmin edilen değerleri ve modeli kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-172">For evaluation, training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="7df3d-173">[MLContext sınıfı](xref:Microsoft.ML.MLContext) bir tüm ML.NET işlemleri için başlangıç noktası ve başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7df3d-173">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="7df3d-174">Bu, kavramsal olarak, benzer `DBContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="7df3d-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="7df3d-175">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="7df3d-175">Initialize variables in Main</span></span>

<span data-ttu-id="7df3d-176">Değiştirin `Console.WriteLine("Hello World!")` satırına `Main` mlContext değişkeni bildirmek ve başlatmak için aşağıdaki kod ile yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

<span data-ttu-id="7df3d-177">Sonraki kod satırı olarak ekleyin `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-177">Add the following as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

<span data-ttu-id="7df3d-178">`LoadData()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7df3d-178">The `LoadData()` method executes the following tasks:</span></span>

* <span data-ttu-id="7df3d-179">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="7df3d-179">Loads the data.</span></span>
* <span data-ttu-id="7df3d-180">Yüklenen veri kümesi train böler ve test edin, veri kümeleri.</span><span class="sxs-lookup"><span data-stu-id="7df3d-180">Splits the loaded dataset into train and test datasets.</span></span>
* <span data-ttu-id="7df3d-181">Bölme döndürür eğitme ve test etme, veri kümeleri.</span><span class="sxs-lookup"><span data-stu-id="7df3d-181">Returns the split train and test datasets.</span></span>

<span data-ttu-id="7df3d-182">Oluşturma `LoadData()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="7df3d-182">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
public static TrainTestData LoadData(MLContext mlContext)
{

}
```

## <a name="load-the-data"></a><span data-ttu-id="7df3d-183">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="7df3d-183">Load the data</span></span>

<span data-ttu-id="7df3d-184">ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="7df3d-184">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="7df3d-185">`IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur.</span><span class="sxs-lookup"><span data-stu-id="7df3d-185">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="7df3d-186">Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.</span><span class="sxs-lookup"><span data-stu-id="7df3d-186">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>
<span data-ttu-id="7df3d-187">İlk satırı olarak aşağıdaki kodu ekleyin `LoadData()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-187">Add the following code as the first line of the `LoadData()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="7df3d-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur.</span><span class="sxs-lookup"><span data-stu-id="7df3d-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="7df3d-189">Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="7df3d-189">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="7df3d-190">Eğitim ve test modeli için veri kümesi bölünemiyor</span><span class="sxs-lookup"><span data-stu-id="7df3d-190">Split the dataset for model training and testing</span></span>

<span data-ttu-id="7df3d-191">Ardından, hem bir eğitim veri kümesi modeli eğitmek için hem de model değerlendirmek için test veri kümesini gerekir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-191">Next, you need both a training dataset to train the model and a test dataset to evaluate the model.</span></span>

<span data-ttu-id="7df3d-192">Yüklenen verilere gerekli veri kümelerine ayırmak için bir sonraki satırda olarak aşağıdaki kodu ekleyin `LoadData()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-192">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

[!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

<span data-ttu-id="7df3d-193">Önceki kod [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) train yüklenen veri kümesi bölün ve veri kümeleri sınayabilir ve bunları yöntemi [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7df3d-193">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="7df3d-194">Test verileri ile yüzdesi belirlemek `testFraction`parametresi.</span><span class="sxs-lookup"><span data-stu-id="7df3d-194">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="7df3d-195">Varsayılan % 10'dur ancak, % 20 Bu durumda daha fazla veri değerlendirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7df3d-195">The default is 10% but you use 20% in this case to evaluate more data.</span></span>  

<span data-ttu-id="7df3d-196">Dönüş `splitDataView` sonunda `LoadData()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-196">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

[!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="7df3d-197">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="7df3d-197">Build and train the model</span></span>

<span data-ttu-id="7df3d-198">Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-198">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="7df3d-199">`BuildAndTrainModel()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7df3d-199">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="7df3d-200">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7df3d-200">Extracts and transforms the data.</span></span>
* <span data-ttu-id="7df3d-201">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-201">Trains the model.</span></span>
* <span data-ttu-id="7df3d-202">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="7df3d-202">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="7df3d-203">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="7df3d-203">Returns the model.</span></span>

<span data-ttu-id="7df3d-204">Oluşturma `BuildAndTrainModel()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="7df3d-204">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="7df3d-205">Verileri dönüştürme ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="7df3d-205">Extract and transform the data</span></span>

<span data-ttu-id="7df3d-206">Çağrı `FeaturizeText` sonraki kod satırına olarak:</span><span class="sxs-lookup"><span data-stu-id="7df3d-206">Call `FeaturizeText` as the next line of code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

<span data-ttu-id="7df3d-207">`FeaturizeText()` Yöntemi önceki kodda, metin sütununu dönüştürür (`SentimentText`) sayısal bir anahtar türü `Features` sütun makine öğrenimi algoritması tarafından kullanılan ve yeni veri kümesi bir sütun olarak ekler:</span><span class="sxs-lookup"><span data-stu-id="7df3d-207">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

|<span data-ttu-id="7df3d-208">SentimentText</span><span class="sxs-lookup"><span data-stu-id="7df3d-208">SentimentText</span></span>                         |<span data-ttu-id="7df3d-209">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="7df3d-209">Sentiment</span></span> |<span data-ttu-id="7df3d-210">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7df3d-210">Features</span></span>              |
|--------------------------------------|----------|----------------------|
|<span data-ttu-id="7df3d-211">Waitress hizmetinde biraz yavaş.</span><span class="sxs-lookup"><span data-stu-id="7df3d-211">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="7df3d-212">0</span><span class="sxs-lookup"><span data-stu-id="7df3d-212">0</span></span>     |<span data-ttu-id="7df3d-213">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="7df3d-213">[0.76, 0.65, 0.44, …]</span></span> |
|<span data-ttu-id="7df3d-214">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="7df3d-214">Crust is not good.</span></span>                    |    <span data-ttu-id="7df3d-215">0</span><span class="sxs-lookup"><span data-stu-id="7df3d-215">0</span></span>     |<span data-ttu-id="7df3d-216">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="7df3d-216">[0.98, 0.43, 0.54, …]</span></span> |
|<span data-ttu-id="7df3d-217">WOW... Burası sevdiği.</span><span class="sxs-lookup"><span data-stu-id="7df3d-217">Wow... Loved this place.</span></span>              |    <span data-ttu-id="7df3d-218">1.</span><span class="sxs-lookup"><span data-stu-id="7df3d-218">1</span></span>     |<span data-ttu-id="7df3d-219">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="7df3d-219">[0.35, 0.73, 0.46, …]</span></span> |
|<span data-ttu-id="7df3d-220">Hizmet çok sor.</span><span class="sxs-lookup"><span data-stu-id="7df3d-220">Service was very prompt.</span></span>              |    <span data-ttu-id="7df3d-221">1.</span><span class="sxs-lookup"><span data-stu-id="7df3d-221">1</span></span>     |<span data-ttu-id="7df3d-222">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="7df3d-222">[0.39, 0, 0.75, …]</span></span>    |

## <a name="add-a-learning-algorithm"></a><span data-ttu-id="7df3d-223">Bir öğrenme algoritması Ekle</span><span class="sxs-lookup"><span data-stu-id="7df3d-223">Add a learning algorithm</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="7df3d-224">Sınıflandırma görevi hakkında</span><span class="sxs-lookup"><span data-stu-id="7df3d-224">About the classification task</span></span>

<span data-ttu-id="7df3d-225">"Bu A veya B?"</span><span class="sxs-lookup"><span data-stu-id="7df3d-225">"Is it A or B?"</span></span>

![Sınıflandırma makine öğrenimi algoritması](./media/sentiment-analysis/classification.png)

<span data-ttu-id="7df3d-227">Sınıflandırma olan verileri kullanan bir machine learning algoritmasını **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı ve sık sık aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="7df3d-227">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="7df3d-228">İkili: ya da A veya b</span><span class="sxs-lookup"><span data-stu-id="7df3d-228">Binary: either A or B.</span></span>
* <span data-ttu-id="7df3d-229">Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.</span><span class="sxs-lookup"><span data-stu-id="7df3d-229">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="7df3d-230">Web sitesi açıklamaları pozitif veya negatif olarak sınıflandırılması gerektiğinden, ikili sınıflandırma görevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7df3d-230">Because the website comments need to be classified as either positive or negative, you use the Binary Classification task.</span></span>

<span data-ttu-id="7df3d-231">Machine learning görev sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını ekleme `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="7df3d-231">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="7df3d-232">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) sınıflandırma eğitim algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-232">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="7df3d-233">Bu eklenen `estimator` ve özellikleri tespit `SentimentText` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7df3d-233">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="7df3d-234">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="7df3d-234">Train the model</span></span>

<span data-ttu-id="7df3d-235">Modele uygun `splitTrainSet` veri ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `BuildAndTrainModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-235">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="7df3d-236">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-236">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="7df3d-237">Değerlendirme için kullanılacak modeli eğitilir döndürür</span><span class="sxs-lookup"><span data-stu-id="7df3d-237">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="7df3d-238">Model sonunda dönüş `BuildAndTrainModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-238">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="7df3d-239">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="7df3d-239">Evaluate the model</span></span>

<span data-ttu-id="7df3d-240">Modelinizi eğitildi sonra modelinizi kalite güvencesi ve doğrulama için nasıl gerçekleştiriyor değerlendirmek için test verilerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7df3d-240">After your model is trained, use your test data to evaluate how your model is performing for quality assurance and validation.</span></span> <span data-ttu-id="7df3d-241">Oluşturma `Evaluate()` yöntemi hemen sonrasına `BuildAndTrainModel()`, aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="7df3d-241">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

<span data-ttu-id="7df3d-242">`Evaluate()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7df3d-242">The `Evaluate()` method executes the following tasks:</span></span>

* <span data-ttu-id="7df3d-243">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="7df3d-243">Loads the test dataset.</span></span>
* <span data-ttu-id="7df3d-244">BinaryClassification değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7df3d-244">Creates the BinaryClassification evaluator.</span></span>
* <span data-ttu-id="7df3d-245">Model değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7df3d-245">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="7df3d-246">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7df3d-246">Displays the metrics.</span></span>

<span data-ttu-id="7df3d-247">Yeni yönteme bir çağrı ekleyin `Main()` yöntemi, sağda altında `BuildAndTrainModel()` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="7df3d-247">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

<span data-ttu-id="7df3d-248">Dönüştürme `splitTestSet` aşağıdakileri ekleyerek veri kod için `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="7df3d-248">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

<span data-ttu-id="7df3d-249">Önceki kod [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) birden çok test veri kümesini girdi satırları sağlanan için tahminde bulunmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7df3d-249">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="7df3d-250">Sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirme `Evaluate()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-250">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="7df3d-251">Ayarlama tahmin aldıktan sonra (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi değerlendirir gerçek tahmin edilen değerlerle karşılaştırır modeli `Labels` test veri kümesini ve döndürür bir [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) modelin nasıl performans gösterdiğini üzerinde nesne.</span><span class="sxs-lookup"><span data-stu-id="7df3d-251">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="7df3d-252">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7df3d-252">Displaying the metrics for model validation</span></span>

<span data-ttu-id="7df3d-253">Ölçümleri görüntülemek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="7df3d-253">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="7df3d-254">`Accuracy` Ölçüm doğru tahminler elde etmek test kümesindeki oranı olan bir model doğruluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-254">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="7df3d-255">`AreaUnderRocCurve` Ölçüm nasıl başarılara model doğru pozitif ve negatif sınıfları sınıflandırma olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-255">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="7df3d-256">İstediğiniz `AreaUnderRocCurve` biri olarak mümkün olduğunca yakın olmasını.</span><span class="sxs-lookup"><span data-stu-id="7df3d-256">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="7df3d-257">`F1Score` Ölçüm Bakiye ölçüsüdür modelin F1 puanı alır arasında [duyarlık](../resources/glossary.md#precision) ve [geri çağırma](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="7df3d-257">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="7df3d-258">İstediğiniz `F1Score` biri olarak mümkün olduğunca yakın olmasını.</span><span class="sxs-lookup"><span data-stu-id="7df3d-258">You want the `F1Score` to be as close to one as possible.</span></span>

## <a name="predict-the-test-data-outcome"></a><span data-ttu-id="7df3d-259">Test verileri sonucu tahmin edin</span><span class="sxs-lookup"><span data-stu-id="7df3d-259">Predict the test data outcome</span></span>

<span data-ttu-id="7df3d-260">Oluşturma `UseModelWithSingleItem()` yöntemi hemen sonrasına `Evaluate()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="7df3d-260">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="7df3d-261">`UseModelWithSingleItem()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7df3d-261">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

* <span data-ttu-id="7df3d-262">Test verilerini tek bir yorum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7df3d-262">Creates a single comment of test data.</span></span>
* <span data-ttu-id="7df3d-263">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="7df3d-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="7df3d-264">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="7df3d-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="7df3d-265">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7df3d-265">Displays the predicted results.</span></span>

<span data-ttu-id="7df3d-266">Yeni yönteme bir çağrı ekleyin `Main()` yöntemi, sağda altında `Evaluate()` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="7df3d-266">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

[!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

<span data-ttu-id="7df3d-267">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) geçirin ve ardından verileri tek bir örneğini tahmin gerçekleştirin izin veren bir kolaylık API, bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-267">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="7df3d-268">ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin `Predict()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-268">add the following code to create as the first line in the `Predict()` Method:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
<span data-ttu-id="7df3d-269">Eğitilen modelin tahmine test etmek için bir açıklama ekleyin `Predict()` bir örneğini oluşturarak yöntemi `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="7df3d-269">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

<span data-ttu-id="7df3d-270">Test açıklaması verileri geçirmek `Prediction Engine` aşağıdaki kodda bir sonraki satırı olarak ekleyerek `UseModelWithSingleItem()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-270">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

<span data-ttu-id="7df3d-271">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi verilerin tek bir satırda bir tahmin sağlar.</span><span class="sxs-lookup"><span data-stu-id="7df3d-271">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

### <a name="use-the-model-prediction"></a><span data-ttu-id="7df3d-272">Model kullanmak: tahmin</span><span class="sxs-lookup"><span data-stu-id="7df3d-272">Use the model: prediction</span></span>

<span data-ttu-id="7df3d-273">Görüntü `SentimentText` ve aşağıdaki kodu kullanarak ilgili yaklaşım tahmin:</span><span class="sxs-lookup"><span data-stu-id="7df3d-273">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="7df3d-274">Toplu iş öğeleri tahmin edin ve dağıtın</span><span class="sxs-lookup"><span data-stu-id="7df3d-274">Deploy and predict batch items</span></span>

<span data-ttu-id="7df3d-275">Oluşturma `UseModelWithBatchItems()` yöntemi hemen sonrasına `UseModelWithSingleItem()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="7df3d-275">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

```csharp
public static void UseModelWithBatchItems(MLContext mlContext)
{

}
```

<span data-ttu-id="7df3d-276">`UseModelWithBatchItems()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7df3d-276">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

* <span data-ttu-id="7df3d-277">Toplu test verilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7df3d-277">Creates batch test data.</span></span>
* <span data-ttu-id="7df3d-278">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="7df3d-278">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="7df3d-279">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="7df3d-279">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="7df3d-280">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7df3d-280">Displays the predicted results.</span></span>

<span data-ttu-id="7df3d-281">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `UseModelWithSingleItem()` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="7df3d-281">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

<span data-ttu-id="7df3d-282">Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `UseModelWithBatchItems()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-282">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="use-the-model-for-prediction"></a><span data-ttu-id="7df3d-283">Model için tahmin kullanın</span><span class="sxs-lookup"><span data-stu-id="7df3d-283">Use the model for prediction</span></span>

<span data-ttu-id="7df3d-284">Açıklama veri yaklaşım kullanarak tahmin modelini kullanan [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-284">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="7df3d-285">Birleştirme ve Öngörüler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7df3d-285">Combine and display the predictions</span></span>

<span data-ttu-id="7df3d-286">Aşağıdaki kodu kullanarak tahminler elde etmek için bir başlık oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7df3d-286">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="7df3d-287">Özgün açıklamayı, tahmin edilen bir yaklaşım kullanarak ile birleştirerek tahmin sonuçlarını görüntülemeden önce [Zip()](xref:System.Linq.Enumerable.Zip%2A) yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7df3d-287">Before displaying the predicted results, combine the original comment with its predicted sentiment using the [Zip()](xref:System.Linq.Enumerable.Zip%2A) method:</span></span>

[!code-csharp[BuildTuples](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="7df3d-288">Şimdi `SentimentText` ve `Sentiment` olan bir sınıf içinde kullanıldığında, sonuçları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="7df3d-288">Now that `SentimentText` and `Sentiment` are combined in a class, display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="7df3d-289">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="7df3d-289">Results</span></span>

<span data-ttu-id="7df3d-290">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-290">Your results should be similar to the following.</span></span> <span data-ttu-id="7df3d-291">İşleme sırasında iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-291">During processing, messages are displayed.</span></span> <span data-ttu-id="7df3d-292">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7df3d-292">You may see warnings, or processing messages.</span></span> <span data-ttu-id="7df3d-293">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7df3d-293">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="7df3d-294">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="7df3d-294">Congratulations!</span></span> <span data-ttu-id="7df3d-295">Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="7df3d-295">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="7df3d-296">Başarılı modeller oluşturma yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-296">Building successful models is an iterative process.</span></span> <span data-ttu-id="7df3d-297">Bu model düşük ilk kalite hızlı modeli eğitimi sağlamak için öğretici kullanan küçük veri kümeleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7df3d-297">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="7df3d-298">Model kalitesi memnun değilseniz farklı farklı eğitim algoritmalarıyla seçerek ya da daha büyük bir eğitim veri kümeleri sağlayarak geliştirmek deneyebilirsiniz [hyper-parametreleriyle](../resources/glossary.md##hyperparameter) her bir algoritmanın için.</span><span class="sxs-lookup"><span data-stu-id="7df3d-298">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="7df3d-299">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="7df3d-299">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7df3d-300">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7df3d-300">Next steps</span></span>

<span data-ttu-id="7df3d-301">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="7df3d-301">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7df3d-302">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="7df3d-302">Understand the problem</span></span>
> * <span data-ttu-id="7df3d-303">Uygun makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="7df3d-303">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="7df3d-304">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="7df3d-304">Prepare your data</span></span>
> * <span data-ttu-id="7df3d-305">Verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7df3d-305">Transform the data</span></span>
> * <span data-ttu-id="7df3d-306">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="7df3d-306">Train the model</span></span>
> * <span data-ttu-id="7df3d-307">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="7df3d-307">Evaluate the model</span></span>
> * <span data-ttu-id="7df3d-308">Eğitilen modeli tahmin edin</span><span class="sxs-lookup"><span data-stu-id="7df3d-308">Predict with the trained model</span></span>
> * <span data-ttu-id="7df3d-309">Dağıtma ve yüklenen modeliyle tahmin edin</span><span class="sxs-lookup"><span data-stu-id="7df3d-309">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="7df3d-310">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="7df3d-310">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7df3d-311">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="7df3d-311">Issue Classification</span></span>](github-issue-classification.md)
