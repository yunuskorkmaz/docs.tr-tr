---
title: 'Öğretici: gerileme kullanarak fiyatları tahmin etme'
description: Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.NET kullanarak bir gerileme modelinin nasıl oluşturulacağı gösterilmektedir.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 298dd4aa97518bcfdb0c5c4f00e0135a328b3b9a
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774428"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="b1bb3-103">Öğretici: ML.NET ile gerileme kullanarak fiyatları tahmin etme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="b1bb3-104">Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.NET kullanarak bir [gerileme modelinin](../resources/glossary.md#regression) nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="b1bb3-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="b1bb3-106">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="b1bb3-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="b1bb3-107">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-107">Load and transform the data</span></span>
> * <span data-ttu-id="b1bb3-108">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="b1bb3-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="b1bb3-109">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-109">Train the model</span></span>
> * <span data-ttu-id="b1bb3-110">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-110">Evaluate the model</span></span>
> * <span data-ttu-id="b1bb3-111">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="b1bb3-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1bb3-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b1bb3-112">Prerequisites</span></span>

* <span data-ttu-id="b1bb3-113">[Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b1bb3-114">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1bb3-114">Create a console application</span></span>

1. <span data-ttu-id="b1bb3-115">"Taxifaretahminini" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="b1bb3-116">Veri kümesi ve model dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="b1bb3-117">**Microsoft.ml** NuGet paketini yükler:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="b1bb3-118">**Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b1bb3-119">Paket kaynağı olarak "nuget.org" öğesini seçin, **Araştır** sekmesini seçin, **Microsoft.ml**için arama yapın, listeden paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b1bb3-120">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="b1bb3-121">**Microsoft. ml. FastTree** NuGet paketi için de aynısını yapın.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-121">Do the same for the **Microsoft.ML.FastTree** Nuget package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="b1bb3-122">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="b1bb3-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="b1bb3-123">[Taxi-fare-train. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [Taxi-fare-test. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri kümelerini indirin ve önceki adımda oluşturduğunuz *veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="b1bb3-124">Machine Learning modelini eğitmek için bu veri kümelerini kullanıyoruz ve sonra modelin ne kadar doğru olduğunu değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="b1bb3-125">Bu veri kümeleri başlangıçta [NYC TLC TAXI seyahat veri kümesinden](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)alınır.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-125">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="b1bb3-126">**Çözüm Gezgini**, \*. csv dosyalarının her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="b1bb3-127">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="b1bb3-128">**Taxi-fare-train. csv** veri kümesini açın ve ilk satırdaki sütun başlıklarına bakın.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="b1bb3-129">Her sütuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-129">Take a look at each of the columns.</span></span> <span data-ttu-id="b1bb3-130">Verileri anlayın ve hangi sütunların **Özellikler** olduğunu ve hangisinin **etiket**olduğunu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="b1bb3-131">@No__t_0, tahmin etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="b1bb3-132">@No__t_1 tahmin etmek için modele verdiğiniz girdilerin `Features`are tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="b1bb3-133">Belirtilen veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="b1bb3-134">**vendor_id:** Taxı satıcısının KIMLIĞI bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="b1bb3-135">**rate_code:** Taxı seyahati 'ın hız türü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="b1bb3-136">**passenger_count:** Seyahat üzerindeki pascuların sayısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="b1bb3-137">**trip_time_in_secs:** Seyahati için geçen süre.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="b1bb3-138">Seyahat tamamlanmadan önce seyahat tarifeli havayolu tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="b1bb3-139">Bu anda seyahati ne kadar süreyle yapılacağını bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="b1bb3-140">Bu nedenle, seyahat süresi bir özellik değildir ve bu sütunu modelden dışlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="b1bb3-141">**trip_distance:** Seyahat uzaklığı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="b1bb3-142">**payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="b1bb3-143">**fare_amount:** Ödenen toplam TAXI tarifeli havayolu etikettir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="b1bb3-144">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1bb3-144">Create data classes</span></span>

<span data-ttu-id="b1bb3-145">Giriş verileri ve tahminleri için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="b1bb3-146">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b1bb3-147">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *TaxiTrip.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="b1bb3-148">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b1bb3-149">Aşağıdaki `using` yönergelerini yeni dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="b1bb3-150">Mevcut sınıf tanımını kaldırın ve *TaxiTrip.cs* dosyasına `TaxiTrip` ve `TaxiTripFarePrediction` iki sınıfa sahip aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="b1bb3-151">`TaxiTrip`, giriş veri sınıfıdır ve veri kümesi sütunlarının her biri için tanımlar içerir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="b1bb3-152">Veri kümesindeki kaynak sütunlarının dizinlerini belirtmek için <xref:Microsoft.ML.Data.LoadColumnAttribute> özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="b1bb3-153">@No__t_0 sınıfı tahmin edilen sonuçları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="b1bb3-154">Tek bir float alanına sahiptir ve bir `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> özniteliği uygulanmış `FareAmount`.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="b1bb3-155">Regresyon görevi söz konusu olduğunda, **puan** sütunu tahmin edilen etiket değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-155">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="b1bb3-156">Giriş ve tahmin veri sınıflarında kayan nokta değerlerini göstermek için `float` türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="b1bb3-157">Veri ve model yollarını tanımlama</span><span class="sxs-lookup"><span data-stu-id="b1bb3-157">Define data and model paths</span></span>

<span data-ttu-id="b1bb3-158">*Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="b1bb3-159">Veri kümelerine sahip dosyaların yollarını tutmak için üç alan oluşturmanız ve modelin kaydedileceği dosyanın olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="b1bb3-160">`_trainDataPath`, modeli eğitmek için kullanılan veri kümesiyle dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="b1bb3-161">`_testDataPath`, modeli değerlendirmek için kullanılan veri kümesi ile dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="b1bb3-162">`_modelPath`, eğitilen modelin depolandığı dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="b1bb3-163">Bu yolları ve `_textLoader` değişkenini belirtmek için `Main` yönteminin üstüne aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="b1bb3-164">Tüm ML.NET işlemleri [Mlcontext sınıfında](xref:Microsoft.ML.MLContext)başlar.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="b1bb3-165">@No__t_0 başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="b1bb3-166">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="b1bb3-167">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="b1bb3-167">Initialize variables in Main</span></span>

<span data-ttu-id="b1bb3-168">@No__t_2 değişkenini bildirmek ve başlatmak için `Main` yöntemindeki `Console.WriteLine("Hello World!")` satırı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="b1bb3-169">@No__t_1 yöntemini çağırmak için `Main` metoduna sonraki kod satırı olarak aşağıdakini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="b1bb3-170">@No__t_0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="b1bb3-171">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-171">Loads the data.</span></span>
* <span data-ttu-id="b1bb3-172">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="b1bb3-173">Modeli TRAIN.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-173">Trains the model.</span></span>
* <span data-ttu-id="b1bb3-174">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-174">Returns the model.</span></span>

<span data-ttu-id="b1bb3-175">@No__t_0 yöntemi modeli trafelar.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-175">The `Train` method trains the model.</span></span> <span data-ttu-id="b1bb3-176">Aşağıdaki kodu kullanarak bu yöntemi hemen `Main` aşağıda oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="b1bb3-177">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-177">Load and transform data</span></span>

<span data-ttu-id="b1bb3-178">ML.NET, sayısal veya metin tablolu verileri tanımlamaya yönelik esnek ve verimli bir yöntem olarak [ıdataview sınıfını](xref:Microsoft.ML.IDataView) kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="b1bb3-179">`IDataView` metin dosyalarını veya gerçek zamanlı olarak yükleyebilirsiniz (örneğin, SQL veritabanı veya günlük dosyaları).</span><span class="sxs-lookup"><span data-stu-id="b1bb3-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="b1bb3-180">@No__t_0 yönteminin ilk satırı olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="b1bb3-181">Taxı seyahat tarifeli havayolu tahmin etmek istediğiniz için `FareAmount` sütunu tahmin ettiğiniz `Label` (modelin çıktısı) `FareAmount` kopyalamak için `CopyColumnsEstimator` dönüştürme sınıfını kullanır ve aşağıdaki kodu eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model)Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="b1bb3-182">Modeli gösteren algoritma **sayısal** Özellikler gerektirir, bu nedenle kategorik verileri (`VendorId`, `RateCode` ve `PaymentType`) değerlerini sayılara (`VendorIdEncoded`, `RateCodeEncoded` ve `PaymentTypeEncoded`) dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-182">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="b1bb3-183">Bunu yapmak için, sütunların her birinde farklı değerlere farklı sayısal anahtar değerleri atayan [Onehotencodingtransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) dönüştürme sınıfını kullanın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-183">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="b1bb3-184">Veri hazırlığının son adımı, tüm özellik sütunlarını `mlContext.Transforms.Concatenate` dönüştürme sınıfını kullanarak **Özellikler** sütunuyla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-184">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="b1bb3-185">Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="b1bb3-186">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-186">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="b1bb3-187">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="b1bb3-187">Choose a learning algorithm</span></span>

<span data-ttu-id="b1bb3-188">Bu sorun, New York şehrinde bir TAXI seyahat tarifeli havayolu tahmin etmeye yönelik olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-188">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="b1bb3-189">İlk bakışta, yalnızca seyahat mesafesini temel alan görünebilir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-189">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="b1bb3-190">Ancak, New York 'taki TAXI satıcıları, ek Pastörler veya nakit yerine kredi kartıyla ödeme yapma gibi diğer faktörlere göre farklılık gösteren ücretler ücretlendirir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-190">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="b1bb3-191">Veri kümesindeki diğer faktörlere bağlı olarak gerçek bir değer olan fiyat değerini tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-191">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="b1bb3-192">Bunu yapmak için bir [gerileme](../resources/glossary.md#regression) makine öğrenimi görevi seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-192">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="b1bb3-193">Aşağıdaki `Train()` kod satırı olarak aşağıdakini ekleyerek [Fasttreeregressiontrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) Machine Learning görevini veri dönüştürme tanımlarına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-193">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="b1bb3-194">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-194">Train the model</span></span>

<span data-ttu-id="b1bb3-195">Modeli eğitim `dataview` sığdırın ve aşağıdaki kod satırını `Train()` yöntemine ekleyerek eğitilen modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-195">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="b1bb3-196">[Fit ()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-196">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="b1bb3-197">@No__t_0 yönteminde aşağıdaki kod satırıyla eğitilen modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-197">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="b1bb3-198">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-198">Evaluate the model</span></span>

<span data-ttu-id="b1bb3-199">Daha sonra, kalite güvencesi ve doğrulama için test verilerinize ait model performansınızı değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-199">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="b1bb3-200">Aşağıdaki kodla `Train()` hemen sonra `Evaluate()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-200">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="b1bb3-201">@No__t_0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-201">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="b1bb3-202">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-202">Loads the test dataset.</span></span>
* <span data-ttu-id="b1bb3-203">Regresyon Değerlendiricisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-203">Creates the regression evaluator.</span></span>
* <span data-ttu-id="b1bb3-204">Modeli değerlendirir ve ölçümler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-204">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="b1bb3-205">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-205">Displays the metrics.</span></span>

<span data-ttu-id="b1bb3-206">Aşağıdaki kodu kullanarak, `Train` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-206">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="b1bb3-207">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) yöntemini kullanarak test veri kümesini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-207">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="b1bb3-208">@No__t_0 yöntemine aşağıdaki kodu ekleyerek bu veri kümesini bir kalite denetimi olarak kullanarak modeli değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-208">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="b1bb3-209">Ardından, aşağıdaki kodu `Evaluate()` ekleyerek `Test` verileri dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-209">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="b1bb3-210">[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesi giriş satırları için tahminleri yapar.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-210">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="b1bb3-211">@No__t_0 yöntemi, belirtilen veri kümesini kullanarak `PredictionModel` için kalite ölçümlerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-211">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="b1bb3-212">Regresyon değerlendiricileri tarafından hesaplanan genel ölçümleri içeren bir <xref:Microsoft.ML.Data.RegressionMetrics> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-212">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="b1bb3-213">Modelin kalitesini belirlemede bunları göstermek için öncelikle ölçümleri almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-213">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="b1bb3-214">Aşağıdaki kodu `Evaluate` yönteminin sonraki satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-214">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="b1bb3-215">Tahmin kümesine sahip olduktan sonra, tahmin edilen değerleri test veri kümesindeki gerçek `Labels` karşılaştıran ve modelin nasıl çalıştığı hakkında ölçümler döndüren [değerlendir ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) yöntemi, modeli değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-215">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="b1bb3-216">Modeli değerlendirmek ve değerlendirme ölçümlerini oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-216">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="b1bb3-217">[RKARE](../resources/glossary.md#coefficient-of-determination) , regresyon modellerinin başka bir değerlendirme ölçümdür.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-217">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="b1bb3-218">RKARE 0 ile 1 arasında değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-218">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="b1bb3-219">Daha yakın değeri 1 ' dir, model daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-219">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="b1bb3-220">RKARE değerini göstermek için `Evaluate` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-220">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="b1bb3-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) , regresyon modelinin değerlendirme ölçümlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="b1bb3-222">Bunun ne kadar küçük olması, modelin ne kadar iyi olduğu.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-222">The lower it is, the better the model is.</span></span> <span data-ttu-id="b1bb3-223">RMS değerini göstermek için `Evaluate` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-223">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="b1bb3-224">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="b1bb3-224">Use the model for predictions</span></span>

<span data-ttu-id="b1bb3-225">Aşağıdaki kodu kullanarak, `Evaluate` yönteminden hemen sonra `TestSinglePrediction` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-225">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="b1bb3-226">@No__t_0 yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-226">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="b1bb3-227">Test verileri için tek bir açıklama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-227">Creates a single comment of test data.</span></span>
* <span data-ttu-id="b1bb3-228">Sınama verilerine göre tarifeli havayolu miktarını tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-228">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="b1bb3-229">Raporlama için test verilerini ve tahminleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-229">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="b1bb3-230">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-230">Displays the predicted results.</span></span>

<span data-ttu-id="b1bb3-231">Aşağıdaki kodu kullanarak, `Evaluate` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-231">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="b1bb3-232">Aşağıdaki kodu `TestSinglePrediction()` ekleyerek tarifeli havayolu tahmin etmek için `PredictionEngine` kullanın:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-232">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="b1bb3-233">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-233">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="b1bb3-234">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-234">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="b1bb3-235">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-235">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="b1bb3-236">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-236">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="b1bb3-237">[ASP.NET Core Web API 'sindeki `PredictionEnginePool` kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-237">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="b1bb3-238">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-238">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="b1bb3-239">Bu öğretici, bu sınıf içinde bir test yolculuğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-239">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="b1bb3-240">Daha sonra, modelle denemeler yapmak için başka senaryolar da ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-240">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="b1bb3-241">Bir `TaxiTrip` örneği oluşturarak eğitilen modelin Maliyet tahminini `TestSinglePrediction()` yönteminde test etmek için bir seyahat ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-241">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="b1bb3-242">Ardından, tarifeli havayolu yöntemine bir sonraki `TestSinglePrediction()` kod satırı olarak ekleyerek, bir TAXI seyahat verisinin tek bir örneğine göre ' yi tahmin edin ve `PredictionEngine` geçirin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-242">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="b1bb3-243">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, verilerin tek bir örneğini tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-243">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="b1bb3-244">Belirtilen yolculuğa ait tahmini tarifeli havayolu göstermek için `TestSinglePrediction` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-244">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="b1bb3-245">Test çalışmanıza yönelik tahmini TAXI tarifeli havayolu görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-245">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="b1bb3-246">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="b1bb3-246">Congratulations!</span></span> <span data-ttu-id="b1bb3-247">Artık TAXI seyahat Fares 'yi tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz, doğruluğu değerlendirildi ve tahmine dayalı hale getirmek için kullandınız.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-247">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="b1bb3-248">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-248">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b1bb3-249">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="b1bb3-249">Next steps</span></span>

<span data-ttu-id="b1bb3-250">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="b1bb3-250">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="b1bb3-251">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="b1bb3-251">Prepare and understand the data</span></span>
> * <span data-ttu-id="b1bb3-252">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1bb3-252">Create a learning pipeline</span></span>
> * <span data-ttu-id="b1bb3-253">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-253">Load and transform the data</span></span>
> * <span data-ttu-id="b1bb3-254">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="b1bb3-254">Choose a learning algorithm</span></span>
> * <span data-ttu-id="b1bb3-255">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-255">Train the model</span></span>
> * <span data-ttu-id="b1bb3-256">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="b1bb3-256">Evaluate the model</span></span>
> * <span data-ttu-id="b1bb3-257">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="b1bb3-257">Use the model for predictions</span></span>

<span data-ttu-id="b1bb3-258">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="b1bb3-258">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b1bb3-259">Iris kümelemesi</span><span class="sxs-lookup"><span data-stu-id="b1bb3-259">Iris clustering</span></span>](iris-clustering.md)
