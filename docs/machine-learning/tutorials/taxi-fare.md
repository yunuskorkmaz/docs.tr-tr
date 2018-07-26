---
title: ML.NET New York taksi fares (gerileme) tahmin etmek için kullanın
description: ML.NET bir regresyon senaryosunda kullanmayı öğrenin.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e3ff2124a43cf42ce26cf94cfd5384387eef0ed9
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937078"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="2f9b5-103">Öğretici: Kullanımı ML.NET New York taksi fares (gerileme) tahmin etmek için</span><span class="sxs-lookup"><span data-stu-id="2f9b5-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="2f9b5-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="2f9b5-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="2f9b5-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="2f9b5-106">Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [regresyon modeli](../resources/glossary.md#regression) oturan taksi fares tahmin etmeye yönelik.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="2f9b5-107">Bu öğreticide, şunların nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="2f9b5-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="2f9b5-108">Understand the problem</span></span>
> * <span data-ttu-id="2f9b5-109">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="2f9b5-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="2f9b5-110">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="2f9b5-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="2f9b5-111">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f9b5-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="2f9b5-112">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-112">Load and transform the data</span></span>
> * <span data-ttu-id="2f9b5-113">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="2f9b5-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="2f9b5-114">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-114">Train the model</span></span>
> * <span data-ttu-id="2f9b5-115">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-115">Evaluate the model</span></span>
> * <span data-ttu-id="2f9b5-116">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="2f9b5-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f9b5-117">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2f9b5-117">Prerequisites</span></span>

* <span data-ttu-id="2f9b5-118">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="2f9b5-119">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="2f9b5-119">Understand the problem</span></span>

<span data-ttu-id="2f9b5-120">Bu sorunu geçici olarak ortalanır **bir taksi, taksi tahmin geçirmek New York City**.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="2f9b5-121">İlk bakışta takip edilerek özgün uzaklık üzerinde yalnızca bağımlı görünüyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="2f9b5-122">Ancak, New York taksi satıcıları ek Yolcuların veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere için değişken miktarda ücret alınır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="2f9b5-123">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="2f9b5-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="2f9b5-124">Taksi taksi tahmin etmek için önce uygun makine öğrenme görevini seçin.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="2f9b5-125">Gerçek bir değer (Fiyat gösteren bir double) kümesindeki diğer etkenlere göre tahmin etmek için arıyoruz.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="2f9b5-126">Seçtiğiniz bir [ **regresyon** ](../resources/glossary.md#regression) görev.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2f9b5-127">Bir konsol uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="2f9b5-127">Create a console application</span></span>

1. <span data-ttu-id="2f9b5-128">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="2f9b5-129">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="2f9b5-130">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="2f9b5-131">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="2f9b5-132">İçinde **adı** metin kutusuna "TaxiFarePrediction" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-132">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="2f9b5-133">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyaları kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-133">Create a directory named *Data* in your project to save the data set files:</span></span>

    <span data-ttu-id="2f9b5-134">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="2f9b5-135">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="2f9b5-136">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-136">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="2f9b5-137">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2f9b5-138">Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="2f9b5-139">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="2f9b5-140">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="2f9b5-140">Prepare and understand the data</span></span>

1. <span data-ttu-id="2f9b5-141">İndirme [taksi taksi train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taksi taksi test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-141">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="2f9b5-142">Machine learning modeli eğitmek ve modelin nasıl doğru olup'ı değerlendirmek için bu veri kümesi kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-142">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="2f9b5-143">Bu veri kümesi başlangıçta arasındadır [NYC TLC taksi seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="2f9b5-143">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="2f9b5-144">İçinde **Çözüm Gezgini**, her birini sağ tıklayın \*.csv dosyalarını ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-144">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="2f9b5-145">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **her zaman**.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-145">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="2f9b5-146">Açık **taksi taksi train.csv** veri kümesi ve ilk satırında sütun üst bilgilerini bakın.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-146">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="2f9b5-147">Her sütun bir göz atın.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-147">Take a look at each of the columns.</span></span> <span data-ttu-id="2f9b5-148">Verileri anlamak ve hangi sütunların karar **özellikleri** hangisinin **etiket**.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-148">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="2f9b5-149">**Etiket** tahmin etmek istediğiniz sütunu tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-149">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="2f9b5-150">Tanımlanan **özellikleri** etiketi tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-150">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="2f9b5-151">Sağlanan veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-151">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="2f9b5-152">**vendor_id:** taksi satıcı kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="2f9b5-153">**rate_code:** taksi dönüş oranı türünü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="2f9b5-154">**passenger_count:** Yolcuların seyahat üzerinde sayısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="2f9b5-155">**trip_time_in_secs:** seyahat süresini sürdü.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="2f9b5-156">Seyahat, taksi seyahat tamamlanmadan önce tahmin etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-156">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="2f9b5-157">Bu ne kadar seyahat bilmiyorum dakikamızı ayıralım.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-157">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="2f9b5-158">Bu nedenle, seyahat süresi, bir özellik değildir ve bu sütunu modelden dışında bırakacağız.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-158">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="2f9b5-159">**trip_distance:** seyahat mesafesini bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-159">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="2f9b5-160">**payment_type:** (nakit veya kredi kartı) ödeme yöntemini bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-160">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="2f9b5-161">**fare_amount:** ödenen toplam taksi taksi etiketidir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-161">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="2f9b5-162">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f9b5-162">Create data classes</span></span>

<span data-ttu-id="2f9b5-163">Girdi verilerini ve Öngörüler için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-163">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="2f9b5-164">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-164">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="2f9b5-165">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="2f9b5-166">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-166">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="2f9b5-167">Aşağıdaki `using` yeni dosya için yönergeler:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-167">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="2f9b5-168">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-168">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="2f9b5-169">`TaxiTrip` giriş verisi sınıfıdır ve her bir veri kümesi sütunları tanımlarına sahip.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-169">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="2f9b5-170">Kullanım [sütun](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) veri kümesinde kaynak sütunları dizin belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-170">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="2f9b5-171">`TaxiTripFarePrediction` Sınıfı, tahmin edilen sonuçları göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-171">The `TaxiTripFarePrediction` class is used to represent predicted results.</span></span> <span data-ttu-id="2f9b5-172">Tek bir kayan nokta vardır (`FareAmount`) alanına bir `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-172">It has a single float (`FareAmount`) field with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="2f9b5-173">**Puanı** ML.NET özel sütunda bir sütundur.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-173">The **Score** column is the special column in ML.NET.</span></span> <span data-ttu-id="2f9b5-174">Model, bu sütuna tahmin edilen değerleri çıkarır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-174">The model outputs predicted values into that column.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="2f9b5-175">Veri ve model tanımlar</span><span class="sxs-lookup"><span data-stu-id="2f9b5-175">Define data and model paths</span></span>

<span data-ttu-id="2f9b5-176">Geri Git *Program.cs* dosya ve veri kümeleri dosyalarına ve modeli kaydedin ve dosyaya yolları tutmak için üç alanları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-176">Go back to the *Program.cs* file and add three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="2f9b5-177">`_datapath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-177">`_datapath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="2f9b5-178">`_testdatapath` model değerlendirmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-178">`_testdatapath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="2f9b5-179">`_modelpath` eğitilen modelin depolandığı dosya yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-179">`_modelpath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="2f9b5-180">Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-180">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="2f9b5-181">Derleme, aşağıdaki ekleyin önceki kodun `using` üst kısmındaki yönergeleri *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-181">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="2f9b5-182">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f9b5-182">Create a learning pipeline</span></span>

<span data-ttu-id="2f9b5-183">Aşağıdaki ek ekleyin `using` yönergeleri üstüne *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-183">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="2f9b5-184">İçinde `Main`, değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-184">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="2f9b5-185">`Train` Yöntemi modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-185">The `Train` method trains the model.</span></span> <span data-ttu-id="2f9b5-186">Bu yöntem oluşturma hemen altına `Main`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-186">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="2f9b5-187">Öğrenme işlem hattınızı tüm veri ve algoritmaları modeli eğitmek gerekli yükler.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-187">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="2f9b5-188">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-188">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="2f9b5-189">Veri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-189">Load and transform data</span></span>

<span data-ttu-id="2f9b5-190">Öğrenme işlem hattının gerçekleştirdiği ilk adım eğitim veri kümesinden veri yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-190">The first step that the learning pipeline performs is loading data from the training data set.</span></span> <span data-ttu-id="2f9b5-191">Bu örnekte, tarafından tanımlanan bir yol ile metin dosyasında eğitim veri kümesi depolanır `_datapath` alan.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-191">In our case, training data set is stored in the text file with a path defined by the `_datapath` field.</span></span> <span data-ttu-id="2f9b5-192">İlk satır verileri yüklenirken yoksayılmalıdır. Bu nedenle bu dosyayı başlığını sütun adlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-192">That file contains the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="2f9b5-193">Bir dosyadaki sütunları virgülle ayrılmış (",").</span><span class="sxs-lookup"><span data-stu-id="2f9b5-193">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="2f9b5-194">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-194">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="2f9b5-195">Sonraki adımlarda sütunlara adlarıyla tanımlanan diyoruz `TaxiTrip` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-195">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="2f9b5-196">Ne zaman model eğitim ve hesaplanan değerler **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-196">When the model is trained and evaluated, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="2f9b5-197">Taksi seyahat taksi tahmin etmek istediğimiz gibi kopyalayın `FareAmount` sütuna **etiket** sütun.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-197">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="2f9b5-198">Bunu yapmak için kullanın <xref:Microsoft.ML.Transforms.ColumnCopier> ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-198">To do that, use <xref:Microsoft.ML.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="2f9b5-199">Modeli eğitir algoritması **sayısal** kategorik verileri dönüştürmek zorunda özellikleri (`VendorId`, `RateCode`, ve `PaymentType`) içine numaraları değerleri.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-199">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="2f9b5-200">Bunu yapmak için kullanın <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, anahtar değerlerini farklı değerlerle her sütun, farklı sayısal atar ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-200">To do that, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="2f9b5-201">Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak <xref:Microsoft.ML.Transforms.ColumnConcatenator> dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-201">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="2f9b5-202">Bu adım yalnızca özelliklerinden bir learner işlenmesi sırasında gereklidir **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-202">This step is necessary as a learner processes only features from the **Features** column.</span></span> <span data-ttu-id="2f9b5-203">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-203">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="2f9b5-204">Dikkat `TripTime` karşılık gelen sütun `trip_time_in_secs` sütunu veri kümesi dosyası içindeki dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-204">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="2f9b5-205">Zaten bir kullanışlı tahmin özelliği değil belirledi.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-205">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="2f9b5-206">Aşağıdaki adımları başarılı yürütme için yukarıda belirtilen sırada ardışık düzene eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-206">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="2f9b5-207">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="2f9b5-207">Choose a learning algorithm</span></span>

<span data-ttu-id="2f9b5-208">Veri ardışık düzenine eklemek ve giriş doğru biçime dönüştürme sonra bir öğrenme algoritması seçin (**learner**).</span><span class="sxs-lookup"><span data-stu-id="2f9b5-208">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="2f9b5-209">Learner modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-209">The learner trains the model.</span></span> <span data-ttu-id="2f9b5-210">Seçtiğiniz bir **regresyon görev** Bu sorun için bu nedenle eklediğiniz bir <xref:Microsoft.ML.Trainers.FastTreeRegressor> ML.NET tarafından sağlanan regresyon öğrencileriyle biri olan learner.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-210">You chose a **regression task** for this problem, so you add a <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="2f9b5-211"><xref:Microsoft.ML.Trainers.FastTreeRegressor> Gradyan artırma learner kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-211"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="2f9b5-212">Gradyan artırma bir machine learning teknik regresyon sorunları var.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-212">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="2f9b5-213">Bu, her regresyon ağaç tarafınızdaki bir biçimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-213">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="2f9b5-214">Her adımda hata oluştu ölçmenizi ve sonraki düzeltmek için önceden tanımlanmış kaybı işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-214">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="2f9b5-215">Aslında bir topluluğu, tahmin modellerini daha zayıf bir tahmin modeli sonucudur.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-215">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="2f9b5-216">Gradyan artırma hakkında daha fazla bilgi için bkz. [artırılmış karar ağacı regresyonu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="2f9b5-216">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="2f9b5-217">Aşağıdaki kodu ekleyin `Train` önceki adımda eklenen koddan veri işleme yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-217">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="2f9b5-218">Yukarıdaki adımların tümünü ayrı deyimler ardışık düzenine eklenen, ancak C# oluşturma ve başlatma işlem hattını basitleştirir bir kullanışlı toplama başlatma söz dizimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-218">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="2f9b5-219">Şimdiye kadar eklediğiniz kodu değiştirin `Train` yöntemini aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-219">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="2f9b5-220">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-220">Train the model</span></span>

<span data-ttu-id="2f9b5-221">Modeli eğitmek için son adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-221">The final step is to train the model.</span></span> <span data-ttu-id="2f9b5-222">Bu noktaya kadar hiçbir işlem hattı çalıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-222">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="2f9b5-223">`pipeline.Train<TInput, TOutput>` Yöntemi üreten bir örneğini alan modeli `TInput` türü ve örneği çıkaran `TOutput` türü.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-223">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="2f9b5-224">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-224">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="2f9b5-225">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="2f9b5-225">And that's it!</span></span> <span data-ttu-id="2f9b5-226">Başarıyla bir makine öğrenimi taksi fares NYC içinde tahmin edebilen bir model eğitim.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-226">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="2f9b5-227">Şimdi şimdi modelin nasıl doğru olup olmadığını anlamak için göz atın ve taksi taksi değerleri tahmin etmek için kullanmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-227">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="2f9b5-228">Modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="2f9b5-228">Save the model</span></span>

<span data-ttu-id="2f9b5-229">Sonraki adıma geçmeden önce modeli bir .zip dosyası olarak sonuna aşağıdaki kodu ekleyerek kaydedin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-229">Before you go onto the next step, save the model to a .zip file by adding the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="2f9b5-230">Ekleme `await` ifadesine `model.WriteAsync` çağrı anlamına `Train` yöntemi bir görev döndüren zaman uyumsuz yöntemi için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-230">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="2f9b5-231">Değişiklik imzası `Train` aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-231">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="2f9b5-232">Dönüş türünün değiştirilmesi `Train` yöntemi eklemek sahip olduğunuz anlamına gelir; bir `await` çağıran koda `Train` içinde `Main` aşağıdaki kodda gösterildiği gibi yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-232">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="2f9b5-233">Kullanarak `await` içinde `Main` yöntemi anlamına gelir `Main` yöntemi olmalıdır `async` değiştiricisi ve dönüş bir `Task`:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-233">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="2f9b5-234">Ayrıca aşağıdakileri eklemeniz gerekir `using` dosyasının en üstüne yönergenizi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-234">You also need to add the following `using` directive at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="2f9b5-235">Çünkü `async Main` yöntemi, C# 7.1 eklenen özelliğidir ve C# 7.0 projesi varsayılan dil sürümü değil, C# 7.1 veya üzeri dil sürümünü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-235">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="2f9b5-236">Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-236">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="2f9b5-237">Seçin **derleme** sekmenize **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-237">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="2f9b5-238">Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm).</span><span class="sxs-lookup"><span data-stu-id="2f9b5-238">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="2f9b5-239">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-239">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="2f9b5-240">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-240">Evaluate the model</span></span>

<span data-ttu-id="2f9b5-241">Değerlendirme model etiket değerlerini ne kadar iyi tahmin denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-241">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="2f9b5-242">Model modeli eğitmek için kullanılmayan verileri iyi tahminler yapar önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-242">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="2f9b5-243">Bu öğreticide yapıldığını bunu yapmanın bir yolu train verileri bölme ve veri kümeleri, test etmek için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-243">One way to do this is to split the data into train and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="2f9b5-244">Modeli eğitme veri çubuğunda eğittiğimize göre test verileri ne kadar iyi gerçekleştirdiği görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-244">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="2f9b5-245">Geri Git `Main` yöntemi çağrısı altına aşağıdaki kodu ekleyin `Train`yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-245">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="2f9b5-246">`Evaluate` Yöntemi modeli değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-246">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="2f9b5-247">Bu yöntem oluşturmak için aşağıdaki kodu ekleyin. `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-247">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="2f9b5-248">Aşağıdaki kodu ekleyin `Evaluate` test verilerini Kurulum yüklemeyi yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-248">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="2f9b5-249">Modeli değerlendirme ve değerlendirme ölçümleri üretmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-249">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="2f9b5-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) gerileme modelini değerlendirme ölçümlerini biridir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="2f9b5-251">Daha düşük olan, daha iyi modelidir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-251">The lower it is, the better the model is.</span></span> <span data-ttu-id="2f9b5-252">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RMS değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-252">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="2f9b5-253">[RSquared](../resources/glossary.md#coefficient-of-determination) regresyon modelleri, başka bir değerlendirme unsurdur.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-253">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="2f9b5-254">RSquared 0 ile 1 arasındaki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-254">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="2f9b5-255">Daha değerini 1 olarak daha iyi modelidir yakınız.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-255">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="2f9b5-256">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RSquared değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-256">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="2f9b5-257">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="2f9b5-257">Use the model for predictions</span></span>

<span data-ttu-id="2f9b5-258">Ardından, model doğru şekilde çalıştığından emin olmak için kullanabileceğiniz merkezi test senaryoları için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-258">Next, create a class to house test scenarios that you can use to make sure the model is working correctly:</span></span>

1. <span data-ttu-id="2f9b5-259">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-259">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="2f9b5-260">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-260">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="2f9b5-261">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-261">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="2f9b5-262">Sınıfı gibi aşağıdaki örnekte de statik olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-262">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="2f9b5-263">Bu öğretici, bu sınıf içinde bir test seyahat kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-263">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="2f9b5-264">Daha sonra modeli denemek için diğer senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-264">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="2f9b5-265">Aşağıdaki kodu ekleyin `TestTrips` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-265">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="2f9b5-266">Bu yolculuğu'nın gerçek taksi 29.5 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-266">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="2f9b5-267">Model taksi tahmin etme gibi yer tutucu olarak 0'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-267">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="2f9b5-268">Belirtilen seyahat, taksi tahmin etmek için geri gidin *Program.cs* dosya ve içine aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-268">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="2f9b5-269">Test durumunuz için tahmin edilen taksi taksi görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-269">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="2f9b5-270">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="2f9b5-270">Congratulations!</span></span> <span data-ttu-id="2f9b5-271">Başarıyla taksi seyahat fares tahmin etmeye yönelik bir machine learning modeli, doğruluğunun değerlendirilir, derleyip tahminlerde bulunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-271">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="2f9b5-272">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) depo.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-272">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2f9b5-273">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2f9b5-273">Next steps</span></span>

<span data-ttu-id="2f9b5-274">Bu öğreticide şunları öğrendiniz: nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="2f9b5-274">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="2f9b5-275">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="2f9b5-275">Understand the problem</span></span>
> * <span data-ttu-id="2f9b5-276">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="2f9b5-276">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="2f9b5-277">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="2f9b5-277">Prepare and understand the data</span></span>
> * <span data-ttu-id="2f9b5-278">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f9b5-278">Create a learning pipeline</span></span>
> * <span data-ttu-id="2f9b5-279">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-279">Load and transform the data</span></span>
> * <span data-ttu-id="2f9b5-280">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="2f9b5-280">Choose a learning algorithm</span></span>
> * <span data-ttu-id="2f9b5-281">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-281">Train the model</span></span>
> * <span data-ttu-id="2f9b5-282">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-282">Evaluate the model</span></span>
> * <span data-ttu-id="2f9b5-283">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="2f9b5-283">Use the model for predictions</span></span>

<span data-ttu-id="2f9b5-284">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="2f9b5-284">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2f9b5-285">Iris kümeleme</span><span class="sxs-lookup"><span data-stu-id="2f9b5-285">Iris clustering</span></span>](iris-clustering.md)
