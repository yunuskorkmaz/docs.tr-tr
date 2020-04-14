---
title: 'Öğretici: Analiz web sitesi yorumları - ikili sınıflandırma'
description: 'Bu öğretici, web sitesi yorumlarından duyguları sınıflandıran ve uygun eylemi yapan bir .NET Core konsol uygulamasının nasıl oluşturulabileceğinizi gösterir. İkili duygu sınıflandırıcı Visual Studio C # kullanır.'
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6e13cfca93c54648b1a0423c5983013d3e2a1a0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243303"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="930dc-104">Öğretici: ML.NET ikili sınıflandırma ile web sitesi yorumlarının duyarlılığını analiz edin</span><span class="sxs-lookup"><span data-stu-id="930dc-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="930dc-105">Bu öğretici, web sitesi yorumlarından duyguları sınıflandıran ve uygun eylemi yapan bir .NET Core konsol uygulamasının nasıl oluşturulabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="930dc-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="930dc-106">İkili duygu sınıflandırıcısı Visual Studio 2017'de C# kullanır.</span><span class="sxs-lookup"><span data-stu-id="930dc-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="930dc-107">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="930dc-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="930dc-108">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="930dc-108">Create a console application</span></span>
> - <span data-ttu-id="930dc-109">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="930dc-109">Prepare data</span></span>
> - <span data-ttu-id="930dc-110">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="930dc-110">Load the data</span></span>
> - <span data-ttu-id="930dc-111">Modeli oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="930dc-111">Build and train the model</span></span>
> - <span data-ttu-id="930dc-112">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="930dc-112">Evaluate the model</span></span>
> - <span data-ttu-id="930dc-113">Tahminde bulunmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="930dc-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="930dc-114">Sonuçları görme</span><span class="sxs-lookup"><span data-stu-id="930dc-114">See the results</span></span>

<span data-ttu-id="930dc-115">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="930dc-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="930dc-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="930dc-116">Prerequisites</span></span>

- <span data-ttu-id="930dc-117">[Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core çapraz platform geliştirme" iş yükü yüklü</span><span class="sxs-lookup"><span data-stu-id="930dc-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="930dc-118">[UCI Sentiment Etiketli Cümleler dataset](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası)</span><span class="sxs-lookup"><span data-stu-id="930dc-118">[UCI Sentiment Labeled Sentences dataset](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="930dc-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="930dc-119">Create a console application</span></span>

1. <span data-ttu-id="930dc-120">"SentimentAnalysis" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="930dc-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="930dc-121">Veri kümesi dosyalarınızı kaydetmek için projenizde *Veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="930dc-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="930dc-122">Microsoft.ML **NuGet Paketini**Yükleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="930dc-123">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="930dc-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="930dc-124">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin ve ardından **Gözat** sekmesini seçin. **Microsoft.ML**ara, istediğiniz paketi seçin ve sonra **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="930dc-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="930dc-125">Seçtiğiniz paketin lisans koşullarını kabul ederek yüklemeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="930dc-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="930dc-126">**Microsoft.ML.FastTree** NuGet paketi için aynı şeyi yapın.</span><span class="sxs-lookup"><span data-stu-id="930dc-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="930dc-127">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="930dc-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="930dc-128">Bu öğretici için veri kümeleri 'Derin Özellikleri Kullanarak Gruptan Bireysel Etiketlere', Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="930dc-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="930dc-129">al,.</span><span class="sxs-lookup"><span data-stu-id="930dc-129">al,.</span></span> <span data-ttu-id="930dc-130">KDD 2015 ve UCI Machine Learning Deposu - Dua, D. ve Karra Taniskidou, E. (2017) ev sahipliği yaptı.</span><span class="sxs-lookup"><span data-stu-id="930dc-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="930dc-131">UCI Makine Öğrenme Deposuhttp://archive.ics.uci.edu/ml[ ].</span><span class="sxs-lookup"><span data-stu-id="930dc-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="930dc-132">Irvine, CA: Kaliforniya Üniversitesi, Bilgi ve Bilgisayar Bilimleri Fakültesi.</span><span class="sxs-lookup"><span data-stu-id="930dc-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="930dc-133">[INDIR UCI Sentiment Etiketli Cümleler dataset ZIP dosyası](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve unzip.</span><span class="sxs-lookup"><span data-stu-id="930dc-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="930dc-134">Dosyayı `yelp_labelled.txt` oluşturduğunuz *Veri* dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="930dc-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="930dc-135">Çözüm Gezgini'nde dosyayı `yelp_labeled.txt` sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="930dc-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="930dc-136">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="930dc-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="930dc-137">Sınıflar oluşturma ve yolları tanımlama</span><span class="sxs-lookup"><span data-stu-id="930dc-137">Create classes and define paths</span></span>

1. <span data-ttu-id="930dc-138">Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="930dc-139">En son indirilen dataset dosya `Main` yolunu tutmak için bir alan oluşturmak için yöntemin hemen üstündeki satıra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-139">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="930dc-140">Ardından, giriş verileriniz ve öngörüleriniz için sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="930dc-140">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="930dc-141">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-141">Add a new class to your project:</span></span>

    - <span data-ttu-id="930dc-142">**Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="930dc-142">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="930dc-143">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="930dc-143">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="930dc-144">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="930dc-144">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="930dc-145">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="930dc-145">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="930dc-146">SentimentData.cs üstüne `using` aşağıdaki ifadeyi *SentimentData.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-146">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="930dc-147">Varolan sınıf tanımını kaldırın ve iki sınıfı `SentimentData` `SentimentPrediction`ve SentimentData.cs *dosyasına* aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-147">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="930dc-148">Veriler nasıl hazırlandı?</span><span class="sxs-lookup"><span data-stu-id="930dc-148">How the data was prepared</span></span>

<span data-ttu-id="930dc-149">Giriş `SentimentData`veri kümesi sınıfı, kullanıcı `string` yorumları için`SentimentText`bir `bool` (`Sentiment`) ve ( ) değeri 1 (pozitif) veya 0 (negatif) duyarlılık için vardır.</span><span class="sxs-lookup"><span data-stu-id="930dc-149">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="930dc-150">Her iki alanda da, her alanın veri dosyası sırasını açıklayan [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri bunlara eklenir.</span><span class="sxs-lookup"><span data-stu-id="930dc-150">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="930dc-151">Buna ek `Sentiment` olarak, özellik `Label` alan olarak belirlemek için bir [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="930dc-151">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="930dc-152">Aşağıdaki örnek dosyanın üstbilgi satırı yoktur ve aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="930dc-152">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="930dc-153">SentimentText</span><span class="sxs-lookup"><span data-stu-id="930dc-153">SentimentText</span></span>                         |<span data-ttu-id="930dc-154">Duygusallık (Etiket)</span><span class="sxs-lookup"><span data-stu-id="930dc-154">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="930dc-155">Garson biraz yavaş hizmet etti.</span><span class="sxs-lookup"><span data-stu-id="930dc-155">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="930dc-156">0</span><span class="sxs-lookup"><span data-stu-id="930dc-156">0</span></span>     |
|<span data-ttu-id="930dc-157">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="930dc-157">Crust is not good.</span></span>                    |    <span data-ttu-id="930dc-158">0</span><span class="sxs-lookup"><span data-stu-id="930dc-158">0</span></span>     |
|<span data-ttu-id="930dc-159">Wow... Burayı çok severdim.</span><span class="sxs-lookup"><span data-stu-id="930dc-159">Wow... Loved this place.</span></span>              |    <span data-ttu-id="930dc-160">1</span><span class="sxs-lookup"><span data-stu-id="930dc-160">1</span></span>     |
|<span data-ttu-id="930dc-161">Servis çok hızlı oldu.</span><span class="sxs-lookup"><span data-stu-id="930dc-161">Service was very prompt.</span></span>              |    <span data-ttu-id="930dc-162">1</span><span class="sxs-lookup"><span data-stu-id="930dc-162">1</span></span>     |

<span data-ttu-id="930dc-163">`SentimentPrediction`model eğitiminden sonra kullanılan tahmin sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="930dc-163">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="930dc-164">Girişin çıktı `SentimentData` tahminiyle birlikte `SentimentText` görüntülenebilmeleri için bu gelirden devralır.</span><span class="sxs-lookup"><span data-stu-id="930dc-164">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="930dc-165">Boolean, `Prediction` modelin yeni girdiyle `SentimentText`birlikte verildiğinde öngördüğü değerdir.</span><span class="sxs-lookup"><span data-stu-id="930dc-165">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="930dc-166">Çıktı sınıfı `SentimentPrediction` model tarafından hesaplanan iki `Score` başka özellik içerir: - model `Probability` tarafından hesaplanan ham puan ve - pozitif duyarlılığa sahip metnin olasılığına kalibre edilen puan.</span><span class="sxs-lookup"><span data-stu-id="930dc-166">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="930dc-167">Bu öğretici için, en `Prediction`önemli özelliği .</span><span class="sxs-lookup"><span data-stu-id="930dc-167">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="930dc-168">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="930dc-168">Load the data</span></span>

<span data-ttu-id="930dc-169">ML.NET'daki veriler [IDataView sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="930dc-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="930dc-170">`IDataView`tabular verileri (sayısal ve metin) tanımlamanın esnek ve etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="930dc-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="930dc-171">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı `IDataView` veya günlük dosyaları) bir nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="930dc-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="930dc-172">[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="930dc-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="930dc-173">İlk `mlContext` başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="930dc-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="930dc-174">Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.</span><span class="sxs-lookup"><span data-stu-id="930dc-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="930dc-175">Uygulamayı hazırlarsınız ve verileri yüklersiniz:</span><span class="sxs-lookup"><span data-stu-id="930dc-175">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="930dc-176">MlContext `Console.WriteLine("Hello World!")` değişkenini `Main` bildirmek ve başlatmak için yöntemdeki satırı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="930dc-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="930dc-177">`Main()` Yöntemde bir sonraki kod satırı olarak aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-177">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="930dc-178">Yöntemden `LoadData()` `Main()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="930dc-178">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="930dc-179">Yöntem `LoadData()` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="930dc-179">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="930dc-180">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="930dc-180">Loads the data.</span></span>
    - <span data-ttu-id="930dc-181">Yüklenen veri kümesini tren ve test veri kümelerine böler.</span><span class="sxs-lookup"><span data-stu-id="930dc-181">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="930dc-182">Bölünmüş tren ve test veri kümelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="930dc-182">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="930dc-183">`LoadData()` Yöntemin ilk satırı olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-183">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="930dc-184">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) yöntemi veri şemasını tanımlar ve dosyada okur.</span><span class="sxs-lookup"><span data-stu-id="930dc-184">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) method defines the data schema and reads in the file.</span></span> <span data-ttu-id="930dc-185">Veri yolu değişkenlerini alır ve `IDataView`bir .</span><span class="sxs-lookup"><span data-stu-id="930dc-185">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="930dc-186">Model eğitimi ve testi için veri kümesini bölme</span><span class="sxs-lookup"><span data-stu-id="930dc-186">Split the dataset for model training and testing</span></span>

<span data-ttu-id="930dc-187">Bir model hazırlarken, onu eğitmek için veri kümesinin bir kısmını ve modelin doğruluğunu test etmek için veri kümesinin bir kısmını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="930dc-187">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="930dc-188">Yüklenen verileri gerekli veri kümelerine bölmek için `LoadData()` yöntemde bir sonraki satır olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-188">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="930dc-189">Önceki kod, yüklenen veri kümesini trene bölmek ve veri kümelerini test etmek <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> ve bunları sınıfta döndürmek için [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="930dc-189">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> class.</span></span> <span data-ttu-id="930dc-190">Parametreile verilerin test kümesi `testFraction`yüzdesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="930dc-190">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="930dc-191">Varsayılan değer %10'dur, bu durumda daha fazla veriyi değerlendirmek için %20'dir.</span><span class="sxs-lookup"><span data-stu-id="930dc-191">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="930dc-192">Yöntemin sonunda ki döndürme: `splitDataView` `LoadData()`</span><span class="sxs-lookup"><span data-stu-id="930dc-192">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="930dc-193">Modeli oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="930dc-193">Build and train the model</span></span>

1. <span data-ttu-id="930dc-194">Yöntemde `BuildAndTrainModel`bir sonraki kod satırı olarak yönteme `Main()` aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-194">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="930dc-195">Yöntem `BuildAndTrainModel()` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="930dc-195">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="930dc-196">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="930dc-196">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="930dc-197">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="930dc-197">Trains the model.</span></span>
    - <span data-ttu-id="930dc-198">Test verilerine dayalı duyarlılığı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="930dc-198">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="930dc-199">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="930dc-199">Returns the model.</span></span>

2. <span data-ttu-id="930dc-200">Yöntemden `BuildAndTrainModel()` `Main()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="930dc-200">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="930dc-201">Verileri ayıklayın ve dönüştürün</span><span class="sxs-lookup"><span data-stu-id="930dc-201">Extract and transform the data</span></span>

1. <span data-ttu-id="930dc-202">Bir `FeaturizeText` sonraki kod satırı olarak arayın:</span><span class="sxs-lookup"><span data-stu-id="930dc-202">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="930dc-203">Önceki `FeaturizeText()` koddaki yöntem metin sütununa`SentimentText`( ) makine öğrenme `Features` algoritması tarafından kullanılan sayısal anahtar türü sütununa dönüştürür ve yeni bir veri kümesi sütunu olarak ekler:</span><span class="sxs-lookup"><span data-stu-id="930dc-203">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="930dc-204">SentimentText</span><span class="sxs-lookup"><span data-stu-id="930dc-204">SentimentText</span></span>                         |<span data-ttu-id="930dc-205">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="930dc-205">Sentiment</span></span> |<span data-ttu-id="930dc-206">Özellikler</span><span class="sxs-lookup"><span data-stu-id="930dc-206">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="930dc-207">Garson biraz yavaş hizmet etti.</span><span class="sxs-lookup"><span data-stu-id="930dc-207">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="930dc-208">0</span><span class="sxs-lookup"><span data-stu-id="930dc-208">0</span></span>     |<span data-ttu-id="930dc-209">[0.76, 0.65, 0.44, ...]</span><span class="sxs-lookup"><span data-stu-id="930dc-209">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="930dc-210">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="930dc-210">Crust is not good.</span></span>                    |    <span data-ttu-id="930dc-211">0</span><span class="sxs-lookup"><span data-stu-id="930dc-211">0</span></span>     |<span data-ttu-id="930dc-212">[0.98, 0.43, 0.54, ...]</span><span class="sxs-lookup"><span data-stu-id="930dc-212">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="930dc-213">Wow... Burayı çok severdim.</span><span class="sxs-lookup"><span data-stu-id="930dc-213">Wow... Loved this place.</span></span>              |    <span data-ttu-id="930dc-214">1</span><span class="sxs-lookup"><span data-stu-id="930dc-214">1</span></span>     |<span data-ttu-id="930dc-215">[0.35, 0.73, 0.46, ...]</span><span class="sxs-lookup"><span data-stu-id="930dc-215">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="930dc-216">Servis çok hızlı oldu.</span><span class="sxs-lookup"><span data-stu-id="930dc-216">Service was very prompt.</span></span>              |    <span data-ttu-id="930dc-217">1</span><span class="sxs-lookup"><span data-stu-id="930dc-217">1</span></span>     |<span data-ttu-id="930dc-218">[0.39, 0, 0.75, ...]</span><span class="sxs-lookup"><span data-stu-id="930dc-218">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="930dc-219">Öğrenme algoritması ekleme</span><span class="sxs-lookup"><span data-stu-id="930dc-219">Add a learning algorithm</span></span>

<span data-ttu-id="930dc-220">Bu uygulama, öğeleri veya veri satırlarını kategorilere ayıran bir sınıflandırma algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="930dc-220">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="930dc-221">Uygulama web sitesi yorumlarını olumlu veya olumsuz olarak kategorilere ayırır, bu nedenle ikili sınıflandırma görevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="930dc-221">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="930dc-222">Bir sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarına makine `BuildAndTrainModel()`öğrenimi görevini ekleme:</span><span class="sxs-lookup"><span data-stu-id="930dc-222">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="930dc-223">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) sınıflandırma eğitim algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="930dc-223">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="930dc-224">Bu, `estimator` geçmiş verilerden öğrenmek için featurized `SentimentText` ( `Label` `Features`) ve giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="930dc-224">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="930dc-225">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="930dc-225">Train the model</span></span>

<span data-ttu-id="930dc-226">Modeli `splitTrainSet` verilere sığdırın ve yöntemde bir sonraki kod satırı olarak `BuildAndTrainModel()` aşağıdakileri ekleyerek eğitilmiş modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="930dc-226">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="930dc-227">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="930dc-227">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="930dc-228">Değerlendirme için kullanılmak üzere eğitilmiş modeli döndürme</span><span class="sxs-lookup"><span data-stu-id="930dc-228">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="930dc-229">Yöntemin sonunda modeli döndürün: `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="930dc-229">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="930dc-230">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="930dc-230">Evaluate the model</span></span>

<span data-ttu-id="930dc-231">Modeliniz eğitildikten sonra, test verilerinizi modelin performansını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="930dc-231">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="930dc-232">`Evaluate()` Yöntemi aşağıdaki kodla `BuildAndTrainModel()`hemen sonra oluşturun:</span><span class="sxs-lookup"><span data-stu-id="930dc-232">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="930dc-233">Yöntem `Evaluate()` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="930dc-233">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="930dc-234">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="930dc-234">Loads the test dataset.</span></span>
    - <span data-ttu-id="930dc-235">İkili Sınıflandırma değerlendiricisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="930dc-235">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="930dc-236">Modeli değerlendirir ve ölçümler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="930dc-236">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="930dc-237">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="930dc-237">Displays the metrics.</span></span>

2. <span data-ttu-id="930dc-238">Aşağıdaki kodu `Main()` kullanarak, yöntem çağrısının `BuildAndTrainModel()` hemen altında, yöntemden yeni yönteme çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-238">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="930dc-239">Aşağıdaki `splitTestSet` kodu ekleyerek verileri dönüştürün: `Evaluate()`</span><span class="sxs-lookup"><span data-stu-id="930dc-239">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="930dc-240">Önceki kod, bir test veri kümesinin birden çok sağlanan giriş satırları için öngörüler yapmak için [Dönüştür()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="930dc-240">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="930dc-241">Yöntemde bir sonraki kod satırı olarak aşağıdakileri `Evaluate()` ekleyerek modeli değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="930dc-241">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="930dc-242">Tahmin kümesine sahip`predictions`olduktan sonra (), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi, öngörülen değerleri test veri `Labels` kümesindeki gerçek değerlerle karşılaştıran ve modelin nasıl performans gösterdiğine ilişkin [kalibreli BirLeştirilmişBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) nesnesini döndüren modeli değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="930dc-242">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="930dc-243">Model doğrulama için ölçümlerin görüntülenmesi</span><span class="sxs-lookup"><span data-stu-id="930dc-243">Displaying the metrics for model validation</span></span>

<span data-ttu-id="930dc-244">Ölçümleri görüntülemek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="930dc-244">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="930dc-245">`Accuracy` Metrik, test kümesindeki doğru tahminlerin oranı olan bir modelin doğruluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="930dc-245">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="930dc-246">Metrik, `AreaUnderRocCurve` modelin pozitif ve negatif sınıfları doğru bir şekilde sınıflandıracağından ne kadar emin olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="930dc-246">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="930dc-247">Mümkün olduğunca `AreaUnderRocCurve` birine yakın olmasını istiyorsun.</span><span class="sxs-lookup"><span data-stu-id="930dc-247">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="930dc-248">`F1Score` Metrik, [modelin](../resources/glossary.md#precision) F1 puanını alır, bu da hassasiyet ve [geri çağırma](../resources/glossary.md#recall)arasındaki dengenin bir ölçüsüdür.</span><span class="sxs-lookup"><span data-stu-id="930dc-248">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="930dc-249">Mümkün olduğunca `F1Score` birine yakın olmasını istiyorsun.</span><span class="sxs-lookup"><span data-stu-id="930dc-249">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="930dc-250">Test verisi sonucunu tahmin etme</span><span class="sxs-lookup"><span data-stu-id="930dc-250">Predict the test data outcome</span></span>

1. <span data-ttu-id="930dc-251">Yöntemden `UseModelWithSingleItem()` `Evaluate()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="930dc-251">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="930dc-252">Yöntem `UseModelWithSingleItem()` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="930dc-252">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="930dc-253">Test verilerinin tek bir yorumunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="930dc-253">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="930dc-254">Test verilerine dayalı duyarlılığı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="930dc-254">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="930dc-255">Raporlama için test verilerini ve öngörüleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="930dc-255">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="930dc-256">Öngörülen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="930dc-256">Displays the predicted results.</span></span>

2. <span data-ttu-id="930dc-257">Aşağıdaki kodu `Main()` kullanarak, yöntem çağrısının `Evaluate()` hemen altında, yöntemden yeni yönteme çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-257">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="930dc-258">`UseModelWithSingleItem()` Yöntem'de ilk satır olarak oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-258">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="930dc-259">[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir.</span><span class="sxs-lookup"><span data-stu-id="930dc-259">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="930dc-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="930dc-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="930dc-261">Tek dişli veya prototip ortamlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="930dc-261">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="930dc-262">Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın.</span><span class="sxs-lookup"><span data-stu-id="930dc-262">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="930dc-263">ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="930dc-263">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="930dc-264">`PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="930dc-264">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="930dc-265">Bir örnek oluşturarak `UseModelWithSingleItem()` yöntemde eğitimli modelin tahminsına test `SentimentData`etmek için bir açıklama ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-265">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="930dc-266">Yöntemde bir sonraki [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) kod satırı olarak aşağıdakileri ekleyerek test `UseModelWithSingleItem()` yorum verilerini geçirin:</span><span class="sxs-lookup"><span data-stu-id="930dc-266">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="930dc-267">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="930dc-267">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="930dc-268">Aşağıdaki `SentimentText` kodu kullanarak görüntülenmesi ve buna karşılık gelen duyarlılık tahmini:</span><span class="sxs-lookup"><span data-stu-id="930dc-268">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="930dc-269">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="930dc-269">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="930dc-270">Toplu iş öğelerini dağıtma ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="930dc-270">Deploy and predict batch items</span></span>

1. <span data-ttu-id="930dc-271">Yöntemden `UseModelWithBatchItems()` `UseModelWithSingleItem()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="930dc-271">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="930dc-272">Yöntem `UseModelWithBatchItems()` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="930dc-272">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="930dc-273">Toplu test verileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="930dc-273">Creates batch test data.</span></span>
    - <span data-ttu-id="930dc-274">Test verilerine dayalı duyarlılığı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="930dc-274">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="930dc-275">Raporlama için test verilerini ve öngörüleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="930dc-275">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="930dc-276">Öngörülen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="930dc-276">Displays the predicted results.</span></span>

2. <span data-ttu-id="930dc-277">Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `UseModelWithSingleItem()` hemen altında, yöntemden yeni yönteme çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-277">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="930dc-278">`UseModelWithBatchItems()` Yöntemde eğitimli modelin öngörülerini sınamak için bazı açıklamalar ekleyin:</span><span class="sxs-lookup"><span data-stu-id="930dc-278">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="930dc-279">Yorum duyarlılığını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="930dc-279">Predict comment sentiment</span></span>

<span data-ttu-id="930dc-280">[Dönüştür()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak yorum veri duyarlılığını tahmin etmek için modeli kullanın:</span><span class="sxs-lookup"><span data-stu-id="930dc-280">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="930dc-281">Tahminleri birleştirin ve görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="930dc-281">Combine and display the predictions</span></span>

<span data-ttu-id="930dc-282">Aşağıdaki kodu kullanarak öngörüler için bir üstbilgi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="930dc-282">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="930dc-283">Çünkü, `SentimentPrediction` `SentimentData` `Transform()` tahmin edilen alanları ile `SentimentText` doldurulan yöntem devralır.</span><span class="sxs-lookup"><span data-stu-id="930dc-283">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="930dc-284">ML.NET işlem işlendikçe, her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="930dc-284">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="930dc-285">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="930dc-285">Results</span></span>

<span data-ttu-id="930dc-286">Sonuçlarınız aşağıdakilere benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="930dc-286">Your results should be similar to the following.</span></span> <span data-ttu-id="930dc-287">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="930dc-287">During processing, messages are displayed.</span></span> <span data-ttu-id="930dc-288">Uyarılar veya iletileri işleme görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="930dc-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="930dc-289">Bunlar netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="930dc-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="930dc-290">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="930dc-290">Congratulations!</span></span> <span data-ttu-id="930dc-291">İletilerin duyarlılığını sınıflandırmak ve tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturmuşsunuz.</span><span class="sxs-lookup"><span data-stu-id="930dc-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="930dc-292">Başarılı modeller oluşturmak yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="930dc-292">Building successful models is an iterative process.</span></span> <span data-ttu-id="930dc-293">Öğretici hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu model in ilk düşük kaliteye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="930dc-293">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="930dc-294">Model kalitesinden memnun değilseniz, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı [hiper parametrelere](../resources/glossary.md#hyperparameter) sahip farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="930dc-294">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="930dc-295">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="930dc-295">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="930dc-296">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="930dc-296">Next steps</span></span>

<span data-ttu-id="930dc-297">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="930dc-297">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="930dc-298">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="930dc-298">Create a console application</span></span>
> - <span data-ttu-id="930dc-299">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="930dc-299">Prepare data</span></span>
> - <span data-ttu-id="930dc-300">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="930dc-300">Load the data</span></span>
> - <span data-ttu-id="930dc-301">Modeli oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="930dc-301">Build and train the model</span></span>
> - <span data-ttu-id="930dc-302">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="930dc-302">Evaluate the model</span></span>
> - <span data-ttu-id="930dc-303">Tahminde bulunmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="930dc-303">Use the model to make a prediction</span></span>
> - <span data-ttu-id="930dc-304">Sonuçları görme</span><span class="sxs-lookup"><span data-stu-id="930dc-304">See the results</span></span>

<span data-ttu-id="930dc-305">Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="930dc-305">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="930dc-306">Konu Sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="930dc-306">Issue Classification</span></span>](github-issue-classification.md)
