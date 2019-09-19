---
title: 'Öğretici: Model Oluşturucu ile gerileme kullanarak fiyatları tahmin etme'
description: Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.net model Oluşturucu kullanarak bir gerileme modeli oluşturma gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 09/18/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bb344a7f01e8ffe0e40578c6fb2f28bebd2eb807
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117969"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="c4b21-103">Öğretici: Model Oluşturucu ile gerileme kullanarak fiyatları tahmin etme</span><span class="sxs-lookup"><span data-stu-id="c4b21-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="c4b21-104">Fiyatları tahmin etmek için bir gerileme modeli () oluşturmak üzere ML.NET model Oluşturucu 'Yu nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-104">Learn how to use ML.NET Model Builder to build a regression model() to predict prices.</span></span>  <span data-ttu-id="c4b21-105">Bu öğreticide geliştirdiğiniz .NET konsol uygulaması, geçmiş New York taksi tarifeli havayolu verilerine dayalı olarak taksi Fares 'yi tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="c4b21-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="c4b21-106">Model Oluşturucu fiyat tahmin şablonu, sayısal tahmin değeri gerektiren herhangi bir senaryo için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="c4b21-107">Örnek senaryolar şunlardır: ev fiyat tahmini, talep tahmini ve satış tahmini.</span><span class="sxs-lookup"><span data-stu-id="c4b21-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="c4b21-108">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="c4b21-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="c4b21-109">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="c4b21-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="c4b21-110">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="c4b21-110">Choose a scenario</span></span>
> - <span data-ttu-id="c4b21-111">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="c4b21-111">Load the data</span></span>
> - <span data-ttu-id="c4b21-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c4b21-112">Train the model</span></span>
> - <span data-ttu-id="c4b21-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c4b21-113">Evaluate the model</span></span>
> - <span data-ttu-id="c4b21-114">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="c4b21-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="c4b21-115">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="c4b21-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="c4b21-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="c4b21-116">Pre-requisites</span></span>

<span data-ttu-id="c4b21-117">Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="c4b21-118">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4b21-118">Create a console application</span></span>

1. <span data-ttu-id="c4b21-119">"Taxifaretahminini" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4b21-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="c4b21-120">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="c4b21-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="c4b21-121">Veri kümesi dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4b21-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="c4b21-122">Machine Learning modelini eğmekte ve değerlendirmek için kullanılan veri kümesi, ilk olarak NYC TLC TAXI seyahat veri kümesinden.</span><span class="sxs-lookup"><span data-stu-id="c4b21-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    <span data-ttu-id="c4b21-123">Veri kümesini indirmek için [Taxi-fare-train. csv indirme bağlantısına](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv)gidin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    <span data-ttu-id="c4b21-124">Sayfa yüklendiğinde, sayfada herhangi bir yere sağ tıklayın ve **farklı kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    <span data-ttu-id="c4b21-125">Dosyayı önceki adımda oluşturduğunuz *veri* klasörüne kaydetmek Için **Farklı Kaydet iletişim kutusunu** kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4b21-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="c4b21-126">**Çözüm Gezgini**, *Taxi-fare-train. csv* dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="c4b21-127">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="c4b21-128">`taxi-fare-train.csv` Veri kümesindeki her satır bir TAXI tarafından yapılan gelişlerin ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="c4b21-129">**Taxi-fare-train. csv** veri kümesini açın</span><span class="sxs-lookup"><span data-stu-id="c4b21-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="c4b21-130">Belirtilen veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="c4b21-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="c4b21-131">**vendor_id:** Taxı satıcısının KIMLIĞI bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="c4b21-132">**rate_code:** Taxı seyahati 'ın hız türü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="c4b21-133">**passenger_count:** Seyahat üzerindeki pascuların sayısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="c4b21-134">**trip_time_in_secs:** Seyahati için geçen süre.</span><span class="sxs-lookup"><span data-stu-id="c4b21-134">**trip_time_in_secs:** The amount of time the trip took.</span></span>
    - <span data-ttu-id="c4b21-135">**trip_distance:** Seyahat uzaklığı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-135">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="c4b21-136">**payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-136">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="c4b21-137">**fare_amount:** Ödenen toplam TAXI tarifeli havayolu etikettir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-137">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="c4b21-138">`label` Tahmin etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="c4b21-138">The `label` is the column you want to predict.</span></span> <span data-ttu-id="c4b21-139">Regresyon görevi gerçekleştirirken, amaç sayısal bir değeri tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4b21-139">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="c4b21-140">Bu fiyat tahmin senaryosunda, bir TAXI arttırıldığında 'nın maliyeti tahmin ediliyor.</span><span class="sxs-lookup"><span data-stu-id="c4b21-140">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="c4b21-141">Bu nedenle, **fare_amount** etikettir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-141">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="c4b21-142">`features` ,`label`Modeli tahmin etmek için size izin verdiğiniz girişlerdir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-142">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="c4b21-143">Bu durumda, sütunların geri kalanı tarifeli havayolu tutarını tahmin etmek için özellik veya giriş olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4b21-143">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="c4b21-144">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="c4b21-144">Choose a scenario</span></span>

<span data-ttu-id="c4b21-145">Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-145">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="c4b21-146">Bu durumda senaryo `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="c4b21-146">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="c4b21-147">**Çözüm Gezgini**, *taxifaretahmin* projesine sağ tıklayın ve**Machine Learning** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-147">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="c4b21-148">Model Oluşturucu aracının senaryo adımında *fiyat tahmini* senaryosu ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-148">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="c4b21-149">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="c4b21-149">Load the data</span></span>

<span data-ttu-id="c4b21-150">Model Oluşturucu, bir SQL Server veritabanı veya CSV ya da TSV biçimindeki yerel bir dosya olan iki kaynaktan verileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c4b21-150">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="c4b21-151">Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden *Dosya* ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-151">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="c4b21-152">*Dosya Seç* metin kutusunun yanındaki düğmeyi seçin ve *veri* dizinindeki *Taxi-fare-test. csv* dosyasına gidip seçmek için dosya Gezgini 'ni kullanın</span><span class="sxs-lookup"><span data-stu-id="c4b21-152">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="c4b21-153">Açılan menüyü *tahmin etmek Için etiket veya sütunda* *fare_amount* öğesini seçin ve model Oluşturucu aracının eğitme adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-153">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="c4b21-154">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c4b21-154">Train the model</span></span>

<span data-ttu-id="c4b21-155">Bu öğreticide fiyat tahmin modelini eğitmek için kullanılan makine öğrenimi görevi gerileme.</span><span class="sxs-lookup"><span data-stu-id="c4b21-155">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="c4b21-156">Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı gerileme algoritmaları ve ayarları kullanarak modelleri ayrı ayrı işler.</span><span class="sxs-lookup"><span data-stu-id="c4b21-156">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="c4b21-157">Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı.</span><span class="sxs-lookup"><span data-stu-id="c4b21-157">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="c4b21-158">Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer.</span><span class="sxs-lookup"><span data-stu-id="c4b21-158">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="c4b21-159">Daha uzun bir süre eğmemeyi tercih etmediğiniz sürece varsayılan değeri *eğitme süresi (saniye)* olarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="c4b21-159">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="c4b21-160">*Eğitimi Başlat*' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-160">Select *Start Training*.</span></span>

<span data-ttu-id="c4b21-161">Eğitim süreci boyunca, ilerleme verileri eğitme adımının `Progress` bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-161">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="c4b21-162">Durum, eğitim sürecinin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c4b21-162">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="c4b21-163">En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-163">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="c4b21-164">Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-164">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="c4b21-165">En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c4b21-165">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="c4b21-166">Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c4b21-166">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="c4b21-167">Eğitim tamamlandıktan sonra değerlendir adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-167">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="c4b21-168">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c4b21-168">Evaluate the model</span></span>

<span data-ttu-id="c4b21-169">Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c4b21-169">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="c4b21-170">Model Oluşturucu aracının değerlendir adımında, çıkış bölümü en iyi *model girişinde en* iyi işlem modeli tarafından kullanılan algoritmayı *(RKARE)* içerir.</span><span class="sxs-lookup"><span data-stu-id="c4b21-170">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="c4b21-171">Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu.</span><span class="sxs-lookup"><span data-stu-id="c4b21-171">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="c4b21-172">Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu denemeye yönelik bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="c4b21-172">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="c4b21-173">Aksi takdirde, kod adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-173">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="c4b21-174">Tahminleri yapmak için kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="c4b21-174">Add the code to make predictions</span></span>

<span data-ttu-id="c4b21-175">Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="c4b21-175">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="c4b21-176">TaxiFarePredictionML. ConsoleApp: Model eğitimi ve tüketim kodu içeren bir .NET Core konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="c4b21-176">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="c4b21-177">TaxiFarePredictionML. Model: Eğitim sırasında en iyi gerçekleştirme modelinin kalıcı sürümü ve giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini içeren .NET Standard sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="c4b21-177">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="c4b21-178">Model Oluşturucu aracının kod adımında, otomatik olarak oluşturulan projeleri çözüme eklemek için **Proje Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-178">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="c4b21-179">*Taxifaretahmin* projesi öğesine sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c4b21-179">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="c4b21-180">Ardından **> başvuru ekleyin**.</span><span class="sxs-lookup"><span data-stu-id="c4b21-180">Then, **Add > Reference**.</span></span> <span data-ttu-id="c4b21-181">**Projeler > çözüm** düğümünü seçin ve listeden *TaxiFarePredictionML. model* projesini denetleyip Tamam ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-181">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>
1. <span data-ttu-id="c4b21-182">*Program.cs* dosyasını *Taxifaretahmin* projesinde açın.</span><span class="sxs-lookup"><span data-stu-id="c4b21-182">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="c4b21-183">*Microsoft.ml* NuGet paketini ve *TaxiFarePredictionML. model* projesine başvurmak için aşağıdaki using deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c4b21-183">Add the following using statements to reference the *Microsoft.ML* NuGet package and *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. <span data-ttu-id="c4b21-184">`ConsumeModel` Yöntemini`Program` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-184">Add the `ConsumeModel` method to the `Program` class.</span></span>

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

    <span data-ttu-id="c4b21-185">Eğitilen modeli yükler, model için bir [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) oluşturun ve yeni verilerde tahmine dayalı hale getirmek için onu kullanın. `ConsumeModel`</span><span class="sxs-lookup"><span data-stu-id="c4b21-185">The `ConsumeModel` will load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and use it to make predictions on new data.</span></span>

1. <span data-ttu-id="c4b21-186">Modeli kullanarak yeni verileri tahmin etmek için, `ModelInput` sınıfın yeni bir örneğini oluşturun ve `ConsumeModel` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4b21-186">To make a prediction on new data using the model, create a new instance of the `ModelInput` class and use the `ConsumeModel` method.</span></span> <span data-ttu-id="c4b21-187">Tarifeli havayolu tutarının girişin bir parçası olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c4b21-187">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="c4b21-188">Bunun nedeni, modelin tahmin oluşturması olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c4b21-188">This is because the model will generate the prediction for it.</span></span> <span data-ttu-id="c4b21-189">`Main` Yöntemine aşağıdaki kodu ekleyin ve uygulamayı çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c4b21-189">Add the following code to the `Main` method and run the application</span></span>

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

    <span data-ttu-id="c4b21-190">Program tarafından oluşturulan çıkış aşağıdaki kod parçacığına benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="c4b21-190">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="c4b21-191">Oluşturulan projelere başka bir çözümün içinde daha sonraki bir zamanda başvurmanız gerekirse, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizin içinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4b21-191">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c4b21-192">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="c4b21-192">Next Steps</span></span>

<span data-ttu-id="c4b21-193">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="c4b21-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="c4b21-194">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="c4b21-194">Prepare and understand the data</span></span>
> - <span data-ttu-id="c4b21-195">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="c4b21-195">Choose a scenario</span></span>
> - <span data-ttu-id="c4b21-196">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="c4b21-196">Load the data</span></span>
> - <span data-ttu-id="c4b21-197">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c4b21-197">Train the model</span></span>
> - <span data-ttu-id="c4b21-198">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c4b21-198">Evaluate the model</span></span>
> - <span data-ttu-id="c4b21-199">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="c4b21-199">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c4b21-200">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c4b21-200">Additional Resources</span></span>

<span data-ttu-id="c4b21-201">Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:</span><span class="sxs-lookup"><span data-stu-id="c4b21-201">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="c4b21-202">Model Oluşturucu senaryoları</span><span class="sxs-lookup"><span data-stu-id="c4b21-202">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="c4b21-203">Regresyon</span><span class="sxs-lookup"><span data-stu-id="c4b21-203">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="c4b21-204">Regresyon modeli ölçümleri</span><span class="sxs-lookup"><span data-stu-id="c4b21-204">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="c4b21-205">NYC TLC TAXI seyahat veri kümesi</span><span class="sxs-lookup"><span data-stu-id="c4b21-205">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
