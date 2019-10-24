---
title: 'Öğretici: Web sitesi açıklamalarını çözümleme-ikili sınıflandırma'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 'da kullanır.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 454b9c94d717d7af098ee982d9eaffe18f1c347c
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774413"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="bf950-104">Öğretici: ML.NET 'de ikili sınıflandırmayla Web sitesi açıklamalarını çözümleyin</span><span class="sxs-lookup"><span data-stu-id="bf950-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="bf950-105">Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf950-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="bf950-106">İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 2017 ' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf950-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="bf950-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="bf950-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bf950-108">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="bf950-108">Create a console application</span></span>
> - <span data-ttu-id="bf950-109">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="bf950-109">Prepare data</span></span>
> - <span data-ttu-id="bf950-110">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="bf950-110">Load the data</span></span>
> - <span data-ttu-id="bf950-111">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="bf950-111">Build and train the model</span></span>
> - <span data-ttu-id="bf950-112">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="bf950-112">Evaluate the model</span></span>
> - <span data-ttu-id="bf950-113">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="bf950-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="bf950-114">Sonuçlara bakın</span><span class="sxs-lookup"><span data-stu-id="bf950-114">See the results</span></span>

<span data-ttu-id="bf950-115">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf950-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bf950-116">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="bf950-116">Prerequisites</span></span>

- <span data-ttu-id="bf950-117">[Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi</span><span class="sxs-lookup"><span data-stu-id="bf950-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="bf950-118">[UCI yaklaşım cümleler veri kümesi](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası) etiketli</span><span class="sxs-lookup"><span data-stu-id="bf950-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="bf950-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="bf950-119">Create a console application</span></span>

1. <span data-ttu-id="bf950-120">"SentimentAnalysis" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf950-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="bf950-121">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf950-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="bf950-122">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="bf950-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="bf950-123">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="bf950-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="bf950-124">Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="bf950-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="bf950-125">Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin.</span><span class="sxs-lookup"><span data-stu-id="bf950-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="bf950-126">**Microsoft. ml. FastTree** NuGet paketi için de aynısını yapın.</span><span class="sxs-lookup"><span data-stu-id="bf950-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="bf950-127">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="bf950-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="bf950-128">Bu öğreticinin veri kümeleri, ' Kimden grubundan, derin özellikler kullanılarak tekil etiketlere, Kotzıas et ' e ait.</span><span class="sxs-lookup"><span data-stu-id="bf950-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="bf950-129">Al,.</span><span class="sxs-lookup"><span data-stu-id="bf950-129">al,.</span></span> <span data-ttu-id="bf950-130">KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="bf950-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="bf950-131">UCI Machine Learning deposu [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="bf950-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="bf950-132">Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.</span><span class="sxs-lookup"><span data-stu-id="bf950-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="bf950-133">[Utiment, cümleler veri KÜMESI ZIP dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve unzip 'i indirin.</span><span class="sxs-lookup"><span data-stu-id="bf950-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="bf950-134">`yelp_labelled.txt` dosyasını oluşturduğunuz *veri* dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bf950-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="bf950-135">Çözüm Gezgini, `yelp_labeled.txt` dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="bf950-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="bf950-136">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bf950-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="bf950-137">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="bf950-137">Create classes and define paths</span></span>

1. <span data-ttu-id="bf950-138">*Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="bf950-139">Son indirilen veri kümesi dosya yolunu tutacak bir alan oluşturmak için, `Main` yönteminin hemen altına satıra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-139">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="bf950-140">Ardından, giriş verileriniz ve tahminlerinizi için sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf950-140">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="bf950-141">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-141">Add a new class to your project:</span></span>

    - <span data-ttu-id="bf950-142">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="bf950-142">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="bf950-143">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bf950-143">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="bf950-144">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="bf950-144">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="bf950-145">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="bf950-145">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="bf950-146">Aşağıdaki `using` ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-146">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="bf950-147">Mevcut sınıf tanımını kaldırın ve *SentimentData.cs* dosyasına `SentimentData` ve `SentimentPrediction` olmak üzere iki sınıfa sahip aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-147">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="bf950-148">Verilerin nasıl hazırlandığını</span><span class="sxs-lookup"><span data-stu-id="bf950-148">How the data was prepared</span></span>
<span data-ttu-id="bf950-149">`SentimentData`giriş veri kümesi sınıfı, Kullanıcı yorumları için bir `string` (`SentimentText`) ve bir`Sentiment``bool` (pozitif) ya da 0 (negatif) değeri için bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="bf950-149">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="bf950-150">Her iki alana de eklenen [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri vardır ve bu, her alanın veri dosyası sırasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bf950-150">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="bf950-151">Ayrıca, `Sentiment` özelliğinin, `Label` alanı olarak belirlemek için [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="bf950-151">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="bf950-152">Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="bf950-152">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="bf950-153">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="bf950-153">SentimentText</span></span>                         |<span data-ttu-id="bf950-154">Yaklaşım (etiket)</span><span class="sxs-lookup"><span data-stu-id="bf950-154">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="bf950-155">Waitress, hizmette çok yavaş.</span><span class="sxs-lookup"><span data-stu-id="bf950-155">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="bf950-156">0</span><span class="sxs-lookup"><span data-stu-id="bf950-156">0</span></span>     |
|<span data-ttu-id="bf950-157">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="bf950-157">Crust is not good.</span></span>                    |    <span data-ttu-id="bf950-158">0</span><span class="sxs-lookup"><span data-stu-id="bf950-158">0</span></span>     |
|<span data-ttu-id="bf950-159">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="bf950-159">Wow... Loved this place.</span></span>              |    <span data-ttu-id="bf950-160">1\.</span><span class="sxs-lookup"><span data-stu-id="bf950-160">1</span></span>     |
|<span data-ttu-id="bf950-161">Hizmet çok soriydi.</span><span class="sxs-lookup"><span data-stu-id="bf950-161">Service was very prompt.</span></span>              |    <span data-ttu-id="bf950-162">1\.</span><span class="sxs-lookup"><span data-stu-id="bf950-162">1</span></span>     |

<span data-ttu-id="bf950-163">`SentimentPrediction`, model eğitimi sonrasında kullanılan tahmin sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="bf950-163">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="bf950-164">Giriş `SentimentText`, çıkış tahminiyle birlikte görüntülenebilmeleri için `SentimentData` öğesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="bf950-164">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="bf950-165">`Prediction` Boolean, modelin yeni giriş `SentimentText`sağlandığında tahmin edilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="bf950-165">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="bf950-166">Çıkış sınıfı `SentimentPrediction`, model tarafından hesaplanan iki diğer özelliği içerir: `Score`-model tarafından hesaplanan ham puan ve `Probability` puanı pozitif yaklaşım olan metnin olasılığına ayarlanmış puan.</span><span class="sxs-lookup"><span data-stu-id="bf950-166">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="bf950-167">Bu öğretici için en önemli özellik `Prediction` ' dır.</span><span class="sxs-lookup"><span data-stu-id="bf950-167">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="bf950-168">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="bf950-168">Load the data</span></span>
<span data-ttu-id="bf950-169">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="bf950-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="bf950-170">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="bf950-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="bf950-171">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) `IDataView` nesnesine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf950-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="bf950-172">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="bf950-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="bf950-173">@No__t_0 başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf950-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="bf950-174">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="bf950-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="bf950-175">Uygulamayı hazırlayın ve sonra verileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-175">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="bf950-176">MlContext değişkenini bildirmek ve başlatmak için `Main` yöntemindeki `Console.WriteLine("Hello World!")` satırı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bf950-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="bf950-177">`Main()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-177">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="bf950-178">Aşağıdaki kodu kullanarak, `Main()` yönteminden hemen sonra `LoadData()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bf950-178">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="bf950-179">`LoadData()` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="bf950-179">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="bf950-180">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="bf950-180">Loads the data.</span></span>
    - <span data-ttu-id="bf950-181">Yüklenen veri kümesini tren ve test veri kümelerine böler.</span><span class="sxs-lookup"><span data-stu-id="bf950-181">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="bf950-182">Bölünmüş eğitme ve test veri kümelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf950-182">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="bf950-183">`LoadData()` yönteminin ilk satırı olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-183">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="bf950-184">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf950-184">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="bf950-185">Veri yolu değişkenlerini alır ve `IDataView` döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf950-185">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="bf950-186">Model eğitimi ve test için veri kümesini bölme</span><span class="sxs-lookup"><span data-stu-id="bf950-186">Split the dataset for model training and testing</span></span>

<span data-ttu-id="bf950-187">Bir modeli hazırlarken, modelin doğruluğunu test etmek için veri kümesinin bir kısmını eğitmeniz ve veri kümesinin bir parçası kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bf950-187">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="bf950-188">Yüklenen verileri gereken veri kümelerine bölmek için, `LoadData()` yönteminde sonraki satır olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-188">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="bf950-189">Önceki kod, yüklenen veri kümesini eğmek ve test veri kümelerine bölmek için [Traintestsplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) yöntemini kullanır ve onları [Traintestdata](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfında döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf950-189">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="bf950-190">`testFraction`parametresine sahip verilerin test kümesi yüzdesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="bf950-190">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="bf950-191">Varsayılan değer %10 ' dur, bu durumda daha fazla veri değerlendirmek için %20 kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf950-191">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="bf950-192">`LoadData()` yönteminin sonundaki `splitDataView` döndürün:</span><span class="sxs-lookup"><span data-stu-id="bf950-192">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="bf950-193">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="bf950-193">Build and train the model</span></span>

1. <span data-ttu-id="bf950-194">`BuildAndTrainModel`yöntemine aşağıdaki çağrıyı `Main()` yönteminde sonraki kod satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-194">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="bf950-195">`BuildAndTrainModel()` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="bf950-195">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="bf950-196">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bf950-196">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="bf950-197">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="bf950-197">Trains the model.</span></span>
    - <span data-ttu-id="bf950-198">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="bf950-198">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="bf950-199">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf950-199">Returns the model.</span></span>

2. <span data-ttu-id="bf950-200">Aşağıdaki kodu kullanarak, `Main()` yönteminden hemen sonra `BuildAndTrainModel()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bf950-200">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="bf950-201">Verileri ayıklama ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="bf950-201">Extract and transform the data</span></span>

1. <span data-ttu-id="bf950-202">Sonraki kod satırı olarak `FeaturizeText` öğesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="bf950-202">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="bf950-203">Önceki koddaki `FeaturizeText()` yöntemi, metin sütununu (`SentimentText`) makine öğrenimi algoritması tarafından kullanılan sayısal anahtar türü `Features` sütununa dönüştürür ve yeni bir veri kümesi sütunu olarak ekler:</span><span class="sxs-lookup"><span data-stu-id="bf950-203">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="bf950-204">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="bf950-204">SentimentText</span></span>                         |<span data-ttu-id="bf950-205">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="bf950-205">Sentiment</span></span> |<span data-ttu-id="bf950-206">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf950-206">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="bf950-207">Waitress, hizmette çok yavaş.</span><span class="sxs-lookup"><span data-stu-id="bf950-207">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="bf950-208">0</span><span class="sxs-lookup"><span data-stu-id="bf950-208">0</span></span>     |<span data-ttu-id="bf950-209">[0,76, 0,65, 0,44,...]</span><span class="sxs-lookup"><span data-stu-id="bf950-209">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="bf950-210">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="bf950-210">Crust is not good.</span></span>                    |    <span data-ttu-id="bf950-211">0</span><span class="sxs-lookup"><span data-stu-id="bf950-211">0</span></span>     |<span data-ttu-id="bf950-212">[0,98, 0,43, 0,54,...]</span><span class="sxs-lookup"><span data-stu-id="bf950-212">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="bf950-213">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="bf950-213">Wow... Loved this place.</span></span>              |    <span data-ttu-id="bf950-214">1\.</span><span class="sxs-lookup"><span data-stu-id="bf950-214">1</span></span>     |<span data-ttu-id="bf950-215">[0,35, 0,73, 0,46,...]</span><span class="sxs-lookup"><span data-stu-id="bf950-215">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="bf950-216">Hizmet çok soriydi.</span><span class="sxs-lookup"><span data-stu-id="bf950-216">Service was very prompt.</span></span>              |    <span data-ttu-id="bf950-217">1\.</span><span class="sxs-lookup"><span data-stu-id="bf950-217">1</span></span>     |<span data-ttu-id="bf950-218">[0,39, 0, 0,75,...]</span><span class="sxs-lookup"><span data-stu-id="bf950-218">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="bf950-219">Öğrenme algoritması ekleme</span><span class="sxs-lookup"><span data-stu-id="bf950-219">Add a learning algorithm</span></span>

<span data-ttu-id="bf950-220">Bu uygulama, öğeleri veya veri satırlarını kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="bf950-220">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="bf950-221">Uygulama, Web sitesi açıklamalarını pozitif veya negatif olarak kategorilere ayırır, bu nedenle ikili sınıflandırma görevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf950-221">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="bf950-222">Aşağıdaki `BuildAndTrainModel()`kod satırı olarak aşağıdakini ekleyerek, Machine Learning görevini veri dönüştürme tanımlarına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-222">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="bf950-223">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) , sınıflandırma eğitim algoritmanız.</span><span class="sxs-lookup"><span data-stu-id="bf950-223">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="bf950-224">Bu, `estimator` ' a eklenir ve geçmiş verilerden öğrenme `SentimentText` (`Features`) ve `Label` giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="bf950-224">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="bf950-225">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="bf950-225">Train the model</span></span>

<span data-ttu-id="bf950-226">Modeli `splitTrainSet` verilerine sığdırın ve `BuildAndTrainModel()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="bf950-226">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="bf950-227">[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.</span><span class="sxs-lookup"><span data-stu-id="bf950-227">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="bf950-228">Değerlendirme için kullanılmak üzere eğitilen modeli döndürün</span><span class="sxs-lookup"><span data-stu-id="bf950-228">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="bf950-229">`BuildAndTrainModel()` yönteminin sonundaki modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="bf950-229">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="bf950-230">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="bf950-230">Evaluate the model</span></span>

<span data-ttu-id="bf950-231">Modelinize eğitim verdikten sonra, test verilerinizi, modelin performansını doğrulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf950-231">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="bf950-232">Aşağıdaki kodla `BuildAndTrainModel()`hemen sonra `Evaluate()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bf950-232">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="bf950-233">`Evaluate()` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="bf950-233">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="bf950-234">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="bf950-234">Loads the test dataset.</span></span>
    - <span data-ttu-id="bf950-235">BinaryClassification Değerlendiricisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf950-235">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="bf950-236">Modeli değerlendirir ve ölçümler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf950-236">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="bf950-237">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bf950-237">Displays the metrics.</span></span>

2. <span data-ttu-id="bf950-238">Aşağıdaki kodu kullanarak, `Main()` yönteminden yeni yönteme bir çağrı ekleyin, `BuildAndTrainModel()` yöntem çağrısının altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-238">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="bf950-239">Aşağıdaki kodu `Evaluate()` ' e ekleyerek `splitTestSet` verisini dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="bf950-239">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="bf950-240">Önceki kod, bir test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapmak üzere [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf950-240">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="bf950-241">`Evaluate()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="bf950-241">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="bf950-242">Tahmin kümesine (`predictions`) sahip olduktan sonra, tahmine dayalı değerleri test veri kümesindeki gerçek `Labels` ile karşılaştıran ve şu şekilde bir [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) nesnesi döndüren [değerlendirme ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi değerlendirir. Model gerçekleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="bf950-242">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="bf950-243">Model doğrulama ölçümlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="bf950-243">Displaying the metrics for model validation</span></span>

<span data-ttu-id="bf950-244">Ölçümleri göstermek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="bf950-244">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="bf950-245">`Accuracy` ölçümü, test kümesindeki doğru tahminlerden oranı olan bir modelin doğruluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="bf950-245">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="bf950-246">`AreaUnderRocCurve` ölçümü, modelin pozitif ve negatif sınıfları doğru bir şekilde sınıflandırarak ne kadar süden emin olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf950-246">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="bf950-247">`AreaUnderRocCurve` mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="bf950-247">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="bf950-248">`F1Score` ölçümü, [duyarlık](../resources/glossary.md#precision) ve [geri çekme](../resources/glossary.md#recall)arasındaki Bakiyenin ölçüsü olan modelin F1 Puanını alır.</span><span class="sxs-lookup"><span data-stu-id="bf950-248">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="bf950-249">`F1Score` mümkün olduğunca yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="bf950-249">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="bf950-250">Test verilerinin sonucunu tahmin etme</span><span class="sxs-lookup"><span data-stu-id="bf950-250">Predict the test data outcome</span></span>

1. <span data-ttu-id="bf950-251">Aşağıdaki kodu kullanarak, `Evaluate()` yönteminden hemen sonra `UseModelWithSingleItem()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bf950-251">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="bf950-252">`UseModelWithSingleItem()` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="bf950-252">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="bf950-253">Test verileri için tek bir açıklama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf950-253">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="bf950-254">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="bf950-254">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="bf950-255">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="bf950-255">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="bf950-256">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bf950-256">Displays the predicted results.</span></span>

2. <span data-ttu-id="bf950-257">Aşağıdaki kodu kullanarak, `Main()` yönteminden yeni yönteme bir çağrı ekleyin, `Evaluate()` yöntem çağrısının altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-257">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="bf950-258">`UseModelWithSingleItem()` yönteminin ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-258">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="bf950-259">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="bf950-259">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="bf950-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="bf950-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="bf950-261">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="bf950-261">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="bf950-262">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf950-262">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="bf950-263">[ASP.NET Core Web API 'sindeki `PredictionEnginePool` kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="bf950-263">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="bf950-264">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="bf950-264">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="bf950-265">Bir `SentimentData`örneği oluşturarak eğitilen modelin `UseModelWithSingleItem()` yönteminde tahminini test etmek için bir açıklama ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-265">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="bf950-266">`UseModelWithSingleItem()` yöntemine sonraki kod satırları olarak aşağıdakileri ekleyerek test açıklama verilerini [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) geçirin:</span><span class="sxs-lookup"><span data-stu-id="bf950-266">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="bf950-267">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="bf950-267">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="bf950-268">Aşağıdaki kodu kullanarak `SentimentText` ve karşılık gelen yaklaşım tahminini görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-268">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="bf950-269">Tahmin için modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="bf950-269">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="bf950-270">Toplu iş öğelerini dağıtma ve tahmin etme</span><span class="sxs-lookup"><span data-stu-id="bf950-270">Deploy and predict batch items</span></span>

1. <span data-ttu-id="bf950-271">Aşağıdaki kodu kullanarak, `UseModelWithSingleItem()` yönteminden hemen sonra `UseModelWithBatchItems()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bf950-271">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="bf950-272">`UseModelWithBatchItems()` yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="bf950-272">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="bf950-273">Batch test verileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf950-273">Creates batch test data.</span></span>
    - <span data-ttu-id="bf950-274">Sınama verilerine göre yaklaşımı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="bf950-274">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="bf950-275">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="bf950-275">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="bf950-276">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bf950-276">Displays the predicted results.</span></span>

2. <span data-ttu-id="bf950-277">Aşağıdaki kodu kullanarak, `Main` yönteminden yeni yönteme bir çağrı ekleyin, `UseModelWithSingleItem()` yöntem çağrısının altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-277">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="bf950-278">`UseModelWithBatchItems()` yönteminde eğitilen modelin tahminlerini test etmek için bazı açıklamalar ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf950-278">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="bf950-279">Açıklama yaklaşımını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="bf950-279">Predict comment sentiment</span></span>

<span data-ttu-id="bf950-280">[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak açıklama verisi yaklaşımını tahmin etmek için modeli kullanın:</span><span class="sxs-lookup"><span data-stu-id="bf950-280">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="bf950-281">Tahminleri birleştirin ve görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="bf950-281">Combine and display the predictions</span></span>

<span data-ttu-id="bf950-282">Aşağıdaki kodu kullanarak tahminler için bir üst bilgi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bf950-282">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="bf950-283">`SentimentPrediction` `SentimentData`devralındığından `Transform()` yöntemi tahmin edilen alanlarla `SentimentText` doldurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="bf950-283">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="bf950-284">ML.NET işlem işlemleri sırasında her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="bf950-284">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="bf950-285">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="bf950-285">Results</span></span>

<span data-ttu-id="bf950-286">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf950-286">Your results should be similar to the following.</span></span> <span data-ttu-id="bf950-287">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bf950-287">During processing, messages are displayed.</span></span> <span data-ttu-id="bf950-288">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf950-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="bf950-289">Bunlar, netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="bf950-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="bf950-290">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="bf950-290">Congratulations!</span></span> <span data-ttu-id="bf950-291">İleti yaklaşımını sınıflandırma ve tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="bf950-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="bf950-292">Başarılı modellerin oluşturulması, yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="bf950-292">Building successful models is an iterative process.</span></span> <span data-ttu-id="bf950-293">Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır.</span><span class="sxs-lookup"><span data-stu-id="bf950-293">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="bf950-294">Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı [Hyper-parametreleri](../resources/glossary.md##hyperparameter) ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf950-294">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="bf950-295">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf950-295">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bf950-296">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bf950-296">Next steps</span></span>

<span data-ttu-id="bf950-297">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="bf950-297">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bf950-298">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="bf950-298">Create a console application</span></span>
> - <span data-ttu-id="bf950-299">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="bf950-299">Prepare data</span></span>
> - <span data-ttu-id="bf950-300">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="bf950-300">Load the data</span></span>
> - <span data-ttu-id="bf950-301">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="bf950-301">Build and train the model</span></span>
> - <span data-ttu-id="bf950-302">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="bf950-302">Evaluate the model</span></span>
> - <span data-ttu-id="bf950-303">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="bf950-303">Use the model to make a prediction</span></span>
> - <span data-ttu-id="bf950-304">Sonuçlara bakın</span><span class="sxs-lookup"><span data-stu-id="bf950-304">See the results</span></span>

<span data-ttu-id="bf950-305">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="bf950-305">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="bf950-306">Sorun sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="bf950-306">Issue Classification</span></span>](github-issue-classification.md)
