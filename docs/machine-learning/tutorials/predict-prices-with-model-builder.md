---
title: 'Öğretici: Model Oluşturucu ile gerileme kullanarak fiyatları tahmin'
description: Bu öğretici fiyatları tahmin etmek için ML.NET Model Builder kullanarak bir regresyon modeli oluşturmak için nasıl göstermektedir, özellikle, New York Taksi ücretleri.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: c027fe57f571c791784b0bdb7ad9503fc49daa1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187704"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="dd525-103">Öğretici: Model Oluşturucu ile gerileme kullanarak fiyatları tahmin</span><span class="sxs-lookup"><span data-stu-id="dd525-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="dd525-104">Fiyatları tahmin etmek için bir regresyon modeli oluşturmak için ML.NET Model Builder'ı nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="dd525-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="dd525-105">Bu eğitimde geliştirdiğiniz .NET konsol uygulaması, tarihsel New York taksi ücreti verilerine göre taksi ücretlerini tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="dd525-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="dd525-106">Model Oluşturucu fiyat tahmin şablonu, sayısal tahmin değeri gerektiren herhangi bir senaryo için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd525-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="dd525-107">Örnek senaryolar şunlardır: ev fiyat tahmini, talep tahmini ve satış tahmini.</span><span class="sxs-lookup"><span data-stu-id="dd525-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="dd525-108">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dd525-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="dd525-109">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="dd525-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="dd525-110">Bir senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="dd525-110">Choose a scenario</span></span>
> - <span data-ttu-id="dd525-111">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="dd525-111">Load the data</span></span>
> - <span data-ttu-id="dd525-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="dd525-112">Train the model</span></span>
> - <span data-ttu-id="dd525-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="dd525-113">Evaluate the model</span></span>
> - <span data-ttu-id="dd525-114">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="dd525-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="dd525-115">Model Oluşturucu şu anda Önizleme'de.</span><span class="sxs-lookup"><span data-stu-id="dd525-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="dd525-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="dd525-116">Pre-requisites</span></span>

<span data-ttu-id="dd525-117">Ön koşul ve yükleme yönergelerinin listesi için [Model Oluşturucu yükleme kılavuzunu ziyaret edin.](../how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="dd525-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="dd525-118">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd525-118">Create a console application</span></span>

1. <span data-ttu-id="dd525-119">"TaxiFarePrediction" adlı **bir C# .NET Çekirdek Konsol Uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dd525-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="dd525-120">Çözüm **ve projeyi aynı dizindeki yerleştir** çözümve proje **işaretsiz** olduğundan emin olun (VS 2019) veya **çözüm için create directory** (VS 2017) **işaretlenir.**</span><span class="sxs-lookup"><span data-stu-id="dd525-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="dd525-121">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="dd525-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="dd525-122">Veri kümesi dosyalarını depolamak için projenizde *Veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dd525-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="dd525-123">Makine öğrenimi modelini eğitmek ve değerlendirmek için kullanılan veri seti aslında NYC TLC Taksi Gezisi veri kümesindendir.</span><span class="sxs-lookup"><span data-stu-id="dd525-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="dd525-124">Veri kümesini indirmek için [taksi-ücret-train.csv indirme linkine](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv)gidin.</span><span class="sxs-lookup"><span data-stu-id="dd525-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="dd525-125">Sayfa yüklendiğinde, sayfanın herhangi bir yerine sağ tıklayın ve **Olarak Kaydet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="dd525-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="dd525-126">Önceki adımda oluşturduğunuz *Veri* klasörüne dosyayı kaydetmek için **Kaydet İletişim** kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd525-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="dd525-127">**Çözüm Gezgini'nde,** *taksi-ücret-train.csv* dosyasına sağ tıklayın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="dd525-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="dd525-128">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dd525-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="dd525-129">Veri kümesindeki `taxi-fare-train.csv` her satır, bir taksi tarafından yapılan seyahatlerin ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="dd525-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="dd525-130">**Taksi-ücret-train.csv** veri setini açın</span><span class="sxs-lookup"><span data-stu-id="dd525-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="dd525-131">Sağlanan veri kümesi aşağıdaki sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="dd525-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="dd525-132">**vendor_id:** Taksi satıcısının kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="dd525-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="dd525-133">**rate_code:** Taksi gezisinin fiyat türü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="dd525-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="dd525-134">**passenger_count:** Yolculuktaki yolcu sayısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="dd525-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="dd525-135">**trip_time_in_secs:** Yolculuğun aldığı süre.</span><span class="sxs-lookup"><span data-stu-id="dd525-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="dd525-136">Yolculuk tamamlanmadan önce seyahat ücretini tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="dd525-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="dd525-137">O anda yolculuğun ne kadar süreceğini bilemezsin.</span><span class="sxs-lookup"><span data-stu-id="dd525-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="dd525-138">Bu nedenle, yolculuk süresi bir özellik değildir ve bu sütunu modelden dışlarsınız.</span><span class="sxs-lookup"><span data-stu-id="dd525-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="dd525-139">**trip_distance:** Yolculuk mesafesi bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="dd525-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="dd525-140">**payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="dd525-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="dd525-141">**fare_amount:** Ödenen toplam taksi ücreti etikettir.</span><span class="sxs-lookup"><span data-stu-id="dd525-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="dd525-142">Tahmin `label` etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="dd525-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="dd525-143">Bir regresyon görevi gerçekleştirirken, amaç sayısal bir değeri tahmin etmektir.</span><span class="sxs-lookup"><span data-stu-id="dd525-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="dd525-144">Bu fiyat tahmini senaryosunda, bir taksi yolculuğu maliyeti tahmin ediliyor.</span><span class="sxs-lookup"><span data-stu-id="dd525-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="dd525-145">Bu nedenle, **fare_amount** etikettir.</span><span class="sxs-lookup"><span data-stu-id="dd525-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="dd525-146">Tanımlanan `features` girdiler, modeli tahmin etmek için `label`verdiğiniz girdilerdir.</span><span class="sxs-lookup"><span data-stu-id="dd525-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="dd525-147">Bu durumda, **trip_time_in_secs** hariç sütunların geri kalanı, ücret tutarını tahmin etmek için özellik veya girdi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd525-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="dd525-148">Bir senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="dd525-148">Choose a scenario</span></span>

<span data-ttu-id="dd525-149">Modelinizi eğitmek için Model Builder tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd525-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="dd525-150">Bu durumda, `Price Prediction`senaryo.</span><span class="sxs-lookup"><span data-stu-id="dd525-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="dd525-151">**Solution Explorer'da** *TaxiFarePrediction* projesine sağ tıklayın ve**Machine Learning** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="dd525-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="dd525-152">Model Oluşturucu aracının senaryo adımında *Fiyat Tahmini* senaryosunu seçin.</span><span class="sxs-lookup"><span data-stu-id="dd525-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="dd525-153">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="dd525-153">Load the data</span></span>

<span data-ttu-id="dd525-154">Model Builder iki kaynaktan, bir SQL Server veritabanından veya yerel bir dosyadan csv veya tsv formatında veri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="dd525-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="dd525-155">Model Oluşturucu aracının veri adımında, veri kaynağı açılır tarafından *Dosya'yı* seçin.</span><span class="sxs-lookup"><span data-stu-id="dd525-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="dd525-156">Dosya metin kutusunu *seç'in* yanındaki düğmeyi seçin ve *Veri* dizinindeki *taksi-fare-test.csv'ye* göz atmak ve seçmek için Dosya Gezgini'ni kullanın</span><span class="sxs-lookup"><span data-stu-id="dd525-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="dd525-157">Sütundaki *fare_amount* 'yi seçin *(Label) açılır düşüşünü tahmin edin.*</span><span class="sxs-lookup"><span data-stu-id="dd525-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="dd525-158">Giriş *Sütunları (Özellikler)* açılır bırak'ı genişletin ve eğitim sırasında özellik olarak hariç tutmak için *trip_time_in_secs* sütunun denetimini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="dd525-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="dd525-159">Model Oluşturucu aracının tren adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="dd525-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="dd525-160">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="dd525-160">Train the model</span></span>

<span data-ttu-id="dd525-161">Bu öğretici fiyat tahmin modeli eğitmek için kullanılan makine öğrenme görevi gerileme olduğunu.</span><span class="sxs-lookup"><span data-stu-id="dd525-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="dd525-162">Model eğitim süreci sırasında Model Builder, veri setiniz için en iyi performans gösteren modeli bulmak için farklı regresyon algoritmaları ve ayarları kullanarak ayrı modeller eğitir.</span><span class="sxs-lookup"><span data-stu-id="dd525-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="dd525-163">Modelin eğitilmesi için gereken süre veri miktarıyla orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="dd525-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="dd525-164">Model Oluşturucu, veri kaynağınızın boyutuna bağlı **olarak, eğitme Süresi (saniye)** için varsayılan bir değer seçer.</span><span class="sxs-lookup"><span data-stu-id="dd525-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="dd525-165">Daha uzun süre antrenman yapmayı tercih etmedikçe, varsayılan değeri, *eğitme süresi (saniye)* olduğu gibi bırakın.</span><span class="sxs-lookup"><span data-stu-id="dd525-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="dd525-166">*Start Training'i*seçin.</span><span class="sxs-lookup"><span data-stu-id="dd525-166">Select *Start Training*.</span></span>

<span data-ttu-id="dd525-167">Eğitim süreci boyunca, ilerleme verileri tren `Progress` adımı bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dd525-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="dd525-168">Durum, eğitim sürecinin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dd525-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="dd525-169">En iyi doğruluk, Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren modelin doğruluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dd525-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="dd525-170">Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin ettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dd525-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="dd525-171">En iyi algoritma, Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dd525-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="dd525-172">Son algoritma, modeli eğitmek için Model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dd525-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="dd525-173">Eğitim tamamlandıktan sonra değerlendirme adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="dd525-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="dd525-174">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="dd525-174">Evaluate the model</span></span>

<span data-ttu-id="dd525-175">Eğitim adımının sonucu en iyi performansa sahip bir model olacaktır.</span><span class="sxs-lookup"><span data-stu-id="dd525-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="dd525-176">Model Oluşturucu aracının değerlendirme adımında, çıkış bölümü, *Best Model* Girişinde en iyi performans gösteren model tarafından kullanılan algoritmayı içerecek ve En İyi Model *Kalitesi (RSquared)* ölçütleri ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="dd525-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="dd525-177">Ayrıca, en iyi beş modeli ve bunların ölçümlerini içeren bir özet tablo.</span><span class="sxs-lookup"><span data-stu-id="dd525-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="dd525-178">Doğruluk ölçümlerinizden memnun değilseniz, model doğruluğunu geliştirmeyi denemenin ve geliştirmenin bazı kolay yolları, modeli eğitmek veya daha fazla veri kullanmak için gereken süreyi artırmakiçindir.</span><span class="sxs-lookup"><span data-stu-id="dd525-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="dd525-179">Aksi takdirde, kod adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="dd525-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="dd525-180">Tahminlerde bulunmak için kodu ekleme</span><span class="sxs-lookup"><span data-stu-id="dd525-180">Add the code to make predictions</span></span>

<span data-ttu-id="dd525-181">Eğitim süreci sonucunda iki proje oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="dd525-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="dd525-182">TaxiFarePredictionML.ConsoleApp: Model eğitimi ve örnek tüketim kodunu içeren bir .NET Core Console uygulaması.</span><span class="sxs-lookup"><span data-stu-id="dd525-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="dd525-183">TaxiFarePredictionML.Model: Giriş ve çıktı modeli verilerinin şemasını tanımlayan veri modellerini, eğitim sırasında en iyi performans gösteren modelin kaydedilmiş `ConsumeModel` sürümünü ve tahminde bulunmak için çağrılan yardımcı sınıfı içeren bir .NET Standart sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="dd525-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="dd525-184">Model Oluşturucu aracının kod adımında, çözüme otomatik oluşturulan projeleri eklemek için **Projeler Ekle'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="dd525-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="dd525-185">*TaxiFarePrediction* projesinde *Program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="dd525-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="dd525-186">*TaxiFarePredictionML.Model* projesine başvurmak için aşağıdaki ifadeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dd525-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="dd525-187">Modeli kullanarak yeni veriler üzerinde bir tahminde bulunmak `ModelInput` için, `Main` uygulama yöntemi içinde sınıfın yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dd525-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="dd525-188">Ücret tutarının girişin bir parçası olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dd525-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="dd525-189">Bunun nedeni, modelin bunun için tahmin oluşturacağıdır.</span><span class="sxs-lookup"><span data-stu-id="dd525-189">This is because the model will generate the prediction for it.</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. <span data-ttu-id="dd525-190">Sınıftaki `Predict` `ConsumeModel` yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd525-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="dd525-191">Yöntem, `Predict` eğitilen modeli [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) yükler, model için bir model oluşturur ve yeni veriler üzerinde öngörülerde bulunmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd525-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="dd525-192">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dd525-192">Run the application.</span></span>

    <span data-ttu-id="dd525-193">Program tarafından oluşturulan çıktı aşağıdaki snippet benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="dd525-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="dd525-194">Oluşturulan projeleri başka bir çözüm içinde daha sonra göndermeniz gerekiyorsa, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizinin içinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd525-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dd525-195">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="dd525-195">Next Steps</span></span>

<span data-ttu-id="dd525-196">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="dd525-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="dd525-197">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="dd525-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="dd525-198">Bir senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="dd525-198">Choose a scenario</span></span>
> - <span data-ttu-id="dd525-199">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="dd525-199">Load the data</span></span>
> - <span data-ttu-id="dd525-200">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="dd525-200">Train the model</span></span>
> - <span data-ttu-id="dd525-201">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="dd525-201">Evaluate the model</span></span>
> - <span data-ttu-id="dd525-202">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="dd525-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dd525-203">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="dd525-203">Additional Resources</span></span>

<span data-ttu-id="dd525-204">Bu eğitimde bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:</span><span class="sxs-lookup"><span data-stu-id="dd525-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="dd525-205">Model Oluşturucu Senaryolar</span><span class="sxs-lookup"><span data-stu-id="dd525-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="dd525-206">Regresyon</span><span class="sxs-lookup"><span data-stu-id="dd525-206">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="dd525-207">Regresyon Model Ölçümleri</span><span class="sxs-lookup"><span data-stu-id="dd525-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="dd525-208">NYC TLC Taksi Gezisi veri seti</span><span class="sxs-lookup"><span data-stu-id="dd525-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
