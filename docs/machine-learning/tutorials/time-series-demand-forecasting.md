---
title: 'Öğretici: Tahmin bisiklet kiralama talebi - zaman serisi'
description: Bu öğretici, tek değişkenli zaman serisi analizi ve ML.NET kullanarak bir bisiklet kiralama hizmeti için talebi tahmin nasıl gösterir.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: bceb32f4ea22ade6d3b49b3a99d7ec48a7ba168d
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607408"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="50300-103">Öğretici: Zaman serisi analizi ve ML.NET ile tahmin bisiklet kiralama hizmeti talebi</span><span class="sxs-lookup"><span data-stu-id="50300-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="50300-104">ML.NET ile sql server veritabanında depolanan veriler üzerinde tek değişkenli zaman serisi analizini kullanarak bisiklet kiralama hizmeti talebini nasıl tahmin edebilirsiniz öğrenin.</span><span class="sxs-lookup"><span data-stu-id="50300-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="50300-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="50300-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="50300-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="50300-106">Understand the problem</span></span>
> * <span data-ttu-id="50300-107">Veritabanından veri yükleme</span><span class="sxs-lookup"><span data-stu-id="50300-107">Load data from a database</span></span>
> * <span data-ttu-id="50300-108">Tahmin modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="50300-108">Create a forecasting model</span></span>
> * <span data-ttu-id="50300-109">Tahmin modelini değerlendirme</span><span class="sxs-lookup"><span data-stu-id="50300-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="50300-110">Tahmin modelini kaydetme</span><span class="sxs-lookup"><span data-stu-id="50300-110">Save a forecasting model</span></span>
> * <span data-ttu-id="50300-111">Tahmin modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="50300-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="50300-112">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="50300-112">Prerequisites</span></span>

- <span data-ttu-id="50300-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonrası veya Visual Studio 2017 sürümü 15.6 veya daha sonra ".NET Core çapraz platform geliştirme" iş yükü yüklü.</span><span class="sxs-lookup"><span data-stu-id="50300-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="50300-114">Zaman serisi tahmin örnek genel bakış</span><span class="sxs-lookup"><span data-stu-id="50300-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="50300-115">Bu örnek, Tek Spektrum Analizi olarak bilinen tek değişkenli zaman serileri analiz algoritması kullanarak bisiklet kiralama talebini tahmin eden bir **C# .NET Core konsol uygulamasıdır.**</span><span class="sxs-lookup"><span data-stu-id="50300-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="50300-116">Bu örneğin kodu GitHub'daki [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="50300-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="50300-117">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="50300-117">Understand the problem</span></span>

<span data-ttu-id="50300-118">Verimli bir çalışma yürütmek için, envanter yönetimi önemli bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="50300-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="50300-119">Stokta çok fazla ürün olması, raflarda yer alan satılmayan ürünlerin herhangi bir gelir getirmeyecek olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="50300-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="50300-120">Çok az ürün olması, satışların kaybolmasına ve müşterilere rakiplerinden satın alma yol açar.</span><span class="sxs-lookup"><span data-stu-id="50300-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="50300-121">Bu nedenle, sürekli soru, ne stok en uygun miktarda elde tutmak nedir?</span><span class="sxs-lookup"><span data-stu-id="50300-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="50300-122">Zaman serisi çözümlemesi, geçmiş verilere bakarak, desenleri tanımlayarak ve gelecekte değerleri tahmin etmek için bu bilgileri kullanarak bu soruların yanıtlanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="50300-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="50300-123">Bu öğreticide kullanılan verileri çözümleme tekniği, tek değişkenli zaman serisi çözümlemesidir.</span><span class="sxs-lookup"><span data-stu-id="50300-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="50300-124">Univariate zaman serisi analizi, aylık satışlar gibi belirli aralıklarla belirli aralıklarla belirli bir zaman dilimi içinde tek bir sayısal gözleme bakar.</span><span class="sxs-lookup"><span data-stu-id="50300-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="50300-125">Bu eğitimde kullanılan algoritma [Tek Spektrum Analizi(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf)olduğunu.</span><span class="sxs-lookup"><span data-stu-id="50300-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="50300-126">SSA, bir zaman serisini bir dizi ana bileşene ayrıştarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="50300-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="50300-127">Bu bileşenler, bir sinyalin eğilimlere, gürültüye, mevsimselliğe ve diğer birçok faktöre karşılık gelen parçaları olarak yorumlanabilir.</span><span class="sxs-lookup"><span data-stu-id="50300-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="50300-128">Daha sonra, bu bileşenler yeniden oluşturulur ve gelecekte bir süre değerleri tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50300-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="50300-129">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="50300-129">Create console application</span></span>

1. <span data-ttu-id="50300-130">"BikeDemandForecasting" adlı yeni bir **C# .NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50300-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="50300-131">sürüm **1.4.0** NuGet **paketini Microsoft.ML** yükleyin</span><span class="sxs-lookup"><span data-stu-id="50300-131">Install **Microsoft.ML** version **1.4.0** NuGet package</span></span>
    1. <span data-ttu-id="50300-132">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="50300-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="50300-133">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, **Gözat** sekmesini seçin, **Microsoft.ML**arayın.</span><span class="sxs-lookup"><span data-stu-id="50300-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="50300-134">Yayın **aet'i ekle** onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="50300-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="50300-135">**Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="50300-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="50300-136">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="50300-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="50300-137">**System.Data.SqlClient** sürüm **4.7.0** ve **Microsoft.ML.TimeSeries** sürüm **1.4.0**için bu adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="50300-137">Repeat these steps for **System.Data.SqlClient** version **4.7.0** and **Microsoft.ML.TimeSeries** version **1.4.0**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="50300-138">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="50300-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="50300-139">*Veri*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50300-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="50300-140">[ *DailyDemand.mdf* veritabanı dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) indirin ve *Veri* dizinine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="50300-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="50300-141">Bu öğreticide kullanılan veriler [UCI Bike Sharing Dataset'ten](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)gelir.</span><span class="sxs-lookup"><span data-stu-id="50300-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="50300-142">Fanaee-T, Hadi ve Gama, Joao, 'Topluluk dedektörleri ve arka plan bilgisi birleştiren olay etiketleme', İlerleme Yapay Zeka (2013): s. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="50300-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="50300-143">Orijinal veri kümesi mevsimsellik ve hava koşullarına karşılık gelen birkaç sütun içerir.</span><span class="sxs-lookup"><span data-stu-id="50300-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="50300-144">Kısaltma için ve bu öğreticide kullanılan algoritma yalnızca tek bir sayısal sütundaki değerleri gerektirdiğinden, özgün veri kümesi yalnızca aşağıdaki sütunları içerecek şekilde yoğunlaştırılmıştır:</span><span class="sxs-lookup"><span data-stu-id="50300-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="50300-145">**dteday**: Gözlem tarihi.</span><span class="sxs-lookup"><span data-stu-id="50300-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="50300-146">**yıl**: Gözlemin kodlanmış yılı (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="50300-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="50300-147">**cnt**: O gün için toplam bisiklet kiralama sayısı.</span><span class="sxs-lookup"><span data-stu-id="50300-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="50300-148">Özgün veri kümesi, sql server veritabanında aşağıdaki şemaya sahip bir veritabanı tablosuna eşlenir.</span><span class="sxs-lookup"><span data-stu-id="50300-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="50300-149">Aşağıdaki verilerin bir örneğidir:</span><span class="sxs-lookup"><span data-stu-id="50300-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="50300-150">Kiralama Tarihi</span><span class="sxs-lookup"><span data-stu-id="50300-150">RentalDate</span></span> | <span data-ttu-id="50300-151">Yıl</span><span class="sxs-lookup"><span data-stu-id="50300-151">Year</span></span> | <span data-ttu-id="50300-152">Toplam Kiralama</span><span class="sxs-lookup"><span data-stu-id="50300-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="50300-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="50300-153">1/1/2011</span></span>|<span data-ttu-id="50300-154">0</span><span class="sxs-lookup"><span data-stu-id="50300-154">0</span></span>|<span data-ttu-id="50300-155">985</span><span class="sxs-lookup"><span data-stu-id="50300-155">985</span></span>|
|<span data-ttu-id="50300-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="50300-156">1/2/2011</span></span>|<span data-ttu-id="50300-157">0</span><span class="sxs-lookup"><span data-stu-id="50300-157">0</span></span>|<span data-ttu-id="50300-158">801</span><span class="sxs-lookup"><span data-stu-id="50300-158">801</span></span>|
|<span data-ttu-id="50300-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="50300-159">1/3/2011</span></span>|<span data-ttu-id="50300-160">0</span><span class="sxs-lookup"><span data-stu-id="50300-160">0</span></span>|<span data-ttu-id="50300-161">1349</span><span class="sxs-lookup"><span data-stu-id="50300-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="50300-162">Giriş ve çıktı sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="50300-162">Create input and output classes</span></span>

1. <span data-ttu-id="50300-163">*Dosya Program.csyı açın* `using` ve varolan deyimleri aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="50300-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="50300-164">`ModelInput` sınıfını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50300-164">Create `ModelInput` class.</span></span> <span data-ttu-id="50300-165">`Program` Sınıfın altına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="50300-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="50300-166">Sınıf `ModelInput` aşağıdaki sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="50300-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="50300-167">**Kiralama Tarihi**: Gözlem tarihi.</span><span class="sxs-lookup"><span data-stu-id="50300-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="50300-168">**Yıl**: Gözlemin kodlanmış yılı (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="50300-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="50300-169">**Toplam Kiralama**: O gün için toplam bisiklet kiralama sayısı.</span><span class="sxs-lookup"><span data-stu-id="50300-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="50300-170">Yeni `ModelOutput` oluşturulan sınıfın `ModelInput` altında sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50300-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="50300-171">Sınıf `ModelOutput` aşağıdaki sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="50300-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="50300-172">**Tahmini Kiralamalar**: Tahmin edilen dönem için öngörülen değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="50300-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="50300-173">**LowerBoundRentals**: Öngörülen dönem için öngörülen minimum değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="50300-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="50300-174">**UpperBoundRentals**: Tahmin edilen dönem için öngörülen maksimum değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="50300-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="50300-175">Yolları tanımlayın ve değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="50300-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="50300-176">Yöntemin `Main` içinde, verilerinizin konumunu, bağlantı dizesini ve eğitilmiş modeli nerede kaydedebileceğinizi depolamak için değişkenleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="50300-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="50300-177">Yönteme `mlContext` aşağıdaki satırı ekleyerek [`MLContext`](xref:Microsoft.ML.MLContext) değişkeni yeni bir örnekle başharfe ait hale getirmek. `Main`</span><span class="sxs-lookup"><span data-stu-id="50300-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="50300-178">Sınıf [`MLContext`](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç noktasıdır ve mlContext'ı başlatmak, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50300-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="50300-179">Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.</span><span class="sxs-lookup"><span data-stu-id="50300-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="50300-180">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="50300-180">Load the data</span></span>

1. <span data-ttu-id="50300-181">Bu `DatabaseLoader` tür `ModelInput`kayıtları yükler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50300-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="50300-182">Veritabanından veri yüklemek için sorgu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="50300-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="50300-183">ML.NET algoritmaları veri türü [`Single`](xref:System.Single)olmasını bekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="50300-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="50300-184">Bu nedenle, tür [`Real`](xref:System.Data.SqlDbType)olmayan veritabanından gelen sayısal değerlerin , tek bir hassas kayan nokta [`Real`](xref:System.Data.SqlDbType)değerine dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="50300-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="50300-185">Ve `Year` `TotalRental` sütunlar veritabanında hem de sasayı türleridir.</span><span class="sxs-lookup"><span data-stu-id="50300-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="50300-186">Dahili `CAST` işlevi kullanarak, her ikisi `Real`de döküm .</span><span class="sxs-lookup"><span data-stu-id="50300-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="50300-187">Veritabanına `DatabaseSource` bağlanmak için a oluşturun ve sorguyu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="50300-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="50300-188">Verileri bir `IDataView`' ye yükleyin.</span><span class="sxs-lookup"><span data-stu-id="50300-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="50300-189">Veri kümesi iki yıllık veri içerir.</span><span class="sxs-lookup"><span data-stu-id="50300-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="50300-190">Yalnızca ilk yıla ait veriler eğitim için kullanılır, ikinci yıl ise model tarafından üretilen tahminle gerçek değerleri karşılaştırmak için düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="50300-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="50300-191">Dönüşümü kullanarak verileri [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="50300-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="50300-192">İlk yıl için, `Year` `upperBound` parametre 1 olarak ayarlanırken yalnızca sütundaki 1'den küçük değerler seçilir.</span><span class="sxs-lookup"><span data-stu-id="50300-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="50300-193">Tersine, ikinci yıl için, parametre 1'e `lowerBound` ayarlayarak 1'den büyük veya eşit değerler seçilir.</span><span class="sxs-lookup"><span data-stu-id="50300-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="50300-194">Zaman serisi analiz boru hattını tanımla</span><span class="sxs-lookup"><span data-stu-id="50300-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="50300-195">Zaman serisi veri kümesindeki değerleri tahmin etmek için [SsaForecastingEstimator'u](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) kullanan bir ardışık kaynak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="50300-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="50300-196">İlk `forecastingPipeline` yıl için 365 veri puanı alır ve zaman serisi veri kümesini `seriesLength` parametrede belirtildiği şekilde 30 günlük (aylık) aralıklara böler.</span><span class="sxs-lookup"><span data-stu-id="50300-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="50300-197">Bu örneklerin her biri haftalık veya 7 günlük bir süre ile analiz edilir.</span><span class="sxs-lookup"><span data-stu-id="50300-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="50300-198">Bir sonraki dönem(ler) için öngörülen değerin ne olduğu belirlenirken, önceki yedi güne ait değerler tahmin yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50300-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="50300-199">Model, `horizon` parametre tarafından tanımlandığı şekilde geleceğe yedi dönem tahmin etmek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="50300-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="50300-200">Bir tahmin bilinçli bir tahmin olduğundan, her zaman % 100 doğru değildir.</span><span class="sxs-lookup"><span data-stu-id="50300-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="50300-201">Bu nedenle, üst ve alt sınırlar tarafından tanımlanan en iyi ve en kötü durum senaryolarında değerlerin aralığını bilmek iyidir.</span><span class="sxs-lookup"><span data-stu-id="50300-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="50300-202">Bu durumda, alt ve üst sınırlar için güven düzeyi% 95 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="50300-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="50300-203">Güven düzeyi buna göre artırılabilir veya azaltılabilir.</span><span class="sxs-lookup"><span data-stu-id="50300-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="50300-204">Değer ne kadar yüksekse, istenilen güven düzeyine ulaşmak için üst ve alt sınırlar arasındaki aralık da o kadar geniştir.</span><span class="sxs-lookup"><span data-stu-id="50300-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="50300-205">Modeli [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) eğitmek ve verileri daha önce tanımlanana `forecastingPipeline`sığdırmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="50300-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="50300-206">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="50300-206">Evaluate the model</span></span>

<span data-ttu-id="50300-207">Modelin gelecek yılın verilerini tahmin ederek ve gerçek değerlerle karşılaştırarak ne kadar iyi performans gösterdiğini değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="50300-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="50300-208">Yöntemin `Main` altında, adı verilen `Evaluate`yeni bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50300-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="50300-209">Yöntemin `Evaluate` içinde, eğitilmiş model ile [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) yöntemi kullanarak ikinci yılın verilerini tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="50300-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="50300-210">[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) Yöntemi kullanarak verilerden gerçek değerleri alın.</span><span class="sxs-lookup"><span data-stu-id="50300-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="50300-211">[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) Yöntemi kullanarak tahmin değerlerini alın.</span><span class="sxs-lookup"><span data-stu-id="50300-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="50300-212">Hata olarak adanılan gerçek ve tahmin değerleri arasındaki farkı hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="50300-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="50300-213">Ortalama Mutlak Hata ve Kök Ortalama Kareli Hata değerlerini hesaplayarak performansı ölçün.</span><span class="sxs-lookup"><span data-stu-id="50300-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="50300-214">Performansı değerlendirmek için aşağıdaki ölçümler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="50300-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="50300-215">**Ortalama Mutlak Hata**: Tahminlerin gerçek değere ne kadar yakın olduğunu ölçer.</span><span class="sxs-lookup"><span data-stu-id="50300-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="50300-216">Bu değer 0 ile sonsuzluk arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="50300-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="50300-217">0'a ne kadar yakınsa, modelin kalitesi de o kadar iyi.</span><span class="sxs-lookup"><span data-stu-id="50300-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="50300-218">**Kök Ortalama Kareli Hata**: Modeldeki hatayı özetler.</span><span class="sxs-lookup"><span data-stu-id="50300-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="50300-219">Bu değer 0 ile sonsuzluk arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="50300-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="50300-220">0'a ne kadar yakınsa, modelin kalitesi de o kadar iyi.</span><span class="sxs-lookup"><span data-stu-id="50300-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="50300-221">Ölçümleri konsola çıktın.</span><span class="sxs-lookup"><span data-stu-id="50300-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="50300-222">`Evaluate` Yöntem in içindeki yöntemi `Main` kullanın.</span><span class="sxs-lookup"><span data-stu-id="50300-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="50300-223">Modeli kaydetme</span><span class="sxs-lookup"><span data-stu-id="50300-223">Save the model</span></span>

<span data-ttu-id="50300-224">Modelinizden memnunsanız, modelinizi diğer uygulamalarda daha sonra kullanmak üzere kaydedin.</span><span class="sxs-lookup"><span data-stu-id="50300-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="50300-225">Yöntemde, `Main` bir [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="50300-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="50300-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)tek tahminler yapmak için bir kolaylık yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="50300-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="50300-227">Modeli daha önce tanımlanan `MLModel.zip` değişken tarafından belirtildiği `modelPath` gibi çağrılan bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="50300-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="50300-228">Modeli [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) kaydetmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="50300-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="50300-229">Talebi tahmin etmek için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="50300-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="50300-230">Yöntemin `Evaluate` altında, adı verilen `Forecast`yeni bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50300-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="50300-231">Yöntemin `Forecast` içinde, [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) önümüzdeki yedi gün için kiralama tahmin etmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="50300-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="50300-232">Yedi dönem için gerçek ve tahmin değerlerini hizala.</span><span class="sxs-lookup"><span data-stu-id="50300-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="50300-233">Tahmin çıktısını yineleyin ve konsolda görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="50300-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="50300-234">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="50300-234">Run the application</span></span>

1. <span data-ttu-id="50300-235">Yöntemin `Main` içinde, `Forecast` yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="50300-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="50300-236">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="50300-236">Run the application.</span></span> <span data-ttu-id="50300-237">Aşağıdakine benzer çıkış konsolda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="50300-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="50300-238">Kısalık için, çıkış yoğunlaştırılmış tır.</span><span class="sxs-lookup"><span data-stu-id="50300-238">For brevity, the output has been condensed.</span></span>

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

<span data-ttu-id="50300-239">Gerçek ve tahmin edilen değerlerin incelenmesi aşağıdaki ilişkileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="50300-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Gerçek vs Tahmin Karşılaştırması](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="50300-241">Tahmin edilen değerler tam kiralama sayısını tahmin etmese de, bir işlemin kaynak kullanımını optimize etmesine olanak tanıyan daha dar bir değer aralığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="50300-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="50300-242">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="50300-242">Congratulations!</span></span> <span data-ttu-id="50300-243">Şimdi başarılı bisiklet kiralama talebi tahmin etmek için bir zaman serisi makine öğrenme modeli inşa ettik.</span><span class="sxs-lookup"><span data-stu-id="50300-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="50300-244">Bu öğreticinin kaynak kodunu [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50300-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="50300-245">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="50300-245">Next steps</span></span>

- [<span data-ttu-id="50300-246">ML.NET makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="50300-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="50300-247">Model doğruluğunu artırma</span><span class="sxs-lookup"><span data-stu-id="50300-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
