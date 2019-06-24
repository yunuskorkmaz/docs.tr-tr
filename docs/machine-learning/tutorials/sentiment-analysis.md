---
title: 'Öğretici: Web sitesi açıklamaları - ikili sınıflandırma analiz edin'
description: Bu öğreticide, elde edilen Web sitesi açıklamaları duyarlılığı sınıflandırır ve uygun tedbiri alır bir .NET Core konsol uygulaması oluşturma işlemini gösterir. İkili yaklaşım sınıflandırıcı kullanan C# Visual Studio'da.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: a766d95c62fd3a89e3291e1ab803f5222fac46ea
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306176"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="ab557-104">Öğretici: ML.NET ikili sınıflandırma ile Web sitesi yorumların düşüncelerini çözümleme</span><span class="sxs-lookup"><span data-stu-id="ab557-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="ab557-105">Bu öğreticide, elde edilen Web sitesi açıklamaları duyarlılığı sınıflandırır ve uygun tedbiri alır bir .NET Core konsol uygulaması oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab557-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="ab557-106">İkili yaklaşım sınıflandırıcı kullanan C# Visual Studio 2017'de.</span><span class="sxs-lookup"><span data-stu-id="ab557-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="ab557-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="ab557-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ab557-108">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab557-108">Create a console application</span></span>
> * <span data-ttu-id="ab557-109">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="ab557-109">Prepare data</span></span>
> * <span data-ttu-id="ab557-110">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="ab557-110">Load the data</span></span>
> * <span data-ttu-id="ab557-111">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="ab557-111">Build and train the model</span></span>
> * <span data-ttu-id="ab557-112">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ab557-112">Evaluate the model</span></span>
> * <span data-ttu-id="ab557-113">Model bir tahminde kullanmak</span><span class="sxs-lookup"><span data-stu-id="ab557-113">Use the model to make a prediction</span></span>
> * <span data-ttu-id="ab557-114">Sonuçları göster</span><span class="sxs-lookup"><span data-stu-id="ab557-114">See the results</span></span>

<span data-ttu-id="ab557-115">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="ab557-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ab557-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ab557-116">Prerequisites</span></span>

* <span data-ttu-id="ab557-117">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır</span><span class="sxs-lookup"><span data-stu-id="ab557-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

* <span data-ttu-id="ab557-118">[UCI yaklaşım cümleler etiketli veri kümesini](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası)</span><span class="sxs-lookup"><span data-stu-id="ab557-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ab557-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab557-119">Create a console application</span></span>

1. <span data-ttu-id="ab557-120">Oluşturma bir **.NET Core konsol uygulaması** "SentimentAnalysis" denir.</span><span class="sxs-lookup"><span data-stu-id="ab557-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="ab557-121">Adlı bir dizin oluşturmak *veri* , projenizdeki veri kümesi dosyalarınızı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ab557-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="ab557-122">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="ab557-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="ab557-123">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="ab557-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ab557-124">Paket kaynağı olarak "nuget.org" seçin ve ardından **Gözat** sekmesi. Arama **Microsoft.ML**, seçin ve ardından paketi **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ab557-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="ab557-125">Seçtiğiniz paket için lisans koşullarını kabul ederek kuruluma devam edin.</span><span class="sxs-lookup"><span data-stu-id="ab557-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="ab557-126">İçin de aynısını yapın **Microsoft.ML.FastTree** NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="ab557-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="ab557-127">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="ab557-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="ab557-128">Bu öğretici için veri kümeleri Kotzias 'kaynak grubundan ayrıntılı özelliklerini kullanarak her bir etiketi için' olan et.</span><span class="sxs-lookup"><span data-stu-id="ab557-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="ab557-129">Al.</span><span class="sxs-lookup"><span data-stu-id="ab557-129">al,.</span></span> <span data-ttu-id="ab557-130">2015 ve barındırılan KDD UCI Machine Learning deposu - Dua, d ve Karra Taniskidou, e (2017).</span><span class="sxs-lookup"><span data-stu-id="ab557-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="ab557-131">UCI Makine deposu [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="ab557-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="ab557-132">Irvine, CA: California Üniversitesi, okul bilgi ve bilgisayar Bilimine.</span><span class="sxs-lookup"><span data-stu-id="ab557-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="ab557-133">İndirme [UCI yaklaşım cümleler etiketli veri kümesini ZIP dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="ab557-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="ab557-134">Kopyalama `yelp_labelled.txt` doyasını *veri* oluşturduğunuz dizin.</span><span class="sxs-lookup"><span data-stu-id="ab557-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="ab557-135">Çözüm Gezgini'nde sağ `yelp_labeled.txt` seçin ve dosya **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="ab557-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="ab557-136">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="ab557-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="ab557-137">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab557-137">Create classes and define paths</span></span>

1. <span data-ttu-id="ab557-138">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="ab557-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="ab557-139">En son indirilen veri kümesi dosyası yolu ve kayıtlı modeli dosya yolu tutmak için iki genel alanlar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ab557-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="ab557-140">`_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab557-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="ab557-141">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="ab557-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="ab557-142">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="ab557-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="ab557-143">Ardından, girdi verilerini ve Öngörüler için sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ab557-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="ab557-144">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ab557-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="ab557-145">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="ab557-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="ab557-146">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ab557-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="ab557-147">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ab557-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="ab557-148">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="ab557-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ab557-149">Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ab557-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="ab557-150">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="ab557-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="ab557-151">Verilerin nasıl hazırlanmıştır</span><span class="sxs-lookup"><span data-stu-id="ab557-151">How the data was prepared</span></span>
<span data-ttu-id="ab557-152">Giriş veri kümesi sınıfı `SentimentData`, sahip bir `string` kullanıcı yorumları için (`SentimentText`) ve bir `bool` (`Sentiment`) değeri 1 (pozitif) veya yaklaşım için 0 (negatif).</span><span class="sxs-lookup"><span data-stu-id="ab557-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="ab557-153">Her iki alanınız [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri bağlı, her bir alanın veri dosyası siparişi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ab557-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="ab557-154">Ayrıca, `Sentiment` özelliğine sahip bir [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) olarak belirtmek için özniteliği `Label` alan.</span><span class="sxs-lookup"><span data-stu-id="ab557-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="ab557-155">Aşağıdaki örnek dosyası, bir başlık satırı yok ve şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="ab557-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="ab557-156">SentimentText</span><span class="sxs-lookup"><span data-stu-id="ab557-156">SentimentText</span></span>                         |<span data-ttu-id="ab557-157">Yaklaşım (etiketi)</span><span class="sxs-lookup"><span data-stu-id="ab557-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="ab557-158">Waitress hizmetinde biraz yavaş.</span><span class="sxs-lookup"><span data-stu-id="ab557-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="ab557-159">0</span><span class="sxs-lookup"><span data-stu-id="ab557-159">0</span></span>     |
|<span data-ttu-id="ab557-160">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="ab557-160">Crust is not good.</span></span>                    |    <span data-ttu-id="ab557-161">0</span><span class="sxs-lookup"><span data-stu-id="ab557-161">0</span></span>     |
|<span data-ttu-id="ab557-162">WOW... Burası sevdiği.</span><span class="sxs-lookup"><span data-stu-id="ab557-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="ab557-163">1\.</span><span class="sxs-lookup"><span data-stu-id="ab557-163">1</span></span>     |
|<span data-ttu-id="ab557-164">Hizmet çok sor.</span><span class="sxs-lookup"><span data-stu-id="ab557-164">Service was very prompt.</span></span>              |    <span data-ttu-id="ab557-165">1\.</span><span class="sxs-lookup"><span data-stu-id="ab557-165">1</span></span>     |

<span data-ttu-id="ab557-166">`SentimentPrediction` Tahmin sınıf, model eğitiminin sonra kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab557-166">`SentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="ab557-167">Devraldığı `SentimentData` görüntülemek için `SentimentText` Öngörüler ile.</span><span class="sxs-lookup"><span data-stu-id="ab557-167">It inherits from `SentimentData` for displaying the `SentimentText` with the predictions.</span></span> <span data-ttu-id="ab557-168">`SentimentPrediction` sahip tek bir Boole değeri (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ab557-168">`SentimentPrediction` has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="ab557-169">`Label` Oluşturabilir ve ayrıca bölünmüş test veri kümesini kullanıma ile model değerlendirmek için kullanılan model ya da onun eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab557-169">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="ab557-170">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab557-170">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="ab557-171">Değerlendirme, eğitim verileri, tahmin edilen değerleri ve modeli kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab557-171">For evaluation, training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="ab557-172">[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="ab557-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="ab557-173">Başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab557-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="ab557-174">Bu, kavramsal olarak, benzer `DBContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ab557-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="ab557-175">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="ab557-175">Load the data</span></span>
<span data-ttu-id="ab557-176">ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="ab557-176">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="ab557-177">`IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur.</span><span class="sxs-lookup"><span data-stu-id="ab557-177">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="ab557-178">Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.</span><span class="sxs-lookup"><span data-stu-id="ab557-178">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="ab557-179">Uygulamayı hazırlama ve ardından veri yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ab557-179">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="ab557-180">Değiştirin `Console.WriteLine("Hello World!")` satırına `Main` mlContext değişkeni bildirmek ve başlatmak için aşağıdaki kod ile yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-180">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="ab557-181">Sonraki kod satırı olarak ekleyin `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-181">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="ab557-182">Oluşturma `LoadData()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="ab557-182">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="ab557-183">`LoadData()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="ab557-183">The `LoadData()` method executes the following tasks:</span></span>

    * <span data-ttu-id="ab557-184">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="ab557-184">Loads the data.</span></span>
    * <span data-ttu-id="ab557-185">Yüklenen veri kümesi train böler ve test edin, veri kümeleri.</span><span class="sxs-lookup"><span data-stu-id="ab557-185">Splits the loaded dataset into train and test datasets.</span></span>
    * <span data-ttu-id="ab557-186">Bölme döndürür eğitme ve test etme, veri kümeleri.</span><span class="sxs-lookup"><span data-stu-id="ab557-186">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="ab557-187">İlk satırı olarak aşağıdaki kodu ekleyin `LoadData()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-187">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="ab557-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur.</span><span class="sxs-lookup"><span data-stu-id="ab557-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="ab557-189">Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="ab557-189">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="ab557-190">Eğitim ve test modeli için veri kümesi bölünemiyor</span><span class="sxs-lookup"><span data-stu-id="ab557-190">Split the dataset for model training and testing</span></span>

<span data-ttu-id="ab557-191">Bir model hazırlarken ve modelin doğruluğunu test etmek için veri kümesinin parçası eğitmek için veri kümesinin parçası kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab557-191">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="ab557-192">Yüklenen verilere gerekli veri kümelerine ayırmak için bir sonraki satırda olarak aşağıdaki kodu ekleyin `LoadData()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-192">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="ab557-193">Önceki kod [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) train yüklenen veri kümesi bölün ve veri kümeleri sınayabilir ve bunları yöntemi [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ab557-193">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="ab557-194">Test verileri ile yüzdesi belirlemek `testFraction`parametresi.</span><span class="sxs-lookup"><span data-stu-id="ab557-194">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="ab557-195">Varsayılan % 10, bu durumda, % 20 daha fazla veri değerlendirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab557-195">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="ab557-196">Dönüş `splitDataView` sonunda `LoadData()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-196">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="ab557-197">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="ab557-197">Build and train the model</span></span>

1. <span data-ttu-id="ab557-198">Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-198">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="ab557-199">`BuildAndTrainModel()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="ab557-199">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    * <span data-ttu-id="ab557-200">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ab557-200">Extracts and transforms the data.</span></span>
    * <span data-ttu-id="ab557-201">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="ab557-201">Trains the model.</span></span>
    * <span data-ttu-id="ab557-202">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="ab557-202">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="ab557-203">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab557-203">Returns the model.</span></span>

2. <span data-ttu-id="ab557-204">Oluşturma `BuildAndTrainModel()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="ab557-204">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="ab557-205">Verileri dönüştürme ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="ab557-205">Extract and transform the data</span></span>

1. <span data-ttu-id="ab557-206">Çağrı `FeaturizeText` sonraki kod satırına olarak:</span><span class="sxs-lookup"><span data-stu-id="ab557-206">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="ab557-207">`FeaturizeText()` Yöntemi önceki kodda, metin sütununu dönüştürür (`SentimentText`) sayısal bir anahtar türü `Features` sütun makine öğrenimi algoritması tarafından kullanılan ve yeni veri kümesi bir sütun olarak ekler:</span><span class="sxs-lookup"><span data-stu-id="ab557-207">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="ab557-208">SentimentText</span><span class="sxs-lookup"><span data-stu-id="ab557-208">SentimentText</span></span>                         |<span data-ttu-id="ab557-209">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="ab557-209">Sentiment</span></span> |<span data-ttu-id="ab557-210">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ab557-210">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="ab557-211">Waitress hizmetinde biraz yavaş.</span><span class="sxs-lookup"><span data-stu-id="ab557-211">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="ab557-212">0</span><span class="sxs-lookup"><span data-stu-id="ab557-212">0</span></span>     |<span data-ttu-id="ab557-213">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="ab557-213">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="ab557-214">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="ab557-214">Crust is not good.</span></span>                    |    <span data-ttu-id="ab557-215">0</span><span class="sxs-lookup"><span data-stu-id="ab557-215">0</span></span>     |<span data-ttu-id="ab557-216">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="ab557-216">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="ab557-217">WOW... Burası sevdiği.</span><span class="sxs-lookup"><span data-stu-id="ab557-217">Wow... Loved this place.</span></span>              |    <span data-ttu-id="ab557-218">1\.</span><span class="sxs-lookup"><span data-stu-id="ab557-218">1</span></span>     |<span data-ttu-id="ab557-219">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="ab557-219">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="ab557-220">Hizmet çok sor.</span><span class="sxs-lookup"><span data-stu-id="ab557-220">Service was very prompt.</span></span>              |    <span data-ttu-id="ab557-221">1\.</span><span class="sxs-lookup"><span data-stu-id="ab557-221">1</span></span>     |<span data-ttu-id="ab557-222">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="ab557-222">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="ab557-223">Bir öğrenme algoritması Ekle</span><span class="sxs-lookup"><span data-stu-id="ab557-223">Add a learning algorithm</span></span>

<span data-ttu-id="ab557-224">Bu uygulama, öğeleri veya veri satırı kategorilere ayıran bir sınıflandırma algoritmasıdır kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab557-224">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="ab557-225">Uygulama Web sitesi açıklamaları artı veya eksi olarak kategorilere ayırır, ikili sınıflandırma görevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab557-225">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="ab557-226">Machine learning görev sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını ekleme `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="ab557-226">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="ab557-227">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) sınıflandırma eğitim algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ab557-227">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="ab557-228">Bu eklenen `estimator` ve özellikleri tespit `SentimentText` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="ab557-228">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="ab557-229">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="ab557-229">Train the model</span></span>

<span data-ttu-id="ab557-230">Modele uygun `splitTrainSet` veri ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `BuildAndTrainModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-230">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="ab557-231">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="ab557-231">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="ab557-232">Değerlendirme için kullanılacak modeli eğitilir döndürür</span><span class="sxs-lookup"><span data-stu-id="ab557-232">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="ab557-233">Model sonunda dönüş `BuildAndTrainModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-233">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="ab557-234">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ab557-234">Evaluate the model</span></span>

<span data-ttu-id="ab557-235">Modelinizi eğitildi sonra testinizi kullanın veri modelinin performans doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="ab557-235">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="ab557-236">Oluşturma `Evaluate()` yöntemi hemen sonrasına `BuildAndTrainModel()`, aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="ab557-236">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="ab557-237">`Evaluate()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="ab557-237">The `Evaluate()` method executes the following tasks:</span></span>

    * <span data-ttu-id="ab557-238">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="ab557-238">Loads the test dataset.</span></span>
    * <span data-ttu-id="ab557-239">BinaryClassification değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab557-239">Creates the BinaryClassification evaluator.</span></span>
    * <span data-ttu-id="ab557-240">Model değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab557-240">Evaluates the model and creates metrics.</span></span>
    * <span data-ttu-id="ab557-241">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab557-241">Displays the metrics.</span></span>

2. <span data-ttu-id="ab557-242">Yeni yönteme bir çağrı ekleyin `Main()` yöntemi, sağda altında `BuildAndTrainModel()` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="ab557-242">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="ab557-243">Dönüştürme `splitTestSet` aşağıdakileri ekleyerek veri kod için `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="ab557-243">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="ab557-244">Önceki kod [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) birden çok test veri kümesini girdi satırları sağlanan için tahminde bulunmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ab557-244">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="ab557-245">Sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirme `Evaluate()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-245">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="ab557-246">Ayarlama tahmin aldıktan sonra (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi değerlendirir gerçek tahmin edilen değerlerle karşılaştırır modeli `Labels` test veri kümesini ve döndürür bir [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) modelin nasıl performans gösterdiğini üzerinde nesne.</span><span class="sxs-lookup"><span data-stu-id="ab557-246">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="ab557-247">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ab557-247">Displaying the metrics for model validation</span></span>

<span data-ttu-id="ab557-248">Ölçümleri görüntülemek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="ab557-248">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="ab557-249">`Accuracy` Ölçüm doğru tahminler elde etmek test kümesindeki oranı olan bir model doğruluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="ab557-249">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="ab557-250">`AreaUnderRocCurve` Ölçüm nasıl başarılara model doğru pozitif ve negatif sınıfları sınıflandırma olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab557-250">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="ab557-251">İstediğiniz `AreaUnderRocCurve` biri olarak mümkün olduğunca yakın olmasını.</span><span class="sxs-lookup"><span data-stu-id="ab557-251">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="ab557-252">`F1Score` Ölçüm Bakiye ölçüsüdür modelin F1 puanı alır arasında [duyarlık](../resources/glossary.md#precision) ve [geri çağırma](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="ab557-252">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="ab557-253">İstediğiniz `F1Score` biri olarak mümkün olduğunca yakın olmasını.</span><span class="sxs-lookup"><span data-stu-id="ab557-253">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="ab557-254">Test verileri sonucu tahmin edin</span><span class="sxs-lookup"><span data-stu-id="ab557-254">Predict the test data outcome</span></span>

1. <span data-ttu-id="ab557-255">Oluşturma `UseModelWithSingleItem()` yöntemi hemen sonrasına `Evaluate()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="ab557-255">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="ab557-256">`UseModelWithSingleItem()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="ab557-256">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    * <span data-ttu-id="ab557-257">Test verilerini tek bir yorum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab557-257">Creates a single comment of test data.</span></span>
    * <span data-ttu-id="ab557-258">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="ab557-258">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="ab557-259">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="ab557-259">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="ab557-260">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab557-260">Displays the predicted results.</span></span>

2. <span data-ttu-id="ab557-261">Yeni yönteme bir çağrı ekleyin `Main()` yöntemi, sağda altında `Evaluate()` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="ab557-261">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="ab557-262">ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin `UseModelWithSingleItem()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-262">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="ab557-263">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) geçirin ve ardından verileri tek bir örneğini tahmin gerçekleştirin izin veren bir kolaylık API, bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="ab557-263">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

4. <span data-ttu-id="ab557-264">Eğitilen modelin tahmine test etmek için bir açıklama ekleyin `UseModelWithSingleItem()` bir örneğini oluşturarak yöntemi `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="ab557-264">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="ab557-265">Test açıklaması verileri geçirmek `Prediction Engine` aşağıdaki kodda bir sonraki satırı olarak ekleyerek `UseModelWithSingleItem()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-265">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="ab557-266">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi verilerin tek bir satırda bir tahmin sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab557-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="ab557-267">Görüntü `SentimentText` ve aşağıdaki kodu kullanarak ilgili yaklaşım tahmin:</span><span class="sxs-lookup"><span data-stu-id="ab557-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="ab557-268">Model için tahmin kullanın</span><span class="sxs-lookup"><span data-stu-id="ab557-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="ab557-269">Toplu iş öğeleri tahmin edin ve dağıtın</span><span class="sxs-lookup"><span data-stu-id="ab557-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="ab557-270">Oluşturma `UseModelWithBatchItems()` yöntemi hemen sonrasına `UseModelWithSingleItem()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="ab557-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="ab557-271">`UseModelWithBatchItems()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="ab557-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    * <span data-ttu-id="ab557-272">Toplu test verilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab557-272">Creates batch test data.</span></span>
    * <span data-ttu-id="ab557-273">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="ab557-273">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="ab557-274">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="ab557-274">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="ab557-275">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab557-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="ab557-276">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `UseModelWithSingleItem()` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="ab557-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="ab557-277">Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `UseModelWithBatchItems()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="ab557-278">Açıklama yaklaşım tahmin edin</span><span class="sxs-lookup"><span data-stu-id="ab557-278">Predict comment sentiment</span></span>

<span data-ttu-id="ab557-279">Açıklama veri yaklaşım kullanarak tahmin modelini kullanan [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab557-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="ab557-280">Birleştirme ve Öngörüler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ab557-280">Combine and display the predictions</span></span>

<span data-ttu-id="ab557-281">Aşağıdaki kodu kullanarak tahminler elde etmek için bir başlık oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ab557-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="ab557-282">Çünkü `SentimentPrediction` devralındı `SentimentData`, `Transform()` doldurulmuş yöntemi `SentimentText` tahmin edilen alanlara sahip.</span><span class="sxs-lookup"><span data-stu-id="ab557-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="ab557-283">ML.NET işlemi işlerken, her bileşen sütunları ekler ve bu sonuçları görüntülemek kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="ab557-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="ab557-284">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="ab557-284">Results</span></span>

<span data-ttu-id="ab557-285">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab557-285">Your results should be similar to the following.</span></span> <span data-ttu-id="ab557-286">İşleme sırasında iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ab557-286">During processing, messages are displayed.</span></span> <span data-ttu-id="ab557-287">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab557-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="ab557-288">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ab557-288">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="ab557-289">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="ab557-289">Congratulations!</span></span> <span data-ttu-id="ab557-290">Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="ab557-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="ab557-291">Başarılı modeller oluşturma yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="ab557-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="ab557-292">Bu model düşük ilk kalite hızlı modeli eğitimi sağlamak için öğretici kullanan küçük veri kümeleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab557-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="ab557-293">Model kalitesi memnun değilseniz farklı farklı eğitim algoritmalarıyla seçerek ya da daha büyük bir eğitim veri kümeleri sağlayarak geliştirmek deneyebilirsiniz [hyper-parametreleriyle](../resources/glossary.md##hyperparameter) her bir algoritmanın için.</span><span class="sxs-lookup"><span data-stu-id="ab557-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="ab557-294">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="ab557-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ab557-295">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ab557-295">Next steps</span></span>

<span data-ttu-id="ab557-296">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="ab557-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ab557-297">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab557-297">Create a console application</span></span>
> * <span data-ttu-id="ab557-298">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="ab557-298">Prepare data</span></span>
> * <span data-ttu-id="ab557-299">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="ab557-299">Load the data</span></span>
> * <span data-ttu-id="ab557-300">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="ab557-300">Build and train the model</span></span>
> * <span data-ttu-id="ab557-301">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ab557-301">Evaluate the model</span></span>
> * <span data-ttu-id="ab557-302">Model bir tahminde kullanmak</span><span class="sxs-lookup"><span data-stu-id="ab557-302">Use the model to make a prediction</span></span>
> * <span data-ttu-id="ab557-303">Sonuçları göster</span><span class="sxs-lookup"><span data-stu-id="ab557-303">See the results</span></span>

<span data-ttu-id="ab557-304">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="ab557-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ab557-305">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="ab557-305">Issue Classification</span></span>](github-issue-classification.md)
