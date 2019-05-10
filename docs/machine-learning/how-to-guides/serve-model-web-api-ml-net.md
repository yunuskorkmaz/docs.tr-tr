---
title: Bir ASP.NET Core Web API'si, model dağıtma
description: ML.NET yaklaşım analizi, makine öğrenme modelinin ASP.NET Core Web API'si kullanarak internet üzerinden hizmet
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c78e58dbec6b2ba3065fc46c4d4fd65abdcd37cd
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063477"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="ed1aa-103">Bir ASP.NET Core Web API'si, model dağıtma</span><span class="sxs-lookup"><span data-stu-id="ed1aa-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="ed1aa-104">Bir ASP.NET Core Web API'si kullanarak web üzerinde önceden eğitilen ML.NET makine öğrenme modeli hizmet öğrenin.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="ed1aa-105">Bir modeli bir web API'si sunan standart HTTP yöntemleri aracılığıyla Öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="ed1aa-106">`PredictionEnginePool` Hizmet uzantısı, şu anda Önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ed1aa-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ed1aa-107">Prerequisites</span></span>

- <span data-ttu-id="ed1aa-108">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="ed1aa-109">PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-109">Powershell.</span></span>
- <span data-ttu-id="ed1aa-110">Önceden eğitilmiş model.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-110">Pre-trained model.</span></span> <span data-ttu-id="ed1aa-111">Kullanım [ML.NET yaklaşım analizi Öğreticisi](../tutorials/sentiment-analysis.md) kendi modelinizi oluşturun veya bunu indirmek üzere [önceden eğitilmiş yaklaşım analizi, machine learning modeli](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="ed1aa-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="ed1aa-112">ASP.NET Core Web API projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed1aa-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="ed1aa-113">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="ed1aa-114">Seçin **Dosya > Yeni > Proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="ed1aa-115">Yeni Proje iletişim kutusunda, seçmek **Visual C#**  düğümünü ve ardından **Web** düğümü.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="ed1aa-116">Ardından **ASP.NET Core Web uygulaması** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="ed1aa-117">İçinde **adı** metin kutusuna "SentimentAnalysisWebAPI" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="ed1aa-118">ASP.NET Core projeleri farklı türde görüntüler penceresinde seçin **API** ve select **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="ed1aa-119">Adlı bir dizin oluşturmak *MLModels* projenizde, önceden oluşturulmuş makine öğrenimi modeli dosyaları kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="ed1aa-120">Çözüm Gezgini'nde projenize sağ tıklayın ve Ekle > Yeni bir klasör.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="ed1aa-121">"MLModels" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="ed1aa-122">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="ed1aa-123">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ed1aa-124">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, listesinde o paketi seçin ve Yükle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="ed1aa-125">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** için lisans şartlarını kabul ediyorsanız lisans kabulü iletişim kutusunda düğmesi listelenen paketler.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ed1aa-126">Yükleme **Microsoft.Extensions.ML Nuget paketini**:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="ed1aa-127">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ed1aa-128">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.Extensions.ML**, listesinde o paketi seçin ve Yükle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="ed1aa-129">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** için lisans şartlarını kabul ediyorsanız lisans kabulü iletişim kutusunda düğmesi listelenen paketler.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="ed1aa-130">Model için ASP.NET Core Web API projesi Ekle</span><span class="sxs-lookup"><span data-stu-id="ed1aa-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="ed1aa-131">Önceden oluşturulmuş modelinizi kopyalama *MLModels* dizini</span><span class="sxs-lookup"><span data-stu-id="ed1aa-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="ed1aa-132">Çözüm Gezgini'nde, model zip dosyasını sağ tıklayın ve Özellikler'i seçin.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="ed1aa-133">Gelişmiş altında kopyalama çıkış dizinine kopyalanacak yeniyse değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="ed1aa-134">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed1aa-134">Create data models</span></span>

<span data-ttu-id="ed1aa-135">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="ed1aa-136">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="ed1aa-137">Adlı bir dizin oluşturmak *DataModels* projenizde veri Modellerinizi kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="ed1aa-138">Çözüm Gezgini'nde projenize sağ tıklayın ve Ekle > Yeni bir klasör.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="ed1aa-139">"DataModels" yazın ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="ed1aa-140">Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından Ekle > Yeni öğe.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="ed1aa-141">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="ed1aa-142">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-142">Then, select the **Add** button.</span></span> <span data-ttu-id="ed1aa-143">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ed1aa-144">Aşağıdaki using deyimini üstüne *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="ed1aa-145">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin **SentimentData.cs** dosyası:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
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

4. <span data-ttu-id="ed1aa-146">Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="ed1aa-147">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="ed1aa-148">Ardından Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-148">Then, select the Add button.</span></span> <span data-ttu-id="ed1aa-149">*SentimentPrediction.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="ed1aa-150">Aşağıdaki using deyimini üstüne *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="ed1aa-151">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *SentimentPrediction.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="ed1aa-152">`SentimentPrediction` devralınan `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="ed1aa-153">Bu, özgün veri görmeyi kolaylaştırır `SentimentText` modeli tarafından oluşturulan çıktı birlikte özelliği.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="ed1aa-154">Uygulama kullanım PredictionEnginePool kaydolun</span><span class="sxs-lookup"><span data-stu-id="ed1aa-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="ed1aa-155">Tek bir tahminde bulunmak için kullanmak [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="ed1aa-155">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="ed1aa-156">Kullanmak için [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) gerektiğinde uygulamanızı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-156">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="ed1aa-157">Bu durumda, dikkate alınması gereken bir en iyi bağımlılık ekleme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-157">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="ed1aa-158">Hakkında bilgi edinmek istiyorsanız aşağıdaki bağlantıda daha fazla bilgi sağlar. [ASP.NET Core bağımlılık ekleme](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="ed1aa-158">The following link provides more information if you want to learn about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="ed1aa-159">Açık *Startup.cs* sınıfı ve aşağıdaki using deyimini dosyanın en üstüne:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-159">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="ed1aa-160">Aşağıdaki kodu ekleyin *Createservicereplicalisteners()* yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-160">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

<span data-ttu-id="ed1aa-161">Yüksek düzeyde, bu kod nesneleri ve otomatik yerine el ile yapmanıza gerek kalmadan uygulama tarafından istendiğinde hizmetlerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-161">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="ed1aa-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="ed1aa-163">Performansı artırmak ve iş parçacığı güvenliği için kullanmak `PredictionEnginePool` oluşturan hizmeti bir [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) , `PredictionEngine` nesneleri uygulama kullanımı.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-163">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="ed1aa-164">Hakkında daha fazla bilgi edinmek için şu blog gönderisini okuyun [oluşturma ve kullanma `PredictionEngine` nesne ASP.NET Core havuzlarında](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="ed1aa-164">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>  

## <a name="create-predict-controller"></a><span data-ttu-id="ed1aa-165">Predıct denetleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed1aa-165">Create Predict controller</span></span>

<span data-ttu-id="ed1aa-166">Gelen HTTP isteklerini işlemek için bir denetleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-166">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="ed1aa-167">Çözüm Gezgini'nde sağ *denetleyicileri* dizin ve ardından **Ekle > denetleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-167">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="ed1aa-168">İçinde **Yeni Öğe Ekle** iletişim kutusunda **boş API denetleyicisi** seçip **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-168">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="ed1aa-169">Komut istemi değişim **Denetleyici adı** alanı *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-169">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="ed1aa-170">Ardından Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-170">Then, select the Add button.</span></span> <span data-ttu-id="ed1aa-171">*PredictController.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-171">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="ed1aa-172">Aşağıdaki using deyimini üstüne *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-172">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="ed1aa-173">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *PredictController.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-173">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
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

<span data-ttu-id="ed1aa-174">Bu kod atar `PredictionEnginePool` bağımlılık ekleme erişmenizi denetleyicinin oluşturucusuna geçirerek.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-174">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="ed1aa-175">Ardından, `Predict` denetleyicinin `Post` yöntemi kullanan `PredictionEnginePool` tahminlerde bulunabilir ve başarılı olursa sonuçları kullanıcıya geri döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-175">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="ed1aa-176">Yerel olarak test web API'si</span><span class="sxs-lookup"><span data-stu-id="ed1aa-176">Test web API locally</span></span>

<span data-ttu-id="ed1aa-177">Her şeyi ayarlandıktan sonra uygulama test etme vakti.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-177">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="ed1aa-178">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-178">Run the application.</span></span>
1. <span data-ttu-id="ed1aa-179">PowerShell'i açın ve bağlantı noktası, bağlantı noktası olduğu aşağıdaki kodu girin. uygulamanızı dinlediği.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-179">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="ed1aa-180">Başarılı olursa çıktı aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ed1aa-180">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="ed1aa-181">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="ed1aa-181">Congratulations!</span></span> <span data-ttu-id="ed1aa-182">Ayrıca, bir ASP.NET Core Web API'si kullanarak internet üzerinden tahminlerde bulunmak üzere modelinizi başarıyla hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="ed1aa-182">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ed1aa-183">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="ed1aa-183">Next Steps</span></span>

- [<span data-ttu-id="ed1aa-184">Azure’a dağıtma</span><span class="sxs-lookup"><span data-stu-id="ed1aa-184">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)