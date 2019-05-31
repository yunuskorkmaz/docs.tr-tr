---
title: Bir satış anomali algılama senaryosunda ML.NET kullanın
description: ML.NET ürün satış anomali algılama senaryoda anomali ani verileri analiz etmek ve uygun eylemi gerçekleştirin noktalarını değiştirmek nasıl anlamak için nasıl kullanılacağını keşfedin.
ms.date: 05/29/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d31765aa4ff2a0be9c4f140f33de1f5678fc7612
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423904"
---
# <a name="tutorial-use-mlnet-for-product-sales-anomaly-detection"></a><span data-ttu-id="94dec-103">Öğretici: ML.NET ürün satış anomali algılama için kullanın.</span><span class="sxs-lookup"><span data-stu-id="94dec-103">Tutorial: Use ML.NET for product sales anomaly detection</span></span> 

<span data-ttu-id="94dec-104">Bu örnek öğretici ML.NET ürün satış verileri bir .NET Core konsol uygulaması kullanarak aracılığıyla uygun eylemde için anomalileri algılamak için kullanma gösterilmektedir C# Visual Studio 2019 içinde.</span><span class="sxs-lookup"><span data-stu-id="94dec-104">This sample tutorial illustrates using ML.NET to detect anomalies in product sales data to take the appropriate action via a .NET Core console application using C# in Visual Studio 2019.</span></span> 

<span data-ttu-id="94dec-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="94dec-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="94dec-106">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="94dec-106">Load the data</span></span>
> * <span data-ttu-id="94dec-107">Depo anomali algılama için modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="94dec-107">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="94dec-108">Eğitilen modeli ile depo anomalileri algılayın</span><span class="sxs-lookup"><span data-stu-id="94dec-108">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="94dec-109">Değişiklik noktası anomali algılama için modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="94dec-109">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="94dec-110">Eğitilen modeli ile değişiklik noktası anomalileri algılayın</span><span class="sxs-lookup"><span data-stu-id="94dec-110">Detect change point anomalies with the trained model</span></span>

<span data-ttu-id="94dec-111">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) depo.</span><span class="sxs-lookup"><span data-stu-id="94dec-111">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94dec-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="94dec-112">Prerequisites</span></span>

* <span data-ttu-id="94dec-113">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="94dec-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="94dec-114">Ürün sales.csv veri kümesi</span><span class="sxs-lookup"><span data-stu-id="94dec-114">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="94dec-115">Verileri biçiminde `product-sales.csv` "Shampoo satış üzerinden bir üç yıl boyunca" Başlangıçta Datamarket'ten kaynaklıdır ve sağlanan veri kümesinde tarafından zaman serisi verileri kitaplığı (Rob Hyndman tarafından oluşturulan TSDL), temel alır.</span><span class="sxs-lookup"><span data-stu-id="94dec-115">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span> <span data-ttu-id="94dec-116">DataMarket varsayılan Open Lisansı altında lisanslı "Sales üç yıl boyunca shampoo" veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="94dec-116">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="94dec-117">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="94dec-117">Create a console application</span></span>

1. <span data-ttu-id="94dec-118">Oluşturma bir **.NET Core konsol uygulaması** "ProductSalesAnomalyDetection" denir.</span><span class="sxs-lookup"><span data-stu-id="94dec-118">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="94dec-119">Adlı bir dizin oluşturmak *veri* , projenizdeki veri kümesi dosyalarınızı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="94dec-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="94dec-120">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="94dec-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="94dec-121">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="94dec-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="94dec-122">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**seçin **v1.0.0** paketini listede bulun ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="94dec-122">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="94dec-123">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="94dec-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="94dec-124">Bu adımı yineleyin **Microsoft.ML.TimeSeries v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="94dec-124">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="94dec-125">Aşağıdaki `using` en üstündeki deyimleri, *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="94dec-125">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="94dec-126">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="94dec-126">Download your data</span></span>

1. <span data-ttu-id="94dec-127">Veri kümesini indirin ve kaydetmesi *veri* daha önce oluşturduğunuz klasör:</span><span class="sxs-lookup"><span data-stu-id="94dec-127">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="94dec-128">Sağ tıklayın [ *ürün sales.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) seçip "bağlantısına (veya hedef) olarak kaydedin. …"</span><span class="sxs-lookup"><span data-stu-id="94dec-128">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="94dec-129">Ya da kaydettiğinizden emin olun \*.csv dosyasına *veri* klasöründe veya başka bir yerde kaydettikten sonra taşıma \*.csv dosyasına *veri* klasör.</span><span class="sxs-lookup"><span data-stu-id="94dec-129">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="94dec-130">Çözüm Gezgini'nde sağ \*.csv dosyasını seçip alt **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="94dec-130">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="94dec-131">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="94dec-131">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="94dec-132">Aşağıdaki tabloda, bir veri Önizlemesi'nden vardır, \*.csv dosyası:</span><span class="sxs-lookup"><span data-stu-id="94dec-132">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="94dec-133">Ay</span><span class="sxs-lookup"><span data-stu-id="94dec-133">Month</span></span>  |<span data-ttu-id="94dec-134">ProductSales</span><span class="sxs-lookup"><span data-stu-id="94dec-134">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="94dec-135">1 Ocak</span><span class="sxs-lookup"><span data-stu-id="94dec-135">1-Jan</span></span>  |    <span data-ttu-id="94dec-136">271</span><span class="sxs-lookup"><span data-stu-id="94dec-136">271</span></span>      |
|<span data-ttu-id="94dec-137">2 - Ocak</span><span class="sxs-lookup"><span data-stu-id="94dec-137">2-Jan</span></span>  |    <span data-ttu-id="94dec-138">150.9</span><span class="sxs-lookup"><span data-stu-id="94dec-138">150.9</span></span>    |
|<span data-ttu-id="94dec-139">.....</span><span class="sxs-lookup"><span data-stu-id="94dec-139">.....</span></span>  |    <span data-ttu-id="94dec-140">.....</span><span class="sxs-lookup"><span data-stu-id="94dec-140">.....</span></span>    |
|<span data-ttu-id="94dec-141">1 Şubat</span><span class="sxs-lookup"><span data-stu-id="94dec-141">1-Feb</span></span>  |    <span data-ttu-id="94dec-142">199.3</span><span class="sxs-lookup"><span data-stu-id="94dec-142">199.3</span></span>    |
|<span data-ttu-id="94dec-143">.....</span><span class="sxs-lookup"><span data-stu-id="94dec-143">.....</span></span>  |    <span data-ttu-id="94dec-144">.....</span><span class="sxs-lookup"><span data-stu-id="94dec-144">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="94dec-145">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="94dec-145">Create classes and define paths</span></span>

<span data-ttu-id="94dec-146">Ardından, girdi sınıfı data yapınız tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="94dec-146">Next, define your input class data structure.</span></span>

<span data-ttu-id="94dec-147">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="94dec-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="94dec-148">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="94dec-148">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="94dec-149">İçinde **Yeni Öğe Ekle iletişim kutusu**seçin **sınıfı** değiştirip **adı** alanı *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="94dec-149">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="94dec-150">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="94dec-150">Then, select the **Add** button.</span></span>

<span data-ttu-id="94dec-151">*ProductSalesData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="94dec-151">The *ProductSalesData.cs* file opens in the code editor.</span></span> <span data-ttu-id="94dec-152">Aşağıdaki `using` üstüne deyimi *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="94dec-152">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="94dec-153">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `ProductSalesData` ve `ProductSalesPrediction`, *ProductSalesData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="94dec-153">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="94dec-154">`ProductSalesData` bir giriş veri sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="94dec-154">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="94dec-155">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği (sütun dizini tarafından) veri kümesindeki sütunları yüklenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="94dec-155">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> 

<span data-ttu-id="94dec-156">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="94dec-156">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="94dec-157">En son indirilen veri kümesi dosyası yolu ve kayıtlı modeli dosya yolu tutmak için iki genel alanlar oluşturmak ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="94dec-157">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="94dec-158">`_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="94dec-158">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="94dec-159">`_docsize` veri kümesi dosyasında kayıt sayısını içeriyor.</span><span class="sxs-lookup"><span data-stu-id="94dec-159">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="94dec-160">Bu hesaplamak için kullanacağınız `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="94dec-160">You'll use this to calculate `pvalueHistoryLength`.</span></span>

<span data-ttu-id="94dec-161">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="94dec-161">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="94dec-162">[MLContext sınıfı](xref:Microsoft.ML.MLContext) bir tüm ML.NET işlemleri için başlangıç noktası ve başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94dec-162">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="94dec-163">Bu, kavramsal olarak, benzer `DBContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="94dec-163">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="94dec-164">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="94dec-164">Initialize variables in Main</span></span>

<span data-ttu-id="94dec-165">Değiştirin `Console.WriteLine("Hello World!")` satırına `Main` bildirmek ve başlatmak için aşağıdaki kod ile yöntemi `mlContext` değişkeni:</span><span class="sxs-lookup"><span data-stu-id="94dec-165">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a><span data-ttu-id="94dec-166">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="94dec-166">Load the data</span></span>

<span data-ttu-id="94dec-167">ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="94dec-167">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="94dec-168">`IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur.</span><span class="sxs-lookup"><span data-stu-id="94dec-168">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="94dec-169">Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.</span><span class="sxs-lookup"><span data-stu-id="94dec-169">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span> <span data-ttu-id="94dec-170">Sonraki satırı olarak aşağıdaki kodu ekleyin `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="94dec-170">Add the following code as the next line of the `Main()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="94dec-171">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur.</span><span class="sxs-lookup"><span data-stu-id="94dec-171">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="94dec-172">Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="94dec-172">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="ml-task---time-series-anomaly-detection"></a><span data-ttu-id="94dec-173">ML görevi - zaman serisi anomali algılama</span><span class="sxs-lookup"><span data-stu-id="94dec-173">ML task - time series anomaly detection</span></span> 

<span data-ttu-id="94dec-174">Anomali algılama, olağan dışı ya da beklenmeyen olaylar veya davranışları işaretler.</span><span class="sxs-lookup"><span data-stu-id="94dec-174">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="94dec-175">Bu sorunları ve yardımcı soruyu yanıtlamak için "Bu tuhaf nedir?" aranacağı ipuçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="94dec-175">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Bu tuhaf mi](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="94dec-177">Anomali algılama zaman serisi verilerini aykırı değerleri algılama işlemidir; bir verilen giriş zaman serisi hakkında burada beklenen bir davranış değildir veya "tuhaf" işaret eder.</span><span class="sxs-lookup"><span data-stu-id="94dec-177">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="94dec-178">Bu şekilde çok sayıda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="94dec-178">This can be useful in lots of ways.</span></span> <span data-ttu-id="94dec-179">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="94dec-179">For instance:</span></span>

<span data-ttu-id="94dec-180">Bir araba varsa bilmek isteyebilirsiniz: Bu Petrol ölçer normal okuma veya sızıntı sahip mi?</span><span class="sxs-lookup"><span data-stu-id="94dec-180">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="94dec-181">Güç tüketimini izliyorsanız bilmek istersiniz: Kesinti var mı?</span><span class="sxs-lookup"><span data-stu-id="94dec-181">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="94dec-182">Algılanabilir zaman serisi anomalileri iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="94dec-182">There are two types of time series anomalies that can be detected:</span></span> 

* <span data-ttu-id="94dec-183">**Ani artışlar** sistemde geçici artışları anormal davranışları gösterir.</span><span class="sxs-lookup"><span data-stu-id="94dec-183">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span> 

* <span data-ttu-id="94dec-184">**Değiştirme noktaları** sistemde zaman içinde kalıcı değişiklikler başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="94dec-184">**Change points** indicate the beginning of persistent changes over time in the system.</span></span> 

<span data-ttu-id="94dec-185">ML.NET içinde IID depo algılama veya işaret IID değişiklik algılama algoritmalarını için uygun [bağımsız ve aynı şekilde Dağıtılmış veri kümeleri](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="94dec-185">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span> 

<span data-ttu-id="94dec-186">Ani algılamak ve değişim noktaları için aynı ürün satış verilerini analiz etmek.</span><span class="sxs-lookup"><span data-stu-id="94dec-186">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="94dec-187">Oluşturmanın ve eğitim modeli işlemi depo algılama ve değişiklik noktası algılama ile aynıdır; ikisi arasındaki temel fark, kullanılan belirli algılama algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="94dec-187">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="94dec-188">Depo algılama</span><span class="sxs-lookup"><span data-stu-id="94dec-188">Spike detection</span></span> 

<span data-ttu-id="94dec-189">Hedef depo algılama zaman serisi veri değerleri büyük çoğunluğu önemli ölçüde farklılık ani henüz geçici artışları belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="94dec-189">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="94dec-190">Bu şüpheli nadir öğeleri, olayları veya gözlemleri küçültülmesine için zamanında algılamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="94dec-190">It's important to detect these suspicious rare items, events or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="94dec-191">Aşağıdaki yaklaşımı gibi çeşitli anomalileri algılamak için kullanılabilir: kesintiler, siber saldırılardan veya viral web içeriği.</span><span class="sxs-lookup"><span data-stu-id="94dec-191">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="94dec-192">Aşağıdaki görüntüde, ani bir zaman serisi veri kümesi örneğidir:</span><span class="sxs-lookup"><span data-stu-id="94dec-192">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a><span data-ttu-id="94dec-194">DetectSpike() yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="94dec-194">Create the DetectSpike() method</span></span>

<span data-ttu-id="94dec-195">Aşağıdaki çağrısı ekleyin `DetectSpike()`yöntemi sonraki kod satırı olarak `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="94dec-195">Add the following call to the `DetectSpike()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

<span data-ttu-id="94dec-196">`DetectSpike()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="94dec-196">The `DetectSpike()` method executes the following tasks:</span></span>

* <span data-ttu-id="94dec-197">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="94dec-197">Trains the model.</span></span>
* <span data-ttu-id="94dec-198">Geçmiş satış verilerini temel ani değişiklikleri algılar.</span><span class="sxs-lookup"><span data-stu-id="94dec-198">Detects spikes based on on historical sales data.</span></span>
* <span data-ttu-id="94dec-199">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="94dec-199">Displays the results.</span></span>

<span data-ttu-id="94dec-200">Oluşturma `DetectSpike()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="94dec-200">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="94dec-201">Kullanım [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) Depo'yu algılamak için modeli eğitmek için.</span><span class="sxs-lookup"><span data-stu-id="94dec-201">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="94dec-202">Ekleyin `DetectChangepoint()` yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="94dec-202">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

<span data-ttu-id="94dec-203">Modele uygun `productSales` sonraki kod satırı olarak aşağıdakileri ekleyerek veri `DetectSpike()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="94dec-203">Fit the model to the `productSales` data by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

<span data-ttu-id="94dec-204">[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="94dec-204">The [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="94dec-205">Kod dönüştürmek için aşağıdaki satırı ekleyin `productSales` sonraki satırı olarak veri `DetectSpike()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="94dec-205">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

<span data-ttu-id="94dec-206">Önceki kod [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) birden çok test veri kümesini girdi satırları sağlanan için tahminde bulunmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="94dec-206">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="94dec-207">Dönüştürme, `transformedData` türü kesin belirlenmiş bir içine `IEnumerable` kullanarak daha kolay görüntüleme için [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="94dec-207">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

<span data-ttu-id="94dec-208">Aşağıdakileri kullanarak görünen üst bilgi satırı oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:</span><span class="sxs-lookup"><span data-stu-id="94dec-208">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

<span data-ttu-id="94dec-209">Depo algılama sonuçlarınızı aşağıdaki bilgileri görüntüleyeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="94dec-209">You'll display the following information in your spike detection results:</span></span>

* <span data-ttu-id="94dec-210">`Alert` verilen veri noktası için bir depo uyarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="94dec-210">`Alert` indicates a spike alert for a given data point.</span></span>

* <span data-ttu-id="94dec-211">`Score` olan `ProductSales` kümesindeki belirli bir veri noktası değeri.</span><span class="sxs-lookup"><span data-stu-id="94dec-211">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>

* <span data-ttu-id="94dec-212">`P-Value` "P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="94dec-212">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="94dec-213">Bu nasıl büyük olasılıkla bu veri noktasına bir anomali olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="94dec-213">This indicates how likely this data point is an anomaly.</span></span> 

<span data-ttu-id="94dec-214">Yinelemek için aşağıdaki kodu kullanın `predictions` `IEnumerable` ve sonuçları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="94dec-214">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a><span data-ttu-id="94dec-215">Depo algılama sonuçları</span><span class="sxs-lookup"><span data-stu-id="94dec-215">Spike detection results</span></span>

<span data-ttu-id="94dec-216">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94dec-216">Your results should be similar to the following.</span></span> <span data-ttu-id="94dec-217">İşleme sırasında iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="94dec-217">During processing, messages are displayed.</span></span> <span data-ttu-id="94dec-218">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94dec-218">You may see warnings, or processing messages.</span></span> <span data-ttu-id="94dec-219">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="94dec-219">These have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="94dec-220">Değişiklik noktası algılama</span><span class="sxs-lookup"><span data-stu-id="94dec-220">Change point detection</span></span>

<span data-ttu-id="94dec-221">`Change points` Düzey değişiklikleri ve eğilimleri gibi bir değerler zaman serisi olay akışı dağıtımı kalıcı değişiklikler var.</span><span class="sxs-lookup"><span data-stu-id="94dec-221">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="94dec-222">Bu kalıcı değişiklikler çok son daha uzun `spikes` ve yıkıcı olaylar olduğunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="94dec-222">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="94dec-223">`Change points` genellikle çıplak gözle görünür değildir, ancak aşağıdaki yöntemi olduğu gibi bu yaklaşımları kullanarak veri algılandı.</span><span class="sxs-lookup"><span data-stu-id="94dec-223">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="94dec-224">Aşağıdaki resimde, bir değişiklik noktası algılama örneğidir:</span><span class="sxs-lookup"><span data-stu-id="94dec-224">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="94dec-226">DetectChangepoint() yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="94dec-226">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="94dec-227">Aşağıdaki çağrısı ekleyin `DetectChangepoint()`yöntemi sonraki kod satırı olarak `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="94dec-227">Add the following call to the `DetectChangepoint()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

<span data-ttu-id="94dec-228">`DetectChangepoint()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="94dec-228">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="94dec-229">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="94dec-229">Trains the model.</span></span>
* <span data-ttu-id="94dec-230">Değişim noktaları geçmiş satış verilerine göre algılar.</span><span class="sxs-lookup"><span data-stu-id="94dec-230">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="94dec-231">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="94dec-231">Displays the results.</span></span>

<span data-ttu-id="94dec-232">Oluşturma `DetectChangepoint()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="94dec-232">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="94dec-233">[İidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) değişiklik noktası algılama modeli eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94dec-233">The [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) is used to train the model for change point detection.</span></span> <span data-ttu-id="94dec-234">Ekleyin `DetectChangepoint()` yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="94dec-234">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

<span data-ttu-id="94dec-235">Daha önce yaptığınız gibi modele uygun `productSales` sonraki kod satırı olarak aşağıdakileri ekleyerek veri `DetectChangePoint()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="94dec-235">As you did previously, fit the model to the `productSales` data by adding the following as the next line of code in the `DetectChangePoint()` method:</span></span>

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

<span data-ttu-id="94dec-236">Kullanım `Transform()` dönüştürmek için yöntemi `Training` aşağıdakileri ekleyerek veri kod için `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="94dec-236">Use the `Transform()` method to transform the `Training` data by adding the following code to `DetectChangePoint()`:</span></span>

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

<span data-ttu-id="94dec-237">Daha önce yaptığınız gibi dönüştürme, `transformedData` türü kesin belirlenmiş bir içine `IEnumerable` kullanarak daha kolay görüntüleme için `CreateEnumerable()`yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="94dec-237">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

<span data-ttu-id="94dec-238">Sonraki satırda olarak aşağıdaki kod ile bir görüntü başlığı oluşturun `DetectChangePoint()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="94dec-238">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

<span data-ttu-id="94dec-239">Değişiklik noktası algılama sonuçlarınızı aşağıdaki bilgileri görüntüleyeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="94dec-239">You'll display the following information in your change point detection results:</span></span>

* <span data-ttu-id="94dec-240">`Alert` verilen veri noktası için bir değişiklik noktası uyarısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="94dec-240">`Alert` indicates a change point alert for a given data point.</span></span>
* <span data-ttu-id="94dec-241">`Score` olan `ProductSales` kümesindeki belirli bir veri noktası değeri.</span><span class="sxs-lookup"><span data-stu-id="94dec-241">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
* <span data-ttu-id="94dec-242">`P-Value` "P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="94dec-242">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="94dec-243">Bu nasıl büyük olasılıkla bu veri noktasına bir anomali olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="94dec-243">This indicates how likely this data point is an anomaly.</span></span> 
* <span data-ttu-id="94dec-244">`Martingale value` "tuhaf" bir veri noktasına nasıl olduğunu belirlemek için kullanılan, P-değerlerinin sıralarına göre.</span><span class="sxs-lookup"><span data-stu-id="94dec-244">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>  

<span data-ttu-id="94dec-245">Yinelemek `predictions` `IEnumerable` ve aşağıdaki kodla sonuçları görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="94dec-245">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a><span data-ttu-id="94dec-246">Değişiklik noktası algılama sonuçları</span><span class="sxs-lookup"><span data-stu-id="94dec-246">Change point detection results</span></span>

<span data-ttu-id="94dec-247">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94dec-247">Your results should be similar to the following.</span></span> <span data-ttu-id="94dec-248">İşleme sırasında iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="94dec-248">During processing, messages are displayed.</span></span> <span data-ttu-id="94dec-249">Uyarıları ve iletileri işlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94dec-249">You may see warnings, or processing messages.</span></span> <span data-ttu-id="94dec-250">Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="94dec-250">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="94dec-251">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="94dec-251">Congratulations!</span></span> <span data-ttu-id="94dec-252">Artık ani değişiklikleri algılama için machine learning modellerini başarıyla oluşturduktan ve satış veri noktası anomalileri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="94dec-252">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="94dec-253">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) depo.</span><span class="sxs-lookup"><span data-stu-id="94dec-253">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="94dec-254">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="94dec-254">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="94dec-255">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="94dec-255">Load the data</span></span>
> * <span data-ttu-id="94dec-256">Depo anomali algılama için modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="94dec-256">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="94dec-257">Eğitilen modeli ile depo anomalileri algılayın</span><span class="sxs-lookup"><span data-stu-id="94dec-257">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="94dec-258">Değişiklik noktası anomali algılama için modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="94dec-258">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="94dec-259">Eğitilen moduyla değişiklik noktası anomalileri algılayın</span><span class="sxs-lookup"><span data-stu-id="94dec-259">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="94dec-260">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="94dec-260">Next steps</span></span>

<span data-ttu-id="94dec-261">Bir güç tüketimi Anomali algılama örnek keşfetmek için Machine Learning örnekleri GitHub havuzuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="94dec-261">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="94dec-262">DotNet/machinelearning-samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="94dec-262">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/TimeSeries_PowerAnomalyDetection)
