---
title: ASP.NET Core Web API 'sinde model dağıtma
description: ASP.NET Core Web API 'sini kullanarak Internet üzerinden ML.NET yaklaşım analizi makine öğrenimi modelini sunar
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 42f8d51f2547cd6f3240a05420b2da10b7cf52e3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179389"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="656c3-103">ASP.NET Core Web API 'sinde model dağıtma</span><span class="sxs-lookup"><span data-stu-id="656c3-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="656c3-104">Bir ASP.NET Core Web API 'SI kullanarak Web 'de önceden eğitilen ML.NET makine öğrenimi modelini nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="656c3-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="656c3-105">Bir Web API 'SI üzerinde bir modele hizmet sunmak, standart HTTP yöntemleri aracılığıyla tahmine dayalı hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="656c3-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="656c3-106">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="656c3-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="656c3-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="656c3-107">Prerequisites</span></span>

- <span data-ttu-id="656c3-108">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="656c3-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="656c3-109">PowerShell.</span><span class="sxs-lookup"><span data-stu-id="656c3-109">Powershell.</span></span>
- <span data-ttu-id="656c3-110">Önceden eğitilen model.</span><span class="sxs-lookup"><span data-stu-id="656c3-110">Pre-trained model.</span></span> <span data-ttu-id="656c3-111">Kendi modelinizi derlemek için [ML.NET yaklaşım Analizi öğreticisini](../tutorials/sentiment-analysis.md) kullanın veya bu [önceden eğitilen yaklaşım Analizi Machine Learning modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirin</span><span class="sxs-lookup"><span data-stu-id="656c3-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="656c3-112">ASP.NET Core Web API projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="656c3-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="656c3-113">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="656c3-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="656c3-114">Menü çubuğundan **dosya > yeni > projesi** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="656c3-115">Yeni proje iletişim kutusunda, **Visual C#**  düğümünü ve ardından **Web** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="656c3-116">**ASP.NET Core Web uygulaması** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="656c3-117">**Ad** metin kutusuna "SentimentAnalysisWebAPI" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="656c3-118">Farklı türlerde ASP.NET Core projeler görüntüleyen pencerede, **API** ' yi seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="656c3-119">Önceden oluşturulmuş makine öğrenimi modeli dosyalarınızı kaydetmek için projenizde *Mlmodeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="656c3-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="656c3-120">Çözüm Gezgini, projenize sağ tıklayın ve > Yeni klasör Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="656c3-121">"Mlmodeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="656c3-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="656c3-122">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="656c3-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="656c3-123">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="656c3-124">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden bu paketi seçin ve sonra da Install düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="656c3-125">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız Lisans Kabulü iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="656c3-126">**Microsoft.Extensions.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="656c3-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="656c3-127">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="656c3-128">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.Extensions.ml**için arama yapın, listeden bu paketi seçin ve sonra da Install düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="656c3-129">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız Lisans Kabulü iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="656c3-130">Modeli ASP.NET Core Web API projesine ekle</span><span class="sxs-lookup"><span data-stu-id="656c3-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="656c3-131">Önceden oluşturulmuş modelinizi *Mlmodeller* dizinine kopyalayın</span><span class="sxs-lookup"><span data-stu-id="656c3-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="656c3-132">Çözüm Gezgini, model ZIP dosyasına sağ tıklayın ve Özellikler ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="656c3-133">Gelişmiş ' in altında, çıkış dizinine Kopyala değerini daha yeniyse kopyala olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="656c3-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="656c3-134">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="656c3-134">Create data models</span></span>

<span data-ttu-id="656c3-135">Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="656c3-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="656c3-136">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="656c3-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="656c3-137">Veri modellerinizi kaydetmek için projenizde *Datamodeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="656c3-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="656c3-138">Çözüm Gezgini, projenize sağ tıklayın ve > Yeni klasör Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="656c3-139">"Datamodeller" yazın ve **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="656c3-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="656c3-140">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra > yeni öğe Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="656c3-141">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="656c3-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="656c3-142">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-142">Then, select the **Add** button.</span></span> <span data-ttu-id="656c3-143">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="656c3-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="656c3-144">Aşağıdaki using ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="656c3-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="656c3-145">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu **SentimentData.cs** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="656c3-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="656c3-146">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="656c3-147">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="656c3-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="656c3-148">Sonra Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-148">Then, select the Add button.</span></span> <span data-ttu-id="656c3-149">*SentimentPrediction.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="656c3-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="656c3-150">Aşağıdaki using ifadesini *SentimentPrediction.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="656c3-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="656c3-151">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentPrediction.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="656c3-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="656c3-152">`SentimentPrediction` `SentimentData` ' den devralır.</span><span class="sxs-lookup"><span data-stu-id="656c3-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="656c3-153">Bu, `SentimentText` özelliğindeki özgün verileri, model tarafından oluşturulan çıkışın yanında görmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="656c3-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="656c3-154">Uygulamada kullanmak için PredictionEnginePool Kaydet</span><span class="sxs-lookup"><span data-stu-id="656c3-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="656c3-155">Tek bir tahmin yapmak için bir [@no__t](xref:Microsoft.ML.PredictionEngine%602)oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="656c3-155">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="656c3-156">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="656c3-156">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="656c3-157">Ayrıca, uygulamanızın içinde gerek duyduğu her yerde bir örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="656c3-157">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="656c3-158">Uygulamanız büyüdükçe, bu işlem yönetilebilir hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="656c3-158">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="656c3-159">Daha iyi performans ve iş parçacığı güvenliği için, uygulamanız genelinde kullanılmak üzere bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan bağımlılık ekleme ve `PredictionEnginePool` hizmeti birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="656c3-159">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="656c3-160">[ASP.NET Core ' de bağımlılık ekleme](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)hakkında daha fazla bilgi edinmek istiyorsanız aşağıdaki bağlantıda daha fazla bilgi sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="656c3-160">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="656c3-161">*Startup.cs* sınıfını açın ve aşağıdaki using ifadesini dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="656c3-161">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="656c3-162">*ConfigureServices* yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="656c3-162">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    }
    ```

<span data-ttu-id="656c3-163">Yüksek düzeyde, bu kod, uygulama tarafından el ile yapmak yerine, daha sonra kullanmak üzere nesne ve hizmetleri otomatik olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="656c3-163">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span> 

<span data-ttu-id="656c3-164">Makine öğrenimi modelleri statik değildir.</span><span class="sxs-lookup"><span data-stu-id="656c3-164">Machine learning models are not static.</span></span> <span data-ttu-id="656c3-165">Yeni eğitim verileri kullanılabilir hale geldiğinde, model geri çekme ve yeniden dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="656c3-165">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="656c3-166">Bir modelin en son sürümünü uygulamanıza almanın bir yolu, uygulamanın tamamını yeniden dağıtmaktan biridir.</span><span class="sxs-lookup"><span data-stu-id="656c3-166">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="656c3-167">Ancak bu, uygulama kapalı kalma süresini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="656c3-167">However, this introduces application downtime.</span></span> <span data-ttu-id="656c3-168">@No__t-0 hizmeti, uygulamanızı kapatmak zorunda kalmadan güncelleştirilmiş bir modeli yeniden yüklemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="656c3-168">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span> 

<span data-ttu-id="656c3-169">@No__t-0 parametresini `true` olarak ayarlayın ve `PredictionEnginePool`, dosya sistemi değişiklik bildirimlerini dinleyen ve dosyada değişiklik olduğunda olay başlatan bir [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) başlatır.</span><span class="sxs-lookup"><span data-stu-id="656c3-169">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="656c3-170">Bu, modeli otomatik olarak yeniden yüklemek için `PredictionEnginePool` ' a sorar.</span><span class="sxs-lookup"><span data-stu-id="656c3-170">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="656c3-171">Model `modelName` parametresiyle tanımlanır, böylece değişiklik yapıldığında uygulama başına birden fazla model yeniden yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="656c3-171">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span> 

> [!TIP]
> <span data-ttu-id="656c3-172">Alternatif olarak, uzaktan depolanan modellerle çalışırken `FromUri` yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="656c3-172">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="656c3-173">Dosya değiştirilen olayları izlemek yerine `FromUri`, uzak konumu değişiklikler için yoklar.</span><span class="sxs-lookup"><span data-stu-id="656c3-173">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="656c3-174">Yoklama aralığı varsayılan olarak 5 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="656c3-174">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="656c3-175">Uygulama gereksinimlerine bağlı olarak yoklama aralığını artırabilir veya azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="656c3-175">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="656c3-176">Aşağıdaki kod örneğinde, `PredictionEnginePool` her dakikada belirtilen URI 'de depolanan modeli yoklar.</span><span class="sxs-lookup"><span data-stu-id="656c3-176">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>    
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel", 
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip", 
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="656c3-177">Tahmin denetleyicisi oluştur</span><span class="sxs-lookup"><span data-stu-id="656c3-177">Create Predict controller</span></span>

<span data-ttu-id="656c3-178">Gelen HTTP isteklerinizi işlemek için bir denetleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="656c3-178">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="656c3-179">Çözüm Gezgini, *denetleyiciler* dizinine sağ tıklayın ve sonra **> denetleyicisi Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-179">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="656c3-180">**Yeni öğe Ekle** iletişim kutusunda, **API denetleyicisi boş** ' ı seçin ve **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-180">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="656c3-181">İstemde, **Denetleyici adı** alanını *PredictController.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="656c3-181">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="656c3-182">Sonra Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="656c3-182">Then, select the Add button.</span></span> <span data-ttu-id="656c3-183">*PredictController.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="656c3-183">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="656c3-184">Aşağıdaki using ifadesini *PredictController.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="656c3-184">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="656c3-185">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *PredictController.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="656c3-185">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="656c3-186">Bu kod, bağımlılığı ekleme yoluyla aldığınız denetleyicinin oluşturucusuna geçirerek `PredictionEnginePool` ' a atar.</span><span class="sxs-lookup"><span data-stu-id="656c3-186">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="656c3-187">Ardından, `Predict` denetleyicisinin `Post` yöntemi `Startup` sınıfında kayıtlı `SentimentAnalysisModel` ' ü kullanarak tahminleri yapmak için `PredictionEnginePool` kullanır ve başarılı olursa sonuçları kullanıcıya geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="656c3-187">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="656c3-188">Web API 'sini yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="656c3-188">Test web API locally</span></span>

<span data-ttu-id="656c3-189">Her şey ayarlandıktan sonra, uygulamayı test etmek zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="656c3-189">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="656c3-190">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="656c3-190">Run the application.</span></span>
1. <span data-ttu-id="656c3-191">PowerShell 'i açın ve aşağıdaki kodu girerek bağlantı noktasının, uygulamanızın dinlediği bağlantı noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="656c3-191">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="656c3-192">Başarılı olursa, çıkış aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="656c3-192">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="656c3-193">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="656c3-193">Congratulations!</span></span> <span data-ttu-id="656c3-194">ASP.NET Core bir Web API 'SI kullanarak internet üzerinden tahmin etmek için modelinize başarıyla hizmet sundu.</span><span class="sxs-lookup"><span data-stu-id="656c3-194">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="656c3-195">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="656c3-195">Next Steps</span></span>

- [<span data-ttu-id="656c3-196">Azure’a Dağıtma</span><span class="sxs-lookup"><span data-stu-id="656c3-196">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
