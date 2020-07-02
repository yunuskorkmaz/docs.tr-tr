---
title: 'Öğretici: Web sitesi açıklamalarını çözümleme-ikili sınıflandırma'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio 'Da C# kullanır.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b193752437c3e84476858bb3b70ba642d8562769
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803254"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="21e7e-104">Öğretici: ML.NET 'de ikili sınıflandırmayla Web sitesi açıklamalarını çözümleyin</span><span class="sxs-lookup"><span data-stu-id="21e7e-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="21e7e-105">Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="21e7e-106">İkili yaklaşım Sınıflandırıcısı, Visual Studio 2017 ' de C# kullanır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="21e7e-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="21e7e-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="21e7e-108">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="21e7e-108">Create a console application</span></span>
> - <span data-ttu-id="21e7e-109">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="21e7e-109">Prepare data</span></span>
> - <span data-ttu-id="21e7e-110">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="21e7e-110">Load the data</span></span>
> - <span data-ttu-id="21e7e-111">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="21e7e-111">Build and train the model</span></span>
> - <span data-ttu-id="21e7e-112">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="21e7e-112">Evaluate the model</span></span>
> - <span data-ttu-id="21e7e-113">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="21e7e-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="21e7e-114">Sonuçları görme</span><span class="sxs-lookup"><span data-stu-id="21e7e-114">See the results</span></span>

<span data-ttu-id="21e7e-115">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e7e-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21e7e-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="21e7e-116">Prerequisites</span></span>

- <span data-ttu-id="21e7e-117">[Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi</span><span class="sxs-lookup"><span data-stu-id="21e7e-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="21e7e-118">[UCI yaklaşım cümleler veri kümesi](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası) etiketli</span><span class="sxs-lookup"><span data-stu-id="21e7e-118">[UCI Sentiment Labeled Sentences dataset](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="21e7e-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="21e7e-119">Create a console application</span></span>

1. <span data-ttu-id="21e7e-120">"SentimentAnalysis" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="21e7e-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="21e7e-121">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="21e7e-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="21e7e-122">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="21e7e-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="21e7e-123">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="21e7e-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="21e7e-124">Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="21e7e-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="21e7e-125">Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin.</span><span class="sxs-lookup"><span data-stu-id="21e7e-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="21e7e-126">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="21e7e-126">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="21e7e-127">Bu öğreticinin veri kümeleri, ' Kimden grubundan, derin özellikler kullanılarak tekil etiketlere, Kotzıas et ' e ait.</span><span class="sxs-lookup"><span data-stu-id="21e7e-127">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="21e7e-128">Al,.</span><span class="sxs-lookup"><span data-stu-id="21e7e-128">al,.</span></span> <span data-ttu-id="21e7e-129">KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="21e7e-129">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="21e7e-130">UCI Machine Learning deposu [ http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="21e7e-130">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="21e7e-131">Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.</span><span class="sxs-lookup"><span data-stu-id="21e7e-131">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="21e7e-132">[Utiment, cümleler veri KÜMESI ZIP dosyası](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve unzip 'i indirin.</span><span class="sxs-lookup"><span data-stu-id="21e7e-132">Download [UCI Sentiment Labeled Sentences dataset ZIP file](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="21e7e-133">`yelp_labelled.txt`Dosyayı oluşturduğunuz *veri* dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="21e7e-133">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="21e7e-134">Çözüm Gezgini, dosyaya sağ tıklayın `yelp_labeled.txt` ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="21e7e-134">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="21e7e-135">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="21e7e-135">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="21e7e-136">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="21e7e-136">Create classes and define paths</span></span>

1. <span data-ttu-id="21e7e-137">Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="21e7e-137">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="21e7e-138">`Main`Son indirilen veri kümesi dosya yolunu tutacak bir alan oluşturmak için aşağıdaki kodu metodun hemen üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="21e7e-138">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="21e7e-139">Ardından, giriş verileriniz ve tahminlerinizi için sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="21e7e-139">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="21e7e-140">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="21e7e-140">Add a new class to your project:</span></span>

    - <span data-ttu-id="21e7e-141">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="21e7e-141">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="21e7e-142">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="21e7e-142">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="21e7e-143">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="21e7e-143">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="21e7e-144">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-144">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="21e7e-145">Aşağıdaki `using` ifadeyi *SentimentData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="21e7e-145">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="21e7e-146">Mevcut sınıf tanımını kaldırın ve iki sınıfa `SentimentData` ve `SentimentPrediction` *SentimentData.cs* dosyasına sahip olan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="21e7e-146">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="21e7e-147">Verilerin nasıl hazırlandığını</span><span class="sxs-lookup"><span data-stu-id="21e7e-147">How the data was prepared</span></span>

<span data-ttu-id="21e7e-148">Giriş veri kümesi sınıfı, `SentimentData` bir `string` for User Comments ( `SentimentText` ) ve bir `bool` ( `Sentiment` ) değeri için 1 (pozitif) ya da 0 (negatif) değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-148">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="21e7e-149">Her iki alana de eklenen [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri vardır ve bu, her alanın veri dosyası sırasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="21e7e-149">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="21e7e-150">Ayrıca, `Sentiment` özelliği alanı olarak belirlemek için bir [sütunadı](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) özniteliği vardır `Label` .</span><span class="sxs-lookup"><span data-stu-id="21e7e-150">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="21e7e-151">Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="21e7e-151">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="21e7e-152">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="21e7e-152">SentimentText</span></span>                         |<span data-ttu-id="21e7e-153">Yaklaşım (etiket)</span><span class="sxs-lookup"><span data-stu-id="21e7e-153">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="21e7e-154">Waitress, hizmette çok yavaş.</span><span class="sxs-lookup"><span data-stu-id="21e7e-154">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="21e7e-155">0</span><span class="sxs-lookup"><span data-stu-id="21e7e-155">0</span></span>     |
|<span data-ttu-id="21e7e-156">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="21e7e-156">Crust is not good.</span></span>                    |    <span data-ttu-id="21e7e-157">0</span><span class="sxs-lookup"><span data-stu-id="21e7e-157">0</span></span>     |
|<span data-ttu-id="21e7e-158">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="21e7e-158">Wow... Loved this place.</span></span>              |    <span data-ttu-id="21e7e-159">1</span><span class="sxs-lookup"><span data-stu-id="21e7e-159">1</span></span>     |
|<span data-ttu-id="21e7e-160">Hizmet çok soriydi.</span><span class="sxs-lookup"><span data-stu-id="21e7e-160">Service was very prompt.</span></span>              |    <span data-ttu-id="21e7e-161">1</span><span class="sxs-lookup"><span data-stu-id="21e7e-161">1</span></span>     |

<span data-ttu-id="21e7e-162">`SentimentPrediction`, model eğitiminden sonra kullanılan tahmin sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-162">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="21e7e-163">`SentimentData`Girişin `SentimentText` Çıkış tahminiyle birlikte görüntülenebilmesini sağlayacak şekilde öğesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-163">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="21e7e-164">`Prediction`Boole değeri, modelin yeni girişle sağlandığı sırada tahmin edilen değerdir `SentimentText` .</span><span class="sxs-lookup"><span data-stu-id="21e7e-164">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="21e7e-165">Çıkış sınıfı, `SentimentPrediction` model tarafından hesaplanan iki diğer özellik içerir: `Score` -model tarafından hesaplanan ham puan ve, `Probability` pozitif yaklaşım olan metnin olasılığına ayarlanmış puan.</span><span class="sxs-lookup"><span data-stu-id="21e7e-165">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="21e7e-166">Bu öğretici için en önemli özellik ' dir `Prediction` .</span><span class="sxs-lookup"><span data-stu-id="21e7e-166">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="21e7e-167">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="21e7e-167">Load the data</span></span>

<span data-ttu-id="21e7e-168">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-168">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="21e7e-169">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="21e7e-169">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="21e7e-170">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-170">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="21e7e-171">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-171">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="21e7e-172">Başlatma `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilecek yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21e7e-172">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="21e7e-173">Entity Framework, kavramsal olarak da benzerdir `DBContext` .</span><span class="sxs-lookup"><span data-stu-id="21e7e-173">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="21e7e-174">Uygulamayı hazırlayın ve sonra verileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="21e7e-174">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="21e7e-175">`Console.WriteLine("Hello World!")` `Main` Mlcontext değişkenini bildirmek ve başlatmak için yöntemindeki satırı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="21e7e-175">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="21e7e-176">Aşağıdaki kod satırını `Main()` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="21e7e-176">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="21e7e-177">`LoadData()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `Main()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-177">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="21e7e-178">`LoadData()`Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="21e7e-178">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="21e7e-179">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="21e7e-179">Loads the data.</span></span>
    - <span data-ttu-id="21e7e-180">Yüklenen veri kümesini tren ve test veri kümelerine böler.</span><span class="sxs-lookup"><span data-stu-id="21e7e-180">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="21e7e-181">Bölünmüş eğitme ve test veri kümelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="21e7e-181">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="21e7e-182">Aşağıdaki kodu yönteminin ilk satırı olarak ekleyin `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-182">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="21e7e-183">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) yöntemi, veri şemasını tanımlar ve dosyada okur.</span><span class="sxs-lookup"><span data-stu-id="21e7e-183">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) method defines the data schema and reads in the file.</span></span> <span data-ttu-id="21e7e-184">Veri yolu değişkenlerini alır ve döndürür `IDataView` .</span><span class="sxs-lookup"><span data-stu-id="21e7e-184">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="21e7e-185">Model eğitimi ve test için veri kümesini bölme</span><span class="sxs-lookup"><span data-stu-id="21e7e-185">Split the dataset for model training and testing</span></span>

<span data-ttu-id="21e7e-186">Bir modeli hazırlarken, modelin doğruluğunu test etmek için veri kümesinin bir kısmını eğitmeniz ve veri kümesinin bir parçası kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="21e7e-186">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="21e7e-187">Yüklenen verileri gereken veri kümelerine bölmek için, aşağıdaki kodu yöntemine bir sonraki satır olarak ekleyin `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-187">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="21e7e-188">Önceki kod, yüklenen veri kümesini eğmek ve test veri kümelerine bölmek ve bunları sınıfında döndürmek için [Traintestsplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) yöntemini kullanır <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> .</span><span class="sxs-lookup"><span data-stu-id="21e7e-188">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> class.</span></span> <span data-ttu-id="21e7e-189">Parametreli veri test kümesi yüzdesini belirtin `testFraction` .</span><span class="sxs-lookup"><span data-stu-id="21e7e-189">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="21e7e-190">Varsayılan değer %10 ' dur, bu durumda daha fazla veri değerlendirmek için %20 kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-190">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="21e7e-191">`splitDataView`Yönteminin sonuna döndürün `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-191">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="21e7e-192">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="21e7e-192">Build and train the model</span></span>

1. <span data-ttu-id="21e7e-193">Yöntemi `BuildAndTrainModel` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin `Main()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-193">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="21e7e-194">`BuildAndTrainModel()`Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="21e7e-194">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="21e7e-195">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="21e7e-195">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="21e7e-196">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="21e7e-196">Trains the model.</span></span>
    - <span data-ttu-id="21e7e-197">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="21e7e-197">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="21e7e-198">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="21e7e-198">Returns the model.</span></span>

2. <span data-ttu-id="21e7e-199">`BuildAndTrainModel()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `Main()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-199">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="21e7e-200">Verileri ayıklama ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="21e7e-200">Extract and transform the data</span></span>

1. <span data-ttu-id="21e7e-201">`FeaturizeText`Sonraki kod satırı olarak çağır:</span><span class="sxs-lookup"><span data-stu-id="21e7e-201">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="21e7e-202">`FeaturizeText()`Önceki koddaki yöntemi, metin sütununu ( `SentimentText` ) `Features` makine öğrenimi algoritması tarafından kullanılan sayısal anahtar türü sütununa dönüştürür ve yeni bir veri kümesi sütunu olarak ekler:</span><span class="sxs-lookup"><span data-stu-id="21e7e-202">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="21e7e-203">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="21e7e-203">SentimentText</span></span>                         |<span data-ttu-id="21e7e-204">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="21e7e-204">Sentiment</span></span> |<span data-ttu-id="21e7e-205">Özellikler</span><span class="sxs-lookup"><span data-stu-id="21e7e-205">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="21e7e-206">Waitress, hizmette çok yavaş.</span><span class="sxs-lookup"><span data-stu-id="21e7e-206">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="21e7e-207">0</span><span class="sxs-lookup"><span data-stu-id="21e7e-207">0</span></span>     |<span data-ttu-id="21e7e-208">[0,76, 0,65, 0,44,...]</span><span class="sxs-lookup"><span data-stu-id="21e7e-208">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="21e7e-209">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="21e7e-209">Crust is not good.</span></span>                    |    <span data-ttu-id="21e7e-210">0</span><span class="sxs-lookup"><span data-stu-id="21e7e-210">0</span></span>     |<span data-ttu-id="21e7e-211">[0,98, 0,43, 0,54,...]</span><span class="sxs-lookup"><span data-stu-id="21e7e-211">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="21e7e-212">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="21e7e-212">Wow... Loved this place.</span></span>              |    <span data-ttu-id="21e7e-213">1</span><span class="sxs-lookup"><span data-stu-id="21e7e-213">1</span></span>     |<span data-ttu-id="21e7e-214">[0,35, 0,73, 0,46,...]</span><span class="sxs-lookup"><span data-stu-id="21e7e-214">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="21e7e-215">Hizmet çok soriydi.</span><span class="sxs-lookup"><span data-stu-id="21e7e-215">Service was very prompt.</span></span>              |    <span data-ttu-id="21e7e-216">1</span><span class="sxs-lookup"><span data-stu-id="21e7e-216">1</span></span>     |<span data-ttu-id="21e7e-217">[0,39, 0, 0,75,...]</span><span class="sxs-lookup"><span data-stu-id="21e7e-217">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="21e7e-218">Öğrenme algoritması ekleme</span><span class="sxs-lookup"><span data-stu-id="21e7e-218">Add a learning algorithm</span></span>

<span data-ttu-id="21e7e-219">Bu uygulama, öğeleri veya veri satırlarını kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-219">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="21e7e-220">Uygulama, Web sitesi açıklamalarını pozitif veya negatif olarak kategorilere ayırır, bu nedenle ikili sınıflandırma görevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="21e7e-220">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="21e7e-221">Aşağıdaki kod satırı olarak aşağıdakini ekleyerek, Machine Learning görevini veri dönüştürme tanımlarına ekleyin `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-221">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="21e7e-222">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) , sınıflandırma eğitim algoritmanız.</span><span class="sxs-lookup"><span data-stu-id="21e7e-222">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="21e7e-223">Bu öğesine eklenir `estimator` ve `SentimentText` `Features` `Label` Geçmiş verilerden bilgi edinmek için uygun () ve giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="21e7e-223">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="21e7e-224">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="21e7e-224">Train the model</span></span>

<span data-ttu-id="21e7e-225">`splitTrainSet`Yöntemine bir sonraki kod satırı olarak aşağıdakileri ekleyerek modeli verilere sığdırın ve eğitilen modeli döndürün `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-225">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="21e7e-226">[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.</span><span class="sxs-lookup"><span data-stu-id="21e7e-226">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="21e7e-227">Değerlendirme için kullanılmak üzere eğitilen modeli döndürün</span><span class="sxs-lookup"><span data-stu-id="21e7e-227">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="21e7e-228">Metodun sonundaki modeli döndürün `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-228">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="21e7e-229">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="21e7e-229">Evaluate the model</span></span>

<span data-ttu-id="21e7e-230">Modelinize eğitim verdikten sonra, test verilerinizi, modelin performansını doğrulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="21e7e-230">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="21e7e-231">`Evaluate()`Aşağıdaki kodla hemen sonra yöntemi oluşturun `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-231">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="21e7e-232">`Evaluate()`Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="21e7e-232">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="21e7e-233">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="21e7e-233">Loads the test dataset.</span></span>
    - <span data-ttu-id="21e7e-234">BinaryClassification Değerlendiricisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21e7e-234">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="21e7e-235">Modeli değerlendirir ve ölçümler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21e7e-235">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="21e7e-236">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="21e7e-236">Displays the metrics.</span></span>

2. <span data-ttu-id="21e7e-237">`Main()`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-237">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="21e7e-238">`splitTestSet`Aşağıdaki kodu öğesine ekleyerek verileri dönüştürün `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-238">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="21e7e-239">Önceki kod, bir test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapmak üzere [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-239">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="21e7e-240">Yöntemine aşağıdaki kod satırı olarak aşağıdakini ekleyerek modeli değerlendirin `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-240">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="21e7e-241">Tahmin kümesine () sahip olduktan sonra, tahmini `predictions` değerleri test veri kümesindeki gerçek ile karşılaştıran ve modelin nasıl çalıştığı hakkında bir CalibratedBinaryClassificationMetrics nesnesi döndüren [değerlendir ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi değerlendirir `Labels` . [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics)</span><span class="sxs-lookup"><span data-stu-id="21e7e-241">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="21e7e-242">Model doğrulama ölçümlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="21e7e-242">Displaying the metrics for model validation</span></span>

<span data-ttu-id="21e7e-243">Ölçümleri göstermek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="21e7e-243">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="21e7e-244">`Accuracy`Ölçüm, test kümesindeki doğru tahminlerden oranı olan bir modelin doğruluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-244">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="21e7e-245">`AreaUnderRocCurve`Ölçüm, modelin pozitif ve negatif sınıfları doğru şekilde sınıflandırarak ne kadar süden emin olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-245">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="21e7e-246">`AreaUnderRocCurve`Bunun mümkün olduğunca yakın olmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="21e7e-246">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="21e7e-247">`F1Score`Ölçüm, [duyarlık](../resources/glossary.md#precision) ve [geri çekme](../resources/glossary.md#recall)arasındaki Bakiyenin ölçüsü olan modelin F1 Puanını alır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-247">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="21e7e-248">`F1Score`Bunun mümkün olduğunca yakın olmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="21e7e-248">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="21e7e-249">Test verilerinin sonucunu tahmin etme</span><span class="sxs-lookup"><span data-stu-id="21e7e-249">Predict the test data outcome</span></span>

1. <span data-ttu-id="21e7e-250">`UseModelWithSingleItem()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-250">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="21e7e-251">`UseModelWithSingleItem()`Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="21e7e-251">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="21e7e-252">Test verileri için tek bir açıklama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21e7e-252">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="21e7e-253">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="21e7e-253">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="21e7e-254">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-254">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="21e7e-255">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="21e7e-255">Displays the predicted results.</span></span>

2. <span data-ttu-id="21e7e-256">`Main()`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-256">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="21e7e-257">Yönteminin ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin `UseModelWithSingleItem()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-257">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="21e7e-258">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-258">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="21e7e-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="21e7e-260">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-260">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="21e7e-261">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="21e7e-261">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="21e7e-262">[ `PredictionEnginePool` ASP.NET Core Web API 'sinde kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="21e7e-262">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="21e7e-263">`PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-263">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="21e7e-264">Bir örneği oluşturarak eğitilen modelin, yöntemi içindeki tahminini test etmek için bir açıklama ekleyin `UseModelWithSingleItem()` `SentimentData` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-264">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="21e7e-265">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)Yöntemine bir sonraki kod satırı olarak aşağıdakileri ekleyerek test açıklama verilerini öğesine geçirin `UseModelWithSingleItem()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-265">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="21e7e-266">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="21e7e-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="21e7e-267">`SentimentText`Aşağıdaki kodu kullanarak ve ilgili yaklaşım tahminini görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="21e7e-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="21e7e-268">Tahmin için modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="21e7e-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="21e7e-269">Toplu iş öğelerini dağıtma ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="21e7e-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="21e7e-270">`UseModelWithBatchItems()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `UseModelWithSingleItem()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="21e7e-271">`UseModelWithBatchItems()`Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="21e7e-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="21e7e-272">Batch test verileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21e7e-272">Creates batch test data.</span></span>
    - <span data-ttu-id="21e7e-273">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="21e7e-273">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="21e7e-274">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-274">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="21e7e-275">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="21e7e-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="21e7e-276">`Main`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `UseModelWithSingleItem()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="21e7e-277">Eğitim modelinin kullanım tahminlerini test etmek için bazı açıklamalar ekleyin `UseModelWithBatchItems()` :</span><span class="sxs-lookup"><span data-stu-id="21e7e-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="21e7e-278">Açıklama yaklaşımını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="21e7e-278">Predict comment sentiment</span></span>

<span data-ttu-id="21e7e-279">[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak açıklama verisi yaklaşımını tahmin etmek için modeli kullanın:</span><span class="sxs-lookup"><span data-stu-id="21e7e-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="21e7e-280">Tahminleri birleştirin ve görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="21e7e-280">Combine and display the predictions</span></span>

<span data-ttu-id="21e7e-281">Aşağıdaki kodu kullanarak tahminler için bir üst bilgi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="21e7e-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="21e7e-282">`SentimentPrediction`Öğesinden devralındığından `SentimentData` , `Transform()` yöntemi tahmin edilen `SentimentText` alanlarla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="21e7e-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="21e7e-283">ML.NET işlem işlemleri sırasında her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="21e7e-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="21e7e-284">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="21e7e-284">Results</span></span>

<span data-ttu-id="21e7e-285">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-285">Your results should be similar to the following.</span></span> <span data-ttu-id="21e7e-286">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-286">During processing, messages are displayed.</span></span> <span data-ttu-id="21e7e-287">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e7e-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="21e7e-288">Bunlar, netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-288">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="21e7e-289">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="21e7e-289">Congratulations!</span></span> <span data-ttu-id="21e7e-290">İleti yaklaşımını sınıflandırma ve tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="21e7e-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="21e7e-291">Başarılı modellerin oluşturulması, yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="21e7e-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="21e7e-292">Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır.</span><span class="sxs-lookup"><span data-stu-id="21e7e-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="21e7e-293">Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı [Hyper-parametreleri](../resources/glossary.md#hyperparameter) ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e7e-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="21e7e-294">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e7e-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="21e7e-295">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="21e7e-295">Next steps</span></span>

<span data-ttu-id="21e7e-296">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="21e7e-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="21e7e-297">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="21e7e-297">Create a console application</span></span>
> - <span data-ttu-id="21e7e-298">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="21e7e-298">Prepare data</span></span>
> - <span data-ttu-id="21e7e-299">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="21e7e-299">Load the data</span></span>
> - <span data-ttu-id="21e7e-300">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="21e7e-300">Build and train the model</span></span>
> - <span data-ttu-id="21e7e-301">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="21e7e-301">Evaluate the model</span></span>
> - <span data-ttu-id="21e7e-302">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="21e7e-302">Use the model to make a prediction</span></span>
> - <span data-ttu-id="21e7e-303">Sonuçları görme</span><span class="sxs-lookup"><span data-stu-id="21e7e-303">See the results</span></span>

<span data-ttu-id="21e7e-304">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="21e7e-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="21e7e-305">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="21e7e-305">Issue Classification</span></span>](github-issue-classification.md)
