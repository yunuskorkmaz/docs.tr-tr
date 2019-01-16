---
title: ML.NET ile bir regresyon learner kullanarak New York taksi fares tahmin edin
description: ML.NET ile bir regresyon learner kullanarak fares tahmin edin.
author: aditidugar
ms.author: johalex
ms.date: 01/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: b17b4e31a60d6eaf432577281004bcf2c7ca1da2
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333791"
---
# <a name="tutorial-predict-new-york-taxi-fares-using-a-regression-learner-with-mlnet"></a><span data-ttu-id="72aab-103">Öğretici: ML.NET ile bir regresyon learner kullanarak New York taksi fares tahmin edin</span><span class="sxs-lookup"><span data-stu-id="72aab-103">Tutorial: Predict New York taxi fares using a regression learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="72aab-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="72aab-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="72aab-105">Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="72aab-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="72aab-106">Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [regresyon modeli](../resources/glossary.md#regression) oturan taksi fares tahmin etmeye yönelik.</span><span class="sxs-lookup"><span data-stu-id="72aab-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="72aab-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="72aab-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="72aab-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="72aab-108">Understand the problem</span></span>
> * <span data-ttu-id="72aab-109">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="72aab-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="72aab-110">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="72aab-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="72aab-111">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="72aab-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="72aab-112">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="72aab-112">Load and transform the data</span></span>
> * <span data-ttu-id="72aab-113">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="72aab-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="72aab-114">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="72aab-114">Train the model</span></span>
> * <span data-ttu-id="72aab-115">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="72aab-115">Evaluate the model</span></span>
> * <span data-ttu-id="72aab-116">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="72aab-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72aab-117">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="72aab-117">Prerequisites</span></span>

* <span data-ttu-id="72aab-118">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="72aab-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="72aab-119">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="72aab-119">Understand the problem</span></span>

<span data-ttu-id="72aab-120">Bu da oturan bir taksi seyahat, taksi tahmin etme hakkında bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="72aab-120">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="72aab-121">İlk bakışta takip edilerek özgün uzaklık üzerinde yalnızca bağımlı görünüyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="72aab-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="72aab-122">Ancak, New York taksi satıcıları ek Yolcuların veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere için değişken miktarda ücret alınır.</span><span class="sxs-lookup"><span data-stu-id="72aab-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="72aab-123">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="72aab-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="72aab-124">Veri kümesindeki diğer etkenlere göre bir gerçek değer için fiyat değerini tahmin etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="72aab-124">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="72aab-125">Seçtiğiniz yapmak için bir [regresyon](../resources/glossary.md#regression) machine learning görev.</span><span class="sxs-lookup"><span data-stu-id="72aab-125">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="72aab-126">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="72aab-126">Create a console application</span></span>

1. <span data-ttu-id="72aab-127">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="72aab-127">Open Visual Studio 2017.</span></span> <span data-ttu-id="72aab-128">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="72aab-128">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="72aab-129">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="72aab-129">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="72aab-130">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="72aab-130">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="72aab-131">İçinde **adı** metin kutusuna "TaxiFarePrediction" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="72aab-131">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="72aab-132">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için:</span><span class="sxs-lookup"><span data-stu-id="72aab-132">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="72aab-133">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="72aab-133">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="72aab-134">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="72aab-134">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="72aab-135">Yükleme **Microsoft.ML** NuGet paketi:</span><span class="sxs-lookup"><span data-stu-id="72aab-135">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="72aab-136">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="72aab-136">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="72aab-137">Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="72aab-137">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="72aab-138">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="72aab-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="72aab-139">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="72aab-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="72aab-140">İndirme [taksi taksi train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taksi taksi test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="72aab-140">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="72aab-141">Machine learning modeli eğitmek ve modelin nasıl doğru olup'ı değerlendirmek için bu veri kümesi kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="72aab-141">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="72aab-142">Bu veri kümesi başlangıçta arasındadır [NYC TLC taksi seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="72aab-142">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="72aab-143">İçinde **Çözüm Gezgini**, her birini sağ tıklayın \*.csv dosyalarını ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="72aab-143">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="72aab-144">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="72aab-144">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="72aab-145">Açık **taksi taksi train.csv** veri kümesi ve ilk satırında sütun üst bilgilerini bakın.</span><span class="sxs-lookup"><span data-stu-id="72aab-145">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="72aab-146">Her sütun bir göz atın.</span><span class="sxs-lookup"><span data-stu-id="72aab-146">Take a look at each of the columns.</span></span> <span data-ttu-id="72aab-147">Verileri anlamak ve hangi sütunların karar **özellikleri** hangisinin **etiket**.</span><span class="sxs-lookup"><span data-stu-id="72aab-147">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="72aab-148">**Etiket** tahmin etmek istediğiniz sütunu tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="72aab-148">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="72aab-149">Tanımlanan **özellikleri** etiketi tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72aab-149">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="72aab-150">Sağlanan veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="72aab-150">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="72aab-151">**vendor_id:** Taksi satıcı kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="72aab-151">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="72aab-152">**rate_code:** Taksi dönüş oranı türünü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="72aab-152">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="72aab-153">**passenger_count:** Bir özellik Yolcuların seyahat üzerinde sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="72aab-153">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="72aab-154">**trip_time_in_secs:** Seyahat geçen süre miktarı.</span><span class="sxs-lookup"><span data-stu-id="72aab-154">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="72aab-155">Seyahat, taksi seyahat tamamlanmadan önce tahmin etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="72aab-155">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="72aab-156">Bu ne kadar seyahat bilmiyorum dakikamızı ayıralım.</span><span class="sxs-lookup"><span data-stu-id="72aab-156">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="72aab-157">Bu nedenle, seyahat süresi, bir özellik değildir ve bu sütunu modelden dışında bırakacağız.</span><span class="sxs-lookup"><span data-stu-id="72aab-157">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="72aab-158">**trip_distance:** Seyahat mesafesini bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="72aab-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="72aab-159">**payment_type:** Ödeme yöntemini (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="72aab-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="72aab-160">**fare_amount:** Ücretli toplam taksi taksi etiketi olur.</span><span class="sxs-lookup"><span data-stu-id="72aab-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="72aab-161">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="72aab-161">Create data classes</span></span>

<span data-ttu-id="72aab-162">Girdi verilerini ve Öngörüler için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="72aab-162">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="72aab-163">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="72aab-163">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="72aab-164">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="72aab-164">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="72aab-165">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="72aab-165">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="72aab-166">Aşağıdaki `using` yeni dosya için yönergeler:</span><span class="sxs-lookup"><span data-stu-id="72aab-166">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="72aab-167">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="72aab-167">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="72aab-168">`TaxiTrip` giriş verisi sınıfıdır ve her bir veri kümesi sütunları tanımlarına sahip.</span><span class="sxs-lookup"><span data-stu-id="72aab-168">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="72aab-169">Kullanım <xref:Microsoft.ML.Data.ColumnAttribute> veri kümesinde kaynak sütunları dizin belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="72aab-169">Use the <xref:Microsoft.ML.Data.ColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="72aab-170">`TaxiTripFarePrediction` Sınıfı, tahmini sonuçlar'ı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="72aab-170">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="72aab-171">Tek bir kayan noktalı sayı alana sahip `FareAmount`, ile bir `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="72aab-171">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="72aab-172">Regresyon görev durumunda **puanı** sütun tahmin edilen etiket değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="72aab-172">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="72aab-173">Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="72aab-173">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="72aab-174">Veri ve model tanımlar</span><span class="sxs-lookup"><span data-stu-id="72aab-174">Define data and model paths</span></span>

<span data-ttu-id="72aab-175">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="72aab-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="72aab-176">Veri kümeleri ile dosya ve model ve için genel bir değişkendir kaydedileceği dosyayı yolları tutmak için üç alanı oluşturmak için ihtiyacınız `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="72aab-176">You need to create three fields to hold the paths to the files with data sets and the file to save the model, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="72aab-177">`_trainDataPath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="72aab-177">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="72aab-178">`_testDataPath` model değerlendirmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="72aab-178">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="72aab-179">`_modelPath` eğitilen modelin depolandığı dosya yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="72aab-179">`_modelPath` contains the path to the file where the trained model is stored.</span></span>
* <span data-ttu-id="72aab-180">`_textLoader` olan <xref:Microsoft.ML.Data.TextLoader> yüklemek ve veri kümeleri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72aab-180">`_textLoader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="72aab-181">Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için ve `_textLoader` değişkeni:</span><span class="sxs-lookup"><span data-stu-id="72aab-181">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="72aab-182">ML.NET modeliyle oluştururken ML bağlam oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="72aab-182">When building a model with ML.NET you start by creating an ML Context.</span></span> <span data-ttu-id="72aab-183">Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="72aab-183">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="72aab-184">Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilmesi için machine learning işiniz için bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="72aab-184">The environment provides a context for your machine learning job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="72aab-185">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="72aab-185">Initialize variables in Main</span></span>

<span data-ttu-id="72aab-186">Adlı bir değişken oluşturma `mlContext` ve yeni bir örneğini ile başlatma `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="72aab-186">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="72aab-187">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="72aab-187">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="72aab-188">Sonra Kurulum başlatma veri yükleme için `_textLoader` yeniden kullanmak için genel değişkeni.</span><span class="sxs-lookup"><span data-stu-id="72aab-188">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span>  <span data-ttu-id="72aab-189">Kullanıyoruz bildirimi bir `TextReader`.</span><span class="sxs-lookup"><span data-stu-id="72aab-189">Notice that we are using a `TextReader`.</span></span> <span data-ttu-id="72aab-190">Oluşturduğunuzda, bir `TextLoader` kullanarak bir `TextReader`, gerekli bağlamı geçirdiğiniz ve <xref:Microsoft.ML.Data.TextLoader.Arguments> özelleştirme sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="72aab-190">When you create a `TextLoader` using a `TextReader`, you pass in the context needed and the <xref:Microsoft.ML.Data.TextLoader.Arguments> class which enables customization.</span></span> <span data-ttu-id="72aab-191">Bir dizi geçirerek veri şemasını belirtin <xref:Microsoft.ML.Data.TextLoader.Column> nesneleri için `TextReader` tüm sütun adlarını ve türlerini içeren.</span><span class="sxs-lookup"><span data-stu-id="72aab-191">Specify the data schema by passing an array of <xref:Microsoft.ML.Data.TextLoader.Column> objects to the `TextReader` containing all the column names and their types.</span></span> <span data-ttu-id="72aab-192">Oluşturduğumuz zaman veri şemasını daha önce tanımladığımız bizim `TaxiTrip` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="72aab-192">We defined the data schema previously when we created our `TaxiTrip` class.</span></span>

<span data-ttu-id="72aab-193">`TextReader` Sınıf tam olarak başlatılmış döndürür <xref:Microsoft.ML.Data.TextLoader></span><span class="sxs-lookup"><span data-stu-id="72aab-193">The `TextReader` class returns a fully initialized <xref:Microsoft.ML.Data.TextLoader></span></span>  

<span data-ttu-id="72aab-194">Başlatmak için `_textLoader` gerekli veri kümeleri için yeniden kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:</span><span class="sxs-lookup"><span data-stu-id="72aab-194">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Initialize the TextLoader")]

<span data-ttu-id="72aab-195">Sonraki kod satırı olarak ekleyin `Main` çağrılacak yöntem `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="72aab-195">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="72aab-196">`Train` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="72aab-196">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="72aab-197">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="72aab-197">Loads the data.</span></span>
* <span data-ttu-id="72aab-198">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="72aab-198">Extracts and transforms the data.</span></span>
* <span data-ttu-id="72aab-199">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="72aab-199">Trains the model.</span></span>
* <span data-ttu-id="72aab-200">Model .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="72aab-200">Saves the model as .zip file.</span></span>
* <span data-ttu-id="72aab-201">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="72aab-201">Returns the model.</span></span>

<span data-ttu-id="72aab-202">`Train` Yöntemi modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="72aab-202">The `Train` method trains the model.</span></span> <span data-ttu-id="72aab-203">Bu yöntem oluşturma hemen altına `Main`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="72aab-203">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="72aab-204">İki parametre olarak geçiriyoruz `Train` yöntemi; bir `MLContext` bağlamının (`mlContext`) ve veri kümesi yolu için bir dize (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="72aab-204">We are passing two parameters into the `Train` method; an `MLContext` for the context (`mlContext`), and a string for the dataset path (`dataPath`).</span></span> <span data-ttu-id="72aab-205">Veri kümelerini yüklemek için bu yöntem yeniden oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="72aab-205">We're going to reuse this method for loading datasets.</span></span>

## <a name="load-and-transform-data"></a><span data-ttu-id="72aab-206">Veri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="72aab-206">Load and transform data</span></span>

<span data-ttu-id="72aab-207">Biz kullanarak verileri yüklemek `_textLoader` genel değişkenin `dataPath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="72aab-207">We'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="72aab-208">Döndürür bir <xref:Microsoft.ML.Data.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="72aab-208">It returns a <xref:Microsoft.ML.Data.IDataView>.</span></span> <span data-ttu-id="72aab-209">Giriş ve çıkış, Dönüşümlerin bir `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="72aab-209">As the input and output of Transforms, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="72aab-210">ML.NET veriler SQL görünümüne benzer.</span><span class="sxs-lookup"><span data-stu-id="72aab-210">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="72aab-211">Bu, gevşek değerlendirilen, şema ve heterojen olur.</span><span class="sxs-lookup"><span data-stu-id="72aab-211">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="72aab-212">Nesne, işlem hattını ilk kısmı ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="72aab-212">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="72aab-213">Bu öğreticide, taksi seyahat bilgileri fares tahmin etmek kullanışlı bir veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="72aab-213">For this tutorial, it loads a dataset with taxi trip information useful to predict fares.</span></span> <span data-ttu-id="72aab-214">Bu model oluşturmayı ve bunu eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72aab-214">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="72aab-215">İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="72aab-215">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="72aab-216">Sonraki adımlarda sütunlara adlarıyla tanımlanan diyoruz `TaxiTrip` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="72aab-216">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="72aab-217">Model eğitim ve diğer değerleri varsayılan olarak, hesaplanan zaman **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="72aab-217">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="72aab-218">Taksi seyahat taksi tahmin etmek istediğimiz gibi kopyalayın `FareAmount` sütuna **etiket** sütun.</span><span class="sxs-lookup"><span data-stu-id="72aab-218">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="72aab-219">Bunu yapmak için kullanın `CopyColumnsEstimator` dönüştürme sınıfı ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72aab-219">To do that, use the `CopyColumnsEstimator` transformation class, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="72aab-220">Modeli eğitir algoritması **sayısal** kategorik verileri dönüştürmek zorunda özellikleri (`VendorId`, `RateCode`, ve `PaymentType`) içine numaraları değerleri.</span><span class="sxs-lookup"><span data-stu-id="72aab-220">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="72aab-221">Bunu yapmak için kullanın `OneHotEncodingEstimator` atayan farklı sayısal dönüştürme sınıfına anahtar sütunları farklı değerlerle değerlerini ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72aab-221">To do that, use the `OneHotEncodingEstimator` transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="72aab-222">Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak `ColumnConcatenatingEstimator` dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="72aab-222">The last step in data preparation combines all of the feature columns into the **Features** column using the `ColumnConcatenatingEstimator` transformation class.</span></span> <span data-ttu-id="72aab-223">Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="72aab-223">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="72aab-224">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72aab-224">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="72aab-225">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="72aab-225">Choose a learning algorithm</span></span>

<span data-ttu-id="72aab-226">Veri ardışık düzenine eklemek ve giriş doğru biçime dönüştürme sonra bir öğrenme algoritması seçiyoruz (**learner**).</span><span class="sxs-lookup"><span data-stu-id="72aab-226">After adding the data to the pipeline and transforming it into the correct input format, we select a learning algorithm (**learner**).</span></span> <span data-ttu-id="72aab-227">Learner modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="72aab-227">The learner trains the model.</span></span> <span data-ttu-id="72aab-228">Seçtik bir **regresyon** görev kullanacağız Bu sorun için bir `FastTreeRegressionTrainer` ML.NET tarafından sağlanan regresyon öğrencileriyle biri olan learner.</span><span class="sxs-lookup"><span data-stu-id="72aab-228">We chose a **regression** task for this problem, so we use a `FastTreeRegressionTrainer` learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="72aab-229">`FastTreeRegressionTrainer` Learner gradyan artırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="72aab-229">The `FastTreeRegressionTrainer` learner utilizes gradient boosting.</span></span> <span data-ttu-id="72aab-230">Gradyan artırma bir machine learning teknik regresyon sorunları var.</span><span class="sxs-lookup"><span data-stu-id="72aab-230">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="72aab-231">Bu, her regresyon ağaç tarafınızdaki bir biçimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72aab-231">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="72aab-232">Her adımda hata oluştu ölçmenizi ve sonraki düzeltmek için önceden tanımlanmış kaybı işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="72aab-232">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="72aab-233">Aslında bir topluluğu, tahmin modellerini daha zayıf bir tahmin modeli sonucudur.</span><span class="sxs-lookup"><span data-stu-id="72aab-233">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="72aab-234">Gradyan artırma hakkında daha fazla bilgi için bkz. [artırılmış karar ağacı regresyonu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="72aab-234">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="72aab-235">Aşağıdaki kodu ekleyin `Train` ekleme yöntemi `FastTreeRegressionTrainer` önceki adımda eklenen veri işleme kodu:</span><span class="sxs-lookup"><span data-stu-id="72aab-235">Add the following code into the `Train` method to add the `FastTreeRegressionTrainer` to the data processing code added in the previous step:</span></span>

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="72aab-236">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="72aab-236">Train the model</span></span>

<span data-ttu-id="72aab-237">Modeli eğitmek için son adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="72aab-237">The final step is to train the model.</span></span> <span data-ttu-id="72aab-238">Biz modeli eğitmek <xref:Microsoft.ML.Data.TransformerChain>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="72aab-238">We train the model, <xref:Microsoft.ML.Data.TransformerChain>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="72aab-239">Tahmin tanımlandıktan sonra kullanarak modeli eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> zaten yüklenmiş eğitim verilerini sağlayarak.</span><span class="sxs-lookup"><span data-stu-id="72aab-239">Once the estimator has been defined, we train the model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="72aab-240">Bu tahminler elde etmek için kullanılacak bir modelini döndürür.</span><span class="sxs-lookup"><span data-stu-id="72aab-240">This returns a model to use for predictions.</span></span> <span data-ttu-id="72aab-241">`pipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi.</span><span class="sxs-lookup"><span data-stu-id="72aab-241">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="72aab-242">Denemeyi böyle kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="72aab-242">The experiment is not executed until this happens.</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="72aab-243">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="72aab-243">And that's it!</span></span> <span data-ttu-id="72aab-244">Başarıyla bir makine öğrenimi taksi fares NYC içinde tahmin edebilen bir model eğitim.</span><span class="sxs-lookup"><span data-stu-id="72aab-244">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="72aab-245">Şimdi şimdi modelin nasıl doğru olup olmadığını anlamak için göz atın ve taksi taksi değerleri tahmin etmek için kullanmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="72aab-245">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="72aab-246">Modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="72aab-246">Save the model</span></span>

<span data-ttu-id="72aab-247">Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine.</span><span class="sxs-lookup"><span data-stu-id="72aab-247">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="72aab-248">Model bir .zip dosyası olarak kaydetmek için aşağıdaki kodu ekleyin sonunda `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="72aab-248">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="72aab-249">Bir .zip dosyası olarak modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="72aab-249">Save the model as a .zip file</span></span>

<span data-ttu-id="72aab-250">Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `Train` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="72aab-250">Create the `SaveModelAsFile` method, just after the `Train` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="72aab-251">`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="72aab-251">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="72aab-252">Model bir .zip dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="72aab-252">Saves the model as a .zip file.</span></span>

<span data-ttu-id="72aab-253">Modeli yeniden ve diğer uygulamalarda kullanılan üzere kaydetmek için bir yöntem için oluşturmamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="72aab-253">We need to create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="72aab-254">`ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="72aab-254">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="72aab-255">Bu zip dosyası olarak kaydetmek istediğimiz beri oluşturacağız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="72aab-255">Since we want to save this as a zip file, we'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="72aab-256">Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="72aab-256">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

<span data-ttu-id="72aab-257">Biz burada dosyanın bir konsol iletisi ile yazarak yazılmıştır görüntüleyebilir `_modelPath`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="72aab-257">We could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="72aab-258">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="72aab-258">Evaluate the model</span></span>

<span data-ttu-id="72aab-259">Değerlendirme model etiket değerlerini ne kadar iyi tahmin denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="72aab-259">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="72aab-260">Model modeli eğitmek için kullanılmayan verileri iyi tahminler yapar önemlidir.</span><span class="sxs-lookup"><span data-stu-id="72aab-260">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="72aab-261">Bu öğreticide işlendiğinden bunu yapmanın bir yolu, verileri eğitim ve test veri kümesi bölme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="72aab-261">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="72aab-262">Eğitim verileri modeli eğittiğimize göre test verileri ne kadar iyi gerçekleştirdiği görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72aab-262">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="72aab-263">`Evaluate` Yöntemi modeli değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="72aab-263">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="72aab-264">Bu yöntem oluşturmak için aşağıdaki kodu ekleyin. `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="72aab-264">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
<span data-ttu-id="72aab-265">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="72aab-265">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="72aab-266">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="72aab-266">Loads the test dataset.</span></span>
* <span data-ttu-id="72aab-267">Regresyon değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72aab-267">Creates the regression evaluator.</span></span>
* <span data-ttu-id="72aab-268">Model değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72aab-268">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="72aab-269">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72aab-269">Displays the metrics.</span></span>

<span data-ttu-id="72aab-270">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="72aab-270">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="72aab-271">Daha önce başlatılmış kullanarak test veri kümesini yüklediğimiz `_textLoader` genel değişkenin `_testDataPath` genel alan.</span><span class="sxs-lookup"><span data-stu-id="72aab-271">We'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="72aab-272">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="72aab-272">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="72aab-273">Aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="72aab-273">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="72aab-274">Ardından, makine öğrenimi kullanacağız `model` özellikleri giriş ve tahmin döndürmek için parametre (dönüştürücü).</span><span class="sxs-lookup"><span data-stu-id="72aab-274">Next, we'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="72aab-275">Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="72aab-275">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="72aab-276">`RegressionContext.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma.</span><span class="sxs-lookup"><span data-stu-id="72aab-276">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="72aab-277">Döndürür bir <xref:Microsoft.ML.Data.RegressionMetrics> regresyon değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="72aab-277">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> <span data-ttu-id="72aab-278">Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="72aab-278">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="72aab-279">Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="72aab-279">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="72aab-280">Modeli değerlendirme ve değerlendirme ölçümleri üretmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72aab-280">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="72aab-281">[RSquared](../resources/glossary.md#coefficient-of-determination) regresyon modelleri, başka bir değerlendirme unsurdur.</span><span class="sxs-lookup"><span data-stu-id="72aab-281">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="72aab-282">RSquared 0 ile 1 arasındaki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="72aab-282">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="72aab-283">Daha değerini 1 olarak daha iyi modelidir yakınız.</span><span class="sxs-lookup"><span data-stu-id="72aab-283">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="72aab-284">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RSquared değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="72aab-284">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="72aab-285">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) gerileme modelini değerlendirme ölçümlerini biridir.</span><span class="sxs-lookup"><span data-stu-id="72aab-285">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="72aab-286">Daha düşük olan, daha iyi modelidir.</span><span class="sxs-lookup"><span data-stu-id="72aab-286">The lower it is, the better the model is.</span></span> <span data-ttu-id="72aab-287">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RMS değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="72aab-287">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="72aab-288">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="72aab-288">Use the model for predictions</span></span>


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a><span data-ttu-id="72aab-289">Model ve tek bir yorum ile test veri sonucu tahmin edin</span><span class="sxs-lookup"><span data-stu-id="72aab-289">Predict the test data outcome with the model and a single comment</span></span>

<span data-ttu-id="72aab-290">Oluşturma `TestSinglePrediction` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="72aab-290">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

<span data-ttu-id="72aab-291">`TestSinglePrediction` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="72aab-291">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="72aab-292">Test verilerini tek bir yorum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72aab-292">Creates a single comment of test data.</span></span>
* <span data-ttu-id="72aab-293">Test verilerini temel alarak taksi miktarı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="72aab-293">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="72aab-294">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="72aab-294">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="72aab-295">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72aab-295">Displays the predicted results.</span></span>

<span data-ttu-id="72aab-296">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="72aab-296">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="72aab-297">Modeli zip dosyasından yükleme istiyoruz beri kaydettik, oluşturacağız `FileStream` çağırmadan önce hemen `Load` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="72aab-297">Since we want to load the model from the zip file we saved, we'll create the `FileStream` immediately before calling the `Load` method.</span></span> <span data-ttu-id="72aab-298">Aşağıdaki kodu ekleyin `TestSinglePrediction` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="72aab-298">Add the following code to the `TestSinglePrediction` method as the next line:</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

<span data-ttu-id="72aab-299">Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="72aab-299">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="72aab-300"><xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="72aab-300">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="72aab-301">Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` ilk satırı olarak `Predict` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="72aab-301">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
<span data-ttu-id="72aab-302">Bu öğretici, bu sınıf içinde bir test seyahat kullanır.</span><span class="sxs-lookup"><span data-stu-id="72aab-302">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="72aab-303">Daha sonra modeli denemek için diğer senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72aab-303">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="72aab-304">Eğitilen modelin Maliyet tahminini test etmek için bir seyahat ekleme `Predict` bir örneğini oluşturarak yöntemi `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="72aab-304">Add a trip to test the trained model's prediction of cost in the `Predict` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 <span data-ttu-id="72aab-305">Biz taksi seyahat verilerini tek bir örneği temel taksi tahmin etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72aab-305">We can use that to predict the fare based on a single instance of the taxi trip data.</span></span> <span data-ttu-id="72aab-306">Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri.</span><span class="sxs-lookup"><span data-stu-id="72aab-306">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="72aab-307">Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="72aab-307">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="72aab-308">İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="72aab-308">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="72aab-309">Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.</span><span class="sxs-lookup"><span data-stu-id="72aab-309">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="72aab-310">Belirtilen seyahat, tahmin edilen taksi görüntülemek için aşağıdaki kodu ekleyin. `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="72aab-310">To display the predicted fare of the specified trip, add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="72aab-311">Test durumunuz için tahmin edilen taksi taksi görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72aab-311">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="72aab-312">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="72aab-312">Congratulations!</span></span> <span data-ttu-id="72aab-313">Başarıyla taksi seyahat fares tahmin etmeye yönelik bir machine learning modeli, doğruluğunun değerlendirilir, derleyip tahminlerde bulunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72aab-313">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="72aab-314">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="72aab-314">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="72aab-315">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="72aab-315">Next steps</span></span>

<span data-ttu-id="72aab-316">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="72aab-316">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="72aab-317">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="72aab-317">Understand the problem</span></span>
> * <span data-ttu-id="72aab-318">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="72aab-318">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="72aab-319">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="72aab-319">Prepare and understand the data</span></span>
> * <span data-ttu-id="72aab-320">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="72aab-320">Create a learning pipeline</span></span>
> * <span data-ttu-id="72aab-321">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="72aab-321">Load and transform the data</span></span>
> * <span data-ttu-id="72aab-322">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="72aab-322">Choose a learning algorithm</span></span>
> * <span data-ttu-id="72aab-323">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="72aab-323">Train the model</span></span>
> * <span data-ttu-id="72aab-324">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="72aab-324">Evaluate the model</span></span>
> * <span data-ttu-id="72aab-325">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="72aab-325">Use the model for predictions</span></span>

<span data-ttu-id="72aab-326">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="72aab-326">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="72aab-327">Iris kümelemesi</span><span class="sxs-lookup"><span data-stu-id="72aab-327">Iris clustering</span></span>](iris-clustering.md)
