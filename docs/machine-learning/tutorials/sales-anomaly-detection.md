---
title: 'Öğretici: Ürün satış anomalileri algılayın'
description: Ürün satış verileri için anomali algılama uygulama oluşturmayı öğrenin. Bu öğreticide, bir .NET Core konsol uygulaması kullanarak oluşturur C# Visual Studio 2019 içinde.
ms.date: 06/11/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 6ea5adf79a17bb10ddea676eaea483c2cf627d82
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026040"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="3fb24-104">Öğretici: ML.NET ile ürün satış anomalileri algılayın</span><span class="sxs-lookup"><span data-stu-id="3fb24-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="3fb24-105">Ürün satış verileri için anomali algılama uygulama oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="3fb24-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="3fb24-106">Bu öğreticide, bir .NET Core konsol uygulaması kullanarak oluşturur C# Visual Studio'da.</span><span class="sxs-lookup"><span data-stu-id="3fb24-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="3fb24-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="3fb24-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3fb24-108">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="3fb24-108">Load the data</span></span>
> * <span data-ttu-id="3fb24-109">Depo anomali algılama için modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="3fb24-109">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="3fb24-110">Eğitilen modeli ile depo anomalileri algılayın</span><span class="sxs-lookup"><span data-stu-id="3fb24-110">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="3fb24-111">Değişiklik noktası anomali algılama için modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="3fb24-111">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="3fb24-112">Eğitilen modeli ile değişiklik noktası anomalileri algılayın</span><span class="sxs-lookup"><span data-stu-id="3fb24-112">Detect change point anomalies with the trained model</span></span>

<span data-ttu-id="3fb24-113">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) depo.</span><span class="sxs-lookup"><span data-stu-id="3fb24-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3fb24-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3fb24-114">Prerequisites</span></span>

* <span data-ttu-id="3fb24-115">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3fb24-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="3fb24-116">Ürün sales.csv veri kümesi</span><span class="sxs-lookup"><span data-stu-id="3fb24-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="3fb24-117">Verileri biçiminde `product-sales.csv` "Shampoo satış üzerinden bir üç yıl boyunca" Başlangıçta Datamarket'ten kaynaklıdır ve sağlanan veri kümesinde tarafından zaman serisi verileri kitaplığı (Rob Hyndman tarafından oluşturulan TSDL), temel alır.</span><span class="sxs-lookup"><span data-stu-id="3fb24-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span> <span data-ttu-id="3fb24-118">DataMarket varsayılan Open Lisansı altında lisanslı "Sales üç yıl boyunca shampoo" veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="3fb24-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="3fb24-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fb24-119">Create a console application</span></span>

1. <span data-ttu-id="3fb24-120">Oluşturma bir **.NET Core konsol uygulaması** "ProductSalesAnomalyDetection" denir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="3fb24-121">Adlı bir dizin oluşturmak *veri* , projenizdeki veri kümesi dosyalarınızı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3fb24-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="3fb24-122">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="3fb24-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="3fb24-123">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="3fb24-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="3fb24-124">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**seçin **v1.0.0** paketini listede bulun ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3fb24-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="3fb24-125">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="3fb24-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="3fb24-126">Bu adımı yineleyin **Microsoft.ML.TimeSeries v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="3fb24-126">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="3fb24-127">Aşağıdaki `using` en üstündeki deyimleri, *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="3fb24-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="3fb24-128">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="3fb24-128">Download your data</span></span>

1. <span data-ttu-id="3fb24-129">Veri kümesini indirin ve kaydetmesi *veri* daha önce oluşturduğunuz klasör:</span><span class="sxs-lookup"><span data-stu-id="3fb24-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="3fb24-130">Sağ tıklayın [ *ürün sales.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) seçip "bağlantısına (veya hedef) olarak kaydedin. …"</span><span class="sxs-lookup"><span data-stu-id="3fb24-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="3fb24-131">Ya da kaydettiğinizden emin olun \*.csv dosyasına *veri* klasöründe veya başka bir yerde kaydettikten sonra taşıma \*.csv dosyasına *veri* klasör.</span><span class="sxs-lookup"><span data-stu-id="3fb24-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="3fb24-132">Çözüm Gezgini'nde sağ \*.csv dosyasını seçip alt **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="3fb24-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="3fb24-133">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="3fb24-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="3fb24-134">Aşağıdaki tabloda, bir veri Önizlemesi'nden vardır, \*.csv dosyası:</span><span class="sxs-lookup"><span data-stu-id="3fb24-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="3fb24-135">Ay</span><span class="sxs-lookup"><span data-stu-id="3fb24-135">Month</span></span>  |<span data-ttu-id="3fb24-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="3fb24-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="3fb24-137">1 Ocak</span><span class="sxs-lookup"><span data-stu-id="3fb24-137">1-Jan</span></span>  |    <span data-ttu-id="3fb24-138">271</span><span class="sxs-lookup"><span data-stu-id="3fb24-138">271</span></span>      |
|<span data-ttu-id="3fb24-139">2 - Ocak</span><span class="sxs-lookup"><span data-stu-id="3fb24-139">2-Jan</span></span>  |    <span data-ttu-id="3fb24-140">150.9</span><span class="sxs-lookup"><span data-stu-id="3fb24-140">150.9</span></span>    |
|<span data-ttu-id="3fb24-141">.....</span><span class="sxs-lookup"><span data-stu-id="3fb24-141">.....</span></span>  |    <span data-ttu-id="3fb24-142">.....</span><span class="sxs-lookup"><span data-stu-id="3fb24-142">.....</span></span>    |
|<span data-ttu-id="3fb24-143">1 Şubat</span><span class="sxs-lookup"><span data-stu-id="3fb24-143">1-Feb</span></span>  |    <span data-ttu-id="3fb24-144">199.3</span><span class="sxs-lookup"><span data-stu-id="3fb24-144">199.3</span></span>    |
|<span data-ttu-id="3fb24-145">.....</span><span class="sxs-lookup"><span data-stu-id="3fb24-145">.....</span></span>  |    <span data-ttu-id="3fb24-146">.....</span><span class="sxs-lookup"><span data-stu-id="3fb24-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="3fb24-147">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fb24-147">Create classes and define paths</span></span>

<span data-ttu-id="3fb24-148">Ardından, girdi sınıfı data yapınız tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3fb24-148">Next, define your input class data structure.</span></span>

<span data-ttu-id="3fb24-149">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3fb24-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="3fb24-150">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="3fb24-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="3fb24-151">İçinde **Yeni Öğe Ekle iletişim kutusu**seçin **sınıfı** değiştirip **adı** alanı *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="3fb24-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="3fb24-152">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3fb24-152">Then, select the **Add** button.</span></span>

<span data-ttu-id="3fb24-153">*ProductSalesData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="3fb24-153">The *ProductSalesData.cs* file opens in the code editor.</span></span> <span data-ttu-id="3fb24-154">Aşağıdaki `using` üstüne deyimi *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="3fb24-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="3fb24-155">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `ProductSalesData` ve `ProductSalesPrediction`, *ProductSalesData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="3fb24-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="3fb24-156">`ProductSalesData` bir giriş veri sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="3fb24-157">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği (sütun dizini tarafından) veri kümesindeki sütunları yüklenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> 

<span data-ttu-id="3fb24-158">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="3fb24-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="3fb24-159">En son indirilen veri kümesi dosyası yolu ve kayıtlı modeli dosya yolu tutmak için iki genel alanlar oluşturmak ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="3fb24-159">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="3fb24-160">`_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-160">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="3fb24-161">`_docsize` veri kümesi dosyasında kayıt sayısını içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3fb24-161">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="3fb24-162">Bu hesaplamak için kullanacağınız `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="3fb24-162">You'll use this to calculate `pvalueHistoryLength`.</span></span>

<span data-ttu-id="3fb24-163">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="3fb24-163">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="3fb24-164">[MLContext sınıfı](xref:Microsoft.ML.MLContext) bir tüm ML.NET işlemleri için başlangıç noktası ve başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3fb24-164">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="3fb24-165">Bu, kavramsal olarak, benzer `DBContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="3fb24-165">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="3fb24-166">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="3fb24-166">Initialize variables in Main</span></span>

<span data-ttu-id="3fb24-167">Değiştirin `Console.WriteLine("Hello World!")` satırına `Main` bildirmek ve başlatmak için aşağıdaki kod ile yöntemi `mlContext` değişkeni:</span><span class="sxs-lookup"><span data-stu-id="3fb24-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a><span data-ttu-id="3fb24-168">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="3fb24-168">Load the data</span></span>

<span data-ttu-id="3fb24-169">ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="3fb24-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="3fb24-170">`IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur.</span><span class="sxs-lookup"><span data-stu-id="3fb24-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="3fb24-171">Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.</span><span class="sxs-lookup"><span data-stu-id="3fb24-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span> <span data-ttu-id="3fb24-172">Sonraki satırı olarak aşağıdaki kodu ekleyin `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3fb24-172">Add the following code as the next line of the `Main()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="3fb24-173">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur.</span><span class="sxs-lookup"><span data-stu-id="3fb24-173">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="3fb24-174">Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="3fb24-174">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="ml-task---time-series-anomaly-detection"></a><span data-ttu-id="3fb24-175">ML görevi - zaman serisi anomali algılama</span><span class="sxs-lookup"><span data-stu-id="3fb24-175">ML task - time series anomaly detection</span></span> 

<span data-ttu-id="3fb24-176">Anomali algılama, olağan dışı ya da beklenmeyen olaylar veya davranışları işaretler.</span><span class="sxs-lookup"><span data-stu-id="3fb24-176">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="3fb24-177">Bu sorunları ve yardımcı soruyu yanıtlamak için "Bu tuhaf nedir?" aranacağı ipuçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fb24-177">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Bu tuhaf mi](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="3fb24-179">Anomali algılama zaman serisi verilerini aykırı değerleri algılama işlemidir; bir verilen giriş zaman serisi hakkında burada beklenen bir davranış değildir veya "tuhaf" işaret eder.</span><span class="sxs-lookup"><span data-stu-id="3fb24-179">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="3fb24-180">Bu şekilde çok sayıda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-180">This can be useful in lots of ways.</span></span> <span data-ttu-id="3fb24-181">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3fb24-181">For instance:</span></span>

<span data-ttu-id="3fb24-182">Bir araba varsa bilmek isteyebilirsiniz: Bu Petrol ölçer normal okuma veya sızıntı sahip mi?</span><span class="sxs-lookup"><span data-stu-id="3fb24-182">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="3fb24-183">Güç tüketimini izliyorsanız bilmek istersiniz: Kesinti var mı?</span><span class="sxs-lookup"><span data-stu-id="3fb24-183">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="3fb24-184">Algılanabilir zaman serisi anomalileri iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="3fb24-184">There are two types of time series anomalies that can be detected:</span></span> 

* <span data-ttu-id="3fb24-185">**Ani artışlar** sistemde geçici artışları anormal davranışları gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-185">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span> 

* <span data-ttu-id="3fb24-186">**Değiştirme noktaları** sistemde zaman içinde kalıcı değişiklikler başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-186">**Change points** indicate the beginning of persistent changes over time in the system.</span></span> 

<span data-ttu-id="3fb24-187">ML.NET içinde IID depo algılama veya işaret IID değişiklik algılama algoritmalarını için uygun [bağımsız ve aynı şekilde Dağıtılmış veri kümeleri](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="3fb24-187">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span> 

<span data-ttu-id="3fb24-188">Ani algılamak ve değişim noktaları için aynı ürün satış verilerini analiz etmek.</span><span class="sxs-lookup"><span data-stu-id="3fb24-188">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="3fb24-189">Oluşturmanın ve eğitim modeli işlemi depo algılama ve değişiklik noktası algılama ile aynıdır; ikisi arasındaki temel fark, kullanılan belirli algılama algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3fb24-189">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="3fb24-190">Depo algılama</span><span class="sxs-lookup"><span data-stu-id="3fb24-190">Spike detection</span></span> 

<span data-ttu-id="3fb24-191">Hedef depo algılama zaman serisi veri değerleri büyük çoğunluğu önemli ölçüde farklılık ani henüz geçici artışları belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-191">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="3fb24-192">Bu şüpheli nadir öğeleri, olayları veya gözlemleri küçültülmesine için zamanında algılamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-192">It's important to detect these suspicious rare items, events or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="3fb24-193">Aşağıdaki yaklaşımı gibi çeşitli anomalileri algılamak için kullanılabilir: kesintiler, siber saldırılardan veya viral web içeriği.</span><span class="sxs-lookup"><span data-stu-id="3fb24-193">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="3fb24-194">Aşağıdaki görüntüde, ani bir zaman serisi veri kümesi örneğidir:</span><span class="sxs-lookup"><span data-stu-id="3fb24-194">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a><span data-ttu-id="3fb24-196">DetectSpike() yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fb24-196">Create the DetectSpike() method</span></span>

<span data-ttu-id="3fb24-197">Aşağıdaki çağrısı ekleyin `DetectSpike()`yöntemi sonraki kod satırı olarak `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3fb24-197">Add the following call to the `DetectSpike()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

<span data-ttu-id="3fb24-198">`DetectSpike()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="3fb24-198">The `DetectSpike()` method executes the following tasks:</span></span>

* <span data-ttu-id="3fb24-199">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-199">Trains the model.</span></span>
* <span data-ttu-id="3fb24-200">Geçmiş satış verilerini temel ani değişiklikleri algılar.</span><span class="sxs-lookup"><span data-stu-id="3fb24-200">Detects spikes based on on historical sales data.</span></span>
* <span data-ttu-id="3fb24-201">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3fb24-201">Displays the results.</span></span>

<span data-ttu-id="3fb24-202">Oluşturma `DetectSpike()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3fb24-202">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="3fb24-203">Kullanım [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) Depo'yu algılamak için modeli eğitmek için.</span><span class="sxs-lookup"><span data-stu-id="3fb24-203">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="3fb24-204">Ekleyin `DetectChangepoint()` yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="3fb24-204">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

<span data-ttu-id="3fb24-205">Modele uygun `productSales` sonraki kod satırı olarak aşağıdakileri ekleyerek veri `DetectSpike()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3fb24-205">Fit the model to the `productSales` data by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

<span data-ttu-id="3fb24-206">[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-206">The [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="3fb24-207">Kod dönüştürmek için aşağıdaki satırı ekleyin `productSales` sonraki satırı olarak veri `DetectSpike()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3fb24-207">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

<span data-ttu-id="3fb24-208">Önceki kod [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) birden çok test veri kümesini girdi satırları sağlanan için tahminde bulunmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3fb24-208">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="3fb24-209">Dönüştürme, `transformedData` türü kesin belirlenmiş bir içine `IEnumerable` kullanarak daha kolay görüntüleme için [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="3fb24-209">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

<span data-ttu-id="3fb24-210">Aşağıdakileri kullanarak görünen üst bilgi satırı oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="3fb24-210">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

<span data-ttu-id="3fb24-211">Depo algılama sonuçlarınızı aşağıdaki bilgileri görüntüleyeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="3fb24-211">You'll display the following information in your spike detection results:</span></span>

* <span data-ttu-id="3fb24-212">`Alert` verilen veri noktası için bir depo uyarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-212">`Alert` indicates a spike alert for a given data point.</span></span>

* <span data-ttu-id="3fb24-213">`Score` olan `ProductSales` kümesindeki belirli bir veri noktası değeri.</span><span class="sxs-lookup"><span data-stu-id="3fb24-213">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>

* <span data-ttu-id="3fb24-214">`P-Value` "P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-214">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="3fb24-215">Bu nasıl büyük olasılıkla bu veri noktasına bir anomali olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-215">This indicates how likely this data point is an anomaly.</span></span> 

<span data-ttu-id="3fb24-216">Yinelemek için aşağıdaki kodu kullanın `predictions` `IEnumerable` ve sonuçları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="3fb24-216">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a><span data-ttu-id="3fb24-217">Depo algılama sonuçları</span><span class="sxs-lookup"><span data-stu-id="3fb24-217">Spike detection results</span></span>

<span data-ttu-id="3fb24-218">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fb24-218">Your results should be similar to the following.</span></span> <span data-ttu-id="3fb24-219">İşleme sırasında iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-219">During processing, messages are displayed.</span></span> <span data-ttu-id="3fb24-220">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fb24-220">You may see warnings, or processing messages.</span></span> <span data-ttu-id="3fb24-221">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3fb24-221">These have been removed from the following results for clarity.</span></span>

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a><span data-ttu-id="3fb24-222">Değişiklik noktası algılama</span><span class="sxs-lookup"><span data-stu-id="3fb24-222">Change point detection</span></span>

<span data-ttu-id="3fb24-223">`Change points` Düzey değişiklikleri ve eğilimleri gibi bir değerler zaman serisi olay akışı dağıtımı kalıcı değişiklikler var.</span><span class="sxs-lookup"><span data-stu-id="3fb24-223">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="3fb24-224">Bu kalıcı değişiklikler çok son daha uzun `spikes` ve yıkıcı olaylar olduğunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-224">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="3fb24-225">`Change points` genellikle çıplak gözle görünür değildir, ancak aşağıdaki yöntemi olduğu gibi bu yaklaşımları kullanarak veri algılandı.</span><span class="sxs-lookup"><span data-stu-id="3fb24-225">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="3fb24-226">Aşağıdaki resimde, bir değişiklik noktası algılama örneğidir:</span><span class="sxs-lookup"><span data-stu-id="3fb24-226">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="3fb24-228">DetectChangepoint() yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fb24-228">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="3fb24-229">Aşağıdaki çağrısı ekleyin `DetectChangepoint()`yöntemi sonraki kod satırı olarak `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3fb24-229">Add the following call to the `DetectChangepoint()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

<span data-ttu-id="3fb24-230">`DetectChangepoint()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="3fb24-230">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="3fb24-231">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-231">Trains the model.</span></span>
* <span data-ttu-id="3fb24-232">Değişim noktaları geçmiş satış verilerine göre algılar.</span><span class="sxs-lookup"><span data-stu-id="3fb24-232">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="3fb24-233">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3fb24-233">Displays the results.</span></span>

<span data-ttu-id="3fb24-234">Oluşturma `DetectChangepoint()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="3fb24-234">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="3fb24-235">[İidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) değişiklik noktası algılama modeli eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fb24-235">The [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) is used to train the model for change point detection.</span></span> <span data-ttu-id="3fb24-236">Ekleyin `DetectChangepoint()` yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="3fb24-236">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

<span data-ttu-id="3fb24-237">Daha önce yaptığınız gibi modele uygun `productSales` sonraki kod satırı olarak aşağıdakileri ekleyerek veri `DetectChangePoint()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3fb24-237">As you did previously, fit the model to the `productSales` data by adding the following as the next line of code in the `DetectChangePoint()` method:</span></span>

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

<span data-ttu-id="3fb24-238">Kullanım `Transform()` dönüştürmek için yöntemi `Training` aşağıdakileri ekleyerek veri kod için `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="3fb24-238">Use the `Transform()` method to transform the `Training` data by adding the following code to `DetectChangePoint()`:</span></span>

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

<span data-ttu-id="3fb24-239">Daha önce yaptığınız gibi dönüştürme, `transformedData` türü kesin belirlenmiş bir içine `IEnumerable` kullanarak daha kolay görüntüleme için `CreateEnumerable()`yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="3fb24-239">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

<span data-ttu-id="3fb24-240">Sonraki satırda olarak aşağıdaki kod ile bir görüntü başlığı oluşturun `DetectChangePoint()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3fb24-240">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

<span data-ttu-id="3fb24-241">Değişiklik noktası algılama sonuçlarınızı aşağıdaki bilgileri görüntüleyeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="3fb24-241">You'll display the following information in your change point detection results:</span></span>

* <span data-ttu-id="3fb24-242">`Alert` verilen veri noktası için bir değişiklik noktası uyarısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-242">`Alert` indicates a change point alert for a given data point.</span></span>
* <span data-ttu-id="3fb24-243">`Score` olan `ProductSales` kümesindeki belirli bir veri noktası değeri.</span><span class="sxs-lookup"><span data-stu-id="3fb24-243">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
* <span data-ttu-id="3fb24-244">`P-Value` "P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-244">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="3fb24-245">Bu nasıl büyük olasılıkla bu veri noktasına bir anomali olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-245">This indicates how likely this data point is an anomaly.</span></span> 
* <span data-ttu-id="3fb24-246">`Martingale value` "tuhaf" bir veri noktasına nasıl olduğunu belirlemek için kullanılan, P-değerlerinin sıralarına göre.</span><span class="sxs-lookup"><span data-stu-id="3fb24-246">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>  

<span data-ttu-id="3fb24-247">Yinelemek `predictions` `IEnumerable` ve aşağıdaki kodla sonuçları görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="3fb24-247">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a><span data-ttu-id="3fb24-248">Değişiklik noktası algılama sonuçları</span><span class="sxs-lookup"><span data-stu-id="3fb24-248">Change point detection results</span></span>

<span data-ttu-id="3fb24-249">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fb24-249">Your results should be similar to the following.</span></span> <span data-ttu-id="3fb24-250">İşleme sırasında iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3fb24-250">During processing, messages are displayed.</span></span> <span data-ttu-id="3fb24-251">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fb24-251">You may see warnings, or processing messages.</span></span> <span data-ttu-id="3fb24-252">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3fb24-252">These have been removed from the following results for clarity.</span></span>

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

<span data-ttu-id="3fb24-253">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="3fb24-253">Congratulations!</span></span> <span data-ttu-id="3fb24-254">Artık ani değişiklikleri algılama için machine learning modellerini başarıyla oluşturduktan ve satış veri noktası anomalileri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3fb24-254">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="3fb24-255">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) depo.</span><span class="sxs-lookup"><span data-stu-id="3fb24-255">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="3fb24-256">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="3fb24-256">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3fb24-257">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="3fb24-257">Load the data</span></span>
> * <span data-ttu-id="3fb24-258">Depo anomali algılama için modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="3fb24-258">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="3fb24-259">Eğitilen modeli ile depo anomalileri algılayın</span><span class="sxs-lookup"><span data-stu-id="3fb24-259">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="3fb24-260">Değişiklik noktası anomali algılama için modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="3fb24-260">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="3fb24-261">Eğitilen moduyla değişiklik noktası anomalileri algılayın</span><span class="sxs-lookup"><span data-stu-id="3fb24-261">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="3fb24-262">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3fb24-262">Next steps</span></span>

<span data-ttu-id="3fb24-263">Bir güç tüketimi Anomali algılama örnek keşfetmek için Machine Learning örnekleri GitHub havuzuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="3fb24-263">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3fb24-264">DotNet/machinelearning-samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="3fb24-264">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
