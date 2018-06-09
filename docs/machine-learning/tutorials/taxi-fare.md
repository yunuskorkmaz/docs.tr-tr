---
title: New York ücreti fares (regresyon) tahmin etmek için ML.NET kullanın
description: Regresyon senaryoda ML.NET kullanmayı öğrenin.
author: aditidugar
ms.author: johalex
ms.date: 06/05/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 048ed1d38408c1ba4901c554cae33d5552c9e303
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "35017308"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="1cae9-103">Öğretici: Kullanım ML.NET New York ücreti fares (regresyon) tahmin etmek için</span><span class="sxs-lookup"><span data-stu-id="1cae9-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="1cae9-104">Bu konuda şu anda önizlemede değil, ML.NET başvuruyor ve malzeme değiştirilebilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="1cae9-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="1cae9-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="1cae9-106">Bu öğretici ML.NET oluşturmak için nasıl kullanılacağı gösterilmektedir bir [regresyon modeli](../resources/glossary.md#regression) New York şehrinde ücreti fares tahmin etmeye yönelik.</span><span class="sxs-lookup"><span data-stu-id="1cae9-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="1cae9-107">Bu öğreticide, bilgi nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="1cae9-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="1cae9-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="1cae9-108">Understand the problem</span></span>
> * <span data-ttu-id="1cae9-109">Uygun makine öğrenme görevini seçin</span><span class="sxs-lookup"><span data-stu-id="1cae9-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="1cae9-110">Hazırlama ve verilerinizi anlama</span><span class="sxs-lookup"><span data-stu-id="1cae9-110">Prepare and understand your data</span></span>
> * <span data-ttu-id="1cae9-111">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1cae9-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="1cae9-112">Yük ve verilerinizi dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1cae9-112">Load and transform your data</span></span>
> * <span data-ttu-id="1cae9-113">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="1cae9-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="1cae9-114">Modeli eğitmek</span><span class="sxs-lookup"><span data-stu-id="1cae9-114">Train the model</span></span>
> * <span data-ttu-id="1cae9-115">Modeli değerlendirin</span><span class="sxs-lookup"><span data-stu-id="1cae9-115">Evaluate the model</span></span>
> * <span data-ttu-id="1cae9-116">Model için tahminde kullanın</span><span class="sxs-lookup"><span data-stu-id="1cae9-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1cae9-117">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1cae9-117">Prerequisites</span></span>

* <span data-ttu-id="1cae9-118">[Visual Studio 2017 15,6 veya üstü](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile.</span><span class="sxs-lookup"><span data-stu-id="1cae9-118">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="1cae9-119">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="1cae9-119">Understand the problem</span></span>

<span data-ttu-id="1cae9-120">Bu sorunu kalmaz **bir ücreti ücreti tahmin etmeye seyahat New York şehirde**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="1cae9-121">İlk bakışta, seyahat uzaklığı üzerinde yalnızca bağımlı görünebilir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="1cae9-122">Ancak, New York'taki ücreti satıcıları ek yolcu veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere değişen tutarlarının gider.</span><span class="sxs-lookup"><span data-stu-id="1cae9-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="1cae9-123">Uygun makine öğrenme görevini seçin</span><span class="sxs-lookup"><span data-stu-id="1cae9-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="1cae9-124">Ücreti ücreti tahmin etmek için önce uygun makine öğrenme görevi seçin.</span><span class="sxs-lookup"><span data-stu-id="1cae9-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="1cae9-125">Gerçek değer (Fiyat gösteren bir double) kümesindeki diğer faktörleri temel tahmin etmek için aramaktadır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="1cae9-126">Seçtiğiniz bir [ **regresyon** ](../resources/glossary.md#regression) görev.</span><span class="sxs-lookup"><span data-stu-id="1cae9-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

<span data-ttu-id="1cae9-127">Modeli eğitmek işleminin hangi kümesindeki son ücreti fiyatını tahmin etmeye durumlarda en etkili faktörlerdir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1cae9-127">The process of training the model identifies which factors in the dataset are most influential when predicting the final fare price.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="1cae9-128">Bir konsol uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="1cae9-128">Create a console application</span></span>

1. <span data-ttu-id="1cae9-129">Visual Studio 2017'ni açın.</span><span class="sxs-lookup"><span data-stu-id="1cae9-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="1cae9-130">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="1cae9-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="1cae9-131">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="1cae9-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="1cae9-132">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="1cae9-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="1cae9-133">İçinde **adı** metin kutusu, "TaxiFarePrediction" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="1cae9-134">Adlı bir dizin oluşturun *veri* projenize veri kümesi dosyalarınızı kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="1cae9-134">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="1cae9-135">İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-135">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="1cae9-136">"Data" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1cae9-136">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="1cae9-137">Yükleme **Microsoft.ML NuGet paketi**:</span><span class="sxs-lookup"><span data-stu-id="1cae9-137">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="1cae9-138">Çözüm Gezgini'nde projenizi ve select üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-138">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="1cae9-139">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-139">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="1cae9-140">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulünü** iletişim varsa, listelenen paketler için lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="1cae9-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-and-understand-your-data"></a><span data-ttu-id="1cae9-141">Hazırlama ve verilerinizi anlama</span><span class="sxs-lookup"><span data-stu-id="1cae9-141">Prepare and understand your data</span></span>

1. <span data-ttu-id="1cae9-142">Karşıdan [ücreti ücreti train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [ücreti ücreti test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="1cae9-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="1cae9-143">Ücreti seyahat veri kümesi makine öğrenimi modeline eğitir ve nasıl modelinizi doğrudur değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-143">The Taxi Trip data set trains the machine learning model and can be used to evaluate how accurate your model is.</span></span> <span data-ttu-id="1cae9-144">Bu veri kümeleri başlangıçta arasındadır [NYC TLC ücreti seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="1cae9-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="1cae9-145">Çözüm Gezgini'nde, her biri sağ \*.csv dosyaları ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="1cae9-146">Altında **Gelişmiş**, değerini değiştirme **çıktı dizinine Kopyala** için **her zaman**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="1cae9-147">Açık **ücreti ücreti train.csv** veri Kod düzenleyicisinde ayarlama ve sütun üst bilgileri ilk satırda bakın.</span><span class="sxs-lookup"><span data-stu-id="1cae9-147">Open the **taxi-fare-train.csv** data set in the code editor and look at column headers in the first row.</span></span> <span data-ttu-id="1cae9-148">Her sütun göz atın.</span><span class="sxs-lookup"><span data-stu-id="1cae9-148">Take a look at each of the columns.</span></span> <span data-ttu-id="1cae9-149">İçin verileri anlamak ve hangi sütunların olduğuna karar **özellikleri** ve olduğu **etiket**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-149">Understand the data and decide which columns are **features** and which is the **label**.</span></span>

<span data-ttu-id="1cae9-150">**Etiket** tahmin etmek için çalıştığınız sütun tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-150">The **label** is the identifier of the column you are trying to predict.</span></span> <span data-ttu-id="1cae9-151">Tanımlanan **özellikleri** etiketi tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-151">The identified **features** are used to predict the label.</span></span>

* <span data-ttu-id="1cae9-152">**vendor_id:** ücreti satıcı kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="1cae9-153">**rate_code:** ücreti seyahat hızı türünü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="1cae9-154">**passenger_count:** seyahat üzerinde yolcu sayısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="1cae9-155">**trip_time_in_secs:** süreyi seyahat sürdü.</span><span class="sxs-lookup"><span data-stu-id="1cae9-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="1cae9-156">Bu tamamlandıktan sonra seyahat kadar gereken süreyi bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cae9-156">You won't know how long the trip takes until after it is completed.</span></span> <span data-ttu-id="1cae9-157">Bu sütunu modelden hariç.</span><span class="sxs-lookup"><span data-stu-id="1cae9-157">You exclude this column from the model.</span></span>
* <span data-ttu-id="1cae9-158">**trip_distance:** seyahat mesafesini bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="1cae9-159">**payment_type:** ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="1cae9-160">**fare_amount:** Ücretli toplam ücreti ücreti etiketidir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="1cae9-161">Sınıflar oluşturma ve yolları tanımla</span><span class="sxs-lookup"><span data-stu-id="1cae9-161">Create classes and define paths</span></span>

<span data-ttu-id="1cae9-162">Aşağıdaki ek ekleyin `using` deyimleri üstüne *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="1cae9-162">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="1cae9-163">En son indirilen dosyaları yolları tutun ve model kaydetmek için üç genel değişkenler oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1cae9-163">You need to create three global variables to hold the paths to the recently downloaded files and to save the model:</span></span>

* <span data-ttu-id="1cae9-164">`_datapath` veri modeli eğitmek için kullanılan yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-164">`_datapath` has the path to the data set used to train the model.</span></span>
* <span data-ttu-id="1cae9-165">`_testdatapath` veri modeli değerlendirmek için kullanılan yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-165">`_testdatapath` has the path to the data set used to evaluate the model.</span></span>
* <span data-ttu-id="1cae9-166">`_modelpath` Eğitim modeli depolandığı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-166">`_modelpath` has the path where the trained model is stored.</span></span>

<span data-ttu-id="1cae9-167">Satırının sağındaki aşağıdaki kodu ekleyin `Main` en son indirilen dosyaları belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="1cae9-167">Add the following code to the line right above `Main` to specify the recently downloaded files:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="1cae9-168">Ardından, girdi verileri ve tahminleri için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1cae9-168">Next, create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="1cae9-169">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-169">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="1cae9-170">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="1cae9-170">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="1cae9-171">Ardından, seçin **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-171">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="1cae9-172">Aşağıdakileri ekleyin `using` deyimleri yeni dosya için:</span><span class="sxs-lookup"><span data-stu-id="1cae9-172">Add the following `using` statements to the new file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="1cae9-173">Varolan sınıf tanımına kaldırmak ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="1cae9-173">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="1cae9-174">`TaxiTrip` Giriş veri kümesi sınıfı olup veri kümesi sütunların her biri için tanımları içerir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-174">`TaxiTrip` is the input data set class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="1cae9-175">`TaxiTripFarePrediction` Model eğitilmiş sonra sınıfı tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-175">The `TaxiTripFarePrediction` class is used for prediction after the model has been trained.</span></span> <span data-ttu-id="1cae9-176">Tek bir kayan nokta vardır (`FareAmount`) ve bir `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) özniteliği uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-176">It has a single float (`FareAmount`) and a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span>

<span data-ttu-id="1cae9-177">Şimdi geri dönerek **Program.cs** dosya.</span><span class="sxs-lookup"><span data-stu-id="1cae9-177">Now go back to the **Program.cs** file.</span></span> <span data-ttu-id="1cae9-178">İçinde `Main`, yerine `Console.WriteLine("Hello World!")` aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="1cae9-178">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="1cae9-179">`Train` Yöntemi eğitir modelinizi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-179">The `Train` method trains your model.</span></span> <span data-ttu-id="1cae9-180">Bu işlev oluşturmak yalnızca aşağıda `Main`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="1cae9-180">Create that function just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="1cae9-181">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1cae9-181">Create a learning pipeline</span></span>

<span data-ttu-id="1cae9-182">Öğrenme ardışık düzen tüm veri ve algoritma modeli eğitmek için gerekli yükler.</span><span class="sxs-lookup"><span data-stu-id="1cae9-182">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="1cae9-183">Aşağıdaki kodu ekleyin `Train()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1cae9-183">Add the following code into the `Train()` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a><span data-ttu-id="1cae9-184">Yük ve verilerinizi dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1cae9-184">Load and transform your data</span></span>

<span data-ttu-id="1cae9-185">Ardından, verilerinizi ardışık düzenine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1cae9-185">Next, load your data into the pipeline.</span></span> <span data-ttu-id="1cae9-186">İşaret `_datapath` başlangıçta oluşturulması ve .csv dosyasını (,) sınırlayıcıyı belirtin.</span><span class="sxs-lookup"><span data-stu-id="1cae9-186">Point to the `_datapath` created initially and specify the delimiter of the .csv file (,).</span></span> <span data-ttu-id="1cae9-187">Aşağıdaki kodu ekleyin `Train()` son adımı yöntemini:</span><span class="sxs-lookup"><span data-stu-id="1cae9-187">Add the following code into the `Train()` method underneath the last step:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

<span data-ttu-id="1cae9-188">Alt çizgi, oluşturmakta olduğunuz kod olmadan sütunları başvuracağınız.</span><span class="sxs-lookup"><span data-stu-id="1cae9-188">You'll refer to the columns without the underscores in the code you're creating.</span></span> <span data-ttu-id="1cae9-189">Kopya `FareAmount` yeni bir sütun sütununa adında "kullanarak etiket" `ColumnCopier()` işlevi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-189">Copy the `FareAmount` column into a new column called "Label" using the `ColumnCopier()` function.</span></span> <span data-ttu-id="1cae9-190">Bu sütun **etiket**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-190">This column is the **Label**.</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="1cae9-191">Bazı gerçekleştir **özellik Mühendisliği** böylece machine learning için etkili bir şekilde kullanılabilir verileri dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="1cae9-191">Conduct some **feature engineering** to transform the data so that it can be used effectively for machine learning.</span></span> <span data-ttu-id="1cae9-192">Model eğitir algoritması **sayısal** özellikleri kategorik veri dönüştürme (`VendorId`, `RateCode`, ve `PaymentType`) numaraları içine.</span><span class="sxs-lookup"><span data-stu-id="1cae9-192">The algorithm that trains the model requires **numeric** features, you transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) into numbers.</span></span> <span data-ttu-id="1cae9-193">`CategoricalOneHotVectorizer()` İşlevi değerleri bu sütunların her biri için sayısal anahtar atar.</span><span class="sxs-lookup"><span data-stu-id="1cae9-193">The `CategoricalOneHotVectorizer()` function assigns a numeric key to the values in each of these columns.</span></span> <span data-ttu-id="1cae9-194">Bu kod ekleyerek, verilerinizi dönüştürmek:</span><span class="sxs-lookup"><span data-stu-id="1cae9-194">Transform your data by adding this code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="1cae9-195">Veri hazırlama son adımda tüm birleştirir, **özellikleri** bir vektör kullanarak `ColumnConcatenator()` işlevi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-195">The last step in data preparation combines all of your **features** into one vector using the `ColumnConcatenator()` function.</span></span> <span data-ttu-id="1cae9-196">Bu gerekli bir adım kolayca özelliklerinizi işlem algoritması yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1cae9-196">This necessary step helps the algorithm easily process your features.</span></span> <span data-ttu-id="1cae9-197">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1cae9-197">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="1cae9-198">Dikkat `trip_time_in_secs` sütun dahil değil.</span><span class="sxs-lookup"><span data-stu-id="1cae9-198">Notice that the `trip_time_in_secs` column isn't included.</span></span> <span data-ttu-id="1cae9-199">Zaten bir yararlı tahmin özelliği değil belirledi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-199">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="1cae9-200">Bu adımları başarılı yürütme için yukarıda belirtilen sırada ardışık düzene eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-200">These steps must be added to Pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="1cae9-201">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="1cae9-201">Choose a learning algorithm</span></span>

<span data-ttu-id="1cae9-202">Veri ardışık düzenine eklemek ve doğru giriş biçimine dönüştürme sonra bir öğrenme algoritması seçin (**öğrenen**).</span><span class="sxs-lookup"><span data-stu-id="1cae9-202">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="1cae9-203">Öğrenme algoritmasını model eğitir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-203">The learning algorithm trains the model.</span></span> <span data-ttu-id="1cae9-204">Seçtiğiniz bir **regresyon görev** Bu sorun için bu nedenle eklediğiniz adlı bir öğrenen `FastTreeRegressor()` yararlanan ardışık düzene **gradyan artırmanın**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-204">You chose a **regression task** for this problem, so you add a learner called `FastTreeRegressor()` to the pipeline that utilizes **gradient boosting**.</span></span>

<span data-ttu-id="1cae9-205">Gradyan artırmanın regresyon sorunları için tekniği öğrenme bir makinedir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-205">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="1cae9-206">Her regresyon ağaç step-wise bir şekilde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1cae9-206">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="1cae9-207">Her adım hata ölçmek ve sonraki düzeltmek için önceden tanımlanmış kaybı işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-207">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="1cae9-208">Gerçekte bir ensemble zayıf tahmin modellerin olduğu bir tahmin modeli sonucudur.</span><span class="sxs-lookup"><span data-stu-id="1cae9-208">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="1cae9-209">Gradyan artırma hakkında daha fazla bilgi için bkz: [Boosted karar ağacı regresyon](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="1cae9-209">For more information about gradient boosting, see [Boosted Decision Tree Regression](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="1cae9-210">Aşağıdaki kodu ekleyin `Train()` son adımda eklediğiniz veri işleme koddan yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1cae9-210">Add the following code into the `Train()` method following the data processing code added in the last step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="1cae9-211">Yukarıdaki adımların tümünü tek tek deyimleri ardışık düzenine eklenen ancak C# oluşturma ve ardışık düzeni başlatan basitleştiren bir kullanışlı koleksiyonu başlatma sözdizimine sahip.</span><span class="sxs-lookup"><span data-stu-id="1cae9-211">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="1cae9-212">Şimdiye kadar eklediğiniz kod değiştirin `Train()` aşağıdaki kod ile yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1cae9-212">Replace the code you added so far to the `Train()` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="1cae9-213">Modeli eğitmek</span><span class="sxs-lookup"><span data-stu-id="1cae9-213">Train the model</span></span>

<span data-ttu-id="1cae9-214">Modeli eğitmek için son adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="1cae9-214">The final step is to train the model.</span></span> <span data-ttu-id="1cae9-215">Bu noktaya kadar ardışık düzeninde bir şey çalıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="1cae9-215">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="1cae9-216">`pipeline.Train<T_Input, T_Output>()` İşlev alır önceden tanımlanmış `TaxiTrip` sınıf türü ve çıkış bir `TaxiTripFarePrediction` türü.</span><span class="sxs-lookup"><span data-stu-id="1cae9-216">The `pipeline.Train<T_Input, T_Output>()` function takes in the pre-defined `TaxiTrip` class type and outputs a `TaxiTripFarePrediction` type.</span></span> <span data-ttu-id="1cae9-217">Bu son parçası, koda ekleme `Train()` işlevi:</span><span class="sxs-lookup"><span data-stu-id="1cae9-217">Add this final piece of code into the `Train()` function:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="1cae9-218">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="1cae9-218">And that's it!</span></span> <span data-ttu-id="1cae9-219">Başarıyla bir makine ücreti fares NYC, tahmin modeli öğrenme eğitilmiş.</span><span class="sxs-lookup"><span data-stu-id="1cae9-219">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="1cae9-220">Şimdi ne kadar doğru modelinizi anlamak ve bunu kullanma konusunda bilgi almak için göz atın.</span><span class="sxs-lookup"><span data-stu-id="1cae9-220">Now take a look to understand how accurate your model is and learn how to consume it.</span></span>

## <a name="save-the-model"></a><span data-ttu-id="1cae9-221">Modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="1cae9-221">Save the model</span></span>

<span data-ttu-id="1cae9-222">Sonraki adıma geçmeden önce modelinizi bir .zip dosyasına sonuna aşağıdaki kodu ekleyerek kaydetmek, `Train()` işlevi:</span><span class="sxs-lookup"><span data-stu-id="1cae9-222">Before you go onto the next step, save your model to a .zip file by adding the following code at the end of your `Train()` function:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="1cae9-223">Ekleme `await` ifadesine `model.WriteAsync()` çağrı anlamına `Train()` döndüren bir zaman uyumsuz yöntem yöntemi değiştirilmiş bir `Task`.</span><span class="sxs-lookup"><span data-stu-id="1cae9-223">Adding the `await` statement to the `model.WriteAsync()` call means that the `Train()` method must be changed to an async method that returns a `Task`.</span></span> <span data-ttu-id="1cae9-224">İmzasını değiştirmek `Train` aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="1cae9-224">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="1cae9-225">Dönüş türünü değiştirme `Train` yöntemi anlamına gelir eklemek zorunda bir `await` çağıran kodu için `Train` içinde `Main` yöntemini aşağıdaki kodda gösterildiği gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1cae9-225">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="1cae9-226">Ekleme bir `await` içinde `Main` yöntemi anlamına gelir `Main` yöntemi olmalıdır `async` değiştiricisini ve return bir `Task`:</span><span class="sxs-lookup"><span data-stu-id="1cae9-226">Adding an `await` in your `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="1cae9-227">Ayrıca aşağıdaki eklemeniz gerekir deyimini dosyanın üst kısmında kullanarak:</span><span class="sxs-lookup"><span data-stu-id="1cae9-227">You also need to add the following using statement at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="1cae9-228">Çünkü `async Main` yöntemdir C# 7.1 yeni bir özelliktir ve C# 7.0 projesinin varsayılan dil sürümünü ise, C# 7.1 veya üzeri dil sürümü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-228">Because the `async Main` method is a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="1cae9-229">Bunu yapmak için proje düğümüne sağ tıklayın **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-229">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="1cae9-230">Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-230">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="1cae9-231">Açılır listede seçin **C# 7.1** (veya daha yüksek bir sürüm).</span><span class="sxs-lookup"><span data-stu-id="1cae9-231">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="1cae9-232">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-232">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="1cae9-233">Modeli değerlendirin</span><span class="sxs-lookup"><span data-stu-id="1cae9-233">Evaluate the model</span></span>

<span data-ttu-id="1cae9-234">Değerlendirme modeli ne kadar iyi çalıştığı denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-234">Evaluation is the process of checking how well the model works.</span></span> <span data-ttu-id="1cae9-235">Modelinizi eğitilmiş zaman, onu kullanmadı veriler üzerinde iyi tahminleri yapar önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-235">It's important that your model makes good predictions on data that it didn't use when it was trained.</span></span> <span data-ttu-id="1cae9-236">Yapmanın bir yolu tren veri bölerek budur ve Bu öğreticide yaptığınız gibi veri kümeleri, test.</span><span class="sxs-lookup"><span data-stu-id="1cae9-236">One way to do this is by splitting the data into train and test datasets, as you did in this tutorial.</span></span> <span data-ttu-id="1cae9-237">Tren veri modeli eğittiğimize göre ne kadar iyi test verileri üzerindeki işlevini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cae9-237">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="1cae9-238">Geri dönerek, `Main` işlev ve çağrının altına aşağıdaki kodu ekleyin `Train()`yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1cae9-238">Go back to your `Main` function and add the following code beneath the call to the `Train()`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="1cae9-239">`Evaluate()` İşlevi modelinizi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="1cae9-239">The `Evaluate()` function evaluates your model.</span></span> <span data-ttu-id="1cae9-240">Bu işlev oluşturma `Train()`.</span><span class="sxs-lookup"><span data-stu-id="1cae9-240">Create that function below `Train()`.</span></span> <span data-ttu-id="1cae9-241">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1cae9-241">Add the following code:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="1cae9-242">Test verileri kullanarak yük `TextLoader()` işlevi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-242">Load the test data using the `TextLoader()` function.</span></span> <span data-ttu-id="1cae9-243">Aşağıdaki kodu ekleyin `Evaluate()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1cae9-243">Add the following code into the `Evaluate()` method:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="1cae9-244">Modeli değerlendirin ve ölçümler için üretmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1cae9-244">Add the following code to evaluate the model and produce the metrics for it:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="1cae9-245">RMS regresyon sorunları değerlendirmek için bir ölçümüdür.</span><span class="sxs-lookup"><span data-stu-id="1cae9-245">RMS is one metric for evaluating regression problems.</span></span> <span data-ttu-id="1cae9-246">Bu daha düşükse, daha iyi modelinizi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-246">The lower it is, the better your model.</span></span> <span data-ttu-id="1cae9-247">Aşağıdaki kodu ekleyin `Evaluate()` modeliniz için RMS yazdırmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-247">Add the following code into the `Evaluate()` function to print the RMS for your model.</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="1cae9-248">RSquared regresyon sorunları değerlendirmek için başka bir ölçümüdür.</span><span class="sxs-lookup"><span data-stu-id="1cae9-248">RSquared is another metric for evaluating regression problems.</span></span> <span data-ttu-id="1cae9-249">RSquared 0 ile 1 arasında bir değer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-249">RSquared will be a value between 0 and 1.</span></span> <span data-ttu-id="1cae9-250">1, daha iyi olduğunuz yakınsa modelinizi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-250">The closer you are to 1, the better your model.</span></span> <span data-ttu-id="1cae9-251">Aşağıdaki kodu ekleyin `Evaluate()` modeliniz için RSquared değeri yazdırmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-251">Add the following code into the `Evaluate()` function to print the RSquared value for your model.</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="1cae9-252">Model için tahminde kullanın</span><span class="sxs-lookup"><span data-stu-id="1cae9-252">Use the model for predictions</span></span>

<span data-ttu-id="1cae9-253">Ardından, modelinizin doğru şekilde çalıştığından emin olmak için kullanabileceğiniz merkezi test senaryoları için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1cae9-253">Next, create a class to house test scenarios that you can use to make sure your model is working correctly:</span></span>

1. <span data-ttu-id="1cae9-254">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="1cae9-254">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="1cae9-255">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="1cae9-255">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="1cae9-256">Ardından, seçin **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-256">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="1cae9-257">Sınıfı aşağıdaki örnekte gibi statik olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1cae9-257">Modify the class to be static like in the following example:</span></span>

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="1cae9-258">Bu öğretici, bu sınıf içinde bir test seyahat kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cae9-258">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="1cae9-259">Daha sonra bu örnekle denemek için diğer senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cae9-259">Later you can add other scenarios to experiment with this sample.</span></span> <span data-ttu-id="1cae9-260">Aşağıdaki kodu ekleyin `TestTrips` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="1cae9-260">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="1cae9-261">Bu seyahat 's gerçek ücreti, 29.5 olmakla birlikte bir yer tutucu olarak 0'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="1cae9-261">This trip's actual fare is 29.5, but use 0 as a placeholder.</span></span> <span data-ttu-id="1cae9-262">Makine öğrenme algoritmasını ücreti tahmin.</span><span class="sxs-lookup"><span data-stu-id="1cae9-262">The machine learning algorithm will predict the fare.</span></span>

<span data-ttu-id="1cae9-263">Aşağıdaki kodu ekleyin, `Main` işlevi.</span><span class="sxs-lookup"><span data-stu-id="1cae9-263">Add the following code in your `Main` function.</span></span> <span data-ttu-id="1cae9-264">Modeli kullanarak test `TestTrip` verileri:</span><span class="sxs-lookup"><span data-stu-id="1cae9-264">It tests out your model using the `TestTrip` data:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="1cae9-265">Test çalışması için tahmin edilen ücreti ücreti görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1cae9-265">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="1cae9-266">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="1cae9-266">Congratulations!</span></span> <span data-ttu-id="1cae9-267">Şimdi başarıyla ücreti fares tahmin etmeye yönelik bir machine learning modelini yerleşik, doğruluğunu değerlendirilir ve test.</span><span class="sxs-lookup"><span data-stu-id="1cae9-267">You've now successfully built a machine learning model for predicting taxi fares, evaluated its accuracy, and tested it.</span></span> <span data-ttu-id="1cae9-268">Bu öğreticinin için kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) deposu.</span><span class="sxs-lookup"><span data-stu-id="1cae9-268">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1cae9-269">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1cae9-269">Next steps</span></span>

<span data-ttu-id="1cae9-270">Bu öğreticide, öğrenilen nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="1cae9-270">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="1cae9-271">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="1cae9-271">Understand the problem</span></span>
> * <span data-ttu-id="1cae9-272">Uygun makine öğrenme görevini seçin</span><span class="sxs-lookup"><span data-stu-id="1cae9-272">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="1cae9-273">Hazırlama ve verilerinizi anlama</span><span class="sxs-lookup"><span data-stu-id="1cae9-273">Prepare and understand your data</span></span>
> * <span data-ttu-id="1cae9-274">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1cae9-274">Create a learning pipeline</span></span>
> * <span data-ttu-id="1cae9-275">Yük ve verilerinizi dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1cae9-275">Load and transform your data</span></span>
> * <span data-ttu-id="1cae9-276">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="1cae9-276">Choose a learning algorithm</span></span>
> * <span data-ttu-id="1cae9-277">Modeli eğitmek</span><span class="sxs-lookup"><span data-stu-id="1cae9-277">Train the model</span></span>
> * <span data-ttu-id="1cae9-278">Modeli değerlendirin</span><span class="sxs-lookup"><span data-stu-id="1cae9-278">Evaluate the model</span></span>
> * <span data-ttu-id="1cae9-279">Model için tahminde kullanın</span><span class="sxs-lookup"><span data-stu-id="1cae9-279">Use the model for predictions</span></span>

<span data-ttu-id="1cae9-280">Bilgi almaya devam etmek ve daha fazla örneklerini bulmak için GitHub depomuzda denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1cae9-280">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="1cae9-281">DotNet/machinelearning GitHub deposunu</span><span class="sxs-lookup"><span data-stu-id="1cae9-281">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
