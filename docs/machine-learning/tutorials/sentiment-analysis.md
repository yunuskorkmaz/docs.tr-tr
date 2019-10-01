---
title: 'Öğretici: Web sitesi açıklamalarını çözümleme-ikili sınıflandırma'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 'da kullanır.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: c6b9d51a8ab91b4365c909993211f11ab3436808
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700852"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="f3726-104">Öğretici: ML.NET 'de ikili sınıflandırmayla Web sitesi açıklamalarını çözümleyin</span><span class="sxs-lookup"><span data-stu-id="f3726-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="f3726-105">Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f3726-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="f3726-106">İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 2017 ' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3726-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="f3726-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="f3726-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f3726-108">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3726-108">Create a console application</span></span>
> - <span data-ttu-id="f3726-109">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="f3726-109">Prepare data</span></span>
> - <span data-ttu-id="f3726-110">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f3726-110">Load the data</span></span>
> - <span data-ttu-id="f3726-111">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="f3726-111">Build and train the model</span></span>
> - <span data-ttu-id="f3726-112">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f3726-112">Evaluate the model</span></span>
> - <span data-ttu-id="f3726-113">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="f3726-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="f3726-114">Sonuçlara bakın</span><span class="sxs-lookup"><span data-stu-id="f3726-114">See the results</span></span>

<span data-ttu-id="f3726-115">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3726-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f3726-116">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f3726-116">Prerequisites</span></span>

- <span data-ttu-id="f3726-117">".NET Core platformlar arası geliştirme" iş yükü yüklüyken [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)</span><span class="sxs-lookup"><span data-stu-id="f3726-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="f3726-118">[UCI yaklaşım cümleler veri kümesi](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası) etiketli</span><span class="sxs-lookup"><span data-stu-id="f3726-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f3726-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3726-119">Create a console application</span></span>

1. <span data-ttu-id="f3726-120">"SentimentAnalysis" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f3726-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="f3726-121">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f3726-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="f3726-122">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="f3726-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f3726-123">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f3726-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f3726-124">Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f3726-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="f3726-125">Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin.</span><span class="sxs-lookup"><span data-stu-id="f3726-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="f3726-126">**Microsoft. ml. FastTree** NuGet paketi için de aynısını yapın.</span><span class="sxs-lookup"><span data-stu-id="f3726-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="f3726-127">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="f3726-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="f3726-128">Bu öğreticinin veri kümeleri, ' Kimden grubundan, derin özellikler kullanılarak tekil etiketlere, Kotzıas et ' e ait.</span><span class="sxs-lookup"><span data-stu-id="f3726-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="f3726-129">Al,.</span><span class="sxs-lookup"><span data-stu-id="f3726-129">al,.</span></span> <span data-ttu-id="f3726-130">KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="f3726-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="f3726-131">UCI Machine Learning deposu [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="f3726-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="f3726-132">Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.</span><span class="sxs-lookup"><span data-stu-id="f3726-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="f3726-133">[Utiment, cümleler veri KÜMESI ZIP dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve unzip 'i indirin.</span><span class="sxs-lookup"><span data-stu-id="f3726-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="f3726-134">@No__t-0 dosyasını, oluşturduğunuz *veri* dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f3726-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="f3726-135">Çözüm Gezgini, `yelp_labeled.txt` dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f3726-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="f3726-136">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f3726-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f3726-137">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="f3726-137">Create classes and define paths</span></span>

1. <span data-ttu-id="f3726-138">*Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="f3726-139">Son indirilen veri kümesi dosya yolunu ve kaydedilen model dosyası yolunu tutmak için iki genel alan oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f3726-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    - <span data-ttu-id="f3726-140">`_dataPath`, modeli eğitmek için kullanılan veri kümesinin yoluna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f3726-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    - <span data-ttu-id="f3726-141">`_modelPath`, eğitilen modelin kaydedildiği yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="f3726-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="f3726-142">Yolları belirtmek için, aşağıdaki kodu `Main` yönteminin üstüne doğru satıra ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="f3726-143">Ardından, giriş verileriniz ve tahminlerinizi için sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f3726-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="f3726-144">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="f3726-145">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f3726-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="f3726-146">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f3726-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="f3726-147">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f3726-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="f3726-148">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="f3726-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="f3726-149">Aşağıdaki `using` ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="f3726-150">Mevcut sınıf tanımını kaldırın ve *SentimentData.cs* dosyasına `SentimentData` ve `SentimentPrediction` olmak üzere iki sınıfa sahip aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="f3726-151">Verilerin nasıl hazırlandığını</span><span class="sxs-lookup"><span data-stu-id="f3726-151">How the data was prepared</span></span>
<span data-ttu-id="f3726-152">@No__t-0 giriş veri kümesi sınıfının kullanıcı açıklamaları için bir `string` (`SentimentText`) ve yaklaşım için 1 (pozitif) ya da 0 (negatif) bir `bool` (`Sentiment`) değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="f3726-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="f3726-153">Her iki alana de eklenen [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri vardır ve bu, her alanın veri dosyası sırasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f3726-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="f3726-154">Ayrıca, `Sentiment` özelliğinin, `Label` alanı olarak belirlemek için [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="f3726-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="f3726-155">Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="f3726-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="f3726-156">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="f3726-156">SentimentText</span></span>                         |<span data-ttu-id="f3726-157">Yaklaşım (etiket)</span><span class="sxs-lookup"><span data-stu-id="f3726-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="f3726-158">Waitress, hizmette çok yavaş.</span><span class="sxs-lookup"><span data-stu-id="f3726-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="f3726-159">0</span><span class="sxs-lookup"><span data-stu-id="f3726-159">0</span></span>     |
|<span data-ttu-id="f3726-160">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="f3726-160">Crust is not good.</span></span>                    |    <span data-ttu-id="f3726-161">0</span><span class="sxs-lookup"><span data-stu-id="f3726-161">0</span></span>     |
|<span data-ttu-id="f3726-162">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="f3726-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="f3726-163">1\.</span><span class="sxs-lookup"><span data-stu-id="f3726-163">1</span></span>     |
|<span data-ttu-id="f3726-164">Hizmet çok soriydi.</span><span class="sxs-lookup"><span data-stu-id="f3726-164">Service was very prompt.</span></span>              |    <span data-ttu-id="f3726-165">1\.</span><span class="sxs-lookup"><span data-stu-id="f3726-165">1</span></span>     |

<span data-ttu-id="f3726-166">`SentimentPrediction`, model eğitimi sonrasında kullanılan tahmin sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="f3726-166">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="f3726-167">@No__t-0 ' dan devraldığından, giriş `SentimentText` ' in çıkış tahminiyle birlikte görüntülenmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3726-167">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="f3726-168">@No__t-0 Boole değeri, modelin yeni giriş `SentimentText` ile birlikte sağlandığı zaman tahmin edilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="f3726-168">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="f3726-169">@No__t-0 çıkış sınıfı, model tarafından hesaplanan iki diğer özellik içerir: `Score`-model tarafından hesaplanan ham puan ve `Probability`-pozitif yaklaşım olan metnin olasılığına ayarlanmış puan.</span><span class="sxs-lookup"><span data-stu-id="f3726-169">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="f3726-170">Bu öğretici için en önemli özellik `Prediction` ' dır.</span><span class="sxs-lookup"><span data-stu-id="f3726-170">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="f3726-171">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f3726-171">Load the data</span></span>
<span data-ttu-id="f3726-172">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f3726-172">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="f3726-173">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="f3726-173">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="f3726-174">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) `IDataView` nesnesine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f3726-174">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="f3726-175">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="f3726-175">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="f3726-176">@No__t başlatılıyor-0, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3726-176">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f3726-177">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="f3726-177">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="f3726-178">Uygulamayı hazırlayın ve sonra verileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-178">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="f3726-179">@No__t-1 yöntemindeki `Console.WriteLine("Hello World!")` satırını, mlContext değişkenini bildirmek ve başlatmak için aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f3726-179">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="f3726-180">@No__t-0 yöntemine sonraki kod satırı olarak aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-180">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="f3726-181">Aşağıdaki kodu kullanarak, `Main()` yönteminden hemen sonra `LoadData()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f3726-181">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="f3726-182">@No__t-0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f3726-182">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="f3726-183">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="f3726-183">Loads the data.</span></span>
    - <span data-ttu-id="f3726-184">Yüklenen veri kümesini tren ve test veri kümelerine böler.</span><span class="sxs-lookup"><span data-stu-id="f3726-184">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="f3726-185">Bölünmüş eğitme ve test veri kümelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3726-185">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="f3726-186">@No__t-0 yönteminin ilk satırı olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-186">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="f3726-187">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3726-187">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="f3726-188">Veri yolu değişkenlerini alır ve `IDataView` döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3726-188">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="f3726-189">Model eğitimi ve test için veri kümesini bölme</span><span class="sxs-lookup"><span data-stu-id="f3726-189">Split the dataset for model training and testing</span></span>

<span data-ttu-id="f3726-190">Bir modeli hazırlarken, modelin doğruluğunu test etmek için veri kümesinin bir kısmını eğitmeniz ve veri kümesinin bir parçası kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f3726-190">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="f3726-191">Yüklenen verileri gereken veri kümelerine bölmek için, `LoadData()` yönteminde sonraki satır olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-191">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="f3726-192">Önceki kod, yüklenen veri kümesini eğmek ve test veri kümelerine bölmek için [Traintestsplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) yöntemini kullanır ve onları [Traintestdata](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfında döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3726-192">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="f3726-193">@No__t-0parametresiyle verilerin test kümesi yüzdesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="f3726-193">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="f3726-194">Varsayılan değer% 10 ' dur, bu durumda daha fazla veri değerlendirmek için% 20 kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3726-194">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="f3726-195">@No__t-1 yönteminin sonundaki `splitDataView` döndürün:</span><span class="sxs-lookup"><span data-stu-id="f3726-195">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="f3726-196">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="f3726-196">Build and train the model</span></span>

1. <span data-ttu-id="f3726-197">@No__t-0yöntemine `Main()` yönteminde sonraki kod satırı olarak aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-197">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="f3726-198">@No__t-0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f3726-198">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="f3726-199">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f3726-199">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="f3726-200">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="f3726-200">Trains the model.</span></span>
    - <span data-ttu-id="f3726-201">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="f3726-201">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="f3726-202">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3726-202">Returns the model.</span></span>

2. <span data-ttu-id="f3726-203">Aşağıdaki kodu kullanarak, `Main()` yönteminden hemen sonra `BuildAndTrainModel()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f3726-203">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="f3726-204">Verileri ayıklama ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f3726-204">Extract and transform the data</span></span>

1. <span data-ttu-id="f3726-205">Sonraki kod satırı olarak `FeaturizeText` öğesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="f3726-205">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="f3726-206">Önceki koddaki `FeaturizeText()` yöntemi, metin sütununu (`SentimentText`) makine öğrenimi algoritması tarafından kullanılan sayısal anahtar türü `Features` sütununa dönüştürür ve yeni bir veri kümesi sütunu olarak ekler:</span><span class="sxs-lookup"><span data-stu-id="f3726-206">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="f3726-207">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="f3726-207">SentimentText</span></span>                         |<span data-ttu-id="f3726-208">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="f3726-208">Sentiment</span></span> |<span data-ttu-id="f3726-209">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f3726-209">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="f3726-210">Waitress, hizmette çok yavaş.</span><span class="sxs-lookup"><span data-stu-id="f3726-210">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="f3726-211">0</span><span class="sxs-lookup"><span data-stu-id="f3726-211">0</span></span>     |<span data-ttu-id="f3726-212">[0,76, 0,65, 0,44,...]</span><span class="sxs-lookup"><span data-stu-id="f3726-212">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="f3726-213">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="f3726-213">Crust is not good.</span></span>                    |    <span data-ttu-id="f3726-214">0</span><span class="sxs-lookup"><span data-stu-id="f3726-214">0</span></span>     |<span data-ttu-id="f3726-215">[0,98, 0,43, 0,54,...]</span><span class="sxs-lookup"><span data-stu-id="f3726-215">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="f3726-216">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="f3726-216">Wow... Loved this place.</span></span>              |    <span data-ttu-id="f3726-217">1\.</span><span class="sxs-lookup"><span data-stu-id="f3726-217">1</span></span>     |<span data-ttu-id="f3726-218">[0,35, 0,73, 0,46,...]</span><span class="sxs-lookup"><span data-stu-id="f3726-218">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="f3726-219">Hizmet çok soriydi.</span><span class="sxs-lookup"><span data-stu-id="f3726-219">Service was very prompt.</span></span>              |    <span data-ttu-id="f3726-220">1\.</span><span class="sxs-lookup"><span data-stu-id="f3726-220">1</span></span>     |<span data-ttu-id="f3726-221">[0,39, 0, 0,75,...]</span><span class="sxs-lookup"><span data-stu-id="f3726-221">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="f3726-222">Öğrenme algoritması ekleme</span><span class="sxs-lookup"><span data-stu-id="f3726-222">Add a learning algorithm</span></span>

<span data-ttu-id="f3726-223">Bu uygulama, öğeleri veya veri satırlarını kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="f3726-223">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="f3726-224">Uygulama, Web sitesi açıklamalarını pozitif veya negatif olarak kategorilere ayırır, bu nedenle ikili sınıflandırma görevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3726-224">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="f3726-225">@No__t-0 ' a bir sonraki kod satırı olarak aşağıdakini ekleyerek makine öğrenimi görevini veri dönüştürme tanımlarına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-225">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="f3726-226">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) , sınıflandırma eğitim algoritmanız.</span><span class="sxs-lookup"><span data-stu-id="f3726-226">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="f3726-227">Bu, `estimator` ' a eklenir ve geçmiş verilerden öğrenme `SentimentText` (`Features`) ve `Label` giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f3726-227">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="f3726-228">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f3726-228">Train the model</span></span>

<span data-ttu-id="f3726-229">Modeli `splitTrainSet` verilerine sığdırın ve `BuildAndTrainModel()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="f3726-229">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="f3726-230">[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.</span><span class="sxs-lookup"><span data-stu-id="f3726-230">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="f3726-231">Değerlendirme için kullanılmak üzere eğitilen modeli döndürün</span><span class="sxs-lookup"><span data-stu-id="f3726-231">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="f3726-232">@No__t-0 yönteminin sonundaki modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="f3726-232">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="f3726-233">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f3726-233">Evaluate the model</span></span>

<span data-ttu-id="f3726-234">Modelinize eğitim verdikten sonra, test verilerinizi, modelin performansını doğrulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3726-234">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="f3726-235">@No__t-0 yöntemini aşağıdaki kodla `BuildAndTrainModel()` ' den sonra oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f3726-235">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="f3726-236">@No__t-0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f3726-236">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="f3726-237">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="f3726-237">Loads the test dataset.</span></span>
    - <span data-ttu-id="f3726-238">BinaryClassification Değerlendiricisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3726-238">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="f3726-239">Modeli değerlendirir ve ölçümler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3726-239">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="f3726-240">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f3726-240">Displays the metrics.</span></span>

2. <span data-ttu-id="f3726-241">Aşağıdaki kodu kullanarak, `Main()` yönteminden yeni yönteme bir çağrı ekleyin, `BuildAndTrainModel()` yöntem çağrısının altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-241">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="f3726-242">Aşağıdaki kodu `Evaluate()` ' e ekleyerek `splitTestSet` verisini dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="f3726-242">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="f3726-243">Önceki kod, bir test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapmak üzere [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3726-243">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="f3726-244">@No__t-0 yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="f3726-244">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="f3726-245">Tahmin kümesine (`predictions`) sahip olduktan sonra, tahmine dayalı değerleri test veri kümesindeki gerçek `Labels` ile karşılaştıran ve şu şekilde bir [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) nesnesi döndüren [değerlendirme ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi değerlendirir. Model gerçekleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="f3726-245">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="f3726-246">Model doğrulama ölçümlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f3726-246">Displaying the metrics for model validation</span></span>

<span data-ttu-id="f3726-247">Ölçümleri göstermek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f3726-247">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="f3726-248">@No__t-0 ölçümü, test kümesindeki doğru tahminlerden oranı olan bir modelin doğruluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="f3726-248">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="f3726-249">@No__t-0 ölçümü, modelin ne kadar duyarlı olduğunu pozitif ve negatif sınıfların doğru sınıflandırdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3726-249">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="f3726-250">@No__t-0 ' nın mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f3726-250">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="f3726-251">@No__t-0 ölçümü, [duyarlık](../resources/glossary.md#precision) ve [geri çekme](../resources/glossary.md#recall)arasındaki Bakiyenin ölçüsü olan modelin F1 Puanını alır.</span><span class="sxs-lookup"><span data-stu-id="f3726-251">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="f3726-252">@No__t-0 ' nın mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f3726-252">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="f3726-253">Test verilerinin sonucunu tahmin etme</span><span class="sxs-lookup"><span data-stu-id="f3726-253">Predict the test data outcome</span></span>

1. <span data-ttu-id="f3726-254">Aşağıdaki kodu kullanarak, `Evaluate()` yönteminden hemen sonra `UseModelWithSingleItem()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f3726-254">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="f3726-255">@No__t-0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f3726-255">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="f3726-256">Test verileri için tek bir açıklama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3726-256">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="f3726-257">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="f3726-257">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="f3726-258">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f3726-258">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="f3726-259">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f3726-259">Displays the predicted results.</span></span>

2. <span data-ttu-id="f3726-260">Aşağıdaki kodu kullanarak, `Main()` yönteminden yeni yönteme bir çağrı ekleyin, `Evaluate()` yöntem çağrısının altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-260">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="f3726-261">@No__t-0 yönteminde ilk satır olarak oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-261">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="f3726-262">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="f3726-262">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="f3726-263">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="f3726-263">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="f3726-264">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="f3726-264">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="f3726-265">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3726-265">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="f3726-266">[ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın</span><span class="sxs-lookup"><span data-stu-id="f3726-266">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

    > [!NOTE]
    > <span data-ttu-id="f3726-267">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="f3726-267">`PredictionEnginePool` service extension is currently in preview.</span></span>
    
4. <span data-ttu-id="f3726-268">@No__t-1 ' in bir örneğini oluşturarak eğitilen modelin tahminini `UseModelWithSingleItem()` yönteminde test etmek için bir açıklama ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-268">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="f3726-269">@No__t-2 yöntemine sonraki kod satırları olarak aşağıdakini ekleyerek test açıklama verilerini [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) ' e geçirin:</span><span class="sxs-lookup"><span data-stu-id="f3726-269">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="f3726-270">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="f3726-270">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="f3726-271">Aşağıdaki kodu kullanarak `SentimentText` ve karşılık gelen yaklaşım tahminini görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-271">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="f3726-272">Tahmin için modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="f3726-272">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="f3726-273">Toplu iş öğelerini dağıtma ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="f3726-273">Deploy and predict batch items</span></span>

1. <span data-ttu-id="f3726-274">Aşağıdaki kodu kullanarak, `UseModelWithSingleItem()` yönteminden hemen sonra `UseModelWithBatchItems()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f3726-274">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="f3726-275">@No__t-0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f3726-275">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="f3726-276">Batch test verileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3726-276">Creates batch test data.</span></span>
    - <span data-ttu-id="f3726-277">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="f3726-277">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="f3726-278">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f3726-278">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="f3726-279">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f3726-279">Displays the predicted results.</span></span>

2. <span data-ttu-id="f3726-280">Aşağıdaki kodu kullanarak, `Main` yönteminden yeni yönteme bir çağrı ekleyin, `UseModelWithSingleItem()` yöntem çağrısının altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-280">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="f3726-281">@No__t-0 yönteminde eğitilen modelin tahminlerini test etmek için bazı açıklamalar ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f3726-281">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="f3726-282">Açıklama yaklaşımını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="f3726-282">Predict comment sentiment</span></span>

<span data-ttu-id="f3726-283">[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak açıklama verisi yaklaşımını tahmin etmek için modeli kullanın:</span><span class="sxs-lookup"><span data-stu-id="f3726-283">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="f3726-284">Tahminleri birleştirin ve görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="f3726-284">Combine and display the predictions</span></span>

<span data-ttu-id="f3726-285">Aşağıdaki kodu kullanarak tahminler için bir üst bilgi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f3726-285">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="f3726-286">@No__t-0 `SentimentData` ' den devralındığından, `SentimentText` ' i tahmin edilen alanlarla doldurulmuş `Transform()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f3726-286">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="f3726-287">ML.NET işlem işlemleri sırasında her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="f3726-287">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="f3726-288">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="f3726-288">Results</span></span>

<span data-ttu-id="f3726-289">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3726-289">Your results should be similar to the following.</span></span> <span data-ttu-id="f3726-290">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f3726-290">During processing, messages are displayed.</span></span> <span data-ttu-id="f3726-291">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3726-291">You may see warnings, or processing messages.</span></span> <span data-ttu-id="f3726-292">Bunlar, netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f3726-292">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="f3726-293">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="f3726-293">Congratulations!</span></span> <span data-ttu-id="f3726-294">İleti yaklaşımını sınıflandırma ve tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="f3726-294">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="f3726-295">Başarılı modellerin oluşturulması, yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="f3726-295">Building successful models is an iterative process.</span></span> <span data-ttu-id="f3726-296">Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır.</span><span class="sxs-lookup"><span data-stu-id="f3726-296">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="f3726-297">Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı [Hyper-parametreleri](../resources/glossary.md##hyperparameter) ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3726-297">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="f3726-298">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3726-298">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f3726-299">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f3726-299">Next steps</span></span>

<span data-ttu-id="f3726-300">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="f3726-300">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f3726-301">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3726-301">Create a console application</span></span>
> - <span data-ttu-id="f3726-302">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="f3726-302">Prepare data</span></span>
> - <span data-ttu-id="f3726-303">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f3726-303">Load the data</span></span>
> - <span data-ttu-id="f3726-304">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="f3726-304">Build and train the model</span></span>
> - <span data-ttu-id="f3726-305">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f3726-305">Evaluate the model</span></span>
> - <span data-ttu-id="f3726-306">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="f3726-306">Use the model to make a prediction</span></span>
> - <span data-ttu-id="f3726-307">Sonuçlara bakın</span><span class="sxs-lookup"><span data-stu-id="f3726-307">See the results</span></span>

<span data-ttu-id="f3726-308">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="f3726-308">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f3726-309">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="f3726-309">Issue Classification</span></span>](github-issue-classification.md)
