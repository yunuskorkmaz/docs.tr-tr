---
title: 'Öğretici: yaklaşım-ikili sınıflandırmayı çözümle'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir Razor Pages uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio 'da model Oluşturucu kullanır.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e919341130c6778207f324dd9eb3b3f54c8a9c68
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74551843"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="1f4c1-104">Öğretici: ML.NET model Oluşturucu kullanarak Web uygulamasındaki Web sitesindeki açıklamaları çözümleme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="1f4c1-105">Bir Web uygulamasının içinde gerçek zamanlı açıklamalardan yaklaşımı çözümleme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="1f4c1-106">Bu öğreticide, Web sitesi açıklamalarından gerçek zamanlı olarak yaklaşım sınıflandıran bir ASP.NET Core Razor Pages uygulamasının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="1f4c1-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="1f4c1-108">ASP.NET Core Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="1f4c1-109">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="1f4c1-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="1f4c1-110">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="1f4c1-110">Choose a scenario</span></span>
> - <span data-ttu-id="1f4c1-111">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-111">Load the data</span></span>
> - <span data-ttu-id="1f4c1-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-112">Train the model</span></span>
> - <span data-ttu-id="1f4c1-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-113">Evaluate the model</span></span>
> - <span data-ttu-id="1f4c1-114">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="1f4c1-115">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="1f4c1-116">Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="1f4c1-117">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="1f4c1-117">Pre-requisites</span></span>

<span data-ttu-id="1f4c1-118">Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="1f4c1-119">Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="1f4c1-120">ASP.NET Core bir **Razor Pages uygulaması**oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="1f4c1-121">Visual Studio 'Yu açın ve menü çubuğundan **dosya > yeni > projesi** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="1f4c1-122">Yeni proje iletişim kutusunda, **Visual C#**  düğümünü ve ardından **Web** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="1f4c1-123">**ASP.NET Core Web uygulaması** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="1f4c1-124">**Ad** metin kutusuna "SentimentRazor" yazın.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="1f4c1-125">**Çözümün ve projenin aynı dizine yerleştirdiğinizden** emin **olun (vs** 2019) veya **çözüm için dizin oluşturma** **denetlenir** (vs 2017).</span><span class="sxs-lookup"><span data-stu-id="1f4c1-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="1f4c1-126">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="1f4c1-127">Pencerede farklı ASP.NET Core proje türlerini görüntüleyen **Web uygulaması** ' nı seçin ve ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="1f4c1-128">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="1f4c1-128">Prepare and understand the data</span></span>

<span data-ttu-id="1f4c1-129">[Vikipedi Detox veri kümesini](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)indirin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="1f4c1-130">Web sayfası açıldığında, sayfaya sağ tıklayın, **farklı kaydet** ' i seçin ve dosyayı bilgisayarınızda herhangi bir yere kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="1f4c1-131">*Vivtox-250-Line-Data. tsv* veri kümesindeki her satır, visede bir kullanıcı tarafından bırakılan farklı bir gözden geçirmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="1f4c1-132">İlk sütun metnin (0-Toxic, 1 ' in Toxic) yaklaşımını temsil eder ve ikinci sütun Kullanıcı tarafından bırakılan yorumu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="1f4c1-133">Sütunlar sekmelerle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-133">The columns are separated by tabs.</span></span> <span data-ttu-id="1f4c1-134">Veriler aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-134">The data looks like the following:</span></span>

| <span data-ttu-id="1f4c1-135">yaklaşım</span><span class="sxs-lookup"><span data-stu-id="1f4c1-135">Sentiment</span></span> | <span data-ttu-id="1f4c1-136">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="1f4c1-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="1f4c1-137">1\.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-137">1</span></span> | <span data-ttu-id="1f4c1-138">= = İşlenmemiş = = dude, o Carl resmini geri yüklemeniz veya başka bir şey yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="1f4c1-139">1\.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-139">1</span></span> | <span data-ttu-id="1f4c1-140">= = TAMAM!</span><span class="sxs-lookup"><span data-stu-id="1f4c1-140">== OK!</span></span> <span data-ttu-id="1f4c1-141">= = ıM, DAHA SONRA BIR WIKI 'YI DAHA SONRA!!!</span><span class="sxs-lookup"><span data-stu-id="1f4c1-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="1f4c1-142">0</span><span class="sxs-lookup"><span data-stu-id="1f4c1-142">0</span></span> | <span data-ttu-id="1f4c1-143">Bunu umuyoruz.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="1f4c1-144">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="1f4c1-144">Choose a scenario</span></span>

![Visual Studio 'da model Oluşturucu Sihirbazı](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="1f4c1-146">Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="1f4c1-147">**Çözüm Gezgini**, *SentimentRazor* projesine sağ tıklayın ve > **Ekle** **Machine Learning**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="1f4c1-148">Bu örnek için senaryo, yaklaşım analiziydi.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="1f4c1-149">Model Oluşturucu aracının *senaryo* adımında **yaklaşım Analizi** senaryosunu seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="1f4c1-150">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-150">Load the data</span></span>

<span data-ttu-id="1f4c1-151">Model Oluşturucu, bir SQL Server veritabanı veya `csv` veya `tsv` biçimindeki yerel bir dosya olan iki kaynaktan verileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="1f4c1-152">Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden **Dosya** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="1f4c1-153">**Dosya seçin** metin kutusunun yanındaki düğmeyi seçin ve dosya Gezgini 'ni kullanarak, *vibtox-250-Line-Data. tsv* dosyasına gidin ve seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="1f4c1-154">**Tahmin edilecek sütun (etiket)** açılan **listesini seçin.**</span><span class="sxs-lookup"><span data-stu-id="1f4c1-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="1f4c1-155">**Giriş sütunları (Özellikler)** açılır menüsü için varsayılan değerleri bırakın.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="1f4c1-156">Model Oluşturucu aracında bir sonraki adıma geçmek için **eğitme** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="1f4c1-157">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-157">Train the model</span></span>

<span data-ttu-id="1f4c1-158">Bu öğreticide yaklaşım Analizi modelini eğitmek için kullanılan makine öğrenimi görevi ikili sınıflandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="1f4c1-159">Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı ikili sınıflandırma algoritmalarını ve ayarlarını kullanarak modelleri ayrı ayrı işler.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="1f4c1-160">Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="1f4c1-161">Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="1f4c1-162">Model Oluşturucu değeri, " **saniye)** ila 10 saniye arasında bir süre olarak ayarlasa da, 30 saniyeye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="1f4c1-163">Daha uzun bir süre için eğitim, model oluşturucunun en iyi modeli aramada daha fazla sayıda algoritmaların ve parametrelerin birleşimini keşfetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="1f4c1-164">**Eğitimi Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-164">Select **Start Training**.</span></span>

    <span data-ttu-id="1f4c1-165">Eğitim süreci boyunca, ilerleme verileri eğitme adımının `Progress` bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="1f4c1-166">Durum, eğitim sürecinin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="1f4c1-167">En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="1f4c1-168">Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="1f4c1-169">En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="1f4c1-170">Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="1f4c1-171">Eğitim tamamlandıktan sonra bir sonraki adıma geçmek için bağlantıyı **değerlendir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="1f4c1-172">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-172">Evaluate the model</span></span>

<span data-ttu-id="1f4c1-173">Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="1f4c1-174">Model Oluşturucu aracının değerlendir adımında, çıkış **bölümü en iyi model girişinde en** iyi işlem modeli tarafından kullanılan algoritmayı ve **En Iyi model doğruluğunun**ölçümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="1f4c1-175">Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="1f4c1-176">Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu denemeye yönelik bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="1f4c1-177">Aksi takdirde, model Oluşturucu aracında son adıma geçmek için **kod** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="1f4c1-178">Tahminleri yapmak için kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="1f4c1-178">Add the code to make predictions</span></span>

<span data-ttu-id="1f4c1-179">Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="1f4c1-180">Eğitilen modele başvur</span><span class="sxs-lookup"><span data-stu-id="1f4c1-180">Reference the trained model</span></span>

1. <span data-ttu-id="1f4c1-181">Model Oluşturucu aracının *kod* adımında, otomatik olarak oluşturulan projeleri çözüme eklemek Için **Proje Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="1f4c1-182">Aşağıdaki projeler **Çözüm Gezgini**görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="1f4c1-183">*SentimentRazorML. ConsoleApp*: model eğitimi ve tahmin kodunu içeren bir .NET Core konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="1f4c1-184">*SentimentRazorML. model*: giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini ve eğitim sırasında en iyi uygulanan modelin kaydedilmiş sürümünü içeren .NET Standard bir sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="1f4c1-185">Bu öğretici için, *SentimentRazorML. model* projesi yalnızca, tahmine dayalı olarak konsolu yerine *SentimentRazor* Web uygulamasında yapılabilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="1f4c1-186">*SentimentRazorML. ConsoleApp* , Puanlama için kullanılmayacak olsa da, daha sonra yeni verileri kullanarak modeli yeniden eğitebilmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="1f4c1-187">Yeniden eğitim, Bu öğreticinin kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="1f4c1-188">PredictionEngine havuzunu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="1f4c1-189">Tek bir tahmin yapmak için bir [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-189">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="1f4c1-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="1f4c1-191">Ayrıca, uygulamanızın içinde gerek duyduğu her yerde bir örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-191">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="1f4c1-192">Uygulamanız büyüdükçe, bu işlem yönetilebilir hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="1f4c1-193">Daha iyi performans ve iş parçacığı güvenliği için, uygulamanız genelinde kullanılmak üzere [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnelerinin bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) oluşturan bağımlılık ekleme ve `PredictionEnginePool` hizmeti birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="1f4c1-194">*Microsoft.Extensions.ml* NuGet paketini yükler:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="1f4c1-195">**Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="1f4c1-196">Paket kaynağı olarak "nuget.org" öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="1f4c1-197">**Araştır** sekmesini seçin ve **Microsoft.Extensions.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="1f4c1-198">Listeden paketi seçin ve ardından **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="1f4c1-199">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin</span><span class="sxs-lookup"><span data-stu-id="1f4c1-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="1f4c1-200">Listelenen paketlerin lisans koşullarını kabul ediyorsanız, **Lisans kabulü** Iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="1f4c1-201">*SentimentRazor* projesindeki *Startup.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="1f4c1-202">*Microsoft.Extensions.ml* NuGet paketini ve *SentimentRazorML. model* projesine başvurmak için aşağıdaki using deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="1f4c1-203">Eğitilen model dosyasının konumunu depolamak için genel bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="1f4c1-204">Model dosyası, uygulamanızın derleme dosyalarının yanı sıra derleme dizininde depolanır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="1f4c1-205">Daha kolay erişim sağlamak için, `Configure` yönteminden sonra `GetAbsolutePath` adlı bir yardımcı yöntem oluşturun</span><span class="sxs-lookup"><span data-stu-id="1f4c1-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="1f4c1-206">`_modelPath`ayarlamak için `Startup` sınıf oluşturucusunda `GetAbsolutePath` yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="1f4c1-207">`ConfigureServices` yönteminde uygulamanız için `PredictionEnginePool` yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="1f4c1-208">Yaklaşım Analizi işleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="1f4c1-209">Tahmine dayalı, uygulamanın ana sayfasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="1f4c1-210">Bu nedenle, Kullanıcı girişini alan ve bir tahmin eklenmesi için `PredictionEnginePool` kullanan bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="1f4c1-211">*Pages* dizininde bulunan *Index.cshtml.cs* dosyasını açın ve aşağıdaki using deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="1f4c1-212">`Startup` sınıfında yapılandırılan `PredictionEnginePool` kullanmak için, bu dosyayı kullanmak istediğiniz modelin oluşturucusuna eklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="1f4c1-213">`IndexModel` sınıfının içindeki `PredictionEnginePool` başvurmak için bir değişken ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="1f4c1-214">`IndexModel` sınıfında bir Oluşturucu oluşturun ve `PredictionEnginePool` hizmetini ona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="1f4c1-215">Web sayfasından alınan Kullanıcı girişinden tahminleri yapmak için `PredictionEnginePool` kullanan bir yöntem işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="1f4c1-216">`OnGet` yönteminin altında, adlı yeni bir yöntem oluşturun `OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="1f4c1-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="1f4c1-217">`OnGetAnalyzeSentiment` yönteminin içinde, kullanıcının girişi boş veya null olduğunda *nötr* yaklaşım döndürün.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="1f4c1-218">Geçerli bir giriş verildiğinde `ModelInput`yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="1f4c1-219">Yaklaşımı tahmin etmek için `PredictionEnginePool` kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="1f4c1-220">Tahmin edilen `bool` değerini, aşağıdaki kodla Toxic öğesine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="1f4c1-221">Son olarak, yaklaşımı Web sayfasına geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="1f4c1-222">Web sayfasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-222">Configure the web page</span></span>

<span data-ttu-id="1f4c1-223">`OnGetAnalyzeSentiment` tarafından döndürülen sonuçlar, `Index` Web sayfasında dinamik olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="1f4c1-224">*Pages* dizinindeki *Index. cshtml* dosyasını açın ve içeriğini şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="1f4c1-225">Ardından, *wwwroot\css* dizinindeki *site. css* sayfasının sonuna CSS stil oluşturma kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="1f4c1-226">Bundan sonra, Web sayfasından `OnGetAnalyzeSentiment` işleyicisine giriş göndermek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="1f4c1-227">*Wwwroot\js* dizininde bulunan *site. js* dosyasında, `OnGetAnalyzeSentiment` IŞLEYICISINE Kullanıcı GIRIŞIYLE bir HTTP isteği almak için `getSentiment` adlı bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="1f4c1-228">Bunun altında, yaklaşım tahmin edildiğinde Web sayfasındaki işaretin konumunu dinamik olarak güncelleştirmek için `updateMarker` adlı başka bir işlev ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="1f4c1-229">Kullanıcıdan girişi almak için `updateSentiment` adlı bir olay işleyici işlevi oluşturun, `getSentiment` işlevini kullanarak `OnGetAnalyzeSentiment` işlevine gönderin ve işaretçiyi `updateMarker` işleviyle güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="1f4c1-230">Son olarak, olay işleyicisini kaydedin ve `id=Message` özniteliğiyle `textarea` öğesine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="1f4c1-231">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-231">Run the application</span></span>

<span data-ttu-id="1f4c1-232">Uygulamanız ayarlandığına göre, tarayıcınızda başlatması gereken uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-232">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="1f4c1-233">Uygulama başlatıldığında, *model Oluşturucu* seyrek erişimli yazın!</span><span class="sxs-lookup"><span data-stu-id="1f4c1-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="1f4c1-234">metin alanına.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-234">into the text area.</span></span> <span data-ttu-id="1f4c1-235">Görünen tahmini yaklaşım, *Toxic*olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Tahmin edilen yaklaşım penceresiyle pencere çalıştırma](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="1f4c1-237">Model Oluşturucu tarafından oluşturulan projelere daha sonra başka bir çözümün içinde başvurulmaları gerekiyorsa, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizin içinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f4c1-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f4c1-238">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1f4c1-238">Next steps</span></span>

<span data-ttu-id="1f4c1-239">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1f4c1-240">ASP.NET Core Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="1f4c1-241">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="1f4c1-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="1f4c1-242">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="1f4c1-242">Choose a scenario</span></span>
> - <span data-ttu-id="1f4c1-243">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-243">Load the data</span></span>
> - <span data-ttu-id="1f4c1-244">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-244">Train the model</span></span>
> - <span data-ttu-id="1f4c1-245">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1f4c1-245">Evaluate the model</span></span>
> - <span data-ttu-id="1f4c1-246">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1f4c1-247">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1f4c1-247">Additional Resources</span></span>

<span data-ttu-id="1f4c1-248">Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:</span><span class="sxs-lookup"><span data-stu-id="1f4c1-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="1f4c1-249">Model Oluşturucu senaryoları</span><span class="sxs-lookup"><span data-stu-id="1f4c1-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="1f4c1-250">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="1f4c1-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="1f4c1-251">İkili sınıflandırma modeli ölçümleri</span><span class="sxs-lookup"><span data-stu-id="1f4c1-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)
