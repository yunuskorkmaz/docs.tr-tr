---
title: 'Öğretici: Web sitesi açıklamaları - ikili sınıflandırma analiz edin'
description: Bu öğreticide, elde edilen Web sitesi açıklamaları duyarlılığı sınıflandırır ve uygun tedbiri alır bir .NET Core konsol uygulaması oluşturma işlemini gösterir. İkili yaklaşım sınıflandırıcı kullanan C# Visual Studio 2017'de.
ms.date: 04/18/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 317590e2623dc4962eb83cab696d19363bc0d5eb
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063391"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="c7dc8-104">Öğretici: ML.NET ikili sınıflandırma ile Web sitesi yorumların düşüncelerini çözümleme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="c7dc8-105">Bu öğreticide, elde edilen Web sitesi açıklamaları duyarlılığı sınıflandırır ve uygun tedbiri alır bir .NET Core konsol uygulaması oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="c7dc8-106">İkili yaklaşım sınıflandırıcı kullanan C# Visual Studio 2017'de.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span> 

<span data-ttu-id="c7dc8-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c7dc8-108">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7dc8-108">Create a console application</span></span>
> * <span data-ttu-id="c7dc8-109">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="c7dc8-109">Prepare data</span></span>
> * <span data-ttu-id="c7dc8-110">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-110">Load the data</span></span>
> * <span data-ttu-id="c7dc8-111">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-111">Build and train the model</span></span>
> * <span data-ttu-id="c7dc8-112">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-112">Evaluate the model</span></span>
> * <span data-ttu-id="c7dc8-113">Model bir tahminde kullanmak</span><span class="sxs-lookup"><span data-stu-id="c7dc8-113">Use the model to make a prediction</span></span>
> * <span data-ttu-id="c7dc8-114">Sonuçları göster</span><span class="sxs-lookup"><span data-stu-id="c7dc8-114">See the results</span></span>

<span data-ttu-id="c7dc8-115">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7dc8-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c7dc8-116">Prerequisites</span></span>

* <span data-ttu-id="c7dc8-117">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır</span><span class="sxs-lookup"><span data-stu-id="c7dc8-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed</span></span>

* <span data-ttu-id="c7dc8-118">[UCI yaklaşım cümleler etiketli veri kümesini](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası)</span><span class="sxs-lookup"><span data-stu-id="c7dc8-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="c7dc8-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7dc8-119">Create a console application</span></span>

1. <span data-ttu-id="c7dc8-120">Oluşturma bir **.NET Core konsol uygulaması** "SentimentAnalysis" denir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="c7dc8-121">Adlı bir dizin oluşturmak *veri* , projenizdeki veri kümesi dosyalarınızı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="c7dc8-122">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="c7dc8-123">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="c7dc8-124">Paket kaynağı olarak "nuget.org" seçin ve ardından **Gözat** sekmesi. Arama **Microsoft.ML**, seçin ve ardından paketi **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="c7dc8-125">Kuruluma devam etmek için kabul ederek, seçtiğiniz paket için lisans koşulları.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-125">Proceed with the installation by agreeing to the the license terms for the package you choose.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="c7dc8-126">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="c7dc8-126">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="c7dc8-127">Bu öğretici için veri kümeleri Kotzias 'kaynak grubundan ayrıntılı özelliklerini kullanarak her bir etiketi için' olan et.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-127">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="c7dc8-128">Al.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-128">al,.</span></span> <span data-ttu-id="c7dc8-129">2015 ve barındırılan KDD UCI Machine Learning deposu - Dua, d ve Karra Taniskidou, e (2017).</span><span class="sxs-lookup"><span data-stu-id="c7dc8-129">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="c7dc8-130">UCI Makine deposu [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="c7dc8-130">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="c7dc8-131">Irvine, CA: California Üniversitesi, okul bilgi ve bilgisayar Bilimine.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-131">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="c7dc8-132">İndirme [UCI yaklaşım cümleler etiketli veri kümesini ZIP dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-132">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="c7dc8-133">Kopyalama `yelp_labelled.txt` doyasını *veri* oluşturduğunuz dizin.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-133">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="c7dc8-134">Çözüm Gezgini'nde sağ `yelp_labeled.txt` seçin ve dosya **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-134">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="c7dc8-135">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-135">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="c7dc8-136">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7dc8-136">Create classes and define paths</span></span>

1. <span data-ttu-id="c7dc8-137">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-137">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="c7dc8-138">En son indirilen veri kümesi dosyası yolu ve kayıtlı modeli dosya yolu tutmak için iki genel alanlar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-138">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="c7dc8-139">`_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-139">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="c7dc8-140">`_modelPath` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-140">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="c7dc8-141">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-141">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="c7dc8-142">Ardından, girdi verilerini ve Öngörüler için sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-142">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="c7dc8-143">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-143">Add a new class to your project:</span></span>

    - <span data-ttu-id="c7dc8-144">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-144">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="c7dc8-145">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-145">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="c7dc8-146">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-146">Then, select the **Add** button.</span></span>

    
5. <span data-ttu-id="c7dc8-147">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-147">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="c7dc8-148">Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-148">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="c7dc8-149">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-149">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="c7dc8-150">Verilerin nasıl hazırlanmıştır</span><span class="sxs-lookup"><span data-stu-id="c7dc8-150">How the data was prepared</span></span>
<span data-ttu-id="c7dc8-151">Giriş veri kümesi sınıfı `SentimentData`, sahip bir `string` kullanıcı yorumları için (`SentimentText`) ve bir `bool` (`Sentiment`) değeri 1 (pozitif) veya yaklaşım için 0 (negatif).</span><span class="sxs-lookup"><span data-stu-id="c7dc8-151">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="c7dc8-152">Her iki alanınız [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri bağlı, her bir alanın veri dosyası siparişi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-152">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="c7dc8-153">Ayrıca, `Sentiment` özelliğine sahip bir [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) olarak belirtmek için özniteliği `Label` alan.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-153">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="c7dc8-154">Aşağıdaki örnek dosyası, bir başlık satırı yok ve şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-154">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="c7dc8-155">SentimentText</span><span class="sxs-lookup"><span data-stu-id="c7dc8-155">SentimentText</span></span>                         |<span data-ttu-id="c7dc8-156">Yaklaşım (etiketi)</span><span class="sxs-lookup"><span data-stu-id="c7dc8-156">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="c7dc8-157">Waitress hizmetinde biraz yavaş.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-157">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="c7dc8-158">0</span><span class="sxs-lookup"><span data-stu-id="c7dc8-158">0</span></span>     |
|<span data-ttu-id="c7dc8-159">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-159">Crust is not good.</span></span>                    |    <span data-ttu-id="c7dc8-160">0</span><span class="sxs-lookup"><span data-stu-id="c7dc8-160">0</span></span>     |
|<span data-ttu-id="c7dc8-161">WOW... Burası sevdiği.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-161">Wow... Loved this place.</span></span>              |    <span data-ttu-id="c7dc8-162">1.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-162">1</span></span>     |
|<span data-ttu-id="c7dc8-163">Hizmet çok sor.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-163">Service was very prompt.</span></span>              |    <span data-ttu-id="c7dc8-164">1.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-164">1</span></span>     |

<span data-ttu-id="c7dc8-165">`SentimentPrediction` Tahmin sınıf, model eğitiminin sonra kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-165">`SentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="c7dc8-166">Devraldığı `SentimentData` görüntülemek için `SentimentText` Öngörüler ile.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-166">It inherits from `SentimentData` for displaying the `SentimentText` with the predictions.</span></span> <span data-ttu-id="c7dc8-167">`SentimentPrediction` sahip tek bir Boole değeri (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-167">`SentimentPrediction` has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="c7dc8-168">`Label` Oluşturabilir ve ayrıca bölünmüş test veri kümesini kullanıma ile model değerlendirmek için kullanılan model ya da onun eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-168">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="c7dc8-169">`PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-169">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="c7dc8-170">Değerlendirme, eğitim verileri, tahmin edilen değerleri ve modeli kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-170">For evaluation, training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="c7dc8-171">[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-171">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="c7dc8-172">Başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-172">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="c7dc8-173">Bu, kavramsal olarak, benzer `DBContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-173">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="c7dc8-174">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-174">Load the data</span></span>
<span data-ttu-id="c7dc8-175">ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="c7dc8-175">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="c7dc8-176">`IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-176">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="c7dc8-177">Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-177">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="c7dc8-178">Uygulamayı hazırlama ve ardından veri yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-178">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="c7dc8-179">Değiştirin `Console.WriteLine("Hello World!")` satırına `Main` mlContext değişkeni bildirmek ve başlatmak için aşağıdaki kod ile yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-179">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="c7dc8-180">Sonraki kod satırı olarak ekleyin `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-180">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="c7dc8-181">Oluşturma `LoadData()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-181">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="c7dc8-182">`LoadData()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-182">The `LoadData()` method executes the following tasks:</span></span>

    * <span data-ttu-id="c7dc8-183">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-183">Loads the data.</span></span>
    *  <span data-ttu-id="c7dc8-184">Yüklenen veri kümesi train böler ve test edin, veri kümeleri.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-184">Splits the loaded dataset into train and test datasets.</span></span>
    * <span data-ttu-id="c7dc8-185">Bölme döndürür eğitme ve test etme, veri kümeleri.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-185">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="c7dc8-186">İlk satırı olarak aşağıdaki kodu ekleyin `LoadData()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-186">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="c7dc8-187">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-187">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="c7dc8-188">Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-188">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="c7dc8-189">Eğitim ve test modeli için veri kümesi bölünemiyor</span><span class="sxs-lookup"><span data-stu-id="c7dc8-189">Split the dataset for model training and testing</span></span>

<span data-ttu-id="c7dc8-190">Bir model hazırlarken ve modelin doğruluğunu test etmek için veri kümesinin parçası eğitmek için veri kümesinin parçası kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-190">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>  

1. <span data-ttu-id="c7dc8-191">Yüklenen verilere gerekli veri kümelerine ayırmak için bir sonraki satırda olarak aşağıdaki kodu ekleyin `LoadData()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-191">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="c7dc8-192">Önceki kod [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) train yüklenen veri kümesi bölün ve veri kümeleri sınayabilir ve bunları yöntemi [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-192">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="c7dc8-193">Test verileri ile yüzdesi belirlemek `testFraction`parametresi.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-193">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="c7dc8-194">Varsayılan % 10, bu durumda, % 20 daha fazla veri değerlendirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-194">The default is 10%, in this case you use 20% to evaluate more data.</span></span>  

2. <span data-ttu-id="c7dc8-195">Dönüş `splitDataView` sonunda `LoadData()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-195">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="c7dc8-196">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-196">Build and train the model</span></span>

1. <span data-ttu-id="c7dc8-197">Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-197">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="c7dc8-198">`BuildAndTrainModel()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-198">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    * <span data-ttu-id="c7dc8-199">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-199">Extracts and transforms the data.</span></span>
    * <span data-ttu-id="c7dc8-200">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-200">Trains the model.</span></span>
    * <span data-ttu-id="c7dc8-201">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-201">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="c7dc8-202">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-202">Returns the model.</span></span>

2. <span data-ttu-id="c7dc8-203">Oluşturma `BuildAndTrainModel()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-203">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>
    
    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="c7dc8-204">Verileri dönüştürme ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="c7dc8-204">Extract and transform the data</span></span>

1. <span data-ttu-id="c7dc8-205">Çağrı `FeaturizeText` sonraki kod satırına olarak:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-205">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="c7dc8-206">`FeaturizeText()` Yöntemi önceki kodda, metin sütununu dönüştürür (`SentimentText`) sayısal bir anahtar türü `Features` sütun makine öğrenimi algoritması tarafından kullanılan ve yeni veri kümesi bir sütun olarak ekler:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-206">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="c7dc8-207">SentimentText</span><span class="sxs-lookup"><span data-stu-id="c7dc8-207">SentimentText</span></span>                         |<span data-ttu-id="c7dc8-208">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="c7dc8-208">Sentiment</span></span> |<span data-ttu-id="c7dc8-209">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c7dc8-209">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="c7dc8-210">Waitress hizmetinde biraz yavaş.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-210">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="c7dc8-211">0</span><span class="sxs-lookup"><span data-stu-id="c7dc8-211">0</span></span>     |<span data-ttu-id="c7dc8-212">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="c7dc8-212">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="c7dc8-213">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-213">Crust is not good.</span></span>                    |    <span data-ttu-id="c7dc8-214">0</span><span class="sxs-lookup"><span data-stu-id="c7dc8-214">0</span></span>     |<span data-ttu-id="c7dc8-215">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="c7dc8-215">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="c7dc8-216">WOW... Burası sevdiği.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-216">Wow... Loved this place.</span></span>              |    <span data-ttu-id="c7dc8-217">1.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-217">1</span></span>     |<span data-ttu-id="c7dc8-218">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="c7dc8-218">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="c7dc8-219">Hizmet çok sor.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-219">Service was very prompt.</span></span>              |    <span data-ttu-id="c7dc8-220">1.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-220">1</span></span>     |<span data-ttu-id="c7dc8-221">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="c7dc8-221">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="c7dc8-222">Bir öğrenme algoritması Ekle</span><span class="sxs-lookup"><span data-stu-id="c7dc8-222">Add a learning algorithm</span></span>

<span data-ttu-id="c7dc8-223">Bu uygulama, öğeleri veya veri satırı kategorilere ayıran bir sınıflandırma algoritmasıdır kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-223">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="c7dc8-224">Uygulama Web sitesi açıklamaları artı veya eksi olarak kategorilere ayırır, ikili sınıflandırma görevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-224">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="c7dc8-225">Machine learning görev sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını ekleme `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-225">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

    
[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

    
<span data-ttu-id="c7dc8-226">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) sınıflandırma eğitim algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-226">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="c7dc8-227">Bu eklenen `estimator` ve özellikleri tespit `SentimentText` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-227">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="c7dc8-228">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-228">Train the model</span></span>

<span data-ttu-id="c7dc8-229">Modele uygun `splitTrainSet` veri ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `BuildAndTrainModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-229">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="c7dc8-230">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-230">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="c7dc8-231">Değerlendirme için kullanılacak modeli eğitilir döndürür</span><span class="sxs-lookup"><span data-stu-id="c7dc8-231">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="c7dc8-232">Model sonunda dönüş `BuildAndTrainModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-232">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="c7dc8-233">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-233">Evaluate the model</span></span>

<span data-ttu-id="c7dc8-234">Modelinizi eğitildi sonra testinizi kullanın veri modelinin performans doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-234">After your model is trained, use your test data validate the model's performance.</span></span> 

1. <span data-ttu-id="c7dc8-235">Oluşturma `Evaluate()` yöntemi hemen sonrasına `BuildAndTrainModel()`, aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-235">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="c7dc8-236">`Evaluate()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-236">The `Evaluate()` method executes the following tasks:</span></span>

    * <span data-ttu-id="c7dc8-237">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-237">Loads the test dataset.</span></span>
    * <span data-ttu-id="c7dc8-238">BinaryClassification değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-238">Creates the BinaryClassification evaluator.</span></span>
    * <span data-ttu-id="c7dc8-239">Model değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-239">Evaluates the model and creates metrics.</span></span>
    * <span data-ttu-id="c7dc8-240">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-240">Displays the metrics.</span></span>

2. <span data-ttu-id="c7dc8-241">Yeni yönteme bir çağrı ekleyin `Main()` yöntemi, sağda altında `BuildAndTrainModel()` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-241">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="c7dc8-242">Dönüştürme `splitTestSet` aşağıdakileri ekleyerek veri kod için `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-242">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="c7dc8-243">Önceki kod [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) birden çok test veri kümesini girdi satırları sağlanan için tahminde bulunmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-243">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="c7dc8-244">Sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirme `Evaluate()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-244">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="c7dc8-245">Ayarlama tahmin aldıktan sonra (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi değerlendirir gerçek tahmin edilen değerlerle karşılaştırır modeli `Labels` test veri kümesini ve döndürür bir [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) modelin nasıl performans gösterdiğini üzerinde nesne.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-245">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="c7dc8-246">Model doğrulama için ölçümleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-246">Displaying the metrics for model validation</span></span>

<span data-ttu-id="c7dc8-247">Ölçümleri görüntülemek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-247">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="c7dc8-248">`Accuracy` Ölçüm doğru tahminler elde etmek test kümesindeki oranı olan bir model doğruluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-248">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="c7dc8-249">`AreaUnderRocCurve` Ölçüm nasıl başarılara model doğru pozitif ve negatif sınıfları sınıflandırma olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-249">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="c7dc8-250">İstediğiniz `AreaUnderRocCurve` biri olarak mümkün olduğunca yakın olmasını.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-250">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="c7dc8-251">`F1Score` Ölçüm Bakiye ölçüsüdür modelin F1 puanı alır arasında [duyarlık](../resources/glossary.md#precision) ve [geri çağırma](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="c7dc8-251">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="c7dc8-252">İstediğiniz `F1Score` biri olarak mümkün olduğunca yakın olmasını.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-252">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="c7dc8-253">Test verileri sonucu tahmin edin</span><span class="sxs-lookup"><span data-stu-id="c7dc8-253">Predict the test data outcome</span></span>

1. <span data-ttu-id="c7dc8-254">Oluşturma `UseModelWithSingleItem()` yöntemi hemen sonrasına `Evaluate()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-254">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="c7dc8-255">`UseModelWithSingleItem()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-255">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    * <span data-ttu-id="c7dc8-256">Test verilerini tek bir yorum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-256">Creates a single comment of test data.</span></span>
    * <span data-ttu-id="c7dc8-257">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-257">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="c7dc8-258">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-258">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="c7dc8-259">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-259">Displays the predicted results.</span></span>

2. <span data-ttu-id="c7dc8-260">Yeni yönteme bir çağrı ekleyin `Main()` yöntemi, sağda altında `Evaluate()` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-260">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="c7dc8-261">ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin `Predict()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-261">Add the following code to create as the first line in the `Predict()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="c7dc8-262">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) geçirin ve ardından verileri tek bir örneğini tahmin gerçekleştirin izin veren bir kolaylık API, bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-262">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>
  
4. <span data-ttu-id="c7dc8-263">Eğitilen modelin tahmine test etmek için bir açıklama ekleyin `Predict()` bir örneğini oluşturarak yöntemi `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-263">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="c7dc8-264">Test açıklaması verileri geçirmek `Prediction Engine` aşağıdaki kodda bir sonraki satırı olarak ekleyerek `UseModelWithSingleItem()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-264">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="c7dc8-265">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi verilerin tek bir satırda bir tahmin sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-265">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="c7dc8-266">Görüntü `SentimentText` ve aşağıdaki kodu kullanarak ilgili yaklaşım tahmin:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-266">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="c7dc8-267">Model için tahmin kullanın</span><span class="sxs-lookup"><span data-stu-id="c7dc8-267">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="c7dc8-268">Toplu iş öğeleri tahmin edin ve dağıtın</span><span class="sxs-lookup"><span data-stu-id="c7dc8-268">Deploy and predict batch items</span></span>

1. <span data-ttu-id="c7dc8-269">Oluşturma `UseModelWithBatchItems()` yöntemi hemen sonrasına `UseModelWithSingleItem()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-269">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="c7dc8-270">`UseModelWithBatchItems()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-270">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    * <span data-ttu-id="c7dc8-271">Toplu test verilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-271">Creates batch test data.</span></span>
    * <span data-ttu-id="c7dc8-272">Test verilerine dayalı yaklaşım tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-272">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="c7dc8-273">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-273">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="c7dc8-274">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-274">Displays the predicted results.</span></span>

2. <span data-ttu-id="c7dc8-275">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `UseModelWithSingleItem()` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-275">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="c7dc8-276">Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `UseModelWithBatchItems()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-276">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="c7dc8-277">Açıklama yaklaşım tahmin edin</span><span class="sxs-lookup"><span data-stu-id="c7dc8-277">Predict comment sentiment</span></span>

<span data-ttu-id="c7dc8-278">Açıklama veri yaklaşım kullanarak tahmin modelini kullanan [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-278">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="c7dc8-279">Birleştirme ve Öngörüler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-279">Combine and display the predictions</span></span>

<span data-ttu-id="c7dc8-280">Aşağıdaki kodu kullanarak tahminler elde etmek için bir başlık oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-280">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="c7dc8-281">Çünkü `SentimentPrediction` devralındı `SentimentData`, `Transform()` doldurulmuş yöntemi `SentimentText` tahmin edilen alanlara sahip.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-281">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="c7dc8-282">ML.NET işlemi işlerken, her bileşen sütunları ekler ve bu sonuçları görüntülemek kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-282">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="c7dc8-283">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="c7dc8-283">Results</span></span>

<span data-ttu-id="c7dc8-284">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-284">Your results should be similar to the following.</span></span> <span data-ttu-id="c7dc8-285">İşleme sırasında iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-285">During processing, messages are displayed.</span></span> <span data-ttu-id="c7dc8-286">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-286">You may see warnings, or processing messages.</span></span> <span data-ttu-id="c7dc8-287">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-287">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="c7dc8-288">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="c7dc8-288">Congratulations!</span></span> <span data-ttu-id="c7dc8-289">Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-289">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="c7dc8-290">Başarılı modeller oluşturma yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-290">Building successful models is an iterative process.</span></span> <span data-ttu-id="c7dc8-291">Bu model düşük ilk kalite hızlı modeli eğitimi sağlamak için öğretici kullanan küçük veri kümeleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-291">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="c7dc8-292">Model kalitesi memnun değilseniz farklı farklı eğitim algoritmalarıyla seçerek ya da daha büyük bir eğitim veri kümeleri sağlayarak geliştirmek deneyebilirsiniz [hyper-parametreleriyle](../resources/glossary.md##hyperparameter) her bir algoritmanın için.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-292">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="c7dc8-293">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-293">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c7dc8-294">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c7dc8-294">Next steps</span></span>

<span data-ttu-id="c7dc8-295">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="c7dc8-295">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c7dc8-296">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7dc8-296">Create a console application</span></span>
> * <span data-ttu-id="c7dc8-297">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="c7dc8-297">Prepare data</span></span>
> * <span data-ttu-id="c7dc8-298">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-298">Load the data</span></span>
> * <span data-ttu-id="c7dc8-299">Derleme ve modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-299">Build and train the model</span></span>
> * <span data-ttu-id="c7dc8-300">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c7dc8-300">Evaluate the model</span></span>
> * <span data-ttu-id="c7dc8-301">Model bir tahminde kullanmak</span><span class="sxs-lookup"><span data-stu-id="c7dc8-301">Use the model to make a prediction</span></span>
> * <span data-ttu-id="c7dc8-302">Sonuçları göster</span><span class="sxs-lookup"><span data-stu-id="c7dc8-302">See the results</span></span>

<span data-ttu-id="c7dc8-303">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="c7dc8-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="c7dc8-304">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="c7dc8-304">Issue Classification</span></span>](github-issue-classification.md)
