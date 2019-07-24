---
title: 'Öğretici: Ürün satışlardaki anormallikleri Algıla'
description: Ürün satış verileri için anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici, Visual Studio 2019 ' de kullanarak C# bir .NET Core konsol uygulaması oluşturur.
ms.date: 07/17/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: e87034733b048153202bc11ab94ed7605749f60c
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331699"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="84b05-104">Öğretici: ML.NET ile ürün satışlardaki anormallikleri Algıla</span><span class="sxs-lookup"><span data-stu-id="84b05-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="84b05-105">Ürün satış verileri için anomali algılama uygulaması oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="84b05-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="84b05-106">Bu öğretici, Visual Studio 'da kullanarak C# bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="84b05-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="84b05-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="84b05-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="84b05-108">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="84b05-108">Load the data</span></span>
> * <span data-ttu-id="84b05-109">Modeli, ani anomali algılama için eğitme</span><span class="sxs-lookup"><span data-stu-id="84b05-109">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="84b05-110">Eğitilen modeliyle ani bozukluklar algılama</span><span class="sxs-lookup"><span data-stu-id="84b05-110">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="84b05-111">Modeli değişiklik noktası anomali algılama için eğitme</span><span class="sxs-lookup"><span data-stu-id="84b05-111">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="84b05-112">Eğitilen modeliyle değişiklik noktası bozuklularını Algıla</span><span class="sxs-lookup"><span data-stu-id="84b05-112">Detect change point anomalies with the trained model</span></span>

<span data-ttu-id="84b05-113">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84b05-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84b05-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="84b05-114">Prerequisites</span></span>

* <span data-ttu-id="84b05-115">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="84b05-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="84b05-116">Product-Sales. csv veri kümesi</span><span class="sxs-lookup"><span data-stu-id="84b05-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="84b05-117">' Deki `product-sales.csv` veri biçimi, ilk olarak DataMarket 'ten kaynaklıdır ve, ramiz Hyndman tarafından oluşturulan zaman serisi veri kitaplığı (tsdl) tarafından sağlanmış olan "üç yıllık dönem içinde" Shampoo Sales "veri kümesini temel alır.</span><span class="sxs-lookup"><span data-stu-id="84b05-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span> <span data-ttu-id="84b05-118">"Üç yıllık dönem Içinde Shampoo Sales" veri kümesi, varsayılan DataMarket açık lisansı kapsamında lisanslanır.</span><span class="sxs-lookup"><span data-stu-id="84b05-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="84b05-119">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="84b05-119">Create a console application</span></span>

1. <span data-ttu-id="84b05-120">"Productsalesanomalyıdetection" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="84b05-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="84b05-121">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="84b05-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="84b05-122">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="84b05-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="84b05-123">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="84b05-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="84b05-124">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden **v 1.0.0** paketini seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="84b05-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="84b05-125">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="84b05-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="84b05-126">**Microsoft. ml. TimeSeries v 0.12.0**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="84b05-126">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="84b05-127">*Program.cs* dosyanızın en `using` üstüne aşağıdaki deyimleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="84b05-128">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="84b05-128">Download your data</span></span>

1. <span data-ttu-id="84b05-129">Veri kümesini indirin ve daha önce oluşturduğunuz *veri* klasörüne kaydedin:</span><span class="sxs-lookup"><span data-stu-id="84b05-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="84b05-130">[*Product-Sales. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) ' ye sağ tıklayın ve "bağlantıyı (veya hedefi) farklı kaydet" i seçin.</span><span class="sxs-lookup"><span data-stu-id="84b05-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="84b05-131">\*. Csv dosyasını *veri* klasörüne kaydettiğinizden ya da \*başka bir yere kaydettikten sonra,. csv dosyasını *veri* klasörüne taşıdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="84b05-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="84b05-132">Çözüm Gezgini, \*. csv dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="84b05-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="84b05-133">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="84b05-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="84b05-134">Aşağıdaki tabloda, \*. csv dosyanızdaki bir veri önizlemesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="84b05-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="84b05-135">Başından</span><span class="sxs-lookup"><span data-stu-id="84b05-135">Month</span></span>  |<span data-ttu-id="84b05-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="84b05-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="84b05-137">1-Jan</span><span class="sxs-lookup"><span data-stu-id="84b05-137">1-Jan</span></span>  |    <span data-ttu-id="84b05-138">271</span><span class="sxs-lookup"><span data-stu-id="84b05-138">271</span></span>      |
|<span data-ttu-id="84b05-139">2-Jan</span><span class="sxs-lookup"><span data-stu-id="84b05-139">2-Jan</span></span>  |    <span data-ttu-id="84b05-140">150,9</span><span class="sxs-lookup"><span data-stu-id="84b05-140">150.9</span></span>    |
|<span data-ttu-id="84b05-141">.....</span><span class="sxs-lookup"><span data-stu-id="84b05-141">.....</span></span>  |    <span data-ttu-id="84b05-142">.....</span><span class="sxs-lookup"><span data-stu-id="84b05-142">.....</span></span>    |
|<span data-ttu-id="84b05-143">1-Şub</span><span class="sxs-lookup"><span data-stu-id="84b05-143">1-Feb</span></span>  |    <span data-ttu-id="84b05-144">199,3</span><span class="sxs-lookup"><span data-stu-id="84b05-144">199.3</span></span>    |
|<span data-ttu-id="84b05-145">.....</span><span class="sxs-lookup"><span data-stu-id="84b05-145">.....</span></span>  |    <span data-ttu-id="84b05-146">.....</span><span class="sxs-lookup"><span data-stu-id="84b05-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="84b05-147">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="84b05-147">Create classes and define paths</span></span>

<span data-ttu-id="84b05-148">Sonra, giriş sınıfı veri yapınızı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="84b05-148">Next, define your input class data structure.</span></span>

<span data-ttu-id="84b05-149">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="84b05-150">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="84b05-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="84b05-151">**Yeni öğe Ekle iletişim kutusunda** **sınıf** ' ı seçin ve **ad** alanını *ProductSalesData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="84b05-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="84b05-152">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="84b05-152">Then, select the **Add** button.</span></span>

<span data-ttu-id="84b05-153">*ProductSalesData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="84b05-153">The *ProductSalesData.cs* file opens in the code editor.</span></span> <span data-ttu-id="84b05-154">Aşağıdaki `using` ifadeyi *ProductSalesData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="84b05-155">Mevcut sınıf tanımını kaldırın ve iki sınıfa `ProductSalesData` ve  `ProductSalesPrediction`ProductSalesData.cs dosyasına sahip olan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="84b05-156">`ProductSalesData`bir giriş veri sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="84b05-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="84b05-157">[Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yükleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="84b05-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> 

<span data-ttu-id="84b05-158">Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="84b05-159">Son indirilen veri kümesi dosya yolunu ve kaydedilen model dosyası yolunu tutmak için iki genel alan oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="84b05-159">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="84b05-160">`_dataPath`, modeli eğitmek için kullanılan veri kümesinin yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="84b05-160">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="84b05-161">`_docsize`veri kümesi dosyasındaki kayıt sayısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="84b05-161">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="84b05-162">Bunu hesaplamak `pvalueHistoryLength`için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="84b05-162">You'll use this to calculate `pvalueHistoryLength`.</span></span>

<span data-ttu-id="84b05-163">Aşağıdaki kodu, bu yolları belirtmek için `Main` yönteminin hemen üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-163">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="84b05-164">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="84b05-164">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="84b05-165">Entity Framework, kavramsal `DBContext` olarak da benzerdir.</span><span class="sxs-lookup"><span data-stu-id="84b05-165">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="84b05-166">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="84b05-166">Initialize variables in Main</span></span>

<span data-ttu-id="84b05-167">Yöntemi bildirmek ve başlatmak`mlContext` için yöntemindeki satırıaşağıdakikodladeğiştirin:`Console.WriteLine("Hello World!")` `Main`</span><span class="sxs-lookup"><span data-stu-id="84b05-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a><span data-ttu-id="84b05-168">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="84b05-168">Load the data</span></span>

<span data-ttu-id="84b05-169">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="84b05-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="84b05-170">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="84b05-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="84b05-171">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="84b05-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span> <span data-ttu-id="84b05-172">Aşağıdaki kodu `Main()` yönteminin sonraki satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-172">Add the following code as the next line of the `Main()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="84b05-173">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84b05-173">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="84b05-174">Veri yolu değişkenlerini alır ve döndürür `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="84b05-174">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="ml-task---time-series-anomaly-detection"></a><span data-ttu-id="84b05-175">ML görev-zaman serisi anomali algılama</span><span class="sxs-lookup"><span data-stu-id="84b05-175">ML task - time series anomaly detection</span></span> 

<span data-ttu-id="84b05-176">Anomali algılama, olağan dışı ya da beklenmeyen olaylar veya davranışları işaretler.</span><span class="sxs-lookup"><span data-stu-id="84b05-176">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="84b05-177">Sorunları nerede aramak ve "Bu tuhaf?" sorusunu cevaplamanıza yardımcı olacak ipuçları verir.</span><span class="sxs-lookup"><span data-stu-id="84b05-177">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Bu tuhaf](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="84b05-179">Anomali algılama, zaman serisi veri aykırı durumları algılama işlemidir; belirli bir giriş zaman serisini, davranışın beklenmediği veya "tuhaf" olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="84b05-179">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="84b05-180">Bu çok sayıda şekilde yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="84b05-180">This can be useful in lots of ways.</span></span> <span data-ttu-id="84b05-181">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="84b05-181">For instance:</span></span>

<span data-ttu-id="84b05-182">Bir otomobil varsa şunları bilmeniz gerekebilir: Bu yağ ölçer normal okunuyor mi, yoksa sızıntı mı var?</span><span class="sxs-lookup"><span data-stu-id="84b05-182">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="84b05-183">Güç tüketimini izliyorsanız şunları öğrenmek istersiniz: Kesinti var mı?</span><span class="sxs-lookup"><span data-stu-id="84b05-183">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="84b05-184">Tespit edilebilir iki tür zaman serisi bozukluklar vardır:</span><span class="sxs-lookup"><span data-stu-id="84b05-184">There are two types of time series anomalies that can be detected:</span></span> 

* <span data-ttu-id="84b05-185">**Ani artışlar** , sistemde anormal davranıştaki geçici bir davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="84b05-185">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span> 

* <span data-ttu-id="84b05-186">**Değişiklik noktaları** , sistemdeki zaman içindeki kalıcı değişikliklerin başlangıcını belirtir.</span><span class="sxs-lookup"><span data-stu-id="84b05-186">**Change points** indicate the beginning of persistent changes over time in the system.</span></span> 

<span data-ttu-id="84b05-187">ML.NET ' de, IID depo algılama veya IID değişiklik noktası algılama algoritmaları [bağımsız ve benzer şekilde dağıtılmış veri kümelerine](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)uygundur.</span><span class="sxs-lookup"><span data-stu-id="84b05-187">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span> 

<span data-ttu-id="84b05-188">Artışlar ve değişiklik noktalarını algılamak için aynı ürün satış verilerini analiz edersiniz.</span><span class="sxs-lookup"><span data-stu-id="84b05-188">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="84b05-189">Derleme ve eğitim modeli işlemi, ani algılama ve değişiklik noktası algılama için aynıdır; Ana fark, kullanılan belirli bir algılama algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="84b05-189">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="84b05-190">Depo algılama</span><span class="sxs-lookup"><span data-stu-id="84b05-190">Spike detection</span></span> 

<span data-ttu-id="84b05-191">Ani algılamanın amacı, zaman serisi veri değerlerinin çoğunluğunun önemli ölçüde farklı olduğu ani, geçici bir artışlarıyla 'yi belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="84b05-191">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="84b05-192">Bu şüpheli nadir öğe, olay veya gözlemlerin en aza indirme zamanında algılanması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="84b05-192">It's important to detect these suspicious rare items, events or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="84b05-193">Aşağıdaki yaklaşım,: kesintiler, Cyber saldırıları veya viral web içeriği gibi çeşitli anormallikleri algılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="84b05-193">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="84b05-194">Aşağıdaki görüntü, zaman serisi veri kümesindeki ani artışlar örneğidir:</span><span class="sxs-lookup"><span data-stu-id="84b05-194">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a><span data-ttu-id="84b05-196">Detectani () yöntemini oluşturma</span><span class="sxs-lookup"><span data-stu-id="84b05-196">Create the DetectSpike() method</span></span>

<span data-ttu-id="84b05-197">`DetectSpike()` Yöntemi`Main()` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-197">Add the following call to the `DetectSpike()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

<span data-ttu-id="84b05-198">`DetectSpike()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="84b05-198">The `DetectSpike()` method executes the following tasks:</span></span>

* <span data-ttu-id="84b05-199">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="84b05-199">Trains the model.</span></span>
* <span data-ttu-id="84b05-200">Geçmiş satış verilerine göre ani artışları algılar.</span><span class="sxs-lookup"><span data-stu-id="84b05-200">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="84b05-201">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="84b05-201">Displays the results.</span></span>

<span data-ttu-id="84b05-202">Aşağıdaki kodu kullanarak yönteminden hemen `Main()` sonra yönteminioluşturun:`DetectSpike()`</span><span class="sxs-lookup"><span data-stu-id="84b05-202">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="84b05-203">Modeli ani algılamayı eğitmek için [ııdspikeestimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) 'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="84b05-203">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="84b05-204">Aşağıdaki kodla `DetectSpike()` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-204">Add it to the `DetectSpike()` method with the following code:</span></span>

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

<span data-ttu-id="84b05-205">`DetectSpike()` Yöntemine bir sonraki kod satırı `productSales` olarak aşağıdakileri ekleyerek modeli verilere uydurun:</span><span class="sxs-lookup"><span data-stu-id="84b05-205">Fit the model to the `productSales` data by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

<span data-ttu-id="84b05-206">[Fit ()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.</span><span class="sxs-lookup"><span data-stu-id="84b05-206">The [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="84b05-207">Aşağıdaki kod satırını, `productSales` `DetectSpike()` yönteminin bir sonraki satırı olarak dönüştürmek için ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-207">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

<span data-ttu-id="84b05-208">Önceki kod, bir test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapmak üzere [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="84b05-208">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="84b05-209">`transformedData` [Createsıralanabilir ()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) yöntemini kullanarak aşağıdaki `IEnumerable` kodla daha kolay bir şekilde görüntülenmesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="84b05-209">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

<span data-ttu-id="84b05-210">Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu kullanarak bir görüntüleme üst bilgisi satırı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="84b05-210">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

<span data-ttu-id="84b05-211">Aşağıdaki bilgileri, depo algılama sonuçlarında görüntüleriz:</span><span class="sxs-lookup"><span data-stu-id="84b05-211">You'll display the following information in your spike detection results:</span></span>

* <span data-ttu-id="84b05-212">`Alert`belirli bir veri noktası için ani bir uyarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="84b05-212">`Alert` indicates a spike alert for a given data point.</span></span>

* <span data-ttu-id="84b05-213">`Score`, veri kümesindeki belirli bir veri noktasının değeridir.`ProductSales`</span><span class="sxs-lookup"><span data-stu-id="84b05-213">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>

* <span data-ttu-id="84b05-214">`P-Value`"P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="84b05-214">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="84b05-215">Bu, bu veri noktasının bir anomali olma olasılığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="84b05-215">This indicates how likely this data point is an anomaly.</span></span> 

<span data-ttu-id="84b05-216">`predictions` Üzerinde`IEnumerable` yinelemek ve sonuçları göstermek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="84b05-216">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a><span data-ttu-id="84b05-217">Depo algılama sonuçları</span><span class="sxs-lookup"><span data-stu-id="84b05-217">Spike detection results</span></span>

<span data-ttu-id="84b05-218">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84b05-218">Your results should be similar to the following.</span></span> <span data-ttu-id="84b05-219">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="84b05-219">During processing, messages are displayed.</span></span> <span data-ttu-id="84b05-220">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84b05-220">You may see warnings, or processing messages.</span></span> <span data-ttu-id="84b05-221">Bunlar, netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="84b05-221">These have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="84b05-222">Değişiklik noktası algılama</span><span class="sxs-lookup"><span data-stu-id="84b05-222">Change point detection</span></span>

<span data-ttu-id="84b05-223">`Change points`, değerlerin bir zaman serisi olay akışı dağıtımında, düzey değişiklikleri ve eğilimleri gibi kalıcı değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="84b05-223">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="84b05-224">Bu kalıcı değişiklikler en son çok daha `spikes` uzundur ve çok zararlı olay (ler) i gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="84b05-224">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="84b05-225">`Change points`genellikle çıplak göz için görünür değildir, ancak verilerinizde aşağıdaki yöntemde olduğu gibi yaklaşımlar kullanılarak algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="84b05-225">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="84b05-226">Aşağıdaki görüntü, değişiklik noktası algılamayı bir örneğidir:</span><span class="sxs-lookup"><span data-stu-id="84b05-226">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="84b05-228">DetectChangepoint () metodunu oluşturma</span><span class="sxs-lookup"><span data-stu-id="84b05-228">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="84b05-229">`DetectChangepoint()` Yöntemi`Main()` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-229">Add the following call to the `DetectChangepoint()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

<span data-ttu-id="84b05-230">`DetectChangepoint()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="84b05-230">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="84b05-231">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="84b05-231">Trains the model.</span></span>
* <span data-ttu-id="84b05-232">Geçmiş satış verilerine göre değişiklik noktalarını algılar.</span><span class="sxs-lookup"><span data-stu-id="84b05-232">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="84b05-233">Sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="84b05-233">Displays the results.</span></span>

<span data-ttu-id="84b05-234">Aşağıdaki kodu kullanarak yönteminden hemen `Main()` sonra yönteminioluşturun:`DetectChangepoint()`</span><span class="sxs-lookup"><span data-stu-id="84b05-234">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="84b05-235">[Iıdchangepointestimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) , modeli değişiklik noktası algılaması için eğitmek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84b05-235">The [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) is used to train the model for change point detection.</span></span> <span data-ttu-id="84b05-236">Aşağıdaki kodla `DetectChangepoint()` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-236">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

<span data-ttu-id="84b05-237">Daha önce yaptığınız gibi, `productSales` `DetectChangePoint()` yönteme aşağıdaki kod satırı olarak ekleyerek modeli verilere uydurun:</span><span class="sxs-lookup"><span data-stu-id="84b05-237">As you did previously, fit the model to the `productSales` data by adding the following as the next line of code in the `DetectChangePoint()` method:</span></span>

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

<span data-ttu-id="84b05-238">Aşağıdaki kodu öğesine `Training` `Transform()` ekleyerekverileridönüştürmek`DetectChangePoint()`için yöntemini kullanın:</span><span class="sxs-lookup"><span data-stu-id="84b05-238">Use the `Transform()` method to transform the `Training` data by adding the following code to `DetectChangePoint()`:</span></span>

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

<span data-ttu-id="84b05-239">Daha önce yaptığınız gibi, `transformedData` `CreateEnumerable()`yöntemi aşağıdaki kodla kullanarak daha kolay bir `IEnumerable` şekilde görüntülenmesi için, bir türü kesin belirlenmiş olarak dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="84b05-239">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

<span data-ttu-id="84b05-240">`DetectChangePoint()` Yönteminde bir sonraki satır olarak aşağıdaki kodla bir görüntüleme üstbilgisi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="84b05-240">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

<span data-ttu-id="84b05-241">Değişiklik noktası algılama sonuçlarında aşağıdaki bilgileri görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="84b05-241">You'll display the following information in your change point detection results:</span></span>

* <span data-ttu-id="84b05-242">`Alert`belirli bir veri noktası için bir değişiklik noktası uyarısı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="84b05-242">`Alert` indicates a change point alert for a given data point.</span></span>
* <span data-ttu-id="84b05-243">`Score`, veri kümesindeki belirli bir veri noktasının değeridir.`ProductSales`</span><span class="sxs-lookup"><span data-stu-id="84b05-243">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
* <span data-ttu-id="84b05-244">`P-Value`"P" olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="84b05-244">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="84b05-245">Bu, bu veri noktasının bir anomali olma olasılığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="84b05-245">This indicates how likely this data point is an anomaly.</span></span> 
* <span data-ttu-id="84b05-246">`Martingale value`, P-değerleri dizisine göre "tuhaf" bir veri noktasının nasıl olduğunu belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84b05-246">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>  

<span data-ttu-id="84b05-247">`predictions` Üzerinde`IEnumerable` yineleme yapın ve sonuçları aşağıdaki kodla görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="84b05-247">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a><span data-ttu-id="84b05-248">Nokta algılama sonuçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="84b05-248">Change point detection results</span></span>

<span data-ttu-id="84b05-249">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84b05-249">Your results should be similar to the following.</span></span> <span data-ttu-id="84b05-250">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="84b05-250">During processing, messages are displayed.</span></span> <span data-ttu-id="84b05-251">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84b05-251">You may see warnings, or processing messages.</span></span> <span data-ttu-id="84b05-252">Bunlar, netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="84b05-252">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="84b05-253">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="84b05-253">Congratulations!</span></span> <span data-ttu-id="84b05-254">Artık, satış verilerinde ani artışları ve değişiklik noktası bozukluklarını algılamak için makine öğrenimi modellerini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="84b05-254">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="84b05-255">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84b05-255">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="84b05-256">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="84b05-256">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="84b05-257">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="84b05-257">Load the data</span></span>
> * <span data-ttu-id="84b05-258">Modeli, ani anomali algılama için eğitme</span><span class="sxs-lookup"><span data-stu-id="84b05-258">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="84b05-259">Eğitilen modeliyle ani bozukluklar algılama</span><span class="sxs-lookup"><span data-stu-id="84b05-259">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="84b05-260">Modeli değişiklik noktası anomali algılama için eğitme</span><span class="sxs-lookup"><span data-stu-id="84b05-260">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="84b05-261">Eğitilen mod ile değişiklik noktası bozuklulıkları Algıla</span><span class="sxs-lookup"><span data-stu-id="84b05-261">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="84b05-262">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="84b05-262">Next steps</span></span>

<span data-ttu-id="84b05-263">Güç tüketimi anomali algılama örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="84b05-263">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="84b05-264">DotNet/machinöğrenim-Samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="84b05-264">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
