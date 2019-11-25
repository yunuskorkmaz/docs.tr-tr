---
title: 'Öğretici: tahmin Bisiklet Kiralama talep-süre serisi'
description: Bu öğreticide, tek bir zaman serisi analizi ve ML.NET kullanarak bir bisiklet kiralama hizmeti için talebin nasıl tahmin yapılacağı gösterilir.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 2482709abfadad0505a40f4c37fd58cee4a2634c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978197"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="9edf6-103">Öğretici: zaman serisi analizi ve ML.NET ile tahmin Bisiklet kiralama hizmeti talebi</span><span class="sxs-lookup"><span data-stu-id="9edf6-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="9edf6-104">ML.NET ile SQL Server veritabanında depolanan veriler üzerinde bağımsız zamanlı bir zaman serisi analizi kullanarak bir bisiklet kiralama hizmeti için talebi tahmin etme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="9edf6-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="9edf6-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="9edf6-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="9edf6-106">Understand the problem</span></span>
> * <span data-ttu-id="9edf6-107">Veritabanından veri yükleme</span><span class="sxs-lookup"><span data-stu-id="9edf6-107">Load data from a database</span></span>
> * <span data-ttu-id="9edf6-108">Tahmin modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="9edf6-108">Create a forecasting model</span></span>
> * <span data-ttu-id="9edf6-109">Tahmin modelini değerlendir</span><span class="sxs-lookup"><span data-stu-id="9edf6-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="9edf6-110">Tahmin modelini kaydetme</span><span class="sxs-lookup"><span data-stu-id="9edf6-110">Save a forecasting model</span></span>
> * <span data-ttu-id="9edf6-111">Tahmin modeli kullan</span><span class="sxs-lookup"><span data-stu-id="9edf6-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9edf6-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="9edf6-112">Prerequisites</span></span>

- <span data-ttu-id="9edf6-113">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="9edf6-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="9edf6-114">Zaman serisi tahmin örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="9edf6-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="9edf6-115">Bu örnek, tek bir spekme analizi olarak bilinen bağımsız bir zaman serisi analiz algoritması kullanarak bisiklet için talebi tahmin eden bir  **C# .NET Core konsol uygulamasıdır** .</span><span class="sxs-lookup"><span data-stu-id="9edf6-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="9edf6-116">Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="9edf6-117">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="9edf6-117">Understand the problem</span></span>

<span data-ttu-id="9edf6-118">Verimli bir işlem çalıştırmak için, envanter yönetimi bir anahtar rol oynar.</span><span class="sxs-lookup"><span data-stu-id="9edf6-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="9edf6-119">Ücretteki bir ürünün çok fazla olması, raflardan herhangi bir gelir üretmeden satışa açık ürünler anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="9edf6-120">Çok az ürün, rakiplerden satın alınan satışları ve müşterileri kaybetmeyecek.</span><span class="sxs-lookup"><span data-stu-id="9edf6-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="9edf6-121">Bu nedenle, sabit soru, elinizin altında tutulacak en uygun stok miktarı nedir?</span><span class="sxs-lookup"><span data-stu-id="9edf6-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="9edf6-122">Zaman serisi analizi, geçmiş verileri inceleyerek, desenleri tanımlayarak ve bu bilgileri gelecekte bir süre tahmin etmek için kullanarak bu sorulara yanıt sağlanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9edf6-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="9edf6-123">Bu öğreticide kullanılan verileri çözümlemeye yönelik teknik, zaman serisi analizinden bağımsız bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="9edf6-124">Tek bir zaman serisi analizi, aylık satış gibi belirli aralıklarda tek bir sayısal izlemeye göz atacağız.</span><span class="sxs-lookup"><span data-stu-id="9edf6-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="9edf6-125">Bu öğreticide kullanılan algoritma, [tek bir Spekme analizidir (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="9edf6-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="9edf6-126">SSA, bir dizi sorumlu bileşen için zaman serisini kaldırarak işe yarar.</span><span class="sxs-lookup"><span data-stu-id="9edf6-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="9edf6-127">Bu bileşenler, eğilimler, gürültü, mevsimsellik ve birçok başka etkene karşılık gelen bir sinyalin parçaları olarak yorumlanamaz.</span><span class="sxs-lookup"><span data-stu-id="9edf6-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="9edf6-128">Ardından, bu bileşenler yeniden yapılandırılır ve gelecekte değerleri tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9edf6-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="9edf6-129">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9edf6-129">Create console application</span></span>

1. <span data-ttu-id="9edf6-130">"Bikeisteğtahmini" adlı yeni  **C# bir .NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9edf6-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="9edf6-131">**Microsoft.ml** Version **1.4.0** NuGet paketini yükler</span><span class="sxs-lookup"><span data-stu-id="9edf6-131">Install **Microsoft.ML** version **1.4.0** NuGet package</span></span>
    1. <span data-ttu-id="9edf6-132">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="9edf6-133">Paket kaynağı olarak "nuget.org" öğesini seçin, **Gözden** geçirme sekmesini seçin, **Microsoft.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="9edf6-134">**Ön sürümü dahil et** onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="9edf6-135">**Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="9edf6-136">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız Lisans Kabulü iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="9edf6-137">**System. Data. SqlClient** sürüm **4.7.0** ve **Microsoft. ml. timeseries** sürüm **1.4.0**için bu adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-137">Repeat these steps for **System.Data.SqlClient** version **4.7.0** and **Microsoft.ML.TimeSeries** version **1.4.0**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="9edf6-138">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="9edf6-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="9edf6-139">*Veri*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9edf6-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="9edf6-140">[ *Dailydemand. mdf* veritabanı dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) indirin ve *veri* dizinine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="9edf6-141">Bu öğreticide kullanılan veriler, [UCI bisiklet paylaşımı veri kümesinden](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)gelir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="9edf6-142">Fanaee-T, hadi ve gama, Joao, ' olay etiketleme birleştirme algılayıcıları ve arka plan bilgisi ', yapay zeka 'da Ilerleme (2013): PP. 1-15, Sprümlberg, [Web bağlantısı](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="9edf6-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="9edf6-143">Özgün veri kümesi mevsimsellik ve hava durumu ile ilgili birkaç sütun içerir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="9edf6-144">Breçekimi ve bu öğreticide kullanılan algoritma yalnızca tek bir sayısal sütundan değer gerektirdiğinden, özgün veri kümesi yalnızca aşağıdaki sütunları içerecek şekilde yoğunlaştırılmış:</span><span class="sxs-lookup"><span data-stu-id="9edf6-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="9edf6-145">**dteday**: Gözlem tarihi.</span><span class="sxs-lookup"><span data-stu-id="9edf6-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="9edf6-146">**yıl**: gözlemin kodlanmış yılı (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="9edf6-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="9edf6-147">**sayisi**: o güne ait bisiklet salları toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="9edf6-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="9edf6-148">Özgün veri kümesi, bir SQL Server veritabanında aşağıdaki şemaya sahip bir veritabanı tablosuyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="9edf6-149">Aşağıda, verilerin bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9edf6-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="9edf6-150">RentalDate</span><span class="sxs-lookup"><span data-stu-id="9edf6-150">RentalDate</span></span> | <span data-ttu-id="9edf6-151">Yıl</span><span class="sxs-lookup"><span data-stu-id="9edf6-151">Year</span></span> | <span data-ttu-id="9edf6-152">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="9edf6-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="9edf6-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="9edf6-153">1/1/2011</span></span>|<span data-ttu-id="9edf6-154">0</span><span class="sxs-lookup"><span data-stu-id="9edf6-154">0</span></span>|<span data-ttu-id="9edf6-155">985</span><span class="sxs-lookup"><span data-stu-id="9edf6-155">985</span></span>|
|<span data-ttu-id="9edf6-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="9edf6-156">1/2/2011</span></span>|<span data-ttu-id="9edf6-157">0</span><span class="sxs-lookup"><span data-stu-id="9edf6-157">0</span></span>|<span data-ttu-id="9edf6-158">801</span><span class="sxs-lookup"><span data-stu-id="9edf6-158">801</span></span>|
|<span data-ttu-id="9edf6-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="9edf6-159">1/3/2011</span></span>|<span data-ttu-id="9edf6-160">0</span><span class="sxs-lookup"><span data-stu-id="9edf6-160">0</span></span>|<span data-ttu-id="9edf6-161">1349</span><span class="sxs-lookup"><span data-stu-id="9edf6-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="9edf6-162">Giriş ve çıkış sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="9edf6-162">Create input and output classes</span></span>

1. <span data-ttu-id="9edf6-163">*Program.cs* dosyasını açın ve var olan `using` deyimlerini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9edf6-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="9edf6-164">`ModelInput` sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9edf6-164">Create `ModelInput` class.</span></span> <span data-ttu-id="9edf6-165">`Program` sınıfının altına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="9edf6-166">`ModelInput` sınıfı şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="9edf6-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="9edf6-167">**Rentaldate**: Gözlem tarihi.</span><span class="sxs-lookup"><span data-stu-id="9edf6-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="9edf6-168">**Yıl**: gözlemin kodlanmış yılı (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="9edf6-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="9edf6-169">**Totalrentals**: Bu güne ait toplam Bisiklet randevu sayısı.</span><span class="sxs-lookup"><span data-stu-id="9edf6-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="9edf6-170">Yeni oluşturulan `ModelInput` sınıfının altında `ModelOutput` sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9edf6-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="9edf6-171">`ModelOutput` sınıfı şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="9edf6-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="9edf6-172">**ForecastedRentals**: tahmin edilen dönem için tahmin edilen değerler.</span><span class="sxs-lookup"><span data-stu-id="9edf6-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="9edf6-173">**Ials Boundrentals**: tahmin edilen dönem için öngörülen minimum değerler.</span><span class="sxs-lookup"><span data-stu-id="9edf6-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="9edf6-174">**Üsteboundrentals**: tahmin edilen dönem için öngörülen maksimum değer.</span><span class="sxs-lookup"><span data-stu-id="9edf6-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="9edf6-175">Yolları tanımlama ve değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="9edf6-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="9edf6-176">`Main` yönteminin içinde, verilerinizin konumunu, Bağlantı dizenizi ve eğitilen modelin kaydedileceği yeri depolamak için değişkenleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="9edf6-177">Aşağıdaki satırı `Main` yöntemine ekleyerek `mlContext` değişkenini yeni bir [`MLContext`](xref:Microsoft.ML.MLContext) örneğiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="9edf6-178">[`MLContext`](xref:Microsoft.ML.MLContext) sınıfı tüm ml.NET işlemleri için bir başlangıç noktasıdır ve mlcontext 'i başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9edf6-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="9edf6-179">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="9edf6-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="9edf6-180">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="9edf6-180">Load the data</span></span>

1. <span data-ttu-id="9edf6-181">`ModelInput`türünde kayıtları yükleyen `DatabaseLoader` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9edf6-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="9edf6-182">Veritabanından verileri yükleyecek sorguyu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="9edf6-183">ML.NET algoritmaları verilerin [`Single`](xref:System.Single)türünde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="9edf6-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="9edf6-184">Bu nedenle, tek duyarlıklı kayan noktalı bir değer olan [`Real`](xref:System.Data.SqlDbType)türünde olmayan veritabanından gelen sayısal değerlerin [`Real`](xref:System.Data.SqlDbType)olarak dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="9edf6-185">`Year` ve `TotalRental` sütunları, veritabanındaki tamsayı türlerdir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="9edf6-186">`CAST` yerleşik işlevini kullanarak her ikisi de `Real`dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="9edf6-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="9edf6-187">Veritabanına bağlanmak ve sorguyu yürütmek için bir `DatabaseSource` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9edf6-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="9edf6-188">Verileri bir `IDataView`yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="9edf6-189">Veri kümesi iki yıl değer içerir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="9edf6-190">Eğitim için yalnızca ilk yılın verileri kullanılır, ikinci yıl, gerçek değerleri model tarafından üretilen tahmine göre karşılaştırmak için tutulur.</span><span class="sxs-lookup"><span data-stu-id="9edf6-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="9edf6-191">[`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) dönüşümünü kullanarak verileri filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="9edf6-192">İlk yılda, `upperBound` parametresi 1 olarak ayarlanarak yalnızca `Year` sütunundaki değerler 1 ' den az seçilir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="9edf6-193">Bunun tersine, ikinci yıl için 1 ' den büyük veya eşit değerler `lowerBound` parametresi 1 olarak ayarlanarak seçilir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="9edf6-194">Zaman serisi analizi ardışık düzenini tanımlama</span><span class="sxs-lookup"><span data-stu-id="9edf6-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="9edf6-195">Bir zaman serisi veri kümesindeki değerleri tahmin etmek için [Ssaforekılaringestimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) kullanan bir işlem hattı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="9edf6-196">`forecastingPipeline`, ilk yıl ve örnekler için 365 veri noktası alır ya da zaman serisi veri kümesini, `seriesLength` parametresi tarafından belirtilen 30 günlük (aylık) aralıklarına böler.</span><span class="sxs-lookup"><span data-stu-id="9edf6-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="9edf6-197">Bu örneklerin her biri haftalık veya 7 günlük bir pencere ile çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="9edf6-198">Sonraki periyotalar için tahmin edilen değerin ne olduğu belirlenirken, önceki yedi günün değerleri bir tahmin yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9edf6-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="9edf6-199">Model, daha sonra `horizon` parametresi tarafından tanımlanan şekilde yedi dönemi tahmin etmek üzere ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9edf6-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="9edf6-200">Tahmin bilinçli bir tahmin olduğundan, her zaman %100 doğru değildir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="9edf6-201">Bu nedenle, üst ve alt sınırlar tarafından tanımlanan en iyi ve en kötü durum senaryolarında değer aralığını bilmemiz yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="9edf6-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="9edf6-202">Bu durumda, alt ve üst sınırlara yönelik güven düzeyi %95 olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9edf6-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="9edf6-203">Güvenirlik düzeyi, uygun şekilde artırılabilir veya azaltılabilir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="9edf6-204">Değerin ne kadar yüksekse, istenen güven düzeyini elde etmek için Aralık üst ve alt sınır arasındadır.</span><span class="sxs-lookup"><span data-stu-id="9edf6-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="9edf6-205">Modeli eğitme ve verileri daha önce tanımlanan `forecastingPipeline`sığacak şekilde [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="9edf6-206">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="9edf6-206">Evaluate the model</span></span>

<span data-ttu-id="9edf6-207">Sonraki yılın verilerini tahmin ederek ve gerçek değerlerle karşılaştırarak modelin ne kadar iyi performans kullandığını değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="9edf6-208">`Main` yönteminin altında `Evaluate`adlı yeni bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9edf6-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="9edf6-209">`Evaluate` yönteminin içinde, eğitilen modeliyle [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) yöntemini kullanarak ikinci yılın verilerini tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="9edf6-210">[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemi kullanarak verilerden gerçek değerleri alın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="9edf6-211">[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemini kullanarak tahmin değerlerini alın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="9edf6-212">Yaygın olarak hata olarak adlandırılan gerçek ve tahmin değerleri arasındaki farkı hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="9edf6-213">Ortalama mutlak hata ve kök ortalama kare hata değerlerini hesaplayarak performansı ölçün.</span><span class="sxs-lookup"><span data-stu-id="9edf6-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="9edf6-214">Performansı değerlendirmek için aşağıdaki ölçümler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="9edf6-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="9edf6-215">**Mutlak ortalama hata**: kapanış tahminlerinin gerçek değere nasıl geldiğini ölçer.</span><span class="sxs-lookup"><span data-stu-id="9edf6-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="9edf6-216">Bu değer 0 ile sonsuz arasında aralıklar.</span><span class="sxs-lookup"><span data-stu-id="9edf6-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="9edf6-217">0 ' a yaklaşarak modelin kalitesi daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="9edf6-218">**Kök ortalama kare hatası**: modeldeki hatayı özetler.</span><span class="sxs-lookup"><span data-stu-id="9edf6-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="9edf6-219">Bu değer 0 ile sonsuz arasında aralıklar.</span><span class="sxs-lookup"><span data-stu-id="9edf6-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="9edf6-220">0 ' a yaklaşarak modelin kalitesi daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="9edf6-221">Ölçümleri konsola çıkış.</span><span class="sxs-lookup"><span data-stu-id="9edf6-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="9edf6-222">`Main` yönteminin içindeki `Evaluate` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="9edf6-223">Modeli kaydetme</span><span class="sxs-lookup"><span data-stu-id="9edf6-223">Save the model</span></span>

<span data-ttu-id="9edf6-224">Modelinize memnun kaldıysanız, daha sonra diğer uygulamalarda kullanmak üzere kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="9edf6-225">`Main` yönteminde bir [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9edf6-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="9edf6-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) , tek tahminleri yapmak için kullanışlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="9edf6-227">Modeli, daha önce tanımlanan `modelPath` değişkeni tarafından belirtilen `MLModel.zip` adlı bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="9edf6-228">Modeli kaydetmek için [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="9edf6-229">Talebi tahmin etmek için modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="9edf6-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="9edf6-230">`Evaluate` yönteminin altında `Forecast`adlı yeni bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9edf6-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="9edf6-231">`Forecast` yönteminin içinde, sonraki yedi güne ait yeniden örnekleri tahmin etmek için [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="9edf6-232">Gerçek ve tahmin değerlerini yedi dönem için hizalayın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="9edf6-233">Tahmin çıktısını yineleyin ve konsolunda görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="9edf6-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="9edf6-234">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9edf6-234">Run the application</span></span>

1. <span data-ttu-id="9edf6-235">`Main` yönteminin içinde `Forecast` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="9edf6-236">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9edf6-236">Run the application.</span></span> <span data-ttu-id="9edf6-237">Aşağıdakine benzer bir çıktı konsolunda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="9edf6-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="9edf6-238">Breçekimi için çıkış yoğunlaştırılmış.</span><span class="sxs-lookup"><span data-stu-id="9edf6-238">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="9edf6-239">Gerçek ve tahmin edilen değerlerin incelemesinde aşağıdaki ilişkiler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9edf6-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Gerçek vs tahmini karşılaştırması](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="9edf6-241">Tahmin edilen değerler tam sayı sayısını tahmin etmez, ancak bir işlemin kaynakları kullanımlarını en uygun hale getirmesine izin veren daha dar bir değer aralığı sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="9edf6-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="9edf6-242">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="9edf6-242">Congratulations!</span></span> <span data-ttu-id="9edf6-243">Artık Bisiklet Kiralama talebini tahmin etmek için bir zaman serisi makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="9edf6-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="9edf6-244">Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9edf6-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9edf6-245">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9edf6-245">Next steps</span></span>

- [<span data-ttu-id="9edf6-246">ML.NET 'de makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="9edf6-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="9edf6-247">Model doğruluğunu geliştirme</span><span class="sxs-lookup"><span data-stu-id="9edf6-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
