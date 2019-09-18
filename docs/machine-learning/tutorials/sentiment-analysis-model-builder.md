---
title: 'Öğretici: Yaklaşım-ikili sınıflandırmayı çözümle'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir Razor Pages uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio 'da model Oluşturucu kullanır.
ms.date: 09/13/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6184e097daf4604173db9e2a34606e68eb0fdc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054323"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="c6045-104">Öğretici: ML.NET model Oluşturucu kullanarak Web uygulamasındaki Web sitesindeki açıklamaları çözümleme</span><span class="sxs-lookup"><span data-stu-id="c6045-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="c6045-105">Bir Web uygulamasının içinde gerçek zamanlı açıklamalardan yaklaşımı çözümleme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="c6045-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="c6045-106">Bu öğreticide, Web sitesi açıklamalarından gerçek zamanlı olarak yaklaşım sınıflandıran bir ASP.NET Core Razor Pages uygulamasının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6045-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="c6045-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="c6045-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="c6045-108">ASP.NET Core Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6045-108">Create an ASP.NET Core Razor Pages application</span></span>
> * <span data-ttu-id="c6045-109">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="c6045-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="c6045-110">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="c6045-110">Choose a scenario</span></span>
> * <span data-ttu-id="c6045-111">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="c6045-111">Load the data</span></span>
> * <span data-ttu-id="c6045-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c6045-112">Train the model</span></span>
> * <span data-ttu-id="c6045-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c6045-113">Evaluate the model</span></span>
> * <span data-ttu-id="c6045-114">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="c6045-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="c6045-115">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="c6045-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="c6045-116">Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6045-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="c6045-117">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="c6045-117">Pre-requisites</span></span>

<span data-ttu-id="c6045-118">Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="c6045-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="c6045-119">Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6045-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="c6045-120">ASP.NET Core bir **Razor Pages uygulaması**oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6045-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="c6045-121">Visual Studio 'Yu açın ve menü çubuğundan **dosya > yeni > projesi** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span> 
    1. <span data-ttu-id="c6045-122">Yeni proje iletişim kutusunda, **Visual C#**  düğümünü ve ardından **Web** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> 
    1. <span data-ttu-id="c6045-123">**ASP.NET Core Web uygulaması** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-123">Then select the **ASP.NET Core Web Application** project template.</span></span> 
    1. <span data-ttu-id="c6045-124">**Ad** metin kutusuna "SentimentRazor" yazın.</span><span class="sxs-lookup"><span data-stu-id="c6045-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="c6045-125">**Çözüm için dizin oluşturma** onay kutusu varsayılan olarak denetlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c6045-125">The **Create a directory for solution** checkbox should be checked by default.</span></span> <span data-ttu-id="c6045-126">Böyle bir durum söz konusu değilse, kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="c6045-126">If that's not the case, check it.</span></span> 
    1. <span data-ttu-id="c6045-127">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-127">Select the **OK** button.</span></span>
    1. <span data-ttu-id="c6045-128">Pencerede farklı ASP.NET Core proje türlerini görüntüleyen **Web uygulaması** ' nı seçin ve ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-128">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="c6045-129">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="c6045-129">Prepare and understand the data</span></span>

<span data-ttu-id="c6045-130">[Vikipedi Detox veri kümesini](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)indirin.</span><span class="sxs-lookup"><span data-stu-id="c6045-130">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="c6045-131">Web sayfası açıldığında, sayfaya sağ tıklayın, **farklı kaydet** ' i seçin ve dosyayı bilgisayarınızda herhangi bir yere kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c6045-131">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span> 

<span data-ttu-id="c6045-132">*Vivtox-250-Line-Data. tsv* veri kümesindeki her satır, visede bir kullanıcı tarafından bırakılan farklı bir gözden geçirmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6045-132">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="c6045-133">İlk sütun metnin (0-Toxic, 1 ' in Toxic) yaklaşımını temsil eder ve ikinci sütun Kullanıcı tarafından bırakılan yorumu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6045-133">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="c6045-134">Sütunlar sekmelerle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c6045-134">The columns are separated by tabs.</span></span> <span data-ttu-id="c6045-135">Veriler aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="c6045-135">The data looks like the following:</span></span>

| <span data-ttu-id="c6045-136">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="c6045-136">Sentiment</span></span> | <span data-ttu-id="c6045-137">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="c6045-137">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="c6045-138">1\.</span><span class="sxs-lookup"><span data-stu-id="c6045-138">1</span></span> | <span data-ttu-id="c6045-139">= = İşlenmemiş = = dude, o Carl resmini geri yüklemeniz veya başka bir şey yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6045-139">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="c6045-140">1\.</span><span class="sxs-lookup"><span data-stu-id="c6045-140">1</span></span> | <span data-ttu-id="c6045-141">= = TAMAM!</span><span class="sxs-lookup"><span data-stu-id="c6045-141">== OK!</span></span> <span data-ttu-id="c6045-142">= = IM, DAHA SONRA BIR WIKI 'YI DAHA SONRA!!!</span><span class="sxs-lookup"><span data-stu-id="c6045-142">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="c6045-143">0</span><span class="sxs-lookup"><span data-stu-id="c6045-143">0</span></span> | <span data-ttu-id="c6045-144">Bunu umuyoruz.</span><span class="sxs-lookup"><span data-stu-id="c6045-144">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="c6045-145">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="c6045-145">Choose a scenario</span></span>

![](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="c6045-146">Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6045-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> 

1. <span data-ttu-id="c6045-147">**Çözüm Gezgini**, *SentimentRazor* projesine sağ tıklayın ve**Machine Learning** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="c6045-148">Bu örnek için senaryo, yaklaşım analiziydi.</span><span class="sxs-lookup"><span data-stu-id="c6045-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="c6045-149">Model Oluşturucu aracının *senaryo* adımında **yaklaşım Analizi** senaryosunu seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="c6045-150">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="c6045-150">Load the data</span></span>

<span data-ttu-id="c6045-151">Model Oluşturucu iki kaynaktan (bir SQL Server veritabanı ya da yerel bir dosya `csv` ) veya `tsv` biçimdeki verileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c6045-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="c6045-152">Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden **Dosya** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="c6045-153">**Dosya seçin** metin kutusunun yanındaki düğmeyi seçin ve dosya Gezgini 'ni kullanarak, *vibtox-250-Line-Data. tsv* dosyasına gidin ve seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="c6045-154">Açılan menüyü **tahmin etmek Için etiket veya sütundaki** **yaklaşımı seçin**</span><span class="sxs-lookup"><span data-stu-id="c6045-154">Choose **Sentiment** in the **Label or Column to Predict** dropdown</span></span>
1. <span data-ttu-id="c6045-155">Model Oluşturucu aracında bir sonraki adıma geçmek için **eğitme** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-155">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="c6045-156">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c6045-156">Train the model</span></span>

<span data-ttu-id="c6045-157">Bu öğreticide fiyat tahmin modelini eğitmek için kullanılan makine öğrenimi görevi ikili sınıflandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c6045-157">The machine learning task used to train the price prediction model in this tutorial is binary classification.</span></span> <span data-ttu-id="c6045-158">Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı ikili sınıflandırma algoritmalarını ve ayarlarını kullanarak modelleri ayrı ayrı işler.</span><span class="sxs-lookup"><span data-stu-id="c6045-158">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="c6045-159">Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı.</span><span class="sxs-lookup"><span data-stu-id="c6045-159">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="c6045-160">Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer.</span><span class="sxs-lookup"><span data-stu-id="c6045-160">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span> 

1. <span data-ttu-id="c6045-161">Model Oluşturucu değeri, " **saniye)** ila 10 saniye arasında bir süre olarak ayarlasa da, 30 saniyeye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="c6045-161">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="c6045-162">Daha uzun bir süre için eğitim, model oluşturucunun en iyi modeli aramada daha fazla sayıda algoritmaların ve parametrelerin birleşimini keşfetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c6045-162">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="c6045-163">**Eğitimi Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-163">Select **Start Training**.</span></span>

    <span data-ttu-id="c6045-164">Eğitim süreci boyunca, ilerleme verileri eğitme adımının `Progress` bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c6045-164">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="c6045-165">Durum, eğitim sürecinin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c6045-165">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="c6045-166">En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6045-166">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="c6045-167">Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c6045-167">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="c6045-168">En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c6045-168">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="c6045-169">Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c6045-169">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="c6045-170">Eğitim tamamlandıktan sonra bir sonraki adıma geçmek için bağlantıyı **değerlendir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-170">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="c6045-171">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c6045-171">Evaluate the model</span></span>

<span data-ttu-id="c6045-172">Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c6045-172">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="c6045-173">Model Oluşturucu aracının değerlendir adımında, çıkış bölümü en iyi **model girişinde en** iyi işlem modeli tarafından kullanılan algoritmayı **(RKARE)** içerir.</span><span class="sxs-lookup"><span data-stu-id="c6045-173">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Quality (RSquared)**.</span></span> <span data-ttu-id="c6045-174">Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu.</span><span class="sxs-lookup"><span data-stu-id="c6045-174">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="c6045-175">Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu denemeye yönelik bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="c6045-175">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="c6045-176">Aksi takdirde, model Oluşturucu aracında son adıma geçmek için **kod** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-176">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="c6045-177">Tahminleri yapmak için kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="c6045-177">Add the code to make predictions</span></span>

<span data-ttu-id="c6045-178">Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="c6045-178">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="c6045-179">Eğitilen modele başvur</span><span class="sxs-lookup"><span data-stu-id="c6045-179">Reference the trained model</span></span>

1. <span data-ttu-id="c6045-180">Model Oluşturucu aracının *kod* adımında, otomatik olarak oluşturulan projeleri çözüme eklemek Için **Proje Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-180">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="c6045-181">Aşağıdaki projeler **Çözüm Gezgini**görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="c6045-181">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="c6045-182">*SentimentRazorML. ConsoleApp*: Model eğitimi ve tahmin kodunu içeren bir .NET Core konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="c6045-182">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="c6045-183">*SentimentRazorML. model*: Eğitim sırasında en iyi gerçekleştirme modelinin kalıcı sürümü ve giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini içeren .NET Standard sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="c6045-183">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

    <span data-ttu-id="c6045-184">Bu öğretici için, *SentimentRazorML. model* projesi yalnızca, tahmine dayalı olarak konsolu yerine *SentimentRazor* Web uygulamasında yapılabilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6045-184">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="c6045-185">*SentimentRazorML. ConsoleApp* , Puanlama için kullanılmayacak olsa da, daha sonra yeni verileri kullanarak modeli yeniden eğitebilmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6045-185">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="c6045-186">Yeniden eğitim, Bu öğreticinin kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="c6045-186">Retraining is outside the scope of this tutorial though.</span></span>

1. <span data-ttu-id="c6045-187">Razor Pages uygulamanızın içinde eğitilen modeli kullanmak için, *SentimentRazorML. model* projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6045-187">To use the trained model inside your Razor Pages application, add a reference to the *SentimentRazorML.Model* project.</span></span>

    1. <span data-ttu-id="c6045-188">**SentimentRazor** projesi öğesine sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6045-188">Right-click **SentimentRazor** project.</span></span> 
    1. <span data-ttu-id="c6045-189">**> başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-189">Select **Add > Reference**.</span></span> 
    1. <span data-ttu-id="c6045-190">**Projeler > çözüm** düğümünü seçin ve listeden **SentimentRazorML. model** projesini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="c6045-190">Choose the **Projects > Solution** node and from the list, check the **SentimentRazorML.Model** project.</span></span>
    1. <span data-ttu-id="c6045-191">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-191">Select **OK**.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="c6045-192">PredictionEngine havuzunu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c6045-192">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="c6045-193">Tek bir tahmin yapmak için kullanın [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="c6045-193">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="c6045-194">Uygulamanızda kullanabilmeniz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, gerektiğinde oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6045-194">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application, you must create it when it's needed.</span></span> <span data-ttu-id="c6045-195">Bu durumda, dikkate alınması gereken en iyi yöntem bağımlılık ekleme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="c6045-195">In that case, a best practice to consider is dependency injection.</span></span>

> [!WARNING]
> <span data-ttu-id="c6045-196">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="c6045-196">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="c6045-197">Gelişmiş performans ve iş parçacığı güvenliği için, uygulama `PredictionEnginePool` kullanımı için `PredictionEngine` bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) nesne oluşturan hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6045-197">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="c6045-198">[ASP.NET Core içinde nesne havuzları `PredictionEngine` oluşturma ve kullanma](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)hakkında daha fazla bilgi edinmek için aşağıdaki blog gönderisini okuyun.</span><span class="sxs-lookup"><span data-stu-id="c6045-198">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

1. <span data-ttu-id="c6045-199">*Microsoft.Extensions.ml* NuGet paketini yükler:</span><span class="sxs-lookup"><span data-stu-id="c6045-199">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="c6045-200">**Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-200">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> 
    1. <span data-ttu-id="c6045-201">Paket kaynağı olarak "nuget.org" öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-201">Choose "nuget.org" as the Package source.</span></span> 
    1. <span data-ttu-id="c6045-202">**Araştır** sekmesini seçin ve **Microsoft.Extensions.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="c6045-202">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span> 
    1. <span data-ttu-id="c6045-203">Listeden paketi seçin ve ardından **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-203">Select the package in the list, and select the **Install** button.</span></span> 
    1. <span data-ttu-id="c6045-204">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin</span><span class="sxs-lookup"><span data-stu-id="c6045-204">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="c6045-205">Listelenen paketlerin lisans koşullarını kabul ediyorsanız, **Lisans kabulü** Iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c6045-205">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> 

1. <span data-ttu-id="c6045-206">*SentimentRazor* projesindeki *Startup.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c6045-206">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="c6045-207">*Microsoft.Extensions.ml* NuGet paketini ve *SentimentRazorML. model* projesine başvurmak için aşağıdaki using deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6045-207">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L12-L14)]        

1. <span data-ttu-id="c6045-208">Eğitilen model dosyasının konumunu depolamak için genel bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6045-208">Create a global variable to store the location of the trained model file.</span></span>

    [!code-csharp [ModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L20)]

1. <span data-ttu-id="c6045-209">Model dosyası, uygulamanızın derleme dosyalarının yanı sıra derleme dizininde depolanır.</span><span class="sxs-lookup"><span data-stu-id="c6045-209">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="c6045-210">Daha kolay erişim sağlamak için, `GetAbsolutePath` `Configure` yönteminden sonra adlı bir yardımcı yöntem oluşturun</span><span class="sxs-lookup"><span data-stu-id="c6045-210">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    [!code-csharp [GetAbsolutePathMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L66-L73)]

1. <span data-ttu-id="c6045-211">Öğesini ayarlamak için `Startup` `GetAbsolutePath` sınıf`_modelPath`oluşturucusunda metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6045-211">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    [!code-csharp [InitModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L25)]

1. <span data-ttu-id="c6045-212">`ConfigureServices` Yöntemi için `PredictionEnginePool` uygulamanızı için yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="c6045-212">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    [!code-csharp [InitPredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L42)]

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="c6045-213">Yaklaşım Analizi işleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6045-213">Create sentiment analysis handler</span></span>

<span data-ttu-id="c6045-214">Tahmine dayalı, uygulamanın ana sayfasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="c6045-214">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="c6045-215">Bu nedenle, Kullanıcı girişini alan ve bir tahmin eklenmesi `PredictionEnginePool` için kullanması gereken bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="c6045-215">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="c6045-216">*Pages* dizininde bulunan *Index.cshtml.cs* dosyasını açın ve aşağıdaki using deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6045-216">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    [!code-csharp [IndexUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L7-L8)]

    <span data-ttu-id="c6045-217">`PredictionEnginePool` Sınıfında yapılandırılan`Startup` ' ı kullanmak için, onu kullanmak istediğiniz modelin oluşturucusuna eklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6045-217">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span> 

1. <span data-ttu-id="c6045-218">`PredictionEnginePool` Sınıfının içine başvurmak için bir değişken ekleyin. `IndexModel`</span><span class="sxs-lookup"><span data-stu-id="c6045-218">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    [!code-csharp [PredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L14)]

1. <span data-ttu-id="c6045-219">`IndexModel` Sınıfında bir Oluşturucu oluşturun ve `PredictionEnginePool` hizmeti ona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6045-219">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    [!code-csharp [IndexConstructor](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L16-L19)]

1. <span data-ttu-id="c6045-220">Web sayfasından alınan Kullanıcı girişinden tahminleri yapmak `PredictionEnginePool` için öğesini kullanan bir yöntem işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6045-220">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="c6045-221">`OnGet` Yönteminin altında, adlı yeni bir yöntem oluşturun`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="c6045-221">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="c6045-222">Yöntemi içinde, kullanıcının girişi boş veya null olduğunda nötr yaklaşım döndürün. `OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="c6045-222">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L28)] 
    
    1. <span data-ttu-id="c6045-223">Geçerli bir giriş verildiğinde yeni bir örneğini `ModelInput`oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6045-223">Given a valid input, create a new instance of `ModelInput`.</span></span> 

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L29)] 

    1. <span data-ttu-id="c6045-224">Yaklaşımı tahmin `PredictionEnginePool` etmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6045-224">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        [!code-csharp [MakePrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L30)] 

    1. <span data-ttu-id="c6045-225">Tahmin `bool` edilen değeri, aşağıdaki kodla birlikte Toxic öğesine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="c6045-225">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        [!code-csharp [ConvertPrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L31)]

    1. <span data-ttu-id="c6045-226">Son olarak, yaklaşımı Web sayfasına geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="c6045-226">Finally, return the sentiment back to the web page.</span></span>

        [!code-csharp [ReturnSentiment](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L32)]

### <a name="configure-the-web-page"></a><span data-ttu-id="c6045-227">Web sayfasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c6045-227">Configure the web page</span></span>

<span data-ttu-id="c6045-228">Tarafından döndürülen sonuçlar, `OnGetAnalyzeSentiment` `Index` Web sayfasında dinamik olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c6045-228">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="c6045-229">*Pages* dizinindeki *Index. cshtml* dosyasını açın ve içeriğini şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c6045-229">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span> 

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="c6045-230">Ardından, *wwwroot\css* dizinindeki *site. css* sayfasının sonuna CSS stil oluşturma kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6045-230">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="c6045-231">Bundan sonra, Web sayfasından `OnGetAnalyzeSentiment` işleyiciye giriş göndermek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6045-231">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="c6045-232">*Wwwroot\js* dizininde bulunan *site. js* dosyasında, `OnGetAnalyzeSentiment` işleyiciye Kullanıcı girişiyle bir http isteği almak için `getSentiment` adlı bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6045-232">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="c6045-233">Bunun altında, yaklaşım tahmin edildiğinde Web `updateMarker` sayfasındaki işaretin konumunu dinamik olarak güncelleştirmek için adlı başka bir işlev ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6045-233">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="c6045-234">Kullanıcıdan girişi almak `updateSentiment` için çağrılan bir olay işleyici işlevi oluşturun, `getSentiment` işlevi kullanarak `OnGetAnalyzeSentiment` işleve gönderin ve işaretleyiciyi `updateMarker` işlevle güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c6045-234">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="c6045-235">Son olarak, olay işleyicisini kaydedin ve `textarea` `id=Message` özniteliği ile öğesine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="c6045-235">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="c6045-236">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c6045-236">Run the application</span></span>

<span data-ttu-id="c6045-237">Uygulamanız ayarlandığına göre, tarayıcınızda başlatması gereken uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c6045-237">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="c6045-238">Uygulama başlatıldığında, *model Oluşturucu* seyrek erişimli yazın!</span><span class="sxs-lookup"><span data-stu-id="c6045-238">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="c6045-239">metin alanına.</span><span class="sxs-lookup"><span data-stu-id="c6045-239">into the text area.</span></span> <span data-ttu-id="c6045-240">Görünen tahmini yaklaşım, *Toxic*olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6045-240">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="c6045-241">Model Oluşturucu tarafından oluşturulan projelere daha sonra başka bir çözümün içinde başvurulmaları gerekiyorsa, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizin içinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6045-241">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c6045-242">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c6045-242">Next steps</span></span>

<span data-ttu-id="c6045-243">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="c6045-243">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c6045-244">ASP.NET Core Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6045-244">Create an ASP.NET Core Razor Pages application</span></span>
> * <span data-ttu-id="c6045-245">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="c6045-245">Prepare and understand the data</span></span>
> * <span data-ttu-id="c6045-246">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="c6045-246">Choose a scenario</span></span>
> * <span data-ttu-id="c6045-247">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="c6045-247">Load the data</span></span>
> * <span data-ttu-id="c6045-248">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c6045-248">Train the model</span></span>
> * <span data-ttu-id="c6045-249">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c6045-249">Evaluate the model</span></span>
> * <span data-ttu-id="c6045-250">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="c6045-250">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c6045-251">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c6045-251">Additional Resources</span></span>

<span data-ttu-id="c6045-252">Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:</span><span class="sxs-lookup"><span data-stu-id="c6045-252">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="c6045-253">Model Oluşturucu senaryoları</span><span class="sxs-lookup"><span data-stu-id="c6045-253">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="c6045-254">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="c6045-254">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="c6045-255">İkili sınıflandırma modeli ölçümleri</span><span class="sxs-lookup"><span data-stu-id="c6045-255">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)