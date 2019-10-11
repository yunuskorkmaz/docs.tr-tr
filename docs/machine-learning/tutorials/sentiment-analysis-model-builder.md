---
title: 'Öğretici: yaklaşım-ikili sınıflandırmayı çözümle'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir Razor Pages uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio 'da model Oluşturucu kullanır.
ms.date: 10/08/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4a97fb70caafd7b0003830259ddbb0ec72a2ca8a
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180264"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="0960f-104">Öğretici: ML.NET model Oluşturucu kullanarak Web uygulamasındaki Web sitesindeki açıklamaları çözümleme</span><span class="sxs-lookup"><span data-stu-id="0960f-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="0960f-105">Bir Web uygulamasının içinde gerçek zamanlı açıklamalardan yaklaşımı çözümleme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="0960f-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="0960f-106">Bu öğreticide, Web sitesi açıklamalarından gerçek zamanlı olarak yaklaşım sınıflandıran bir ASP.NET Core Razor Pages uygulamasının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0960f-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="0960f-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="0960f-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="0960f-108">ASP.NET Core Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0960f-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="0960f-109">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="0960f-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="0960f-110">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="0960f-110">Choose a scenario</span></span>
> - <span data-ttu-id="0960f-111">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="0960f-111">Load the data</span></span>
> - <span data-ttu-id="0960f-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="0960f-112">Train the model</span></span>
> - <span data-ttu-id="0960f-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="0960f-113">Evaluate the model</span></span>
> - <span data-ttu-id="0960f-114">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="0960f-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="0960f-115">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="0960f-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="0960f-116">Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0960f-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="0960f-117">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0960f-117">Pre-requisites</span></span>

<span data-ttu-id="0960f-118">Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="0960f-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="0960f-119">Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0960f-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="0960f-120">ASP.NET Core bir **Razor Pages uygulaması**oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0960f-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="0960f-121">Visual Studio 'Yu açın ve menü çubuğundan **dosya > yeni > projesi** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="0960f-122">Yeni proje iletişim kutusunda, **Visual C#**  düğümünü ve ardından **Web** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="0960f-123">**ASP.NET Core Web uygulaması** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="0960f-124">**Ad** metin kutusuna "SentimentRazor" yazın.</span><span class="sxs-lookup"><span data-stu-id="0960f-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="0960f-125">**Çözüm için dizin oluşturma** onay kutusu varsayılan olarak denetlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0960f-125">The **Create a directory for solution** checkbox should be checked by default.</span></span> <span data-ttu-id="0960f-126">Böyle bir durum söz konusu değilse, kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="0960f-126">If that's not the case, check it.</span></span>
    1. <span data-ttu-id="0960f-127">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-127">Select the **OK** button.</span></span>
    1. <span data-ttu-id="0960f-128">Pencerede farklı ASP.NET Core proje türlerini görüntüleyen **Web uygulaması** ' nı seçin ve ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-128">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="0960f-129">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="0960f-129">Prepare and understand the data</span></span>

<span data-ttu-id="0960f-130">[Vikipedi Detox veri kümesini](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)indirin.</span><span class="sxs-lookup"><span data-stu-id="0960f-130">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="0960f-131">Web sayfası açıldığında, sayfaya sağ tıklayın, **farklı kaydet** ' i seçin ve dosyayı bilgisayarınızda herhangi bir yere kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0960f-131">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="0960f-132">*Vivtox-250-Line-Data. tsv* veri kümesindeki her satır, visede bir kullanıcı tarafından bırakılan farklı bir gözden geçirmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0960f-132">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="0960f-133">İlk sütun metnin (0-Toxic, 1 ' in Toxic) yaklaşımını temsil eder ve ikinci sütun Kullanıcı tarafından bırakılan yorumu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0960f-133">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="0960f-134">Sütunlar sekmelerle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="0960f-134">The columns are separated by tabs.</span></span> <span data-ttu-id="0960f-135">Veriler aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="0960f-135">The data looks like the following:</span></span>

| <span data-ttu-id="0960f-136">Duygu</span><span class="sxs-lookup"><span data-stu-id="0960f-136">Sentiment</span></span> | <span data-ttu-id="0960f-137">Sentimentmetni</span><span class="sxs-lookup"><span data-stu-id="0960f-137">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="0960f-138">1</span><span class="sxs-lookup"><span data-stu-id="0960f-138">1</span></span> | <span data-ttu-id="0960f-139">= = İşlenmemiş = = dude, o Carl resmini geri yüklemeniz veya başka bir şey yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-139">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="0960f-140">1</span><span class="sxs-lookup"><span data-stu-id="0960f-140">1</span></span> | <span data-ttu-id="0960f-141">= = TAMAM!</span><span class="sxs-lookup"><span data-stu-id="0960f-141">== OK!</span></span> <span data-ttu-id="0960f-142">= = ıM, DAHA SONRA BIR WIKI 'YI DAHA SONRA!!!</span><span class="sxs-lookup"><span data-stu-id="0960f-142">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="0960f-143">0</span><span class="sxs-lookup"><span data-stu-id="0960f-143">0</span></span> | <span data-ttu-id="0960f-144">Bunu umuyoruz.</span><span class="sxs-lookup"><span data-stu-id="0960f-144">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="0960f-145">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="0960f-145">Choose a scenario</span></span>

![Visual Studio 'da model Oluşturucu Sihirbazı](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="0960f-147">Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-147">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="0960f-148">**Çözüm Gezgini**, *SentimentRazor* projesine sağ tıklayın ve **Ekle** > **Machine Learning**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-148">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="0960f-149">Bu örnek için senaryo, yaklaşım analiziydi.</span><span class="sxs-lookup"><span data-stu-id="0960f-149">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="0960f-150">Model Oluşturucu aracının *senaryo* adımında **yaklaşım Analizi** senaryosunu seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-150">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="0960f-151">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="0960f-151">Load the data</span></span>

<span data-ttu-id="0960f-152">Model Oluşturucu iki kaynaktan verileri, bir SQL Server veritabanını veya `csv` veya `tsv` biçiminde yerel bir dosyayı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0960f-152">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="0960f-153">Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden **Dosya** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-153">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="0960f-154">**Dosya seçin** metin kutusunun yanındaki düğmeyi seçin ve dosya Gezgini 'ni kullanarak, *vibtox-250-Line-Data. tsv* dosyasına gidin ve seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-154">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="0960f-155">**Tahmin edilecek sütun (etiket)** açılan **listesini seçin.**</span><span class="sxs-lookup"><span data-stu-id="0960f-155">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="0960f-156">**Giriş sütunları (Özellikler)** açılır menüsü için varsayılan değerleri bırakın.</span><span class="sxs-lookup"><span data-stu-id="0960f-156">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="0960f-157">Model Oluşturucu aracında bir sonraki adıma geçmek için **eğitme** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-157">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="0960f-158">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="0960f-158">Train the model</span></span>

<span data-ttu-id="0960f-159">Bu öğreticide yaklaşım Analizi modelini eğitmek için kullanılan makine öğrenimi görevi ikili sınıflandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0960f-159">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="0960f-160">Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı ikili sınıflandırma algoritmalarını ve ayarlarını kullanarak modelleri ayrı ayrı işler.</span><span class="sxs-lookup"><span data-stu-id="0960f-160">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="0960f-161">Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı.</span><span class="sxs-lookup"><span data-stu-id="0960f-161">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="0960f-162">Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer.</span><span class="sxs-lookup"><span data-stu-id="0960f-162">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="0960f-163">Model Oluşturucu değeri, " **saniye)** ila 10 saniye arasında bir süre olarak ayarlasa da, 30 saniyeye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="0960f-163">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="0960f-164">Daha uzun bir süre için eğitim, model oluşturucunun en iyi modeli aramada daha fazla sayıda algoritmaların ve parametrelerin birleşimini keşfetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0960f-164">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="0960f-165">**Eğitimi Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-165">Select **Start Training**.</span></span>

    <span data-ttu-id="0960f-166">Eğitim süreci boyunca, ilerleme verileri eğitme adımının `Progress` bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0960f-166">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="0960f-167">Durum, eğitim sürecinin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0960f-167">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="0960f-168">En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0960f-168">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="0960f-169">Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0960f-169">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="0960f-170">En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0960f-170">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="0960f-171">Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0960f-171">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="0960f-172">Eğitim tamamlandıktan sonra bir sonraki adıma geçmek için bağlantıyı **değerlendir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-172">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="0960f-173">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="0960f-173">Evaluate the model</span></span>

<span data-ttu-id="0960f-174">Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0960f-174">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="0960f-175">Model Oluşturucu aracının değerlendir adımında, çıkış **bölümü en iyi model girişinde en** iyi işlem modeli tarafından kullanılan algoritmayı ve **En Iyi model doğruluğunun**ölçümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0960f-175">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="0960f-176">Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu.</span><span class="sxs-lookup"><span data-stu-id="0960f-176">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="0960f-177">Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu denemeye yönelik bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="0960f-177">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="0960f-178">Aksi takdirde, model Oluşturucu aracında son adıma geçmek için **kod** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-178">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="0960f-179">Tahminleri yapmak için kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="0960f-179">Add the code to make predictions</span></span>

<span data-ttu-id="0960f-180">Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="0960f-180">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="0960f-181">Eğitilen modele başvur</span><span class="sxs-lookup"><span data-stu-id="0960f-181">Reference the trained model</span></span>

1. <span data-ttu-id="0960f-182">Model Oluşturucu aracının *kod* adımında, otomatik olarak oluşturulan projeleri çözüme eklemek Için **Proje Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-182">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="0960f-183">Aşağıdaki projeler **Çözüm Gezgini**görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="0960f-183">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="0960f-184">*SentimentRazorML. ConsoleApp*: model eğitimi ve tahmin kodunu içeren bir .NET Core konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="0960f-184">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="0960f-185">*SentimentRazorML. model*: giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini ve eğitim sırasında en iyi uygulanan modelin kaydedilmiş sürümünü içeren .NET Standard bir sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="0960f-185">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="0960f-186">Bu öğretici için, *SentimentRazorML. model* projesi yalnızca, tahmine dayalı olarak konsolu yerine *SentimentRazor* Web uygulamasında yapılabilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0960f-186">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="0960f-187">*SentimentRazorML. ConsoleApp* , Puanlama için kullanılmayacak olsa da, daha sonra yeni verileri kullanarak modeli yeniden eğitebilmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0960f-187">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="0960f-188">Yeniden eğitim, Bu öğreticinin kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="0960f-188">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="0960f-189">PredictionEngine havuzunu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0960f-189">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="0960f-190">Tek bir tahmin yapmak için bir [@no__t](xref:Microsoft.ML.PredictionEngine%602)oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-190">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="0960f-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="0960f-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="0960f-192">Ayrıca, uygulamanızın içinde gerek duyduğu her yerde bir örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-192">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="0960f-193">Uygulamanız büyüdükçe, bu işlem yönetilebilir hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="0960f-193">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="0960f-194">Daha iyi performans ve iş parçacığı güvenliği için, uygulamanız genelinde kullanılmak üzere bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan bağımlılık ekleme ve `PredictionEnginePool` hizmeti birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0960f-194">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="0960f-195">*Microsoft.Extensions.ml* NuGet paketini yükler:</span><span class="sxs-lookup"><span data-stu-id="0960f-195">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="0960f-196">**Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-196">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="0960f-197">Paket kaynağı olarak "nuget.org" öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-197">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="0960f-198">**Araştır** sekmesini seçin ve **Microsoft.Extensions.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="0960f-198">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="0960f-199">Listeden paketi seçin ve ardından **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-199">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="0960f-200">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin</span><span class="sxs-lookup"><span data-stu-id="0960f-200">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="0960f-201">Listelenen paketlerin lisans koşullarını kabul ediyorsanız, **Lisans kabulü** Iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0960f-201">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="0960f-202">*SentimentRazor* projesindeki *Startup.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0960f-202">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="0960f-203">*Microsoft.Extensions.ml* NuGet paketini ve *SentimentRazorML. model* projesine başvurmak için aşağıdaki using deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0960f-203">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="0960f-204">Eğitilen model dosyasının konumunu depolamak için genel bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0960f-204">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="0960f-205">Model dosyası, uygulamanızın derleme dosyalarının yanı sıra derleme dizininde depolanır.</span><span class="sxs-lookup"><span data-stu-id="0960f-205">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="0960f-206">Daha kolay erişim sağlamak için, `Configure` yönteminden sonra `GetAbsolutePath` adlı bir yardımcı yöntem oluşturun</span><span class="sxs-lookup"><span data-stu-id="0960f-206">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }    
    ```

1. <span data-ttu-id="0960f-207">@No__t-2 ' i ayarlamak için `Startup` sınıf oluşturucusunda `GetAbsolutePath` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0960f-207">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="0960f-208">@No__t-1 yönteminde uygulamanız için `PredictionEnginePool` yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="0960f-208">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="0960f-209">Yaklaşım Analizi işleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0960f-209">Create sentiment analysis handler</span></span>

<span data-ttu-id="0960f-210">Tahmine dayalı, uygulamanın ana sayfasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="0960f-210">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="0960f-211">Bu nedenle, Kullanıcı girişi alan ve bir tahmin eklenmesi için `PredictionEnginePool` kullanan bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="0960f-211">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="0960f-212">*Pages* dizininde bulunan *Index.cshtml.cs* dosyasını açın ve aşağıdaki using deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0960f-212">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="0960f-213">@No__t-1 sınıfında yapılandırılmış `PredictionEnginePool` ' ı kullanmak için, onu kullanmak istediğiniz modelin oluşturucusuna yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0960f-213">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="0960f-214">@No__t-1 sınıfının içindeki `PredictionEnginePool` ' a başvuracak bir değişken ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0960f-214">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="0960f-215">@No__t-0 sınıfında bir Oluşturucu oluşturun ve buna `PredictionEnginePool` hizmetini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0960f-215">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }    
    ```

1. <span data-ttu-id="0960f-216">Web sayfasından alınan Kullanıcı girişinden tahminleri yapmak için `PredictionEnginePool` kullanan bir yöntem işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0960f-216">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="0960f-217">@No__t-0 yönteminin altında, `OnGetAnalyzeSentiment` adlı yeni bir yöntem oluşturun</span><span class="sxs-lookup"><span data-stu-id="0960f-217">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="0960f-218">@No__t-0 yönteminin içinde, kullanıcının girişi boş veya null olduğunda *nötr* yaklaşım döndürün.</span><span class="sxs-lookup"><span data-stu-id="0960f-218">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="0960f-219">Geçerli bir giriş verildiğinde @no__t yeni bir örneğini oluşturun-0.</span><span class="sxs-lookup"><span data-stu-id="0960f-219">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="0960f-220">Duymayı tahmin etmek için `PredictionEnginePool` kullanın.</span><span class="sxs-lookup"><span data-stu-id="0960f-220">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="0960f-221">Tahmin edilen `bool` değerini aşağıdaki kodla Toxic öğesine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="0960f-221">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="0960f-222">Son olarak, yaklaşımı Web sayfasına geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="0960f-222">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="0960f-223">Web sayfasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0960f-223">Configure the web page</span></span>

<span data-ttu-id="0960f-224">@No__t-0 tarafından döndürülen sonuçlar, `Index` Web sayfasında dinamik olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0960f-224">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="0960f-225">*Pages* dizinindeki *Index. cshtml* dosyasını açın ve içeriğini şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0960f-225">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="0960f-226">Ardından, *wwwroot\css* dizinindeki *site. css* sayfasının sonuna CSS stil oluşturma kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0960f-226">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="0960f-227">Bundan sonra, Web sayfasından `OnGetAnalyzeSentiment` işleyicisine giriş göndermek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0960f-227">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="0960f-228">*Wwwroot\js* dizininde bulunan *site. js* dosyasında, `OnGetAnalyzeSentiment` IŞLEYICISINE Kullanıcı GIRIŞIYLE bir HTTP isteği almak için `getSentiment` adlı bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0960f-228">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="0960f-229">Bunun altında, yaklaşım tahmin edildiğinde Web sayfasındaki işaretin konumunu dinamik olarak güncelleştirmek için `updateMarker` adlı başka bir işlev ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0960f-229">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="0960f-230">Kullanıcıdan girişi almak için `updateSentiment` adlı bir olay işleyici işlevi oluşturun, `getSentiment` işlevini kullanarak `OnGetAnalyzeSentiment` işlevine gönderin ve işaretçiyi `updateMarker` işleviyle güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="0960f-230">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="0960f-231">Son olarak, olay işleyicisini kaydedin ve `id=Message` özniteliğiyle `textarea` öğesine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="0960f-231">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="0960f-232">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0960f-232">Run the application</span></span>

<span data-ttu-id="0960f-233">Uygulamanız ayarlandığına göre, tarayıcınızda başlatması gereken uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0960f-233">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="0960f-234">Uygulama başlatıldığında, *model Oluşturucu* seyrek erişimli yazın!</span><span class="sxs-lookup"><span data-stu-id="0960f-234">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="0960f-235">metin alanına.</span><span class="sxs-lookup"><span data-stu-id="0960f-235">into the text area.</span></span> <span data-ttu-id="0960f-236">Görünen tahmini yaklaşım, *Toxic*olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0960f-236">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Tahmin edilen yaklaşım penceresiyle pencere çalıştırma](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="0960f-238">Model Oluşturucu tarafından oluşturulan projelere daha sonra başka bir çözümün içinde başvurulmaları gerekiyorsa, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizininde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0960f-238">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0960f-239">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0960f-239">Next steps</span></span>

<span data-ttu-id="0960f-240">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="0960f-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0960f-241">ASP.NET Core Razor Pages uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0960f-241">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="0960f-242">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="0960f-242">Prepare and understand the data</span></span>
> - <span data-ttu-id="0960f-243">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="0960f-243">Choose a scenario</span></span>
> - <span data-ttu-id="0960f-244">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="0960f-244">Load the data</span></span>
> - <span data-ttu-id="0960f-245">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="0960f-245">Train the model</span></span>
> - <span data-ttu-id="0960f-246">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="0960f-246">Evaluate the model</span></span>
> - <span data-ttu-id="0960f-247">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="0960f-247">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0960f-248">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0960f-248">Additional Resources</span></span>

<span data-ttu-id="0960f-249">Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:</span><span class="sxs-lookup"><span data-stu-id="0960f-249">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="0960f-250">Model Oluşturucu senaryoları</span><span class="sxs-lookup"><span data-stu-id="0960f-250">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="0960f-251">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="0960f-251">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="0960f-252">İkili sınıflandırma modeli ölçümleri</span><span class="sxs-lookup"><span data-stu-id="0960f-252">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)
