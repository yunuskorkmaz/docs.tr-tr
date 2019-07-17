---
title: Regresyon modeli Oluşturucu ile kullanarak fiyatlarını tahmin etme
description: Bu öğreticide ML.NET Model Fiyatlar, özellikle tahmin etmek için oluşturucu oturan taksi fares kullanarak bir regresyon modeli derler gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d8c901a10c91c8a6c16ca59516b633a99785ebac
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238562"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="195e9-103">Regresyon modeli Oluşturucu ile kullanarak fiyatlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="195e9-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="195e9-104">ML.NET Model Oluşturucu fiyatlarını tahmin etmek için regresyon model() oluşturmak için kullanmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="195e9-104">Learn how to use ML.NET Model Builder to build a regression model() to predict prices.</span></span>  <span data-ttu-id="195e9-105">Bu öğreticide geliştirdiğiniz .NET konsol uygulaması taksi fares geçmiş New York taksi taksi verilerini temel alarak tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="195e9-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="195e9-106">Model Oluşturucu fiyatı tahmin şablon sayısal tahmin değeri gerektiren her senaryo için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="195e9-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="195e9-107">Örnek senaryoları şunları içerir: barındırmak fiyat tahmini, Talep tahmini ve satış tahmini.</span><span class="sxs-lookup"><span data-stu-id="195e9-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="195e9-108">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="195e9-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="195e9-109">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="195e9-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="195e9-110">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="195e9-110">Choose a scenario</span></span>
> * <span data-ttu-id="195e9-111">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="195e9-111">Load the data</span></span>
> * <span data-ttu-id="195e9-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="195e9-112">Train the model</span></span>
> * <span data-ttu-id="195e9-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="195e9-113">Evaluate the model</span></span>
> * <span data-ttu-id="195e9-114">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="195e9-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="195e9-115">Model Oluşturucu şu anda Önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="195e9-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="195e9-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="195e9-116">Pre-requisites</span></span>

<span data-ttu-id="195e9-117">Önkoşullar ve yükleme yönergeleri bir listesi için ziyaret edin [Model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="195e9-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="195e9-118">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="195e9-118">Create a console application</span></span>

1. <span data-ttu-id="195e9-119">Oluşturma bir **.NET Core konsol uygulaması** "TaxiFarePrediction" denir.</span><span class="sxs-lookup"><span data-stu-id="195e9-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="195e9-120">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="195e9-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="195e9-121">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyaları depolamak için.</span><span class="sxs-lookup"><span data-stu-id="195e9-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="195e9-122">Veri eğitmek ve machine learning modeli değerlendirmek için kullanılan özgün NYC TLC taksi seyahat veri kümesinden kümesidir.</span><span class="sxs-lookup"><span data-stu-id="195e9-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span> 

    <span data-ttu-id="195e9-123">Veri kümesi indirmek için Git [taksi taksi train.csv indirme bağlantısı](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="195e9-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span> 
    
    <span data-ttu-id="195e9-124">Sayfa yüklendiğinde, herhangi bir sayfanın sağ tıklatın ve **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="195e9-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span> 
    
    <span data-ttu-id="195e9-125">Kullanım **Kaydet iletişim** dosyasına kaydetmek için *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="195e9-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span> 
    
1. <span data-ttu-id="195e9-126">İçinde **Çözüm Gezgini**, sağ *taksi taksi train.csv* seçin ve dosya **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="195e9-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="195e9-127">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="195e9-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="195e9-128">Her satırda `taxi-fare-train.csv` veri kümesi bir taksi tarafından yapılan gelişlerin ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="195e9-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="195e9-129">Açık **taksi taksi train.csv** veri kümesi</span><span class="sxs-lookup"><span data-stu-id="195e9-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="195e9-130">Sağlanan veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="195e9-130">The provided data set contains the following columns:</span></span>

    * <span data-ttu-id="195e9-131">**vendor_id:** Taksi satıcı kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="195e9-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    * <span data-ttu-id="195e9-132">**rate_code:** Taksi dönüş oranı türünü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="195e9-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    * <span data-ttu-id="195e9-133">**passenger_count:** Bir özellik Yolcuların seyahat üzerinde sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="195e9-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    * <span data-ttu-id="195e9-134">**trip_time_in_secs:** Seyahat geçen süre miktarı.</span><span class="sxs-lookup"><span data-stu-id="195e9-134">**trip_time_in_secs:** The amount of time the trip took.</span></span> 
    * <span data-ttu-id="195e9-135">**trip_distance:** Seyahat mesafesini bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="195e9-135">**trip_distance:** The distance of the trip is a feature.</span></span>
    * <span data-ttu-id="195e9-136">**payment_type:** Ödeme yöntemini (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="195e9-136">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    * <span data-ttu-id="195e9-137">**fare_amount:** Ücretli toplam taksi taksi etiketi olur.</span><span class="sxs-lookup"><span data-stu-id="195e9-137">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="195e9-138">`label` Tahmin etmek istediğiniz sütun.</span><span class="sxs-lookup"><span data-stu-id="195e9-138">The `label` is the column you want to predict.</span></span> <span data-ttu-id="195e9-139">Bir regresyon görevi gerçekleştirirken, sayısal bir değer tahmin hedeftir.</span><span class="sxs-lookup"><span data-stu-id="195e9-139">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="195e9-140">Bu fiyat tahmini senaryoda taksi kılma maliyetini tahmin edildiğinde.</span><span class="sxs-lookup"><span data-stu-id="195e9-140">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="195e9-141">Bu nedenle, **fare_amount** etiketidir.</span><span class="sxs-lookup"><span data-stu-id="195e9-141">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="195e9-142">Tanımlanan `features` modeli tahmin etmek için size girişleri `label`.</span><span class="sxs-lookup"><span data-stu-id="195e9-142">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="195e9-143">Bu durumda, geri kalan sütunların özellikleri veya girişleri olarak taksi miktarı tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="195e9-143">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="195e9-144">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="195e9-144">Choose a scenario</span></span>

<span data-ttu-id="195e9-145">Modelinizi eğitmek için kullanılabilir makine öğrenme modeli oluşturucusu tarafından sağlanan senaryolar listesinden seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="195e9-145">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="195e9-146">Bu durumda, senaryodur `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="195e9-146">In this case, the scenario is `Price Prediction`.</span></span> 

1. <span data-ttu-id="195e9-147">İçinde **Çözüm Gezgini**, sağ *TaxiFarePrediction* proje ve seçin **Ekle** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="195e9-147">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="195e9-148">Model Oluşturucu aracı senaryo adımda seçin *fiyat tahmini* senaryo.</span><span class="sxs-lookup"><span data-stu-id="195e9-148">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="195e9-149">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="195e9-149">Load the data</span></span>

<span data-ttu-id="195e9-150">Model Oluşturucu iki kaynağı, bir SQL Server veritabanı veya yerel bir dosya biçiminde, csv veya tsv verileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="195e9-150">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span> 

1. <span data-ttu-id="195e9-151">Model Oluşturucu aracı verileri adımda seçin *dosya* veri kaynağı açılır listeden.</span><span class="sxs-lookup"><span data-stu-id="195e9-151">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="195e9-152">Düğmeyi seçin *bir dosya seçin* metin kutusu ve kullanım ve seçmek için dosya Gezgini'ni *taksi taksi test.csv* içinde *veri* dizini</span><span class="sxs-lookup"><span data-stu-id="195e9-152">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="195e9-153">Seçin *fare_amount* içinde *etiket veya Predıct sütun* açılır ve Model Oluşturucu aracı train adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="195e9-153">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="195e9-154">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="195e9-154">Train the model</span></span>

<span data-ttu-id="195e9-155">Bu öğreticide fiyatı tahmin modeli eğitmek için kullanılan görev öğrenme regresyon makinedir.</span><span class="sxs-lookup"><span data-stu-id="195e9-155">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="195e9-156">Model eğitimi işlemi sırasında en iyi performansa sahip veri kümeniz için model bulmak için farklı bir regresyon algoritmaları ve ayarları'nı kullanarak ayrı modeller Model Oluşturucu eğitir.</span><span class="sxs-lookup"><span data-stu-id="195e9-156">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="195e9-157">Modeli eğitmek gereken süreyi veri miktarı için uygun.</span><span class="sxs-lookup"><span data-stu-id="195e9-157">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="195e9-158">Bu grafik için yeterli bir değer seçmek için kılavuz kullanın. `Time to train (seconds)` alan:</span><span class="sxs-lookup"><span data-stu-id="195e9-158">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="195e9-159">\* Veri kümesi boyutu</span><span class="sxs-lookup"><span data-stu-id="195e9-159">\*Dataset Size</span></span>  | <span data-ttu-id="195e9-160">Veri kümesi türü</span><span class="sxs-lookup"><span data-stu-id="195e9-160">Dataset Type</span></span>       | <span data-ttu-id="195e9-161">Ort. Eğitimi \* süresi</span><span class="sxs-lookup"><span data-stu-id="195e9-161">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="195e9-162">0 - 10 mb</span><span class="sxs-lookup"><span data-stu-id="195e9-162">0 - 10 Mb</span></span>     | <span data-ttu-id="195e9-163">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="195e9-163">Numeric and Text</span></span>   | <span data-ttu-id="195e9-164">10 saniye</span><span class="sxs-lookup"><span data-stu-id="195e9-164">10 sec</span></span>
<span data-ttu-id="195e9-165">10 - 100 mb</span><span class="sxs-lookup"><span data-stu-id="195e9-165">10 - 100 Mb</span></span>   | <span data-ttu-id="195e9-166">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="195e9-166">Numeric and Text</span></span>   | <span data-ttu-id="195e9-167">10 dakikalık</span><span class="sxs-lookup"><span data-stu-id="195e9-167">10 min</span></span>
<span data-ttu-id="195e9-168">100 - 500 mb</span><span class="sxs-lookup"><span data-stu-id="195e9-168">100 - 500 Mb</span></span>  | <span data-ttu-id="195e9-169">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="195e9-169">Numeric and Text</span></span>   | <span data-ttu-id="195e9-170">30 dakika</span><span class="sxs-lookup"><span data-stu-id="195e9-170">30 min</span></span>
<span data-ttu-id="195e9-171">500 - 1 Gb</span><span class="sxs-lookup"><span data-stu-id="195e9-171">500 - 1 Gb</span></span>    | <span data-ttu-id="195e9-172">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="195e9-172">Numeric and Text</span></span>   | <span data-ttu-id="195e9-173">60 dk önce</span><span class="sxs-lookup"><span data-stu-id="195e9-173">60 min</span></span>
<span data-ttu-id="195e9-174">1 Gb +</span><span class="sxs-lookup"><span data-stu-id="195e9-174">1 Gb+</span></span>         | <span data-ttu-id="195e9-175">Sayısal ve metin</span><span class="sxs-lookup"><span data-stu-id="195e9-175">Numeric and Text</span></span>   | <span data-ttu-id="195e9-176">3 saat +</span><span class="sxs-lookup"><span data-stu-id="195e9-176">3 hour+</span></span>

1. <span data-ttu-id="195e9-177">Eğitim verileri dosyası 10 MB'tan fazla olduğundan, 600 saniye (10 dakika) değeri olarak kullanın *süresi (saniye) eğitmek için*.</span><span class="sxs-lookup"><span data-stu-id="195e9-177">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="195e9-178">Seçin *eğitim Başlat*.</span><span class="sxs-lookup"><span data-stu-id="195e9-178">Select *Start Training*.</span></span>

<span data-ttu-id="195e9-179">Eğitim işlem boyunca ilerleme veri görüntülenen `Progress` eğitimi adım bölümü.</span><span class="sxs-lookup"><span data-stu-id="195e9-179">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="195e9-180">Durum eğitim işleminin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="195e9-180">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="195e9-181">En yüksek doğruluğa en iyi performansa sahip Model Oluşturucu bulundu modelinin doğruluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="195e9-181">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="195e9-182">Daha yüksek doğruluk testi veri daha doğru bir şekilde tahmin modeli anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="195e9-182">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="195e9-183">En iyi algoritmayı bulundu modelinin oluşturucusu tarafından gerçekleştirilen en iyi performansa algoritma adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="195e9-183">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="195e9-184">Son algoritması, en son Model Oluşturucu, modeli eğitmek için kullanılan algoritma adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="195e9-184">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="195e9-185">Alıştırma tamamlandıktan sonra değerlendir adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="195e9-185">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="195e9-186">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="195e9-186">Evaluate the model</span></span>

<span data-ttu-id="195e9-187">En iyi performansı sahip bir model eğitimi adım olacaktır.</span><span class="sxs-lookup"><span data-stu-id="195e9-187">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="195e9-188">Model Oluşturucu aracı değerlendir adımda çıkış bölümüne en iyi performansa sahip modeli tarafından kullanılan algoritmayı içerecek *en iyi modeli* ölçümlerde yanı sıra giriş *en iyi Model kalitesi (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="195e9-188">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="195e9-189">İlk beş modelleri ve bunların ölçümleri içeren ek olarak, bir Özet Tablosu.</span><span class="sxs-lookup"><span data-stu-id="195e9-189">Additionally, a summary table containing top five models and their metrics.</span></span> 

<span data-ttu-id="195e9-190">Doğruluk ölçümlerinizi memnun değilseniz, deneyin ve doğruluğu artırmak için bazı kolay veya daha fazla veri modeli eğitme süre miktarını artırmak için yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="195e9-190">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="195e9-191">Aksi takdirde, kod adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="195e9-191">Otherwise, navigate to the code step.</span></span> 

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="195e9-192">Tahminde bulunmak için kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="195e9-192">Add the code to make predictions</span></span>

<span data-ttu-id="195e9-193">İki proje eğitim işleminin sonucu olarak oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="195e9-193">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="195e9-194">TaxiFarePredictionML.ConsoleApp: Model eğitimi ve tüketim kodunu içeren bir .NET Core konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="195e9-194">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="195e9-195">TaxiFarePredictionML.Model: Giriş şemasını tanımlayan ve en iyi performansa sahip sırasında eğitim modeli kalıcı sürümünü yanı sıra model verileri çıkış veri modelleri içeren .NET Standard sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="195e9-195">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>


1. <span data-ttu-id="195e9-196">Model Oluşturucu aracı kod adımda seçin **ekleme projeleri** otomatik olarak oluşturulan projeleri çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="195e9-196">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="195e9-197">Sağ *TaxiFarePrediction* proje.</span><span class="sxs-lookup"><span data-stu-id="195e9-197">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="195e9-198">Ardından, **Ekle > başvuru**.</span><span class="sxs-lookup"><span data-stu-id="195e9-198">Then, **Add > Reference**.</span></span> <span data-ttu-id="195e9-199">Seçin **projeleri > Çözüm** düğüm ve listeden *TaxiFarePredictionML.Model* proje ve Tamam'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="195e9-199">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>
1. <span data-ttu-id="195e9-200">Açık *Program.cs* dosyası *TaxiFarePrediction* proje.</span><span class="sxs-lookup"><span data-stu-id="195e9-200">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="195e9-201">Aşağıdaki using deyimlerini başvurmak için *Microsoft.ML* NuGet paketi ve *TaxiFarePredictionML.Model* proje:</span><span class="sxs-lookup"><span data-stu-id="195e9-201">Add the following using statements to reference the *Microsoft.ML* NuGet package and *TaxiFarePredictionML.Model* project:</span></span>


    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. <span data-ttu-id="195e9-202">Ekleme `ConsumeModel` yönteme `Program` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="195e9-202">Add the `ConsumeModel` method to the `Program` class.</span></span> 

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

    <span data-ttu-id="195e9-203">`ConsumeModel` , Eğitilen model yük oluşturma bir [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) modeli için ve yeni veri tahminlerde bulunmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="195e9-203">The `ConsumeModel` will load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and use it to make predictions on new data.</span></span>

7. <span data-ttu-id="195e9-204">Üzerinde yeni veri modelini kullanarak bir tahminde bulunmak için yeni bir örneğini oluşturun. `ModelInput` kullanın ve sınıf `ConsumeModel` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="195e9-204">To make a prediction on new data using the model, create a new instance of the `ModelInput` class and use the `ConsumeModel` method.</span></span> <span data-ttu-id="195e9-205">Taksi miktarı girişinin parçası olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="195e9-205">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="195e9-206">Bu durum, onun için tahmin modeli oluşturur çünkü.</span><span class="sxs-lookup"><span data-stu-id="195e9-206">This is because the model will generate the prediction for it.</span></span> <span data-ttu-id="195e9-207">Aşağıdaki kodu ekleyin `Main` yöntemi ve uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="195e9-207">Add the following code to the `Main` method and run the application</span></span>

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

    <span data-ttu-id="195e9-208">Program tarafından oluşturulan çıktı kod parçacığını aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="195e9-208">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="195e9-209">Daha sonra başka bir çözüm içinde oluşturulan projeleri başvurmanız gerekiyorsa, içinde bulabilirsiniz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizin.</span><span class="sxs-lookup"><span data-stu-id="195e9-209">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="195e9-210">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="195e9-210">Next Steps</span></span>

<span data-ttu-id="195e9-211">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="195e9-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="195e9-212">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="195e9-212">Prepare and understand the data</span></span>
> * <span data-ttu-id="195e9-213">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="195e9-213">Choose a scenario</span></span>
> * <span data-ttu-id="195e9-214">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="195e9-214">Load the data</span></span>
> * <span data-ttu-id="195e9-215">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="195e9-215">Train the model</span></span>
> * <span data-ttu-id="195e9-216">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="195e9-216">Evaluate the model</span></span>
> * <span data-ttu-id="195e9-217">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="195e9-217">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="195e9-218">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="195e9-218">Additional Resources</span></span>

<span data-ttu-id="195e9-219">Bu öğreticide bahsedilen konuları hakkında daha fazla bilgi için aşağıdaki kaynakları ziyaret edin:</span><span class="sxs-lookup"><span data-stu-id="195e9-219">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="195e9-220">Model Oluşturucu senaryoları</span><span class="sxs-lookup"><span data-stu-id="195e9-220">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="195e9-221">Model Oluşturucu veri biçimleri</span><span class="sxs-lookup"><span data-stu-id="195e9-221">Model Builder Data Formats</span></span>](../automate-training-with-model-builder.md#data-formats)
- [<span data-ttu-id="195e9-222">Regresyon</span><span class="sxs-lookup"><span data-stu-id="195e9-222">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="195e9-223">Regresyon modeli ölçümleri</span><span class="sxs-lookup"><span data-stu-id="195e9-223">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="195e9-224">NYC TLC taksi seyahat veri kümesi</span><span class="sxs-lookup"><span data-stu-id="195e9-224">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
