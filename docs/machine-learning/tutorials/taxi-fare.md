---
title: New York ücreti fares (regresyon) tahmin etmek için ML.NET kullanın
description: Regresyon senaryoda ML.NET kullanmayı öğrenin.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 690e39dcbd02d81b8d4afe918a74795aa02f7fc6
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314971"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="e58fb-103">Öğretici: Kullanım ML.NET New York ücreti fares (regresyon) tahmin etmek için</span><span class="sxs-lookup"><span data-stu-id="e58fb-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="e58fb-104">Bu konuda şu anda önizlemede değil, ML.NET başvuruyor ve malzeme değiştirilebilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="e58fb-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e58fb-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="e58fb-106">Bu öğretici ML.NET oluşturmak için nasıl kullanılacağı gösterilmektedir bir [regresyon modeli](../resources/glossary.md#regression) New York şehrinde ücreti fares tahmin etmeye yönelik.</span><span class="sxs-lookup"><span data-stu-id="e58fb-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="e58fb-107">Bu öğreticide, bilgi nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="e58fb-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="e58fb-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="e58fb-108">Understand the problem</span></span>
> * <span data-ttu-id="e58fb-109">Uygun makine öğrenme görevini seçin</span><span class="sxs-lookup"><span data-stu-id="e58fb-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="e58fb-110">Hazırlama ve verileri anlamak</span><span class="sxs-lookup"><span data-stu-id="e58fb-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="e58fb-111">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="e58fb-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="e58fb-112">Yük ve veri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e58fb-112">Load and transform the data</span></span>
> * <span data-ttu-id="e58fb-113">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="e58fb-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="e58fb-114">Modeli eğitmek</span><span class="sxs-lookup"><span data-stu-id="e58fb-114">Train the model</span></span>
> * <span data-ttu-id="e58fb-115">Modeli değerlendirin</span><span class="sxs-lookup"><span data-stu-id="e58fb-115">Evaluate the model</span></span>
> * <span data-ttu-id="e58fb-116">Model için tahminde kullanın</span><span class="sxs-lookup"><span data-stu-id="e58fb-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e58fb-117">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e58fb-117">Prerequisites</span></span>

* <span data-ttu-id="e58fb-118">[Visual Studio 2017 15,6 veya üstü](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile.</span><span class="sxs-lookup"><span data-stu-id="e58fb-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="e58fb-119">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="e58fb-119">Understand the problem</span></span>

<span data-ttu-id="e58fb-120">Bu sorunu kalmaz **bir ücreti ücreti tahmin etmeye seyahat New York şehirde**.</span><span class="sxs-lookup"><span data-stu-id="e58fb-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="e58fb-121">İlk bakışta, seyahat uzaklığı üzerinde yalnızca bağımlı görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="e58fb-122">Ancak, New York'taki ücreti satıcıları ek yolcu veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere değişen tutarlarının gider.</span><span class="sxs-lookup"><span data-stu-id="e58fb-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="e58fb-123">Uygun makine öğrenme görevini seçin</span><span class="sxs-lookup"><span data-stu-id="e58fb-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="e58fb-124">Ücreti ücreti tahmin etmek için önce uygun makine öğrenme görevi seçin.</span><span class="sxs-lookup"><span data-stu-id="e58fb-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="e58fb-125">Gerçek değer (Fiyat gösteren bir double) kümesindeki diğer faktörleri temel tahmin etmek için aramaktadır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="e58fb-126">Seçtiğiniz bir [ **regresyon** ](../resources/glossary.md#regression) görev.</span><span class="sxs-lookup"><span data-stu-id="e58fb-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e58fb-127">Bir konsol uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="e58fb-127">Create a console application</span></span>

1. <span data-ttu-id="e58fb-128">Visual Studio 2017'ni açın.</span><span class="sxs-lookup"><span data-stu-id="e58fb-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="e58fb-129">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="e58fb-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="e58fb-130">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="e58fb-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="e58fb-131">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="e58fb-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="e58fb-132">İçinde **adı** metin kutusu, "TaxiFarePrediction" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e58fb-132">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="e58fb-133">Adlı bir dizin oluşturun *veri* projenize veri kümesi dosyaları kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="e58fb-133">Create a directory named *Data* in your project to save the data set files:</span></span>

    <span data-ttu-id="e58fb-134">İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="e58fb-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="e58fb-135">"Data" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e58fb-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="e58fb-136">Yükleme **Microsoft.ML NuGet paketi**:</span><span class="sxs-lookup"><span data-stu-id="e58fb-136">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="e58fb-137">İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="e58fb-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="e58fb-138">Paket, kaynak olarak seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e58fb-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="e58fb-139">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulünü** iletişim varsa, listelenen paketler için lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e58fb-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="e58fb-140">Hazırlama ve verileri anlamak</span><span class="sxs-lookup"><span data-stu-id="e58fb-140">Prepare and understand the data</span></span>

1. <span data-ttu-id="e58fb-141">Karşıdan [ücreti ücreti train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [ücreti ücreti test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="e58fb-141">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="e58fb-142">Machine learning modelini eğitmek ve ne kadar doğru modeldir değerlendirmek için bu veri kümeleri kullanırız.</span><span class="sxs-lookup"><span data-stu-id="e58fb-142">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="e58fb-143">Bu veri kümeleri başlangıçta arasındadır [NYC TLC ücreti seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="e58fb-143">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="e58fb-144">İçinde **Çözüm Gezgini**, her biri sağ \*.csv dosyaları ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e58fb-144">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="e58fb-145">Altında **Gelişmiş**, değerini değiştirme **çıktı dizinine Kopyala** için **her zaman**.</span><span class="sxs-lookup"><span data-stu-id="e58fb-145">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="e58fb-146">Açık **ücreti ücreti train.csv** veri kümesi ve sütun üst bilgileri ilk satırda bakın.</span><span class="sxs-lookup"><span data-stu-id="e58fb-146">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="e58fb-147">Her sütun göz atın.</span><span class="sxs-lookup"><span data-stu-id="e58fb-147">Take a look at each of the columns.</span></span> <span data-ttu-id="e58fb-148">İçin verileri anlamak ve hangi sütunların olduğuna karar **özellikleri** ve hangisinin **etiket**.</span><span class="sxs-lookup"><span data-stu-id="e58fb-148">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="e58fb-149">**Etiket** tahmin etmek istediğiniz sütun tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-149">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="e58fb-150">Tanımlanan **özellikleri** etiketi tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-150">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="e58fb-151">Sağlanan veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="e58fb-151">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="e58fb-152">**vendor_id:** ücreti satıcı kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="e58fb-153">**rate_code:** ücreti seyahat hızı türünü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="e58fb-154">**passenger_count:** seyahat üzerinde yolcu sayısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="e58fb-155">**trip_time_in_secs:** süreyi seyahat sürdü.</span><span class="sxs-lookup"><span data-stu-id="e58fb-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="e58fb-156">Seyahat tamamlanmadan önce Seyahat Ücreti tahmin etmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="e58fb-156">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="e58fb-157">Bu ne kadar süreyle seyahat tanımadığınız dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="e58fb-157">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="e58fb-158">Bu nedenle, dönüş süresi bir özellik değildir ve bu sütunu modelden hariç.</span><span class="sxs-lookup"><span data-stu-id="e58fb-158">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="e58fb-159">**trip_distance:** seyahat mesafesini bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-159">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="e58fb-160">**payment_type:** ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-160">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="e58fb-161">**fare_amount:** Ücretli toplam ücreti ücreti etiketidir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-161">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="e58fb-162">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="e58fb-162">Create data classes</span></span>

<span data-ttu-id="e58fb-163">Giriş verilerini ve tahminleri için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e58fb-163">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="e58fb-164">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="e58fb-164">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="e58fb-165">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="e58fb-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="e58fb-166">Ardından, seçin **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e58fb-166">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="e58fb-167">Aşağıdakileri ekleyin `using` deyimleri yeni dosya için:</span><span class="sxs-lookup"><span data-stu-id="e58fb-167">Add the following `using` statements to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="e58fb-168">Varolan sınıf tanımına kaldırmak ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="e58fb-168">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="e58fb-169">`TaxiTrip` giriş verisi sınıfı olup veri kümesi sütunların her biri için tanımları içerir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-169">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="e58fb-170">Kullanım [sütun](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) veri kümesinde kaynak sütunların dizinlerini belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e58fb-170">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="e58fb-171">`TaxiTripFarePrediction` Sınıfı, tahmin edilen sonuçları göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-171">The `TaxiTripFarePrediction` class is used to represent predicted results.</span></span> <span data-ttu-id="e58fb-172">Tek bir kayan nokta vardır (`FareAmount`) ile alan bir `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) özniteliği uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-172">It has a single float (`FareAmount`) field with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="e58fb-173">**Puan** ML.NET özel sütununda bir sütundur.</span><span class="sxs-lookup"><span data-stu-id="e58fb-173">The **Score** column is the special column in ML.NET.</span></span> <span data-ttu-id="e58fb-174">Model tahmin edilen değerler bu sütuna çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-174">The model outputs predicted values into that column.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="e58fb-175">Veriler ve model yolları tanımla</span><span class="sxs-lookup"><span data-stu-id="e58fb-175">Define data and model paths</span></span>

<span data-ttu-id="e58fb-176">Geri dönerek *Program.cs* dosya ve veri kümeleri ile dosyalara yolları tutun ve model kaydetmek için üç genel sabitler oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e58fb-176">Go back to the *Program.cs* file and create three global constants to hold the paths to the files with data sets and to save the model:</span></span>

* <span data-ttu-id="e58fb-177">`_datapath` veri modeli eğitmek için kullanılan yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-177">`_datapath` has the path to the data set used to train the model.</span></span>
* <span data-ttu-id="e58fb-178">`_testdatapath` veri modeli değerlendirmek için kullanılan yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-178">`_testdatapath` has the path to the data set used to evaluate the model.</span></span>
* <span data-ttu-id="e58fb-179">`_modelpath` Eğitim modeli depolandığı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-179">`_modelpath` has the path where the trained model is stored.</span></span>

<span data-ttu-id="e58fb-180">Satırının sağındaki aşağıdaki kodu ekleyin `Main` yöntemi bu yollarını belirtin:</span><span class="sxs-lookup"><span data-stu-id="e58fb-180">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="e58fb-181">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="e58fb-181">Create a learning pipeline</span></span>

<span data-ttu-id="e58fb-182">Aşağıdaki ek ekleyin `using` deyimleri üstüne *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="e58fb-182">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="e58fb-183">İçinde `Main`, yerine `Console.WriteLine("Hello World!")` aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="e58fb-183">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="e58fb-184">`Train` Yöntemi eğitir modeli.</span><span class="sxs-lookup"><span data-stu-id="e58fb-184">The `Train` method trains the model.</span></span> <span data-ttu-id="e58fb-185">Bu yöntem oluşturma yalnızca aşağıda `Main`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="e58fb-185">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="e58fb-186">Öğrenme ardışık düzen tüm veri ve algoritma modeli eğitmek için gerekli yükler.</span><span class="sxs-lookup"><span data-stu-id="e58fb-186">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="e58fb-187">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-187">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="e58fb-188">Yükleme ve dönüştürme verileri</span><span class="sxs-lookup"><span data-stu-id="e58fb-188">Load and transform data</span></span>

<span data-ttu-id="e58fb-189">Öğrenme ardışık düzen gerçekleştirir ilk adımı verileri eğitim veri kümesinden yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="e58fb-189">The first step that the learning pipeline performs is loading data from the training data set.</span></span> <span data-ttu-id="e58fb-190">Örneğimizde, eğitim veri kümesi metin dosyasında tarafından tanımlanan bir yol ile depolanan `_datapath` sabit.</span><span class="sxs-lookup"><span data-stu-id="e58fb-190">In our case, training data set is stored in the text file with a path defined by the `_datapath` constant.</span></span> <span data-ttu-id="e58fb-191">Bu dosyayı sütun adları üstbilgiyle içerdiğinden, verileri yüklenirken ilk satırın yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="e58fb-191">That file contains the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="e58fb-192">Dosyadaki sütunları virgülle ayrılmış (",").</span><span class="sxs-lookup"><span data-stu-id="e58fb-192">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="e58fb-193">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-193">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="e58fb-194">Sonraki adımlarda size sütunlara tanımlanan adlarıyla başvurmak `TaxiTrip` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e58fb-194">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="e58fb-195">Ne zaman model eğitilmiş ve hesaplanan değerler **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-195">When the model is trained and evaluated, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="e58fb-196">Ücreti Seyahat Ücreti tahmin etmek istiyoruz gibi kopyalamak `FareAmount` sütununa **etiket** sütun.</span><span class="sxs-lookup"><span data-stu-id="e58fb-196">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="e58fb-197">Bunu yapmak için kullanmak <xref:Microsoft.ML.Transforms.ColumnCopier> ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e58fb-197">To do that, use <xref:Microsoft.ML.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="e58fb-198">Model eğitir algoritması **sayısal** kategorik veri dönüştürme böylece özellikleri (`VendorId`, `RateCode`, ve `PaymentType`) numaraları değerlere.</span><span class="sxs-lookup"><span data-stu-id="e58fb-198">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="e58fb-199">Bunu yapmak için kullanmak <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, hangi farklı sayısal atar anahtar sütunların her biri farklı değerler değerlerini ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e58fb-199">To do that, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="e58fb-200">Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak <xref:Microsoft.ML.Transforms.ColumnConcatenator> dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e58fb-200">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="e58fb-201">Bu adım bir öğrenen yalnızca özelliklerinden işlerken gereklidir **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="e58fb-201">This step is necessary as a learner processes only features from the **Features** column.</span></span> <span data-ttu-id="e58fb-202">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e58fb-202">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="e58fb-203">Dikkat `TripTime` karşılık gelen sütun `trip_time_in_secs` veri kümesi dosyasındaki sütun dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-203">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="e58fb-204">Zaten bir yararlı tahmin özelliği değil belirledi.</span><span class="sxs-lookup"><span data-stu-id="e58fb-204">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="e58fb-205">Bu adımları başarılı yürütme için yukarıda belirtilen sırada ardışık düzene eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-205">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="e58fb-206">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="e58fb-206">Choose a learning algorithm</span></span>

<span data-ttu-id="e58fb-207">Veri ardışık düzenine eklemek ve doğru giriş biçimine dönüştürme sonra bir öğrenme algoritması seçin (**öğrenen**).</span><span class="sxs-lookup"><span data-stu-id="e58fb-207">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="e58fb-208">Öğrenen model eğitir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-208">The learner trains the model.</span></span> <span data-ttu-id="e58fb-209">Seçtiğiniz bir **regresyon görev** Bu sorun için bu nedenle eklediğiniz bir <xref:Microsoft.ML.Trainers.FastTreeRegressor> ML.NET tarafından sağlanan regresyon öğrencileriyle biri öğrenen.</span><span class="sxs-lookup"><span data-stu-id="e58fb-209">You chose a **regression task** for this problem, so you add a <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="e58fb-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> Gradyan artırmanın öğrenen kullanır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="e58fb-211">Gradyan artırmanın regresyon sorunları için tekniği öğrenme bir makinedir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-211">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="e58fb-212">Her regresyon ağaç step-wise bir şekilde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e58fb-212">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="e58fb-213">Her adım hata ölçmek ve sonraki düzeltmek için önceden tanımlanmış kaybı işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-213">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="e58fb-214">Gerçekte bir ensemble zayıf tahmin modellerin olduğu bir tahmin modeli sonucudur.</span><span class="sxs-lookup"><span data-stu-id="e58fb-214">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="e58fb-215">Gradyan artırma hakkında daha fazla bilgi için bkz: [Boosted karar ağacı regresyon](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="e58fb-215">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="e58fb-216">Aşağıdaki kodu ekleyin `Train` önceki adımda eklenen veri işleme koddan yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-216">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="e58fb-217">Yukarıdaki adımların tümünü tek tek deyimleri ardışık düzenine eklenen ancak C# oluşturma ve ardışık düzeni başlatan basitleştiren bir kullanışlı koleksiyonu başlatma sözdizimine sahip.</span><span class="sxs-lookup"><span data-stu-id="e58fb-217">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="e58fb-218">Şimdiye kadar eklediğiniz kod değiştirin `Train` aşağıdaki kod ile yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-218">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="e58fb-219">Modeli eğitmek</span><span class="sxs-lookup"><span data-stu-id="e58fb-219">Train the model</span></span>

<span data-ttu-id="e58fb-220">Modeli eğitmek için son adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="e58fb-220">The final step is to train the model.</span></span> <span data-ttu-id="e58fb-221">Bu noktaya kadar ardışık düzeninde bir şey çalıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="e58fb-221">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="e58fb-222">`pipeline.Train<TInput, TOutput>` Yöntemi üreten bir örnekte geçen modeli `TInput` yazın ve bir örneğini çıkaran `TOutput` türü.</span><span class="sxs-lookup"><span data-stu-id="e58fb-222">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="e58fb-223">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-223">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="e58fb-224">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="e58fb-224">And that's it!</span></span> <span data-ttu-id="e58fb-225">Başarıyla bir makine ücreti fares NYC, tahmin modeli öğrenme eğitilmiş.</span><span class="sxs-lookup"><span data-stu-id="e58fb-225">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="e58fb-226">Şimdi şimdi ne kadar doğru modeli olduğunu anlamak için göz atın ve ücreti ücreti değerleri tahmin etmek için kullanmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e58fb-226">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="e58fb-227">Modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="e58fb-227">Save the model</span></span>

<span data-ttu-id="e58fb-228">Sonraki adıma geçmeden önce modeli bir .zip dosyasına aşağıdaki kodu sonunda ekleyerek kaydedin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-228">Before you go onto the next step, save the model to a .zip file by adding the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="e58fb-229">Ekleme `await` ifadesine `model.WriteAsync` çağrı anlamına `Train` yöntemi bir görev döndüren bir zaman uyumsuz yöntem değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-229">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="e58fb-230">İmzasını değiştirmek `Train` aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-230">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="e58fb-231">Dönüş türünü değiştirme `Train` yöntemi anlamına gelir eklemek zorunda bir `await` çağıran kodu için `Train` içinde `Main` yöntemini aşağıdaki kodda gösterildiği gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e58fb-231">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="e58fb-232">Kullanarak `await` içinde `Main` yöntemi anlamına gelir `Main` yöntemi olmalıdır `async` değiştiricisini ve return bir `Task`:</span><span class="sxs-lookup"><span data-stu-id="e58fb-232">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="e58fb-233">Ayrıca aşağıdaki eklemeniz gerekir `using` deyimini dosyanın üst:</span><span class="sxs-lookup"><span data-stu-id="e58fb-233">You also need to add the following `using` statement at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="e58fb-234">Çünkü `async Main` yöntemi, C# 7.1 eklenen özelliğidir ve C# 7.0 projesinin varsayılan dil sürümünü ise, C# 7.1 veya üzeri dil sürümü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-234">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="e58fb-235">Bunu yapmak için proje düğümüne sağ tıklayın **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e58fb-235">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="e58fb-236">Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e58fb-236">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="e58fb-237">Açılır listede seçin **C# 7.1** (veya daha yüksek bir sürüm).</span><span class="sxs-lookup"><span data-stu-id="e58fb-237">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="e58fb-238">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e58fb-238">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="e58fb-239">Modeli değerlendirin</span><span class="sxs-lookup"><span data-stu-id="e58fb-239">Evaluate the model</span></span>

<span data-ttu-id="e58fb-240">Değerlendirme ne kadar iyi etiket değerlerini modeli tahmin denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-240">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="e58fb-241">Model, modeli eğitmek için kullanılmamış veriler üzerinde iyi tahminleri yapar önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-241">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="e58fb-242">Bu öğreticide yapılır bunu yapmanın bir yolu tren verileri bölün ve veri kümelerini, test için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-242">One way to do this is to split the data into train and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="e58fb-243">Tren veri modeli eğittiğimize göre ne kadar iyi test verileri üzerindeki işlevini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e58fb-243">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="e58fb-244">Geri dönerek `Main` yöntemi çağrısı altına aşağıdaki kodu ekleyin `Train`yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-244">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="e58fb-245">`Evaluate` Yöntemi modeli değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-245">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="e58fb-246">Bu yöntem oluşturmak için aşağıdaki aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-246">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="e58fb-247">Aşağıdaki kodu ekleyin `Evaluate` test verilerinin Kurulum yükleme yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-247">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="e58fb-248">Modeli değerlendirin ve değerlendirme ölçümleri üretmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e58fb-248">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="e58fb-249">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) regresyon modeli değerlendirme ölçümlerini biridir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-249">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="e58fb-250">Daha az olduğundan, daha iyi modelidir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-250">The lower it is, the better the model is.</span></span> <span data-ttu-id="e58fb-251">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RMS değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="e58fb-251">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="e58fb-252">[RSquared](../resources/glossary.md#coefficient-of-determination) bir regresyon modelini başka bir değerlendirme ölçümüdür.</span><span class="sxs-lookup"><span data-stu-id="e58fb-252">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="e58fb-253">RSquared değer 0 ile 1 arasında bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-253">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="e58fb-254">Yakınsa değeri 1'e daha iyi modeldir olduğu.</span><span class="sxs-lookup"><span data-stu-id="e58fb-254">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="e58fb-255">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RSquared değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="e58fb-255">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="e58fb-256">Model için tahminde kullanın</span><span class="sxs-lookup"><span data-stu-id="e58fb-256">Use the model for predictions</span></span>

<span data-ttu-id="e58fb-257">Ardından, model düzgün çalıştığından emin olmak için kullanabileceğiniz merkezi test senaryoları için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e58fb-257">Next, create a class to house test scenarios that you can use to make sure the model is working correctly:</span></span>

1. <span data-ttu-id="e58fb-258">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="e58fb-258">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="e58fb-259">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="e58fb-259">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="e58fb-260">Ardından, seçin **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e58fb-260">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="e58fb-261">Sınıfı aşağıdaki örnekte gibi statik olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e58fb-261">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="e58fb-262">Bu öğretici, bu sınıf içinde bir test seyahat kullanır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-262">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="e58fb-263">Daha sonra modelle denemek için diğer senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e58fb-263">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="e58fb-264">Aşağıdaki kodu ekleyin `TestTrips` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="e58fb-264">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="e58fb-265">Bu seyahat 's gerçek ücreti 29.5 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e58fb-265">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="e58fb-266">Model ücreti tahmin etmek gibi bir yer tutucu olarak 0'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e58fb-266">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="e58fb-267">Belirtilen Seyahat Ücreti tahmin etmek için geri dönüp *Program.cs* dosya ve aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e58fb-267">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="e58fb-268">Test çalışması için tahmin edilen ücreti ücreti görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e58fb-268">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="e58fb-269">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="e58fb-269">Congratulations!</span></span> <span data-ttu-id="e58fb-270">Şimdi başarıyla ücreti seyahat fares tahmin etmeye yönelik bir machine learning modelini yerleşik, doğruluğunu değerlendirilir ve tahminleri yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e58fb-270">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="e58fb-271">Bu öğreticinin için kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) deposu.</span><span class="sxs-lookup"><span data-stu-id="e58fb-271">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e58fb-272">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e58fb-272">Next steps</span></span>

<span data-ttu-id="e58fb-273">Bu öğreticide, öğrenilen nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="e58fb-273">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="e58fb-274">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="e58fb-274">Understand the problem</span></span>
> * <span data-ttu-id="e58fb-275">Uygun makine öğrenme görevini seçin</span><span class="sxs-lookup"><span data-stu-id="e58fb-275">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="e58fb-276">Hazırlama ve verileri anlamak</span><span class="sxs-lookup"><span data-stu-id="e58fb-276">Prepare and understand the data</span></span>
> * <span data-ttu-id="e58fb-277">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="e58fb-277">Create a learning pipeline</span></span>
> * <span data-ttu-id="e58fb-278">Yük ve veri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e58fb-278">Load and transform the data</span></span>
> * <span data-ttu-id="e58fb-279">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="e58fb-279">Choose a learning algorithm</span></span>
> * <span data-ttu-id="e58fb-280">Modeli eğitmek</span><span class="sxs-lookup"><span data-stu-id="e58fb-280">Train the model</span></span>
> * <span data-ttu-id="e58fb-281">Modeli değerlendirin</span><span class="sxs-lookup"><span data-stu-id="e58fb-281">Evaluate the model</span></span>
> * <span data-ttu-id="e58fb-282">Model için tahminde kullanın</span><span class="sxs-lookup"><span data-stu-id="e58fb-282">Use the model for predictions</span></span>

<span data-ttu-id="e58fb-283">Bilgi almaya devam etmek ve daha fazla örneklerini bulmak için GitHub depomuzda denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e58fb-283">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e58fb-284">DotNet/machinelearning GitHub deposunu</span><span class="sxs-lookup"><span data-stu-id="e58fb-284">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
