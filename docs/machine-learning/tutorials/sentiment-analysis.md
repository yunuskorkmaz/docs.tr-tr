---
title: 'Öğretici: Web sitesi açıklamalarını çözümle-ikili sınıflandırma'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 'da kullanır.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 4daa7734f12c57a177fab3c62fdd96bda22838af
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107173"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="d6dc3-104">Öğretici: ML.NET içinde ikili sınıflandırmayla Web sitesi açıklamalarının yaklaşımını çözümleyin</span><span class="sxs-lookup"><span data-stu-id="d6dc3-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="d6dc3-105">Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="d6dc3-106">İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 2017 ' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="d6dc3-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="d6dc3-108">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6dc3-108">Create a console application</span></span>
> - <span data-ttu-id="d6dc3-109">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="d6dc3-109">Prepare data</span></span>
> - <span data-ttu-id="d6dc3-110">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-110">Load the data</span></span>
> - <span data-ttu-id="d6dc3-111">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-111">Build and train the model</span></span>
> - <span data-ttu-id="d6dc3-112">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-112">Evaluate the model</span></span>
> - <span data-ttu-id="d6dc3-113">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="d6dc3-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="d6dc3-114">Sonuçlara bakın</span><span class="sxs-lookup"><span data-stu-id="d6dc3-114">See the results</span></span>

<span data-ttu-id="d6dc3-115">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d6dc3-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d6dc3-116">Prerequisites</span></span>

- <span data-ttu-id="d6dc3-117">".NET Core platformlar arası geliştirme" iş yükü yüklüyken [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)</span><span class="sxs-lookup"><span data-stu-id="d6dc3-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="d6dc3-118">[Ustaklama tümce veri kümesi etiketli](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası)</span><span class="sxs-lookup"><span data-stu-id="d6dc3-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="d6dc3-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6dc3-119">Create a console application</span></span>

1. <span data-ttu-id="d6dc3-120">"SentimentAnalysis" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="d6dc3-121">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="d6dc3-122">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="d6dc3-123">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d6dc3-124">Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve ardından **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="d6dc3-125">Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="d6dc3-126">**Microsoft. ml. FastTree** NuGet paketi için de aynısını yapın.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="d6dc3-127">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="d6dc3-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="d6dc3-128">Bu öğreticinin veri kümeleri, ' Kimden grubundan, derin özellikler kullanılarak tekil etiketlere, Kotzıas et ' e ait.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="d6dc3-129">Al,.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-129">al,.</span></span> <span data-ttu-id="d6dc3-130">KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="d6dc3-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="d6dc3-131">UCI Machine Learning deposu [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="d6dc3-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="d6dc3-132">Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="d6dc3-133">[Utiment, cümleler veri KÜMESI ZIP dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve unzip 'i indirin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="d6dc3-134">Dosyayı oluşturduğunuz veri dizinine kopyalayın. `yelp_labelled.txt`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="d6dc3-135">Çözüm Gezgini, `yelp_labeled.txt` dosyaya sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="d6dc3-136">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="d6dc3-137">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="d6dc3-137">Create classes and define paths</span></span>

1. <span data-ttu-id="d6dc3-138">Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="d6dc3-139">Son indirilen veri kümesi dosya yolunu ve kaydedilen model dosyası yolunu tutmak için iki genel alan oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    - <span data-ttu-id="d6dc3-140">`_dataPath`, modeli eğitmek için kullanılan veri kümesinin yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    - <span data-ttu-id="d6dc3-141">`_modelPath`Eğitim modelinin kaydedildiği yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="d6dc3-142">Yolları belirtmek için aşağıdaki kodu `Main` metodun hemen üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="d6dc3-143">Ardından, giriş verileriniz ve tahminlerinizi için sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="d6dc3-144">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="d6dc3-145">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="d6dc3-146">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="d6dc3-147">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="d6dc3-148">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="d6dc3-149">Aşağıdaki `using` ifadeyi *SentimentData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="d6dc3-150">Mevcut sınıf tanımını kaldırın ve iki sınıfa `SentimentData` ve `SentimentPrediction`SentimentData.cs dosyasına sahip olan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="d6dc3-151">Verilerin nasıl hazırlandığını</span><span class="sxs-lookup"><span data-stu-id="d6dc3-151">How the data was prepared</span></span>
<span data-ttu-id="d6dc3-152">`SentimentData`Giriş veri kümesi sınıfı, bir `string` for User Comments (`SentimentText`) ve bir `bool` (`Sentiment`) değeri için 1 (pozitif) ya da 0 (negatif) değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="d6dc3-153">Her iki alana de eklenen [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri vardır ve bu, her alanın veri dosyası sırasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="d6dc3-154">Ayrıca, `Sentiment` özelliği `Label` alanı olarak belirlemek için bir [sütunadı](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="d6dc3-155">Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="d6dc3-156">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="d6dc3-156">SentimentText</span></span>                         |<span data-ttu-id="d6dc3-157">Yaklaşım (etiket)</span><span class="sxs-lookup"><span data-stu-id="d6dc3-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="d6dc3-158">Waitress, hizmette çok yavaş.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="d6dc3-159">0</span><span class="sxs-lookup"><span data-stu-id="d6dc3-159">0</span></span>     |
|<span data-ttu-id="d6dc3-160">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-160">Crust is not good.</span></span>                    |    <span data-ttu-id="d6dc3-161">0</span><span class="sxs-lookup"><span data-stu-id="d6dc3-161">0</span></span>     |
|<span data-ttu-id="d6dc3-162">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="d6dc3-163">1\.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-163">1</span></span>     |
|<span data-ttu-id="d6dc3-164">Hizmet çok soriydi.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-164">Service was very prompt.</span></span>              |    <span data-ttu-id="d6dc3-165">1\.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-165">1</span></span>     |

<span data-ttu-id="d6dc3-166">`SentimentPrediction`, model eğitiminden sonra kullanılan tahmin sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-166">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="d6dc3-167">`SentimentData` Girişin`SentimentText` çıkış tahminiyle birlikte görüntülenebilmesini sağlayacak şekilde öğesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-167">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="d6dc3-168">Boole değeri, modelin yeni girişle `SentimentText`sağlandığı sırada tahmin edilen değerdir. `Prediction`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-168">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="d6dc3-169">Çıkış sınıfı `SentimentPrediction` , model tarafından hesaplanan iki diğer özellik içerir: `Score` -model tarafından hesaplanan ham puan ve `Probability` , pozitif yaklaşım olan metnin olasılığına ayarlanmış puan.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-169">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="d6dc3-170">Bu öğretici için en önemli özellik ' dir `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-170">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="d6dc3-171">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-171">Load the data</span></span>
<span data-ttu-id="d6dc3-172">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-172">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="d6dc3-173">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-173">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="d6dc3-174">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-174">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="d6dc3-175">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-175">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="d6dc3-176">Başlatma `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilecek yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-176">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="d6dc3-177">Entity Framework, kavramsal `DBContext` olarak da benzerdir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-177">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="d6dc3-178">Uygulamayı hazırlayın ve sonra verileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-178">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="d6dc3-179">Mlcontext değişkenini bildirmek ve `Main` başlatmak için yöntemindeki satırıaşağıdakikodladeğiştirin:`Console.WriteLine("Hello World!")`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-179">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="d6dc3-180">Aşağıdaki kod `Main()` satırını yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-180">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="d6dc3-181">Aşağıdaki kodu kullanarak yönteminden hemen `Main()` sonra yönteminioluşturun:`LoadData()`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-181">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="d6dc3-182">`LoadData()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-182">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="d6dc3-183">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-183">Loads the data.</span></span>
    - <span data-ttu-id="d6dc3-184">Yüklenen veri kümesini tren ve test veri kümelerine böler.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-184">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="d6dc3-185">Bölünmüş eğitme ve test veri kümelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-185">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="d6dc3-186">Aşağıdaki kodu `LoadData()` yönteminin ilk satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-186">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="d6dc3-187">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-187">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="d6dc3-188">Veri yolu değişkenlerini alır ve döndürür `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-188">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="d6dc3-189">Model eğitimi ve test için veri kümesini bölme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-189">Split the dataset for model training and testing</span></span>

<span data-ttu-id="d6dc3-190">Bir modeli hazırlarken, modelin doğruluğunu test etmek için veri kümesinin bir kısmını eğitmeniz ve veri kümesinin bir parçası kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-190">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="d6dc3-191">Yüklenen verileri gereken veri kümelerine bölmek için, aşağıdaki kodu `LoadData()` yöntemine bir sonraki satır olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-191">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="d6dc3-192">Önceki kod, yüklenen veri kümesini eğmek ve test veri kümelerine bölmek için [Traintestsplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) yöntemini kullanır ve onları [Traintestdata](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfında döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-192">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="d6dc3-193">`testFraction`Parametreli veri test kümesi yüzdesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-193">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="d6dc3-194">Varsayılan değer% 10 ' dur, bu durumda daha fazla veri değerlendirmek için% 20 kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-194">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="d6dc3-195">Yöntemininsonuna`LoadData()`döndürün: `splitDataView`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-195">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="d6dc3-196">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-196">Build and train the model</span></span>

1. <span data-ttu-id="d6dc3-197">`BuildAndTrainModel` Yöntemi`Main()` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-197">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="d6dc3-198">`BuildAndTrainModel()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-198">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="d6dc3-199">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-199">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="d6dc3-200">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-200">Trains the model.</span></span>
    - <span data-ttu-id="d6dc3-201">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-201">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="d6dc3-202">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-202">Returns the model.</span></span>

2. <span data-ttu-id="d6dc3-203">Aşağıdaki kodu kullanarak yönteminden hemen `Main()` sonra yönteminioluşturun:`BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-203">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="d6dc3-204">Verileri ayıklama ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-204">Extract and transform the data</span></span>

1. <span data-ttu-id="d6dc3-205">Sonraki `FeaturizeText` kod satırı olarak çağır:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-205">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="d6dc3-206">Önceki koddaki`SentimentText` `Features`yöntemi, metin sütununu () makine öğrenimi algoritması tarafından kullanılan sayısal anahtar türü sütununa dönüştürür ve yeni bir veri kümesi sütunu olarak ekler: `FeaturizeText()`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-206">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="d6dc3-207">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="d6dc3-207">SentimentText</span></span>                         |<span data-ttu-id="d6dc3-208">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="d6dc3-208">Sentiment</span></span> |<span data-ttu-id="d6dc3-209">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d6dc3-209">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="d6dc3-210">Waitress, hizmette çok yavaş.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-210">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="d6dc3-211">0</span><span class="sxs-lookup"><span data-stu-id="d6dc3-211">0</span></span>     |<span data-ttu-id="d6dc3-212">[0,76, 0,65, 0,44,...]</span><span class="sxs-lookup"><span data-stu-id="d6dc3-212">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="d6dc3-213">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-213">Crust is not good.</span></span>                    |    <span data-ttu-id="d6dc3-214">0</span><span class="sxs-lookup"><span data-stu-id="d6dc3-214">0</span></span>     |<span data-ttu-id="d6dc3-215">[0,98, 0,43, 0,54,...]</span><span class="sxs-lookup"><span data-stu-id="d6dc3-215">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="d6dc3-216">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-216">Wow... Loved this place.</span></span>              |    <span data-ttu-id="d6dc3-217">1\.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-217">1</span></span>     |<span data-ttu-id="d6dc3-218">[0,35, 0,73, 0,46,...]</span><span class="sxs-lookup"><span data-stu-id="d6dc3-218">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="d6dc3-219">Hizmet çok soriydi.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-219">Service was very prompt.</span></span>              |    <span data-ttu-id="d6dc3-220">1\.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-220">1</span></span>     |<span data-ttu-id="d6dc3-221">[0,39, 0, 0,75,...]</span><span class="sxs-lookup"><span data-stu-id="d6dc3-221">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="d6dc3-222">Öğrenme algoritması ekleme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-222">Add a learning algorithm</span></span>

<span data-ttu-id="d6dc3-223">Bu uygulama, öğeleri veya veri satırlarını kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-223">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="d6dc3-224">Uygulama, Web sitesi açıklamalarını pozitif veya negatif olarak kategorilere ayırır, bu nedenle ikili sınıflandırma görevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-224">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="d6dc3-225">Aşağıdaki kod `BuildAndTrainModel()`satırı olarak aşağıdakini ekleyerek, Machine Learning görevini veri dönüştürme tanımlarına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-225">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="d6dc3-226">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) , sınıflandırma eğitim algoritmanız.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-226">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="d6dc3-227">Bu öğesine `estimator` eklenir ve geçmiş verilerden bilgi edinmek için uygun `SentimentText` (`Features`) ve `Label` giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-227">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="d6dc3-228">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-228">Train the model</span></span>

<span data-ttu-id="d6dc3-229">Yöntemine bir sonraki kod satırı `splitTrainSet` olarak aşağıdakileri ekleyerek modeli verilere sığdırın ve eğitilen modeli döndürün: `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-229">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="d6dc3-230">[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-230">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="d6dc3-231">Değerlendirme için kullanılmak üzere eğitilen modeli döndürün</span><span class="sxs-lookup"><span data-stu-id="d6dc3-231">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="d6dc3-232">`BuildAndTrainModel()` Metodun sonundaki modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-232">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="d6dc3-233">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-233">Evaluate the model</span></span>

<span data-ttu-id="d6dc3-234">Modelinize eğitim verdikten sonra, test verilerinizi, modelin performansını doğrulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-234">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="d6dc3-235">Aşağıdaki kodla hemen sonra `BuildAndTrainModel()` yöntemioluşturun:`Evaluate()`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-235">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="d6dc3-236">`Evaluate()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-236">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="d6dc3-237">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-237">Loads the test dataset.</span></span>
    - <span data-ttu-id="d6dc3-238">BinaryClassification Değerlendiricisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-238">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="d6dc3-239">Modeli değerlendirir ve ölçümler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-239">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="d6dc3-240">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-240">Displays the metrics.</span></span>

2. <span data-ttu-id="d6dc3-241">Aşağıdaki kodu kullanarak yöntem çağrısının hemen `Main()` `BuildAndTrainModel()` altına, yönteminden yeni yönteme bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-241">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="d6dc3-242">Aşağıdaki kodu öğesine `Evaluate()`ekleyerek verileridönüştürün:`splitTestSet`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-242">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="d6dc3-243">Önceki kod, bir test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapmak üzere [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-243">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="d6dc3-244">`Evaluate()` Yöntemine aşağıdaki kod satırı olarak aşağıdakini ekleyerek modeli değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-244">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="d6dc3-245">Tahmin kümesine (`predictions`) sahip olduktan sonra, tahmini değerleri test veri kümesindeki `Labels` gerçek ile karşılaştıran ve bir [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) döndüren [değerlendir ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi, modeli değerlendirir. modelin nasıl çalıştığı hakkında nesne.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-245">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="d6dc3-246">Model doğrulama ölçümlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-246">Displaying the metrics for model validation</span></span>

<span data-ttu-id="d6dc3-247">Ölçümleri göstermek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-247">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="d6dc3-248">`Accuracy` Ölçüm, test kümesindeki doğru tahminlerden oranı olan bir modelin doğruluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-248">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="d6dc3-249">`AreaUnderRocCurve` Ölçüm, modelin pozitif ve negatif sınıfları doğru şekilde sınıflandırarak ne kadar süden emin olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-249">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="d6dc3-250">Bunun mümkün olduğunca `AreaUnderRocCurve` yakın olmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-250">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="d6dc3-251">Ölçüm, duyarlık ve [geri çekme](../resources/glossary.md#recall)arasındaki Bakiyenin ölçüsü olan modelin F1 Puanını alır. [](../resources/glossary.md#precision) `F1Score`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-251">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="d6dc3-252">Bunun mümkün olduğunca `F1Score` yakın olmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-252">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="d6dc3-253">Test verilerinin sonucunu tahmin etme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-253">Predict the test data outcome</span></span>

1. <span data-ttu-id="d6dc3-254">Aşağıdaki kodu kullanarak yönteminden hemen `Evaluate()` sonra yönteminioluşturun:`UseModelWithSingleItem()`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-254">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="d6dc3-255">`UseModelWithSingleItem()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-255">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="d6dc3-256">Test verileri için tek bir açıklama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-256">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="d6dc3-257">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-257">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="d6dc3-258">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-258">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="d6dc3-259">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-259">Displays the predicted results.</span></span>

2. <span data-ttu-id="d6dc3-260">Aşağıdaki kodu kullanarak yöntem çağrısının hemen `Main()` `Evaluate()` altına, yönteminden yeni yönteme bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-260">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="d6dc3-261">`UseModelWithSingleItem()` Yönteminin ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-261">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="d6dc3-262">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneği üzerinde bir tahmin gerçekleştirmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-262">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

4. <span data-ttu-id="d6dc3-263">`UseModelWithSingleItem()` Bir`SentimentData`örneği oluşturarak eğitilen modelin, yöntemi içindeki tahminini test etmek için bir açıklama ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-263">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="d6dc3-264">`UseModelWithSingleItem()` Yöntemine bir sonraki kod satırı olarak aşağıdakileri `Prediction Engine` ekleyerek test açıklama verilerini öğesine geçirin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-264">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="d6dc3-265">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-265">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="d6dc3-266">Aşağıdaki `SentimentText` kodu kullanarak ve ilgili yaklaşım tahminini görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-266">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="d6dc3-267">Tahmin için modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="d6dc3-267">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="d6dc3-268">Toplu iş öğelerini dağıtma ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-268">Deploy and predict batch items</span></span>

1. <span data-ttu-id="d6dc3-269">Aşağıdaki kodu kullanarak yönteminden hemen `UseModelWithSingleItem()` sonra yönteminioluşturun:`UseModelWithBatchItems()`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-269">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="d6dc3-270">`UseModelWithBatchItems()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-270">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="d6dc3-271">Batch test verileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-271">Creates batch test data.</span></span>
    - <span data-ttu-id="d6dc3-272">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-272">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="d6dc3-273">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-273">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="d6dc3-274">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-274">Displays the predicted results.</span></span>

2. <span data-ttu-id="d6dc3-275">Aşağıdaki kodu kullanarak yöntem çağrısının hemen `Main` `UseModelWithSingleItem()` altına, yönteminden yeni yönteme bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-275">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="d6dc3-276">Eğitim modelinin kullanım tahminlerini `UseModelWithBatchItems()` test etmek için bazı açıklamalar ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-276">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="d6dc3-277">Açıklama yaklaşımını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-277">Predict comment sentiment</span></span>

<span data-ttu-id="d6dc3-278">[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak açıklama verisi yaklaşımını tahmin etmek için modeli kullanın:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-278">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="d6dc3-279">Tahminleri birleştirin ve görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="d6dc3-279">Combine and display the predictions</span></span>

<span data-ttu-id="d6dc3-280">Aşağıdaki kodu kullanarak tahminler için bir üst bilgi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-280">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="d6dc3-281">Öğesinden devralındığından ,`Transform()` yöntemi tahmin edilen alanlarla `SentimentText`doldurulur. `SentimentPrediction` `SentimentData`</span><span class="sxs-lookup"><span data-stu-id="d6dc3-281">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="d6dc3-282">ML.NET işlem işlemleri sırasında her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-282">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="d6dc3-283">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="d6dc3-283">Results</span></span>

<span data-ttu-id="d6dc3-284">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-284">Your results should be similar to the following.</span></span> <span data-ttu-id="d6dc3-285">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-285">During processing, messages are displayed.</span></span> <span data-ttu-id="d6dc3-286">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-286">You may see warnings, or processing messages.</span></span> <span data-ttu-id="d6dc3-287">Bunlar, netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-287">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="d6dc3-288">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="d6dc3-288">Congratulations!</span></span> <span data-ttu-id="d6dc3-289">İleti yaklaşımını sınıflandırma ve tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-289">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="d6dc3-290">Başarılı modellerin oluşturulması, yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-290">Building successful models is an iterative process.</span></span> <span data-ttu-id="d6dc3-291">Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-291">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="d6dc3-292">Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı [Hyper-parametreleri](../resources/glossary.md##hyperparameter) ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-292">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="d6dc3-293">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6dc3-293">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d6dc3-294">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d6dc3-294">Next steps</span></span>

<span data-ttu-id="d6dc3-295">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="d6dc3-295">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="d6dc3-296">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6dc3-296">Create a console application</span></span>
> - <span data-ttu-id="d6dc3-297">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="d6dc3-297">Prepare data</span></span>
> - <span data-ttu-id="d6dc3-298">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-298">Load the data</span></span>
> - <span data-ttu-id="d6dc3-299">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-299">Build and train the model</span></span>
> - <span data-ttu-id="d6dc3-300">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="d6dc3-300">Evaluate the model</span></span>
> - <span data-ttu-id="d6dc3-301">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="d6dc3-301">Use the model to make a prediction</span></span>
> - <span data-ttu-id="d6dc3-302">Sonuçlara bakın</span><span class="sxs-lookup"><span data-stu-id="d6dc3-302">See the results</span></span>

<span data-ttu-id="d6dc3-303">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="d6dc3-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d6dc3-304">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="d6dc3-304">Issue Classification</span></span>](github-issue-classification.md)
