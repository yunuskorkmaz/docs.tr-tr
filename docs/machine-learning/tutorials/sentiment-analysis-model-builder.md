---
title: 'Öğretici: Duyarlılığı analiz et - ikili sınıflandırma'
description: Bu öğretici, web sitesi yorumlarından duyguları sınıflandıran ve uygun eylemi yapan bir Razor Pages uygulamasını nasıl oluşturabileceğinizi gösterir. İkili duygu sınıflandırıcı Visual Studio Model Builder kullanır.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 98c9f28ca4ce6365ed4cf4ff1566a33dbe8f35ca
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438222"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="ead32-104">Öğretici: ML.NET Model Builder kullanarak bir web uygulamasında web sitesi yorumlarının duyarlılığını analiz edin</span><span class="sxs-lookup"><span data-stu-id="ead32-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="ead32-105">Bir web uygulaması içinde gerçek zamanlı olarak yorumlardan duyguları analiz etmeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="ead32-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="ead32-106">Bu öğretici, web sitesi yorumlarından gelen duyguları gerçek zamanlı olarak sınıflandıran bir ASP.NET Core Razor Pages uygulamasını nasıl oluşturabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ead32-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="ead32-107">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ead32-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ead32-108">ASP.NET Core Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ead32-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="ead32-109">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="ead32-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="ead32-110">Bir senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="ead32-110">Choose a scenario</span></span>
> - <span data-ttu-id="ead32-111">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="ead32-111">Load the data</span></span>
> - <span data-ttu-id="ead32-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="ead32-112">Train the model</span></span>
> - <span data-ttu-id="ead32-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ead32-113">Evaluate the model</span></span>
> - <span data-ttu-id="ead32-114">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="ead32-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="ead32-115">Model Oluşturucu şu anda Önizleme'de.</span><span class="sxs-lookup"><span data-stu-id="ead32-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="ead32-116">Bu öğreticinin kaynak kodunu [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ead32-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="ead32-117">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="ead32-117">Pre-requisites</span></span>

<span data-ttu-id="ead32-118">Ön koşul ve yükleme yönergelerinin listesi için [Model Oluşturucu yükleme kılavuzunu ziyaret edin.](../how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="ead32-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="ead32-119">Jilet Sayfaları uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ead32-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="ead32-120">Core **Razor Pages Uygulaması ASP.NET**oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ead32-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="ead32-121">Visual Studio'yu açın ve menü çubuğundan **Dosya > Yeni > Projesi'ni** seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="ead32-122">Yeni Proje iletişim kutusunda, **Web** düğümü tarafından izlenen **Visual C#** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="ead32-123">Ardından **ASP.NET Çekirdek Web Uygulaması** proje şablonuna gidin.</span><span class="sxs-lookup"><span data-stu-id="ead32-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="ead32-124">**Ad** metin kutusuna "SentimentRazor" yazın.</span><span class="sxs-lookup"><span data-stu-id="ead32-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="ead32-125">Çözüm **ve projeyi aynı dizindeki yerleştir** çözümve proje **işaretsiz** olduğundan emin olun (VS 2019) veya **çözüm için create directory** (VS 2017) **işaretlenir.**</span><span class="sxs-lookup"><span data-stu-id="ead32-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="ead32-126">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="ead32-127">Farklı ASP.NET çekirdek projeleri görüntüleyen pencerede **Web Uygulaması'nı** seçin ve ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="ead32-128">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="ead32-128">Prepare and understand the data</span></span>

<span data-ttu-id="ead32-129">[Vikipedi detoks dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)indirin.</span><span class="sxs-lookup"><span data-stu-id="ead32-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="ead32-130">Web sayfası açıldığında, sayfaya sağ tıklayın, **Farklı Kaydet'i** seçin ve dosyayı bilgisayarınızın herhangi bir yerine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ead32-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="ead32-131">*wikipedia-detox-250-line-data.tsv* veri kümesindeki her satır, Wikipedia'daki bir kullanıcı tarafından bırakılan farklı bir incelemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ead32-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="ead32-132">İlk sütun metnin duyarlılığını temsil eder (0 toksik değildir, 1 zehirlidir) ve ikinci sütun kullanıcı tarafından bırakılan yorumu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ead32-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="ead32-133">Sütunlar sekmelerle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ead32-133">The columns are separated by tabs.</span></span> <span data-ttu-id="ead32-134">Veriler aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="ead32-134">The data looks like the following:</span></span>

| <span data-ttu-id="ead32-135">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="ead32-135">Sentiment</span></span> | <span data-ttu-id="ead32-136">SentimentText</span><span class="sxs-lookup"><span data-stu-id="ead32-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="ead32-137">1</span><span class="sxs-lookup"><span data-stu-id="ead32-137">1</span></span> | <span data-ttu-id="ead32-138">== RUDE == Dostum, o carl resmini geri yükle, yoksa kabasın.</span><span class="sxs-lookup"><span data-stu-id="ead32-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="ead32-139">1</span><span class="sxs-lookup"><span data-stu-id="ead32-139">1</span></span> | <span data-ttu-id="ead32-140">== Tamam!</span><span class="sxs-lookup"><span data-stu-id="ead32-140">== OK!</span></span> <span data-ttu-id="ead32-141">== IM WILD ONES WIKI SONRA VANDALIZE OLACAK!!!</span><span class="sxs-lookup"><span data-stu-id="ead32-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="ead32-142">0</span><span class="sxs-lookup"><span data-stu-id="ead32-142">0</span></span> | <span data-ttu-id="ead32-143">Umarım yardımı olur.</span><span class="sxs-lookup"><span data-stu-id="ead32-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="ead32-144">Bir senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="ead32-144">Choose a scenario</span></span>

![Model Oluşturucu sihirbazı Visual Studio'da](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="ead32-146">Modelinizi eğitmek için Model Builder tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ead32-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="ead32-147">**Solution Explorer'da** *SentimentRazor* projesine sağ tıklayın ve**Machine Learning** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="ead32-148">Bu örnek için, senaryo duygu analizidir.</span><span class="sxs-lookup"><span data-stu-id="ead32-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="ead32-149">Model Oluşturucu aracının *senaryo* adımında, **Duyarlılık Analizi** senaryosunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="ead32-150">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="ead32-150">Load the data</span></span>

<span data-ttu-id="ead32-151">Model Oluşturucu, iki kaynaktan, bir SQL Server `csv` veritabanından veya yerel bir dosyadan veya `tsv` biçimdeki verileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ead32-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="ead32-152">Model Oluşturucu aracının veri adımında, veri kaynağı açılır tarafından **Dosya'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="ead32-153">Dosya metin kutusunu **seç'in** yanındaki düğmeyi seçin ve *wikipedia-detoks-250-line-data.tsv* dosyasına göz atmak ve seçmek için Dosya Gezgini'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="ead32-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="ead32-154">Sütundaki **Duygu'yu** seçin ve açılır düşüşü **tahmin edin (Etiket)** yazın.</span><span class="sxs-lookup"><span data-stu-id="ead32-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="ead32-155">**Giriş Sütunları (Özellikler)** açılır açılır açılır için varsayılan değerleri bırakın.</span><span class="sxs-lookup"><span data-stu-id="ead32-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="ead32-156">Model Oluşturucu aracında bir sonraki adıma geçmek için **Tren** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="ead32-157">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="ead32-157">Train the model</span></span>

<span data-ttu-id="ead32-158">Bu öğreticide duygu analizi modelini eğitmek için kullanılan makine öğrenme görevi ikili sınıflandırmadır.</span><span class="sxs-lookup"><span data-stu-id="ead32-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="ead32-159">Model eğitim işlemi sırasında Model Builder, veri setiniz için en iyi performans gösteren modeli bulmak için farklı ikili sınıflandırma algoritmaları ve ayarları kullanarak ayrı modeller eğitir.</span><span class="sxs-lookup"><span data-stu-id="ead32-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="ead32-160">Modelin eğitilmesi için gereken süre veri miktarıyla orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="ead32-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="ead32-161">Model Oluşturucu, veri kaynağınızın boyutuna bağlı **olarak, eğitme Süresi (saniye)** için varsayılan bir değer seçer.</span><span class="sxs-lookup"><span data-stu-id="ead32-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="ead32-162">Model Oluşturucu, **(saniye) eğitmek için Zamanın** değerini 10 saniyeye ayarlasa da, bunu 30 saniyeye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="ead32-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="ead32-163">Daha uzun bir süre için eğitim Model Builder algoritmaları ve en iyi modeli arama parametrelerinin kombinasyonu daha fazla sayıda keşfetmek için izin verir.</span><span class="sxs-lookup"><span data-stu-id="ead32-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="ead32-164">**Start Training'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-164">Select **Start Training**.</span></span>

    <span data-ttu-id="ead32-165">Eğitim süreci boyunca, ilerleme verileri tren `Progress` adımı bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ead32-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="ead32-166">Durum, eğitim sürecinin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ead32-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="ead32-167">En iyi doğruluk, Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren modelin doğruluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ead32-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="ead32-168">Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin ettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ead32-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="ead32-169">En iyi algoritma, Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ead32-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="ead32-170">Son algoritma, modeli eğitmek için Model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ead32-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="ead32-171">Eğitim tamamlandıktan sonra, bir sonraki adıma geçmek için **değerlendirme** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="ead32-172">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ead32-172">Evaluate the model</span></span>

<span data-ttu-id="ead32-173">Eğitim adımının sonucu en iyi performansa sahip bir model olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ead32-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="ead32-174">Model Oluşturucu aracının değerlendirme adımında, çıkış bölümü, **Best Model** Girişinde en iyi performans gösteren model tarafından kullanılan algoritmayı ve En İyi **Model Doğruluğu'ndaki**ölçümleri içerecektir.</span><span class="sxs-lookup"><span data-stu-id="ead32-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="ead32-175">Ayrıca, en iyi beş modeli ve bunların ölçümlerini içeren bir özet tablo.</span><span class="sxs-lookup"><span data-stu-id="ead32-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="ead32-176">Doğruluk ölçümlerinizden memnun değilseniz, model doğruluğunu geliştirmeyi denemenin ve geliştirmenin bazı kolay yolları, modeli eğitmek veya daha fazla veri kullanmak için gereken süreyi artırmakiçindir.</span><span class="sxs-lookup"><span data-stu-id="ead32-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="ead32-177">Aksi takdirde, Model Oluşturucu aracında son adıma geçmek için **kod** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="ead32-178">Tahminlerde bulunmak için kodu ekleme</span><span class="sxs-lookup"><span data-stu-id="ead32-178">Add the code to make predictions</span></span>

<span data-ttu-id="ead32-179">Eğitim süreci sonucunda iki proje oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="ead32-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="ead32-180">Eğitimli modele başvurun</span><span class="sxs-lookup"><span data-stu-id="ead32-180">Reference the trained model</span></span>

1. <span data-ttu-id="ead32-181">Model Oluşturucu aracının *kod* adımında, çözüme otomatik oluşturulan projeleri eklemek için **Projeler Ekle'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="ead32-182">Çözüm Gezgini'nde **Solution Explorer**aşağıdaki projeler görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ead32-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="ead32-183">*SentimentRazorML.ConsoleApp*: Model eğitimi ve tahmin kodunu içeren bir .NET Core Console uygulaması.</span><span class="sxs-lookup"><span data-stu-id="ead32-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="ead32-184">*SentimentRazorML.Model*: Giriş ve çıktı modeli verilerinin şemalarının yanı sıra eğitim sırasında en iyi performans gösteren modelin kaydedilmiş sürümünü tanımlayan veri modellerini içeren bir .NET Standart sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="ead32-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="ead32-185">Tahminler *sentimentrazor* web uygulaması yerine konsolda yapılacaktır, çünkü bu öğretici için, sadece *SentimentRazorML.Model* proje kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ead32-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="ead32-186">*SentimentRazorML.ConsoleApp* puanlama için kullanılmayacak olsa da, daha sonra yeni veriler kullanarak modeli yeniden eğitmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ead32-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="ead32-187">Yeniden eğitim olsa bu öğretici kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="ead32-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="ead32-188">PredictionEngine havuzunu yapılandırın</span><span class="sxs-lookup"><span data-stu-id="ead32-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="ead32-189">Tek bir tahmin yapmak için, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)bir .</span><span class="sxs-lookup"><span data-stu-id="ead32-189">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="ead32-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="ead32-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="ead32-191">Ayrıca, uygulamanız içinde gerekli olan her yerde bunun bir örneğini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ead32-191">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="ead32-192">Uygulamanız büyüdükçe, bu işlem yönetilemez hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="ead32-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="ead32-193">Daha iyi performans ve iş parçacığı güvenliği için, `PredictionEnginePool` uygulamanız boyunca [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) kullanılmak [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) üzere bir nesne oluşturan bağımlılık enjeksiyonu ve hizmetin bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ead32-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="ead32-194">*Microsoft.Extensions.ML* NuGet paketini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="ead32-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="ead32-195">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="ead32-196">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="ead32-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="ead32-197">**Gözat** sekmesini seçin ve **Microsoft.Extensions.ML**arayın.</span><span class="sxs-lookup"><span data-stu-id="ead32-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="ead32-198">Listedeki paketi seçin ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="ead32-199">**Değişiklikleri Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin</span><span class="sxs-lookup"><span data-stu-id="ead32-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="ead32-200">Listelenen paketlerin lisans koşullarını kabul **ederseniz, Lisans Kabul** iletişim kutusundaki **I Kabul** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ead32-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ead32-201">*SentimentRazor* projesindeki *Startup.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ead32-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="ead32-202">*Microsoft.Extensions.ML* NuGet paketi ve *SentimentRazorML.Model* projesine atıfta bulunmak için aşağıdaki ifadeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ead32-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="ead32-203">Eğitilen model dosyasının konumunu depolamak için genel bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ead32-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="ead32-204">Model dosyası, uygulamanızın derleme dosyalarının yanında yapı dizininde depolanır.</span><span class="sxs-lookup"><span data-stu-id="ead32-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="ead32-205">Erişimi kolaylaştırmak için, yöntemden `GetAbsolutePath` `Configure` sonra çağrılan bir yardımcı yöntemi oluşturun</span><span class="sxs-lookup"><span data-stu-id="ead32-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="ead32-206">'yi `GetAbsolutePath` `Startup` ayarlamak için sınıf oluşturucudaki yöntemi `_modelPath`kullanın.</span><span class="sxs-lookup"><span data-stu-id="ead32-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="ead32-207">`ConfigureServices` Uygulamanız `PredictionEnginePool` için yöntemi yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="ead32-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="ead32-208">Duyarlılık analizi işleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ead32-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="ead32-209">Tahminler uygulamanın ana sayfası içinde yapılacaktır.</span><span class="sxs-lookup"><span data-stu-id="ead32-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="ead32-210">Bu nedenle, kullanıcı girişi alır ve `PredictionEnginePool` bir tahmin dönmek için kullanan bir yöntem eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ead32-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="ead32-211">*Sayfalar* dizininde bulunan *Index.cshtml.cs* dosyasını açın ve aşağıdaki ifadeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ead32-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="ead32-212">`Startup` Sınıfta `PredictionEnginePool` yapılandırılan kullanımı için, kullanmak istediğiniz modelin oluşturucuiçine enjekte etmek zorunda.</span><span class="sxs-lookup"><span data-stu-id="ead32-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="ead32-213">`IndexModel` Sınıfın içine `PredictionEnginePool` başvurmak için bir değişken ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ead32-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="ead32-214">`IndexModel` Sınıfta bir oluşturucu oluşturun ve `PredictionEnginePool` hizmeti ona enjekte edin.</span><span class="sxs-lookup"><span data-stu-id="ead32-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="ead32-215">Web sayfasından alınan kullanıcı `PredictionEnginePool` girişinden öngörüler yapmak için bir yöntem işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ead32-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="ead32-216">Yöntemin `OnGet` altında, yeni bir yöntem oluşturmak`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="ead32-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="ead32-217">Yöntemin `OnGetAnalyzeSentiment` içinde, kullanıcıdan giriş boş veya null ise *Nötr* duyarlılığı döndürün.</span><span class="sxs-lookup"><span data-stu-id="ead32-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="ead32-218">Geçerli bir giriş göz önüne alındığında, yeni bir örnek `ModelInput`oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ead32-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="ead32-219">Duyguları `PredictionEnginePool` tahmin etmek için kullan.</span><span class="sxs-lookup"><span data-stu-id="ead32-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="ead32-220">Aşağıdaki kodla `bool` öngörülen değeri toksik veya toksik olmayan bir değere dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="ead32-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="ead32-221">Son olarak, duyguları web sayfasına geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="ead32-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="ead32-222">Web sayfasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ead32-222">Configure the web page</span></span>

<span data-ttu-id="ead32-223">Döndürülen `OnGetAnalyzeSentiment` sonuçlar `Index` web sayfasında dinamik olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ead32-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="ead32-224">*Pages* dizinindeki *Index.cshtml* dosyasını açın ve içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ead32-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="ead32-225">Ardından, *wwwroot\css* dizininde *site.css* sayfasının sonuna css stil kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ead32-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="ead32-226">Bundan sonra, web sayfasından `OnGetAnalyzeSentiment` işleyiciye giriş göndermek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ead32-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="ead32-227">*wwwroot\js* dizininde bulunan *site.js* dosyasında, `OnGetAnalyzeSentiment` işleyiciye `getSentiment` kullanıcı girişi yle GET HTTP isteği nde bulunmak için çağrılan bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ead32-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="ead32-228">Bunun altında, duyarlılık `updateMarker` tahmin edildiği gibi web sayfasında işaretçinin konumunu dinamik olarak güncelleştirmek için çağrılan başka bir işlev ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ead32-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="ead32-229">Kullanıcıdan giriş almak `updateSentiment` için çağrılan bir olay işleyicisi `OnGetAnalyzeSentiment` işlevi oluşturun, `getSentiment` işlevi kullanarak işleve gönderin ve işaretçiyi `updateMarker` işlek ile güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ead32-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="ead32-230">Son olarak, olay işleyicisini kaydedin `textarea` ve `id=Message` öznitelik ile öğeye bağla.</span><span class="sxs-lookup"><span data-stu-id="ead32-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="ead32-231">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ead32-231">Run the application</span></span>

<span data-ttu-id="ead32-232">Uygulamanız ayarlandığına göre, tarayıcınızda başlatılması gereken uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ead32-232">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="ead32-233">Uygulama başlatıldığında, *Model Oluşturucu girin serin!*</span><span class="sxs-lookup"><span data-stu-id="ead32-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="ead32-234">metin alanına.</span><span class="sxs-lookup"><span data-stu-id="ead32-234">into the text area.</span></span> <span data-ttu-id="ead32-235">Görüntülenen öngörülen duyarlılık *Toksik olmamalıdır.*</span><span class="sxs-lookup"><span data-stu-id="ead32-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Öngörülen duyarlılık penceresi ile çalışan pencere](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="ead32-237">Model Oluşturucu'nun oluşturduğu projeleri başka bir çözüm içinde daha sonra göndermeniz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` gerekiyorsa, bunları dizinin içinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ead32-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ead32-238">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ead32-238">Next steps</span></span>

<span data-ttu-id="ead32-239">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="ead32-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ead32-240">ASP.NET Core Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ead32-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="ead32-241">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="ead32-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="ead32-242">Bir senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="ead32-242">Choose a scenario</span></span>
> - <span data-ttu-id="ead32-243">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="ead32-243">Load the data</span></span>
> - <span data-ttu-id="ead32-244">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="ead32-244">Train the model</span></span>
> - <span data-ttu-id="ead32-245">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ead32-245">Evaluate the model</span></span>
> - <span data-ttu-id="ead32-246">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="ead32-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ead32-247">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ead32-247">Additional Resources</span></span>

<span data-ttu-id="ead32-248">Bu eğitimde bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:</span><span class="sxs-lookup"><span data-stu-id="ead32-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="ead32-249">Model Oluşturucu Senaryolar</span><span class="sxs-lookup"><span data-stu-id="ead32-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="ead32-250">İkili Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="ead32-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="ead32-251">İkili Sınıflandırma Modeli Ölçümleri</span><span class="sxs-lookup"><span data-stu-id="ead32-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-binary-classification)
