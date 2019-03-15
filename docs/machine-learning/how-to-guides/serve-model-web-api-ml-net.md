---
title: Machine Learning modeli ASP.NET Core Web API hizmet
description: ML.NET yaklaşım analizi, makine öğrenme modelinin ASP.NET Core Web API'si kullanarak internet üzerinden hizmet
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 07b751caff8ef0ca9a23bed68ddf88feb7b5ae4f
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57849064"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a><span data-ttu-id="a57ba-103">Nasıl yapılır: Machine Learning modeli ASP.NET Core Web API'si aracılığıyla hizmet</span><span class="sxs-lookup"><span data-stu-id="a57ba-103">How-To: Serve Machine Learning Model Through ASP.NET Core Web API</span></span>

<span data-ttu-id="a57ba-104">Bu nasıl yapılır, önceden oluşturulmuş ML.NET makine öğrenme modeli kullanarak bir ASP.NET Core Web API'si Web hizmet işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a57ba-104">This how-to shows how to serve a pre-built ML.NET machine learning model to the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="a57ba-105">Bunun yapılması kullanıcıların tahmin amacıyla standart HTTP yöntemleri aracılığıyla API'sine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a57ba-105">By doing so it allows for users to access the API for prediction purposes via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="a57ba-106">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="a57ba-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="a57ba-107">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a57ba-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="a57ba-108">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="a57ba-108">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="a57ba-109">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="a57ba-109">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a57ba-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a57ba-110">Prerequisites</span></span>

- <span data-ttu-id="a57ba-111">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a57ba-111">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="a57ba-112">PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a57ba-112">Powershell.</span></span>
- <span data-ttu-id="a57ba-113">Önceden eğitilmiş model.</span><span class="sxs-lookup"><span data-stu-id="a57ba-113">Pre-trained model.</span></span>
    - <span data-ttu-id="a57ba-114">Kullanım [ML.NET yaklaşım analizi Öğreticisi](../tutorials/sentiment-analysis.md) kendi modeli derler.</span><span class="sxs-lookup"><span data-stu-id="a57ba-114">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model.</span></span>
    - <span data-ttu-id="a57ba-115">Bu indirme [önceden eğitilmiş yaklaşım analizi, machine learning modeli](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="a57ba-115">Download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="a57ba-116">ASP.NET Core Web API projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a57ba-116">Create ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="a57ba-117">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="a57ba-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="a57ba-118">Seçin **Dosya > Yeni > Proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="a57ba-118">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="a57ba-119">Yeni Proje iletişim kutusunda, seçmek **Visual C#**  düğümünü ve ardından **Web** düğümü.</span><span class="sxs-lookup"><span data-stu-id="a57ba-119">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="a57ba-120">Ardından **ASP.NET Core Web uygulaması** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="a57ba-120">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="a57ba-121">İçinde **adı** metin kutusuna "SentimentAnalysisWebAPI" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a57ba-121">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>
1. <span data-ttu-id="a57ba-122">ASP.NET Core projeleri farklı türde görüntüler penceresinde seçin **API** ve select **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a57ba-122">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>
1. <span data-ttu-id="a57ba-123">Adlı bir dizin oluşturmak *MLModels* projenizde, önceden oluşturulmuş makine öğrenimi modeli dosyaları kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="a57ba-123">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="a57ba-124">Çözüm Gezgini'nde projenize sağ tıklayın ve Ekle > Yeni bir klasör.</span><span class="sxs-lookup"><span data-stu-id="a57ba-124">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="a57ba-125">"MLModels" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a57ba-125">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="a57ba-126">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="a57ba-126">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="a57ba-127">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="a57ba-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="a57ba-128">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, listesinde o paketi seçin ve Yükle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a57ba-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="a57ba-129">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** için lisans şartlarını kabul ediyorsanız lisans kabulü iletişim kutusunda düğmesi listelenen paketler.</span><span class="sxs-lookup"><span data-stu-id="a57ba-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="a57ba-130">Model için ASP.NET Core Web API projesi Ekle</span><span class="sxs-lookup"><span data-stu-id="a57ba-130">Add Model to ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="a57ba-131">Önceden oluşturulmuş modelinizi kopyalama *MLModels* dizini</span><span class="sxs-lookup"><span data-stu-id="a57ba-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="a57ba-132">Çözüm Gezgini'nde, model zip dosyasını sağ tıklayın ve Özellikler'i seçin.</span><span class="sxs-lookup"><span data-stu-id="a57ba-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="a57ba-133">Gelişmiş altında kopyalama çıkış dizinine kopyalanacak yeniyse değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a57ba-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="build-data-models"></a><span data-ttu-id="a57ba-134">Veri modelleri oluşturabilir</span><span class="sxs-lookup"><span data-stu-id="a57ba-134">Build Data Models</span></span>

<span data-ttu-id="a57ba-135">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a57ba-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="a57ba-136">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a57ba-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="a57ba-137">Adlı bir dizin oluşturmak *DataModels* projenizde veri Modellerinizi kaydetmek için:</span><span class="sxs-lookup"><span data-stu-id="a57ba-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="a57ba-138">Çözüm Gezgini'nde projenize sağ tıklayın ve Ekle > Yeni bir klasör.</span><span class="sxs-lookup"><span data-stu-id="a57ba-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="a57ba-139">"DataModels" yazın ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="a57ba-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="a57ba-140">Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından Ekle > Yeni öğe.</span><span class="sxs-lookup"><span data-stu-id="a57ba-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="a57ba-141">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="a57ba-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="a57ba-142">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a57ba-142">Then, select the **Add** button.</span></span> <span data-ttu-id="a57ba-143">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="a57ba-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="a57ba-144">Aşağıdaki using deyimini üstüne *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="a57ba-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="a57ba-145">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin **SentimentData.cs** dosyası:</span><span class="sxs-lookup"><span data-stu-id="a57ba-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }   
}
```

4. <span data-ttu-id="a57ba-146">Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="a57ba-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="a57ba-147">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="a57ba-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="a57ba-148">Ardından Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a57ba-148">Then, select the Add button.</span></span> <span data-ttu-id="a57ba-149">*SentimentPrediction.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="a57ba-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="a57ba-150">Aşağıdaki using deyimini üstüne *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="a57ba-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="a57ba-151">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *SentimentPrediction.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="a57ba-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

## <a name="create-prediction-service"></a><span data-ttu-id="a57ba-152">Öngörü hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="a57ba-152">Create Prediction Service</span></span>

<span data-ttu-id="a57ba-153">Düzenleme ve tahmin mantıksal uygulamanın tamamı boyunca yeniden kullanmak için bir öngörü hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a57ba-153">To organize and re-use the prediction logic throughout the entire application, create a prediction service.</span></span>

1. <span data-ttu-id="a57ba-154">Adlı bir dizin oluşturmak *Hizmetleri* uygulama tarafından kullanılan hizmetler tutmak için projenizdeki:</span><span class="sxs-lookup"><span data-stu-id="a57ba-154">Create a directory named *Services* in your project to hold services to be used by the application:</span></span>

    <span data-ttu-id="a57ba-155">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **Ekle > Yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="a57ba-155">In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="a57ba-156">"Hizmetler" yazın ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="a57ba-156">Type "Services" and hit **Enter**.</span></span>

1. <span data-ttu-id="a57ba-157">Çözüm Gezgini'nde sağ *Hizmetleri* dizin ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="a57ba-157">In Solution Explorer, right-click the *Services* directory, and then select **Add > New Item**.</span></span>
1. <span data-ttu-id="a57ba-158">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *PredictionService.cs*.</span><span class="sxs-lookup"><span data-stu-id="a57ba-158">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *PredictionService.cs*.</span></span> <span data-ttu-id="a57ba-159">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a57ba-159">Then, select the **Add** button.</span></span> <span data-ttu-id="a57ba-160">*PredictionService.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="a57ba-160">The *PredictionService.cs* file opens in the code editor.</span></span> <span data-ttu-id="a57ba-161">Aşağıdaki using deyimini üstüne *PredictionService.cs*:</span><span class="sxs-lookup"><span data-stu-id="a57ba-161">Add the following using statement to the top of *PredictionService.cs*:</span></span>

```csharp
using System;
using System.IO;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
```

<span data-ttu-id="a57ba-162">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *PredictionService.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="a57ba-162">Remove the existing class definition and add the following code to the *PredictionService.cs* file:</span></span>

```csharp
public class PredictionService
{
    private readonly PredictionEngine<SentimentData, SentimentPrediction> _predictionEngine;
    public PredictionService(PredictionEngine<SentimentData,SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine;
    }

    public string Predict(SentimentData input)
    {
        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return isToxic;

    }
}
```

## <a name="register-predictions-service-for-use-in-application"></a><span data-ttu-id="a57ba-163">Uygulamada Öngörüler hizmeti kullanmak için kaydetme</span><span class="sxs-lookup"><span data-stu-id="a57ba-163">Register Predictions Service for Use in Application</span></span>

<span data-ttu-id="a57ba-164">Öngörü hizmeti kullanmak için gereken her zaman oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a57ba-164">To use the prediction service in your application you will have to create it every time it is needed.</span></span> <span data-ttu-id="a57ba-165">Bu durumda, dikkate alınması gereken bir en iyi ASP.NET Core bağımlılık ekleme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="a57ba-165">In that case, a best practice to consider is ASP.NET Core dependency injection.</span></span>

<span data-ttu-id="a57ba-166">Hakkında bilgi edinmek istiyorsanız aşağıdaki bağlantıda daha fazla bilgi sağlar. [bağımlılık ekleme](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="a57ba-166">The following link provides more information if you want to learn about [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="a57ba-167">Açık *Startup.cs* sınıfı ve aşağıdaki using deyimini dosyanın en üstüne:</span><span class="sxs-lookup"><span data-stu-id="a57ba-167">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

```csharp
using System.IO;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
using SentimentAnalysisWebAPI.Services;
```

1. <span data-ttu-id="a57ba-168">Aşağıdaki kod satırlarını ekleme *Createservicereplicalisteners()* yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a57ba-168">Add the following lines of code to the *ConfigureServices* method:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddSingleton<MLContext>();
    services.AddSingleton<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
    {
        MLContext mlContext = ctx.GetRequiredService<MLContext>();
        string modelFilePathName = "MLModels/sentiment_model.zip";

        //Load model from file
        ITransformer model;
        using (var stream = File.OpenRead(modelFilePathName))
        {
            model = mlContext.Model.Load(stream);
        }

        // Return prediction engine
        return model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);
    });
    services.AddSingleton<PredictionService>();
}
```

<span data-ttu-id="a57ba-169">Yüksek düzeyde, bu kod nesneleri ve otomatik yerine el ile yapmanıza gerek kalmadan uygulama tarafından istendiğinde hizmetlerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="a57ba-169">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

## <a name="create-predict-controller"></a><span data-ttu-id="a57ba-170">Oluşturma denetleyicisi tahmin edin</span><span class="sxs-lookup"><span data-stu-id="a57ba-170">Create Predict Controller</span></span>

<span data-ttu-id="a57ba-171">Gelen HTTP isteklerini işlemek için bir denetleyici oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a57ba-171">To process your incoming HTTP requests, you need to create a controller.</span></span>

1. <span data-ttu-id="a57ba-172">Çözüm Gezgini'nde sağ *denetleyicileri* dizin ve ardından **Ekle > denetleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="a57ba-172">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="a57ba-173">İçinde **Yeni Öğe Ekle** iletişim kutusunda **boş API denetleyicisi** seçip **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a57ba-173">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="a57ba-174">Komut istemi değişim **Denetleyici adı** alanı *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="a57ba-174">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="a57ba-175">Ardından Ekle düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a57ba-175">Then, select the Add button.</span></span> <span data-ttu-id="a57ba-176">*PredictController.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="a57ba-176">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="a57ba-177">Aşağıdaki using deyimini üstüne *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="a57ba-177">Add the following using statement to the top of *PredictController.cs*:</span></span>

```csharp
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using SentimentAnalysisWebAPI.Services;
```

<span data-ttu-id="a57ba-178">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *PredictController.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="a57ba-178">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

```csharp
public class PredictController : ControllerBase
{

    private readonly PredictionService _predictionService;

    public PredictController(PredictionService predictionService)
    {
        _predictionService = predictionService; //Define prediction service
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }
        return Ok(_predictionService.Predict(input));
    }

}
```

<span data-ttu-id="a57ba-179">Bağımlılık ekleme erişmenizi denetleyicinin oluşturucusuna geçirerek bu tahmin hizmet atanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a57ba-179">This is assigning the Prediction service by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="a57ba-180">Ardından, İLETİDE bu denetleyicinin öngörü hizmeti yöntemi tahminlerde bulunabilir ve kullanıcıya geri başarılı olursa sonuçları döndürmek için kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="a57ba-180">Then, in the POST method of this controller the Prediction service is being used to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="a57ba-181">Web API'si yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="a57ba-181">Test Web API Locally</span></span>

<span data-ttu-id="a57ba-182">Her şeyi ayarlandıktan sonra uygulama test etme vakti.</span><span class="sxs-lookup"><span data-stu-id="a57ba-182">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="a57ba-183">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a57ba-183">Run the application.</span></span>
1. <span data-ttu-id="a57ba-184">PowerShell'i açın ve bağlantı noktası, bağlantı noktası olduğu aşağıdaki kodu girin. uygulamanızı dinlediği.</span><span class="sxs-lookup"><span data-stu-id="a57ba-184">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

<span data-ttu-id="a57ba-185">Başarılı olursa çıktı aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="a57ba-185">If successful, the output should look similar to the text below:</span></span>

```powershell
Toxic
```

<span data-ttu-id="a57ba-186">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="a57ba-186">Congratulations!</span></span> <span data-ttu-id="a57ba-187">Ayrıca, bir ASP.NET Core API'si kullanarak internet üzerinden tahminlerde bulunmak üzere modelinizi başarıyla hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="a57ba-187">You have successfully served your model to make predictions over the internet using an ASP.NET Core API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a57ba-188">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="a57ba-188">Next Steps</span></span>

- [<span data-ttu-id="a57ba-189">Azure’a dağıtma</span><span class="sxs-lookup"><span data-stu-id="a57ba-189">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)