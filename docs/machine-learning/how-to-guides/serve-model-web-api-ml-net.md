---
title: ASP.NET Core Web API 'sinde model dağıtma
description: ASP.NET Core Web API 'sini kullanarak Internet üzerinden ML.NET yaklaşım analizi makine öğrenimi modelini sunar
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 8d21ae5ae3aa4701ddd7d042d5069351c22864bb
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182555"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="43de2-103">ASP.NET Core Web API 'sinde model dağıtma</span><span class="sxs-lookup"><span data-stu-id="43de2-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="43de2-104">Bir ASP.NET Core Web API 'SI kullanarak Web 'de önceden eğitilen ML.NET makine öğrenimi modelini nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="43de2-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="43de2-105">Bir Web API 'SI üzerinde bir modele hizmet sunmak, standart HTTP yöntemleri aracılığıyla tahmine dayalı hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="43de2-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="43de2-106">`PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="43de2-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="43de2-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="43de2-107">Prerequisites</span></span>

- <span data-ttu-id="43de2-108">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="43de2-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="43de2-109">PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43de2-109">Powershell.</span></span>
- <span data-ttu-id="43de2-110">Önceden eğitilen model.</span><span class="sxs-lookup"><span data-stu-id="43de2-110">Pre-trained model.</span></span> <span data-ttu-id="43de2-111">Kendi modelinizi derlemek için [ML.NET yaklaşım Analizi öğreticisini](../tutorials/sentiment-analysis.md) kullanın veya bu [önceden eğitilen yaklaşım Analizi Machine Learning modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirin</span><span class="sxs-lookup"><span data-stu-id="43de2-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="43de2-112">ASP.NET Core Web API projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="43de2-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="43de2-113">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="43de2-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="43de2-114">Menü çubuğundan **dosya > yeni > projesi** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="43de2-115">Yeni proje iletişim kutusunda, **Visual C#**  düğümünü ve ardından **Web** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="43de2-116">**ASP.NET Core Web uygulaması** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="43de2-117">**Ad** metin kutusuna "SentimentAnalysisWebAPI" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="43de2-118">Farklı türlerde ASP.NET Core projeler görüntüleyen pencerede, **API** ' yi seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="43de2-119">Önceden oluşturulmuş makine öğrenimi modeli dosyalarınızı kaydetmek için projenizde *Mlmodeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="43de2-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="43de2-120">Çözüm Gezgini, projenize sağ tıklayın ve > Yeni klasör Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="43de2-121">"Mlmodeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="43de2-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="43de2-122">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="43de2-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="43de2-123">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="43de2-124">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden bu paketi seçin ve sonra da Install düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="43de2-125">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız Lisans Kabulü iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="43de2-126">**Microsoft.Extensions.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="43de2-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="43de2-127">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="43de2-128">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.Extensions.ml**için arama yapın, listeden bu paketi seçin ve sonra da Install düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="43de2-129">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız Lisans Kabulü iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="43de2-130">Modeli ASP.NET Core Web API projesine ekle</span><span class="sxs-lookup"><span data-stu-id="43de2-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="43de2-131">Önceden oluşturulmuş modelinizi *Mlmodeller* dizinine kopyalayın</span><span class="sxs-lookup"><span data-stu-id="43de2-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="43de2-132">Çözüm Gezgini, model ZIP dosyasına sağ tıklayın ve Özellikler ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="43de2-133">Gelişmiş ' in altında, çıkış dizinine Kopyala değerini daha yeniyse kopyala olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43de2-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="43de2-134">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="43de2-134">Create data models</span></span>

<span data-ttu-id="43de2-135">Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="43de2-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="43de2-136">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43de2-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="43de2-137">Veri modellerinizi kaydetmek için projenizde *Datamodeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="43de2-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="43de2-138">Çözüm Gezgini, projenize sağ tıklayın ve > Yeni klasör Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="43de2-139">"Datamodeller" yazın ve **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="43de2-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="43de2-140">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra > yeni öğe Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="43de2-141">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43de2-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="43de2-142">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-142">Then, select the **Add** button.</span></span> <span data-ttu-id="43de2-143">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="43de2-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="43de2-144">Aşağıdaki using ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43de2-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="43de2-145">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu **SentimentData.cs** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43de2-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
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

4. <span data-ttu-id="43de2-146">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="43de2-147">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43de2-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="43de2-148">Sonra Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-148">Then, select the Add button.</span></span> <span data-ttu-id="43de2-149">*SentimentPrediction.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="43de2-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="43de2-150">Aşağıdaki using ifadesini *SentimentPrediction.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43de2-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="43de2-151">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentPrediction.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43de2-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="43de2-152">`SentimentPrediction`öğesinden `SentimentData`devralır.</span><span class="sxs-lookup"><span data-stu-id="43de2-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="43de2-153">Bu, `SentimentText` özellikte orijinal verileri, model tarafından oluşturulan çıktıyı birlikte görmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="43de2-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="43de2-154">Uygulamada kullanmak için PredictionEnginePool Kaydet</span><span class="sxs-lookup"><span data-stu-id="43de2-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="43de2-155">Tek bir tahmin yapmak için kullanın [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="43de2-155">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="43de2-156">Uygulamanızda kullanabilmeniz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, gerektiğinde oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="43de2-156">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="43de2-157">Bu durumda, dikkate alınması gereken en iyi yöntem bağımlılık ekleme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="43de2-157">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="43de2-158">[ASP.NET Core ' de bağımlılık ekleme](/aspnet/core/fundamentals/dependency-injection)hakkında bilgi edinmek istiyorsanız aşağıdaki bağlantıda daha fazla bilgi sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43de2-158">The following link provides more information if you want to learn about [dependency injection in ASP.NET Core](/aspnet/core/fundamentals/dependency-injection).</span></span>

1. <span data-ttu-id="43de2-159">*Startup.cs* sınıfını açın ve aşağıdaki using ifadesini dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43de2-159">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="43de2-160">*ConfigureServices* yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43de2-160">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

<span data-ttu-id="43de2-161">Yüksek düzeyde bu kod, uygulama tarafından el ile yapmak yerine nesneleri ve hizmetleri otomatik olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="43de2-161">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="43de2-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="43de2-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="43de2-163">Gelişmiş performans ve iş parçacığı güvenliği için, uygulama `PredictionEnginePool` kullanımı için `PredictionEngine` bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) nesne oluşturan hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="43de2-163">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="43de2-164">[ASP.NET Core içinde nesne havuzları `PredictionEngine` oluşturma ve kullanma](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)hakkında daha fazla bilgi edinmek için aşağıdaki blog gönderisini okuyun.</span><span class="sxs-lookup"><span data-stu-id="43de2-164">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>  

## <a name="create-predict-controller"></a><span data-ttu-id="43de2-165">Tahmin denetleyicisi oluştur</span><span class="sxs-lookup"><span data-stu-id="43de2-165">Create Predict controller</span></span>

<span data-ttu-id="43de2-166">Gelen HTTP isteklerinizi işlemek için bir denetleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43de2-166">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="43de2-167">Çözüm Gezgini, *denetleyiciler* dizinine sağ tıklayın ve sonra **> denetleyicisi Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-167">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="43de2-168">**Yeni öğe Ekle** iletişim kutusunda, **API denetleyicisi boş** ' ı seçin ve **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-168">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="43de2-169">İstemde, **Denetleyici adı** alanını *PredictController.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43de2-169">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="43de2-170">Sonra Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="43de2-170">Then, select the Add button.</span></span> <span data-ttu-id="43de2-171">*PredictController.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="43de2-171">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="43de2-172">Aşağıdaki using ifadesini *PredictController.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43de2-172">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="43de2-173">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *PredictController.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="43de2-173">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
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

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="43de2-174">Bu kod, `PredictionEnginePool` bağımlılığı ekleme yoluyla aldığınız denetleyicinin oluşturucusuna geçirerek öğesine atar.</span><span class="sxs-lookup"><span data-stu-id="43de2-174">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="43de2-175">Ardından, `Predict` `Post` denetleyicinin yöntemi tahmin yapmak `PredictionEnginePool` için öğesini kullanır ve başarılı olursa sonuçları kullanıcıya geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="43de2-175">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="43de2-176">Web API 'sini yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="43de2-176">Test web API locally</span></span>

<span data-ttu-id="43de2-177">Her şey ayarlandıktan sonra, uygulamayı test etmek zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="43de2-177">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="43de2-178">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="43de2-178">Run the application.</span></span>
1. <span data-ttu-id="43de2-179">PowerShell 'i açın ve aşağıdaki kodu girerek bağlantı noktasının, uygulamanızın dinlediği bağlantı noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="43de2-179">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="43de2-180">Başarılı olursa, çıkış aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="43de2-180">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="43de2-181">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="43de2-181">Congratulations!</span></span> <span data-ttu-id="43de2-182">ASP.NET Core bir Web API 'SI kullanarak internet üzerinden tahmin etmek için modelinize başarıyla hizmet sundu.</span><span class="sxs-lookup"><span data-stu-id="43de2-182">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="43de2-183">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="43de2-183">Next Steps</span></span>

- [<span data-ttu-id="43de2-184">Azure’a dağıtma</span><span class="sxs-lookup"><span data-stu-id="43de2-184">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
