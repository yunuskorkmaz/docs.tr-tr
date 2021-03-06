---
title: 'Öğretici: telefon aramalarındaki bozukluklar'
description: Zaman serisi verileri için anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici, Visual Studio 2019 ' de C# kullanarak bir .NET Core konsol uygulaması oluşturur.
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7edb84ae53f1da7903cf4b3f77d215206ffbf1ef
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259830"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a><span data-ttu-id="f2649-104">Öğretici: ML.NET ile zaman serisinde anomali algılama</span><span class="sxs-lookup"><span data-stu-id="f2649-104">Tutorial: Detect anomalies in time series with ML.NET</span></span>

<span data-ttu-id="f2649-105">Zaman serisi verileri için anomali algılama uygulaması oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="f2649-105">Learn how to build an anomaly detection application for time series data.</span></span> <span data-ttu-id="f2649-106">Bu öğretici, Visual Studio 2019 ' de C# kullanarak bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2649-106">This tutorial creates a .NET Core console application using C# in Visual Studio 2019.</span></span>

<span data-ttu-id="f2649-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="f2649-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f2649-108">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f2649-108">Load the data</span></span>
> * <span data-ttu-id="f2649-109">Zaman serisi için dönemi algılama</span><span class="sxs-lookup"><span data-stu-id="f2649-109">Detect period for a time series</span></span>
> * <span data-ttu-id="f2649-110">Süreli bir zaman serisi için anomali algılama</span><span class="sxs-lookup"><span data-stu-id="f2649-110">Detect anomaly for a periodical time series</span></span>

<span data-ttu-id="f2649-111">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2649-111">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2649-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f2649-112">Prerequisites</span></span>

* <span data-ttu-id="f2649-113">[Visual Studio 2019 sürüm 16.7.8 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="f2649-113">[Visual Studio 2019 version 16.7.8 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="f2649-114">[phone-calls.csv veri kümesi](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv).</span><span class="sxs-lookup"><span data-stu-id="f2649-114">[The phone-calls.csv dataset](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f2649-115">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2649-115">Create a console application</span></span>

1. <span data-ttu-id="f2649-116">"Phonecallsanomalyıdetection" adlı bir **C# .NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2649-116">Create a **C# .NET Core Console Application** called "PhoneCallsAnomalyDetection".</span></span>

2. <span data-ttu-id="f2649-117">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2649-117">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="f2649-118">**Microsoft.ml NuGet paketini** yükler:</span><span class="sxs-lookup"><span data-stu-id="f2649-118">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="f2649-119">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2649-119">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f2649-120">Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml** araması yapın ve **yüklemeyi** seçin.</span><span class="sxs-lookup"><span data-stu-id="f2649-120">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="f2649-121">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f2649-121">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="f2649-122">**Microsoft. ml. TimeSeries** için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2649-122">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="f2649-123">`using` *Program.cs* dosyanızın en üstüne aşağıdaki deyimleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2649-123">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="f2649-124">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="f2649-124">Download your data</span></span>

1. <span data-ttu-id="f2649-125">Veri kümesini indirin ve daha önce oluşturduğunuz *veri* klasörüne kaydedin:</span><span class="sxs-lookup"><span data-stu-id="f2649-125">Download the dataset and save it to the *Data* folder you previously created:</span></span>

    <span data-ttu-id="f2649-126">[*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) sağ tıklayıp "bağlantıyı (veya hedefi) farklı kaydet" i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2649-126">Right click on [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="f2649-127">\*. Csv dosyasını *veri* klasörüne kaydettiğinizden ya da başka bir yere kaydettikten sonra, \* . csv dosyasını *veri* klasörüne taşıdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f2649-127">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="f2649-128">Çözüm Gezgini, \* . csv dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2649-128">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="f2649-129">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala** olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2649-129">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="f2649-130">Aşağıdaki tabloda,. csv dosyanızdaki bir veri önizlemesi verilmiştir \* :</span><span class="sxs-lookup"><span data-stu-id="f2649-130">The following table is a data preview from your \*.csv file:</span></span>

| <span data-ttu-id="f2649-131">timestamp</span><span class="sxs-lookup"><span data-stu-id="f2649-131">timestamp</span></span>  | <span data-ttu-id="f2649-132">değer</span><span class="sxs-lookup"><span data-stu-id="f2649-132">value</span></span> |
|--------|--------------|
| <span data-ttu-id="f2649-133">2018/9/3</span><span class="sxs-lookup"><span data-stu-id="f2649-133">2018/9/3</span></span>  | <span data-ttu-id="f2649-134">36,69670857</span><span class="sxs-lookup"><span data-stu-id="f2649-134">36.69670857</span></span>  |
| <span data-ttu-id="f2649-135">2018/9/4</span><span class="sxs-lookup"><span data-stu-id="f2649-135">2018/9/4</span></span>  | <span data-ttu-id="f2649-136">35,74160571</span><span class="sxs-lookup"><span data-stu-id="f2649-136">35.74160571</span></span>  |
| <span data-ttu-id="f2649-137">.....</span><span class="sxs-lookup"><span data-stu-id="f2649-137">.....</span></span>  | <span data-ttu-id="f2649-138">.....</span><span class="sxs-lookup"><span data-stu-id="f2649-138">.....</span></span>  |
| <span data-ttu-id="f2649-139">2018/10/3</span><span class="sxs-lookup"><span data-stu-id="f2649-139">2018/10/3</span></span>  | <span data-ttu-id="f2649-140">34,49893429</span><span class="sxs-lookup"><span data-stu-id="f2649-140">34.49893429</span></span>  |
| <span data-ttu-id="f2649-141">...</span><span class="sxs-lookup"><span data-stu-id="f2649-141">...</span></span>    | <span data-ttu-id="f2649-142">....</span><span class="sxs-lookup"><span data-stu-id="f2649-142">....</span></span>   |

<span data-ttu-id="f2649-143">Bu dosya bir zaman serisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2649-143">This file represents a time-series.</span></span> <span data-ttu-id="f2649-144">Dosyadaki her bir satır bir veri noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2649-144">Each row in the file is a data point.</span></span> <span data-ttu-id="f2649-145">Her bir `timestamp` `value` günlük telefon araması sayısını göstermek için her bir veri noktasının, ve, iki özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="f2649-145">Each data point has two attributes, namely, `timestamp` and `value`, to represent the number of phone calls at each day.</span></span> <span data-ttu-id="f2649-146">Telefon çağrılarının sayısı, büyük/küçük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f2649-146">The number of phone calls is transformed to de-sensitivity.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f2649-147">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="f2649-147">Create classes and define paths</span></span>

<span data-ttu-id="f2649-148">Sonra, giriş ve tahmin sınıfı veri yapılarınızı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f2649-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="f2649-149">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2649-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="f2649-150">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f2649-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="f2649-151">**Yeni öğe Ekle iletişim kutusunda** **sınıf** ' ı seçin ve **ad** alanını *PhoneCallsData.cs* olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2649-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *PhoneCallsData.cs*.</span></span> <span data-ttu-id="f2649-152">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f2649-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="f2649-153">*PhoneCallsData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="f2649-153">The *PhoneCallsData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="f2649-154">Aşağıdaki `using` ifadeyi *PhoneCallsData.cs* öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2649-154">Add the following `using` statement to the top of *PhoneCallsData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="f2649-155">Mevcut sınıf tanımını kaldırın ve iki sınıfa `PhoneCallsData` ve `PhoneCallsPrediction` *PhoneCallsData.cs* dosyasına sahip olan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2649-155">Remove the existing class definition and add the following code, which has two classes `PhoneCallsData` and `PhoneCallsPrediction`, to the *PhoneCallsData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="f2649-156">`PhoneCallsData` bir giriş veri sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2649-156">`PhoneCallsData` specifies an input data class.</span></span> <span data-ttu-id="f2649-157">[Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yükleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2649-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="f2649-158">İki özniteliğe sahiptir `timestamp` ve `value` veri dosyasındaki aynı özniteliklere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f2649-158">It has two attributes `timestamp` and `value` that correspond to the same attributes in the data file.</span></span>

    <span data-ttu-id="f2649-159">`PhoneCallsPrediction` tahmin verileri sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2649-159">`PhoneCallsPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="f2649-160">SR-CNN algılayıcısı için tahmin, belirtilen [algılama moduna](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2649-160">For SR-CNN detector, the prediction depends on the [detect mode](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) specified.</span></span> <span data-ttu-id="f2649-161">Bu örnekte, modu seçtik `AnomalyAndMargin` .</span><span class="sxs-lookup"><span data-stu-id="f2649-161">In this sample, we select the `AnomalyAndMargin` mode.</span></span> <span data-ttu-id="f2649-162">Çıktı yedi sütun içerir.</span><span class="sxs-lookup"><span data-stu-id="f2649-162">The output contains seven columns.</span></span> <span data-ttu-id="f2649-163">Çoğu durumda,, `IsAnomaly` , `ExpectedValue` `UpperBoundary` ve çok `LowerBoundary` bilgilendirme yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="f2649-163">In most cases, `IsAnomaly`, `ExpectedValue`, `UpperBoundary`, and `LowerBoundary` are informative enough.</span></span> <span data-ttu-id="f2649-164">Bir noktanın bir anomali, noktanın beklenen değeri ve noktanın alt/üst sınır bölgesi olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f2649-164">They tell you if a point is an anomaly, the expected value of the point and the lower / upper boundary region of the point.</span></span>

5. <span data-ttu-id="f2649-165">Aşağıdaki kodu, `Main` veri dosyanızın yolunu belirtmek için yönteminin hemen üzerindeki satıra ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2649-165">Add the following code to the line right above the `Main` method to specify the path to your data file:</span></span>

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="f2649-166">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="f2649-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="f2649-167">`Console.WriteLine("Hello World!")` `Main` Yöntemi bildirmek ve başlatmak için yöntemindeki satırı aşağıdaki kodla değiştirin `mlContext` :</span><span class="sxs-lookup"><span data-stu-id="f2649-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="f2649-168">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor, `mlContext` model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2649-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f2649-169">Entity Framework, kavramsal olarak da benzerdir `DBContext` .</span><span class="sxs-lookup"><span data-stu-id="f2649-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="f2649-170">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f2649-170">Load the data</span></span>

<span data-ttu-id="f2649-171">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f2649-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="f2649-172">`IDataView` , tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="f2649-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="f2649-173">Veriler bir metin dosyasından veya diğer kaynaklardan (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f2649-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="f2649-174">Aşağıdaki kodu yönteminin sonraki satırı olarak ekleyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="f2649-174">Add the following code as the next line of the `Main` method:</span></span>

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="f2649-175">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2649-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="f2649-176">Veri yolu değişkenlerini alır ve döndürür `IDataView` .</span><span class="sxs-lookup"><span data-stu-id="f2649-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="f2649-177">Zaman serisi anomali algılama</span><span class="sxs-lookup"><span data-stu-id="f2649-177">Time series anomaly detection</span></span>

<span data-ttu-id="f2649-178">Zaman serisi anomali algılama, zaman serisi veri aykırı durumları algılama işlemidir; belirli bir giriş zaman serisini, davranışın beklenmediği veya "tuhaf" olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2649-178">Time series anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span> <span data-ttu-id="f2649-179">Bu anormaller genellikle sorun etki alanı ile ilgili bazı olayları ifade eder: Kullanıcı hesaplarında bir Cyber-saldırı, güç kesintisi, bir sunucu üzerinde RPS, bellek sızıntısı vb.</span><span class="sxs-lookup"><span data-stu-id="f2649-179">These anomalies are typically indicative of some events of interest in the problem domain: a cyber-attack on user accounts, power outage, bursting RPS on a server, memory leak, etc.</span></span>

<span data-ttu-id="f2649-180">Zaman serisinde anomali bulmak için, önce serinin dönemini belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f2649-180">To find anomaly on time series, you should first determine the period of the series.</span></span> <span data-ttu-id="f2649-181">Daha sonra, zaman serisi çeşitli bileşenlere parçalanır `Y = T + S + R` , burada `Y` özgün seriler, `T` eğilim bileşeni, `S` mevsimdir ve `R` serinin kalan bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="f2649-181">Then, the time series can be decomposed into several components as `Y = T + S + R`, where `Y` is the original series, `T` is the trend component, `S` is the seasonal component, and `R` is the residual component of the series.</span></span> <span data-ttu-id="f2649-182">Bu adım [ayrıştırma](https://en.wikipedia.org/wiki/Decomposition_of_time_series)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f2649-182">This step is called [decomposition](https://en.wikipedia.org/wiki/Decomposition_of_time_series).</span></span> <span data-ttu-id="f2649-183">Son olarak, algılama işlemi, diğer bileşende, anormallikleri bulmak için gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f2649-183">Finally, detection is performed on the residual component to find the anomalies.</span></span> <span data-ttu-id="f2649-184">ML.NET ' de, SR-CNN algoritması, zaman serisinde anomali algılama için Spectral artımı (SR) ve evsel sinir ağı (CNN) temel alan gelişmiş ve önemli algoritmadır.</span><span class="sxs-lookup"><span data-stu-id="f2649-184">In ML.NET, The SR-CNN algorithm is an advanced and novel algorithm that is based on Spectral Residual (SR) and Convolutional Neural Network(CNN) to detect anomaly on time-series.</span></span> <span data-ttu-id="f2649-185">Bu algoritma hakkında daha fazla bilgi için bkz. [Microsoft 'Ta zaman serisi anomali algılama hizmeti](https://arxiv.org/pdf/1906.03821.pdf).</span><span class="sxs-lookup"><span data-stu-id="f2649-185">For more information on this algorithm, see [Time-Series Anomaly Detection Service at Microsoft](https://arxiv.org/pdf/1906.03821.pdf).</span></span>

<span data-ttu-id="f2649-186">Bu öğreticide, bu yordamların iki işlev kullanılarak tamamlanbir şekilde görülecektir.</span><span class="sxs-lookup"><span data-stu-id="f2649-186">In this tutorial, you will see that these procedures can be completed using two functions.</span></span>

## <a name="detect-period"></a><span data-ttu-id="f2649-187">Süreyi Algıla</span><span class="sxs-lookup"><span data-stu-id="f2649-187">Detect Period</span></span>

<span data-ttu-id="f2649-188">İlk adımda, `DetectSeasonality` serinin dönemini belirlemede işlevi çağıracağız.</span><span class="sxs-lookup"><span data-stu-id="f2649-188">In the first step, we invoke the `DetectSeasonality` function to determine the period of the series.</span></span>

### <a name="create-the-detectperiod-method"></a><span data-ttu-id="f2649-189">DetectPeriod metodunu oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2649-189">Create the DetectPeriod method</span></span>

1. <span data-ttu-id="f2649-190">`DetectPeriod` `Main` Aşağıdaki kodu kullanarak yönteminin hemen altındaki yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2649-190">Create the `DetectPeriod` method, just below the `Main` method, using the following code:</span></span>

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. <span data-ttu-id="f2649-191"><xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A>Dönemi algılamak için işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2649-191">Use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> function to detect period.</span></span> <span data-ttu-id="f2649-192">`DetectPeriod`Aşağıdaki kodla yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2649-192">Add it to the `DetectPeriod` method with the following code:</span></span>

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. <span data-ttu-id="f2649-193">Yöntemine sonraki kod satırı olarak aşağıdakini ekleyerek period değerini görüntüleyin `DetectPeriod` :</span><span class="sxs-lookup"><span data-stu-id="f2649-193">Display the period value by adding the following as the next line of code in the `DetectPeriod` method:</span></span>

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. <span data-ttu-id="f2649-194">Yöntemine aşağıdaki çağrıyı ekleyin `DetectPeriod` `Main` :</span><span class="sxs-lookup"><span data-stu-id="f2649-194">Add the following call to the `DetectPeriod` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a><span data-ttu-id="f2649-195">Süre algılama sonuçları</span><span class="sxs-lookup"><span data-stu-id="f2649-195">Period detection results</span></span>

<span data-ttu-id="f2649-196">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f2649-196">Run the application.</span></span> <span data-ttu-id="f2649-197">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2649-197">Your results should be similar to the following.</span></span>

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a><span data-ttu-id="f2649-198">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="f2649-198">Detect Anomaly</span></span>

<span data-ttu-id="f2649-199">Bu adımda, <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> anormallikleri bulmak için yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f2649-199">In this step, you use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> method to find anomalies.</span></span>

### <a name="create-the-detectanomaly-method"></a><span data-ttu-id="f2649-200">DetectAnomaly yöntemini oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2649-200">Create the DetectAnomaly method</span></span>

1. <span data-ttu-id="f2649-201">`DetectAnomaly` `DetectPeriod` Aşağıdaki kodu kullanarak yönteminin hemen altındaki yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2649-201">Create the `DetectAnomaly` method, just below the `DetectPeriod` method, using the following code:</span></span>

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. <span data-ttu-id="f2649-202"><xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> `DetectAnomaly` Yönteminde aşağıdaki kodla ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="f2649-202">Set up <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> in the `DetectAnomaly` method with the following code:</span></span>

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. <span data-ttu-id="f2649-203">Aşağıdaki kod satırını yöntemine ekleyerek SR-CNN algoritmasına göre anomali algılama `DetectAnomaly` :</span><span class="sxs-lookup"><span data-stu-id="f2649-203">Detect anomaly by SR-CNN algorithm by adding the following line of code in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. <span data-ttu-id="f2649-204">`IEnumerable`Aşağıdaki kodla yöntemi kullanılarak daha kolay görüntülenmek üzere çıkış veri görünümünü kesin bir şekilde belirlenmiş bir [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) şekilde dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="f2649-204">Convert the output data view into a strongly typed `IEnumerable` for easier display using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. <span data-ttu-id="f2649-205">Yönteminde bir sonraki satır olarak aşağıdaki kodla bir görüntüleme üstbilgisi oluşturun `DetectAnomaly` :</span><span class="sxs-lookup"><span data-stu-id="f2649-205">Create a display header with the following code as the next line in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    <span data-ttu-id="f2649-206">Değişiklik noktası algılama sonuçlarında aşağıdaki bilgileri görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f2649-206">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="f2649-207">`Index` her noktanın dizinidir.</span><span class="sxs-lookup"><span data-stu-id="f2649-207">`Index` is the index of each point.</span></span>
    * <span data-ttu-id="f2649-208">`Anomaly` her noktanın anomali olarak algılanıp algılanmadığını gösteren göstergedir.</span><span class="sxs-lookup"><span data-stu-id="f2649-208">`Anomaly` is the indicator of whether each point is detected as anomaly.</span></span>
    * <span data-ttu-id="f2649-209">`ExpectedValue` her noktanın tahmini değeridir.</span><span class="sxs-lookup"><span data-stu-id="f2649-209">`ExpectedValue` is the estimated value of each point.</span></span>
    * <span data-ttu-id="f2649-210">`LowerBoundary` her noktanın en düşük değeri anomali olamaz.</span><span class="sxs-lookup"><span data-stu-id="f2649-210">`LowerBoundary` is the lowest value each point can be to be not anomaly.</span></span>
    * <span data-ttu-id="f2649-211">`UpperBoundary` en yüksek değer, her noktanın anomali olmaması olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2649-211">`UpperBoundary` is the highest value each point can be to be not anomaly.</span></span>

6. <span data-ttu-id="f2649-212">Üzerinde yineleme `predictions` `IEnumerable` yapın ve sonuçları aşağıdaki kodla görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="f2649-212">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. <span data-ttu-id="f2649-213">Yöntemine aşağıdaki çağrıyı ekleyin `DetectAnomaly` `Main` :</span><span class="sxs-lookup"><span data-stu-id="f2649-213">Add the following call to the `DetectAnomaly` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a><span data-ttu-id="f2649-214">Anomali algılama sonuçları</span><span class="sxs-lookup"><span data-stu-id="f2649-214">Anomaly detection results</span></span>

<span data-ttu-id="f2649-215">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f2649-215">Run the application.</span></span> <span data-ttu-id="f2649-216">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2649-216">Your results should be similar to the following.</span></span> <span data-ttu-id="f2649-217">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f2649-217">During processing, messages are displayed.</span></span> <span data-ttu-id="f2649-218">Uyarıları veya işlem iletilerini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2649-218">You may see warnings or processing messages.</span></span> <span data-ttu-id="f2649-219">Bazı iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f2649-219">Some messages have been removed from the following results for clarity.</span></span>

```console
Detect period of the series
Period of the series is: 7.
Detect anomaly points in the series
Index   Data    Anomaly AnomalyScore    Mag     ExpectedValue   BoundaryUnit    UpperBoundary   LowerBoundary
0,0,36.841787256739266,41.14206982401966,32.541504689458876
1,0,35.67303618137362,39.97331874865401,31.372753614093227
2,0,34.710132999891826,39.029491313022824,30.390774686760828
3,0,33.44765248883495,37.786086547816545,29.10921842985335
4,0,28.937110922276364,33.25646923540736,24.61775260914537
5,0,5.143895892785781,9.444178460066171,0.843613325505391
6,0,5.163325228419392,9.463607795699783,0.8630426611390014
7,0,36.76414836240396,41.06443092968435,32.46386579512357
8,0,35.77908590657007,40.07936847385046,31.478803339289676
9,0,34.547259536635245,38.847542103915636,30.246976969354854
10,0,33.55193524820608,37.871293561337076,29.23257693507508
11,0,29.091800129624648,33.392082696905035,24.79151756234426
12,0,5.154836630338823,9.455119197619213,0.8545540630584334
13,0,5.234332502492464,9.534615069772855,0.934049935212073
14,0,36.54992549471526,40.85020806199565,32.24964292743487
15,0,35.79526470980883,40.095547277089224,31.494982142528443
16,0,34.34099013096804,38.64127269824843,30.040707563687647
17,0,33.61201516582131,37.9122977331017,29.31173259854092
18,0,29.223563320561812,33.5238458878422,24.923280753281425
19,0,5.170512168851533,9.470794736131923,0.8702296015711433
20,0,5.2614938889462834,9.561776456226674,0.9612113216658926
21,0,36.37103858487317,40.67132115215356,32.07075601759278
22,0,35.813544599026855,40.113827166307246,31.513262031746464
23,0,34.05600492733225,38.356287494612644,29.755722360051863
24,0,33.65828319077884,37.95856575805923,29.358000623498448
25,0,29.381125690882463,33.681408258162854,25.080843123602072
26,0,5.261543539820418,9.561826107100808,0.9612609725400283
27,0,5.4873712582971805,9.787653825577571,1.1870886910167897
28,1,36.504694001629254,40.804976568909645,32.20441143434886  <-- alert is on, detected anomaly
...
```

<span data-ttu-id="f2649-220">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="f2649-220">Congratulations!</span></span> <span data-ttu-id="f2649-221">Artık bir dönemsel serisinde dönem ve anomali algılama için makine öğrenimi modellerini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="f2649-221">You've now successfully built machine learning models for detecting period and anomaly on a periodical series.</span></span>

<span data-ttu-id="f2649-222">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2649-222">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

<span data-ttu-id="f2649-223">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="f2649-223">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f2649-224">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f2649-224">Load the data</span></span>
> * <span data-ttu-id="f2649-225">Zaman serisi verilerinde süreyi Algıla</span><span class="sxs-lookup"><span data-stu-id="f2649-225">Detect period on the time series data</span></span>
> * <span data-ttu-id="f2649-226">Zaman serisi verilerinde anomali algılama</span><span class="sxs-lookup"><span data-stu-id="f2649-226">Detect anomaly on the time series data</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2649-227">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f2649-227">Next steps</span></span>

<span data-ttu-id="f2649-228">Güç tüketimi anomali algılama örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="f2649-228">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f2649-229">DotNet/machinöğrenim-Samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="f2649-229">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
