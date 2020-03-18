---
title: ASP.NET Core Web API'sinde bir model dağıtma
description: ASP.NET Core Web API kullanarak internet üzerinden ML.NET duygu analizi makine öğrenme modeli hizmet
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398932"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="0fb43-103">ASP.NET Core Web API'sinde bir model dağıtma</span><span class="sxs-lookup"><span data-stu-id="0fb43-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="0fb43-104">ASP.NET Core Web API kullanarak web üzerinde önceden eğitilmiş ML.NET makine öğrenimi modelinin nasıl hizmet verilebildiğini öğrenin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="0fb43-105">Bir web API üzerinden bir model hizmet standart HTTP yöntemleri ile tahminler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fb43-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0fb43-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0fb43-106">Prerequisites</span></span>

- <span data-ttu-id="0fb43-107">[Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="0fb43-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="0fb43-108">Powershell.</span><span class="sxs-lookup"><span data-stu-id="0fb43-108">Powershell.</span></span>
- <span data-ttu-id="0fb43-109">Önceden eğitilmiş bir model.</span><span class="sxs-lookup"><span data-stu-id="0fb43-109">Pre-trained model.</span></span> <span data-ttu-id="0fb43-110">Kendi modelinizi oluşturmak veya bu [önceden eğitilmiş duygu analizi makine öğrenme modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirmek için ML.NET Sentiment Analysis [öğreticisini](../tutorials/sentiment-analysis.md) kullanın</span><span class="sxs-lookup"><span data-stu-id="0fb43-110">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="0fb43-111">Çekirdek Web API ASP.NET oluşturma</span><span class="sxs-lookup"><span data-stu-id="0fb43-111">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="0fb43-112">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="0fb43-112">Open Visual Studio 2017.</span></span> <span data-ttu-id="0fb43-113">Menü çubuğundan **Dosya > Yeni > Projesi'ni** seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-113">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="0fb43-114">Yeni Proje iletişim kutusunda, **Web** düğümü tarafından izlenen **Visual C#** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-114">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="0fb43-115">Ardından **ASP.NET Çekirdek Web Uygulaması** proje şablonuna gidin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-115">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="0fb43-116">**Ad** metin kutusunda "SentimentAnalysisWebAPI" yazın ve ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-116">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="0fb43-117">Farklı ASP.NET Çekirdek Projeleri türlerini görüntüleyen **pencerede, API'yi** ve **Tamam** düğmesini seçin' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-117">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="0fb43-118">Önceden oluşturulmuş makine öğrenme modeli dosyalarınızı kaydetmek için projenizde *MLModels* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0fb43-118">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="0fb43-119">Çözüm Gezgini'nde projenize sağ tıklayın ve Yeni Klasör > Ekle'yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-119">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="0fb43-120">"MLModels" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0fb43-120">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="0fb43-121">Microsoft.ML **NuGet Paketini**Yükleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-121">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="0fb43-122">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-122">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0fb43-123">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML**arayın, listedeki paketi seçin ve Yükle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-123">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="0fb43-124">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-124">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="0fb43-125">Microsoft.Extensions.ML **Nuget Paketini**Yükleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-125">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="0fb43-126">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-126">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0fb43-127">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.Extensions.ML**arayın, listedeki paketi seçin ve Yükle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-127">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="0fb43-128">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-128">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="0fb43-129">Core Web API projesine model ekleme ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0fb43-129">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="0fb43-130">Önceden oluşturulmuş modelinizi *MLModels* dizinine kopyalayın</span><span class="sxs-lookup"><span data-stu-id="0fb43-130">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="0fb43-131">Çözüm Gezgini'nde, model zip dosyasına sağ tıklayın ve Özellikler'i seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-131">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="0fb43-132">Gelişmiş altında, daha yeniyse, Kopya'nın değerini Çıktı Dizini'ne kopyaolarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-132">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="0fb43-133">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0fb43-133">Create data models</span></span>

<span data-ttu-id="0fb43-134">Giriş verileriniz ve öngörüleriniz için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fb43-134">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="0fb43-135">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-135">Add a new class to your project:</span></span>

1. <span data-ttu-id="0fb43-136">Veri modellerinizi kaydetmek için projenizde *Veri Modelleri* adında bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0fb43-136">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="0fb43-137">Çözüm Gezgini'nde projenize sağ tıklayın ve Yeni Klasör > Ekle'yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-137">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="0fb43-138">"DataModels" yazın ve **Enter**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0fb43-138">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="0fb43-139">Çözüm Gezgini'nde, *DataModels* dizinini sağ tıklatın ve ardından Yeni Öğe > ekle'yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-139">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="0fb43-140">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-140">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="0fb43-141">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-141">Then, select the **Add** button.</span></span> <span data-ttu-id="0fb43-142">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-142">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="0fb43-143">*SentimentData.cs*üst kısmında aşağıdaki ifadesini kullanarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-143">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="0fb43-144">Varolan sınıf tanımını kaldırın ve **SentimentData.cs** dosyasına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-144">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

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

4. <span data-ttu-id="0fb43-145">Çözüm Gezgini'nde, *DataModels* dizinini sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-145">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="0fb43-146">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="0fb43-147">Ardından Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-147">Then, select the Add button.</span></span> <span data-ttu-id="0fb43-148">kod düzenleyicisinde *SentimentPrediction.cs* dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-148">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="0fb43-149">*SentimentPrediction.cs*üstüne aşağıdaki ifadesini kullanarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-149">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="0fb43-150">Varolan sınıf tanımını kaldırın ve *SentimentPrediction.cs* dosyasına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-150">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="0fb43-151">`SentimentPrediction`'den `SentimentData`devralır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-151">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="0fb43-152">Bu, model tarafından oluşturulan çıktıyla `SentimentText` birlikte özellikteki özgün verileri görmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-152">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span>

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="0fb43-153">Register PredictionEnginePool uygulamada kullanılmak üzere</span><span class="sxs-lookup"><span data-stu-id="0fb43-153">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="0fb43-154">Tek bir tahmin yapmak için, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)bir .</span><span class="sxs-lookup"><span data-stu-id="0fb43-154">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="0fb43-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="0fb43-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="0fb43-156">Ayrıca, uygulamanız içinde gerekli olan her yerde bunun bir örneğini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fb43-156">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="0fb43-157">Uygulamanız büyüdükçe, bu işlem yönetilemez hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="0fb43-157">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="0fb43-158">Daha iyi performans ve iş parçacığı güvenliği için, `PredictionEnginePool` uygulamanız boyunca [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) kullanılmak [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) üzere bir nesne oluşturan bağımlılık enjeksiyonu ve hizmetin bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0fb43-158">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="0fb43-159">Eğer [ASP.NET Core bağımlılık enjeksiyon](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1)hakkında daha fazla bilgi edinmek istiyorsanız aşağıdaki bağlantı daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fb43-159">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="0fb43-160">*Startup.cs* sınıfını açın ve dosyanın üst bölümüne aşağıdaki ifadesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-160">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="0fb43-161">*ConfigureServices* yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-161">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

<span data-ttu-id="0fb43-162">Yüksek düzeyde, bu kod, uygulama tarafından el ile yapmak zorunda kalmak yerine daha sonra kullanılmak üzere nesneleri ve hizmetleri otomatik olarak başlatir.</span><span class="sxs-lookup"><span data-stu-id="0fb43-162">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="0fb43-163">Makine öğrenimi modelleri statik değildir.</span><span class="sxs-lookup"><span data-stu-id="0fb43-163">Machine learning models are not static.</span></span> <span data-ttu-id="0fb43-164">Yeni eğitim verileri kullanılabilir hale geldikçe, model yeniden eğitilir ve yeniden dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-164">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="0fb43-165">Uygulamanıza modelin en son sürümünü almanın bir yolu, tüm uygulamayı yeniden dağıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-165">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="0fb43-166">Ancak, bu uygulama kapalı kalma süresi tanır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-166">However, this introduces application downtime.</span></span> <span data-ttu-id="0fb43-167">Hizmet, `PredictionEnginePool` uygulamanızı kaldırmadan güncelleştirilmiş bir modeli yeniden yüklemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fb43-167">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="0fb43-168">Parametreyi `watchForChanges` `true`ve dosya `PredictionEnginePool` sistemi [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) değişiklik bildirimlerini dinleyen ve dosyada bir değişiklik olduğunda olayları yükselten bir başlat' olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0fb43-168">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="0fb43-169">Bu, modeli `PredictionEnginePool` otomatik olarak yeniden yüklemesini ister.</span><span class="sxs-lookup"><span data-stu-id="0fb43-169">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="0fb43-170">`modelName` Model, uygulama başına birden fazla modelin değişiklik üzerine yeniden yüklenebilmeleri için parametre ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-170">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="0fb43-171">Alternatif olarak, uzaktan `FromUri` depolanan modeller ile çalışırken yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fb43-171">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="0fb43-172">Dosya değiştirilen olayları izlemek `FromUri` yerine, değişiklikler için uzak konumu yoklar.</span><span class="sxs-lookup"><span data-stu-id="0fb43-172">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="0fb43-173">Yoklama aralığı varsayılan olarak 5 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-173">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="0fb43-174">Uygulamanızın gereksinimlerine bağlı olarak yoklama aralığını artırabilir veya azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fb43-174">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="0fb43-175">Aşağıdaki kod örneğinde, `PredictionEnginePool` model her dakika belirtilen URI'de depolanır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-175">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="0fb43-176">Predict denetleyicisi oluştur</span><span class="sxs-lookup"><span data-stu-id="0fb43-176">Create Predict controller</span></span>

<span data-ttu-id="0fb43-177">Gelen HTTP isteklerinizi işlemek için bir denetleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0fb43-177">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="0fb43-178">Çözüm Gezgini'nde, *Denetleyiciler* dizinine sağ tıklayın ve ardından **> Denetleyicisi Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-178">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="0fb43-179">Yeni **Öğe Ekle** iletişim kutusunda **API Denetleyicisi Boş'u** seçin ve **Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-179">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="0fb43-180">Komut istemiyle **Denetleyici Adı** alanını *PredictController.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-180">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="0fb43-181">Ardından Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-181">Then, select the Add button.</span></span> <span data-ttu-id="0fb43-182">kod düzenleyicisinde *PredictController.cs* dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="0fb43-182">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="0fb43-183">*PredictController.cs*üst kısmında aşağıdaki ifadesini kullanarak deyimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-183">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="0fb43-184">Varolan sınıf tanımını kaldırın ve *PredictController.cs* dosyasına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0fb43-184">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

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

<span data-ttu-id="0fb43-185">Bu kod, `PredictionEnginePool` bağımlılık enjeksiyonu yoluyla aldığınız denetleyicinin oluşturucuya geçirerek atar.</span><span class="sxs-lookup"><span data-stu-id="0fb43-185">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="0fb43-186">Daha sonra, `Predict` denetleyicinin `Post` yöntemi `PredictionEnginePool` `SentimentAnalysisModel` `Startup` sınıfta kayıtlı kullanarak öngörüler yapmak için kullanır ve başarılı olursa sonuçları kullanıcıya geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0fb43-186">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="0fb43-187">Web API'yi yerel olarak test edin</span><span class="sxs-lookup"><span data-stu-id="0fb43-187">Test web API locally</span></span>

<span data-ttu-id="0fb43-188">Her şey ayarlandıktan sonra, uygulamayı test etme zamanı.</span><span class="sxs-lookup"><span data-stu-id="0fb43-188">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="0fb43-189">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0fb43-189">Run the application.</span></span>
1. <span data-ttu-id="0fb43-190">Powershell'i açın ve uygulamanızın dinlediği bağlantı noktası PORT'un bulunduğu aşağıdaki kodu girin.</span><span class="sxs-lookup"><span data-stu-id="0fb43-190">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="0fb43-191">Başarılı olursa, çıktı aşağıdaki metne benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="0fb43-191">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="0fb43-192">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="0fb43-192">Congratulations!</span></span> <span data-ttu-id="0fb43-193">ASP.NET Core Web API kullanarak internet üzerinden öngörülerde bulunmak için modelinizi başarıyla hizmet ettiniz.</span><span class="sxs-lookup"><span data-stu-id="0fb43-193">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0fb43-194">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="0fb43-194">Next Steps</span></span>

- [<span data-ttu-id="0fb43-195">Azure'a Dağıt</span><span class="sxs-lookup"><span data-stu-id="0fb43-195">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
