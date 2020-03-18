---
title: 'Öğretici: Regresyon kullanarak fiyatları tahmin edin'
description: Bu öğretici fiyatları tahmin etmek için ML.NET kullanarak bir regresyon modeli oluşturmak için nasıl göstermektedir, özellikle, New York taksi ücretleri.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 51cef97178c2dbc6a5b572a7045bdad4bc382ba0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78240993"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="71e9c-103">Öğretici: ML.NET ile regresyon kullanarak fiyatları tahmin</span><span class="sxs-lookup"><span data-stu-id="71e9c-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="71e9c-104">Bu öğretici fiyatları tahmin etmek için ML.NET kullanarak bir [regresyon modeli](../resources/glossary.md#regression) oluşturmak için nasıl göstermektedir, özellikle, New York taksi ücretleri.</span><span class="sxs-lookup"><span data-stu-id="71e9c-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="71e9c-105">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="71e9c-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="71e9c-106">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="71e9c-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="71e9c-107">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="71e9c-107">Load and transform the data</span></span>
> * <span data-ttu-id="71e9c-108">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="71e9c-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="71e9c-109">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="71e9c-109">Train the model</span></span>
> * <span data-ttu-id="71e9c-110">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="71e9c-110">Evaluate the model</span></span>
> * <span data-ttu-id="71e9c-111">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="71e9c-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="71e9c-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="71e9c-112">Prerequisites</span></span>

* <span data-ttu-id="71e9c-113">[Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="71e9c-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="71e9c-114">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="71e9c-114">Create a console application</span></span>

1. <span data-ttu-id="71e9c-115">"TaxiFarePrediction" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71e9c-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="71e9c-116">Veri kümesini ve model dosyalarını depolamak için projenizde *Veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71e9c-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="71e9c-117">**Microsoft.ML** NuGet Paketini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="71e9c-118">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="71e9c-119">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, **Gözat** sekmesini seçin, **Microsoft.ML**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="71e9c-120">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="71e9c-121">**Microsoft.ML.FastTree** NuGet paketi için aynı şeyi yapın.</span><span class="sxs-lookup"><span data-stu-id="71e9c-121">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="71e9c-122">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="71e9c-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="71e9c-123">[Taksi-ücret-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taksi-ücret-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri kümelerini indirin ve bunları bir önceki adımda oluşturduğunuz *Veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="71e9c-124">Bu veri kümelerini makine öğrenimi modelini eğitmek ve modelin ne kadar doğru olduğunu değerlendirmek için kullanırız.</span><span class="sxs-lookup"><span data-stu-id="71e9c-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="71e9c-125">Bu veri setleri aslında [NYC TLC Taksi Gezisi veri kümesinden.](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)</span><span class="sxs-lookup"><span data-stu-id="71e9c-125">These data sets are originally from the [NYC TLC Taxi Trip data set](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span></span>

1. <span data-ttu-id="71e9c-126">**Çözüm Gezgini'nde** \*,.csv dosyalarının her birini sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="71e9c-127">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="71e9c-128">**Taksi-ücret-train.csv** veri kümesini açın ve ilk satırdaki sütun başlıklarına bakın.</span><span class="sxs-lookup"><span data-stu-id="71e9c-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="71e9c-129">Sütunların her birine bir göz atın.</span><span class="sxs-lookup"><span data-stu-id="71e9c-129">Take a look at each of the columns.</span></span> <span data-ttu-id="71e9c-130">Verileri anlayın ve hangi sütunların **özellik** olduğuna ve hangilerinin **etiket**olduğuna karar verin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="71e9c-131">Tahmin `label` etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="71e9c-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="71e9c-132">Tanımlanan `Features`girdiler, modeli tahmin etmek için `Label`verdiğiniz girdilerdir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="71e9c-133">Sağlanan veri kümesi aşağıdaki sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="71e9c-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="71e9c-134">**vendor_id:** Taksi satıcısının kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="71e9c-135">**rate_code:** Taksi gezisinin fiyat türü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="71e9c-136">**passenger_count:** Yolculuktaki yolcu sayısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="71e9c-137">**trip_time_in_secs:** Yolculuğun aldığı süre.</span><span class="sxs-lookup"><span data-stu-id="71e9c-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="71e9c-138">Yolculuk tamamlanmadan önce seyahat ücretini tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="71e9c-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="71e9c-139">O anda, yolculuğun ne kadar süreceğini bilemezsin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-139">At that moment, you don't know how long the trip would take.</span></span> <span data-ttu-id="71e9c-140">Bu nedenle, yolculuk süresi bir özellik değildir ve bu sütunu modelden dışlarsınız.</span><span class="sxs-lookup"><span data-stu-id="71e9c-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="71e9c-141">**trip_distance:** Yolculuk mesafesi bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="71e9c-142">**payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="71e9c-143">**fare_amount:** Ödenen toplam taksi ücreti etikettir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="71e9c-144">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="71e9c-144">Create data classes</span></span>

<span data-ttu-id="71e9c-145">Giriş verileri ve öngörüler için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="71e9c-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="71e9c-146">**Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="71e9c-147">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *TaxiTrip.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="71e9c-148">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="71e9c-149">Yeni dosyaya aşağıdaki `using` yönergeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="71e9c-150">Varolan sınıf tanımını kaldırın ve iki sınıfı `TaxiTrip` `TaxiTripFarePrediction`ve TaxiTrip.cs *dosyasına* aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="71e9c-151">`TaxiTrip`giriş veri sınıfıdır ve veri kümesi sütunlarının her biri için tanımlar vardır.</span><span class="sxs-lookup"><span data-stu-id="71e9c-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="71e9c-152">Veri <xref:Microsoft.ML.Data.LoadColumnAttribute> kümesindeki kaynak sütunların dizinlerini belirtmek için özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="71e9c-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="71e9c-153">Sınıf, `TaxiTripFarePrediction` öngörülen sonuçları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71e9c-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="71e9c-154">Tek bir float alanı `FareAmount`vardır, `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> uygulanan bir öznitelik ile.</span><span class="sxs-lookup"><span data-stu-id="71e9c-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="71e9c-155">Regresyon görevi söz konusu olduğunda, **Puan** sütunu tahmin edilmiş etiket değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-155">In case of the regression task, the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="71e9c-156">Giriş `float` ve tahmin veri sınıflarında kayan nokta değerlerini temsil etmek için türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="71e9c-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="71e9c-157">Veri ve model yollarını tanımlama</span><span class="sxs-lookup"><span data-stu-id="71e9c-157">Define data and model paths</span></span>

<span data-ttu-id="71e9c-158">Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="71e9c-159">Verileri kümeleri ve modeli kaydetmek için dosya ile dosyaların yollarını tutmak için üç alan oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="71e9c-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="71e9c-160">`_trainDataPath`modeli eğitmek için kullanılan veri kümesi ile dosyaya giden yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="71e9c-161">`_testDataPath`modeli değerlendirmek için kullanılan veri kümesi ile dosyaya giden yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="71e9c-162">`_modelPath`ilgili modelin depolandığı dosyaya giden yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="71e9c-163">Bu yolları belirtmek ve `Main` `_textLoader` değişken için yöntemin hemen üstüne aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="71e9c-164">Tüm ML.NET işlemleri [MLContext sınıfında](xref:Microsoft.ML.MLContext)başlar.</span><span class="sxs-lookup"><span data-stu-id="71e9c-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="71e9c-165">İlk `mlContext` başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71e9c-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="71e9c-166">Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.</span><span class="sxs-lookup"><span data-stu-id="71e9c-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="71e9c-167">Main'deki değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="71e9c-167">Initialize variables in Main</span></span>

<span data-ttu-id="71e9c-168">Değişkeni `Console.WriteLine("Hello World!")` `Main` bildirmek ve başlatmak için yöntemdeki satırı `mlContext` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="71e9c-169">`Main` Yöntemi çağırmak için yöntemde bir sonraki kod satırı olarak aşağıdakileri `Train` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

<span data-ttu-id="71e9c-170">Yöntem `Train()` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="71e9c-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="71e9c-171">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="71e9c-171">Loads the data.</span></span>
* <span data-ttu-id="71e9c-172">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="71e9c-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="71e9c-173">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-173">Trains the model.</span></span>
* <span data-ttu-id="71e9c-174">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="71e9c-174">Returns the model.</span></span>

<span data-ttu-id="71e9c-175">Yöntem `Train` modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-175">The `Train` method trains the model.</span></span> <span data-ttu-id="71e9c-176">Aşağıdaki kodu kullanarak `Main`bu yöntemi hemen aşağıda oluşturun:</span><span class="sxs-lookup"><span data-stu-id="71e9c-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="71e9c-177">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="71e9c-177">Load and transform data</span></span>

<span data-ttu-id="71e9c-178">ML.NET, sayısal veya metin tabular verileri açıklamanın esnek ve verimli bir yolu olarak [IDataView sınıfını](xref:Microsoft.ML.IDataView) kullanır.</span><span class="sxs-lookup"><span data-stu-id="71e9c-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="71e9c-179">`IDataView`metin dosyalarını veya gerçek zamanlı olarak yükleyebilir (örneğin, SQL veritabanı veya günlük dosyaları).</span><span class="sxs-lookup"><span data-stu-id="71e9c-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="71e9c-180">`Train()` Yöntemin ilk satırı olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

<span data-ttu-id="71e9c-181">Taksi yolculuğu ücretini tahmin etmek `FareAmount` istediğinizde, `Label` sütun tahmin edeceğiniz sütundur (modelin çıktısı).</span><span class="sxs-lookup"><span data-stu-id="71e9c-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model).</span></span> <span data-ttu-id="71e9c-182">Kopyalamak `CopyColumnsEstimator` `FareAmount`ve aşağıdaki kodu eklemek için dönüşüm sınıfını kullanın:</span><span class="sxs-lookup"><span data-stu-id="71e9c-182">Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="71e9c-183">Modeli eğiten algoritma **sayısal** özellikler gerektirir, bu nedenle kategorik verileri`VendorId`( `RateCode`, `PaymentType`ve )`VendorIdEncoded`değerlerini `RateCodeEncoded`sayılara ( , , ve `PaymentTypeEncoded`) dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-183">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="71e9c-184">Bunu yapmak için, sütunların her birinde farklı değerlere farklı sayısal anahtar değerleri atayan [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) dönüşüm sınıfını kullanın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-184">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="71e9c-185">Veri hazırlamadaki son adım, dönüşüm sınıfını **Features** kullanarak tüm `mlContext.Transforms.Concatenate` özellik sütunlarını Özellikler sütununa dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="71e9c-185">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="71e9c-186">Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler.</span><span class="sxs-lookup"><span data-stu-id="71e9c-186">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="71e9c-187">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-187">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="71e9c-188">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="71e9c-188">Choose a learning algorithm</span></span>

<span data-ttu-id="71e9c-189">Bu sorun New York'ta bir taksi gezisi ücret tahmin hakkında.</span><span class="sxs-lookup"><span data-stu-id="71e9c-189">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="71e9c-190">İlk bakışta, sadece kat edilen mesafeye bağlı gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-190">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="71e9c-191">Ancak, New York'taki taksi satıcıları ek yolcular veya nakit yerine kredi kartı ile ödeme gibi diğer faktörler için değişen tutarlar ücret.</span><span class="sxs-lookup"><span data-stu-id="71e9c-191">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="71e9c-192">Veri kümesindeki diğer etkenlere bağlı olarak gerçek bir değer olan fiyat değerini tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="71e9c-192">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="71e9c-193">Bunu yapmak için, bir [regresyon](../resources/glossary.md#regression) makinesi öğrenme görevi seçin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-193">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="71e9c-194">[FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) makine öğrenme görevini veri dönüştürme tanımlarına aşağıdaki kodu ekleyerek `Train()`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-194">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="71e9c-195">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="71e9c-195">Train the model</span></span>

<span data-ttu-id="71e9c-196">Modele eğitime `dataview` uygun hale getirin ve yönteme aşağıdaki `Train()` kod satırını ekleyerek eğitilmiş modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="71e9c-196">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

<span data-ttu-id="71e9c-197">[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-197">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="71e9c-198">`Train()` Yöntemde aşağıdaki kod satırı ile eğitilmiş modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="71e9c-198">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="71e9c-199">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="71e9c-199">Evaluate the model</span></span>

<span data-ttu-id="71e9c-200">Ardından, kalite güvencesi ve doğrulama için model performansınızı test verilerinizle değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-200">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="71e9c-201">`Evaluate()` Yöntemi aşağıdaki kodla `Train()`hemen sonra oluşturun:</span><span class="sxs-lookup"><span data-stu-id="71e9c-201">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="71e9c-202">Yöntem `Evaluate` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="71e9c-202">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="71e9c-203">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="71e9c-203">Loads the test dataset.</span></span>
* <span data-ttu-id="71e9c-204">Regresyon değerlendiricioluşturur.</span><span class="sxs-lookup"><span data-stu-id="71e9c-204">Creates the regression evaluator.</span></span>
* <span data-ttu-id="71e9c-205">Modeli değerlendirir ve ölçümler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71e9c-205">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="71e9c-206">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="71e9c-206">Displays the metrics.</span></span>

<span data-ttu-id="71e9c-207">Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `Train` hemen altında, yöntemden yeni yönteme çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-207">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="71e9c-208">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) yöntemini kullanarak test veri kümesini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-208">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="71e9c-209">Yönteme aşağıdaki kodu ekleyerek bu veri kümesini kalite `Evaluate` denetimi olarak kullanarak modeli değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-209">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="71e9c-210">Ardından, aşağıdaki `Test` kodu ekleyerek verileri `Evaluate()`dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="71e9c-210">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="71e9c-211">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesi giriş satırları için öngörüler yapar.</span><span class="sxs-lookup"><span data-stu-id="71e9c-211">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="71e9c-212">Yöntem, `RegressionContext.Evaluate` belirtilen veri kümesini `PredictionModel` kullanarak kalite ölçümlerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="71e9c-212">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="71e9c-213">Regresyon değerlendiriciler tarafından hesaplanan genel ölçümleri içeren bir <xref:Microsoft.ML.Data.RegressionMetrics> nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="71e9c-213">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="71e9c-214">Modelin kalitesini belirlemek için bunları görüntülemek için önce ölçümleri almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-214">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="71e9c-215">`Evaluate` Yöntemde sonraki satır olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-215">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="71e9c-216">Tahmin kümesini aldıktan sonra, Tahmin edilen değerleri test veri kümesindeki gerçek `Labels` değerlerle karşılaştıran ve modelin nasıl performans gösterdiğine ilişkin ölçümleri döndüren modeli [değerlendirin.](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A)</span><span class="sxs-lookup"><span data-stu-id="71e9c-216">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="71e9c-217">Modeli değerlendirmek ve değerlendirme ölçümlerini üretmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-217">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="71e9c-218">[RSquared](../resources/glossary.md#coefficient-of-determination) regresyon modellerinin başka bir değerlendirme ölçüsüdür.</span><span class="sxs-lookup"><span data-stu-id="71e9c-218">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="71e9c-219">RSquared 0 ile 1 arasındaki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="71e9c-219">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="71e9c-220">Değeri 1'e ne kadar yakınsa, model o kadar iyi.</span><span class="sxs-lookup"><span data-stu-id="71e9c-220">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="71e9c-221">RSquared değerini `Evaluate` görüntülemek için yönteme aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-221">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="71e9c-222">[RMS,](../resources/glossary.md#root-of-mean-squared-error-rmse) regresyon modelinin değerlendirme ölçümlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="71e9c-223">Ne kadar düşükse, model o kadar iyi olur.</span><span class="sxs-lookup"><span data-stu-id="71e9c-223">The lower it is, the better the model is.</span></span> <span data-ttu-id="71e9c-224">RMS değerini görüntülemek `Evaluate` için yönteme aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-224">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="71e9c-225">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="71e9c-225">Use the model for predictions</span></span>

<span data-ttu-id="71e9c-226">Yöntemden `TestSinglePrediction` `Evaluate` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="71e9c-226">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="71e9c-227">Yöntem `TestSinglePrediction` aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="71e9c-227">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="71e9c-228">Test verilerinin tek bir yorumunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71e9c-228">Creates a single comment of test data.</span></span>
* <span data-ttu-id="71e9c-229">Test verilerine göre ücret tutarını tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="71e9c-229">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="71e9c-230">Raporlama için test verilerini ve öngörüleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-230">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="71e9c-231">Öngörülen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="71e9c-231">Displays the predicted results.</span></span>

<span data-ttu-id="71e9c-232">Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `Evaluate` hemen altında, yöntemden yeni yönteme çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-232">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="71e9c-233">Aşağıdaki `PredictionEngine` kodu ekleyerek ücreti tahmin etmek `TestSinglePrediction()`için kullanın:</span><span class="sxs-lookup"><span data-stu-id="71e9c-233">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="71e9c-234">[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-234">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="71e9c-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="71e9c-236">Tek dişli veya prototip ortamlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-236">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="71e9c-237">Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın.</span><span class="sxs-lookup"><span data-stu-id="71e9c-237">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="71e9c-238">ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="71e9c-238">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="71e9c-239">`PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="71e9c-239">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="71e9c-240">Bu öğretici, bu sınıf içinde bir test gezisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="71e9c-240">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="71e9c-241">Daha sonra modelle deneme yapmak için başka senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71e9c-241">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="71e9c-242">Bir örnek oluşturarak `TestSinglePrediction()` yöntemde maliyet eğitimli modelin tahmin test `TaxiTrip`etmek için bir gezi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-242">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="71e9c-243">Ardından, taksi yolculuğu verilerinin tek bir örneğine `PredictionEngine` göre ücreti tahmin edin ve yöntemde bir `TestSinglePrediction()` sonraki kod satırları olarak aşağıdakileri ekleyerek bu ücreti iletin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-243">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="71e9c-244">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri örneği üzerinde bir tahminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="71e9c-244">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="71e9c-245">Belirtilen seyahatin öngörülen ücretini görüntülemek için `TestSinglePrediction` yönteme aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="71e9c-245">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="71e9c-246">Test örneğiniz için öngörülen taksi ücretini görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="71e9c-246">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="71e9c-247">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="71e9c-247">Congratulations!</span></span> <span data-ttu-id="71e9c-248">Şimdi başarılı taksi yolculuk ücretleri tahmin etmek için bir makine öğrenme modeli inşa ettik, doğruluğunu değerlendirdi, ve tahminler yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71e9c-248">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="71e9c-249">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71e9c-249">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="71e9c-250">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="71e9c-250">Next steps</span></span>

<span data-ttu-id="71e9c-251">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="71e9c-251">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="71e9c-252">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="71e9c-252">Prepare and understand the data</span></span>
> * <span data-ttu-id="71e9c-253">Öğrenme ardışık bir yol oluşturma</span><span class="sxs-lookup"><span data-stu-id="71e9c-253">Create a learning pipeline</span></span>
> * <span data-ttu-id="71e9c-254">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="71e9c-254">Load and transform the data</span></span>
> * <span data-ttu-id="71e9c-255">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="71e9c-255">Choose a learning algorithm</span></span>
> * <span data-ttu-id="71e9c-256">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="71e9c-256">Train the model</span></span>
> * <span data-ttu-id="71e9c-257">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="71e9c-257">Evaluate the model</span></span>
> * <span data-ttu-id="71e9c-258">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="71e9c-258">Use the model for predictions</span></span>

<span data-ttu-id="71e9c-259">Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="71e9c-259">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="71e9c-260">Iris kümelemesi</span><span class="sxs-lookup"><span data-stu-id="71e9c-260">Iris clustering</span></span>](iris-clustering.md)
