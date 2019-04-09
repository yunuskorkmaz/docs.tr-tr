---
title: ML.NET ile bir regresyon learner kullanarak fiyatlarını tahmin etme
description: ML.NET ile bir regresyon learner kullanarak fiyatlarını tahmin etme.
author: aditidugar
ms.author: johalex
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: b97ea433b36aa52682e5e86ab493cfabf8f86193
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122089"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a><span data-ttu-id="2b9b6-103">Öğretici: ML.NET ile bir regresyon learner kullanarak fiyatlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-103">Tutorial: Predict prices using a regression learner with ML.NET</span></span>

<span data-ttu-id="2b9b6-104">Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [regresyon modeli](../resources/glossary.md#regression) Fiyatlar, özellikle tahmin etmede, New York City taksi fares.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-104">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting prices, specifically, New York City taxi fares.</span></span>

> [!NOTE]
> <span data-ttu-id="2b9b6-105">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-105">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="2b9b6-106">Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="2b9b6-106">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="2b9b6-107">Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.11**.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-107">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="2b9b6-108">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="2b9b6-108">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="2b9b6-109">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="2b9b6-110">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="2b9b6-110">Understand the problem</span></span>
> * <span data-ttu-id="2b9b6-111">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="2b9b6-111">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="2b9b6-112">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="2b9b6-112">Prepare and understand the data</span></span>
> * <span data-ttu-id="2b9b6-113">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b9b6-113">Create a learning pipeline</span></span>
> * <span data-ttu-id="2b9b6-114">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-114">Load and transform the data</span></span>
> * <span data-ttu-id="2b9b6-115">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="2b9b6-115">Choose a learning algorithm</span></span>
> * <span data-ttu-id="2b9b6-116">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-116">Train the model</span></span>
> * <span data-ttu-id="2b9b6-117">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-117">Evaluate the model</span></span>
> * <span data-ttu-id="2b9b6-118">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="2b9b6-118">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2b9b6-119">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2b9b6-119">Prerequisites</span></span>

* <span data-ttu-id="2b9b6-120">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-120">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="2b9b6-121">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="2b9b6-121">Understand the problem</span></span>

<span data-ttu-id="2b9b6-122">Bu da oturan bir taksi seyahat, taksi tahmin etme hakkında bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-122">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="2b9b6-123">İlk bakışta takip edilerek özgün uzaklık üzerinde yalnızca bağımlı görünüyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-123">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="2b9b6-124">Ancak, New York taksi satıcıları ek Yolcuların veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere için değişken miktarda ücret alınır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-124">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="2b9b6-125">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="2b9b6-125">Select the appropriate machine learning task</span></span>

<span data-ttu-id="2b9b6-126">Veri kümesindeki diğer etkenlere göre bir gerçek değer için fiyat değerini tahmin etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-126">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="2b9b6-127">Seçtiğiniz yapmak için bir [regresyon](../resources/glossary.md#regression) machine learning görev.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-127">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2b9b6-128">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b9b6-128">Create a console application</span></span>

1. <span data-ttu-id="2b9b6-129">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="2b9b6-130">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="2b9b6-131">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="2b9b6-132">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="2b9b6-133">İçinde **adı** metin kutusuna "TaxiFarePrediction" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="2b9b6-134">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-134">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="2b9b6-135">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-135">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="2b9b6-136">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-136">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="2b9b6-137">Yükleme **Microsoft.ML** NuGet paketi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-137">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="2b9b6-138">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-138">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2b9b6-139">Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-139">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="2b9b6-140">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="2b9b6-141">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="2b9b6-141">Prepare and understand the data</span></span>

1. <span data-ttu-id="2b9b6-142">İndirme [taksi taksi train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taksi taksi test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="2b9b6-143">Machine learning modeli eğitmek ve modelin nasıl doğru olup'ı değerlendirmek için bu veri kümesi kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-143">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="2b9b6-144">Bu veri kümesi başlangıçta arasındadır [NYC TLC taksi seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="2b9b6-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="2b9b6-145">İçinde **Çözüm Gezgini**, her birini sağ tıklayın \*.csv dosyalarını ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-145">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="2b9b6-146">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="2b9b6-147">Açık **taksi taksi train.csv** veri kümesi ve ilk satırında sütun üst bilgilerini bakın.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-147">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="2b9b6-148">Her sütun bir göz atın.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-148">Take a look at each of the columns.</span></span> <span data-ttu-id="2b9b6-149">Verileri anlamak ve hangi sütunların karar **özellikleri** hangisinin **etiket**.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-149">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="2b9b6-150">**Etiket** tahmin etmek istediğiniz sütunu tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-150">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="2b9b6-151">Tanımlanan **özellikleri** etiketi tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-151">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="2b9b6-152">Sağlanan veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-152">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="2b9b6-153">**vendor_id:** Taksi satıcı kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-153">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="2b9b6-154">**rate_code:** Taksi dönüş oranı türünü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-154">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="2b9b6-155">**passenger_count:** Bir özellik Yolcuların seyahat üzerinde sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-155">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="2b9b6-156">**trip_time_in_secs:** Seyahat geçen süre miktarı.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-156">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="2b9b6-157">Seyahat, taksi seyahat tamamlanmadan önce tahmin etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-157">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="2b9b6-158">Bu ne kadar seyahat bilmiyorum dakikamızı ayıralım.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-158">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="2b9b6-159">Bu nedenle, seyahat süresi, bir özellik değildir ve bu sütunu modelden dışında bırakacağız.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-159">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="2b9b6-160">**trip_distance:** Seyahat mesafesini bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-160">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="2b9b6-161">**payment_type:** Ödeme yöntemini (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-161">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="2b9b6-162">**fare_amount:** Ücretli toplam taksi taksi etiketi olur.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-162">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="2b9b6-163">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b9b6-163">Create data classes</span></span>

<span data-ttu-id="2b9b6-164">Girdi verilerini ve Öngörüler için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-164">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="2b9b6-165">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-165">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="2b9b6-166">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-166">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="2b9b6-167">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-167">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="2b9b6-168">Aşağıdaki `using` yeni dosya için yönergeler:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-168">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="2b9b6-169">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-169">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` <span data-ttu-id="2b9b6-170">giriş verisi sınıfıdır ve her bir veri kümesi sütunları tanımlarına sahip.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-170">is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="2b9b6-171">Kullanım <xref:Microsoft.ML.Data.LoadColumnAttribute> veri kümesinde kaynak sütunları dizin belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-171">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="2b9b6-172">`TaxiTripFarePrediction` Sınıfı, tahmini sonuçlar'ı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-172">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="2b9b6-173">Tek bir kayan noktalı sayı alana sahip `FareAmount`, ile bir `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-173">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="2b9b6-174">Regresyon görev durumunda **puanı** sütun tahmin edilen etiket değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-174">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="2b9b6-175">Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-175">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="2b9b6-176">Veri ve model tanımlar</span><span class="sxs-lookup"><span data-stu-id="2b9b6-176">Define data and model paths</span></span>

<span data-ttu-id="2b9b6-177">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-177">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="2b9b6-178">Veri kümeleri dosyalarına ve modeli kaydedin ve dosyaya yolları tutmak için üç alanı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-178">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* `_trainDataPath` <span data-ttu-id="2b9b6-179">modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-179">contains the path to the file with the data set used to train the model.</span></span>
* `_testDataPath` <span data-ttu-id="2b9b6-180">model değerlendirmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-180">contains the path to the file with the data set used to evaluate the model.</span></span>
* `_modelPath` <span data-ttu-id="2b9b6-181">eğitilen modelin depolandığı dosya yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-181">contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="2b9b6-182">Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için ve `_textLoader` değişkeni:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-182">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="2b9b6-183">ML.NET modeliyle oluştururken ML bağlam oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-183">When building a model with ML.NET you start by creating an ML Context.</span></span> <span data-ttu-id="2b9b6-184">Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-184">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="2b9b6-185">Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilmesi için machine learning işiniz için bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-185">The environment provides a context for your machine learning job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="2b9b6-186">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="2b9b6-186">Initialize variables in Main</span></span>

<span data-ttu-id="2b9b6-187">Adlı bir değişken oluşturma `mlContext` ve yeni bir örneğini ile başlatma `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-187">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="2b9b6-188">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-188">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="2b9b6-189">Sonraki kod satırı olarak ekleyin `Main` çağrılacak yöntem `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-189">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="2b9b6-190">`Train` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-190">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="2b9b6-191">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-191">Loads the data.</span></span>
* <span data-ttu-id="2b9b6-192">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-192">Extracts and transforms the data.</span></span>
* <span data-ttu-id="2b9b6-193">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-193">Trains the model.</span></span>
* <span data-ttu-id="2b9b6-194">Model .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-194">Saves the model as .zip file.</span></span>
* <span data-ttu-id="2b9b6-195">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-195">Returns the model.</span></span>

<span data-ttu-id="2b9b6-196">`Train` Yöntemi modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-196">The `Train` method trains the model.</span></span> <span data-ttu-id="2b9b6-197">Bu yöntem oluşturma hemen altına `Main`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-197">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="2b9b6-198">İki parametre olarak geçiriyoruz `Train` yöntemi; bir `MLContext` bağlamının (`mlContext`) ve veri kümesi yolu için bir dize (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="2b9b6-198">We are passing two parameters into the `Train` method; an `MLContext` for the context (`mlContext`), and a string for the dataset path (`dataPath`).</span></span> <span data-ttu-id="2b9b6-199">Veri kümelerini yüklemek için bu yöntem yeniden oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-199">We're going to reuse this method for loading datasets.</span></span>

## <a name="load-and-transform-data"></a><span data-ttu-id="2b9b6-200">Veri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-200">Load and transform data</span></span>

<span data-ttu-id="2b9b6-201">Kullanarak verileri yüklemek `MLContext.Data.LoadFromTextFile` için sarmalayıcı [LoadFromTextFile yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span><span class="sxs-lookup"><span data-stu-id="2b9b6-201">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="2b9b6-202">Döndürür bir <xref:Microsoft.Data.DataView.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-202">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> 

<span data-ttu-id="2b9b6-203">Giriş ve çıkış olarak `Transforms`, `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-203">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="2b9b6-204">ML.NET veriler SQL görünümüne benzer.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-204">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="2b9b6-205">Bu, gevşek değerlendirilen, şema ve heterojen olur.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-205">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="2b9b6-206">Nesne, işlem hattını ilk kısmı ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-206">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="2b9b6-207">Bu öğreticide, bir veri kümesi ile taksi seyahat fiyatlandırma bilgileri yükler.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-207">For this tutorial, it loads a dataset with taxi trip pricing information.</span></span> <span data-ttu-id="2b9b6-208">Bu model oluşturmayı ve bunu eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-208">This is used to create the model, and train it.</span></span>

<span data-ttu-id="2b9b6-209">İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-209">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="2b9b6-210">Sonraki adımlarda sütunlara adlarıyla tanımlanan diyoruz `TaxiTrip` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-210">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="2b9b6-211">Model eğitim ve diğer değerleri varsayılan olarak, hesaplanan zaman **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-211">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="2b9b6-212">Taksi seyahat taksi tahmin etmek istediğimiz gibi kopyalayın `FareAmount` sütuna **etiket** sütun.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-212">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="2b9b6-213">Bunu yapmak için kullanın `CopyColumnsEstimator` dönüştürme sınıfı ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-213">To do that, use the `CopyColumnsEstimator` transformation class, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="2b9b6-214">Modeli eğitir algoritması **sayısal** kategorik verileri dönüştürmek zorunda özellikleri (`VendorId`, `RateCode`, ve `PaymentType`) içine numaraları değerleri (`VendorIdEncoded`, `RateCodeEncoded`, ve `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="2b9b6-214">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="2b9b6-215">Bunu yapmak için Microsoft.ML.Transforms.OneHotEncodingTransformer kullanmak > atayan farklı sayısal dönüştürme sınıfına anahtar sütunları farklı değerlerle değerlerini ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-215">To do that, use the Microsoft.ML.Transforms.OneHotEncodingTransformer> transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="2b9b6-216">Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak `mlContext.Transforms.Concatenate` dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-216">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="2b9b6-217">Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-217">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="2b9b6-218">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-218">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="2b9b6-219">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="2b9b6-219">Choose a learning algorithm</span></span>

<span data-ttu-id="2b9b6-220">Veri ardışık düzenine eklemek ve giriş doğru biçime dönüştürme sonra bir öğrenme algoritması seçiyoruz (**learner**).</span><span class="sxs-lookup"><span data-stu-id="2b9b6-220">After adding the data to the pipeline and transforming it into the correct input format, we select a learning algorithm (**learner**).</span></span> <span data-ttu-id="2b9b6-221">Learner modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-221">The learner trains the model.</span></span> <span data-ttu-id="2b9b6-222">Seçtik bir **regresyon** görev kullanacağız Bu sorun için bir `FastTreeRegressionTrainer` ML.NET tarafından sağlanan regresyon öğrencileriyle biri olan learner.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-222">We chose a **regression** task for this problem, so we use a `FastTreeRegressionTrainer` learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="2b9b6-223">`FastTreeRegressionTrainer` Eğitim algoritması kullanan gradyan artırma.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-223">The `FastTreeRegressionTrainer` training algorithm utilizes gradient boosting.</span></span> <span data-ttu-id="2b9b6-224">Gradyan artırma bir machine learning teknik regresyon sorunları var.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-224">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="2b9b6-225">Bu, her regresyon ağaç tarafınızdaki bir biçimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-225">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="2b9b6-226">Her adımda hata oluştu ölçmenizi ve sonraki düzeltmek için önceden tanımlanmış kaybı işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-226">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="2b9b6-227">Aslında bir topluluğu, tahmin modellerini daha zayıf bir tahmin modeli sonucudur.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-227">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="2b9b6-228">Gradyan artırma hakkında daha fazla bilgi için bkz. [artırılmış karar ağacı regresyonu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="2b9b6-228">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="2b9b6-229">Aşağıdaki kodu ekleyin `Train` ekleme yöntemi `FastTreeRegressionTrainer` önceki adımda eklenen veri işleme kodu:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-229">Add the following code into the `Train` method to add the `FastTreeRegressionTrainer` to the data processing code added in the previous step:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="2b9b6-230">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-230">Train the model</span></span>

<span data-ttu-id="2b9b6-231">Modeli eğitmek için son adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-231">The final step is to train the model.</span></span> <span data-ttu-id="2b9b6-232">Biz modeli eğitmek <xref:Microsoft.ML.Data.TransformerChain>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-232">We train the model, <xref:Microsoft.ML.Data.TransformerChain>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="2b9b6-233">Tahmin tanımlandıktan sonra kullanarak modeli eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> zaten yüklenmiş eğitim verilerini sağlayarak.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-233">Once the estimator has been defined, we train the model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="2b9b6-234">Bu tahminler elde etmek için kullanılacak bir modelini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-234">This returns a model to use for predictions.</span></span> `pipeline.Fit()` <span data-ttu-id="2b9b6-235">işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-235">trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="2b9b6-236">Denemeyi böyle kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-236">The experiment is not executed until this happens.</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

### <a name="save-the-model"></a><span data-ttu-id="2b9b6-237">Modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="2b9b6-237">Save the model</span></span>

<span data-ttu-id="2b9b6-238">Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-238">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="2b9b6-239">Model bir .zip dosyası olarak kaydetmek için aşağıdaki kodu ekleyin sonunda `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-239">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="2b9b6-240">Bir .zip dosyası olarak modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="2b9b6-240">Save the model as a .zip file</span></span>

<span data-ttu-id="2b9b6-241">Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `Train` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-241">Create the `SaveModelAsFile` method, just after the `Train` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="2b9b6-242">`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-242">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="2b9b6-243">Model bir .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-243">Saves the model as a .zip file.</span></span>

<span data-ttu-id="2b9b6-244">Modeli yeniden ve diğer uygulamalarda kullanılan üzere kaydetmek için bir yöntem için oluşturmamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-244">We need to create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="2b9b6-245">`ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-245">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="2b9b6-246">Bu zip dosyası olarak kaydetmek istediğimiz beri oluşturacağız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-246">Since we want to save this as a zip file, we'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="2b9b6-247">Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-247">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

<span data-ttu-id="2b9b6-248">Biz burada dosyanın bir konsol iletisi ile yazarak yazılmıştır görüntüleyebilir `_modelPath`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-248">We could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="2b9b6-249">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-249">Evaluate the model</span></span>

<span data-ttu-id="2b9b6-250">Değerlendirme model etiket değerlerini ne kadar iyi tahmin denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-250">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="2b9b6-251">Model modeli eğitmek için kullanılmayan verileri iyi tahminler yapar önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-251">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="2b9b6-252">Bu öğreticide işlendiğinden bunu yapmanın bir yolu, verileri eğitim ve test veri kümesi bölme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-252">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="2b9b6-253">Eğitim verileri modeli eğittiğimize göre test verileri ne kadar iyi gerçekleştirdiği görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-253">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="2b9b6-254">`Evaluate` Yöntemi modeli değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-254">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="2b9b6-255">Bu yöntem oluşturmak için aşağıdaki kodu ekleyin. `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-255">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
<span data-ttu-id="2b9b6-256">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-256">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="2b9b6-257">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-257">Loads the test dataset.</span></span>
* <span data-ttu-id="2b9b6-258">Regresyon değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-258">Creates the regression evaluator.</span></span>
* <span data-ttu-id="2b9b6-259">Model değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-259">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="2b9b6-260">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-260">Displays the metrics.</span></span>

<span data-ttu-id="2b9b6-261">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-261">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="2b9b6-262">Test veri kümesini kullanarak yük `MLContext.Data.LoadFromTextFile` sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-262">Load the test dataset using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="2b9b6-263">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-263">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="2b9b6-264">Aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-264">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="2b9b6-265">Ardından, makine öğrenimi kullanın `model` özellikleri giriş ve tahmin döndürmek için parametre (dönüştürücü).</span><span class="sxs-lookup"><span data-stu-id="2b9b6-265">Next, use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="2b9b6-266">Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-266">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="2b9b6-267">`RegressionContext.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-267">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="2b9b6-268">Döndürür bir <xref:Microsoft.ML.Data.RegressionMetrics> regresyon değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-268">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> <span data-ttu-id="2b9b6-269">Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-269">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="2b9b6-270">Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-270">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="2b9b6-271">Modeli değerlendirme ve değerlendirme ölçümleri üretmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-271">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="2b9b6-272">[RSquared](../resources/glossary.md#coefficient-of-determination) regresyon modelleri, başka bir değerlendirme unsurdur.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-272">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="2b9b6-273">RSquared 0 ile 1 arasındaki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-273">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="2b9b6-274">Daha değerini 1 olarak daha iyi modelidir yakınız.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-274">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="2b9b6-275">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RSquared değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-275">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="2b9b6-276">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) gerileme modelini değerlendirme ölçümlerini biridir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-276">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="2b9b6-277">Daha düşük olan, daha iyi modelidir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-277">The lower it is, the better the model is.</span></span> <span data-ttu-id="2b9b6-278">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RMS değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-278">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="2b9b6-279">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="2b9b6-279">Use the model for predictions</span></span>

## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a><span data-ttu-id="2b9b6-280">Model ve tek bir yorum ile test veri sonucu tahmin edin</span><span class="sxs-lookup"><span data-stu-id="2b9b6-280">Predict the test data outcome with the model and a single comment</span></span>

<span data-ttu-id="2b9b6-281">Oluşturma `TestSinglePrediction` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-281">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

<span data-ttu-id="2b9b6-282">`TestSinglePrediction` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-282">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="2b9b6-283">Test verilerini tek bir yorum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-283">Creates a single comment of test data.</span></span>
* <span data-ttu-id="2b9b6-284">Test verilerini temel alarak taksi miktarı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-284">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="2b9b6-285">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-285">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="2b9b6-286">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-286">Displays the predicted results.</span></span>

<span data-ttu-id="2b9b6-287">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-287">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="2b9b6-288">Modeli zip dosyasından yükleme istiyoruz beri kaydettik, oluşturacağız `FileStream` çağırmadan önce hemen `Load` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-288">Since we want to load the model from the zip file we saved, we'll create the `FileStream` immediately before calling the `Load` method.</span></span> <span data-ttu-id="2b9b6-289">Aşağıdaki kodu ekleyin `TestSinglePrediction` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-289">Add the following code to the `TestSinglePrediction` method as the next line:</span></span>

[!code-csharp[LoadTheModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

<span data-ttu-id="2b9b6-290">Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-290">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="2b9b6-291"><xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-291">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="2b9b6-292">Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` sonraki satırı olarak `TestSinglePrediction` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-292">Let's add the following code to create the `PredictionEngine` as the next line in the `TestSinglePrediction` Method:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
<span data-ttu-id="2b9b6-293">Bu öğretici, bu sınıf içinde bir test seyahat kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-293">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="2b9b6-294">Daha sonra modeli denemek için diğer senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-294">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="2b9b6-295">Eğitilen modelin Maliyet tahminini test etmek için bir seyahat ekleme `TestSinglePrediction` bir örneğini oluşturarak yöntemi `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-295">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 <span data-ttu-id="2b9b6-296">Biz taksi seyahat verilerini tek bir örneği temel taksi tahmin etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-296">We can use that to predict the fare based on a single instance of the taxi trip data.</span></span> <span data-ttu-id="2b9b6-297">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-297">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="2b9b6-298">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-298">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="2b9b6-299">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-299">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="2b9b6-300">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-300">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="2b9b6-301">Belirtilen seyahat, tahmin edilen taksi görüntülemek için aşağıdaki kodu ekleyin. `TestSinglePrediction` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-301">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="2b9b6-302">Test durumunuz için tahmin edilen taksi taksi görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-302">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="2b9b6-303">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="2b9b6-303">Congratulations!</span></span> <span data-ttu-id="2b9b6-304">Başarıyla taksi seyahat fares tahmin etmeye yönelik bir machine learning modeli, doğruluğunun değerlendirilir, derleyip tahminlerde bulunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-304">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="2b9b6-305">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-305">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2b9b6-306">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2b9b6-306">Next steps</span></span>

<span data-ttu-id="2b9b6-307">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="2b9b6-307">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="2b9b6-308">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="2b9b6-308">Understand the problem</span></span>
> * <span data-ttu-id="2b9b6-309">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="2b9b6-309">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="2b9b6-310">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="2b9b6-310">Prepare and understand the data</span></span>
> * <span data-ttu-id="2b9b6-311">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b9b6-311">Create a learning pipeline</span></span>
> * <span data-ttu-id="2b9b6-312">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-312">Load and transform the data</span></span>
> * <span data-ttu-id="2b9b6-313">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="2b9b6-313">Choose a learning algorithm</span></span>
> * <span data-ttu-id="2b9b6-314">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-314">Train the model</span></span>
> * <span data-ttu-id="2b9b6-315">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-315">Evaluate the model</span></span>
> * <span data-ttu-id="2b9b6-316">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="2b9b6-316">Use the model for predictions</span></span>

<span data-ttu-id="2b9b6-317">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="2b9b6-317">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2b9b6-318">Iris kümeleme</span><span class="sxs-lookup"><span data-stu-id="2b9b6-318">Iris clustering</span></span>](iris-clustering.md)
