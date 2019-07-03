---
title: Regresyon modeli Oluşturucu ile kullanarak fiyatlarını tahmin etme
description: Bu öğreticide ML.NET Model Fiyatlar, özellikle tahmin etmek için oluşturucu oturan taksi fares kullanarak bir regresyon modeli derler gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9a6f193d877fc1a679b7a3cafd7491e021cb2ad
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539627"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="12aeb-103">Regresyon modeli Oluşturucu ile kullanarak fiyatlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="12aeb-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="12aeb-104">ML.NET Model Oluşturucu oluşturmak için kullanmayı öğrenin bir [regresyon modeli](../resources/glossary.md#regression) fiyatlarını tahmin etmek için.</span><span class="sxs-lookup"><span data-stu-id="12aeb-104">Learn how to use ML.NET Model Builder to build a [regression model](../resources/glossary.md#regression) to predict prices.</span></span>  <span data-ttu-id="12aeb-105">Bu öğreticide geliştirdiğiniz .NET konsol uygulaması taksi fares geçmiş New York taksi taksi verilerini temel alarak tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="12aeb-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="12aeb-106">Model Oluşturucu fiyatı tahmin şablon sayısal tahmin değeri gerektiren her senaryo için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="12aeb-107">Örnek senaryoları şunları içerir: barındırmak fiyat tahmini, Talep tahmini ve satış tahmini.</span><span class="sxs-lookup"><span data-stu-id="12aeb-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="12aeb-108">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="12aeb-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="12aeb-109">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="12aeb-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="12aeb-110">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="12aeb-110">Choose a scenario</span></span>
> * <span data-ttu-id="12aeb-111">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="12aeb-111">Load the data</span></span>
> * <span data-ttu-id="12aeb-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="12aeb-112">Train the model</span></span>
> * <span data-ttu-id="12aeb-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="12aeb-113">Evaluate the model</span></span>
> * <span data-ttu-id="12aeb-114">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="12aeb-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="12aeb-115">Model Oluşturucu şu anda Önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="12aeb-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="12aeb-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="12aeb-116">Pre-requisites</span></span>

<span data-ttu-id="12aeb-117">Önkoşullar ve yükleme yönergeleri bir listesi için ziyaret edin [Model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="12aeb-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="12aeb-118">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="12aeb-118">Create a console application</span></span>

1. <span data-ttu-id="12aeb-119">Oluşturma bir **.NET Core konsol uygulaması** "TaxiFarePrediction" denir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="12aeb-120">Yükleme **Microsoft.ML** NuGet paketi:</span><span class="sxs-lookup"><span data-stu-id="12aeb-120">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="12aeb-121">İçinde **Çözüm Gezgini**, sağ *TaxiFarePrediction* seçin ve proje **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="12aeb-121">In **Solution Explorer**, right-click the *TaxiFarePrediction* project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="12aeb-122">Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listeden bir paket seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="12aeb-122">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="12aeb-123">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="12aeb-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="12aeb-124">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="12aeb-124">Prepare and understand the data</span></span>

1. <span data-ttu-id="12aeb-125">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyaları depolamak için.</span><span class="sxs-lookup"><span data-stu-id="12aeb-125">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="12aeb-126">İndirme [taksi taksi train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) veri kümesi ve kaydetmesi *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="12aeb-126">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) data set and save it to the *Data* folder you created at the previous step.</span></span> <span data-ttu-id="12aeb-127">Bu veri kümesi, eğitmek ve machine learning modeli değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12aeb-127">This data set is used to train and evaluate the machine learning model.</span></span> <span data-ttu-id="12aeb-128">Bu veri kümesi başlangıçta dandır [NYC TLC taksi seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="12aeb-128">This data set is originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="12aeb-129">İçinde **Çözüm Gezgini**, sağ *taksi taksi train.csv* seçin ve dosya **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="12aeb-129">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="12aeb-130">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="12aeb-130">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="12aeb-131">Her satırda `taxi-fare-train.csv` veri kümesi bir taksi tarafından yapılan gelişlerin ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-131">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="12aeb-132">Açık **taksi taksi train.csv** veri kümesi</span><span class="sxs-lookup"><span data-stu-id="12aeb-132">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="12aeb-133">Sağlanan veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="12aeb-133">The provided data set contains the following columns:</span></span>

    * <span data-ttu-id="12aeb-134">**vendor_id:** Taksi satıcı kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    * <span data-ttu-id="12aeb-135">**rate_code:** Taksi dönüş oranı türünü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    * <span data-ttu-id="12aeb-136">**passenger_count:** Bir özellik Yolcuların seyahat üzerinde sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="12aeb-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    * <span data-ttu-id="12aeb-137">**trip_time_in_secs:** Seyahat geçen süre miktarı.</span><span class="sxs-lookup"><span data-stu-id="12aeb-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="12aeb-138">Seyahat, taksi seyahat tamamlanmadan önce tahmin etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="12aeb-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="12aeb-139">Bu ne kadar seyahat bilmiyorum dakikamızı ayıralım.</span><span class="sxs-lookup"><span data-stu-id="12aeb-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="12aeb-140">Bu nedenle, seyahat süresi, bir özellik değildir ve bu sütunu modelden dışında bırakacağız.</span><span class="sxs-lookup"><span data-stu-id="12aeb-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    * <span data-ttu-id="12aeb-141">**trip_distance:** Seyahat mesafesini bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-141">**trip_distance:** The distance of the trip is a feature.</span></span>
    * <span data-ttu-id="12aeb-142">**payment_type:** Ödeme yöntemini (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    * <span data-ttu-id="12aeb-143">**fare_amount:** Ücretli toplam taksi taksi etiketi olur.</span><span class="sxs-lookup"><span data-stu-id="12aeb-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="12aeb-144">`label` Tahmin etmek istediğiniz sütun.</span><span class="sxs-lookup"><span data-stu-id="12aeb-144">The `label` is the column you want to predict.</span></span> <span data-ttu-id="12aeb-145">Bir regresyon görevi gerçekleştirirken, sayısal bir değer tahmin hedeftir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-145">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="12aeb-146">Bu fiyat tahmini senaryoda taksi kılma maliyetini tahmin edildiğinde.</span><span class="sxs-lookup"><span data-stu-id="12aeb-146">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="12aeb-147">Bu nedenle, **fare_amount** etiketidir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-147">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="12aeb-148">Tanımlanan `features` modeli tahmin etmek için size girişleri `label`.</span><span class="sxs-lookup"><span data-stu-id="12aeb-148">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="12aeb-149">Bu durumda, geri kalan sütunların özellikleri veya girişleri olarak taksi miktarı tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12aeb-149">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="12aeb-150">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="12aeb-150">Choose a scenario</span></span>

<span data-ttu-id="12aeb-151">Modelinizi eğitmek için kullanılabilir makine öğrenme modeli oluşturucusu tarafından sağlanan senaryolar listesinden seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-151">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="12aeb-152">Bu durumda, senaryodur `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="12aeb-152">In this case, the scenario is `Price Prediction`.</span></span> <span data-ttu-id="12aeb-153">Daha kapsamlı bir liste için ziyaret edin [Model Oluşturucu genel bakış makalesi](../automate-training-with-model-builder.md#scenarios).</span><span class="sxs-lookup"><span data-stu-id="12aeb-153">For a more extensive list visit the [Model Builder overview article](../automate-training-with-model-builder.md#scenarios).</span></span>

1. <span data-ttu-id="12aeb-154">İçinde **Çözüm Gezgini**, sağ *TaxiFarePrediction* proje ve seçin **Ekle** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="12aeb-154">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="12aeb-155">Model Oluşturucu aracı senaryo adımda seçin *fiyat tahmini* senaryo.</span><span class="sxs-lookup"><span data-stu-id="12aeb-155">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="12aeb-156">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="12aeb-156">Load the data</span></span>

<span data-ttu-id="12aeb-157">Model Oluşturucu verileri iki kaynağı, bir SQL Server veritabanı veya bir yerel dosya csv veya tsv dosyasını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="12aeb-157">Model Builder accepts data from two sources, a SQL Server database or a local file csv or tsv file.</span></span> <span data-ttu-id="12aeb-158">Aşağıdaki veri biçimi gereksinimleri hakkında daha fazla bilgi için ziyaret [bağlantı](../how-to-guides/install-model-builder.md#limitations).</span><span class="sxs-lookup"><span data-stu-id="12aeb-158">For more information on data format requirements, visit the following [link](../how-to-guides/install-model-builder.md#limitations).</span></span>

1. <span data-ttu-id="12aeb-159">Model Oluşturucu aracı verileri adımda seçin *dosya* veri kaynağı açılır listeden.</span><span class="sxs-lookup"><span data-stu-id="12aeb-159">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="12aeb-160">Düğmeyi seçin *bir dosya seçin* metin kutusu ve kullanım ve seçmek için dosya Gezgini'ni *taksi taksi test.csv* içinde *veri* dizini</span><span class="sxs-lookup"><span data-stu-id="12aeb-160">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="12aeb-161">Seçin *fare_amount* içinde *etiket veya Predıct sütun* açılır ve Model Oluşturucu aracı train adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="12aeb-161">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="12aeb-162">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="12aeb-162">Train the model</span></span>

<span data-ttu-id="12aeb-163">Bu öğreticide fiyatı tahmin modeli eğitmek için kullanılan görev öğrenme regresyon makinedir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-163">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="12aeb-164">Model eğitimi işlemi sırasında en iyi performansa sahip veri kümeniz için model bulmak için farklı bir regresyon algoritmaları ve ayarları'nı kullanarak ayrı modeller Model Oluşturucu eğitir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-164">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="12aeb-165">Modeli eğitmek gereken süreyi veri miktarı için uygun.</span><span class="sxs-lookup"><span data-stu-id="12aeb-165">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="12aeb-166">Bu grafik için yeterli bir değer seçmek için kılavuz kullanın. `Time to train (seconds)` alan:</span><span class="sxs-lookup"><span data-stu-id="12aeb-166">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="12aeb-167">\* Veri kümesi boyutu</span><span class="sxs-lookup"><span data-stu-id="12aeb-167">\*Dataset Size</span></span>  | <span data-ttu-id="12aeb-168">Veri kümesi türü</span><span class="sxs-lookup"><span data-stu-id="12aeb-168">Dataset Type</span></span>       | <span data-ttu-id="12aeb-169">Ort. Eğitimi \* süresi</span><span class="sxs-lookup"><span data-stu-id="12aeb-169">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="12aeb-170">0 - 10 mb</span><span class="sxs-lookup"><span data-stu-id="12aeb-170">0 - 10 Mb</span></span>     | <span data-ttu-id="12aeb-171">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="12aeb-171">Numeric and Text</span></span>   | <span data-ttu-id="12aeb-172">10 saniye</span><span class="sxs-lookup"><span data-stu-id="12aeb-172">10 sec</span></span>
<span data-ttu-id="12aeb-173">10 - 100 mb</span><span class="sxs-lookup"><span data-stu-id="12aeb-173">10 - 100 Mb</span></span>   | <span data-ttu-id="12aeb-174">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="12aeb-174">Numeric and Text</span></span>   | <span data-ttu-id="12aeb-175">10 dakikalık</span><span class="sxs-lookup"><span data-stu-id="12aeb-175">10 min</span></span>
<span data-ttu-id="12aeb-176">100 - 500 mb</span><span class="sxs-lookup"><span data-stu-id="12aeb-176">100 - 500 Mb</span></span>  | <span data-ttu-id="12aeb-177">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="12aeb-177">Numeric and Text</span></span>   | <span data-ttu-id="12aeb-178">30 dakika</span><span class="sxs-lookup"><span data-stu-id="12aeb-178">30 min</span></span>
<span data-ttu-id="12aeb-179">500 - 1 Gb</span><span class="sxs-lookup"><span data-stu-id="12aeb-179">500 - 1 Gb</span></span>    | <span data-ttu-id="12aeb-180">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="12aeb-180">Numeric and Text</span></span>   | <span data-ttu-id="12aeb-181">60 dk önce</span><span class="sxs-lookup"><span data-stu-id="12aeb-181">60 min</span></span>
<span data-ttu-id="12aeb-182">1 Gb+</span><span class="sxs-lookup"><span data-stu-id="12aeb-182">1 Gb+</span></span>         | <span data-ttu-id="12aeb-183">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="12aeb-183">Numeric and Text</span></span>   | <span data-ttu-id="12aeb-184">3 saat +</span><span class="sxs-lookup"><span data-stu-id="12aeb-184">3 hour+</span></span>

1. <span data-ttu-id="12aeb-185">Eğitim verileri dosyası 10 MB'tan fazla olduğundan, 600 saniye (10 dakika) değeri olarak kullanın *süresi (saniye) eğitmek için*.</span><span class="sxs-lookup"><span data-stu-id="12aeb-185">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="12aeb-186">Seçin *eğitim Başlat*.</span><span class="sxs-lookup"><span data-stu-id="12aeb-186">Select *Start Training*.</span></span>

<span data-ttu-id="12aeb-187">Eğitim işlem boyunca ilerleme veri görüntülenen `Progress` eğitimi adım bölümü.</span><span class="sxs-lookup"><span data-stu-id="12aeb-187">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="12aeb-188">Durum eğitim işleminin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12aeb-188">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="12aeb-189">En yüksek doğruluğa en iyi performansa sahip Model Oluşturucu bulundu modelinin doğruluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12aeb-189">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="12aeb-190">Daha yüksek doğruluk testi veri daha doğru bir şekilde tahmin modeli anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-190">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="12aeb-191">En iyi algoritmayı bulundu modelinin oluşturucusu tarafından gerçekleştirilen en iyi performansa algoritma adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12aeb-191">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="12aeb-192">Son algoritması, en son Model Oluşturucu, modeli eğitmek için kullanılan algoritma adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12aeb-192">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="12aeb-193">Alıştırma tamamlandıktan sonra değerlendir adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="12aeb-193">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="12aeb-194">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="12aeb-194">Evaluate the model</span></span>

<span data-ttu-id="12aeb-195">En iyi performansı sahip bir model eğitimi adım olacaktır.</span><span class="sxs-lookup"><span data-stu-id="12aeb-195">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="12aeb-196">Model Oluşturucu aracı değerlendir adımda çıkış bölümüne en iyi performansa sahip modeli tarafından kullanılan algoritmayı içerecek *en iyi modeli* ölçümlerde yanı sıra giriş *en iyi Model kalitesi (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="12aeb-196">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="12aeb-197">İlk beş modelleri ve bunların ölçümleri içeren ek olarak, bir Özet Tablosu.</span><span class="sxs-lookup"><span data-stu-id="12aeb-197">Additionally, a summary table containing top five models and their metrics.</span></span> <span data-ttu-id="12aeb-198">Hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı ziyaret edin [model ölçümlerini değerlendirme](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span><span class="sxs-lookup"><span data-stu-id="12aeb-198">Visit the following link to learn more about [evaluating model metrics](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span></span>

<span data-ttu-id="12aeb-199">Doğruluk ölçümlerinizi memnun değilseniz, deneyin ve doğruluğu artırmak için bazı kolay veya daha fazla veri modeli eğitme süre miktarını artırmak için yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="12aeb-199">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="12aeb-200">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="12aeb-200">Use the model for predictions</span></span>

<span data-ttu-id="12aeb-201">İki proje eğitim işleminin sonucu olarak oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="12aeb-201">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="12aeb-202">TaxiFarePredictionML.ConsoleApp: Model eğitimi ve tüketim kodu içeren bir .NET konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="12aeb-202">TaxiFarePredictionML.ConsoleApp: A .NET Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="12aeb-203">TaxiFarePredictionML.Model: Giriş şemasını tanımlayan ve en iyi performansa sahip sırasında eğitim modeli kalıcı sürümünü yanı sıra model verileri çıkış veri modelleri içeren .NET Standard sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="12aeb-203">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="12aeb-204">Kod Model Oluşturucu aracının bölümünde **eklenen projeleri** projeleri çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="12aeb-204">In the code section of the Model Builder tool, select **Added Projects** to add the projects to the solution.</span></span>
2. <span data-ttu-id="12aeb-205">Çözüm Gezgini'nde sağ *TaxiFarePrediction* proje.</span><span class="sxs-lookup"><span data-stu-id="12aeb-205">In solution explorer, right-click the *TaxiFarePrediction* project.</span></span> <span data-ttu-id="12aeb-206">Ardından, **Ekle > var olan öğe**.</span><span class="sxs-lookup"><span data-stu-id="12aeb-206">Then, select **Add > Existing Item**.</span></span> <span data-ttu-id="12aeb-207">İçin dosya türü açılan listesinde seçin `All Files`, gitmek *TaxiFarePredictionML.Model* dizin ve select projeyi `MLModel.zip` dosya.</span><span class="sxs-lookup"><span data-stu-id="12aeb-207">For file type drop down, select `All Files`, navigate to the *TaxiFarePredictionML.Model* project directory and select the `MLModel.zip` file.</span></span> <span data-ttu-id="12aeb-208">Son eklenen'ı sağ `MLModel.zip` seçin ve dosya *özellikleri*.</span><span class="sxs-lookup"><span data-stu-id="12aeb-208">Then right-click the recently added `MLModel.zip` file and select *Properties*.</span></span> <span data-ttu-id="12aeb-209">Çıkış dizini seçeneğini Kopyala için *yeniyse Kopyala* açılır listeden.</span><span class="sxs-lookup"><span data-stu-id="12aeb-209">For the Copy to Output Directory option, select *Copy if Newer* from the dropdown.</span></span>
3. <span data-ttu-id="12aeb-210">Sağ *TaxiFarePrediction* proje.</span><span class="sxs-lookup"><span data-stu-id="12aeb-210">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="12aeb-211">Ardından, **Ekle > başvuru**.</span><span class="sxs-lookup"><span data-stu-id="12aeb-211">Then, **Add > Reference**.</span></span> <span data-ttu-id="12aeb-212">Seçin **projeleri > Çözüm** düğüm ve listeden *TaxiFarePredictionML.Model* proje ve Tamam'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="12aeb-212">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>

4. <span data-ttu-id="12aeb-213">Açık *Program.cs* dosyası *TaxiFarePrediction* proje.</span><span class="sxs-lookup"><span data-stu-id="12aeb-213">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
5. <span data-ttu-id="12aeb-214">Aşağıdaki using deyimlerini:</span><span class="sxs-lookup"><span data-stu-id="12aeb-214">Add the following using statements:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. <span data-ttu-id="12aeb-215">Ekleme `ConsumeModel` yönteme `Program` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12aeb-215">Add the `ConsumeModel` method to the `Program` class.</span></span> <span data-ttu-id="12aeb-216">`ConsumeModel` Oluşturacak bir `PredictionEngine` yeni veri tahminlerde bulunabilir ve konsola yazdırmanız için Model Oluşturucu tarafından oluşturulan model göre.</span><span class="sxs-lookup"><span data-stu-id="12aeb-216">The `ConsumeModel` will create a `PredictionEngine` based on the model generated by Model Builder to make predictions on new data and print them out to the console.</span></span>

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

7. <span data-ttu-id="12aeb-217">Aşağıdaki kodu ekleyin `Main` yöntemi ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="12aeb-217">Add the following code to the `Main` method and run the application.</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    <span data-ttu-id="12aeb-218">Program tarafından oluşturulan çıktı kod parçacığını aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="12aeb-218">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="12aeb-219">Daha sonra başka bir çözüm içinde oluşturulan projeleri başvurmanız gerekiyorsa, içinde bulabilirsiniz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizin.</span><span class="sxs-lookup"><span data-stu-id="12aeb-219">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="12aeb-220">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="12aeb-220">Next Steps</span></span>

<span data-ttu-id="12aeb-221">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="12aeb-221">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="12aeb-222">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="12aeb-222">Prepare and understand the data</span></span>
> * <span data-ttu-id="12aeb-223">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="12aeb-223">Choose a scenario</span></span>
> * <span data-ttu-id="12aeb-224">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="12aeb-224">Load the data</span></span>
> * <span data-ttu-id="12aeb-225">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="12aeb-225">Train the model</span></span>
> * <span data-ttu-id="12aeb-226">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="12aeb-226">Evaluate the model</span></span>
> * <span data-ttu-id="12aeb-227">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="12aeb-227">Use the model for predictions</span></span>

<span data-ttu-id="12aeb-228">Modelinizi dağıtma hakkında bilgi edinmek için aşağıdaki nasıl yapılır makaleleri birini ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="12aeb-228">Advance to either of the following how-to articles to learn how to deploy your model.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="12aeb-229">Azure işlevleri için model dağıtma</span><span class="sxs-lookup"><span data-stu-id="12aeb-229">Deploy a model to Azure Functions</span></span>](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="12aeb-230">Bir Web API'si için model dağıtma</span><span class="sxs-lookup"><span data-stu-id="12aeb-230">Deploy a model to a Web API</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
