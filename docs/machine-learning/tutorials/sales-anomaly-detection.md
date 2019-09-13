---
title: 'Öğretici: Ürün satışlardaki anormallikleri Algıla'
description: Ürün satış verileri için anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici, Visual Studio 2019 ' de kullanarak C# bir .NET Core konsol uygulaması oluşturur.
ms.date: 07/17/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: ed75f1ba0b102ba73eb5671667b5731519c12eb0
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929051"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="e0608-104">Öğretici: ML.NET ile ürün satışlardaki anormallikleri Algıla</span><span class="sxs-lookup"><span data-stu-id="e0608-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="e0608-105">Ürün satış verileri için anomali algılama uygulaması oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e0608-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="e0608-106">Bu öğretici, Visual Studio 'da kullanarak C# bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0608-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="e0608-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="e0608-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="e0608-108">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="e0608-108">Load the data</span></span>
> * <span data-ttu-id="e0608-109">Ani anomali algılama için bir dönüşüm oluşturun</span><span class="sxs-lookup"><span data-stu-id="e0608-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="e0608-110">Dönüşümle birlikte ani bozukluklar Algıla</span><span class="sxs-lookup"><span data-stu-id="e0608-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="e0608-111">Değişiklik noktası anomali algılama için bir dönüşüm oluşturun</span><span class="sxs-lookup"><span data-stu-id="e0608-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="e0608-112">Dönüşümle değişiklik noktası bozuklularını Algıla</span><span class="sxs-lookup"><span data-stu-id="e0608-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="e0608-113">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0608-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e0608-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e0608-114">Prerequisites</span></span>

* <span data-ttu-id="e0608-115">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="e0608-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="e0608-116">Product-Sales. csv veri kümesi</span><span class="sxs-lookup"><span data-stu-id="e0608-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="e0608-117">' Deki `product-sales.csv` veri biçimi, ilk olarak DataMarket 'ten kaynaklıdır ve, ramiz Hyndman tarafından oluşturulan zaman serisi veri kitaplığı (tsdl) tarafından sağlanmış olan "üç yıllık dönem içinde" Shampoo Sales "veri kümesini temel alır.</span><span class="sxs-lookup"><span data-stu-id="e0608-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="e0608-118">"Üç yıllık dönem Içinde Shampoo Sales" veri kümesi, varsayılan DataMarket açık lisansı kapsamında lisanslanır.</span><span class="sxs-lookup"><span data-stu-id="e0608-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e0608-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0608-119">Create a console application</span></span>

1. <span data-ttu-id="e0608-120">"Productsalesanomalyıdetection" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0608-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="e0608-121">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0608-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="e0608-122">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="e0608-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="e0608-123">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e0608-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="e0608-124">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden **v 1.0.0** paketini seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e0608-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="e0608-125">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e0608-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="e0608-126">**Microsoft. ml. TimeSeries v 0.12.0**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="e0608-126">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="e0608-127">*Program.cs* dosyanızın en `using` üstüne aşağıdaki deyimleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="e0608-128">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="e0608-128">Download your data</span></span>

1. <span data-ttu-id="e0608-129">Veri kümesini indirin ve daha önce oluşturduğunuz *veri* klasörüne kaydedin:</span><span class="sxs-lookup"><span data-stu-id="e0608-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="e0608-130">[*Product-Sales. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) ' ye sağ tıklayın ve "bağlantıyı (veya hedefi) farklı kaydet" i seçin.</span><span class="sxs-lookup"><span data-stu-id="e0608-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="e0608-131">\*. Csv dosyasını *veri* klasörüne kaydettiğinizden ya da \*başka bir yere kaydettikten sonra,. csv dosyasını *veri* klasörüne taşıdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e0608-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="e0608-132">Çözüm Gezgini, \*. csv dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e0608-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="e0608-133">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0608-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="e0608-134">Aşağıdaki tabloda, \*. csv dosyanızdaki bir veri önizlemesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0608-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="e0608-135">Başından</span><span class="sxs-lookup"><span data-stu-id="e0608-135">Month</span></span>  |<span data-ttu-id="e0608-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="e0608-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="e0608-137">1-Jan</span><span class="sxs-lookup"><span data-stu-id="e0608-137">1-Jan</span></span>  |    <span data-ttu-id="e0608-138">271</span><span class="sxs-lookup"><span data-stu-id="e0608-138">271</span></span>      |
|<span data-ttu-id="e0608-139">2-Jan</span><span class="sxs-lookup"><span data-stu-id="e0608-139">2-Jan</span></span>  |    <span data-ttu-id="e0608-140">150,9</span><span class="sxs-lookup"><span data-stu-id="e0608-140">150.9</span></span>    |
|<span data-ttu-id="e0608-141">.....</span><span class="sxs-lookup"><span data-stu-id="e0608-141">.....</span></span>  |    <span data-ttu-id="e0608-142">.....</span><span class="sxs-lookup"><span data-stu-id="e0608-142">.....</span></span>    |
|<span data-ttu-id="e0608-143">1-Şub</span><span class="sxs-lookup"><span data-stu-id="e0608-143">1-Feb</span></span>  |    <span data-ttu-id="e0608-144">199,3</span><span class="sxs-lookup"><span data-stu-id="e0608-144">199.3</span></span>    |
|<span data-ttu-id="e0608-145">.....</span><span class="sxs-lookup"><span data-stu-id="e0608-145">.....</span></span>  |    <span data-ttu-id="e0608-146">.....</span><span class="sxs-lookup"><span data-stu-id="e0608-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="e0608-147">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="e0608-147">Create classes and define paths</span></span>

<span data-ttu-id="e0608-148">Sonra, giriş ve tahmin sınıfı veri yapılarınızı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e0608-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="e0608-149">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="e0608-150">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e0608-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="e0608-151">**Yeni öğe Ekle iletişim kutusunda** **sınıf** ' ı seçin ve **ad** alanını *ProductSalesData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0608-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="e0608-152">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e0608-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="e0608-153">*ProductSalesData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="e0608-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="e0608-154">Aşağıdaki `using` ifadeyi *ProductSalesData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="e0608-155">Mevcut sınıf tanımını kaldırın ve iki sınıfa `ProductSalesData` ve `ProductSalesPrediction`ProductSalesData.cs dosyasına sahip olan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="e0608-156">`ProductSalesData`bir giriş veri sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0608-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="e0608-157">[Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yükleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0608-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="e0608-158">`ProductSalesPrediction`tahmin verileri sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0608-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="e0608-159">Anomali algılama için tahmin, bir anomali, ham puan ve p değeri olup olmadığını belirten bir uyarıdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0608-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="e0608-160">P değeri 0 ' a yaklaşarak daha büyük bir anomali meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="e0608-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="e0608-161">Son indirilen veri kümesi dosya yolunu ve kaydedilen model dosyası yolunu tutmak için iki genel alan oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e0608-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="e0608-162">`_dataPath`, modeli eğitmek için kullanılan veri kümesinin yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e0608-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="e0608-163">`_docsize`veri kümesi dosyasındaki kayıt sayısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e0608-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="e0608-164">Öğesini hesaplamak `_docSize` `pvalueHistoryLength`için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e0608-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="e0608-165">Aşağıdaki kodu, bu yolları belirtmek için `Main` yönteminin hemen üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="e0608-166">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="e0608-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="e0608-167">Yöntemi bildirmek ve başlatmak`mlContext` için yöntemindeki satırıaşağıdakikodladeğiştirin:`Console.WriteLine("Hello World!")` `Main`</span><span class="sxs-lookup"><span data-stu-id="e0608-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="e0608-168">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0608-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="e0608-169">Entity Framework, kavramsal `DBContext` olarak da benzerdir.</span><span class="sxs-lookup"><span data-stu-id="e0608-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="e0608-170">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="e0608-170">Load the data</span></span>

<span data-ttu-id="e0608-171">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="e0608-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="e0608-172">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="e0608-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="e0608-173">Veriler bir metin dosyasından veya diğer kaynaklardan (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e0608-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="e0608-174">Aşağıdaki kodu `Main()` yönteminin sonraki satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="e0608-175">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e0608-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="e0608-176">Veri yolu değişkenlerini alır ve döndürür `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="e0608-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="e0608-177">Zaman serisi anomali algılama</span><span class="sxs-lookup"><span data-stu-id="e0608-177">Time series anomaly detection</span></span>

<span data-ttu-id="e0608-178">Anomali algılama, olağan dışı ya da beklenmeyen olaylar veya davranışları işaretler.</span><span class="sxs-lookup"><span data-stu-id="e0608-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="e0608-179">Sorunları nerede aramak ve "Bu tuhaf?" sorusunu cevaplamanıza yardımcı olacak ipuçları verir.</span><span class="sxs-lookup"><span data-stu-id="e0608-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Bu tuhaf](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="e0608-181">Anomali algılama, zaman serisi veri aykırı durumları algılama işlemidir; belirli bir giriş zaman serisini, davranışın beklenmediği veya "tuhaf" olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0608-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="e0608-182">Anomali algılama çok sayıda şekilde yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0608-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="e0608-183">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e0608-183">For instance:</span></span>

<span data-ttu-id="e0608-184">Bir otomobil varsa şunları bilmeniz gerekebilir: Bu yağ ölçer normal okunuyor mi, yoksa sızıntı mı var?</span><span class="sxs-lookup"><span data-stu-id="e0608-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="e0608-185">Güç tüketimini izliyorsanız şunları öğrenmek istersiniz: Kesinti var mı?</span><span class="sxs-lookup"><span data-stu-id="e0608-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="e0608-186">Tespit edilebilir iki tür zaman serisi bozukluklar vardır:</span><span class="sxs-lookup"><span data-stu-id="e0608-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="e0608-187">**Ani artışlar** , sistemde anormal davranıştaki geçici bir davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0608-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="e0608-188">**Değişiklik noktaları** , sistemdeki zaman içindeki kalıcı değişikliklerin başlangıcını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0608-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="e0608-189">ML.NET ' de, IID depo algılama veya IID değişiklik noktası algılama algoritmaları [bağımsız ve benzer şekilde dağıtılmış veri kümelerine](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)uygundur.</span><span class="sxs-lookup"><span data-stu-id="e0608-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="e0608-190">Diğer öğreticilerdeki modellerin aksine, anomali algılayıcı dönüştürmeleri doğrudan giriş verilerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e0608-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="e0608-191">`IEstimator.Fit()` Metodun dönüştürmeyi üretmek için eğitim verileri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e0608-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="e0608-192">, Boş bir listesinden `ProductSalesData`oluşturulan veri görünümü tarafından sağlanmış olan veri şemasına gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="e0608-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="e0608-193">Artışlar ve değişiklik noktalarını algılamak için aynı ürün satış verilerini analiz edersiniz.</span><span class="sxs-lookup"><span data-stu-id="e0608-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="e0608-194">Derleme ve eğitim modeli işlemi, ani algılama ve değişiklik noktası algılama için aynıdır; Ana fark, kullanılan belirli bir algılama algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e0608-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="e0608-195">Depo algılama</span><span class="sxs-lookup"><span data-stu-id="e0608-195">Spike detection</span></span>

<span data-ttu-id="e0608-196">Ani algılamanın amacı, zaman serisi veri değerlerinin çoğunluğunun önemli ölçüde farklı olduğu ani, geçici bir artışlarıyla 'yi belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="e0608-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="e0608-197">Bu şüpheli nadir öğe, olay veya gözlemlerin en aza indirme zamanında algılanması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e0608-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="e0608-198">Aşağıdaki yaklaşım,: kesintiler, Cyber saldırıları veya viral web içeriği gibi çeşitli anormallikleri algılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0608-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="e0608-199">Aşağıdaki görüntü, zaman serisi veri kümesindeki ani artışlar örneğidir:</span><span class="sxs-lookup"><span data-stu-id="e0608-199">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="e0608-201">CreateEmptyDataView () yöntemi ekleme</span><span class="sxs-lookup"><span data-stu-id="e0608-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="e0608-202">Aşağıdaki yöntemi öğesine `Program.cs`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="e0608-203">, `CreateEmptyDataView()` `IEstimator.Fit()` Yönteme giriş olarak kullanılacak doğru şemaya sahip boş bir veri görünümü nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0608-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="e0608-204">Detectani () yöntemini oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0608-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="e0608-205">`DetectSpike()` Yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e0608-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="e0608-206">Estimator 'dan dönüşüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0608-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="e0608-207">Geçmiş satış verilerine göre ani artışları algılar.</span><span class="sxs-lookup"><span data-stu-id="e0608-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="e0608-208">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e0608-208">Displays the results.</span></span>

1. <span data-ttu-id="e0608-209">Aşağıdaki kodu kullanarak yönteminden hemen `Main()` sonra yönteminioluşturun:`DetectSpike()`</span><span class="sxs-lookup"><span data-stu-id="e0608-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="e0608-210">Modeli ani algılamayı eğitmek için [ııdspikeestimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) 'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0608-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="e0608-211">Aşağıdaki kodla `DetectSpike()` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="e0608-212">`DetectSpike()` Yöntemine sonraki kod satırı olarak aşağıdakini ekleyerek depo algılama dönüşümü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e0608-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

1. <span data-ttu-id="e0608-213">Aşağıdaki kod satırını, `productSales` `DetectSpike()` yönteminin bir sonraki satırı olarak dönüştürmek için ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

    <span data-ttu-id="e0608-214">Önceki kod, bir veri kümesinin birden çok giriş satırına ilişkin tahminleri yapmak için [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0608-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="e0608-215">`transformedData` [Createsıralanabilir ()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) yöntemini kullanarak aşağıdaki `IEnumerable` kodla daha kolay bir şekilde görüntülenmesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="e0608-215">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="e0608-216">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu kullanarak bir görüntüleme üst bilgisi satırı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e0608-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

    <span data-ttu-id="e0608-217">Aşağıdaki bilgileri, depo algılama sonuçlarında görüntüleriz:</span><span class="sxs-lookup"><span data-stu-id="e0608-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="e0608-218">`Alert`belirli bir veri noktası için ani bir uyarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0608-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="e0608-219">`Score`, veri kümesindeki belirli bir veri noktasının değeridir.`ProductSales`</span><span class="sxs-lookup"><span data-stu-id="e0608-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="e0608-220">`P-Value`"P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e0608-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="e0608-221">P değerinin 0 olması, büyük olasılıkla veri noktasının bir anomali olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0608-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="e0608-222">`predictions` Üzerinde`IEnumerable` yinelemek ve sonuçları göstermek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="e0608-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

1. <span data-ttu-id="e0608-223">Yöntemine`Main()` çağrı `DetectSpike()`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="e0608-224">Depo algılama sonuçları</span><span class="sxs-lookup"><span data-stu-id="e0608-224">Spike detection results</span></span>

<span data-ttu-id="e0608-225">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0608-225">Your results should be similar to the following.</span></span> <span data-ttu-id="e0608-226">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e0608-226">During processing, messages are displayed.</span></span> <span data-ttu-id="e0608-227">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0608-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="e0608-228">Bazı iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e0608-228">Some of the messages have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="e0608-229">Değişiklik noktası algılama</span><span class="sxs-lookup"><span data-stu-id="e0608-229">Change point detection</span></span>

<span data-ttu-id="e0608-230">`Change points`, değerlerin bir zaman serisi olay akışı dağıtımında, düzey değişiklikleri ve eğilimleri gibi kalıcı değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="e0608-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="e0608-231">Bu kalıcı değişiklikler en son çok daha `spikes` uzundur ve çok zararlı olay (ler) i gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e0608-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="e0608-232">`Change points`genellikle çıplak göz için görünür değildir, ancak verilerinizde aşağıdaki yöntemde olduğu gibi yaklaşımlar kullanılarak algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="e0608-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="e0608-233">Aşağıdaki görüntü, değişiklik noktası algılamayı bir örneğidir:</span><span class="sxs-lookup"><span data-stu-id="e0608-233">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="e0608-235">DetectChangepoint () metodunu oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0608-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="e0608-236">`DetectChangepoint()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="e0608-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="e0608-237">Estimator 'dan dönüşüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0608-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="e0608-238">Geçmiş satış verilerine göre değişiklik noktalarını algılar.</span><span class="sxs-lookup"><span data-stu-id="e0608-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="e0608-239">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e0608-239">Displays the results.</span></span>

1. <span data-ttu-id="e0608-240">Aşağıdaki kodu kullanarak yönteminden hemen `Main()` sonra yönteminioluşturun:`DetectChangepoint()`</span><span class="sxs-lookup"><span data-stu-id="e0608-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="e0608-241">`DetectChangepoint()` Yönteminde aşağıdaki kodla birlikte [ııdchangepointestimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e0608-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="e0608-242">Daha önce yaptığınız gibi, aşağıdaki kod `DetectChangePoint()` satırını yöntemine ekleyerek tahmin aracı 'dan dönüştürmeyi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e0608-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

1. <span data-ttu-id="e0608-243">Aşağıdaki kodu öğesine `DetectChangePoint()`ekleyerek verileri dönüştürmek için yönteminikullanın:`Transform()`</span><span class="sxs-lookup"><span data-stu-id="e0608-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

1. <span data-ttu-id="e0608-244">Daha önce yaptığınız gibi, `transformedData` `CreateEnumerable()`yöntemi aşağıdaki kodla kullanarak daha kolay bir `IEnumerable` şekilde görüntülenmesi için, bir türü kesin belirlenmiş olarak dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="e0608-244">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="e0608-245">`DetectChangePoint()` Yönteminde bir sonraki satır olarak aşağıdaki kodla bir görüntüleme üstbilgisi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e0608-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

    <span data-ttu-id="e0608-246">Değişiklik noktası algılama sonuçlarında aşağıdaki bilgileri görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0608-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="e0608-247">`Alert`belirli bir veri noktası için bir değişiklik noktası uyarısı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0608-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="e0608-248">`Score`, veri kümesindeki belirli bir veri noktasının değeridir.`ProductSales`</span><span class="sxs-lookup"><span data-stu-id="e0608-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="e0608-249">`P-Value`"P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e0608-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="e0608-250">P değerinin 0 olması, büyük olasılıkla veri noktasının bir anomali olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0608-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="e0608-251">`Martingale value`, P-değerleri dizisine göre "tuhaf" bir veri noktasının nasıl olduğunu belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0608-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="e0608-252">`predictions` Üzerinde`IEnumerable` yineleme yapın ve sonuçları aşağıdaki kodla görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

1. <span data-ttu-id="e0608-253">`Main()` Yöntemine aşağıdaki çağrıyı `DetectChangepoint()`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0608-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="e0608-254">Nokta algılama sonuçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="e0608-254">Change point detection results</span></span>

<span data-ttu-id="e0608-255">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0608-255">Your results should be similar to the following.</span></span> <span data-ttu-id="e0608-256">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e0608-256">During processing, messages are displayed.</span></span> <span data-ttu-id="e0608-257">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0608-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="e0608-258">Bazı iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e0608-258">Some messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="e0608-259">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="e0608-259">Congratulations!</span></span> <span data-ttu-id="e0608-260">Artık, satış verilerinde ani artışları ve değişiklik noktası bozukluklarını algılamak için makine öğrenimi modellerini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="e0608-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="e0608-261">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0608-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="e0608-262">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="e0608-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="e0608-263">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="e0608-263">Load the data</span></span>
> * <span data-ttu-id="e0608-264">Modeli, ani anomali algılama için eğitme</span><span class="sxs-lookup"><span data-stu-id="e0608-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="e0608-265">Eğitilen modeliyle ani bozukluklar algılama</span><span class="sxs-lookup"><span data-stu-id="e0608-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="e0608-266">Modeli değişiklik noktası anomali algılama için eğitme</span><span class="sxs-lookup"><span data-stu-id="e0608-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="e0608-267">Eğitilen mod ile değişiklik noktası bozuklulıkları Algıla</span><span class="sxs-lookup"><span data-stu-id="e0608-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="e0608-268">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e0608-268">Next steps</span></span>

<span data-ttu-id="e0608-269">Güç tüketimi anomali algılama örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="e0608-269">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e0608-270">DotNet/machinöğrenim-Samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="e0608-270">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
