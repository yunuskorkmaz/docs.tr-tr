---
title: 'Öğretici: tahmin Bisiklet Kiralama talep-süre serisi'
description: Bu öğreticide, tek bir zaman serisi analizi ve ML.NET kullanarak bir bisiklet kiralama hizmeti için talebin nasıl tahmin yapılacağı gösterilir.
ms.date: 10/31/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: f30aac5f8467c2410e9008bafea3cf35af3f4e2a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425641"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="9ed58-103">Öğretici: zaman serisi analizi ve ML.NET ile tahmin Bisiklet kiralama hizmeti talebi</span><span class="sxs-lookup"><span data-stu-id="9ed58-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="9ed58-104">ML.NET ile SQL Server veritabanında depolanan veriler üzerinde bağımsız zamanlı bir zaman serisi analizi kullanarak bir bisiklet kiralama hizmeti için talebi tahmin etme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="9ed58-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="9ed58-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="9ed58-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="9ed58-106">Understand the problem</span></span>
> * <span data-ttu-id="9ed58-107">Veritabanından veri yükleme</span><span class="sxs-lookup"><span data-stu-id="9ed58-107">Load data from a database</span></span>
> * <span data-ttu-id="9ed58-108">Tahmin modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ed58-108">Create a forecasting model</span></span>
> * <span data-ttu-id="9ed58-109">Tahmin modelini değerlendir</span><span class="sxs-lookup"><span data-stu-id="9ed58-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="9ed58-110">Tahmin modelini kaydetme</span><span class="sxs-lookup"><span data-stu-id="9ed58-110">Save a forecasting model</span></span>
> * <span data-ttu-id="9ed58-111">Tahmin modeli kullan</span><span class="sxs-lookup"><span data-stu-id="9ed58-111">Use a forecasting model</span></span>

> [!NOTE]
> <span data-ttu-id="9ed58-112">Bu öğretici, DatabaseLoader 'ın önizleme sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ed58-112">This tutorial uses a preview version of DatabaseLoader.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ed58-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="9ed58-113">Prerequisites</span></span>

- <span data-ttu-id="9ed58-114">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="9ed58-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="9ed58-115">Zaman serisi tahmin örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="9ed58-115">Time series forecasting sample overview</span></span>

<span data-ttu-id="9ed58-116">Bu örnek, tek bir spekme analizi olarak bilinen bağımsız bir zaman serisi analiz algoritması kullanarak bisiklet için talebi tahmin eden bir  **C# .NET Core konsol uygulamasıdır** .</span><span class="sxs-lookup"><span data-stu-id="9ed58-116">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="9ed58-117">Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-117">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="9ed58-118">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="9ed58-118">Understand the problem</span></span>

<span data-ttu-id="9ed58-119">Verimli bir işlem çalıştırmak için, envanter yönetimi bir anahtar rol oynar.</span><span class="sxs-lookup"><span data-stu-id="9ed58-119">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="9ed58-120">Ücretteki bir ürünün çok fazla olması, raflardan herhangi bir gelir üretmeden satışa açık ürünler anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-120">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="9ed58-121">Çok az ürün, rakiplerden satın alınan satışları ve müşterileri kaybetmeyecek.</span><span class="sxs-lookup"><span data-stu-id="9ed58-121">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="9ed58-122">Bu nedenle, sabit soru, elinizin altında tutulacak en uygun stok miktarı nedir?</span><span class="sxs-lookup"><span data-stu-id="9ed58-122">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="9ed58-123">Zaman serisi analizi, geçmiş verileri inceleyerek, desenleri tanımlayarak ve bu bilgileri gelecekte bir süre tahmin etmek için kullanarak bu sorulara yanıt sağlanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9ed58-123">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span> 

<span data-ttu-id="9ed58-124">Bu öğreticide kullanılan verileri çözümlemeye yönelik teknik, zaman serisi analizinden bağımsız bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-124">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="9ed58-125">Tek bir zaman serisi analizi, aylık satış gibi belirli aralıklarda tek bir sayısal izlemeye göz atacağız.</span><span class="sxs-lookup"><span data-stu-id="9ed58-125">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span> 

<span data-ttu-id="9ed58-126">Bu öğreticide kullanılan algoritma, [tek bir Spekme analizidir (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="9ed58-126">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="9ed58-127">SSA, bir dizi sorumlu bileşen için zaman serisini kaldırarak işe yarar.</span><span class="sxs-lookup"><span data-stu-id="9ed58-127">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="9ed58-128">Bu bileşenler, eğilimler, gürültü, mevsimsellik ve birçok başka etkene karşılık gelen bir sinyalin parçaları olarak yorumlanamaz.</span><span class="sxs-lookup"><span data-stu-id="9ed58-128">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="9ed58-129">Ardından, bu bileşenler yeniden yapılandırılır ve gelecekte değerleri tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ed58-129">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="9ed58-130">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ed58-130">Create console application</span></span>

1. <span data-ttu-id="9ed58-131">"Bikeisteğtahmini" adlı yeni  **C# bir .NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ed58-131">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="9ed58-132">**Microsoft.ml** Version **1.4.0-preview2** NuGet paketini yükler</span><span class="sxs-lookup"><span data-stu-id="9ed58-132">Install **Microsoft.ML** version **1.4.0-preview2** NuGet package</span></span>
    1. <span data-ttu-id="9ed58-133">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="9ed58-134">Paket kaynağı olarak "nuget.org" öğesini seçin, **Gözden** geçirme sekmesini seçin, **Microsoft.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="9ed58-135">**Ön sürümü dahil et** onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-135">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="9ed58-136">**Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-136">Select the **Install** button.</span></span>
    1. <span data-ttu-id="9ed58-137">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız Lisans Kabulü iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="9ed58-138">**System. Data. SqlClient** sürüm **4.7.0**, **Microsoft. ml. deneysel** sürüm **0.16.0-Preview2**ve **Microsoft. ml. timeseries** sürüm **1.4.0-preview2**için bu adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-138">Repeat these steps for **System.Data.SqlClient** version **4.7.0**, **Microsoft.ML.Experimental** version **0.16.0-preview2**, and **Microsoft.ML.TimeSeries** version **1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="9ed58-139">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="9ed58-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="9ed58-140">*Veri*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ed58-140">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="9ed58-141">[ *Dailydemand. mdf* veritabanı dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) indirin ve *veri* dizinine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-141">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="9ed58-142">Bu öğreticide kullanılan veriler, [UCI bisiklet paylaşımı veri kümesinden](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)gelir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-142">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="9ed58-143">Fanaee-T, hadi ve gama, Joao, ' olay etiketleme birleştirme algılayıcıları ve arka plan bilgisi ', yapay zeka 'da Ilerleme (2013): PP. 1-15, Sprümlberg, [Web bağlantısı](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="9ed58-143">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="9ed58-144">Özgün veri kümesi mevsimsellik ve hava durumu ile ilgili birkaç sütun içerir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-144">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="9ed58-145">Breçekimi ve bu öğreticide kullanılan algoritma yalnızca tek bir sayısal sütundan değer gerektirdiğinden, özgün veri kümesi yalnızca aşağıdaki sütunları içerecek şekilde yoğunlaştırılmış:</span><span class="sxs-lookup"><span data-stu-id="9ed58-145">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>  

- <span data-ttu-id="9ed58-146">**dteday**: Gözlem tarihi.</span><span class="sxs-lookup"><span data-stu-id="9ed58-146">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="9ed58-147">**yıl**: gözlemin kodlanmış yılı (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="9ed58-147">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="9ed58-148">**sayisi**: o güne ait bisiklet salları toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="9ed58-148">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="9ed58-149">Özgün veri kümesi, bir SQL Server veritabanında aşağıdaki şemaya sahip bir veritabanı tablosuyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-149">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="9ed58-150">Aşağıda, verilerin bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9ed58-150">The following is a sample of the data:</span></span>

| <span data-ttu-id="9ed58-151">RentalDate</span><span class="sxs-lookup"><span data-stu-id="9ed58-151">RentalDate</span></span> | <span data-ttu-id="9ed58-152">Yıl</span><span class="sxs-lookup"><span data-stu-id="9ed58-152">Year</span></span> | <span data-ttu-id="9ed58-153">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="9ed58-153">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="9ed58-154">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="9ed58-154">1/1/2011</span></span>|<span data-ttu-id="9ed58-155">0</span><span class="sxs-lookup"><span data-stu-id="9ed58-155">0</span></span>|<span data-ttu-id="9ed58-156">985</span><span class="sxs-lookup"><span data-stu-id="9ed58-156">985</span></span>|
|<span data-ttu-id="9ed58-157">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="9ed58-157">1/2/2011</span></span>|<span data-ttu-id="9ed58-158">0</span><span class="sxs-lookup"><span data-stu-id="9ed58-158">0</span></span>|<span data-ttu-id="9ed58-159">801</span><span class="sxs-lookup"><span data-stu-id="9ed58-159">801</span></span>|
|<span data-ttu-id="9ed58-160">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="9ed58-160">1/3/2011</span></span>|<span data-ttu-id="9ed58-161">0</span><span class="sxs-lookup"><span data-stu-id="9ed58-161">0</span></span>|<span data-ttu-id="9ed58-162">1349</span><span class="sxs-lookup"><span data-stu-id="9ed58-162">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="9ed58-163">Giriş ve çıkış sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ed58-163">Create input and output classes</span></span>

1. <span data-ttu-id="9ed58-164">*Program.cs* dosyasını açın ve var olan `using` deyimlerini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9ed58-164">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="9ed58-165">`ModelInput` sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ed58-165">Create `ModelInput` class.</span></span> <span data-ttu-id="9ed58-166">`Program` sınıfının altına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-166">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]    

    <span data-ttu-id="9ed58-167">`ModelInput` sınıfı şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="9ed58-167">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="9ed58-168">**Rentaldate**: Gözlem tarihi.</span><span class="sxs-lookup"><span data-stu-id="9ed58-168">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="9ed58-169">**Yıl**: gözlemin kodlanmış yılı (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="9ed58-169">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="9ed58-170">**Totalrentals**: Bu güne ait toplam Bisiklet randevu sayısı.</span><span class="sxs-lookup"><span data-stu-id="9ed58-170">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="9ed58-171">Yeni oluşturulan `ModelInput` sınıfının altında `ModelOutput` sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ed58-171">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="9ed58-172">`ModelOutput` sınıfı şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="9ed58-172">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="9ed58-173">**ForecastedRentals**: tahmin edilen dönem için tahmin edilen değerler.</span><span class="sxs-lookup"><span data-stu-id="9ed58-173">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="9ed58-174">**Ials Boundrentals**: tahmin edilen dönem için öngörülen minimum değerler.</span><span class="sxs-lookup"><span data-stu-id="9ed58-174">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="9ed58-175">**Üsteboundrentals**: tahmin edilen dönem için öngörülen maksimum değer.</span><span class="sxs-lookup"><span data-stu-id="9ed58-175">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="9ed58-176">Yolları tanımlama ve değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="9ed58-176">Define paths and initialize variables</span></span>

1. <span data-ttu-id="9ed58-177">`Main` yönteminin içinde, verilerinizin konumunu, Bağlantı dizenizi ve eğitilen modelin kaydedileceği yeri depolamak için değişkenleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-177">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="9ed58-178">Aşağıdaki satırı `Main` yöntemine ekleyerek `mlContext` değişkenini yeni bir [`MLContext`](xref:Microsoft.ML.MLContext) örneğiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-178">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="9ed58-179">[`MLContext`](xref:Microsoft.ML.MLContext) sınıfı tüm ml.NET işlemleri için bir başlangıç noktasıdır ve mlcontext 'i başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9ed58-179">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="9ed58-180">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="9ed58-180">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="9ed58-181">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="9ed58-181">Load the data</span></span>

1. <span data-ttu-id="9ed58-182">`ModelInput`türünde kayıtları yükleyen `DatabaseLoader` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ed58-182">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="9ed58-183">Veritabanından verileri yükleyecek sorguyu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-183">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="9ed58-184">ML.NET algoritmaları verilerin [`Single`](xref:System.Single)türünde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="9ed58-184">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="9ed58-185">Bu nedenle, tek duyarlıklı kayan noktalı bir değer olan [`Real`](xref:System.Data.SqlDbType)türünde olmayan veritabanından gelen sayısal değerlerin [`Real`](xref:System.Data.SqlDbType)olarak dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-185">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> 

    <span data-ttu-id="9ed58-186">`Year` ve `TotalRental` sütunları, veritabanındaki tamsayı türlerdir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-186">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="9ed58-187">`CAST` yerleşik işlevini kullanarak her ikisi de `Real`dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="9ed58-187">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="9ed58-188">Veritabanına bağlanmak ve sorguyu yürütmek için bir `DatabaseSource` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ed58-188">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="9ed58-189">Verileri bir `IDataView`yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-189">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="9ed58-190">Veri kümesi iki yıl değer içerir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-190">The dataset contains two years worth of data.</span></span> <span data-ttu-id="9ed58-191">Eğitim için yalnızca ilk yılın verileri kullanılır, ikinci yıl, gerçek değerleri model tarafından üretilen tahmine göre karşılaştırmak için tutulur.</span><span class="sxs-lookup"><span data-stu-id="9ed58-191">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="9ed58-192">[`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) dönüşümünü kullanarak verileri filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-192">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span> 

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="9ed58-193">İlk yılda, `upperBound` parametresi 1 olarak ayarlanarak yalnızca `Year` sütunundaki değerler 1 ' den az seçilir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-193">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="9ed58-194">Bunun tersine, ikinci yıl için 1 ' den büyük veya eşit değerler `lowerBound` parametresi 1 olarak ayarlanarak seçilir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-194">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="9ed58-195">Zaman serisi analizi ardışık düzenini tanımlama</span><span class="sxs-lookup"><span data-stu-id="9ed58-195">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="9ed58-196">Bir zaman serisi veri kümesindeki değerleri tahmin etmek için [Ssaforekılaringestimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) kullanan bir işlem hattı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-196">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="9ed58-197">`forecastingPipeline`, ilk yıl ve örnekler için 365 veri noktası alır ya da zaman serisi veri kümesini, `seriesLength` parametresi tarafından belirtilen 30 günlük (aylık) aralıklarına böler.</span><span class="sxs-lookup"><span data-stu-id="9ed58-197">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="9ed58-198">Bu örneklerin her biri haftalık veya 7 günlük bir pencere ile çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-198">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="9ed58-199">Sonraki periyotalar için tahmin edilen değerin ne olduğu belirlenirken, önceki yedi günün değerleri bir tahmin yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ed58-199">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="9ed58-200">Model, daha sonra `horizon` parametresi tarafından tanımlanan şekilde yedi dönemi tahmin etmek üzere ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9ed58-200">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="9ed58-201">Tahmin bilinçli bir tahmin olduğundan, her zaman %100 doğru değildir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-201">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="9ed58-202">Bu nedenle, üst ve alt sınırlar tarafından tanımlanan en iyi ve en kötü durum senaryolarında değer aralığını bilmemiz yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="9ed58-202">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="9ed58-203">Bu durumda, alt ve üst sınırlara yönelik güven düzeyi %95 olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9ed58-203">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="9ed58-204">Güvenirlik düzeyi, uygun şekilde artırılabilir veya azaltılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-204">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="9ed58-205">Değerin ne kadar yüksekse, istenen güven düzeyini elde etmek için Aralık üst ve alt sınır arasındadır.</span><span class="sxs-lookup"><span data-stu-id="9ed58-205">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span> 

1. <span data-ttu-id="9ed58-206">Modeli eğitme ve verileri daha önce tanımlanan `forecastingPipeline`sığacak şekilde [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-206">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="9ed58-207">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="9ed58-207">Evaluate the model</span></span>

<span data-ttu-id="9ed58-208">Sonraki yılın verilerini tahmin ederek ve gerçek değerlerle karşılaştırarak modelin ne kadar iyi performans kullandığını değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-208">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="9ed58-209">`Main` yönteminin altında `Evaluate`adlı yeni bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ed58-209">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {
        
    }
    ```

1. <span data-ttu-id="9ed58-210">`Evaluate` yönteminin içinde, eğitilen modeliyle [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) yöntemini kullanarak ikinci yılın verilerini tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-210">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="9ed58-211">[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemi kullanarak verilerden gerçek değerleri alın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-211">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="9ed58-212">[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemini kullanarak tahmin değerlerini alın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-212">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="9ed58-213">Yaygın olarak hata olarak adlandırılan gerçek ve tahmin değerleri arasındaki farkı hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-213">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="9ed58-214">Ortalama mutlak hata ve kök ortalama kare hata değerlerini hesaplayarak performansı ölçün.</span><span class="sxs-lookup"><span data-stu-id="9ed58-214">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="9ed58-215">Performansı değerlendirmek için aşağıdaki ölçümler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="9ed58-215">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="9ed58-216">**Mutlak ortalama hata**: kapanış tahminlerinin gerçek değere nasıl geldiğini ölçer.</span><span class="sxs-lookup"><span data-stu-id="9ed58-216">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="9ed58-217">Bu değer 0 ile sonsuz arasında aralıklar.</span><span class="sxs-lookup"><span data-stu-id="9ed58-217">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="9ed58-218">0 ' a yaklaşarak modelin kalitesi daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-218">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="9ed58-219">**Kök ortalama kare hatası**: modelde hata olduğunu özetler.</span><span class="sxs-lookup"><span data-stu-id="9ed58-219">**Root Mean Squared Error**: Summarizes thhe error in the model.</span></span> <span data-ttu-id="9ed58-220">Bu değer 0 ile sonsuz arasında aralıklar.</span><span class="sxs-lookup"><span data-stu-id="9ed58-220">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="9ed58-221">0 ' a yaklaşarak modelin kalitesi daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-221">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="9ed58-222">Ölçümleri konsola çıkış.</span><span class="sxs-lookup"><span data-stu-id="9ed58-222">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="9ed58-223">`Main` yönteminin içindeki `Evaluate` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-223">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="9ed58-224">Modeli kaydetme</span><span class="sxs-lookup"><span data-stu-id="9ed58-224">Save the model</span></span>

<span data-ttu-id="9ed58-225">Modelinize memnun kaldıysanız, daha sonra diğer uygulamalarda kullanmak üzere kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-225">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="9ed58-226">`Main` yönteminde bir [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ed58-226">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="9ed58-227">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) , tek tahminleri yapmak için kullanışlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-227">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="9ed58-228">Modeli, daha önce tanımlanan `modelPath` değişkeni tarafından belirtilen `MLModel.zip` adlı bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-228">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="9ed58-229">Modeli kaydetmek için [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-229">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="9ed58-230">Talebi tahmin etmek için modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="9ed58-230">Use the model to forecast demand</span></span>

1. <span data-ttu-id="9ed58-231">`Evaluate` yönteminin altında `Forecast`adlı yeni bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ed58-231">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="9ed58-232">`Forecast` yönteminin içinde, sonraki yedi güne ait yeniden örnekleri tahmin etmek için [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-232">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="9ed58-233">Gerçek ve tahmin değerlerini yedi dönem için hizalayın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-233">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="9ed58-234">Tahmin çıktısını yineleyin ve konsolunda görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="9ed58-234">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="9ed58-235">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9ed58-235">Run the application</span></span>

1. <span data-ttu-id="9ed58-236">`Main` yönteminin içinde `Forecast` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-236">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="9ed58-237">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ed58-237">Run the application.</span></span> <span data-ttu-id="9ed58-238">Aşağıdakine benzer bir çıktı konsolunda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="9ed58-238">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="9ed58-239">Breçekimi için çıkış yoğunlaştırılmış.</span><span class="sxs-lookup"><span data-stu-id="9ed58-239">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="9ed58-240">Gerçek ve tahmin edilen değerlerin incelemesinde aşağıdaki ilişkiler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9ed58-240">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Gerçek vs tahmini karşılaştırması](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="9ed58-242">Tahmin edilen değerler tam sayı sayısını tahmin etmez, ancak bir işlemin kaynakları kullanımlarını en uygun hale getirmesine izin veren daha dar bir değer aralığı sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="9ed58-242">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span> 

<span data-ttu-id="9ed58-243">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="9ed58-243">Congratulations!</span></span> <span data-ttu-id="9ed58-244">Artık Bisiklet Kiralama talebini tahmin etmek için bir zaman serisi makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="9ed58-244">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="9ed58-245">Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ed58-245">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9ed58-246">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9ed58-246">Next steps</span></span>

- [<span data-ttu-id="9ed58-247">ML.NET 'de makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="9ed58-247">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="9ed58-248">Model doğruluğunu geliştirme</span><span class="sxs-lookup"><span data-stu-id="9ed58-248">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
