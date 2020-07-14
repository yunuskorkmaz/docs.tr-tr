---
title: 'Öğretici: gerileme kullanarak fiyatları tahmin etme'
description: Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.NET kullanarak bir gerileme modelinin nasıl oluşturulacağı gösterilmektedir.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 27054e28f9a4fa628f0d7348d45528b690d7da83
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281777"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="0ea95-103">Öğretici: ML.NET ile gerileme kullanarak fiyatları tahmin etme</span><span class="sxs-lookup"><span data-stu-id="0ea95-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="0ea95-104">Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.NET kullanarak bir [gerileme modelinin](../resources/glossary.md#regression) nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="0ea95-105">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="0ea95-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="0ea95-106">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="0ea95-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="0ea95-107">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0ea95-107">Load and transform the data</span></span>
> * <span data-ttu-id="0ea95-108">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="0ea95-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="0ea95-109">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="0ea95-109">Train the model</span></span>
> * <span data-ttu-id="0ea95-110">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="0ea95-110">Evaluate the model</span></span>
> * <span data-ttu-id="0ea95-111">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="0ea95-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0ea95-112">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="0ea95-112">Prerequisites</span></span>

* <span data-ttu-id="0ea95-113">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri, ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="0ea95-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="0ea95-114">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ea95-114">Create a console application</span></span>

1. <span data-ttu-id="0ea95-115">"Taxifaretahminini" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ea95-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="0ea95-116">Veri kümesi ve model dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ea95-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="0ea95-117">**Microsoft.ml** NuGet paketini yükler:</span><span class="sxs-lookup"><span data-stu-id="0ea95-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="0ea95-118">**Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0ea95-119">Paket kaynağı olarak "nuget.org" öğesini seçin, **Araştır** sekmesini seçin, **Microsoft.ml**için arama yapın, listeden paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0ea95-120">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="0ea95-121">**Microsoft. ml. FastTree** NuGet paketi için de aynısını yapın.</span><span class="sxs-lookup"><span data-stu-id="0ea95-121">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="0ea95-122">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="0ea95-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="0ea95-123">[taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri kümelerini indirin ve önceki adımda oluşturduğunuz *veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="0ea95-124">Machine Learning modelini eğitmek için bu veri kümelerini kullanıyoruz ve sonra modelin ne kadar doğru olduğunu değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="0ea95-125">Bu veri kümeleri başlangıçta [NYC TLC TAXI seyahat veri kümesinden](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)alınır.</span><span class="sxs-lookup"><span data-stu-id="0ea95-125">These data sets are originally from the [NYC TLC Taxi Trip data set](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span></span>

1. <span data-ttu-id="0ea95-126">**Çözüm Gezgini**,. csv dosyalarının her birine sağ tıklayın \* ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="0ea95-127">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="0ea95-128">**taxi-fare-train.csv** veri kümesini açın ve ilk satırdaki sütun başlıklarına bakın.</span><span class="sxs-lookup"><span data-stu-id="0ea95-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="0ea95-129">Her sütuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="0ea95-129">Take a look at each of the columns.</span></span> <span data-ttu-id="0ea95-130">Verileri anlayın ve hangi sütunların **Özellikler** olduğunu ve hangisinin **etiket**olduğunu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="0ea95-131">`label`Tahmin etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="0ea95-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="0ea95-132">`Features`, Modeli tahmin etmek için size izin verdiğiniz girişlerdir `Label` .</span><span class="sxs-lookup"><span data-stu-id="0ea95-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="0ea95-133">Belirtilen veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="0ea95-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="0ea95-134">**vendor_id:** Taxı satıcısının KIMLIĞI bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="0ea95-135">**rate_code:** Taxı seyahati 'ın hız türü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="0ea95-136">**passenger_count:** Seyahat üzerindeki pascuların sayısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="0ea95-137">**trip_time_in_secs:** Seyahati için geçen süre.</span><span class="sxs-lookup"><span data-stu-id="0ea95-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="0ea95-138">Seyahat tamamlanmadan önce seyahat tarifeli havayolu tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="0ea95-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="0ea95-139">Bu sırada, seyahati ne kadar süreyle yapılacağını bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ea95-139">At that moment, you don't know how long the trip would take.</span></span> <span data-ttu-id="0ea95-140">Bu nedenle, seyahat süresi bir özellik değildir ve bu sütunu modelden dışlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ea95-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="0ea95-141">**trip_distance:** Seyahat uzaklığı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="0ea95-142">**payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="0ea95-143">**fare_amount:** Ödenen toplam TAXI tarifeli havayolu etikettir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="0ea95-144">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ea95-144">Create data classes</span></span>

<span data-ttu-id="0ea95-145">Giriş verileri ve tahminleri için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0ea95-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="0ea95-146">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="0ea95-147">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *TaxiTrip.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="0ea95-148">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="0ea95-149">Aşağıdaki `using` yönergeleri yeni dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](./snippets/predict-prices/csharp/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="0ea95-150">Mevcut sınıf tanımını kaldırın ve iki sınıfa `TaxiTrip` ve `TaxiTripFarePrediction` *TaxiTrip.cs* dosyasına sahip olan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](./snippets/predict-prices/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="0ea95-151">`TaxiTrip`, giriş veri sınıfıdır ve veri kümesi sütunlarının her biri için tanımlar içerir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="0ea95-152"><xref:Microsoft.ML.Data.LoadColumnAttribute>Veri kümesindeki kaynak sütunlarının dizinlerini belirtmek için özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ea95-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="0ea95-153">`TaxiTripFarePrediction`Sınıfı tahmin edilen sonuçları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ea95-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="0ea95-154">Özniteliği uygulanmış tek bir float alanı vardır `FareAmount` `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0ea95-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="0ea95-155">Regresyon görevi söz konusu olduğunda, **puan** sütunu tahmin edilen etiket değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-155">In case of the regression task, the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="0ea95-156">`float`Giriş ve tahmin veri sınıflarında kayan nokta değerlerini göstermek için türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ea95-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="0ea95-157">Veri ve model yollarını tanımlama</span><span class="sxs-lookup"><span data-stu-id="0ea95-157">Define data and model paths</span></span>

<span data-ttu-id="0ea95-158">Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](./snippets/predict-prices/csharp/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="0ea95-159">Veri kümelerine sahip dosyaların yollarını tutmak için üç alan oluşturmanız ve modelin kaydedileceği dosyanın olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="0ea95-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="0ea95-160">`_trainDataPath`modeli eğitmek için kullanılan veri kümesiyle dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="0ea95-161">`_testDataPath`modeli değerlendirmek için kullanılan veri kümesiyle dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="0ea95-162">`_modelPath`eğitilen modelin depolandığı dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="0ea95-163">`Main`Bu yolları ve değişkeni belirtmek için yönteminin hemen üstüne aşağıdaki kodu ekleyin `_textLoader` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](./snippets/predict-prices/csharp/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="0ea95-164">Tüm ML.NET işlemleri [Mlcontext sınıfında](xref:Microsoft.ML.MLContext)başlar.</span><span class="sxs-lookup"><span data-stu-id="0ea95-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="0ea95-165">Başlatma `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilecek yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ea95-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="0ea95-166">Entity Framework, kavramsal olarak da benzerdir `DBContext` .</span><span class="sxs-lookup"><span data-stu-id="0ea95-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="0ea95-167">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="0ea95-167">Initialize variables in Main</span></span>

<span data-ttu-id="0ea95-168">`Console.WriteLine("Hello World!")` `Main` Yöntemi bildirmek ve başlatmak için yöntemindeki satırı aşağıdaki kodla değiştirin `mlContext` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](./snippets/predict-prices/csharp/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="0ea95-169">`Main`Yöntemi çağırmak için yöntemi içindeki sonraki kod satırı olarak aşağıdakini ekleyin `Train` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](./snippets/predict-prices/csharp/Program.cs#5 "Train your model")]

<span data-ttu-id="0ea95-170">`Train()`Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="0ea95-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="0ea95-171">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="0ea95-171">Loads the data.</span></span>
* <span data-ttu-id="0ea95-172">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0ea95-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="0ea95-173">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="0ea95-173">Trains the model.</span></span>
* <span data-ttu-id="0ea95-174">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ea95-174">Returns the model.</span></span>

<span data-ttu-id="0ea95-175">`Train`Yöntemi modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="0ea95-175">The `Train` method trains the model.</span></span> <span data-ttu-id="0ea95-176">Aşağıdaki kodu kullanarak bu yöntemi hemen aşağıda oluşturun `Main` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="0ea95-177">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0ea95-177">Load and transform data</span></span>

<span data-ttu-id="0ea95-178">ML.NET, sayısal veya metin tablolu verileri tanımlamaya yönelik esnek ve verimli bir yöntem olarak [ıdataview sınıfını](xref:Microsoft.ML.IDataView) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ea95-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="0ea95-179">`IDataView`metin dosyalarını veya gerçek zamanlı olarak yükleyebilirsiniz (örneğin, SQL veritabanı veya günlük dosyaları).</span><span class="sxs-lookup"><span data-stu-id="0ea95-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="0ea95-180">Aşağıdaki kodu yönteminin ilk satırı olarak ekleyin `Train()` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](./snippets/predict-prices/csharp/Program.cs#6 "loading training dataset")]

<span data-ttu-id="0ea95-181">Taxı seyahat tarifeli havayolu tahmin etmek istediğiniz gibi, `FareAmount` `Label` Bu sütun tahmin ettiğiniz (modelin çıktısı) olur.</span><span class="sxs-lookup"><span data-stu-id="0ea95-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model).</span></span> <span data-ttu-id="0ea95-182">`CopyColumnsEstimator`Kopyalamak için dönüştürme sınıfını kullanın `FareAmount` ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-182">Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](./snippets/predict-prices/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="0ea95-183">Modeli gösteren algoritma **sayısal** Özellikler gerektirir, bu nedenle kategorik verileri ( `VendorId` , `RateCode` ve `PaymentType` ) değerlerini sayılara ( `VendorIdEncoded` ,, `RateCodeEncoded` ve `PaymentTypeEncoded` ) dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-183">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="0ea95-184">Bunu yapmak için, sütunların her birinde farklı değerlere farklı sayısal anahtar değerleri atayan [Onehotencodingtransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) dönüştürme sınıfını kullanın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-184">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](./snippets/predict-prices/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="0ea95-185">Veri hazırlığının son adımı, tüm özellik sütunlarını, dönüştürme sınıfını kullanarak **Özellikler** sütunuyla birleştirir `mlContext.Transforms.Concatenate` .</span><span class="sxs-lookup"><span data-stu-id="0ea95-185">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="0ea95-186">Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler.</span><span class="sxs-lookup"><span data-stu-id="0ea95-186">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="0ea95-187">Şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-187">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](./snippets/predict-prices/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="0ea95-188">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="0ea95-188">Choose a learning algorithm</span></span>

<span data-ttu-id="0ea95-189">Bu sorun, New York şehrinde bir TAXI seyahat tarifeli havayolu tahmin etmeye yönelik olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0ea95-189">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="0ea95-190">İlk bakışta, yalnızca seyahat mesafesini temel alan görünebilir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-190">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="0ea95-191">Ancak, New York 'taki TAXI satıcıları, ek Pastörler veya nakit yerine kredi kartıyla ödeme yapma gibi diğer faktörlere göre farklılık gösteren ücretler ücretlendirir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-191">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="0ea95-192">Veri kümesindeki diğer faktörlere bağlı olarak gerçek bir değer olan fiyat değerini tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="0ea95-192">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="0ea95-193">Bunu yapmak için bir [gerileme](../resources/glossary.md#regression) makine öğrenimi görevi seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="0ea95-193">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="0ea95-194">Aşağıdaki kod satırı olarak aşağıdakini ekleyerek [Fasttreeregressiontrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) Machine Learning görevini veri dönüştürme tanımlarına ekleyin `Train()` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-194">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](./snippets/predict-prices/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="0ea95-195">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="0ea95-195">Train the model</span></span>

<span data-ttu-id="0ea95-196">`dataview`Aşağıdaki kod satırını yönteme ekleyerek modeli eğitimine sığdırın ve eğitilen modeli döndürün `Train()` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-196">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](./snippets/predict-prices/csharp/Program.cs#11 "Train the model")]

<span data-ttu-id="0ea95-197">[Fit ()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.</span><span class="sxs-lookup"><span data-stu-id="0ea95-197">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="0ea95-198">Aşağıdaki kod satırıyla eğitilen modeli döndürün `Train()` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-198">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](./snippets/predict-prices/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="0ea95-199">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="0ea95-199">Evaluate the model</span></span>

<span data-ttu-id="0ea95-200">Daha sonra, kalite güvencesi ve doğrulama için test verilerinize ait model performansınızı değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-200">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="0ea95-201">`Evaluate()`Aşağıdaki kodla hemen sonra yöntemi oluşturun `Train()` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-201">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0ea95-202">`Evaluate`Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="0ea95-202">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="0ea95-203">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="0ea95-203">Loads the test dataset.</span></span>
* <span data-ttu-id="0ea95-204">Regresyon Değerlendiricisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ea95-204">Creates the regression evaluator.</span></span>
* <span data-ttu-id="0ea95-205">Modeli değerlendirir ve ölçümler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ea95-205">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="0ea95-206">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ea95-206">Displays the metrics.</span></span>

<span data-ttu-id="0ea95-207">`Main`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `Train` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-207">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](./snippets/predict-prices/csharp/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="0ea95-208">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) yöntemini kullanarak test veri kümesini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-208">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="0ea95-209">Yöntemine aşağıdaki kodu ekleyerek bu veri kümesini bir kalite denetimi olarak kullanarak modeli değerlendirin `Evaluate` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-209">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](./snippets/predict-prices/csharp/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="0ea95-210">Ardından, `Test` aşağıdaki kodu öğesine ekleyerek verileri dönüştürün `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-210">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](./snippets/predict-prices/csharp/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="0ea95-211">[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesi giriş satırları için tahminleri yapar.</span><span class="sxs-lookup"><span data-stu-id="0ea95-211">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="0ea95-212">`RegressionContext.Evaluate`Yöntemi, `PredictionModel` belirtilen veri kümesini kullanarak için kalite ölçümlerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="0ea95-212">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="0ea95-213"><xref:Microsoft.ML.Data.RegressionMetrics>Regresyon değerlendiricileri tarafından hesaplanan genel ölçümleri içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ea95-213">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="0ea95-214">Modelin kalitesini belirlemede bunları göstermek için öncelikle ölçümleri almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-214">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="0ea95-215">Aşağıdaki kodu yönteminin sonraki satırı olarak ekleyin `Evaluate` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-215">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](./snippets/predict-prices/csharp/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="0ea95-216">Tahmin kümesine sahip olduktan sonra, tahmin edilen değerleri test veri kümesindeki gerçek ile karşılaştıran ve modelin nasıl çalıştığı hakkında ölçümler döndüren [değerlendir ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) yöntemi, modeli değerlendirir `Labels` .</span><span class="sxs-lookup"><span data-stu-id="0ea95-216">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="0ea95-217">Modeli değerlendirmek ve değerlendirme ölçümlerini oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-217">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="0ea95-218">[RKARE](../resources/glossary.md#coefficient-of-determination) , regresyon modellerinin başka bir değerlendirme ölçümdür.</span><span class="sxs-lookup"><span data-stu-id="0ea95-218">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="0ea95-219">RKARE 0 ile 1 arasında değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="0ea95-219">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="0ea95-220">Daha yakın değeri 1 ' dir, model daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-220">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="0ea95-221">`Evaluate`RKARE değerini göstermek için yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-221">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](./snippets/predict-prices/csharp/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="0ea95-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) , regresyon modelinin değerlendirme ölçümlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="0ea95-223">Bunun ne kadar küçük olması, modelin ne kadar iyi olduğu.</span><span class="sxs-lookup"><span data-stu-id="0ea95-223">The lower it is, the better the model is.</span></span> <span data-ttu-id="0ea95-224">`Evaluate`RMS değerini göstermek için yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-224">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](./snippets/predict-prices/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="0ea95-225">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="0ea95-225">Use the model for predictions</span></span>

<span data-ttu-id="0ea95-226">`TestSinglePrediction`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `Evaluate` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-226">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0ea95-227">`TestSinglePrediction`Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="0ea95-227">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="0ea95-228">Test verileri için tek bir açıklama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ea95-228">Creates a single comment of test data.</span></span>
* <span data-ttu-id="0ea95-229">Sınama verilerine göre tarifeli havayolu miktarını tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="0ea95-229">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="0ea95-230">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-230">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="0ea95-231">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ea95-231">Displays the predicted results.</span></span>

<span data-ttu-id="0ea95-232">`Main`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `Evaluate` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-232">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](./snippets/predict-prices/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="0ea95-233">`PredictionEngine`Aşağıdaki kodu öğesine ekleyerek tarifeli havayolu tahmin etmek için kullanın `TestSinglePrediction()` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-233">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](./snippets/predict-prices/csharp/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="0ea95-234">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-234">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="0ea95-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="0ea95-236">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="0ea95-236">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="0ea95-237">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ea95-237">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="0ea95-238">[ `PredictionEnginePool` ASP.NET Core Web API 'sinde kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="0ea95-238">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="0ea95-239">`PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="0ea95-239">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="0ea95-240">Bu öğretici, bu sınıf içinde bir test yolculuğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ea95-240">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="0ea95-241">Daha sonra, modelle denemeler yapmak için başka senaryolar da ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ea95-241">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="0ea95-242">Bir örneği oluşturarak eğitilen modelin Maliyet tahminini test etmek için bir seyahat ekleyin `TestSinglePrediction()` `TaxiTrip` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-242">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](./snippets/predict-prices/csharp/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="0ea95-243">Sonra, tarifeli havayolu öğesini bir taksi seyahat verisinin tek bir örneğine göre tahmin edin ve `PredictionEngine` Aşağıdaki kod satırları yöntemine ekleyerek bunu öğesine geçirin `TestSinglePrediction()` :</span><span class="sxs-lookup"><span data-stu-id="0ea95-243">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="0ea95-244">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, verilerin tek bir örneğini tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="0ea95-244">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="0ea95-245">Belirtilen seyahati için öngörülen tarifeli havayolu 'yi göstermek için aşağıdaki kodu `TestSinglePrediction` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ea95-245">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="0ea95-246">Test çalışmanıza yönelik tahmini TAXI tarifeli havayolu görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0ea95-246">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="0ea95-247">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="0ea95-247">Congratulations!</span></span> <span data-ttu-id="0ea95-248">Artık TAXI seyahat Fares 'yi tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz, doğruluğu değerlendirildi ve tahmine dayalı hale getirmek için kullandınız.</span><span class="sxs-lookup"><span data-stu-id="0ea95-248">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="0ea95-249">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ea95-249">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0ea95-250">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0ea95-250">Next steps</span></span>

<span data-ttu-id="0ea95-251">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="0ea95-251">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="0ea95-252">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="0ea95-252">Prepare and understand the data</span></span>
> * <span data-ttu-id="0ea95-253">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ea95-253">Create a learning pipeline</span></span>
> * <span data-ttu-id="0ea95-254">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0ea95-254">Load and transform the data</span></span>
> * <span data-ttu-id="0ea95-255">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="0ea95-255">Choose a learning algorithm</span></span>
> * <span data-ttu-id="0ea95-256">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="0ea95-256">Train the model</span></span>
> * <span data-ttu-id="0ea95-257">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="0ea95-257">Evaluate the model</span></span>
> * <span data-ttu-id="0ea95-258">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="0ea95-258">Use the model for predictions</span></span>

<span data-ttu-id="0ea95-259">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="0ea95-259">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0ea95-260">Iris kümelemesi</span><span class="sxs-lookup"><span data-stu-id="0ea95-260">Iris clustering</span></span>](iris-clustering.md)
