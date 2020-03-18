---
title: 'Öğretici: Ürün satışlarındaki anormallikleri tespit edin'
description: Ürün satış verileri için bir anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici, Visual Studio 2019'da C# kullanarak bir .NET Core konsol uygulaması oluşturur.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: c3fd4aa715a64a20f1eff9b789f6a87eaa749163
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78239995"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="f2441-104">Öğretici: ML.NET ile ürün satışlarında anormallikleri tespit</span><span class="sxs-lookup"><span data-stu-id="f2441-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="f2441-105">Ürün satış verileri için bir anomali algılama uygulaması oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="f2441-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="f2441-106">Bu öğretici Visual Studio'da C# kullanarak bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2441-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="f2441-107">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f2441-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f2441-108">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f2441-108">Load the data</span></span>
> * <span data-ttu-id="f2441-109">Ani anomali tespiti için dönüşüm oluşturun</span><span class="sxs-lookup"><span data-stu-id="f2441-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="f2441-110">Dönüşüm ile ani anomalileri tespit edin</span><span class="sxs-lookup"><span data-stu-id="f2441-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="f2441-111">Değişim noktası anomali tespiti için dönüşüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2441-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="f2441-112">Dönüşüm ile değişim noktası anomalileri tespit</span><span class="sxs-lookup"><span data-stu-id="f2441-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="f2441-113">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2441-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2441-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f2441-114">Prerequisites</span></span>

* <span data-ttu-id="f2441-115">[Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="f2441-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="f2441-116">Product-sales.csv veri kümesi</span><span class="sxs-lookup"><span data-stu-id="f2441-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="f2441-117">Veri formatı, `product-sales.csv` "Şampuan Satışları Üç Yıllık Bir Dönem Boyunca" veri setine dayanmaktadır ve başlangıçta DataMarket'ten temin edilir ve Rob Hyndman tarafından oluşturulan Time Series Data Library (TSDL) tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f2441-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="f2441-118">"Üç Yıllık Bir Süre Boyunca Şampuan Satışları" Dataset DataMarket Varsayılan Açık Lisans altında lisanslı.</span><span class="sxs-lookup"><span data-stu-id="f2441-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f2441-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2441-119">Create a console application</span></span>

1. <span data-ttu-id="f2441-120">"ProductSalesAnomalyDetection" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2441-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="f2441-121">Veri kümesi dosyalarınızı kaydetmek için projenizde *Veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2441-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="f2441-122">Microsoft.ML **NuGet Paketini**Yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f2441-123">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="f2441-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f2441-124">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML** arayın ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f2441-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="f2441-125">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f2441-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="f2441-126">**Microsoft.ML.TimeSeries**için bu adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="f2441-126">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="f2441-127">`using` *Program.cs* dosyanızın üst kısmında aşağıdaki ifadeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="f2441-128">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="f2441-128">Download your data</span></span>

1. <span data-ttu-id="f2441-129">Veri kümesini indirin ve daha önce oluşturduğunuz *Veri* klasörüne kaydedin:</span><span class="sxs-lookup"><span data-stu-id="f2441-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="f2441-130">[*Product-sales.csv'ye*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) sağ tıklayın ve "Bağlantıyı Kaydet (veya Hedef) Olarak..." seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="f2441-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="f2441-131">.csv dosyasını \* *Veri* klasörüne kaydettiğinizi veya başka bir yere kaydettikten sonra .csv dosyasını \* *Veri* klasörüne taşıdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f2441-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="f2441-132">Çözüm Gezgini'nde .csv dosyasına \*sağ tıklayın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="f2441-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="f2441-133">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2441-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="f2441-134">Aşağıdaki tablo .csv \*dosyanızdan bir veri önizlemesidir:</span><span class="sxs-lookup"><span data-stu-id="f2441-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="f2441-135">Ay</span><span class="sxs-lookup"><span data-stu-id="f2441-135">Month</span></span>  |<span data-ttu-id="f2441-136">Ürün Satışları</span><span class="sxs-lookup"><span data-stu-id="f2441-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="f2441-137">1-Ocak</span><span class="sxs-lookup"><span data-stu-id="f2441-137">1-Jan</span></span>  |    <span data-ttu-id="f2441-138">271</span><span class="sxs-lookup"><span data-stu-id="f2441-138">271</span></span>      |
|<span data-ttu-id="f2441-139">2-Ocak</span><span class="sxs-lookup"><span data-stu-id="f2441-139">2-Jan</span></span>  |    <span data-ttu-id="f2441-140">150.9</span><span class="sxs-lookup"><span data-stu-id="f2441-140">150.9</span></span>    |
|<span data-ttu-id="f2441-141">.....</span><span class="sxs-lookup"><span data-stu-id="f2441-141">.....</span></span>  |    <span data-ttu-id="f2441-142">.....</span><span class="sxs-lookup"><span data-stu-id="f2441-142">.....</span></span>    |
|<span data-ttu-id="f2441-143">1-Şubat</span><span class="sxs-lookup"><span data-stu-id="f2441-143">1-Feb</span></span>  |    <span data-ttu-id="f2441-144">199.3</span><span class="sxs-lookup"><span data-stu-id="f2441-144">199.3</span></span>    |
|<span data-ttu-id="f2441-145">.....</span><span class="sxs-lookup"><span data-stu-id="f2441-145">.....</span></span>  |    <span data-ttu-id="f2441-146">.....</span><span class="sxs-lookup"><span data-stu-id="f2441-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f2441-147">Sınıflar oluşturma ve yolları tanımlama</span><span class="sxs-lookup"><span data-stu-id="f2441-147">Create classes and define paths</span></span>

<span data-ttu-id="f2441-148">Ardından, giriş ve tahmin sınıfı veri yapılarınızı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f2441-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="f2441-149">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="f2441-150">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="f2441-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="f2441-151">Yeni **Öğe Ekle iletişim kutusunda,** **Sınıf'ı** seçin ve **Ad** alanını *ProductSalesData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2441-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="f2441-152">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f2441-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="f2441-153">ProductSalesData.cs *ProductSalesData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="f2441-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="f2441-154">ProductSalesData.cs üstüne `using` aşağıdaki ifadeyi *ProductSalesData.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="f2441-155">Varolan sınıf tanımını kaldırın ve iki sınıfı `ProductSalesData` `ProductSalesPrediction`ve ProductSalesData.cs *dosyasına* aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="f2441-156">`ProductSalesData`bir giriş veri sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2441-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="f2441-157">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yüklenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2441-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="f2441-158">`ProductSalesPrediction`tahmin veri sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2441-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="f2441-159">Anomali tespiti için, tahmin bir anomali, ham skor ve p-değeri olup olmadığını belirtmek için bir uyarı oluşur.</span><span class="sxs-lookup"><span data-stu-id="f2441-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="f2441-160">P değeri 0'a ne kadar yakınsa, bir anomali oluşma olasılığı da o kadar artar.</span><span class="sxs-lookup"><span data-stu-id="f2441-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="f2441-161">En son indirilen veri kümesi dosya yolunu ve kaydedilen model dosya yolunu tutmak için iki genel alan oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2441-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="f2441-162">`_dataPath`modeli eğitmek için kullanılan veri kümesine giden yola sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f2441-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="f2441-163">`_docsize`dataset dosyasındaki kayıt sayısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f2441-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="f2441-164">Hesaplamak `pvalueHistoryLength`için `_docSize` kullanacaksın.</span><span class="sxs-lookup"><span data-stu-id="f2441-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="f2441-165">Bu yolları belirtmek için yöntemin `Main` hemen üstündeki satıra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="f2441-166">Main'deki değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="f2441-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="f2441-167">Değişkeni `Console.WriteLine("Hello World!")` `Main` bildirmek ve başlatmak için yöntemdeki satırı `mlContext` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f2441-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="f2441-168">[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç `mlContext` noktasıdır ve başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2441-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f2441-169">Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.</span><span class="sxs-lookup"><span data-stu-id="f2441-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="f2441-170">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f2441-170">Load the data</span></span>

<span data-ttu-id="f2441-171">ML.NET'daki veriler [IDataView sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f2441-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="f2441-172">`IDataView`tabular verileri (sayısal ve metin) tanımlamanın esnek ve etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="f2441-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="f2441-173">Veriler bir metin dosyasından veya başka kaynaklardan (örneğin, SQL veritabanı `IDataView` veya günlük dosyaları) bir nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f2441-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="f2441-174">`Main()` Yöntemin bir sonraki satırı olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="f2441-175">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyada okur.</span><span class="sxs-lookup"><span data-stu-id="f2441-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="f2441-176">Veri yolu değişkenlerini alır ve `IDataView`bir .</span><span class="sxs-lookup"><span data-stu-id="f2441-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="f2441-177">Zaman serisi anomali tespiti</span><span class="sxs-lookup"><span data-stu-id="f2441-177">Time series anomaly detection</span></span>

<span data-ttu-id="f2441-178">Anomali algılama, beklenmeyen veya olağandışı olaylar veya davranışlar alabını işaretler.</span><span class="sxs-lookup"><span data-stu-id="f2441-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="f2441-179">Nerede sorunları aramak için ipuçları verir ve sorusuna cevap yardımcı olur "Bu garip mi?".</span><span class="sxs-lookup"><span data-stu-id="f2441-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

!["Bu garip" anomali tespiti örneği.](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

<span data-ttu-id="f2441-181">Anomali tespiti, zaman serisi veri aykırılıklarını tespit etme işlemidir; davranışın beklendiği gibi olmadığı veya "garip" olmadığı belirli bir giriş zaman serisine işaret edin.</span><span class="sxs-lookup"><span data-stu-id="f2441-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="f2441-182">Anomali tespiti birçok yönden yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2441-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="f2441-183">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f2441-183">For instance:</span></span>

<span data-ttu-id="f2441-184">Eğer bir araba varsa, bilmek isteyebilirsiniz: Bu yağ göstergesi normal okuma, ya da bir sızıntı var mı?</span><span class="sxs-lookup"><span data-stu-id="f2441-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="f2441-185">Eğer güç tüketimini izliyorsanız, şunu bilmek istersiniz: Bir kesinti var mı?</span><span class="sxs-lookup"><span data-stu-id="f2441-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="f2441-186">Algılanabilen iki tür zaman serisi anomalileri vardır:</span><span class="sxs-lookup"><span data-stu-id="f2441-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="f2441-187">**Ani artışlar** sistemde geçici anormal davranış patlamaları olduğunu gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="f2441-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="f2441-188">**Değişiklik noktaları,** sistemde zaman içinde kalıcı değişikliklerin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2441-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="f2441-189">ML.NET, IID Spike Detection veya IID Change nokta Algılama algoritmaları [bağımsız ve aynı şekilde dağıtılan veri kümeleri](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)için uygundur.</span><span class="sxs-lookup"><span data-stu-id="f2441-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="f2441-190">Diğer öğreticilerde modellerin aksine, zaman serisi anomali dedektörü dönüşümleri doğrudan giriş verileri üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="f2441-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="f2441-191">Dönüştürmeyi `IEstimator.Fit()` üretmek için yöntemin eğitim verilerine ihtiyacı yoktur.</span><span class="sxs-lookup"><span data-stu-id="f2441-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="f2441-192">Boş bir listeden oluşturulan bir veri görünümü tarafından sağlanan olsa da, `ProductSalesData`veri şeması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2441-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="f2441-193">Ani artışları ve noktaları değiştirmek için aynı ürün satış verilerini analiz ememezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2441-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="f2441-194">Bina ve eğitim modeli süreci başak algılama ve değişim noktası algılama için aynıdır; ana fark kullanılan özel algılama algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2441-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="f2441-195">Başak algılama</span><span class="sxs-lookup"><span data-stu-id="f2441-195">Spike detection</span></span>

<span data-ttu-id="f2441-196">Başak algılamanın amacı, zaman serisi veri değerlerinin çoğundan önemli ölçüde farklı olan ani ama geçici patlamaları belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="f2441-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="f2441-197">Bu şüpheli nadir öğeleri, olayları veya gözlemleri en aza indirilecek şekilde zamanında tespit etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f2441-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="f2441-198">Aşağıdaki yaklaşım, kesintiler, siber saldırılar veya viral web içeriği gibi çeşitli anormallikleri tespit etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2441-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="f2441-199">Aşağıdaki resim, bir zaman serisi veri kümesindeki ani artışlara bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="f2441-199">The following image is an example of spikes in a time series dataset:</span></span>

![İki ani algılama gösteren ekran görüntüsü.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="f2441-201">CreateEmptyDataView() yöntemini ekleyin</span><span class="sxs-lookup"><span data-stu-id="f2441-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="f2441-202">Aşağıdaki yöntemi `Program.cs`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="f2441-203">Yönteme `CreateEmptyDataView()` giriş olarak kullanılacak doğru şemaya sahip boş bir veri `IEstimator.Fit()` görünümü nesnesi üretir.</span><span class="sxs-lookup"><span data-stu-id="f2441-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="f2441-204">DetectSpike() yöntemini oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2441-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="f2441-205">Yöntem: `DetectSpike()`</span><span class="sxs-lookup"><span data-stu-id="f2441-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="f2441-206">Tahminciden dönüşümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2441-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="f2441-207">Geçmiş satış verilerine göre ani artışlar algılar.</span><span class="sxs-lookup"><span data-stu-id="f2441-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="f2441-208">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f2441-208">Displays the results.</span></span>

1. <span data-ttu-id="f2441-209">Yöntemden `DetectSpike()` `Main()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2441-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="f2441-210">Modeli ani algılama için eğitmek için [IidSpikeEstimator'u](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2441-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="f2441-211">Yönteme `DetectSpike()` aşağıdaki kodla ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="f2441-212">`DetectSpike()` Yöntemde bir sonraki kod satırı olarak aşağıdakileri ekleyerek başak algılama dönüşümü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2441-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel1)]

1. <span data-ttu-id="f2441-213">Yöntemde `productSales` verileri bir sonraki satır olarak dönüştürmek için `DetectSpike()` aşağıdaki kod satırını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData1)]

    <span data-ttu-id="f2441-214">Önceki kod, bir veri kümesinin birden çok giriş satırı için öngörüler yapmak için [Dönüştür()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2441-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="f2441-215">`transformedData` Aşağıdaki kodla [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) yöntemini kullanarak daha kolay görüntü için güçlü bir şekilde yazılan `IEnumerable` bir ekrana dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="f2441-215">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="f2441-216">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu kullanarak bir ekran üstbilgi satırı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2441-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader1)]

    <span data-ttu-id="f2441-217">Başak algılama sonuçlarınızda aşağıdaki bilgileri görüntülersiniz:</span><span class="sxs-lookup"><span data-stu-id="f2441-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="f2441-218">`Alert`belirli bir veri noktası için ani bir uyarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2441-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="f2441-219">`Score`veri `ProductSales` kümesindeki belirli bir veri noktasının değeridir.</span><span class="sxs-lookup"><span data-stu-id="f2441-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="f2441-220">`P-Value`"P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f2441-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="f2441-221">P değeri 0'a ne kadar yakınsa, veri noktası nın anomali olma olasılığı da o kadar yüksektir.</span><span class="sxs-lookup"><span data-stu-id="f2441-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="f2441-222">Aşağıdaki kodu kullanarak aşağıdaki kodu `predictions` `IEnumerable` kullanarak sonuçları yineleyin ve görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults1)]

1. <span data-ttu-id="f2441-223">Yöntemde `DetectSpike()`yönteme çağrı `Main()` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="f2441-224">Başak algılama sonuçları</span><span class="sxs-lookup"><span data-stu-id="f2441-224">Spike detection results</span></span>

<span data-ttu-id="f2441-225">Sonuçlarınız aşağıdakilere benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2441-225">Your results should be similar to the following.</span></span> <span data-ttu-id="f2441-226">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f2441-226">During processing, messages are displayed.</span></span> <span data-ttu-id="f2441-227">Uyarılar veya iletileri işleme görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2441-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="f2441-228">Bazı iletiler netlik için aşağıdaki sonuçlardan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="f2441-228">Some of the messages have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="f2441-229">Nokta algılamayı değiştirme</span><span class="sxs-lookup"><span data-stu-id="f2441-229">Change point detection</span></span>

<span data-ttu-id="f2441-230">`Change points`düzey değişiklikleri ve eğilimleri gibi değerlerin zaman serisi olay akışı dağıtımında kalıcı değişikliklerdir.</span><span class="sxs-lookup"><span data-stu-id="f2441-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="f2441-231">Bu kalıcı değişiklikler çok `spikes` daha uzun sürer ve felaket olay (lar) gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f2441-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="f2441-232">`Change points`genellikle çıplak gözle görülemez, ancak aşağıdaki yöntemdeki gibi yaklaşımlar kullanılarak verilerinizde algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="f2441-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="f2441-233">Aşağıdaki resim bir değişim noktası algılama örneğidir:</span><span class="sxs-lookup"><span data-stu-id="f2441-233">The following image is an example of a change point detection:</span></span>

![Değişiklik noktası algılamayı gösteren ekran görüntüsü.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="f2441-235">DetectChangepoint() yöntemini oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2441-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="f2441-236">Yöntem `DetectChangepoint()` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="f2441-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="f2441-237">Tahminciden dönüşümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2441-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="f2441-238">Geçmiş satış verilerine dayalı değişim noktalarını algılar.</span><span class="sxs-lookup"><span data-stu-id="f2441-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="f2441-239">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f2441-239">Displays the results.</span></span>

1. <span data-ttu-id="f2441-240">Yöntemden `DetectChangepoint()` `Main()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2441-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="f2441-241">`DetectChangepoint()` Yöntemde aşağıdaki kodla [iidChangePointEstimator'u](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2441-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="f2441-242">Daha önce yaptığınız gibi, yönteme aşağıdaki kod satırını ekleyerek tahminciden dönüştürmeyi `DetectChangePoint()` oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2441-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel2)]

1. <span data-ttu-id="f2441-243">Aşağıdaki `Transform()` kodu ekleyerek verileri dönüştürmek için `DetectChangePoint()`yöntemi kullanın:</span><span class="sxs-lookup"><span data-stu-id="f2441-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData2)]

1. <span data-ttu-id="f2441-244">Daha önce yaptığınız gibi, `transformedData` aşağıdaki kodu kullanarak `IEnumerable` `CreateEnumerable()`yöntemi kullanarak daha kolay görüntü için güçlü bir şekilde yazılan bir görüntüye dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="f2441-244">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="f2441-245">Yöntemde bir sonraki satır olarak aşağıdaki kodu `DetectChangePoint()` içeren bir ekran üstbilgisi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f2441-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader2)]

    <span data-ttu-id="f2441-246">Değişim noktası algılama sonuçlarınızda aşağıdaki bilgileri görüntülersiniz:</span><span class="sxs-lookup"><span data-stu-id="f2441-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="f2441-247">`Alert`belirli bir veri noktası için bir değişim noktası uyarısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2441-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="f2441-248">`Score`veri `ProductSales` kümesindeki belirli bir veri noktasının değeridir.</span><span class="sxs-lookup"><span data-stu-id="f2441-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="f2441-249">`P-Value`"P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f2441-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="f2441-250">P değeri 0'a ne kadar yakınsa, veri noktası nın anomali olma olasılığı da o kadar yüksektir.</span><span class="sxs-lookup"><span data-stu-id="f2441-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="f2441-251">`Martingale value`P-değerlerinin sırasına göre bir veri noktasının ne kadar "garip" olduğunu belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2441-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="f2441-252">Sonuçları aşağıdaki kodla titretin `predictions` `IEnumerable` ve görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults2)]

1. <span data-ttu-id="f2441-253">Yöntemde yönteme `DetectChangepoint()`aşağıdaki çağrıyı `Main()` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2441-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="f2441-254">Nokta algılama sonuçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="f2441-254">Change point detection results</span></span>

<span data-ttu-id="f2441-255">Sonuçlarınız aşağıdakilere benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2441-255">Your results should be similar to the following.</span></span> <span data-ttu-id="f2441-256">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f2441-256">During processing, messages are displayed.</span></span> <span data-ttu-id="f2441-257">Uyarılar veya iletileri işleme görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2441-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="f2441-258">Bazı iletiler netlik için aşağıdaki sonuçlardan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="f2441-258">Some messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="f2441-259">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="f2441-259">Congratulations!</span></span> <span data-ttu-id="f2441-260">Şimdi başarıyla ani tespit ve satış verilerinde nokta anomalileri değiştirmek için makine öğrenme modelleri oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="f2441-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="f2441-261">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2441-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="f2441-262">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="f2441-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f2441-263">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f2441-263">Load the data</span></span>
> * <span data-ttu-id="f2441-264">Ani anomali tespiti için modeli eğitin</span><span class="sxs-lookup"><span data-stu-id="f2441-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="f2441-265">Eğitimli model ile başak anomalileri tespit</span><span class="sxs-lookup"><span data-stu-id="f2441-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="f2441-266">Değişim noktası anomali tespiti için modeli eğitin</span><span class="sxs-lookup"><span data-stu-id="f2441-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="f2441-267">Eğitilmiş mod ile değişim noktası anomalilerini tespit</span><span class="sxs-lookup"><span data-stu-id="f2441-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2441-268">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f2441-268">Next steps</span></span>

<span data-ttu-id="f2441-269">Güç Tüketimi Anomali Algılama örneğini keşfetmek için GitHub deposundaki Machine Learning örneklerine göz atın.</span><span class="sxs-lookup"><span data-stu-id="f2441-269">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f2441-270">dotnet/machinelearning-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="f2441-270">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
